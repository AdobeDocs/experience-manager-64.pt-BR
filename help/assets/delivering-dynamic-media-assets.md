---
title: Entrega de ativos de Mídia dinâmica
seo-title: Entrega de ativos de Mídia dinâmica
description: Saiba como fornecer ativos de mídia dinâmica
seo-description: Saiba como fornecer ativos de mídia dinâmica
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4

---


# Entrega de ativos de Mídia dinâmica {#delivering-dynamic-media-assets}

A forma como você pode fornecer seus ativos de mídia dinâmica - vídeo e imagens - depende de como seu site é implementado.

Com a Mídia dinâmica, você tem várias opções:

* Se o seu site estiver hospedado no AEM, convém adicionar os ativos de mídia dinâmica diretamente à sua página.
* Se o seu site não estiver no AEM, você terá a opção de:

   * Incorporar seu vídeo ou imagem em seu site.
   * Vincule URLs ao aplicativo da Web. Use a vinculação quando quiser fornecer um player de vídeo como uma janela pop-up ou modal.
   * Se o site estiver respondendo, você poderá [fornecer imagens otimizadas.](responsive-site.md)

>[!NOTE]
>
>A geração de imagens inteligentes funciona com as predefinições de imagens existentes e usa inteligência no último milissegundo de entrega para reduzir ainda mais o tamanho do arquivo de imagem com base na velocidade do navegador ou da conexão de rede. Consulte Imagens [inteligentes](imaging-faq.md) para obter mais informações.

Para obter mais informações, consulte os seguintes tópicos:

* [Adicionar ativos de mídia dinâmica a páginas da Web](adding-dynamic-media-assets-to-pages.md)
* [Incorporação do visualizador de vídeo ou imagem em uma página da Web](embed-code.md)
* [Ativação da proteção de hotlink na mídia dinâmica](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* Integração da marca d&#39;água digital não visível (Digimarc) com o Dynamic Media (em breve)
* [Vincular URLs ao aplicativo da Web.](linking-urls-to-yourwebapplication.md)
* [Entrega de imagens otimizadas para um site responsivo](responsive-site.md)
* [Entrega de conteúdo HTTP2](http2.md)
* [Invalidação do conteúdo em cache do CDN](invalidate-cdn-cached-content.md)
* [Uso de conjuntos de regras para transformar URLs](using-rulesets-to-transform-urls.md)

## Entrega HTTP/2 de ativos do Dynamic Media {#http-delivery-of-dynamic-media-assets}

O AEM agora oferece suporte à entrega de todo o conteúdo de Dynamic Media (imagens e vídeo) por HTTP/2. Ou seja, um URL publicado ou um código incorporado para a imagem ou o vídeo está disponível para ser integrado a qualquer aplicativo que aceite um ativo hospedado. Esse ativo publicado é então entregue por meio do protocolo HTTP/2. Esse método de entrega melhora a maneira como os navegadores e servidores se comunicam, permitindo uma melhor resposta e tempos de carregamento de todos os ativos do Dynamic Media.

Consulte [HTTP/2 Entrega de Perguntas](/help/sites-administering/scene7-http2faq.md) frequentes sobre conteúdo para saber mais.
