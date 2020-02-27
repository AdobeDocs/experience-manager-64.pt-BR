---
title: Aplicar fluxos de trabalho para processar seus ativos digitais
description: Saiba como aplicar fluxos de trabalho a ativos, pastas e coleções nos ativos AEM para processar seus ativos digitais.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Aplicar fluxos de trabalho a ativos {#applying-workflows-to-assets}

Aplicar fluxos de trabalho a ativos digitais é o mesmo que aplicar a páginas do site. Para obter um guia completo sobre como criar e usar fluxos de trabalho no AEM, consulte [Iniciar fluxos de trabalho](../sites-authoring/workflows-participating.md).

Use fluxos de trabalho em ativos digitais para ativar o ativo ou criar marcas d&#39;água. Muitos dos fluxos de trabalho para ativos são ativados automaticamente. Por exemplo, o fluxo de trabalho que cria automaticamente uma representação depois que uma imagem é editada é ativado automaticamente.

Se um fluxo de trabalho disponível na interface clássica não estiver disponível na interface habilitada para toque, como Solicitar a ativação e Solicitar a desativação, consulte [Disponibilizar modelos de fluxo de trabalho na interface](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)de usuário para toque.

## Aplicar um fluxo de trabalho a um ativo AEM {#applying-a-workflow-to-an-aem-asset}

Para obter detalhes sobre como aplicar um fluxo de trabalho a um ativo AEM, consulte [Iniciar um fluxo de trabalho em um ativo](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset).

## Aplicar um fluxo de trabalho a vários ativos {#applying-a-workflow-to-multiple-assets}

1. No console Ativos, navegue até o local dos ativos para os quais deseja iniciar um fluxo de trabalho e selecione os ativos.
1. Clique no ícone GlobalNav e escolha **[!UICONTROL Linha]** do tempo no menu para exibir a linha do tempo.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. Clique em **[!UICONTROL Iniciar fluxo de trabalho]**.
1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Opcional) Especifique um título para o fluxo de trabalho, que pode ser usado para fazer referência à instância do fluxo de trabalho.
1. Clique em **[!UICONTROL Iniciar]** e em **[!UICONTROL Confirmar]** na caixa de diálogo. O fluxo de trabalho é executado em todos os ativos selecionados.

## Aplicar um fluxo de trabalho a várias pastas {#applying-a-workflow-to-multiple-folders}

O procedimento para aplicar um fluxo de trabalho a várias pastas é semelhante ao procedimento para aplicar um fluxo de trabalho a vários ativos. Selecione as pastas no console Ativos e execute as etapas de 2 a 7 do procedimento [Aplicar um fluxo de trabalho a vários ativos](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Aplicar um fluxo de trabalho a uma coleção {#applying-a-workflow-to-a-collection}

Para obter detalhes sobre como aplicar um fluxo de trabalho a uma coleção, consulte [Execução de um fluxo de trabalho em uma coleção](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).
