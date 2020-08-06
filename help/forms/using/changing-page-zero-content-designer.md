---
title: Alteração do conteúdo Zero da página no Designer
seo-title: Alteração do conteúdo Zero da página no Designer
description: Você sabe como alterar a mensagem exibida na Página Zero de um PDF XFA ao exibi-la em um visualizador que não seja da Adobe PDF?
seo-description: Você sabe como alterar a mensagem exibida na Página Zero de um PDF XFA ao exibi-la em um visualizador que não seja da Adobe PDF?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---


# Alteração do conteúdo Zero da página no Designer {#changing-page-zero-content-in-designer}

O conteúdo da Página zero é exibido por padrão quando um visualizador que não seja o Adobe PDF, como o visualizador de PDF padrão no Chrome ou Firefox, não consegue ler o conteúdo do formulário PDF/XFA. A mensagem padrão de Página zero é mostrada abaixo.

![defaultpage0message](assets/defaultpage0message.png)

A versão do AEM Forms Feature Pack 1 do Designer permite alterar a mensagem exibida na Página Zero. Para alterar a mensagem Page Zero (Zero de página), execute as seguintes etapas:

1. Verifique se a versão do AEM Forms Feature Pack 1 do Designer está instalada. Você pode verificar a versão na tela Sobre do designer.

1. Abra o formulário para o qual deseja alterar o conteúdo de Página zero.

1. Click **File > Form Properties**.

1. Na caixa de diálogo Propriedades do formulário, clique em ![mais](assets/plus.png) (ícone de Mais) para adicionar uma propriedade personalizada.

1. Especifique **_pagezerocontent** como o nome da propriedade.
1. Adicione a nova mensagem Zero da página, no formato Rich Text, como valor. Por exemplo:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Salve o formulário como PDF.

1. Visualização o formulário PDF no navegador para confirmar se a mensagem foi atualizada. O exemplo de valor acima é exibido da seguinte maneira:

   ![mensagem alterada](assets/changedmessage.png)

>[!NOTE]
>
>A propriedade personalizada que você acabou de criar pode não aparecer corretamente na caixa de diálogo Propriedades do formulário ao reabrir o formulário. No entanto, funciona bem e o formulário exibe a mensagem Page Zero atualizada.

