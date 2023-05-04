---
title: Iniciar um novo processo com dados de processo existentes na área de trabalho do AEM Forms
seo-title: Initiating a new process with existing process data in AEM Forms workspace
description: Veja como você pode iniciar um novo processo com dados de processo existentes no espaço de trabalho do AEM Forms.
seo-description: See how you can initiate a new process with existing process data in AEM Forms workspace.
uuid: 57a7f414-c9f2-4acc-890a-e29e1adff084
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 4d55a100-1876-41f0-a06f-7a009c934f3d
exl-id: d7bdbd22-97b0-45cd-8e72-43ca3d0d1215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 2%

---

# Iniciar um novo processo com dados de processo existentes na área de trabalho do AEM Forms {#initiating-a-new-process-with-existing-process-data-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

É possível iniciar um novo processo usando os dados de um processo existente. A necessidade de iniciar um novo processo a partir dos dados de processo existentes ocorre quando temos que usar o mesmo formulário com frequência, com poucas alterações no conteúdo, como o dos formulários de tempo pago. Esse recurso economiza tempo e esforço dos usuários, especialmente quando o processo tem um formulário longo para preencher.

A seguir estão as etapas para iniciar um novo processo a partir dos dados de processo existentes:-

1. Execute uma das seguintes ações:

   * Em Tracking, clique na instância do processo cujos dados você deseja usar. Na exibição Histórico do Processo no painel direito, clique na linha de tarefa que corresponde ao ponto inicial.
   * Em Rastreamento, selecione um modelo de pesquisa para exibir uma lista de instâncias de processo. Selecione a instância cujos dados você deseja usar.
   * No **[!UICONTROL Tarefas Pendentes]** selecione a tarefa. Clique no botão **[!UICONTROL Histórico]** e selecione a tarefa que iniciou a instância do processo.

   ![start3](assets/start3.png) ![start1](assets/start1.png)

1. Na barra de ferramentas da ação Tarefa, clique em **[!UICONTROL Iniciar]**. Um formulário adaptável para a nova instância do processo é exibido com dados pré-preenchidos.

1. Atualize os dados conforme necessário e clique em **[!UICONTROL Concluído]** ou um botão apropriado no formulário.
