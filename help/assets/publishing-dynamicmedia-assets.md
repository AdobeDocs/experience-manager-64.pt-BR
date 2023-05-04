---
title: Publicação de ativos Dynamic Media
description: Como publicar ativos do Dynamic Media, incluindo a entrega HTTP/2 desses ativos.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 9%

---

# Publicação de ativos Dynamic Media {#publishing-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Publique seus ativos do Dynamic Media selecionando os ativos e tocando neles **[!UICONTROL Publicar]**. Depois que os ativos de mídia dinâmica forem publicados, eles estarão disponíveis para inclusão em uma página da Web via URL ou por meio da incorporação.

Você também pode publicar instantaneamente os ativos que você faz upload, sem nenhuma intervenção do usuário. Consulte [Configuração do Dynamic Media - Modo Scene7](config-dms7.md).

Na **[!UICONTROL Exibição de cartão]**, um pequeno ícone de globo aparece logo abaixo do nome de um ativo para indicar que ele foi publicado. Na **[!UICONTROL Exibição em lista]**, uma coluna **[!UICONTROL Publicado]** indica quais ativos foram publicados ou não.

>[!NOTE]
>
>Se um ativo já estiver publicado, você usa AEM para movê-lo para outra pasta e publicar novamente de seu novo local, o local do ativo publicado original ainda estará disponível, juntamente com o ativo recém-republicado. O ativo publicado original, no entanto, é &quot;perdido&quot; para AEM e não pode ser desfeito. Portanto, como prática recomendada, cancele a publicação de ativos primeiro antes de movê-los para uma pasta diferente.

Se você pretende publicar ativos de vídeo imediatamente após codificá-los, verifique se a codificação está totalmente concluída. Quando os vídeos ainda estão sendo codificados, o sistema informa que um fluxo de trabalho de processamento de vídeo está em andamento. Quando a codificação de vídeo estiver concluída, você poderá visualizar as representações de vídeo. Nesse momento, é seguro publicar os vídeos sem incorrer em erros de publicação.

Consulte também [Vincular URLs ao seu aplicativo web](linking-urls-to-yourwebapplication.md).

Consulte também [Incorporação do visualizador de vídeo em uma página da Web.](embed-code.md)

>[!NOTE]
>
>* Os ativos devem ser publicados para usar o URL. Se os ativos não forem publicados, copiar e colar o URL em um navegador da Web não funcionará.
>* As predefinições de imagens e as predefinições do visualizador devem ser ativadas e publicadas para entrega ao vivo.
>


Para obter informações detalhadas sobre a publicação de um conjunto ou ativo, consulte [Publicar ativos.](managing-assets-touch-ui.md)

## Entrega HTTP/2 de ativos do Dynamic Media {#http-delivery-of-dynamic-media-assets}

O AEM agora é compatível com a entrega de todo o conteúdo do Dynamic Media (imagens e vídeo) por HTTP/2. Ou seja, um URL publicado ou código incorporado para a imagem ou vídeo está disponível para ser integrado a qualquer aplicativo que aceite um ativo hospedado. Esse ativo publicado é então entregue por meio do protocolo HTTP/2. Esse método de entrega melhora a maneira como os navegadores e servidores se comunicam, permitindo uma melhor resposta e tempos de carregamento de todos os seus ativos do Dynamic Media.

Consulte [Perguntas frequentes sobre entrega de conteúdo HTTP/2](/help/sites-administering/scene7-http2faq.md) para saber mais.
