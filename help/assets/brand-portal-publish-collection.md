---
title: Publicar coleções no Brand Portal
description: Saiba como publicar e cancelar a publicação de coleções no Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 22%

---

# Publicar coleções no Brand Portal {#publish-collections-to-brand-portal}

Como administrador do Adobe Experience Manager Assets, você pode publicar coleções na instância [!DNL Experience Manager Assets Brand Portal] de sua organização. No entanto, primeiro é necessário integrar Ativos com a Brand Portal. Para obter detalhes, consulte [Configurar o Assets com o Brand Portal](configure-aem-assets-with-brand-portal.md).

Se fizer modificações subsequentes na coleção original em Ativos, as alterações não serão refletidas no Brand Portal até que publique a coleção novamente. Essa característica garante que as alterações de trabalho em andamento não estejam disponíveis no Brand Portal. Somente as alterações aprovadas publicadas por um administrador são disponibilizadas no Brand Portal.

>[!NOTE]
>
>Os fragmentos de conteúdo não podem ser publicados no Brand Portal. Portanto, se você selecionar fragmentos de conteúdo no [!DNL Experience Manager] Autor, a ação **[Publicar no Brand Portal]** não estará disponível.
>
>Se coleções contendo fragmentos de conteúdo forem publicadas do [!DNL Experience Manager] Autor para o Brand Portal, todo o conteúdo da pasta, exceto fragmentos de conteúdo, será replicado para a interface do Brand Portal.

## Publicar uma coleção no Brand Portal {#publish-a-collection-to-brand-portal}

1. Na interface do usuário do Assets, toque/clique no logotipo [!DNL Experience Manager]. Em seguida, vá para **[!UICONTROL Assets > Collections]** da página **[!UICONTROL Navigation]**.
2. No console Coleções , selecione a coleção que deseja publicar no Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Na barra de ferramentas, toque/clique em **[!UICONTROL Publicar no Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Na caixa de diálogo de confirmação, toque/clique em **[!UICONTROL Publicar]**.
5. Feche a mensagem de confirmação.
6. Faça logon no Brand Portal como administrador. A coleção publicada está disponível no console Coleções.

   ![published_collection](assets/published_collection.png)

## Cancelar publicação de coleções {#unpublish-collections}

Você pode cancelar a publicação de coleções que publica de Ativos no Brand Portal. Após cancelar a publicação da coleção original, a cópia não estará mais disponível para os usuários do Brand Portal.

1. No console Coleções da instância [!DNL Assets], selecione a coleção que deseja cancelar a publicação.

   ![select_collection-1](assets/select_collection-1.png)

2. Na barra de ferramentas, toque/clique no ícone **[!UICONTROL Remover do Brand Portal]**.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Na caixa de diálogo, toque/clique em **[!UICONTROL Cancelar publicação]**.
4. Feche a mensagem de confirmação. A coleção é removida da interface do Brand Portal.
