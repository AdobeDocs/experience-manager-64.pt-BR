---
title: Leitores de tela para formulários HTML5
seo-title: Screen readers for HTML5 forms
description: Lista os leitores de tela compatíveis com formulários HTML5.
seo-description: Lists the screen readers supported with HTML5 forms.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: c27eb771-d390-4534-8e67-f1277550e760
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Leitores de tela para formulários HTML5 {#screen-readers-for-html-forms}

Os componentes de formulários HTML5 renderizam o modelo de formulário XFA em um formato HTML5. Todos os navegadores padrão compatíveis com HTML5 podem renderizar esses formulários. Para oferecer suporte a experiências semelhantes de captura de dados em formulários PDF e HTML5, o layout do PDF forms é retido em formulários HTML5.

Os formulários HTML5 usam construções HTML padrão que permitem que ferramentas de acessibilidade comuns para HTML sejam usadas com esses formulários. Se um formulário for projetado de acordo com as práticas recomendadas para formulários acessíveis, ele funcionará com qualquer leitor de tela suportado. Além disso, esses formulários são ativados para navegação pelo teclado.

## Padrões de acessibilidade {#accessibility-standards}

Os formulários HTML5 estão em conformidade com a seção 508 para acessibilidade com exceções conhecidas. Consulte [VPAT para formulários HTML5](http://wwwimages.adobe.com/content/dam/acom/en/accessibility/compliance/pdfs/livecycle-mobile-forms-es4-section-508-vpat.pdf) para obter detalhes.

## Leitores de tela certificados para formulários HTML5 {#certified-screen-readers-for-html-forms}

* JAWS 14.0 no Microsoft Windows
* VoiceOver no Mac OS X e iPad

### JAWS {#jaws}

Todos os pressionamentos de tecla e atalhos padrão funcionam para formulários HTML5. Para obter mais informações sobre como usar o JAWS, visite [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp).

### VoiceOver {#voiceover}

Os formulários HTML5 são compatíveis com todos os pressionamentos de teclas e gestos padrão do Voice over. Para obter mais informações sobre como configurar e usar o VoiceOver, consulte [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Problemas conhecidos {#known-issues}

* **(Somente no Internet Explorer 9)** Nos formulários HTML5, as páginas são carregadas sob demanda (dinamicamente). O carregamento de página sob demanda causa problemas com o funcionamento dos leitores de tela. Quando o foco do leitor de tela estiver no último campo da página e o usuário pressionar a tecla tab, em vez de definir o foco no primeiro campo da próxima página, o leitor de tela retornará o foco para o primeiro campo da primeira página do formulário.
* **(Somente no Explorer 9 interno)** O controle do Seletor de data em formulários HTML5 não é totalmente acessível com teclado. No controle do Seletor de datas, se você pressionar várias vezes as teclas Para cima/Para baixo, o controle do Seletor de datas será fechado e o foco será movido para o campo seguinte/último.

* O VoiceOver não consegue detectar as teclas de seta no widget de data no iPad safari.
