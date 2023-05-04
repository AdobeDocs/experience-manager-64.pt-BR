---
title: Trabalho com seletores
seo-title: Working with Selectors
description: Selecionar ativos para imagens interativas, vídeo interativo e banners de carrossel
seo-description: Selecting assets for interactive images, interactive video, and carousel banners
uuid: 6231739c-bf49-4069-90a4-57848cc68d9a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 262eb911-3dcb-475d-b410-8bcac1347905
exl-id: 6bd68afe-bd54-4482-bd6e-cb318868c8d0
feature: Selectors
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 19%

---

# Trabalho com seletores {#working-with-selectors}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao trabalhar com uma Imagem interativa, Vídeo interativo ou Banner de carrossel, você seleciona ativos e seleciona sites e produtos para pontos de acesso e mapas de imagem para os quais vincular. Ao trabalhar com Conjuntos de imagens, Conjuntos de rotação e Conjuntos de multimídia, você também seleciona ativos com o Seletor de ativo.

Este tópico aborda como usar os seletores Produto, Site e Ativo, incluindo a capacidade de navegar, filtrar e classificar dentro dos seletores.

Você acessa os seletores ao criar conjuntos de carrossel, adicionar pontos de acesso e mapas de imagem, criar vídeos e imagens interativas.

Por exemplo, neste Banner de carrossel, você usa o seletor de produto se estiver vinculando um ponto de acesso ou mapa de imagem a uma página do Quickview; use o seletor de site se estiver vinculando um ponto de acesso ou mapa de imagem a um hiperlink; use o seletor de Ativos ao criar um novo slide.

![chlimage_1-520](assets/chlimage_1-520.png)

Ao selecionar (em vez de inserir manualmente) para onde os pontos de acesso ou mapas de imagem são direcionados, você está usando o seletor. O seletor de site só funcionará se você for um cliente do AEM Sites. O seletor de produto também requer AEM Commerce.

## Seleção de produtos {#selecting-products}

Use o seletor de produto para escolher um produto quando quiser um ponto de acesso ou mapa de imagem para fornecer uma exibição rápida a um produto específico em seu catálogo de produtos.

1. Navegue até o Conjunto de carrosséis, Imagem interativa ou Vídeo interativo e toque na guia **[!UICONTROL Ações]** (disponível somente se tiver definido um ponto de acesso ou mapa de imagem).

   O seletor de Produto está no **[!UICONTROL Tipo de ação]** área.

   ![chlimage_1-521](assets/chlimage_1-521.png)

1. Toque no **[!UICONTROL Seletor de produto]** ícone (lupa) e navegue até um produto no catálogo.

   ![chlimage_1-522](assets/chlimage_1-522.png)

   Também é possível filtrar por palavra-chave ou tag ao tocar em **[!UICONTROL Filtro]** e inserir palavras-chave, ou selecionar tags, ou ambos.

   ![chlimage_1-523](assets/chlimage_1-523.png)

   Você pode alterar o local em que AEM procura dados do produto ao tocar em **[!UICONTROL Procurar]** e navegar para outra pasta.

   ![chlimage_1-524](assets/chlimage_1-524.png)

   Toque **[!UICONTROL Classificar]** para alterar se o AEM classifica do mais novo para o mais antigo ou do mais antigo para o mais recente.

   ![chlimage_1-525](assets/chlimage_1-525.png)

   Toque em **[!UICONTROL Visualizar como]** para alterar a exibição de produtos - **[!UICONTROL Exibição em lista]** ou **[!UICONTROL Exibição de cartão]**.

   ![chlimage_1-526](assets/chlimage_1-526.png)

1. Após a seleção do produto, o campo é preenchido com a miniatura e o nome do produto.

   ![chlimage_1-527](assets/chlimage_1-527.png)

1. Quando em **[!UICONTROL Visualizar]** , você pode tocar no ponto de acesso ou mapa de imagem e ver a aparência do Quickview.

   ![chlimage_1-528](assets/chlimage_1-528.png)

## Seleção de sites {#selecting-sites}

Use o seletor de site para escolher uma página da Web quando quiser um ponto de acesso ou mapa de imagem para vincular a uma página da Web que seja gerenciada em AEM sites.

1. Navegue até o Conjunto de carrosséis, Imagem interativa ou Vídeo interativo e toque na guia **[!UICONTROL Ações]** (disponível somente se tiver definido um ponto de acesso ou mapa de imagem).

   O Seletor de site está na área **[!UICONTROL Tipo de ação]**.

   ![chlimage_1-529](assets/chlimage_1-529.png)

1. Toque no ícone do **[!UICONTROL Seletor de sites]** (pasta com lupa) e navegue até uma página no AEM Sites a qual você deseja vincular o ponto de acesso ou mapa de imagem.

   ![chlimage_1-530](assets/chlimage_1-530.png)

1. Após a seleção do site, o campo é preenchido com o caminho.

   ![chlimage_1-531](assets/chlimage_1-531.png)

1. Quando em **[!UICONTROL Visualizar]** modo , se você tocar no ponto de acesso ou mapa de imagem, navegará até a página do site AEM que você especificou.

## Seleção de ativos {#selecting-assets}

Use este seletor para escolher imagens para usar em um Banner de carrossel, um Vídeo interativo, conjuntos de imagens, conjuntos de mídia mista e conjuntos de rotação. Em Vídeo interativo, o seletor de ativos fica disponível ao tocar em **[!UICONTROL Selecionar ativos]** no **[!UICONTROL Conteúdo]** guia . Em Conjuntos de carrossel, o seletor de ativos fica disponível ao criar um novo slide. Em Conjuntos de imagens, Conjuntos de mídias mistas e Conjuntos de rotação, o seletor de ativo estará disponível ao criar um novo Conjunto de imagens, Conjunto de mídias mistas ou Conjunto de rotação, respectivamente.

Consulte também [Seletor de ativos](asset-selector.md) para obter mais informações.

1. Navegue até o Conjunto de carrossel e crie um novo slide. Ou navegue até o Vídeo interativo, vá para **[!UICONTROL Conteúdo]** e selecione ativos. Ou crie um Conjunto de mídias mistas, um Conjunto de imagens ou um Conjunto de rotação.
1. Toque no ícone **[!UICONTROL Seletor de ativos]** (pasta com uma lupa) e navegue até um ativo.

   ![chlimage_1-532](assets/chlimage_1-532.png)

   Também é possível filtrar por palavra-chave ou tag ao tocar em **[!UICONTROL Filtro]** e inserir palavras-chave, adicionar critérios ou ambos.

   ![chlimage_1-533](assets/chlimage_1-533.png)

   Você pode alterar o local em que o AEM procura por ativos navegando até outra pasta no **[!UICONTROL Caminho]** campo.

   Toque **[!UICONTROL Coleção]** para pesquisar apenas ativos nas coleções.

   ![chlimage_1-534](assets/chlimage_1-534.png)

   Toque em **[!UICONTROL Visualizar como]** para alterar a exibição de produtos - **[!UICONTROL Exibição em lista]**, **[!UICONTROL Exibição em coluna]** ou **[!UICONTROL Exibição de cartão]**.

   ![chlimage_1-535](assets/chlimage_1-535.png)

1. Toque na marca de seleção para selecionar o ativo. O ativo é exibido.

   ![chlimage_1-536](assets/chlimage_1-536.png)
