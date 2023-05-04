---
title: Serviço ConvertPDF
seo-title: ConvertPDF Service
description: Use o serviço AEM Forms ConvertPDF para converter documentos PDF em arquivos PostScript ou de imagem.
seo-description: Use AEM Forms ConvertPDF service to convert PDF documents to PostScript or image files.
uuid: 7fa94c8c-485b-4a77-bcd3-ed716e3cf316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 5ec4f0ec-a9fd-4571-9b9a-278f4622c028
exl-id: a6fe7794-3c31-4706-9e23-fe63a506b0bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 2%

---

# Serviço ConvertPDF {#convertpdf-service}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O serviço Convert PDF converte documentos PDF em arquivos PostScript ou de imagem (JPEG, JPEG 2000, PNG e TIFF). A conversão de um documento PDF em PostScript é útil para a impressão automática baseada em servidor em qualquer impressora PostScript. A conversão de um documento PDF em um arquivo TIFF de várias páginas é prática para arquivar documentos em sistemas de gerenciamento de conteúdo que não oferecem suporte a documentos PDF.

Você pode fazer o seguinte com o serviço Converter PDF:

* Converta documentos PDF para PostScript. Ao converter para PostScript, você pode usar a operação de conversão para especificar o documento de origem e se deve ser convertido para o nível 2 ou 3 do PostScript. O documento do PDF que você converte em um arquivo PostScript deve ser não interativo.
* Converta documentos PDF em formatos JPEG, JPEG 2000, PNG e TIFF image. Ao converter para qualquer um desses formatos de imagem, você pode usar a operação de conversão para especificar o documento de origem e uma especificação de opções de imagem. A especificação contém várias preferências, como formato de conversão de imagem, resolução de imagem e conversão de cores.

## Configurar propriedades do serviço   {#properties}

Você pode usar o **Serviço ConvertPDF do AEMFD** no console AEM para configurar as propriedades desse serviço. O URL padrão AEM console é `https://[host]:[port]/system/console/configMgr`.

## Uso do serviço {#using-the-service}

O serviço ConvertPDF fornece as duas APIs a seguir:

* **[toPS](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: Converte um documento PDF em um arquivo PostScript.

* **[toImage](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: Converte um documento PDF em um arquivo de imagem. Os formatos de imagem suportados são JPEG, JPEG2000, PNG e TIFF.

### Uso da API do paraPS com JSP ou Servlets {#using-tops-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToPSOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.PSLevel,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript langauge
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### Uso da API toImage com um JSP ou Servlets {#using-toimage-api-with-a-jsp-or-servlets}

```java
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToImageOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.ImageConvertFormat,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
 String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for 
 // the flat PDF file which needs to be converted 
 // to image

 Document inputPDF = new Document(documentPath);

 // options object to pass to toImage API
 ToImageOptionsSpec toImageOptions = new ToImageOptionsSpec();

 // mandatory option to pass, image format
 toImageOptions.setImageConvertFormat(ImageConvertFormat.JPEG);

 // invoke toImage method to convert inputPDF to Image
 List<Document> convertedImages = cpdfService.toImage(inputPDF, toImageOptions);

 // save converted image files to disk
 for(int i=0;i<convertedImages.size();i++){
     Document pageImage = convertedImages.get(i);
     pageImage.copyToFile(new File("C:/temp/out_"+(i+1)+".jpeg"));
 }

%>
```

### Uso do Serviço ConvertPDF com fluxos de trabalho de AEM {#using-convertpdf-service-with-aem-workflows}

A execução do serviço ConvertPDF a partir de um fluxo de trabalho é semelhante à execução a partir do JSP/Servlet.

A única diferença é executar o serviço a partir do JSP/Servlet. O objeto do documento recupera automaticamente uma instância do objeto ResourceResolver a partir do objeto ResourceResolverHelper. Este mecanismo automático\
não funciona quando o código é chamado de um workflow. Para um workflow, transmita explicitamente uma instância do objeto ResourceResolver para o construtor da classe Document. Em seguida, o objeto Documento usa\
O objeto ResourceResolver foi fornecido para ler o conteúdo do repositório.

O seguinte processo de fluxo de trabalho de amostra converte o documento de entrada em um documento PostScript. O código é gravado no ECMAScript e o documento é passado como carga útil do workflow:

```
/*
 * Imports 
 */
var ConvertPdfService = Packages.com.adobe.fd.cpdf.api.ConvertPdfService;
var ToPSOptionsSpec = Packages.com.adobe.fd.cpdf.api.ToPSOptionsSpec;
var PSLevel = Packages.com.adobe.fd.cpdf.api.enumeration.PSLevel;
var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to ConvertPdfService
var cpdfService = sling.getService(ConvertPdfService);

/*
 * workflow payload and path to it
 */
var payload = graniteWorkItem.getWorkflowData().getPayload();
var payload_path = payload.toString();

/* Create resource resolver using current session 
 * this resource resolver needs to be passed to Document
 * object constructor when file is to be read from 
 * crx repository. 
 */

/* get ResourceResolverFactory service reference , used 
 * to construct resource resolver
 */
var resourceResolverFactory = sling.getService(ResourceResolverFactory);

var authInfo = {
    "user.jcr.session":graniteWorkflowSession.getSession()
};

var resourceResolver = resourceResolverFactory.getResourceResolver(authInfo);

// Create Document object from payload_path 
var inputDocument = new Document(payload_path, resourceResolver);

// options object to be passed to toPS operation
var toPSOptions = new ToPSOptionsSpec();

// Set PostScript Language Three
toPSOptions.setPsLevel(PSLevel.LEVEL_3);

// invoke toPS operation to convert inputDocument to PS
var convertedPS = cpdfService.toPS(inputDocument, toPSOptions);

// save converted PostScript file to disk
convertedPS.copyToFile(new File("C:/temp/out.ps"));
```
