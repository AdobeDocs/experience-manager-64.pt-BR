---
title: Configurar a integração do AEM Assets com o Experience Cloud
description: Saiba como configurar a integração do AEM Assets com o Experience Cloud.
feature: Asset Management
role: User, Architect, Admin
exl-id: f8629c30-1901-4b6e-b5a6-e46ee3c72fba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 3%

---

# Configurar a integração do AEM Assets com o Experience Cloud {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Se você for um cliente do Adobe Experience Cloud, poderá sincronizar os ativos no Adobe Experience Manager Assets com a Adobe Creative Cloud, e vice-versa. Você também pode sincronizar ativos com o Experience Cloud e vice-versa. Você pode configurar essa sincronização por meio de [!DNL Adobe I/O]. O nome atualizado de [!DNL Adobe Marketing Cloud] é [!DNL Adobe Experience Cloud].

O fluxo de trabalho para configurar essa integração é:

1. Criar uma autenticação em [!DNL Adobe I/O] usando um gateway público e obtenha uma ID de aplicativo.
1. Crie um perfil na instância do AEM Assets usando a ID do aplicativo.
1. Use essa configuração para sincronizar ativos.

No back-end, o servidor do AEM autentica seu perfil no gateway e, em seguida, sincroniza os dados entre o Assets e o Experience Cloud.

