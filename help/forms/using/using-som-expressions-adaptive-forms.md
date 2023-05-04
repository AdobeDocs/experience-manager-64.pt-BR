---
title: Uso de expressões SOM em formulários adaptáveis
seo-title: Using SOM expressions in adaptive forms
description: Saiba como extrair expressões SOM de um painel de um formulário adaptável.
seo-description: Learn how to extract SOM expressions of a panel of an adaptive form.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
feature: Adaptive Forms
exl-id: e4680ede-6a02-4b8b-8a6f-9599a05da8e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 2%

---

# Uso de expressões SOM em formulários adaptáveis {#using-som-expressions-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os formulários adaptáveis são modelados como Página AEM, que é representada como estrutura de conteúdo JCR em AEM repositório. O elemento principal da estrutura de conteúdo é o nó guideContainer . Abaixo guideContainer, há um rootPanel que pode conter campos e painel aninhados.

Você pode usar um SOM (Modelo de objeto de script) para fazer referência a valores, propriedades e métodos em um DOM (Modelo de objeto de documento) específico. Um DOM organiza os objetos e as propriedades da memória em uma hierarquia de árvore. Uma expressão SOM faz referência a elementos e painéis Campos/Desenhar .

A imagem a seguir descreve uma estrutura de nó para a qual um formulário adaptável é convertido ao adicionar componentes a um formulário. Por exemplo, você pode adicionar um painel ao painel raiz e um botão de opção no painel que é transformado em DOM no tempo de execução. A Expressão SOM para o campo de botão de opção no formulário adaptável é especificada como `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![Árvore DOM](assets/hierarchy-1.png)

Uma expressão SOM para qualquer elemento em um formulário adaptável tem o prefixo `guide[0].guide1[0]`. A posição de um componente na hierarquia da estrutura do nó é usada para derivar sua expressão SOM.

![Árvore DOM com dois botões de opção](assets/hierarchy_radio_button.png)

A expressão SOM muda quando você altera a posição dos botões de opção no formulário adaptável. No modo de criação, é possível exibir a expressão SOM de um campo ou elemento no AEM Forms usando a opção Exibir expressão SOM . A opção é exibida no painel e quando você clica com o botão direito do mouse no campo ou elemento.

![Extração de expressões SOM em um formulário adaptável](assets/som-expressions.png)

Em painéis, você pode acessar o recurso na barra de ferramentas do painel. O recurso facilita os scripts de autores de formulários adaptáveis.

![Extraindo expressões SOM usando a barra de ferramentas do painel](assets/som-expression.png)

Algumas APIs listadas em [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) use a expressão SOM de um elemento. Por exemplo, para trazer o foco para um campo específico em um formulário adaptável, passe a expressão SOM correspondente para a variável `getFocus`API em `guideBridge`.
