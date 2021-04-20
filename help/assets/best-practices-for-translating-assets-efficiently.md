---
title: Práticas recomendadas para a tradução eficiente de ativos
description: Práticas recomendadas para o gerenciamento eficiente de ativos para sincronizar várias versões traduzidas e simplificar os fluxos de trabalho de tradução.
contentOwner: AG
feature: Translation
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---


# Práticas recomendadas para converter ativos com eficiência {#best-practices-for-translating-assets-efficiently}

O Adobe Experience Manager (AEM) Assets oferece suporte a fluxos de trabalho multilíngues para traduzir binários, metadados e tags de ativos digitais em vários locais e gerenciar os ativos traduzidos. Para obter detalhes, consulte [Ativos multilíngues](multilingual-assets.md).

Para o gerenciamento eficiente de ativos para garantir que diferentes versões traduzidas permaneçam sincronizadas, crie [cópias de idioma](preparing-assets-for-translation.md) de ativos antes de executar fluxos de trabalho de tradução.

Uma cópia de idioma de um ativo ou de um grupo de ativos é um idioma irmão (ou uma versão do(s) ativo(s) em uma linguagem cognitiva) com uma hierarquia de conteúdo semelhante.

Cada cópia de idioma é um ativo independente. Portanto, traduzir ativos em várias localidades pode aumentar drasticamente o tamanho do repositório CRX. Por exemplo, traduzir ativos com um tamanho combinado de 10 GB em dois idiomas pode aumentar o tamanho do repositório em aproximadamente 20 GB (10 GB para cada idioma).

Os binários de ativos ocupam um espaço de armazenamento muito maior em comparação aos metadados e tags. Portanto, se a tradução de metadados e tags servir apenas à sua finalidade, omita para traduzir os binários. Você pode reter a cópia original dos binários no repositório para associação com metadados e tags traduzidos para diferentes locais. Manter uma única cópia de binários, em vez de várias versões traduzidas, minimiza o impacto no tamanho do repositório.

O File Data Store e o Amazon S3 Data Store fornecem uma infraestrutura de armazenamento mais adequada para esses cenários. Esses repositórios de armazenamento armazenam uma única cópia de binários de ativos (incluindo representações) que podem ser compartilhados por metadados e tags em várias localidades. Portanto, criar cópias de idioma de ativo e traduzir metadados e tags não afeta o tamanho do repositório.

Você também pode fazer algumas alterações na configuração de alguns fluxos de trabalho e na estrutura de integração de tradução para simplificar ainda mais o processo.

1. Faça uma das seguintes opções:

   * [Configurar Arquivo Data Store](/help/sites-deploying/data-store-config.md)
   * [Configurar o Data Store do Amazon S3](/help/sites-deploying/data-store-config.md)

1. Desative o workflow [DAM MetaData Writeback](/help/sites-administering/workflow-offloader.md#disable-offloading)

   Como o nome sugere, o workflow *DAM Metadata Writeback* reescreve os metadados para o arquivo binário. Como os metadados mudam após a tradução, a gravação de volta no arquivo binário gera um binário diferente para uma cópia de idioma.

   >[!NOTE]
   >
   >Desativar o fluxo de trabalho *DAM MetaData Writeback* desativa XMP gravação de metadados em binários de ativos. Consequentemente, alterações futuras de metadados não são mais salvas nos ativos. Avalie as consequências antes de desabilitar esse workflow.

1. Habilite o workflow *Definir data da última modificação*.

   O workflow *DAM MetaData Writeback* configura a data da última modificação para um ativo. Como você desativa esse fluxo de trabalho na etapa 2, a AEM Assets não é mais capaz de manter a data da última modificação dos ativos atualizada. Portanto, ative o workflow *Definir data da última modificação* para garantir que as datas da última modificação dos ativos estejam atualizadas. Os ativos com datas da última modificação desatualizadas podem causar erros.

1. [Configure a ](/help/sites-administering/tc-tic.md) estrutura de integração de tradução para parar a tradução de binários de ativos. Desmarque a opção &quot;Traduzir ativos&quot; na guia Ativos para interromper a tradução dos binários do ativo.
1. Traduza metadados/tags de ativos usando [Fluxos de trabalho de ativos multilíngues](multilingual-assets.md).

