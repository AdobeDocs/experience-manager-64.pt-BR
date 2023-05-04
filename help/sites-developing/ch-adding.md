---
title: Adicionar o ContextHub às páginas e acessar armazenamentos
seo-title: Adding ContextHub to Pages and Accessing Stores
description: Adicionar o ContextHub às suas páginas para ativar os recursos do ContextHub e para vincular às bibliotecas JavaScript do ContextHub
seo-description: Add ContextHub to your pages to enable the ContextHub features and to link to the ContextHub Javascript libraries
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# Adicionar o ContextHub às páginas e acessar armazenamentos {#adding-contexthub-to-pages-and-accessing-stores}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Adicionar o ContextHub às suas páginas para ativar os recursos do ContextHub e para vincular às bibliotecas JavaScript do ContextHub

A API Javascript do ContextHub fornece acesso aos dados de contexto que o ContextHub gerencia. Esta página descreve resumidamente os principais recursos da API para acessar e manipular dados de contexto. Siga os links para a documentação de referência da API para ver informações detalhadas e exemplos de código.

## Adicionar o ContextHub a um componente de página {#adding-contexthub-to-a-page-component}

Para ativar os recursos do ContextHub e vincular às bibliotecas JavaScript do ContextHub, inclua o componente contexthub na `head` da sua página. O código JSP do seu componente de página é semelhante ao seguinte exemplo:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

