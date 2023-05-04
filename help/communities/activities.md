---
title: Recurso Fluxos de atividade
seo-title: Activity Streams Feature
description: Atividades de um membro da comunidade com sessão iniciada
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Recurso Fluxos de atividade {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

As atividades de um membro da comunidade assinado, como postar em um fórum ou blog, são coletadas em um fluxo que pode ser filtrado e exibido de várias maneiras pela configuração do `Activity Streams` componente.

A capacidade de seguir adiciona outra exibição de atividades quando os membros da comunidade seguem postagens de interesse ou seguem as atividades de outros membros da comunidade.

Esta seção da documentação descreve

* Adicionar o componente Fluxos de atividade a um site AEM
* Configurações do componente Fluxos de atividade

## Adicionar fluxos de atividade a uma página {#adding-activity-streams-to-a-page}

Se desejar adicionar uma `Activity Streams` para uma página no modo autor, use o navegador de componentes para localizar

* `Communities / Activity Streams`

e arraste-o para o lugar em uma página onde os fluxos de atividade devem aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](essentials-activities.md#essentials-for-client-side) são incluídos, é assim que a variável `Activity Streams` componente será exibido:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuração de fluxos de atividade {#configuring-activity-streams}

Selecione o `Activity Streams` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-196](assets/chlimage_1-196.png)

Em **[!UICONTROL Atividades do usuário]** , especifique quais atividades exibir:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Número máximo de atividades]**
O número de atividades a serem exibidas
* **[!UICONTROL Caminho do recurso de fluxo]**
Deixe em branco como padrão para o site da comunidade ou grupo da comunidade. O caminho do recurso de fluxo identifica a origem das atividades. O padrão está em branco.
* **[!UICONTROL Exibir exibição de atividades do usuário]**
se marcada, a página de atividades incluirá uma guia que filtra as atividades com base nas geradas na comunidade pelo membro atual. O padrão está marcado.
* **[!UICONTROL Exibir visualização de todas as atividades]**
Se marcada, a página de atividades incluirá uma guia que inclui todas as atividades geradas na comunidade às quais o membro atual tem acesso. O padrão está marcado.
* **[!UICONTROL Exibir a seguinte exibição]**
Se marcada, a página de atividades incluirá uma guia que filtra as atividades com base nas atividades que o membro atual está seguindo. O padrão está marcado.

## Seguinte exibição {#following-view}

Os componentes devem ser configurados para ativar o seguinte. Os recursos que permitem o seguinte são [blog](blog-feature.md), [fórum](forum.md), [QnA](working-with-qna.md), [calendário](calendar.md), [filelibrary](file-library.md)e [comentários](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

O **Seguir** fornece um meio de seguir entradas como atividades, [notificações](notifications.md)e/ou [assinaturas](subscriptions.md). Sempre que a variável **Seguir** for selecionado, é possível ativar ou desativar uma seleção. O `Email Subscriptions` A seleção só está presente quando configurada.

Se qualquer método de seguir for selecionado, o texto do botão será alterado para **Seguindo**. Para maior comodidade, é possível selecionar `Unfollow All` para desativar todos os métodos.

O **Seguir** será exibido:

* Ao visualizar o perfil de outro membro
* Em uma página principal do recurso, como fóruns, QnA e blogs
   * Segue todas as atividades para esse recurso geral

* Para uma entrada específica, como um tópico de fórum, pergunta de QnA ou artigo de blog
   * Segue todas as atividades para essa entrada específica

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos dos fluxos de atividade](essentials-activities.md) página para desenvolvedores.
