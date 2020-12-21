---
title: Configuração dos recursos de ativação
seo-title: Configuração dos recursos de ativação
description: Configurar recursos de ativação nas Comunidades
seo-description: Configurar recursos de ativação nas Comunidades
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Configurando os recursos de ativação {#configuring-enablement-features}

## Visão geral {#overview}

Os recursos de ativação fornecem a capacidade de criar [comunidades de ativação](overview.md#enablement-community).

* Este recurso requer licenciamento adicional para uso em um ambiente de produção.

O uso dos recursos de ativação exige o seguinte:

Instalação de:

* **O**
SCORMSharable Content Object Reference Model (SCORM) é uma coleção de padrões e especificações para e-learning. O SCORM também define como o conteúdo pode ser empacotado em um arquivo ZIP transferível.

* **O**
MySQLMySQL é um banco de dados relacional usado principalmente para rastreamento SCORM e dados de relatórios para Ativação, bem como tabelas para rastrear o progresso do vídeo. O SCORM para o pacote de recursos de ativação requer o driver JDBC MySQL.

* **O**
FFmpegFFmpeg é uma solução para conversão e transmissão de áudio e vídeo e, quando instalada, é usada para transcodificação adequada dos ativos [ de ](../../help/sites-authoring/default-components-foundation.md#video)vídeo. Para comunidades de ativação, é usado no ambiente do autor para obter metadados para recursos carregados, bem como para gerar uma miniatura para exibição ao listar o recurso.

Configuração de:

* **Gerentes**
da comunidadePara comunidades de ativação, somente os membros do 
`Community Enablement Managers` o grupo de usuários pode receber a função de  `*Community Site* Enablement Manager`, cujas permissões podem incluir criação de conteúdo, atribuições e gerenciamento de membros no ambiente de publicação.

Configuração opcional de:

* **A integração do Adobe**
Analytics com a Adobe Analytics adiciona recursos abrangentes do relatórios e oferece suporte à adição do Video Heartbeat ao Analytics.

* **Dispatcher**

## Etapas de configuração {#configuration-steps}

Veja a seguir as etapas necessárias para ativar as comunidades.

Cada etapa vincula-se à documentação que fornece os detalhes necessários.

**Em todas as instâncias de autor/publicação:**

1. **[instale o driver JDBC para o](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (pacotes): Instale  *http://localhost:4502/system/console/*
bundlesInstale  ** antes de instalar o pacote SCORM

1. **[instale o](deploy-communities.md#scorm-package)**
pacote SCORMuse o Gerenciador de pacotes: 
*http://localhost:4502/crx/packmgr/*

**Em qualquer servidor:**

1. **[instalar MySQL, MySQL Workbench](mysql.md)**

1. **[instalar](mysql.md#database-setup)**
bancos de dados MySQLExecutar scripts SQL baixados da instância do autor
\
   Usar o MySQL Workbench

**Na mesma instância do autor de hospedagem do servidor:**

1. **[instalar FFmpeg](ffmpeg.md)**

**Em todas as instâncias de autor/publicação:**

1. **[configurar o](mysql.md#configure-jdbc-connections)**
pool de Conexões JDBCuse o Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configure o](mysql.md#aem-communities-scormengine-service)**
serviço de mecanismo SCORMUse o Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar](mysql.md#adobe-granite-csrf-filter)**
filtros CSRFusar o Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**Na instância do autor:**

1. (*opcional*) **[configurar o serviço do Analytics](analytics.md)**
Use Ferramentas, Implantação, console Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurar o console Fluxo de Trabalho/Modelos](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUse

1. **[habilitar o](deploy-communities.md#tunnel-service-on-author)**
serviço de túnelUse o console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[criar](users.md#creating-community-members)** administradores de comunidadePara o ambiente do autor, use o console de segurança clássica-IU:  *http://localhost:4502/*
usreadmincreate usuário(s) com caminho = /home/users/community

   * Adicione membros aos seguintes grupos:

      * Gerentes de habilitação da comunidade
      * Administradores de comunidades

## Dispatcher {#dispatcher}

Quando a implantação inclui [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), para que os recursos de ativação funcionem corretamente, as seções `clientheader`e `filter`precisam de modificação. Consulte [Configurando o Dispatcher para Comunidades](dispatcher.md#enablement).
