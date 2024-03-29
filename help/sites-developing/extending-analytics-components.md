---
title: Adicionar rastreamento do Adobe Analytics aos componentes
seo-title: Adding Adobe Analytics Tracking to Components
description: Adicionar rastreamento do Adobe Analytics aos componentes
seo-description: null
uuid: 447b140c-678c-428d-a1c9-ecbdec75cd42
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: a11c39b4-c23b-4207-8898-33aea25f2ad0
exl-id: f3926a15-4378-464f-968f-661745af117c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1299'
ht-degree: 0%

---

# Adicionar rastreamento do Adobe Analytics aos componentes{#adding-adobe-analytics-tracking-to-components}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Inclusão do módulo Adobe Analytics em um componente de página {#including-the-adobe-analytics-module-in-a-page-component}

Componentes do modelo da página (por exemplo, `head.jsp, body.jsp`) precisa de JSPs para carregar o ContextHub e a integração do Adobe Analytics (que faz parte do Cloud Services). Tudo inclui carregar arquivos JavaScript.

A entrada do ContextHub deve ser incluída imediatamente abaixo do `<head>` , enquanto Cloud Services deve ser incluído na variável `<head>` e antes da `</body>` seção; por exemplo:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
...
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
...
</head>
<body>
...
    <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
</body>
```

O `contexthub` script inserido após a variável `<head>` adiciona os recursos do ContextHub à página.

O `cloudservices` scripts adicionados na `<head>` e `<body>` as seções se aplicam às configurações dos serviços de nuvem que são adicionadas à página. (Se a página usar mais de uma configuração de Cloud Services, será necessário incluir o jsp do ContextHub e o jsp do Cloud Services apenas uma vez.)

Quando uma estrutura do Adobe Analytics é adicionada à página, a variável `cloudservices` os scripts geram um javascript relacionado ao Adobe Analytics e referências a bibliotecas do lado do cliente, semelhante ao seguinte exemplo:

```xml
<div class="sitecatalyst cloudservice">
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/util.js"></script>
<script type="text/javascript" src="/content/geometrixx-outdoors/_jcr_content/analytics.sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/mac/mac-sc.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/plugins.js"></script>
<script type="text/javascript">
<!--
CQ_Analytics.Sitecatalyst.frameworkComponents = ['foundation/components/page'];
/**
 * Sets Adobe Analytics variables accordingly to mapped components. If <code>options</code> 
 * object is provided only variables matching the options.componentPath are set.
 *
 * @param {Object} options Parameter object from CQ_Analytics.record() call. Optional.
 */
CQ_Analytics.Sitecatalyst.updateEvars = function(options) {
    this.frameworkMappings = [];
 this.frameworkMappings.push({scVar:"pageName",cqVar:"pagedata.title",resourceType:"foundation/components/page"});
    for (var i=0; i<this.frameworkMappings.length; i++){
  var m = this.frameworkMappings[i];
  if (!options || options.compatibility || (options.componentPath == m.resourceType)) {
   CQ_Analytics.Sitecatalyst.setEvar(m);
  }
    }
}

CQ_Analytics.CCM.addListener("storesinitialize", function(e) {
 var collect = true;
    var lte = s.linkTrackEvents;
    s.pageName="content:geometrixx-outdoors:en";
    CQ_Analytics.Sitecatalyst.collect(collect);
    if (collect) {
  CQ_Analytics.Sitecatalyst.updateEvars();
     /************* DO NOT ALTER ANYTHING BELOW THIS LINE ! **************/
     var s_code=s.t();if(s_code)document.write(s_code);
     s.linkTrackEvents = lte;
     if(s.linkTrackVars.indexOf('events')==-1){delete s.events};
     $CQ(document).trigger("sitecatalystAfterCollect");
    }
});
//-->
</script>
<script type="text/javascript">
<!--
if(navigator.appVersion.indexOf('MSIE')>=0)document.write(unescape('%3C')+'\!-'+'-')
//-->
</script>
<noscript><img src="https://daydocumentation.112.2o7.net/b/ss/daydocumentation/1/H.25--NS/1380120772954?cdp=3&gn=content%3Ageometrixx-outdoors%3Aen" height="1" width="1" border="0" alt=""/></noscript>
<span data-tracking="{event:'pageView', values:{}, componentPath:'foundation/components/page'}"></span>
<div id="cq-analytics-texthint" style="background:white; padding:0 10px; display:none;">
 <h3 class="cq-texthint-placeholder">Component clientcontext is missing or misplaced.</h3>
