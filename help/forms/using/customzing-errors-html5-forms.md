---
title: Personalização de mensagens de erro para formulários HTML5
seo-title: Customizing error messages for HTML5 forms
description: Saiba como personalizar a exibição de mensagens de erro para formulários HTML5, incluindo como alterar sua posição e aparência.
seo-description: Learn how to customize the display of error messages for HTML5 forms including how to change their position and appearance.
uuid: 6f48b64e-858f-4323-ad50-88e25f3c2e3d
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 44e49789-9075-41b3-bce8-03e8efce2d5a
feature: Mobile Forms
exl-id: e8a53976-e9bd-459d-92f5-88527c72428b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---

# Personalização de mensagens de erro para formulários HTML5 {#customizing-error-messages-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Nos formulários HTML5, prontos para uso, as mensagens e avisos de erro têm uma posição e aparência fixas (fonte e cor), o erro é exibido somente para um campo selecionado e apenas um erro é exibido.

O artigo fornece as etapas para personalizar mensagens de erro de formulários do HTML5 para o,

* alterar a aparência e a posição das mensagens de erro. Você pode fazer um erro para aparecer na parte superior, inferior e à direita de qualquer campo.
* exibir mensagens de erro para vários campos em um determinado momento.
* exiba o erro independentemente de um campo estar selecionado ou não.

## Personalização de mensagens de erro  {#customizing-error-messages-nbsp}

Antes de personalizar as mensagens de erro, baixe e extraia o pacote anexado (CustomErrorManager-1.0-SNAPSHOT.zip).

Após extrair o pacote, abra a pasta CustomErrorManager-1.0-SNAPSHOT . Ele contém pastas jcr_root e META-INF. Essas pastas contêm os arquivos CSS e .JS necessários para personalizar a mensagem de erro.

[Obter arquivo](assets/customerrormanager-1.0-snapshot.zip)

### Personalização da posição das mensagens de erro  {#customizing-the-position-of-error-messages-nbsp}

Para personalizar a posição da mensagem de erro, adicione &lt;div> para cada campo de erro e aviso, posicione a variável &lt;div> à esquerda ou à direita e aplique estilos de css na &lt;div> . Para obter etapas detalhadas, consulte o procedimento listado abaixo:

1. Navegue até o `CustomErrorManager-1.0-SNAPSHOT`e abra o `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript` pasta.
1. Abra o `customErrorManager.js` para edição. O `markError` no arquivo aceita os seguintes parâmetros:

   |  |  |
   |---|---|
   | jqWidget | jqWidget é o identificador do widget. |
   | msg | contém a mensagem de erro |
   | tipo | indica se é um erro ou aviso |

1. Na implementação predefinida, mensagens de erro são exibidas à direita do campo . Para que as mensagens de erro apareçam na parte superior, use o seguinte código.

   ```
   markError: function (jqWidget, msg, type) {
               var element = jqWidget.element,                                //Gives the div containing widget
                   pos = $(element).offset(),                          //Calculates the position of the div in the view port
                                                                   msgHeight = xfalib.view.util.TextMetrics.measureExtent(msg).height + 5;  //Calculating the height of the Error Message
                   styles = {};
                   styles.left = pos.left + "px";         // Assign the desired left position using pos.left. Here it is calculated for exact left of the field 
                   styles.top = pos.top - msgHeight + "px";  // Assign the desired top position using pos.top. Here it is calculated for top of the field 
               if (type != "warning") {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the warning div if it is not present already
                       jqWidget.errorDiv=$("<div id='customError'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the warning div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               } else {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the error div if it is not present already
                       jqWidget.errorDiv=$("<div id='customWarning'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the error div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               }
   
           },
   ```

1. Salve e feche o arquivo.
1. Navegue até o `CustomErrorManager-1.0-SNAPSHOT` e crie um arquivo de pastas jcr_root e META-INF . Renomeie o arquivo para CustomErrorManager-1.0-SNAPSHOT.zip.
1. Use o gerenciador de pacotes para fazer upload e instalar o pacote.

## Exibir mensagens de erro para vários campos  {#display-error-messages-for-multiple-fields-nbsp}

Use o pacote anexado para exibir simultaneamente mensagens de erro para todos os campos. Para exibir uma única mensagem de erro, use o perfil padrão.

### Personalização da aparência das mensagens de erro.  {#customizing-the-appearance-of-error-messages-nbsp}

1. Navegue até etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css folder.

1. Abra o arquivo sample.css para edição. O arquivo css contém 2 ids- #customError, #customWarning. É possível usar essas IDs para alterar várias propriedades, como cor, tamanho da fonte etc.

   Use o código a seguir para alterar o tamanho da fonte e a cor das mensagens de erro/aviso.

   ```
   #customError {
   color: #0000FF; // it changes the color of Error Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 24px;  // it changes the font size of Error Message
   z-index:5;
   }
   
   #customWarning {
   color: #00FF00;  // it changes the color of Warning Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 18px;   // it changes the font size of Warning Message
   z-index:5;
   }
   
   Save the changes.
   ```

1. Salve e feche o arquivo.
1. Navegue até a pasta CustomErrorManager-1.0-SNAPSHOT e crie um arquivo de pastas jcr_root e META-INF. Renomeie o arquivo para CustomErrorManager-1.0-SNAPSHOT.zip.
1. Use o gerenciador de pacotes para fazer upload e instalar o pacote.

## Renderize o formulário com o novo perfil.  {#render-the-form-with-the-new-profile-nbsp}

Imediatamente, os formulários html5 usam um perfil padrão: https://&lt;server>/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location=&quot;&quot;>&amp;template=&lt;name of=&quot;&quot; the=&quot;&quot; xdp=&quot;&quot;>

Para exibir um formulário com mensagens de erro personalizadas, renderize o formulário com um perfil de erro: https://&lt;server>/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location=&quot;&quot;>&amp;template=&lt;name of=&quot;&quot; the=&quot;&quot; xdp=&quot;&quot;>

>[!NOTE]
>
>O pacote anexado instala o perfil de erro.
