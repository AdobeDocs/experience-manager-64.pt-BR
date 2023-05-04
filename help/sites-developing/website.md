---
title: Criar um site com recursos completos (JSP)
seo-title: Create a Fully-Featured Website (JSP)
description: Este tutorial permite que você crie um site em destaque com o AEM
seo-description: This tutorial enables you to create a fully featured website with AEM
uuid: bb8d4efd-7631-4cc5-8084-b03c6aabdef3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8d14017d-d311-45e9-8aea-4a5ca46f1a07
exl-id: 6d408fd6-9241-4069-9b04-806e30e03ff2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4935'
ht-degree: 2%

---

# Criar um site com recursos completos (JSP){#create-a-fully-featured-website-jsp}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Este artigo descreve como criar um site usando o JSP e com base na interface clássica. O Adobe recomenda o aproveitamento das tecnologias de AEM mais recentes para seus sites, conforme descrito detalhadamente no artigo [Introdução ao desenvolvimento do AEM Sites](/help/sites-developing/getting-started.md).

Este tutorial permite que você crie um site em destaque com o Adobe Experience Manager (AEM). O site será baseado em um site genérico e será direcionado principalmente para desenvolvedores da Web. Todo o desenvolvimento ocorrerá em um ambiente de criação.

Este tutorial descreve como:

1. Instalar AEM.
1. Acesse o CRXDE Lite (o ambiente de desenvolvimento).
1. Configure a estrutura do projeto no CRXDE Lite.
1. Crie o modelo, o componente e os scripts usados como a base para a criação de páginas de conteúdo.
1. Crie a página raiz do seu site e, em seguida, as páginas de conteúdo.
1. Crie os seguintes componentes para uso em suas páginas:

   * **[!UICONTROL Navegação superior]**
   * **[!UICONTROL Listar secundários]**
   * **[!UICONTROL Logotipo]**
   * **[!UICONTROL Imagem]**
   * **[!UICONTROL Imagem de texto]**
   * **[!UICONTROL Pesquisar]**

1. Inclua vários componentes fundamentais.

Depois de executar todas as etapas, suas páginas terão a seguinte aparência:

![chlimage_1-99](assets/chlimage_1-99.png)

**Baixe o resultado final**

Para acompanhar o tutorial em vez de realizar os exercícios, baixe o site-1.0.zip. Este arquivo é um pacote de conteúdo AEM que contém os resultados deste tutorial. Use [Gerenciador de pacotes](/help/sites-administering/package-manager.md) para instalar o pacote na instância do autor.

>[!NOTE]
>A instalação deste pacote substituirá todos os recursos na sua instância de criação que você criou usando este tutorial.

Pacote de conteúdo do site

[Obter arquivo](assets/website-1_0.zip)

## Instalação do Adobe Experience Manager {#installing-adobe-experience-manager}

