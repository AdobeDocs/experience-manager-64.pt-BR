---
title: Personalizando guias de uma tarefa
seo-title: Customizing tabs for a task
description: Como personalizar os nomes das guias para suas tarefas na área de trabalho do LiveCycle AEM Forms.
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 5%

---

# Personalizando guias de uma tarefa {#customizing-tabs-for-a-task}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode personalizar nomes de guias para a variável `Start Process` no `Start Process` Visualização do Uber e o `Task Details` no `ToDo` Visualização Uber.

1. Siga as [Etapas genéricas para personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Altere o valor de `tabname`no `translation.json` arquivo.

   Por exemplo, alterar `/apps/ws/locales/en-US/translation.json` em inglês, para o seguinte.

   * Para tarefas iniciadas no processo de início, use o seguinte trecho do `"startprocess" : {}` bloco.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Para tarefas em Tarefas pendentes, use o seguinte trecho do `"todo" : {}` bloco.

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
   >Adicione um par de valores chave correspondente para todos os idiomas compatíveis.