</div>
<script type="text/javascript">
$CQ(function(){
 if( CQ_Analytics &&
  CQ_Analytics.ClientContextMgr &&
  !CQ_Analytics.ClientContextMgr.isConfigLoaded ) 
  {
   $CQ("#cq-analytics-texthint").show();
  }
});
</script>
</div>
```

Todos AEM sites de exemplo, como Geometrixx Outdoors, têm esse código incluído.

### O evento sitecatalystAfterCollect {#the-sitecatalystaftercollect-event}

O `cloudservices` o script aciona a variável `sitecatalystAfterCollect` evento:

```
$CQ(document).trigger("sitecatalystAfterCollect");
```

Esse evento é acionado para indicar que o rastreamento de página foi concluído. Se você estiver executando operações de rastreamento adicionais nesta página, é necessário ouvir esse evento em vez do evento document load ou document ready . Usar o `sitecatalystAfterCollect` evita colisões ou outro comportamento imprevisível.

>[!NOTE]
>
>O `/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js` A biblioteca inclui o código da Adobe Analytics `s_code.js` arquivo.

## Implementação do rastreamento do Adobe Analytics para componentes personalizados {#implementing-adobe-analytics-tracking-for-custom-components}

Permitir que os componentes do AEM interajam com a estrutura do Adobe Analytics. Em seguida, configure sua estrutura para que o Adobe Analytics rastreie os dados do componente.

Os componentes que interagem com a estrutura do Adobe Analytics aparecem no SideKick quando você está editando uma estrutura. Depois de arrastar o componente para a estrutura, as propriedades do componente são exibidas e você pode mapeá-las com as propriedades do Adobe Analytics. (Consulte [Configuração de uma estrutura para rastreamento básico](/help/sites-administering/adobeanalytics-connect.md#creating-a-adobe-analytics-framework).)

Os componentes podem interagir com a estrutura do Adobe Analytics quando o componente tem um nó filho chamado `analytics`. O `analytics` O nó tem as seguintes propriedades:

* `cq:trackevents`: Identifica os eventos CQ que o componente expõe. (Consulte Eventos personalizados.)
* `cq:trackvars`: Nomes das variáveis CQ que são mapeadas com propriedades do Adobe Analytics.
* `cq:componentName`: O nome do componente que aparece no Sidekick.
* `cq:componentGroup`: O grupo no Sidekick que inclui o componente.

O código no componente JSP adiciona o javascript à página que aciona o rastreamento e define os dados que são rastreados. O nome do evento e os nomes de dados usados no javascript devem corresponder aos valores correspondentes da variável `analytics` propriedades do nó.

* Use o atributo de rastreamento de dados para rastrear os dados do evento quando uma página for carregada. (Consulte [Rastreamento de eventos personalizados no carregamento da página](/help/sites-developing/extending-analytics.md#tracking-custom-events-on-page-load).)
* Use a função CQ_Analytics.record para rastrear os dados do evento quando os usuários interagirem com os recursos da página. (Consulte [Rastreamento de eventos personalizados após o carregamento da página](/help/sites-developing/extending-analytics.md#tracking-custom-events-after-page-load).)

Quando você usa esses métodos de rastreamento de dados, o módulo de integração do Adobe Analytics realiza automaticamente as chamadas para o Adobe Analytics para registrar os eventos e dados.

### Exemplo: Rastreamento de cliques de navegação superior {#example-tracking-topnav-clicks}

Estenda o componente de navegação superior de base para que o Adobe Analytics rastreie cliques em links de navegação na parte superior da página. Quando um link de navegação é clicado, o Adobe Analytics registra o link que foi clicado e a página na qual ele foi clicado.

Os procedimentos a seguir exigem que você já tenha executado as seguintes tarefas:

* Criado um aplicativo CQ.
* Criação de uma Configuração do Adobe Analytics e uma Estrutura do Adobe Analytics.

#### Copie o componente de navegação superior {#copy-the-topnav-component}

Copie o componente de navegação superior para o aplicativo CQ. O procedimento requer que seu aplicativo esteja configurado no CRXDE Lite.

1. Clique com o botão direito do mouse no `/libs/foundation/components/topnav` e clique em Copiar.
1. Clique com o botão direito do mouse na pasta Componentes abaixo da pasta do aplicativo e clique em Colar.
1. Clique em Salvar tudo.

#### Integração do topnav Com A Estrutura Do Adobe Analytics {#integrating-topnav-with-the-adobe-analytics-framework}

Configure o componente de navegação superior e edite o arquivo JSP para definir os eventos e os dados de rastreamento.

1. Clique com o botão direito do mouse no nó de navegação superior e clique em Criar > Criar nó. Especifique os seguintes valores de propriedade e clique em OK:

   * Nome: `analytics`
   * Tipo: `nt:unstructured`

1. Adicione a seguinte propriedade ao nó do analytics para nomear o evento de rastreamento:

   * Nome: cq:trackevents
   * Tipo: String
   * Valor: topnavClick

1. Adicione a seguinte propriedade ao nó do analytics para nomear as variáveis de dados:

   * Nome: cq:trackvars
   * Tipo: String
   * Valor: topnavTarget,topnavLocation

1. Adicione a seguinte propriedade ao nó do Analytics para nomear o componente do Sidekick:

   * Nome: cq:componentName
   * Tipo: String
   * Valor: topnav (rastreamento)

1. Adicione a seguinte propriedade ao nó do Analytics para nomear o grupo de componentes do Sidekick:

   * Nome: cq:componentGroup
   * Tipo: String
   * Valor: Geral

1. Clique em Salvar tudo.
1. Abra o arquivo topnav.jsp.
1. No elemento a , adicione o seguinte atributo:

   ```xml
   onclick = "tracknav('<%= child.getPath() %>.html')" 
   ```

1. Na parte inferior da página, adicione o seguinte código javascript:

   ```xml
   <script type="text/javascript">
       function tracknav(target) {
               if (CQ_Analytics.Sitecatalyst) {
                   CQ_Analytics.record({
                       event: 'topnavClick',
                       values: {
                           topnavTarget: target,
                           topnavLocation:'<%=currentPage.getPath() %>.html'
                       },
                       componentPath: '<%=resource.getResourceType()%>'
                   });
               }
       }
   </script> 
   ```

1. Clique em Salvar tudo.

O conteúdo do arquivo topnav.jsp deve aparecer da seguinte maneira:

```xml
<%@page session="false"%><%--
  Copyright 1997-2008 Day Management AG
  Barfuesserplatz 6, 4001 Basel, Switzerland
  All Rights Reserved.

  This software is the confidential and proprietary information of
  Day Management AG, ("Confidential Information"). You shall not
  disclose such Confidential Information and shall use it only in
  accordance with the terms of the license agreement you entered into
  with Day.

  ==============================================================================

  Top Navigation component

  Draws the top navigation

