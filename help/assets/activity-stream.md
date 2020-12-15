---
title: Atividade na linha do tempo
description: 'Este artigo descreve como exibir registros de atividades para ativos na linha do tempo. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 36%

---


# Atividade na linha do tempo {#activity-stream-in-timeline}

Este recurso exibe registros de atividades para ativos na linha do tempo. Se você executar qualquer uma das seguintes operações relacionadas a ativos no Adobe Experience Manager (AEM) Assets, o recurso de fluxo de Atividade atualizará a linha do tempo para refletir a atividade.

As seguintes operações são registradas no fluxo de atividade:

* Criar
* Excluir
* Download (incluindo execuções)
* Publicação
* Desfazer publicação
* Aprovar
* Rejeitar
* Mover

Os registros de atividades a serem exibidos na linha do tempo são obtidos do local `/var/audit/com.day.cq.dam/content/dam` no CRX, onde os arquivos de registro são armazenados.

Além disso, a atividade da linha do tempo é registrada quando novos ativos são carregados ou os existentes são modificados e verificados no AEM por meio do [Adobe Asset Link](https://helpx.adobe.com/br/enterprise/using/manage-assets-using-adobe-asset-link.html) ou do [aplicativo de desktop AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>Workflows transitórios não são exibidos na linha do tempo, pois nenhuma informação de histórico é salva para esses workflows.

Para visualização do fluxo de atividade, execute uma ou mais operações no ativo, selecione o ativo e escolha **[!UICONTROL Linha do tempo]** na lista GlobalNav.

![linha do tempo 3](assets/timeline-3.png)

A linha do tempo exibe o fluxo de atividade para as operações que você executa nos ativos.

![atividade_stream](assets/activity_stream.png)

>[!NOTE]
>
>O local de armazenamento de log padrão das tarefas **Publicar** e **Cancelar publicação** é `/var/audit/com.day.cq.replication/content`. Para tarefas **Mover**, o local padrão é `/var/audit/com.day.cq.wcm.core.page`.