Para instalar uma instância do AEM para desenvolver seu site, siga as instruções para configurar um [ambiente de implantação com instâncias de criação e publicação](/help/sites-deploying/deploy.md#author-and-publish-installs)ou executar uma [instalação genérica](/help/sites-deploying/deploy.md#default-local-install). A instalação genérica envolve o download do arquivo AEM Quickstart JAR, colocar o arquivo license.properties no mesmo diretório do arquivo JAR e clicar duas vezes no arquivo JAR.

Depois de instalar o AEM, acesse o ambiente de desenvolvimento do CRXDE Lite clicando no link CRXDE Lite na página de boas-vindas:

![chlimage_1-100](assets/chlimage_1-100.png)

>[!NOTE]
>
>O URL do CRXDE Lite para uma instância de criação de AEM que é instalada localmente usando a porta padrão é [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/).

## Configuração da estrutura do projeto no CRXDE Lite {#setting-up-the-project-structure-in-crxde-lite}

Use o CRXDE Lite para criar a estrutura de aplicativos do meu site no repositório:

1. Na árvore no lado esquerdo do CRXDE Lite, clique com o botão direito do mouse no **`/apps`** e clique em **[!UICONTROL Criar > Criar pasta]**. No **Criar pasta** diálogo, tipo `mywebsite` como o nome da pasta e clique em **OK**.
1. Clique com o botão direito do mouse no `/apps/mywebsite` e clique em **[!UICONTROL Criar > Criar pasta]**. No **[!UICONTROL Criar pasta]** diálogo, tipo `components` como o nome da pasta e clique em **[!UICONTROL OK]**.
1. Clique com o botão direito do mouse no `/apps/mywebsite` e clique em **[!UICONTROL Criar > Criar pasta]**. No **[!UICONTROL Criar pasta]** diálogo, tipo `templates` como o nome da pasta e clique em **[!UICONTROL OK]**.

   A estrutura na árvore agora deve ser parecida com isto:

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. Clique em **[!UICONTROL Salvar tudo]**.

## Configuração do design {#setting-up-the-design}

Nesta seção, crie o design para seu aplicativo usando a ferramenta Designer. O design fornece recursos de CSS e imagem para seu site.

>[!NOTE]
>
>Clique no link a seguir para baixar ``mywebsite.zip``. O arquivo contém os arquivos estáticos.css e de imagem para seu design.

Exemplo de arquivo estático.css e imagens

[Obter arquivo](assets/mywebsite.zip)

1. Na página AEM Boas-vindas, clique em **[!UICONTROL Ferramentas]**. ([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html))

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. Na árvore de pastas, selecione o **[!UICONTROL Designs]** e clique em **[!UICONTROL Novo > Nova página]**. Tipo `mywebsite` como título e clique em **[!UICONTROL Criar]**.

1. Se o item do meu site não aparecer na tabela, atualize a árvore ou a tabela.

1. [Usando o WebDAV](/help/sites-administering/webdav-access.md) acesse o URL em http://localhost:4502, copie a amostra `static.css` e `images` pasta do arquivo mysite.zip baixado na `/etc/designs/mywebsite` pasta.

   ![chlimage_1-103](assets/chlimage_1-103.png)

## Criação do modelo, componente e script da página de conteúdo {#creating-the-contentpage-template-component-and-script}

Nesta seção, você cria o seguinte:

* O modelo de página de conteúdo que será usado para criar páginas de conteúdo no site de exemplo
* O componente página de conteúdo que será usado para renderizar páginas de conteúdo
* O script da página de conteúdo

### Criação do modelo de página de conteúdo {#creating-the-contentpage-template}

Crie um modelo para usar como base das páginas da Web do site.

Um modelo define o conteúdo padrão de uma nova página. Sites complexos podem usar vários modelos para criar os diferentes tipos de páginas no site. Neste exercício, todas as páginas são baseadas em um modelo simples.

1. Na árvore de pastas do CRXDE Lite, clique com o botão direito do mouse `/apps/mywebsite/templates` e clique em **[!UICONTROL Criar > Criar modelo]**.

1. Na caixa de diálogo Criar modelo, digite os seguintes valores e clique em **[!UICONTROL Próximo]**:

   * **[!UICONTROL Rótulo]**: contentpage
   * **[!UICONTROL Título]**: Modelo de página de conteúdo do meu site
   * **[!UICONTROL Descrição]**: Este é meu modelo de página de conteúdo do site
   * **[!UICONTROL Tipo de recurso]**: mysite/components/contentpage

   Use o valor padrão para a propriedade Classificação .

   ![chlimage_1-104](assets/chlimage_1-104.png)

   O tipo de recurso identifica o componente que renderiza a página. Nesse caso, todas as páginas criadas usando o modelo de página de conteúdo são renderizadas pelo `mywebsite/components/contentpage` componente.

1. Para especificar os caminhos das páginas que podem usar esse modelo, clique no botão de adição e digite `/content(/.*)?` na caixa de texto exibida. Em seguida, clique em **[!UICONTROL Próximo]**.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   O valor da propriedade de caminho permitida é um *expressão regular.* As páginas que têm um caminho que corresponde à expressão podem usar o modelo . Nesse caso, a expressão regular corresponde ao caminho da variável `/content` e todas as subpáginas.

   Quando um autor cria uma página abaixo `/content`, o **[!UICONTROL contentpage]** O modelo é exibido em uma lista de modelos disponíveis para uso.

1. Clique em **[!UICONTROL Próximo]** no **[!UICONTROL Pais permitidos]** e **[!UICONTROL Filhos permitidos]** painéis e clique em **[!UICONTROL OK]**. No CRXDE Lite, clique em **[!UICONTROL Salvar tudo]**.

   ![chlimage_1-106](assets/chlimage_1-106.png)

#### Criação do componente Conteúdo da página {#creating-the-contentpage-component}

Crie o *componente* que define o conteúdo e renderiza as páginas que usam o modelo contentpage. O local do componente deve corresponder ao valor da propriedade Tipo de recurso do modelo de página de conteúdo.

1. No CRXDE Lite, clique com o botão direito do mouse `/apps/mywebsite/components` e clique em **[!UICONTROL Criar > Componente]**.
1. No **[!UICONTROL Criar componente]** digite os seguintes valores de propriedade:

   * **[!UICONTROL Rótulo]**: contentpage
   * **[!UICONTROL Título]**: Componente da página Conteúdo do meu site
   * **[!UICONTROL Descrição]**: Este é o Componente da Página Conteúdo do Meu Site

   ![chlimage_1-107](assets/chlimage_1-107.png)

   O local do novo componente é `/apps/mywebsite/components/contentpage`. Esse caminho corresponde ao tipo de recurso do modelo de página de conteúdo (menos o `/apps/` parte do caminho).

   Essa correspondência conecta o modelo ao componente e é essencial para o funcionamento correto do site.

1. Clique em **[!UICONTROL Próximo]** até que o **[!UICONTROL Filhos permitidos]** O painel da caixa de diálogo é exibido e, em seguida, clique em **[!UICONTROL OK]**. No CRXDE Lite, clique em **[!UICONTROL Salvar tudo]**.

   A estrutura agora tem a seguinte aparência:

   ![chlimage_1-108](assets/chlimage_1-108.png)

#### Desenvolvimento do script de componente de página de conteúdo {#developing-the-contentpage-component-script}

Adicione o código ao script contentpage.jsp para definir o conteúdo da página.

1. No CRXDE Lite, abra o arquivo `contentpage.jsp` em `/apps/mywebsite/components/contentpage`. O arquivo contém o seguinte código por padrão:

   ```java
   <%--
   
     My Website Content Page Component component.
   
     This is My Website Content Page Component.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %><%
   %><%
       /* TODO add you code here */
   %>
   ```

1. Copie o código a seguir e cole-o em contentpage.jsp após o código padrão:

   ```java
   <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
       pageEncoding="ISO-8859-1"%>
   <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
   "https://www.w3.org/TR/html4/loose.dtd">
   <html>
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
   <title>My title</title>
   </head>
   <body>
   <div>My body</div>
   </body>
   </html>
   ```

1. Clique em **[!UICONTROL Salvar tudo]** para salvar as alterações.

### Criação da página do site e das páginas de conteúdo {#creating-your-website-page-and-content-pages}

Nesta seção, crie as seguintes páginas que usam o modelo de página de conteúdo: Meu site, inglês, produtos, serviços e clientes.

1. Na página de boas-vindas do AEM ([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html)), clique em Sites.

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. Na árvore de pastas, selecione o **[!UICONTROL Sites]** e clique em **[!UICONTROL Novo > Nova página]**.
1. No **[!UICONTROL Criar página]** digite:

   * **[!UICONTROL Título]**: `My Website`
   * **[!UICONTROL Nome]**: `mywebsite`
   * Selecione o **[!UICONTROL Modelo de página de conteúdo do meu site]**

   ![chlimage_1-110](assets/chlimage_1-110.png)

1. Clique em **[!UICONTROL Criar]**. Na árvore de pastas, selecione o `/Websites/My Website` e clique em **[!UICONTROL Novo > Nova página]**.
1. No **[!UICONTROL Criar página]** , insira os seguintes valores de propriedade e clique em Criar:

   * **[!UICONTROL Título]**: Inglês
   * **[!UICONTROL Nome]**: en
   * Selecione o **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. Na árvore de pastas, selecione o `/Websites/My Website/English` e clique em **[!UICONTROL Novo > Nova página]**.
1. No **[!UICONTROL Criar página]** , insira os seguintes valores de propriedade e clique em **[!UICONTROL Criar]**:

   * **[!UICONTROL Título]**: Produtos
   * Selecione o **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. Na árvore de pastas, selecione o `/Websites/My Website/English` e clique em **[!UICONTROL Novo > Nova página]**.
1. No **[!UICONTROL Criar página]** , insira os seguintes valores de propriedade e clique em **[!UICONTROL Criar]**:

   * **Título**: Serviços
   * Selecione o **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. Na árvore de pastas, selecione o `/Websites/My Website/English` e clique em **[!UICONTROL Novo > Nova página]**.
1. No **[!UICONTROL Criar página]** , insira os seguintes valores de propriedade e clique em **[!UICONTROL Criar]**:

   * **Título**: Clientes
   * Selecione o **[!UICONTROL Modelo de página de conteúdo do meu site]**

   Sua estrutura tem a seguinte aparência:

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. Para vincular suas páginas ao design do mysite, no CRXDE Lite, selecione a variável `/content/mywebsite/en/jcr:content` nó . No **[!UICONTROL Propriedades]** , digite os seguintes valores para uma nova propriedade e clique em Adicionar:

   * **[!UICONTROL Nome]**: cq:designPath
   * **[!UICONTROL Tipo]**: String
   * **[!UICONTROL Valor]**: /etc/designs/mywebsite

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. Em uma nova guia ou janela do navegador da Web, abra [http://localhost:4502/content/mywebsite/en/products.html](http://localhost:4502/content/mywebsite/en/products.html) para ver a página Produtos:

   ![chlimage_1-113](assets/chlimage_1-113.png)

### Aprimoramento do script de página de conteúdo {#enhancing-the-contentpage-script}

Esta seção descreve como aprimorar o script de página de conteúdo usando os scripts de componente de base AEM e escrevendo seus próprios scripts.

O **[!UICONTROL Produtos]** será exibida da seguinte maneira:

![chlimage_1-4](assets/chlimage_1-4.jpeg)

#### Uso de scripts de página de base {#using-the-foundation-page-scripts}

Neste exercício, você configura seu componente de conteúdo de página para que seu supertipo seja o componente Página de AEM. Como os componentes herdam os recursos de seu supertipo, o conteúdo da página herda os scripts e as propriedades do componente Página.

Por exemplo, no código JSP do seu componente, é possível referenciar os scripts que o componente de supertipo fornece como se estivessem incluídos no seu componente.

1. No CRXDE Lite, adicione uma propriedade ao `/apps/mywebsite/components/contentpage` nó .

   1. Selecione o `/apps/mywebsite/components/contentpage` nó .
   1. Na parte inferior da guia Propriedades, digite os seguintes valores de propriedade e clique em Adicionar:

      * **[!UICONTROL Nome]**: sling:resourceSuperType
      * **[!UICONTROL Tipo]**: String
      * **[!UICONTROL Valor]**: foundation/components/page
   1. Clique em **[!UICONTROL Salvar tudo]**.


1. Abra o `contentpage.jsp` arquivo em `/apps/mywebsite/components/contentpage` e substitua o código existente pelo seguinte código:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" contentType="text/html; charset=utf-8" %><%
   %><!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
   <html>
   <cq:include script="head.jsp"/>
   <cq:include script="body.jsp"/>
   </html>
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. Tem a seguinte aparência:

   ![chlimage_1-5](assets/chlimage_1-5.jpeg)

   Abra a fonte da página para ver os elementos javascript e HTML que os scripts head.jsp e body.jsp geraram. O seguinte trecho de script abre o Sidekick quando você abre a página:

   ```java
   CQ.WCM.launchSidekick("/content/mywebsite/en/products",
               {propsDialog: "/libs/foundation/components/page/dialog",
                  locked: false locked: false
                }); 
   ```

#### Usar seus próprios scripts {#using-your-own-scripts}

Nesta seção, você cria vários scripts que geram uma parte do corpo da página. Em seguida, crie o arquivo body.jsp no componente pagecontent para substituir o body.jsp do componente Página AEM. No arquivo body.jsp, você inclui os scripts que geram as diferentes partes do corpo da página.

**Dica:** Quando um componente inclui um arquivo que tem o mesmo nome e o mesmo local relativo de um arquivo no supertipo do componente, ele é chamado *sobreposição*.

1. No CRXDE Lite, crie o arquivo `left.jsp` under `/apps/mywebsite/components/contentpage`:

   1. Clique com o botão direito do mouse no nó `/apps/mywebsite/components/contentpage`, em seguida selecione **[!UICONTROL Criar]** then **[!UICONTROL Criar arquivo]**.
   1. Na janela , digite `left.jsp` como** Nome** e clique em **[!UICONTROL OK]**.

1. Editar o arquivo `left.jsp` para remover o conteúdo existente e substituir pelo seguinte código:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="left">
   <div>logo</div>
   <div>newslist</div>
   <div>search</div>
   </div>
   ```

1. Salve as alterações.
1. No CRXDE Lite, crie o arquivo `center.jsp` under `/apps/mywebsite/components/contentpage`:

   1. Clique com o botão direito do mouse no nó `/apps/mywebsite/components/contentpage`, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar arquivo]**.
   1. Na caixa de diálogo, digite `center.jsp` as **[!UICONTROL Nome]** e clique em **[!UICONTROL OK]**.

1. Editar o arquivo `center.jsp` para remover o conteúdo existente e substituí-lo pelo seguinte código:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="center">
   <div>trail</div>
   <div>title</div>
   <div>parsys</div>
   </div>
   ```

1. Salve as alterações.
1. No CRXDE Lite, crie o arquivo `right.jsp` under `/apps/mywebsite/components/contentpage`:

   1. Clique com o botão direito do mouse no nó `/apps/mywebsite/components/contentpage`, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar arquivo]**.
   1. Na caixa de diálogo, digite `right.jsp` as **[!UICONTROL Nome]** e clique em **[!UICONTROL OK]**.

1. Editar o arquivo `right.jsp` para remover o conteúdo existente e substituir pelo seguinte código:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="right">
   <div>iparsys</div>
   </div>
   ```

1. Salve as alterações.
1. No CRXDE Lite, crie o arquivo `body.jsp` under `/apps/mywebsite/components/contentpage`:
1. Editar o arquivo `body.jsp` para remover o conteúdo existente e substituir pelo seguinte código:

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><body>
   <div id="CQ">
   <div class="topnav">topnav</div>
   <div class="content">
   <cq:include script="left.jsp" />
   <cq:include script="center.jsp" />
   <cq:include script="right.jsp" />
   </div>
   <div class="footer">
   <div class="toolbar">toolbar</div>
   </div>
   </div>
   </body>
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. Tem a seguinte aparência:

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

### Criação do componente Navegação superior {#creating-the-top-navigation-component}

Nesta seção, você cria um componente que exibe links para todas as páginas de nível superior do site para facilitar a navegação. Esse conteúdo de componente é exibido na parte superior de todas as páginas criadas usando o modelo de página de conteúdo.

Na primeira versão do componente de navegação superior (topnav) os itens de navegação são apenas links de texto. Na segunda versão, você implementa a navegação superior com links de navegação de imagem.

Sua navegação superior terá a seguinte aparência:

![chlimage_1-114](assets/chlimage_1-114.png)

#### Criação do componente Navegação superior {#creating-the-top-navigation-component-1}

1. No CRXDE Lite, clique com o botão direito do mouse `/apps/mywebsite/components`, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar componente]**.
1. No **[!UICONTROL Criar componente]** digite:

   * **[!UICONTROL Rótulo]**: `topnav`
   * **[!UICONTROL Título]**: `My Top Navigation Component`
   * **[!UICONTROL Descrição]**: `This is My Top Navigation Component`

1. Clique em **[!UICONTROL Próximo]** até chegar à última janela em que você clicou **[!UICONTROL OK]**. Salve as alterações.

#### Criação do script de navegação superior com links textuais {#creating-the-top-navigation-script-with-textual-links}

Adicione o script de renderização ao topnav para gerar links de texto para páginas filhas:

1. No CRXDE Lite, abra o arquivo `topnav.jsp` under `/apps/mywebsite/components/topnav`.
1. Substitua o código que está lá copiando e colando o seguinte código:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><% 
   %><%@ page import="java.util.Iterator,
           com.day.text.Text, 
           com.day.cq.wcm.api.PageFilter, com.day.cq.wcm.api.Page" %><% 
       /* get starting point of navigation */
       Page navRootPage = currentPage.getAbsoluteParent(2); 
       if (navRootPage == null && currentPage != null) { 
       navRootPage = currentPage; 
       }
       if (navRootPage != null) { 
           Iterator<Page> children = navRootPage.listChildren(new PageFilter(request));
           while (children.hasNext()) { 
               Page child = children.next(); 
               %><a href="<%= child.getPath() %>.html"><%=child.getTitle() %></a><% 
           } 
       } 
   %> 
   ```

#### Inclusão da navegação superior no componente Página de conteúdo {#including-top-navigation-in-the-contentpage-component}

Para incluir o topnav no seu componente contentpage:

1. No CRXDE Lite, abra o `body.jsp` under `/apps/mywebsite/components/contentpage`e substituir:

   ```xml
   <div class="topnav">topnav</div>
   ```

   com:

   ```xml
   <cq:include path="topnav" resourceType="mywebsite/components/topnav" />
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** Página. A navegação superior é exibida da seguinte maneira:

   ![chlimage_1-115](assets/chlimage_1-115.png)

#### Aprimoramento de páginas com legendas {#enhancing-pages-with-subtitles}

O **[!UICONTROL Página]** O componente define propriedades que permitem fornecer legendas para páginas. Adicione legendas que fornecem informações sobre o conteúdo da página.

1. No seu navegador, abra o **[!UICONTROL Produtos]** página.
1. No Sidekick **[!UICONTROL Página]** clique em **[!UICONTROL Propriedades da página]**.
1. No **[!UICONTROL Básico]** da caixa de diálogo, expandir **[!UICONTROL Mais títulos e descrição]** e para o **[!UICONTROL Legenda]** propriedade, tipo `what we do`. Clique em **[!UICONTROL OK]**.
1. Repita as etapas anteriores para adicionar o subtítulo **sobre nossos serviços** para **[!UICONTROL Serviços]** página.
1. Repita as etapas anteriores para adicionar o subtítulo **a confiança que ganhamos** para **[!UICONTROL Clientes]** página.

   **Dica:** No CRXDE Lite, selecione o nó /content/mywebsite/en/products/jcr:content para ver que a propriedade de subtítulo é adicionada.

#### Aprimorar a navegação superior usando links de imagem {#enhance-top-navigation-by-using-image-links}

Aprimore o script de renderização do componente de navegação superior para usar links de imagem em vez de hipertexto para os controles de navegação. A imagem inclui o título e o subtítulo do direcionamento do link.

Este exercício demonstra [Processamento de solicitação Sling](/help/sites-developing/the-basics.md#sling-request-processing). O script topnav.jsp é modificado para chamar um script que gera dinamicamente imagens para serem usadas nos links de navegação da página. Neste exercício, o Sling analisa o URL dos arquivos de origem da imagem para determinar o script a ser usado para renderizar as imagens.

Por exemplo, a origem do link da imagem para a página Produtos pode ser http://localhost:4502/content/mywebsite/en/products.navimage.png. O Sling analisa esse URL para determinar o tipo de recurso e o script a ser usado para renderizar o recurso:

1. O Sling determina o caminho do recurso a ser `/content/mwebysite/en/products.png.`
1. O Sling corresponde a este caminho com o `/content/mywebsite/en/products` nó .
1. O Sling determina o `sling:resourceType` deste nó a ser `mywebsite/components/contentpage`.

1. O Sling encontra o script neste componente que melhor corresponde ao seletor de URL ( `navimage`) e extensão de nome de arquivo ( `png`).

Neste exercício, o Sling corresponde esses URLs ao script /apps/mywebsite/components/contentpage/navimage.png.java que você cria.

1. No CRXDE Lite, abra o `topnav.jsp` under `/apps/mywebsite/components/topnav.`Localize o conteúdo do elemento de âncora (linha 14):

   ```xml
   <%=child.getTitle() %>
   ```

1. Substitua o conteúdo da âncora pelo seguinte código:

   ```xml
   <img alt="<%= child.getTitle() %>" src="<%= child.getPath() %>.navimage.png">
   ```

1. Salve as alterações.
1. Clique com o botão direito do mouse no `/apps/mywebsite/components/contentpage` e clique em **[!UICONTROL Criar > Criar arquivo]**.
1. No **[!UICONTROL Criar arquivo]** janela, como **[!UICONTROL Nome]**, tipo `navimage.png.java`.

   A extensão de nome de arquivo .java indica ao Sling que o suporte Java a scripts do Apache deve ser usado para compilar o script e criar um servlet.

1. Copie o código a seguir em `navimage.png.java.`O código estende a classe AbstractImageServlet:

   * [AbstractImageServlet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) cria um objeto ImageContext que armazena as propriedades do recurso atual.
   * A página principal do recurso é extraída do objeto ImageContext. O título e o subtítulo da página são obtidos.
   * [ImageHelper](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ImageHelper.html) é usada para gerar a imagem do arquivo navimage_bg.jpg do design do site, o título da página e o subtítulo da página.

   ```java
   package apps.mywebsite.components.contentpage;
   
   import java.awt.Color; 
   import java.awt.Paint; 
   import java.awt.geom.Rectangle2D; 
   
   import java.io.IOException;
   import javax.jcr.RepositoryException; 
   
   import com.day.cq.wcm.api.Page; 
   import com.day.cq.wcm.api.PageManager; 
   import com.day.cq.wcm.api.components.Component; 
   import com.day.cq.wcm.api.designer.Designer;
   
   import com.day.cq.commons.SlingRepositoryException; 
   import com.day.cq.wcm.commons.WCMUtils; 
   import com.day.cq.wcm.commons.AbstractImageServlet; 
   import com.day.cq.commons.ImageHelper; 
   
   import com.day.image.Font; 
   import com.day.image.Layer; 
   
   import org.apache.sling.api.SlingHttpServletRequest; 
   import org.apache.sling.api.SlingHttpServletResponse; 
   import org.apache.sling.api.resource.Resource; 
   import org.apache.sling.api.servlets.SlingSafeMethodsServlet; 
   
   /**
     * Renders the navigation image
     */ 
   public class navimage_png extends AbstractImageServlet {
   
         protected Layer createLayer(ImageContext ctx)
                throws RepositoryException, IOException {
            PageManager pageManager = ctx.resolver.adaptTo(PageManager.class);
            Page currentPage = pageManager.getContainingPage(ctx.resource);
   
            /* constants for image appearance */
            int scale = 6;
            int paddingX = 24;
            int paddingY = 24;
            Color bgColor = new Color(0x004a565c, true);
   
            /* obtain the page title */
            String title = currentPage.getTitle();
            if (title == null) {
                title = currentPage.getName();
            }
   
            /* format the title text */
            title = title.toUpperCase();
            Paint titleColor = Color.WHITE;
            Font titleFont = new Font("Myriad Pro", 10 * scale, Font.BOLD);
            int titleBase = 10 * scale;
   
            /* obtain and format the page subtitle */
            String subtitle = currentPage.getProperties().get("subtitle", "");
            Paint subtitleColor = new Color(0xffa9afb1, true);
            Font subTitleFont = new Font("Tahoma", 7);
            int subTitleBase = 20;
   
            /* create a layer that contains the background image from the mywebsite design */
            Designer dg = ctx.resolver.adaptTo(Designer.class);
            String imgPath = new String(dg.getDesignPath(currentPage)+"/images/navimage_bg.jpg");
            Layer bg = ImageHelper.createLayer(ctx.resolver.resolve(imgPath));
   
            /* draw the title text (4 times bigger) */
            Rectangle2D titleExtent = titleFont.getTextExtent(0, 0, 0, 0, title, Font.ALIGN_LEFT, 0, 0);
            Rectangle2D subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
   
            /* ensure subtitleExtent is wide enough */
            if ( subtitle.length() > 0 ) {
                int titleWidth = (int)titleExtent.getWidth() / scale;
                if ( subtitleExtent.getWidth() > titleWidth && subtitleExtent.getWidth() + 2 * paddingX >
    bg.getWidth() ) {
                    int charWidth = (int)subtitleExtent.getWidth() / subtitle.length();
                    int maxWidth = (bg.getWidth() > titleWidth + 2  * paddingX ? bg.getWidth() - 2 * paddingX : titleWidth);
                    int len = (maxWidth - ( 2 * charWidth) ) / charWidth;
                    subtitle = subtitle.substring(0, len) + "...";
                    subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
                }
            }
            int width = Math.max((int) titleExtent.getWidth(), (int) subtitleExtent.getWidth());
           /* create the text layer */
            Layer text = new Layer(width, (int) titleExtent.getHeight() + 40, new Color(0x01ffffff, true));
            text.setPaint(titleColor);
            text.drawText(0, titleBase, 0, 0, title, titleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0);
            text.resize(text.getWidth() / scale, text.getHeight() / scale);
            text.setX(0);
            text.setY(0);
   
            if (subtitle.length() > 0) {
                /* draw the subtitle normal sized */
                text.setPaint(subtitleColor);
                text.drawText(0, subTitleBase, 0, 0, subtitle, subTitleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0); 
            }
   
            /* merge the image and text layers */
            text.setY(paddingY);
            text.setX(paddingX);
            text.setBackgroundColor(bgColor);
   
            int bgWidth = bg.getWidth();
            if ( text.getWidth() + 2 * paddingX > bgWidth ) {
                bgWidth = text.getWidth() + 2 * paddingX;
                bg.resize(bgWidth, bg.getHeight());
            }
            bg.merge(text);
   
            return bg;
        }
    }
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. A navegação superior agora aparece da seguinte maneira:

   ![screen_shot_2012-03-07at10047pm](assets/screen_shot_2012-03-07at10047pm.png)

### Criação do componente Filhos da lista {#creating-the-list-children-component}

Crie o componente listchildren que gera uma lista de links de página que incluem o título, a descrição e a data das páginas (por exemplo, páginas de produto). Os links direcionam as páginas filhas da página atual ou de uma página raiz especificada na caixa de diálogo do componente.

![chlimage_1-116](assets/chlimage_1-116.png)

#### Criação de páginas de produtos {#creating-product-pages}

Crie duas páginas localizadas abaixo da variável **[!UICONTROL Produtos]** página. Para cada página, que descreve dois produtos específicos, você define um título, uma descrição e uma data.

1. Na árvore de pastas do **[!UICONTROL Sites]** selecione o **[!UICONTROL Sites/Meu site/Inglês/Produtos]** item e clique em **[!UICONTROL Novo > Nova página]**.
1. Na caixa de diálogo, digite os seguintes valores de propriedade e clique em **[!UICONTROL Criar]**:

   * **[!UICONTROL Título]**: Produto 1.
   * **[!UICONTROL Nome]**: produto1.
   * Selecionar **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. Crie outra página abaixo de Produtos usando os seguintes valores de propriedade:

   * **[!UICONTROL Título]**: Produto 2
   * **[!UICONTROL Nome]**: produto2
   * Selecionar **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. No CRXDE Lite, defina uma descrição e uma data para a página do Produto 1:

   1. Selecione o `/content/mywebsite/en/products/product1/jcr:content` nó .
   1. No **[!UICONTROL Propriedades]** , insira os seguintes valores:

      * **[!UICONTROL Nome]**: `jcr:description`
      * **[!UICONTROL Tipo]**: `String`
      * **[!UICONTROL Valor]**: `This is a description of the Product 1!.`
   1. Clique em **[!UICONTROL Adicionar]**.
   1. No **[!UICONTROL Propriedades]** , crie outra propriedade usando os seguintes valores:

      * **[!UICONTROL Nome]**: data
      * **[!UICONTROL Tipo]**: String
      * **[!UICONTROL Valor]**: 14/02/2008
      * Clique em **[!UICONTROL Adicionar]**.
   1. Clique em **[!UICONTROL Salvar tudo]**.



1. No CRXDE Lite, defina uma descrição e uma data para a página Produto 2:

   1. Selecione o `/content/mywebsite/en/products/product2/jcr:content` nó .
   1. No **[!UICONTROL Propriedades]** , insira os seguintes valores:

      * **[!UICONTROL Nome]**: jcr:description
      * **[!UICONTROL Tipo]**: String
      * **[!UICONTROL Valor]**: Esta é uma descrição do Produto 2!.
   1. Clique em **[!UICONTROL Adicionar]**.
   1. Nas mesmas caixas de texto, substitua os valores anteriores pelos seguintes valores:

      * **[!UICONTROL Nome]**: data
      * **[!UICONTROL Tipo]**: String
      * **[!UICONTROL Valor]**: 11/05/2012
      * Clique em **[!UICONTROL Adicionar]**.
   1. Clique em **[!UICONTROL Salvar tudo]**.



#### Criação do componente Filhos da lista {#creating-the-list-children-component-1}

Para criar o componente listchildren:

1. No CRXDE Lite, clique com o botão direito do mouse `/apps/mywebsite/components`, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar componente]**.
1. Na caixa de diálogo, digite os seguintes valores de propriedade e clique em **[!UICONTROL Próximo]**:

   * **[!UICONTROL Rótulo]**: listem crianças.
   * **[!UICONTROL Título]**: Componente Minhas Listchildren.
   * **[!UICONTROL Descrição]**: Este é o Componente Minhas Listchildren .

