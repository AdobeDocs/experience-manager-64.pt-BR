---
title: Criar uma página de amostra
seo-title: Criar uma página de amostra
description: Criar um site de comunidade de amostra
seo-description: Criar um site de comunidade de amostra
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 2%

---


# Criar uma página de amostra {#create-a-sample-page}

A partir AEM Comunidades 6.1, a maneira mais fácil de criar uma página de amostra é criar um site da comunidade simples, que consiste apenas em uma função de Página.

Isso incluirá um componente parsys para que você possa [ativar componentes para criação](basics.md#accessing-communities-components).

Outra opção para explorar componentes de amostra é usar os recursos apresentados no [Guia de componentes da comunidade](components-guide.md).

## Criar um site da comunidade {#create-a-community-site}

Isso é muito semelhante à criação de um novo site descrito em [Introdução ao AEM Communities](getting-started.md).

A principal diferença é que este tutorial criará um novo modelo de site da comunidade que contém apenas a [função de página](functions.md#page-function) para criar um site da comunidade simples sem outros recursos (que não sejam os recursos pré-conectados básicos para todos os sites da comunidade).

### Criar Novo Modelo de Site {#create-new-site-template}

Para começar, crie um simples [modelo de site da comunidade](sites.md).

Na navegação global em uma instância do autor, selecione **[!UICONTROL Ferramentas > Comunidades > Modelos do site]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* Selecionar `Create button`
* INFORMAÇÕES BÁSICAS

   * `Name`: Modelo de página única
   * `Description`: Um modelo que consiste em uma única função de Página.
   * select `Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* ESTRUTURA

   * Arraste uma função `Page` para o Construtor de modelos
   * Para obter detalhes sobre a função de configuração, digite

      * `Title`: Página única
      * `URL`: page

![chlimage_1-84](assets/chlimage_1-84.png)

* Selecione **`Save`** para a configuração
* Selecione **`Save`** para o modelo de site

### Criar novo site da comunidade {#create-new-community-site}

Agora, crie um novo site da comunidade com base no modelo de site simples.

Depois de criar o modelo de site, na navegação global selecione **[!UICONTROL Comunidades > Sites]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* Selecionar **`Create`** ícone

* Etapa `1 - Site Template`

   * `Title`: Site simples da comunidade
   * `Description`: Um site da comunidade que consiste em uma única página para experimentação.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: amostra

      * url = http://localhost:4502/content/sites/sample
   * `Template`: choice  `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* Selecionar `Next`
* Etapa `2 - Design`

   * Selecionar qualquer design

* Selecionar `Next`
* Selecionar `Next`

   (Aceitar todas as configurações padrão)

* Selecionar `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## Publicar o Site {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

No [console de sites da comunidade](sites-console.md), selecione o ícone de publicação para publicar o site, por padrão, em http://localhost:4503.

## Abra o Site no Autor no Modo de edição {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

Selecione o ícone de abrir site para visualização do site no modo de edição.

O URL será [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

No home page simples é possível ver o que está pré-conectado através das funções e modelos da comunidade, e brincar com a adição e configuração de componentes da comunidade.

## Site de visualização na publicação {#view-site-on-publish}

Depois de publicar a página, abra a página na [instância de publicação](http://localhost:4503/content/sites/sample/en.html) para experimentar os recursos como um visitante de site anônimo, membro conectado ou administrador. O link Administração visível no ambiente do autor não aparecerá no ambiente de publicação, a menos que um administrador faça logon.