--%><%@include file="/libs/foundation/global.jsp"%><%
%><%@ page import="java.util.Iterator,
        com.day.text.Text,
        com.day.cq.wcm.api.PageFilter,
        com.day.cq.wcm.api.Page,
        com.day.cq.commons.Doctype,
        org.apache.commons.lang3.StringEscapeUtils" %><%

    // get starting point of navigation
    long absParent = currentStyle.get("absParent", 2L);
    String navstart = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);

    //if not deep enough take current node
    if (navstart.equals("")) navstart=currentPage.getPath();

    Resource rootRes = slingRequest.getResourceResolver().getResource(navstart);
    Page rootPage = rootRes == null ? null : rootRes.adaptTo(Page.class);
    String xs = Doctype.isXHTML(request) ? "/" : "";
    if (rootPage != null) {
        Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
        while (children.hasNext()) {
            Page child = children.next();
            %><a onclick = "tracknav('<%= child.getPath() %>.html')"  href="<%= child.getPath() %>.html"><%
            %><img alt="<%= StringEscapeUtils.escapeXml(child.getTitle()) %>" src="<%= child.getPath() %>.navimage.png"<%= xs %>></a><%
        }
    }
%><script type="text/javascript">
    function tracknav(target) {
            if (CQ_Analytics.Sitecatalyst) {
                CQ_Analytics.record({
                    event: 'topnavClick',
                    values: {
                        topnavTarget:target,
                        topnavLocation:'<%=currentPage.getPath() %>.html'
                    },
                    componentPath: '<%=resource.getResourceType()%>'
                });
            }
    }
