---
title: Componente de comentários de sobreposição
seo-title: Overlay Comments Component
description: Visão geral do componente Comentários de sobreposição
seo-description: Overlay Comments component overview
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---

# Componente de comentários de sobreposição {#overlay-comments-component}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A intenção de [sobreposição](client-customize.md#overlays) um componente padrão é alterar a aparência ou o comportamento de um componente globalmente, para todas as referências relativas ao componente. Ele depende da natureza do sling para resolver para a pasta /apps antes de pesquisar na pasta /libs. Assim, o caminho para o componente é idêntico ao caminho para o componente padrão, exceto que está na pasta /apps e não na pasta /libs.

## Exemplo {#example}

Suponha que você gostaria de modificar o recurso de comentário para que ele corresponda ao design do seu site, alterando o cabeçalho do comentário para que ele não exiba mais o avatar para qualquer comentário. As soluções para ocultar o avatar estão usando o CSS ou, conforme descrito aqui, sobrepondo o header.jsp na pasta de aplicativos para que o HTML contendo o avatar nunca seja enviado ao cliente.

Para sobrepor comentários, você precisará:

1. [Página Comentários](overlay-create-comments-page.md)
1. [Criar nós](overlay-create-nodes.md)
1. [Alterar a aparência](overlay-alter-appearance.md)
