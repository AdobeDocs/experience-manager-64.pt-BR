---
title: Início rápido (SOAP) do Java do serviço Forms com código de barras
seo-title: Barcoded Forms Service Java APIQuick Start(SOAP)
description: Use o serviço Forms com código de barras para decodificar dados de formulário com código de barras usando o Início rápido da API Java.
seo-description: Use the Barcoded Forms service to decode barcoded form data using the Java API Quick Start.
uuid: a6739695-ee0b-4480-8cef-0f91a72deaad
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 245b9cc4-5837-4a22-b5f4-a1d4c5d66918
role: Developer
exl-id: fbeefa4e-966d-43b5-ae59-9548fe520cc2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---

# Início rápido da API Java do serviço de Forms com código de barras (SOAP) {#barcoded-forms-service-java-apiquick-start-soap}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Java API Quick Start (SOAP) está disponível para o serviço Forms com códigos de barras:

[Início rápido (modo SOAP): Decodificação de dados de formulário com código de barras usando a API Java](barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

As operações do AEM Forms podem ser executadas usando a API altamente digitada do AEM Forms e o modo de conexão deve ser definido como SOAP.

>[!NOTE]
>
>Os Inícios rápidos localizados em Programação com o AEM Forms são baseados no Forms Server que está sendo implantado no JBoss Application Server e no sistema operacional Microsoft Windows. No entanto, se estiver usando outro sistema operacional, como UNIX, substitua caminhos específicos do Windows por caminhos compatíveis com o sistema operacional aplicável. Da mesma forma, se estiver usando outro servidor de aplicativos J2EE, certifique-se de especificar propriedades de conexão válidas. Consulte [Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Início rápido (modo SOAP): Decodificação de dados de formulário com código de barras usando a API Java {#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api}

O código Java a seguir decodifica dados de formulário localizados em um formulário PDF salvo como Loan.pdf. Os dados decodificados são salvos como um arquivo XML chamado extratedData.xml. Este exemplo de código converte um `org.w3c.dom.Document` em um `com.adobe.idp.Document` objeto. (Consulte [Decodificação de dados de formulário com código de barras](/help/forms/developing/barcoded-forms.md#decoding-barcoded-form-data).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-barcodedforms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.*; 
 import java.util.Iterator; 
 import java.util.List; 
 import java.util.Properties; 
 import javax.xml.transform.*; 
 import javax.xml.transform.dom.DOMSource; 
 import javax.xml.transform.stream.StreamResult; 
 import com.adobe.livecycle.barcodedforms.CharSet; 
 import com.adobe.livecycle.barcodedforms.Delimiter ; 
 import com.adobe.livecycle.barcodedforms.XMLFormat ;  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.barcodedforms.client.*; 
  
 public class DecodeFormDataSOAP { 
  
     public static void main(String[] args) { 
          
     try 
         { 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
         BarcodedFormsServiceClient barClient = new BarcodedFormsServiceClient(myFactory); 
                          
         //Specify a PDF document to convert to a XDP file 
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanBarForms.pdf");     
         Document inDoc = new Document (fileInputStream); 
          
         java.lang.Boolean myFalse = new java.lang.Boolean(false); 
         java.lang.Boolean myTrue = new java.lang.Boolean(true); 
          
         //Decode barcoded form data 
         org.w3c.dom.Document decodeXML = barClient.decode( 
             inDoc, 
             myTrue, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             CharSet.UTF_8); 
                                                  
         //Convert the decoded data to XDP data 
         List extractedData = barClient.extractToXML( 
             decodeXML,  
             Delimiter.Carriage_Return, 
             Delimiter.Tab, 
             XMLFormat.XDP); 
                  
         //Create an Iterator object and iterate through  
         //the List object 
         Iterator iter = extractedData.iterator();  
         int i = 0 ;  
              
         while (iter.hasNext()) {  
              
             //Get the org.w3c.dom.Document object in each element 
             org.w3c.dom.Document myDom = (org.w3c.dom.Document)iter.next();  
                  
             //Convert the org.w3c.dom.Document object to a  
             //com.adobe.idp.Document object 
             com.adobe.idp.Document myDocument = convertDOM(decodeXML); 
              
             //Save the XML data to extractedData.xml 
             File myFile = new File("C:\\Adobe\extractedData"+i+".xml"); 
              
             myDocument.copyToFile(myFile); 
             i++;  
             }     
         } 
     catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
  
  
     //This user-defined method converts an org.w3c.dom.Document to a  
     //com.adobe.idp.Document object 
     public static com.adobe.idp.Document convertDOM(org.w3c.dom.Document doc) 
         { 
              
             byte[] mybytes = null ; 
         com.adobe.idp.Document myDocument = null;  
         try 
             { 
  
             //Create a Java Transformer object 
          TransformerFactory transFact = TransformerFactory.newInstance(); 
          Transformer transForm = transFact.newTransformer(); 
      
          //Create a Java ByteArrayOutputStream object 
          ByteArrayOutputStream myOutStream = new ByteArrayOutputStream(); 
  
         //Create a Java Source object 
          Source myInput = new DOMSource(doc); 
  
         //Create a Java Result object 
          Result myOutput = new StreamResult(myOutStream); 
      
         //Populate the Java ByteArrayOutputStream object 
          transForm.transform(myInput,myOutput); 
  
         //Get the size of the ByteArrayOutputStream buffer 
          int myByteSize = myOutStream.size(); 
  
         //Allocate myByteSize to the byte array 
         mybytes = new byte[myByteSize]; 
  
         //Copy the content to the byte array 
         mybytes = myOutStream.toByteArray();  
         com.adobe.idp.Document myDoc = new com.adobe.idp.Document(mybytes); 
      
          myDocument = myDoc ;  
          } 
              
         catch(Exception ee) 
         { 
             ee.printStackTrace(); 
         } 
              
     return myDocument;     
       } 
 }
```

>[!NOTE]
>
>Ao usar a `org.w3c.dom.Document` e um `com.adobe.idp.Document` na mesma lógica de aplicativo, é uma boa prática qualificar totalmente ambos os objetos.
