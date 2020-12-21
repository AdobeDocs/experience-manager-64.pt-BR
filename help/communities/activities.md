---
title: Recurso de fluxos de atividade
seo-title: Recurso de fluxos de atividade
description: Atividades de um membro da comunidade conectado
seo-description: Atividades de um membro da comunidade conectado
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Recurso de fluxos de atividade {#activity-streams-feature}

## Introdução {#introduction}

As atividades de um membro da comunidade conectado, como postar em um fórum ou blog, são coletadas em um fluxo que pode ser filtrado e exibido de várias maneiras pela configuração do componente `Activity Streams`.

A habilidade de seguir adiciona outra visualização de atividades quando os membros da comunidade seguem postagens de interesse ou seguem as atividades de outros membros da comunidade.

Esta seção da documentação descreve

* Adicionar o componente de Fluxos de Atividade a um site AEM
* Configurações do componente Fluxos de Atividade

## Adicionando fluxos de Atividade a uma página {#adding-activity-streams-to-a-page}

Se desejar adicionar um componente `Activity Streams` a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Activity Streams`

e arraste-o para o lugar em uma página onde os fluxos de atividade devem aparecer.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](essentials-activities.md#essentials-for-client-side) forem incluídas, o componente `Activity Streams` aparecerá desta forma:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configurando fluxos de Atividade {#configuring-activity-streams}

Selecione o componente `Activity Streams` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-196](assets/chlimage_1-196.png)

Na guia **[!UICONTROL Atividades do usuário]**, especifique as atividades a serem exibidas:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Número máximo de]**
atividadesO número de atividades a serem exibidas
* **[!UICONTROL Caminho]**
do recurso de fluxoDeixe em branco como padrão para o site da comunidade ou grupo da comunidade. O caminho do recurso de fluxo identifica a origem do atividade. O padrão está em branco.
* **[!UICONTROL Exibição de Atividades de usuário]**
marcada, a página de atividades incluirá uma guia que filtros atividades com base nas  geradas na comunidade pelo membro atual. O padrão está marcado.
* **[!UICONTROL Exibir todas as Atividades]**
VisualizaçãoSe marcada, a página atividades incluirá uma guia que inclui todas as atividades geradas na comunidade à qual o membro atual tem acesso. O padrão está marcado.
* **[!UICONTROL Exibir]**
exibição seguinteSe marcada, a página do atividade incluirá uma guia que filtros atividades com base nos  que o membro atual está seguindo. O padrão está marcado.

## Visualização a seguir {#following-view}

Os componentes devem ser configurados para permitir o seguinte. Os recursos que permitem o seguinte são [blog](blog-feature.md), [fórum](forum.md), [QnA](working-with-qna.md), [calendário](calendar.md), [filelibrary](file-library.md) e [comentários](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

O botão **Seguir** fornece um meio de seguir as entradas como atividade, [notificações](notifications.md) e/ou [subscrição](subscriptions.md). Sempre que o botão **Seguir** for selecionado, é possível ativar ou desativar uma seleção. A seleção `Email Subscriptions` só está presente quando configurada.

Se algum método do seguinte for selecionado, o texto do botão mudará para **Seguindo**. Para conveniência, é possível selecionar `Unfollow All` para desativar todos os métodos.

O botão **Seguir** será exibido:

* Ao exibir o perfil de outro membro
* Em uma página principal de recursos, como fóruns, QnA e blogs
   * Segue toda a atividade desse recurso geral

* Para uma entrada específica, como um tópico do fórum, uma pergunta de QnA ou um artigo do blog
   * Segue toda a atividade para essa entrada específica

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Atividade Streams Essentials](essentials-activities.md) para desenvolvedores.
