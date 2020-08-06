---
title: Usar modelos de email personalizados em uma etapa Atribuir Tarefa
seo-title: Usar modelos de email personalizados em uma etapa Atribuir Tarefa
description: 'Modelos de email personalizados para notificações por email de fluxo de trabalho de formulários '
seo-description: 'Modelos de email personalizados para notificações por email de fluxo de trabalho de formulários '
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
translation-type: tm+mt
source-git-commit: 8b5a3e1f6616c3a07da91e4347596961ac4a8e22
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Usar modelos de email personalizados em uma etapa Atribuir Tarefa {#use-custom-email-templates-in-an-assign-task-step}

Modelos de email personalizados para notificações por email de fluxo de trabalho de formulários

Você pode usar a etapa Atribuir Tarefa para criar e atribuir tarefas a um usuário ou grupo. Quando uma tarefa é atribuída a um usuário ou grupo, uma notificação por email é enviada para o usuário definido ou para cada membro do grupo definido. Uma notificação por email típica contém um link da tarefa atribuída e informações relacionadas à tarefa. A imagem a seguir exibe um exemplo de notificação por email:

![Notificação por e-mail com modelo fora da caixa](do-not-localize/default-email-template.png)

Você pode personalizar a aparência e usar metadados personalizados em uma notificação por email. A AEM Forms fornece um modelo pronto para receber notificações por e-mail. Você pode personalizar o modelo out of box ou criar um novo modelo do zero.

Os modelos de notificação por e-mail são baseados em e-mail [](https://en.wikipedia.org/wiki/HTML_email)HTML. Esses e-mails se adaptam a diferentes clientes de e-mail e tamanhos de tela. Além disso, o estilo do email é definido no modelo.

A imagem a seguir exibe uma notificação por email personalizada:

![Notificação por email usando modelo personalizado](do-not-localize/customized-email.png)

## Personalizar o modelo existente {#customize-the-existing-template}

A AEM Forms fornece um modelo para notificações por email. O modelo fornece descrição do título, data de vencimento, prioridade, nome do fluxo de trabalho e link da tarefa atribuída. Você pode personalizar o modelo para alterar a aparência. Execute as seguintes etapas para personalizar o modelo:

1. Faça logon no CRXDE com a conta de administrador.

1. Navegue até /libs/fd/painel/modelos/email.

1. Abra o arquivo htmlEmailTemplate.txt. Ele contém o modelo padrão.

1. Substitua o conteúdo do arquivo htmlEmailTemplate.txt por conteúdo personalizado.

   Um modelo de notificação por email é um email [](https://en.wikipedia.org/wiki/HTML_email)HTML. Você pode substituir o código html existente pelo código personalizado para alterar a aparência do modelo.

1. Salve o arquivo. Agora, o modelo personalizado está pronto para uso.

## Criar um modelo de email {#create-an-email-template}

A AEM Forms fornece um modelo para notificações por email. O modelo fornece descrição do título, data de vencimento, prioridade, nome do fluxo de trabalho e link da tarefa atribuída. Você também pode adicionar um modelo de email personalizado (seu próprio modelo) para as etapas Atribuir tarefa. Execute as seguintes etapas para adicionar um modelo de email personalizado:

1. Faça logon no CRXDE com a conta de administrador.

1. Navegue até /libs/fd/painel/modelos/email.

1. Crie um arquivo .txt. Por exemplo, EmailOnTaskAssign.txt.

1. Adicione o código HTML personalizado ao arquivo.

   Um modelo de notificação por email é um email [](https://en.wikipedia.org/wiki/HTML_email)HTML. Você pode adicionar um código HTML personalizado ao arquivo para criar um novo modelo.

1. Salve o arquivo. O modelo está pronto para uso na etapa Atribuir Tarefa.

## Usar um modelo de email em uma etapa Atribuir Tarefa {#use-an-email-template-in-an-assign-task-step}

A etapa Atribuir tarefa está configurada para usar o modelo padrão, htmlEmailTemplate.txt. Você pode optar por usar um modelo personalizado. Para alterar o modelo:

1. Abra a etapa **[!UICONTROL Atribuir Tarefa]** .

1. Navegue até **[!UICONTROL Destinatário > Modelo]** de email HTML.

1. Selecione o modelo de e-mail HTML recém-criado.

1. Clique em **[!UICONTROL OK]**. O modelo é alterado.

Uma notificação por email também usa [metadados](/help/forms/using/use-metadata-in-email-notifications.md). Por exemplo, data de vencimento, prioridade, nome do fluxo de trabalho e muito mais. Você também pode configurar o modelo para usar metadados [](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification)personalizados.
