---
title: Usar modelos de email personalizados em uma etapa Atribuir tarefa
seo-title: Use custom email templates in an Assign Task step
description: Modelos de email personalizados para notificações por email do fluxo de trabalho de formulários
seo-description: Custom email templates for forms workflow email notifications
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Usar modelos de email personalizados em uma etapa Atribuir tarefa {#use-custom-email-templates-in-an-assign-task-step}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Modelos de email personalizados para notificações por email do fluxo de trabalho de formulários

Você pode usar a etapa Atribuir tarefa para criar e atribuir tarefas a um usuário ou grupo. Quando uma tarefa é atribuída a um usuário ou grupo, uma notificação por email é enviada ao usuário definido ou a cada membro do grupo definido. Uma notificação de email típica contém um link da tarefa atribuída e informações relacionadas à tarefa. A imagem a seguir exibe um exemplo de notificação por email:

![Notificação por email com modelo pronto para uso](do-not-localize/default-email-template.png)

Você pode personalizar a aparência e usar metadados personalizados em uma notificação por email. O AEM Forms fornece um modelo pronto para uso para notificações por email. Você pode personalizar o modelo pronto para uso ou criar um novo modelo do zero.

Os modelos de notificação por email são baseados em [HTML email](https://en.wikipedia.org/wiki/HTML_email). Esses emails se adaptam a diferentes clientes de email e tamanhos de tela. Além disso, o estilo do email é definido no template .

A imagem a seguir exibe uma notificação por email personalizada:

![Notificação por email usando modelo personalizado](do-not-localize/customized-email.png)

## Personalizar o modelo existente {#customize-the-existing-template}

Pronto para uso, o AEM Forms fornece um modelo para notificações por email. O modelo fornece a descrição do título, data de vencimento, prioridade, nome do fluxo de trabalho e link da tarefa atribuída. Você pode personalizar o modelo para alterar a aparência. Execute as seguintes etapas para personalizar o modelo:

1. Faça logon no CRXDE com a conta de administrador.

1. Navegue até /libs/fd/dashboard/templates/email.

1. Abra o arquivo htmlEmailTemplate.txt. Ele contém o template padrão.

1. Substitua o conteúdo do arquivo htmlEmailTemplate.txt por conteúdo personalizado.

   Um modelo de notificação por email é um [HTML email](https://en.wikipedia.org/wiki/HTML_email). Você pode substituir o código html existente pelo seu código personalizado para alterar a aparência do modelo.

1. Salve o arquivo. Agora, o modelo personalizado está pronto para uso.

## Criar um template de email {#create-an-email-template}

Pronto para uso, o AEM Forms fornece um modelo para notificações por email. O modelo fornece a descrição do título, data de vencimento, prioridade, nome do fluxo de trabalho e link da tarefa atribuída. Você também pode adicionar um modelo de email personalizado (seu próprio modelo) para as etapas da tarefa Atribuir. Execute as seguintes etapas para adicionar um modelo de email personalizado:

1. Faça logon no CRXDE com a conta de administrador.

1. Navegue até /libs/fd/dashboard/templates/email.

1. Crie um arquivo .txt. Por exemplo, EmailOnTaskAssign.txt.

1. Adicione o código HTML personalizado ao arquivo.

   Um modelo de notificação por email é um [HTML email](https://en.wikipedia.org/wiki/HTML_email). Você pode adicionar código de HTML personalizado ao arquivo para criar um novo modelo.

1. Salve o arquivo. O modelo está pronto para uso na etapa Atribuir tarefa .

## Usar um modelo de email em uma etapa Atribuir tarefa {#use-an-email-template-in-an-assign-task-step}

Pronto para uso, a etapa Atribuir tarefa está configurada para usar o modelo padrão, htmlEmailTemplate.txt. Você pode optar por usar um modelo personalizado. Para alterar o modelo:

1. Abra o **[!UICONTROL Atribuir tarefa]** etapa.

1. Navegar para **[!UICONTROL Destinatário > Modelo de email do HTML]**.

1. Selecione o modelo de email HTML recém-criado.

1. Clique em **[!UICONTROL OK]**. O modelo é alterado.

Uma notificação por email também usa [metadados](/help/forms/using/use-metadata-in-email-notifications.md). Por exemplo, data de vencimento, prioridade, nome do workflow e muito mais. Você também pode configurar o modelo para usar [metadados personalizados](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification).
