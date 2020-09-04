---
title: Adicionar Clientlibs
seo-title: Adicionar Clientlibs
description: Adicionar uma ClientLibraryFolder
seo-description: Adicionar uma ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 805e4411930749ff4b6b05ea4a8b87b4f96d72fd
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---


# Adicionar Clientlibs {#add-clientlibs}

## Adicionar uma ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Crie uma ClientLibraryFolder com o nome `clientlibs`que conterá o JS e o CSS usados para renderizar as páginas do site.

O valor de `categories`propriedade fornecido para essa biblioteca de cliente é o identificador usado para incluir diretamente essa clientlib de uma página de conteúdo ou para incorporá-la a outras clientlibs.

1. Usando o **[!UICONTROL CRXDE Lite]**, expanda `/etc/designs`

1. Clique com o botão direito do mouse em `an-scf-sandbox` e selecione `Create Node`

   * Nome: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Clique em **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Na guia **[!UICONTROL Propriedades]** do novo `clientlibs` nó, digite a **`categories`** propriedade:

* Nome: **[!UICONTROL categorias]**
* Tipo: **[!UICONTROL String]**
* Valor: **[!UICONTROL apps.an-scf-sandbox]**
* Clique em **[!UICONTROL Adicionar]**
* Clique em **[!UICONTROL Salvar tudo]**

Observação: como visualizar o valor do categoria com &quot;aplicativos&quot;. é uma convenção para identificar o &quot;aplicativo proprietário&quot; como estando na pasta /apps, não /libs.  IMPORTANTE: Adicione espaço reservado `js.txt` e `css.txt` arquivos. (Não é oficialmente uma cq:ClientLibraryFolder sem eles.)


1. Clique com o botão direito em **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Selecione **[!UICONTROL Criar Arquivo...]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. Selecione **[!UICONTROL Criar Arquivo...]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. Clique em **[!UICONTROL Salvar tudo]**

![chlimage_1-221](assets/chlimage_1-221.png)

A primeira linha do css.txt e do js.txt identifica o local base a partir do qual as seguintes listas de arquivos são encontradas.

Tente definir o conteúdo de css.txt como:

```
#base=.
 style.css
```

Em seguida, crie um arquivo em clientlibs chamado style.css e defina o conteúdo como:

`body {`

`background-color: #b0c4de;`

`}`

## Incorporar Clientlibs SCF {#embed-scf-clientlibs}

