---
title: Aprimoramentos na experiência do usuário em ativos
description: Este artigo descreve as melhorias na experiência do usuário no AEM 6.4 Assets.
contentOwner: AG
feature: Release Information
role: Leader,Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 1%

---


# Melhorias na experiência do usuário no Assets {#user-experience-enhancements-in-assets}

O AEM 6.4 Assets inclui várias melhorias de usabilidade que proporcionam uma experiência contínua do usuário e melhora a produtividade. O aumento na velocidade com que você pode criar/gerenciar seu conteúdo do mercado melhora a velocidade do conteúdo da empresa.

A interface é mais ágil, o que ajuda a gerenciar com eficiência um grande portfólio de ativos. Você pode pesquisar, exibir, classificar e rolar rapidamente por uma longa lista de itens.

É possível personalizar as várias exibições - Cartão, Lista e Coluna. Por exemplo, você pode configurar o tamanho das miniaturas que deseja exibir na exibição de Cartão. Para a exibição em Lista, é possível configurar o nível de detalhes que deseja exibir para os ativos na lista. O AEM 6.4 Assets inclui uma nova visualização em árvore que permite navegar convenientemente pelo repositório de Ativos e localizar seus ativos.

## Carregamento lento {#lazy-loading}

Quando você navega/pesquisa por ativos no AEM 6.4 Assets, até 200 ativos são exibidos de cada vez. Você pode rolar os resultados mais rapidamente, o que é especialmente útil ao navegar por uma longa lista de resultados. Como um número significativo de ativos é carregado de cada vez, a experiência de navegação é tranquila.

Se você tocar/clicar em um ativo para revisar sua página de detalhes, é possível retornar à página de resultados simplesmente tocando/clicando no botão Voltar na barra de ferramentas.

## Aprimoramentos na exibição de cartão {#card-view-improvements}

Dependendo do dispositivo usado e da quantidade de detalhes necessários, é possível redimensionar as miniaturas de ativos na exibição de Cartão. Dessa forma, você pode personalizar sua visualização e controlar o número de miniaturas exibidas.

Para redimensionar miniaturas na exibição de Cartão, execute estas etapas:

1. Toque/clique no ícone Layout na barra de ferramentas e escolha a opção **[!UICONTROL Configurações de exibição]**.

   ![view_settings](assets/view_settings.png)

1. Na caixa de diálogo **[!UICONTROL Exibir configurações]**, selecione o tamanho da miniatura desejado e toque/clique em **[!UICONTROL Atualizar]**.

   ![view_settings_dialog](assets/view_settings_dialog.png)

1. Revise as miniaturas exibidas no tamanho escolhido.

   ![thumbnails_changed](assets/thumbnails_changed.png)

O bloco na exibição Cartão agora exibe informações adicionais, como status da publicação.

![publish_status](assets/publish_status.png)

## Melhorias na exibição de lista {#list-view-improvements}

Na exibição de Lista, a primeira coluna agora exibe os nomes de arquivo dos ativos por padrão. Informações adicionais, como status de publicação e processamento e local, também são exibidas.

![list_view](assets/list_view.png)

Você pode optar por configurar a quantidade de detalhes que deseja exibir. Toque/clique no ícone Layout, escolha a opção **[!UICONTROL Configurações de exibição]** e especifique as colunas que deseja exibir na caixa de diálogo **[!UICONTROL Configurações de exibição]**.

![view_settings_dialog_listview](assets/view_settings_dialoglistview.png)

## Melhorias na exibição de coluna {#column-view-improvements}

Além das exibições Cartão e Lista, agora é possível navegar até a página de detalhes de um ativo na exibição Coluna. Selecione um ativo na exibição Coluna e toque/clique em **[!UICONTROL Mais detalhes]** no instantâneo do ativo.

![more_details](assets/more_details.png)

## Exibição em árvore {#tree-view}

AEM 6.4 Os ativos incluem uma visualização em árvore que permite navegar convenientemente pela hierarquia de ativos e navegar até o ativo ou a pasta desejada.

Para abrir a exibição em Árvore, toque/clique no ícone Navegação global no `Assets UI` e escolha **[!UICONTROL Árvore de conteúdo]** no menu.

![árvore_de_conteúdo](assets/content_tree.png)

Na hierarquia de conteúdo, navegue até o ativo desejado.

![navegar_contenttree](assets/navigate_contenttree.png)

## Navegar pelos detalhes do ativo {#navigating-asset-details}

A página de detalhes do ativo agora inclui os botões Anterior e Próximo na barra de ferramentas para que você possa exibir todas as imagens em uma pasta em sucessão.

Dependendo do seu dispositivo, você também pode deslizar ou usar as teclas de seta no teclado para avançar e para trás entre as imagens.

Dependendo do layout escolhido, você pode abrir a página de detalhes de um ativo das seguintes maneiras:

| **Exibir** | **Como abrir a página de detalhes do ativo** |
|---|---|
| [!UICONTROL Exibição de cartão] | Toque/clique no bloco de ativos. |
| [!UICONTROL Exibição de lista  ] | Toque/clique na entrada de linha do ativo na lista. |
| [!UICONTROL Exibição de coluna] | Toque/clique no botão **[!UICONTROL Mais detalhes]** no instantâneo do ativo. |

Use os botões Anterior/Próximo para avançar e voltar entre os ativos.

![prev_next_button](assets/prev_next_buttons.png)
