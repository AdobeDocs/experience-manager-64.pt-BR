---
title: Exibição de dados adicionais na lista do ToDo
seo-title: Exibição de dados adicionais na lista do ToDo
description: Como personalizar a exibição da lista de tarefas da área de trabalho do LiveCycle AEM Forms para mostrar mais informações além do padrão.
seo-description: Como personalizar a exibição da lista de tarefas da área de trabalho do LiveCycle AEM Forms para mostrar mais informações além do padrão.
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
translation-type: tm+mt
source-git-commit: a5cac0d369bb40659cfde011e5d6ef9a68dc4012
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Exibição de dados adicionais na lista do ToDo {#displaying-additional-data-in-todo-list}

Por padrão, a lista do AEM Forms Workspace To-do exibe o nome de exibição e a descrição da tarefa. No entanto, você pode adicionar outras informações, como data de criação e data de término. Você também pode adicionar ícones e alterar o estilo da exibição.

![Uma amostra da guia HTML Workspace To-do mostrando a configuração padrão](assets/html-todo-list.png)

Este artigo detalha as etapas para adicionar informações a serem exibidas para cada tarefa na lista de Tarefas.

## O que pode ser adicionado {#what-can-be-added}

Você pode adicionar as informações disponíveis em `task.json` enviadas pelo servidor. As informações podem ser adicionadas como texto sem formatação ou você pode usar estilos para formatar as informações.

Para obter mais informações sobre a descrição do objeto JSON, consulte o artigo [this](/help/forms/using/html-workspace-json-object-description.md).

## Exibição de informações em uma tarefa {#displaying-information-on-a-task}

1. Siga as [etapas genéricas para personalização do espaço de trabalho AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Para exibir informações adicionais de uma tarefa, os pares de valores chave correspondentes devem ser adicionados dentro do bloco de tarefa de `translation.json`.

   Por exemplo, altere `/apps/ws/locales/en-US/translation.json` para inglês:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Adicione pares de valores chave correspondentes para todos os idiomas suportados.

1. Por exemplo, adicione informações dentro do bloco de tarefa:

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## Definição de CSS para a nova propriedade {#defining-css-for-the-new-property}

1. Você pode aplicar estilo às informações (propriedade) adicionadas a uma tarefa. Para fazer isso, é necessário adicionar informações de estilo para a nova propriedade adicionada a `/apps/ws/css/newStyle.css`.

   Por exemplo, adicione:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Adicionando entrada no Modelo HTML {#adding-entry-in-the-html-template}

Por fim, é necessário incluir uma entrada no pacote dev para cada propriedade que você deseja adicionar à tarefa. Para criar um, consulte Criar código de espaço de trabalho AEM Forms.

1. Copiar `task.html`:

   * de: `/libs/ws/js/runtime/templates/`
   * para: `/apps/ws/js/runtime/templates/`

1. Adicione as novas informações a `/apps/ws/js/runtime/templates/task.html`.

   Por exemplo, adicione em `div class="taskProperties"`:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
