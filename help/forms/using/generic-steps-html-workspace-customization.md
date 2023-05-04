---
title: Etapas genéricas para personalização do espaço de trabalho do AEM Forms
seo-title: Generic steps for AEM Forms workspace customization
description: Como começar a personalizar a interface do usuário do AEM Forms workspace.
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 4%

---

# Etapas genéricas para personalização do espaço de trabalho do AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

As etapas genéricas para executar qualquer personalização são:

1. Faça logon no CRXDE Lite acessando `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Crie uma pasta chamada `ws`at `/apps`, se não existir. Clique em **[!UICONTROL Salvar tudo]**.
1. Navegue até `/apps/ws`e navegue até o **[!UICONTROL Controle de acesso]** guia .
1. No **[!UICONTROL Controle de acesso]** listar, clique em **[!UICONTROL +]** para adicionar uma nova entrada. Clique em **[!UICONTROL +]** novamente.
1. Pesquise e selecione o **[!UICONTROL PERM_WORKSPACE_USER]** Principal.

   ![Selecione PERM_WORKSPACE_USER principal como parte das etapas genéricas para personalizar o HTML Workspace](assets/perm_workspace_user.png)

1. Dar `jcr:read` privilégio do diretor.
1. Clique em **[!UICONTROL Salvar tudo]**.
1. Copie o `GET.jsp` e `html.jsp`arquivos da `/libs/ws`para `/apps/ws` pasta.
1. Copie o `/libs/ws/locales` na pasta `/apps/ws` pasta. Clique em **[!UICONTROL Salvar tudo]**.
1. Atualize as referências e os caminhos relativos na `GET.jsp` como mostrado abaixo e clique em **[!UICONTROL Salvar tudo]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Faça o seguinte para personalizações de CSS:

   1. Navegue até o `/apps/ws` e crie uma nova pasta chamada `css`.
   1. No `css`pasta, crie um novo arquivo chamado `newStyle.css`.
   1. Abrir `/apps/ws/html`.jsp e alterar de

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   para

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Coloque a entrada do arquivo CSS definido pelo usuário após a entrada de newStyle.css, conforme mostrado acima.

1. No arquivo /apps/ws/html.jsp, altere de

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   para

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Faça o seguinte:

   1. Crie uma pasta chamada `js`at `/apps/ws`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Crie uma pasta chamada `libs`at `/apps/ws/js`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Crie uma pasta chamada `jqueryui`at `/apps/ws/js/libs`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Copiar `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` para `/apps/ws/js/libs/jqueryui`. Clique em **[!UICONTROL Salvar tudo]**.

1. Faça o seguinte para personalizações de HTML:

   1. Em `/apps/ws/js`, crie uma pasta chamada `runtime`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Em `/apps/ws/js/runtime`, crie uma pasta chamada `templates`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Copiar `/libs/ws/js/main.js` para `/apps/ws/js/main.js`.
   1. Copiar /libs/ws/js/registry.js para `/apps/ws/js/registry.js`.

1. Clique em **[!UICONTROL Salvar tudo]**, limpe o cache e atualize o espaço de trabalho do AEM Forms.

   Acessar o URL `https://[server]:[port]/lc/ws` e faça logon com credenciais de administrador/senha. O navegador redireciona para `https://[server]:[port]/lc/apps/ws/index.html`.
