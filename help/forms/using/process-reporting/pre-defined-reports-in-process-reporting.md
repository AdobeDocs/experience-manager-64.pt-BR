---
title: Relatórios predefinidos no Relatórios em andamento
seo-title: Relatórios predefinidos no Relatórios em andamento
description: Query para dados de processo do AEM Forms em JEE para criar relatórios em processos de execução longa, duração do processo e volume do fluxo de trabalho
seo-description: Query para dados de processo do AEM Forms em JEE para criar relatórios em processos de execução longa, duração do processo e volume do fluxo de trabalho
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Relatórios predefinidos no Relatórios em andamento {#pre-defined-reports-in-process-reporting}

O Relatórios do AEM Forms Process é fornecido com os seguintes relatórios *prontos para uso* :

* **[Processos](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**de longa duração: Um relatório de todos os processos da AEM Forms que levaram mais de um tempo para serem concluídos

* **[Gráfico](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**de Duração do Processo: Um relatório de um processo AEM Forms especificado por duração

* **[Volume](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**do fluxo de trabalho: Um relatório das instâncias em execução e concluídas do processo especificado por data

## Processos de longa execução {#long-running-processes}

O relatório de Processos de longa execução exibe os processos do AEM Forms que levaram mais de um tempo para serem concluídos.

### Para executar um relatório de Processo Longo de Execução {#to-execute-a-long-running-process-report-br}

1. Para visualização da lista de relatórios predefinidos no Process Relatórios, na visualização em árvore do Relatórios **** Process, clique no nó **Reports** .
1. Clique no nó do relatório Processos **de Execução** Longa.

   ![long_running_node](assets/long_running_node.png)

   Quando você seleciona um relatório, o painel Parâmetros **de** relatório é exibido à direita da visualização em árvore.

   ![painel de parâmetros do relatório de processos longos](assets/report_parameters_panel.png)

   Parâmetros:

   * **Duração**(*obrigatório*): Especifique uma duração e uma unidade de tempo. Exibe todos os processos do AEM Forms que foram executados por mais de uma duração especificada.
   * **Iniciado após** (*opcional*): Selecione uma data. Filtre o relatório para exibir instâncias de processo que começaram após a data especificada.
   * **Iniciado antes** (*opcional*): Selecione uma data. Filtre o relatório para exibir as instâncias de processo iniciadas antes da data especificada.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido no painel **Relatório** à direita da janela **Processar Relatórios** .

   ![long_running_process](assets/long_running_processes.png)

   Use as opções no canto superior direito do painel **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor** da legenda: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas

## Relatório de duração do processo {#process-duration-report-br}

O relatório Duração do processo exibe o número de instâncias de um processo do Forms por número de dias que cada instância executou.

### Para executar um relatório de Duração do processo {#to-execute-a-process-duration-report-br}

1. Para visualização dos relatórios predefinidos no Relatórios Process, na visualização em árvore do Relatórios **** Process, clique no nó **Reports** .
1. Clique no nó do relatório Duração **** dos processos.

   ![process_duration_node](assets/process_duration_node.png)

   Quando você seleciona um relatório, o painel Parâmetros **de** relatório é exibido à direita da visualização em árvore.

   ![painel de parâmetros do relatório de processos longos](assets/process_duration_params.png)

   Parâmetros:

   * **Selecionar Processo** (*obrigatório*): Selecione um processo AEM Forms.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido no painel **Relatório** à direita da janela Processar Relatórios.

   ![process_duration_report](assets/process_duration_report.png)

   Use as opções no canto superior direito do painel **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor** da legenda: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas

## Relatório de volume do fluxo de trabalho {#workflow-volume-report}

O relatório de Volume do fluxo de trabalho exibe o número de instâncias atualmente em execução e concluídas de um processo AEM Forms por dia de calendário.

### Para executar um relatório de Volume do fluxo de trabalho {#to-execute-a-workflow-volume-report-br}

1. Para visualização dos relatórios predefinidos no Relatórios Process, na visualização em árvore do Relatórios **** Process, clique no nó **Reports** .
1. Clique no nó do relatório Volume **do** fluxo de trabalho.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Quando você seleciona um relatório, o painel Parâmetros **de** relatório é exibido à direita da visualização em árvore.

   ![painel de parâmetros do relatório de processos longos](assets/workflow_volume_params.png)

   Parâmetros:

   * **Selecione Processo**(*obrigatório*): Selecione um processo AEM Forms.
   * **Iniciado após** (*opcional*): Selecione uma data. Filtros o relatório para exibir instâncias de processo que foram iniciadas após a data especificada.
   * **Iniciado antes** (*opcional*): Selecione uma data. Filtros o relatório para exibir instâncias de processo iniciadas antes da data especificada.

1. Clique em **Ir** para executar o relatório.

   O relatório é exibido no painel **Relatório** à direita da janela **Processar Relatórios** .

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Use as opções no canto superior direito do painel **Relatório** para executar as seguintes operações no relatório.

   * **Atualizar**: Atualiza o relatório com os dados mais recentes no armazenamento
   * **Alterar cor** da legenda: Selecionar e alterar a cor da legenda do relatório
   * **Exportar para CSV**: Exportar e baixar os dados do relatório para um arquivo separado por vírgulas

