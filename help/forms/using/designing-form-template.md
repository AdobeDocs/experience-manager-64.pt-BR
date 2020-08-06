---
title: Criar modelos de formulário para formulários HTML5
seo-title: Criar modelos de formulário para formulários HTML5
description: 'O AEM Forms oferta renderiza o modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o Designer e usar o recurso de execução HTML5. '
seo-description: 'O AEM Forms oferta renderiza o modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o Designer e usar o recurso de execução HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# Criar modelos de formulário para formulários HTML5 {#designing-form-templates-for-html-forms}

O componente de formulários HTML5 no AEM oferta que renderiza o modelo de formulário XFA para o formato HTML5. Os designers de formulário podem criar modelos de formulário usando o [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) e usar o recurso de execução HTML5. Esses modelos de formulário, juntamente com seus ativos, podem residir AEM repositório, sistema de arquivos ou expostos via http. No entanto, se você planeja gerenciar seus formulários usando o Forms Manager, os modelos e ativos devem residir no repositório AEM.

Embora os formulários HTML5 correspondam em grande medida ao comportamento dos PDF forms, há alguns recursos em ambos os formatos que não são aplicáveis ao outro formato. Por exemplo, o modo como os códigos de barras são aplicados em um formulário PDF no Adobe Reader varia de um formulário móvel ou como um formulário é assinado digitalmente também varia de acordo com os formatos. Para obter mais informações sobre essas variações, consulte Diferenciação de [recursos entre formulários HTML5 e PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Para obter recursos comuns do XFA, consulte as seguintes práticas recomendadas e diretrizes para projetar um formulário que funcione em ambos os formatos.

## Recursos no AEM Forms Designer para HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### HTML de Pré-visualização {#preview-html}

A guia HTML de Pré-visualização é adicionada no modo Design para designers de formulário para pré-visualização de formulários no formato HTML5 durante o processo de design. Para obter mais informações sobre como habilitar e configurar esse recurso no AEM Forms Designer, consulte HTML [de](/help/forms/using/preview-xdp-forms-html.md)Pré-visualização.

### Assinatura {#scribble-signature}

O público alvo principal para formulários HTML5 é dispositivos de toque. Portanto, um novo controle de assinatura de script é adicionado no AEM Forms Designer. Você pode clicar ou arrastar e soltar o controle de assinatura em seu modelo de formulário e configurá-lo. Ele é renderizado como um campo de script na execução HTML5 e pode ser usado para rabiscar a assinatura em dispositivos de toque. Em computadores desktop, ele pode ser usado como um campo de script usando o controle do mouse. Para obter mais informações sobre como usar esse recurso, consulte Campo de script [XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
