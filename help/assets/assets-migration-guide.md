---
title: Migrar ativos para o Adobe Experience Manager Assets em massa
description: Como trazer ativos para o AEM, aplicar metadados, gerar representações e ativá-los para publicar instâncias.
contentOwner: AG
feature: Migration,Renditions,Asset Management
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1808'
ht-degree: 8%

---

# Guia de migração de ativos {#assets-migration-guide}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao migrar ativos para o AEM, há várias etapas a serem consideradas. A extração de ativos e metadados para fora de sua casa atual está fora do escopo desse documento, pois varia muito entre as implementações. Em vez disso, este documento descreve como trazer esses ativos para o AEM, aplicar seus metadados, gerar representações e ativar ou publicar os ativos.

## Pré-requisitos {#prerequisites}

Antes de executar qualquer uma das etapas descritas abaixo, analise e implemente as orientações em [Dicas de ajuste de desempenho de ativos](performance-tuning-guidelines.md). Muitas etapas, como configurar o máximo de trabalhos simultâneos, aprimoram a estabilidade e o desempenho do servidor sob carga. Outras etapas, como a configuração do File Data Store, são difíceis de executar depois que o sistema é carregado com ativos.

>[!NOTE]
>
>As seguintes ferramentas de migração de ativos não fazem parte do Adobe Experience Manager. O Suporte ao cliente do Adobe não oferece suporte a essas ferramentas.
>
>* ACS [!DNL Experience Manager] Criador de tags de ferramentas
>* ACS [!DNL Experience Manager] Ferramentas Importador de ativos CSV
>* Gerente de Fluxo de Trabalho em Massa do ACS Commons
>* ACS Commons Fast Action Manager
>* Fluxo de trabalho sintético
>
>Este software é de código aberto e é coberto pela [Licença Apache v2](https://adobe-consulting-services.github.io/pages/license.html). Para fazer uma pergunta ou relatar um problema, visite os respectivos [ [!DNL Experience Manager] Problemas do GitHub para as ferramentas do ACS ](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) e os [ [!DNL Experience Manager] ACS Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrar para [!DNL Experience Manager] {#migrate-to-aem}

Migrar ativos para [!DNL Experience Manager] O requer várias etapas e deve ser exibido como um processo em fases. As fases da migração são as seguintes:

1. Desative workflows.
1. Carregue tags.
1. Assimilar ativos.
1. Processar representações.
1. Ativar ativos.
1. Habilite workflows.

![chlimage_1-223](assets/chlimage_1-223.png)

### Desativar workflows {#disable-workflows}

Antes de iniciar uma migração, desative os lançadores da `DAM Update Asset` fluxo de trabalho. É melhor assimilar todos os ativos no sistema e, em seguida, executar os workflows em lotes. Se você já estiver ao vivo enquanto a migração estiver ocorrendo, poderá agendar essas atividades para serem executadas fora do horário.

### Carregar tags {#load-tags}

É possível que você já tenha uma taxonomia de tags em vigor que esteja aplicando às imagens. Ferramentas como o Importador de ativos CSV e a funcionalidade de perfis de metadados podem ajudar a automatizar a aplicação de tags em ativos. Antes disso, adicione as tags no Experience Manager. O [ACS [!DNL Experience Manager] Criador de tags de ferramentas](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) permite que você preencha as tags usando uma planilha do Excel do Microsoft carregada no sistema.

### Assimilar ativos {#ingest-assets}

O desempenho e a estabilidade são questões importantes ao assimilar ativos no sistema. Ao carregar muitos dados no Experience Manager, verifique se o sistema está funcionando bem. Isso minimizou o tempo necessário para adicionar os dados e ajuda a evitar sobrecarga do sistema. Isso ajuda a evitar falhas do sistema, especialmente em sistemas que já estão em produção.

Há duas abordagens para carregar os ativos no sistema: uma abordagem por push usando HTTP ou uma abordagem por pull usando as APIs do JCR.

#### Enviar por HTTP {#push-through-http}

A equipe do Managed Services do Adobe usa uma ferramenta chamada Glutton para carregar dados em ambientes do cliente. O Glutton é um pequeno aplicativo Java que carrega todos os ativos de um diretório em outro diretório em um [!DNL Experience Manager] instância. Em vez do Glutton, você também pode usar ferramentas como scripts Perl para publicar os ativos no repositório.

Há duas desvantagens principais ao usar a abordagem de passar por https:

1. Transmita os ativos por HTTP para o servidor. Isso requer bastante sobrecarga e é demorado, prolongando assim o tempo necessário para executar sua migração.
1. Se você tiver tags e metadados personalizados que devem ser aplicados aos ativos, essa abordagem exigirá um segundo processo personalizado que será necessário executar para aplicar esses metadados aos ativos depois que eles forem importados.

A outra abordagem para assimilar ativos é obter ativos do sistema de arquivos local. No entanto, se não for possível obter uma unidade externa ou compartilhamento de rede montado no servidor para executar uma abordagem baseada em pull, publicar os ativos por HTTP é a melhor opção.

#### Retirar do sistema de arquivos local {#pull-from-the-local-file-system}

O [ACS [!DNL Experience Manager] Ferramentas Importador de ativos CSV](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) extrai ativos do sistema de arquivos e metadados de ativos de um arquivo CSV para a importação de ativos. O [!DNL Experience Manager] A API do Asset Manager é usada para importar os ativos para o sistema e aplicar as propriedades de metadados configuradas. Idealmente, os ativos são montados no servidor por meio de uma montagem de arquivo de rede ou por uma unidade externa.

Quando os ativos não são transmitidos através de uma rede, o desempenho geral melhora bastante. Esse método geralmente é o método mais eficiente para carregar ativos no repositório. Além disso, é possível importar todos os ativos e metadados em uma única etapa, pois a ferramenta suporta a assimilação de metadados. Nenhuma outra etapa é necessária para aplicar os metadados, digamos usando uma ferramenta separada.

### Processar representações {#process-renditions}

Após carregar os ativos no sistema, é necessário processá-los por meio do fluxo de trabalho Ativo de atualização do DAM para extrair metadados e gerar representações. Antes de executar essa etapa, você precisa duplicar e modificar o fluxo de trabalho do Ativo de atualização do DAM para atender às suas necessidades. Algumas etapas no fluxo de trabalho padrão podem não ser necessárias para você, como a geração do Dynamic Media Classic PTIFF ou a integração do servidor InDesign.

Depois de configurar o workflow de acordo com suas necessidades, você tem duas opções para executá-lo:

1. A abordagem mais simples é [Gerente de fluxo de trabalho em massa do ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Essa ferramenta permite executar um query e processar os resultados do query por meio de um workflow. Também há opções para definir tamanhos de lote.
1. Use o [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) em conjunto com [Fluxos de trabalho sintéticos](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html). Embora essa abordagem seja muito mais abrangente, ela permite remover a sobrecarga do [!DNL Experience Manager] mecanismo de fluxo de trabalho ao otimizar o uso de recursos do servidor. Além disso, o Fast Action Manager aumenta ainda mais o desempenho, monitorando dinamicamente os recursos do servidor e diminuindo a carga colocada no sistema. Os exemplos de scripts foram fornecidos na página de recursos ACS Commons.

### Ativar ativos {#activate-assets}

Para implantações com um nível de publicação, é necessário ativar os ativos no farm de publicação. Embora o Adobe recomende executar mais de uma única instância de publicação, é mais eficiente replicar todos os ativos para uma única instância de publicação e clonar essa instância. Ao ativar grandes números de ativos, após acionar uma ativação de árvore, talvez seja necessário intervir. Veja o porquê: Ao disparar ativações, os itens são adicionados à fila de trabalhos/eventos do Sling. Depois que o tamanho dessa fila começar a exceder aproximadamente 40.000 itens, o processamento ficará lento drasticamente. Depois que o tamanho dessa fila exceder 100.000 itens, a estabilidade do sistema começará a sofrer.

Para contornar esse problema, use o [Gerenciador de ação rápida](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) para gerenciar a replicação de ativos. Isso funciona sem usar as filas do Sling, diminuindo a sobrecarga, enquanto limita a carga de trabalho para impedir que o servidor fique sobrecarregado. Um exemplo de uso do FAM para gerenciar a replicação é mostrado na página de documentação do recurso.

Outras opções para obter ativos para o farm de publicação incluem o uso de [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) ou [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), que são fornecidos como ferramentas, como parte do Jackrabbit. Outra opção é usar uma ferramenta de software livre para sua [!DNL Experience Manager] infraestrutura chamada [Grabbit](https://github.com/TWCable/grabbit), que alega ter desempenho mais rápido do que o vlt.

Para qualquer uma dessas abordagens, o aviso é que os ativos na instância do autor não aparecem como ativados. Para lidar com a sinalização desses ativos com o status de ativação correto, também é necessário executar um script para marcar os ativos como ativados.

>[!NOTE]
>
>O Adobe não mantém nem suporta Grabbit.

### Clonar publicação {#clone-publish}

Depois que os ativos tiverem sido ativados, você poderá clonar sua instância de publicação para criar quantas cópias forem necessárias para a implantação. A clonagem de um servidor é bastante simples, mas há alguns passos importantes a serem lembrados. Para clonar a publicação:

1. Faça backup da instância de origem e do armazenamento de dados.
1. Restaure o backup da instância e do armazenamento de dados para o local de destino. As etapas a seguir se referem a essa nova instância.
1. Execute uma pesquisa no sistema de arquivos em `crx-quickstart/launchpad/felix` para `sling.id`. Exclua esse arquivo.
1. No caminho raiz do armazenamento de dados, localize e exclua qualquer `repository-XXX` arquivos.
1. Editar `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` e `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` para apontar para o local do armazenamento de dados no novo ambiente.
1. Inicie o ambiente.
1. Atualize a configuração de qualquer agente de replicação no(s) autor(es) para apontar para as instâncias de publicação corretas ou os agentes de liberação do dispatcher na nova instância para apontar para os dispatchers corretos para o novo ambiente.

### Ativar workflows {#enable-workflows}

Depois de concluir a migração, os iniciadores dos fluxos de trabalho do Ativo de atualização do DAM devem ser reativados para oferecer suporte à geração de representação e extração de metadados para o uso diário do sistema.

## Migrar ativos em [!DNL Experience Manager] implantações {#migrate-between-aem-instances}

Embora não seja quase tão comum, às vezes você precisa migrar grandes quantidades de dados de um [!DNL Experience Manager] instância para outra; por exemplo, ao executar um [!DNL Experience Manager] atualizar, atualizar seu hardware ou migrar para um novo data center, como com uma migração do AMS.

Nesse caso, seus ativos já estão preenchidos com metadados e as representações já são geradas. Você pode simplesmente se concentrar em mover ativos de uma instância para outra. Ao migrar entre [!DNL Experience Manager] você executa as seguintes etapas:

1. Desativar fluxos de trabalho: Como você está migrando representações junto com nossos ativos, deseja desativar os inicializadores do fluxo de trabalho para o Ativo de atualização do DAM.

1. Migrar tags: Porque você já tem tags carregadas na origem [!DNL Experience Manager] Você pode criá-los em um pacote de conteúdo e instalar o pacote na instância de destino.

1. Migrar ativos: Há duas ferramentas recomendadas para mover ativos de um [!DNL Experience Manager] instância para outra:

   * **Cofre de cópia remota** ou `vlt rcp`, permite usar o vlt em uma rede. Você pode especificar um diretório de origem e de destino e o vlt baixa todos os dados do repositório de uma instância e os carrega na outra. O rcp da vlt está documentado em [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** é uma ferramenta de sincronização de conteúdo de código aberto desenvolvida pelo Time Warner Cable para seus [!DNL Experience Manager] implementação. Como usa fluxos de dados contínuos, em comparação ao vlt rcp, ele tem uma latência mais baixa e alega uma melhoria de velocidade de duas a dez vezes mais rápida que o vlt rcp. O Grabbit também suporta a sincronização somente do conteúdo delta, o que permite sincronizar as alterações depois que uma passagem de migração inicial for concluída.

1. Ativar ativos: Siga as instruções para [ativação de ativos](#activate-assets) documentado para a migração inicial para o AEM.

1. Publicação de clone: Assim como com uma nova migração, carregar uma única instância de publicação e clonar é mais eficiente do que ativar o conteúdo em ambos os nós. Consulte [Clonando publicação.](#clone-publish)

1. Ativar workflows: Após concluir a migração, ative novamente os iniciadores dos fluxos de trabalho do Ativo de atualização do DAM para oferecer suporte à geração de representação e extração de metadados para uso diário do sistema.