</script>  
```

>[!NOTE]
>
>Geralmente, é desejável rastrear dados do ContextHub. Para obter informações sobre como usar o javascript para obter essas informações, consulte [Acesso a valores no ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).

#### Adicionar o componente de rastreamento ao Sidekick {#adding-the-tracking-component-to-sidekick}

Adicione componentes ativados para rastreamento com o Adobe Analytics ao Sidekick, para que você possa adicioná-los à sua estrutura.

1. Abra sua estrutura do Adobe Analytics em sua configuração do Adobe Analytics. ([http://localhost:4502/etc/cloudservices/sitecatalyst.html](http://localhost:4502/etc/cloudservices/sitecatalyst.html))
1. No Sidekick, clique no botão Design .

   ![](do-not-localize/chlimage_1.png)

1. Na área Configuração de rastreamento de link , clique em Configurar herança.

   ![chlimage_1](assets/chlimage_1.png)

1. Na lista Componentes permitidos , selecione topnav (tracking) na seção Geral e clique em OK.
1. Expanda Sidekick para entrar no modo de edição. O componente agora está disponível no grupo Geral .

#### Adicionar o componente de navegação superior à estrutura {#adding-the-topnav-component-to-your-framework}

Arraste o componente de navegação superior para a estrutura do Adobe Analytics e mapeie as variáveis e os eventos do componente para as variáveis e os eventos do Adobe Analytics. (Consulte [Configuração de uma estrutura para rastreamento básico](/help/sites-administering/adobeanalytics-connect.md).)

![chlimage_1-1](assets/chlimage_1-1.png)

O componente de navegação superior agora é integrado à estrutura do Adobe Analytics. Ao adicionar o componente a uma página, clicar nos itens na barra de navegação superior faz com que os dados de rastreamento sejam enviados para o Adobe Analytics.

### Envio de dados de s.products para o Adobe Analytics {#sending-s-products-data-to-adobe-analytics}

Os componentes podem gerar dados para a variável s.products enviada para o Adobe Analytics. Projete seus componentes para contribuir com a variável s.products :

* Registrar um valor com o nome `product` de uma estrutura específica.
* Exponha os membros de dados do `product` para que possam ser mapeadas com variáveis do Adobe Analytics na estrutura do Adobe Analytics.

A variável s.products do Adobe Analytics usa a seguinte sintaxe:

```
s.products="category;product;quantity;price;eventY={value}|eventZ={value};evarA={value}|evarB={value}"
```

O módulo de integração do Adobe Analytics constrói o `s.products` usando a variável `product` valores que AEM componentes gerados. O `product` no javascript que AEM componentes gerados é uma matriz de valores que tem a seguinte estrutura:

```
"product": [{
    "category": "",
    "sku"     : "path to product node",
    "quantity": quantity,
    "price"   : price,
    "events   : {
      "eventName1": "eventValue1",
      "eventName_n": "eventValue_n"
    }
    "evars"   : {
      "eVarName1": "eVarValue1",
      "eVarName_n": "eVarValue_n"
    }
}]
```

Quando um item de dados é omitido do `product` , ele é enviado como uma string vazia em s.products.

>[!NOTE]
>
>Quando nenhum evento está associado a um valor de produto, a Adobe Analytics usa a variável `prodView` por padrão.

O `analytics` do componente deve expor os nomes das variáveis usando o `cq:trackvars` propriedade:

* product.category
* product.sku
* product.quantity
* product.price
* product.events.eventName1
* product.events.eventName_n
* product.evars.eVarName1
* product.evars.eVarName_n

O módulo eCommerce fornece vários componentes que geram dados variáveis s.products . Por exemplo, o componente de submissão ([http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp](http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp)) gera um javascript semelhante ao seguinte exemplo:

```
<script type="text/javascript">
    function trackCartPurchase() {
        if (CQ_Analytics.Sitecatalyst) {
            CQ_Analytics.record({
                "event": ["productsCartPurchase"],
                "values": {
                    "product": [
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/1",
                            "quantity": 3,
                            "price"   : 179.7,
                            "evars"   : {
                                "childSku": "/path/to/prod/1/green/xs",
                                "size"    : "XS"
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/2",
                            "quantity": 10,
                            "price"   : 150,
                            "evars"   : {
                                "childSku": "/path/to/prod/2",
                                "size"    : ""
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/3",
                            "quantity": 2,
                            "price"   : 102,
                            "evars"   : {
                                "childSku": "/path/to/prod/3/m",
                                "size"    : "M"
                            }
                        }
                    ]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["discountRedemption"],
                "values": {
                    "discount": "/path/to/discount/1 - /path/to/discount/2",
                    "product" : [{
                        "category": "",
                        "sku"     : "Promotional Discount",
                        "events"  : {"discountRedemption": 20.00}
                    }]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["cartPurchase"],
                "values": {
                    "orderId"       : "00e40e2d-13a2-4a00-a8ee-01a9ebb0bf68",
                    "shippingMethod": "overnight",
                    "paymentMethod" : "Amex",
                    "billingState"  : "NY",
                    "billingZip"    : "10458",
                    "product"       : [{"category": "", "sku": "", "quantity": "", "price": ""}]
                },
                "componentPath": "commerce/components/submitorder"
            });
        }
        return true;
    }
</script>
```

#### Limite do tamanho das chamadas de rastreamento {#limiting-the-size-of-tracking-calls}

Geralmente, os navegadores da Web limitam o tamanho das solicitações do GET. Como o produto CQ e os valores de SKU são caminhos de repositório, as matrizes de produtos que incluem vários valores podem exceder o limite de tamanho da solicitação. Portanto, seus componentes devem limitar o número de itens no `product` matriz de cada `CQ_Analytics.record function`. Crie várias funções se o número de itens que você precisa rastrear puder exceder o limite.

Por exemplo, o componente de remetente de comércio eletrônico limita o número de `product` itens em uma chamada para quatro. Quando o carrinho contém mais de quatro produtos, ele gera vários `CQ_Analytics.record` funções.
