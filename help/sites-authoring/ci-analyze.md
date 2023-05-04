---
title: Analisar o desempenho da página
seo-title: Analyzing Page Performance
description: Use a página Content Insight para analisar o desempenho da página que você está criando
seo-description: Use the Content Insight page to analyze the performance of the page that you are authoring
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
exl-id: dc24edaf-ca1d-4a6b-a2dc-86677267e18d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 1%

---

# Analisar o desempenho da página{#analyzing-page-performance}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Abra o [Content Insight](/help/sites-authoring/content-insights.md) para analisar o desempenho da página que você está criando. Configure o período de relatório para concentrar sua análise.

## Abrir o Analytics e o Recommendations para uma página {#opening-analytics-and-recommendations-for-a-page}

Use o procedimento a seguir para visualizar o Analytics e o Recommendations de uma página:

1. Navegue até a página que deseja analisar.
1. Na barra de ferramentas, clique ou toque em **Analytics e Recommendations**.

   >[!NOTE]
   >
   >O Analytics e o Recommendations para uma página só serão exibidos se você tiver configurado AEM para [integrar com o Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md).

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## Alterar o período de relatório {#changing-the-reporting-period}

Altere os seguintes aspectos relacionados ao tempo dos relatórios de análise:

* O período de tempo do relatório.
* A granularidade dos dados.

As ferramentas para alterar os aspectos relacionados ao tempo dos relatórios são exibidas na parte superior da página Content Insight . ![chlimage_1-249](assets/chlimage_1-249.png)

### Alterar o período de relatório {#changing-the-reporting-period-1}

Altere o período de relatório da página Content Insight para concentrar a análise da atividade da página em um período específico. Quando você altera o período de relatório, os relatórios são atualizados automaticamente. A área sombreada no período de tempo representa o período de relatório. As datas no período de tempo aumentam da esquerda para a direita.

![chlimage_1-250](assets/chlimage_1-250.png)

Para alterar o período de relatório de uma página Content Insight:

1. Se o período não for exibido na parte superior da página, clique ou toque no ícone Alternar período.

   ![](do-not-localize/chlimage_1-22.png)

1. Para alterar a data de início do período de relatório, arraste o círculo exibido no lado esquerdo da área sombreada para a data de início desejada.

   Se não conseguir ver o lado esquerdo da área sombreada, use a barra de rolagem para trazê-la à exibição.

1. Para alterar a data de término do período de relatório, arraste o círculo exibido no lado direito da área sombreada para a data de término desejada.

### Alterar a granularidade do período de relatório {#changing-the-granularity-of-the-reporting-period}

Altere a quantidade de tempo que cada ponto de dados abrange em um relatório. Por exemplo, quando a granularidade Semana é selecionada, cada ponto de dados no relatório de Exibições representa o número de exibições para uma semana.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

A granularidade afeta os relatórios que plotam dados ao longo do tempo, como os relatórios Exibições e Média de minutos envolvidos na página . A granularidade também afeta a escala do período.

1. Se o controle de granularidade não for exibido, clique ou toque no ícone Alternar granularidade .

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Clique ou toque na granularidade desejada. Depois de selecionado, o relatório é atualizado automaticamente para refletir a granularidade.

## Atribuir tarefas ao SEO Recommendations {#assigning-tasks-for-seo-recommendations}

Use o relatório SEO Recommendations para criar tarefas para melhorar a visibilidade da página para os mecanismos de pesquisa. Para cada recomendação no relatório que não tenha uma marca de seleção, você pode criar uma tarefa que você atribui a um usuário para executar o trabalho necessário.

![chlimage_1-252](assets/chlimage_1-252.png)

O status da recomendação de SEO indica quando a tarefa foi criada, mas ainda não foi concluída.

![chlimage_1-253](assets/chlimage_1-253.png)

Quando criada, a tarefa é exibida na lista de Tarefas do usuário. Para obter informações sobre tarefas, consulte [Trabalhar com tarefas](/help/sites-authoring/task-content.md).

Use o procedimento a seguir para criar uma tarefa para uma recomendação de SEO.

1. Clique ou toque no ícone de informações da recomendação de SEO.

   ![](do-not-localize/chlimage_1-23.png)

1. Clique no ícone de triângulo circundado que aparece ao lado do ícone de informações.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Preencha os campos de formulário que aparecem e toque em Criar:

   * Projeto: Selecione o projeto no qual criar a tarefa.
   * Nome: O nome que identifica a tarefa. O nome padrão é o título da recomendação de SEO.
   * Atribuir a: Selecione o usuário ao qual a tarefa será atribuída. Comece digitando o nome do usuário para filtrar a lista.
   * Descrição: Uma descrição da atividade necessária para concluir a tarefa. A descrição padrão são as informações que acompanham a recomendação de SEO.
   * Prioridade da tarefa: A prioridade da tarefa.
   * Data de Vencimento: A data em que a tarefa deve ser concluída.

1. Clique ou toque em Concluído para fechar a mensagem Tarefa criada .

>[!NOTE]
>
>A tarefa criada também inclui o caminho para a página à qual a recomendação de SEO se aplica.
