---
title: Práticas recomendadas de descarregamento de ativos
description: Casos de uso recomendados e práticas recomendadas para descarregar a ingestão de ativos e workflows de replicação no AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# Práticas recomendadas de descarregamento de ativos {#assets-offloading-best-practices}

>[!WARNING]
>
>Este recurso foi descontinuado AEM 6.4 e foi removido no AEM 6.5. Planeje de acordo.

Manusear arquivos grandes e executar workflows nos ativos Adobe Experience Manager (AEM) pode consumir recursos consideráveis de CPU, memória e E/S. Em particular, a dimensão dos ativos, os workflows, o número de usuários e a frequência de ingestão dos ativos podem afetar o desempenho geral do sistema. As operações mais intensivas em recursos incluem AEM ingestão de ativos e workflows de replicação. O uso intensivo desses workflows em uma única instância de criação de AEM pode afetar negativamente a eficiência da criação.

Descarregar essas tarefas para instâncias de trabalho dedicadas pode reduzir as despesas gerais de CPU, memória e E/S. Em geral, a ideia por trás da descarga é distribuir tarefas que consomem recursos intensivos de CPU/Memória/E para instâncias de trabalho dedicadas. As seções a seguir incluem casos de uso recomendados para descarregamento de Ativos.

## Descarregamento do AEM Assets {#aem-assets-offloading}

A AEM Assets implementa uma extensão de fluxo de trabalho nativa específica do ativo para descarregamento. Ele se baseia na extensão de fluxo de trabalho genérica fornecida pela estrutura de descarga, mas inclui recursos adicionais específicos de ativos na implementação. O objetivo da descarga de Ativos é executar com eficiência o fluxo de trabalho Atualizar ativo DAM em um ativo carregado. A descarga de ativos permite que você tenha maior controle dos workflows de ingestão.

## Componentes de descarga AEM Assets {#aem-assets-offloading-components}

