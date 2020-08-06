---
title: Permitir que AEM pesquise documentos PDF protegidos pela segurança do documento
seo-title: Permitir que AEM pesquise documentos PDF protegidos pela segurança do documento
description: 'Saiba como habilitar a pesquisa nativa AEM para realizar a pesquisa de texto completo em documentos PDF protegidos por DRM.  '
seo-description: 'Saiba como habilitar a pesquisa nativa AEM para realizar a pesquisa de texto completo em documentos PDF protegidos por DRM.  '
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 1%

---


# Permitir que AEM pesquise documentos PDF protegidos pela segurança do documento {#enable-aem-to-search-document-security-protected-pdf-documents}

AEM pesquisa é capaz de pesquisar e localizar ativos AEM e executar pesquisa de texto em vários formatos de documento comumente usados, como arquivos de texto simples, documentos do Microsoft Office e documentos PDF. Você também pode estender a pesquisa nativa para realizar a pesquisa em texto completo em Documentos [PDF protegidos com AEM segurança](/help/forms/using/admin-help/document-security.md)do Documento. Para permitir que o AEM execute a pesquisa de texto completo nesses documentos, execute as seguintes etapas:

1. Estabeleça uma conexão segura
1. Indexar um exemplo de documento PDF protegido por política

## Pré-requisitos {#prerequisites}

* Se você estiver usando o AEM Forms no OSGi:

   * Instale o pacote [Indexador de segurança do](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) AEM Forms Documento no servidor AEM Forms.
   * Verifique se um servidor AEM Forms em JEE está ativo e em execução e se a segurança do documento está instalada no AEM Forms correspondente no servidor JEE. O formulário AEM no servidor JEE é necessário para indexar o documento protegido.

* Se você estiver usando somente o AEM Forms no servidor JEE, o pacote indexador já estará instalado.
* Verifique se todos os pacotes estão ativos e em execução. Se todos os pacotes não estiverem ativos, aguarde até que todos os pacotes estejam ativos e em execução.

   * Para AEM Forms no OSGi, os pacotes estão listados em `https://[server]:[port]/system/console/bundles`.
   * Para AEM Forms em JEE, os pacotes estão listados em `https://[server]:[port]/[context-path]/system/console/bundles`. Por exemplo `http://localhost:8080/lc/system/console/bundles`.

* Adicione o pacote *sun.util.calendário* à lista de permissões. Para adicionar o pacote à lista de permissões, execute as seguintes etapas:

   1. Abra AEM Web Console. O URL é `https://[server]:[port]/system/console/configMgr`.
   1. Localize e abra a Configuração **do Firewall de** Deserialização.
   1. Adicione o pacote sun.util.calendário ao campo Classes da lista de permissões ou prefixos do pacote e clique em **Salvar**.

## Estabeleça uma conexão segura entre as pilhas AEM Forms JEE e OSGi {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Você pode usar um dos seguintes métodos para estabelecer a conexão segura:

* Configurar o pacote SDK do cliente do LiveCycle Adobe com o AEM Forms em credenciais de administrador do JEE
* Configurar o pacote SDK do cliente do LiveCycle Adobe usando autenticação mútua

### Configurar o pacote SDK do cliente do LiveCycle Adobe com o AEM Forms em credenciais de administrador do JEE {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Abra AEM Web Console. O URL é `https://[server]:[port]/system/console/configMgr`.
1. Localize e abra o pacote SDK do cliente do **Adobe LiveCycle**. Especifique o valor para os seguintes campos:

   * **URL do servidor:** Especifique o URL HTTPS do AEM Forms no servidor JEE. Para ativar a comunicação por https, reinicie o servidor com o parâmetro -Djavax.net.ssl.trustStore=&lt;caminho do AEM Forms no arquivo de armazenamento de chaves JEE>.
   * **Nome** do serviço: Adicione o Rights ManagementService à lista de serviços especificados.
   * **Nome de usuário:** Especifique o nome de usuário da conta AEM Forms em JEE a ser usado para iniciar chamadas do servidor AEM. A conta especificada deve ter permissões para os serviços de documento de start no AEM Forms no servidor JEE.
   * **Senha**: Especifique a senha da conta AEM Forms em JEE mencionada no campo Nome de usuário.

   Clique em **Salvar**. AEM está habilitado para pesquisar documentos PDF protegidos pela segurança do documento.

### Configurar o pacote SDK do cliente do LiveCycle Adobe usando autenticação mútua {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Ative a autenticação mútua para AEM Forms no JEE. Para obter informações detalhadas, consulte [CAC e autenticação](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html)mútua.
1. Abra AEM Web Console. O URL é `https://[server]:[port]/system/console/configMgr`.
1. Localize e abra o pacote SDK **do cliente do** Adobe LiveCycle. Especifique o valor para as seguintes propriedades:

   * **URL** do servidor: Especifique o URL HTTPS do AEM Forms no servidor JEE. Para ativar a comunicação por https, reinicie o servidor AEM com o parâmetro -Djavax.net.ssl.trustStore=&lt;caminho do AEM Forms no arquivo de armazenamento de chaves JEE>.
   * **Habilitar SSL** de 2 vias: Ative a opção Ativar SSL de 2 vias.
   * **URL** do arquivo KeyStore: Especifique o URL do arquivo de armazenamento de chaves.
   * **URL** do arquivo TrustStore: Especifique o URL do arquivo Truststore.
   * **Senha** do KeyStore: Especifique a senha para o arquivo de armazenamento de chaves.
   * **TrustStorePassword**: Especifique a senha para o arquivo Truststore.
   * **Nome** do serviço: Adicione o Rights ManagementService à lista de serviços especificados.

   Clique em **Salvar**. AEM está habilitado para pesquisar documentos PDF protegidos pela segurança do documento

## Indexar um exemplo de documento PDF protegido por política {#index-a-sample-policy-protected-pdf-document}

1. Faça logon na AEM Assets como administrador.
1. Crie uma pasta AEM Digital Asset Manager e carregue os documentos PDF protegidos por política para a pasta recém-criada.

   Agora, você pode pesquisar os documentos protegidos por política usando AEM pesquisa.

