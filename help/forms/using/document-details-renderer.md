---
title: Detalhes do documento para renderizador
seo-title: Detalhes do documento para renderizador
description: Informações conceituais sobre como as renderizações funcionam na área de trabalho do AEM Forms para renderizar os vários tipos de formulários e arquivos suportados.
seo-description: Informações conceituais sobre como as renderizações funcionam na área de trabalho do AEM Forms para renderizar os vários tipos de formulários e arquivos suportados.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---


# Detalhes do documento para renderizador {#document-details-for-renderer}

## Introdução {#introduction}

Na área de trabalho do AEM Forms, vários tipos de formulário são suportados perfeitamente. Dentre elas:

* PDF forms (XDP / Acroform / PDFs achatados)
* Novos formulários HTML
* Imagens
* Aplicativos de terceiros (por exemplo, Gerenciamento de correspondência)

Este documento explica o funcionamento desses renderizadores da perspectiva de personalização semântica / reutilização de componentes, de modo que as necessidades do cliente sejam atendidas sem interromper nenhuma execução. Embora a área de trabalho do AEM Forms permita qualquer interface de usuário/alteração semântica, recomenda-se que a lógica de renderização de diferentes tipos de formulário não seja alterada, caso contrário, os resultados podem ser imprevisíveis. Este documento serve para orientação / conhecimento para suportar a renderização do mesmo formulário, usando os mesmos componentes de espaço de trabalho em portais diferentes, e não para modificar a lógica de renderização propriamente dita.

## PDF forms {#pdf-forms}

PDF forms são renderizados por `PdfTaskForm View`.

Quando um formulário XDP é renderizado como PDF, um `FormBridge` JavaScript™ é adicionado pelo serviço FormsAugmenter. Esse JavaScript™ (dentro do formulário PDF) ajuda a executar ações como enviar formulários, salvar formulários ou tornar o formulário off-line.

Na área de trabalho do AEM Forms, a visualização PDFTaskForm se comunica com `FormBridge`javascript, por meio de um HTML intermediário presente em `/lc/libs/ws/libs/ws/pdf.html`. O fluxo é:

**VISUALIZAÇÃO PDFTaskForm - pdf.html**

Comunica-se usando `window.postMessage` / `window.attachEvent('message')`

Este método é a forma padrão de comunicação entre um quadro pai e um iframe. Os ouvintes de eventos existentes de PDF forms abertos anteriormente são removidos antes de adicionar um novo. Essa limpeza também considera a alternância entre a guia de formulário e a guia de histórico na visualização de detalhes da tarefa.

**pdf.html -  `FormBridge`javascript dentro do PDF renderizado**

Comunica-se usando `pdfObject.postMessage` / `pdfObject.messageHandler`

Este método é a maneira padrão de comunicação com um javascript PDF de um HTML. A visualização PdfTaskForm também cuida de PDF simples e o renderiza claramente.

>[!NOTE]
>
>Não é recomendado modificar o pdf.html / conteúdo da visualização PdfTaskForm.

## Novo Forms HTML {#new-html-forms}

Novos formulários HTML são renderizados pela Visualização NewHTMLTaskForm.

Quando um formulário XDP é renderizado como HTML usando o pacote de formulários móveis implantado no CRX, ele também adiciona `FormBridge` javascript adicional ao formulário, o que expõe diferentes métodos para salvar e enviar dados de formulário.

Esse javascript é diferente daquele mencionado em PDF forms acima, mas tem um propósito semelhante.

>[!NOTE]
>
>Não é recomendado modificar o conteúdo da visualização NewHTMLTaskForm.

## Flex Forms e Guias {#flex-forms-and-guides}

O Flex Forms é renderizado por SwfTaskForm e os guias são renderizados por Visualizações HtmlTaskForm, respectivamente.

No espaço de trabalho do AEM Forms, essas visualizações se comunicam com o SWF real, que compõe o formulário/guia flexível usando um SWF intermediário presente em `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

A comunicação ocorre usando `swfObject.postMessage` / `window.flexMessageHandler`.

Este protocolo é definido pelo `WsNextAdapter.swf`. O objeto existente `flexMessageHandlers`na janela, de formulários SWF abertos anteriormente, são removidos antes de adicionar um novo. A lógica também considera a alternância entre a guia de formulário e a guia de histórico na visualização de detalhes da tarefa. `WsNextAdapter.swf` é usado para executar várias ações de formulário, como salvar ou enviar.

>[!NOTE]
>
>Não é recomendado modificar `WSNextAdapter.swf` ou o conteúdo da visualização SwfTaskForm / HtmlTaskForm.

## Aplicativos de terceiros (por exemplo, Gerenciamento de correspondência) {#third-party-applications-for-example-correspondence-management}

Aplicativos de terceiros são renderizados usando a visualização ExtAppTaskForm.

**Comunicação de aplicativos de terceiros para a área de trabalho AEM Forms**

A área de trabalho do AEM Forms escuta em `window.global.postMessage([Message],[Payload])`

[O ] Messagecan pode ser uma cadeia especificada como  `SubmitMessage`|  `CancelMessage`|  `ErrorMessage`|  `actionEnabledMessage`na  `runtimeMap`. Aplicativos de terceiros devem usar essa interface para notificar a área de trabalho da AEM Forms, conforme necessário. O uso dessa interface é obrigatório, pois a área de trabalho do AEM Forms deve saber isso quando a tarefa é enviada para que possa limpar a janela da tarefa.

**Área de trabalho AEM Forms para comunicação de aplicativos de terceiros**

Se os botões de ação direta do espaço de trabalho AEM Forms estiverem visíveis, ele chamará `window.[External-App-Name].getMessage([Action])`, onde `[Action]` será lido a partir de `routeActionMap`. O aplicativo de terceiros deve acompanhar essa interface e notificar o espaço de trabalho da AEM Forms por meio da API `postMessage ()`.

Por exemplo, um aplicativo Flex pode definir `ExternalInterface.addCallback('getMessage', listener)` para suportar essa comunicação. Se o aplicativo de terceiros desejar manipular o envio do formulário por meio de seus próprios botões, você deverá especificar `hideDirectActions = true() in the runtimeMap` e poderá ignorar esse ouvinte. Por isso, essa construção é opcional.

Você pode ler mais sobre a integração de aplicativos de terceiros em relação ao Gerenciamento de correspondência em [Integrando o Gerenciamento de correspondência na área de trabalho da AEM Forms](/help/forms/using/integrating-correspondence-management-html-workspace.md).

