---
title: Extensão da pesquisa de ativos
description: Estenda os recursos de pesquisa do  [!DNL Experience Manager] Assets além das pesquisas prontas para uso de ativos por strings.
contentOwner: AG
feature: Search
role: Developer
exl-id: d68c735f-2699-4923-a7e7-4d1356eae335
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 15%

---

# Extensão da pesquisa de ativos {#extending-assets-search}

Você pode estender os recursos de pesquisa do Adobe Experience Manager Assets. Imediatamente, [!DNL Experience Manager] o Assets pesquisa por ativos por strings.

A pesquisa é feita por meio da interface do QueryBuilder para que a pesquisa possa ser personalizada com vários predicados. Você pode sobrepor o conjunto padrão de predicados no seguinte diretório: `/apps/dam/content/search/searchpanel/facets`.

Também é possível adicionar outras guias ao painel de administração [!DNL Experience Manager] do Assets.

>[!CAUTION]
>
>A partir de [!DNL Experience Manager] 6.4, a interface do usuário clássica está obsoleta. Para anúncio, consulte [Recursos obsoletos e removidos](../release-notes/deprecated-removed-features.md). É recomendável usar a interface habilitada para toque. Para personalizações, consulte [Pesquisar aspectos](search-facets.md).

## Sobreposição {#overlaying}

