---
title: Pesquisar ativos no AEM
description: Saiba como localizar os ativos necessários em [!DNL Experience Manager] usando o painel Filtros e como usar os ativos que aparecem na pesquisa.
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---

# Pesquisar ativos em [!DNL Experience Manager] {#search-assets-in-aem}

Saiba como encontrar os ativos necessários em [!DNL Experience Manager] usando o painel Filtros e como usar os ativos exibidos na pesquisa.

Use o painel Filtros para pesquisar ativos, pastas, tags e metadados. Você pode pesquisar partes de uma string usando o asterisco curinga.

O painel Filtros fornece várias opções para procurar ativos e pastas de várias maneiras, em vez de em uma ordem taxonômica genérica.

Você pode pesquisar com base nas seguintes opções (predicados):

* Tipo de arquivo
* Tamanho de arquivo
* Nome do campo
* Última modificação
* Status
* Orientação
* Estilo
* Insights

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

Você pode personalizar o painel Filtros e adicionar/remover predicados de pesquisa usando [facetas de pesquisa](search-facets.md). Para exibir o painel Filtros, execute estas etapas:

1. Na interface do usuário do Assets, toque/clique em ![search_icon](assets/search_icon.png) na barra de ferramentas para exibir a caixa Omnisearch.
1. Insira o termo de pesquisa e pressione Enter. Como alternativa, basta pressionar Enter sem inserir qualquer termo de pesquisa. Não insira espaços à esquerda; caso contrário, a pesquisa não funcionará.

1. Toque/clique no ícone de Navegação global. O painel Filtros é exibido.

   ![filters_panel-1](assets/filters_panel-1.png)

   Dependendo do tipo de itens que você pesquisar, o número de correspondências é indicado na parte superior dos resultados da pesquisa.

   ![number_of_search](assets/number_of_searches.png)

## Pesquisar tipos de arquivo {#search-for-file-types}

O painel Filtros ajuda a adicionar mais granularidade à sua experiência de pesquisa e torna a funcionalidade de pesquisa mais versátil. Você pode detalhar facilmente até o nível de detalhes desejado.

Por exemplo, se estiver procurando uma imagem, use o predicado **[!UICONTROL Tipo de arquivo]** para escolher se deseja uma imagem de bitmap ou uma imagem vetorial.

![image_type](assets/image_type.png)

Você pode limitar ainda mais o escopo da pesquisa especificando o tipo MIME da imagem.

![mime_type](assets/mime_type.png)

Da mesma forma, ao pesquisar documentos, é possível especificar o formato, por exemplo PDF ou MS Word.

![documentos](assets/documents.png)

## Pesquisar com base no tamanho do arquivo {#search-based-on-file-size}

Use o predicado **Tamanho do arquivo** para procurar ativos com base em seu tamanho. Você pode especificar os limites inferiores e superiores para o intervalo de tamanho para restringir sua pesquisa. Você também pode especificar a unidade de medida, por exemplo Kilobytes, Megabytes e assim por diante.

![unit_of_measure](assets/unit_of_measure.png)

## Pesquisar com base em quando os ativos foram modificados pela última vez {#search-based-on-when-assets-are-last-modified}

Se você estiver gerenciando ativos do trabalho em andamento ou monitorando um fluxo de trabalho de revisão, poderá pesquisar quando um ativo foi modificado pela última vez com base em carimbos de data e hora precisos. Por exemplo, especifique datas antes ou depois de quais os ativos foram modificados.

![last_modified_dates](assets/last_modified_dates.png)

Você também pode usar as seguintes opções para alcançar um nível mais alto de granularidade em sua pesquisa:

![timestamp](assets/timestamp.png)

## Pesquisar com base no status {#search-based-on-status}

Use o predicado **Status** para pesquisar ativos com base em vários tipos de status, como Publicar, Aprovação, Check-out e Expiração.

![status](assets/status.png)

Por exemplo, ao monitorar a publicação de ativos, você pode usar a opção apropriada para pesquisar por quais ativos são publicados.

![Publicar](assets/publish.png)

Ao monitorar o status de revisão de ativos, use a opção apropriada para descobrir quais ativos estão aprovados ou quais ativos estão pendentes de aprovação.

![aprovação](assets/approval.png)

## Pesquisar com base nos dados de insights {#search-based-on-insights-data}

Use o predicado **Insights** para pesquisar ativos com base em suas estatísticas de uso obtidas de vários aplicativos Creative. Os dados de uso são agrupados nas seguintes categorias:

* Pontuação de uso
* Impressões
* Cliques
* Canais de mídia nos quais os ativos aparecem

![insights](assets/insights.png)
