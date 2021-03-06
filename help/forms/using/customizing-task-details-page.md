---
title: Personalização da página de detalhes da tarefa
seo-title: Personalização da página de detalhes da tarefa
description: Como personalizar a página de detalhes da tarefa na área de trabalho do AEM Forms para modificar as informações padrão exibidas sobre uma tarefa.
seo-description: Como personalizar a página de detalhes da tarefa na área de trabalho do AEM Forms para modificar as informações padrão exibidas sobre uma tarefa.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
translation-type: tm+mt
source-git-commit: 5e764edb3d8ed98542c50b80cac40776c886ccf5
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Personalizar a página de detalhes da tarefa {#customizing-the-task-details-page}

A página de detalhes da tarefa contém informações sobre uma tarefa e seus processos. No entanto, você pode personalizar a página de detalhes da tarefa para adicionar ou excluir informações.

Você pode adicionar as seguintes informações à página de detalhes da tarefa:

* Informações disponíveis no objeto JSON de uma tarefa (seção Tarefa em [Descrição de objeto JSON do espaço de trabalho AEM Forms](/help/forms/using/html-workspace-json-object-description.md))
* Informações disponíveis no objeto JSON de uma instância do processo (seção da instância do processo em [Descrição do objeto JSON do espaço de trabalho AEM Forms](/help/forms/using/html-workspace-json-object-description.md))

Para personalizar a página de detalhes da tarefa:

1. Siga [Etapas genéricas para personalização do espaço de trabalho AEM Forms.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Para mostrar quaisquer informações adicionais, adicione pares de valores chave correspondentes ao arquivo `translation.json` em `todo`block > `details`block > `app`block > [ `required`block].

   O [ `required`block] refere-se aos blocos disponíveis, como o bloco de tarefa para informações de tarefa, o bloco de processo para informações de processo e o bloco de tarefas atual para informações tarefas pendentes.

   Por exemplo, para adicionar informações sobre a Seleção de rota obrigatória na página de detalhes da tarefa, adicione o seguinte par de valores chave no bloco de tarefa:

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Adicione pares de valores chave correspondentes para todos os idiomas suportados.

1. Copie `/libs/ws/js/runtime/templates/taskdetails.html` para `/apps/ws/js/runtime/templates/taskdetails.html`.

   Adicione as novas informações a `/apps/ws/js/runtime/templates/taskdetails.html`. Por exemplo:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Abra /apps/ws/js/registry.js para edição.

   Pesquise e substitua `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` por `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Para personalizar a página de detalhes da tarefa com tarefas criadas na **guia Processo de Start **da área de trabalho do AEM Forms, adicione as novas informações a `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Para adicionar novos estilos para as informações adicionadas na página de detalhes, modifique o arquivo CSS usando a seção *Alterações na interface do usuário* em [Personalização da Workspace](/help/forms/using/changing-locale-user-interface.md).
