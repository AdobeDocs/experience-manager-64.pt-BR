---
title: Componente Estender comentários
seo-title: Extend Comments Component
description: Estender o componente Comentários para alterar sua aparência ou comportamento para usos específicos
seo-description: Extend the Comments component to alter its appearance or behavior for specific uses
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
exl-id: f6722953-ff71-4fba-b76e-1d566f71f6d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---

# Componente Estender comentários {#extend-comments-component}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A intenção de [extensão](client-customize.md#extensions) um componente padrão é alterar a aparência ou o comportamento de um componente para usos específicos.

O caminho para o componente é exclusivo e faz referência ao componente padrão como um tipo de super recurso. Há menos risco, pois o escopo é limitado em comparação ao escopo global de uma sobreposição de componente.

>[!NOTE]
>
>Extensão de um [sobreposto](client-customize.md#overlays) não é suportado.

## Exemplo {#example}

Suponha que o cabeçalho do componente de comentário deve ser exibido com uma aparência alternativa em um site da instância de AEM, enquanto aparece com a exibição padrão em outro site. Em vez de sobrepor o comentário padrão, que altera o componente de comentário para todas as instâncias, uma solução melhor é garantir que haja vários componentes de comentário disponíveis para uso em vários sites.

Para implementar essa solução, crie um novo componente que estenda (substitui) o existente e modifique o script Handlebars. A área do site que usa os novos comentários pode usar a extensão, enquanto os sites que usam a aparência padrão permanecem inalterados.

O componente comentário é, na verdade, um dos dois componentes que compõem o sistema de comentários. Dessa forma, há dois componentes a serem estendidos: *comentários* e *comentário*. O script a ser editado está no *comentário *componente `header.hbs` enquanto o pai *comentários* componente (o sistema de comentários) é o que um autor realmente adiciona à página.

Para estender comentários, você precisará:

1. [Criar os componentes](extend-create-components.md)
1. [Adicionar comentário à página de exemplo](extend-sample-page.md)
1. [Alterar a aparência](extend-alter-appearance.md)
