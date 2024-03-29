---
title: Bibliotecas de tags
seo-title: Tag Libraries
description: As bibliotecas de tags Granite, CQ e Sling fornecem acesso a funções específicas para uso no script JSP de seus modelos e componentes
seo-description: The Granite, CQ, and Sling tag libraries give you access to specific functions for use in the JSP script of your templates and components
uuid: e622d47b-cfb3-4b4a-b8e3-e1adee294219
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6678e3c3-fb0f-4300-8838-38f23f14db07
exl-id: 24d53784-5915-4638-ab2b-26f897cca13b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 1%

---

# Bibliotecas de tags{#tag-libraries}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

As bibliotecas de tags Granite, CQ e Sling fornecem acesso a funções específicas para uso no script JSP de seus modelos e componentes.

## Biblioteca de tags do Granite {#granite-tag-library}

A biblioteca de tags do Granite contém funções úteis.

Ao desenvolver o script jsp de um componente da interface do usuário do Granite, é recomendável incluir o seguinte código na parte superior do script:

```xml
<%@include file="/libs/granite/ui/global.jsp"%>
```

O global também declara que [Biblioteca Sling](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### &lt;ui:includeClientLib> {#ui-includeclientlib}

O `<ui:includeClientLib>` tag Inclui uma biblioteca de cliente html AEM, que pode ser uma biblioteca js, css ou de temas. Para várias inclusões de tipos diferentes, por exemplo js e css, essa tag precisa ser usada várias vezes no jsp. Esta tag é um invólucro de conveniência em torno do ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)` interface de serviço.

Ela tem os seguintes atributos:

**categorias** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas Javascript e CSS para as categorias fornecidas. O nome do tema é extraído da solicitação.

Equivalente a: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**tema** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas relacionadas ao tema (tanto CSS quanto JS) para as categorias fornecidas. O nome do tema é extraído da solicitação.

Equivalente a: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas JavaScript para as categorias fornecidas.

Equivalente a: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas CSS para as categorias fornecidas.

Equivalente a: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**temático** - Deve ser incluído um sinalizador que indique apenas bibliotecas temáticas ou não. Se omitido, ambos os conjuntos serão incluídos. Aplica-se somente a JS ou CSS puro (não para categorias ou inclui temas).

O `<ui:includeClientLib>` pode ser usada da seguinte maneira em um jsp:

```xml
<%-- all: js + theme (theme-js + css) --%>
<ui:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<ui:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<ui:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<ui:includeClientLib css="cq.collab.calendar, cq.security" />
```

## Biblioteca de tags CQ {#cq-tag-library}

A biblioteca de tags CQ contém funções úteis.

Para usar a Biblioteca de tags do CQ no script, o script deve começar com o seguinte código:

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
```

>[!NOTE]
>
>Quando a variável `/libs/foundation/global.jsp` estiver incluído no script, o taglib será declarado automaticamente.

Ao desenvolver o script jsp de um componente AEM, é recomendável incluir o seguinte código na parte superior do script:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

