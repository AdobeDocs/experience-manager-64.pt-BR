---
title: Alteração de estilos padrão de formulários HTML5
seo-title: Alteração de estilos padrão de formulários HTML5
description: O estilo de formulários HTML5 é baseado em CSS. É possível alterar os estilos padrão do formulário.
seo-description: O estilo de formulários HTML5 é baseado em CSS. É possível alterar os estilos padrão do formulário.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Alteração de estilos padrão de formulários HTML5 {#changing-default-styles-of-html-forms}

Os formulários HTML5 são renderizados usando recursos HTML5 e o estilo do formulário renderizado é feito usando CSS. A aparência padrão de formulários HTML5 é semelhante à sua execução em PDF. Os desenvolvedores podem usar CSS personalizado para alterar a aparência padrão dos formulários HTML5.

Este artigo fornece informações passo a passo para alterar o estilo de um formulário HTML5 e o artigo [Introdução aos estilos](/help/forms/using/css-styles.md) contém informações detalhadas sobre vários aspectos de estilização de formulários HTML5. Certifique-se de ler o artigo Introdução aos estilos antes de executar as etapas mencionadas neste artigo.

As duas imagens a seguir mostram a diferença entre os estilos padrão e personalizado.

![picture-002-small](assets/pictures-002-small.png)

## Estilo de seus formulários {#style-your-forms}

1. **Escolha um perfil para adicionar estilos personalizados**

   Acesse a interface CRX DE no URL: **https://&lt;servidor>:&lt;porta>/crx/de** e crie um perfil ou escolha um perfil existente. Para saber como criar um perfil, consulte [Criação de um novo Perfil](/help/forms/using/custom-profile.md)

1. **Criar uma folha de estilos CSS para estilizar os formulários HTML5**

   Navegue até a pasta na qual você criou o renderizador de perfis e crie um arquivo de folha de estilos CSS. As etapas a seguir são

   1. Clique com o botão direito do mouse na pasta e selecione **criar** -> **criar arquivo** no menu
   Para saber quais classes CSS criar para um componente específico em seus formulários HTML5, consulte [Introdução aos estilos](/help/forms/using/css-styles.md).

1. **Incluir a folha de estilos no Renderizador de Perfis**

   Abra a página do Renderizador de Perfis (arquivo jsp) no CRX DE e inclua o arquivo CSS na página logo abaixo da biblioteca do cliente XFA. Execute estas etapas para incluir o arquivo CSS no perfil.

   1. Pesquise na página do renderizador a seguinte linha:

      &lt;cq:includeClientLib categoria=&quot;xfaforms.perfil&quot; />

   1. Insira o seguinte abaixo da linha acima para incluir a folha de estilos:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Salve o arquivo.

