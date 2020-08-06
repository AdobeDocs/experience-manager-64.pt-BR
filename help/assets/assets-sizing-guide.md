---
title: Guia de dimensionamento de ativos
description: 'Práticas recomendadas para determinar métricas eficientes para estimar a infraestrutura e os recursos necessários para a implantação do AEM Assets. '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
translation-type: tm+mt
source-git-commit: 6aec5927c00f70ce2c044ffd56cabbf68a81071a
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 0%

---


# Guia de dimensionamento de ativos {#assets-sizing-guide}

Ao dimensionar o ambiente para uma implementação do Adobe Experience Manager (AEM) Assets, é importante garantir que haja recursos suficientes disponíveis em termos de disco, CPU, memória, E/S e throughput da rede. Dimensionar muitos desses recursos requer uma compreensão de quantos ativos estão sendo carregados no sistema. Se uma métrica melhor não estiver disponível, é possível dividir o tamanho da biblioteca existente pela idade da biblioteca para localizar a taxa na qual os ativos são criados.

## Disco {#disk}

### DataStore {#datastore}

Um erro comum cometido ao dimensionar o espaço em disco necessário para uma implementação do Assets é basear os cálculos no tamanho das imagens brutas a serem ingeridas no sistema. Por padrão, AEM cria três execuções além da imagem original para uso na renderização dos elementos da interface AEM. Em implementações anteriores, essas execuções assumiram o dobro do tamanho dos ativos que são assimilados.

A maioria dos usuários define representações personalizadas, além de execuções prontas. Além das execuções, a AEM Assets permite que você extraia subativos de tipos de arquivos comuns, como InDesign e Illustrator.

Por fim, os recursos de controle de versão do AEM armazenam duplicados dos ativos no histórico de versões. Você pode configurar as versões a serem removidas com frequência. Entretanto, muitos usuários optam por reter versões no sistema por um longo tempo, o que consome mais espaço no armazenamento.

Considerando esses fatores, você precisa de uma metodologia para calcular um espaço de armazenamento com precisão aceitável para armazenar os ativos do usuário.

1. Determine o tamanho e o número de ativos que serão carregados no sistema.
1. Obtenha uma amostra representativa dos ativos a serem carregados no AEM. Por exemplo, se você planeja carregar arquivos PSD, JPG, AI e PDF no sistema, é necessário várias imagens de amostra de cada formato de arquivo. Além disso, essas amostras devem ser representativas dos diferentes tamanhos de arquivo e complexidades das imagens.
1. Defina as representações a serem usadas.
1. Crie as execuções no AEM usando os aplicativos ImageMagick ou Adobe. Além das representações que os usuários especificam, crie execuções prontas para uso. Para usuários que implementam o Scene7, você pode usar o binário IC para gerar as execuções PTIFF a serem armazenadas no AEM.
1. Se você planeja usar subativos, gere-os para os tipos de arquivo apropriados. Consulte a documentação on-line sobre como gerar páginas de subativos de arquivos de InDesign ou arquivos PNG/PDF de camadas do Illustrator.
1. Compare o tamanho das imagens de saída, representações e subativos com as imagens originais. Ele permite gerar um fator de crescimento esperado quando o sistema é carregado. Por exemplo, se você gerar representações e subativos com um tamanho combinado de 3 GB após o processamento de 1 GB de ativos, o fator de crescimento da representação será 3.
1. Determine o tempo máximo durante o qual as versões de ativos devem ser mantidas no sistema.
1. Determine com que frequência os ativos existentes são modificados no sistema. Se AEM for usado como um hub de colaboração em workflows criativos, a quantidade de alterações é alta. Se apenas os ativos finalizados forem carregados no sistema, esse número será muito menor.
1. Determine quantos ativos são carregados no sistema a cada mês. Se não tiver certeza, verifique o número de ativos que estão disponíveis no momento e divida o número pela idade do ativo mais antigo para calcular um número aproximado.

A execução das etapas 1 a 9 ajuda a determinar o seguinte:

* Tamanho bruto dos ativos a carregar
* Número de ativos a serem carregados
* Fator de crescimento da renderização
* Número de modificações de ativos feitas por mês
* Número de meses para manter versões de ativos
* Número de novos ativos carregados mensalmente
* Anos de crescimento para alocar espaço para

Você pode especificar esses números na planilha Dimensionamento de rede para determinar o espaço total necessário para o armazenamento de dados. Também é uma ferramenta útil para determinar o impacto da manutenção de versões de ativos ou da modificação de ativos em AEM sobre o crescimento do disco.

