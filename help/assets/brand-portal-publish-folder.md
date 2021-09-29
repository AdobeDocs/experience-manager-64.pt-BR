---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e desfazer a publicação de pastas no Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# Publicar pastas no Brand Portal {#publish-folders-to-brand-portal}

Como administrador do Adobe Experience Manager Assets, você pode publicar ativos e pastas na instância [!DNL Experience Manager Assets Brand Portal] (ou agendar o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. No entanto, primeiro você deve integrar [!DNL Experience Manager Assets] com [!DNL Brand Portal]. Para obter detalhes, consulte [Configurar [!DNL Experience Manager Assets] com Brand Portal](configure-aem-assets-with-brand-portal.md).

Após publicar um ativo ou uma pasta, ele fica disponível para os usuários no Brand Portal.

Se fizer modificações subsequentes no ativo ou pasta original em [!DNL Assets], as alterações não serão refletidas no Brand Portal até que publique novamente o ativo ou a pasta. Esse recurso garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

## Publicar pastas no Brand Portal {#publish-folders-to-brand-portal-1}

1. Na interface [!DNL Assets], passe o mouse sobre a pasta desejada e selecione a opção **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione a pasta desejada e siga as etapas adicionais.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar pastas agora**

   Para publicar as pastas selecionadas no Brand Portal, siga um dos procedimentos a seguir:

   * Na barra de ferramentas, selecione **[!UICONTROL Publicação rápida]**. Em seguida, no menu, selecione **[!UICONTROL Publish to Brand Portal]**.
   * Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

3. Em seguida, no **[!UICONTROL Action]** selecione **[!UICONTROL Publish to Brand Portal]** e, em **[!UICONTROL Scheduling]**, selecione **[!UICONTROL Now]**. Toque em **[!UICONTROL Próximo].**
4. Dentro de **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Publicar no Brand Portal]**.

   Será exibida uma mensagem informando que a pasta foi colocada na fila para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver a pasta publicada.

   **Publicar pastas mais tarde**

   Para agendar a publicação no fluxo de trabalho do Brand Portal de pastas de ativos para uma data ou hora posterior:

   1. Depois de selecionar os ativos/pastas para publicar, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas na parte superior.
   2. Na página **[!UICONTROL Gerenciar publicação]**, selecione **[!UICONTROL Publicar no Brand Portal]** a partir de **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais Tarde]** a partir de **[!UICONTROL Programação]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque em **[!UICONTROL Próximo]**.
   4. Confirme sua seleção no **[!UICONTROL Escopo]**. Toque em **[!UICONTROL Próximo]**.
   5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque em **[!UICONTROL Publicar mais tarde]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Cancelar publicação de pastas do Brand Portal {#unpublish-folders-from-brand-portal}

Você pode remover qualquer pasta de ativos publicada no Brand Portal ao cancelar a publicação da instância do autor [!DNL Experience Manager]. Após cancelar a publicação da pasta original, a cópia não estará mais disponível para os usuários do Brand Portal.

Você tem a opção de cancelar a publicação de pastas do Brand Portal rapidamente ou agendá-las para uma data e hora posteriores. Para cancelar a publicação de pastas de ativos do Brand Portal:

1. Na interface [!DNL Assets] na instância [!DNL Experience Manager] do autor, selecione a pasta que deseja cancelar a publicação.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Na barra de ferramentas, toque/clique em **[!UICONTROL Gerenciar publicação]**.

3. **Cancelar a publicação do Brand Portal agora**

   Para cancelar a publicação rapidamente da pasta desejada do Brand Portal:

   1. Na página **[!UICONTROL Gerenciar publicação]**, em **[!UICONTROL Ação]** selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]**, selecione **[!UICONTROL Agora]**.
   2. Toque/ clique em **[!UICONTROL Próximo].**
   3. Dentro de **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Cancelar publicação do Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Cancelar a publicação do Brand Portal mais tarde**

   Para agendar a publicação de uma pasta do Brand Portal para uma data e hora posteriores:

   1. Na página **[!UICONTROL Gerenciar publicação]**, em **[!UICONTROL Ação]** selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]**, selecione **[!UICONTROL Mais Tarde].**
   2. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque em **[!UICONTROL Próximo]**.
   3. Dentro de **[!UICONTROL Scope]**, confirme a seleção e toque em **[!UICONTROL Next]**.
   4. Especifique um **[!UICONTROL Título do fluxo de trabalho]** em **[!UICONTROL Fluxos de trabalho]**. Toque em **[!UICONTROL Cancelar publicação mais tarde].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>O procedimento para publicar/cancelar a publicação de um ativo de/para o Brand Portal é semelhante ao procedimento correspondente para uma pasta.