Na guia **[!UICONTROL Propriedades]** do `clientlibs` nó, digite a propriedade String com vários valores **[!UICONTROL incorporada]**. Isso incorporará as bibliotecas necessárias do lado do [cliente (clientlibs) para componentes](client-customize.md#clientlibs-for-scf)SCF. Neste tutorial, adicionaremos muitas das clientlibs necessárias para os componentes Comunidades.

**Observe** que essa pode ou não ser a abordagem desejada para usar em um site de produção, pois há considerações de conveniência em relação ao tamanho/velocidade dos clientlibs baixados para cada página.

Se apenas estiver usando um recurso em uma página, você poderá incluir a clientlib completa desse recurso diretamente na página, por exemplo, &lt;% ui:includeClientLib categoria=cq.social.hbs.forum&quot; %>

Nesse caso, estamos incluindo todos, e assim preferimos os clientlibs SCF mais básicos que são os clientlibs do autor:

* Nome: **`embed`**
* Tipo: **`String`**

* Clique em **`Multi`**
* Valor: **`cq.social.scf`**

   *O &lt;enter> irá abrir uma caixa de diálogo*

   *Clique **[+]**após cada entrada para adicionar as seguintes categorias clientlib:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Clique em **[!UICONTROL OK]**

* Clique em **[!UICONTROL Salvar tudo]**

![chlimage_1-222](assets/chlimage_1-222.png)

É assim que agora `/etc/designs/an-scf-sandbox/clientlibs` deve aparecer no repositório:

![chlimage_1-223](assets/chlimage_1-223.png)

## Incluir Clientlibs no modelo PlayPage {#include-clientlibs-in-playpage-template}

Sem incluir a categoria `apps.an-scf-sandbox` ClientLibraryFolder na página, os componentes do SCF não estarão funcionais nem com estilo, pois os Javascript e o(s) estilo(s) necessários não estarão disponíveis.

Por exemplo, sem incluir clientlibs, o componente de comentários SCF aparece sem estilo:

![chlimage_1-224](assets/chlimage_1-224.png)

Depois que apps.an-scf-sandbox clientlibs é incluído, o componente de comentários SCF aparece no estilo:

![chlimage_1-225](assets/chlimage_1-225.png)

A instrução include pertence à seção `<head>` do `<html>` script. O padrão **`foundation head.jsp`** inclui um script que pode ser sobreposto: **`headlibs.jsp`**.

**Copie headlibs.jsp e inclua clientlibs:**

1. Usando o **[!UICONTROL CRXDE Lite]**, selecione **`/libs/foundation/components/page/headlibs.jsp`**
1. Clique com o botão direito do mouse e selecione **[!UICONTROL Copiar]** (ou selecione Copiar na barra de ferramentas)
1. Selecionar **`/apps/an-scf-sandbox/components/playpage`**
1. Clique com o botão direito do mouse e selecione **[!UICONTROL Colar]** (ou selecione Colar na barra de ferramentas)
1. Clique no duplo **`headlibs.jsp`** para abri-lo
1. Anexar a seguinte linha ao final do arquivo

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Clique em **[!UICONTROL Salvar tudo]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Carregue seu site no navegador e veja se o plano de fundo não é uma sombra de azul.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Salvando Seu Trabalho Até Agora {#saving-your-work-so-far}

Nesse ponto, existe uma caixa de proteção minimalista e pode valer a pena salvar como um pacote para que, durante a reprodução, se o seu repositório ficar corrompido e você desejar start, você possa desligar, renomear ou excluir a pasta crx-quickstart/, ligar o servidor, carregar e instalar esse pacote salvo e não precisar repetir essas etapas mais básicas.

Este pacote existe no tutorial [Criar uma página](create-sample-page.md) de amostra para aqueles que não podem esperar para pular e reproduzir start!...

Para criar um pacote:


* Na **[!UICONTROL CRXDE Lite]**, clique no ícone [Pacote](http://localhost:4502/crx/packmgr/)
* Clique em **[!UICONTROL Criar pacote]**

   * Nome do pacote: `an-scf-sandbox-minimal-pkg`
   * Versão: `0.1`
   * Grupo: &lt;deixar como padrão>
   * Clique em **[!UICONTROL OK]**

* Clique em **[!UICONTROL Editar]**

   * Guia Selecionar **[!UICONTROL Filtros]**

      * Clique em **[!UICONTROL Adicionar filtro]**
      * Caminho raiz: &lt;navegar até `/apps/an-scf-sandbox`>
      * Clique em **[!UICONTROL Concluído]**
      * Clique em **[!UICONTROL Adicionar filtro]**
      * Caminho raiz: &lt;navegar até `/etc/designs/an-scf-sandbox`>
      * Clique em **[!UICONTROL Concluído]**
      * Clique em **[!UICONTROL Adicionar filtro]**
      * Caminho raiz: &lt;navegar até `/content/an-scf-sandbox`>
      * Clique em **[!UICONTROL Concluído]**
   * Clique em **[!UICONTROL Salvar]**


* Clique em **[!UICONTROL Criar]**

Agora você pode selecionar **[!UICONTROL Download]** para salvá-lo em disco e **[!UICONTROL Carregar pacote]** em outro lugar, bem como selecionar **[!UICONTROL Mais > Replicar]** para encaminhar a caixa de proteção para uma instância de publicação de host local a fim de expandir o realm da sua caixa de proteção.
