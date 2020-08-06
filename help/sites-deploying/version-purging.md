---
title: Expurgação de versão
seo-title: Expurgação de versão
description: Este artigo descreve as opções disponíveis para a remoção de versão.
seo-description: Este artigo descreve as opções disponíveis para a remoção de versão.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
translation-type: tm+mt
source-git-commit: 0dced2f56fcebfb03fa6264e98cd686e8e7902c6
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---


# Expurgação de versão{#version-purging}

Em uma instalação padrão, o AEM cria uma nova versão de uma página ou nó quando você ativa uma página depois de atualizar o conteúdo.

>[!NOTE]
>
>Se nenhuma alteração de conteúdo for feita, você verá a mensagem informando que a página foi ativada, mas nenhuma nova versão será criada

Você pode criar versões adicionais mediante solicitação usando a guia **Controle de versão** do sidekick. Essas versões são armazenadas no repositório e podem ser restauradas se necessário.

Essas versões nunca são expurgadas, portanto, o tamanho do repositório crescerá com o tempo e, portanto, precisará ser gerenciado.

AEM é enviado com vários mecanismos para ajudá-lo a gerenciar seu repositório:

* o Gerenciador [de versões](#version-manager)

   Isso pode ser configurado para expurgar versões antigas quando novas versões forem criadas.

* a ferramenta [Expurgar versões](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   Isso é usado como parte do monitoramento e da manutenção do repositório.

   Ele permite que você intervenha para remover versões antigas de um nó, ou uma hierarquia de nós, de acordo com estes parâmetros:

   * O número máximo de versões a serem mantidas no repositório.

      Quando esse número é excedido, a versão mais antiga é removida.

   * A idade máxima de qualquer versão mantida no repositório.

      Quando a idade de uma versão exceder esse valor, ele será removido do repositório.

* a tarefa [de manutenção Expurgação da](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks)versão. Você pode agendar a tarefa de manutenção Expurgação da versão para excluir versões antigas automaticamente. Como resultado, isso minimiza a necessidade de usar manualmente as ferramentas de Expurgação de versão.

>[!CAUTION]
>
>Para otimizar o tamanho do repositório, execute a tarefa de expurgação da versão com frequência. A tarefa deve ser agendada fora do horário comercial quando houver uma quantidade limitada de tráfego.

## Gerenciador de versão {#version-manager}

Além da expurgação explícita por meio da ferramenta de expurgação, o Gerenciador de versões pode ser configurado para expurgar versões antigas quando novas versões são criadas.

Para configurar o Gerenciador de versões, crie uma configuração para:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

As opções disponíveis são as seguintes:

* `versionmanager.createVersionOnActivation` (Booleano, padrão: true)

   se é necessário criar uma versão quando as páginas são ativadas.

   Uma versão é criada, a menos que o agente de replicação esteja configurado para suprimir a criação de versões, o que é respeitado pelo Gerenciador de versões

   Uma versão só será criada se a ativação ocorrer em caminhos contidos em versionmanager.ivCaminhos (veja abaixo).

* `versionmanager.ivPaths` (String[], padrão: {&quot;/&quot;})

   caminhos nos quais as versões são criadas implicitamente na ativação se versionmanager.createVersionOnActivation for verdadeiro.

* `versionmanager.purgingEnabled` (Booleano, padrão: falso)

   se ativar a remoção quando novas versões forem criadas

* `versionmanager.purgePaths` (String[], padrão: {&quot;/content&quot;})

   em quais caminhos expurgar versões quando novas versões forem criadas.

* `versionmanager.maxAgeDays` (int, padrão: 30)

   ao expurgar, qualquer versão anterior a esse valor será removida. Se esse valor for menor que 1, a expurgação não será realizada com base na idade da versão

* `versionmanager.maxNumberVersions` (int, padrão 5)

   ao limpar, qualquer versão anterior à n-ª versão mais recente será removida. Se esse valor for menor que 1, a expurgação não será realizada com base no número de versões

* `versionmanager.minNumberVersions` (int, padrão 0)

   O número mínimo de versões a serem mantidas independentemente da idade. Se esse valor for definido como um valor menor que 1, nenhum número mínimo de versões será retido.

>[!NOTE]
>
>Não é recomendável manter um grande número de versões no repositório. Portanto, ao configurar a operação de expurgação da versão, tenha cuidado para não excluir muitas versões da expurgação; caso contrário, o tamanho do repositório não será otimizado corretamente. Se você mantiver um grande número de versões devido a um requisito comercial, entre em contato com o suporte da Adobe para encontrar formas alternativas de otimizar o tamanho do repositório.

### Combinando opções de retenção {#combining-retention-options}

As opções que definem como quais versões devem ser retidas ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`) podem ser combinadas, dependendo de seus requisitos.

Por exemplo, ao definir o número máximo de versões a serem retidas E a versão mais antiga a ser retida:

* Configuração:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Com:

   * 10 versões feitas nos últimos 60 dias
   * 3 dessas versões criadas nos últimos 30 dias

* Isso significa que:

   * As últimas três versões serão retidas

Por exemplo, ao definir o número máximo E mínimo de versões a serem retidas E a versão mais antiga a ser retida:

* Configuração:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Com:

   * 5 versões feitas há 60 dias

* Isso significa que:

   * 3 versões serão retidas

## Ferramenta Expurgar Versões {#purge-versions-tool}

A ferramenta [Expurgar Versões](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) destina-se a expurgar as versões de um nó ou uma hierarquia de nós no repositório. Seu objetivo principal é ajudar a reduzir o tamanho do repositório, removendo versões antigas de seus nós.