O diagrama a seguir descreve os componentes principais no processo de descarga de ativos:

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM Update Asset Offloading workflow {#dam-update-asset-offloading-workflow}

O fluxo de trabalho de Descarregamento de ativos de atualização do DAM é executado no servidor principal (autor) no qual o usuário carrega os ativos. Esse fluxo de trabalho é acionado por um inicializador de fluxo de trabalho regular. Em vez de processar o ativo carregado, esse fluxo de trabalho de descarregamento cria um novo trabalho, usando o tópico *com/adobe/granite/workflow/offloading*. O fluxo de trabalho de descarregamento adiciona o nome do fluxo de trabalho do público alvo - o fluxo de trabalho de Atualizar ativo DAM nesse caso e o caminho do ativo para a carga do trabalho. Depois de criar a tarefa de descarregamento, o fluxo de trabalho de descarregamento na instância principal aguarda até que a tarefa de descarregamento seja executada.

### Gerente de emprego {#job-manager}

O gerenciador de trabalhos distribui novos trabalhos para instâncias de trabalho. Ao projetar o mecanismo de distribuição, é importante levar a ativação do tópico em consideração. Os trabalhos só podem ser atribuídos a instâncias nas quais o tópico da tarefa está ativado. Desative o tópico `com/adobe/granite/workflow/offloading` no principal e ative-o no trabalhador para garantir que o trabalho seja atribuído ao trabalhador.

### Descarga de AEM {#aem-offloading}

A estrutura de descarga identifica os trabalhos de descarga de fluxo de trabalho atribuídos às instâncias do trabalhador e usa a replicação para transportá-los fisicamente, incluindo sua carga útil (por exemplo, imagens a serem assimiladas), aos trabalhadores.

### Consumidor de trabalho de descarregamento de fluxo de trabalho {#workflow-offloading-job-consumer}

Quando um trabalho é gravado no trabalhador, o gerente de trabalho chama o consumidor de trabalho responsável pelo tópico *com/adobe/granite/workflow/offloading* . O consumidor do trabalho executa o fluxo de trabalho Atualizar ativo DAM no ativo.

## Topologia Sling {#sling-topology}

A topologia Sling agrupa instâncias AEM e permite que elas estejam cientes umas das outras, independentemente da persistência subjacente. Essa característica da topologia Sling permite criar topologias para cenários não agrupados, agrupados e mistos. Uma instância pode expor as propriedades à topologia inteira. A estrutura fornece retornos de chamada para acompanhar as alterações na topologia (instâncias e propriedades). A topologia Sling fornece a base para trabalhos distribuídos Sling.

### Sling de trabalhos distribuídos {#sling-distributed-jobs}

A divisão de tarefas distribuídas facilita a distribuição de tarefas entre um conjunto de instâncias que são membros da topologia. Trabalhos de sling são baseados na ideia de capacidades. Um trabalho é definido pelo seu tópico de trabalho. Para executar um trabalho, uma instância deve fornecer um consumidor de trabalho para um tópico de trabalho específico. O tópico da tarefa é o principal impulsionador do mecanismo de distribuição.

Os trabalhos são distribuídos somente para instâncias que fornecem um consumidor de trabalho para o tópico. Ao ativar/desativar os consumidores de trabalho em uma instância, você pode definir os recursos de uma instância e influenciar o mecanismo de distribuição. Os consumidores de trabalho disponíveis de uma instância são transmitidos para toda a topologia.

Neste contexto, o termo distribuição significa a atribuição de uma tarefa a uma instância específica que fornece um consumidor de trabalho. A atribuição a uma instância é armazenada no repositório. Em outras palavras, os trabalhos distribuídos Sling podem ser atribuídos a qualquer instância na topologia por padrão. No entanto, outros trabalhos só podem ser executados por instâncias que compartilham o mesmo repositório. Isso implica que esses trabalhos só podem ser executados por instâncias que fazem parte do mesmo cluster. Os trabalhos atribuídos a instâncias de um cluster diferente não são executados.

### Granite offloading framework {#granite-offloading-framework}

A estrutura de descarga de Granite complementa a distribuição de trabalhos Sling para executar ordens de produção atribuídas a instâncias não agrupadas. Não executa nenhuma distribuição (atribuição de instância). No entanto, identifica os trabalhos Sling que foram distribuídos para instâncias não clusterizadas e os transporta para a instância do público alvo para execução. Atualmente, a descarga usa a replicação para executar esse transporte de trabalho. Para executar uma tarefa, a descarga define a entrada e a saída, que são então combinadas com a tarefa para criar a carga da tarefa.

A venda de trabalhos distribuídos fornece a estrutura de trabalho e distribuição. A descarga de granito só cuida do transporte para o caso especial em que os empregos são distribuídos para instâncias não agrupadas.

Além do transporte, o quadro de descarga fornece uma extensão para o motor de workflow. Permite que a estrutura crie trabalhos distribuídos como parte de um fluxo de trabalho e aguarde sua conclusão, antes que o fluxo de trabalho avance. Ela é implementada usando a API de etapa externa do fluxo de trabalho do motor de workflow. Uma das extensões facilita a distribuição genérica de workflows. Não há suporte para a distribuição de etapas únicas do fluxo de trabalho.

A estrutura de descarga também vem com uma interface do usuário (UI) para visualizar e controlar a ativação do tópico de trabalho em toda a topologia. A interface do usuário permite que você configure convenientemente o tópico ativado dos trabalhos distribuídos Sling. Você também pode configurar a descarga sem a interface do usuário.

## Orientação geral e práticas recomendadas para a descarga de ativos {#general-guidance-and-best-practices-for-asset-offloading}

Toda implementação é exclusiva e, como tal, não há configuração de descarga de tamanho único para todos. As seções a seguir fornecem orientação e práticas recomendadas para a descarga de ingestão de ativos.

A descarga de ativos também impõe despesas gerais ao sistema, incluindo despesas gerais de operação. Se você encontrar problemas com a carga de ingestão do ativo, o Adobe recomenda que você primeiro aprimore a configuração sem descarregar. Considere as seguintes opções antes de mover para a descarga de ativos:

* Dimensionar hardware
* Otimizar workflows
* Usar workflows transitórios
* Limitar o número de núcleos usados para workflows

Se você concluir que a descarga de ativos é uma abordagem apropriada para você, o Adobe fornece as seguintes orientações:

* Recomenda-se uma implantação com base em TarMK
* A descarga de ativos baseados em TarMK não foi projetada para ampliar a escala horizontal
* Verifique se o desempenho da rede entre o autor e os trabalhadores é satisfatório

### Implantação de descarregamento de ativos recomendados {#recommended-assets-offloading-deployment}

Com AEM e Oak, há vários cenários de implantação possíveis. Para descarregamento de Ativos, recomenda-se uma implantação com base em TarMK com um armazenamento de dados compartilhado. O diagrama a seguir descreve a implantação recomendada:

![chlimage_1-56](assets/chlimage_1-56.png)

Para obter detalhes sobre como configurar um armazenamento de dados, consulte [Configuração de armazenamentos de nós e armazenamentos de dados em AEM](../sites-deploying/data-store-config.md).

### Desativação do gerenciamento automático de agentes {#turning-off-automatic-agent-management}

O Adobe recomenda desativar o gerenciamento automático de agentes, pois ele não oferece suporte à replicação sem binários e pode causar confusão ao configurar uma nova topologia de descarga. Além disso, ele não suporta automaticamente o fluxo de replicação de encaminhamento necessário para a replicação sem binários.

1. Abra o Configuration Manager a partir do URL `http://localhost:4502/system/console/configMgr`.
1. Abra a configuração para `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Desative o gerenciamento automático de agentes.

### Uso da replicação avançada {#using-forward-replication}

Por padrão, a descarga de transporte usa replicação reversa para retornar os ativos descarregados do trabalhador para o principal. Os agentes de replicação reversa não suportam replicação sem binários. Você deve configurar o descarregamento para usar a replicação direta para retornar os ativos descarregados do trabalhador para o principal.

1. Se você estiver migrando da configuração padrão usando replicação reversa, desabilite ou exclua todos os agentes chamados &quot; `offloading_outbox`&quot; e &quot; `offloading_reverse_*`&quot; no primário e no trabalhador, onde &amp;ast; representa a ID Sling da instância do público alvo.
1. Em cada trabalhador, crie um novo agente de replicação de encaminhamento apontando para o principal. O procedimento é o mesmo que criar agentes encaminhados do primário ao trabalhador. Consulte [Criação de Agentes de Replicação para Descarregamento](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) para obter instruções sobre como configurar agentes de replicação de descarregamento.
1. Abra a configuração para `OffloadingDefaultTransporter` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Altere o valor da propriedade `default.transport.agent-to-master.prefix` de `offloading_reverse` para `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Uso de armazenamento de dados compartilhado e replicação sem binários entre o autor e os trabalhadores  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

O uso de replicação sem binários é recomendado para reduzir a sobrecarga de transporte para descarregamento de ativos. Para saber como configurar a replicação sem binários para um armazenamento de dados compartilhado, consulte [Configuração de armazenamento de nós e armazenamento de dados em AEM](/help/sites-deploying/data-store-config.md). O procedimento não é diferente para o descarregamento de Ativos, exceto que envolve outros agentes de replicação. Como a replicação sem binários só funciona com agentes de replicação de encaminhamento, você também deve usar a replicação de encaminhamento para todos os agentes de descarga.

### Desativação de pacotes de transporte {#turning-off-transport-packages}

Por padrão, a descarga cria um pacote de conteúdo que contém a tarefa de descarregamento e a carga da tarefa (o ativo original) e transporta esse único pacote de descarregamento usando uma única solicitação de replicação. A criação desses pacotes de descarga é contraproducente ao usar replicação sem binários, pois os binários são serializados no pacote novamente ao criar o pacote. O uso desses pacotes de transporte pode ser desativado, o que faz com que o trabalho de descarregamento e a carga sejam transportados em várias solicitações de replicação, uma para cada entrada de carga. Dessa forma, os benefícios da replicação sem binários podem ser utilizados.

1. Abra a configuração do componente de *OffloadingDefaultTransporter* em [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Desative a propriedade *Replication Package (default.transport.contentpackage)*.

### Desabilitar o transporte do modelo de fluxo de trabalho {#disabling-the-transport-of-workflow-model}

Por padrão, o fluxo de trabalho de descarga de ativos de atualização ** do DAM adiciona o modelo de fluxo de trabalho para chamar o trabalhador à carga da tarefa. Como esse fluxo de trabalho segue o modelo predefinido de Ativo *de atualização de* DAM, por padrão, essa carga adicional pode ser removida.

Se o modelo de fluxo de trabalho estiver desabilitado da carga do trabalho, certifique-se de distribuir as alterações para o modelo de fluxo de trabalho referenciado usando outras ferramentas, como o gerenciador de pacotes.

Para desativar o transporte do modelo de fluxo de trabalho, modifique o fluxo de trabalho de Descarregamento de ativos de atualização de DAM.

1. Abra o console de fluxo de trabalho em [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Abra a guia Modelos.
1. Abra o modelo de fluxo de trabalho Atualizar descarregamento de ativos do DAM.
1. Abra as propriedades da etapa de descarga do fluxo de trabalho do DAM.
1. Abra a guia Argumentos e desmarque as opções Adicionar modelo à entrada e Adicionar modelo à saída.
1. Salve as alterações no modelo.

### Otimização do intervalo de polling {#optimizing-the-polling-interval}

A descarga do fluxo de trabalho é implementada usando um fluxo de trabalho externo no principal, que pesquisa a conclusão do fluxo de trabalho descarregado no trabalhador. O intervalo de sondagem padrão para os processos de fluxo de trabalho externo é de cinco segundos. O Adobe recomenda que você aumente o intervalo de sondagem da etapa de descarga de Ativos para pelo menos 15 segundos para reduzir a sobrecarga de descarga no principal.

1. Abra o console de fluxo de trabalho em [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Abra a guia Modelos.
1. Abra o modelo de fluxo de trabalho Atualizar descarregamento de ativos do DAM.
1. Abra as propriedades da etapa para a etapa de descarga de fluxo de trabalho do DAM.
1. Abra a guia Comuns e ajuste o valor da propriedade Período.
1. Salve as alterações no modelo.

## Mais recursos {#more-resources}

Este documento foca na descarga de ativos. Esta é uma documentação adicional sobre descarga:

* [Descarregamento de tarefas](/help/sites-deploying/offloading.md)
* [Descarga do fluxo de trabalho de ativos](/help/sites-administering/workflow-offloader.md)

