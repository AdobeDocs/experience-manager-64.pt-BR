---
title: Configure operações assíncronas em [!DNL Adobe Experience Manager].
description: Conclua de forma assíncrona algumas tarefas que consomem muitos recursos para otimizar o desempenho em [!DNL Experience Manager Assets].
contentOwner: AG
feature: Gerenciamento de ativos
role: Profissional
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 22%

---


# Operações assíncronas {#asynchronous-operations}

Para reduzir o impacto adverso no desempenho, [!DNL Adobe Experience Manger Assets] processa de forma assíncrona determinadas operações de ativos de longa duração e com uso intenso de recursos. O processamento assíncrono envolve enfileiramento de várias tarefas e, eventualmente, executá-las em série, dependendo da disponibilidade dos recursos do sistema. Essas operações incluem:

* Exclusão de muitos ativos.
* Movimentação de muitos ativos ou ativos com muitas referências.
* Exportação e importação de metadados de ativos em massa.

Você pode visualizar o status de tarefas assíncronas na página **[!UICONTROL Status do trabalho assíncrono]**.

>[!NOTE]
>
>Por padrão, as tarefas [!DNL Assets] são executadas em paralelo. Se `N` for o número de núcleos da CPU, `N/2` as tarefas podem ser executadas em paralelo, por padrão. Para usar configurações personalizadas para a fila de tarefas, modifique a configuração **[!UICONTROL Async Operation Default Queue]** do [!UICONTROL Web Console]. Para obter mais informações, consulte [Configurações de fila](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitorar o status de operações assíncronas {#monitoring-the-status-of-asynchronous-operations}

Sempre que [!DNL Assets] processar uma operação de forma assíncrona, você receberá uma notificação em [!DNL Experience Manager] [Caixa de entrada](/help/sites-authoring/inbox.md) e por email. Para visualizar o status das operações assíncronas em detalhes, acesse a página **[!UICONTROL Status do trabalho assíncrono]**.

1. Na interface [!DNL Experience Manager] clique em **[!UICONTROL Operações]** > **[!UICONTROL Trabalhos]**.

1. Na página **[!UICONTROL Status do trabalho assíncrono]**, verifique os detalhes das operações.

   ![Status e detalhes de operações assíncronas](assets/job_status.png)

   Para determinar o progresso de uma operação, consulte a coluna **[!UICONTROL Status]**. Dependendo do progresso, será exibido um dos seguintes status:

   * **[!UICONTROL Ativo]**: a operação está sendo processada.
   * **[!UICONTROL Sucesso]**: a operação foi concluída.
   * **[!UICONTROL Falha]** ou **[!UICONTROL Erro]**: não foi possível processar a operação.
   * **[!UICONTROL Agendado]**: a operação está programada para ser processada mais tarde.

1. Para interromper uma operação ativa, selecione-a na lista e clique em **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) na barra de ferramentas.

1. Para visualizar mais detalhes, por exemplo, descrição e registros, selecione a operação e clique em **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) na barra de ferramentas. A página de detalhes da tarefa é exibida.

   ![Detalhes de uma tarefa de importação de metadados](assets/job_details.png)

1. Para excluir a operação da lista, selecione **[!UICONTROL Excluir]** na barra de ferramentas. Para baixar os detalhes em um arquivo CSV, clique em **[!UICONTROL Baixar]**.

   >[!NOTE]
   >
   >Não é possível excluir uma tarefa se seu status estiver ativo ou na fila.

## Limpar tarefas concluídas {#purge-completed-tasks}

[!DNL Experience Manager Assets] O executa uma tarefa de limpeza todos os dias às 100 horas para excluir tarefas assíncronas concluídas com mais de um dia.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Você pode modificar o agendamento da tarefa de limpeza e a duração para a qual os detalhes das tarefas concluídas são retidos antes de serem excluídos. Você também pode configurar o número máximo de tarefas concluídas para as quais os detalhes são retidos a qualquer momento.

1. Na interface [!DNL Experience Manager] clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
1. Abra a tarefa **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]**.
1. Especifique o limite de dias após o qual as tarefas concluídas são excluídas e o número máximo de tarefas para as quais os detalhes são retidos no histórico. Salve as alterações.

   ![Configuração para agendar a limpeza de tarefas assíncronas](assets/purge_job.png)

## Configurar limite para operações de exclusão assíncronas {#configure-thresholds-for-asynchronous-delete-operations}

Se o número de ativos ou pastas que serão excluídos exceder o limite definido, a operação de exclusão será executada de forma assíncrona.

1. Na interface [!DNL Experience Manager] clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
1. No [!UICONTROL Console da Web], abra a configuração **[!UICONTROL Async Delete Operation Job Processing]**.
1. Na caixa **[!UICONTROL Limite de ativos]**, especifique os limites de números para excluir ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite da tarefa para excluir ativos](assets/delete_threshold.png)

## Configurar limite para operações assíncronas de movimentação {#configure-thresholds-for-asynchronous-move-operations}

Se o número de ativos, pastas ou referências que serão movidos exceder o limite definido, a operação de movimentação será executada de forma assíncrona.

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
1. No [!UICONTROL Console da Web], abra a configuração **[!UICONTROL Async Move Operation Job Processing]**.
1. Na caixa **[!UICONTROL Limite de ativos/referências]**, especifique os limites de números para mover ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite da tarefa para mover ativos](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configure o email no Experience Manager](/help/sites-administering/notification.md).
>* [Importar e exportar metadados de ativos em massa](/help/assets/metadata-import-export.md).

