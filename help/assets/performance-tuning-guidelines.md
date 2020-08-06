---
title: Guia de ajuste de desempenho de ativos
description: Principais áreas de foco em torno AEM configuração, alterações no hardware, software e componentes de rede para remover gargalos e otimizar o desempenho do AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c407cecf4f4de9aa00ba987f96df3c75784e0171
workflow-type: tm+mt
source-wordcount: '3202'
ht-degree: 0%

---


# Guia de ajuste de desempenho de ativos {#assets-performance-tuning-guide}

Uma configuração do Adobe Experience Manager (AEM) Assets contém vários componentes de hardware, software e rede. Dependendo do cenário de implantação, talvez você precise de alterações específicas na configuração de hardware, software e componentes de rede para remover gargalos de desempenho.

Além disso, identificar e seguir determinadas diretrizes de otimização de hardware e software ajuda a criar uma base sólida que permite que a implantação do AEM Assets atenda às expectativas de desempenho, escalabilidade e confiabilidade.

O baixo desempenho no AEM Assets pode afetar a experiência do usuário em relação ao desempenho interativo, processamento de ativos, velocidade de download e outras áreas.

Na verdade, a otimização do desempenho é uma tarefa fundamental que você executa antes de estabelecer métricas de público alvo para qualquer projeto.

Estas são algumas áreas de foco chave em torno das quais você descobre e corrige problemas de desempenho antes que eles afetem os usuários.

## Plataforma {#platform}

Embora o AEM seja suportado em várias plataformas, o Adobe encontrou o maior suporte para ferramentas nativas no Linux e no Windows, o que contribui para o desempenho otimizado e a facilidade de implementação. Idealmente, você deve implantar um sistema operacional de 64 bits para atender aos requisitos de alta memória de uma implantação da AEM Assets. Como em qualquer implantação AEM, você deve implementar o TarMK sempre que possível. Embora o TarMK não possa ser dimensionado além de uma única instância do autor, ele tem um desempenho melhor do que o MongoMK. Você pode adicionar instâncias de descarregamento TarMK para aumentar o poder de processamento do fluxo de trabalho de sua implantação do AEM Assets.

### Pasta temporária {#temp-folder}

Para melhorar os tempos de upload de ativos, use o armazenamento de alto desempenho para o diretório temporário Java. No Linux e no Windows, uma unidade de RAM ou SSD pode ser usada. Em ambientes baseados em nuvem, um tipo de armazenamento de alta velocidade equivalente pode ser usado. Por exemplo, no Amazon EC2, uma unidade [efêmera](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) pode ser usada para a pasta temp.

Supondo que o servidor tenha ampla memória, configure uma unidade RAM. No Linux, execute estes comandos para criar uma unidade de 8 GB de RAM:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

No SO Windows, você precisaria usar um driver de terceiros para criar uma unidade de RAM ou apenas usar um armazenamento de alto desempenho, como SSD.

