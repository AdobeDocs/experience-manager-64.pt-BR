---
title: Publicar coleções no Brand Portal
description: Saiba como publicar e cancelar a publicação de coleções no Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 22%

---

# Publicar coleções no Brand Portal {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Como administrador do Adobe Experience Manager Assets, você pode publicar coleções no [!DNL Experience Manager Assets Brand Portal] para sua organização. No entanto, primeiro é necessário integrar Ativos com a Brand Portal. Para obter detalhes, consulte [Configurar o Assets com o Brand Portal](configure-aem-assets-with-brand-portal.md).

Se você fizer modificações subsequentes na coleção original em Ativos, as alterações não serão refletidas no Brand Portal até que você publique a coleção novamente. Essa característica garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

>[!NOTE]
>
>Os fragmentos de conteúdo não podem ser publicados no Brand Portal. Portanto, se você selecionar fragmentos de conteúdo em [!DNL Experience Manager] Autor, então **[Publicar no Brand Portal]** não está disponível.
>
>Se as coleções que contêm fragmentos de conteúdo forem publicadas de [!DNL Experience Manager] Crie para o Brand Portal e então todo o conteúdo da pasta, exceto fragmentos de conteúdo, é replicado para a interface do Brand Portal.

## Publicar uma coleção no Brand Portal {#publish-a-collection-to-brand-portal}

1. Na interface do usuário do Assets, toque/clique no botão [!DNL Experience Manager] logotipo. Em seguida, vá para **[!UICONTROL Ativos > Coleções]** do **[!UICONTROL Navegação]** página.
2. No console Coleções , selecione a coleção que deseja publicar no Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Na barra de ferramentas, toque/clique **[!UICONTROL Publicar no Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Na caixa de diálogo de confirmação, toque/clique em **[!UICONTROL Publicar]**.
5. Feche a mensagem de confirmação.
6. Faça logon no Brand Portal como administrador. A coleção publicada está disponível no console Coleções.

   ![published_collection](assets/published_collection.png)

## Cancelar publicação de coleções {#unpublish-collections}

Você pode cancelar a publicação de coleções que publica de Ativos no Brand Portal. Após cancelar a publicação da coleção original, a cópia não estará mais disponível para os usuários do Brand Portal.

1. No console Coleções do [!DNL Assets] e selecione a coleção que deseja cancelar a publicação.

   ![select_collection-1](assets/select_collection-1.png)

2. Na barra de ferramentas, toque/clique no botão **[!UICONTROL Remover do Brand Portal]** ícone .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Na caixa de diálogo, toque/clique em **[!UICONTROL Cancelar publicação]**.
4. Feche a mensagem de confirmação. A coleção é removida da interface do Brand Portal.
