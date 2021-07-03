---
title: Adicionar marca d'água aos ativos digitais
description: Saiba como usar o recurso Marca d'água para adicionar uma marca d'água digital aos ativos.
contentOwner: AG
feature: Gerenciamento de ativos
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# Marque com água seus ativos digitais {#watermarking}

[!DNL Adobe Experience Manager Assets] O permite adicionar uma marca d&#39;água digital aos ativos, o que ajuda os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. [!DNL Experience Manager Assets] suporta texto a ser usado como uma marca d&#39;água em arquivos PNG e JPEG.

Os ativos Adobe Experience Manager (AEM) permitem adicionar uma marca d&#39;água digital a imagens que ajudam os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. O AEM Assets suporta texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

Para poder aplicar marca d&#39;água em ativos, adicione a etapa marca d&#39;água no fluxo de trabalho [!UICONTROL Ativo de atualização do DAM] .

1. Acesse a interface do usuário [!DNL Experience Manager] e vá para **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.
1. Na página Modelos de fluxo de trabalho , selecione o fluxo de trabalho **[!UICONTROL Ativo de atualização do DAM]** e clique em **[!UICONTROL Editar]**.

1. No painel lateral, arraste a etapa **[!UICONTROL Adicionar marca d&#39;água]** e adicione-a ao workflow [!UICONTROL Ativo de atualização do DAM].

   ![Arraste a etapa adicionar marca d&#39;água no fluxo de trabalho do ativo de atualização do DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque a etapa [!UICONTROL Adicionar marca d&#39;água] em qualquer lugar antes da etapa [!UICONTROL Processar miniatura].

1. Abra a etapa **[!UICONTROL Adicionar marca d&#39;água]** para exibir suas propriedades.
1. Na guia **[!UICONTROL Argumentos]**, especifique valores válidos nos vários campos, incluindo texto, tipo de fonte, tamanho, cor, posição, orientação e assim por diante. Para confirmar as alterações, clique em **[!UICONTROL Concluído]**.

   ![Forneça os argumentos na etapa adicionar marca d&#39;água no Assets](assets/arguments_add_watermark_aem_assets.png)

1. Salve o fluxo de trabalho do **[!UICONTROL Ativo de atualização do DAM]** com a etapa Marca d&#39;água.
1. Na interface do usuário do AEM, faça upload de um ativo de amostra. A marca d&#39;água aparece com o tamanho da fonte, cor e assim por diante, na posição configurada nas etapas acima.

Para marcar documentos PDF de forma programática ou com informações dinâmicas, considere usar a oferta [AEM Document Services](/help/forms/using/overview-aem-document-services.md).

## Dicas e limitações {#tips-limitations}

* Somente marcas d&#39;água baseadas em texto são suportadas. As imagens não são usadas como marcas d&#39;água, mesmo que você possa fazer upload de imagens ao criar o [!UICONTROL Adicionar processo de marca d&#39;água].
* Somente os arquivos PNG e JPEG têm suporte para marca d&#39;água. Outros formatos de ativos não são marcados com marca d&#39;água.
