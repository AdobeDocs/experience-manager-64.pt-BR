---
title: Compartilhamento de pasta privada
description: Saiba como criar uma pasta privada no Adobe Experience Manager Assets e compartilhá-la com outros usuários e atribuir vários privilégios a eles.
contentOwner: AG
feature: Collaboration
role: User
exl-id: b6aa3cba-4085-47ac-a249-7461baee2a00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 7%

---

# Compartilhamento de pasta privada {#private-folder-sharing}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode criar uma pasta privada na interface do usuário do Adobe Experience Manager Assets que está disponível exclusivamente para você. Você pode compartilhar essa pasta privada com outros usuários e atribuir vários privilégios a eles. Com base no nível de privilégio atribuído, os usuários podem executar várias tarefas na pasta, por exemplo, visualizar ativos na pasta ou editar os ativos.

1. No console Assets, toque/clique em **[!UICONTROL Criar]** na barra de ferramentas e escolha **[!UICONTROL Pasta]** no menu .

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. No **[!UICONTROL Adicionar pasta]** , insira um título e nome (opcional) para a pasta e selecione **[!UICONTROL Privado]**.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. Toque/clique em **[!UICONTROL Criar]**. Uma pasta privada é criada na interface do usuário do .

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Para compartilhar a pasta com outros usuários e atribuir privilégios a eles, selecione a pasta e clique/toque no ícone **[!UICONTROL Propriedades]** na barra de ferramentas.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >A pasta não fica visível para nenhum outro usuário até que você a compartilhe.

1. Na página Propriedades da pasta , selecione um usuário no **[!UICONTROL Adicionar usuário]** , atribua uma função ao usuário na pasta privada e clique em **[!UICONTROL Adicionar]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Você pode atribuir várias funções, como Editor, Proprietário ou Visualizador ao usuário com quem você compartilha a pasta. Se você atribuir uma função de Proprietário ao usuário, ele terá privilégios de Editores na pasta. Além disso, o usuário pode compartilhar a pasta com outras pessoas. Se você atribuir uma função de Editor, o usuário poderá editar os ativos em sua pasta privada. Se você atribuir uma função de Visualizador, o usuário só poderá visualizar os ativos em sua pasta privada.

1. Clique em **[!UICONTROL Salvar]**. Dependendo da função atribuída, o usuário recebe um conjunto de privilégios em sua pasta privada quando ele faz logon no [!DNL Experience Manager] Ativos.
1. Clique em **[!UICONTROL Ok]** para fechar a mensagem de confirmação.
1. O usuário com quem você compartilha a pasta recebe uma notificação de compartilhamento. Faça logon em [!DNL Experience Manager] Ativos com as credenciais do usuário para exibir a notificação.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Toque/clique no ícone Notification para abrir a lista de notificações.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. Clique/toque na entrada da pasta privada compartilhada pelo administrador para abrir a pasta.

>[!NOTE]
>
>Para criar uma pasta privada, você precisa de permissões Ler e Editar ACL na pasta pai na qual deseja criar uma pasta privada. Se você não for um administrador, essas permissões não serão ativadas para você por padrão em */content/dam*. Nesse caso, primeiro obtenha essas permissões para sua ID/grupo de usuários antes de tentar criar pastas privadas ou exibir configurações da pasta.
