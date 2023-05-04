---
title: Incorporar formulário adaptável na página externa da Web
seo-title: Embed adaptive form in external web page
description: Saiba como incorporar um formulário adaptável em uma página da Web externa
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
feature: Adaptive Forms
exl-id: 84a46197-9933-4b94-a8e3-e7baf9c644b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 2%

---

# Incorporar formulário adaptável na página externa da Web{#embed-adaptive-form-in-external-web-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como incorporar um formulário adaptável em uma página da Web externa

Você pode [Incorporar formulários adaptáveis ao AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) ou uma página da Web hospedada fora do AEM. O formulário adaptável incorporado é totalmente funcional e os usuários podem preencher e enviar o formulário sem sair da página. Ajuda o usuário a permanecer no contexto de outros elementos na página da Web e interagir simultaneamente com o formulário.

## Pré-requisitos {#prerequisites}

Execute as seguintes etapas antes de incorporar um formulário adaptável a um site externo:

* Publique o formulário adaptável na instância de publicação do AEM.
* Crie ou identifique uma página da Web no seu site para hospedar o formulário adaptável. Certifique-se de que a página da Web possa [ler arquivos jQuery de um CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) ou tem uma cópia local do jQuery incorporada. jQuery é necessário para renderizar um formulário adaptável.
* Quando AEM servidor e a página da Web estiverem em domínios diferentes, execute as etapas listadas na seção , [permitir que o AEM Forms forneça formulários adaptáveis a um site de domínio cruzado](#cross-domain-sites).
* [Configurar proxy reverso](#reveseproxy) para permitir a comunicação entre a página externa e o servidor do AEM Forms.

## Incorporar formulário adaptável {#embed-adaptive-form}

É possível incorporar um formulário adaptável inserindo algumas linhas de JavaScript na página da Web. A API no código envia uma solicitação HTTP para o servidor de AEM para recursos de formulário adaptáveis e injeta o formulário adaptável no contêiner de formulário especificado. Este é um exemplo de código para incorporar um formulário adaptável a uma página externa. Não use o código como ele está em um ambiente de produção. Personalize o código para se adequar ao seu site, como usar um iFrame para sites que usam sua própria versão do jQuery. O uso do iFrame ajuda a evitar conflitos nas versões do jQuery:


1. Incorpore o seguinte código a uma página da Web no seu site:

   ```html
   <!doctype html>
   <html>
   <head>
    <title>This is the title of the webpage!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
   </head>
   <body>
   <div class="customafsection"/>
   <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
        // options.path refers to the publish URL of the adaptive form
        // For Example: http:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
        // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path 
        var path = options.path;
        path += "/jcr:content/guideContainer.html";
        $.ajax({
            url  : path ,
            type : "GET",
            data : {
                // Set the wcmmode to be disabled
                wcmmode : "disabled"
                // Set the data reference, if any
               // "dataRef": options.dataRef
                // Specify a different theme for the form object
              //  "themeOverride" : options.themepath
            },
            async: false,
            success: function (data) {
                // If jquery is loaded, set the inner html of the container
                // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                // For example: document.getElementById().innerHTML
                if(window.$ && options.CSS_Selector){
                    // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                    $(options.CSS_Selector).html(data);
                }
            },
            error: function (data) {
                // any error handler
            }
        });
    } else {
        if (typeof(console) !== "undefined") {
            console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
        }
    }
    }(options);
   
    </script>
   </body>
   </html>
   ```

1. No código incorporado:

   * Alterar valor da variável `options.path` com o caminho da URL de publicação do formulário adaptável. Se o servidor AEM estiver em execução em um caminho de contexto, verifique se o URL inclui o caminho de contexto. Por exemplo, o código acima e adaptável do residem no mesmo servidor do aem forms, de modo que o exemplo usa o caminho de contexto do formulário adaptável /content/forms/af/locbasic.html.
   * Substituir `options.dataRef` com atributos a serem enviados com o URL. Você pode usar a variável dataref para [preencher previamente um formulário adaptável](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Substituir `options.themePath` com o caminho para um tema diferente do configurado na forma adaptável. Como alternativa, você pode especificar o caminho do tema usando o atributo de solicitação.
   * `CSS_Selector` é o seletor de CSS do contêiner de formulário no qual o formulário adaptável está incorporado. Por exemplo, a classe css .customafsection é o seletor de CSS no exemplo acima.

O formulário adaptável é incorporado na página da Web. Observe o seguinte na forma adaptável incorporada:

* O cabeçalho e o rodapé no formulário adaptável original não estão incluídos no formulário incorporado.
* Os rascunhos e os formulários enviados estão disponíveis na guia Rascunhos e envios no Portal do Forms.
* A ação Enviar configurada no formulário adaptável original é mantida no formulário incorporado.
* As regras de formulário adaptável são retidas e totalmente funcionais no formulário incorporado.
* O direcionamento de experiência e os testes A/B configurados no formulário adaptável original não funcionam no formulário incorporado.
* Se o Adobe Analytics estiver configurado no formulário original, os dados de análise serão capturados no servidor do Adobe Analytics. No entanto, não está disponível no relatório de análise do Forms.

## Proxy reverso da configuração  {#reveseproxy}

A página da Web externa que incorpora o formulário adaptável envia solicitações ao servidor de AEM, que normalmente fica atrás do firewall em uma rede privada. Para garantir que as solicitações sejam direcionadas com segurança para o servidor AEM, é recomendável configurar um servidor proxy reverso.

Vamos ver um exemplo de como você pode configurar um servidor proxy reverso do Apache 2.4 sem o dispatcher. Neste exemplo, você hospedará o servidor AEM com `/forms` caminho e mapa de contexto `/forms` para o proxy reverso. Assegura que qualquer pedido de `/forms` no servidor Apache são direcionados para a instância do AEM. Essa topologia ajuda a reduzir o número de regras na camada do dispatcher, pois todas as solicitações têm o prefixo `/forms` para o servidor AEM.

1. Abra o `httpd.conf` arquivo de configuração e exclua o comentário das seguintes linhas de código. Como alternativa, você pode adicionar essas linhas de código no arquivo .

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configure regras de proxy adicionando as seguintes linhas de código no `httpd-proxy.conf` arquivo de configuração.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Substituir `[AEM_Instance]` com o URL de publicação do servidor AEM nas regras.

Se você não montar o servidor AEM em um caminho de contexto, as regras de proxy na camada Apache serão as seguintes:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Se você configurar qualquer outra topologia, adicione o envio, o preenchimento prévio e outros URLs à lista de permissões na camada do dispatcher.

## Práticas recomendadas {#best-practices}

Ao incorporar um formulário adaptável em uma página da Web, considere as seguintes práticas recomendadas:

* Verifique se as regras de estilo definidas no CSS da página da Web não estão em conflito com o CSS do objeto de formulário. Para evitar conflitos, é possível reutilizar o CSS da página da Web no tema do formulário adaptável usando AEM biblioteca do cliente. Para obter informações sobre como usar a biblioteca do cliente em temas de forma adaptável, consulte [Temas no AEM Forms](/help/forms/using/themes.md).
* Faça com que o contêiner de formulário na página da Web use toda a largura da janela. Isso garante que as regras de CSS configuradas para dispositivos móveis funcionem sem alterações. Se o contêiner de formulário não tiver a largura total da janela, será necessário gravar CSS personalizado para adaptar o formulário a diferentes dispositivos móveis.
* Use  [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API para obter a representação XML ou JSON dos dados de formulário no cliente.
* Use [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API para descarregar o formulário adaptável do HTML DOM.
* Configure o cabeçalho access-control-origin ao enviar resposta de AEM servidor.

## Permitir que o AEM Forms forneça formulários adaptáveis a um site de domínio cruzado  {#cross-domain-sites}

1. Em AEM instância de publicação, vá para AEM Web Console Configuration Manager em `http://[server]:[port]/system/console/configMgr`.
1. Localize e abra o **Referenciador do Apache Sling** Configuração do filtro.
1. No **Hosts permitidos** , especifique o domínio em que a página da Web está. Ela permite que o host faça solicitações do POST para o servidor AEM. Também é possível usar a expressão regular para especificar uma série de domínios externos de aplicativos.
