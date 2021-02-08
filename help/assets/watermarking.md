---
title: Adicionar marca d'água aos seus ativos digitais
description: Saiba como usar o recurso Marca d'água para adicionar uma marca d'água digital aos ativos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfd6d022ef7d21ab6fc4ed17483890eb5766af18
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 3%

---


# Marque seus ativos digitais {#watermarking}

[!DNL Adobe Experience Manager Assets] permite que você adicione uma marca d&#39;água digital aos ativos que ajudam os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. [!DNL Experience Manager Assets] suporta texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

Os ativos Adobe Experience Manager (AEM) permitem que você adicione uma marca d&#39;água digital a imagens que ajudam os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. A AEM Assets oferece suporte ao texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

Para poder aplicar uma marca d&#39;água em ativos, adicione a etapa de marca d&#39;água no fluxo de trabalho [!UICONTROL Atualizar ativo do DAM].

1. Acesse a [!DNL Experience Manager] interface do usuário e vá para **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.
1. Na página Modelos de fluxo de trabalho, selecione o fluxo de trabalho **[!UICONTROL DAM Update Asset]** e clique em **[!UICONTROL Editar]**.

1. No painel lateral, arraste a etapa **[!UICONTROL Adicionar marca d&#39;água]** e adicione-a ao fluxo de trabalho [!UICONTROL Atualizar ativo do DAM].

   ![Arraste a etapa Adicionar marca d&#39;água no fluxo de trabalho de ativos de atualização do DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque a etapa [!UICONTROL Adicionar marca d&#39;água] em qualquer lugar antes da etapa [!UICONTROL Processar miniatura].

1. Abra a etapa **[!UICONTROL Adicionar marca d&#39;água]** para exibir suas propriedades.
1. Na guia **[!UICONTROL Argumentos]**, especifique valores válidos nos vários campos, incluindo texto, tipo de fonte, tamanho, cor, posição, orientação e assim por diante. Para confirmar as alterações, clique em **[!UICONTROL Concluído]**.

   ![Forneça os argumentos na etapa adicionar marca d&#39;água em Ativos](assets/arguments_add_watermark_aem_assets.png)

1. Salve o fluxo de trabalho do **[!UICONTROL Ativo de atualização do DAM]** com a etapa Marca d&#39;água.
1. Na interface do usuário AEM, carregue um ativo de amostra. A marca d&#39;água é exibida com o tamanho da fonte, a cor e assim por diante, na posição configurada nas etapas acima.

Para marcar documentos PDF de forma programática ou com informações dinâmicas, considere usar a oferta [AEM Documento Services](/help/forms/using/overview-aem-document-services.md).

## Dicas e limitações {#tips-limitations}

* Somente marcas d&#39;água baseadas em texto são suportadas. As imagens não são usadas como marcas d&#39;água, mesmo que você possa fazer upload de imagens ao criar o [!UICONTROL Adicionar processo de marca d&#39;água].
* Somente arquivos PNG e JPEG têm suporte para marca d&#39;água. Outros formatos de ativos não têm marca d&#39;água.
