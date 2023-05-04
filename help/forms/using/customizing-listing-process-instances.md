---
title: Personalização da lista de instâncias de processo
seo-title: Customizing the listing of process instances
description: Como personalizar as propriedades exibidas na instância do processo no espaço de trabalho do AEM Forms.
seo-description: How-to customize the properties displayed in process instance in AEM Forms workspace.
uuid: 3b55d9b9-7f73-46dd-9eb6-42be218440a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 40d7d43f-ee0a-4e34-ae93-20c9c940f76b
exl-id: e7b8206c-bac2-48a6-b353-d06bc73b29f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%

---

# Personalização da lista de instâncias de processo {#customizing-the-listing-of-process-instances}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A lista de instâncias do processo é exibida na guia Tracking do espaço de trabalho do AEM Forms.

Na lista de instâncias de processo, para cada instância de processo, o AEM Forms workspace mostra algumas propriedades dessa instância. As seguintes propriedades estão disponíveis para cada instância do processo. Essas propriedades são armazenadas como atributos no modelo de componente da instância do processo e estão disponíveis para uso na visualização e no modelo.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Propriedade</strong></td> 
   <td><strong>Comentários</strong></td> 
  </tr> 
  <tr> 
   <td>descrição</td> 
   <td>Descrição da instância do processo.</td> 
  </tr> 
  <tr> 
   <td>iniciador</td> 
   <td>Nome do iniciador da instância do processo.</td> 
  </tr> 
  <tr> 
   <td>initiatorId</td> 
   <td>ID do iniciador da instância do processo.</td> 
  </tr> 
  <tr> 
   <td>processCompleteTime</td> 
   <td>Carimbo de data/hora quando o processo é concluído.</td> 
  </tr> 
  <tr> 
   <td>processInstanceId</td> 
   <td>ID da instância do processo.</td> 
  </tr> 
  <tr> 
   <td>processInstanceStatus</td> 
   <td>0 = Iniciado<br /> 1 = Em Execução<br /> 2 = Concluído<br /> 3 = Concluindo<br /> 4 = Terminado<br /> 5 = Terminando<br /> 6 = Suspenso<br /> 7 = Suspensão<br /> 8 = Suspensão</td> 
  </tr> 
  <tr> 
   <td>processName</td> 
   <td>Nome do processo.</td> 
  </tr> 
  <tr> 
   <td>processStartTime</td> 
   <td>Carimbo de data e hora quando o processo foi iniciado.</td> 
  </tr> 
  <tr> 
   <td>processVariables</td> 
   <td>Matriz de objetos de variáveis de processo. Cada objeto de variável de processo contém <strong>name</strong> (o nome da variável de processo), <strong>value</strong> (valor da variável de processo) e<strong> type</strong> (o tipo de variável de processo).</td> 
  </tr> 
 </tbody> 
</table>

**Exemplo:**

Para exibir o `description` da instância do processo no cartão de instância do processo, execute as seguintes etapas.

1. Siga as [Etapas genéricas para personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Faça o seguinte:

   1. Copie /libs/ws/js/runtime/templates/processinstance.html para/apps/ws/js/runtime/templates/, se não existir. Clique em **Salvar tudo**.
   1. Adicione a descrição do processo div com class = &#39;processDescription&#39; inprocessinstance.html.

   ```
   <div class="processDescription" title="<%= description%>"><%= description%></div>
   ```

1. Faça o seguinte:

   1. Abra /apps/ws/js/registry.js para edição.
   1. Pesquisar e substituir `text!/lc/libs/ws/js/runtime/templates/processinstance.html`com `text!/lc/`**aplicativos**/ws/js/runtime/templates/processinstance.html.

1. As alterações acima podem exigir uma atualização do arquivo CSS, adicionando uma entrada na folha de estilos /apps/ws/css/newStyle.css da seguinte maneira:

   ```css
   .processinstance .processDescription {
    <!--Dummy values, need to be configured by user as per requirement as well as user can add or delete any property depending upon requirement-->
       width : 250px;
       font-size : 11pt;
       padding : 2px;
   }
   ```
