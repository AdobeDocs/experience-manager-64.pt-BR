---
title: Tendências da atividade
seo-title: Tendências da atividade
description: Adicionar um componente de Lista de atividades da comunidade a uma página
seo-description: Adicionar um componente de Lista de atividades da comunidade a uma página
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Tendências da atividade {#activity-trends}

## Introdução {#introduction}

O `Community Activity List` componente fornece a capacidade de adicionar informações de tendência sobre postagens e exibições por membros, bem como postagens e exibições de conteúdo.

Esta seção da documentação descreve

* Adicionar o `Community Activity List` componente a um site da [comunidade](overview.md#community-sites)

* Configurações para o `Community Activity List` componente

## Requisito {#requirement}

Os dados para o `Community Activity List` estão disponíveis somente quando o Adobe Analytics está licenciado e configurado para o site da comunidade.

Consulte Configuração [do Analytics para recursos](analytics.md)de comunidades.

## Adicionar uma lista de atividades da comunidade a uma página {#adding-a-community-activity-list-to-a-page}

Para adicionar um `Community Activity List` componente a uma página no modo de autor, localize o componente `Communities / Community Activity List` e arraste-o para o lugar em uma página.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando colocado pela primeira vez em uma página de um site da comunidade, é assim que o componente aparece:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configurando a lista de atividades da comunidade {#configuring-community-activity-list}

Selecione o componente inserido a ser acessado e selecione o `Community Activity List` `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-228](assets/chlimage_1-228.png)

Na guia **[!UICONTROL Comentários]** , especifique se e como os comentários dos arquivos carregados serão exibidos:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Especifique se deseja exibir dados referentes a membros da comunidade ou conteúdo gerado pelo usuário (UGC).

   Selecionar de
   * `Members`
   * `Content`
   O padrão é `Members`.

* **[!UICONTROL Título de exibição]**

   Um título descritivo a ser exibido acima dos dados, como `Trending Content`.

   O padrão não é título.

* **[!UICONTROL Contagem de exibições]**

   O número de itens a serem listados.

   O padrão é 10.

* **[!UICONTROL Tipo de atividade]**

   Selecione um de
   * `Views`(visitas à página)
   * `Posts`(criação de UGC)
   * `Follows`
   * `Likes`
   O padrão é Exibições.

* **[!UICONTROL Período de tempo]**

   Selecione um de
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`
   O padrão é `Total`.

* **[!UICONTROL Caminho do contexto]**

   Fornece a capacidade de escopo da atividade para um subconjunto do site, como um Blog específico.

   O padrão é todo o site da comunidade.

* **[!UICONTROL Agregação da contagem de membros]**

   Quando desmarcada (desativada), somente as publicações de nível superior são contadas. Por exemplo, se o contexto for a página raiz (o padrão), um `Activity Type`dos `Posts`eventos nunca mostrará nenhuma atividade, pois não há capacidade de publicar conteúdo na página raiz. Quando marcado, as contagens em todas as páginas descendentes são incluídas.

   O padrão está marcado.

## Exemplo de página com 4 componentes {#example-page-with-components}

**Configuração dos visitantes** principais: Tipo = Membros, tipo de atividade = Exibições

**Configuração dos principais contribuidores** : Tipo = Membros, Tipo de atividade = Publicações

**Configuração do conteúdo** principal: Tipo = Conteúdo, Tipo de atividade = Exibições,

**Configuração do conteúdo** de tendência: Tipo = Conteúdo, Tipo de atividade = Postagens

![chlimage_1-230](assets/chlimage_1-230.png)