1. Continue clicando em **[!UICONTROL Próximo]** até que o **[!UICONTROL Filhos permitidos]** for exibido e clique em **[!UICONTROL OK]**.

#### Criando o script de lista de filhos {#creating-the-list-children-script}

Desenvolva o script para o componente listchildren.

1. No CRXDE Lite, abra o arquivo `listchildren.jsp` under `/apps/mywebsite/components/listchildren`.
1. Substitua o código padrão pelo seguinte código:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="java.util.Iterator,
            com.day.cq.wcm.api.PageFilter"%><%
        /* Create a new Page object using the path of the current page */ 
         String listroot = properties.get("listroot", currentPage.getPath());
        Page rootPage = pageManager.getPage(listroot);
        /* iterate through the child pages and gather properties */
        if (rootPage != null) {
            Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
            while (children.hasNext()) {
                Page child = children.next();
                String title = child.getTitle() == null ? child.getName() : child.getTitle();
                String date = child.getProperties().get("date","");
                %><div class="item">
                <a href="<%= child.getPath() %>.html"><b><%= title %></b></a>
                <span><%= date %></span><br>
                <%= child.getProperties().get("jcr:description","") %><br>
                </div><%
            }
        }
    %>
   ```

1. Salve as alterações.

#### Caixa de diálogo Filhos da lista {#creating-the-list-children-dialog}

Crie a caixa de diálogo usada para configurar as propriedades do componente listchildren.

1. Crie o nó de diálogo sob o componente listchildren:

   1. No CRXDE Lite, clique com o botão direito do mouse no `/apps/mywebsite/components/listchildren`e clique em **[!UICONTROL Criar > Criar caixa de diálogo]**.
   1. Na caixa de diálogo, digite os seguintes valores de propriedade e clique em OK

      * **[!UICONTROL Rótulo]**: `dialog`
      * **[!UICONTROL Título]**: `Edit Component` e clique em **[!UICONTROL OK]**.

   ![screen_shot_2012-03-07at45818pm](assets/screen_shot_2012-03-07at45818pm.png)

   Com as seguintes propriedades:

   ![screen_shot_2012-03-07at50415pm](assets/screen_shot_2012-03-07at50415pm.png)

1. Selecione o `/apps/mywebsite/components/listchildren/dialog/items/items/tab1` nó .
1. No **[!UICONTROL Propriedades]** , altere o valor da variável **[!UICONTROL título]** propriedade para `List Children`

   ![chlimage_1-117](assets/chlimage_1-117.png)

1. Selecione o **tab1** e clique em **[!UICONTROL Criar > Criar nó]**, insira os seguintes valores de propriedade e clique em **[!UICONTROL OK]**:

   * **[!UICONTROL Nome]**: items
   * **[!UICONTROL Tipo]**: cq:WidgetCollection

   ![screen_shot_2012-03-07at51018pm](assets/screen_shot_2012-03-07at51018pm.png)

1. Crie um nó abaixo do nó items usando os seguintes valores de propriedade:

   * **[!UICONTROL Nome]**: listroot
   * **[!UICONTROL Tipo]**: cq:Widget

   ![screen_shot_2012-03-07at51031pm](assets/screen_shot_2012-03-07at51031pm.png)

1. Adicione propriedades para o nó listroot para configurá-lo como um campo de texto. Cada linha na tabela a seguir representa uma propriedade. Quando terminar, clique em **[!UICONTROL Salvar tudo]**.

   | Nome | Tipo | Valor |
   |---|---|---|
   | fieldLabel | String | Caminho da raiz da lista |
   | name | String | ./listroot |
   | xtype | String | campo de texto |

   ![screen_shot_2012-03-07at51433pm](assets/screen_shot_2012-03-07at51433pm.png)

#### Inclusão de filhos da lista no componente Página de conteúdo {#including-list-children-in-the-contentpage-component}

Para incluir o componente listchildren no seu componente página de conteúdo, proceda da seguinte maneira:

1. No CRXDE Lite, abra o arquivo `left.jsp` under `/apps/mywebsite/components/contentpage` e localize o seguinte código (linha 4):

   ```xml
   <div>newslist</div>
   ```

1. Substitua esse código pelo seguinte código:

   ```xml
   <cq:include path="newslist" resourceType="mywebsite/components/listchildren" />
   ```

1. Salve as alterações.

#### Exibindo filhos da lista em uma página {#viewing-list-children-in-a-page}

Para ver a operação completa deste componente, é possível visualizar a página Produtos :

* quando a página pai (&quot;Caminho da raiz da lista&quot;) não estiver definida.
* quando a página pai (&quot;Caminho da raiz da lista&quot;) é definida.

1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. O componente listchildren aparece da seguinte maneira:

   ![chlimage_1-118](assets/chlimage_1-118.png)

1. ![chlimage_1-119](assets/chlimage_1-119.png)

1. Como Caminho da raiz da lista, insira: `/content/mywebsite/en`. Clique em **[!UICONTROL OK]**. O componente listchildren na sua página agora tem a seguinte aparência:

   ![chlimage_1-120](assets/chlimage_1-120.png)

### Criação do componente de logotipo {#creating-the-logo-component}

Crie um componente que exiba o logotipo da empresa e forneça um link para a página inicial do site. O componente contém uma caixa de diálogo do modo de design para que os valores de propriedade sejam armazenados no design do site (/etc/designs/mywebsite):

* Os valores da propriedade se aplicam a todas as instâncias do componente que são adicionadas a páginas que usam o design.
* As propriedades podem ser configuradas usando qualquer instância do componente que esteja em uma página que use o design.

A caixa de diálogo do modo de design contém propriedades para definir a imagem e o caminho do link. O componente de logotipo será colocado no lado superior esquerdo de todas as páginas do site.

Ele terá a seguinte aparência:

![chlimage_1-121](assets/chlimage_1-121.png)

>[!NOTE]
>
>O Adobe Experience Manager fornece um componente de logotipo mais completo ( `/libs/foundation/components/logo`).

#### Criação do nó do componente de logotipo {#creating-the-logo-component-node}

Para criar o componente de logotipo, siga as etapas:

1. No CRXDE Lite, clique com o botão direito do mouse em /apps/mywebsite/components, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar componente]**.
1. Na caixa de diálogo Criar componente , digite os seguintes valores de propriedade e clique em Próximo:

   * **[!UICONTROL Rótulo]**: `logo`.
   * **[!UICONTROL Título]**: `My Logo Component`.
   * **[!UICONTROL Descrição]**: `This is My Logo Component`.

1. Clique em Avançar até acessar o painel final da caixa de diálogo e clique em **[!UICONTROL OK]**.

#### Criação do script do logotipo {#creating-the-logo-script}

Esta seção descreve como criar o script para exibir a imagem do logotipo com um link para a página inicial.

1. No CRXDE Lite, abra o arquivo `logo.jsp` under `/apps/mywebsite/components/logo`.
1. O código a seguir cria o link para a página inicial do site e adiciona uma referência à imagem do logotipo. Copie o código para `logo.jsp`:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.text.Text,
                      com.day.cq.wcm.foundation.Image,
                      com.day.cq.commons.Doctype" %><%
       /* obtain the path for home */
       long absParent = currentStyle.get("absParent", 2L);
       String home = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);
       /* obtain the image */
       Resource res = currentStyle.getDefiningResource("imageReference");
       if (res == null) {
           res = currentStyle.getDefiningResource("image");
       }
       /* if no image use text link, otherwise draw the image */
       %>
   <a href="<%= home %>.html"><%
       if (res == null) {
           %>Home<%
       } else {
           Image img = new Image(res);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out);
       }
       %></a>
   ```

