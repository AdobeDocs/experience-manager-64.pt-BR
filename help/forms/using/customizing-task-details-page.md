---
title: Personalização da página de detalhes da tarefa
seo-title: Customizing the task details page
description: Como personalizar a página de detalhes da tarefa no espaço de trabalho do AEM Forms para modificar as informações padrão exibidas sobre uma tarefa.
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Personalização da página de detalhes da tarefa {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A página de detalhes da tarefa contém informações sobre uma tarefa e seus processos. No entanto, é possível personalizar a página de detalhes da tarefa para adicionar ou excluir informações.

Você pode adicionar as seguintes informações à página de detalhes da tarefa:

* Informações disponíveis no objeto JSON de uma tarefa (seção Tarefa em [Descrição do objeto JSON do espaço de trabalho do AEM Forms](/help/forms/using/html-workspace-json-object-description.md))
* Informações disponíveis no objeto JSON de uma instância do processo (seção Instância do processo em [Descrição do objeto JSON do espaço de trabalho do AEM Forms](/help/forms/using/html-workspace-json-object-description.md))

Para personalizar a página de detalhes da tarefa:

1. Seguir [Etapas genéricas para personalização do espaço de trabalho do AEM Forms.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Para mostrar qualquer informação adicional, adicione pares de valores chave correspondentes à variável `translation.json` arquivo em `todo`bloco > `details`bloco > `app`bloco > [ `required`bloco].

   O [ `required`bloco] refere-se aos blocos disponíveis, como o bloco de tarefas para informações de tarefas, o bloco de processos para informações de processos e o bloco de tarefas pendente atual para informações de tarefas pendentes.

   Por exemplo, para adicionar informações sobre a Seleção de rota necessária na página de detalhes da tarefa, você pode adicionar o seguinte par de valores chave no bloco de tarefas:

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

1. Copiar `/libs/ws/js/runtime/templates/taskdetails.html` para `/apps/ws/js/runtime/templates/taskdetails.html`.

   Adicione as novas informações em `/apps/ws/js/runtime/templates/taskdetails.html`. Por exemplo:

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

   Pesquisar e substituir `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` com `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Para personalizar a página de detalhes da tarefa com tarefas criadas na guia **Iniciar processo **do espaço de trabalho do AEM Forms, adicione as novas informações a `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Para adicionar novos estilos para as informações adicionadas na página de detalhes, modifique o arquivo CSS usando o *Alterações na interface do usuário* seção em [Personalização do Workspace](/help/forms/using/changing-locale-user-interface.md).
