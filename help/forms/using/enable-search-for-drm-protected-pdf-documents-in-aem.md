---
title: Habilitar AEM pesquisar documentos de PDF protegido de segurança de documentos
seo-title: Enable AEM to search document security protected PDF documents
description: Saiba como habilitar a pesquisa de AEM nativa para executar a pesquisa de texto completo em documentos de PDF protegidos por DRM.
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: Document Security
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# Habilitar AEM pesquisar documentos de PDF protegido de segurança de documentos {#enable-aem-to-search-document-security-protected-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

AEM pesquisa é capaz de pesquisar e localizar AEM ativos e executar pesquisa de texto em vários formatos de documento comumente usados, como arquivos de texto simples, documentos do Microsoft Office e documentos do PDF. Também é possível estender a pesquisa nativa para realizar a pesquisa de texto completo em [Documentos do PDF protegidos com AEM segurança de documentos](/help/forms/using/admin-help/document-security.md). Para permitir que o AEM execute a pesquisa de texto completo em tais documentos, execute as seguintes etapas:

1. Estabelecer uma conexão segura
1. Indexar um documento PDF protegido por política de exemplo

## Pré-requisitos {#prerequisites}

* Se estiver usando o AEM Forms no OSGi:

   * Instalar [Pacote do Indexador de segurança de documentos do AEM Forms](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) no servidor do AEM Forms.
   * Certifique-se de que um AEM Forms no servidor JEE esteja ativo e em execução e que a segurança do documento esteja instalada no AEM Forms correspondente no servidor JEE. O Formulário AEM no servidor JEE é necessário para indexar o documento protegido.

* Se você estiver usando somente o AEM Forms no servidor JEE, o pacote de indexador já estará instalado.
* Certifique-se de que todos os pacotes estejam funcionando. Se todos os pacotes não estiverem ativos, espere até que todos os pacotes estejam ativos e em execução.

   * Para o AEM Forms no OSGi, os pacotes são listados em `https://[server]:[port]/system/console/bundles`.
   * Para o AEM Forms no JEE, os pacotes são listados em `https://[server]:[port]/[context-path]/system/console/bundles`. Por exemplo, `http://localhost:8080/lc/system/console/bundles`.

* Adicione o *sun.util.calendar* para a lista de permissões. Para adicionar o pacote à  lista de permissões, execute as seguintes etapas:

   1. Abra AEM Console da Web. O URL é `https://[server]:[port]/system/console/configMgr`.
   1. Localizar e abrir **Configuração do firewall de desserialização**.
   1. Adicione o pacote sun.util.calendar ao campo Classes da lista de permissões ou prefixos de pacotes e clique em **Salvar**.

## Estabelecer uma conexão segura entre as pilhas AEM Forms JEE e OSGi {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Você pode usar um dos seguintes métodos para estabelecer a conexão segura:

* Configurar o pacote SDK do cliente do Adobe LiveCycle com o AEM Forms em credenciais de administrador do JEE
* Configurar o pacote SDK do cliente do Adobe LiveCycle usando autenticação mútua

### Configurar o pacote SDK do cliente do Adobe LiveCycle com o AEM Forms em credenciais de administrador do JEE {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Abra AEM Console da Web. O URL é `https://[server]:[port]/system/console/configMgr`.
1. Localize e abra o **Pacote de SDK do cliente do Adobe LiveCycle**. Especifique o valor para os seguintes campos:

   * **URL do servidor:** Especifique o URL HTTPS do AEM Forms no servidor JEE. Para ativar a comunicação via https, reinicie o servidor com o -Djavax.net.ssl.trustStore=&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parâmetro.
   * **Nome do serviço**: Adicione o RightsManagementService à lista de serviços especificados.
   * **Nome de usuário:** Especifique o nome de usuário da AEM Forms na conta JEE a ser usada para iniciar chamadas AEM servidor. A conta especificada deve ter permissões para iniciar serviços de documento no AEM Forms no servidor JEE.
   * **Senha**: Especifique a senha da AEM Forms na conta JEE mencionada no campo Nome de usuário.

   Clique em **Salvar**. AEM é ativado para pesquisar documentos PDF protegidos pela segurança do documento.

### Configurar o pacote SDK do cliente do Adobe LiveCycle usando autenticação mútua {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Ative a autenticação mútua para AEM Forms no JEE. Para obter informações detalhadas, consulte [Autenticação CAC e Mútua](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Abra AEM Console da Web. O URL é `https://[server]:[port]/system/console/configMgr`.
1. Localize e abra o **Adobe LiveCycle Client SDK** Pacote. Especifique o valor das seguintes propriedades:

   * **URL do servidor**: Especifique o URL HTTPS do AEM Forms no servidor JEE. Para habilitar a comunicação por https, reinicie o servidor AEM com o -Djavax.net.ssl.trustStore=&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parâmetro.
   * **Habilitar SSL de 2 vias**: Habilite a opção Habilitar SSL de 2 vias.
   * **URL do arquivo KeyStore**: Especifique o URL do arquivo de repositório de chaves.
   * **URL de arquivo de confiança do TrustStore**: Especifique o URL do arquivo truststore.
   * **Senha do KeyStore**: Especifique a senha do arquivo de repositório de chaves.
   * **TrustStorePassword**: Especifique a senha para o arquivo truststore.
   * **Nome do serviço**: Adicione o RightsManagementService à lista de serviços especificados.

   Clique em **Salvar**. AEM está ativado para procurar documentos de PDF protegido de segurança de documentos

## Indexar um documento PDF protegido por política de exemplo {#index-a-sample-policy-protected-pdf-document}

1. Faça logon no AEM Assets como administrador.
1. Crie uma pasta no AEM Digital Asset Manager e faça upload dos documentos do PDF protegidos por política para a pasta recém-criada.

   Agora, você pode pesquisar os documentos protegidos por política usando AEM pesquisa.
