---
title: Conversão de Postscript em documentos PDF
seo-title: Conversão de Postscript em documentos PDF
description: Use o serviço Distiller para converter arquivos PostScript®, Encapsulated PostScript (EPS) e PRN em arquivos PDF compactos, confiáveis e mais seguros em uma rede. O serviço Distiller converte grandes volumes de documentos impressos em documentos eletrônicos, como faturas e declarações usando a API do Java e a API do serviço da Web.
seo-description: Use o serviço Distiller para converter arquivos PostScript®, Encapsulated PostScript (EPS) e PRN em arquivos PDF compactos, confiáveis e mais seguros em uma rede. O serviço Distiller converte grandes volumes de documentos impressos em documentos eletrônicos, como faturas e declarações usando a API do Java e a API do serviço da Web.
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 0%

---


# Convertendo Postscript em documentos PDF {#converting-postscript-to-pdf-documents}

## Sobre o Distiller Service {#about-the-distiller-service}

O serviço Distiller® converte arquivos PostScript®, Encapsulated PostScript (EPS) e PRN em arquivos PDF compactos, confiáveis e mais seguros em uma rede. O serviço Distiller é frequentemente usado para converter grandes volumes de documentos impressos em documentos eletrônicos, como faturas e declarações. A conversão de documentos em PDF também permite que as empresas enviem aos seus clientes uma versão em papel e uma versão eletrônica de um documento.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Distiller, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Converter PostScript em documentos PDF {#converting-postscript-to-pdf-documents-inner}

Este tópico descreve como você pode usar a API de serviço do Distiller (Java e serviço da Web) para converter programaticamente arquivos PostScript (PS), Encapsulated PostScript (EPS) e PRN em documentos PDF.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Distiller, consulte [Referência de serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Para converter arquivos PostScript em documentos PDF, um dos itens a seguir precisa ser instalado no servidor que hospeda o AEM Forms: Pacote redistribuível Acrobat 9 ou Microsoft Visual C++ 2005.

### Resumo das etapas {#summary-of-steps}

Para converter qualquer um dos tipos suportados em um documento PDF, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente de serviço Distiller.
1. Recupere o arquivo para converter.
1. Chame a operação de criação de PDF.
1. Salve o documento PDF.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente de serviço Distiller**

Antes de executar programaticamente uma operação de serviço do Distiller, você deve criar um cliente de serviço do Distiller. Se estiver usando a API do Java, crie um objeto `DistillerServiceClient` . Se estiver usando a API do serviço da Web, crie um objeto `DistillerServiceService` .

**Recuperar o arquivo para converter**

Você deve recuperar o arquivo que deseja converter. Por exemplo, para converter um arquivo PS em um documento PDF, você deve recuperar o arquivo PS.

**Chamar a operação de criação de PDF**

Depois de criar o cliente de serviço, você pode invocar a operação de criação de PDF. Essa operação precisará de informações sobre o documento a ser convertido, incluindo o caminho para o documento de destino.

**Salvar o documento PDF**

Você pode salvar o documento PDF como um arquivo PDF.

**Consulte também:**

[Converter um arquivo PostScript em PDF usando a API Java](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Conversão de um arquivo PostScript para PDF usando a API de serviço da Web](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Saída](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Converter um arquivo PostScript em PDF usando a API Java {#convert-a-postscript-file-to-pdf-using-the-java-api}

Converta um arquivo PostScript em documento PDF usando a API do serviço de Distiller (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-destiller-client.jar, no caminho da classe do seu projeto Java.

1. Crie um cliente de serviço Distiller.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `DistillerServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Recupere o arquivo para converter.

   * Crie um objeto `java.io.FileInputStream` que represente o arquivo a ser convertido usando seu construtor e transmitindo um valor de string que especifique o local do arquivo.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Chame a operação de criação de PDF.

   Chame o método `DistillerServiceClient` do objeto `createPDF` e passe os seguintes valores:

   * O objeto `com.adobe.idp.Document` que representa o arquivo PS, EPS ou PRN a ser convertido
   * Um objeto `java.lang.String` que contém o nome do arquivo a ser convertido
   * Um objeto `java.lang.String` que contém o nome das configurações do Adobe PDF a serem usadas
   * Um objeto `java.lang.String` que contém o nome das configurações de segurança a serem usadas
   * Um objeto `com.adobe.idp.Document` opcional que contém configurações a serem aplicadas durante a geração do documento PDF
   * Um objeto `com.adobe.idp.Document` opcional que contém informações de metadados a serem aplicadas ao documento PDF

   O método `createPDF` retorna um objeto `CreatePDFResult` que contém o novo documento PDF e um arquivo de log que pode ser gerado. O arquivo de log normalmente contém mensagens de erro ou aviso geradas pela solicitação de conversão.

1. Salve o documento PDF.

   Para obter o documento PDF recém-criado, execute as seguintes ações:

   * Chame o método `CreatePDFResult` do objeto `getCreatedDocument`. Isso retorna um objeto `com.adobe.idp.Document`.
   * Chame o método `com.adobe.idp.Document` do objeto `copyToFile` para extrair o documento PDF.

   Da mesma forma, para obter o documento de log, execute as seguintes ações.

   * Chame o método `CreatePDFResult` do objeto `getLogDocument`. Isso retorna um objeto `com.adobe.idp.Document`.
   * Chame o método `com.adobe.idp.Document` do objeto `copyToFile` para extrair o documento de log.


**Consulte também:**

[Resumo das etapas](converting-postscript-pdf-documents.md#summary-of-steps)

[Início rápido (modo SOAP): Conversão de um arquivo PostScript em um documento PDF usando a API Java](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Conversão de um arquivo PostScript para PDF usando a API do serviço da Web {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Converta um arquivo PostScript em um documento PDF usando a API do serviço da Distiller (serviço da Web):

1. Inclua arquivos de projeto.

   Crie um projeto do Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição de WSDL: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente de serviço Distiller.

   * Crie um objeto `DistillerServiceClient` usando seu construtor padrão.
   * Crie um objeto `DistillerServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Passe um valor de string que especifica o WSDL para o serviço do AEM Forms (por exemplo, `http://localhost:8080/soap/services/DistillerService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado ao criar uma referência de serviço. No entanto, especifique `?blob=mtom` para usar MTOM.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `DistillerServiceClient.Endpoint.Binding`. Converta o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `System.ServiceModel.BasicHttpBinding` `MessageEncoding` do objeto para `WSMessageEncoding.Mtom`. Esse valor garante que o MTOM seja usado.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor correspondente da senha ao campo `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupere o arquivo para converter.

   * Crie um objeto `BLOB` usando seu construtor. Esse objeto `BLOB` é usado para armazenar o arquivo para conversão em um documento PDF.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e passando um valor de string que representa o local do arquivo e o modo para abrir o arquivo no.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `System.IO.FileStream` do objeto `Length`.
   * Preencha a matriz de bytes com dados de fluxo chamando o método `System.IO.FileStream` do objeto `Read` e passando a matriz de bytes, a posição inicial e o comprimento do fluxo a ser lido.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` ao conteúdo da matriz de bytes.

1. Chame a operação de criação de PDF.

   Chame o método `DistillerServiceService` do objeto `CreatePDF2` e passe os seguintes valores obrigatórios:

   * O objeto `BLOB` que representa o arquivo PS a ser convertido
   * Uma string que contém o nome do caminho do arquivo a ser convertido
   * Um objeto de string que contém as configurações do Adobe PDF a serem usadas (por exemplo, `Standard`)
   * Um objeto de string que contém as configurações de segurança a serem usadas (por exemplo, `No Securit`y)
   * Um objeto `BLOB` opcional que contém configurações a serem aplicadas durante a geração do documento PDF
   * Um objeto `BLOB` opcional que contém informações de metadados a serem aplicadas ao documento PDF
   * Um parâmetro de saída `BLOB` usado para armazenar o documento PDF
   * Um parâmetro de saída `BLOB` usado para armazenar o log

1. Salve o documento PDF.

   * Crie um objeto `System.IO.FileStream` chamando seu construtor. Passe um valor de string que representa o local do arquivo do documento PDF assinado e o modo no qual o arquivo deve ser aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `BLOB` retornado pelo método `CreatePDF2` (o parâmetro de saída). Preencha a matriz de bytes obtendo o valor do membro de dados `BLOB` do objeto `MTOM`.
   * Crie um objeto `System.IO.BinaryWriter` chamando seu construtor e passando o objeto `System.IO.FileStream`.
   * Grave o conteúdo da matriz de bytes em um arquivo PDF chamando o método `System.IO.BinaryWriter` do objeto `Write` e transmitindo a matriz de bytes.

**Consulte também:**

[Resumo das etapas](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
