---
title: Montando Documentos Usando a Numeração de Bates
seo-title: Montando Documentos Usando a Numeração de Bates
description: 'Use a numeração de Bates para montar documentos PDF usando a API do Java e do serviço da Web. '
seo-description: 'Use a numeração de Bates para montar documentos PDF usando a API do Java e do serviço da Web. '
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1928'
ht-degree: 0%

---


# Montando Documentos Usando Numeração de Bates {#assembling-documents-using-bates-numbering}

Você pode montar documentos PDF que contêm identificadores de página exclusivos usando a numeração de Bates. *A* numeração de Bates é um método de aplicação de identificadores exclusivos a um lote de documentos relacionados. Cada página no documento (ou conjunto de documentos) recebe um número de Bates que identifica exclusivamente a página. Por exemplo, documentos de fabricação que contêm informações de lista de materiais e que estão associados à produção de uma montagem podem conter um identificador. Um número de Bates contém um valor numérico incrementado sequencialmente e um prefixo e sufixo opcionais. O prefixo + sufixo numérico + é conhecido como um *padrão de barras*.

A ilustração a seguir mostra um documento PDF que contém um identificador exclusivo localizado no cabeçalho do documento.

![au_au_batesnumber](assets/au_au_batesnumber.png)

Para a finalidade desta discussão, o identificador de página exclusivo é colocado no cabeçalho de um documento. Suponha que o seguinte documento DDX seja usado.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/"> 
        <PDF result="out.pdf"> 
        <Header> 
         <Center> 
             <StyledText> 
                 <p font-size="20pt"><BatesNumber/></p> 
             </StyledText> 
         </Center> 
     </Header> 
           <PDF source="map.pdf" /> 
          <PDF source="directions.pdf" /> 
          </PDF> 
 </DDX>
