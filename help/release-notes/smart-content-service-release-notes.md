---
title: Notas de versão do Smart Content Service
seo-title: Notas de versão do Smart Content Service
description: Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.
seo-description: Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 9%

---


# Notas de versão do Smart Content Service {#smart-content-service-release-notes}

Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.

As organizações exigem que seus ativos digitais sejam marcados com tags com base na taxonomia que os funcionários, parceiros e clientes usam para consultar e pesquisar ativos digitais. Comparados às tags genéricas, os ativos que são marcados com base na taxonomia comercial são mais facilmente identificados e recuperados por pesquisas baseadas em tags.

O Serviço de conteúdo inteligente usa a taxonomia comercial dos AEM Assets para marcar automaticamente os ativos digitais, garantindo que os ativos mais relevantes sejam exibidos nas pesquisas.

Você deve treinar o Serviço de conteúdo inteligente em um conjunto organizado de ativos e tags AEM para reconhecer a taxonomia de sua empresa. Depois de treinado, o serviço pode aplicar essas tags em um conjunto de ativos semelhante.

O Serviço de conteúdo inteligente é acionado pela plataforma Adobe Sensei, que permite que você treine o algoritmo de reconhecimento de imagem na taxonomia de sua empresa. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em ativos semelhantes.

## Melhorias importantes {#key-improvements}

O Serviço de conteúdo inteligente inclui os seguintes aprimoramentos principais:

* Otimizações de algoritmo para melhorar ainda mais a precisão do modelo, recuperar valores
* Suporte para redefinir o treinamento de modelo para todas as tags no nível do locatário
* Suporte para namespaces de Tags inteligentes aprimoradas para evitar conflitos
* Nova política de substituição de modelos para evitar qualquer degradação devido à reciclagem
* Monitoramento em nível de locatário para uso do serviço
* Correções para problemas de cluster e conexão, que aumentam a robustez do serviço

## Problemas corrigidos {#fixed-issues}

Os seguintes problemas foram corrigidos nesta versão:

* Os processos de trabalho para marcação e workflows de treinamento serão encerrados se não for possível se conectar ao servidor MySQL. CQ-4242886

* A pontuação enviesada de precisão não é calculada corretamente. CQ-4241797

* Cálculo de RP incorreto para o modelo. CQ-4241381

* O fluxo de trabalho de treinamento não usa os ativos de exemplo ao processá-los da fila CQ-4240901

* Melhorias na recuperação de precisão. CQ-4239895

* Política de substituição de modelo. CQ-4239886

* Imagens da camisa masculina são marcadas com a etiqueta da jaqueta feminina. CQ-4239650

* A implantação do palco não inclui exemplos de treinamento. CQ-4239483

* A validação no trabalho de formação deve ocorrer num conjunto de ativos submetidos a formação. CQ-4238834

* A criação do modelo falha para a coleta negativa, mesmo se houver mínimo de positivos/negativos presentes em uma tag . CQ-4240741

* Entradas enganosas para criação de alimentos negativos em registros de treinadores. CQ-4240738

* Problema com treinamento pela primeira vez se as tags enviadas para treinamento forem negativas aleatórias umas das outras. CQ-4240118

* Melhora os registros para monitorar o uso do serviço por locatário. CQ-4239781

## Idiomas {#languages}

O Serviço de conteúdo inteligente está disponível para as seguintes localidades:

* Inglês
* Alemão
* Francês
* Espanhol
* Italiano
* Português
* Japonês
* Chinês simplificado
* Coreano

## Links {#links}

* [Página do produto Adobe Experience Manager em adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentação aprimorada de tags inteligentes](/help/assets/enhanced-smart-tags.md)

## Acesso e suporte ao produto (sites restritos) {#product-access-and-support-restricted-sites}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com seu gerente de contas do Adobe.

* [Acesso ao produto](https://login.marketing.adobe.com)
* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/).
* Atualizações, patches e pacotes de produtos para funcionalidade adicional na Distribuição [de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)software.
* [Suporte ao cliente via Admin Console](https://adminconsole.adobe.com/). Para obter mais informações, consulte [Nova experiência](https://docs.adobe.com/content/help/en/customer-one/using/home.html)de suporte ao cliente do Adobe.
