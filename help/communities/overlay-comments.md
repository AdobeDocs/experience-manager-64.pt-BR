---
title: Componente Comentários da sobreposição
seo-title: Componente Comentários da sobreposição
description: Visão geral do componente Comentários da sobreposição
seo-description: Visão geral do componente Comentários da sobreposição
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Componente Comentários da sobreposição {#overlay-comments-component}

A intenção de [sobrepor](client-customize.md#overlays) um componente padrão é alterar a aparência ou o comportamento de um componente globalmente, para todas as referências relativas ao componente. Ele depende da natureza do sling para resolver a pasta /apps antes de pesquisar na pasta /libs. Assim, o caminho para o componente é idêntico ao caminho para o componente padrão, exceto que está na pasta /apps e não na pasta /libs.

## Exemplo {#example}

Suponha que você queira modificar o recurso de comentário para que ele corresponda ao design do seu site, alterando o cabeçalho do comentário para que ele não exiba mais o avatar para qualquer comentário. As soluções para ocultar o avatar estão usando o CSS ou, conforme descrito aqui, sobrepondo o header.jsp na pasta de aplicativos para que o HTML que contém o avatar nunca seja enviado para o cliente.

Para sobrepor comentários, você precisará:

1. [Página de comentários](overlay-create-comments-page.md)
1. [Criar nós](overlay-create-nodes.md)
1. [Alterar a aparência](overlay-alter-appearance.md)