Observe que também é necessário configurar se a barra de ferramentas do ContextHub aparece no modo de Visualização. Consulte [Exibir e ocultar a interface do usuário do ContextHub](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Sobre armazenamentos do ContextHub {#about-contexthub-stores}

Use armazenamentos do ContextHub para persistir os dados de contexto. O ContextHub fornece os seguintes tipos de lojas que formam a base de todos os tipos de lojas:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [JSONPStorePersisted](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Todos os tipos de armazenamento são extensões do [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) classe . Para obter informações sobre como criar um novo tipo de armazenamento, consulte [Criação de lojas personalizadas](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Para obter informações sobre tipos de armazenamentos de amostra, consulte [Exemplos de candidatos à loja do ContextHub](/help/sites-developing/ch-samplestores.md).

### Modos de persistência {#persistence-modes}

Os armazenamentos do Context Hub usam um dos seguintes modos de persistência:

* **Local:** Usa HTML5 localStorage para manter os dados. O armazenamento local é mantido no navegador em todas as sessões.
* **Sessão:** Usa HTML5 sessionStorage para manter os dados. O armazenamento de sessão é mantido pela duração da sessão do navegador e está disponível para todas as janelas do navegador.
* **Cookie:** Usa o suporte nativo de cookies do navegador para armazenamento de dados. Os dados do cookie são enviados para e do servidor em solicitações HTTP.
* **Window.name:** Usa a propriedade window.name para persistir os dados.
* **Memória:** Usa um objeto Javascript para persistir dados.

Por padrão, o Context Hub usa o modo de persistência Local. Se o navegador não suportar ou permitir o HTML5 localStorage, a persistência da sessão será usada. Se o navegador não suportar ou permitir o HTML5 sessionStorage, a persistência de Window.name será usada.

### Armazenamento de dados {#store-data}

Internamente, armazene formulários de dados em uma estrutura em árvore, permitindo que valores sejam adicionados como tipos primários ou objetos complexos. Quando objetos complexos são adicionados aos armazenamentos, as propriedades do objeto formam ramificações na árvore de dados. Por exemplo, o seguinte objeto complexo é adicionado a um armazenamento vazio chamado location:

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

A estrutura em árvore dos dados de armazenamento pode ser conceitualizada da seguinte maneira:

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

A estrutura de árvore define itens de dados no armazenamento como pares de chave/valor. No exemplo acima, a chave `/number` corresponde ao valor `321`e a tecla `/data/country` corresponde ao valor `Switzerland`.

### Manipulação de Objetos {#manipulating-objects}

O ContextHub fornece a variável [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) classe para manipular objetos Javascript. Use as funções dessa classe para manipular objetos Javascript antes de adicioná-los a uma loja ou depois de obtê-los de uma loja.

Além disso, a variável [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) A classe fornece funções para serializar objetos para cadeia de caracteres e desserializar cadeias de caracteres para objetos. Use essa classe para manipular dados JSON para suportar navegadores que não incluem nativamente a variável `JSON.parse` e `JSON.stringify` funções.

## Interagir com armazenamentos do ContextHub {#interacting-with-contexthub-stores}

Use o [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) Objeto Javascript para obter uma loja como um objeto Javascript. Depois de obter o objeto de armazenamento, você pode manipular os dados que ele contém. Use o [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) ou [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) para obter a loja.

### Acesso aos dados do armazenamento {#accessing-store-data}

O [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) A classe Javascript define várias funções para interagir com dados de armazenamento. As seguintes funções armazenam e recuperam vários itens de dados contidos em objetos:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

Os itens de dados individuais são armazenados como um conjunto de pares de chave/valor. Para armazenar e recuperar valores, especifique a chave correspondente:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

Observe que os candidatos a armazenamento personalizado podem definir funções adicionais que fornecem acesso para armazenar dados.

>[!NOTE]
>
>Por padrão, o ContextHub não tem conhecimento do logon atualmente usado nos servidores de publicação e esses usuários são considerados pelo ContextHub como &quot;Anônimos&quot;.
>
>Você pode tornar o ContextHub ciente dos usuários conectados carregando o armazenamento de perfis conforme implementado na [Site de referência We.Retail](/help/sites-developing/we-retail.md). Consulte a [código relevante no GitHub aqui](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Eventos do ContextHub {#contexthub-eventing}

O ContextHub inclui uma estrutura de evento que permite reagir automaticamente para armazenar eventos. Cada objeto de armazenamento contém um [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) objeto que está disponível como [`eventing`](/help/sites-developing/contexthub-api.md#eventing) propriedade. Use o [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) ou [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) para vincular uma função Javascript a um evento de loja.

## Uso do Context Hub para Manipular cookies {#using-context-hub-to-manipulate-cookies}

A API Javascript do Context Hub fornece suporte entre navegadores para manipular cookies do navegador. O [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) o namespace define várias funções para criar, manipular e excluir cookies.

## Determinar segmentos do ContextHub resolvidos {#determining-resolved-contexthub-segments}

O mecanismo de segmento do ContextHub permite determinar qual dos segmentos registrados é resolvido no contexto atual. Use a função getResolvedSegments do [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) classe para recuperar segmentos resolvidos. Em seguida, use o `getName` ou `getPath` da [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) classe para testar um segmento.

### Segmentos instalados {#installed-segments}

Os segmentos do ContextHub são instalados abaixo da variável `/conf/we-retail/settings/wcm/segments` nó .

* feminino
* fêmea acima de 30
* fêmea com menos de 30 anos
* masculino
* masculino-acima de 30
* macho-menor-30
* order-value-75-to-100
* order-value-over-100
* acima de 30
* verão
* fêmea de verão
* verão-fêmea acima de 30
* verão-fêmea com menos de 30 anos
* homem do verão
* verão-masculino-acima-30
* verão-homem-menor-30
* sub-30
* inverno
* fêmea de inverno
* inverno-fêmea acima de 30
* inverno-fêmea com menos de 30 anos
* macho de inverno
* inverno-masculino-acima-30
* inverno-homem-menos de 20

As regras usadas para resolver esses segmentos são resumidas da seguinte maneira:

* O sexo feminino ou masculino é determinado a partir do `gender` da [perfil](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) armazenar.

* A idade é determinada pelo item de dados da idade do armazenamento de perfil.
* A temporada é determinada a partir do item de dados de latitude do [geolocalização](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) armazenar e o item de dados do mês do armazenamento de informações de surferências.

>[!WARNING]
>
>Os segmentos instalados são fornecidos como configurações de referência para ajudar você a criar sua própria configuração dedicada para o seu projeto e, como tal, não devem ser usados diretamente.

## Registro de mensagens de depuração do ContextHub {#logging-debug-messages-for-contexthub}

Configurar o serviço OSGi do Adobe Granite ContextHub (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) para registrar mensagens de Depuração detalhadas que são úteis no desenvolvimento.

Para configurar o serviço, você pode usar o [Console da Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou usar um [Nó JCR no repositório](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Console da Web: Para registrar mensagens de depuração, selecione a propriedade Debug .
* Nó JCR: Para registrar mensagens de depuração, defina o booleano `com.adobe.granite.contexthub.debug` propriedade para `true`.

## Consulte a Visão geral da estrutura do ContextHub {#see-an-overview-of-the-contexthub-framework}

O ContextHub fornece uma [página de diagnósticos](/help/sites-developing/ch-diagnostics.md) onde você pode ver uma visão geral da estrutura do ContextHub.
