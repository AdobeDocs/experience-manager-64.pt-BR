---
title: Fornecer imagens otimizadas para um site responsivo
description: Como usar o recurso Código responsivo no Dynamic Media para fornecer imagens otimizadas
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
exl-id: 36bb526c-a6d9-4296-8318-97ac72d6b3ba
feature: Publishing
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 12%

---

# Entrega de imagens otimizadas para um site responsivo {#delivering-optimized-images-for-a-responsive-site}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Use o recurso de código responsivo quando quiser compartilhar o código para serviço responsivo com seu desenvolvedor da Web. Você copia a variável responsiva (**[!UICONTROL RESS]**) à área de transferência para compartilhá-la com o desenvolvedor da Web.

Esse recurso faz sentido usar se o site estiver em um WCM de terceiros. No entanto, se seu site estiver em AEM, um servidor de imagem externo renderiza a imagem e a fornece à página da Web.

Consulte também [Incorporação do visualizador de vídeo em uma página da Web.](embed-code.md)

Consulte também [Vincular URLs ao aplicativo da Web.](linking-urls-to-yourwebapplication.md)

**Fornecer imagens otimizadas para um site responsivo**:

1. Navegue até a imagem para a qual deseja fornecer o código responsivo e, no menu suspenso, toque em **[!UICONTROL Representações]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Selecione uma predefinição de imagem responsiva. Os botões **[!UICONTROL URL]** e **[!UICONTROL RESS]** são exibidos.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >O ativo selecionado *e* a predefinição de imagem ou a predefinição do visualizador selecionado devem ser publicados para disponibilizar os botões **[!UICONTROL URL]** ou **[!UICONTROL RESS]**.
   >
   >Dynamic Media - O modo híbrido requer a publicação de predefinições de imagens; Dynamic Media - O modo Scene7 publica automaticamente predefinições de imagens.

1. Toque **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. No **[!UICONTROL Incorporar imagem responsiva]** , selecione e copie o texto do código responsivo e o cole no site para acessar o ativo responsivo.
1. Edite os pontos de interrupção padrão no código incorporado para corresponder aos do site responsivo diretamente no código. Além disso, teste as diferentes resoluções de imagem que estão sendo veiculadas em diferentes pontos de interrupção da página.

## Usar HTTP/2 para fornecer ativos da Dynamic Media {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 é o novo protocolo da Web atualizado que melhora a maneira como os navegadores e servidores se comunicam. Ele oferece transferência mais rápida de informações e reduz a quantidade de poder de processamento necessário. A entrega de ativos do Dynamic Media é compatível com o uso do HTTP/2, o que oferece melhor resposta e tempos de carregamento.

Consulte [Entrega de conteúdo HTTP2](http2.md) para obter detalhes completos sobre a introdução ao HTTP/2 com sua conta do Dynamic Media.
