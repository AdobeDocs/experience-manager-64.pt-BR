---
title: Usar o Apache Tika para detectar o tipo MIME de ativos digitais
description: Ative o Apache Tika para ajudar o AEM Assets a detectar o tipo MIME de ativos do fluxo de conteúdo durante a operação de upload em vez da extensão do arquivo.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Usar o Apache Tika para detectar o tipo MIME de ativos digitais {#detecting-mime-type-of-assets-using-apache-tika}

Normalmente, os ativos Adobe Experience Manager (AEM) detectam o tipo MIME de ativos que você carrega de sua extensão de arquivo. Se você usar o Apache Tika para fazer upload de ativos, os ativos AEM detectarão o tipo MIME do fluxo de conteúdo durante a operação de upload em vez da extensão do arquivo.

Esse recurso é desativado por padrão. Para ativar o recurso, configure o serviço **Day CQ DAM Mime Type** do Configuration Manager.

>[!NOTE]
>
>A detecção de tipo MIME usando a biblioteca Apache Tika é uma operação que consome muitos recursos.

1. Vá até `https://[AEM_server]:[port]/system/console/configMgr` para abrir o console da Web do Configuration Manager.
1. Na lista de serviços, localize o **[!UICONTROL Dia CQ DAM Mime Type Service]** e toque/clique no ícone **[!UICONTROL Editar]** ao lado dele para abri-lo no modo Editar.

1. Selecione a opção **[!UICONTROL Detectar MIME do conteúdo]** para permitir a análise de ativos carregados para determinar seu tipo MIME ao ignorar extensões de arquivo. Por padrão, essa opção não está selecionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Clique/toque em **[!UICONTROL Salvar]** para salvar as alterações.
