---
title: Preparação de conteúdo para tradução
seo-title: Preparação de conteúdo para tradução
description: Saiba como preparar conteúdo para tradução.
seo-description: Saiba como preparar conteúdo para tradução.
uuid: 369630a8-2ed7-48db-973e-bd8213231d49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 8bd67d71-bcb7-4ca0-9751-3ff3ee054011
feature: Language Copy
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---


# Preparando conteúdo para tradução{#preparing-content-for-translation}

Sites multilíngues geralmente fornecem alguma quantidade de conteúdo em vários idiomas. O site é criado em um idioma e depois traduzido para outros idiomas. Geralmente, sites multilíngues consistem em ramificações de páginas, onde cada ramificação contém as páginas do site em um idioma diferente.

O exemplo de Site de demonstração do Geometrixx inclui várias ramificações de idioma e usa a seguinte estrutura:

```xml
/content
    |- geometrixx
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Cada ramificação de idioma de um site é chamada de cópia de idioma. A página raiz de uma cópia de idioma, conhecida como raiz de idioma, identifica o idioma do conteúdo na cópia de idioma. Por exemplo, `/content/geometrixx/fr` é a raiz do idioma para a cópia em francês. As cópias de idioma devem usar uma [raiz de idioma corretamente configurada](/help/sites-administering/tc-prep.md#creating-a-language-root) para que o idioma correto seja direcionado quando as traduções de um site de origem forem executadas.

A cópia de idioma para a qual você criou originalmente o conteúdo do site é o idioma principal. O idioma principal é a fonte traduzida para outros idiomas.

Use as seguintes etapas para preparar seu site para tradução:

1. Crie a raiz do idioma do principal. Por exemplo, a raiz do idioma do site de demonstração do Geometrixx em inglês é /content/geometrixx/en. Certifique-se de que a raiz do idioma esteja configurada corretamente de acordo com as informações em [Criação de uma Raiz de Idioma](/help/sites-administering/tc-prep.md#creating-a-language-root).
1. Crie o conteúdo do seu idioma principal.
1. Crie a raiz de idioma de cada cópia de idioma para o site. Por exemplo, a cópia em francês do site de amostra do Geometrixx é /content/geometrixx/fr.

Depois de preparar o conteúdo para tradução, você pode criar automaticamente as páginas ausentes em suas cópias de idioma e projetos de tradução associados. (Consulte [Criação de um projeto de tradução](/help/sites-administering/tc-manage.md).) Para obter uma visão geral do processo de tradução de conteúdo no AEM, consulte [Tradução de conteúdo para sites multilíngues](/help/sites-administering/translation.md).

## Criação de uma Raiz de Idioma {#creating-a-language-root}

Crie uma raiz de idioma como a página raiz de uma cópia de idioma que identifica o idioma do conteúdo. Depois de criar a raiz do idioma, você pode criar projetos de tradução que incluem a cópia de idioma.

Para criar a raiz de idioma, crie uma página e use um código de idioma ISO como o valor da propriedade Name. O código de idioma deve estar em um dos seguintes formatos:

* `<language-code>`O código de idioma suportado é um código de duas letras, conforme definido por ISO-639-1, por exemplo  `en`.

* `<language-code>_<country-code>` ou  `<language-code>-<country-code>`O código do país suportado é um código de duas letras em letras minúsculas ou maiúsculas, conforme definido pela ISO 3166, por exemplo,  `en_US`,  `en_us`,  `en_GB`,  `en-gb`.

Você pode usar qualquer um dos formatos, de acordo com a estrutura escolhida para o site global.  Por exemplo, a página raiz da cópia em francês do site do Geometrixx tem `fr` como a propriedade Name . Observe que a propriedade Name é usada como o nome do nó da página no repositório e, portanto, determina o caminho da página. (http://localhost:4502/content/geometrixx/fr.html)

O procedimento a seguir usa a interface otimizada para toque para criar uma cópia de idioma de um site. Para obter instruções que usam a interface clássica, consulte [Criar uma raiz de idioma usando a interface clássica](/help/sites-administering/tc-lroot-classic.md).

1. Navegue até Sites.
1. Clique ou toque no site para o qual deseja criar uma cópia de idioma.

   Por exemplo, para criar uma cópia de idioma do site Geometrixx Outdoors, você clicaria ou tocaria em Geometrixx Outdoors Site.

1. Clique ou toque em Criar e, em seguida, clique ou toque em Criar página.

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Selecione o modelo de página e clique ou toque em Próximo.
1. No campo Nome, digite o código do país no formato `<language-code>` ou `<language-code>_<country-code>`, por exemplo `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Digite um título para a página.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Clique ou toque em Criar. Na caixa de diálogo de confirmação, clique ou toque em **Concluído** para retornar ao console Sites ou em **Abrir** para abrir a cópia de idioma.

## Ver o status das raízes de idioma {#seeing-the-status-of-language-roots}

A interface otimizada para toque fornece um painel Referências que mostra uma lista de raízes de idioma que foram criadas.

![chlimage_1-23](assets/chlimage_1-23.png)

O procedimento a seguir usa a interface otimizada para toque para abrir o painel Referências para uma página.

1. No console Sites , selecione uma página do site e clique ou toque em **Referências**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. No painel de referências, clique ou toque em **Cópias de idioma**. O painel Cópias de idioma mostra as cópias de idioma do site.

