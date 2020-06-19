---
title: Incorporar formulário adaptável na página da Web externa
seo-title: Incorporar formulário adaptável na página da Web externa
description: Saiba como incorporar um formulário adaptável em uma página da Web externa
seo-description: Saiba como incorporar um formulário adaptável em uma página da Web HTML externa
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---


# Incorporar formulário adaptável na página da Web externa{#embed-adaptive-form-in-external-web-page}

Saiba como incorporar um formulário adaptável em uma página da Web externa

Você pode [Incorporar formulário adaptável na página AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) ou em uma página da Web hospedada fora do AEM. O formulário adaptativo incorporado está totalmente funcional e os usuários podem preencher e enviar o formulário sem sair da página. Ajuda o usuário a permanecer no contexto de outros elementos na página da Web e a interagir simultaneamente com o formulário.

## Pré-requisitos {#prerequisites}

Execute as seguintes etapas antes de incorporar um formulário adaptável a um site externo:

* Publique o formulário adaptável na instância AEM Publish.
* Crie ou identifique uma página da Web em seu site para hospedar o formulário adaptável. Certifique-se de que a página da Web possa [ler arquivos jQuery de um CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) ou tenha uma cópia local do jQuery incorporada. jQuery é necessário para renderizar um formulário adaptável.
* Quando o servidor AEM e a página da Web estiverem em domínios diferentes, execute as etapas listadas na seção, [ative o AEM Forms para fornecer formulários adaptáveis a um site](#cross-domain-sites)entre domínios.
* [Configure o proxy](#reveseproxy) reverso para ativar a comunicação entre a página externa e o servidor de AEM Forms.

## Incorporar formulário adaptativo {#embed-adaptive-form}

É possível incorporar um formulário adaptável inserindo algumas linhas do JavaScript na página da Web. A API no código envia uma solicitação HTTP ao servidor AEM para recursos de formulário adaptável e injeta o formulário adaptável no container de formulário especificado. Este é um exemplo de código para incorporar um formulário adaptável a uma página externa. Não use o código como ele está em um ambiente de produção. Personalize o código de acordo com seu site, como usar um iFrame para sites que usam sua própria versão do jQuery. O uso do iFrame ajuda a evitar conflitos nas versões do jQuery:


1. Incorpore o seguinte código a uma página da Web em seu site:

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Este é o título da página da web!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>Esta seção é substituída pelo formulário adaptável.</p>


    &lt;script>opções de
    var = {caminho:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;&quot;, caminho:&quot;, CSS_Seletor:&quot;.customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
    /// options.path se refere ao URL de publicação formulário
    adaptável// Por exemplo: http:myserver:4503/content/forms/af/ABC, onde ABC é o formulário
    adaptável// Nota: Se o servidor AEM estiver sendo executado em um caminho de contexto, o URL do formulário adaptável deverá conter o caminho do
    caminho de contexto = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url : path,
    type : &quot;GET&quot;,
    dados: {
    // Defina wcmmode como
    disabledwcmmode : &quot;disabled&quot;
    // Defina a referência de dados, se houver
    / &quot;dataRef&quot;: options.dataRef
    // Especifique um tema diferente para o objeto
    de formulário// &quot;subjectOverride&quot; : options.themepath
    },
    async: false,
    success: função (data) {
    // Se jquery for carregada, defina o html interno do container
    // Se jquery não for carregado, use as APIs fornecidas pelo documento para definir o HTML interno, mas essas APIs não avaliariam a tag do script em HTML de acordo com as especificações
    do HTML5/ Por exemplo: documento.getElementById().
    innerHTMLif(window).$ &amp;&amp; options.CSS_Selector){
    / API HTML do jquery extrai as tags, atualiza o DOM e avalia o código incorporado na tag do script.
    $(options.CSS_Seletor).html(data);
    }
    },
    erro: function (data) {
    // qualquer manipulador
    de erros}
    });
    } else {
    if (typeof(console) !== &quot;undefined&quot;) {
    console.log(&quot;Path of Adaptive Form not specified to loadAdaptiveForm&quot;);
    }
    }
    }(opções);
    
    &lt;/script>
