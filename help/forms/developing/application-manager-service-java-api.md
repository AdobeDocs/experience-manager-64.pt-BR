---
title: Início rápido de JavaAPI do serviço do Application Manager (SOAP)
seo-title: Application Manager Service JavaAPI Quick Start(SOAP)
description: Use o serviço Application Manager para implantar e remover aplicativos usando o Início rápido da API Java.
seo-description: Use the Application Manager service to deploy and remove applications using the Java API Quick Start.
uuid: 01a9bce3-868b-495b-bdee-bc60f029129e
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 12da2a9b-4009-496e-953f-c2ae0352f59f
role: Developer
exl-id: 1d93a7c2-631a-4cf7-938f-0133536c7e09
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%

---

# Início rápido de JavaAPI (SOAP) do Serviço do Application Manager {#application-manager-service-javaapi-quick-start-soap}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Java API Quick Start (SOAP) está disponível para o serviço do Application Manager.

[Início rápido: Implantação de aplicativos usando a API do Java (SOAP)](application-manager-service-java-api.md#quick-start-soap-mode-deploying-applications-using-the-java-api)

[Início rápido: Remoção de um aplicativo usando a API Java (SOAP)](application-manager-service-java-api.md#quick-start-soap-mode-removing-an-application-using-the-java-api)

>[!NOTE]
>
>As APIs do gerenciador de aplicativos são compatíveis apenas com arquivos AEM Forms LCA. Ele não oferece suporte a arquivos LCA do LiveCycle ES2 e ES4.

As operações do AEM Forms podem ser executadas usando a API altamente digitada do AEM Forms e o modo de conexão deve ser definido como SOAP.

>[!NOTE]
>
>O Início rápido da API Java (SOAP), localizado em Programação com formulários de AEM, é baseado na Forms se você estiver usando outro sistema operacional, como o Unix, substitua caminhos específicos do Windows por caminhos compatíveis com o sistema operacional aplicável. Da mesma forma, se estiver usando outro servidor de aplicativos J2EE, certifique-se de especificar propriedades de conexão válidas. Consulte [Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Início rápido (modo SOAP): Implantação de aplicativos usando a API do Java {#quick-start-soap-mode-deploying-applications-using-the-java-api}

O seguinte exemplo de código Java importa um aplicativo com base em um arquivo LCA existente chamado *EncryptDocument.lca*.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 19. adobe-workflow-client-sdk.jar 
     * 20. adobe-applicationmanager-client-sdk.jar 
      
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.io.FileInputStream; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.applicationmanager.application.ApplicationStatus; 
 import com.adobe.idp.applicationmanager.client.ApplicationManager; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class DeployApplication { 
  
     public static void main(String[] args) { 
      
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Get the AEM Forms application to deploy  
             FileInputStream fileApp = new FileInputStream("C:\\Adobe\EncryptDocument.lca"); 
             Document lcApp = new Document(fileApp); 
                                  
             //Create an ApplicationManager object 
             ApplicationManager appManager = new ApplicationManager(myFactory);  
              
             //Import the application into the production server 
             ApplicationStatus appStatus = appManager.importApplicationArchive(lcApp); 
             int status = appStatus.getStatusCode(); 
              
             //Determine if the application was successfully deployed 
             if (status==1) 
                     System.out.println("The application was successfully deployed"); 
             else 
                     System.out.println("The application was not successfully deployed. The status is "+status); 
         } 
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Início rápido (modo SOAP): Remoção de um aplicativo usando a API Java {#quick-start-soap-mode-removing-an-application-using-the-java-api}

O seguinte exemplo de código Java remove um aplicativo chamado *EncryptDocument*.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 19. adobe-workflow-client-sdk.jar 
     * 20. adobe-applicationmanager-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
  
 import java.util.*; 
  
 import com.adobe.idp.applicationmanager.application.Application; 
 import com.adobe.idp.applicationmanager.application.ApplicationId; 
  
 import com.adobe.idp.applicationmanager.client.ApplicationManager; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RemoveApplication { 
  
     public static void main(String[] args) { 
          
          
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a ComponentRegistryClient object 
             ApplicationManager appManager = new ApplicationManager(myFactory);  
                                  
             //Get all the deployed applications 
             List allApps = appManager.getApplications(); 
                      
             //Iterate through the applications 
             Iterator iter= allApps.iterator(); 
             while (iter.hasNext()) { 
                          
              //Cast each element to an Application object 
              Application myApplication  = (Application)iter.next();     
              ApplicationId appID = myApplication.getApplicationId(); 
              String appName = appID.getApplicationName(); 
                           
              System.out.println("The name of the AEM Forms application is "+ appID.getApplicationName());  
              //Determine the name of the application 
              if (appName.compareTo("EncryptDocument")==0) 
              { 
                  //Remove the application 
                 appManager.removeApplication(appID); 
                 System.out.println("The  "+ appID.getApplicationName() +" application was removed."); 
              } 
         } 
         } 
         catch(Exception e) 
             { 
             e.printStackTrace(); 
             } 
     } 
 } 
 
```
