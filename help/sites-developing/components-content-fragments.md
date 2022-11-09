---
title: Componentes para fragmentos de conteúdo
seo-title: Components for Content Fragments
description: AEM fragmentos de conteúdo são criados e gerenciados como ativos independentes da página
seo-description: AEM content fragments are created and managed as page-independent assets
uuid: 289ed9cb-9531-43a9-b0d8-a3499e2e9ee5
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 76b63c7c-f7ea-46be-8d10-6c1a30af2e2b
pagetitle: Components for Content Fragments
exl-id: 516c1561-5c13-4301-8009-9b021087cec7
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 5%

---

# Componentes para fragmentos de conteúdo{#components-for-content-fragments}

>[!CAUTION]
>
>Algumas funcionalidades do Fragmento de conteúdo exigem a aplicação de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md).

## Componentes para criação de fragmentos {#components-for-fragment-authoring}

>[!CAUTION]
>
>Não é recomendável estender ou alterar os componentes reais usados no Editor de fragmentos, pois eles ainda estão sujeitos a alterações.

Consulte a [API de gerenciamento de fragmentos de conteúdo - Lado do cliente](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side).

## Componentes da autoria de página {#components-for-page-authoring}

>[!CAUTION]
>
>O [Componente principal do fragmento de conteúdo](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) agora é recomendado. Consulte [Desenvolvimento dos componentes principais](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) para obter mais detalhes.
>
>Esta seção detalha o componente original entregue para uso com fragmentos de conteúdo (**Fragmento de conteúdo** no **Geral** grupo).