</body>
</html>
   ```

1. No código incorporado:

   * Altere o valor da `options.path` variável com o caminho do URL de publicação do formulário adaptável. Se o servidor AEM estiver sendo executado em um caminho de contexto, verifique se o URL inclui o caminho de contexto. Por exemplo, o código acima e adaptável de residir no mesmo servidor de formulários aem, de modo que o exemplo usa o caminho de contexto de formulário adaptável /content/forms/af/locbasic.html.
   * Substituir `options.dataRef` por atributos para passar pelo URL. É possível usar a variável dataref para [preencher previamente um formulário](/help/forms/using/prepopulate-adaptive-form-fields.md)adaptável.
   * Substitua `options.themePath` pelo caminho para um tema diferente do configurado no formulário adaptável. Como alternativa, você pode especificar o caminho do tema usando o atributo de solicitação.
   * `CSS_Selector` é o seletor de CSS do container de formulário no qual o formulário adaptável está incorporado. Por exemplo, a classe css .customafsection é o seletor de CSS no exemplo acima.

O formulário adaptável é incorporado na página da Web. Observe o seguinte na forma adaptativa incorporada:

* O cabeçalho e o rodapé no formulário adaptativo original não estão incluídos no formulário incorporado.
* Os rascunhos e formulários enviados estão disponíveis na guia Rascunhos e envios no Portal de formulários.
* A ação Enviar configurada no formulário adaptável original é retida no formulário incorporado.
* As regras de formulário adaptável são retidas e totalmente funcionais no formulário incorporado.
* O direcionamento de experiência e os testes A/B configurados no formulário adaptativo original não funcionam no formulário incorporado.
* Se o Adobe Analytics estiver configurado no formulário original, os dados de análise serão capturados no servidor Adobe Analytics. No entanto, ele não está disponível no relatório de análise do Forms.

## Proxy reverso da configuração  {#reveseproxy}

A página da Web externa que incorpora o formulário adaptativo envia solicitações ao servidor AEM, que normalmente fica atrás do firewall em uma rede privada. Para garantir que as solicitações sejam direcionadas com segurança para o servidor AEM, é recomendável configurar um servidor proxy reverso.

Vamos ver um exemplo de como você pode configurar um servidor proxy reverso Apache 2.4 sem despachante. Neste exemplo, você hospedará o servidor AEM com o caminho de `/forms` contexto e mapeará `/forms` o proxy reverso. Ela garante que qualquer solicitação para `/forms` o servidor Apache seja direcionada para a instância do AEM. Essa topologia ajuda a reduzir o número de regras na camada do despachante, já que todas as solicitações com prefixo `/forms` de rota para o servidor AEM.

1. Abra o arquivo de `httpd.conf` configuração e exclua as barras de comentário das seguintes linhas de código. Como alternativa, você pode adicionar essas linhas de código no arquivo.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configure as regras de proxy adicionando as seguintes linhas de código no arquivo de `httpd-proxy.conf` configuração.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Substitua `[AEM_Instance`] pelo URL de publicação do servidor AEM nas regras.

Se você não montar o servidor AEM em um caminho de contexto, as regras de proxy na camada Apache serão as seguintes:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Se você configurar qualquer outra topologia, adicione os URLs de envio, preenchimento prévio e outros à lista permitida na camada do despachante.

## Best practices {#best-practices}

Ao incorporar um formulário adaptável em uma página da Web, considere as seguintes práticas recomendadas:

* Certifique-se de que as regras de estilização definidas na página da Web CSS não entrem em conflito com o objeto de formulário CSS. Para evitar conflitos, é possível reutilizar a página da Web CSS no tema do formulário adaptável usando a biblioteca do cliente AEM. Para obter informações sobre como usar a biblioteca do cliente em temas de formulário adaptáveis, consulte [Temas em AEM Forms](/help/forms/using/themes.md).
* Faça com que o container de formulário na página da Web use toda a largura da janela. Isso garante que as regras de CSS configuradas para dispositivos móveis funcionem sem alterações. Se o container de formulário não tiver a largura total da janela, será necessário gravar um CSS personalizado para fazer com que o formulário se adapte a diferentes dispositivos móveis.
* Use a API [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para obter a representação XML ou JSON dos dados do formulário no cliente.
* Use a API [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) para descarregar o formulário adaptável do DOM HTML.
* Configure o cabeçalho access-control-origem ao enviar resposta do servidor AEM.

## Permitir que os AEM Forms disponibilizem formulários adaptáveis para um site entre domínios  {#cross-domain-sites}

1. Na instância do autor de AEM, vá para Gerenciador de configuração do console da Web de AEM em `http://[server]:[port]/system/console/configMgr`.
1. Localize e abra a configuração do Filtro de Quem indicou **** Apache Sling.
1. No campo Hosts **** permitidos, especifique o domínio onde a página da Web está. Ela permite que o host faça solicitações POST ao servidor AEM. Também é possível usar expressão regular para especificar uma série de domínios externos de aplicativos.