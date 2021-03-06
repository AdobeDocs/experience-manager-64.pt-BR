---
title: Obtendo variáveis de Tarefa no URL de resumo
seo-title: Obtendo variáveis de Tarefa no URL de resumo
description: Como reutilizar as informações sobre uma tarefa e gerar um URL de resumo para resumir ou descrever uma tarefa.
seo-description: Como reutilizar as informações sobre uma tarefa e gerar um URL de resumo para resumir ou descrever uma tarefa.
uuid: 9eab3a6a-a99a-40ae-b483-33ec7d21c5b6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6dc31bec-b02d-47db-a4f4-be8c14c5619e
translation-type: tm+mt
source-git-commit: d0bb877bb6a502ad0131e4f1a7e399caa474a7c9
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Obtendo variáveis de Tarefa no URL de resumo {#getting-task-variables-in-summary-url}

A página de resumo exibe informações relacionadas à tarefa. Este artigo descreve como você pode reutilizar informações relacionadas à tarefa na página de resumo.

Nessa orquestração de amostra, um funcionário envia um formulário de solicitação de licença. O formulário de inscrição será então enviado ao gerente do funcionário para aprovação.

1. Crie um renderizador HTML de amostra (html.esp) para resourceType **Funcionários/PtoApplication**.

   O renderizador assume as seguintes propriedades a serem definidas no nó:

   * ename
   * empid
   * reason
   * duration

   >[!NOTE]
   >
   >Esse renderizador é o modelo de página de resumo.

   O código de amostra a seguir para este renderizador está contido em:

   `apps/Employees/PtoApplication/html.esp`

   ```
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. Modifique a orquestração para extrair as quatro propriedades dos dados de formulário enviados. Depois disso, crie um nó no CRX do tipo **Funcionários/PtoApplication**, com as propriedades preenchidas.

   1. Crie um processo **crie um resumo PTO** e use-o como um subprocesso antes da operação **Atribuir Tarefa** na sua orquestração.
   1. Defina **empregadoName**, **empregadoID**, **ptoReason**, **totalDays** e **nodeName** como variáveis de entrada no novo processo. Essas variáveis serão passadas como dados de formulário enviados.

      Defina também uma variável de saída **ptoNodePath **que será usada ao configurar o URL de resumo.

   1. No processo **criar resumo PTO**, use o componente **set value** para definir os detalhes de entrada em um mapa **nodeProperty **(**nodeProps**).

      As teclas neste mapa devem ser as mesmas definidas no seu renderizador HTML na etapa anterior.

      Além disso, adicione uma tecla **sling:resourceType** com o valor **Funcionários/PtoApplication** no mapa.

   1. Use o subprocesso **storeContent** do serviço **ContentRepositoryConnector** no processo **criar resumo PTO**. Esse subprocesso cria um nó CRX.

      São necessárias três variáveis de entrada:

      * **Caminho** da pasta: O caminho onde o novo nó CRX é criado. Defina o caminho como **/content**.
      * **Nome** do nó: Atribua a variável de entrada nodeName a este campo. Esta é uma string de nome de nó exclusiva.
      * **Tipo** de nó: Defina o tipo como  **nt:unstruct**. A saída desse processo é nodePath. O nodePath é o caminho CRX do nó recém-criado. O ndoePath seria a saída final do processo de resumo **create PTO**.
   1. Passe os dados de formulário enviados (**empregadoName**, **empregadoID**, **ptoReason** e **totalDays**) como entrada para o novo processo **criar resumo PTO**. Obtenha a saída como **ptoSummaryNodePath**.


1. Defina o URL de resumo como uma expressão XPath contendo os detalhes do servidor junto com **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Na área de trabalho do AEM Forms, quando você abre uma tarefa, o URL de resumo acessa o nó CRX e o renderizador HTML exibe o resumo.

O layout de resumo pode ser alterado sem modificar o processo. O renderizador HTML exibe o resumo adequadamente.

