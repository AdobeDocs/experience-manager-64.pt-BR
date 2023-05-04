---
title: Fluxo de atividades na linha do tempo
description: Este artigo descreve como exibir registros de atividades para ativos na linha do tempo.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 24%

---

# Fluxo de atividades na linha do tempo {#activity-stream-in-timeline}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esse recurso exibe registros de atividades para ativos na linha do tempo. Se você executar qualquer uma das seguintes operações relacionadas a ativos em [!DNL Adobe Experience Manager Assets], o recurso de fluxo de atividade atualiza a linha do tempo para refletir a atividade.

As seguintes operações são registradas no fluxo de atividade:

* Criar
* Excluir
* Download (incluindo representações)
* Publicação
* Desfazer publicação
* Aprovar
* Rejeitar
* Mover

Os registros de atividades a serem exibidos na linha do tempo são obtidos do local `/var/audit/com.day.cq.dam/content/dam` no CRX, onde os arquivos de registro são armazenados.

Além disso, a atividade da linha do tempo é registrada quando novos ativos são carregados ou os existentes são modificados e verificados no Experience Manager via [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) ou [[!DNL Experience Manager] aplicativo de desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=pt-BR).

>[!NOTE]
>
>Fluxos de trabalho transitórios não são exibidos na linha do tempo, pois nenhuma informação de histórico é salva para esses fluxos de trabalho.

Para exibir o fluxo de atividades, execute uma ou mais operações no ativo, selecione o ativo e escolha **[!UICONTROL Linha do tempo]** na lista GlobalNavigation.

![linha do tempo-3](assets/timeline-3.png)

A linha do tempo exibe o fluxo de atividades para as operações que você executa nos ativos.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>O local de armazenamento de log padrão das tarefas **Publicar** e **Cancelar publicação** é `/var/audit/com.day.cq.replication/content`. Para tarefas **Mover**, o local padrão é `/var/audit/com.day.cq.wcm.core.page`.
