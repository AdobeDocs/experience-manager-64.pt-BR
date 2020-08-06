---
title: Criar uma nova tela de login
seo-title: Criar uma nova tela de login
description: Como modificar a página de logon dos módulos de LiveCycle, por exemplo, da área de trabalho da AEM Forms ou do Forms Manager.
seo-description: Como modificar a página de logon dos módulos de LiveCycle, por exemplo, da área de trabalho da AEM Forms ou do Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---


# Criar uma nova tela de login {#creating-a-new-login-screen}

Você pode modificar a tela de logon de todos os módulos AEM Forms que usam a tela de logon AEM Forms. Por exemplo, as modificações afetam a tela de logon da área de trabalho do Forms Manager e do AEM Forms.

## Pré-requisitos {#prerequisite}

1. Faça logon com permissões `/lc/crx/de` de administrador.
1. Execute as seguintes ações:

   1. Replicar a estrutura hierárquica: de `/libs/livecycle/core/content` na `/apps/livecycle/core/content`. Mantenha as mesmas propriedades (nó/pasta) e controle de acesso.
   1. Copie a pasta de conteúdo: de `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Exclua o conteúdo da `/apps/livecycle/core` pasta.

1. Execute estas ações:

   1. Replicar a estrutura hierárquica: de `/libs/livecycle/core/components/login` na `/apps/livecycle/core/components/login`. Mantenha as mesmas propriedades (nó/pasta) e controle de acesso.
   1. Copie a pasta de componentes: de `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Exclua o conteúdo da pasta: `/apps/livecycle/core/components/login`.

## Adicionar uma nova localidade {#adding-a-new-locale}

1. Copie a `i18n` pasta:

   * de `/libs/livecycle/core/components/login`
   * para `/apps/livecycle/core/components/login`

1. Exclua todas as pastas dentro `i18n` exceto uma, digamos `en`.
1. Na pasta `en`, execute estas ações:

   1. Renomeie a pasta para o nome da localidade que deseja suportar. Por exemplo, `ar`.
   1. Altere o `jcr:language` valor da propriedade para `ar`(para a `ar` pasta).

   >[!NOTE]
   >
   >Se locale for uma combinação de código de país de idioma, digamos, `ar-DZ`altere o nome da pasta e o valor da propriedade para `ar-DZ`.

1. Copiar `login.jsp`:

   * de `/libs/livecycle/core/components/login`
   * para `/apps/livecycle/core/components/login`

1. Modifique o seguinte trecho de código para `/apps/livecycle/core/components/login/login.jsp`:

   ***Localidade é código de idioma***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***A localidade é o código do país do idioma***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Para alterar a localidade padrão***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## Adicionar novo texto ou modificar um texto existente {#adding-new-text-or-modifying-existing-text}

1. Copiar `i18n` pasta:

   * de `/libs/livecycle/core/components/login`
   * para `/apps/livecycle/core/components/login`

1. Agora, modifique o valor da propriedade `sling:message` do nó (sob a pasta de código de localidade desejada) para o qual você deseja alterar o texto. A tradução é feita por meio da chave mencionada no valor da `sling:key` propriedade do nó.
1. Para adicionar um novo par de valores chave, execute as seguintes ações. Verifique um exemplo na captura de tela a seguir.

   1. Crie um nó do tipo `sling:MessageEntry`, ou copie um nó existente e renomeie-o em todas as pastas de localidade.
   1. Copiar `login.jsp` :

      * de `/libs/livecycle/core/components/login`
      * para `/apps/livecycle/core/components/login`
   1. Modificar `/apps/livecycle/core/components/login/login.jsp` para incorporar o texto recém-adicionado.

   ![captura](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## Adicionar novo estilo ou modificar um estilo existente {#adding-new-style-or-modifying-existing-style}

1. Copy `login` node:

   * de `/libs/livecycle/core/content`
   * para `/apps/livecycle/core/content`

1. Excluir arquivos `login.js` e `jquery-1.8.0.min.js`, do nó `/apps/livecycle/core/content/login.`
1. Modifique os estilos no arquivo CSS.
1. Para adicionar novos estilos:

   1. Adicionar novos estilos a `/apps/livecycle/core/content/login/login.css`
   1. Copiar `login.jsp`

      * de `/libs/livecycle/core/components/login`
      * para `/apps/livecycle/core/components/login`
   1. Modifique `/apps/livecycle/core/components/login/login.jsp` para incorporar os estilos recém-adicionados.


1. Por exemplo:

   * Adicione o seguinte a `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Modifique o seguinte em /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Se as imagens existentes em `/apps/livecycle/core/content/login` (copiadas de `/libs/livecycle/core/content/login`) forem removidas, remova as referências correspondentes em CSS.

## Adicionar novas imagens {#add-new-images}

1. Siga as etapas de Adicionar novo estilo ou modificar o estilo existente (documentado acima).
1. Adicione novas imagens em `/apps/livecycle/core/content/login`. Para adicionar imagem:

   1. Instale o cliente WebDAV.
   1. Navegue até a `/apps/livecycle/core/content/login` pasta, usando o cliente webDAV. Para obter mais informações, consulte: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Adicione novas imagens.

1. Adicione novos estilos `/apps/livecycle/core/content/login/login.css,` correspondentes a novas imagens adicionadas em `/apps/livecycle/core/content/login`.
1. Use os novos estilos em `login.jsp` em `/apps/livecycle/core/components`.
1. Por exemplo:

   * Adicione o seguinte a `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Modifique o seguinte em /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
