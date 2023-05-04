---
title: Integração de componentes do espaço de trabalho do AEM Forms em aplicativos da Web
seo-title: Integrating AEM Forms workspace components in web applications
description: Como reutilizar componentes do espaço de trabalho do AEM Forms em seus próprios aplicativos da Web para aproveitar a funcionalidade e fornecer integração rigorosa.
seo-description: How to reuse AEM Forms workspace components in your own webapps to leverage functionality and provide tight integration.
uuid: bb9b8aa0-3f41-4f44-8eb7-944e778ee8a6
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 6be87939-007e-42c7-8a41-e34ac2b8bed4
exl-id: 4e3ed3c8-ef77-432e-ad4d-7d341787cc5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Integração de componentes do espaço de trabalho do AEM Forms em aplicativos da Web {#integrating-aem-forms-workspace-components-in-web-applications}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode usar a área de trabalho do AEM Forms [componentes](/help/forms/using/description-reusable-components.md) em seu próprio aplicativo web. O exemplo de implementação a seguir usa componentes de um pacote dev de espaço de trabalho do AEM Forms instalado em uma instância do CRX™ para criar um aplicativo da Web. Personalize a solução abaixo para atender às suas necessidades específicas. A implementação de exemplo reutiliza `UserInfo`, `FilterList`e `TaskList`componentes dentro de um portal da Web.

1. Faça logon no ambiente CRXDE Lite em `https://[server]:[port]/lc/crx/de/`. Verifique se você tem um pacote de desenvolvimento de espaço de trabalho do AEM Forms instalado.
1. Criar um caminho `/apps/sampleApplication/wscomponents`.
1. Copie css, imagens, js/libs, js/runtime e js/registry.js

   * de `/libs/ws`
   * para `/apps/sampleApplication/wscomponents`.

1. Crie um arquivo demomain.js dentro da pasta /apps/sampleApplication/wscomponents/js . Copie o código de /libs/ws/js/main.js para demomain.js.
1. Em demomain.js, remova o código para inicializar o Roteador e adicione o seguinte código:

   ```
   require(['initializer','runtime/util/usersession'], 
       function(initializer, UserSession) { 
           UserSession.initialize( 
               function() { 
                   // Render all the global components
                   initializer.initGlobal();  
               }); 
       });
   ```

1. Criar um nó em /content por nome `sampleApplication` e tipo `nt:unstructured`. Nas propriedades desse nó, adicione `sling:resourceType` do tipo String e value `sampleApplication`. Na Lista de Controle de Acesso deste nó, adicione uma entrada para `PERM_WORKSPACE_USER` permissão de privilégios jcr:read. Além disso, na Lista de Controle de Acesso de `/apps/sampleApplication` adicionar uma entrada para `PERM_WORKSPACE_USER` permissão de privilégios jcr:read.
1. Em `/apps/sampleApplication/wscomponents/js/registry.js` atualizar caminhos de `/lc/libs/ws/` para `/lc/apps/sampleApplication/wscomponents/` para valores de modelo.
1. No arquivo JSP da página inicial do portal em `/apps/sampleApplication/GET.jsp`, adicione o seguinte código para incluir os componentes necessários dentro do portal.

   ```as3
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div> 
   <div class="filterListView gcomponent" data-name="filterlist"></div> 
   <div class="taskListView gcomponent" data-name="tasklist"></div> 
   ```

   Inclua também os arquivos CSS necessários para os componentes do espaço de trabalho do AEM Forms.

   >[!NOTE]
   >
   >Cada componente é adicionado à tag do componente (tendo um componente de classe) durante a renderização. Certifique-se de que sua página inicial contenha essas tags. Consulte a `html.jsp` arquivo do espaço de trabalho do AEM Forms para saber mais sobre essas tags de controle básicas.

1. Para personalizar os componentes, você pode estender as exibições existentes para o componente desejado da seguinte maneira:

   ```as3
   define([ 
       ‘jquery’, 
       ‘underscore’, 
       ‘backbone’, 
       ‘runtime/views/userinfo'],
       function($, _, Backbone, UserInfo){ 
           var demoUserInfo = UserInfo.extend({ 
               //override the functions to customize the functionality 
               render: function() { 
                   UserInfo.prototype.render.call(this); // call the render function of the super class 
                   … 
                   //other tasks 
                   … 
               } 
           }); 
           return demoUserInfo; 
   });
   ```

1. Modifique o CSS do portal para configurar o layout, o posicionamento e o estilo dos componentes necessários no portal. Por exemplo, você gostaria de manter a cor de fundo como preta para que este portal exiba bem o componente userInfo . Você pode fazer isso alterando a cor do fundo em `/apps/sampleApplication/wscomponents/css/style.css` como se segue:

   ```as3
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC    
       position: relative;
       margin: 0 auto;
   }
   ```
