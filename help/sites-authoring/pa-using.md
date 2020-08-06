---
title: Visualizar dados de análise de página
seo-title: Visualizar dados de análise de página
description: Use dados de análise de página para avaliar a eficácia do conteúdo da página
seo-description: Use dados de análise de página para avaliar a eficácia do conteúdo da página
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
translation-type: tm+mt
source-git-commit: e99e29425578005ed9d215946d63f67e7229e8d6
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 93%

---


# Visualizar dados de análise de página{#seeing-page-analytics-data}

Use dados de análise de página para avaliar a eficácia do conteúdo da página.

## Análise visível do console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Dados de análise de página são exibidos na [Visualização de lista](/help/sites-authoring/basic-handling.md#list-view) do console Sites. Quando as páginas são exibidas em formato de lista, as seguintes colunas estão disponíveis por padrão:

* Exibições da página
* Visitantes únicos
* Tempo na página

Cada coluna mostra um valor para o período de relatório atual e também indica se o valor aumentou ou diminuiu em relação ao período do relatório anterior. Os dados exibidos são atualizados a cada 12 horas.

>[!NOTE]
>
>Para alterar o período de atualização, [configure o intervalo de importação](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Abra o console **Sites**, por exemplo, [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. Na extremidade direita da barra de ferramentas (canto superior direito), clique ou toque no ícone para selecionar **Visualização de lista** (o ícone mostrado dependerá da [visualização atual](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Novamente, na extremidade direita da barra de ferramentas (canto superior direito), clique ou toque no ícone e selecione **Configurações de exibição**. A caixa de diálogo **Configurar colunas** será aberta. Faça as alterações necessárias e confirme com **Atualizar**.

   ![aa-04](assets/aa-04.png)

### Seleção do período de relatório {#selecting-the-reporting-period}

Selecione o período de relatório para o qual os dados de Analítica devem aparecer no console Sites:

* Dados dos últimos 30 dias
* Dados dos últimos 90 dias
* Dados deste ano

O período do relatório atual aparece na barra de ferramentas do console Sites (à direita da barra de ferramentas superior). Use o menu suspenso para selecionar o período de relatório necessário.\
![aa-05](assets/aa-05.png)

### Configurar colunas de dados disponíveis {#configuring-available-data-columns}

Os membros do grupo de usuários análise-administradores podem configurar o console Sites para permitir que os autores vejam colunas de análise adicionais.

>[!NOTE]
>
>Quando uma árvore de páginas contém páginas secundárias associadas a diferentes configurações de nuvem do Adobe Analytics, você não pode configurar as colunas de dados disponíveis para as páginas.

1. No modo de Exibição de lista, use os seletores de exibição (à direita da barra de ferramentas), selecione **Exibir configurações** e, em seguida, **Adicionar dados do Analytics**.

   ![aa-15](assets/aa-15.png)

1. Selecione as métricas que deseja expor aos autores do console Sites e clique em **Adicionar**.

   As colunas que aparecem são recuperadas do Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Abrir Content Insight do Sites {#opening-content-insights-from-sites}

Open [Content Insight](/help/sites-authoring/content-insights.md) from the Sites console to further investigate page effectiveness.

1. No console Sites, selecione a página para da qual você deseja ver os Content Insights.
1. Na barra de ferramentas, clique no ícone Analytics e Recomendações.

   ![](do-not-localize/chlimage_1-16.png)

## Análise visível do Editor de página (Mapa de atividades) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Devido a alterações de segurança na API do Adobe Analytics, não é mais possível usar a versão do Activity Map incluída no AEM.
>
>The [ActivityMap plugin provided by Adobe Analytics](https://docs.adobe.com/content/help/br/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used.
