---
title: Recurso de pesquisa
seo-title: Search Feature
description: Adicionar e configurar a Pesquisa em um site do Communities
seo-description: Adding and configuring Search to a Communities site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 2%

---

# Recurso de pesquisa {#search-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O recurso de pesquisa funciona com vários outros recursos, como fóruns, para fornecer a capacidade de pesquisar conteúdo.

Ao adicionar a capacidade de pesquisar postagens inseridas por membros da comunidade, conhecidas como conteúdo gerado pelo usuário (UGC), há dois componentes: [ `Search`](#search-features) e [ `Search Results`](#search-results).

A página que inclui a variável `Search Results` O componente suporta pesquisa e a exibição de resultados.

A página que inclui a variável `Search`fornece um local para iniciar uma pesquisa com os resultados que aparecem no `Search Results` página.

O recurso de pesquisa pode ser usado com qualquer outro recurso que permita que visitantes e membros do site visualizem o conteúdo.

## Pesquisar {#search-features}

### Adicionar Pesquisa a uma Página {#add-search-to-a-page}

Para adicionar uma `Search` para uma página no modo autor, use o navegador de componentes para localizar `Communities / Search` e arraste-a para o local em uma página. Utilização de `Search` O requer uma segunda página para o `Search Results.`

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a biblioteca do lado do cliente necessária, `cq.social.hbs.search`, está incluído, é assim que a função `Search` será exibido.

![chlimage_1-373](assets/chlimage_1-373.png)

### Configure a pesquisa adicionada {#configure-the-added-search}

Selecione o `Search` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-374](assets/chlimage_1-374.png)

Em **[!UICONTROL Configurações de pesquisa]** , especifique como são os caminhos de pesquisa quando uma consulta é inserida por um visitante.

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL Caminhos de pesquisa]**
Ao adicionar caminhos de pesquisa usando o botão Adicionar item, a pesquisa de conteúdo é limitada. Como exemplo, para limitar a pesquisa a um fórum específico, selecione um componente de fórum inserido em uma página:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Página de resultados]**
Os resultados serão exibidos em uma página separada especificada usando o navegador para selecionar uma página contendo o 
`Search Results` componente.

## Resultados da pesquisa {#search-results}

### Adicionar resultados de pesquisa a uma página {#add-search-results-to-a-page}

Para adicionar uma `Search Results` para uma página no modo autor, use o navegador de componentes para localizar

* `Communities / Search Results`

e arraste-a para o local em uma página. Diferentemente do componente de Pesquisa, nenhuma segunda página é necessária, pois os resultados serão exibidos na mesma página.

Se estiver usando Pesquisar em outro lugar do site, esta página terá `Search Results` pode ser configurado para ser `Result Page` para qualquer ou todas as instâncias de `Search`.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a biblioteca do lado do cliente necessária, `cq.social.hbs.search`, está incluído, é assim que a função `Search Result` componente será exibido:

![chlimage_1-376](assets/chlimage_1-376.png)

### Configurar o resultado da pesquisa adicionada {#configure-the-added-search-result}

Selecione o `Search Results` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-377](assets/chlimage_1-377.png)

Em **[!UICONTROL Configurações do Resultado da Pesquisa]** , é possível especificar quais caminhos estão incluídos na pesquisa quando um query é inserido por um visitante.

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL Resultados da pesquisa por página]**
Defina o número de tópicos/postagens exibidos por página. O padrão é 10.

* **[!UICONTROL Caminhos de pesquisa]**
Ao adicionar caminhos de pesquisa usando o botão Adicionar item, a pesquisa de conteúdo é limitada.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos da pesquisa](search-implementation.md) página para desenvolvedores.
