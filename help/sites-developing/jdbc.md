---
title: Conexão com Bancos de Dados SQL
seo-title: Connecting to SQL Databases
description: Acesse um banco de dados SQL externo para que seus aplicativos AEM possam interagir com os dados
seo-description: Access an external SQL database to so that your AEM applications can interact with the data
uuid: 0af0ed08-9487-4c37-87ce-049c9b4c1ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 11a11803-bce4-4099-9b50-92327608f37b
exl-id: 7f10451d-3acb-4298-82f3-07897f66e407
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 0%

---

# Conexão com Bancos de Dados SQL{#connecting-to-sql-databases}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Acesse um banco de dados SQL externo para que seus aplicativos CQ possam interagir com os dados:

1. [Crie ou obtenha um pacote OSGi que exporte o pacote de driver JDBC](#bundling-the-jdbc-database-driver).
1. [Configurar um provedor de pool de fontes de dados JDBC](#configuring-the-jdbc-connection-pool-service).
1. [Obter um objeto de fonte de dados e criar a conexão no seu código](#connecting-to-the-database).

## Pacote do driver de banco de dados JDBC {#bundling-the-jdbc-database-driver}

Alguns fornecedores de banco de dados fornecem drivers JDBC em um pacote OSGi, por exemplo [MySQL](https://www.mysql.com/downloads/connector/j/). Se o driver JDBC do seu banco de dados não estiver disponível como um pacote OSGi, obtenha o JAR do driver e coloque-o em um pacote OSGi. O pacote deve exportar os pacotes necessários para interagir com o servidor de banco de dados. O pacote também deve importar os pacotes que ele faz referência.

O exemplo a seguir usa a variável [Plug-in do pacote para Maven](https://felix.apache.org/site/apache-felix-maven-bundle-plugin-bnd.html) para embrulhar o driver HSQLDB em um pacote OSGi. O POM instrui o plug-in a incorporar o arquivo hsqldb.jar identificado como uma dependência. Todos os pacotes org.hsqldb são exportados.

O plug-in determina automaticamente quais pacotes serão importados e os lista no arquivo MANIFEST.MF do pacote. Se algum dos pacotes não estiver disponível no servidor CQ, o pacote não será iniciado após a instalação. Duas soluções possíveis são as seguintes:

* Indique no POM que os pacotes são opcionais. Use essa solução quando a conexão JDBC não exigir os membros do pacote. Use o elemento Importar-Pacote para indicar pacotes opcionais, como no exemplo a seguir:

   `<Import-Package>org.jboss.*;resolution:=optional,*</Import-Package>`
* Encapsule os arquivos JAR que contêm os pacotes em um pacote OSGi que exporta os pacotes e implante o pacote. Use essa solução quando os membros do pacote forem necessários durante a execução do código.

O conhecimento do código-fonte permite que você decida qual solução usar. Você também pode tentar qualquer solução e realizar testes para validar a solução.

### POM que empacota hsqldb.jar {#pom-that-bundles-hsqldb-jar}

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>hsqldb-jdbc-driver-bundle</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <name>wrapper-bundle-hsqldb-driver</name>
  <url>www.adobe.com</url>
  <description>Exports the HSQL JDBC driver</description>
  <packaging>bundle</packaging>
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.felix</groupId> 
        <artifactId>maven-bundle-plugin</artifactId>
        <version>1.4.3</version> 
        <extensions>true</extensions> 
        <configuration> 
         <instructions> 
            <Embed-Dependency>*</Embed-Dependency>
            <_exportcontents>org.hsqldb.*</_exportcontents>
          </instructions>
        </configuration> 
      </plugin>
    </plugins>
  </build>
  <dependencies>
    <dependency>
      <groupId>hsqldb</groupId>
      <artifactId>hsqldb</artifactId>
      <version>2.2.9</version>
    </dependency>
  </dependencies>
</project>
```

Os links a seguir abrem as páginas de download de alguns produtos de banco de dados populares:

* [Microsoft SQL Server](https://www.microsoft.com/en-us/download/details.aspx?displaylang=en&amp;id=11774)
* [Oracle](https://www.oracle.com/technetwork/database/features/jdbc/index-091264.html)
* [IBM DB2](https://www-01.ibm.com/support/docview.wss?uid=swg27007053)

### Configuração do Serviço de Pool de Conexões JDBC {#configuring-the-jdbc-connection-pool-service}

Adicione uma configuração para o serviço Pool de conexões JDBC que usa o driver JDBC para criar objetos de fonte de dados. O código de aplicativo usa esse serviço para obter o objeto e se conectar ao banco de dados.

Pool de conexões JDBC ( `com.day.commons.datasource.jdbcpool.JdbcPoolService`) é um serviço de fábrica. Se você precisar de conexões que usam propriedades diferentes, por exemplo, acesso somente leitura ou leitura/gravação, crie várias configurações.

Ao trabalhar com o CQ, há vários métodos de gerenciamento das configurações desses serviços; see [Configuração do OSGi](/help/sites-deploying/configuring-osgi.md) para obter detalhes completos.

As seguintes propriedades estão disponíveis para configurar um serviço de conexão agrupado. Os nomes das propriedades são listados conforme aparecem no Console da Web. O nome correspondente de um `sling:OsgiConfig` é exibido entre parênteses. Os valores de exemplo são mostrados para um servidor HSQLDB e um banco de dados que tem um alias de `mydb`:

* Classe de Driver JDBC ( `jdbc.driver.class`): A classe Java a ser usada que implementa a interface java.sql.Driver, por exemplo `org.hsqldb.jdbc.JDBCDriver`. O tipo de dados é `String`.

* URI de Conexão JDBC ( `jdbc.connection.uri`): O URL do banco de dados a ser usado para criar a conexão, por exemplo `jdbc:hsqldb:hsql//10.36.79.223:9001/mydb`. O formato do URL deve ser válido para uso com o método getConnection da classe java.sql.DriverManager. O tipo de dados é `String`.

* Nome de usuário ( `jdbc.username`): O nome de usuário a ser usado para autenticação com o servidor de banco de dados. O tipo de dados é `String`.

* Senha ( `jdbc.password`): A senha a ser usada para autenticação do usuário. O tipo de dados é `String`.

* Consulta de validação ( `jdbc.validation.query`): A instrução SQL a ser usada para verificar se a conexão foi bem-sucedida, por exemplo `select 1 from INFORMATION_SCHEMA.SYSTEM_USERS`. O tipo de dados é `String`.

* Somente leitura por padrão (default.readonly): Selecione esta opção quando quiser que a conexão forneça acesso somente leitura. O tipo de dados é `Boolean`.
* Confirmação Automática Por Padrão ( `default.autocommit`): Selecione esta opção para criar transações separadas para cada comando SQL que é enviado para o banco de dados e cada transação é automaticamente confirmada. Não selecione essa opção quando estiver confirmando transações explicitamente em seu código. O tipo de dados é `Boolean`.

* Tamanho do Pool ( `pool.size`): O número de conexões simultâneas a serem disponibilizadas para o banco de dados. O tipo de dados é `Long`.

* Aguardar pool ( `pool.max.wait.msec`): O tempo decorrido antes de uma solicitação de conexão expirar. O tipo de dados é `Long`.

* Nome da origem de dados ( `datasource.name`): O nome dessa fonte de dados. O tipo de dados é `String`.

* Propriedades adicionais do serviço ( `datasource.svc.properties`): Um conjunto de pares de nome/valor que você deseja anexar ao URL de conexão. O tipo de dados é `String[]`.

O serviço Pool de Conexões JDBC é de fábrica. Portanto, se você usar um `sling:OsgiConfig` nó para configurar o serviço de conexão, o nome do nó deve incluir o PID do serviço de fábrica seguido por *`-alias`*. O alias que você usa deve ser exclusivo para todos os nós de configuração desse PID. Um exemplo de nome de nó é `com.day.commons.datasource.jdbcpool.JdbcPoolService-myhsqldbpool`.

![chlimage_1-7](assets/chlimage_1-7.png)

### Conexão com o banco de dados {#connecting-to-the-database}

No seu código Java, use o serviço DataSourcePool para obter um `javax.sql.DataSource` objeto para a configuração criada. O serviço DataSourcePool fornece a variável `getDataSource` que retorna um método `DataSource` para um determinado nome da fonte de dados. Como argumento do método, use o valor do Nome da Fonte de Dados (ou `datasource.name`) que você especificou para a configuração do Pool de Conexões JDBC.

O exemplo de código JSP a seguir obtém uma instância da fonte de dados hsqldbds, executa uma consulta SQL simples e exibe o número de resultados que são retornados.

#### JSP que executa uma pesquisa de banco de dados {#jsp-that-performs-a-database-lookup}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false"%><%
%><%@ page import="com.day.commons.datasource.poolservice.DataSourcePool" %><%
%><%@ page import="javax.sql.DataSource" %><%
%><%@ page import="java.sql.Connection" %><%
%><%@ page import="java.sql.SQLException" %><%
%><%@ page import="java.sql.Statement" %><%
%><%@ page import="java.sql.ResultSet"%><%
%><html>
<cq:include script="head.jsp"/>
<body>
<%DataSourcePool dspService = sling.getService(DataSourcePool.class);
  try {
     DataSource ds = (DataSource) dspService.getDataSource("hsqldbds"); 
     if(ds != null) {
         %><p>Obtained the datasource!</p><%
         %><%final Connection connection = ds.getConnection();
          final Statement statement = connection.createStatement();
          final ResultSet resultSet = statement.executeQuery("SELECT * from INFORMATION_SCHEMA.SYSTEM_USERS"); 
          int r=0;
          while(resultSet.next()){
             r=r+1;
          } 
          resultSet.close();
          %><p>Number of results: <%=r%></p><%
      } 
   }catch (Exception e) {
        %><p>error! <%=e.getMessage()%></p><%
    } 
%></body>
</html>
```

>[!NOTE]
>
>Se o método getDataSource lançar uma exceção porque a fonte de dados não foi encontrada, verifique se a configuração do serviço Pool de Conexões está correta. Verifique os nomes, valores e tipos de dados da propriedade.

>[!NOTE]
>
>Para saber como injetar um DataSourcePool em um pacote OSGi, consulte [Injetando um serviço DataSourcePool em um pacote OSGi do Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/datasourcepool.html).