1. Salve as alterações.

#### Criação da caixa de diálogo Design do logotipo {#creating-the-logo-design-dialog}

Crie a caixa de diálogo para configurar o componente do logotipo no modo Design . Os nós de diálogo do modo de design devem ser nomeados `design_dialog`.

1. Crie o nó de diálogo sob o componente de logotipo:

   1. Clique com o botão direito do mouse no `/apps/mywebsite/components/logo` e clique em **[!UICONTROL Criar > Criar caixa de diálogo]**.
   1. Digite os seguintes valores de propriedade e clique em **[!UICONTROL OK]**:

      * **[!UICONTROL Rótulo]** `design_dialog`
      * **[!UICONTROL Título]** `Logo (Design)`

1. Clique com o botão direito do mouse no nó tab1 na ramificação design_dialog e clique em Excluir. Clique em **[!UICONTROL Salvar tudo]**.
1. Em `design_dialog/items/items`nó , crie um novo nó chamado `img` de tipo `cq:Widget`. Adicione as seguintes propriedades e clique em **[!UICONTROL Salvar tudo]**:

   | Nome | Tipo | Valor |
   |---|---|---|
   | fileNameParameter | String | ./imageName |
   | fileReferenceParameter | String | ./imageReference |
   | name | String | ./imagem |
   | título | String | Imagem |
   | xtype | String | html5smartimage |

   ![chlimage_1-122](assets/chlimage_1-122.png)

