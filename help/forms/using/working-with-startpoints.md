---
title: Trabalhar com pontos de partida
seo-title: Working with Startpoints
description: Etapas para trabalhar com um processo do AEM Forms no dispositivo móvel definido no Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---

# Trabalhar com pontos de partida {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Um ponto de partida chama um processo criado no Workbench. Ele é associado a um formulário que chama o processo quando o formulário é enviado. Consulte [Apresentação do Site de Referência do Geometrixx Finance](/help/forms/using/finance-reference-site-walkthrough.md) para entender os processos.

>[!NOTE]
>
>Os termos pontos de partida, processo de início e formulário são usados alternadamente quando se refere a esse conceito.

Para iniciar um processo a partir do aplicativo AEM Forms, é necessário ter um ponto de partida do tipo **Workspace** em seu processo. Além disso, é necessário selecionar a variável **[!UICONTROL Visível no Mobile Workspace]** para o ponto de partida.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Para iniciar um processo definido no Workbench**

1. Para exibir os Pontos de partida disponíveis no aplicativo AEM Forms, acesse [Tela inicial](/help/forms/using/home-screen.md).
1. No **[!UICONTROL Início]** por padrão, a variável **[!UICONTROL Todos os Forms]** é exibida.

   O ponto de partida está associado a um formulário. Toque no formulário associado ao ponto de partida na lista para abri-lo.

   O formulário associado ao ponto de partida é aberto.

1. Insira os detalhes na **[!UICONTROL Ponto de partida]** formulário.

   Você pode adicionar anotações para essa tarefa usando o [anexo](/help/forms/using/add-attachments.md) botão.

1. Depois de preencher o formulário, toque no **Enviar** botão.

Se o aplicativo estiver offline, o formulário e seus dados serão salvos na pasta Caixa de saída.

Se o aplicativo estiver online, a tarefa será sincronizada com o servidor do AEM Forms e atribuída ao usuário especificado no processo.

Para trabalhar com a tarefa na lista de tarefas, consulte [Abrir uma tarefa](/help/forms/using/open-task.md).
