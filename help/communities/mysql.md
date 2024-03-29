---
title: Configuração do MySQL para Recursos de Ativação
seo-title: MySQL Configuration for Enablement Features
description: Conectando seu servidor MySQL
seo-description: Connecting your MySQL server
uuid: e02d9404-de75-4fdb-896c-ea3f64f980a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9222bc93-c231-4ac8-aa28-30d784a4ca3b
role: Admin
exl-id: 1dfb55c2-41cb-445f-9bf8-f12ab6b8e9d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 3%

---

# Configuração do MySQL para Recursos de Ativação {#mysql-configuration-for-enablement-features}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O MySQL é um banco de dados relacional usado principalmente para rastreamento e relatórios de dados SCORM para recursos de capacitação. Inclui tabelas para outros recursos, como rastreamento de pausa/retomada de vídeo.

Essas instruções descrevem como se conectar ao servidor MySQL, estabelecer o banco de dados de ativação e preencher o banco de dados com dados iniciais.

## Requisitos {#requirements}

Antes de configurar o recurso de ativação do MySQL for Communities, certifique-se de

* Instalar [Servidor MySQL](https://dev.mysql.com/downloads/mysql/) Community Server versão 5.6
   * A versão 5.7 não é compatível com SCORM
   * Pode ser o mesmo servidor que a instância do autor AEM
* Em todas as instâncias AEM, instale o [Driver JDBC para MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Instalar [Workbench MySQL](https://dev.mysql.com/downloads/tools/workbench/)
* Em todas as instâncias AEM, instale o [Pacote SCORM](enablement.md#scorm)

## Instalando o MySQL {#installing-mysql}

O MySQL deve ser baixado e instalado de acordo com as instruções para o SO de destino.

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

## Habilitar conexão {#enablement-connection}

Quando o MySQL Workbench é iniciado pela primeira vez, a menos que já esteja em uso para outros fins, ele ainda não mostrará conexões:

![chlimage_1-327](assets/chlimage_1-327.png)

### Novas configurações de conexão {#new-connection-settings}

1. Selecione o ícone &quot;+&quot; à direita de `MySQL Connections`.
1. Na caixa de diálogo `Setup New Connection`, insira os valores adequados para sua plataforma para fins de demonstração, com a instância de AEM do autor e o MySQL no mesmo servidor:
   * Nome da conexão: `Enablement`
   * Método de conexão: `Standard (TCP/IP)`
   * Nome do host: `127.0.0.1`
   * Nome de usuário: `root`
   * Senha: `no password by default`
   * Esquema padrão: `leave blank`
1. Selecionar `Test Connection` para verificar a conexão com o serviço MySQL em execução

**Notas**:

* A porta padrão é `3306`
* O `Connection Name` escolhido é inserido como `datasource` nome em [Configuração JDBC OSGi](#configure-jdbc-connections)

#### Conexão bem-sucedida {#successful-connection}

![chlimage_1-328](assets/chlimage_1-328.png)

#### Nova conexão de ativação {#new-enablement-connection}

![chlimage_1-329](assets/chlimage_1-329.png)

## Configuração do banco de dados {#database-setup}

Ao abrir a nova conexão de Ativação, observe que há um esquema de teste e contas de usuário padrão.

![chlimage_1-330](assets/chlimage_1-330.png)

### Obter Scripts SQL {#obtain-sql-scripts}

Os scripts SQL são obtidos usando o CRXDE Lite na instância do autor. O [Pacote SCORM](deploy-communities.md#scorm) deve ser instalado:

1. Navegue até CRXDE Lite
   * Por exemplo, [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. Expanda o `/libs/social/config/scorm/` pasta
1. Download `database_scormengine.sql`
1. Download `database_scorm_integration.sql`

![chlimage_1-331](assets/chlimage_1-331.png)

Um método para baixar o esquema é

* Selecione o `jcr:content`nó para o arquivo sql
* Observe o valor da variável `jcr:data`propriedade é um link de exibição
* Selecione o link de exibição para salvar os dados em um arquivo local

### Criar Banco de Dados SCORM {#create-scorm-database}

O Banco de Dados SCORM de Ativação a ser criado é:

* name: `ScormEngineDB`
* criado a partir de scripts:
   * esquema: `database_scormengine.sql`
   * dados: `database_scorm_integration.sql`
Siga as etapas abaixo (
[open](#step-open-sql-file), [execute](#step-execute-sql-script)) para instalar cada [Script SQL](#obtain-sql-scripts) . [Atualizar](#refresh) quando necessário para ver os resultados da execução do script.

Certifique-se de instalar o esquema antes de instalar os dados.

>[!CAUTION]
>
>Se o nome do banco de dados for alterado, especifique-o corretamente em
>
>* [Configuração JDBC](#configure-jdbc-connections)
>* [Configuração do SCORM](#configure-scorm)
>


#### Etapa 1: abrir arquivo SQL {#step-open-sql-file}

No MySQL Workbench

* No menu suspenso Arquivo
* Selecionar `Open SQL Script ...`
* Nesta ordem, selecione um dos seguintes:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![chlimage_1-332](assets/chlimage_1-332.png)

#### Etapa 2: executar script SQL {#step-execute-sql-script}

Na janela Workbench para o arquivo aberto na Etapa 1, selecione o `lightening (flash) icon` para executar o script.

Observe que a execução da variável `database_scormengine.sql` o script para criar o banco de dados SCORM pode levar um minuto para ser concluído.

![chlimage_1-333](assets/chlimage_1-333.png)

#### Atualizar {#refresh}

Depois que os scripts forem executados, será necessário atualizar a variável `SCHEMAS`da seção `Navigator` para ver o novo banco de dados. Use o ícone de atualização à direita de &#39;SCHEMAS&#39;:

![chlimage_1-334](assets/chlimage_1-334.png)

#### Resultado: scormenginedb {#result-scormenginedb}

Depois de instalar e atualizar o SCHEMAS, o **`scormenginedb`** estará visível.

![chlimage_1-335](assets/chlimage_1-335.png)

## Configurar conexões JDBC {#configure-jdbc-connections}

A configuração OSGi para **Pool de Conexões JDBC do Day Commons** configura o driver JDBC do MySQL.

Todas as instâncias de publicação e criação de AEM devem apontar para o mesmo servidor MySQL.

Quando o MySQL é executado em um servidor diferente de AEM, o nome do host do servidor deve ser especificado no lugar de &#39;localhost&#39; no conector JDBC (que preenche a variável [ScormEngine](#configurescormengineservice) configuração).

* Em cada autor e publicar AEM instância
* Conectado com privilégios de administrador
* Acesse o [console da web](../../help/sites-deploying/configuring-osgi.md)
   * Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Localize a variável `Day Commons JDBC Connections Pool`
* Selecione o `+` ícone para criar uma nova configuração

![chlimage_1-336](assets/chlimage_1-336.png)

* Insira os seguintes valores:
   * **[!UICONTROL Classe de driver JDBC]**: `com.mysql.jdbc.Driver`
   * **URIJ de conexão DBC**: `jdbc:mysql://localhost:3306/aem63reporting` especifique o servidor no lugar de localhost se o servidor MySQL não for o mesmo que &#39;this&#39; AEM server
   * **[!UICONTROL Nome do usuário]**: Raiz ou insira o nome de usuário configurado para o servidor MySQL, se não for &#39;root&#39;
   * **[!UICONTROL Senha]**: Limpar este campo se não houver senha definida para o MySQL, caso contrário, introduzir a senha configurada para o nome de utilizador do MySQL
   * **[!UICONTROL Nome da fonte de dados]**: Nome inserido para o [Conexão MySQL](#new-connection-settings), por exemplo, &quot;ativation&quot;
* Selecione **[!UICONTROL Salvar]**

## Configurar Scorm {#configure-scorm}

### Serviço do AEM Communities ScormEngine {#aem-communities-scormengine-service}

A configuração OSGi para **Serviço do AEM Communities ScormEngine** configura o SCORM para o uso do servidor MySQL pela comunidade de ativação.

Essa configuração está presente quando a variável [Pacote SCORM](deploy-communities.md#scorm-package) está instalado.

Todas as instâncias de publicação e criação apontam para o mesmo servidor MySQL.

Quando o MySQL é executado em um servidor diferente de AEM, o nome do host do servidor deve ser especificado no lugar de &#39;localhost&#39; no Serviço ScormEngine, que normalmente é preenchido a partir do [Conexão JDBC](#configure-jdbc-connections) configuração.

* Em cada autor e publicar AEM instância
* Conectado com privilégios de administrador
* Acesse o [console da web](../../help/sites-deploying/configuring-osgi.md)
   * Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Localize a variável `AEM Communities ScormEngine Service`
* Selecione o ícone de edição
   ![chlimage_1-337](assets/chlimage_1-337.png)
* Verifique se os seguintes valores de parâmetro estão consistentes com a variável [Conexão JDBC](#configurejdbcconnectionspool) configuração:
   * **[!UICONTROL URI de conexão JDBC]**: `jdbc:mysql://localhost:3306/ScormEngineDB` *ScormEngineDB* é o nome padrão do banco de dados nos scripts SQL
   * **[!UICONTROL Nome do usuário]**: Raiz ou insira o nome de usuário configurado para o servidor MySQL, se não for &#39;root&#39;
   * **[!UICONTROL Senha]**: Limpar este campo se não houver senha definida para o MySQL, caso contrário, introduzir a senha configurada para o nome de utilizador do MySQL
* Em relação ao seguinte parâmetro:
   * **[!UICONTROL Senha do usuário do Scorm]**: NÃO EDITAR

      Apenas para uso interno. É para um usuário de serviço especial usado pelo AEM Communities para se comunicar com o mecanismo de pontuação.
* Selecione **[!UICONTROL Salvar]**

### Filtro CSRF do Adobe Granite {#adobe-granite-csrf-filter}

Para garantir que os cursos de ativação funcionem corretamente em todos os navegadores, é necessário adicionar o Mozilla como Agente de usuário que não é verificado pelo filtro CSRF.

* Em cada instância do AEM de publicação
* Conectado com privilégios de administrador
* Acesse o [console da web](../../help/sites-deploying/configuring-osgi.md)
   * Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* Localizar `Adobe Granite CSRF Filter`
* Selecione o ícone de edição
   ![chlimage_1-338](assets/chlimage_1-338.png)
* Selecione o `[+]` ícone para adicionar um Agente de Usuário Seguro
* Insira `Mozilla/*`
* Selecione **[!UICONTROL Salvar]**