#### Criação do script de renderização do logotipo {#creating-the-logo-render-script}

Crie o script que recupera a imagem do logotipo e a grava na página.

1. Clique com o botão direito do mouse no nó do componente de logotipo e clique em **[!UICONTROL Criar > Criar arquivo]** para criar o arquivo de script com o nome img.GET.java.
1. Abra o arquivo, copie o seguinte código no arquivo e clique em **[!UICONTROL Salvar tudo]**:

```java
package apps.mywebsite.components.logo;

import java.io.IOException;
import java.io.InputStream;

import javax.jcr.RepositoryException;
import javax.jcr.Property;
import javax.servlet.http.HttpServletResponse;

import com.day.cq.wcm.foundation.Image;
import com.day.cq.wcm.commons.RequestHelper;
import com.day.cq.wcm.commons.WCMUtils;
import com.day.cq.wcm.commons.AbstractImageServlet;
import com.day.cq.commons.SlingRepositoryException;
import com.day.image.Layer;
import org.apache.commons.io.IOUtils;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ValueMap;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;

/**
 * Renders an image
 */
public class img_GET extends AbstractImageServlet {

    protected Layer createLayer(ImageContext c)
            throws RepositoryException, IOException {
        /* don't create the layer yet. handle everything later */
        return null;
    }

    protected void writeLayer(SlingHttpServletRequest req,
                              SlingHttpServletResponse resp,
                              ImageContext c, Layer layer)
            throws IOException, RepositoryException {

        Image image = new Image(c.resource);
        image.setItemName(Image.NN_FILE, "image");
        image.setItemName(Image.PN_REFERENCE, "imageReference");
        if (!image.hasContent()) {
            resp.sendError(HttpServletResponse.SC_NOT_FOUND);
            return;
        }
        /* get pure layer */
        layer = image.getLayer(false, false, false);

        /* do not re-encode layer, just spool */
        Property data = image.getData();
        InputStream in = data.getStream();
        resp.setContentLength((int) data.getLength());
        String contentType = image.getMimeType();
        if (contentType.equals("application/octet-stream")) {
            contentType=c.requestImageType;
        }
        resp.setContentType(contentType);
        IOUtils.copy(in, resp.getOutputStream());
        in.close();

        resp.flushBuffer();
    }
}
```