```

Este documento DDX mescla dois documentos PDF chamados *map.pdf* e* direcçõespdf* em um único documento PDF. O documento PDF resultante contém um cabeçalho que consiste em um identificador de página exclusivo. Por exemplo, o documento na ilustração acima mostra 000016.

>[!NOTE]
>
>Antes de ler esta seção, é recomendável que você esteja familiarizado com a montagem de documentos PDF usando o serviço Assembler. Esta seção não discute os conceitos, como criar um objeto de coleção que contenha documentos de entrada ou extrair os resultados do objeto de coleção retornado. (Consulte [Montagem programática de documentos PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Para obter mais informações sobre o serviço Assembler, consulte [Referência de Serviços para AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Para obter mais informações sobre um documento DDX, consulte [Assembler Service e DDX Reference](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Resumo das etapas {#summary-of-steps}

Para montar um documento PDF que contém um identificador de página exclusivo (numeração de Bates), execute as seguintes tarefas:

1. Inclua arquivos de projeto.
1. Crie um cliente Assembler do PDF.
1. Faça referência a um documento DDX existente.
1. Faça referência a documentos PDF de entrada.
1. Defina o valor do número Bates inicial.
1. Monte os documentos PDF de entrada.
1. Extraia os resultados.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

Os seguintes arquivos JAR devem ser adicionados ao caminho de classe do seu projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (necessário se o AEM Forms estiver implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

Se o AEM Forms for implantado em um servidor de aplicativos J2EE compatível diferente do JBoss, você deverá substituir os arquivos adobe-utilities.jar e jbossall-client.jar por arquivos JAR específicos do servidor de aplicativos J2EE no qual o AEM Forms é implantado. Para obter informações sobre a localização de todos os arquivos AEM Forms JAR, consulte [Incluindo arquivos da biblioteca AEM Forms Java](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um cliente do Assembler do PDF**

Antes de poder executar programaticamente uma operação Assembler, é necessário criar um cliente de serviço Assembler.

**Referência a um documento DDX existente**

Um documento DDX deve ser referenciado para montar um documento PDF. Por exemplo, considere o documento DDX que foi introduzido nesta seção. Para montar um documento PDF que contém identificadores de página exclusivos, o documento DDX deve conter o elemento `BatesNumber` .

**Referência a documentos PDF de entrada**

Os documentos PDF de entrada devem ser referenciados para montar um documento PDF. Por exemplo, os documentos map.pdf e Direction.pdf devem ser referenciados para reunir esses documentos PDF em um único documento PDF.

**Definir o valor do número Bates inicial**

Você pode definir o valor do número de Bates inicial para atender às suas necessidades comerciais. Por exemplo, suponha que seja um requisito definir o valor inicial como 000100. Se você não definir o valor inicial, o valor da primeira página será 000000.

**Montar os documentos PDF de entrada**

Depois de criar o cliente do serviço Assembler, faça referência ao documento DDX que contém `BatesNumber` informações do elemento, faça referência a um documento PDF de entrada e defina opções de tempo de execução, você pode chamar a operação `invokeDDX` que resulta na montagem pelo serviço Assembler de um documento PDF que contém identificadores de página exclusivos.

**Extraia os resultados**

O serviço Assembler retorna um objeto de coleção que contém os resultados da tarefa. Você pode extrair o documento PDF resultante e quaisquer exceções lançadas. Nessa situação, um documento PDF criptografado está localizado dentro do objeto de coleção.

>[!NOTE]
>
>Um objeto de coleção é retornado se você chamar a operação `invokeDDX`. Essa operação é usada ao passar dois ou mais documentos PDF de entrada para o serviço Assembler. No entanto, se você passar apenas um documento PDF de entrada para o serviço Assembler, deverá chamar a operação `invokeOneDocument`. Para obter informações sobre como usar essa operação, consulte [Assembling Encrypted PDF Documents](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Consulte também:**

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Montagem programática de documentos PDF](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Monte documentos com a numeração de Bates usando a API Java {#assemble-documents-with-bates-numbering-using-the-java-api}

Monte um documento PDF que usa identificadores de página exclusivos (numeração de Bates) usando a API do serviço Assembler (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-assembler-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente Assembler do PDF.

   * Crie um objeto `ServiceClientFactory` que contenha propriedades de conexão.
   * Crie um objeto `AssemblerServiceClient` usando seu construtor e transmitindo o objeto `ServiceClientFactory`.

1. Faça referência a um documento DDX existente.

   * Crie um objeto `java.io.FileInputStream` que represente o documento DDX usando seu construtor e transmitindo um valor de string que especifique o local do arquivo DX.
   * Crie um objeto `com.adobe.idp.Document` usando seu construtor e transmitindo o objeto `java.io.FileInputStream`.

1. Faça referência a documentos PDF de entrada.

   * Crie um objeto `java.util.Map` usado para armazenar documentos PDF de entrada usando um construtor `HashMap`.
   * Para cada documento PDF de entrada, crie um objeto `java.io.FileInputStream` usando seu construtor e transmitindo o local do documento PDF de entrada. Nessa situação, passe o local de um documento PDF não seguro.
   * Para cada documento PDF de entrada, crie um objeto `com.adobe.idp.Document` e passe o objeto `java.io.FileInputStream` que contém o documento PDF.
   * Adicione uma entrada ao objeto `java.util.Map` chamando seu método `put` e passando os seguintes argumentos:

      * Um valor de string que representa o nome da chave. Esse valor deve corresponder ao valor do elemento de origem do PDF especificado no documento DX. Por exemplo, o nome do arquivo de origem PDF especificado no documento DDX que é introduzido nesta seção é Loan.pdf.
      * Um objeto `com.adobe.idp.Document` que contém o documento PDF inseguro.

1. Defina o valor do número Bates inicial.

   * Crie um objeto `AssemblerOptionSpec` que armazene opções de tempo de execução usando seu construtor .
   * Defina o número Bates inicial chamando o `AssemblerOptionSpec` do objeto `setFirstBatesNumber` e passando um valor numérico que especifica o valor inicial.

1. Monte os documentos PDF de entrada.

   Chame o método `AssemblerServiceClient` do objeto `invokeDDX` e passe os seguintes valores obrigatórios:

   * Um objeto `com.adobe.idp.Document` que representa o documento DDX.
   * Um objeto `java.util.Map` que contém o arquivo PDF inseguro de entrada.
   * Um objeto `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` que especifica as opções de tempo de execução, incluindo a fonte padrão e o nível de log do trabalho.

   O método `invokeDDX` retorna um objeto `com.adobe.livecycle.assembler.client.AssemblerResult` que contém um documento PDF criptografado por senha.

1. Extraia os resultados.

   Para obter o documento PDF recém-criado, execute as seguintes ações:

   * Chame o método `AssemblerResult` do objeto `getDocuments`. Esta ação retorna um objeto `java.util.Map`.
   * Itere pelo objeto `java.util.Map` até encontrar o objeto `com.adobe.idp.Document`.
   * Chame o método `com.adobe.idp.Document` do objeto `copyToFile` para extrair o documento PDF.

**Consulte também:**

[Início rápido (modo SOAP): Montagem de um documento PDF com numeração de barras usando a API Java](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Monte documentos com a numeração de Bates usando a API do serviço da Web {#assemble-documents-with-bates-numbering-using-the-web-service-api}

Monte um documento PDF que usa identificadores de página exclusivos (numeração de Bates) usando a API do Serviço de Assembler (serviço da Web):

1. Inclua arquivos de projeto.

   Crie um projeto do Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição de WSDL: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente Assembler do PDF.

   * Crie um objeto `AssemblerServiceClient` usando seu construtor padrão.
   * Crie um objeto `AssemblerServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Passe um valor de string que especifica o WSDL para o serviço do AEM Forms (por exemplo, `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). Você não precisa usar o atributo `lc_version`. Esse atributo é usado ao criar uma referência de serviço.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `AssemblerServiceClient.Endpoint.Binding`. Converta o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `System.ServiceModel.BasicHttpBinding` `MessageEncoding` do objeto para `WSMessageEncoding.Mtom`. Esse valor garante que o MTOM seja usado.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor correspondente da senha ao campo `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Faça referência a um documento DDX existente.

   * Crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento DDX.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor e passando um valor de string que representa o local do arquivo do documento DX e o modo para abrir o arquivo.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `System.IO.FileStream` do objeto `Length`.
   * Preencha a matriz de bytes com dados de fluxo chamando o método `System.IO.FileStream` do objeto `Read`. Passe a matriz de bytes, a posição inicial e o comprimento do fluxo para ler.
   * Preencha o objeto `BLOB` atribuindo seu campo `MTOM` ao conteúdo da matriz de bytes.

1. Faça referência a documentos PDF de entrada.

   * Para cada documento PDF de entrada, crie um objeto `BLOB` usando seu construtor. O objeto `BLOB` é usado para armazenar o documento PDF de entrada.
   * Crie um objeto `System.IO.FileStream` chamando seu construtor. Passe um valor de string que representa o local do arquivo do documento PDF de entrada e o modo no qual o arquivo deve ser aberto.
   * Crie uma matriz de bytes que armazene o conteúdo do objeto `System.IO.FileStream`. Você pode determinar o tamanho da matriz de bytes obtendo a propriedade `System.IO.FileStream` do objeto `Length`.
   * Preencha a matriz de bytes com dados de fluxo chamando o método `System.IO.FileStream` do objeto `Read`. Passe a matriz de bytes, a posição inicial e o comprimento do fluxo para ler.
   * Preencha o objeto `BLOB` atribuindo sua propriedade `MTOM` ao conteúdo da matriz de bytes.
   * Crie um objeto `MyMapOf_xsd_string_To_xsd_anyType`. Esse objeto de coleção é usado para armazenar os documentos PDF de entrada.
   * Para cada documento PDF de entrada, crie um objeto `MyMapOf_xsd_string_To_xsd_anyType_Item`. Por exemplo, se dois documentos PDF de entrada forem usados, crie dois objetos `MyMapOf_xsd_string_To_xsd_anyType_Item` .
   * Atribua um valor de string que represente o nome da chave ao campo `MyMapOf_xsd_string_To_xsd_anyType_Item` `key` do objeto. Esse valor deve corresponder ao valor do elemento de origem do PDF especificado no documento DX. (Execute essa tarefa para cada documento PDF de entrada.)
   * Atribua o objeto `BLOB` que armazena o documento PDF ao campo `MyMapOf_xsd_string_To_xsd_anyType_Item` `value` do objeto. (Execute essa tarefa para cada documento PDF de entrada.)
   * Adicione o objeto `MyMapOf_xsd_string_To_xsd_anyType_Item` ao objeto `MyMapOf_xsd_string_To_xsd_anyType`. Chame o método `MyMapOf_xsd_string_To_xsd_anyType` do objeto `Add` e passe o objeto `MyMapOf_xsd_string_To_xsd_anyType`. (Execute essa tarefa para cada documento PDF de entrada.)

1. Defina o valor do número Bates inicial.

   * Crie um objeto `AssemblerOptionSpec` que armazene opções de tempo de execução usando seu construtor .
   * Defina o número Bates inicial atribuindo um valor numérico ao membro de dados `firstBatesNumber` que pertence ao objeto `AssemblerOptionSpec`.

1. Monte os documentos PDF de entrada.

   Chame o método `AssemblerServiceClient` do objeto `invoke` e passe os seguintes valores:

   * Um objeto `BLOB` que representa o documento DDX.
   * O objeto `MyMapOf_xsd_string_To_xsd_anyType` que contém os documentos PDF de entrada. Suas chaves devem corresponder aos nomes dos arquivos de origem do PDF e seus valores devem ser os objetos `BLOB` que correspondem a esses arquivos.
   * Um objeto `AssemblerOptionSpec` que especifica as opções de tempo de execução.

   O método `invoke` retorna um objeto `AssemblerResult` que contém os resultados da tarefa e quaisquer exceções que ocorreram.

1. Extraia os resultados.

   Para obter o documento PDF recém-criado, execute as seguintes ações:

   * Acesse o campo `AssemblerResult` do objeto `documents`, que é um objeto `Map` que contém os documentos PDF de resultado.
   * Itere pelo objeto `Map` até encontrar a chave que corresponde ao nome do documento resultante. Em seguida, converta esse membro da matriz `value` em um `BLOB`.
   * Extraia os dados binários que representam o documento PDF acessando a propriedade `BLOB` do objeto `MTOM`. Isso retorna uma matriz de bytes que podem ser gravados em um arquivo PDF.

**Consulte também:**

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
