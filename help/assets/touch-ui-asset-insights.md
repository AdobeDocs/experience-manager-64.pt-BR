---
title: Use o recurso do Assets Insights para rastrear o uso de suas imagens
description: O recurso do Assets Insights permite que você acompanhe as estatísticas de usuário e uso de imagens usadas em sites de terceiros, campanhas de marketing e soluções criativas de classificações do Adobe.
contentOwner: AG
feature: Insights de ativos,Relatórios de ativos
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 7%

---

# Insights de ativos {#asset-insights}

Saiba como o recurso Insights do Assets permite que você acompanhe as classificações de usuários e as estatísticas de uso de ativos usados em sites de terceiros, campanhas de marketing e soluções criativas do Adobe.

O Assets Insights permite que você acompanhe as estatísticas de classificação e uso de ativos usados em campanhas de marketing de terceiros e nas soluções criativas de sites do Adobe para obter insights sobre o desempenho e a popularidade.

O Assets Insights captura detalhes da atividade do usuário, como o número de vezes que um ativo é avaliado, clicado e impressões (número de vezes que o ativo é carregado no site). Ela atribui pontuações a ativos com base nessas estatísticas. Você pode usar as pontuações e as estatísticas de desempenho para selecionar os ativos mais populares para inclusão em catálogos, campanhas de marketing e assim por diante. Você pode até mesmo formular políticas de renovação de arquivos e licenças para ativos com base nessas estatísticas.

Para que o Assets Insights capture as estatísticas de uso de ativos de um site, você deve incluir o código incorporado do ativo no código do site.

Para permitir que o Assets Insights exiba estatísticas de uso de ativos, primeiro configure o recurso para buscar dados de relatório de [!DNL Adobe Analytics]. Para obter detalhes, consulte [Configurar o Assets Insights](touch-ui-configuring-asset-insights.md). Para usar esse recurso em uma instalação local, compre a licença [!DNL Adobe Analytics] separadamente. Os clientes em [!DNL Managed Services] recebem [!DNL Analytics] licença fornecida com [!DNL Experience Manager]. Consulte [Descrição do produto Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Os insights são suportados e fornecidos apenas para imagens.

## Exibir estatísticas de um ativo {#viewing-statistics-for-an-asset}

Você pode exibir as pontuações do Assets Insights da página de metadados.

1. Na interface do usuário do Assets (UI), selecione o ativo e toque/clique no ícone **[!UICONTROL Propriedades]** na barra de ferramentas.
1. Na página Propriedades, toque/clique na guia **[!UICONTROL Insights]**.
1. Revise os detalhes de uso do ativo na guia **[!UICONTROL Insights]**. A seção **[!UICONTROL Pontuação]** descreve o uso total de ativos e as funções de desempenho de um ativo.

   A pontuação de uso descreve a quantidade de vezes que o ativo é usado em várias soluções.

   A pontuação **[!UICONTROL Impressões]** é o número de vezes que o ativo é carregado no site. O número exibido em **[!UICONTROL Clicks]** é o número de vezes que o ativo é clicado.

1. Revise a seção **[!UICONTROL Estatísticas de uso]** para saber quais entidades o ativo fazia parte e quais soluções criativas o usaram recentemente. Quanto maior for o uso, maior será a probabilidade de o ativo ser popular entre os usuários. Os dados de uso são exibidos abaixo dos seguintes cabeçalhos:

   * **[!UICONTROL Ativo]**: O número de vezes que o ativo fez parte de uma coleção ou de um ativo composto
   * **[!UICONTROL Web e móvel]**: O número de vezes que o ativo foi parte de sites e aplicativos
   * **[!UICONTROL Social]**: O número de vezes que o ativo foi usado em soluções, como Adobe Social e Adobe Campaign
   * **[!UICONTROL Email]**: O número de vezes que o ativo foi usado em campanhas de email

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >O recurso do Assets Insights busca os dados das soluções de [!DNL Adobe Analytics] de maneira periódica, a seção de soluções pode não exibir os dados mais recentes. O período de tempo para o qual os dados são exibidos depende do agendamento da operação de busca que o Assets Insights executa para recuperar dados [!DNL Analytics].

1. Para exibir estatísticas de desempenho do ativo graficamente durante um período de tempo, selecione o período na seção **[!UICONTROL Estatísticas de desempenho]**. Detalhes, incluindo cliques e impressões, são exibidos como linhas de tendência de um gráfico.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Ao contrário dos dados na seção soluções , a seção estatísticas de desempenho exibe os dados mais recentes.

1. Para obter o código incorporado do ativo que você inclui nos sites para obter dados de desempenho, clique em **[!UICONTROL Obter código incorporado]** abaixo da miniatura do ativo. Para obter mais informações sobre como incluir o código Incorporado em páginas da Web de terceiros, consulte [Usar o rastreador de páginas e Incorporar código em páginas da Web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Exibir estatísticas agregadas de ativos {#viewing-aggregate-statistics-for-assets}

Exiba pontuações de todos os ativos em uma pasta simultaneamente usando a **[!UICONTROL Exibição do Insights]**.

1. Na interface do usuário do Assets, navegue até a pasta que contém os ativos para os quais deseja exibir insights.
1. Toque/clique no ícone Layout na barra de ferramentas e escolha **[!UICONTROL Exibição do Insights]**.
1. A página exibe as pontuações de uso dos ativos. Compare as classificações dos vários ativos e obtenha insights.

## Agendar tarefa em segundo plano {#scheduling-background-job}

O Assets Insights busca dados de uso de ativos dos conjuntos de relatórios do Adobe Analytics de maneira periódica. Por padrão, o Assets Insights executa um trabalho em segundo plano a cada 24 horas às 2:00 AM para buscar dados. No entanto, você pode modificar a frequência e o tempo configurando o serviço **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** do console da Web.

1. Toque no logotipo do AEM e acesse **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. Abra a configuração do serviço **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique a frequência do agendador desejada e a hora de início da tarefa na expressão do agendador de propriedades. Salve as alterações.