O exemplo de dados preenchido na ferramenta demonstra a importância de executar as etapas mencionadas. Se você dimensionar o armazenamento de dados com base apenas nas imagens brutas carregadas (1 TB), talvez tenha subestimado o tamanho do repositório em um fator de 15.

[Obter arquivo](assets/disk_sizing_tool.xlsx)

### Armazenamento de dados compartilhado {#shared-datastores}

Para grandes armazenamentos de dados, você pode implementar um armazenamento de dados compartilhado por meio de um armazenamento de dados de arquivo compartilhado em uma unidade conectada à rede ou por meio de um armazenamento de dados S3. Nesse caso, as instâncias individuais não precisam manter uma cópia dos binários. Além disso, um armazenamento de dados compartilhado facilita a replicação sem binários e ajuda a reduzir a largura de banda usada para replicar ativos para publicar ambientes ou descarregar instâncias.

#### Use Cases {#use-cases}

O armazenamento de dados pode ser compartilhado entre uma instância de autor principal e em espera para minimizar o tempo necessário para atualizar a instância em espera com as alterações feitas na instância principal. O Adobe recomenda compartilhar o armazenamento de dados entre uma instância do autor principal e descarregar instâncias do autor para reduzir os custos indiretos na descarga do fluxo de trabalho. Você também pode compartilhar o armazenamento de dados entre as instâncias de autor e publicação para minimizar o tráfego durante a replicação.

#### Desvantagens {#drawbacks}

Devido a algumas armadilhas, o compartilhamento de um armazenamento de dados não é recomendado em todos os casos.

#### Ponto único de falha {#single-point-of-failure}

Com um armazenamento de dados compartilhado, apresenta um único ponto de falha em uma infraestrutura. Considere um cenário em que seu sistema tenha uma e duas instâncias de publicação, cada uma com seu próprio armazenamento de dados. Se algum deles falhar, os outros dois ainda poderão continuar em execução. No entanto, se o armazenamento de dados for compartilhado, uma única falha de disco poderá derrubar toda a infraestrutura. Portanto, certifique-se de manter um backup do armazenamento de dados compartilhado de onde você pode restaurar o armazenamento de dados rapidamente.

É preferível implantar o serviço AWS S3 para armazenamentos de dados compartilhados, pois reduz significativamente a probabilidade de falha em comparação às arquiteturas de disco normais.

#### Maior complexidade {#increased-complexity}

Os armazenamentos de dados compartilhados também aumentam a complexidade das operações, como a coleta de lixo. Normalmente, a coleta de lixo para um armazenamento de dados independente pode ser iniciada com um único clique. No entanto, os armazenamentos de dados compartilhados exigem operações de varredura de marca em cada membro que usa o armazenamento de dados, além de executar a coleção real em um único nó.

Para operações AWS, a implementação de um único local central (via S3), em vez de construir uma matriz RAID de volumes EBS, pode compensar significativamente a complexidade e os riscos operacionais no sistema.

#### Problemas de desempenho {#performance-concerns}

Um armazenamento de dados compartilhado exige que os binários sejam armazenados em uma unidade montada em rede que seja compartilhada entre todas as instâncias. Como esses binários são acessados em uma rede, o desempenho do sistema é afetado negativamente. Você pode atenuar parcialmente o impacto usando uma conexão de rede rápida para um array rápido de discos. No entanto, esta é uma proposta dispendiosa. No caso de operações AWS, todos os discos são remotos e exigem conectividade de rede. Os volumes efêmeros perdem dados quando a instância é start ou interrompida.

#### Latência {#latency}

A latência em implementações S3 é introduzida pelos threads de escrita em segundo plano. Os procedimentos de backup devem levar em conta essa latência e quaisquer procedimentos de descarga. O ativo S3 pode não estar presente no S3 quando um start de trabalho de descarregamento é desativado. Além disso, os índices Lucene podem ficar incompletos ao fazer um backup. Ele se aplica a qualquer arquivo que faz distinção de tempo gravado no armazenamento de dados S3 e acessado de outra instância.

### Loja de nós/Loja de Documentos {#node-store-document-store}

É difícil obter números precisos de dimensionamento para um NodeStore ou DocumentStore devido aos recursos consumidos pelos seguintes:

* Metadados do ativo
* Versões de ativos
* Logs de auditoria
* workflows arquivados e ativos

