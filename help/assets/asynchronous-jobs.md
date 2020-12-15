---
title: Configure operações assíncronas em [!DNL Adobe Experience Manager].
description: Conclua de forma assíncrona algumas tarefas que consomem muitos recursos para otimizar o desempenho em [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Operações assíncronas {#asynchronous-operations}

Para reduzir o impacto adverso no desempenho, [!DNL Adobe Experience Manger Assets] processa de modo assíncrono determinadas operações de ativos de longa duração e de uso intensivo de recursos. O processamento assíncrono envolve enfileirar várias tarefas e, eventualmente, executá-las de forma serial, dependendo da disponibilidade de recursos do sistema. Essas operações incluem:

* Exclusão de muitos ativos.
* Movimentação de muitos ativos ou ativos com muitas referências.
* Exportar e importar metadados de ativos em massa.

Você pode visualização o status de tarefas assíncronas da página **[!UICONTROL Status do trabalho assíncrono]**.

>[!NOTE]
>
>Por padrão, as tarefas [!DNL Assets] são executadas em paralelo. Se `N` for o número de núcleos da CPU, `N/2` o tarefa poderá ser executado em paralelo, por padrão. Para usar configurações personalizadas para a fila de tarefas, modifique a configuração **[!UICONTROL Fila padrão de operação assíncrona]** do [!UICONTROL Console da Web]. Para obter mais informações, consulte [Configurações de fila](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitore o status das operações assíncronas {#monitoring-the-status-of-asynchronous-operations}

Sempre que [!DNL Assets] processar uma operação de forma assíncrona, você receberá uma notificação em sua [!DNL Experience Manager] [Caixa de entrada](/help/sites-authoring/inbox.md) e por um email. Para visualizar o status das operações assíncronas em detalhes, acesse a página **[!UICONTROL Status do trabalho assíncrono]**.

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Operações]** > **[!UICONTROL Tarefas]**.

1. Na página **[!UICONTROL Status do trabalho assíncrono]**, verifique os detalhes das operações.

   ![Status e detalhes de operações assíncronas](assets/job_status.png)

   Para verificar o progresso de uma operação, consulte a coluna **[!UICONTROL Status]**. Dependendo do progresso, será exibido um dos seguintes status:

   * **[!UICONTROL Ativo]**: a operação está sendo processada.
   * **[!UICONTROL Sucesso]**: a operação foi concluída.
   * **[!UICONTROL Falha]** ou **[!UICONTROL Erro]**: não foi possível processar a operação.
   * **[!UICONTROL Agendado]**: a operação está programada para ser processada mais tarde.

1. Para interromper uma operação ativa, selecione-a na lista e clique em **[!UICONTROL Parar]** ![ícone de parada](assets/do-not-localize/stop_icon.svg) na barra de ferramentas.

1. Para visualização de detalhes adicionais, por exemplo, descrição e registros, selecione a operação e clique em **[!UICONTROL Abrir]** ![open_icon](assets/do-not-localize/edit_icon.svg) na barra de ferramentas. A página de detalhes da tarefa é exibida.

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

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console Web]**.
1. Abra a tarefa **[!UICONTROL Adobe CQ DAM Async Jobs Expurgar Programados]**.
1. Especifique o número limite de dias após o qual as tarefas concluídas são excluídas e o número máximo de tarefas para as quais os detalhes são mantidos no histórico. Salve as alterações.

   ![Configuração para agendar a remoção de tarefas assíncronas](assets/purge_job.png)

## Configurar limite para operações de exclusão assíncronas {#configure-thresholds-for-asynchronous-delete-operations}

Se o número de ativos ou pastas a serem excluídos exceder o número limite definido, a operação de exclusão será executada de forma assíncrona.

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console Web]**.
1. No [!UICONTROL Console Web], abra a configuração **[!UICONTROL Async Delete Operation Job Processing]**.
1. Na caixa **[!UICONTROL Número limite de ativos]**, especifique os números limite para excluir ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite para a tarefa excluir ativos](assets/delete_threshold.png)

## Configurar limite para operações de movimentação assíncronas {#configure-thresholds-for-asynchronous-move-operations}

Se o número de ativos, pastas ou referências a serem movidos exceder o número limite definido, a operação de movimentação será executada de forma assíncrona.

1. Na interface [!DNL Experience Manager], clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console Web]**.
1. No [!UICONTROL Console Web], abra a configuração **[!UICONTROL Async Move Operation Job Processing]**.
1. Na caixa **[!UICONTROL Número limite de ativos/referências]**, especifique os números limite para mover ativos, pastas ou referências de forma assíncrona. Salve as alterações.

   ![Definir o limite de tarefa para mover ativos](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configure e-mail no Experience Manager](/help/sites-administering/notification.md).
>* [Importar e exportar metadados de ativos em massa](/help/assets/metadata-import-export.md).

