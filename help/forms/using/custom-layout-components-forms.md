---
title: Criação de componentes de layout personalizados para formulários adaptáveis
seo-title: Criação de componentes de layout personalizados para formulários adaptáveis
description: Procedimento para criar componentes de layout personalizados para formulários adaptáveis.
seo-description: Procedimento para criar componentes de layout personalizados para formulários adaptáveis.
uuid: 09a0cacc-d693-46dc-90a3-254d1878a68a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 102718cb-592a-4a5c-89a6-ad4d56f3d547
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Criação de componentes de layout personalizados para formulários adaptáveis {#creating-custom-layout-components-for-adaptive-forms}

## Pré-requisitos {#prerequisite}

Conhecimento de layouts, que permite criar/usar um layout personalizado. Consulte [Alteração do layout do painel](/help/forms/using/layout-capabilities-adaptive-forms.md).

## Componente de layout do painel de formulário adaptável {#adaptive-form-panel-layout-component}

O componente Layout do painel de formulário adaptável controla a maneira como os componentes de formulário adaptáveis são posicionados em um painel relativo à interface do usuário.

## Criação de um layout de painel personalizado {#creating-a-custom-panel-layout}

1. Navegue até o local `/crx/de`.
1. Copie um layout de painel do local `/libs/fd/af/layouts/panel` (por exemplo, `tabbedPanelLayout`) para `/apps` (por exemplo, `/apps/af-custom-layout`).
1. Renomeie o layout copiado para `customPanelLayout`. Altere as propriedades dos nós `qtip` e `jcr:description`. Por exemplo, altere-os para `Custom layout - Toggle tabs`.

![Instantâneo CRX DE Layout do Painel Personalizado](assets/custom.png)

>[!NOTE]
>
>Definir a propriedade `guideComponentType`como o valor `fd/af/layouts/panel` determina que o layout é um layout de painel.

1. Renomeie o arquivo `tabbedPanelLayout.jsp` sob o novo layout para customPanelLayout.jsp.
1. Para introduzir novos estilos e comportamentos, crie uma biblioteca de cliente no nó `etc`. Por exemplo, no local /etc/af-custom-layout-clientlib, crie o nó client-library. Deixe que o nó tenha a propriedade categoria af.panel.custom. Ele tem os seguintes arquivos .css e .js:

   ```css
   /** CSS defining new styles used by custom layout **/
   
   .menu-nav {
       background-color: rgb(198, 38, 76);
       height: 30px;
    width: 30px;
    font-size: 2em;
    color: white;
       -webkit-transition: -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: transform 1s;
   }
   
   .tab-content {
    border: 1px solid #08b1cf;
   }
   
   .custom-navigation {
       -webkit-transition: width 1s, height 1s, -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: width 1s, height 1s, transform 1s;
   }
   
   .panel-name {
       padding-left: 30px;
       font-size: 20px;
   }
   
   @media (min-width: 992px) {
    .nav-close {
     width: 0px;
       }
   }
   
   @media (min-width: 768px) and (max-width: 991px) {
    .nav-close {
     height: 0px;
       }
   }
   
   @media (max-width: 767px) {
    .menu-nav, .custom-navigation {
        display: none;
       }
   }
   ```

   ```
   /** function for toggling the navigators **/
   var toggleNav = function () {
   
       var nav = $('.custom-navigation');
       if (nav) {
           nav.toggleClass('nav-close');
       }
   }
   
   /** function to populate the panel title **/
   $(window).on('load', function() {
       if (window.guideBridge) {
           window.guideBridge.on("elementNavigationChanged",
           function (evntName, evnt) {
                       var activePanelSom = evnt.newText,
                           activePanel = window.guideBridge._guideView.getView(activePanelSom);
                       $('.panel-name').html(activePanel.$itemNav.find('a').html());
                   }
           );
       }
   });
   ```

1. Para aprimorar a aparência e o comportamento, você pode incluir um `client library`.

   Além disso, atualize os caminhos dos scripts incluídos em arquivos .jsp. Por exemplo, atualize o arquivo `customPanelLayout.jsp` da seguinte maneira:

   ```
   <%-- jsp encapsulating navigator container and panel container divs --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <cq:includeClientLib categories="af.panel.custom"/>
   <div>
       <div class="row">
           <div class="col-md-2 col-sm-2 hidden-xs menu-nav glyphicon glyphicon-align-justify" onclick="toggleNav();"></div>
           <div class="col-md-10 col-sm-10 hidden-xs panel-name"></div>
       </div>
       <div class="row">
           <div class="col-md-2 hidden-xs guide-tab-stamp-list custom-navigation">
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp" />
           </div>
           <div  class="col-md-10">
               <c:if test="${fn:length(guidePanel.description) > 0}">
                   <div class="<%=GuideConstants.GUIDE_PANEL_DESCRIPTION%>">
                       ${guide:encodeForHtml(guidePanel.description,xssAPI)}
                           <cq:include script="/libs/fd/af/components/panel/longDescription.jsp"/>
                   </div>
               </c:if>
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/panelContainer.jsp"/>
           </div>
       </div>
   </div>
   ```

   O arquivo `/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp`:

   ```
   <%-- jsp governing the navigation part --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <%@ page import="com.adobe.aemds.guide.utils.StyleUtils" %>
   <%-- navigation tabs --%>
   <ul id="${guidePanel.id}_guide-item-nav-container" class="tab-navigators tab-navigators-vertical in"
       data-guide-panel-edit="reorderItems" role="tablist">
       <c:forEach items="${guidePanel.items}" var="panelItem">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <li id="${panelItem.id}_guide-item-nav" title="${guide:encodeForHtmlAttr(panelItem.navTitle,xssAPI)}" data-path="${panelItem.path}" role="tab" aria-controls="${panelItem.id}_guide-item">
               <c:set var="panelItemCss" value="${panelItem.cssClassName}"/>
               <% String panelItemCss = (String) pageContext.getAttribute("panelItemCss");%>
               <a data-guide-toggle="tab" class="<%= StyleUtils.addPostfixToClasses(panelItemCss, "_nav") %> guideNavIcon nested_${isNestedLayout}">${guide:encodeForHtml(panelItem.navTitle,xssAPI)}</a>
               <c:if test="${isNestedLayout}">
                   <guide:initializeBean name="guidePanel" className="com.adobe.aemds.guide.common.GuidePanel"
                       resourcePath="${panelItem.path}" restoreOnExit="true">
                       <sling:include path="${panelItem.path}"
                                      resourceType="/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp"/>
                   </guide:initializeBean>
               </c:if>
               <em></em>
           </li>
       </c:forEach>
   </ul>
   ```

   O `/apps/af-custom-layout/customPanelLayout/panelContainer.jsp` atualizado:

   ```
   <%-- jsp governing the panel content --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   
   <div id="${guidePanel.id}_guide-item-container" class="tab-content">
       <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Top') }">
           <sling:include path="${guidePanel.toolbar.path}"/>
       </c:if>
   
   <c:forEach items="${guidePanel.items}" var="panelItem">
       <div class="tab-pane" id="${panelItem.id}_guide-item" role="tabpanel">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <c:if test="${isNestedLayout}">
               <c:set var="guidePanelResourceType" value="/apps/af-custom-layout/customPanelLayout/panelContainer.jsp" scope="request"/>
           </c:if>
           <sling:include path="${panelItem.path}" resourceType="${panelItem.resourceType}"/>
       </div>
   </c:forEach>
   <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Bottom')}">
       <sling:include path="${guidePanel.toolbar.path}"/>
   </c:if>
   </div>
   ```

1. Abra um formulário adaptável no modo Criação. O layout do painel definido é adicionado à lista para configurar layouts de painel.

   ![O layout do Painel personalizado é exibido na ](assets/auth-layt.png) ![lista de layout do painelCaptura de tela do formulário adaptativo, usando o ](assets/s1.png) ![layout personalizado do painelCaptura de tela que demonstra a funcionalidade de alternância do layout personalizado](assets/s2.png)

Amostra de ZIP para um layout de painel personalizado e um formulário adaptável usando-o.

[Obter arquivo](assets/af-custom-layout.zip)