Quando o volume temporário de alto desempenho estiver pronto, defina o parâmetro JVM -Djava.io.tmpdir. Por exemplo, você pode adicionar o parâmetro JVM abaixo à variável CQ_JVM_OPTS no script bin/start do AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Configuração do Java {#java-configuration}

### Versão do Java {#java-version}

Como a Oracle parou de lançar atualizações para o Java 7 a partir de abril de 2015, a Adobe recomenda implantar a AEM Assets no Java 8. Em alguns casos, demonstrou um melhor desempenho.

### Parâmetros JVM {#jvm-parameters}

Você deve definir os seguintes parâmetros JVM:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=verdadeiro

## Configuração do armazenamento de dados e da memória {#data-store-and-memory-configuration}

### Configuração do armazenamento de dados de arquivo {#file-data-store-configuration}

É recomendável separar o armazenamento de dados do armazenamento de segmentos para todos os usuários do AEM Assets. Além disso, configurar os parâmetros `maxCachedBinarySize` e `cacheSizeInMB` pode ajudar a maximizar o desempenho. Defina `maxCachedBinarySize` para o menor tamanho de arquivo que pode ser mantido no cache. Especifique o tamanho do cache na memória a ser usado para o armazenamento de dados no `cacheSizeInMB`. O Adobe recomenda que você defina esse valor entre 2 a 10% do tamanho total do heap. No entanto, o teste de carga/desempenho pode ajudar a determinar a configuração ideal.

### Configurar o tamanho máximo do cache de imagem em buffer {#configure-the-maximum-size-of-the-buffered-image-cache}

Ao fazer upload de grandes quantidades de ativos para a Adobe Experience Manager, para permitir picos inesperados no consumo de memória e para evitar falhas de JVM com OutOfMemoryErrors, reduza o tamanho máximo configurado do cache de imagem em buffer. Considere um exemplo de que você tem um sistema com um heap ( `Xmx`param) máximo de 5 GB, um BlobCache Oak definido em 1 GB e um cache de documento definido em 2 GB. Nesse caso, o cache armazenado em buffer levaria no máximo 1,25 GB e memória, o que deixaria apenas 0,75 GB de memória para picos inesperados.

Configure o tamanho do cache armazenado em buffer no console da Web OSGi. Em `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, defina a propriedade `cq.dam.image.cache.max.memory` em bytes. Por exemplo, 1073741824 é 1 GB (1024 x 1024 x 1024 = 1 GB).

No AEM 6.1 SP1, se você estiver usando um `sling:osgiConfig` nó para configurar essa propriedade, certifique-se de definir o tipo de dados como Longo. Para obter mais detalhes, consulte [CQBufferedImageCache consome heap durante os uploads](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)do ativo.

### Armazenamentos de dados compartilhados {#shared-data-stores}

A implementação de um armazenamento de dados de arquivos compartilhados ou S3 pode ajudar a economizar espaço em disco e aumentar o throughput da rede em implementações de larga escala. Para obter mais informações sobre os prós e contras do uso de um armazenamento de dados compartilhado, consulte o Guia [de dimensionamento de](assets-sizing-guide.md)ativos.

### S3 data store {#s-data-store}

A seguinte configuração do S3 Data Store ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) ajudou a Adobe extrair 12,8 TB de BLOBs (objetos grandes binários) de um armazenamento de dados de arquivo existente para um armazenamento de dados S3 em um local do cliente:

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Otimização da rede {#network-optimization}

O Adobe recomenda habilitar o HTTPS porque muitas empresas têm firewalls que cheiram o tráfego HTTP, o que afeta negativamente os uploads e corrompe os arquivos. Para fazer uploads de arquivos grandes, verifique se os usuários têm conexões com fio à rede, pois uma rede WiFi fica rapidamente saturada. Para obter diretrizes sobre como identificar gargalos de rede, consulte Guia [de dimensionamento de](assets-sizing-guide.md)ativos. Para avaliar o desempenho da rede analisando a topologia da rede, consulte Considerações [de rede do](assets-network-considerations.md)Assets.

Primariamente, sua estratégia de otimização de rede depende da quantidade de largura de banda disponível e da carga da sua instância AEM. Opções comuns de configuração, incluindo firewalls ou proxies, podem ajudar a melhorar o desempenho da rede. Estes são alguns pontos-chave que devem ser levados em conta:

* Dependendo do tipo de instância (pequena, moderada, grande), verifique se você tem largura de banda de rede suficiente para a instância AEM. A alocação de largura de banda adequada é especialmente importante se AEM estiver hospedado no AWS.
* Se sua instância AEM estiver hospedada no AWS, você poderá se beneficiar se tiver uma política de dimensionamento versátil. Atualize a instância se os usuários esperarem carga alta. Baixe-o para uma carga moderada/baixa.
* HTTPS: A maioria dos usuários tem firewalls que cheiram o tráfego HTTP, o que pode afetar negativamente o carregamento de arquivos ou até mesmo arquivos corrompidos durante a operação de upload.
* Carregamentos de arquivos grandes: Verifique se os usuários têm conexões com fio à rede (as conexões WiFi se saturam rapidamente).

## Fluxos de trabalhos {#workflows}

### workflows transitórios {#transient-workflows}

Sempre que possível, defina o fluxo de trabalho Atualizar ativo DAM como Transitório. A configuração reduz significativamente os custos indiretos necessários para processar workflows porque, nesse caso, os workflows não precisam passar pelos processos normais de rastreamento e arquivamento.

>[!NOTE]
>
>Por padrão, o fluxo de trabalho do Ativo de atualização do DAM está definido como Transitório no AEM 6.3. Nesse caso, você pode ignorar o procedimento a seguir.

1. Abra `http://localhost:4502/miscadmin` a instância AEM que deseja configurar.

1. Na árvore de navegação, expanda **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]** > **[!UICONTROL dam]**.
1. Duplo clique em Ativo **[!UICONTROL de atualização]** DAM.
1. No painel de ferramentas flutuante, alterne para a guia **[!UICONTROL Página]** e clique em Propriedades **** da página.
1. Selecione Fluxo de trabalho **[!UICONTROL temporário Clique em]** OK ****.

   >[!NOTE]
   >
   >Alguns recursos não suportam workflows transitórios. Se sua implantação do AEM Assets exigir esses recursos, não configure workflows transitórios.

   Nos casos em que workflows transitórios não podem ser usados, execute a remoção de fluxo de trabalho regularmente para excluir workflows arquivados de ativos de atualização de DAM para garantir que o desempenho do sistema não diminua.

   Normalmente, você deve executar workflows de expurgação semanalmente. No entanto, em cenários com muitos recursos, como durante a ingestão de ativos em larga escala, você pode executá-los com mais frequência.

   Para configurar a expurgação do fluxo de trabalho, adicione uma nova configuração de Expurgação do fluxo de trabalho de Adobe Granite por meio do console OSGi. Em seguida, configure e agende o fluxo de trabalho como parte da janela de manutenção semanal.

   Se a limpeza for longa demais, ela expira. Portanto, você deve garantir que as tarefas de purga sejam concluídas para evitar situações em que workflows de expurgação não sejam concluídos devido ao alto número de workflows.

   Por exemplo, após executar vários workflows não transitórios (que criam nós de instância do fluxo de trabalho), você pode executar o [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) de forma ad-hoc. Ele remove instâncias de fluxo de trabalho redundantes e concluídas imediatamente, em vez de aguardar a execução do scheduler Adobe Granite Workflow Purge.