Ele declara os taglibs de sling, CQ e jstl e expõe os objetos de script usados regularmente, definidos pela variável [ `<cq:defineObjects />`](#amp-lt-cq-defineobjects) . Isso reduz e simplifica o código jsp do seu componente.

### &lt;cq:text> {#cq-text}

O `<cq:text>` é uma tag de conveniência que gera o texto do componente em um JSP.

Ela tem os seguintes atributos opcionais:

**propriedade** - Nome da propriedade a ser usada. O nome é relativo ao recurso atual.

**value** - Valor a ser usado para saída. Se esse atributo estiver presente, ele substituirá o uso do atributo da propriedade.

**oldValue** - Valor a ser usado para saída diff. Se esse atributo estiver presente, ele substituirá o uso do atributo da propriedade.

**escapeXml** - Define se os caracteres &lt;, >, &amp;, &#39; e &quot; na sequência de caracteres resultante devem ser convertidos em seus códigos de entidade de caractere correspondentes. O valor padrão é false. Observe que o escape é aplicado após a formatação opcional.

**format** - Java.text.Format opcional para usar a formatação do texto.

**noDiff** - Suprime o cálculo de uma saída diff, mesmo que haja uma informação diff presente.

**tagClass** - Nome da classe CSS de um elemento que rodeará uma saída não vazia. Se estiver vazio, nenhum elemento será adicionado.

**tagName** - Nome do elemento que rodeará uma saída não vazia. O padrão é DIV.

**espaço reservado** - Valor padrão a ser usado para texto nulo ou vazio no modo de edição, ou seja, o espaço reservado. Observe que a verificação padrão é executada após a formatação opcional e o escape, ou seja, é gravado como está na saída. O padrão é:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default** - Valor padrão a ser usado para texto nulo ou vazio. Observe que a verificação padrão é executada após a formatação opcional e o escape, ou seja, é gravado como está na saída.

Alguns exemplos de como a função `<cq:text>` pode ser usada em um JSP:

```xml
<cq:text property="jcr:title" tagName="h2"/>
<cq:text property="jcr:description" tagName="p"/>

<cq:text value="<%= listItem.getTitle() %>" tagName="h4" placeholder="" />
<cq:text value="<%= listItem.getDescription() %>" tagName="p" placeholder=""/>

<cq:text property="jcr:title" value="<%= title %>" tagName="h3"/><%
    } else if (type.equals("link")) {
        %><cq:text property="jcr:title" value="<%= "\u00bb " + title %>" tagName="p" tagClass="link"/><%
    } else if (type.equals("extralarge")) {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h1"/><%
    } else {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h2"/><%

<cq:text property="jcr:description" placeholder="" tagName="small"/>

<cq:text property="tableData"
               escapeXml="false"
               placeholder="<img src=\"/libs/cq/ui/resources/0.gif\" class=\"cq-table-placeholder\" alt=\"\">"
    />

<cq:text property="text"/>

<cq:text property="image/jcr:description" placeholder="" tagName="small"/>
<cq:text property="text" tagClass="text"/>
```

### &lt;cq:setContentBundle> {#cq-setcontentbundle}

O `<cq:setContentBundle>` A tag cria um contexto de localização do i18n e o armazena no `javax.servlet.jsp.jstl.fmt.localizationContext` variável de configuração.

Ela tem os seguintes atributos:

**idioma** - O idioma do local para o qual recuperar o pacote de recursos.

**source** - a origem da localidade. Ele pode ser definido como um dos seguintes valores:

* **estático** - a localidade é retirada do `language` se disponível, caso contrário, a partir da localidade padrão do servidor.

* **página** - a localidade é retirada do idioma da página ou recurso atual, se disponível, caso contrário, do `language` se disponível, caso contrário, a partir da localidade padrão do servidor.

* **solicitação** - a localidade é retirada da localidade da solicitação ( `request.getLocale()`).

* **auto** - a localidade é retirada do `language` se disponível, caso contrário, a partir do idioma da página ou recurso atual, se disponível, caso contrário, da solicitação.

Se a variável `source` não está definido:

* Se a variável `language` for definido, a variável `source` padrão do atributo para &quot; `static`.

* Se a variável `language` não estiver definido, a variável `source` padrões de atributo para `auto`.

O &quot;pacote de conteúdo&quot; pode ser simplesmente usado pelo JSTL padrão `<fmt:message>` tags. A pesquisa de mensagens por chaves é de duas vezes:

1. Primeiro, as propriedades do JCR do recurso subjacente que está renderizado no momento são pesquisadas por traduções. Isso permite definir uma caixa de diálogo de componente simples para editar esses valores.
1. Se o nó não contiver uma propriedade chamada exatamente como a chave, o fallback será carregar um pacote de recursos da solicitação de sling ( `SlingHttpServletRequest.getResourceBundle(Locale)`). O idioma ou o local para este pacote é definido pelo idioma e pelos atributos de origem do `<cq:setContentBundle>` .

O `<cq:setContentBundle>` pode ser usada da seguinte maneira em um jsp.

Para páginas que definem seu idioma:

```xml
... %><cq:setContentBundle source="page"/><%  %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

Para páginas personalizadas do usuário:

```xml
... %><cq:setContentBundle scope="request"/><% %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

### &lt;cq:include> {#cq-include}

O `<cq:include>` inclui um recurso na página atual.

Ela tem os seguintes atributos:

**liberação**

* Um booleano que define se libera a saída antes de incluir o target.

**caminho**

* O caminho para o objeto de recurso a ser incluído no processamento de solicitação atual. Se esse caminho for relativo, ele será anexado ao caminho do recurso atual cujo script está incluindo o recurso em questão. O caminho e o resourceType ou o script devem ser especificados.

**resourceType**

* O tipo de recurso do recurso a ser incluído. Se o tipo de recurso estiver definido, o caminho deverá ser o caminho exato para um objeto de recurso: nesse caso, não há suporte para adicionar parâmetros, seletores e extensões ao caminho.
* Se o recurso a ser incluído for especificado com o atributo de caminho que não pode ser resolvido para um recurso, a tag poderá criar um objeto de recurso sintético fora do caminho e desse tipo de recurso.
* O caminho e o resourceType ou o script devem ser especificados.

**script**

* O script jsp a ser incluído. O caminho e o resourceType ou o script devem ser especificados.

**ignoreComponentHierarchy**

* Um booleano que controla se a hierarquia do componente deve ser ignorada para a resolução do script. Se true, somente os caminhos de pesquisa serão respeitados.

**Exemplo:**

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><div class="center">
    <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
    <cq:include path="title" resourceType="foundation/components/title" />
    <cq:include script="redirect.jsp"/>
    <cq:include path="par" resourceType="foundation/components/parsys" />
</div>
```

Você deve usar `<%@ include file="myScript.jsp" %>` ou `<cq:include script="myScript.jsp" %>` para incluir um script?

* O `<%@ include file="myScript.jsp" %>` A diretiva informa o compilador JSP a incluir um arquivo completo no arquivo atual. É como se o conteúdo do arquivo incluído tivesse sido colado diretamente no arquivo original.
* Com o `<cq:include script="myScript.jsp">` , o arquivo é incluído no tempo de execução.

Você deve usar `<cq:include>` ou `<sling:include>`?

* Ao desenvolver componentes AEM, o Adobe recomenda que você use `<cq:include>`.
* `<cq:include>` permite incluir diretamente os arquivos de script pelo nome ao usar o atributo de script. Isso leva em conta a herança do tipo de componente e recurso e geralmente é mais simples do que a adesão estrita à resolução do script do Sling usando seletores e extensões.

### &lt;cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` é descontinuado desde o AEM 5.6. [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) deve ser usada em vez disso.

O `<cq:includeClientLib>` tag Inclui uma biblioteca de cliente html AEM, que pode ser uma biblioteca js, css ou de temas. Para várias inclusões de tipos diferentes, por exemplo js e css, essa tag precisa ser usada várias vezes no jsp. Esta tag é um invólucro de conveniência em torno do `com.day.cq.widget.HtmlLibraryManager` interface de serviço.

Ela tem os seguintes atributos:

**categorias** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas Javascript e CSS para as categorias fornecidas. O nome do tema é extraído da solicitação.

Equivalente a: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**tema** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas relacionadas ao tema (tanto CSS quanto JS) para as categorias fornecidas. O nome do tema é extraído da solicitação.

Equivalente a: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas JavaScript para as categorias fornecidas.

Equivalente a: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css** - Uma lista de categorias de bibliotecas de clientes separadas por vírgulas. Isso incluirá todas as bibliotecas CSS para as categorias fornecidas.

Equivalente a: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**temático** - Deve ser incluído um sinalizador que indique apenas bibliotecas temáticas ou não. Se omitido, ambos os conjuntos serão incluídos. Aplica-se somente a JS ou CSS puro (não para categorias ou inclui temas).

O `<cq:includeClientLib>` pode ser usada da seguinte maneira em um jsp:

```xml
<%-- all: js + theme (theme-js + css) --%>
<cq:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<cq:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<cq:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<cq:includeClientLib css="cq.collab.calendar, cq.security" />
```

### &lt;cq:defineObjects> {#cq-defineobjects}

O `<cq:defineObjects>` A tag expõe os seguintes objetos de script, usados regularmente, que podem ser referenciados pelo desenvolvedor. Também expõe os objetos definidos pela variável [ `<sling:defineObjects>`](#amp-lt-sling-defineobjects) .

**componentContext**

* o objeto de contexto do componente atual da solicitação (com.day.cq.wcm.api.components.ComponentContext interface).

**componente**

* o objeto do componente de AEM atual do recurso atual (com.day.cq.wcm.api.components.Component interface).

**currentDesign**

* o objeto de design atual da página atual (com.day.cq.wcm.api.designer.Design interface).

**currentPage**

* o objeto de página WCM AEM atual (com.day.cq.wcm.api.Page interface).

**currentStyle**

* o objeto de estilo atual da célula atual (com.day.cq.wcm.api.designer.Style interface).

**designer**

* o objeto do designer usado para acessar informações de design (com.day.cq.wcm.api.designer.Designer interface).

**editContext**

* o objeto edit context do componente AEM (com.day.cq.wcm.api.components.EditContext interface).

**pageManager**

* o objeto do gerenciador de página para operações no nível da página (com.day.cq.wcm.api.PageManager interface).

**pageProperties**

* o objeto de propriedades de página da página atual (org.apache.sling.api.resource.ValueMap).

**propriedades**

* o objeto properties do recurso atual (org.apache.sling.api.resource.ValueMap).

**resourceDesign**

* o objeto de design da página de recursos (com.day.cq.wcm.api.designer.Design interface).

**resourcePage**

* o objeto da página de recursos (com.day.cq.wcm.api.Page interface).
* Ela tem os seguintes atributos:

**requestName**

* herdado do sling

**responseName**

* herdado do sling

**resourceName**

* herdado do sling

**nodeName**

* herdado do sling

**logName**

* herdado do sling

**resourceResolverName**

* herdado do sling

**slingName**

* herdado do sling

**componentContextName**

* específico do wcm

**editContextName**

* específico do wcm

**propertiesName**

* específico do wcm

**pageManagerName**

* específico do wcm

**currentPageName**

* específico do wcm

**resourcePageName**

* específico do wcm

**pagePropertiesName**

* específico do wcm

**componentName**

* específico do wcm

**designerName**

* específico do wcm

**currentDesignName**

* específico do wcm

**resourceDesignName**

* específico do wcm

**currentStyleName**

* específico do wcm

**Exemplo**

```xml
<%@page session="false" contentType="text/html; charset=utf-8" %><%
%><%@ page import="com.day.cq.wcm.api.WCMMode" %><%
%><%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><cq:defineObjects/>
```

>[!NOTE]
>
>Quando a variável `/libs/foundation/global.jsp` estiver incluído no script, a variável `<cq:defineObjects />` é incluída automaticamente.

### &lt;cq:requestURL> {#cq-requesturl}

O `<cq:requestURL>` tag grava o URL da solicitação atual no JspWriter. As duas tags [ `<cq:addParam>`](#amp-lt-cq-addparam) e [ `<cq:removeParam>`](#amp-lt-cq-removeparam) e podem ser usados dentro do corpo dessa tag para modificar o URL da solicitação atual antes que ele seja gravado.

Ela permite criar links para a página atual com parâmetros variáveis. Por exemplo, permite transformar a solicitação:

`mypage.html?mode=view&query=something` em `mypage.html?query=something`.

O uso de `addParam` ou `removeParam` somente altera a ocorrência de um determinado parâmetro, todos os outros parâmetros não são afetados.

`<cq:requestURL>` não tem nenhum atributo.

Exemplos:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addParam> {#cq-addparam}

O `<cq:addParam>` adiciona um parâmetro de solicitação com o nome e o valor fornecidos à inclusão [ `<cq:requestURL>`](#amp-lt-cq-requesturl) .

Ela tem os seguintes atributos:

**name**

* nome do parâmetro a ser adicionado

**valor**

* valor do parâmetro a ser adicionado

**Exemplo:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeParam> {#cq-removeparam}

O `<cq:removeParam>` remove um parâmetro de solicitação com o nome e o valor fornecidos da inclusão [ `<cq:requestURL>`](#amp-lt-cq-requesturl) . Se nenhum valor for fornecido, todos os parâmetros com o nome especificado serão removidos.

Ela tem os seguintes atributos:

**name**

* nome do parâmetro a ser removido

Exemplo:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

## Biblioteca de tags Sling {#sling-tag-library}

A biblioteca de tags do Sling contém funções úteis do Sling.

Ao usar a Biblioteca de tags do Sling em seu script, o script deve começar com o seguinte código:

```xml
<%@ taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %>
```

>[!NOTE]
>
>Quando a variável `/libs/foundation/global.jsp` estiver incluído no script, o sling taglib será declarado automaticamente.

### &lt;sling:include> {#sling-include}

O `<sling:include>` inclui um recurso na página atual.

Ela tem os seguintes atributos:

**liberação**

* Um booleano que define se libera a saída antes de incluir o target.

**resource**

* O objeto de recurso a ser incluído no processamento de solicitação atual. É necessário especificar o recurso ou o caminho. Se ambos forem especificados, o recurso terá prioridade.

**caminho**

* O caminho para o objeto de recurso a ser incluído no processamento de solicitação atual. Se esse caminho for relativo, ele será anexado ao caminho do recurso atual cujo script está incluindo o recurso em questão. É necessário especificar o recurso ou o caminho. Se ambos forem especificados, o recurso terá prioridade.

**resourceType**

* O tipo de recurso do recurso a ser incluído. Se o tipo de recurso estiver definido, o caminho deverá ser o caminho exato para um objeto de recurso: nesse caso, não há suporte para adicionar parâmetros, seletores e extensões ao caminho.
* Se o recurso a ser incluído for especificado com o atributo de caminho que não pode ser resolvido para um recurso, a tag poderá criar um objeto de recurso sintético fora do caminho e desse tipo de recurso.

**replaceSelectors**

* Ao despachar, os seletores são substituídos pelo valor desse atributo.

**addSelectors**

* Ao despachar, o valor desse atributo é adicionado aos seletores.

**replaceSuffix**

* Ao despachar, o sufixo é substituído pelo valor desse atributo.

>[!NOTE]
>
>A resolução do recurso e o script incluídos com a variável `<sling:include>` é igual a uma resolução normal de URL do sling. Por padrão, os seletores, a extensão etc. da solicitação atual também são usadas para o script incluído. Eles podem ser modificados por meio dos atributos da tag : por exemplo `replaceSelectors="foo.bar"` permite substituir os seletores.

Exemplos:

```xml
<div class="item"><sling:include path="<%= pathtoinclude %>"/></div>
```

```xml
<sling:include resource="<%= par %>"/>
```

```xml
<sling:include addSelectors="spool"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include replaceSelectors="content" />
```

### &lt;sling:defineObjects> {#sling-defineobjects}

O `<sling:defineObjects>` A tag expõe os seguintes objetos de script, usados regularmente, que podem ser referenciados pelo desenvolvedor:

**slingRequest**

* O objeto SlingHttpServletRequest , que fornece acesso às informações do cabeçalho da solicitação HTTP - estende o HttpServletRequest padrão - e fornece acesso a itens específicos do Sling, como recursos, informações de caminho, seletor, etc.

**slingResponse**

* Objeto SlingHttpServletResponse, que fornece acesso à resposta HTTP criada pelo servidor. Atualmente, é o mesmo que HttpServletResponse, a partir do qual se estende.**solicitação**
* O objeto de solicitação JSP padrão que é um HttpServletRequest puro.**resposta**
* O objeto de resposta JSP padrão que é um HttpServletResponse puro.

**resourceResolver**

* O objeto ResourceResolver atual. É igual a slingRequest.getResourceResolver()

.**sling**

* Um objeto SlingScriptHelper, contendo métodos de conveniência para scripts, principalmente sling.include(&#39;/some/other/resource&#39;) para incluir as respostas de outros recursos dentro dessa resposta (por exemplo, incorporar os snippets html do cabeçalho (embutido) e sling.getService (foo.bar.Service.class) para recuperar os serviços OSGi disponíveis no Sling (notação de classe dependendo da linguagem de script).

**resource**

* o objeto de Recurso atual a ser tratado, dependendo do URL da solicitação. É igual a slingRequest.getResource().

**currentNode**

* Se o recurso atual apontar para um nó JCR (o que normalmente é o caso no Sling), isso dará acesso direto ao objeto Node . Caso contrário, esse objeto não será definido.

**log**

* Fornece um Logger SLF4J para fazer logon no sistema de log do Sling a partir de scripts, por exemplo. log.info(&quot;Executando meu script&quot;).

* Ela tem os seguintes atributos:

**requestName**

**responseName**

**nodeName**

l **ogName resourceResolverName**

**slingName**

**Exemplo:**

```xml
<%@page session="false" %><%
%><%@page import="com.day.cq.wcm.foundation.forms.ValidationHelper"%><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/>
```

## Biblioteca de tags JSTL {#jstl-tag-library}

O [Biblioteca de tags padrão de páginas do JavaServer](https://www.oracle.com/technetwork/java/index-jsp-135995.html) contém muitas tags úteis e padrão. Os taglibs de núcleo, formatação e função são definidos pela variável `/libs/foundation/global.jsp` como mostrado no trecho a seguir.

### Extrato de /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Depois de importar o `/libs/foundation/global.jsp` como descrito anteriormente, você pode usar a variável `c`, `fmt` e `fn` prefixos para acessar esses taglibs. A documentação oficial do JSTL está disponível em [Tutorial do Java EE 5 - Biblioteca de tags padrão de páginas do JavaServer](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
