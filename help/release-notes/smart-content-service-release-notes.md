---
title: Notas de versão do Serviço de conteúdo inteligente
seo-title: Notas de versão do Serviço de conteúdo inteligente
description: Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.
seo-description: Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: a842c45f0a0597f4c7f143974a550874258e5382
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 9%

---

# Notas de versão do Serviço de conteúdo inteligente {#smart-content-service-release-notes}

Visão geral do Serviço de conteúdo inteligente e problemas conhecidos do serviço.

As organizações exigem que seus ativos digitais sejam marcados com base na taxonomia que os funcionários, parceiros e clientes usam para consultar e pesquisar ativos digitais. Comparado às tags genéricas, os ativos marcados com base na taxonomia comercial são mais facilmente identificados e recuperados por pesquisas baseadas em tags.

O Serviço de conteúdo inteligente usa a taxonomia comercial do AEM Assets para marcar ativos digitais automaticamente, o que garante que os ativos mais relevantes apareçam em pesquisas.

Você deve treinar o Serviço de conteúdo inteligente em um conjunto preparado de ativos e tags de AEM para reconhecer a taxonomia comercial. Depois de treinado, o serviço pode aplicar essas tags em um conjunto de ativos semelhante.

O Serviço de conteúdo inteligente é alimentado pela plataforma Adobe Sensei, que permite treinar o algoritmo de reconhecimento de imagem em sua taxonomia comercial. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em ativos semelhantes.

## Melhorias de chaves {#key-improvements}

O Serviço de conteúdo inteligente inclui as seguintes melhorias principais:

* Otimizações de algoritmo para melhorar ainda mais a precisão do modelo, recuperar valores
* Suporte para redefinir o treinamento de modelo para todas as tags no nível do locatário
* Suporte para namespaces de Tags inteligentes aprimoradas para evitar conflitos
* Nova política de substituição de modelo para evitar qualquer degradação devido à reciclagem
* Monitoramento em nível de locatário para uso do serviço
* Correções de problemas em cluster e conexão, que aumentam a robustez do serviço

## Problemas corrigidos {#fixed-issues}

Os seguintes problemas foram corrigidos nesta versão:

* Os processos de trabalho de marcação e treinamento terminam se não for possível se conectar ao servidor MySQL. CQ-4242886

* A pontuação preconceituosa de precisão não é calculada corretamente. CQ-4241797

* Cálculo de PR incorreto para o modelo. CQ-4241381

* O fluxo de trabalho de treinamento não usa os ativos de exemplo ao processá-los da fila CQ-4240901

* Melhorias na recuperação de precisão. CQ-4239895

* Política de substituição de modelo. CQ-4239886

* Imagens da camisa masculina são marcadas com a etiqueta da jaqueta feminina. CQ-4239650

* Não há exemplos de treinamento na implantação do estágio. CQ-4239483

* A validação no trabalho de formação deve ocorrer num conjunto de ativos submetidos à formação. CQ-4238834

* A criação de modelo falha para o encaminhamento negativo mesmo se houver positivos/negativos mínimos para uma tag. CQ-4240741

* Entradas enganosas para a procura de alimentos negativos em registros de formadores. CQ-4240738

* Emitir treinamento pela primeira vez se as tags enviadas para treinamento forem negativas aleatórias umas das outras. CQ-4240118

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
* [Documentação de tags inteligentes aprimoradas](/help/assets/enhanced-smart-tags.md)

## Acesso e suporte ao produto (sites restritos) {#product-access-and-support-restricted-sites}

Estes sites estão disponíveis somente para clientes. Se você for um cliente do e precisar de acesso, entre em contato com o gerente de conta do Adobe.

* [Acesso ao produto](https://login.experiencecloud.adobe.com/exc-content/login.html)
* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/).
* Atualizações, patches e pacotes de produtos para funcionalidade adicional em [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Suporte ao cliente via Admin Console](https://adminconsole.adobe.com/). Para obter mais informações, consulte [Nova experiência de Suporte ao Cliente do Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
