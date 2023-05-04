---
title: AEM Foundation & Repository
seo-title: AEM Foundation & Repository
description: Notas de versão específicas da plataforma e do repositório do Adobe Experience Manager 6.3 AEM.
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# AEM Foundation &amp; Repository {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Lista de alterações {#list-of-changes}

### Repositório {#repository}

* Oak Segment Tar MicroKernel

   * Modo de compactação rápida (compactação de cauda) para Limpeza de Revisão Online
   * Taxas de gravação aprimoradas
   * Estatísticas de operações de segmento expostas via JMXBean
   * Estimativa de duração para Limpeza de Revisão Offline

* Microkernel Oak Mongo

   * A Limpeza de Revisão Contínua para MongoMK substitui a manutenção de limpeza agendada

* Eficiência aprimorada para limpeza de revisão em notebooks de documento
* Consulte [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) e [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) para obter uma visão geral completa dos problemas corrigidos.

>[!CAUTION]
>
>* A nova versão do Oak Segment Tar presente desde o AEM 6.3 requer uma migração de repositório. Esta etapa é obrigatória se você estiver atualizando de uma versão mais antiga do TarMK ou quiser alternar o novo Segment Tar de outro tipo de persistência. Para obter mais informações sobre quais são os benefícios do novo Tar de segmento, consulte o [Perguntas frequentes sobre a migração para o Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### Pesquisa e indexação {#search-amp-indexing}

* Suporte aprimorado para operações de indexação via oak-run (CLI):

   * Verificação de consistência do índice
   * Estatísticas de indexação
   * Im/Exportar configuração de índice
   * Reindexação

* Redução do crescimento do repositório relacionado ao Lucene para um desempenho geral aprimorado do sistema
* Índices de propriedades síncronas do Lucene [(Mais informações)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explicar consulta no Gerenciador de índice agora oferece suporte AEM sintaxe do QueryBuilder
* O Gerenciador de índice agora expõe as métricas de índice: tamanho, última atualização e verificação de consistência

### Interface do usuário {#user-interface}

* Várias melhorias foram feitas na interface do usuário para torná-la mais produtiva e fácil de usar.
* Novo painel Árvore de conteúdo para navegar rapidamente em uma hierarquia. Em combinação com a exibição em lista, isso restaura o modelo de interação da interface do usuário clássica.
* Melhoria na rolagem na exibição de cartão e lista de pastas grandes.
* Interação aprimorada com os resultados da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* Atalhos adicionais do teclado, para as ações mais comuns, como abrir um painel específico, editar, mover e excluir um item ou abrir propriedades.
* Capacidade de desativar atalhos do teclado (ativar/desativar em Preferências).
* Parar de mostrar carimbos de data e hora em toda a interface do usuário em relação após 7 dias (defina o padrão em Preferências).

>[!CAUTION]
>
>* O Adobe não planeja fazer aprimoramentos adicionais à interface clássica. O AEM 6.4 tem a interface do usuário clássica incluída e os clientes que atualizam de versões anteriores podem continuar a usá-la como estão. Observe que a interface do usuário clássica permanece totalmente compatível enquanto está obsoleta [Leia mais](/help/sites-deploying/ui-recommendations.md).
>


### Distribuição de conteúdo {#content-distribution}

* Desempenho de replicação aprimorado para oferecer suporte a publicações de ativos de grande volume
* Suporte à autenticação OAuth 2.0 no Distribution Transport
* Desempenho aprimorado para pacotes VLT

### Monitoramento {#monitoring}

* Uma nova Visão geral do sistema fornece uma visualização instantânea de todos os status e atividades do sistema relacionados ao desempenho
* Novas verificações de integridade:

   * Detectar grandes índices de Lucene
   * Integridade da indexação assíncrona
   * Índices Lucene grandes
   * Desempenho da consulta
   * Limites de cruzamento da consulta
   * Relógios sincronizados
   * Manutenção do Sistema - Limpeza de Revisão
   * Manutenção do sistema - DataStore GC
   * Manutenção do sistema - GC de revisão contínua

* Agora o usuário pode definir o escopo do download status.zip

### Manutenção {#maintenance}

* Exclusão ativa de binários do Lucene usando uma tarefa de manutenção
* A tarefa de manutenção RevisionGC para MongoDB foi desabilitada em favor da Limpeza de Revisão Contínua. Consulte a seção Repositório acima.
* A configuração de limpeza de versão permite manter um número mínimo de versões
* A limpeza de versão é interrompida no final de uma janela de manutenção. Ele também pode ser iniciado e parado manualmente e continuará incrementalmente com o próximo início.

### Atualizar {#upgrade}

* Compatibilidade com versões anteriores: Os recursos compatíveis com versões anteriores da versão 6.4 ajudam o código personalizado a permanecer compatível na maioria dos casos e reduzem o esforço de atualização.
* Avaliação de Complexidade de Atualização: Nova ferramenta de detecção de padrões para avaliar a complexidade de suas atualizações.
* Atualizações sustentáveis: A superfície da API e a Classificação de conteúdo foram apresentadas para ajudar você a seguir facilmente as práticas recomendadas para um upgrade eficiente e perfeito para a próxima versão ao longo do ciclo de desenvolvimento.
* Reestruturação do Repositório: Reestruturação significativa (principalmente /etc) para facilitar as atualizações e promover as práticas recomendadas de implementação. [Leia mais.](/help/sites-deploying/repository-restructuring.md)
* Consulte a [Atualizar documentação](/help/sites-deploying/upgrade.md) para obter mais detalhes sobre esses recursos.

### Cloud Services {#cloud-services}

* Muitos Cloud Services agora podem ser configurados por meio da interface do usuário de toque; o restante pode ser configurado no cartão Cloud Services herdado.
* As pastas Sites e Ativos podem ser configuradas com Cloud Services que são carregadas de maneira sensível ao contexto.

### Segurança {#security}

* Interface do usuário aprimorada e simplificada de criação de usuários com suporte para vários perfis de usuário.
* Desempenho aprimorado para associações de grupo grande para usuários.

### Projetos e fluxos de trabalho {#projects-and-workflows}

* Toque no Editor de fluxo de trabalho baseado na interface do usuário para gerenciar modelos de fluxo de trabalho de maneira mais simplificada.
* Suporte para limpeza de tarefas do projeto em tarefas de manutenção.