### Máximo de trabalhos paralelos {#maximum-parallel-jobs}

Por padrão, AEM executa um número máximo de trabalhos paralelos igual ao número de processadores no servidor. O problema com essa configuração é que, durante períodos de carga pesada, todos os processadores são ocupados pelos workflows de ativos de atualização de DAM, retardando a capacidade de resposta da interface do usuário e impedindo a AEM de executar outros processos que salvaguardem o desempenho e a estabilidade do servidor. Como prática recomendada, defina esse valor para metade dos processadores disponíveis no servidor, executando as seguintes etapas:

1. No AEM Author, vá para [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Clique em Editar em cada fila de fluxo de trabalho relevante para sua implementação, por exemplo, Fila de fluxo de trabalho temporário de granite.
1. Altere o valor de Máximo de Trabalhos Paralelos e clique em Salvar.

Configurar uma fila para metade dos processadores disponíveis é uma solução viável para o start. No entanto, talvez seja necessário aumentar ou diminuir esse número para atingir o throughput máximo e ajustá-lo por ambiente. Há filas separadas para workflows transitórios e não transitórios, bem como outros processos, como workflows externos. Se várias filas definidas como 50% dos processadores estiverem ativos simultaneamente, o sistema poderá ser sobrecarregado rapidamente. As filas muito usadas variam muito entre as implementações do usuário. Portanto, talvez seja necessário configurá-los cuidadosamente para obter a máxima eficiência sem sacrificar a estabilidade do servidor.

### Descarregamento {#offloading}

Para um grande volume de workflows ou workflows que consomem muitos recursos, como a transcodificação de vídeo, você pode descarregar workflows de ativos de atualização de DAM em uma segunda instância do autor. Muitas vezes, o problema com o descarregamento é que qualquer carga salva com o descarregamento do processamento do fluxo de trabalho é compensada pelo custo de replicar o conteúdo para frente e para trás entre as instâncias.

A partir do AEM 6.2 e com um pacote de recursos para o AEM 6.1, você pode fazer o descarregamento com replicação sem binários. Neste modelo, as instâncias do autor compartilham um armazenamento de dados comum e enviam apenas os metadados para frente e para trás por meio da replicação direta. Embora essa abordagem funcione bem com um armazenamento de dados de arquivo compartilhado, pode haver problemas com um armazenamento de dados S3. Como os threads de gravação em segundo plano podem induzir latência, é possível que um ativo não tenha sido gravado no armazenamento de dados antes dos start da tarefa de descarregamento.

### Configuração do ativo de atualização do DAM {#dam-update-asset-configuration}

O fluxo de trabalho do Ativo de atualização do DAM contém um conjunto completo de etapas configuradas para tarefa, como geração do Scene7 PTIFF e integração do InDesign Server. No entanto, a maioria dos usuários pode não exigir várias dessas etapas. O Adobe recomenda que você crie uma cópia personalizada do modelo de fluxo de trabalho Atualizar ativo DAM e remova quaisquer etapas desnecessárias. Nesse caso, atualize os iniciadores do Ativo de atualização do DAM para apontar para o novo modelo.

>[!NOTE]
>
>A execução intensiva do fluxo de trabalho do Ativo de atualização do DAM pode aumentar consideravelmente o tamanho do armazenamento de dados do arquivo. Os resultados de uma experiência realizada pelo Adobe demonstraram que o tamanho do armazenamento de dados pode aumentar aproximadamente 400 GB se cerca de 5500 workflows forem executados em 8 horas.
>
>É um aumento temporário e o armazenamento de dados é restaurado para seu tamanho original depois que você executa a tarefa de coleta de lixo do armazenamento de dados.
>
>Normalmente, a tarefa de coleta de lixo do armazenamento de dados é executada semanalmente junto com outras tarefas de manutenção programadas.
>
>Se você tiver um espaço em disco limitado e executar workflows de ativos de atualização de DAM intensamente, considere programar a tarefa de coleta de lixo com mais frequência.

#### Geração de execução em tempo de execução {#runtime-rendition-generation}

Os clientes usam imagens de vários tamanhos e formatos em seu site ou para distribuição a parceiros comerciais. Como cada representação adiciona ao espaço ocupado do ativo no repositório, o Adobe recomenda usar esse recurso de forma criteriosa. Para reduzir a quantidade de recursos necessários para processar e armazenar imagens, é possível gerar essas imagens em tempo de execução em vez de representações durante a ingestão.

Muitos clientes do Sites implementam um servlet de imagem que redimensiona e corta imagens no momento em que são solicitadas, o que impõe carga adicional na instância de publicação. Entretanto, enquanto essas imagens puderem ser armazenadas em cache, o desafio poderá ser atenuado.

Uma abordagem alternativa é usar a tecnologia Scene7 para entregar a manipulação da imagem totalmente. Além disso, você pode implantar o Brand Portal, que não somente assume as responsabilidades de geração de execução da infraestrutura AEM, mas também toda a camada de publicação.

#### ImageMagick {#imagemagick}

Se você personalizar o fluxo de trabalho do Ativo de atualização do DAM para gerar renderizações usando o ImageMagick, o Adobe recomenda que você modifique o arquivo policy.xml em */etc/ImageMagick/*. Por padrão, o ImageMagick usa todo o espaço em disco disponível no volume do SO e na memória disponível. Faça as seguintes alterações de configuração na `policymap` seção de policy.xml para limitar esses recursos.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Além disso, defina o caminho da pasta temporária do ImageMagick no arquivo *configure.xml* (ou definindo a variável de ambiente `MAGIC_TEMPORARY_PATH`) para uma partição de disco que tenha espaço suficiente e IOPS.

>[!CAUTION]
>
>Uma configuração incorreta pode tornar o servidor instável se o ImageMagick usar todo o espaço em disco disponível. As alterações de política necessárias para processar arquivos grandes usando o ImageMagick podem afetar o desempenho do AEM. Para obter mais informações, consulte [instalar e configurar o ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>Os arquivos ImageMagick `policy.xml` e `configure.xml` ImageMagick podem ser encontrados em `/usr/lib64/ImageMagick-*/config/` vez de `/etc/ImageMagick/`. Consulte a documentação [do](https://www.imagemagick.org/script/resources.php) ImageMagick para obter detalhes sobre os locais dos arquivos de configuração.

Se você estiver usando AEM no Adobe Managed Services (AMS), entre em contato com o Atendimento ao cliente da Adobe se planeja processar vários arquivos PSD ou PSB grandes. O Experience Manager pode não processar arquivos PSB de alta resolução que tenham mais de 30000 x 23000 pixels.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP writeback {#xmp-writeback}

XMP write-back atualiza o ativo original sempre que os metadados são modificados no AEM, o que resulta no seguinte:

* O próprio ativo é modificado
* Uma versão do ativo é criada
* O Ativo de atualização de DAM é executado no ativo

Os resultados listados consomem recursos consideráveis. Portanto, o Adobe recomenda [desativar XMP Writeback](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html), se não for necessário.

A importação de uma grande quantidade de metadados pode resultar em atividade de repetição de gravação de XMP com muitos recursos se o sinalizador workflows de execução estiver marcado. Planeje tal importação durante o uso de servidor simplificado para que o desempenho para outros usuários não seja afetado.

## Replicação {#replication}

Ao replicar ativos para um grande número de instâncias de publicação, por exemplo em uma implementação do Sites, o Adobe recomenda o uso da replicação em cadeia. Nesse caso, a instância do autor é replicada para uma única instância de publicação que, por sua vez, é replicada para outras instâncias de publicação, liberando a instância do autor.

### Configurar replicação em cadeia {#configure-chain-replication}

1. Escolha a instância de publicação que deseja usar para encadear as replicações em
1. Nessa instância de publicação, adicione agentes de replicação que apontem para outras instâncias de publicação
1. Em cada um desses agentes de replicação, ative **[!UICONTROL Ao receber]** na guia **[!UICONTROL Acionadores]**

>[!NOTE]
>
>O Adobe não recomenda a ativação automática de ativos. No entanto, se necessário, o Adobe recomenda fazer isso como a etapa final em um fluxo de trabalho, normalmente o Ativo de atualização do DAM.

## Índices de pesquisa {#search-indexes}

Certifique-se de implementar os service packs mais recentes e os hotfixes relacionados ao desempenho, pois eles frequentemente incluem atualizações para índices do sistema. Consulte Dicas [de ajuste de desempenho | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) para algumas otimizações de índice que podem ser aplicadas, dependendo da sua versão do AEM.

Crie índices personalizados para query executados com frequência. Para obter detalhes, consulte a [metodologia para analisar query](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) lentos e [criar índices](/help/sites-deploying/queries-and-indexing.md)personalizados. Para obter informações adicionais sobre as práticas recomendadas de query e índice, consulte Práticas [recomendadas para Query e indexação](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Configurações do índice Lucene {#lucene-index-configurations}

Algumas otimizações podem ser feitas nas configurações de índice Oak que podem ajudar a melhorar o desempenho do AEM Assets:

Atualize a configuração de LuceneIndexProvider:

1. Navegue até /system/console/configMgrorg.apache.Jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Ative os arquivos **[!UICONTROL de índice]** CopyOnRead, CopyOnWrite e Prefetch nas versões anteriores ao AEM 6.2. Esses valores são ativados por padrão no AEM 6.2 e versões posteriores.

Atualize as configurações de índice para melhorar o tempo de reindexação:

1. Abra o CRXDe /crx/de/index.jsp e faça logon como um usuário administrativo
1. Navegue até /oak:index/lucene
1. Adicionar uma propriedade String[] chamada **[!UICONTROL excludePaths]** com valores &quot;/var&quot;, &quot;/etc/workflow/instance&quot; e &quot;/etc/Replication&quot;
1. Navegue até /oak:index/damAssetLucene
1. Adicionar uma propriedade String[] chamada **[!UICONTROL includePaths]** com um valor &quot;/content/dam&quot;
1. Salvar

(Somente AEM6.1 e 6.2) Atualize o índice ntBaseLucene para melhorar o desempenho de exclusão e movimentação de ativos:

1. Navegue até */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Adicione dois nós não estruturados **[!UICONTROL slingResource]** e **[!UICONTROL damResolvedPath]** em */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Defina as propriedades abaixo nos nós (onde as propriedades order e propertyIndex são do tipo *Boolean*:

   slingResource

   name=&quot;sling:resource&quot;

   order=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvePath&quot;

   order=false

   propertyIndex=true

   type=&quot;String&quot;

1. No nó /oak:index/ntBaseLucene, defina a propriedade `reindex=true`
1. Clique em **[!UICONTROL Salvar tudo]**
1. Monitore o error.log para ver quando a indexação é concluída:

   Reindexação concluída para índices: [/oak:index/ntBaseLucene]

1. Você também pode ver que a indexação foi concluída atualizando o nó /oak:index/ntBaseLucene no CRXDe, pois a propriedade reindex voltaria para false
1. Quando a indexação for concluída, volte para CRXDe e defina a propriedade **[!UICONTROL type]** como desativada nesses dois índices

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Clique em **[!UICONTROL Salvar tudo]**

Desativar Extração de texto de Lucene:

Se os usuários não precisarem pesquisar o conteúdo de ativos, por exemplo, pesquisar o texto contido em documentos PDF, você poderá melhorar o desempenho do índice desabilitando esse recurso.

1. Vá para o gerenciador de pacote AEM /crx/packmgr/index.jsp
1. Carregue e instale o pacote abaixo

[Obter arquivo](assets/disable_indexingbinarytextextraction-10.zip)

### Total de suposições {#guess-total}

Ao criar query que geram grandes conjuntos de resultados, use o `guessTotal` parâmetro para evitar a utilização de memória pesada ao executá-los.

## Problemas conhecidos {#known-issues}

### Arquivos grandes {#large-files}

Há dois problemas conhecidos principais relacionados a arquivos grandes no AEM. Quando os arquivos atingem tamanhos superiores a 2 GB, a sincronização em espera fria pode ocorrer em uma situação de falta de memória. Em alguns casos, impede que a sincronização em espera seja executada. Em outros casos, isso faz com que a instância primária falhe. Esse cenário se aplica a qualquer arquivo em AEM maior que 2 GB, incluindo pacotes de conteúdo.

Da mesma forma, quando os arquivos atingem 2GB ao usar um armazenamento de dados S3 compartilhado, pode levar algum tempo para que o arquivo seja totalmente persistente do cache para o sistema de arquivos. Como resultado, ao usar replicação sem binários, é possível que os dados binários não tenham sido persistentes antes da conclusão da replicação. Essa situação pode levar a problemas, especialmente se a disponibilidade de dados for importante, por exemplo, em cenários de descarregamento.

## Teste de desempenho {#performance-testing}

Para cada implantação AEM, estabeleça um regime de teste de desempenho que possa identificar e resolver gargalos rapidamente. Aqui estão algumas áreas-chave para se focar.

### Teste de rede {#network-testing}

Para todas as preocupações de desempenho de rede do cliente, execute as seguintes tarefas:

* Teste o desempenho da rede na rede do cliente
* Teste o desempenho da rede a partir da rede Adobe. Para clientes do AMS, trabalhe com seu CSE para testar a partir da rede do Adobe.
* Testar o desempenho da rede de outro ponto de acesso
* Usando uma ferramenta de benchmark de rede
* Teste contra o expedidor

### Teste de instância AEM {#aem-instance-testing}

Para minimizar a latência e alcançar alta throughput por meio da utilização eficiente da CPU e do compartilhamento de carga, monitore regularmente o desempenho da instância AEM. Nomeadamente:

* Executar testes de carga na instância AEM
* Monitore o desempenho de upload e a capacidade de resposta da interface do usuário

## Lista de verificação de desempenho AEM Assets {#aem-assets-performance-checklist}

* Ative o HTTPS para contornar qualquer farejador de tráfego HTTP corporativo.
* Use uma conexão com fio para fazer upload de ativos pesados.
* Defina os parâmetros JVM ideais.
* Configure um DataStore do sistema de arquivos ou um S3 DataStore.
* Desabilitar a geração de subativos. Se estiver ativado, AEM fluxo de trabalho cria um ativo separado para cada página em um ativo de várias páginas. Cada uma dessas páginas é um ativo individual que consome mais espaço em disco, requer controle de versão e processamento de fluxo de trabalho adicional. Se você não precisar de páginas separadas, desabilite a geração de subativos e atividades de extração de página.
* Ative workflows transitórios.
* Ajuste as filas de fluxo de trabalho Granite para limitar as tarefas simultâneas.
* Configure ImageMagick para limitar o consumo de recursos.
* Remova etapas desnecessárias do fluxo de trabalho Atualizar ativo do DAM.
* Configure o fluxo de trabalho e a remoção de versão.
* Otimizar a configuração de índice do Lucene.
* Otimize índices com os service packs e hotfixes mais recentes. Consulte o Atendimento ao cliente do Adobe para obter outras otimizações de índice que possam estar disponíveis.
* Use `guessTotal` para otimizar o desempenho do query.
* If you configure AEM to detect file types from the content of the files (by configuring [!UICONTROL Day CQ DAM Mime Type Service] in the [!UICONTROL AEM Web Console]), upload many files in bulk during non-peak hours as the operation is resource-intensive.
