---
title: Tendências da atividade
seo-title: Activity Trends
description: Adicionar um componente de Lista de atividades da comunidade a uma página
seo-description: Adding a Community Activity List component to a page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 6%

---

# Tendências da atividade {#activity-trends}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O `Community Activity List` O componente fornece a capacidade de adicionar informações de tendência relacionadas a postagens e visualizações por membros, bem como postagens e visualizações de conteúdo.

Esta seção da documentação descreve

* Adicionar a `Community Activity List` para um [site da comunidade](overview.md#community-sites)

* Configurações para o `Community Activity List` componente

## Requisito {#requirement}

Dados para a `Community Activity List` O só está disponível quando o Adobe Analytics está licenciado e configurado para o site da comunidade.

Consulte [Configuração do Analytics para recursos das Comunidades](analytics.md).

## Adicionando uma lista de atividades da comunidade a uma página {#adding-a-community-activity-list-to-a-page}

Para adicionar uma `Community Activity List` para uma página no modo autor, localize o componente `Communities / Community Activity List` e arraste-a para o local em uma página.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando colocado pela primeira vez em uma página de um site da comunidade, é assim que o componente aparece:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configuração da lista de atividades da comunidade  {#configuring-community-activity-list}

Selecione o `Community Activity List` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-228](assets/chlimage_1-228.png)

Em **[!UICONTROL Comentários]** , especifique se e como os comentários dos arquivos carregados são exibidos:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Especifique se deseja exibir dados relativos aos membros da comunidade ou ao conteúdo gerado pelo usuário (UGC).

   Selecionar de
   * `Members`
   * `Content`

   O padrão é `Members`.

* **[!UICONTROL Título de exibição]**

   Um título descritivo a ser exibido acima dos dados, como `Trending Content`.

   O padrão não é um título.

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

   Quando desmarcado (desativado), somente as publicações de nível superior são contadas. Por exemplo, se o contexto for a página raiz (o padrão), então uma `Activity Type`de `Posts`O nunca mostrará nenhuma atividade, pois não há capacidade de postar conteúdo na página raiz. Quando marcado, as contagens em todas as páginas descendentes são incluídas.

   O padrão está marcado.

## Exemplo de página com 4 componentes {#example-page-with-components}

**Visitantes principais** configuração: Tipo = Membros, Tipo de atividade = Visualizações

**Principais colaboradores** configuração: Tipo = Membros, Tipo de atividade = Publicações

**Conteúdo principal** configuração: Tipo = Conteúdo, Tipo de atividade = Exibições,

**Conteúdo de tendência** configuração: Tipo = Conteúdo, Tipo de atividade = Publicações

![chlimage_1-230](assets/chlimage_1-230.png)
