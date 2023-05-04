---
title: Trabalhar com conjuntos de formulários no espaço de trabalho do AEM Forms
seo-title: Working with Formsets in AEM Forms workspace
description: Um conjunto de formulários é uma coleção de formulários HTML5 agrupados e apresentados como um conjunto único de formulários para os usuários finais. Saiba como trabalhar com conjuntos de formulários no AEM Forms Workspace.
seo-description: A formset is a collection of HTML5 forms grouped and presented as a single set of forms to end users. Learn how you can work with formsets in AEM Forms workspace.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
exl-id: 4e39f6dd-b7a3-4c6c-be1f-66b9a5743352
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 4%

---

# Trabalhar com conjuntos de formulários no espaço de trabalho do AEM Forms {#working-with-formsets-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Um conjunto de formulários é uma coleção de formulários HTML5 agrupados e apresentados como um conjunto único de formulários para os usuários finais. Quando os usuários finais começam a preencher um conjunto de formulários, eles são perfeitamente transitados de um formulário para outro. O conjunto de formulários pode ser enviado com apenas um clique. Para obter mais informações sobre conjuntos de formulários e como configurá-los, consulte [Conjunto de formulários no AEM Forms](/help/forms/using/formset-in-aem-forms.md).

A área de trabalho do AEM Forms é compatível com conjuntos de formulários. Com conjuntos de formulários, vários formulários relacionados a um serviço ou processo podem ser agrupados para automatizar um processo de negócios e apresentados aos usuários finais. Nesse cenário, os usuários podem preencher todo o conjunto como um único e não há necessidade de arquivar, enviar e rastrear formulários ou processos individuais.

## Anexar um conjunto de formulários ao ponto de partida em um aplicativo do AEM Forms workspace {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Crie o fluxo de trabalho do processo de negócios no Workbench. Para obter mais informações, consulte [Ajuda do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Nas propriedades do processo do ponto de partida, selecione **Usar um ativo CRX** em Apresentação e dados.

   ![1-1](assets/1-1.png)

1. Clique em ![navegar](assets/browse.png) (Navegar) ao lado do caminho do ativo CRX. A caixa de diálogo Selecionar ativo do formulário é exibida.

   ![2](assets/2.png)

1. Clique no botão **Conjunto de formulários** , selecione o conjunto de formulários relevante na lista e clique em **OK**.

1. Implante o aplicativo após atualizar outras propriedades relevantes do processo.

## Uso de formset na área de trabalho do AEM Forms {#using-formset-in-nbsp-aem-forms-workspace}

Depois que um conjunto de formulários é anexado a um ponto de partida, o ponto de partida pode ser chamado, como qualquer outro ponto de partida é chamado, no espaço de trabalho do AEM Forms.

As operações compatíveis com o conjunto de formulários por meio da área de trabalho do AEM Forms são:

* Salvar como rascunho
* Bloquear
* Desistir
* Enviar
* Adicionar anexos
* Adicionar observações
* Mover entre formulários em um conjunto de formulários usando os botões Voltar ou Próximo

![3-1](assets/3-1.png)

>[!NOTE]
>
>Para melhorar o desempenho durante a movimentação de formulários anteriores e próximos em um conjunto de formulários, todos os botões do espaço de trabalho (Voltar, Próximo, Salvar, Enviar e ... (Mais)) são desativados até que o formulário relevante seja totalmente renderizado.
