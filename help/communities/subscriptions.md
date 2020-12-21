---
title: Subscrições de comunidades
seo-title: Subscrições de comunidades
description: 'Os membros da comunidade interagem com outros membros por email '
seo-description: 'Os membros da comunidade interagem com outros membros por email '
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# Subscrições de comunidades {#communities-subscriptions}

## Visão geral {#overview}

A partir de Communities [FP1](deploy-communities.md#latestfeaturepack), os membros da comunidade podem interagir com a comunidade por email usando um recurso chamado subscrição.

As subscrições são semelhantes a [notificações](notifications.md), pois os membros podem se inscrever ao seguir artigos de blog, tópicos do fórum ou perguntas de QnA.

O que distingue as subscrições das notificações é:

* Os membros não podem subscrever quando seguirem outros membros
* A única ação a ser tomada pelos membros é selecionar `Email Subscriptions` ao seguir
* Quando a resposta por e-mail é configurada, os membros podem efetivamente postar o conteúdo simplesmente respondendo ao e-mail recebido

### Requisitos {#requirements}

**Configurar email**

O email deve ser configurado para que as subscrições estejam funcionais e para que os membros respondam por email.

Para obter instruções sobre como configurar o email, consulte [Configuração do Email](email.md).

**Ativar Subscrições e seguir**

Os componentes devem ser configurados para habilitar os seguintes componentes do subscrição *e*. Os recursos que permitem o subscrição são [blog](blog-feature.md), [forum](forum.md) e [QnA](working-with-qna.md).

## Subscrições de Seguir {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

O botão **Seguir** fornece um meio de seguir as entradas como atividades, subscrições e/ou notificações. Sempre que o botão **Seguir** for selecionado, é possível ativar ou desativar uma seleção.

Se algum método do seguinte for selecionado, o texto do botão mudará para **Seguindo**. Para conveniência, é possível selecionar `Unfollow All` para desativar todos os métodos.

O botão **Seguir** incluirá a opção `Email Subscriptions` apenas quando um fórum, QnA ou blog estiver configurado para ativar subscrições de e-mail. Este botão será exibido

* Na página principal de recursos do fórum habilitado, QnA ou blog

   * Enviará um email para todas as atividades deste recurso

* Para uma entrada específica, como um tópico do fórum, uma pergunta de QnA ou um artigo do blog

   * Enviará um email quando houver atividade para essa entrada específica

## Responder por email {#reply-by-email}

Quando o email for [configurado para responder por email](email.md#configure-polling-importer), o membro que se inscreveu receberá um email com o conteúdo publicado e um link para o conteúdo online.

Se eles responderem ao email, o conteúdo digitado na resposta será exibido como conteúdo online.

![chlimage_1-6](assets/chlimage_1-6.png)

O tempo necessário para uma resposta ser postada é controlado pelo [intervalo de atualização do importador de pesquisa](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)

