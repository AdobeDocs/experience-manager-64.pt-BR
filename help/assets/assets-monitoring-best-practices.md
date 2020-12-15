---
title: Práticas recomendadas de monitoramento de ativos
description: Práticas recomendadas para monitorar o ambiente e o desempenho da instância AEM após sua implantação.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c407cecf4f4de9aa00ba987f96df3c75784e0171
workflow-type: tm+mt
source-wordcount: '1765'
ht-degree: 0%

---


# Práticas recomendadas de monitoramento de ativos {#assets-monitoring-best-practices}

Do ponto de vista dos Ativos Adobe Experience Manager (AEM), o monitoramento deve incluir a observação e o relatórios dos seguintes processos e tecnologias:

* CPU do sistema
* Uso da memória do sistema
* Tempo de espera de E/S e E/S do disco do sistema
* E/S de rede do sistema
* MBeans JMX para:

   * Utilização de pilha
   * Processos assíncronos, como workflows

* Verificações de integridade do console OSGi

Normalmente, o AEM Assets pode ser monitorado de duas formas, monitoramento ao vivo e monitoramento de longo prazo.

## Monitoramento ao vivo {#live-monitoring}

Você deve executar monitoração ao vivo durante a fase de teste de desempenho do seu desenvolvimento ou durante situações de alta carga para entender as características de desempenho do seu ambiente. Normalmente, a monitoração ao vivo deve ser realizada usando um conjunto de ferramentas. Estas são algumas recomendações:

