---
title: Preparação de ativos para tradução
description: Crie pastas raiz de idioma para preparar a tradução de ativos multilíngues.
contentOwner: AG
feature: Projects,Translation
role: User,Admin
exl-id: cc6c4f9e-8e22-4622-8b24-230ae258351c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 9%

---

# Preparação de ativos para tradução {#preparing-assets-for-translation}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ativos multilíngues significa ativos com binários, metadados e tags em vários idiomas. Geralmente, os binários, metadados e tags de ativos existem em um idioma, que é traduzido para outros idiomas para uso em projetos multilíngues.

No Adobe Experience Manager Assets, os ativos multilíngues são incluídos nas pastas, onde cada pasta contém os ativos em um idioma diferente.

Cada pasta de idioma é chamada de cópia de idioma. A pasta raiz de uma cópia de idioma, conhecida como raiz de idioma, identifica o idioma do conteúdo na cópia de idioma. Por exemplo, */content/dam/it* é a raiz do idioma italiano para a cópia em língua italiana. As cópias de idioma devem usar um [raiz de idioma configurada corretamente](preparing-assets-for-translation.md#creating-a-language-root) para que o idioma correto seja direcionado quando as traduções de ativos de origem forem executadas.

A cópia de idioma para a qual você adicionou ativos originalmente é o idioma principal. O idioma principal é a fonte traduzida para outros idiomas.

A hierarquia de pastas de exemplo inclui várias raízes de idioma:

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

Execute as seguintes etapas para preparar os ativos para tradução:

1. Crie a raiz do idioma do idioma principal. Por exemplo, a raiz de idioma da cópia em inglês na hierarquia de pasta de amostra é `/content/dam/en`. Verifique se a raiz do idioma está configurada corretamente de acordo com as informações em [Criar uma raiz de idioma](preparing-assets-for-translation.md#creating-a-language-root).

1. Adicione ativos ao idioma principal.
1. Crie a raiz de idioma de cada idioma de destino para o qual você precisa de uma cópia de idioma.

## Criar uma raiz de idioma {#creating-a-language-root}

Para criar a raiz de idioma, crie uma pasta e use um código de idioma ISO como o valor da propriedade Name. Depois de criar a raiz do idioma, você pode criar uma cópia de idioma em qualquer nível na raiz do idioma.

Por exemplo, a página raiz da cópia de idioma italiano da hierarquia de amostra tem `it` como a propriedade Name . A propriedade Name é usada como o nome do nó do ativo no repositório e, portanto, determina o caminho dos ativos. (`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. No console Assets, clique/toque em **[!UICONTROL Criar]** e escolha **[!UICONTROL Pasta]** no menu.

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. No campo Nome, digite o código do país no formato de `<language-code>`.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Clique ou toque em **[!UICONTROL Criar]**. A raiz do idioma é criada no console Assets.

## Exibindo Raízes de Idioma {#viewing-language-roots}

A interface otimizada para toque fornece um painel Referências que mostra uma lista de raízes de idioma que foram criadas em [!DNL Experience Manager] Ativos.

1. No console Assets, selecione o idioma principal para o qual deseja criar cópias de idioma.
1. Clique ou toque no ícone de Navegação global e escolha **[!UICONTROL Referências]** para abrir o painel Referência.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. No painel Referências , clique ou toque em **[!UICONTROL Cópias de idioma]**. O painel Cópias de idioma mostra as cópias de idioma dos ativos.

   ![chlimage_1-123](assets/chlimage_1-123.png)
