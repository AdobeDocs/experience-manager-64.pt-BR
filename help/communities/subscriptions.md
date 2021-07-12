---
title: Assinaturas das Comunidades
seo-title: Assinaturas das Comunidades
description: 'Os membros da comunidade interagem com outros membros por email '
seo-description: 'Os membros da comunidade interagem com outros membros por email '
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Admin
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 1%

---

# Assinaturas das Comunidades {#communities-subscriptions}

## Visão geral {#overview}

A partir de Comunidades [FP1](deploy-communities.md#latestfeaturepack), os membros da comunidade podem interagir com a comunidade por meio de email usando um recurso chamado de assinaturas.

As assinaturas são semelhantes a [notificações](notifications.md), pois os membros podem se inscrever ao seguir artigos de blog, tópicos do fórum ou perguntas de QnA.

O que distingue as assinaturas das notificações é:

* Os membros não podem subscrever-se quando se seguir outros membros
* A única ação que os membros devem tomar é selecionar `Email Subscriptions` ao seguir
* Quando a resposta por email é configurada, os membros podem publicar conteúdo simplesmente respondendo ao email recebido

### Requisitos {#requirements}

**Configurar Email**

O email deve ser configurado para que as assinaturas sejam funcionais e os membros respondam por email.

Para obter instruções sobre como configurar o email, consulte [Configuração do email](email.md).

**Ativar assinaturas e seguir**

Os componentes devem ser configurados para ativar as assinaturas *e* a seguir. Os recursos que permitem assinaturas são [blog](blog-feature.md), [forum](forum.md) e [QnA](working-with-qna.md).

## Assinaturas do seguinte {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

O botão **Follow** fornece um meio de seguir entradas como atividades, assinaturas e/ou notificações. Sempre que o botão **Follow** é selecionado, é possível ativar ou desativar uma seleção.

Se qualquer método do seguinte for selecionado, o texto do botão será alterado para **Seguindo**. Para maior comodidade, é possível selecionar `Unfollow All` para desligar todos os métodos.

O botão **Follow** incluirá a opção `Email Subscriptions` somente quando um fórum, QnA ou blog estiver configurado para ativar assinaturas de email. Este botão será exibido

* Na página de recurso principal do fórum habilitado, QnA ou blog

   * Enviará um email para todas as atividades desse recurso

* Para uma entrada específica, como um tópico de fórum, pergunta de QnA ou artigo de blog

   * Enviará um email quando houver atividade para essa entrada específica

## Responder por email {#reply-by-email}

Quando o email for [configurado para responder por email](email.md#configure-polling-importer), o membro que se inscreveu receberá um email com o conteúdo postado e um link para o conteúdo online.

Se responderem ao email, o conteúdo inserido na resposta será exibido como conteúdo online.

![chlimage_1-6](assets/chlimage_1-6.png)

O tempo que leva para uma resposta ser postada é controlado pelo [intervalo de atualização do importador de pesquisa](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)
