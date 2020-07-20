---
title: Marque com água suas imagens
description: Use o recurso de marca d'água para adicionar uma marca d'água digital às imagens PNG E JPEG.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 04de28347ddf0082d2e224aa3853297cad3aacd8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---


# Marque com água seus ativos {#watermarking}

Os ativos Adobe Experience Manager (AEM) permitem que você adicione uma marca d&#39;água digital a imagens que ajudam os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. O AEM Assets oferece suporte ao texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

Para poder aplicar uma marca d&#39;água em ativos, adicione a etapa [!UICONTROL Marca d&#39;água] no fluxo de trabalho Atualizar ativo [!UICONTROL do] DAM.

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Na página Modelos de fluxo de trabalho, selecione o fluxo de trabalho **[!UICONTROL Atualizar ativo]** DAM e clique em **[!UICONTROL Editar]**.

1. No painel lateral, arraste a etapa **[!UICONTROL Adicionar marca d&#39;água]** e adicione-a ao fluxo de trabalho Atualizar ativo [!UICONTROL do] DAM.

   ![Desenhe a etapa Adicionar marca d&#39;água no fluxo de trabalho do ativo de atualização do DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque a etapa [!UICONTROL Adicionar marca d&#39;água] em qualquer lugar antes da etapa [!UICONTROL Processar miniatura] .

1. Abra a etapa **[!UICONTROL Adicionar marca d&#39;água]** para exibir suas propriedades.
1. Na guia **[!UICONTROL Argumentos]** , especifique valores válidos nos vários campos, incluindo texto, tipo de fonte, tamanho, cor, posição, orientação e assim por diante. Para confirmar as alterações, toque/clique no ícone Concluído.

   ![Forneça os argumentos na etapa adicionar marca d&#39;água em Ativos](assets/arguments_add_watermark_aem_assets.png)

1. Salve o fluxo de trabalho do **[!UICONTROL Ativo de atualização do DAM]** com a etapa Marca d&#39;água.
1. Na interface do usuário do AEM, carregue um ativo de amostra. A marca d&#39;água é exibida com o tamanho da fonte, a cor e assim por diante, na posição configurada nas etapas acima.

Para marcar documentos PDF de forma programada ou com informações dinâmicas, considere usar a oferta de serviços [de Documento](/help/forms/using/overview-aem-document-services.md) AEM.
