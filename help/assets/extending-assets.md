---
title: Personalização e extensão de ativos
description: Saiba como personalizar e estender o Compartilhamento de ativos e o Editor de ativos, que apresenta aos usuários uma interface e um conjunto de funcionalidades especificamente personalizados.
contentOwner: AG
feature: Ferramentas do desenvolvedor
role: Desenvolvedor
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---


# Personalização e extensão de ativos {#customizing-and-extending-assets}

O Editor de ativos é o principal ponto de acesso que os usuários de um site do Adobe Enterprise Manager (AEM) usarão para localizar, exibir e manipular os ativos digitais em seu repositório.

Como desenvolvedor de AEM, você pode personalizar e estender o Editor de ativos de várias maneiras, apresentando aos usuários uma interface especificamente personalizada e um conjunto de funcionalidades.

Os seguintes aspectos da funcionalidade podem ser personalizados ou aprimorados:

* [Extensão do Editor de ativos](asseteditorx.md)
* [Extensão da pesquisa de ativos](searchx.md)
* [Processamento de ativos usando manipuladores de mídia e fluxos de trabalho](media-handlers.md)
* [Integração de ativos ao fluxo de atividade](extending-activity-stream.md)
* [Desenvolvimento de proxy de ativos](proxy.md)
* [Práticas recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md)

## Personalização da aparência {#customizing-the-look-and-feel}

Os seguintes aspectos da aparência do Editor de ativos são personalizáveis:

* Logotipo: Você pode adicionar o logotipo de sua própria organização à interface.
* Cores e fontes: Você pode alterar as cores e as fontes usadas na interface.
* Código HTML: Para uma personalização mais completa, você pode alterar o código HTML subjacente que define as interfaces.

## Personalizar representações {#customizing-renditions}

Na terminologia do AEM Assets, uma representação é o formulário no qual um ativo é apresentado. Em geral, um ativo específico pode ter várias representações. Por exemplo, imagens de cores completas podem ter uma representação em seu tamanho original, outra em um tamanho reduzido e outra que é dimensionada para baixo e convertida em escala de cinza.

As representações em que um ativo específico está disponível podem ser personalizadas e novas representações podem ser criadas.
