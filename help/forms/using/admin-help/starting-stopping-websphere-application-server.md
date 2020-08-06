---
title: Iniciando e parando o WebSphere Application Server
seo-title: Iniciando e parando o WebSphere Application Server
description: Vários procedimentos exigem que você pare ou start a instância do WebSphere onde deseja implantar AEM produtos de formulários. Este documento descreve como start e interromper o WebSphere Application Server.
seo-description: Vários procedimentos exigem que você pare ou start a instância do WebSphere onde deseja implantar AEM produtos de formulários. Este documento descreve como start e interromper o WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Iniciando e parando o WebSphere Application Server {#starting-and-stopping-websphere-application-server}

Vários procedimentos exigem que você pare ou start a instância do WebSphere onde deseja implantar AEM produtos de formulários. Se não tiver certeza se o servidor de aplicativos foi iniciado, você pode primeiro visualização o status do WebSphere Application Server.

## Visualização do status do WebSphere Application Server {#view-the-status-of-websphere-application-server}

1. Em um prompt de comando, vá para o diretório raiz *[/bin do]* appserver.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do Servidor de aplicativos WebSphere:

   * (Windows) `serverStatus.bat`*server_name *
   * (Linux, UNIX) ./ nome_ `serverStatus.sh`*do_servidor *

## Start WebSphere Application Server {#start-websphere-application-server}

1. Em um prompt de comando, vá para o diretório raiz *[/bin do]* appserver.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do Servidor de aplicativos WebSphere:

   * (Windows) `startServer.bat`*server_name *
   * (Linux, UNIX) ./ nome_ `startServer.sh`*do_servidor *

## Parar o WebSphere Application Server {#stop-websphere-application-server}

1. Em um prompt de comando, vá para o diretório raiz *[/bin do]* appserver.
1. Digite o seguinte comando, substituindo *server_name* pelo nome do Servidor de aplicativos WebSphere:

   * (Windows) `stopServer.bat`*server_name *
   * (Linux, UNIX) ./ nome_ `stopServer.sh`*do_servidor *

