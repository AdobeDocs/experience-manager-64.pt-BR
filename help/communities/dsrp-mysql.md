---
title: Configuração do MySQL para DSRP
seo-title: MySQL Configuration for DSRP
description: Como se conectar ao servidor MySQL e estabelecer o banco de dados UGC
seo-description: How to connect to the MySQL server and establish the UGC database
uuid: c058cc88-7ca2-4aed-9a36-b080e603f886
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: edc3043c-7ec4-4e4a-b008-95f1784f012e
role: Admin
exl-id: 1de1ffc6-63f8-4316-a2fa-5095d407c265
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 3%

---

# Configuração do MySQL para DSRP {#mysql-configuration-for-dsrp}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

MySQL é um banco de dados relacional que pode ser usado para armazenar conteúdo gerado pelo usuário (UGC).

Essas instruções descrevem como se conectar ao servidor MySQL e estabelecer o banco de dados UGC.

## Requisitos {#requirements}

* [Pacote de recursos mais recente das Comunidades](deploy-communities.md#latestfeaturepack)
* [Driver JDBC para MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Um banco de dados relacional:

   * [Servidor MySQL](https://dev.mysql.com/downloads/mysql/) Community Server versão 5.6 ou posterior

      * Pode ser executado no mesmo host que AEM ou executado remotamente
   * [Workbench MySQL](https://dev.mysql.com/downloads/tools/workbench/)


## Instalando o MySQL {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) O deve ser baixado e instalado de acordo com as instruções para o SO de destino.

### Nomes de tabela em minúsculas {#lower-case-table-names}

Como o SQL não diferencia maiúsculas de minúsculas, para sistemas operacionais que diferenciam maiúsculas de minúsculas, é necessário incluir uma configuração para minúsculas todos os nomes de tabela.

Por exemplo, para especificar todos os nomes de tabela de letras minúsculas em um sistema operacional Linux:

* Editar arquivo `/etc/my.cnf`
* No `[mysqld]` adicione a seguinte linha:

   `lower_case_table_names = 1`

### Conjunto de caracteres UTF8 {#utf-character-set}

Para oferecer um melhor suporte multilíngue, é necessário usar o conjunto de caracteres UTF8.

Altere MySQL para ter UTF8 como seu conjunto de caracteres:

* mysql> DEFINIR NOMES &#39;utf8&#39;;

Altere o banco de dados MySQL para UTF8:

* Editar arquivo `/etc/my.cnf`
* No `[client]` adicione a seguinte linha:

   `default-character-set=utf8`

* No `[mysqld]` adicione a seguinte linha:

   `character-set-server=utf8`

## Instalar o MySQL Workbench {#installing-mysql-workbench}

O MySQL Workbench fornece uma interface para executar scripts SQL que instalam o esquema e os dados iniciais.

O MySQL Workbench deve ser baixado e instalado seguindo as instruções para o SO de destino.

## Conexão de comunidades {#communities-connection}

Quando o MySQL Workbench é iniciado pela primeira vez, a menos que já esteja em uso para outros fins, ele ainda não mostrará conexões:

![chlimage_1-104](assets/chlimage_1-104.png)

### Novas configurações de conexão {#new-connection-settings}

1. Selecione o `+` à direita de `MySQL Connections`.
1. Na caixa de diálogo `Setup New Connection`, insira os valores adequados para sua plataforma

   Para fins de demonstração, com a instância do autor AEM e o MySQL no mesmo servidor:

   * Nome da conexão: `Communities`
   * Método de conexão: `Standard (TCP/IP)`
   * Nome do host: `127.0.0.1`
   * Nome de usuário: `root`
   * Senha: `no password by default`
   * Esquema padrão: `leave blank`

1. Selecionar `Test Connection` para verificar a conexão com o serviço MySQL em execução

**Notas**:

* A porta padrão é `3306`
* O Nome da Conexão escolhido é inserido como o nome da fonte de dados em [Configuração JDBC OSGi](#configurejdbcconnections)

#### Nova conexão de comunidades {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## Configuração do banco de dados {#database-setup}

Abra a conexão Comunidades para instalar o banco de dados.

![chlimage_1-106](assets/chlimage_1-106.png)

### Obter o script SQL {#obtain-the-sql-script}

O script SQL é obtido do repositório AEM:

1. Navegue até CRXDE Lite

   * Por exemplo, [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Selecione a pasta /libs/social/config/datastore/dsrp/schema
1. Download `init-schema.sql`

![chlimage_1-107](assets/chlimage_1-107.png)

Um método para baixar o esquema é

* Selecione o `jcr:content`nó para o arquivo sql
* Observe o valor da variável `jcr:data`propriedade é um link de exibição

* Selecione o link de exibição para salvar os dados em um arquivo local

### Criar o Banco de Dados DSRP {#create-the-dsrp-database}

Siga as etapas abaixo para instalar o banco de dados. O nome padrão do banco de dados é `communities`.

Se o nome do banco de dados for alterado no script, altere-o também no [Configuração JDBC](#configurejdbcconnections).

#### Etapa 1: abrir arquivo SQL {#step-open-sql-file}

No MySQL Workbench

* No menu suspenso Arquivo
* Selecione o download `init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### Etapa 2: executar script SQL {#step-execute-sql-script}

Na janela Workbench para o arquivo aberto na Etapa 1, selecione o `lightening (flash) icon` para executar o script.

Na imagem a seguir, a variável `init_schema.sql` O arquivo está pronto para ser executado:

![chlimage_1-109](assets/chlimage_1-109.png)

#### Atualizar {#refresh}

Depois que o script é executado, é necessário atualizar a variável `SCHEMAS`da seção `Navigator` para ver o novo banco de dados. Use o ícone de atualização à direita de &#39;SCHEMAS&#39;:

![chlimage_1-110](assets/chlimage_1-110.png)

## Configurar conexão JDBC {#configure-jdbc-connection}

A configuração OSGi para **Pool de Conexões JDBC do Day Commons** configura o driver JDBC do MySQL.

Todas as instâncias de publicação e criação de AEM devem apontar para o mesmo servidor MySQL.

Quando o MySQL é executado em um servidor diferente de AEM, o nome do host do servidor deve ser especificado no lugar de &#39;localhost&#39; no conector JDBC.

* Em cada autor e publicar AEM instância
* Conectado com privilégios de administrador
* Acesse o [console da web](../../help/sites-deploying/configuring-osgi.md)

   * Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Localize a variável `Day Commons JDBC Connections Pool`
* Selecione o `+` ícone para criar uma nova configuração de conexão

![chlimage_1-111](assets/chlimage_1-111.png)

* Insira os seguintes valores:

   * **[!UICONTROL Classe de driver JDBC]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL URI de conexão JDBC]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      Especificar servidor no lugar de localhost se o servidor MySQL não for o mesmo que &#39;this&#39; AEM servidor

      *comunidades* é o nome padrão do banco de dados (schema)

   * **[!UICONTROL Nome do usuário]**: `root`

      Ou insira o Nome de Usuário configurado para o servidor MySQL, se não for &#39;root&#39;

   * **[!UICONTROL Senha]**:

      Limpar este campo se não houver senha definida para o MySQL,

      caso contrário, insira a senha configurada para o nome de usuário do MySQL
   * **[!UICONTROL Nome da fonte de dados]**: nome inserido para o [Conexão MySQL](#new-connection-settings), por exemplo, &quot;comunidades&quot;

* Selecione **[!UICONTROL Salvar]**
