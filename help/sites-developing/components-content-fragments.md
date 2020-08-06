---
title: Componentes para fragmentos de conteúdo
seo-title: Componentes para fragmentos de conteúdo
description: AEM fragmentos de conteúdo são criados e gerenciados como ativos independentes de página
seo-description: AEM fragmentos de conteúdo são criados e gerenciados como ativos independentes de página
uuid: 289ed9cb-9531-43a9-b0d8-a3499e2e9ee5
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 76b63c7c-f7ea-46be-8d10-6c1a30af2e2b
pagetitle: Components for Content Fragments
translation-type: tm+mt
source-git-commit: ce717994831eb3ef90baaffa7413de50f671b07c
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 4%

---


# Componentes para fragmentos de conteúdo{#components-for-content-fragments}

>[!CAUTION]
>
>Algumas funcionalidades do Fragmento de conteúdo exigem a aplicação do [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

## Componentes para criação de fragmentos {#components-for-fragment-authoring}

>[!CAUTION]
>
>Não é recomendável estender ou alterar os componentes reais usados no Editor de fragmentos, pois eles ainda estão sujeitos a alterações.

Consulte a API de gerenciamento de fragmentos de [conteúdo - lado](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side)do cliente.

## Componentes da autoria de página {#components-for-page-authoring}

>[!CAUTION]
>
>O Componente [principal do fragmento de](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) conteúdo agora é recomendado. Consulte [Desenvolvimento de componentes](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) principais para obter mais detalhes.
>
>Esta seção detalha o componente original entregue para uso com fragmentos de conteúdo (Fragmento **de** conteúdo no grupo **Geral** ).

Os fragmentos de conteúdo do Adobe Experience Manager (AEM) são [criados e gerenciados como ativos independentes da página](/help/assets/content-fragments.md). Eles permitem criar conteúdo não vinculado a canais, juntamente com variações (podem ser específicas de cada canal). [Em seguida, é possível usar estes fragmentos e suas variações ao criar suas páginas de conteúdo](/help/sites-authoring/content-fragments.md). Você também pode usar um ativo de fragmento de conteúdo existente [arrastando-o do navegador de ativos para a página](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (como para outros componentes baseados em ativos, como a Imagem do componente de base). O componente de fragmento de conteúdo pronto para uso exibe apenas um [elemento](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) do fragmento de conteúdo referenciado. Usando a caixa de diálogo do componente, você pode definir o [elemento, a variação e o intervalo de parágrafos](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) do fragmento que deseja exibir na página.

>[!NOTE]
>
>Este componente de Fragmento de conteúdo foi introduzido no AEM 6.2 como uma versão aprimorada do componente Artigo, que foi substituída.

>[!NOTE]
>
>Fragmentos de conteúdo não são suportados na interface clássica.

### Definição {#definition}

O componente Fragmento **de** conteúdo é usado para manter uma referência a um ativo de fragmento de conteúdo (ativos de texto efetivamente aprimorados). O tipo de recurso para o fragmento de conteúdo é:

* `dam/cfm/components/contentfragment/contentfragment`

A referência é definida na propriedade:

* `fileReference`

Somente o editor da interface habilitada para toque oferece suporte total aos componentes do fragmento de conteúdo, que inclui a biblioteca do cliente:

* `cq.authoring.editor.plugin.cfm`

Essa biblioteca adiciona recursos específicos aos fragmentos de conteúdo ao editor. Por exemplo, há suporte para a capacidade de adicionar e configurar fragmentos de conteúdo na página, a capacidade de pesquisar ativos de fragmento de conteúdo no navegador de ativos e para o conteúdo associado no painel lateral.

### Conteúdo intermediário {#in-between-content}

O componente **Fragmento** de conteúdo permite que você solte componentes adicionais entre os diferentes parágrafos do [elemento](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment)exibido. Basicamente, o elemento exibido é composto de parágrafos diferentes (cada parágrafo é marcado por um retorno de carro). Entre cada um desses parágrafos, é possível inserir conteúdo usando outros componentes.

De um ponto de vista técnico, cada parágrafo do elemento exibido vive em seu próprio parsys, e cada componente adicionado entre os parágrafos será (sob o capô) inserido no parsys.

Em outras palavras, se a instância do componente de fragmento de conteúdo for composta de três parágrafos, o componente terá três parsys diferentes no repositório. Todo o conteúdo intermediário adicionado ao fragmento de conteúdo será localizado dentro desses parsys.

No repositório, o conteúdo intermediário é armazenado em relação à sua posição dentro da estrutura geral do parágrafo, ou seja, não é anexado ao conteúdo real do parágrafo.

Para ilustrar isto, consideremos que temos:

* Uma instância de um fragmento de conteúdo composto de três parágrafos
* E que algum conteúdo já foi inserido após o segundo parágrafo

   * Isso significa que o conteúdo será armazenado no segundo parsys.

Basicamente, se a estrutura de parágrafo dessa instância mudar (alterando a variação, o elemento ou o intervalo de parágrafos exibidos), isso pode afetar o conteúdo intermediário exibido quando o conteúdo do fragmento do conteúdo:

* É editado e outro parágrafo é adicionado antes do segundo parágrafo:

   * O conteúdo intermediário será exibido após o parágrafo recém-criado (o segundo parágrafo agora contém o parágrafo recém-criado).

* É editado e o segundo parágrafo é removido:

   * O conteúdo intermediário será exibido após o parágrafo anterior ao terceiro (o segundo parsys agora contém o terceiro parágrafo anterior).

* Está configurado de modo que somente o primeiro parágrafo seja exibido:

   * O conteúdo intermediário não será exibido (o segundo parsys não é mais renderizado devido à nova configuração).

### Personalização do componente de fragmento do conteúdo {#customizing-the-content-fragment-component}

Para usar o componente de fragmento de conteúdo pronto para uso como um modelo de extensão, você deve respeitar o seguinte contrato:

* Reutilize o script de renderização HTL e seu POJO associado para ver como o recurso de conteúdo intermediário é implementado.
* Reutilize o nó do fragmento do conteúdo: `cq:editConfig`

   * Os ouvintes `afterinsert`/ `afteredit`/ `afterdelete` são usados para acionar eventos JS. Esses eventos serão manipulados na biblioteca do `cq.authoring.editor.plugin.cfm` cliente para exibir o conteúdo associado no painel lateral.
   * Os `cq:dropTargets` são configurados para suportar arrastar ativos de fragmento de conteúdo.
   * `cq:inplaceEditing` está configurado para suportar a criação de um fragmento de conteúdo no editor de páginas. O editor local do fragmento é definido na biblioteca do `cq.authoring.editor.plugin.cfm` cliente e permite que um link rápido abra o [elemento/variação](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) atual no editor [de](/help/assets/content-fragments-variations.md)fragmentos.

### Regravação de ativos antes da renderização {#asset-rewriting-before-rendering}

O Gerenciamento de fragmentos de conteúdo usa um processo de renderização interno para gerar a saída HTML final para uma página. Isso é usado internamente pelo componente Fragmento do conteúdo, mas também pelo processo em segundo plano que atualiza os fragmentos referenciados nas páginas de referência.

Internamente, o Sling Rewriter é usado para essa renderização. A respectiva configuração é encontrada em `/libs/dam/config/rewriter/cfm` e pode ser ajustada se necessário. Consulte o [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) para obter mais informações.

A configuração predefinida usa os seguintes transformadores:

* `transformer-cfm-payloadfilter` - para recuperar a `body` parte ( `<body>...</body>`) somente do HTML do fragmento

* `transformer-cfm-parfilter` - filtros parágrafos indesejados se um intervalo de parágrafo for especificado (como pode ser feito com o componente Fragmento do conteúdo)
* `transformer-cfm-assetprocessor` - é usado internamente para recuperar uma lista dos ativos incorporados ao fragmento

O processo de renderização é exposto por meio de ` [com.adobe.cq.dam.cfm.content.FragmentRenderService](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html)` e pode ser aproveitado (por exemplo) pelos componentes personalizados, se necessário.