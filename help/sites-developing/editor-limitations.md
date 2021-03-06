---
title: Limitações do editor
seo-title: Limitações do editor
description: O editor na interface habilitada para toque usa sobreposições para interagir com conteúdo confinado em um iframe. Essa interação cria algumas limitações no uso do editor e também para desenvolvedores.
seo-description: O editor na interface habilitada para toque usa sobreposições para interagir com conteúdo confinado em um iframe. Essa interação cria algumas limitações no uso do editor e também para desenvolvedores.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
translation-type: tm+mt
source-git-commit: 9b1b0bd53d6c9e0c2c2857ef34b3409fff8485d2
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Limitações do editor{#editor-limitations}

O editor na interface habilitada para toque usa sobreposições para interagir com conteúdo confinado em um iframe. Essa interação cria algumas limitações no uso do editor e também para desenvolvedores. Esta página resume essas limitações e fornece soluções ou soluções alternativas, sempre que possível.

## Limitações funcionais {#functional-limitations}

Um autor pode encontrar as seguintes limitações funcionais ao usar o editor para criar páginas.

### Links não ativos {#links-not-active}

Quando [editar uma página](/help/sites-authoring/editing-content.md), os links não estão ativos.

* [Alterne para  **** ](/help/sites-authoring/editing-content.md#preview-mode) Visualizar modo de navegação para navegar usando os links no conteúdo.

### Páginas de estrutura {#structure-pages}

As páginas não podem ser nomeadas como `structure`. As páginas nomeadas como `structure` não poderão ser editadas no editor de páginas.

## Limitações de CSS {#css-limitations}

Um desenvolvedor pode encontrar as seguintes limitações com as interações do editor com o CSS.

### Elementos absolutamente posicionados {#absolutely-positioned-elements}

Elementos com posição absoluta podem causar problemas na posição de sua sobreposição.

* Se isso acontecer, verifique se as dimensões do elemento absolutamente posicionado estão corretas, pois o editor criará uma sobreposição com as mesmas dimensões.

### unidades Vh {#vh-units}

`vh` não há suporte para unidades, pois a altura do iframe deve ser automaticamente ajustada por AEM.

### Imagens em segundo plano fixas {#fixed-background-images}

Imagens de plano de fundo fixas podem não ser exibidas como fixas na rolagem devido ao fato de estarem incorporadas em um iframe.

* Selecionar **Página de Visualização como Publicada** nas ações da barra de cabeçalho exibe a página corretamente.

### Altura 100% {#height}

A altura de 100% não é suportada no elemento de corpo de uma página.

* Uma solução alternativa é possível para implementar um corpo de tela cheia &quot;alongando&quot; o elemento do corpo da seguinte forma:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Redução da margem {#margin-collapsing}

Problemas de redução da margem podem ser vistos se o primeiro elemento filho do elemento body tiver uma margem.

* A solução é adicionar uma correção no nível do elemento do corpo, como a seguir:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```

