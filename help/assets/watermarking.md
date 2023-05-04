---
title: Adicionar marca d'água aos ativos digitais
description: Saiba como usar o recurso Marca d'água para adicionar uma marca d'água digital aos ativos.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# Marque com água seus ativos digitais {#watermarking}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] O permite adicionar uma marca d&#39;água digital aos ativos, o que ajuda os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. [!DNL Experience Manager Assets] suporta texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

O Adobe Experience Manager Assets permite adicionar uma marca d&#39;água digital a imagens que ajuda os usuários a verificar a autenticidade e a propriedade de direitos autorais dos ativos. [!DNL Experience Manager] Os ativos oferecem suporte para o texto a ser usado como marca d&#39;água em arquivos PNG e JPEG.

Para poder aplicar marca d&#39;água em ativos, adicione a etapa marca d&#39;água no [!UICONTROL Ativo de atualização DAM] fluxo de trabalho.

1. Acesse o [!DNL Experience Manager] interface do usuário e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.
1. Na página Modelos de fluxo de trabalho , selecione o **[!UICONTROL Ativo de atualização DAM]** e clique em **[!UICONTROL Editar]**.

1. No painel lateral, arraste o **[!UICONTROL Adicionar marca d&#39;água]** e adicione-o ao [!UICONTROL Ativo de atualização DAM] fluxo de trabalho.

   ![Arraste a etapa adicionar marca d&#39;água no fluxo de trabalho do ativo de atualização do DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Coloque o [!UICONTROL Adicionar marca d&#39;água] etapa em qualquer lugar antes da [!UICONTROL Miniatura do processo] etapa.

1. Abra o **[!UICONTROL Adicionar marca d&#39;água]** para exibir suas propriedades.
1. No **[!UICONTROL Argumentos]** , especifique valores válidos nos vários campos, incluindo texto, tipo de fonte, tamanho, cor, posição, orientação e assim por diante. Para confirmar as alterações, clique em **[!UICONTROL Concluído]**.

   ![Forneça os argumentos na etapa adicionar marca d&#39;água no Assets](assets/arguments_add_watermark_aem_assets.png)

1. Salve o fluxo de trabalho do **[!UICONTROL Ativo de atualização do DAM]** com a etapa Marca d&#39;água.
1. No [!DNL Experience Manager] interface do usuário, faça upload de um ativo de amostra. A marca d&#39;água aparece com o tamanho da fonte, cor e assim por diante, na posição configurada nas etapas acima.

Para fazer uma marca d&#39;água em documentos PDF de forma programática ou com informações dinâmicas, considere usar [[!DNL Experience Manager] Serviços de documento](/help/forms/using/overview-aem-document-services.md) oferta.

## Dicas e limitações {#tips-limitations}

* Somente marcas d&#39;água baseadas em texto são suportadas. As imagens não são usadas como marcas d&#39;água, mesmo que você possa fazer upload de imagens ao criar o [!UICONTROL Adicionar processo de marca d&#39;água].
* Somente os arquivos PNG e JPEG têm suporte para marca d&#39;água. Outros formatos de ativos não são marcados com marca d&#39;água.
