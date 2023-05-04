---
title: Configuração de uma solução de gerenciamento de correspondência
seo-title: Configuring a Correspondence Management solution
description: Saiba como definir um URL de instância de autor para a restauração de versão da instância de autor e definir o URL da instância de publicação para o gerenciador de ativação da instância pública.
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 3%

---

# Configuração de uma solução de gerenciamento de correspondência {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Definindo o URL da instância do autor para VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Use as seguintes etapas para definir um URL de instância do autor para a restauração da versão da instância do autor:

1. Ir para *https://:&lt;publishhost>:&lt;publishport>/lc/system/console/configMgr*. Faça logon com as credenciais do usuário do Console de Gerenciamento OSGi. As credenciais padrão são admin/admin.
1. Localize e clique no botão **[!UICONTROL Editar]** ícone ao lado do **[!UICONTROL com.adobe.livecycle.content.ativate.impl.VersionRestoreManagerImpl.name]** configuração.
1. No **[!UICONTROL URL de Autor do VersionRestoreManager]** , especifique o URL da instância do autor de VersionRestoreManager.

   **Sequência de caracteres do URL**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Se houver várias instâncias de autor (em cluster) diante de um Balanceador de carga, especifique o URL para o balanceador de carga na variável **[!UICONTROL URL de Autor do VersionRestoreManager]** campo.

1. Clique em **[!UICONTROL Salvar]**.

## Definição do URL da instância de publicação para AtivationManagerImpl (gerenciador de ativação da instância pública) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Siga estas etapas para definir o URL da instância de publicação para o gerenciador de ativação da instância pública:

1. Ir para *https://:&lt;authorhost>:&lt;authorport>/lc/system/console/configMgr*. Faça logon com as credenciais do usuário do Console de Gerenciamento OSGi. As credenciais padrão são admin/admin.
1. Localize e clique no botão **[!UICONTROL Editar]** ícone ao lado do **[!UICONTROL com.adobe.livecycle.content.ativation.impl.AtivationManagerImpl.name]** configuração.
1. No **[!UICONTROL URL de publicação do AtivationManager]** , especifique o URL para acessar a instância de publicação do AtivationManager. Você pode fornecer os seguintes URLs.

   * **URL do Balanceador de Carga (Recomendado)**: Forneça o URL do balanceador de carga. Caso tenha um servidor da Web atuando como balanceador de carga na frente do farm de publicação (várias instâncias de publicação sem cluster).
   * **URL da instância de publicação**: Forneça qualquer URL de instância de publicação. Se você tiver uma única instância de publicação ou o servidor da Web que encaminha o farm de publicação não estiver acessível a partir do ambiente do autor devido a quaisquer restrições. Caso a instância de publicação especificada esteja inativa, há um mecanismo de fallback com o qual lidar no lado do autor.
   * **Sequência de caracteres do URL**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Clique em **[!UICONTROL Salvar]**.

Para obter mais informações sobre como configurar o Gerenciamento de correspondência, consulte [Propriedades de configuração do gerenciamento de correspondência](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
