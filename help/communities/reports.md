---
title: Console de relatórios
seo-title: Console de relatórios
description: Saiba como acessar relatórios
seo-description: Saiba como acessar relatórios
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---


# Console de relatórios {#reports-console}

## Visão geral {#overview}

No AEM Communities, há vários relatórios que podem ser acessados de várias maneiras a partir do ambiente do autor.

Em geral, os vários relatórios são:

* [Relatório](#assignments-report) de Atribuições - para uma comunidade [de](overview.md#enablement-community)ativação, fornece uma visão geral do progresso dos alunos em suas atribuições, incluindo uma pontuação associada ao implementar o padrão SCORM
* [Relatório](#views-report) de Visualizações - fornece um gráfico de visualizações de conteúdo por membros da comunidade e visitantes do site para qualquer site da comunidade
* [Relatório](#posts-report) de postagens - fornece um gráfico de vários tipos de postagens por membros da comunidade em qualquer site da comunidade

Quando o [Adobe Analytics estiver ativado](sites-console.md#analytics), os relatórios incluirão o número de visualizações, reproduções, comentários e classificações para cada recurso de ativação ao longo do tempo

Os relatórios tabulares podem ser exportados no formato .csv para processamento subsequente.

## Consoles do Relatórios {#reporting-consoles}

### Relatórios para sites da comunidade {#reports-for-community-sites}

* Da navegação global: **[!UICONTROL Navegação > Comunidades > Relatórios]**
* Escolher de
   * **[!UICONTROL Relatório de atribuições]**
      * Gerar um relatório para Site da comunidade, Usuário ou Grupo e Atribuição selecionados
   * **[!UICONTROL Relatório de publicações]**
      * Gerar um relatório para o Site da comunidade, o Tipo de conteúdo e o Período de tempo selecionados
   * **[!UICONTROL Relatório de exibições]**
      * Gerar um relatório para o Site da comunidade, o Tipo de conteúdo e o Período de tempo selecionados
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Relatórios para recursos de ativação e caminhos de aprendizado {#reports-for-enablement-resources-and-learning-paths}

* Da navegação global: **[!UICONTROL Navegação > Comunidades > Recursos]**
* Selecionar um site de comunidade de ativação existente
   * Selecione o ícone **[!UICONTROL Relatório]** para gerar relatórios que abrangem todos os recursos de ativação
   * Selecionar um caminho de aprendizado de ativação
   * Selecione o ícone **[!UICONTROL Relatório]** para o qual gerar relatórios
      * Os recursos de ativação incluídos
      * Os alunos atribuídos ao caminho de aprendizado
* Esses relatórios fornecem:
   * Dados da tabela, disponíveis para download como CSV
      * Como identificar o aluno
      * Seu status
      * Se atribuído ou acessado pelo catálogo
      * Número de comentários feitos
      * Classificação de estrelas fornecida

Para obter mais detalhes, consulte a seção [](resources.md#report) Relatórios do console Recursos.

## Relatório de atribuições {#assignments-report}

O console Atribuições permite que os relatórios sejam filtrados por meio da ativação do site da comunidade, usuários ou grupos e atribuição.

O relatório fornece informações sobre o seu progresso, bem como quaisquer comentários ou notações que lhe sejam fornecidos.

![chlimage_1-157](assets/chlimage_1-157.png)

Selecione os critérios para o relatório:

* **[!UICONTROL Site]** Selecione um site de comunidade de ativação
* **[!UICONTROL Usuário ou grupo]**
   * Selecione Usuário para gerar um relatório para um aluno
   * Selecione Grupo para gerar um relatório para um grupo de alunosO serviço de túnel acessará membros e grupos de membros do ambiente de publicação
* **[!UICONTROL Atribuição]** Escolha entre os recursos de ativação atribuídos ao(s) aluno(s) selecionado(s)

Selecione **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-158](assets/chlimage_1-158.png)

## Relatório de exibições {#views-report}

O console do Visualização permite que os relatórios sejam gerados nas visualizações de página por recursos da comunidade para um determinado período.

![chlimage_1-159](assets/chlimage_1-159.png)

Selecione os critérios para o relatório:

* **[!UICONTROL Site]** Selecione um site da comunidade
* **[!UICONTROL Tipo]** de conteúdoPode escolher Todo o conteúdo ou selecionar um dos recursos presentes no site
* Intervalo de tempoSelecione um dos seguintes:
   * Últimos 7 dias
   * Últimos 30 dias
   * Últimos 90 dias
   * Ano anterior

Selecione **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-160](assets/chlimage_1-160.png)

## Relatório de publicações {#posts-report}

O console Publicações permite que os relatórios sejam gerados em número de publicações para recursos da comunidade em um determinado período.

![chlimage_1-161](assets/chlimage_1-161.png)

Selecione os critérios para o relatório:

* **[!UICONTROL Site]** Selecione um site da comunidade
* **[!UICONTROL Tipo]** de conteúdoPode escolher Todo o conteúdo ou selecionar um dos recursos presentes no site
* Intervalo de tempoSelecione um dos seguintes:
   * Últimos 7 dias
   * Últimos 30 dias
   * Últimos 90 dias
   * Ano anterior

Selecione **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-162](assets/chlimage_1-162.png)

## Resolução de Problemas{#troubleshooting}

### Nenhum site da comunidade listado {#no-community-sites-listed}

Se nenhum site da comunidade estiver listado, verifique se a Adobe Analytics foi ativada para um site. Se você escolher relatórios em atribuições, verifique se a função de atribuições está na estrutura do site da comunidade.
