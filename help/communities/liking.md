---
title: Como usar curtidas
seo-title: Como usar curtidas
description: Adicionar e configurar o componente de curtir
seo-description: Adicionar e configurar o componente de curtir
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
translation-type: tm+mt
source-git-commit: f78f83ef3b9373bcbee3e5179a9bbec4d9462255
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---


# Usando curtir {#using-liking}

O componente `Liking`é uma ferramenta útil que permite aos usuários expressar uma opinião sobre um conteúdo específico, como um comentário em um fórum. Com o componente `Liking`, os membros selecionam o ícone de coração para indicar uma opinião positiva.

## Adicionar curtir a uma página {#adding-liking-to-a-page}

Para adicionar um componente `Liking` a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Liking`

e arraste-o para o lugar em uma página, como uma posição relativa ao recurso que os usuários desejam.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](essentials-liking.md#essentials-for-client-side) forem incluídas, o componente `Liking` aparecerá desta forma.

![chlimage_1-93](assets/chlimage_1-93.png)

## Configuração de curtir {#configuring-liking}

Selecione o componente `Liking` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-94](assets/chlimage_1-94.png)

Na guia **[!UICONTROL Textos e etiquetas]**, especifique as propriedades usadas para registrar curtidas.

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL Rótulo de resposta positiva]**
(
*Obrigatório*) O nome da propriedade para uma resposta positiva.

* **[!UICONTROL Etiqueta de resposta negativa]**
(
*Obrigatório*) O nome da propriedade para uma resposta negativa.

* **[!UICONTROL Nome Tally]**
(
*Obrigatório*) O nome de propriedade interno e identificável para esta instância de um componente de votação.

## Experiência de Visitante do site {#site-visitor-experience}

### Membros {#members}

Os deputados podem mudar de opinião a qualquer momento.

### Anônimo {#anonymous}

Gostos anônimos não são suportados. Os visitantes do site devem se registrar (tornar-se um membro) e fazer logon para participar do curtidas.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Curtir o Essentials](essentials-liking.md) para desenvolvedores.
