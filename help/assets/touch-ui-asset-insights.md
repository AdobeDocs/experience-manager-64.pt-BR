---
title: Use o recurso do Assets Insights para rastrear o uso de suas imagens
description: O recurso do Assets Insights permite que você acompanhe as estatísticas de usuário e uso de imagens usadas em sites de terceiros, campanhas de marketing e soluções criativas de classificações do Adobe.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 6%

---

# Insights de ativos {#asset-insights}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como o recurso Insights do Assets permite que você acompanhe as classificações de usuários e as estatísticas de uso de ativos usados em sites de terceiros, campanhas de marketing e soluções criativas do Adobe.

O Assets Insights permite que você acompanhe as estatísticas de classificação e uso de ativos usados em campanhas de marketing de terceiros e nas soluções criativas de sites do Adobe para obter insights sobre o desempenho e a popularidade.

O Assets Insights captura detalhes da atividade do usuário, como o número de vezes que um ativo é avaliado, clicado e impressões (número de vezes que o ativo é carregado no site). Ela atribui pontuações a ativos com base nessas estatísticas. Você pode usar as pontuações e as estatísticas de desempenho para selecionar os ativos mais populares para inclusão em catálogos, campanhas de marketing e assim por diante. Você pode até mesmo formular políticas de renovação de arquivos e licenças para ativos com base nessas estatísticas.

Para que o Assets Insights capture as estatísticas de uso de ativos de um site, você deve incluir o código incorporado do ativo no código do site.

Para permitir que o Assets Insights exiba as estatísticas de uso dos ativos, primeiro configure o recurso para buscar dados de relatório do [!DNL Adobe Analytics]. Para obter detalhes, consulte [Configurar o Assets Insights](touch-ui-configuring-asset-insights.md). Para usar esse recurso em uma instalação local, compre [!DNL Adobe Analytics] licença separadamente. Clientes em [!DNL Managed Services] receive [!DNL Analytics] licença fornecida com [!DNL Experience Manager]. Consulte [Descrição do produto Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Os insights são suportados e fornecidos apenas para imagens.

## Exibir estatísticas de um ativo {#viewing-statistics-for-an-asset}

Você pode exibir as pontuações do Assets Insights da página de metadados.

1. Na interface do usuário do Assets (UI), selecione o ativo e toque/clique no botão **[!UICONTROL Propriedades]** ícone na barra de ferramentas.
1. Na página Propriedades , toque/clique no botão **[!UICONTROL Insights]** guia .
1. Revise os detalhes de uso do ativo na **[!UICONTROL Insights]** guia . O **[!UICONTROL Pontuação]** descreve o uso total de ativos e as funções de desempenho de um ativo .

   A pontuação de uso descreve a quantidade de vezes que o ativo é usado em várias soluções.

   O **[!UICONTROL Impressões]** pontuação é o número de vezes que o ativo é carregado no site. O número exibido em **[!UICONTROL Cliques]** é o número de vezes em que o ativo é clicado.

1. Revise o **[!UICONTROL Estatísticas de uso]** seção para saber quais entidades o ativo fez parte e quais soluções criativas o usaram recentemente. Quanto maior for o uso, maior será a probabilidade de o ativo ser popular entre os usuários. Os dados de uso são exibidos abaixo dos seguintes cabeçalhos:

   * **[!UICONTROL Ativo]**: O número de vezes que o ativo fez parte de uma coleção ou de um ativo composto
   * **[!UICONTROL Web e móvel]**: O número de vezes que o ativo foi parte de sites e aplicativos
   * **[!UICONTROL Social]**: O número de vezes que o ativo foi usado em soluções, como Adobe Social e Adobe Campaign
   * **[!UICONTROL Email]**: O número de vezes que o ativo foi usado em campanhas de email

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >O recurso do Assets Insights busca os dados das soluções da [!DNL Adobe Analytics] de maneira periódica, a seção de soluções pode não exibir os dados mais recentes. O período de tempo para o qual os dados são exibidos depende da programação da operação de busca que o Assets Insights executa para recuperar [!DNL Analytics] dados.

1. Para exibir estatísticas de desempenho do ativo graficamente durante um período de tempo, selecione o período na seção **[!UICONTROL Estatísticas de desempenho]**. Detalhes, incluindo cliques e impressões, são exibidos como linhas de tendência de um gráfico.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Ao contrário dos dados na seção soluções , a seção estatísticas de desempenho exibe os dados mais recentes.

1. Para obter o código incorporado do ativo que você inclui nos sites para obter dados de desempenho, clique em **[!UICONTROL Obter código incorporado]** abaixo da miniatura do ativo. Para obter mais informações sobre como incluir o código Incorporado em páginas da Web de terceiros, consulte [Usar o rastreador de página e incorporar código em páginas da Web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Exibir estatísticas agregadas de ativos {#viewing-aggregate-statistics-for-assets}

Exiba pontuações de todos os ativos em uma pasta simultaneamente usando a **[!UICONTROL Exibição do Insights]**.

1. Na interface do usuário do Assets, navegue até a pasta que contém os ativos para os quais deseja exibir insights.
1. Toque/clique no ícone Layout na barra de ferramentas e escolha **[!UICONTROL Exibição de insights]**.
1. A página exibe as pontuações de uso dos ativos. Compare as classificações dos vários ativos e obtenha insights.

## Agendar tarefa em segundo plano {#scheduling-background-job}

O Assets Insights busca dados de uso de ativos dos conjuntos de relatórios do Adobe Analytics de maneira periódica. Por padrão, o Assets Insights executa um trabalho em segundo plano a cada 24 horas às 2:00 AM para buscar dados. No entanto, você pode modificar a frequência e o tempo configurando a variável **[!UICONTROL Trabalho de sincronização de relatórios de desempenho de ativos do Adobe CQ DAM]** do console da Web.

1. Toque no [!DNL Experience Manager] logotipo e acesse **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. Abra o **[!UICONTROL Trabalho de sincronização de relatórios de desempenho de ativos do Adobe CQ DAM]** configuração de serviço.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Especifique a frequência do agendador desejada e a hora de início da tarefa na expressão do agendador de propriedades. Salve as alterações.
