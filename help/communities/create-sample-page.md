---
title: Criar uma página de exemplo
seo-title: Create a Sample Page
description: Criar um site de comunidade de exemplo
seo-description: Create a Sample community site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
exl-id: 00ac29fb-cc8f-4dd9-a261-839a4bf664c2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 3%

---

# Criar uma página de exemplo {#create-a-sample-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Desde AEM Comunidades 6.1, a maneira mais fácil de criar uma página de exemplo é criar um site da comunidade simples, que consiste apenas em uma função Página .

Isso incluirá um componente parsys para que você possa [ativar componentes para criação](basics.md#accessing-communities-components).

Outra opção para explorar componentes de amostra é usar os recursos apresentados na [Guia de componentes da comunidade](components-guide.md).

## Criar um site de comunidade {#create-a-community-site}

Isso é muito semelhante à criação de um novo site descrito em [Introdução ao AEM Communities](getting-started.md).

A principal diferença é que este tutorial criará um novo modelo de site da comunidade que contém apenas o [Função da página](functions.md#page-function) para criar um site da comunidade simples sem outros recursos (além dos recursos pré-conectados básicos em todos os sites da comunidade).

### Criar novo modelo de site {#create-new-site-template}

Para começar, crie um [modelo de site da comunidade](sites.md).

Na navegação global em uma instância de autor, selecione **[!UICONTROL Ferramentas > Comunidades > Modelos do site]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* Selecionar `Create button`
* INFORMAÇÕES BÁSICAS

   * `Name`: Modelo de página única
   * `Description`: Um modelo que consiste em uma única função de Página .
   * select `Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* ESTRUTURA

   * Arraste um `Page` para o Construtor de modelos
   * Para Detalhes da Função de Configuração, insira

      * `Title`: Página única
      * `URL`: página

![chlimage_1-84](assets/chlimage_1-84.png)

* Selecionar **`Save`** para a configuração
* Selecionar **`Save`** para o modelo do site

### Criar novo site da comunidade {#create-new-community-site}

Agora crie um novo site da comunidade com base no modelo de site simples.

Depois de criar o modelo de site, na navegação global, selecione **[!UICONTROL Comunidades > Sites]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* Selecionar **`Create`** ícone

* Etapa `1 - Site Template`

   * `Title`: Site da comunidade simples
   * `Description`: Um site da comunidade que consiste em uma única página para experimentação.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: amostra

      * url = http://localhost:4502/content/sites/sample
   * `Template`: Choose `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* Selecionar `Next`
* Etapa `2 - Design`

   * Selecione qualquer design

* Selecionar `Next`
* Selecionar `Next`

   (Aceitar todas as configurações padrão)

* Selecionar `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## Publicar o site {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

No [console sites da comunidade](sites-console.md), selecione o ícone de publicação para publicar o site, por padrão, em http://localhost:4503.

## Abra o site no autor no modo de edição {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

Selecione o ícone de abrir site para exibir o site no modo de edição.

O URL será [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

Na página inicial simples, é possível ver o que é pré-conectado por meio das funções e modelos da comunidade e brincar com a adição e configuração de componentes da comunidade.

## Exibir site na publicação {#view-site-on-publish}

Depois de publicar a página, abra a página no [instância de publicação](http://localhost:4503/content/sites/sample/en.html) para experimentar os recursos como um visitante anônimo do site, membro conectado ou administrador. O link Administração visível no ambiente do autor não aparecerá no ambiente de publicação, a menos que um administrador faça logon.
