---
title: Notificações de comunidades
seo-title: Notificações de comunidades
description: O AEM Communities tem notificações que exibem eventos de interesse para o membro da comunidade conectado
seo-description: O AEM Communities tem notificações que exibem eventos de interesse para o membro da comunidade conectado
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Notificações de comunidades {#communities-notifications}

## Visão geral {#overview}

O AEM Communities fornece uma seção de notificações que exibe eventos de interesse para o membro da comunidade conectado.

As notificações são semelhantes a [atividades](essentials-activities.md) e [assinaturas](subscriptions.md) , pois podem resultar de

* O conteúdo de publicação do membro
* O membro que escolheu seguir outro membro
* O membro optou por seguir tópicos específicos, artigos e outros segmentos de conteúdo

O que distingue as notificações de atividades e assinaturas é

* Um link para a seção de notificações está sempre presente no cabeçalho de um site da comunidade
   * As atividades exigem que a função [de fluxo de](functions.md#activity-stream-function) atividades seja incluída na estrutura do site da comunidade
   * As assinaturas exigem a [configuração do email](email.md)
* A implementação de notificações é feita por canais escaláveis e conectáveis
   * As atividades só estão disponíveis na Web
   * As assinaturas só estão disponíveis por email

A partir do [FP1](deploy-communities.md#latestfeaturepack)das Comunidades, os canais de notificação disponíveis são

* O canal da Web, acessado usando o `Notifications` link
* O canal de email, disponível quando o email está configurado corretamente

Os canais futuros são móveis e desktops.

### Requisitos {#requirements}

**Configurar email**

O e-mail deve ser configurado para que o canal de e-mail possa permitir que as notificações funcionem.

Para obter instruções sobre como configurar o email, consulte [Configuração do email](analytics.md).

**Habilitar Seguir**

Os componentes devem ser configurados para permitir o seguinte. Os recursos que permitem o seguinte são [blog](blog-feature.md), [fórum](forum.md), [QnA](working-with-qna.md), [calendário](calendar.md), [biblioteca](file-library.md)[](comments.md)e comentários.

Observe que

* Os componentes usados nos modelos [de](sites.md) site da comunidade e modelos [de](tools-groups.md) grupo já podem ser configurados para permitir o seguinte

* Os perfis de membros já estão configurados para permitir que outros membros sigam

## Notificações do seguinte {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

O botão **Seguir** fornece um meio de seguir entradas como atividades, assinaturas e/ou notificações. Sempre que o botão **Seguir** é selecionado, é possível ativar ou desativar uma seleção. A `Email Subscriptions` seleção só está presente quando configurada.

Se algum método de seguir for selecionado, o texto do botão mudará para **Seguinte**. Para sua conveniência, é possível optar por desativar todos os métodos `Unfollow All` .

O botão **Seguir** será exibido

* Ao exibir o perfil de outro membro
* Em uma página principal de recursos, como fóruns, QnA e blogs
   * Segue toda a atividade desse recurso geral
* Para uma entrada específica, como um tópico do fórum, uma pergunta de QnA ou um artigo do blog
   * Segue toda a atividade dessa entrada específica

## Gerenciando configurações de notificação {#managing-notification-settings}

Ao selecionar o link Configurações de notificação na página Notificações, é possível que cada membro gerencie como as notificações são recebidas.

O canal da Web está sempre ativado.

![chlimage_1-255](assets/chlimage_1-255.png)

O canal de email, que depende da [configuração correta do email](email.md), fornece as mesmas configurações do canal da Web.

O canal de email está desligado por padrão.

![chlimage_1-256](assets/chlimage_1-256.png)

Pode ser ativado por um membro, mas ainda depende do email que está sendo configurado.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualizar notificações {#viewing-notifications}

### Notificações da Web {#web-notifications}

Um [assistente criou um site](sites-console.md) da comunidade agora inclui um link para o `Notifications` recurso na barra de cabeçalho do site acima do banner. Ao contrário das mensagens, as notificações são criadas para cada site da comunidade, enquanto as mensagens devem ser ativadas durante o processo de criação do site.

Ao visitar o site publicado, selecionar o `Notifications` link exibirá todas as notificações do membro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notificações por email {#email-notifications}

Quando o canal de email está ativado, o membro recebe um email que contém um link para o conteúdo da Web.

![chlimage_1-259](assets/chlimage_1-259.png)

