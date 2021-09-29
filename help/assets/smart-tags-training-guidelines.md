---
title: Diretrizes de treinamento do Serviço de conteúdo inteligente
description: Treinar o serviço de IA para aplicar tags inteligentes a ativos
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 12%

---

# Diretrizes de treinamento do Serviço de conteúdo inteligente {#smart-content-service-training-guidelines}

Para marcar as imagens de sua marca com eficácia, o Serviço de conteúdo inteligente exige que as imagens de treinamento estejam em conformidade com determinadas diretrizes.

## Orientações para a formação {#guidelines-for-training}

Para obter melhores resultados, as imagens em seu conjunto de treinamento devem estar em conformidade com as seguintes diretrizes:

**Quantidade e tamanho:****mínimo de 30 imagens por tag**. Mínimo de 500 pixels no lado maior.

**Coerência**: As imagens de uma tag devem ser visualmente semelhantes.

Por exemplo, não é uma boa ideia marcar todas essas imagens como *my-party* (para treinamento) porque elas não são visualmente semelhantes.

![Imagens ilustrativas para exemplificar as diretrizes de treinamento](assets/do-not-localize/coherence.png)

**Cobertura**: As imagens da formação devem ser suficientemente variadas. A ideia é fornecer alguns exemplos, mas razoavelmente diversos, para que [!DNL Experience Manager] aprenda a se concentrar nas coisas certas. Se você estiver aplicando a mesma tag em imagens visualmente diferentes, inclua pelo menos cinco exemplos de cada tipo.

Por exemplo, para a tag *model-down*, inclua mais imagens de treinamento semelhantes à imagem realçada abaixo para que o serviço identifique imagens semelhantes com mais precisão durante a marcação.

![Imagens ilustrativas para exemplificar as diretrizes de treinamento](assets/do-not-localize/coverage_1.png)

**Desvio/obstrução**: O serviço se concentra melhor em imagens com menos distração (planos de fundo proeminentes, acompanhamento não relacionado, como objetos/pessoas com o assunto principal).

Por exemplo, para a tag *casual-shoe*, a segunda imagem não é um bom candidato a treinamento.

![Imagens ilustrativas para exemplificar as diretrizes de treinamento](assets/do-not-localize/distraction.png)

**Integridade:** se uma imagem se qualificar para mais de uma tag, adicione todas as tags aplicáveis antes de incluir a imagem para treinamento. Por exemplo, para tags, como *capa de chuva* e *perfil de modelo*, adicione ambas as tags ao ativo elegível antes de incluí-lo para treinamento.

![Imagens ilustrativas para exemplificar as diretrizes de treinamento](assets/do-not-localize/completeness.png)

## Limitações           {#limitations}

As tags inteligentes aprimoradas são baseadas no aprendizado de modelos de imagens de marca e suas tags. Esses modelos nem sempre são perfeitos na identificação de tags. A versão atual do Serviço de conteúdo inteligente tem as seguintes limitações:

* Incapacidade de reconhecer sutis diferenças em imagens. Por exemplo, camisas finas versus camisas fixas regulares.
* Incapacidade de identificar tags com base em pequenos padrões/partes de uma imagem. Por exemplo, logotipos em T-shirts.
* A marcação é suportada nas localidades nas quais [!DNL Experience Manager] é suportado. Para obter uma lista de idiomas, consulte as [Notas de versão dos Serviços de Conteúdo Inteligente](/help/release-notes/smart-content-service-release-notes.md).

Para pesquisar ativos com tags inteligentes (regulares ou aprimoradas), use a Pesquisa Omni de ativos (pesquisa de texto completo). Não há predicado de pesquisa separado para tags inteligentes.

>[!NOTE]
>
>A capacidade do Serviço de conteúdo inteligente de treinar em suas tags e aplicá-las em outras imagens depende da qualidade das imagens usadas no treinamento.
>
>Para obter melhores resultados, o Adobe recomenda o uso de imagens visualmente semelhantes para treinar o serviço para cada tag.
