---
title: Incorporação do visualizador de vídeo ou imagem do Dynamic Media em uma página da Web
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: Saiba como incorporar vídeos ou imagens do Dynamic Media em uma página da Web
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 21%

---

# Incorporação do visualizador de vídeo ou imagem do Dynamic Media em uma página da Web {#embedding-the-video-or-image-viewer-on-a-web-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Use o recurso **[!UICONTROL Incorporar código]** quando quiser reproduzir o vídeo ou exibir um ativo incorporado em uma página da Web. Copie o código incorporado na área de transferência para poder colá-lo nuas páginas da Web. A edição do código não é permitida na caixa de diálogo **[!UICONTROL Incorporar código]**.

Você incorporar URLs somente se estiver _not_ usar [!DNL Experience Manager] como seu WCM. Se estiver usando [!DNL Experience Manager] como o WCM, [você adiciona os ativos diretamente na página.](adding-dynamic-media-assets-to-pages.md)

Consulte [Vincular URLs ao aplicativo da Web.](linking-urls-to-yourwebapplication.md)

Consulte [Fornecer imagens otimizadas para um site responsivo.](responsive-site.md)

>[!NOTE]
>
>O código incorporado não está disponível para cópia até que você tenha publicado o ativo selecionado. Além disso, você também deve publicar a predefinição do visualizador ou a predefinição de imagem.
>
>Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
>
>Consulte [Predefinições do visualizador de publicação](managing-viewer-presets.md#publishing-viewer-presets).
>
>Consulte [Publicar predefinições da imagem](managing-image-presets.md#publishing-image-presets).

**Para incorporar o visualizador de vídeo ou imagem do Dynamic Media em uma página da Web**:

1. Navegue até o *publicado* vídeo ou ativo de imagem cujo código incorporado você deseja copiar.

   Lembre-se de que o código incorporado só está disponível para cópia *depois* que você *publicou* os ativos pela primeira vez. Além disso, a predefinição do visualizador ou da imagem também deve ser publicada.

   Consulte [Publicar ativos.](publishing-dynamicmedia-assets.md)

   Consulte [Predefinições do visualizador de publicação](managing-viewer-presets.md#publishing-viewer-presets).

   Consulte [Publicar predefinições da imagem](managing-image-presets.md#publishing-image-presets).

1. No painel à esquerda, selecione o menu suspenso e toque em **[!UICONTROL Visualizadores]**.
1. No painel à esquerda, toque em um nome de predefinição do visualizador. A predefinição do visualizador é aplicada ao ativo.
1. Toque **[!UICONTROL Incorporar]**.
1. No **[!UICONTROL Código incorporado]** , copie o código inteiro para a área de transferência e toque em **[!UICONTROL Fechar]**.
1. Cole o código incorporado nas páginas da Web.

## Usar HTTP/2 para fornecer ativos da Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 é o novo protocolo da Web atualizado que melhora a maneira como os navegadores e servidores se comunicam. Ele oferece transferência mais rápida de informações e reduz a quantidade de poder de processamento necessário. A entrega de ativos do Dynamic Media agora pode ser feita via HTTP/2, o que oferece melhor resposta e tempo de carregamento.

Consulte [Entrega de conteúdo HTTP2](http2.md) para obter detalhes completos sobre a introdução ao HTTP/2 com sua conta do Dynamic Media.
