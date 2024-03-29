---
title: Console de relatórios
seo-title: Reports Console
description: Saiba como acessar relatórios
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 6%

---

# Console de relatórios {#reports-console}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Para o AEM Communities, há vários relatórios que podem ser acessados de várias maneiras do ambiente de criação.

Em geral, os diversos relatórios são:

* [Relatório de Atribuições](#assignments-report) - para um [comunidade de capacitação](overview.md#enablement-community), fornece uma visão geral do progresso dos alunos em suas atribuições, incluindo uma pontuação associada se estiver implementando o padrão SCORM
* [Relatório de exibições](#views-report) - fornece um gráfico de visualizações de conteúdo por membros da comunidade e visitantes do site para qualquer site da comunidade
* [Relatório de publicações](#posts-report) - fornece um gráfico de vários tipos de postagens por membros da comunidade para qualquer site da comunidade

When [O Adobe Analytics está ativado](sites-console.md#analytics), os relatórios incluirão o número de exibições, reproduções, comentários e classificações para cada recurso de ativação ao longo do tempo

Os relatórios tabulares podem ser exportados no formato .csv para processamento subsequente.

## Consoles de relatórios {#reporting-consoles}

### Relatórios para sites da comunidade {#reports-for-community-sites}

* Na navegação global: **[!UICONTROL Navegação > Comunidades > Relatórios]**
* Escolha de
   * **[!UICONTROL Relatório de atribuições]**
      * Gerar um relatório para o Site da Comunidade, Usuário ou Grupo e Atribuição selecionados
   * **[!UICONTROL Relatório de publicações]**
      * Gerar um relatório para o Site da comunidade, Tipo de conteúdo e Período selecionado
   * **[!UICONTROL Relatório de exibições]**
      * Gerar um relatório para o Site da comunidade, Tipo de conteúdo e Período selecionado
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Relatórios para recursos de ativação e caminhos de aprendizado {#reports-for-enablement-resources-and-learning-paths}

* Na navegação global: **[!UICONTROL Navegação > Comunidades > Recursos]**
* Selecionar um site da comunidade de ativação existente
   * Selecionar **[!UICONTROL Relatório]** ícone para gerar relatórios que abrangem todos os recursos de ativação
   * Selecione um caminho de aprendizagem de ativação
   * Selecionar **[!UICONTROL Relatório]** ícone para gerar relatórios para
      * Os recursos de habilitação incluídos
      * Os alunos atribuídos ao caminho de aprendizado
* Esses relatórios fornecem:
   * Dados da tabela, baixáveis como CSV
      * Identificando o aluno
      * Seu status
      * Se atribuído ou acessado pelo catálogo
      * Número de comentários feitos
      * Classificação de estrelas fornecida

Para obter mais detalhes, consulte [Seção Relatórios](resources.md#report) do console Recursos.

## Relatório de atribuições {#assignments-report}

O console Atribuições permite que os relatórios sejam filtrados por ativação do site da comunidade, usuários ou grupos e atribuição.

O relatório fornece informações sobre o seu progresso, bem como quaisquer comentários ou notações fornecidas.

![chlimage_1-157](assets/chlimage_1-157.png)

Selecione os critérios do relatório:

* **[!UICONTROL Site]**
Selecionar um site da comunidade de ativação
* **[!UICONTROL Usuário ou grupo]**
   * Selecione Usuário para gerar um relatório para um aluno
   * Selecione Grupo para gerar um relatório para um grupo de alunos O serviço de túnel acessará membros e grupos de membros do ambiente de publicação
* **[!UICONTROL Atribuição]**
Escolha entre os recursos de habilitação atribuídos ao(s) aluno(s) selecionado(s)

Selecionar **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-158](assets/chlimage_1-158.png)

## Relatório de exibições {#views-report}

O console Exibições permite que os relatórios sejam gerados nas exibições de página por recursos da comunidade por um determinado período.

![chlimage_1-159](assets/chlimage_1-159.png)

Selecione os critérios do relatório:

* **[!UICONTROL Site]**
Selecionar um site da comunidade
* **[!UICONTROL Tipo de conteúdo]**
Pode escolher Todos os conteúdos ou selecionar um dos recursos existentes no site
* Intervalo de tempo Selecione um dos seguintes:
   * Últimos 7 dias
   * Últimos 30 dias
   * Últimos 90 dias
   * Ano anterior

Selecionar **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-160](assets/chlimage_1-160.png)

## Relatório de publicações {#posts-report}

O console Publicações permite que os relatórios sejam gerados no número de publicações para recursos da comunidade por um determinado período.

![chlimage_1-161](assets/chlimage_1-161.png)

Selecione os critérios do relatório:

* **[!UICONTROL Site]**
Selecionar um site da comunidade
* **[!UICONTROL Tipo de conteúdo]**
Pode escolher Todos os conteúdos ou selecionar um dos recursos existentes no site
* Intervalo de tempo Selecione um dos seguintes:
   * Últimos 7 dias
   * Últimos 30 dias
   * Últimos 90 dias
   * Ano anterior

Selecionar **[!UICONTROL Gerar]** para criar o relatório:

![chlimage_1-162](assets/chlimage_1-162.png)

## Resolução de problemas {#troubleshooting}

### Nenhum site da comunidade listado {#no-community-sites-listed}

Se nenhum site da comunidade estiver listado, verifique se o Adobe Analytics foi ativado para um site. Se você escolher relatórios em atribuições, verifique se a função de atribuições está na estrutura do site da comunidade.
