---
title: Assinaturas das Comunidades
seo-title: Communities Subscriptions
description: Os membros da comunidade interagem com outros membros por email
seo-description: Community members interact with other members through email
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Admin
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---

# Assinaturas das Comunidades {#communities-subscriptions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Comunidades [FP1](deploy-communities.md#latestfeaturepack), os membros da comunidade podem interagir com a comunidade por email usando um recurso chamado de assinaturas.

As assinaturas são semelhantes a [notificações](notifications.md) como membros podem se inscrever ao seguir artigos de blog, tópicos do fórum ou perguntas de QnA.

O que distingue as assinaturas das notificações é:

* Os membros não podem subscrever-se quando se seguir outros membros
* A única ação que os membros devem tomar é selecionar `Email Subscriptions` ao seguir
* Quando a resposta por email é configurada, os membros podem publicar conteúdo simplesmente respondendo ao email recebido

### Requisitos {#requirements}

**Configurar Email**

O email deve ser configurado para que as assinaturas sejam funcionais e os membros respondam por email.

Para obter instruções sobre como configurar o email, consulte [Configuração de email](email.md).

**Ativar assinaturas e seguir**

Os componentes devem ser configurados para habilitar assinaturas *e* seguinte. Os recursos que permitem assinaturas são [blog](blog-feature.md), [fórum](forum.md) e [QnA](working-with-qna.md).

## Assinaturas do seguinte {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

O **Seguir** fornece um meio de seguir entradas como atividades, assinaturas e/ou notificações. Sempre que a variável **Seguir** for selecionado, é possível ativar ou desativar uma seleção.

Se qualquer método de seguir for selecionado, o texto do botão será alterado para **Seguindo**. Para maior comodidade, é possível selecionar `Unfollow All` para desativar todos os métodos.

O **Seguir** incluirá o botão `Email Subscriptions` somente quando um fórum, QnA ou blog é configurado para ativar assinaturas de email. Este botão será exibido

* Na página de recurso principal do fórum habilitado, QnA ou blog

   * Enviará um email para todas as atividades desse recurso

* Para uma entrada específica, como um tópico de fórum, pergunta de QnA ou artigo de blog

   * Enviará um email quando houver atividade para essa entrada específica

## Responder por email {#reply-by-email}

Quando o email é [configurado para responder por email](email.md#configure-polling-importer), o membro que se inscreveu receberá um email com o conteúdo publicado e um link para o conteúdo online.

Se responderem ao email, o conteúdo inserido na resposta será exibido como conteúdo online.

![chlimage_1-6](assets/chlimage_1-6.png)

O tempo necessário para uma resposta ser postada é controlado pela variável [intervalo de atualização do importador de pesquisa](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)