Para sobrepor os predicados pré-configurados, copie o nó `facets` de `/libs/dam/content/search/searchpanel` para `/apps/dam/content/search/searchpanel/` ou especifique outra propriedade `facetURL` na configuração do painel de pesquisa (o padrão é `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Por padrão, a estrutura de diretório em / `apps` não existe e precisa ser criada. Certifique-se de que os tipos de nó correspondam àqueles em / `libs`.

## Adição de guias {#adding-tabs}

É possível adicionar outras guias de Pesquisa, configurando-as no [!DNL Experience Manager] Administrador de ativos. Para criar guias adicionais:

1. Crie a estrutura de pastas `/apps/wcm/core/content/damadmin/tabs,`se ela ainda não existir, e copie o nó `tabs` de `/libs/wcm/core/content/damadmin` e cole-o.
1. Crie e configure a segunda guia, conforme desejado.

   >[!NOTE]
   >
   >Ao criar um segundo siteadminsearchpanel, certifique-se de definir uma propriedade `id` para evitar conflitos de formulário.

## Criação de predicados personalizados {#creating-custom-predicates}

[!DNL Experience Manager] Os ativos vêm com um conjunto de predicados predefinidos que podem ser usados para personalizar uma página de Compartilhamento de ativos. Personalizar um Compartilhamento de ativos dessa maneira é abordado em [Criar e configurar uma página de compartilhamento de ativos](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Além de usar predicados pré-existentes, os desenvolvedores [!DNL Experience Manager] também podem criar seus próprios predicados usando a [API do Construtor de consultas](/help/sites-developing/querybuilder-api.md).

Criar predicados personalizados requer conhecimento básico sobre a [estrutura de widgets](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

A prática recomendada é copiar um predicado existente e ajustá-lo. Os predicados de amostra estão localizados em `/libs/cq/search/components/predicates`.

### Exemplo: Criar um predicado de propriedade simples {#example-build-a-simple-property-predicate}

Para criar um predicado de propriedade:

1. Crie uma pasta de componentes no diretório de projetos, por exemplo `/apps/geometrixx/components/titlepredicate`.
1. Adicionar `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Adicionar `titlepredicate.jsp`.

   ```xml
   <%--
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
   
       });
   
   </script>
   ```

1. Para disponibilizar o componente, é necessário editá-lo. Para tornar um componente editável, no CRXDE, adicione um nó `cq:editConfig` do tipo primário `cq:EditConfig`. Para que possa remover parágrafos, adicione uma propriedade de vários valores `cq:actions` com um único valor **DELETE**.
1. Navegue até o navegador e, na página de exemplo (por exemplo, `press.html`), alterne para o modo de design e ative o novo componente para o sistema de predicado de parágrafo (por exemplo, **left**).

1. No modo **Editar**, o novo componente agora está disponível no sidekick (encontrado no grupo **Pesquisar**). Insira o componente na coluna **Predicates** e digite uma palavra de pesquisa, por exemplo, **Diamond** e clique na lupa para iniciar a pesquisa.

   >[!NOTE]
   >
   >Ao pesquisar, digite o termo exatamente, incluindo as letras maiúsculas e minúsculas corretas.

### Exemplo: Criar um predicado de grupo simples {#example-build-a-simple-group-predicate}

Para criar um predicado de grupo:

1. Crie uma pasta de componentes no diretório de projetos, por exemplo `/apps/geometrixx/components/picspredicate`.
1. Adicionar `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Adicionar `titlepredicate.jsp`:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
   
       });
   ```

1. Para disponibilizar o componente, é necessário editá-lo. Para tornar um componente editável, no CRXDE, adicione um nó `cq:editConfig` do tipo primário `cq:EditConfig`. Para que possa remover parágrafos, adicione uma propriedade de vários valores `cq:actions` com um único valor `DELETE`.
1. Navegue até o navegador e, na página de exemplo (por exemplo, `press.html`), alterne para o modo de design e ative o novo componente para o sistema de predicado de parágrafo (por exemplo, **left**).
1. No modo **Editar**, o novo componente agora está disponível no sidekick (encontrado no grupo **Pesquisar**). Insira o componente na coluna **Predicates**.

### Widgets de predicado instalados {#installed-predicate-widgets}

Os predicados a seguir estão disponíveis como widgets ExtJS pré-configurados.

### Predicado de texto completo {#fulltextpredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | Sequência de caracteres | Nome do predicado. O padrão é `fulltext` |
| searchCallback | Função | Retorno de chamada para acionar a pesquisa no evento `keyup`. O padrão é `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | Sequência de caracteres | Nome do predicado. O padrão é `property` |
| propertyName | Sequência de caracteres | Nome da propriedade JCR. O padrão é `jcr:title` |
| defaultValue | Sequência de caracteres | Valor padrão pré-preenchido. |

### PathPredicate {#pathpredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | Sequência de caracteres | Nome do predicado. O padrão é `path` |
| rootPath | Sequência de caracteres | Caminho raiz do predicado. O padrão é `/content/dam` |
| pathFieldPredicateName | Sequência de caracteres | O padrão é `folder` |
| showFlatOption | Booleano | Sinalizador para mostrar a Caixa de seleção `search in subfolders`. O padrão é true. |

### DatePredicate {#datepredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| predicateName | Sequência de caracteres | Nome do predicado. O padrão é `daterange` |
| propertyname | Sequência de caracteres | Nome da propriedade JCR. O padrão é `jcr:content/jcr:lastModified` |
| defaultValue | Sequência de caracteres | Valor padrão pré-preenchido |

### OptionsPredicate {#optionspredicate}

| Propriedade | Tipo | Descrição |
|---|---|---|
| título | Sequência de caracteres | Adiciona um título superior adicional |
| predicateName | Sequência de caracteres | Nome do predicado. O padrão é `daterange` |
| propertyname | Sequência de caracteres | Nome da propriedade JCR. O padrão é `jcr:content/metadata/cq:tags` |
| colapso | Sequência de caracteres | Recolher nível. O padrão é `level1` |
| triggerSearch | Booleano | Sinalizador para acionar a pesquisa ao verificar. O padrão é false |
| searchCallback | Função | Retorno de chamada para acionar a pesquisa. O padrão é `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Número | Tempo limite antes do acionamento de searchCallback. O padrão é 800 ms |

## Personalização dos resultados da pesquisa {#customizing-search-results}

A apresentação dos resultados da pesquisa em uma página Compartilhamento de ativos é regida pela lente selecionada. [!DNL Experience Manager] Os ativos vêm com um conjunto de lentes predefinidas que podem ser usadas para personalizar uma página de Compartilhamento de ativos. Personalizar um Compartilhamento de ativos dessa maneira é abordado em [Criar e configurar uma página de compartilhamento de ativos](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Além de usar lentes pré-existentes, os desenvolvedores [!DNL Experience Manager] também podem criar suas próprias lentes.
