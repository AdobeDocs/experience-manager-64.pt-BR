---
title: Criação de ajuda no contexto para campos de formulário
seo-title: Authoring in-context help for form fields
description: O AEM Forms permite adicionar ajuda em contexto a campos e painéis de formulário adaptáveis, como texto ou mídia avançada, incluindo vídeos.
seo-description: AEM Forms allows you to add in-context help to adaptive form fields and panels, as text or rich media, including videos.
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
feature: Adaptive Forms
exl-id: 0c761c0c-fbe4-4129-8a90-c4ef1127a762
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 3%

---

# Criação de ajuda no contexto para campos de formulário {#authoring-in-context-help-for-form-fields}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

Há situações em que os usuários finais que preenchem um formulário não têm certeza de como preencher os detalhes em um campo de formulário específico. Para resolver esses problemas, os formulários adaptáveis fornecem suporte para adicionar texto ou ajuda rich in-context a um campo de formulário. Ajuda a melhorar a experiência de preenchimento do formulário e evita qualquer ambiguidade para os usuários finais.

Este artigo discute como os autores de formulários podem adicionar ajuda no contexto durante a criação do Adaptive Forms.

## Adicionar ajuda no contexto {#add-in-context-help}

Você pode especificar a ajuda no contexto usando as seguintes opções na seção Conteúdo da Ajuda da guia propriedades na barra lateral.

* [Descrição curta](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [Descrição longa](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![Ajuda no contexto para campos de formulário](assets/descriptions.png)

>[!NOTE]
>
>Descrição longa substitui a Descrição curta. Se você especificou ambos, somente Descrição longa será exibida.

### Descrição curta {#short-description}

O campo Short description é destinado a fornecer dicas rápidas e curtas sobre o preenchimento de um campo de formulário. O texto especificado no campo Short description é exibido como uma dica de ferramenta ao passar o mouse sobre o campo.

![Descrição curta para adicionar ajuda no contexto para campos de formulário](assets/tooltip.png)

>[!NOTE]
>
>Selecionar **Sempre mostrar descrição curta** para exibir permanentemente o texto de ajuda abaixo do campo.

![Ajuda permanente curta no contexto abaixo do campo](assets/short1.png)

### Descrição longa {#long-description}

Você pode usar o campo Long description para especificar texto longo ou incorporar conteúdo de mídia avançada, incluindo vídeos, como ajuda de contexto. Por exemplo, a imagem a seguir mostra como você pode incorporar um vídeo como ajuda de contexto.

![Adicionar mídia avançada como ajuda no contexto para campos de formulário](assets/long-descriptions.png)

Adicionar descrição longa exibe uma **?** ícone ao lado do campo . Clicar no ícone exibe o conteúdo adicionado na seção de descrição longa.

![Exemplo de ajuda em contexto da mídia avançada](assets/photoshop.png)

### Ajuda no nível do painel {#panel-level-help}

Além da ajuda em contexto para campos de formulário, você pode especificar a ajuda em um nível de painel na guia Conteúdo da Ajuda da caixa de diálogo Editar painel.

![Adicionar ajuda no contexto para um painel de formulário](assets/panel-level-help.png)

A adição de ajuda para o painel exibe uma **?** ícone ao lado da descrição do painel. Clicar no ícone exibe o conteúdo adicionado na seção Conteúdo da Ajuda da caixa de diálogo de edição do painel.

![Exemplo de ajuda no contexto no nível do painel de formulário](assets/photoshop-1.png)
