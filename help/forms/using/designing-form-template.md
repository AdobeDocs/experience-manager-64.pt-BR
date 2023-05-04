---
title: Criação de modelos de formulário para formulários HTML5
seo-title: Designing form templates for HTML5 forms
description: A AEM Forms oferece renderizar o modelo de formulário XFA para o formato HTML5. Os designers de formulários podem criar modelos de formulário usando o Designer e usar o recurso de representação HTML5.
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 4%

---

# Criação de modelos de formulário para formulários HTML5 {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O componente Formulários HTML5 no AEM oferece a renderização do modelo de formulário XFA para o formato HTML5. Os designers de formulários podem criar modelos de formulário usando [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_pt) e use o recurso de representação HTML5. Esses modelos de formulário, juntamente com seus ativos, podem residir em AEM repositório, sistema de arquivos ou expostos via http. No entanto, se você planeja gerenciar seus formulários usando o Forms Manager, os modelos e ativos devem residir no repositório AEM.

Embora os formulários de HTML5 correspondam ao comportamento dos PDF forms, há alguns recursos em ambos os formatos que não se aplicam ao outro formato. Por exemplo, a forma como os códigos de barras são aplicados em um formulário PDF no Adobe Reader varia de um formulário móvel ou como um formulário é assinado digitalmente também varia de acordo com os formatos. Para obter mais informações sobre essas variações, consulte [Diferenciação de recursos entre formulários HTML5 e PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Para obter recursos comuns do XFA, consulte as práticas recomendadas e diretrizes a seguir para projetar um formulário que funcione em ambos os formatos.

## Recursos no AEM Forms Designer para HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### Visualizar HTML {#preview-html}

A guia Visualizar HTML é adicionada no modo Design para que os designers de formulários visualizem formulários no formato HTML5 durante o processo de design. Para obter mais informações sobre como habilitar e configurar esse recurso no AEM Forms Designer, consulte [Visualizar HTML](/help/forms/using/preview-xdp-forms-html.md).

### Assinatura escrita {#scribble-signature}

O alvo principal para formulários do HTML5 é dispositivos de toque. Portanto, um novo controle de assinatura de rabisco é adicionado no AEM Forms Designer. Você pode clicar ou arrastar e soltar o controle de assinatura de rabisco no modelo de formulário e configurá-lo. Ele é renderizado como um campo de rabisco na representação do HTML5 e pode ser usado para rabiscar a assinatura em dispositivos de toque. Em máquinas de desktop, ele pode ser usado como um campo de rabisco usando o controle do mouse. Para obter mais informações sobre como usar esse recurso, consulte [Campo de rabisco XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
