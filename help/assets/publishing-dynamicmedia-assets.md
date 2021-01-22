---
title: Publicação de ativos Dynamic Media
description: Como publicar ativos da Dynamic Media, incluindo o delivery HTTP/2 desses ativos.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 8%

---


# Publicar ativos Dynamic Media {#publishing-dynamic-media-assets}

Você publica seus ativos do Dynamic Media selecionando os ativos e tocando em **[!UICONTROL Publicar]**. Depois que seus ativos de mídia dinâmica forem publicados, eles estarão disponíveis para você para inclusão em uma página da Web via URL ou por meio da incorporação.

Você também pode publicar instantaneamente ativos que você carrega, sem nenhuma intervenção do usuário. Consulte [Configuração do Dynamic Media - modo Scene7](config-dms7.md).

Na **[!UICONTROL Exibição de cartão]**, um pequeno ícone de globo aparece logo abaixo do nome de um ativo para indicar que ele foi publicado. Na **[!UICONTROL Exibição em lista]**, uma coluna **[!UICONTROL Publicado]** indica quais ativos foram publicados ou não.

>[!NOTE]
>
>Se um ativo já estiver publicado, você usará AEM para mover o ativo para outra pasta e republicar de seu novo local, o local original do ativo publicado ainda estará disponível, juntamente com o ativo recém-publicado. O ativo publicado original, no entanto, é &quot;perdido&quot; para AEM e não pode ser despublicado. Portanto, como prática recomendada, cancele a publicação de ativos primeiro antes de movê-los para uma pasta diferente.

Se você pretende publicar ativos de vídeo imediatamente após a codificação, certifique-se de que a codificação esteja concluída. Quando os vídeos ainda estão sendo codificados, o sistema permite que você saiba que um fluxo de trabalho de processamento de vídeo está em andamento. Quando a codificação de vídeo estiver concluída, você poderá pré-visualização as execuções de vídeo. Nesse ponto, é seguro publicar os vídeos sem incorrer em erros de publicação.

Consulte também [Vincular URLs à sua Aplicação web](linking-urls-to-yourwebapplication.md).

Consulte também [Incorporar o Visualizador de Vídeo em uma Página da Web.](embed-code.md)

>[!NOTE]
>
>* Os ativos devem ser publicados para usar o URL. Se os ativos não forem publicados, copiar e colar o URL em um navegador da Web não funcionará.
>* As predefinições de imagens e as predefinições do visualizador devem ser ativadas e publicadas para o delivery ao vivo.

>



Para obter informações detalhadas sobre como publicar um conjunto ou ativo, consulte [Publicar ativos.](managing-assets-touch-ui.md)

## DELIVERY HTTP/2 de ativos Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM agora suporta o delivery de todo o conteúdo do Dynamic Media (imagens e vídeo) por HTTP/2. Ou seja, um URL publicado ou um código incorporado para a imagem ou o vídeo está disponível para ser integrado a qualquer aplicativo que aceite um ativo hospedado. Esse ativo publicado é então entregue por meio do protocolo HTTP/2. Este método de delivery melhora a maneira como os navegadores e servidores se comunicam, permitindo uma melhor resposta e tempos de carregamento de todos os seus ativos Dynamic Media.

Consulte [delivery HTTP/2 de conteúdo com perguntas frequentes](/help/sites-administering/scene7-http2faq.md) para saber mais.
