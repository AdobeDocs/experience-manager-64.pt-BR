---
title: Uso do Gráfico Social
seo-title: Using Social Graph
description: Adicionar um componente a seguir a uma página
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# Uso do Gráfico Social {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

A capacidade de um membro da comunidade seguir [atividades](activities.md) e a seguir é estabelecida através de duas componentes: `Follow`e `Following`.

O `Follow`deve ser associado a outro recurso, e essa associação já está estabelecida para membros e recursos da comunidade.

O `Following`simplesmente lista os membros que estão seguindo o membro atual ou que estão sendo seguidos pelo membro atual. Esse gráfico social das relações entre membros está incluído no perfil de usuário estabelecido para um [site da comunidade](overview.md#communitiessites).

## Adicionar o seguinte a uma página {#adding-following-to-a-page}

Se desejar adicionar uma `Following`para uma página no modo autor, localize o componente `Communities / Following` e arraste-o para o lugar em uma página onde o gráfico social deve aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](essentials-socialgraph.md#essentials-for-client-side) são incluídos, é assim que a variável `Following` componente será exibido:

![chlimage_1-447](assets/chlimage_1-447.png)

## Configurar a seguir {#configuring-following}

Atualmente, é necessário definir a propriedade para determinar se o componente exibe a variável `follows`ou a `following`relação.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos do gráfico social](essentials-socialgraph.md) página para desenvolvedores.