>[!NOTE]
>
>Esse recurso foi descontinuado no AEM Assets. Localizar substituições em [Práticas recomendadas de integração do AEM e do Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). Se você tiver alguma query, [entre em contato com o Suporte ao cliente Adobe](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-287.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Criar um aplicativo {#create-an-application}

1. Acesse a interface do gateway do Adobe Developer fazendo logon em [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/).

   >[!NOTE]
   >
   >Você precisa de privilégios de administrador para criar uma ID de aplicativo.

1. No painel esquerdo, navegue até **[!UICONTROL Ferramentas do desenvolvedor]** > **[!UICONTROL Aplicativos]** para exibir uma lista de aplicativos.
1. Clique em **[!UICONTROL Adicionar]** ![aem_assets_addCírculo_ícone](assets/aem_assets_addcircle_icon.png) para criar um aplicativo.
1. No **[!UICONTROL Credenciais do Cliente]** lista, selecione **[!UICONTROL Conta de Serviço (Asserção JWT)]**, que é um serviço de comunicação servidor a servidor para autenticação de servidor.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Especifique um nome para o aplicativo e uma descrição opcional.
1. No **[!UICONTROL Organização]** selecione a organização para a qual deseja sincronizar ativos.
1. No **[!UICONTROL Escopo]** lista, selecione **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** e **[!UICONTROL cc-share]**.
1. Clique em **[!UICONTROL Criar]**. Uma mensagem notifica que o aplicativo foi criado.

   ![Notificação da criação bem-sucedida do aplicativo para integrar o AEM Assets com o Adobe Creative Cloud](assets/chlimage_1-289.png)

1. Copie o **[!UICONTROL ID do aplicativo]** que é gerado para o novo aplicativo.

   >[!CAUTION]
   >
   >Certifique-se de que você não tenha copiado inadvertidamente o **[!UICONTROL Segredo do aplicativo]** em vez de **[!UICONTROL ID do aplicativo]**.

## Adicionar uma nova configuração ao Experience Cloud {#add-a-new-configuration}

1. Clique no logotipo do AEM na interface do usuário da instância local do AEM Assets e navegue até **[!UICONTROL Ferramentas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Cloud Services herdados]**.

1. Localize a variável **[!UICONTROL Adobe Experience Cloud]** serviço. Se não houver configurações, clique em **[!UICONTROL Configurar agora]**. Se houver configurações, clique em **[!UICONTROL Mostrar configurações]** e clique em `+` para adicionar uma nova configuração.

   >[!NOTE]
   >
   >Use uma conta da Adobe ID que tenha privilégios de administrador para a organização.

1. No **[!UICONTROL Criar configuração]** , especifique um título e nome para a nova configuração e clique em **[!UICONTROL Criar]**.

   ![Nomeie uma nova configuração para integrar o AEM Assets e o Creative Cloud](assets/cloudservices_configure_mc.png)

1. No **[!UICONTROL URL do locatário]** , especifique o URL do AEM Assets. No passado, se o URL foi definido como `https://<tenant_id>.marketing.adobe.com`altere para `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Navegue até **Ferramentas > Serviços da nuvem > Serviços da nuvem herdados**. Em Adobe Experience Cloud, clique em **Mostrar configurações**.
   1. Selecione a configuração existente a ser editada. Edite a configuração e substitua `marketing.adobe.com` para `experiencecloud.adobe.com`.
   1. Salve a configuração. Teste os agentes de replicação de sincronização MAC.

1. No **[!UICONTROL ID do cliente]** , cole a ID do aplicativo copiada no final do procedimento [criar um aplicativo](#create-an-application).

   ![Forneça os valores da ID do aplicativo necessários para integrar o AEM Assets e o Creative Cloud](assets/cloudservices_tenant_info.png)

1. Em **[!UICONTROL Sincronização]** select **[!UICONTROL Ativado]** para ativar a sincronização e clique em **[!UICONTROL OK]**. Se você selecionar **desativado**, a sincronização funciona em uma única direção.

1. Na página de configuração, clique em **[!UICONTROL Exibir chave pública]** para exibir a chave pública gerada para sua instância. Como alternativa, clique em **[!UICONTROL Baixar chave pública para o gateway OAuth]** para baixar o arquivo que contém a chave pública. Em seguida, abra o arquivo para exibir a chave pública.

## Ativar sincronização {#enable-synchronization}

1. Exibir a chave pública usando um dos métodos a seguir mencionados na última etapa do procedimento [adicionar uma nova configuração ao Experience Cloud](#add-a-new-configuration). Clique em **[!UICONTROL Exibir chave pública]**.

1. Copie a chave pública e cole-a no **[!UICONTROL Chave pública]** campo da interface de configuração do aplicativo criado em [criar um aplicativo](#create-an-application).

   ![chlimage_1-293](assets/chlimage_1-293.png)

1. Clique em **[!UICONTROL Atualizar]**. Sincronize seus ativos com a instância do AEM Assets agora.

## Testar a sincronização {#test-the-synchronization}

1. Clique no logotipo do AEM na interface do usuário da instância local do AEM Assets e navegue até **[!UICONTROL Ferramentas]**> **[!UICONTROL Implantação]**> **[!UICONTROL Replicação]**para localizar os perfis de replicação criados para sincronização.
1. No **[!UICONTROL Replicação]** página, clique em **[!UICONTROL Agentes do autor]**.
1. Na lista de perfis, clique no perfil de replicação padrão para sua organização abri-lo.
1. Na caixa de diálogo , clique em **[!UICONTROL Testar conexão]**.

   ![Testar conexão e definir o perfil de replicação padrão para sua organização](assets/chlimage_1-294.png)

1. Quando o restante da replicação for concluído, verifique se há uma mensagem de sucesso no final dos resultados do teste.

## Adicionar usuários ao Experience Cloud {#add-users-to-experience-cloud}

1. Faça logon no Experience Cloud usando as credenciais de administrador.
1. Dos trilhos, vá para **[!UICONTROL Administração]** e, em seguida, clique em **[!UICONTROL Iniciar o Enterprise Dashboard]**.
1. No painel , clique em **[!UICONTROL Usuários]** para abrir o **[!UICONTROL Gerenciamento de usuários]** página.
1. Na barra de ferramentas, clique em **Adicionar** ![aem_assets_add_icon](assets/aem_assets_add_icon.png).
1. Adicione um ou mais usuários que você deseja fornecer a capacidade de compartilhar ativos com o Creative Cloud.

   >[!NOTE]
   >
   >Somente os usuários adicionados ao Experience Cloud podem compartilhar ativos do AEM Assets com o Creative Cloud.

## Trocar ativos entre o AEM Assets e o Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Faça logon no AEM Assets.
1. No console Assets, crie uma pasta e faça upload de alguns ativos para ela. Por exemplo, crie uma pasta **mc-demo** e fazer upload de um ativo para ele.
1. Selecione a pasta e clique em **Compartilhar** ![assets_share](assets/assets_share.png).
1. No menu, selecione **[!UICONTROL Adobe Experience Cloud]** e clique em **[!UICONTROL Compartilhar]**. Uma mensagem notifica que a pasta é compartilhada com o Experience Cloud.

   ![chlimage_1-295](assets/chlimage_1-295.png)

   >[!NOTE]
   >
   >Compartilhamento de uma pasta de Ativos do tipo `sling:OrderedFolder`, não é compatível no contexto do compartilhamento no Adobe Experience Cloud. Se você deseja compartilhar uma pasta, ao criá-la no AEM Assets, não selecione a variável **[!UICONTROL Solicitado]** opção.

1. Atualize a interface do usuário do AEM Assets. A pasta criada no console Assets da instância local do AEM Assets é copiada para a interface do usuário do Experience Cloud. O ativo que você faz upload para a pasta no AEM Assets aparece na cópia da pasta no Experience Cloud depois de ser processado pelo servidor AEM.
1. Você também pode fazer upload de um ativo na cópia replicada da pasta no Experience Cloud. Após ser processado, o ativo aparece na pasta compartilhada no AEM Assets.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.
## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Práticas recomendadas de integração de ativos e Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)
>* [Práticas recomendadas de compartilhamento de ativos para a pasta do Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

