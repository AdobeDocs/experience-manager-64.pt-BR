---
title: Como personalizar guias para uma tarefa
seo-title: Como personalizar guias para uma tarefa
description: Como personalizar os nomes das guias para suas tarefas, na área de trabalho do LiveCycle AEM Forms.
seo-description: Como personalizar os nomes das guias para suas tarefas, na área de trabalho do LiveCycle AEM Forms.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Personalizar guias para uma tarefa {#customizing-tabs-for-a-task}

Você pode personalizar nomes de guias para o componente `Start Process` na visualização `Start Process` Uber e o componente `Task Details` na visualização `ToDo` Uber.

1. Siga as [etapas genéricas para personalização do espaço de trabalho AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Altere o valor de `tabname`no arquivo `translation.json`.

   Por exemplo, altere `/apps/ws/locales/en-US/translation.json` para inglês para o seguinte.

   * Para tarefas iniciadas no processo de start, use o seguinte trecho do bloco `"startprocess" : {}`.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Para tarefa em To-do, use o seguinte snippet do bloco `"todo" : {}`.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Adicione um par de valor de chave correspondente para todos os idiomas suportados.
