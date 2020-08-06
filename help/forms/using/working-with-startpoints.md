---
title: Trabalhar com pontos de partida
seo-title: Trabalhar com pontos de partida
description: Etapas para trabalhar com um processo AEM Forms a partir do dispositivo móvel definido no Workbench.
seo-description: Etapas para trabalhar com um processo AEM Forms a partir do dispositivo móvel definido no Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Trabalhar com pontos de partida {#working-with-startpoints}

Um ponto de partida chama um processo criado no Workbench. Ele é associado a um formulário que chama o processo quando o formulário é enviado. Consulte Apresentação do Site de Referência do [Geometrixx Finance](/help/forms/using/finance-reference-site-walkthrough.md) para entender os processos.

>[!NOTE]
>
>Os termos pontos de partida, processo de start e formulário são usados de forma intercambiável ao se referirem a esse conceito.

Para iniciar um processo a partir do aplicativo AEM Forms, é necessário ter um ponto de partida do tipo **Workspace** em seu processo. Além disso, é necessário selecionar a opção **[!UICONTROL Visível no Mobile Workspace]** para o ponto de partida.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Para start de um processo definido no Workbench**

1. Para visualização dos pontos de partida disponíveis no aplicativo AEM Forms, vá para a tela [inicial](/help/forms/using/home-screen.md).
1. Na tela **[!UICONTROL Início]** , por padrão, a lista **[!UICONTROL Todos os Forms]** é exibida.

   O ponto de partida está associado a um formulário. Toque no formulário associado ao ponto de partida na lista para abri-lo.

   O formulário associado ao ponto de partida é aberto.

1. Insira os detalhes no formulário **[!UICONTROL Ponto de partida]** .

   É possível adicionar anotações a essa tarefa usando o botão [anexo](/help/forms/using/add-attachments.md) .

1. Depois de preencher o formulário, toque no botão **Enviar** .

Se o aplicativo estiver offline, o formulário e seus dados serão salvos na pasta Caixa de saída.

Se o aplicativo estiver online, a tarefa será sincronizada com o servidor AEM Forms e atribuída ao usuário especificado no processo.

Para trabalhar com a tarefa na lista da tarefa, consulte [Abrindo uma tarefa](/help/forms/using/open-task.md).
