---
title: Alteração do conteúdo zero da página no Designer
seo-title: Changing Page Zero content in Designer
description: Você sabe como alterar a mensagem exibida na Página Zero de um PDF XFA ao exibi-la em um visualizador que não seja da Adobe PDF?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 4%

---

# Alteração do conteúdo zero da página no Designer {#changing-page-zero-content-in-designer}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O conteúdo zero da página é exibido por padrão quando um visualizador que não seja da Adobe PDF, como o visualizador de PDF padrão no Chrome ou Firefox, não consegue ler o conteúdo do formulário PDF/XFA. A mensagem padrão Zero da página é mostrada abaixo.

![defaultpage0message](assets/defaultpage0message.png)

A versão do AEM Forms Feature Pack 1 do Designer permite alterar a mensagem exibida na Página Zero. Para alterar a mensagem Zero da página, execute as seguintes etapas:

1. Verifique se a versão do AEM Forms Feature Pack 1 do Designer está instalada. Você pode verificar a versão na tela Sobre do designer.

1. Abra o formulário no qual deseja alterar o conteúdo Zero da página.

1. Clique em **Arquivo > Propriedades do formulário**.

1. Na caixa de diálogo Propriedades do formulário, clique em ![plus](assets/plus.png) (Ícone de adição) para adicionar uma propriedade personalizada.

1. Especificar **_pagezerocontent** como o nome da propriedade.
1. Adicione a nova mensagem Zero da página, no formato Rich Text, como valor. Por exemplo:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Salve o formulário como PDF.

1. Exiba o formulário PDF no navegador para confirmar se a mensagem foi atualizada. O exemplo de valor acima é exibido da seguinte maneira:

   ![mensagem alterada](assets/changedmessage.png)

>[!NOTE]
>
>A propriedade personalizada recém-criada pode não aparecer corretamente na caixa de diálogo Propriedades do formulário ao reabrir o formulário. No entanto, funciona bem e o formulário exibe a mensagem Página zero atualizada.
