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
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 18%

---


# Base e repositório do AEM {#aem-foundation-repository}

## Lista de alterações {#list-of-changes}

### Repositório {#repository}

* Tar MicroKernel do Segmento Oak

   * Modo de compactação rápida (compactação de cauda) para Limpeza de revisão online
   * Taxas de gravação aprimoradas
   * Estatísticas de operações de segmento expostas via JMXBean
   * Estimativa de duração para Limpeza de revisão offline

* Microkernel Oak Mongo

   * A Limpeza de revisão contínua do MongoMK substitui a manutenção de limpeza agendada

* Eficiência aprimorada para a limpeza de revisão em notebooks Documentos
* Consulte [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) e [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) para obter uma visão geral completa dos problemas corrigidos.

>[!CAUTION]
>
>* A nova versão do Oak Segment Tar presente desde o AEM 6.3 exige uma migração de repositório. Esta etapa é obrigatória se você estiver atualizando de uma versão mais antiga do TarMK ou quiser alternar o novo segmento de Tar de outro tipo de persistência. Para obter mais informações sobre quais são os benefícios da nova barra de segmentos, consulte [Migração para Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

>



### Pesquisar e indexar {#search-amp-indexing}

* Suporte aprimorado para operações de indexação via CLI (oak-run):

   * Verificação de consistência do índice
   * Estatísticas de indexação
   * Im/Exportar configuração de índice
   * Reindexação

* Redução do crescimento do repositório relacionado à Lucene para um desempenho geral melhorado do sistema
* Índices de propriedades de Lucene síncrono [(Mais informações)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explicar o Query no Gerenciador de índice agora suporta AEM sintaxe do QueryBuilder
* O Gerenciador de índice agora expõe as métricas de índice: tamanho, última atualização e verificação de consistência

### Interface do usuário {#user-interface}

* Vários aprimoramentos foram feitos na interface para torná-la mais produtiva e fácil de usar.
* Novo painel da Árvore de conteúdo para navegar rapidamente em uma hierarquia. Em combinação com a visualização da lista, isso restaura o modelo de interação da interface clássica.
* Melhoria na rolagem no cartão e na visualização de lista de pastas grandes.
* Interação aprimorada com os resultados da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* Atalhos de teclado adicionais, para a maioria das ações comuns, como abrir um trilho específico, editar, mover e excluir itens ou abrir propriedades.
* Capacidade de desativar atalhos do teclado (ativar/desativar em Preferências).
* Parar de mostrar carimbos de data e hora em toda a interface do usuário em relação após 7 dias (defina o padrão em Preferências).

>[!CAUTION]
>
>* A Adobe não planeja fazer aprimoramentos adicionais à interface do usuário clássica. O AEM 6.4 tem a interface do usuário clássica incluída, e os clientes que atualizam de versões anteriores podem continuar a usando da mesma forma. Observe que a interface do usuário clássica permanece totalmente compatível enquanto está sendo substituída [Leia mais](/help/sites-deploying/ui-recommendations.md).

>



### Distribuição de conteúdo {#content-distribution}

* Desempenho de replicação aprimorado para suportar publicações de ativos de grande volume
* Suporte à autenticação OAuth 2.0 no Distribution Transport
* Desempenho aprimorado para pacotes VLT

### Monitoramento {#monitoring}

* Uma nova Visão geral do sistema fornece uma visualização de instantâneo sobre todos os status e atividades do sistema relacionados ao desempenho
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
* A tarefa de manutenção RevisionGC para MongoDB agora está desabilitada em favor da Limpeza de revisão contínua, consulte a seção Repositório acima.
* A configuração de Expurgação de versão permite manter um número mínimo de versões
* A Expurgação da versão é interrompida no final de uma janela de manutenção. Também pode ser iniciado e parado manualmente e continuará incrementalmente com o próximo start.

### Atualização {#upgrade}

* Compatibilidade com versões anteriores: Os recursos compatíveis com versões anteriores da versão 6.4 ajudam seu código personalizado a permanecer compatível na maioria dos casos e reduzem o esforço de atualização.
* Avaliação da complexidade da atualização: Nova ferramenta de detecção de padrões para avaliar a complexidade de suas atualizações.
* Atualizações sustentáveis: A superfície da API e a Classificação de conteúdo foram apresentadas para ajudá-lo a seguir facilmente as práticas recomendadas para uma atualização eficiente e contínua para a próxima versão ao longo do ciclo de desenvolvimento.
* Reestruturação do repositório: Reestruturação significativa (principalmente/etc.) para facilitar as atualizações e promover as práticas recomendadas de implementação. [Leia mais.](/help/sites-deploying/repository-restructuring.md)
* Consulte a [Documentação de atualização](/help/sites-deploying/upgrade.md) para obter mais detalhes sobre esses recursos.

### Cloud Services {#cloud-services}

* Muitos Cloud Services agora podem ser configurados por meio da interface de usuário para toque; o restante pode ser configurado sob a placa Cloud Services herdados.
* As pastas Sites e Ativos podem ser configuradas com Cloud Services que são carregados de maneira sensível ao contexto.

### Segurança {#security}

* Interface do usuário aprimorada e simplificada com suporte para vários perfis de usuário.
* Desempenho aprimorado para associações de grupos grandes para usuários.

### Projetos e fluxos de trabalho {#projects-and-workflows}

* Touch UI baseado no Editor de fluxo de trabalho para gerenciar modelos de fluxo de trabalho de uma maneira mais simplificada.
* Suporte para expurgação de tarefa do projeto em tarefas de manutenção.

