---
title: Use o Apache Tika para detectar o tipo MIME dos ativos digitais
description: Ative o Apache Tika para ajudar [!DNL Experience Manager] Os ativos detectam o tipo MIME de ativos do fluxo de conteúdo durante a operação de upload, em vez da extensão de arquivo.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 3%

---

# Use o Apache Tika para detectar o tipo MIME dos ativos digitais {#detecting-mime-type-of-assets-using-apache-tika}

Normalmente, o Adobe Experience Manager Assets detecta o tipo MIME de ativos que você faz upload de sua extensão de arquivo. Se você usar o Apache Tika para fazer upload de ativos, os [!DNL Experience Manager] Ativos detectam seu tipo MIME do fluxo de conteúdo durante a operação de upload, em vez da extensão de arquivo.

Esse recurso é desativado por padrão. Para ativar o recurso, configure o serviço **Day CQ DAM Mime Type** do Configuration Manager.

>[!NOTE]
>
>A detecção de tipo MIME usando a biblioteca Apache Tika é uma operação que consome muitos recursos.

1. Vá para `https://[AEM_server]:[port]/system/console/configMgr` para abrir o console da Web do Configuration Manager.
1. Na lista de serviços, localize **[!UICONTROL Day CQ DAM Mime Type Service]** e toque/clique no ícone **[!UICONTROL Edit]** ao lado dele para abri-lo no modo de Edição.

1. Selecione a opção **[!UICONTROL Detectar MIME do conteúdo]** para habilitar a análise de ativos carregados para determinar seu tipo MIME ao ignorar as extensões de arquivo. Por padrão, essa opção não está selecionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Clique/toque em **[!UICONTROL Salvar]** para salvar as alterações.
