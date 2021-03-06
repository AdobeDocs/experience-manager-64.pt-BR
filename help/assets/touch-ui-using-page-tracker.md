---
title: Usar o rastreador de página e incorporar código em páginas da Web
description: Saiba como incluir o Rastreador de página e incorporar códigos JavaScript no código do site para permitir que o Adobe Analytics capture dados de uso em ativos.
contentOwner: AG
feature: Asset Reports
role: Architect,Admin
exl-id: b0154c9c-a671-43fb-8733-274a35307a34
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Usar o rastreador de página e incorporar código em páginas da Web {#using-page-tracker-and-embed-code-in-web-pages}

O Rastreador de página é uma parte do código JavaScript que você inclui no código de sites de terceiros para permitir que o Adobe Analytics capture dados de uso em ativos do Adobe Experience Manager nesses sites.

Para capturar eventos, como cliques e assim por diante, específicos dos ativos, você também inclui o código Incorporar no código de sites de terceiros.

O código de exemplo a seguir mostra como uma página da Web que contém o código do Rastreador de página e do Código de inserção se parece com:

```
<!DOCTYPE html>
<html>
    <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in milliseconds
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","xxxx","xxx","list1","eVar3","event8","event7");
            </script>

    </head>

    <body>

                                <img
            src="https://10.41.52.147:4502/xxxx/content/dam/test/abc.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
                <img
                    src="http://localhost/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
</html>
```

## Adicionar o código do rastreador de página {#adding-page-tracker-code}

Você adiciona o código do rastreador de página na seção de cabeçalho do código do site. O trecho de código a seguir exibe o código do Rastreador de página incluído em uma página da Web de exemplo:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>
 </head>
```

## Adicionar código incorporado {#adding-embed-code}

Você adiciona o código incorporado no corpo do código do site. O trecho de código a seguir exibe o código Incorporado incluído em uma página da Web de amostra:

```xml
<body>

      <img
            src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
           <img
                    src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
```