* [VM](https://visualvm.github.io/) visual: A VM visual permite que você visualização informações detalhadas da VM Java, incluindo o uso da CPU e da memória Java. Além disso, permite que você faça uma amostra e avalie o código que é executado em uma instância.
* [Parte superior](http://man7.org/linux/man-pages/man1/top.1.html): Parte superior é um comando Linux que abre um painel, que exibe as estatísticas de uso, incluindo CPU, memória e uso de E/S. Ele fornece uma visão geral de alto nível do que está acontecendo em uma instância.
* [Acima](https://hisham.hm/htop/): Htop é um visualizador de processo interativo. Ele fornece uso detalhado da CPU e da memória além do que o Top pode fornecer. O Htop pode ser instalado na maioria dos sistemas Linux usando `yum install htop` ou `apt-get install htop`.

* [Iotop](http://guichaz.free.fr/iotop/): O Iotop é um painel detalhado para uso de E/S de disco. Ele exibe barras e medidores que mostram os processos que usam E/S de disco e a quantidade que eles usam. O Iotop pode ser instalado na maioria dos sistemas Linux usando `yum install iotop` ou `apt-get install iotop`.

* [Iftop](http://www.ex-parrot.com/pdw/iftop/): O Iftop exibe informações detalhadas sobre o uso da rede/Ethernet. O Iftop exibe as estatísticas por canal de comunicação nas entidades que usam a Ethernet e a quantidade de largura de banda que usam. O Iftop pode ser instalado na maioria dos sistemas Linux usando `yum install iftop` ou `apt-get install iftop`.

* Gravador de Voo Java (JFR): Uma ferramenta comercial da Oracle que você pode usar livremente em ambientes que não sejam de produção. Para obter mais detalhes, consulte [Como usar o Gravador de voo Java para diagnosticar problemas de tempo de execução do CQ](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq).
* AEM arquivo error.log: Você pode investigar o arquivo error.log AEM para obter detalhes dos erros registrados no sistema. Use o comando `tail -F quickstart/logs/error.log` para identificar os erros que devem ser investigados.
* [Console](../sites-administering/workflows.md) de fluxo de trabalho: Aproveite o console de fluxo de trabalho para monitorar workflows que ficam atrás ou travam.

Normalmente, você usa essas ferramentas em conjunto para obter uma ideia abrangente sobre o desempenho da sua instância de AEM.

>[!NOTE]
>
>Essas ferramentas são ferramentas padrão e não são suportadas diretamente pelo Adobe. Eles não exigem licenças adicionais.

![chlimage_1-142](assets/chlimage_1-142.png) ![chlimage_1-143](assets/chlimage_1-143.png)

## Monitoramento de longo prazo {#long-term-monitoring}

A monitorização a longo prazo de uma instância AEM envolve a monitorização, por um período mais longo, das mesmas partes que são monitorizadas ao vivo. Também inclui a definição de alertas específicos para o seu ambiente.

### Agregação e relatórios de registro {#log-aggregation-and-reporting}

Há várias ferramentas disponíveis para registros de agregações, por exemplo Splunk(TM) e Elastic Search/Logstash/Kabana (ELK). Para avaliar o tempo de atividade da instância de AEM, é importante que você entenda eventos de log específicos do seu sistema e crie alertas com base neles. Um bom conhecimento de suas práticas de desenvolvimento e operações pode ajudá-lo a entender melhor como ajustar seu processo de agregação de log para gerar alertas críticos.

### Monitoramento de ambientes {#environment-monitoring}

A monitorização dos ambientes inclui a monitorização dos seguintes elementos:

* Saída de rede
* E/S de disco
* Memória
* Utilização da CPU
* MBeans JMX
* Sites externos

Você precisa de ferramentas externas, como NewRelic(TM) e AppDynamics(TM) para monitorar cada item. Usando essas ferramentas, você pode definir alertas específicos ao seu sistema, por exemplo, alta utilização do sistema, backup do fluxo de trabalho, falhas na verificação de integridade ou acesso não autenticado ao seu site. O Adobe não recomenda nenhuma ferramenta específica sobre outras. Encontre a ferramenta que funciona para você e aproveite-a para monitorar os itens discutidos.

#### Monitoramento interno de aplicativos {#internal-application-monitoring}

O monitoramento interno do aplicativo inclui o monitoramento dos componentes do aplicativo que compõem a pilha de AEM, incluindo JVM, o repositório de conteúdo e o monitoramento por meio do código personalizado do aplicativo criado na plataforma. Em geral, ele é executado por meio de JMX Mbeans que podem ser monitorados diretamente por várias soluções de monitoramento populares, como SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) e outras. Para sistemas que não suportam uma conexão direta com o JMX, você pode gravar scripts de shell para extrair os dados do JMX e expô-los a esses sistemas em um formato que eles compreendem nativamente.

O acesso remoto ao JMX Mbeans não está habilitado por padrão. Para obter mais informações sobre monitoramento por meio do JMX, consulte [Monitoramento e gerenciamento por meio da tecnologia JMX](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

Em muitos casos, é necessária uma linha de base para monitorizar eficazmente uma estatística. Para criar uma linha de base, observe o sistema em condições normais de trabalho por um período predeterminado e identifique a métrica normal.

**Monitoramento JVM**

Assim como em qualquer pilha de aplicativos baseada em Java, AEM depende dos recursos que são fornecidos a ela por meio da Java Virtual Machine subjacente. Você pode monitorar o status de muitos desses recursos por meio da Plataforma MXBeans que são expostos pela JVM. Para obter mais informações sobre MXBeans, consulte [Usando o Servidor MBean e a Plataforma MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Estes são alguns parâmetros de linha de base que você pode monitorar para JVM:

Memória

* `MBean: lava.lang:type=Memory`
* URL: */system/console/jmx/java.lang:type=Memory*
* Instâncias: Todos os servidores
* Limiar de alarme: Quando a utilização da memória heap ou não heap exceder 75% da memória máxima correspondente.
* Definição do alarme: A memória do sistema é insuficiente ou há um vazamento de memória no código. Analise um despejo de thread para chegar a uma definição.

**Observação**: As informações fornecidas por este bean são expressas em bytes.

Threads

* MBean: `java.lang:type=Threading`
* URL: */system/console/jmx/java.lang:type=Threading*
* Instâncias: Todos os servidores
* Limiar de alarme: Quando o número de threads for maior que 150% da linha de base.
* Definição do alarme: Ou há um processo de runaway ativo, ou uma operação ineficiente consome uma grande quantidade de recursos. Analise um despejo de thread para chegar a uma definição.

**AEM monitoramento**

AEM também expõe um conjunto de estatísticas e operações por meio do JMX. Eles podem ajudar a avaliar a integridade do sistema e identificar possíveis problemas antes de afetarem os usuários. Para obter mais informações, consulte [documentação](/help/sites-administering/jmx-console.md) em AEM MBeans JMX.

Estes são alguns parâmetros de linha de base que podem ser monitorados para AEM:

Agentes de replicação

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: */system/console/jmx/com.adobe.granite.Replication:type=agent,id=&quot;&lt;AGENT_NAME>&quot;*
* Instâncias: Um autor e todas as instâncias de publicação (para agentes de liberação)
* Limiar de alarme: Quando o valor de `QueueBlocked` for verdadeiro ou o valor de `QueueNumEntries` for superior a 150% da linha de base.

* Definição do alarme: Presença de uma fila bloqueada no sistema, indicando que o público alvo de replicação está inativo ou inacessível. Muitas vezes, problemas de rede ou infraestrutura fazem com que entradas excessivas sejam enfileiradas, o que pode afetar negativamente o desempenho do sistema.

**Observação**: Para os parâmetros MBean e URL, substitua  `<AGENT_NAME>` pelo nome do agente de replicação que você deseja monitorar.

Contador de sessões

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.Jackrabbit.oak:id=7,name=&quot;Estatísticas OakRepository&quot;,type*=&quot;RepositoryStats&quot;
* Instâncias: Todos os servidores
* Limiar de alarme: Quando as sessões abertas excedem a linha de base em mais de 50%.
* Definição do alarme: As sessões podem ser abertas por meio de um código e nunca fecham. Isso pode acontecer lentamente com o tempo e, eventualmente, causar vazamentos de memória no sistema. Embora o número de sessões deva flutuar em um sistema, elas não devem aumentar continuamente.

Verificações de integridade

As verificações de integridade disponíveis no painel [operations](/help/sites-administering/operations-dashboard.md#health-reports) têm MBeans JMX correspondentes para monitoramento. No entanto, você pode gravar verificações de integridade personalizadas para expor estatísticas adicionais do sistema.

Estas são algumas verificações de integridade prontas que são úteis para monitorar:

* Verificações do sistema

   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthChec`k 
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name=systemcheck,type=HealthCheck*
   * Instâncias: Um autor, todos os servidores de publicação
   * Limiar de alarme: Quando o status não estiver OK
   * Definição do alarme: O status de uma das métricas é AVISO ou CRÍTICO. Verifique o atributo log para obter mais informações sobre a causa do problema.

* Fila de replicação

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck `
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name=ReplicationQueue,type=HealthCheck*
   * Instâncias: Um autor, todos os servidores de publicação
   * Limiar de alarme: Quando o status não estiver OK
   * Definição do alarme: O status de uma das métricas é AVISO ou CRÍTICO. Verifique o atributo log para obter mais informações sobre a fila que causou o problema.

* Desempenho da resposta

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck `
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name=RequestsStatus,type=HealthCheck*
   * Instâncias: Todos os servidores
   * Duração do alarme: Quando o status não estiver OK
   * Definição do alarme: O status de uma das métricas é AVISO ou CRÍTICO. Verifique o atributo log para obter mais informações sobre a fila que causou o problema.

* Desempenho da consulta

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck `
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name= queriesStatus,type=HealthCheck*
   * Instâncias: Um autor, todos os servidores de publicação
   * Limiar de alarme: Quando o status não estiver OK
   * Definição do alarme: Um ou mais query lentamente executados no sistema. Verifique o atributo log para obter mais informações sobre os query que causaram o problema.

* Grupos ativos

   * MBean: org.apache.sling.saudcheck:name=inativeBundles,type=HealthCheck 
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name=inativeBundles,type=HealthCheck*
   * Instâncias: Todos os servidores
   * Limiar de alarme: Quando o status não estiver OK
   * Definição do alarme: Presença de pacotes OSGi inativos ou não resolvidos no sistema. Verifique o atributo log para obter mais informações sobre os pacotes que causaram o problema.

* Erros de log

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck `
   * URL: */system/console/jmx/org.apache.sling.saudcheck:name=logErrorHealthCheck,type=HealthCheck*
   * Instâncias: Todos os servidores
   * Limiar de alarme: Quando o status não estiver OK
   * Definição do alarme: Há erros nos arquivos de registro. Verifique o atributo log para obter mais informações sobre a causa do problema.

## Problemas comuns e resoluções {#common-issues-and-resolutions}

No processo de monitoramento, se você encontrar problemas, veja algumas tarefas de solução de problemas que você pode executar para resolver problemas comuns com instâncias AEM:

* Se estiver usando TarMK, execute a compactação Tar com frequência. Para obter mais detalhes, consulte [Manutenção do Repositório](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
* Verifique os registros `OutOfMemoryError`. Para obter mais informações, consulte [Analisar problemas de memória](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html).
* Verifique os registros em busca de referências a query não indexados, traversais de árvore ou traversais de índice. Estes indicam query não indexados ou query inadequadamente indexados. Para obter as práticas recomendadas de otimização do desempenho de query e indexação, consulte [Práticas recomendadas para Query e Indexação](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Use o console de fluxo de trabalho para verificar se seus workflows têm o desempenho esperado. Se possível, condensar vários workflows em um único fluxo de trabalho.
* Revise o monitoramento ao vivo e procure gargalos adicionais ou grandes consumidores de recursos específicos.
* Investigue os pontos de saída da rede do cliente e os pontos de entrada para a rede de instância AEM, incluindo o dispatcher. Frequentemente, essas são áreas de gargalo. Para obter mais informações, consulte [Considerações de rede do Assets](assets-network-considerations.md).
* Atualize seu servidor AEM. Você pode ter um tamanho inadequado para sua instância AEM. O Atendimento ao cliente do Adobe pode ajudá-lo a identificar se o servidor está com tamanho inferior ao normal.
* Examine os arquivos `access.log` e `error.log` para ver se há entradas na hora em que algo deu errado. Procure padrões que possam indicar anomalias de código personalizadas. Adicione-os à lista de eventos que você monitorar.
