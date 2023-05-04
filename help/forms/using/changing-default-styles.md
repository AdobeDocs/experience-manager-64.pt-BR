---
title: Alteração dos estilos padrão de formulários HTML5
seo-title: Changing default styles of HTML5 forms
description: O estilo de formulários do HTML5 é baseado no CSS. É possível alterar os estilos padrão do formulário.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 3%

---

# Alteração dos estilos padrão de formulários HTML5 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os formulários HTML5 são renderizados usando recursos HTML5 e o estilo do formulário renderizado é feito usando CSS. A aparência padrão de um formulário HTML5 é semelhante à sua representação de PDF. Os desenvolvedores podem usar o CSS personalizado para alterar a aparência padrão dos formulários HTML5.

Este artigo fornece informações passo a passo para alterar o estilo de um formulário HTML5 e [Introdução aos estilos](/help/forms/using/css-styles.md) este artigo contém informações detalhadas sobre vários aspectos de estilo de formulários HTML5. Leia a Introdução ao artigo de estilos antes de executar as etapas mencionadas neste artigo.

As duas imagens a seguir mostram a diferença entre os estilos padrão e personalizado.

![picture-002-small](assets/pictures-002-small.png)

## Estilo dos formulários {#style-your-forms}

1. **Escolha um perfil para adicionar estilos personalizados**

   Acesse a interface CRX DE no URL: **https://&lt;server>:&lt;port>/crx/de** e criar um perfil ou escolher um perfil existente. Para saber como criar um perfil, consulte [Criação de um novo perfil](/help/forms/using/custom-profile.md)

1. **Crie uma folha de estilos CSS para estilizar os formulários HTML5**

   Navegue até a pasta em que você criou o renderizador de perfil e crie um arquivo de folha de estilos CSS. As etapas a seguir são

   1. Clique com o botão direito do mouse na pasta e selecione **criar** -> **criar arquivo** no menu
   Para saber quais classes CSS CSS criar para um componente específico em seus formulários do HTML5, consulte [Introdução aos estilos](/help/forms/using/css-styles.md).

1. **Incluir a folha de estilos no Renderizador de perfis**

   Abra a página Renderizador de perfil (arquivo jsp) no CRX DE e inclua o arquivo CSS na página logo abaixo da biblioteca do cliente XFA. Execute essas etapas para incluir o arquivo CSS no perfil.

   1. Pesquise na página do renderizador a seguinte linha:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Insira o seguinte abaixo da linha acima para incluir a folha de estilos:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Salve o arquivo.
