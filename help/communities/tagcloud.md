---
title: Uso da Nuvem de tags sociais
seo-title: Uso da Nuvem de tags sociais
description: Adicionar um componente da Nuvem de tags sociais a uma página
seo-description: Adicionar um componente da Nuvem de tags sociais a uma página
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 1%

---


# Uso da Nuvem de tags sociais {#using-social-tag-cloud}

## Introdução {#introduction}

O componente `Social Tag Cloud` destaca as tags aplicadas pelos membros da comunidade ao publicar conteúdo. É uma forma de identificar os tópicos de tendência e permitir que os visitantes do site localizem rapidamente o conteúdo marcado.

Para obter outro meio de identificar as tendências atuais, visite [Tendências de Atividade](trends.md).

Esta página documentos as `Social Tag Cloud` configurações de diálogo do componente e descreve a experiência do usuário.

Para obter informações detalhadas para desenvolvedores, consulte [Tag Essentials](tag.md).

Consulte [Administração de tags](../../help/sites-administering/tags.md) para obter informações sobre como criar e gerenciar tags, bem como as tags de conteúdo que foram aplicadas.

## Adicionar uma nuvem de tags sociais {#adding-a-social-tag-cloud}

Para adicionar um componente `Social Tag Cloud` a uma página no modo de autor, use o navegador de componentes para localizar `Communities / Social Tag Cloud` e arraste-o para o lugar em uma página onde a nuvem de tags deve aparecer.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](tag.md#essentials-for-client-side) forem incluídas, o componente `Social Tag Cloud` aparecerá desta forma:

![chlimage_1-303](assets/chlimage_1-303.png)

## Configuração da nuvem de tags sociais {#configuring-social-tag-cloud}

Selecione o componente `Social Tag Cloud` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-304](assets/chlimage_1-304.png)

Na guia **[!UICONTROL Nuvem de tags sociais]**, especifique quais tags serão exibidas e, se as tags forem links ativos, o local da página para os resultados da pesquisa:

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL Tags sociais para]**
exibiçãoIdentifique quais tags UGC devem ser exibidas. As opções de menu suspenso são

   * `From page and child pages`
   * `All tags`

   O padrão é `From page and child pages`, onde &quot;page&quot; se refere à configuração **Page** abaixo.

* **[!UICONTROL Página]**
(obrigatório se não 
`All tags)` O caminho para o UGC de uma página. O padrão é a página atual se deixado em branco.

* **[!UICONTROL Sem links em]**
tagsSe marcadas, as tags são exibidas na nuvem de tags como texto sem formatação. Se desmarcadas, as tags serão exibidas como links ativos que pesquisam todo o conteúdo ao qual essa tag é aplicada. O padrão está desmarcado e requer que **[!UICONTROL Caminho do resultado da pesquisa]** seja definido.

* **[!UICONTROL Caminho]**
do resultado da pesquisaO caminho para uma página na qual uma 
`Search Result` foi colocado, configurado para fazer referência ao UGC que inclui o caminho UGC especificado pela  **** Pagesetting.

## Alterar exibição da nuvem de tags sociais {#change-display-of-social-tag-cloud}

Para editar a exibição da **Nuvem de tags sociais**, digite [Modo de design](../../help/sites-authoring/default-components-designmode.md) e clique no duplo no componente `Social Tag Cloud` colocado para abrir uma caixa de diálogo com uma guia adicional.

Usando a guia **[!UICONTROL Nuvem de tags sociais (Design)]**, especifique como as tags são exibidas. Uma tag pode ser uma tag simples, uma única palavra na namespace padrão ou uma taxonomia hierárquica:

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL Mostrar]**
caminhos de título completoSe marcada, mostra os títulos das tags pai e a namespace de cada tag aplicada.

   Por exemplo:

   * Marcado: `Geometrixx Media: Gadgets / Cars`
   * Desmarcado: `Cars`

   Não há diferença para uma tag simples.

   O padrão está desmarcado.

* **[!UICONTROL Mostrar somente]**
tags de folhaSe marcada, mostra somente tags aplicadas que não contêm outras tags.

   Por exemplo, considerando a TagID de

   `Geometrixx Media: Gadgets / Cars`

   Há três tags que podem ser aplicadas: `Geometrixx Media (the namespace)`, `Gadgets` e `Cars`

   * Verificado: somente `Cars` será exibido, se aplicado
   * Desmarcado: `Geometrixx Media` e `Gadgets`assim como `Cars` serão exibidos, se aplicado

   Uma tag simples é uma tag de folha.

   O padrão está desmarcado.

* **[!UICONTROL Modelo]**
de linkUm modelo, diferente do padrão, usado para exibir os links em uma nuvem de tags, quando os links são ativados pela caixa de diálogo de edição de componentes.

* **[!UICONTROL Mesmo tamanho para todas as]**
tagsSe marcado, todas as palavras na nuvem de tags têm o mesmo estilo. Se não estiver marcada, o estilo das palavras será diferente de acordo com seu uso. O padrão está desmarcado.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Tag Essentials](tag.md) para desenvolvedores.

Consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md) (UGC) para obter informações sobre como criar e gerenciar tags.
