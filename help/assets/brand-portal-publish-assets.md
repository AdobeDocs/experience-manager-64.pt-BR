---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e cancelar a publicação de ativos no Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 30%

---

# Publicar ativos no Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Como administrador do Adobe Experience Manager Assets, você pode publicar ativos na [!DNL Experience Manager Assets Brand Portal] (ou agende o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. No entanto, é necessário primeiro configurar [!DNL Assets] com [!DNL Brand Portal]. Para obter detalhes, consulte [Configurar [!DNL Assets] com [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

Após publicar um ativo, ele fica disponível para os usuários no Brand Portal.

Se você fizer modificações subsequentes no ativo original em [!DNL Assets], as alterações não são refletidas no Brand Portal até que você publique o ativo novamente. Esse recurso garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

Depois que a replicação for bem-sucedida, você poderá publicar ativos, pastas e coleções no [!DNL Brand Portal]. Para publicar ativos no Brand Portal, siga estas etapas:

>[!NOTE]
>
>O Adobe recomenda uma publicação escalonada, de preferência durante horários que não sejam de pico, para que a variável [!DNL Experience Manager] O autor não ocupa recursos excessivos.

1. No console Assets, passe o mouse sobre os ativos desejados e selecione **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione os ativos que deseja publicar no Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Para publicar os ativos no Brand Portal, as duas opções a seguir estão disponíveis:
   * [Publicar ativos imediatamente](#publish-now)
   * [Publicar ativos mais tarde](#publish-later)

## Publicar ativos agora {#publish-now}

Para publicar os ativos selecionados no Brand Portal, siga um dos procedimentos a seguir:

* Na barra de ferramentas, selecione **[!UICONTROL Publicação rápida]**. Em seguida, no menu, selecione **[!UICONTROL Publicar no Brand Portal]**.

* Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

   1. Em seguida, da **[!UICONTROL Ação]** select **[!UICONTROL Publicar no Brand Portal]** e de **[!UICONTROL Agendamento]** select **[!UICONTROL Agora]**. Toque/clique **[!UICONTROL Próximo].**

   2. Within **[!UICONTROL Escopo]**, confirme a seleção e toque/clique **[!UICONTROL Publicar no Brand Portal]**.

Será exibida uma mensagem informando que os ativos foram enfileirados para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver os ativos publicados.

## Publicar ativos mais tarde {#publish-later}

Para agendar a publicação dos ativos no Brand Portal para uma data ou hora posterior:

1. Depois de selecionar os ativos/pastas para publicar, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas, na parte superior.
2. Ligado **[!UICONTROL Gerenciar publicação]** página, selecione **[!UICONTROL Publicar no Brand Portal]** from **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais tarde]** from **[!UICONTROL Agendamento]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque/clique **[!UICONTROL Próximo]**.
4. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque/clique **[!UICONTROL Próximo]**.
5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque/clique **[!UICONTROL Publicar mais tarde]**.

   ![publishworkflow](assets/publishworkflow.png)

Agora, faça logon no Brand Portal para ver se os ativos publicados estão disponíveis na interface da Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
