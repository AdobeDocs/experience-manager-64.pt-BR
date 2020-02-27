---
title: Base e repositório do AEM
seo-title: Base e repositório do AEM
description: Notas de versão específicas da plataforma e do repositório do AEM no Adobe Experience Manager 6.3.
seo-description: Notas de versão específicas da plataforma e do repositório do AEM no Adobe Experience Manager 6.3.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348

---


# Base e repositório do AEM {#aem-foundation-repository}

## Lista de alterações {#list-of-changes}

### Repositório {#repository}

* Tar MicroKernel do Segmento Oak

   * Modo de compactação rápida (compactação de cauda) para Limpeza online de revisão
   * Taxas de gravação aprimoradas
   * Estatísticas de operações de segmento expostas via JMXBean
   * Estimativa de duração para Limpeza de revisão offline

* Microkernel Oak Mongo

   * A Limpeza de revisão contínua do MongoMK substitui a manutenção de limpeza agendada

* Eficiência aprimorada para a limpeza de revisão em notebooks de documentos
* Please see [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) and [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) for a full overview of fixed issues.

>[!CAUTION]
>
>* A nova versão do Oak Segment Tar presente desde o AEM 6.3 exige uma migração de repositório. Esta etapa é obrigatória se você estiver atualizando de uma versão mais antiga do TarMK ou quiser alternar o novo segmento de Tar de outro tipo de persistência. For more information on what the benefits of the new Segment Tar are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>



### Pesquisar e indexar {#search-amp-indexing}

* Suporte aprimorado para operações de indexação via CLI (oak-run):

   * Verificação de consistência do índice
   * Estatísticas de indexação
   * Im/Exportar configuração de índice
   * Reindexação

* Redução do crescimento do repositório relacionado à Lucene para um desempenho geral melhorado do sistema
* Índices de Propriedades de Lucene Síncrono [(Mais informações)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explicar a consulta no Gerenciador de índice agora oferece suporte à sintaxe AEM QueryBuilder
* O Gerenciador de índice agora expõe as métricas de índice: tamanho, última atualização e verificação de consistência

### Interface do usuário {#user-interface}

* Vários aprimoramentos foram feitos na interface para torná-la mais produtiva e fácil de usar.
* Novo painel da Árvore de conteúdo para navegar rapidamente em uma hierarquia. Em combinação com a exibição de lista, isso restaura o modelo de interação da interface clássica.
* Melhoria na rolagem no cartão e na exibição de lista de pastas grandes.
* Interação aprimorada com os resultados da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* Atalhos de teclado adicionais, para a maioria das ações comuns, como abrir um trilho específico, editar, mover e excluir itens ou abrir propriedades.
* Capacidade de desativar atalhos do teclado (ativar/desativar em Preferências).
* Pare de mostrar carimbos de data e hora em toda a interface do usuário em relação após 7 dias (defina o padrão em Preferências).

>[!CAUTION]
>
>* A Adobe não planeja fazer aprimoramentos adicionais à interface do usuário clássica. O AEM 6.4 tem a interface do usuário clássica incluída, e os clientes que atualizam de versões anteriores podem continuar a usando da mesma forma. Note that Classic UI remains fully supported while being deprecated [Read more](/help/sites-deploying/ui-recommendations.md).
>



### Distribuição de conteúdo {#content-distribution}

* Desempenho de replicação aprimorado para suportar publicações de ativos de grande volume
* Suporte à autenticação OAuth 2.0 no Distribution Transport
* Desempenho aprimorado para pacotes VLT

### Monitoramento {#monitoring}

* Uma nova Visão geral do sistema fornece uma visualização instantânea de todos os status e atividades do sistema relacionados ao desempenho
* Novas verificações de integridade:

   * Detectar índices grandes de Lucene
   * Estado de funcionamento da indexação assíncrona
   * Índices Lucene grandes
   * Desempenho da consulta
   * Limites de cruzamento da consulta
   * Relógios sincronizados
   * Manutenção do sistema - Limpeza de revisão
   * Manutenção do sistema - DataStore GC
   * Manutenção do sistema - Revisão contínua GC

* O usuário agora pode definir o escopo do download status.zip

### Manutenção {#maintenance}

* Exclusão ativa de binários Lucene usando uma tarefa de manutenção
* A tarefa de manutenção RevisionGC para MongoDB está desabilitada em favor da Limpeza de revisão contínua, consulte a seção Repositório acima.
* A configuração de Expurgação de versão permite manter um número mínimo de versões
* A Expurgação da versão é interrompida no final de uma janela de manutenção. Também pode ser iniciado e parado manualmente e continuará incrementalmente com o próximo início.

### Atualização {#upgrade}

* Compatibilidade com versões anteriores: Os recursos compatíveis com versões anteriores da versão 6.4 ajudam seu código personalizado a permanecer compatível na maioria dos casos e reduzem o esforço de atualização.
* Avaliação da complexidade da atualização: Nova ferramenta de detecção de padrões para avaliar a complexidade de suas atualizações.
* Atualizações sustentáveis: A superfície da API e a Classificação de conteúdo foram apresentadas para ajudá-lo a seguir facilmente as práticas recomendadas para uma atualização eficiente e contínua para a próxima versão ao longo do ciclo de desenvolvimento.
* Reestruturação do repositório: Reestruturação significativa (principalmente/etc.) para facilitar as atualizações e promover as práticas recomendadas de implementação. [Leia mais.](/help/sites-deploying/repository-restructuring.md)
* Please see the [Upgrade documentation](/help/sites-deploying/upgrade.md) for more details on these features.

### Cloud Services {#cloud-services}

* Muitos serviços em nuvem agora podem ser configurados por meio da interface de usuário para toque; os restantes podem ser configurados no cartão de serviços herdados da Cloud.
* As pastas Sites e Ativos podem ser configuradas com os Serviços em nuvem que são carregados de maneira sensível ao contexto.

### Segurança {#security}

* Interface de usuário aprimorada e simplificada para criação de usuários com suporte para vários perfis de usuário.
* Desempenho aprimorado para associações de grupos grandes para usuários.

### Projetos e fluxos de trabalho {#projects-and-workflows}

* Touch UI baseado no Editor de fluxo de trabalho para gerenciar modelos de fluxo de trabalho de uma maneira mais simplificada.
* Suporte para expurgação de tarefa de projeto em tarefas de manutenção.

