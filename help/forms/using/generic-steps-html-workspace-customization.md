---
title: Etapas genéricas para personalização do espaço de trabalho AEM Forms
seo-title: Etapas genéricas para personalização do espaço de trabalho AEM Forms
description: Como começar a personalizar a interface do usuário da área de trabalho do AEM Forms.
seo-description: Como começar a personalizar a interface do usuário da área de trabalho do AEM Forms.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---


# Etapas genéricas para personalização do espaço de trabalho AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

As etapas genéricas para executar qualquer personalização são:

1. Faça logon no CRXDE Lite acessando `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Crie uma pasta chamada `ws`em `/apps`, se ela não existir. Clique em **[!UICONTROL Salvar tudo]**.
1. Navegue até `/apps/ws` e navegue até a guia **[!UICONTROL Controle de acesso]**.
1. Na lista **[!UICONTROL Controle de acesso]**, clique em **[!UICONTROL +]** para adicionar uma nova entrada. Clique novamente em **[!UICONTROL +]**.
1. Pesquise e selecione a **[!UICONTROL PERM_WORKSPACE_USER]** Principal.

   ![Selecione o principal PERM_WORKSPACE_USER como parte das etapas genéricas para personalizar a área de trabalho HTML](assets/perm_workspace_user.png)

1. Atribua privilégio `jcr:read` ao Principal.
1. Clique em **[!UICONTROL Salvar tudo]**.
1. Copie os arquivos `GET.jsp` e `html.jsp`da pasta `/libs/ws`para a pasta `/apps/ws`.
1. Copie a pasta `/libs/ws/locales` na pasta `/apps/ws`. Clique em **[!UICONTROL Salvar tudo]**.
1. Atualize as referências e os caminhos relativos no arquivo `GET.jsp`, conforme mostrado abaixo, e clique em **[!UICONTROL Salvar tudo]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Faça o seguinte para personalizações de CSS:

   1. Navegue até a pasta `/apps/ws` e crie uma nova pasta chamada `css`.
   1. Na pasta `css`crie um novo arquivo chamado `newStyle.css`.
   1. Abra `/apps/ws/html`.jsp e altere de

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
   >Coloque a entrada do arquivo CSS definido pelo usuário após a entrada de newStyle.css, como mostrado acima.

1. No arquivo /apps/ws/html.jsp, altere de

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   para

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Faça o seguinte:

   1. Crie uma pasta chamada `js`em `/apps/ws`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Crie uma pasta chamada `libs`em `/apps/ws/js`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Crie uma pasta chamada `jqueryui`em `/apps/ws/js/libs`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Copie `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` para `/apps/ws/js/libs/jqueryui`. Clique em **[!UICONTROL Salvar tudo]**.

1. Faça o seguinte para personalizações de HTML:

   1. Em `/apps/ws/js`, crie uma pasta chamada `runtime`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Em `/apps/ws/js/runtime`, crie uma pasta chamada `templates`. Clique em **[!UICONTROL Salvar tudo]**.
   1. Copie `/libs/ws/js/main.js` para `/apps/ws/js/main.js`.
   1. Copie /libs/ws/js/registry.js para `/apps/ws/js/registry.js`.

1. Clique em **[!UICONTROL Salvar tudo]**, limpar o cache e atualizar a área de trabalho do AEM Forms.

   Acesse o URL `https://[server]:[port]/lc/ws` e faça logon com as credenciais de administrador/senha. O navegador redireciona para `https://[server]:[port]/lc/apps/ws/index.html`.

