---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e desfazer a publicação de pastas no Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 26%

---

# Publicar pastas no Brand Portal {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Como administrador do Adobe Experience Manager Assets, você pode publicar ativos e pastas na [!DNL Experience Manager Assets Brand Portal] (ou agende o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. No entanto, primeiro você deve integrar [!DNL Experience Manager Assets] com [!DNL Brand Portal]. Para obter detalhes, consulte [Configurar [!DNL Experience Manager Assets] com o Brand Portal](configure-aem-assets-with-brand-portal.md).

Após publicar um ativo ou uma pasta, ele fica disponível para os usuários no Brand Portal.

Se fizer modificações subsequentes no ativo ou pasta original em [!DNL Assets], as alterações não são refletidas no Brand Portal até que você publique novamente o ativo ou a pasta. Esse recurso garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

## Publicar pastas no Brand Portal {#publish-folders-to-brand-portal-1}

1. No [!DNL Assets] passe o mouse sobre a pasta desejada e selecione **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione a pasta desejada e siga as etapas adicionais.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar pastas agora**

   Para publicar as pastas selecionadas no Brand Portal, siga um dos procedimentos a seguir:

   * Na barra de ferramentas, selecione **[!UICONTROL Publicação rápida]**. Em seguida, no menu, selecione **[!UICONTROL Publicar no Brand Portal]**.
   * Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

3. Em seguida, da **[!UICONTROL Ação]** select **[!UICONTROL Publicar no Brand Portal]** e de **[!UICONTROL Agendamento]** select **[!UICONTROL Agora]**. Toque **[!UICONTROL Próximo].**
4. Within **[!UICONTROL Escopo]**, confirme a seleção e toque em **[!UICONTROL Publicar no Brand Portal]**.

   Será exibida uma mensagem informando que a pasta foi colocada na fila para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver a pasta publicada.

   **Publicar pastas mais tarde**

   Para agendar a publicação no fluxo de trabalho do Brand Portal de pastas de ativos para uma data ou hora posterior:

   1. Após selecionar os ativos/pastas a serem publicados, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas, na parte superior.
   2. Ligado **[!UICONTROL Gerenciar publicação]** página, selecione **[!UICONTROL Publicar no Brand Portal]** from **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais tarde]** from **[!UICONTROL Agendamento]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque **[!UICONTROL Próximo]**.
   4. Confirme sua seleção no **[!UICONTROL Escopo]**. Toque **[!UICONTROL Próximo]**.
   5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque **[!UICONTROL Publicar mais tarde]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Cancelar publicação de pastas do Brand Portal {#unpublish-folders-from-brand-portal}

Você pode remover qualquer pasta de ativos publicada no Brand Portal ao cancelar a publicação no [!DNL Experience Manager] Instância do autor. Após cancelar a publicação da pasta original, a cópia não estará mais disponível para os usuários do Brand Portal.

Você tem a opção de cancelar a publicação de pastas do Brand Portal rapidamente ou agendá-las para uma data e hora posteriores. Para cancelar a publicação de pastas de ativos do Brand Portal:

1. No [!DNL Assets] interface em [!DNL Experience Manager]  Instância do autor, selecione a pasta que deseja cancelar a publicação.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Na barra de ferramentas, toque/clique **[!UICONTROL Gerenciar publicação]**.

3. **Cancelar a publicação do Brand Portal agora**

   Para cancelar a publicação rapidamente da pasta desejada do Brand Portal:

   1. Ligado **[!UICONTROL Gerenciar publicação]** página, de **[!UICONTROL Ação]** select **[!UICONTROL Cancelar publicação do Brand Portal]** e **[!UICONTROL Agendamento]** select **[!UICONTROL Agora]**.
   2. Toque/clique **[!UICONTROL Próximo].**
   3. Within **[!UICONTROL Escopo]**, confirme a seleção e toque em **[!UICONTROL Cancelar publicação do Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Cancelar a publicação do Brand Portal mais tarde**

   Para agendar a publicação de uma pasta do Brand Portal para uma data e hora posteriores:

   1. Ligado **[!UICONTROL Gerenciar publicação]** página, de **[!UICONTROL Ação]** select **[!UICONTROL Cancelar publicação do Brand Portal]** e **[!UICONTROL Agendamento]** select **[!UICONTROL Mais tarde].**
   2. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque **[!UICONTROL Próximo]**.
   3. Within **[!UICONTROL Escopo]**, confirme a seleção e toque em **[!UICONTROL Próximo]**.
   4. Especifique um **[!UICONTROL Título do fluxo de trabalho]** under **[!UICONTROL Fluxos de trabalho]**. Toque **[!UICONTROL Cancelar publicação mais tarde].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>O procedimento para publicar/cancelar a publicação de um ativo de/para o Brand Portal é semelhante ao procedimento correspondente para uma pasta.