#### Adicionar o componente de logotipo ao componente de página de conteúdo {#adding-the-logo-component-to-the-contentpage-component}

1. No CRXDE Lite, abra o `left.jsp` under `/apps/mywebsite/components/contentpage file` e localize a seguinte linha de código:

   ```xml
   <div>logo</div>
   ```

1. Substitua esse código pela seguinte linha de código:

   ```xml
   <cq:include path="logo" resourceType="mywebsite/components/logo" />
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. O logotipo aparece da seguinte maneira, embora atualmente mostre apenas o link subjacente:

   ![chlimage_1-123](assets/chlimage_1-123.png)

#### Configuração da imagem do logotipo em uma página {#setting-the-logo-image-in-a-page}

Esta seção descreve como definir uma imagem como logotipo usando a caixa de diálogo Modo de design.

1. Com o **[!UICONTROL Produtos]** página aberta no navegador, clique no botão **[!UICONTROL Design]** na parte inferior do Sidekick para entrar **[!UICONTROL Design]** modo.

   ![](do-not-localize/chlimage_1-10.png)

1. Na barra Design do logotipo, clique em **[!UICONTROL Editar]** para usar a caixa de diálogo para editar as configurações do componente de logotipo.
1. Na caixa de diálogo , clique em no painel do **[!UICONTROL Imagem]** navegue até a guia `logo.png` imagem que você extraiu do `mywebsite.zip` e clique em **[!UICONTROL OK]**.

   ![chlimage_1-124](assets/chlimage_1-124.png)

1. Clique no triângulo na barra de título do Sidekick para retornar ao **[!UICONTROL Editar]** modo.

   ![chlimage_1-7](assets/chlimage_1-7.jpeg)

1. No CRXDE Lite, vá para o seguinte nó para ver os valores de propriedade armazenados:

   `/etc/designs/mywebsite/jcr:content/contentpage/logo`

### Inclusão do componente de navegação estrutural {#including-the-breadcrumb-component}

Nesta seção, você inclui o componente navegação estrutural (trilha), que é um dos componentes fundamentais.

1. No CRXDE Lite, navegue até `/apps/mywebsite/components/contentpage`, abra o arquivo `center.jsp` e substituir:

   ```java
   <div>trail</div>
   ```

   com:

   ```xml
   <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos 1]** página. O componente de trilha tem a seguinte aparência:

   ![chlimage_1-125](assets/chlimage_1-125.png)

### Inclusão do componente de título {#including-the-title-component}

Nesta seção, você inclui o componente de título, que é um dos componentes fundamentais.

1. No CRXDE Lite, navegue até `/apps/mywebsite/components/contentpage`, abra o arquivo `center.jsp` e substituir:

   ```xml
   <div>title</div>
   ```

   com:

   ```xml
   <cq:include path="title" resourceType="foundation/components/title" />
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. O componente de título tem a seguinte aparência:

   ![chlimage_1-126](assets/chlimage_1-126.png)

>[!NOTE]
>É possível definir um Título diferente e o Tipo/Tamanho em **[!UICONTROL Editar]** modo.

### Inclusão do componente Sistema de parágrafo {#including-the-paragraph-system-component}

O sistema de parágrafo (parsys) é uma parte significativa de um site, pois gerencia uma lista de parágrafos. Ela permite que os autores adicionem componentes de parágrafo à página e fornece estrutura.

Adicione o componente parsys (um dos componentes fundamentais) ao seu componente contentpage.

1. No CRXDE Lite, navegue até `/apps/mywebsite/components/contentpage`, abra o arquivo `center.jsp` e localize a seguinte linha de código:

   ```xml
   <div>parsys</div>
   ```

1. Substitua essa linha de código pelo seguinte código e salve as alterações:

   ```xml
   <cq:include path="par" resourceType="foundation/components/parsys" />
   ```

1. No seu navegador, atualize o **[!UICONTROL Produtos]** página. Agora ele tem o componente parsys, o que é visto da seguinte maneira:

   ![chlimage_1-127](assets/chlimage_1-127.png)

### Criação do componente de imagem {#creating-the-image-component}

Crie um componente que exibe uma imagem no sistema de parágrafo. Para economizar tempo, o componente de imagem é criado como uma cópia do componente de logotipo com algumas alterações de propriedade.

>[!NOTE]
>
>O Adobe Experience Manager fornece um componente de imagem com mais recursos ( `/libs/foundation/components/image`).

#### Criação do componente de imagem {#creating-the-image-component-1}

1. Clique com o botão direito do mouse no `/apps/mywebsite/components/logo` e clique em **[!UICONTROL Copiar]**.
1. Clique com o botão direito do mouse no `/apps/mywebsite/components` e clique em **[!UICONTROL Colar]**.
1. Clique com o botão direito do mouse no `Copy of logo` nó , clique em **[!UICONTROL Renomear]**, exclua o texto e o tipo existentes `image`.

1. Selecione o `image` nó do componente e altere os seguintes valores de propriedade:

   * `jcr:title:` Meu componente de imagem.
   * `jcr:description`: Este é o Meu Componente de Imagem.

1. Adicione uma propriedade ao `image` nó com os seguintes valores de propriedade:

   * **[!UICONTROL Nome]**: componentGroup
   * **[!UICONTROL Tipo]**: String
   * **[!UICONTROL Valor]**: MeuSite

1. Abaixo do `image` , renomeie o `design_dialog` nó para `dialog`.

1. Renomear `logo.jsp` para `image.jsp.`

1. Abra img.GET.java e altere o pacote para `apps.mywebsite.components.image`.

![chlimage_1-128](assets/chlimage_1-128.png)

#### Criação do script de imagem {#creating-the-image-script}

Esta seção descreve como criar o script de imagem.

1. Abrir `/apps/mywebsite/components/image/` `image.jsp`
1. Substitua o código existente pelo seguinte código e salve as alterações:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.cq.commons.Doctype,
                       com.day.cq.wcm.foundation.Image,
                       com.day.cq.wcm.api.components.DropTarget,
                       com.day.cq.wcm.api.components.EditConfig,
                       com.day.cq.wcm.commons.WCMUtils" %><%
    /* global.jsp provides access to the current resource through the resource object */
           Image img = new Image(resource);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out); %>
   ```

