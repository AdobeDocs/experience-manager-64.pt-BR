---
title: Sequências incorporadas
seo-title: Sequências incorporadas
description: Siga esta página para saber mais sobre sequências incorporadas para canais que permitem ao usuário adicionar componentes no canal pai e também reutilizar o conteúdo de um canal diferente e incorporá-lo ao canal pai.
seo-description: Siga esta página para saber mais sobre sequências incorporadas para canais que permitem ao usuário adicionar componentes no canal pai e também reutilizar o conteúdo de um canal diferente e incorporá-lo ao canal pai.
uuid: 3ffbe937-6b60-4eea-acfb-633270b4ded3
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 76be4cc1-4b34-4f1d-b2d3-754a84105dec
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Sequências incorporadas{#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## Adição de sequências incorporadas {#adding-embedded-sequences}

Você tem a opção de adicionar os seguintes componentes ao seu canal de sequência:

* Sequência incorporada
* Sequência incorporada dinâmica

>[!NOTE]
>
>Para aprender a usar outros componentes no seu projeto do Screens, consulte [Adição de componentes a um canal](/help/screens/adding-components-to-a-channel.md).

### Adição de uma sequência incorporada {#adding-an-embedded-sequence}

Você pode adicionar uma sequência incorporada ao seu canal. Uma sequência incorporada é outro canal que inclui ativos como imagens ou vídeos. A adição de uma sequência incorporada permite que o usuário adicione a sequência a um canal por ***Caminho do canal***.

>[!NOTE]
>
>***Caminho do canal ***define uma referência explícita ao canal.
>
>Para saber mais sobre *Caminho do canal*, consulte [Atribuição de canal](/help/screens/channel-assignment.md) na seção sobre criação da documentação do Screens.

Siga as etapas abaixo para adicionar uma sequência incorporada ao seu canal:

1. Selecione o canal em que você deseja incorporar uma página. For example, **We.Retail In-Store** --> **Channels** -->** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Clique no ícone de componentes na barra lateral esquerda para adicionar a página incorporada. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Selecione o **Caminho do canal.**
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. Se o usuário especificar uma duração, a subsequência será interrompida (ou seja, será cortada) no tempo especificado.

1. Defina a Estratégia **de reprodução** medida como **normal**.

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

O exemplo a seguir mostra a adição de uma sequência incorporada (**Canal ocioso - Noite**) a um canal já existente (**Canal ocioso**).

![new2](assets/new2.gif)

### Adição de uma sequência incorporada dinâmica {#adding-a-dynamic-embedded-sequence}

Você pode adicionar uma sequência incorporada dinâmica ao seu canal. Uma sequência incorporada dinâmica é semelhante a uma sequência incorporada, mas permite que o usuário siga uma hierarquia em que as alterações/atualizações feitas em um canal sejam propagadas para o outro usuário. Ela segue a hierarquia pai/filho e também inclui recursos como imagens ou vídeos. Adicionar uma sequência dinâmica permite que o usuário adicione um canal por função de canal.

>[!NOTE]
>
>***Função do canal*** define o contexto da exibição.
>
>Para saber mais sobre *Função do canal*, consulte [Atribuição de canal](/help/screens/channel-assignment.md) na seção sobre criação da documentação do Screens.

Siga as etapas abaixo para adicionar uma sequência incorporada ao seu canal:

1. Selecione o canal em que você deseja incorporar uma sequência dinâmica. For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Clique no ícone de componentes na barra lateral esquerda para adicionar a sequência incorporada dinâmica. Drag and drop the **Dynamic Embedded Sequence** to the editor.

1. Double-click the **Dynamic Embedded Sequence** component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. Defina a Estratégia **de reprodução** medida como **normal**. By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** *(Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![mais recente](assets/latest.gif)

