---
title: Recurso de transmissão de atividades
seo-title: Recurso de transmissão de atividades
description: Atividades de um membro da comunidade com sessão iniciada
seo-description: Atividades de um membro da comunidade com sessão iniciada
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c

---


# Recurso de transmissão de atividades {#activity-streams-feature}

## Introdução {#introduction}

As atividades de um membro da comunidade conectado, como postar em um fórum ou blog, são coletadas em um fluxo que pode ser filtrado e exibido de várias maneiras pela configuração do `Activity Streams` componente.

A capacidade de seguir adiciona outra visão das atividades quando os membros da comunidade seguem postagens de interesse ou atividades de outros membros da comunidade.

Esta seção da documentação descreve

* Adicionar o componente de Fluxos de atividade a um site do AEM
* Configurações do componente de Fluxos de atividade

## Adicionar fluxos de atividade a uma página {#adding-activity-streams-to-a-page}

Se desejar adicionar um `Activity Streams` componente a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Activity Streams`

e arraste-o para o lugar em uma página onde os fluxos de atividade devem aparecer.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando as bibliotecas [do lado do cliente](essentials-activities.md#essentials-for-client-side) necessárias forem incluídas, o `Activity Streams` componente será exibido desta forma:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configuração de fluxos de atividade {#configuring-activity-streams}

Selecione o componente inserido a ser acessado e selecione o `Activity Streams` `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-196](assets/chlimage_1-196.png)

Na guia Atividades **[!UICONTROL do]** usuário, especifique as atividades a serem exibidas:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Número máximo de atividades]** O número de atividades a serem exibidas
* **[!UICONTROL Caminho]** do recurso de fluxo Deixe em branco para o padrão do site da comunidade ou do grupo da comunidade. O caminho do recurso de fluxo identifica a origem das atividades. O padrão está em branco.
* **[!UICONTROL Exibir visualização]** de atividades do usuário se marcada, a página de atividades incluirá uma guia que filtra as atividades com base nas geradas na comunidade pelo membro atual. O padrão está marcado.
* **[!UICONTROL Exibir visualização]** de todas as atividades Se marcada, a página de atividades incluirá uma guia que inclui todas as atividades geradas na comunidade às quais o membro atual tem acesso. O padrão está marcado.
* **[!UICONTROL Exibir seguinte exibição]** Se marcada, a página de atividades incluirá uma guia que filtra as atividades com base nas atividades que o membro atual está seguindo. O padrão está marcado.

## Exibição Seguinte {#following-view}

Os componentes devem ser configurados para permitir o seguinte. Os recursos que permitem o seguinte são [blog](blog-feature.md), [fórum](forum.md), [QnA](working-with-qna.md), [calendário](calendar.md), [biblioteca](file-library.md)[](comments.md)e comentários.

![chlimage_1-198](assets/chlimage_1-198.png)

O botão **Seguir** fornece um meio de seguir entradas como atividades, [notificações](notifications.md)e/ou [assinaturas](subscriptions.md). Sempre que o botão **Seguir** é selecionado, é possível ativar ou desativar uma seleção. A `Email Subscriptions` seleção só está presente quando configurada.

Se algum método de seguir for selecionado, o texto do botão mudará para **Seguinte**. Para sua conveniência, é possível optar por desativar todos os métodos `Unfollow All` .

O botão **Seguir** será exibido:

* Ao exibir o perfil de outro membro
* Em uma página principal de recursos, como fóruns, QnA e blogs
   * Segue toda a atividade desse recurso geral

* Para uma entrada específica, como um tópico do fórum, uma pergunta de QnA ou um artigo do blog
   * Segue toda a atividade dessa entrada específica

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Activity Streams Essentials](essentials-activities.md) para desenvolvedores.
