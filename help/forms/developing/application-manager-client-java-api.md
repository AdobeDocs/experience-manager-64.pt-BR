---
title: Início rápido do JavaAPI do cliente do Application Manager (SOAP)
seo-title: Application Manager Client JavaAPI Quick Start(SOAP)
description: Use o Cliente do Application Manager para criar uma versão de aplicativo, exportar aplicativos, importar aplicativos, obter um aplicativo do AEM Forms, obter o status dos aplicativos, visualizar o AEM Forms e o arquivo de aplicativos posterior e excluir o arquivo de aplicativos do AEM Forms.
seo-description: Use the Application Manager Client to create an application version, export applications, import applications, get an AEM Forms application, get applications, get status of applications, preview AEM Forms and later application archive, and delete AEM Forms application archive.
uuid: 043f1c08-c7de-4e2d-88ca-b46428b1b551
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 2ec2a75e-4191-4660-a6f2-26cc667720b3
role: Developer
exl-id: 8369beeb-4628-40ea-9167-717f112768da
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---

# Início rápido do JavaAPI do cliente do Application Manager (SOAP) {#application-manager-client-javaapi-quick-start-soap}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O seguinte SOAP (Java API Quick Start) está disponível para o cliente do Application Manager.

[Início rápido (modo SOAP): Criando versão do aplicativo usando a API Java](#quick-start-soap-mode-creating-application-version-using-the-java-api)

[Início rápido (modo SOAP): Exportação de aplicativos usando a API Java](#quick-start-soap-mode-exporting-applications-using-the-java-api)

[Início rápido (modo SOAP): Importação de aplicativos usando a API Java](#quick-start-soap-mode-importing-applications-using-the-java-api)

[Início rápido (modo SOAP): Obter um aplicativo do AEM Forms usando a API do Java](application-manager-client-java-api.md#quick-start-soap-mode-getting-a-application-using-the-java-api)

[Início rápido (modo SOAP): Obter os aplicativos usando a API do Java](application-manager-client-java-api.md#quick-start-soap-mode-getting-the-applications-using-the-java-api)

[Início rápido (modo SOAP): Obter o status de aplicativos usando a API Java](application-manager-client-java-api.md#quick-start-soap-mode-getting-status-of-applications-using-java-api)

[Início rápido (modo SOAP):Visualização do AEM Forms e do arquivo de aplicativos posterior usando a API Java](application-manager-client-java-api.md#quick-start-soap-mode-previewing-the-livecycle-es2-and-later-application-archive-using-the-java-api)

[Início rápido (modo SOAP):Excluir o arquivo de aplicativos do AEM Forms usando a API Java](application-manager-client-java-api.md#quick-start-soap-mode-deleting-the-application-archive-using-the-java-api)

As operações do AEM Forms podem ser executadas usando a API altamente digitada do AEM Forms e o modo de conexão deve ser definido como SOAP.

>[!NOTE]
>
>O início rápido localizado em Programação com o AEM Forms é baseado no Forms Server que está sendo implantado no JBoss e no sistema operacional Windows. No entanto, se estiver usando outro sistema operacional, como o Unix, substitua caminhos específicos para janelas por caminhos suportados pelo sistema operacional aplicável. Da mesma forma, se estiver usando outro servidor de aplicativos J2EE, certifique-se de especificar propriedades de conexão válidas. Consulte [Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Início rápido (modo SOAP): Criando versão do aplicativo usando a API Java {#quick-start-soap-mode-creating-application-version-using-the-java-api}

O exemplo de código Java a seguir cria um aplicativo usando a API JAVA.

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. adobe-repository-client.jar 
 * 5. activation.jar (required for SOAP mode) 
 * 6. axis.jar (required for SOAP mode) 
 * 7. commons-codec-1.3.jar (required for SOAP mode) 
 * 8. commons-collections-3.1.jar  (required for SOAP mode) 
 * 9. commons-discovery.jar (required for SOAP mode) 
 * 10. commons-logging.jar (required for SOAP mode) 
 * 11. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 12. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 13. jaxrpc.jar (required for SOAP mode) 
 * 14. log4j.jar (required for SOAP mode) 
 * 15. mail.jar (required for SOAP mode) 
 * 16. saaj.jar (required for SOAP mode) 
 * 17. wsdl4j.jar (required for SOAP mode) 
 * 18. xalan.jar (required for SOAP mode) 
 * 19. xbean.jar (required for SOAP mode) 
 * 20. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.util.Properties; 
import java.util.Random; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.repository.bindings.ResourceRepositoryDelegate; 
import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
public class CreateApplicationVersion_SOAP { 
    private static String applicationFolder = "Applications"; 
    private static String defaultAppVersion = "1.0"; 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        // Create ResourceRepositoryDelegate object 
        ResourceRepositoryDelegate repositoryClient = new ResourceRepositoryClient( 
                myFactory); 
        final Random num = new Random(); 
        String appName = "App" + num.nextInt(); 
        String newAppName = null; 
        try { 
            // Create application with default application version 
            newAppName = appClient.createApplication(appName); 
            if (repositoryClient.resourceExists("/" + applicationFolder + "/" 
                    + appName.toString() + "/" + defaultAppVersion)) { 
                System.out.println("Application with name: " + appName + "/" 
                        + defaultAppVersion + " is created succesfully!"); 
            } 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        try { 
            // Create version of the new application 
            appName = appClient.createApplicationVersion(newAppName, 
                    defaultAppVersion, "2.0", "version increment"); 
            if (repositoryClient.resourceExists("/" + applicationFolder + "/" 
                    + appName.toString() + "/" + "2.0")) { 
                System.out.println("Application version 2.0 created : " 
                        + appName + "/" + "2.0"); 
            } 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP): Exportação de aplicativos usando a API Java {#quick-start-soap-mode-exporting-applications-using-the-java-api}

O exemplo de código Java a seguir exporta um aplicativo usando a API JAVA.

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.File; 
import java.io.FileInputStream; 
import java.util.ArrayList; 
import java.util.List; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class ExportLCA_SOAP { 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        Document doc = null; 
        try { 
            final FileInputStream fileApp = new FileInputStream( 
                    "C:\\ImportSampleApp2.lca"); 
            doc = new Document(fileApp); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        String resourceID = null; 
        try { 
            // Import the application into the LC server 
            resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID:" 
                    + resourceID + " is completed successfully!"); 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "ExportSampleApp2"; 
        try { 
            final List<String> eReqList = new ArrayList<String>(); 
            eReqList.add(resourceID); 
            // Export the application imported above 
            doc = appClient.export(eReqList, "lcaDescription"); 
            // Save into local LCA file 
            final String archiveName = "C:/" + sampleAppName + "-" + "1.0" 
                    + ".lca"; 
            final File fTemp = new File(archiveName); 
            doc.copyToFile(fTemp); 
            System.out.println("Export application completed with name: " 
                    + archiveName); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP): Importação de aplicativos usando a API Java {#quick-start-soap-mode-importing-applications-using-the-java-api}

O exemplo de código Java a seguir importa um aplicativo usando a API JAVA.

>[!NOTE]
>
>A API Java importApplication() substitui aplicativos existentes com o mesmo nome por aplicativos mais recentes. Para atualizar um aplicativo existente, use a API importApplication() no lugar de API updateApplication().

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.FileInputStream; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class ImportLCA_SOAP { 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM FOrms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        Document doc = null; 
        try { 
            final FileInputStream fileApp = new FileInputStream( 
                    "C:\\ImportSampleApp2.lca"); 
            doc = new Document(fileApp); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        try { 
            // Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID:" 
                    + resourceID + " is completed successfully!"); 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP): Obter um aplicativo usando a API do Java {#quick-start-soap-mode-getting-a-application-using-the-java-api}

O exemplo de código Java a seguir obtém um aplicativo usando a API Java.

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.applicationmanager.application.Application; 
import com.adobe.idp.applicationmanager.application.ApplicationId; 
import com.adobe.idp.applicationmanager.application.impl.ApplicationIdImpl; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplication_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
            //Deploy the application 
            boolean result = appClient.deployApplication(sampleAppName); 
            if (result) { 
                System.out.println("Imported application is deployed."); 
            } 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
         
        //Initialize the ApplicationId instance 
        ApplicationId appId = new ApplicationIdImpl(); 
        appId.setApplicationName(sampleAppName); 
 
        try { 
                //Get the application by application id 
                Application app = appClient.getApplication(appId); 
                System.out.println("Get application with name: " + app.getApplicationId().getApplicationName()); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP): Obter os aplicativos usando a API do Java {#quick-start-soap-mode-getting-the-applications-using-the-java-api}

O exemplo de código Java a seguir obtém os aplicativos usando a API Java.

***observação**: Obter a API do aplicativo AEM Forms, getApplications(), retorna somente os aplicativos implantados. *

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 

package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.List; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplications_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
         
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
 
        try { 
                //Get applications from LC server 
                List appList = appClient.getApplications(); 
                System.out.println("Get applications from LC Server: " + appList.size()); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP): Obter o status de aplicativos usando a API Java {#quick-start-soap-mode-getting-status-of-applications-using-java-api}

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.applicationmanager.application.ApplicationId; 
import com.adobe.idp.applicationmanager.application.ApplicationStatus; 
import com.adobe.idp.applicationmanager.application.impl.ApplicationIdImpl; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplicationStatus_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
            //Deploy the application 
            boolean result = appClient.deployApplication(sampleAppName); 
            if (result) { 
                System.out.println("Imported application is deployed."); 
            } 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
         
        //Initialize the ApplicationId instance 
        ApplicationId appId = new ApplicationIdImpl(); 
        appId.setApplicationName(sampleAppName); 
 
        try { 
                //Get the application by application id 
                ApplicationStatus status = appClient.getApplicationStatus(appId); 
                System.out.println("Get application status with code: " + status.getStatusCode()); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## Início rápido (modo SOAP):Visualização do LiveCycle ES2 e do arquivo de aplicativos posterior usando a API Java {#quick-start-soap-mode-previewing-the-livecycle-es2-and-later-application-archive-using-the-java-api}

O exemplo de código Java a seguir é para preve AEM Forms e arquivamento de aplicativos posterior usando a API do Java.

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.FileInputStream; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class PreviewLCA_SOAP { 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Preview the LCA 
            final Document newDoc = appClient.previewLCA(doc); 
                     
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
    } 
}
```

## Início rápido (modo SOAP):Excluir o arquivo de aplicativos usando a API Java {#quick-start-soap-mode-deleting-the-application-archive-using-the-java-api}

O exemplo de código Java a seguir é para excluir um arquivo de aplicativos.

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
 * 8. commons-discovery.jar (required for SOAP mode) 
 * 9. commons-logging.jar (required for SOAP mode) 
 * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 12. jaxrpc.jar (required for SOAP mode) 
 * 13. log4j.jar (required for SOAP mode) 
 * 14. mail.jar (required for SOAP mode) 
 * 15. saaj.jar (required for SOAP mode) 
 * 16. wsdl4j.jar (required for SOAP mode) 
 * 17. xalan.jar (required for SOAP mode) 
 * 18. xbean.jar (required for SOAP mode) 
 * 19. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class DeleteApplication_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
         
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
                //Delete the application imported above 
                appClient.deleteApplication(sampleAppName, "1.0"); 
                System.out.println("Delete application completed with name: " + sampleAppName); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```
