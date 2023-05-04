---
title: Use o Apache Tika para detectar o tipo MIME dos ativos digitais
description: Ativar o Apache Tika para ajudar [!DNL Experience Manager] Os ativos detectam o tipo MIME de ativos do fluxo de conteúdo durante a operação de upload, em vez da extensão de arquivo.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 6%

---

# Use o Apache Tika para detectar o tipo MIME dos ativos digitais {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Normalmente, o Adobe Experience Manager Assets detecta o tipo MIME de ativos que você faz upload de sua extensão de arquivo. Se você usar o Apache Tika para fazer upload de ativos, [!DNL Experience Manager] Os ativos detectam seu tipo MIME do fluxo de conteúdo durante a operação de upload, em vez da extensão de arquivo.

Esse recurso é desativado por padrão. Para ativar o recurso, configure a variável **Tipo Mime Day CQ DAM** do Configuration Manager.

>[!NOTE]
>
>A detecção de tipo MIME usando a biblioteca Apache Tika é uma operação que consome muitos recursos.

1. Ir para `https://[AEM_server]:[port]/system/console/configMgr` para abrir o console da Web do Configuration Manager.
1. Na lista de serviços, localize **[!UICONTROL Serviço de Tipo Mime Day CQ DAM]** e toque/clique no botão **[!UICONTROL Editar]** ao lado dele para abri-lo no modo de Edição.

1. Selecione o **[!UICONTROL Detectar MIME do conteúdo]** para permitir a análise de ativos carregados para determinar seu tipo MIME ao ignorar extensões de arquivo. Por padrão, essa opção não está selecionada.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Clique/toque em **[!UICONTROL Salvar]** para salvar as alterações.
