---
title: Trabalhar com utilitários XMP
seo-title: Trabalhar com utilitários XMP
description: Use os Utilitários XMP APIs do Java e do serviço da Web para importar programaticamente metadados XMP em um documento PDF e recuperar e salvar XMP metadados de um documento PDF.
seo-description: Use os Utilitários XMP APIs do Java e do serviço da Web para importar programaticamente metadados XMP em um documento PDF e recuperar e salvar XMP metadados de um documento PDF.
uuid: 90ce6cef-efe1-456a-8e0c-5ba90249dda0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 01d5677f-5c87-4a6e-987b-8eda9acc0b27
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---


# Trabalhar com XMP Utilitários {#working-with-xmp-utilities}

**Sobre o Serviço de Utilitários XMP**

Os documentos PDF contêm metadados, que são informações sobre o documento como distinto do conteúdo do documento, como texto e gráficos. A Plataforma de metadados extensível do Adobe (XMP) é um padrão para manipular metadados de documento.

O serviço Utilitários de XMP pode recuperar e salvar metadados XMP de documentos PDF e importar XMP metadados para documentos PDF.

Você pode realizar essas tarefas usando o serviço Utilitários XMP:

* Importe metadados em documentos PDF. (Consulte [Importando metadados para documentos PDF](xmp-utilities.md#importing-metadata-into-pdf-documents).)
* Exportar metadados de documentos PDF. (Consulte [Exportar metadados de documentos PDF](xmp-utilities.md#exporting-metadata-from-pdf-documents).)

>[!NOTE]
>
>Para obter mais informações sobre o serviço Utilitários de XMP, consulte [Referência de Serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importação de metadados para documentos PDF {#importing-metadata-into-pdf-documents}

Você pode usar o Java Utilitários XMP e as APIs de serviço da Web para importar XMP metadados de forma programática em um documento PDF. Os metadados fornecem informações sobre um documento PDF, como o autor do documento e palavras-chave relacionadas ao documento. Os metadados podem ser localizados na caixa de diálogo Propriedades do documento, conforme mostrado na ilustração a seguir.

![ww_ww_metadatadialog](assets/ww_ww_metadatadialog.png)

Para importar metadados programaticamente para um documento PDF, você pode usar um documento XML existente que especifica os valores de metadados ou pode usar um objeto do tipo `XMPUtilityMetadata`. (Consulte [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

>[!NOTE]
>
>Esta seção discute como usar um documento XML para importar metadados para um documento PDF.

O código XML a seguir contém valores de metadados que correspondem à ilustração anterior. Por exemplo, observe os itens em negrito, que especificam palavras-chave.

```as3
 <?xpacket begin="?" id="W5M0MpCehiHzreSzNTczkc9d"?> 
 <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 4.2-jc015 52.349034, 2008 Jun 20 00:30:39-PDT (debug)"> 
       <rdf:RDF xmlns:rdf="https://www.w3.org/1999/02/22-rdf-syntax-ns#"> 
          <rdf:Description rdf:about="" 
                xmlns:xmp="https://ns.adobe.com/xap/1.0/"> 
             <xmp:MetadataDate>2008-10-22T10:52:21-04:00</xmp:MetadataDate> 
             <xmp:CreatorTool>AEM Forms</xmp:CreatorTool> 
             <xmp:ModifyDate>2008-10-22T10:52:21-04:00</xmp:ModifyDate> 
             <xmp:CreateDate>2008-02-13T11:00:18-05:00</xmp:CreateDate> 
          </rdf:Description> 
          <rdf:Description rdf:about="" 
                xmlns:pdf="https://ns.adobe.com/pdf/1.3/"> 
             <pdf:Producer>AEM Forms</pdf:Producer> 
             <pdf:Keywords>keyword1, keyword2, keyword3,keyword4</pdf:Keywords> 
          </rdf:Description> 
          <rdf:Description rdf:about="" 
                xmlns:xmpMM="https://ns.adobe.com/xap/1.0/mm/"> 
             <xmpMM:DocumentID>uuid:1cce1f84-331e-4d8d-8538-15441c271dd7</xmpMM:DocumentID> 
             <xmpMM:InstanceID>uuid:cdda0ca6-7c91-4771-9dc9-796c8fe59350</xmpMM:InstanceID> 
          </rdf:Description> 
          <rdf:Description rdf:about="" 
                > 
             <dc:format>application/pdf</dc:format> 
             <dc:description> 
                <rdf:Alt> 
                   <rdf:li xml:lang="x-default">Adobe Designer Sample</rdf:li> 
                </rdf:Alt> 
             </dc:description> 
             <dc:title> 
                <rdf:Alt> 
                   <rdf:li xml:lang="x-default">Grant Application</rdf:li> 
                </rdf:Alt> 
             </dc:title> 
             <dc:creator> 
                <rdf:Seq> 
                   <rdf:li>Tony Blue</rdf:li> 
                </rdf:Seq> 
             </dc:creator> 
             <dc:subject> 
                <rdf:Bag> 
                   <rdf:li>keyword1</rdf:li> 
                   <rdf:li>keyword2</rdf:li> 
                   <rdf:li>keyword3</rdf:li> 
                   <rdf:li>keyword4</rdf:li> 
                </rdf:Bag> 
             </dc:subject> 
          </rdf:Description> 
          <rdf:Description rdf:about="" 
                xmlns:desc="https://ns.adobe.com/xfa/promoted-desc/"> 
             <desc:version rdf:parseType="Resource"> 
                <rdf:value>1.0</rdf:value> 
                <desc:ref>/template/subform[1]</desc:ref> 
             </desc:version> 
             <desc:contact rdf:parseType="Resource"> 
                <rdf:value>Adobe Systems Incorporated</rdf:value> 
                <desc:ref>/template/subform[1]</desc:ref> 
             </desc:contact> 
          </rdf:Description> 
       </rdf:RDF> 
 </x:xmpmeta>
```

>[!NOTE]
>
>Para obter mais informações sobre o serviço Utilitários de XMP, consulte [Referência de Serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para importar metadados de XMP para um documento PDF, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente XMPUUtilityService.
1. Chame a operação de importação de metadados de XMP.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente XMPUtilmentService**

Antes de poder executar programaticamente uma operação Utilitários de XMP, você deve criar um cliente XMPUUtilityService. Com a API do Java, isso é feito criando um objeto `XMPUtilityServiceClient`. Com a API do serviço da Web, isso é feito usando um objeto `XMPUtilityServiceService`.

**Chame a operação de importação de metadados de XMP**

Após criar o cliente de serviço, você pode invocar uma das operações de importação de metadados XMP para importar os metadados XMP para o documento PDF especificado.

**Consulte também:**

[Importar metadados de XMP usando a API do Java](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importação de metadados de XMP usando a API do serviço da Web](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importe metadados de XMP usando a API Java {#import-xmp-metadata-using-the-java-api}

Importe XMP metadados usando a API de utilitários XMP (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente, como adobe-pdfutility-client.jar, no caminho da classe do seu projeto Java.

   >[!NOTE]
   >
   >O arquivo adobe-pdfutility-client.jar contém classes que permitem chamar programaticamente o serviço Utilitários de XMP.

1. Criar um cliente XMPUtilmentService

   Crie um objeto `XMPUtilityServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Chame a operação de importação de metadados de XMP

   Para modificar os metadados de XMP, chame o método `XMPUtilityServiceClient` do objeto ou o método `importMetadata` dele.`importXMP`

   Se você usar o método `importMetadata`, passe os seguintes valores:

   * Um objeto `com.adobe.idp.Document` que representa o arquivo PDF.
   * Um objeto `XMPUtilityMetadata` que contém os metadados a serem importados.

   Se você usar o método `importXMP`, passe os seguintes valores:

   * Um objeto `com.adobe.idp.Document` que representa o arquivo PDF.
   * Um objeto `com.adobe.idp.Document` que representa um arquivo XML que contém os metadados a serem importados.

   Em ambos os casos, o valor retornado é um objeto `com.adobe.idp.Document` que representa o arquivo PDF com os metadados recém-importados. Em seguida, você pode salvar esse objeto em disco.

**Consulte também:**

[Importação de metadados para documentos PDF](xmp-utilities.md#importing-metadata-into-pdf-documents)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importação de metadados de XMP usando a API do serviço da Web {#importing-xmp-metadata-using-the-web-service-api}

Para importar XMP metadados de maneira programática usando a API do serviço da Web XMP Utilitários, execute as seguintes tarefas:

1. Incluir arquivos de projeto

   * Crie uma assemblagem de cliente Microsoft .NET que consome o ficheiro WSDL do serviço Utilitários XMP. (Consulte [Chamar AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Faça referência ao assembly do cliente Microsoft .NET. (Consulte [Criando um assembly de cliente .NET que usa a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Criar um cliente XMPUtilmentService

   Crie um objeto `XMPUtilityServiceService` usando o construtor de classe de proxy.

1. Chame a operação de importação de metadados de XMP

   Para modificar os metadados de XMP, chame o método `XMPUtilityServiceService` do objeto ou o método `importMetadata` dele.`importXMP`

   Se você usar o método `importMetadata`, passe os seguintes valores:

   * Um objeto `BLOB` que representa o arquivo PDF.
   * Um objeto `XMPUtilityMetadata` que contém os metadados a serem importados.

   Se você usar o método `importXMP`, passe os seguintes valores:

   * Um objeto `BLOB` que representa o arquivo PDF.
   * Um objeto `BLOB` que representa um arquivo XML que contém os metadados a serem importados.

   Em ambos os casos, o valor retornado é um objeto `BLOB` que representa o arquivo PDF com os metadados recém-importados. Em seguida, você pode salvar esse objeto em disco.

**Consulte também:**

[Importação de metadados para documentos PDF](xmp-utilities.md#importing-metadata-into-pdf-documents)

<!--REVIEW: [Quick Start (Base64): Importing XMP metadata using the web service API](unresolvedlink-lc-qs-xmp-utilities-xu.xml#ws624e3cba99b79e12e69a9941333732bac8-7be8.2)-->

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Exportar metadados de documentos PDF {#exporting-metadata-from-pdf-documents}

Você pode usar o Java Utilitários XMP e as APIs de serviço da Web para recuperar e salvar programaticamente os metadados XMP de um documento PDF.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Utilitários de XMP, consulte [Referência de Serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para exportar XMP metadados de um documento PDF, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente XMPUUtilityService.
1. Chame a operação de exportação de metadados de XMP.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente XMPUtilmentService**

Antes de poder executar programaticamente uma operação Utilitários de XMP, você deve criar um cliente XMPUUtilityService. Com o Java AP, se isso for feito criando um objeto `XMPUtilityServiceClient`. Com a API do serviço da Web, isso é feito usando um objeto `XMPUtilityServiceService`.

**Chame a operação de exportação de metadados de XMP**

Após criar o cliente de serviço, você pode invocar uma das operações de exportação de metadados de XMP, que pode ser usada para inspecionar os metadados de XMP ou salvá-los em disco.

**Consulte também:**

[Importar metadados de XMP usando a API do Java](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importação de metadados de XMP usando a API do serviço da Web](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportar metadados de XMP usando a API Java {#export-xmp-metadata-using-the-java-api}

Exporte XMP metadados usando a API de utilitários XMP (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente, como adobe-pdfutility-client.jar, no caminho da classe do seu projeto Java.

   >[!NOTE]
   >
   >O arquivo adobe-pdfutility-client.jar contém classes que permitem chamar programaticamente o serviço Utilitário de XMP.

1. Criar um cliente XMPUtilmentService

   Crie um objeto `XMPUtilityServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Chame a operação de importação de metadados de XMP

   Para inspecionar os metadados de XMP, chame o método `XMPUtilityServiceClient` do objeto e passe um objeto `com.adobe.idp.Document` que represente o arquivo PDF. `exportMetadata` O método retorna um objeto `XMPUtilityMetadata` que contém os metadados recuperados.

   Para recuperar e salvar os metadados XMP, chame o método `XMPUtilityServiceClient` do objeto e passe um objeto `com.adobe.idp.Document` que represente o arquivo PDF. `exportXMP` O método retorna um objeto `com.adobe.idp.Document` que contém os metadados recuperados, que podem ser salvos posteriormente em disco como um arquivo XML.

**Consulte também:**

[Exportar metadados de documentos PDF](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportar metadados XMP usando a API de serviço da Web {#export-xmp-metadata-using-the-web-service-api}

Exporte XMP metadados usando a API de Utilitários XMP (serviço da Web):

1. Incluir arquivos de projeto

   * Crie uma assemblagem de cliente Microsoft .NET que consome o ficheiro WSDL do serviço Utilitários XMP.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar um cliente XMPUtilmentService

   Crie um objeto `XMPUtilityServiceService` usando o construtor de classe de proxy.

1. Chame a operação de importação de metadados de XMP

   Para inspecionar os metadados de XMP, chame o método `XMPUtilityServiceClient` do objeto e passe um objeto `BLOB` que represente o arquivo PDF. `exportMetadata` O método retorna um objeto `XMPUtilityMetadata` que contém os metadados recuperados.

   Para recuperar e salvar os metadados XMP, chame o método `XMPUtilityServiceClient` do objeto e passe um objeto `BLOB` que represente o arquivo PDF. `exportXMP` O método retorna um objeto `BLOB` que contém os metadados recuperados, que podem ser salvos posteriormente em disco como um arquivo XML.

**Consulte também:**

[Exportar metadados de documentos PDF](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
