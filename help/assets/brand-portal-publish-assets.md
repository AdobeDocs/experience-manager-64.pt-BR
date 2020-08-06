---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e cancelar a publicação de ativos no Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 35%

---


# Publicar ativos no Brand Portal{#publish-assets-to-brand-portal}

Como administrador do Adobe Experience Manager (AEM) Assets, você pode publicar ativos na instância do AEM Assets Brand Portal (ou agendar o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. No entanto, você deve primeiro configurar o AEM Assets com o Brand Portal. Para obter detalhes, consulte [Configurar o AEM Assets com o Brand Portal](configure-aem-assets-with-brand-portal.md).

Depois de publicar um ativo, ele estará disponível para os usuários no Brand Portal.

Se você fizer modificações subsequentes no ativo original no AEM Assets, as alterações não serão refletidas no Brand Portal até que você publique o ativo novamente. Esse recurso garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

Depois que a replicação for bem-sucedida, você poderá publicar ativos, pastas e coleções no Brand Portal. Para publicar ativos no Brand Portal, siga estas etapas:

>[!NOTE]
>
>A Adobe recomenda uma publicação escalonada, de preferência durante horários que não sejam de pico, para que o autor do AEM não ocupe recursos excessivos.

1. No console Ativos, passe o mouse sobre os ativos desejados e selecione a opção **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione os ativos que deseja publicar no Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Para publicar os ativos no Brand Portal, duas opções estão disponíveis:
   * [Publicar ativos imediatamente](#publish-now)
   * [Publicar ativos mais tarde](#publish-later)

## Publicar ativos agora {#publish-now}

Para publicar os ativos selecionados no Brand Portal, siga um dos procedimentos a seguir:

* Na barra de ferramentas, selecione **[!UICONTROL Publicação rápida]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

   1. Em seguida, na **[!UICONTROL Ação]** , selecione **[!UICONTROL Publicar no Brand Portal]** e, em **[!UICONTROL Agendamento]** , selecione **[!UICONTROL Agora]**. Tap/ click **[!UICONTROL Next].**

   2. Dentro do **[!UICONTROL Escopo]**, confirme sua seleção e toque/clique em **[!UICONTROL Publicar no Portal]** da Marca.

Será exibida uma mensagem informando que os ativos foram enfileirados para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver os ativos publicados.

## Publicar ativos mais tarde {#publish-later}

Para agendar a publicação dos ativos no Brand Portal para uma data ou hora posterior:

1. Depois de selecionar os ativos/ pastas a serem publicados, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas na parte superior.
2. Na página **[!UICONTROL Gerenciar publicação]** , selecione **[!UICONTROL Publicar no portal]** da marca em **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais tarde]** em **[!UICONTROL Agendamento]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Tap/ click **[!UICONTROL Next]**.
4. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Tap/ click **[!UICONTROL Next]**.
5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Tap/ click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

Agora, faça logon no Brand Portal para verificar se os recursos publicados estão disponíveis na interface do Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
