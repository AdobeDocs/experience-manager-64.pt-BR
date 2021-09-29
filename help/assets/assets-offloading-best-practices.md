---
title: Práticas recomendadas de descarregamento de ativos
description: Casos de uso recomendados e práticas recomendadas para descarregar a assimilação de ativos e workflows de replicação no  [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 3ecc8988-add1-47d5-80b4-984beb4d8dab
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---

# Práticas recomendadas de descarregamento de ativos {#assets-offloading-best-practices}

>[!WARNING]
>
>Este recurso está obsoleto [!DNL Experience Manager] 6.4 em diante e é removido em [!DNL Experience Manager] 6.5. Planeje de acordo.

O manuseio de arquivos grandes e a execução de fluxos de trabalho no Adobe Experience Manager Assets podem consumir recursos consideráveis de CPU, memória e E/S. Especificamente, o tamanho dos ativos, os fluxos de trabalho, o número de usuários e a frequência da assimilação de ativos podem afetar o desempenho geral do sistema. As operações com mais recursos incluem a assimilação de ativos e os workflows de replicação. O uso intenso desses workflows em uma única instância de criação pode afetar negativamente a eficiência da criação.

Descarregar essas tarefas em instâncias dedicadas de trabalho pode reduzir os custos indiretos de CPU, memória e E/S. Em geral, a ideia por trás da descarga é distribuir tarefas que consomem recursos intensivos de CPU/Memória/E para instâncias de trabalho dedicadas. As seções a seguir incluem casos de uso recomendados para descarregamento de Ativos.

## [!DNL Experience Manager Assets] Descarregamento {#aem-assets-offloading}

[!DNL Experience Manager] Os ativos implementam uma extensão de fluxo de trabalho específica de ativo nativo para descarregamento. Ele se baseia na extensão de fluxo de trabalho genérica fornecida pela estrutura de descarregamento, mas inclui recursos adicionais específicos de ativos na implementação. O objetivo da descarga de Ativos é executar com eficiência o fluxo de trabalho do Ativo de atualização DAM em um ativo carregado. O descarregamento de ativos permite obter mais controle dos workflows de assimilação.

## [!DNL Experience Manager] Componentes de descarregamento de ativos {#aem-assets-offloading-components}

O diagrama a seguir descreve os componentes principais no processo de descarregamento de ativos:

![chlimage_1-55](assets/chlimage_1-55.png)

### Fluxo de trabalho de Descarregamento de ativo de atualização DAM {#dam-update-asset-offloading-workflow}

O fluxo de trabalho DAM Update Asset Offloading é executado no servidor principal (autor) no qual o usuário faz upload dos ativos. Esse workflow é acionado por um iniciador regular do workflow. Em vez de processar o ativo carregado, esse workflow de descarregamento cria um novo trabalho, usando o tópico *com/adobe/granite/workflow/offloading*. O workflow de descarregamento adiciona o nome do workflow de destino - o fluxo de trabalho do Ativo de atualização DAM , neste caso, e o caminho do ativo para a carga da tarefa. Depois de criar o trabalho de descarregamento, o workflow de descarregamento na instância primária aguarda até que o trabalho de descarregamento tenha sido executado.

### Gerente de emprego {#job-manager}

O gerenciador de tarefas distribui novos trabalhos para instâncias de trabalho. Ao projetar o mecanismo de distribuição, é importante levar a ativação do tópico em consideração. As tarefas só podem ser atribuídas a instâncias em que o tópico da tarefa está ativado. Desative o tópico `com/adobe/granite/workflow/offloading` no principal e ative-o no trabalhador para garantir que o trabalho seja atribuído ao trabalhador.

### [!DNL Experience Manager] descarregamento {#aem-offloading}

A estrutura de descarregamento identifica tarefas de descarregamento de workflow atribuídas a instâncias de trabalhador e usa replicação para transportá-las fisicamente, incluindo sua carga útil (por exemplo, imagens a serem assimiladas), para trabalhadores.

### Descarga de trabalho consumidor {#workflow-offloading-job-consumer}

Depois que um trabalho é gravado no trabalhador, o gerenciador de trabalhos chama o consumidor do trabalho responsável pelo tópico *com/adobe/granite/workflow/offloading*. O consumidor de trabalho executa então o fluxo de trabalho Ativo de atualização do DAM no ativo.

## Topologia do Sling {#sling-topology}

A topologia Sling agrupa [!DNL Experience Manager] instâncias e permite que elas estejam cientes umas das outras, independentemente da persistência subjacente. Essa característica da topologia Sling permite criar topologias para cenários não clusterizados, clusterizados e mistos. Uma instância pode expor propriedades à topologia inteira. A estrutura fornece retornos de chamada para acompanhar as alterações na topologia (instâncias e propriedades). A topologia Sling fornece a base para trabalhos distribuídos Sling.

### Sling trabalhos distribuídos {#sling-distributed-jobs}

Os trabalhos distribuídos do Sling facilitam a distribuição de tarefas entre um conjunto de instâncias que são membros da topologia. Os trabalhos do Sling são baseados na ideia de capacidades. Uma tarefa é definida por seu tópico de trabalho. Para executar um trabalho, uma instância deve fornecer um consumidor de trabalho para um tópico de trabalho específico. O tópico da tarefa é o principal driver do mecanismo de distribuição.

Os trabalhos são distribuídos somente para instâncias que fornecem um consumidor de trabalho para o tópico. Ao ativar/desativar os consumidores de trabalho em uma instância, você pode definir os recursos de uma instância e influenciar o mecanismo de distribuição. Os consumidores de trabalho disponíveis de uma instância são transmitidos para toda a topologia.

Nesse contexto, o termo distribuição significa atribuição de uma tarefa a uma instância específica que fornece um consumidor de trabalho. A atribuição a uma instância é armazenada no repositório. Em outras palavras, os trabalhos distribuídos do Sling podem ser atribuídos a qualquer instância na topologia por padrão. No entanto, outras tarefas só podem ser executadas por instâncias que compartilham o mesmo repositório. Isso implica que esses trabalhos só podem ser executados por instâncias que fazem parte do mesmo cluster. Os trabalhos atribuídos a instâncias de um cluster diferente não são executados.

### Estrutura de descarregamento do Granite {#granite-offloading-framework}

A estrutura de descarregamento do Granite complementa a distribuição de trabalhos do Sling para executar tarefas atribuídas a instâncias sem cluster. Ele não executa nenhuma distribuição (atribuição de instância). No entanto, identifica trabalhos do Sling que foram distribuídos para instâncias não clusterizadas e os transporta para a instância de destino para execução. Atualmente, o descarregamento usa a replicação para executar esse transporte de trabalho. Para executar um trabalho, a descarga define a entrada e a saída, que são combinadas com a tarefa para criar a carga útil do trabalho.

Os trabalhos distribuídos do Sling fornecem a estrutura de trabalho e distribuição. A descarga de granulito só atende ao transporte no caso especial em que os trabalhos são distribuídos em instâncias sem cluster.

Além do transporte, a estrutura de descarregamento fornece uma extensão para o mecanismo de workflow. Ela permite que a estrutura crie trabalhos distribuídos como parte de um workflow e aguarde a conclusão, antes que o workflow avance. Ele é implementado usando a API de etapa externa do fluxo de trabalho do mecanismo de fluxo de trabalho. Uma das extensões facilita a distribuição genérica de workflows. Não há suporte para a distribuição de etapas de fluxo de trabalho único.

A estrutura de descarregamento também vem com uma interface do usuário (UI) para visualizar e controlar a ativação do tópico da tarefa em toda a topologia. A interface do usuário permite configurar convenientemente o tópico que ativa os trabalhos distribuídos do Sling. Você também pode configurar a descarga sem a interface do usuário.

## Orientação geral e práticas recomendadas para descarregamento de ativos {#general-guidance-and-best-practices-for-asset-offloading}

Cada implementação é exclusiva e, como tal, não há configuração de descarregamento de tamanho único para todos. As seções a seguir fornecem orientação e práticas recomendadas para a descarga da ingestão de ativos.

A descarga de ativos também impõe despesas gerais no sistema, incluindo despesas gerais de operação. Se encontrar problemas com a carga de ingestão do ativo, o Adobe recomenda que você primeiro melhore a configuração sem descarregar. Considere as seguintes opções antes de migrar para o descarregamento de ativos:

* Expandir hardware
* Otimizar workflows
* Usar fluxos de trabalho transitórios
* Limite o número de núcleos usados para workflows

Se você concluir que a descarga de ativos é uma abordagem apropriada para você, o Adobe fornece as seguintes orientações:

* É recomendada uma implantação baseada em TarMK
* O descarregamento de ativos com base em TarMK não foi projetado para dimensionamento horizontal abrangente
* Garantir que o desempenho da rede entre o autor e os trabalhadores seja satisfatório

### Implantação recomendada de descarregamento de ativos {#recommended-assets-offloading-deployment}

Com [!DNL Experience Manager] e Oak, há vários cenários de implantação possíveis. Para descarregamento de Ativos, recomenda-se uma implantação baseada em TarMK com um armazenamento de dados compartilhado. O diagrama a seguir descreve a implantação recomendada:

![chlimage_1-56](assets/chlimage_1-56.png)

Para obter detalhes sobre como configurar um armazenamento de dados, consulte [Configurar armazenamentos de nó e armazenamentos de dados em AEM](../sites-deploying/data-store-config.md).

### Desativar o gerenciamento automático de agentes {#turning-off-automatic-agent-management}

O Adobe recomenda desativar o gerenciamento automático de agentes porque ele não oferece suporte à replicação sem binários e pode causar confusão ao configurar uma nova topologia de descarregamento. Além disso, ele não suporta automaticamente o fluxo de replicação de encaminhamento necessário para a replicação sem binários.

1. Abra o Configuration Manager a partir do URL `http://localhost:4502/system/console/configMgr`.
1. Abra a configuração para `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Desative o gerenciamento automático de agentes.

### Uso da replicação de encaminhamento {#using-forward-replication}

Por padrão, o descarregamento do transporte usa a replicação reversa para retornar os ativos descarregados do trabalhador para o principal. Os agentes de replicação inversa não suportam replicação sem binários. Você deve configurar a descarga para usar a replicação direta para empurrar os ativos descarregados de um trabalhador para o principal.

1. Se você estiver migrando da configuração padrão usando replicação inversa, desative ou exclua todos os agentes chamados &quot; `offloading_outbox`&quot; e &quot; `offloading_reverse_*`&quot; no primário e no trabalhador, onde &amp;ast; representa o Sling id da instância de destino.
1. Em cada trabalhador, crie um novo agente de replicação de encaminhamento apontando para o principal. O procedimento é o mesmo que criar agentes de encaminhamento do primário para o trabalhador. Consulte [Criação de agentes de replicação para descarregamento](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) para obter instruções sobre como configurar agentes de replicação de descarregamento.
1. Abra a configuração para `OffloadingDefaultTransporter` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Altere o valor da propriedade `default.transport.agent-to-master.prefix` de `offloading_reverse` para `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Uso do armazenamento de dados compartilhado e da replicação sem binários entre autor e trabalhadores  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

Recomenda-se o uso de replicação sem binários para reduzir a sobrecarga de transporte para descarregamento de ativos. Para saber como configurar a replicação sem binários para um armazenamento de dados compartilhado, consulte [Configuração de armazenamentos de nó e armazenamento de dados em AEM](/help/sites-deploying/data-store-config.md). O procedimento não é diferente para descarregamento de Ativos, exceto que envolve outros agentes de replicação. Como a replicação sem binário só funciona com agentes de replicação de encaminhamento, você também deve usar a replicação de encaminhamento para todos os agentes de descarregamento.

### Desativação de pacotes de transporte {#turning-off-transport-packages}

Por padrão, a descarga cria um pacote de conteúdo que contém o trabalho de descarregamento e a carga útil do trabalho (o ativo original) e transporta esse único pacote de descarregamento usando uma única solicitação de replicação. A criação desses pacotes de descarregamento é contraproducente ao usar a replicação sem binário, pois os binários são serializados no pacote novamente ao criar o pacote. O uso desses pacotes de transporte pode ser desativado, o que faz com que o trabalho de descarregamento e a carga sejam transportados em várias solicitações de replicação, uma para cada entrada de carga. Dessa forma, os benefícios da replicação sem binário podem ser utilizados.

1. Abra a configuração do componente *OffloadingDefaultTransporter* em [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Desative a propriedade *Pacote de Replicação (default.transport.contentpackage)*.

### Desabilitação do modelo de transporte de workflow {#disabling-the-transport-of-workflow-model}

Por padrão, o workflow de descarregamento *DAM Update Asset Offloading* adiciona o modelo de fluxo de trabalho para chamar o trabalhador no payload do trabalho. Como esse workflow segue o modelo pronto para uso *Ativo de atualização do DAM* por padrão, essa carga adicional pode ser removida.

Se o modelo de fluxo de trabalho estiver desativado na carga útil da tarefa, certifique-se de distribuir as alterações para o modelo de fluxo de trabalho referenciado usando outras ferramentas, como o gerenciador de pacotes.

Para desabilitar o transporte do modelo de fluxo de trabalho, modifique o fluxo de trabalho Descarregamento de ativo de atualização do DAM .

1. Abra o console de workflow a partir de [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Abra a guia Modelos .
1. Abra o modelo de fluxo de trabalho Atualizar descarregamento de ativo do DAM .
1. Abra as propriedades da etapa para a etapa Descarregamento do fluxo de trabalho do DAM .
1. Abra a guia Argumentos e desmarque as opções Adicionar modelo à entrada e Adicionar modelo à saída .
1. Salve as alterações no modelo.

### Otimização do intervalo de pesquisa {#optimizing-the-polling-interval}

A descarregamento do workflow é implementada usando um workflow externo no principal, que pesquisa a conclusão do workflow descarregado no trabalhador. O intervalo de sondagem padrão para os processos de workflow externos é de cinco segundos. O Adobe recomenda que você aumente o intervalo de sondagem da etapa Descarga de ativos para pelo menos 15 segundos para reduzir a sobrecarga de descarga no principal.

1. Abra o console de workflow a partir de [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Abra a guia Modelos .
1. Abra o modelo de fluxo de trabalho Atualizar descarregamento de ativo do DAM .
1. Abra as propriedades da etapa para a etapa Descarregamento do fluxo de trabalho do DAM .
1. Abra a guia Commons e ajuste o valor da propriedade Period .
1. Salve as alterações no modelo.

## Mais recursos {#more-resources}

Este documento foca na descarga de ativos. Esta é uma documentação adicional sobre descarregamento:

* [Descarregamento de Tarefas](/help/sites-deploying/offloading.md)
* [Descarregamento do fluxo de trabalho de ativos](/help/sites-administering/workflow-offloader.md)
