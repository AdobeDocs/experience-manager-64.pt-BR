---
title: Uso de classificações
seo-title: Using Ratings
description: Adicionar um componente de Classificação a uma página
seo-description: Adding a Rating component to a page
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
exl-id: 1de28140-5334-4ca2-a476-5ad253809808
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 4%

---

# Uso de classificações {#using-ratings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O `Rating`é usado de forma independente ou em conjunto com outros recursos das Comunidades. Esse componente permite que os membros da comunidade que fizeram logon expressem suas opiniões por meio da classificação do conteúdo.

## Adicionar uma classificação a uma página {#adding-a-rating-to-a-page}

Para adicionar uma `Rating`para uma página no modo autor, localize o componente `Communities / Rating` e arraste-a para o local em uma página, como uma posição relativa ao recurso para os membros classificarem.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](rating-basics.md#essentials-for-client-side) são incluídos, é assim que a variável `Rating` será exibido.

![chlimage_1-493](assets/chlimage_1-493.png)

## Configuração da classificação {#configuring-rating}

Selecione o `Rating` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-494](assets/chlimage_1-494.png)

Em **[!UICONTROL Textos e rótulos]** você especifica o identificador interno para a Classificação.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Nome da Tally]**
(*Obrigatório*) Um nome simples para a variável `Rating`que identifica exclusivamente esta instância. Deve ser um nome de nó válido para o repositório.

## Experiência de visitante do site {#site-visitor-experience}

### Membros {#members}

Só é permitida uma classificação por membro. O membro pode alterar a sua notação a qualquer momento.

### Anônimo {#anonymous}

A publicação anônima de uma classificação não é suportada. Os visitantes do site devem se registrar (se tornar um membro) e fazer logon para participar.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Princípios básicos de classificação](rating-basics.md) página para desenvolvedores.
