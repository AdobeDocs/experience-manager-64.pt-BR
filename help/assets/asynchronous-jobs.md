---
title: Configure operações assíncronas [!DNL Adobe Experience Manager].
description: Conclua de forma assíncrona algumas tarefas que consomem muitos recursos para otimizar o desempenho [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Asynchronous operations {#asynchronous-operations}

Para reduzir o impacto adverso no desempenho, [!DNL Adobe Experience Manger Assets] processa de forma assíncrona determinadas operações de ativos de longa duração e de uso intensivo de recursos. O processamento assíncrono envolve enfileirar várias tarefas e, eventualmente, executá-las de forma serial, dependendo da disponibilidade de recursos do sistema. Essas operações incluem:

* Exclusão de muitos ativos.
* Movimentação de muitos ativos ou ativos com muitas referências.
* Exportar e importar metadados de ativos em massa.

Você pode visualização o status de tarefas assíncronas na página Status **[!UICONTROL do trabalho]** assíncrono.

>[!NOTE]
>
>Por padrão, as [!DNL Assets] tarefas são executadas em paralelo. If `N` is the number of CPU cores, `N/2` tasks can execute in parallel, by default. Para usar configurações personalizadas para a fila de tarefas, modifique a configuração da Fila **[!UICONTROL padrão de operação]** assíncrona do console [!UICONTROL da]Web. Para obter mais informações, consulte [Configurações de fila](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Whenever [!DNL Assets] processes an operation asynchronously, you receive a notification in your [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) and via an email. Para visualizar o status das operações assíncronas em detalhes, acesse a página **[!UICONTROL Status do trabalho assíncrono]**.

1. In the [!DNL Experience Manager] interface click **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Na página **[!UICONTROL Status do trabalho assíncrono]**, verifique os detalhes das operações.

   ![Status e detalhes de operações assíncronas](assets/job_status.png)

   Para verificar o progresso de uma operação, consulte a coluna **[!UICONTROL Status]** . Dependendo do progresso, será exibido um dos seguintes status:

   * **[!UICONTROL Ativo]**: a operação está sendo processada.
   * **[!UICONTROL Sucesso]**: a operação foi concluída.
   * **[!UICONTROL Falha]** ou **[!UICONTROL Erro]**: não foi possível processar a operação.
   * **[!UICONTROL Agendado]**: a operação está programada para ser processada mais tarde.

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) from the toolbar.

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) from the toolbar. A página de detalhes da tarefa é exibida.

   ![Detalhes de uma tarefa de importação de metadados](assets/job_details.png)

1. Para excluir a operação da lista, selecione **[!UICONTROL Excluir]** na barra de ferramentas. Para baixar os detalhes em um arquivo CSV, clique em **[!UICONTROL Baixar]**.

   >[!NOTE]
   >
   >Não é possível excluir uma tarefa se seu status estiver ativo ou na fila.

## Limpar tarefas concluídas {#purge-completed-tasks}

[!DNL Experience Manager Assets] executa uma tarefa de expurgação todos os dias às 100 horas para excluir tarefas assíncronas concluídas com mais de um dia de idade.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Você pode modificar a programação para a tarefa de expurgação e a duração para a qual os detalhes das tarefas concluídas são retidos antes de serem excluídas. Você também pode configurar o número máximo de tarefas concluídas para as quais os detalhes são retidos a qualquer momento.

1. Na [!DNL Experience Manager] interface, clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > Console **[!UICONTROL da Web]**.
1. Abra a tarefa Programada **[!UICONTROL de Expurgação de Tarefas Assíncronas do]** Adobe CQ DAM.
1. Especifique o número limite de dias após o qual as tarefas concluídas são excluídas e o número máximo de tarefas para as quais os detalhes são mantidos no histórico. Salve as alterações.

   ![Configuração para agendar a remoção de tarefas assíncronas](assets/purge_job.png)

## Configurar limite para operações de exclusão assíncronas {#configure-thresholds-for-asynchronous-delete-operations}

Se o número de ativos ou pastas a serem excluídos exceder o número limite definido, a operação de exclusão será executada de forma assíncrona.

1. Na [!DNL Experience Manager] interface, clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > Console **[!UICONTROL da Web]**.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. Na caixa Número **[!UICONTROL limite de ativos]** , especifique os números limite para excluir ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite para a tarefa excluir ativos](assets/delete_threshold.png)

## Configurar limite para operações de movimentação assíncronas {#configure-thresholds-for-asynchronous-move-operations}

Se o número de ativos, pastas ou referências a serem movidos exceder o número limite definido, a operação de movimentação será executada de forma assíncrona.

1. Na [!DNL Experience Manager] interface, clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > Console **[!UICONTROL da Web]**.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. Na caixa Número **[!UICONTROL limite de ativos/referências]** , especifique os números limite para mover ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite de tarefa para mover ativos](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configure e-mail no Experience Manager](/help/sites-administering/notification.md).
>* [Importar e exportar metadados de ativos em massa](/help/assets/metadata-import-export.md).