Como os binários são armazenados no armazenamento de dados, cada binário ocupa algum espaço. A maioria dos repositórios tem menos de 100 GB. No entanto, pode haver repositórios maiores de até 1 TB de tamanho. Além disso, para executar compactação offline, é necessário espaço livre suficiente no volume para regravar o repositório compactado junto com a versão pré-compactada. Uma boa regra é dimensionar o disco para 1,5 vezes o tamanho esperado para o repositório.

Para o repositório, use SSDs ou discos com um nível IOPS superior a 3000. Para eliminar as chances de o IOPS introduzir gargalos no desempenho, monitore os níveis de espera de E/S da CPU para obter os primeiros sinais de problemas.

[Obter arquivo](assets/aem_environment_sizingtool.xlsx)

## Rede {#network}

A AEM Assets tem vários casos de uso que tornam o desempenho da rede mais importante do que em muitos de nossos projetos AEM. Um cliente pode ter um servidor rápido, mas se a conexão de rede não for grande o suficiente para suportar a carga dos usuários que estão carregando e baixando ativos do sistema, ele ainda parecerá estar lento. Há uma boa metodologia para determinar o ponto de bloqueio na conexão de rede de um usuário para AEM em [AEM considerações de ativos para experiência do usuário, dimensionamento de instância, avaliação de fluxo de trabalho e topologia](assets-network-considerations.md)de rede.

## WebDAV {#webdav}

Se você adicionar o aplicativo de desktop AEM ao mix, os problemas de rede se tornam mais graves devido a ineficiências no protocolo WebDAV.

Para ilustrar essas ineficiências, o Adobe testou o desempenho do sistema usando o WebDAV no OS X. Um arquivo de InDesign de 3,5 MB foi aberto, editado e as alterações foram salvas. Foram feitas as seguintes observações:

* Total de cerca de 100 solicitações HTTP geradas para concluir a operação
* O arquivo foi carregado quatro vezes por HTTP
* O arquivo foi baixado uma vez por HTTP
* A operação inteira levou 42 segundos para ser concluída
* Um total de dados de 18 MB foi transferido

Ao analisar o tempo médio de economia para arquivos via WebDAV, descobriu-se que o desempenho aumenta drasticamente à medida que a largura de banda aumenta até o nível de 5 a 10 Mbps. Portanto, a Adobe recomenda que cada usuário que acessa o sistema simultaneamente tenha pelo menos 10 Mbps de velocidade de carregamento e 5 a 10 Mbps de largura de banda.

Para obter mais informações, consulte [Solução de problemas AEM aplicativo](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)para desktop.

## Limitações           {#limitations}

Ao dimensionar uma implementação, é importante ter em mente as limitações do sistema. Se a implementação proposta exceder essas limitações, empregue estratégias criativas, como a divisão dos ativos em várias implementações de Ativos.

O tamanho do arquivo não é o único fator que contribui para problemas de falta de memória (OOM). Também depende das dimensões da imagem. Você pode evitar problemas de OOM fornecendo um tamanho de heap mais alto ao start de AEM.

Além disso, você pode editar a propriedade de tamanho limite do `com.day.cq.dam.commons.handler.StandardImageHandler` componente no Configuration Manager para usar um arquivo temporário intermediário maior que zero.

## Número máximo de ativos {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

O limite para o número de arquivos que podem existir em um armazenamento de dados pode ser de 2,1 bilhões devido às limitações do sistema de arquivos. É provável que o repositório encontre problemas devido ao grande número de nós muito antes de atingir o limite do armazenamento de dados.

Se as renderizações forem geradas incorretamente, use a biblioteca Camera Raw. Entretanto, nesse caso, o lado mais longo da imagem não deve ser maior que 65000 pixels. Além disso, a imagem não deve conter mais de 512 MP (512 &amp;ast; 1024 &amp;ast; 1024 pixels)&#39;. *O tamanho do ativo é inconsequente*.

É difícil estimar com precisão o tamanho do arquivo TIFF compatível out-of-the-box (OOTB) com um heap específico para AEM porque fatores adicionais, como o tamanho dos pixels, influenciam o processamento. É possível que AEM possa processar um arquivo com 255 MB de OOTB, mas não possa processar um tamanho de arquivo de 18 MB, já que este último é composto por um número invulgarmente maior de pixels em comparação ao primeiro.

## Tamanho dos ativos {#size-of-assets}

Por padrão, AEM permite carregar ativos de tamanhos de arquivos de até 2 GBs. Para fazer upload de ativos muito grandes no AEM, consulte [Configuração para fazer upload de ativos](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)muito grandes.
