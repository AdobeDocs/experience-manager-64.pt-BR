---
title: Trabalhar com conjuntos de formulários na área de trabalho do AEM Forms
seo-title: Trabalhar com conjuntos de formulários na área de trabalho do AEM Forms
description: Um conjunto de formulários é uma coleção de formulários HTML5 agrupados e apresentados como um único conjunto de formulários para os usuários finais. Saiba como trabalhar com conjuntos de formulários na área de trabalho do AEM Forms.
seo-description: Um conjunto de formulários é uma coleção de formulários HTML5 agrupados e apresentados como um único conjunto de formulários para os usuários finais. Saiba como trabalhar com conjuntos de formulários na área de trabalho do AEM Forms.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---


# Trabalhar com conjuntos de formulários na área de trabalho do AEM Forms {#working-with-formsets-in-aem-forms-workspace}

Um conjunto de formulários é uma coleção de formulários HTML5 agrupados e apresentados como um único conjunto de formulários para os usuários finais. Quando os usuários finais start para preencher um conjunto de formulários, eles são perfeitamente transitados de um formulário para outro. O conjunto de formulários pode ser submetido com apenas um clique. Para obter mais informações sobre conjuntos de formulários e como configurá-los, consulte [Formset no AEM Forms](/help/forms/using/formset-in-aem-forms.md).

A área de trabalho do AEM Forms suporta conjuntos de formulários. Com conjuntos de formulários, vários formulários relacionados a um serviço ou processo podem ser agrupados para automatizar um processo de negócios e apresentados aos usuários finais. Nesse cenário, os usuários podem preencher o conjunto inteiro como um único e não há necessidade de arquivar, enviar e rastrear formulários ou processos individuais.

## Anexar um conjunto de formulários ao ponto de partida em um aplicativo de área de trabalho AEM Forms {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Crie o fluxo de trabalho do processo de negócios no Workbench. Para obter mais informações, consulte a ajuda [do](https://www.adobe.com/go/learn_aemforms_workbench_63)Workbench.
1. Nas propriedades do processo do ponto de partida, selecione **Usar um ativo** CRX em Apresentação e dados.

   ![1-1](assets/1-1.png)

1. Clique em ![Procurar](assets/browse.png) (Procurar) ao lado do caminho do ativo CRX. A caixa de diálogo Selecionar ativo de formulário é exibida.

   ![2](assets/2.png)

1. Clique na guia **Formset** , selecione o conjunto de formulários relevante na lista e clique em **OK**.

1. Implante o aplicativo depois de atualizar outras propriedades relevantes do processo.

## Uso de formset na área de trabalho do AEM Forms {#using-formset-in-nbsp-aem-forms-workspace}

Quando um formset é anexado a um ponto de partida, o ponto de partida pode ser chamado, como qualquer outro ponto de partida é chamado, a partir da área de trabalho do AEM Forms.

As operações com suporte em formset pela área de trabalho do AEM Forms são:

* Salvar como rascunho
* Bloquear
* Desistir
* Enviar
* Adicionar anexos
* Adicionar notas
* Mover entre formulários em um conjunto de formulários usando os botões Voltar ou Próximo

![3-1](assets/3-1.png)

>[!NOTE]
>
>Para melhorar o desempenho durante a movimentação dos formulários anteriores e seguintes em um conjunto de formulários, todos os botões da área de trabalho (Voltar, Avançar, Salvar, Enviar e ... (Mais) são desativados até que o formulário relevante seja renderizado totalmente.

