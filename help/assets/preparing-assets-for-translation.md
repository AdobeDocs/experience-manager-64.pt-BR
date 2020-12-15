---
title: Preparação de ativos para tradução
description: Crie pastas raiz de idioma para se preparar para a tradução de ativos multilíngues.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 77c62a8f2ca50f8aaff556a6848fabaee71017ce
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# Preparando ativos para tradução {#preparing-assets-for-translation}

Ativos multilíngues são ativos com binários, metadados e tags em vários idiomas. Geralmente, binários, metadados e tags para ativos existem em um idioma, que são traduzidos para outros idiomas para uso em projetos multilíngues.

Nos ativos Adobe Experience Manager (AEM), os ativos multilíngues são incluídos nas pastas, onde cada pasta contém os ativos em um idioma diferente.

Cada pasta de idioma é chamada de cópia de idioma. A pasta raiz de uma cópia de idioma, conhecida como raiz de idioma, identifica o idioma do conteúdo na cópia de idioma. Por exemplo, */content/dam/it* é a raiz do idioma italiano para a cópia do idioma italiano. As cópias de idioma devem usar uma [raiz de idioma configurada corretamente](preparing-assets-for-translation.md#creating-a-language-root) para que o idioma correto seja direcionado quando as traduções dos ativos de origem forem executadas.

A cópia de idioma para a qual você adicionou ativos originalmente é o idioma principal. O idioma principal é a fonte traduzida para outros idiomas.

A hierarquia da pasta de amostra inclui várias raízes de idioma:

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Execute as seguintes etapas para preparar seus ativos para tradução:

1. Crie a raiz do idioma do idioma principal. Por exemplo, a raiz do idioma da cópia em inglês na hierarquia da pasta de amostra é `/content/dam/en`. Verifique se a raiz do idioma está configurada corretamente de acordo com as informações em [Criando uma raiz do idioma](preparing-assets-for-translation.md#creating-a-language-root).

1. Adicione ativos ao seu idioma principal.
1. Crie a raiz do idioma de cada idioma do público alvo para o qual você precisa de uma cópia do idioma.

## Criando uma raiz de idioma {#creating-a-language-root}

Para criar a raiz do idioma, crie uma pasta e use um código de idioma ISO como o valor da propriedade Name. Depois de criar a raiz do idioma, é possível criar uma cópia do idioma em qualquer nível na raiz do idioma.

Por exemplo, a página raiz da cópia de idioma italiano da hierarquia de amostra tem `it` como a propriedade Name. A propriedade Name é usada como o nome do nó do ativo no repositório e, portanto, determina o caminho dos ativos. (`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. No console Assets, clique/toque em **[!UICONTROL Criar]** e escolha **[!UICONTROL Pasta]** no menu.

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. No campo Nome, digite o código do país no formato `<language-code>`.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Clique ou toque em **[!UICONTROL Criar]**. A raiz do idioma é criada no console Ativos.

## Exibindo Raízes de Idioma {#viewing-language-roots}

A interface otimizada para toque fornece um painel Referências que mostra uma lista de raízes de idioma que foram criadas no AEM Assets.

1. No console Ativos, selecione o idioma principal para o qual deseja criar cópias de idioma.
1. Clique ou toque no ícone GlobalNav e escolha **[!UICONTROL Referências]** para abrir o painel Referência.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. No painel Referências, clique ou toque em **[!UICONTROL Cópias de Idioma]**. O painel Cópias de idioma mostra as cópias de idioma dos ativos.

   ![chlimage_1-123](assets/chlimage_1-123.png)

