---
title: Uso da votação
seo-title: Uso da votação
description: Adicionar o componente de Votação a uma página
seo-description: Adicionar o componente de Votação a uma página
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---


# Usando Voting {#using-voting}

O componente `Voting` é uma ferramenta útil que permite que os membros da comunidade classifiquem um conteúdo específico, como uma resposta em um componente QnA. Com o componente `Voting`, os membros selecionam setas para cima ou para baixo para indicar sua opinião.

## Adicionar votação a uma página {#adding-voting-to-a-page}

Para adicionar um componente `Voting` a uma página no modo de autor, use o navegador de componentes para localizar `Communities / Voting` e arraste-o para o lugar em uma página, como uma posição relativa ao recurso no qual os usuários votam.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](essentials-voting.md#essentials-for-client-side) forem incluídas, o componente `Voting` aparecerá desta forma.

![chlimage_1-307](assets/chlimage_1-307.png)

## Configurando a votação {#configuring-voting}

Selecione o componente `Voting` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-308](assets/chlimage_1-308.png)

Na guia **[!UICONTROL Textos e etiquetas]**, especifique as propriedades usadas para registrar votos.

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL Rótulo de resposta positiva]**
(
*Obrigatório*) O nome da propriedade interna para uma resposta positiva.

* **[!UICONTROL Etiqueta de resposta negativa]**
(
*Obrigatório*) O nome da propriedade interna para uma resposta negativa.

* **[!UICONTROL Nome Tally]**
(
*Obrigatório*) O nome de propriedade interno e identificável para esta instância de um componente de votação.

## Experiência de Visitante do site {#site-visitor-experience}

### Membros {#members}

Os deputados só podem votar uma vez, mas podem alterar a sua votação em qualquer altura.

### Anônimo {#anonymous}

Voto anônimo não é apoiado. Os visitantes do site devem se registrar (tornar-se membros) e fazer logon para participar da votação uma vez.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Noting Essentials](essentials-voting.md) para desenvolvedores.