1. Salve as alterações.

#### Criação do nó Image cq:editConfig {#creating-the-image-cq-editconfig-node}

O `cq:editConfig` O tipo de nó permite configurar determinados comportamentos dos componentes ao editar suas propriedades.

Nesta seção, você usa um nó cq:editConfig para permitir que você arraste ativos do Localizador de conteúdo para seu componente de imagem.

1. No CRXDE Lite, no nó /apps/mywebsite/components/image, crie um novo nó da seguinte maneira:

   * **[!UICONTROL Nome]**: cq:editConfig.
   * **[!UICONTROL Tipo]**: cq:EditConfig.

1. No nó cq:editConfig, crie um novo nó da seguinte maneira:

   * **[!UICONTROL Nome]**: cq:dropTargets.
   * **[!UICONTROL Tipo]**: cq:DropTargetConfig.

1. No nó cq:dropTargets, crie um novo nó da seguinte maneira:

   * **[!UICONTROL Nome]**: imagem.
   * **[!UICONTROL Tipo]**: nt:unstructured.

1. No CRXDE, defina as propriedades da seguinte maneira:

| Nome | Tipo | Valor |
|---|---|---|
| Aceitar | String | image/(gif | jpeg | png) |
| grupos | String | mídia |
| propertyName | String | ./imageReference |

![chlimage_1-129](assets/chlimage_1-129.png)

#### Adição do ícone {#adding-the-icon}

Nesta seção, você adiciona o ícone a ser exibido ao lado do componente de imagem quando ele estiver listado no Sidekick:

1. No CRXDE Lite, clique com o botão direito do mouse no arquivo `/libs/foundation/components/image/icon.png` e selecione **[!UICONTROL Copiar]**.
1. Clique com o botão direito do mouse no nó `/apps/mywebsite/components/image` e clique em **[!UICONTROL Colar]**, depois clique em **[!UICONTROL Salvar tudo]**.

#### Uso do componente de imagem {#using-the-image-component}

Nesta seção, você visualizará o **[!UICONTROL Produtos]** e adicione seu componente de imagem ao sistema de parágrafo.

1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página.
1. No Sidekick, clique no botão **[!UICONTROL Modo de design]** ícone .
1. Clique no botão **[!UICONTROL Editar]** para editar a caixa de diálogo de design do par.
1. Na caixa de diálogo, uma lista de **[!UICONTROL Componentes permitidos]** é mostrada; navegue até **[!UICONTROL MeuSite]**, selecione o **[!UICONTROL Meu componente de imagem]** e clique em **[!UICONTROL OK]**.
1. Retornar para **[!UICONTROL Modo de Edição]**.
1. Clique duas vezes no quadro parsys (em **[!UICONTROL Arraste componentes ou ativos aqui]**). O **[!UICONTROL Inserir novo componente]** e **[!UICONTROL Sidekick]** os seletores têm a seguinte aparência:

   ![chlimage_1-8](assets/chlimage_1-8.jpeg)

### Inclusão do componente Barra de ferramentas {#including-the-toolbar-component}

Nesta seção, você inclui o componente da barra de ferramentas, que é um dos componentes fundamentais.

Há várias opções, no modo de edição e também no modo de design.

1. No CRXDE Lite, navegue até `/apps/mywebsite/components/contentpage`, abra o `body.jsp` e localize o seguinte código:

   ```java
   <div class="toolbar">toolbar</div>
   ```

1. Substitua esse código pelo seguinte código e salve as alterações.

   ```java
   <cq:include path="toolbar" resourceType="foundation/components/toolbar"/>
   ```

1. Na árvore de pastas da página Sites AEM, selecione `Websites/My Website/English`, depois clique em **[!UICONTROL Novo > Nova página]**. Especifique os seguintes valores de propriedade e clique em Criar:

   * **[!UICONTROL Título]**: Barra de ferramentas
   * Selecionar **[!UICONTROL Modelo de página de conteúdo do meu site]**

1. Na lista de páginas, clique com o botão direito do mouse no **[!UICONTROL Barra de ferramentas]** e clique em **[!UICONTROL Propriedades]**. Selecionar **[!UICONTROL Ocultar na navegação]** e clique em **[!UICONTROL OK]**.

   O **[!UICONTROL Ocultar na navegação]** impede que a página seja exibida em componentes de navegação, como topnav e listchildren.

1. Em **[!UICONTROL Barra de ferramentas]**, crie as seguintes páginas:

   * Contatos
   * Feedback
   * Logon
   * Pesquisar

1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. Tem a seguinte aparência:

   ![chlimage_1-130](assets/chlimage_1-130.png)

### Criação do componente de pesquisa {#creating-the-search-component}

Nesta seção, você cria o componente para procurar conteúdo no site. Esse componente de pesquisa pode ser colocado no sistema de parágrafo de qualquer página (por exemplo, em uma página de resultados de pesquisa especializada).

Sua caixa de entrada de pesquisa terá a seguinte aparência **[!UICONTROL Inglês]** página:

![chlimage_1-131](assets/chlimage_1-131.png)

#### Criação do componente de pesquisa {#creating-the-search-component-1}

1. No CRXDE Lite, clique com o botão direito do mouse `/apps/mywebsite/components`, selecione **[!UICONTROL Criar]**, em seguida **[!UICONTROL Criar componente]**.
1. Use a caixa de diálogo para configurar o componente:

   1. Um primeiro painel, especifique os seguintes valores de propriedade:

      * **[!UICONTROL Rótulo]**: pesquisa
      * **[!UICONTROL Título]**: Meu componente de pesquisa
      * **[!UICONTROL Descrição]**: Este é o meu componente de pesquisa
      * **[!UICONTROL Grupo]**: MeuSite
   1. Clique em **[!UICONTROL Próximo]**, depois clique em **[!UICONTROL Próximo]** novamente.
   1. No **[!UICONTROL Pais permitidos]** clique no painel **[!UICONTROL +]** botão e tipo `*/parsys`.
   1. Clique em **[!UICONTROL Próximo]** e, em seguida, clique em **[!UICONTROL OK]**.


1. Clique em **[!UICONTROL Salvar tudo]**.
1. Copie os nós a seguir e cole-os no `apps/mywebsite/components/search` nó:

   * `/libs/foundation/components/search/dialog`
   * `` `/libs/foundation/components/search/i18n`
   * `/libs/foundation/components/search/icon.png`

1. Clique em **[!UICONTROL Salvar tudo]**.

#### Criação do script de pesquisa {#creating-the-search-script}

Esta seção descreve como criar o script de pesquisa:

