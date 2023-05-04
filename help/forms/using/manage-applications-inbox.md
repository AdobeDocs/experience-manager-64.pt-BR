---
title: Gerenciar aplicativos e tarefas do Forms na Caixa de entrada AEM
seo-title: Manage Forms applications and tasks in AEM Inbox
description: AEM Caixa de entrada permite iniciar fluxos de trabalho centrados no Forms por meio da submissão de aplicativos e do gerenciamento de tarefas.
seo-description: AEM Inbox allows you to launch Forms-centric workflows through submitting applications and manage tasks.
uuid: 5173558a-542a-4130-8bb6-5ac555ecc507
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: document_services, publish
discoiquuid: c1515c58-7d9a-4a36-9390-f6d6b980b801
exl-id: 7076807a-40ad-4f3b-beb0-70c1577a8ee7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---

# Gerenciar aplicativos e tarefas do Forms na Caixa de entrada AEM {#manage-forms-applications-and-tasks-in-aem-inbox}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Uma das muitas maneiras de iniciar ou acionar um fluxo de trabalho centrado no Forms é por meio de aplicativos em AEM Caixa de entrada. É necessário criar um aplicativo de fluxo de trabalho para disponibilizar um fluxo de trabalho do Forms como aplicativo na Caixa de entrada. Para obter mais informações sobre o aplicativo de fluxo de trabalho e outras maneiras de iniciar fluxos de trabalho do Forms, consulte [Iniciar um fluxo de trabalho centrado na Forms no OSGi](/help/forms/using/aem-forms-workflow.md#launch).

Além disso, AEM Caixa de entrada consolida notificações e tarefas de vários componentes de AEM, incluindo workflows do Forms. Quando um fluxo de trabalho de formulários contendo uma etapa de tarefa Atribuir é acionado, o aplicativo associado é listado como uma tarefa na Caixa de entrada do destinatário. Se o destinatário for um grupo, a tarefa aparecerá na Caixa de entrada de todos os membros do grupo até que um indivíduo reivindique ou delegue a tarefa.

A interface do usuário da Caixa de entrada fornece exibições de lista e calendário para visualizar tarefas. Você também pode definir as configurações de exibição. Você pode filtrar tarefas com base em vários parâmetros. Para obter mais informações sobre visualização e filtros, consulte [Sua Caixa de entrada](/help/sites-authoring/inbox.md).

Em resumo, a Caixa de entrada permite criar um novo aplicativo e gerenciar tarefas atribuídas.

>[!NOTE]
>
>Você deve ser um membro do grupo de usuários do fluxo de trabalho para poder usar AEM Caixa de entrada.

## Criar aplicativo {#create-application}

1. Ir para AEM Caixa de entrada em `https://[server]:[port]/aem/inbox`.
1. Na interface da caixa de entrada, toque em **[!UICONTROL Criar > Aplicativo]**. A página Selecionar aplicativo é exibida.
1. Selecione um aplicativo e clique em **[!UICONTROL Criar]**. O formulário Adaptável associado ao aplicativo é aberto. Preencha os formulários e toque em **[!UICONTROL Enviar]**. Ele inicia o fluxo de trabalho associado e cria uma tarefa na Caixa de entrada do destinatário.

## Gerencie tarefas {#manage-tasks}

Quando um workflow do Forms é acionado e você é um destinatário ou parte do grupo destinatário, uma tarefa é exibida em sua Caixa de entrada. Você pode visualizar os detalhes da tarefa e executar as ações disponíveis na tarefa a partir da Caixa de entrada.

### Solicitar ou delegar tarefas {#claim-or-delegate-tasks}

As tarefas atribuídas a um grupo são exibidas na Caixa de entrada de todos os membros do grupo. Qualquer membro do grupo pode reivindicar essa tarefa ou delegá-la a outro membro do grupo. Para fazer isso:

1. Toque para selecionar a miniatura da tarefa. As opções para abrir ou delegar a tarefa são exibidas na parte superior.

   ![select-task](assets/select-task.png)

1. Siga uma das seguintes opções:

   * Para delegar a tarefa, toque em **[!UICONTROL Delegar]**. A caixa de diálogo Delegar item é aberta. Selecione um usuário, como opção, adicione um comentário e toque em **[!UICONTROL OK]**.

   ![delegate](assets/delegate.png)

   * Para reivindicar a tarefa, toque em **[!UICONTROL Abrir]**. A caixa de diálogo Atribuir a si mesmo é aberta. Toque **[!UICONTROL Continue]** para reivindicar a tarefa. A tarefa reivindicada é exibida com você como o destinatário em sua Caixa de entrada.

   ![reivindicação](assets/claim.png)

