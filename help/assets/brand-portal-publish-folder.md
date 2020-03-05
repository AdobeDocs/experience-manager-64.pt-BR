---
title: Publicar pastas no Brand Portal
description: Saiba como publicar e cancelar a publicação de pastas no Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publish folders to Brand Portal {#publish-folders-to-brand-portal}

Como administrador dos ativos Adobe Experience Manager (AEM), você pode publicar ativos e pastas na instância do AEM Assets Brand Portal (ou agendar o fluxo de trabalho de publicação para uma data/hora posterior) para sua organização. No entanto, primeiro é necessário integrar os ativos AEM ao Portal de marcas. Para obter detalhes, consulte [Configurar ativos AEM com o Portal](configure-aem-assets-with-brand-portal.md)da marca.

Depois de publicar um ativo ou pasta, ele estará disponível para os usuários no Brand Portal.

Se você fizer modificações subsequentes no ativo ou pasta original nos ativos AEM, as alterações não serão refletidas no Portal de marcas até que você publique novamente o ativo ou a pasta. Esse recurso garante que as alterações do trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador estão disponíveis no Brand Portal.

## Publish folders to Brand Portal {#publish-folders-to-brand-portal-1}

1. Na interface dos ativos AEM, passe o mouse sobre a pasta desejada e selecione a opção **[!UICONTROL Publicar]** nas ações rápidas.

   Como alternativa, selecione a pasta desejada e siga as etapas seguintes.

   ![publish2bp](assets/publish2bp.png)

2. **Publicar pastas agora**

   Para publicar as pastas selecionadas no Brand Portal, execute um dos procedimentos a seguir:

   * Na barra de ferramentas, selecione Publicação **[!UICONTROL rápida]**. Em seguida, no menu, selecione **[!UICONTROL Publicar no Brand Portal]**.
   * Na barra de ferramentas, selecione **[!UICONTROL Gerenciar publicação]**.

3. Em seguida, na **[!UICONTROL Ação]** , selecione **[!UICONTROL Publicar no Brand Portal]** e, em **[!UICONTROL Agendamento]** , selecione **[!UICONTROL Agora]**. Toque em **[!UICONTROL Avançar].**
4. Dentro do **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Publicar no Portal]** da Marca.

   Será exibida uma mensagem informando que a pasta foi colocada na fila para publicação no Brand Portal. Faça logon na interface do Brand Portal para ver a pasta publicada.

   **Publicar pastas mais tarde**

   Para agendar a publicação no fluxo de trabalho do Brand Portal das pastas de ativos para uma data ou hora posterior:

   1. Depois de selecionar os ativos/pastas a serem publicados, selecione **[!UICONTROL Gerenciar publicação]** na barra de ferramentas na parte superior.
   2. Na página **[!UICONTROL Gerenciar publicação]** , selecione **[!UICONTROL Publicar no portal]** da marca em **[!UICONTROL Ação]** e selecione **[!UICONTROL Mais tarde]** em **[!UICONTROL Agendamento]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Selecione uma data **[!UICONTROL de]** ativação e especifique a hora. Toque em **[!UICONTROL Avançar]**.
   4. Confirme sua seleção no **[!UICONTROL Escopo]**. Toque em **[!UICONTROL Avançar]**.
   5. Especifique um título de Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque em **[!UICONTROL Publicar mais tarde]**.

      ![manager chedulepub](assets/manageschedulepub.png)

## Unpublish folders from Brand Portal {#unpublish-folders-from-brand-portal}

Você pode remover qualquer pasta de ativos publicada no Brand Portal, desfazendo a publicação da instância do autor de AEM. Após desfazer a publicação da pasta original, a cópia não estará mais disponível para os usuários do Brand Portal.

Você tem a opção de cancelar a publicação rápida de pastas do Brand Portal ou agendá-las para uma data e hora posteriores. Para cancelar a publicação de pastas de ativos do Portal de marcas:

1. Na interface dos ativos AEM na instância do autor de AEM, selecione a pasta que deseja cancelar a publicação.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Na barra de ferramentas, toque/clique em **[!UICONTROL Gerenciar publicação]**.

3. **Cancelar a publicação do Brand Portal agora**

   Para cancelar a publicação rápida da pasta desejada no Portal de marcas:

   1. Na página **[!UICONTROL Gerenciar publicação]** , em **[!UICONTROL Ação]** , selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]** , selecione **[!UICONTROL Agora]**.
   2. Tap/ click **[!UICONTROL Next].**
   3. Dentro do **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Cancelar publicação do Portal]** da marca.
   ![confirmar-desfazer a publicação](assets/confirm-unpublish.png)

   **Cancelar a publicação do Brand Portal mais tarde**

   Para agendar a publicação de uma pasta do Brand Portal para uma data e hora posteriores:

   1. Na página **[!UICONTROL Gerenciar publicação]** , em **[!UICONTROL Ação]** , selecione **[!UICONTROL Cancelar publicação do Brand Portal]** e, em **[!UICONTROL Agendamento]** , selecione **[!UICONTROL Mais tarde].**
   2. Selecione uma data **[!UICONTROL de]** ativação e especifique a hora. Toque em **[!UICONTROL Avançar]**.
   3. Dentro do **[!UICONTROL Escopo]**, confirme sua seleção e toque em **[!UICONTROL Próximo]**.
   4. Especifique um título **[!UICONTROL de]** Fluxo de trabalho em **[!UICONTROL Fluxos de trabalho]**. Toque em **[!UICONTROL Cancelar publicação mais tarde].**

      ![despublicar fluxos de trabalho](assets/unpublishworkflows.png)


>[!NOTE]
>
>O procedimento para publicar/desfazer a publicação de um ativo do/para o Portal da Marca é semelhante ao procedimento correspondente para uma pasta.