1. Abra o `/apps/mywebsite/components/search/search.jsp` arquivo.
1. Copie o código a seguir para `search.jsp`:

   ```java
   <%@ page import="com.day.cq.wcm.foundation.Search,com.day.cq.tagging.TagManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   %><cq:setContentBundle/><%
       Search search = new Search(slingRequest);
   
       String searchIn = (String) properties.get("searchIn");
       String requestSearchPath = request.getParameter("path");
       if (searchIn != null) {
           /* only allow the "path" request parameter to be used if it
            is within the searchIn path configured */
           if (requestSearchPath != null && requestSearchPath.startsWith(searchIn)) {
               search.setSearchIn(requestSearchPath);
           } else {
               search.setSearchIn(searchIn);
           }
       } else if (requestSearchPath != null) {
           search.setSearchIn(requestSearchPath);
       }
   
       pageContext.setAttribute("search", search);
       TagManager tm = resourceResolver.adaptTo(TagManager.class);
   %><c:set var="trends" value="${search.trends}"/><%
   %><center>
     <form action="${currentPage.path}.html">
       <input size="41" maxlength="2048" name="q" value="${fn:escapeXml(search.query)}"/>
       <input value="<fmt:message key="searchButtonText"/>" type="submit" />
     </form>
   </center>
   <br/>
   <c:set var="result" value="${search.result}"/>
   <c:choose>
     <c:when test="${empty result && empty search.query}">
     </c:when>
     <c:when test="${empty result.hits}">
       <c:if test="${result.spellcheck != null}">
         <p><fmt:message key="spellcheckText"/> <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${result.spellcheck}"/></c:url>"><b><c:out value="${result.spellcheck}"/></b></a></p>
       </c:if>
       <fmt:message key="noResultsText">
         <fmt:param value="${fn:escapeXml(search.query)}"/>
       </fmt:message>
     </c:when>
     <c:otherwise>
       <p class="searchmeta">Results ${result.startIndex + 1} - ${result.startIndex + fn:length(result.hits)} of ${result.totalMatches} for <b>${fn:escapeXml(search.query)}</b>. (${result.executionTime} seconds)</p>
      <br/>
   
     <div class="searchresults"> 
       <div class="results">
         <c:forEach var="hit" items="${result.hits}" varStatus="status">
           <div class="hit">
           <a href="${hit.URL}">${hit.title}</a>
           <div class="excerpt">${hit.excerpt}</div>
          <div class="hiturl"> ${hit.URL}<c:if test="${!empty hit.properties['cq:lastModified']}"> - <c:catch><fmt:formatDate value="${hit.properties['cq:lastModified'].time}" dateStyle="medium"/></c:catch></c:if> - <a href="${hit.similarURL}"><fmt:message key="similarPagesText"/></a>
           </div></div>
         </c:forEach>
       </div>
         <br/>
   
        <div class="searchRight">
             <c:if test="${fn:length(trends.queries) > 0}">
                 <p><fmt:message key="searchTrendsText"/></p>
                 <div class="searchTrends">
                     <c:forEach var="query" items="${trends.queries}">
                         <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${query.query}"/></c:url>"><span style="font-size:${query.size}px"><c:out value="${query.query}"/></span></a>
                     </c:forEach>
                 </div>
             </c:if> 
             <c:if test="${result.facets.languages.containsHit}">
                 <p>Languages</p>
                 <c:forEach var="bucket" items="${result.facets.languages.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value='<%= new java.util.Locale((String) pageContext.getAttribute("bucketValue")).getDisplayLanguage(request.getLocale()) %>'/>
                     <c:choose>
                         <c:when test="${param.language != null}">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.tags.containsHit}">
                 <p>Tags</p>
                 <c:forEach var="bucket" items="${result.facets.tags.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="tag" value="<%= tm.resolve((String) pageContext.getAttribute("bucketValue")) %>"/>
                     <c:if test="${tag != null}">
                         <c:set var="label" value="${tag.title}"/>
                         <c:choose>
                             <c:when test="<%= request.getParameter("tag") != null && java.util.Arrays.asList(request.getParameterValues("tag")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="tag" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                             <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="tag" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                         </c:choose><br/>
                     </c:if>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.mimeTypes.containsHit}">
                 <jsp:useBean id="fileTypes" class="com.day.cq.wcm.foundation.FileTypes"/>
                 <p>File types</p>
                 <c:forEach var="bucket" items="${result.facets.mimeTypes.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value="${fileTypes[bucket.value]}"/>
                     <c:choose>
                         <c:when test="<%= request.getParameter("mimeType") != null && java.util.Arrays.asList(request.getParameterValues("mimeType")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.lastModified.containsHit}">
                 <p>Last Modified</p>
                 <c:forEach var="bucket" items="${result.facets.lastModified.buckets}">
                     <c:choose>
                         <c:when test="${param.from == bucket.from && param.to == bucket.to}">${bucket.value} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/><c:if test="${bucket.from != null}"><cq:addParam name="from" value="${bucket.from}"/></c:if><c:if test="${bucket.to != null}"><cq:addParam name="to" value="${bucket.to}"/></c:if></cq:requestURL>">${bucket.value} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
   
         <c:if test="${fn:length(search.relatedQueries) > 0}">
   
          <br/><br/><div class="related">
           <fmt:message key="relatedSearchesText"/>
           <c:forEach var="rq" items="${search.relatedQueries}">
               <a href="${currentPage.path}.html?q=${rq}"><c:out value="${rq}"/></a>
           </c:forEach></div>
         </c:if>
         </div> 
   
         <c:if test="${fn:length(result.resultPages) > 1}">
           <div class="pagination"> 
               <fmt:message key="resultPagesText"/>
           <c:if test="${result.previousPage != null}">
             <a href="${result.previousPage.URL}"><fmt:message key="previousText"/></a>
           </c:if>
           <c:forEach var="page" items="${result.resultPages}">
             <c:choose>
               <c:when test="${page.currentPage}">${page.index + 1}</c:when>
               <c:otherwise>
                 <a href="${page.URL}">${page.index + 1}</a>
               </c:otherwise>
             </c:choose>
           </c:forEach>
           <c:if test="${result.nextPage != null}">
             <a href="${result.nextPage.URL}"><fmt:message key="nextText"/></a>
           </c:if>
           </div>
         </c:if>
         </div>
   
     </c:otherwise>
   </c:choose>
   ```

1. Salve as alterações.

#### Inclusão de uma caixa de pesquisa no componente Página de conteúdo {#including-a-search-box-in-the-contentpage-component}

Para incluir uma caixa de entrada de pesquisa na seção esquerda da página de conteúdo, proceda da seguinte maneira:

1. No CRXDE Lite, abra o arquivo `left.jsp` under `/apps/mywebsite/components/contentpage` e localize o seguinte código (linha 2):

   ```xml
   %><div class="left">
   ```

1. Insira o seguinte código *before* essa linha:

   ```java
   %><%@ page import="com.day.text.Text"%><%
   %><% String docroot = currentDesign.getPath(); 
   String home = Text.getAbsoluteParent(currentPage.getPath(), 2);%><%
   ```

1. Localize a seguinte linha de código:

   ```xml
   <div>search</div>
   ```

1. Substitua esse código pelo seguinte código e salve as alterações.

   ```java
   <div class="form_1">
        <form class="geo" action="<%= home %>/toolbar/search.html" id="form" >
             <p>
                  <input class="geo" type="text" name="q"><br> 
                  <a href="<%= home %>/toolbar/search.html" class="link_1">advanced search</a> 
             </p>
        </form>
   </div>
   ```

1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. O componente de pesquisa tem a seguinte aparência:

   ![chlimage_1-132](assets/chlimage_1-132.png)

#### Inclusão do componente de pesquisa na página de pesquisa {#including-the-search-component-in-the-search-page}

Nesta seção, você adiciona o componente de pesquisa ao sistema de parágrafo.

1. No seu navegador, abra o **Pesquisar** página.
1. No Sidekick, clique no botão **[!UICONTROL Design]** ícone de modo .
1. No bloco Design de par (abaixo do título Pesquisa), clique em **[!UICONTROL Editar]**.
1. Na caixa de diálogo, role para baixo até a **[!UICONTROL Meus sites]** , selecione **[!UICONTROL Meu componente de pesquisa]** e clique em **[!UICONTROL OK]**.
1. No Sidekick, clique no triângulo para retornar ao **[!UICONTROL Editar]** modo.
1. Arraste o **[!UICONTROL Minha Pesquisa]** componente do Sidekick para o quadro parsys. Tem a seguinte aparência:

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Navegue até seu **[!UICONTROL Produtos]** página. Procure clientes na caixa de entrada e pressione **[!UICONTROL Enter]**. Você é redirecionado para a função **[!UICONTROL Pesquisar]** página. Mudar para **[!UICONTROL Visualizar]** modo: a saída está em um formato semelhante ao seguinte:

   ![chlimage_1-134](assets/chlimage_1-134.png)

### Inclusão do componente Iparsys {#including-the-iparsys-component}

Nesta seção, você inclui o componente Sistema de parágrafo de herança (iparsys), que é um dos componentes fundamentais. Esse componente permite que você crie uma estrutura de parágrafos em uma página principal e faça com que páginas filhas herdem os parágrafos.

Para esse componente, você pode definir vários parâmetros no modo de edição e no modo de design.

1. No CRXDE Lite, navegue até `/apps/mywebsite/components/contentpage`, abra o arquivo `right.jsp` e substituir:

   ```java
   <div>iparsys</div>
   ```

   com:

   ```java
   <cq:include path="rightpar" resourceType="foundation/components/iparsys" />
   ```

1. Salve as alterações.
1. No seu navegador, recarregue o **[!UICONTROL Produtos]** página. A página inteira tem a seguinte aparência:

   ![chlimage_1-9](assets/chlimage_1-9.jpeg)