### Exibir detalhes e executar ações em tarefas {#view-details-and-perform-actions-on-tasks}

Ao abrir uma tarefa, você pode exibir os detalhes da tarefa e executar as ações disponíveis. As ações disponíveis para uma tarefa são definidas na etapa Assign task do workflow associado Forms .

1. Toque para selecionar a miniatura da tarefa. As opções para abrir ou delegar a tarefa selecionada aparecem na parte superior.
1. Toque **[!UICONTROL Abrir]** para exibir detalhes da tarefa e realizar ações. A exibição detalhada da tarefa é aberta. Nesta visualização, você pode exibir detalhes da tarefa e realizar ações na tarefa.

   >[!NOTE]
   >
   >Se uma tarefa for atribuída a um grupo, você deverá reivindicar a abertura da tarefa na exibição detalhada.

![detalhes da tarefa](assets/task-details.png)

A exibição detalhada da tarefa compreende as seguintes seções:

* Detalhes da tarefa
* Formulário
* Detalhes do fluxo de trabalho
* Barra de ferramentas Ações

#### Detalhes da tarefa {#task-details}

A seção Detalhes da tarefa exibe informações sobre a tarefa. As informações exibidas dependem das configurações do [Atribuir etapa da tarefa](/help/sites-developing/workflows-step-ref.md) no fluxo de trabalho. O exemplo acima exibe a descrição, o status, a data de início e o workflow usado para a tarefa. Também permite anexar um arquivo à tarefa.

#### Formulário {#form}

A guia Formulário na área de conteúdo principal exibe o formulário enviado e os anexos em nível de campo, se houver.

#### Detalhes do fluxo de trabalho {#workflow-details}

A guia Detalhes do fluxo de trabalho na parte superior mostra o progresso da tarefa em vários estágios no fluxo de trabalho. Ele mostra estágios concluídos, atuais e pendentes para a tarefa. Os estágios de um workflow são definidos na variável [Atribuir etapa da tarefa](/help/sites-developing/workflows-step-ref.md) do fluxo de trabalho associado.

Além disso, a guia exibe o histórico de tarefas para cada estágio concluído no fluxo de trabalho. Você pode tocar em **[!UICONTROL Exibir detalhes]** para uma fase concluída, para conhecer os detalhes dessa fase. Ele exibe comentários, anexos de formulário e tarefa, status, datas de início e término e assim por diante sobre a tarefa.

![detalhes do fluxo de trabalho](assets/workflow-details.png)

#### Barra de ferramentas Ações {#actions-toolbar}

A barra de ferramentas Ações mostra todas as opções disponíveis para a tarefa. Enquanto Salvar, Redefinir e Delegar são ações padrão, outras ações disponíveis são configuradas em [Atribuir etapa da tarefa](/help/sites-developing/workflows-step-ref.md). No exemplo acima, Approve e Reject são configurados no workflow.

À medida que você executa uma ação na tarefa, ela prossegue no fluxo de trabalho.

### Exibir tarefas concluídas {#view-completed-tasks}

AEM Caixa de entrada exibe somente as tarefas ativas. Tarefas concluídas não aparecem na lista. No entanto, você pode usar filtros da Caixa de entrada para filtrar tarefas com base em vários parâmetros, como tipo de tarefa, status, datas de início e término e assim por diante. Para exibir tarefas concluídas:

1. Na Caixa de entrada AEM, toque em ![painel lateral de alternância1](assets/toggle-side-panel1.png) para abrir o seletor de filtro.
1. Toque **[!UICONTROL Status da tarefa]** e selecione **[!UICONTROL Concluído]**. Todas as tarefas concluídas são exibidas.

   ![filter-1](assets/filter-1.png)

1. Toque para selecionar uma tarefa e clique em **[!UICONTROL Abrir]**.

A tarefa é aberta para exibir o documento ou o formulário adaptável associado à tarefa. Para o formulário adaptável, ele exibe o formulário adaptável somente leitura ou seu documento PDF de registro, conforme configurado na guia Formulário/Documento do [Etapa Atribuir fluxo de trabalho da tarefa](/help/sites-developing/workflows-step-ref.md).

A seção de detalhes da tarefa exibe informações como ação executada, status da tarefa, data de início e data de término.

![tarefa concluída](assets/completed-task.png)

O **[!UICONTROL Detalhes do fluxo de trabalho]** mostra cada etapa do fluxo de trabalho. Toque **[!UICONTROL Exibir detalhes]** para obter uma etapa para obter informações detalhadas.

![completed-task-workflow](assets/completed-task-workflow.png)
