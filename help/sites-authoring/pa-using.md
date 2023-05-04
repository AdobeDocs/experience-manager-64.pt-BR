---
title: Visualizar dados de análise da página
seo-title: Seeing Page Analytics Data
description: Usar dados de análise de página para medir a eficácia do conteúdo da página
seo-description: Use page analytics data to gauge the effectiveness of their page content
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 6509c0ce-fc3a-4248-8dc7-db10602c30d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 12%

---

# Visualizar dados de análise da página{#seeing-page-analytics-data}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Use os dados de análise da página para medir a eficácia do conteúdo da página.

## Análise visível do console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

Os dados de análise da página são exibidos em [Exibição de lista](/help/sites-authoring/basic-handling.md#list-view) do console Sites . Quando as páginas são exibidas em formato de lista, as seguintes colunas estão disponíveis por padrão:

* Exibições da página
* Visitantes únicos
* Tempo na página

Cada coluna mostra um valor para o período de relatório atual e também indica se o valor aumentou ou diminuiu em relação ao período de relatório anterior. Os dados exibidos são atualizados a cada 12 horas.

>[!NOTE]
>
>Para alterar o período de atualização, [configurar o intervalo de importação](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Abra o **Sites** console; por exemplo [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. Na extremidade direita da barra de ferramentas (canto superior direito), clique ou toque no ícone para selecionar **Exibição de lista** (o ícone mostrado dependerá do [exibição atual](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Novamente, na extremidade direita da barra de ferramentas (canto superior direito), clique ou toque no ícone e selecione **Exibir configurações**. O **Configurar colunas** será aberta. Faça as alterações necessárias e confirme com **Atualizar**.

   ![aa-04](assets/aa-04.png)

### Selecionar o período de relatório {#selecting-the-reporting-period}

Selecione o período de relatório para o qual os dados do Analytics aparecem no console Sites :

* Dados dos últimos 30 dias
* Dados dos últimos 90 dias
* Dados deste ano

O período de relatório atual aparece na barra de ferramentas do console Sites (à direita da barra de ferramentas superior). Use o menu suspenso para selecionar o período de relatório necessário.\
![aa-05](assets/aa-05.png)

### Configuração das colunas de dados disponíveis {#configuring-available-data-columns}

Os membros do grupo de usuários analytics-administrators podem configurar o console Sites para permitir que os autores vejam colunas adicionais do Analytics.

>[!NOTE]
>
>Quando uma árvore de páginas contém páginas filhas associadas a diferentes configurações de nuvem do Adobe Analytics, você não pode configurar as colunas de dados disponíveis para as páginas.

1. Na Exibição de lista, use os seletores de exibição (à direita da barra de ferramentas), selecione **Exibir configurações** e depois A **Adicionar dados personalizados do Analytics**.

   ![aa-15](assets/aa-15.png)

1. Selecione as métricas que deseja expor aos autores no console Sites e clique em **Adicionar**.

   As colunas que aparecem são recuperadas do Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Abrir Content Insights de Sites {#opening-content-insights-from-sites}

Abrir [Content Insight](/help/sites-authoring/content-insights.md) no console Sites para investigar ainda mais a eficácia da página.

1. No console Sites , selecione a página na qual deseja visualizar os Content Insights.
1. Na barra de ferramentas, clique no ícone Analytics e Recommendations .

   ![](do-not-localize/chlimage_1-16.png)

## Analytics visível do Editor de páginas (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Devido a alterações de segurança na API do Adobe Analytics, não é mais possível usar a versão do Activity Map incluída no AEM.
>
>O [Plug-in do Activity Map fornecido pelo Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=pt-BR) deve ser usada.
