---
title: Relatórios predefinidos em Relatório de Processo
seo-title: Pre-defined reports in Process Reporting
description: Consulte AEM Forms nos dados do processo JEE para criar relatórios em processos de longa execução, duração do processo e volume de fluxo de trabalho
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---

# Relatórios predefinidos em Relatório de Processo {#pre-defined-reports-in-process-reporting}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM Forms Process Reporting é enviado com o seguinte *pronto para uso* relatórios:

* **[Processos de Longa Execução](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: Um relatório de todos os processos do AEM Forms que levaram mais de um tempo especificado para serem concluídos

* **[Gráfico de Duração do Processo](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: Um relatório de um processo AEM Forms especificado por duração

* **[Volume do fluxo de trabalho](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: Um relatório das instâncias em execução e concluídas do processo especificado por data

## Processos de Longa Execução {#long-running-processes}

O relatório Long Running Processes exibe os processos do AEM Forms que levaram mais de um tempo especificado para serem concluídos.

### Para executar um relatório de Processo de Execução Longa {#to-execute-a-long-running-process-report-br}

1. Para exibir a lista de relatórios predefinidos em Relatórios do Processo, no **Relatório de processos** exibição em árvore, clique no botão **Relatórios** nó .
1. Clique no botão **Processos de Longa Execução** nó do relatório.

   ![long_running_node](assets/long_running_node.png)

   Ao selecionar um relatório, a variável **Parâmetros do relatório** é exibido à direita da visualização em árvore.

   ![painel de parâmetros de relatório de processos de execução longa](assets/report_parameters_panel.png)

   Parâmetros:

   * **Duração**(*mandatory*): Especifique uma duração e uma unidade de tempo. Exibe todos os processos do AEM Forms que foram executados por mais do que a duração especificada.
   * **Iniciado após** (*opcional*): Selecione uma data. Filtre o relatório para exibir instâncias de processo que começaram após a data especificada.
   * **Iniciado antes** (*opcional*): Selecione uma data. Filtre o relatório para exibir instâncias de processo que iniciaram antes da data especificada.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido na **Relatório** à direita do **Relatório de processos** janela.

   ![long_running_processes](assets/long_running_processes.png)

   Use as opções no canto superior direito do **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor da legenda**: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas

## Relatório de duração do processo {#process-duration-report-br}

O relatório Duração do processo exibe o número de instâncias de um processo do Forms por número de dias que cada instância foi executada.

### Para executar um relatório de Duração do processo {#to-execute-a-process-duration-report-br}

1. Para exibir os relatórios predefinidos no Relatório do Processo, no **Relatório de processos** exibição em árvore, clique no botão **Relatórios** nó .
1. Clique no botão **Duração dos processos** nó do relatório.

   ![process_duration_node](assets/process_duration_node.png)

   Ao selecionar um relatório, a variável **Parâmetros do relatório** é exibido à direita da visualização em árvore.

   ![painel de parâmetros de relatório de processos de execução longa](assets/process_duration_params.png)

   Parâmetros:

   * **Selecionar processo** (*mandatory*): Selecione um processo do AEM Forms.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido na **Relatório** painel à direita da janela Relatório de Processos.

   ![process_duration_report](assets/process_duration_report.png)

   Use as opções no canto superior direito do **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor da legenda**: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas

## Relatório de volume de fluxo de trabalho {#workflow-volume-report}

O relatório de Volume de fluxo de trabalho exibe o número de instâncias em execução e concluídas no momento de um processo do AEM Forms por dia do calendário.

### Para executar um relatório de Volume de fluxo de trabalho {#to-execute-a-workflow-volume-report-br}

1. Para exibir os relatórios predefinidos no Relatório do Processo, no **Relatório de processos** exibição em árvore, clique no botão **Relatórios** nó .
1. Clique no botão **Volume do fluxo de trabalho** nó do relatório.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Ao selecionar um relatório, a variável **Parâmetros do relatório** é exibido à direita da visualização em árvore.

   ![painel de parâmetros de relatório de processos de execução longa](assets/workflow_volume_params.png)

   Parâmetros:

   * **Selecionar processo**(*mandatory*): Selecione um processo do AEM Forms.
   * **Iniciado após** (*opcional*): Selecione uma data. Filtra o relatório para exibir instâncias de processo que começaram após a data especificada.
   * **Iniciado antes** (*opcional*): Selecione uma data. Filtra o relatório para exibir instâncias de processo que iniciaram antes da data especificada.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido na **Relatório** à direita do **Relatório de processos** janela.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Use as opções no canto superior direito do **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor da legenda**: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas
