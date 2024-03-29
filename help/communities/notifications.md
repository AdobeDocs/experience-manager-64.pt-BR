---
title: Notificações de comunidades
seo-title: Communities Notifications
description: A AEM Communities tem notificações que exibem eventos de interesse para o membro da comunidade que fez logon
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 2%

---

# Notificações de comunidades {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O AEM Communities fornece uma seção de notificações que exibe eventos de interesse para o membro da comunidade com logon assinado.

As notificações são semelhantes a [atividades](essentials-activities.md) e [assinaturas](subscriptions.md) , na medida em que possam resultar de

* O conteúdo de publicação do membro
* O membro que escolheu seguir outro membro
* O membro optando por seguir tópicos específicos, artigos e outros encadeamentos de conteúdo

O que distingue notificações de atividades e subscrições é

* Um link para a seção de notificações está sempre presente no cabeçalho de um site da comunidade
   * As atividades exigem [função de fluxo de atividades](functions.md#activity-stream-function) a ser incluído na estrutura do site da comunidade
   * As assinaturas exigem [configuração do email](email.md)
* A implementação de notificações é por meio de canais escaláveis e conectáveis
   * As atividades só estão disponíveis na Web
   * As assinaturas só estão disponíveis por email

Comunidades [FP1](deploy-communities.md#latestfeaturepack), os canais de notificação disponíveis são

* O canal da Web, acessado por meio do `Notifications` link
* O canal de email, disponível quando o email está configurado corretamente

Os canais futuros são dispositivos móveis e desktop.

### Requisitos {#requirements}

**Configurar Email**

O email deve ser configurado para que o canal de email das notificações funcione.

Para obter instruções sobre como configurar o email, consulte [Configuração de email](analytics.md).

**Habilitar Seguir**

Os componentes devem ser configurados para ativar o seguinte. Os recursos que permitem o seguinte são [blog](blog-feature.md), [fórum](forum.md), [QnA](working-with-qna.md), [calendário](calendar.md), [filelibrary](file-library.md)e [comentários](comments.md).

Observe que

* Componentes usados na comunidade [modelos de site](sites.md) e [modelos de grupo](tools-groups.md) pode já estar configurado para permitir que:

* Os perfis de membro já estão configurados para permitir que outros membros sigam

## Notificações do seguinte {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

O **Seguir** fornece um meio de seguir entradas como atividades, assinaturas e/ou notificações. Sempre que a variável **Seguir** for selecionado, é possível ativar ou desativar uma seleção. O `Email Subscriptions` A seleção só está presente quando configurada.

Se qualquer método de seguir for selecionado, o texto do botão será alterado para **Seguindo**. Para maior comodidade, é possível selecionar `Unfollow All` para desativar todos os métodos.

O **Seguir** o botão será exibido

* Ao visualizar o perfil de outro membro
* Em uma página principal do recurso, como fóruns, QnA e blogs
   * Segue todas as atividades para esse recurso geral
* Para uma entrada específica, como um tópico de fórum, pergunta de QnA ou artigo de blog
   * Segue todas as atividades para essa entrada específica

## Gerenciando configurações de notificação {#managing-notification-settings}

Ao selecionar o link Configurações de notificação na página Notificações , é possível que cada membro gerencie como as notificações são recebidas.

O canal da Web é sempre ativado.

![chlimage_1-255](assets/chlimage_1-255.png)

O canal de email, que depende do [configuração do email](email.md), fornece as mesmas configurações do canal da Web.

O canal de email está desativado por padrão.

![chlimage_1-256](assets/chlimage_1-256.png)

Ele pode ser ativado por um membro, mas ainda depende da configuração do email.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualizar notificações {#viewing-notifications}

### Notificações da Web {#web-notifications}

A [site de comunidade criado pelo assistente](sites-console.md) O agora inclui um link para a `Notifications` na barra de cabeçalho do site acima do banner. Ao contrário das mensagens, as notificações são criadas para cada site da comunidade, enquanto as mensagens devem ser ativadas durante o processo de criação do site.

Ao visitar o site publicado, selecione o `Notifications` exibirá todas as notificações do membro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notificações por email {#email-notifications}

Quando o canal de email está ativado, o membro recebe um email que contém um link para o conteúdo na Web.

![chlimage_1-259](assets/chlimage_1-259.png)
