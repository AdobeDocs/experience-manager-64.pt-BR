---
title: Recurso de quadro de líderes
seo-title: Recurso de quadro de líderes
description: Adicionar um componente de Quadro de líderes a uma página
seo-description: Adicionar um componente de Quadro de líderes a uma página
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 6%

---


# Recurso do Quadro de líderes {#leaderboard-feature}

## Introdução {#introduction}

O componente `Leaderboard` fornece a capacidade de obter uma noção de como os membros estão interagindo dentro da comunidade classificando os membros de acordo com os pontos ganhos (pontuação básica) ou sua experiência (pontuação avançada).

Antes de incluir o componente de quadro de líderes em uma página, é necessário configurar [Pontuação e emblemas das comunidades](implementing-scoring.md).

Esta seção da documentação descreve

* Adicionar o componente `Leaderboard` a um [site da comunidade](overview.md#community-sites)

* Configurações do componente `Leaderboard`

## Adicionar um Quadro de líderes a uma Página {#adding-a-leaderboard-to-a-page}

Para adicionar um componente `Leaderboard` a uma página no modo de autor, localize o componente

* `Communities / Leaderboard`

e arraste-o para o lugar em uma página.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando colocado pela primeira vez em uma página de um site da comunidade, é assim que o componente aparece:

![chlimage_1-8](assets/chlimage_1-8.png)

## Configurando o Quadro de líderes {#configuring-leaderboard}

Selecione o componente `Leaderboard` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Settings]**, especifique as informações relacionadas ao membro que são exibidas:

* **[!UICONTROL Nome para exibiçãoUm nome descritivo a ser exibido para o quadro, refletindo as regras selecionadas para exibição de símbolos e pontuações.]**


   O padrão é `Leaderboard`, se nada for inserido.

* ****
BadgeSe marcada, uma coluna para ícones de crachá é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Nome do]**
seloSe marcada, uma coluna para o nome do crachá é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Usar]**
AvatarSe marcada, a imagem de avatar do membro será incluída no quadro de líderes, ao lado do link do nome para o perfil do membro.

   O padrão está desmarcado.

### Guia Regras {#rules-tab}

Na guia **[!UICONTROL Regras]**, o site da comunidade e suas regras de pontuação e marcação

* **[!UICONTROL Localização]**
 da regra (obrigatório) Local onde a regra de Pontuação/Classificação está configurada.

* **[!UICONTROL Regra]**
 de Pontuação (obrigatório) Regra específica que gera as pontuações a serem exibidas.

* **[!UICONTROL Regra]**
 de identificação (obrigatório) Regra específica que gera o crachá a ser exibido.

* **[!UICONTROL Exibir]**
limiteNúmero de membros a serem exibidos por página.

   O padrão é 10.

## Exemplo: Painel de líderes dos participantes {#example-participants-leaderboard}

Este quadro de líderes informa os resultados da aplicação de regras básicas de pontuação.

Configuração do componente de quadro de líderes:

* **[!UICONTROL Guia]** de configuração:

   * Nome para exibição = `Participation Board`
   * `checked`:

      * Insígnia
      * Nome da insígnia
      * Usar avatar

* **** Regras:

   * Local da regra = `/content/sites/communities/jcr:content`
   * Regra de pontuação = `/etc/community/scoring/rules/forums-scoring`
   * Regra para insígnias = `/etc/community/badging/rules/reference-badging`
   * Limite de exibição = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Exemplo: Painel de líderes de especialistas {#example-experts-leaderboard}

Esse relatório de quadro de líderes resulta da aplicação de regras de pontuação avançadas.

Configuração do componente de quadro de líderes:

* **[!UICONTROL Guia]** de configuração:

   * Nome para exibição = `Expertise Board`
   * `checked`:

      * Insígnia
      * Usar avatar

* **** Regras:

   * Local da regra = `/content/sites/communities/jcr:content`
   * Regra de pontuação = `/etc/community/scoring/rules/adv-forums-scoring`
   * Regra para insígnias = `/etc/community/badging/rules/adv-forums-badging`
   * Limite de exibição = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Principais componentes do Quadro de líderes](leaderboard.md) para desenvolvedores.

As instruções para a criação de regras são fornecidas na página [Pontuação de comunidades e emblemas](implementing-scoring.md) para administradores.
