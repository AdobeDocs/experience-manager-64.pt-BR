---
title: Usar curtir
seo-title: Using Liking
description: Adicionar e configurar o componente de vinculação
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 7%

---

# Usar curtir {#using-liking}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O `Liking`é uma ferramenta útil que permite que os usuários expressem uma opinião sobre um conteúdo específico, como um comentário em um fórum. Com o `Liking`, os membros selecionam o ícone do coração para indicar uma opinião positiva.

## Adicionar curtir a uma página {#adding-liking-to-a-page}

Para adicionar uma `Liking` para uma página no modo autor, use o navegador de componentes para localizar

* `Communities / Liking`

e arraste-a para o local em uma página, como uma posição relativa ao recurso que os usuários desejam.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](essentials-liking.md#essentials-for-client-side) são incluídos, é assim que a variável `Liking` será exibido.

![chlimage_1-93](assets/chlimage_1-93.png)

## Configuração de curtir {#configuring-liking}

Selecione o `Liking` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-94](assets/chlimage_1-94.png)

Em **[!UICONTROL Textos e rótulos]** , especifique as propriedades usadas para registrar curtidas.

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

## Experiência de visitante do site {#site-visitor-experience}

### Membros {#members}

Os deputados podem alterar a sua posição a qualquer momento.

### Anônimo {#anonymous}

A ligação anônima não é suportada. Os visitantes do site devem se registrar (se tornar um membro) e fazer logon para participar do curtidas.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Noções básicas sobre curtir](essentials-liking.md) página para desenvolvedores.
