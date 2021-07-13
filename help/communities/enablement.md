---
title: Configuração dos recursos de ativação
seo-title: Configuração dos recursos de ativação
description: Configurar recursos de ativação em Comunidades
seo-description: Configurar recursos de ativação em Comunidades
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Configuração dos recursos de ativação {#configuring-enablement-features}

## Visão geral {#overview}

Os recursos de ativação fornecem a capacidade de criar [comunidades de ativação](overview.md#enablement-community).

* Esse recurso requer licenciamento adicional para uso em um ambiente de produção.

O uso dos recursos de ativação exige o seguinte:

Instalação de:

* ****
SCORMSharable Content Object Reference Model (SCORM) é uma coleção de padrões e especificações para e-learning. O SCORM também define como o conteúdo pode ser empacotado em um arquivo ZIP transferível.

* ****
MySQLMySQL é um banco de dados relacional usado principalmente para rastreamento e relatórios de dados SCORM para Ativação, bem como tabelas para rastrear o progresso do vídeo. O pacote de recursos SCORM for enablement requer o driver JDBC do MySQL.

* ****
FFmpeg é uma solução para conversão e transmissão de áudio e vídeo e, quando instalada, é usada para a transcodificação adequada dos Ativos de  [vídeo](../../help/sites-authoring/default-components-foundation.md#video). Para comunidades de ativação, ele é usado no ambiente de criação para obter metadados para recursos carregados, bem como gerar uma miniatura para exibição ao listar o recurso.

Configuração de:

* **Gerentes**
da comunidadePara comunidades de ativação, somente membros do 
`Community Enablement Managers` o grupo de usuários pode receber a função de  `*Community Site* Enablement Manager`, cujas permissões podem incluir criação de conteúdo, atribuições e gerenciamento de membros no ambiente de publicação.

Configuração opcional de:

* **Adobe**
AnalyticsIntegration with Adobe Analytics adiciona recursos abrangentes de relatório e oferece suporte à adição do Video Heartbeat ao Analytics.

* **Dispatcher**

## Etapas de configuração {#configuration-steps}

Veja a seguir as etapas necessárias para ativar as comunidades.

Cada etapa vincula-se à documentação que fornece os detalhes necessários.

**Em todas as instâncias de autor/publicação:**

1. **[instale o driver JDBC para](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (pacotes): Instale  *http://localhost:4502/system/console/*
pacotesInstalar  ** antes de instalar o pacote SCORM

1. **[instale o](deploy-communities.md#scorm-package)**
pacote SCORMuse o Gerenciador de Pacotes: 
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
pool de Conexões JDBCUse o Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar o](mysql.md#aem-communities-scormengine-service)**
serviço de mecanismo SCORMusar Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurar](mysql.md#adobe-granite-csrf-filter)**
filtros CSRFuse o Console da Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**Na instância do autor:**

1. (*opcional*) **[configurar o serviço Analytics](analytics.md)**
Use Ferramentas, Implantação, console Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurar o console](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUse Fluxo de trabalho/Modelos

1. **[habilite o Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceUse Web Console (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[criar](users.md#creating-community-members)** administradores de comunidadePara o ambiente de criação, use o console de segurança da interface clássica:  *http://localhost:4502/*
usuário_usuário_usuário_criar com caminho = /home/usuários/comunidade

   * Adicione membros aos seguintes grupos:

      * Gerentes de ativação da comunidade
      * Administradores das Comunidades

## Dispatcher {#dispatcher}

Quando a implantação inclui [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), para que os recursos de ativação funcionem corretamente, as seções `clientheader`e `filter`precisam de modificação. Consulte [Configuração do Dispatcher para Comunidades](dispatcher.md#enablement).
