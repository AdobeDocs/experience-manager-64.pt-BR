---
title: Análise do desempenho das páginas
seo-title: Análise do desempenho das páginas
description: Use a página Content Insight para analisar o desempenho da página que você está criando
seo-description: Use a página Content Insight para analisar o desempenho da página que você está criando
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
translation-type: tm+mt
source-git-commit: 3addef2141ebb831f8677d011d68faf88e648dc2
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 94%

---


# Análise do desempenho das páginas{#analyzing-page-performance}

Abra a página [Content Insight](/help/sites-authoring/content-insights.md) para analisar o desempenho da página que você está criando. Configure o período de relatório para concentrar a análise.

## Abrir as Análises e Recomendações para uma página {#opening-analytics-and-recommendations-for-a-page}

Use o seguinte procedimento para visualizar as Análises e Recomendações para uma página:

1. Navegue até a página que deseja analisar.
1. Na barra de ferramentas, clique ou toque em **Análises e Recomendações**.

   >[!NOTE]
   >
   >As Análises e Recomendações para uma página aparecem somente se tiver configurado o AEM[ para fazer a integração com o Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md).

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## Alterar o período de relatório {#changing-the-reporting-period}

Altere os seguintes aspectos relacionados ao tempo dos relatórios de análise:

* O período de tempo do relatório.
* A granularidade dos dados.

As ferramentas para alterar os aspectos relacionados ao tempo dos relatórios são exibidas na parte superior da página Content Insight. ![chlimage_1-249](assets/chlimage_1-249.png)

### Alterar o período de relatório {#changing-the-reporting-period-1}

Altere o período de relatório da página Content Insight para concentrar a análise das atividades da página em um período específico. Quando você altera o período de relatório, os relatórios são atualizados automaticamente. A área sombreada no período de tempo representa o período de relatório. As datas do período de tempo aumentam da esquerda para a direita.

![chlimage_1-250](assets/chlimage_1-250.png)

Para alterar o período de relatório de uma página Content Insight:

1. Se o período de tempo não for exibido na parte superior da página, clique ou toque no ícone Alternar período de tempo.

   ![](do-not-localize/chlimage_1-22.png)

1. Para alterar a data de início do período de relatório, arraste o círculo exibido no lado esquerdo da área sombreada para a data de início desejada.

   Se não for possível ver o lado esquerdo de área sombreada, use a barra de rolagem para trazê-lo à exibição.

1. Para alterar a data de término do período de relatório, arraste o círculo exibido no lado direito da área sombreada para a data de término desejada.

### Alterar a granularidade do período de relatório  {#changing-the-granularity-of-the-reporting-period}

Altere o intervalo de tempo medido para cada ponto de dados em um relatório. Por exemplo, quando a granularidade de Semana é selecionada, cada ponto de dados no relatório de Exibições representa o número de exibições para uma semana.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

A granularidade afeta os relatórios que representam os dados ao longo do tempo, como os relatórios de Exibições e Média de minutos gastos na página. A granularidade também afeta o período de tempo.

1. Se o controle de granularidade não for exibido, clique ou toque no ícone Alternar granularidade.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Clique ou toque na granularidade desejada. Assim que selecionado, o relatório é atualizado automaticamente para refletir a granularidade.

## Atribuir tarefas para recomendações de SEO  {#assigning-tasks-for-seo-recommendations}

Use o relatório Recomendações de SEO para criar tarefas a fim de melhorar a visibilidade da página aos mecanismos de pesquisa. Para cada recomendação no relatório que não tenha uma marca de verificação, é possível criar uma tarefa a ser atribuída a um usuário para executar o trabalho necessário.

![chlimage_1-252](assets/chlimage_1-252.png)

O status da recomendação de SEO indica quando a tarefa foi criada, mas que ainda não foi concluída.

![chlimage_1-253](assets/chlimage_1-253.png)

Quando criada, a tarefa será exibida na lista de Tarefas do usuário. Para obter informações sobre o tarefa, consulte [Trabalhar com o Tarefa](/help/sites-authoring/task-content.md).

Use o procedimento a seguir para criar uma tarefa para uma recomendação de SEO.

1. Clique ou toque no ícone de informações da recomendação de SEO.

   ![](do-not-localize/chlimage_1-23.png)

1. Clique no ícone de triângulo circundado que aparece ao lado do ícone de informações.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Preencha os campos de formulário que parecem e toque em Criar:

   * Projeto: selecione o projeto no qual criar a tarefa.
   * Nome: o nome que identifica a tarefa. O nome padrão é o título da recomendação de SEO.
   * Atribuir a: selecione o usuário a ser atribuído à tarefa. Comece a digitar o nome do usuário para filtrar a lista.
   * Descrição: uma descrição da atividade necessária para concluir a tarefa. A descrição padrão são as informações que acompanham a recomendação de SEO.
   * Prioridade da tarefa: a prioridade da tarefa.
   * Data de vencimento: a data limite de conclusão da tarefa.

1. Clique ou toque em Concluído para fechar a mensagem Tarefa criada.

>[!NOTE]
>
>A tarefa criada também inclui o caminho para a página à qual a recomendação SEO se aplica.