Os fragmentos de conteúdo do Adobe Experience Manager (AEM) são [criados e gerenciados como ativos independentes da página](/help/assets/content-fragments.md). Eles permitem criar conteúdo não vinculado a canais, juntamente com variações (podem ser específicas de cada canal). [Em seguida, é possível usar estes fragmentos e suas variações ao criar suas páginas de conteúdo](/help/sites-authoring/content-fragments.md). Também é possível usar um ativo de fragmento de conteúdo existente ao [arrastando-o do navegador de ativos para a página](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (como para outros componentes baseados em ativos, como o componente de base Imagem). O componente de fragmento de conteúdo pronto para uso exibe apenas um [elemento](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) do fragmento de conteúdo referenciado. Na caixa de diálogo do componente é possível definir a variável [elemento, variação e intervalo de parágrafos de fragmento](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) que você deseja exibir na página.

>[!NOTE]
>
>Esse componente do Fragmento de conteúdo foi introduzido no AEM 6.2 como uma versão aprimorada do componente Artigo, que foi descontinuada.

>[!NOTE]
>
>Fragmentos de conteúdo não são suportados na interface clássica.

### Definição {#definition}

O **Fragmento de conteúdo** é usado para manter uma referência a um ativo de fragmento de conteúdo (ativos de texto efetivamente aprimorados). O tipo de recurso do fragmento de conteúdo é:

* `dam/cfm/components/contentfragment/contentfragment`

A referência é definida na propriedade :

* `fileReference`

Somente o editor da interface habilitada para toque oferece suporte total aos componentes do fragmento de conteúdo, que inclui a biblioteca do cliente:

* `cq.authoring.editor.plugin.cfm`

Essa biblioteca adiciona recursos, específicos aos fragmentos de conteúdo, ao editor. Por exemplo, há suporte para a capacidade de adicionar e configurar fragmentos de conteúdo na página, a capacidade de pesquisar por ativos do fragmento de conteúdo no navegador de ativos e por conteúdo associado no painel lateral do .

### Conteúdo intermediário {#in-between-content}

O **Fragmento de conteúdo** Esse componente permite que você solte componentes adicionais entre os diferentes parágrafos da tela exibida [elemento](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment). Basicamente, o elemento exibido é composto de parágrafos diferentes (cada parágrafo é marcado por um retorno de carro). Entre cada um desses parágrafos, é possível inserir conteúdo usando outros componentes.

De um ponto de vista técnico, cada parágrafo do elemento exibido fica em seu próprio parsys, e cada componente adicionado entre os parágrafos será (sob o capô) inserido nos parsys.

Em outras palavras, se a instância do componente de fragmento de conteúdo for composta de três parágrafos, o componente terá três parsys diferentes no repositório. Todo o conteúdo intermediário adicionado ao fragmento de conteúdo estará realmente localizado dentro desses parsys.

No repositório, o conteúdo intermediário é armazenado em relação à sua posição dentro da estrutura geral do parágrafo, ou seja, não é anexado ao conteúdo real do parágrafo.

Para ilustrar isto, consideremos que temos:

* Uma instância de um fragmento de conteúdo composto de três parágrafos
* E que já foi inserido algum conteúdo após o segundo parágrafo

   * Isso significa que o conteúdo será armazenado no segundo parsys.

Basicamente, se a estrutura de parágrafo dessa instância for alterada (alterando a variação, o elemento ou o intervalo de parágrafos exibidos), isso poderá afetar o conteúdo intermediário exibido quando o conteúdo do fragmento de conteúdo:

* É editado e outro parágrafo é adicionado antes do segundo parágrafo:

   * O conteúdo intermediário será exibido após o parágrafo recém-criado (o segundo parsys agora retém o parágrafo recém-criado).

* É editado e o segundo parágrafo é removido:

   * O conteúdo intermediário será exibido após o parágrafo que era anteriormente o terceiro (o segundo parsys agora contém o terceiro parágrafo anterior).

* É configurado de forma que somente o primeiro parágrafo seja exibido:

   * O conteúdo intermediário não será exibido (o segundo parsys não é mais renderizado devido à nova configuração).

### Personalização do componente do fragmento de conteúdo {#customizing-the-content-fragment-component}

Para usar o componente de fragmento de conteúdo pronto para uso como um blueprint para extensão, você deve respeitar o seguinte contrato:

* Reutilize o script de renderização HTL e seu POJO associado para ver como o recurso de conteúdo intermediário é implementado.
* Reutilize o nó do fragmento de conteúdo: `cq:editConfig`

   * O `afterinsert`/ `afteredit`/ `afterdelete` os ouvintes são usados para acionar eventos JS. Esses eventos serão tratados na seção `cq.authoring.editor.plugin.cfm` biblioteca do cliente para exibir o conteúdo associado no painel lateral.
   * O `cq:dropTargets` são configuradas para suportar arrastar ativos de fragmento de conteúdo.
   * `cq:inplaceEditing` O é configurado para suportar a criação de um fragmento de conteúdo no editor de páginas. O editor de fragmento no local é definido na variável `cq.authoring.editor.plugin.cfm` biblioteca cliente e permite que um link rápido abra o [elemento/variação](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) no [editor de fragmento](/help/assets/content-fragments-variations.md).

### Regravação de ativos antes da renderização {#asset-rewriting-before-rendering}

O Gerenciamento de fragmentos de conteúdo usa um processo de renderização interno para gerar a saída HTML final de uma página. Isso é usado internamente pelo componente Fragmento do conteúdo , mas também pelo processo em segundo plano que atualiza os fragmentos referenciados nas páginas de referência.

Internamente, o Sling Rewriter é usado para essa renderização. A configuração respectiva é encontrada em `/libs/dam/config/rewriter/cfm` e podem ser ajustadas, se necessário. Consulte a [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) para obter mais informações.

A configuração pronta para uso usa os seguintes transformadores:

* `transformer-cfm-payloadfilter` - para recuperar a `body` parte ( `<body>...</body>`) somente do HTML do fragmento

* `transformer-cfm-parfilter` - filtra parágrafos indesejados se um intervalo de parágrafo for especificado (como pode ser feito com o componente Fragmento de conteúdo)
* `transformer-cfm-assetprocessor` - é usado internamente para recuperar uma lista dos ativos incorporados ao fragmento

O processo de renderização é exposto por meio de ` [com.adobe.cq.dam.cfm.content.FragmentRenderService](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html)` e podem ser aproveitadas (por exemplo) por componentes personalizados, se necessário.
