---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e cancelar a publicação de pastas no Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 27%

---


# Publicar pastas no Brand Portal{#publish-folders-to-brand-portal}

Como administrador do Adobe Experience Manager (AEM) Assets, você pode publicar ativos e pastas na instância do AEM Assets Brand Portal (ou agendar o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. Entretanto, é necessário primeiro integrar a AEM Assets ao Brand Portal. Para obter detalhes, consulte [Configurar o AEM Assets com o Brand Portal](configure-aem-assets-with-brand-portal.md).

Depois de publicar um ativo ou pasta, ele estará disponível para os usuários no Brand Portal.

Se você fizer modificações subsequentes no ativo ou pasta original no AEM Assets, as alterações não serão refletidas no Portal de marcas até que você publique novamente o ativo ou a pasta. Esse recurso garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

## Publicar pastas no Brand Portal{#publish-folders-to-brand-portal-1}

1. Na interface do AEM Assets, passe o mouse sobre a pasta desejada e selecione a opção **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione a pasta desejada e siga as etapas seguintes.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar pastas agora**

   Para publicar as pastas selecionadas no Brand Portal, siga um dos procedimentos a seguir:

   * Na barra de ferramentas, selecione **[!UICONTROL Publicação rápida]**. Em seguida, no menu, selecione **[!UICONTROL Publicar no Brand Portal]**.
   * Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

3. Em seguida, em **[!UICONTROL Action]** selecione **[!UICONTROL Publicar no Brand Portal]** e em **[!UICONTROL Agendamento]** selecione **[!UICONTROL Agora]**. Toque em **[!UICONTROL Próximo].**
4. Dentro de **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Publicar no Brand Portal]**.

   Será exibida uma mensagem informando que a pasta foi colocada na fila para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver a pasta publicada.

   **Publicar pastas mais tarde**

   Para agendar a publicação no fluxo de trabalho do Brand Portal das pastas de ativos para uma data ou hora posterior:

   1. Depois de selecionar os ativos/pastas a serem publicados, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas na parte superior.
   2. Na página **[!UICONTROL Gerenciar publicação]**, selecione **[!UICONTROL Publicar no portal da marca]** em **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais Tarde]** em **[!UICONTROL Agendamento]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque em **[!UICONTROL Next]**.
   4. Confirme sua seleção no **[!UICONTROL Escopo]**. Toque em **[!UICONTROL Next]**.
   5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque em **[!UICONTROL Publicar mais tarde]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Cancelar publicação de pastas do Brand Portal {#unpublish-folders-from-brand-portal}

Você pode remover qualquer pasta de ativos publicada no Brand Portal, desfazendo a publicação da instância do autor de AEM. Após cancelar a publicação da pasta original, a cópia não estará mais disponível para os usuários do Brand Portal.

Você tem a opção de cancelar a publicação rápida de pastas do Brand Portal ou agendá-las para uma data e hora posteriores. Para cancelar a publicação de pastas de ativos do Brand Portal:

1. Na interface do AEM Assets na instância do autor de AEM, selecione a pasta que deseja cancelar a publicação.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Na barra de ferramentas, toque/clique em **[!UICONTROL Gerenciar publicação]**.

3. **Cancelar a publicação do Brand Portal agora**

   Para cancelar a publicação rápida da pasta desejada no Portal de marcas:

   1. Na página **[!UICONTROL Gerenciar publicação]**, em **[!UICONTROL Action]** selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]**, selecione **[!UICONTROL Agora]**.
   2. Toque/ clique em **[!UICONTROL Próximo].**
   3. Dentro de **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Cancelar a publicação do Portal de Marcas]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Cancelar a publicação do Brand Portal mais tarde**

   Para agendar a publicação de uma pasta do Brand Portal para uma data e hora posteriores:

   1. Na página **[!UICONTROL Gerenciar publicação]**, em **[!UICONTROL Ação]** selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]**, selecione **[!UICONTROL Mais Tarde].**
   2. Selecione uma **[!UICONTROL Data de ativação]** e especifique a hora. Toque em **[!UICONTROL Next]**.
   3. Em **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Próximo]**.
   4. Especifique um **[!UICONTROL Título do fluxo de trabalho]** em **[!UICONTROL Workflows]**. Toque em **[!UICONTROL Cancelar a publicação mais tarde].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>O procedimento para publicar/desfazer a publicação de um ativo do/para o Portal da Marca é semelhante ao procedimento correspondente para uma pasta.
