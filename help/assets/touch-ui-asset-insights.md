---
title: Usar o recurso Asset Insights para rastrear o uso de suas imagens
description: O Asset Insights permite que você rastreie as estatísticas de classificação e uso de imagens que são usadas em sites de terceiros, campanhas e soluções criativas de recursos do Adobe.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 8%

---


# Informações de ativos {#asset-insights}

Saiba como o recurso Asset Insights permite rastrear as classificações de usuários e as estatísticas de uso de ativos usados em sites de terceiros, campanhas de marketing e soluções criativas de Adobe.

O Asset Insights permite que você rastreie as classificações e estatísticas de uso de usuários de ativos usados em sites de terceiros, campanhas de marketing e soluções criativas de recursos do Adobe para obter insights sobre o desempenho e a popularidade.

O Assets Insights captura detalhes da atividade do usuário, como o número de vezes que um ativo é classificado, clicado e impressões (número de vezes que o ativo é carregado no site). Atribui pontuações a ativos com base nessas estatísticas. Você pode usar as estatísticas de pontuação e desempenho para selecionar os ativos mais populares para inclusão em catálogos, campanhas de marketing e assim por diante. Você pode até mesmo formular políticas de renovação de arquivos e licenças para ativos com base nessas estatísticas.

Para que o Assets Insights capture as estatísticas de uso de ativos de um site, você deve incluir o código incorporado do ativo no código do site.

Para permitir que o Asset Insights exiba estatísticas de uso de ativos, configure primeiro o recurso para buscar dados de relatórios de [!DNL Adobe Analytics]. Para obter detalhes, consulte [Configurar Insights de Ativos](touch-ui-configuring-asset-insights.md).

>[!NOTE]
>
>Os insights são suportados e fornecidos apenas para imagens.

## Estatísticas de visualização para um ativo {#viewing-statistics-for-an-asset}

Você pode visualização as pontuações do Asset Insights na página de metadados.

1. Na interface do usuário do Assets (UI), selecione o ativo e toque/clique no ícone **[!UICONTROL Propriedades]** na barra de ferramentas.
1. Na página Propriedades, toque/clique na guia **[!UICONTROL Insights]**.
1. Revise os detalhes de uso do ativo na guia **[!UICONTROL Insights]**. A seção **[!UICONTROL Pontuação]** descreve o uso total de ativos e as funções de desempenho de um ativo.

   A pontuação de uso descreve o número de vezes que o ativo é usado em várias soluções.

   A pontuação **[!UICONTROL Impressões]** é o número de vezes que o ativo é carregado no site. O número exibido em **[!UICONTROL Cliques]** é o número de vezes que o ativo é clicado.

1. Revise a seção **[!UICONTROL Estatísticas de uso]** para saber de quais entidades o ativo fazia parte e quais soluções criativas o utilizaram recentemente. Quanto maior o uso, maiores as chances de que o ativo seja popular entre os usuários. Os dados de uso são exibidos sob os seguintes cabeçalhos:

   * **[!UICONTROL Ativo]**: O número de vezes que o ativo fez parte de uma coleção ou de um ativo composto
   * **[!UICONTROL Web e dispositivos móveis]**: O número de vezes que o ativo fez parte de sites e aplicativos
   * **[!UICONTROL Social]**: O número de vezes que o ativo foi usado em soluções, como Adobe Social e Adobe Campaign
   * **[!UICONTROL Email]**: O número de vezes que o ativo foi usado em campanhas de email

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Como o recurso Asset Insights normalmente obtém os dados de Soluções da Adobe Analytics de forma periódica, a seção Soluções pode não exibir os dados mais recentes. O período de tempo para o qual os dados são exibidos depende da programação da operação de busca executada pelo Asset Insights para recuperar os dados do Analytics.

1. Para exibir estatísticas de desempenho do ativo graficamente durante um período de tempo, selecione o período na seção **[!UICONTROL Estatísticas de desempenho]**. Detalhes, incluindo cliques e impressões, são exibidos como linhas de tendência de um gráfico.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Ao contrário dos dados na seção Soluções, a seção Estatísticas de desempenho exibe os dados mais recentes.

1. Para obter o código incorporado para o ativo que você inclui em sites para obter dados de desempenho, toque/clique em **[!UICONTROL Obter código incorporado]** abaixo da miniatura do ativo. Para obter mais informações sobre como incluir o código Incorporado em páginas da Web de terceiros, consulte [Usando o rastreador de páginas e o código Incorporado em páginas da Web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Estatísticas de agregação de visualização para ativos {#viewing-aggregate-statistics-for-assets}

Exiba pontuações de todos os ativos em uma pasta simultaneamente usando a **[!UICONTROL Exibição do Insights]**.

1. Na interface do usuário Ativos, navegue até a pasta que contém os ativos para os quais você deseja visualização insights.
1. Toque/clique no ícone Layout na barra de ferramentas e escolha **[!UICONTROL Visualização do Insights]**.
1. A página exibe as pontuações de uso dos ativos. Compare as classificações dos vários ativos e obtenha insights.

## Agendar tarefa em segundo plano {#scheduling-background-job}

O Asset Insights busca dados de uso de ativos de conjuntos de relatórios da Adobe Analytics de forma periódica. Por padrão, o Asset Insights executa uma tarefa em segundo plano a cada 24 horas às 2 horas da manhã para obter dados. No entanto, você pode modificar a frequência e a hora configurando o serviço **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** do console da Web.

1. Toque no logotipo do AEM e acesse **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. Abra a configuração do serviço **[!UICONTROL Trabalho de sincronização de relatório de desempenho de ativos do Adobe CQ DAM]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique a frequência de scheduler desejada e a hora de start para o trabalho na expressão de scheduler de propriedade. Salve as alterações.
