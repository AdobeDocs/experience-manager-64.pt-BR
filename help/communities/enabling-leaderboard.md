---
title: Recurso de quadro de líderes
seo-title: Leaderboard Feature
description: Adicionar um componente de Quadro de líderes a uma página
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 8%

---

# Recurso de quadro de líderes {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O `Leaderboard` fornece a capacidade de obter uma noção de como os membros estão interagindo dentro da comunidade por meio da classificação de membros de acordo com os pontos obtidos (pontuação básica) ou seu conhecimento (pontuação avançada).

Antes de incluir o componente de quadro de liderança em uma página, é necessário configurar [Pontuação e emblemas de comunidades](implementing-scoring.md).

Esta seção da documentação descreve

* Adicionar a `Leaderboard` para um [site da comunidade](overview.md#community-sites)

* Configurações para o `Leaderboard` componente

## Adicionar um Quadro de líderes a uma página {#adding-a-leaderboard-to-a-page}

Para adicionar uma `Leaderboard` para uma página no modo autor, localize o componente

* `Communities / Leaderboard`

e arraste-a para o local em uma página.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando colocado pela primeira vez em uma página de um site da comunidade, é assim que o componente aparece:

![chlimage_1-8](assets/chlimage_1-8.png)

## Configuração do Quadro de Liderança {#configuring-leaderboard}

Selecione o `Leaderboard` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique quais informações relacionadas ao membro são exibidas:

* **[!UICONTROL Nome de exibição]**
Um nome descritivo a ser exibido para o quadro, refletindo as regras selecionadas para a exibição de emblemas e pontuações.

   O padrão é `Leaderboard`, se nada tiver sido inserido.

* **[!UICONTROL Símbolo]**
Se marcada, uma coluna para ícones de selo é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Nome do selo]**
Se marcada, uma coluna para o nome do símbolo é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Usar Avatar]**
Se marcada, a imagem de avatar do membro é incluída no quadro de líderes, ao lado de seu link de nome para seu perfil de membro.

   O padrão está desmarcado.

### Guia Regras {#rules-tab}

Em **[!UICONTROL Regras]** guia, o site da comunidade e suas regras de pontuação e marcação

* **[!UICONTROL Localização da regra]**
(obrigatório) Local onde a regra de Pontuação/Aviso de falha está configurada.

* **[!UICONTROL Regra de pontuação]**
(obrigatório) Regra específica que gera as pontuações a serem exibidas.

* **[!UICONTROL Regra de marcação]**
(obrigatório) Regra específica que gera o símbolo a ser exibido.

* **[!UICONTROL Limite de exibição]**
Número de membros a serem exibidos por página.

   O padrão é 10.

## Exemplo: Quadro de líderes dos participantes {#example-participants-leaderboard}

Este relatório do painel de líderes resulta da aplicação de regras básicas de pontuação.

Configuração do componente do Quadro de líderes:

* **[!UICONTROL Configurações]** guia :

   * Nome de exibição = `Participation Board`
   * `checked`:

      * Insígnia
      * Nome da insígnia
      * Usar Avatar

* **[!UICONTROL Regras]** guia :

   * Local da regra = `/content/sites/communities/jcr:content`
   * Regra de pontuação = `/etc/community/scoring/rules/forums-scoring`
   * Regra para insígnias = `/etc/community/badging/rules/reference-badging`
   * Limite de exibição = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Exemplo: Quadro de líderes de especialistas {#example-experts-leaderboard}

Esse relatório de painel resulta da aplicação de regras de pontuação avançadas.

Configuração do componente do Quadro de líderes:

* **[!UICONTROL Configurações]** guia :

   * Nome de exibição = `Expertise Board`
   * `checked`:

      * Insígnia
      * Usar Avatar

* **[!UICONTROL Regras]** guia :

   * Local da regra = `/content/sites/communities/jcr:content`
   * Regra de pontuação = `/etc/community/scoring/rules/adv-forums-scoring`
   * Regra para insígnias = `/etc/community/badging/rules/adv-forums-badging`
   * Limite de exibição = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Princípios básicos do painel de líderes](leaderboard.md) página para desenvolvedores.

As instruções para a criação de regras são fornecidas no [Pontuação e emblemas de comunidades](implementing-scoring.md) página para administradores.
