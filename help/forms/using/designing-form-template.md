---
title: Criar modelos de formulário para formulários HTML5
seo-title: Criar modelos de formulário para formulários HTML5
description: 'O AEM Forms oferece a renderização do modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o Designer e usar o recurso de execução HTML5. '
seo-description: 'O AEM Forms oferece a renderização do modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o Designer e usar o recurso de execução HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Criar modelos de formulário para formulários HTML5 {#designing-form-templates-for-html-forms}

O componente de formulários HTML5 no AEM oferece a renderização do modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) e usar o recurso de execução HTML5. Esses modelos de formulário, juntamente com seus ativos, podem residir no repositório do AEM, no sistema de arquivos ou ser expostos via http. No entanto, se você planeja gerenciar seus formulários usando o Gerenciador de Formulários, os modelos e ativos devem residir no repositório do AEM.

Embora os formulários HTML5 correspondam em grande medida ao comportamento dos formulários PDF, há alguns recursos em ambos os formatos que não são aplicáveis ao outro formato. Por exemplo, o modo como os códigos de barras são aplicados em um formulário PDF no Adobe Reader varia de um formulário móvel ou como um formulário é assinado digitalmente também varia entre os formatos. Para obter mais informações sobre essas variações, consulte Diferenciação de [recursos entre formulários HTML5 e formulários](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)PDF.

Para obter recursos comuns do XFA, consulte as seguintes práticas recomendadas e diretrizes para projetar um formulário que funcione em ambos os formatos.

## Recursos no AEM Forms Designer para HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### Visualizar HTML {#preview-html}

A guia Visualizar HTML é adicionada no modo Design para que os designers de formulário visualizem formulários no formato HTML5 durante o processo de design. Para obter mais informações sobre como ativar e configurar esse recurso no AEM Forms Designer, consulte [Visualizar HTML](/help/forms/using/preview-xdp-forms-html.md).

### Assinatura {#scribble-signature}

O principal destino para formulários HTML5 é dispositivos de toque. Portanto, um novo controle de assinatura de script é adicionado no AEM Forms Designer. Você pode clicar ou arrastar e soltar o controle de assinatura em seu modelo de formulário e configurá-lo. Ele é renderizado como um campo de script na execução HTML5 e pode ser usado para rabiscar a assinatura em dispositivos de toque. Em computadores desktop, ele pode ser usado como um campo de script usando o controle do mouse. Para obter mais informações sobre como usar esse recurso, consulte Campo de script [XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)

[Contate o suporte](https://www.adobe.com/account/sign-in.supportportal.html)
