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
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Gerenciamento de ativos
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 25%

---

# Entrega de ativos de Mídia dinâmica {#delivering-dynamic-media-assets}

A maneira de fornecer ativos de mídia dinâmica (vídeo e imagens) depende de como o site está implementado.

Com a Mídia dinâmica, você tem várias opções:

* Se o seu site estiver hospedado no AEM, convém adicionar os ativos de mídia dinâmica diretamente à sua página.
* Se o seu site não estiver no AEM, você terá a opção de:

   * Incorporação do vídeo ou imagem ao seu site.
   * Vincule URLs ao aplicativo da Web. Use a vinculação quando desejar fornecer um reprodutor de vídeo como uma janela pop-up ou modal.
   * Se seu site for responsivo, você poderá [fornecer imagens otimizadas.](responsive-site.md)

>[!NOTE]
>
>A geração de imagens inteligentes funciona com as predefinições de imagens existentes e usa inteligência nos últimos milissegundos do delivery para reduzir ainda mais o tamanho do arquivo de imagem com base na velocidade do navegador ou da conexão de rede. Consulte [Imagem inteligente](imaging-faq.md) para obter mais informações.

Para obter mais informações, consulte os seguintes tópicos:

* [Adicionar ativos Dynamic Media às páginas da Web](adding-dynamic-media-assets-to-pages.md)
* [Incorporação do visualizador de vídeo ou imagem em uma página da Web](embed-code.md)
* [Ativação da proteção de hotlink no Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-64/assets/dynamic/hotlink-protection.html?lang=pt-BR#dynamic)
* Integração de marcas d&#39;água digitais invisíveis (Digimarc) com o Dynamic Media (em breve)
* [Vincular URLs ao aplicativo da Web.](linking-urls-to-yourwebapplication.md)
* [Entrega de imagens otimizadas para um site responsivo](responsive-site.md)
* [Entrega de conteúdo HTTP2](http2.md)
* [Invalidação do conteúdo em cache do CDN](invalidate-cdn-cached-content.md)
* [Uso de conjuntos de regras para transformar URLs](using-rulesets-to-transform-urls.md)

## Entrega HTTP/2 de ativos do Dynamic Media {#http-delivery-of-dynamic-media-assets}

O AEM agora é compatível com a entrega de todo o conteúdo do Dynamic Media (imagens e vídeo) por HTTP/2. Ou seja, um URL publicado ou código incorporado para a imagem ou vídeo está disponível para ser integrado a qualquer aplicativo que aceite um ativo hospedado. Esse ativo publicado é então entregue por meio do protocolo HTTP/2. Esse método de entrega melhora a maneira como os navegadores e servidores se comunicam, permitindo uma melhor resposta e tempos de carregamento de todos os seus ativos do Dynamic Media.

Consulte [Perguntas frequentes sobre entrega de conteúdo HTTP/2](/help/sites-administering/scene7-http2faq.md) para saber mais.
