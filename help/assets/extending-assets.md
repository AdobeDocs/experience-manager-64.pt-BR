---
title: Personalização e extensão de ativos
description: Saiba como personalizar e estender o Asset Share e o Editor de ativos, que apresenta aos usuários uma interface especificamente personalizada e um conjunto de funcionalidades.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Personalização e extensão de ativos {#customizing-and-extending-assets}

O Editor de ativos é o principal ponto de acesso que os usuários de um site do Adobe Enterprise Manager (AEM) usarão para localizar, visualização e manipular os ativos digitais no repositório.

Como um desenvolvedor AEM, você pode personalizar e estender o Editor de ativos de várias maneiras, apresentando aos usuários uma interface especificamente personalizada e um conjunto de funcionalidades.

Os seguintes aspectos da funcionalidade podem ser personalizados ou aprimorados:

* [Extensão do Editor de ativos](asseteditorx.md)
* [Estendendo a pesquisa de ativos](searchx.md)
* [Processando ativos usando manipuladores de mídia e fluxos de trabalho](media-handlers.md)
* [Integração de ativos com o fluxo de atividade](extending-activity-stream.md)
* [Desenvolvimento de proxy de ativos](proxy.md)
* [Práticas recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md)

## Personalização da aparência {#customizing-the-look-and-feel}

Os seguintes aspectos da aparência do Editor de ativos são personalizáveis:

* Logotipo: Você pode adicionar o logotipo de sua própria organização à interface.
* Cores e fontes: É possível alterar as cores e as fontes usadas na interface.
* Código HTML: Para uma personalização mais completa, é possível alterar o código HTML subjacente que define as interfaces.

## Personalizar representações {#customizing-renditions}

Na terminologia do AEM Assets, uma representação é a forma na qual um ativo é apresentado. Em geral, um ativo específico pode ter várias representações. Por exemplo, imagens em cores completas podem ter uma representação em seu tamanho original, outra em tamanho reduzido e outra em escala decrescente e outra em escala de cinza.

As representações nas quais um ativo específico está disponível podem ser personalizadas e novas representações podem ser criadas.
