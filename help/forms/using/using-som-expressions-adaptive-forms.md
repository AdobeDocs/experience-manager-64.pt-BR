---
title: Uso de expressões SOM em formulários adaptáveis
seo-title: Uso de expressões SOM em formulários adaptáveis
description: Saiba como extrair expressões SOM de um painel de um formulário adaptável.
seo-description: Saiba como extrair expressões SOM de um painel de um formulário adaptável.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18

---


# Uso de expressões SOM em formulários adaptáveis {#using-som-expressions-in-adaptive-forms}

Os formulários adaptáveis são modelados como página AEM, que é representada como estrutura de conteúdo JCR no repositório AEM. O elemento principal da estrutura de conteúdo é o nó guideContainer. Abaixo de guideContainer, há um rootPanel que pode conter campos e painel aninhados.

Você pode usar um SOM (Modelo de objeto de script) para fazer referência a valores, propriedades e métodos em um DOM (Modelo de objeto de documento) específico. Um DOM organiza os objetos de memória e as propriedades em uma hierarquia de árvore. Uma expressão SOM faz referência aos elementos Campos/Desenhar e painéis.

A imagem a seguir descreve uma estrutura de nó à qual um formulário adaptável se traduz ao adicionar componentes a um formulário. Por exemplo, você pode adicionar um painel ao painel raiz e um botão de opção no painel que é transformado em DOM no tempo de execução. A expressão SOM para o campo de botão de opção em forma adaptável é especificada como `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![árvore DOM](assets/hierarchy-1.png)

Uma expressão SOM para qualquer elemento em um formulário adaptável recebe o prefixo `guide[0].guide1[0]`. A posição de um componente na hierarquia da estrutura do nó é usada para derivar sua expressão SOM.

![Árvore DOM com dois botões de opção](assets/hierarchy_radio_button.png)

A expressão SOM muda quando você altera a posição dos botões de opção na forma adaptativa. No modo de criação, é possível exibir a expressão SOM de um campo ou elemento dentro do AEM Forms usando a opção Exibir expressão SOM. A opção é exibida no painel e quando você clica com o botão direito do mouse no campo ou elemento.

![Extrair expressões SOM em um formulário adaptável](assets/som-expressions.png)

Em painéis, você pode acessar o recurso na barra de ferramentas do painel. O recurso facilita a criação de scripts por autores de formulários adaptativos.

![Extrair expressões SOM usando a barra de ferramentas do painel](assets/som-expression.png)

Algumas APIs listadas no [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) usam a expressão SOM de um elemento. Por exemplo, para trazer o foco para um campo específico em um formulário adaptável, passe a expressão SOM correspondente para a `getFocus`API em `guideBridge`.

