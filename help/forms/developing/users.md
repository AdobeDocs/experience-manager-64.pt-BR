---
title: Gerenciar usuários
seo-title: Gerenciar usuários
description: Use a API de gerenciamento de usuários para criar aplicativos clientes que possam gerenciar funções, permissões e principais (que podem ser usuários ou grupos), bem como autenticar usuários.
seo-description: Use a API de gerenciamento de usuários para criar aplicativos clientes que possam gerenciar funções, permissões e principais (que podem ser usuários ou grupos), bem como autenticar usuários.
uuid: 68d8a0bc-6e3d-4286-ba5c-534dcf58cb84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 95804bff-9e6f-4807-aae4-790bd9e7cb57
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '6244'
ht-degree: 0%

---


# Gerenciar usuários {#managing-users}

**Sobre o Gerenciamento de usuários**

Você pode usar a API de gerenciamento de usuários para criar aplicativos clientes que possam gerenciar funções, permissões e principais (que podem ser usuários ou grupos), bem como autenticar usuários. A API de gerenciamento de usuários consiste nas seguintes APIs do AEM Forms:

* API de Serviço do Gerenciador de Diretórios
* API de Serviço do Gerenciador de Autenticação
* API de Serviço do Gerenciador de Autorização

O Gerenciamento de usuários permite que você atribua, remova e determine funções e permissões. Ela também permite atribuir, remover e consultar domínios, usuários e grupos. Por fim, você pode usar o Gerenciamento de usuários para autenticar usuários.

Em [Adicionar usuários](users.md#adding-users) você entenderá como adicionar usuários de forma programática. Esta seção usa a API do Serviço do Gerenciador de Diretórios.

Em [Excluindo usuários](users.md#deleting-users) você entenderá como excluir usuários por programação. Esta seção usa a API do Serviço do Gerenciador de Diretórios.

Em [Gerenciar usuários e grupos](users.md#managing-users-and-groups) você entenderá a diferença entre um usuário local e um usuário de diretório, e verá exemplos de como usar as APIs do Java e do serviço da Web para gerenciar usuários e grupos de forma programática. Esta seção usa a API do Serviço do Gerenciador de Diretórios.

Em [Gerenciamento de funções e permissões](users.md#managing-roles-and-permissions) você aprenderá sobre as funções e permissões do sistema e o que poderá fazer de forma programática para aumentá-las, e verá exemplos de como usar as APIs do Java e do serviço da Web para gerenciar programaticamente funções e permissões. Esta seção utiliza a API de Serviço do Gerenciador de Diretórios e a API de Serviço do Gerenciador de Autorizações.

Em [Autenticando usuários](users.md#authenticating-users) você verá exemplos de como usar as APIs do Java e do serviço da Web para autenticar usuários programaticamente. Esta seção usa a API de serviço do Gerenciador de autorizações.

**Noções básicas sobre o processo de autenticação**

O Gerenciamento de usuários fornece funcionalidade de autenticação integrada e também fornece a capacidade de conectá-la a seu próprio provedor de autenticação. Quando o Gerenciamento de usuários recebe uma solicitação de autenticação (por exemplo, um usuário tenta fazer logon), ele transmite as informações do usuário ao provedor de autenticação para autenticação. O Gerenciamento de usuários recebe os resultados do provedor de autenticação depois que ele autentica o usuário.

O diagrama a seguir mostra a interação entre um usuário final tentando fazer logon, o Gerenciamento de usuários e o provedor de autenticação.

![mu_mu_umauth_process](assets/mu_mu_umauth_process.png)

A tabela a seguir descreve cada etapa do processo de autenticação.

<table> 
 <thead> 
  <tr> 
   <th><p>Etapa</p></th> 
   <th><p>Descrição</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>1</p></td> 
   <td><p>Um usuário tenta fazer logon em um serviço que chama o Gerenciamento de usuários. O usuário especifica um nome de usuário e senha. </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>O Gerenciamento de usuários envia o nome de usuário e a senha, bem como informações de configuração, para o provedor de autenticação.</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>O provedor de autenticação se conecta ao armazenamento de usuários e autentica o usuário.</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>O provedor de autenticação retorna os resultados para o Gerenciamento de usuários.</p></td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>O Gerenciamento de usuários permite que o usuário faça logon ou negue acesso ao produto.</p></td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Se o fuso horário do servidor for diferente do fuso horário do cliente, ao consumir o WSDL para o serviço Gerar PDF do AEM Forms em uma pilha SOAP nativa usando um cliente .NET em um cluster do WebSphere Application Server, o seguinte erro de autenticação do Gerenciamento de Usuário poderá ocorrer:

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**Entendendo o gerenciamento de diretórios**

O Gerenciamento de usuários é empacotado com um provedor de serviço de diretório (o DiretoryManagerService) que oferece suporte a conexões com diretórios LDAP. Se sua organização usar um repositório não LDAP para armazenar registros de usuários, você poderá criar seu próprio provedor de serviços de diretório que funcione com seu repositório.

Os provedores de serviços de diretório recuperam registros de um armazenamento de usuários a pedido do Gerenciamento de usuários. O Gerenciamento de usuários armazena em cache regularmente registros de usuários e grupos no banco de dados para melhorar o desempenho.

O provedor de serviço de diretório pode ser usado para sincronizar o banco de dados do Gerenciamento de usuários com o repositório de usuários. Essa etapa garante que todas as informações do diretório de usuário e todos os registros de usuário e grupo estejam atualizados.

Além disso, o DiretoryManagerService fornece a capacidade de criar e gerenciar domínios. Os domínios definem bases de usuários diferentes. O limite de um domínio geralmente é definido de acordo com a maneira como sua organização está estruturada ou como sua loja de usuários está configurada. Os domínios Gerenciamento de usuários fornecem configurações que provedores de autenticação e provedores de serviço de diretório usam.

No XML de configuração que o Gerenciamento de usuários exporta, o nó raiz que tem o valor de atributo `Domains` contém um elemento XML para cada domínio definido para o Gerenciamento de usuários. Cada um desses elementos contém outros elementos que definem os aspectos do domínio associados a provedores de serviços específicos.

**Como entender valores de objectSID**

Ao usar o Ative Diretory, é importante entender que um valor `objectSID` não é um atributo exclusivo em vários domínios. Esse valor armazena o identificador de segurança de um objeto. Em um ambiente de vários domínios (por exemplo, uma árvore de domínios), o valor `objectSID` pode ser diferente.

Um valor `objectSID` seria alterado se um objeto fosse movido de um domínio do Ative Diretory para outro domínio. Alguns objetos têm o mesmo valor `objectSID` em qualquer lugar do domínio. Por exemplo, grupos como BUILTIN\Administrators, BUILTIN\Power Users e assim por diante teriam o mesmo valor `objectSID` independentemente dos domínios. Esses valores `objectSID` são bem conhecidos.

## Adicionar usuários {#adding-users}

Você pode usar a API do Serviço do Gerenciador de Diretórios (Java e serviço da Web) para adicionar usuários de forma programática ao AEM Forms. Depois de adicionar um usuário, você pode usá-lo ao executar uma operação de serviço que requer um usuário. Por exemplo, você pode atribuir uma tarefa ao novo usuário.

### Resumo das etapas {#summary-of-steps}

Para adicionar um usuário, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente DiretoryManagerService.
1. Defina as informações do usuário.
1. Adicione o usuário ao AEM Forms.
1. Verifique se o usuário foi adicionado.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar um cliente DiretoryManagerService**

Antes de executar programaticamente uma operação de serviço do Diretory Manager, crie um cliente de API do Serviço do Diretory Manager.

**Definir informações do usuário**

Ao adicionar um novo usuário usando a API do Serviço do Gerenciador de Diretórios, defina as informações para esse usuário. Normalmente, quando você adiciona um novo usuário, você define os seguintes valores:

* **Nome** do domínio: O domínio ao qual o usuário pertence (por exemplo,  `DefaultDom`).
* **Valor** do identificador do usuário: O valor identificador do usuário (por exemplo,  `wblue`).
* **Tipo** principal: O tipo de usuário (por exemplo, você pode especificar  `USER)`.
* **Nome**: Um determinado nome para o usuário (por exemplo,  `Wendy`).
* **Nome** da família: O nome da família do usuário (por exemplo,  `Blue)`.
* **Localidade**: Informações de localidade para o usuário.

**Adicionar o usuário ao AEM Forms**

Após definir as informações do usuário, é possível adicioná-lo ao AEM Forms. Para adicionar um usuário, chame o método `DirectoryManagerServiceClient` do objeto `createLocalUser`.

**Verificar se o usuário foi adicionado**

Você pode verificar se o usuário foi adicionado para garantir que nenhum problema ocorreu. Localize o novo usuário usando o valor do identificador do usuário.

**Consulte também:**

[Adicionar usuários usando a API do Java](users.md#add-users-using-the-java-api)

[Adicionar usuários usando a API de serviço da Web](users.md#add-users-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Excluir usuários](users.md#deleting-users)

### Adicionar usuários usando a API Java {#add-users-using-the-java-api}

Adicione usuários usando a API do Serviço do Gerenciador de Diretórios (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente DiretoryManagerServices.

   Crie um objeto `DirectoryManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Defina as informações do usuário.

   * Crie um objeto `UserImpl` usando seu construtor.
   * Defina o nome do domínio chamando o método `UserImpl` do objeto `setDomainName`. Passe um valor de string que especifica o nome de domínio.
   * Defina o tipo principal chamando o método `UserImpl` do objeto `setPrincipalType`. Passe um valor de string que especifica o tipo de usuário. Por exemplo, você pode especificar `USER`.
   * Defina o valor do identificador do usuário chamando o método `UserImpl` do objeto `setUserid`. Passe um valor de string que especifica o valor do identificador do usuário. Por exemplo, você pode especificar `wblue`.
   * Defina o nome canônico chamando o método `UserImpl` do objeto `setCanonicalName`. Passe um valor de string que especifica o nome canônico do usuário. Por exemplo, você pode especificar `wblue`.
   * Defina o nome fornecido chamando o método `UserImpl` do objeto `setGivenName`. Passe um valor de string que especifica o nome do usuário. Por exemplo, você pode especificar `Wendy`.
   * Defina o nome da família chamando o método `UserImpl` do objeto `setFamilyName`. Passe um valor de string que especifica o nome da família do usuário. Por exemplo, você pode especificar `Blue`.

   >[!NOTE]
   >
   >Chame um método que pertença ao objeto `UserImpl` para definir outros valores. Por exemplo, é possível definir o valor do local chamando o método `UserImpl` do objeto `setLocale`.

1. Adicione o usuário ao AEM Forms.

   Chame o método `DirectoryManagerServiceClient` do objeto `createLocalUser` e passe os seguintes valores:

   * O objeto `UserImpl` que representa o novo usuário
   * Um valor da string que representa a senha do usuário

   O método `createLocalUser` retorna um valor de string que especifica o valor do identificador de usuário local.

1. Verifique se o usuário foi adicionado.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o valor do identificador do usuário chamando o método `PrincipalSearchFilter` do objeto `setUserId`. Passe um valor de string que representa o valor do identificador do usuário.
   * Chame o método `DirectoryManagerServiceClient` do objeto `findPrincipals` e passe o objeto `PrincipalSearchFilter`. Esse método retorna uma instância `java.util.List`, onde cada elemento é um objeto `User`. Itere pela instância `java.util.List` para localizar o usuário.

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Início rápido (modo SOAP): Adicionar usuários usando a API Java](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Adicionar usuários usando a API do serviço da Web {#add-users-using-the-web-service-api}

Adicione usuários usando a API do Serviço do Gerenciador de Diretórios (serviço da Web):

1. Inclua arquivos de projeto.

   Crie um projeto do Microsoft .NET que use MTOM. Use a seguinte definição WSDL para a referência de serviço: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente DiretoryManagerService.

   * Crie um objeto `DirectoryManagerServiceClient` usando seu construtor padrão.
   * Crie um objeto `DirectoryManagerServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Passe um valor de string que especifica o WSDL para o serviço do AEM Forms (por exemplo, `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Você não precisa usar o atributo `lc_version`. Esse atributo é usado ao criar uma referência de serviço. Certifique-se de especificar `?blob=mtom`.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `DirectoryManagerServiceClient.Endpoint.Binding`. Converta o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `System.ServiceModel.BasicHttpBinding` `MessageEncoding` do objeto para `WSMessageEncoding.Mtom`. Esse valor garante que o MTOM seja usado.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor correspondente da senha ao campo `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Defina as informações do usuário.

   * Crie um objeto `UserImpl` usando seu construtor.
   * Defina o nome do domínio atribuindo um valor de string ao campo `UserImpl` do objeto `domainName`.
   * Defina o tipo principal atribuindo um valor de string ao campo `UserImpl` do objeto `principalType`. Por exemplo, você pode especificar `USER`.
   * Defina o valor do identificador do usuário atribuindo um valor de string ao campo `UserImpl` `userid` do objeto.
   * Defina o valor do nome canônico atribuindo um valor de string ao campo `UserImpl` `canonicalName` do objeto.
   * Defina o valor do nome fornecido atribuindo um valor de string ao campo `UserImpl` do objeto `givenName`.
   * Defina o valor do nome da família atribuindo um valor de string ao campo `UserImpl` do objeto `familyName`.

1. Adicione o usuário ao AEM Forms.

   Chame o método `DirectoryManagerServiceClient` do objeto `createLocalUser` e passe os seguintes valores:

   * O objeto `UserImpl` que representa o novo usuário
   * Um valor da string que representa a senha do usuário

   O método `createLocalUser` retorna um valor de string que especifica o valor do identificador de usuário local.

1. Verifique se o usuário foi adicionado.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o valor do identificador do usuário atribuindo um valor de string que representa o valor do identificador do usuário no campo `PrincipalSearchFilter` `userId` do objeto.
   * Chame o método `DirectoryManagerServiceClient` do objeto `findPrincipals` e passe o objeto `PrincipalSearchFilter`. Este método retorna um objeto de coleção `MyArrayOfUser`, onde cada elemento é um objeto `User`. Itere pela coleção `MyArrayOfUser` para localizar o usuário.

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Excluindo usuários {#deleting-users}

Você pode usar a API do Serviço do Gerenciador de Diretórios (Java e serviço da Web) para excluir programaticamente usuários do AEM Forms. Após excluir um usuário, ele não poderá mais ser usado para executar uma operação de serviço que requer um usuário. Por exemplo, não é possível atribuir uma tarefa a um usuário excluído.

### Resumo das etapas {#summary_of_steps-1}

Para excluir um usuário, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente DiretoryManagerService.
1. Especifique o usuário a ser excluído.
1. Exclua o usuário do AEM Forms.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar um cliente DiretoryManagerService**

Antes de executar programaticamente uma operação de API do Serviço do Gerenciador de Diretórios, crie um cliente de serviço do Gerenciador de Diretórios.

**Especificar o usuário a ser excluído**

Você pode especificar um usuário a ser excluído usando o valor identificador do usuário.

**Excluir o usuário do AEM Forms**

Para excluir um usuário, chame o método `DirectoryManagerServiceClient` do objeto `deleteLocalUser`.

**Consulte também:**

[Excluir usuários usando a API do Java](users.md#delete-users-using-the-java-api)

[Excluir usuários usando a API de serviço da Web](users.md#delete-users-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Adicionar usuários](users.md#adding-users)

### Excluir usuários usando a API Java {#delete-users-using-the-java-api}

Exclua usuários usando a API do Serviço do Gerenciador de Diretórios (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente DiretoryManagerService.

   Crie um objeto `DirectoryManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Especifique o usuário a ser excluído.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o valor do identificador do usuário chamando o método `PrincipalSearchFilter` do objeto `setUserId`. Passe um valor de string que representa o valor do identificador do usuário.
   * Chame o método `DirectoryManagerServiceClient` do objeto `findPrincipals` e passe o objeto `PrincipalSearchFilter`. Esse método retorna uma instância `java.util.List`, onde cada elemento é um objeto `User`. Itere pela instância `java.util.List` para localizar o usuário a ser excluído.

1. Exclua o usuário do AEM Forms.

   Chame o método `DirectoryManagerServiceClient` do objeto `deleteLocalUser` e transmita o valor do campo `User` do objeto `oid`. Chame o método `User` do objeto `getOid`. Use o objeto `User` recuperado da instância `java.util.List`.

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Início rápido (modo EJB): Exclusão de usuários usando a API Java](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Início rápido (modo SOAP): Exclusão de usuários usando a API Java](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Excluir usuários usando a API do serviço da Web {#delete-users-using-the-web-service-api}

Excluir usuários usando a API do Serviço do Gerenciador de Diretórios (serviço da Web):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente DiretoryManagerService.

   * Crie um objeto `DirectoryManagerServiceClient` usando seu construtor padrão.
   * Crie um objeto `DirectoryManagerServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Passe um valor de string que especifica o WSDL para o serviço do AEM Forms (por exemplo, `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Você não precisa usar o atributo `lc_version`. Esse atributo é usado ao criar uma referência de serviço. Certifique-se de especificar `blob=mtom.`
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `DirectoryManagerServiceClient.Endpoint.Binding`. Converta o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `System.ServiceModel.BasicHttpBinding` `MessageEncoding` do objeto para `WSMessageEncoding.Mtom`. Esse valor garante que o MTOM seja usado.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor correspondente da senha ao campo `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Especifique o usuário a ser excluído.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o valor do identificador do usuário atribuindo um valor de string ao campo `PrincipalSearchFilter` `userId` do objeto.
   * Chame o método `DirectoryManagerServiceClient` do objeto `findPrincipals` e passe o objeto `PrincipalSearchFilter`. Este método retorna um objeto de coleção `MyArrayOfUser`, onde cada elemento é um objeto `User`. Itere pela coleção `MyArrayOfUser` para localizar o usuário. O objeto `User` recuperado do objeto de coleção `MyArrayOfUser` é usado para excluir o usuário.

1. Exclua o usuário do AEM Forms.

   Exclua o usuário passando o valor do campo `User` do objeto `oid` para o método `DirectoryManagerServiceClient` do objeto `deleteLocalUser`.

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Criando Grupos {#creating-groups}

Você pode usar a API do Serviço do Gerenciador de Diretórios (Java e serviço da Web) para criar grupos do AEM Forms de forma programática. Depois de criar um grupo, você pode usar esse grupo para executar uma operação de serviço que requer um grupo. Por exemplo, você pode atribuir um usuário ao novo grupo. (Consulte [Gerenciar usuários e grupos](users.md#managing-users-and-groups).)

### Resumo das etapas {#summary_of_steps-2}

Para criar um grupo, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente DiretoryManagerService.
1. Determine se o grupo não existe.
1. Crie o grupo.
1. Execute uma ação com o grupo.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários.

Os seguintes arquivos JAR devem ser adicionados ao classpath do seu projeto:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (obrigatório se o AEM Forms estiver implantado no JBoss)
* jbossall-client.jar (obrigatório se o AEM Forms for implantado no JBoss)

Para obter informações sobre a localização desses arquivos JAR, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Criar um cliente DiretoryManagerService**

Antes de executar programaticamente uma operação de serviço do Diretory Manager, crie um cliente de API do Serviço do Diretory Manager.

**Determine se o grupo existe**

Ao criar um grupo, verifique se o grupo não existe no mesmo domínio. Ou seja, dois grupos não podem ter o mesmo nome no mesmo domínio. Para executar essa tarefa, faça uma pesquisa e filtre os resultados da pesquisa com base em dois valores. Defina o tipo principal como `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` para garantir que somente grupos sejam retornados. Além disso, especifique o nome de domínio.

**Criar o grupo**

Depois de determinar que o grupo não existe no domínio, crie o grupo e especifique os seguintes atributos:

* **CommonName**: O nome do grupo.
* **Domínio**: O domínio no qual o grupo é adicionado.
* **Descrição**: Uma descrição do grupo.

**Executar uma ação com o grupo**

Depois de criar um grupo, você pode executar uma ação usando o grupo . Por exemplo, você pode adicionar um usuário ao grupo. Para adicionar um usuário a um grupo, recupere o valor identificador exclusivo do usuário e do grupo. Passe esses valores para o método `addPrincipalToLocalGroup`.

**Consulte também:**

[Criar grupos usando a API do Java](users.md#create-groups-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Adicionar usuários](users.md#adding-users)

[Excluir usuários](users.md#deleting-users)

### Criar grupos usando a API Java {#create-groups-using-the-java-api}

Crie um grupo usando a API do Serviço do Gerenciador de Diretórios (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente DiretoryManagerService.

   Crie um objeto `DirectoryManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Determine se o grupo existe.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o tipo principal chamando o objeto `PrincipalSearchFilter` do objeto `setPrincipalType`. Passe o valor `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP`.
   * Defina o domínio chamando o objeto `PrincipalSearchFilter` `setSpecificDomainName` do objeto. Passe um valor de string que especifica o nome de domínio.
   * Para localizar um grupo, chame o método `DirectoryManagerServiceClient` do objeto (um principal pode ser um grupo). `findPrincipals` Passe o objeto `PrincipalSearchFilter` que especifica o tipo principal e o nome de domínio. Esse método retorna uma instância `java.util.List` em que cada elemento é uma instância `Group`. Cada instância de grupo está em conformidade com o filtro especificado usando o objeto `PrincipalSearchFilter`.
   * Iterar pela instância `java.util.List`. Para cada elemento, recupere o nome do grupo. Certifique-se de que o nome do grupo não seja igual ao novo nome do grupo.

1. Crie o grupo.

   * Se o grupo não existir, chame o método `Group` do objeto e transmita um valor de string que especifica o nome do grupo.`setCommonName`
   * Chame o método `Group` do objeto `setDescription` e passe um valor de string que especifique a descrição do grupo.
   * Chame o método `Group` do objeto e transmita um valor de string que especifica o nome do domínio.`setDomainName`
   * Chame o método `DirectoryManagerServiceClient` do objeto `createLocalGroup` e passe a instância `Group`.

   O método `createLocalUser` retorna um valor de string que especifica o valor do identificador de usuário local.

1. Execute uma ação com o grupo.

   * Crie um objeto `PrincipalSearchFilter` usando seu construtor.
   * Defina o valor do identificador do usuário chamando o método `PrincipalSearchFilter` do objeto `setUserId`. Passe um valor de string que representa o valor do identificador do usuário.
   * Chame o método `DirectoryManagerServiceClient` do objeto `findPrincipals` e passe o objeto `PrincipalSearchFilter`. Esse método retorna uma instância `java.util.List`, onde cada elemento é um objeto `User`. Itere pela instância `java.util.List` para localizar o usuário.
   * Adicione um usuário ao grupo, chamando o método `DirectoryManagerServiceClient` do objeto `addPrincipalToLocalGroup`. Passe o valor de retorno do método `User` do objeto `getOid`. Passe o valor de retorno do método `Group` dos objetos `getOid` (use a instância `Group` que representa o novo grupo).

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gerenciando usuários e grupos {#managing-users-and-groups}

Este tópico descreve como você pode usar o (Java) para atribuir, remover e consultar domínios, usuários e grupos de forma programática.

>[!NOTE]
>
>Ao configurar um domínio, você deve definir o identificador exclusivo para grupos e usuários. O atributo que é escolhido não só deve ser exclusivo no ambiente LDAP, como também deve ser imutável e não será alterado no diretório. Este atributo também deve ser de um tipo de dados de sequência simples (a única exceção atualmente permitida para o Ative Diretory 2000/2003 é `"objectsid"`, que é um valor binário). O atributo `"GUID"` do Novell eDirectory , por exemplo, não é um tipo de dados de string simples e, portanto, não funcionará.

* Para o Ative Diretory, use `"objectsid"`.
* Para SunOne, use `"nsuniqueid"`.

>[!NOTE]
>
>Não há suporte para a criação de vários usuários e grupos locais enquanto uma sincronização de diretório LDAP está em andamento. Tentar esse processo pode resultar em erros.

### Resumo das etapas {#summary_of_steps-3}

Para gerenciar usuários e grupos, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente DiretoryManagerService.
1. Chame as operações apropriadas do usuário ou grupo.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente DiretoryManagerService**

Antes de executar programaticamente uma operação de serviço do Diretory Manager, você deve criar um cliente de serviço do Diretory Manager. Com a API Java, isso é feito criando um objeto `DirectoryManagerServiceClient`. Com a API do serviço da Web, isso é feito criando um objeto `DirectoryManagerServiceService`.

**Chamar as operações apropriadas do usuário ou grupo**

Depois de criar o cliente de serviço, você pode invocar as operações de gerenciamento de usuários ou grupos. O cliente de serviço permite atribuir, remover e consultar domínios, usuários e grupos. Observe que é possível adicionar um principal de diretório ou um principal local a um grupo local, mas não é possível adicionar um principal local a um grupo de diretórios.

**Consulte também:**

[Gerenciamento de usuários e grupos usando a API do Java](users.md#managing-users-and-groups-using-the-java-api)

[Gerenciamento de usuários e grupos usando a API de serviço da Web](users.md#managing-users-and-groups-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Gerenciador de usuários](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Gerenciamento de usuários e grupos usando a API do Java {#managing-users-and-groups-using-the-java-api}

Para gerenciar de forma programática usuários, grupos e domínios usando o (Java), execute as seguintes tarefas:

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java. Para obter informações sobre a localização desses arquivos, consulte [Incluindo arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Crie um cliente DiretoryManagerService.

   Crie um objeto `DirectoryManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão. Para obter informações, consulte [Definindo propriedades de conexão ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Chame as operações apropriadas do usuário ou grupo.

   Para localizar um usuário ou grupo, chame um dos métodos do objeto `DirectoryManagerServiceClient` para localizar entidades principais (já que uma entidade principal pode ser um usuário ou um grupo). No exemplo abaixo, o método `findPrincipals` é chamado usando um filtro de pesquisa (um objeto `PrincipalSearchFilter`).

   Como o valor de retorno, nesse caso, é um `java.util.List` contendo `Principal` objetos, repita o resultado e converta os objetos `Principal` em `User` ou `Group`.

   Usando o objeto `User` ou `Group` resultante (que ambos herdam da interface `Principal`), recupere as informações necessárias nos workflows. Por exemplo, o nome de domínio e os valores de nome canônico, combinados, identificam exclusivamente um principal. Eles são recuperados chamando os métodos `Principal` do objeto `getDomainName` e `getCanonicalName`, respectivamente.

   Para excluir um usuário local, chame o método `DirectoryManagerServiceClient` do objeto e passe o identificador do usuário.`deleteLocalUser`

   Para excluir um grupo local, chame o método `DirectoryManagerServiceClient` do objeto e passe o identificador do grupo.`deleteLocalGroup`

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gerenciamento de usuários e grupos usando a API do serviço da Web {#managing-users-and-groups-using-the-web-service-api}

Para gerenciar de forma programática usuários, grupos e domínios usando a API do serviço do Diretory Manager (serviço da Web), execute as seguintes tarefas:

1. Inclua arquivos de projeto.

   * Crie uma assemblagem de cliente Microsoft .NET que consome o Gerenciador de Diretórios WSDL. (Consulte [Chamar AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Faça referência ao assembly do cliente Microsoft .NET. (Consulte [Criando um assembly de cliente .NET que usa a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Crie um cliente DiretoryManagerService.

   Crie um objeto `DirectoryManagerServiceService` usando o construtor da classe proxy.

1. Chame as operações apropriadas do usuário ou grupo.

   Para localizar um usuário ou grupo, chame um dos métodos do objeto `DirectoryManagerServiceService` para localizar entidades principais (já que uma entidade principal pode ser um usuário ou um grupo). No exemplo abaixo, o método `findPrincipalsWithFilter` é chamado usando um filtro de pesquisa (um objeto `PrincipalSearchFilter`). Ao usar um objeto `PrincipalSearchFilter`, os principais locais só serão retornados se a propriedade `isLocal` estiver definida como `true`. Esse comportamento é diferente do que ocorria com a API do Java.

   >[!NOTE]
   >
   >Se o número máximo de resultados não for especificado no filtro de pesquisa (por meio do campo `PrincipalSearchFilter.resultsMax` ), um máximo de 1000 resultados será retornado. Esse é um comportamento diferente do que ocorre com a API do Java, em que 10 resultados são o máximo padrão. Além disso, os métodos de pesquisa como `findGroupMembers` não produzirão resultados, a menos que o número máximo de resultados seja especificado no filtro de pesquisa (por exemplo, por meio do campo `GroupMembershipSearchFilter.resultsMax`). Isso se aplica a todos os filtros de pesquisa herdados da classe `GenericSearchFilter`. Para obter mais informações, consulte [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Como o valor de retorno, nesse caso, é um `object[]` contendo `Principal` objetos, repita o resultado e converta os objetos `Principal` em `User` ou `Group`.

   Usando o objeto `User` ou `Group` resultante (que ambos herdam da interface `Principal`), recupere as informações necessárias nos workflows. Por exemplo, o nome de domínio e os valores de nome canônico, combinados, identificam exclusivamente um principal. Eles são recuperados chamando os campos `Principal` `domainName` e `canonicalName` do objeto, respectivamente.

   Para excluir um usuário local, chame o método `DirectoryManagerServiceService` do objeto e passe o identificador do usuário.`deleteLocalUser`

   Para excluir um grupo local, chame o método `DirectoryManagerServiceService` do objeto e passe o identificador do grupo.`deleteLocalGroup`

**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Gerenciando funções e permissões {#managing-roles-and-permissions}

Este tópico descreve como você pode usar a API de serviço do Gerenciador de autorização (Java) para atribuir, remover e determinar funções e permissões de forma programática.

No AEM Forms, uma *role* é um grupo de permissões para acessar um ou mais recursos no nível do sistema. Essas permissões são criadas por meio do Gerenciamento de usuários e são aplicadas pelos componentes do serviço. Por exemplo, um Administrador pode atribuir a função de &quot;Autor do conjunto de políticas&quot; a um grupo de usuários. O Rights Management permitiria que os usuários desse grupo com essa função criassem conjuntos de políticas por meio do console de administração.

Há dois tipos de funções: *funções padrão* e *funções personalizadas*. As funções padrão (*funções do sistema)* já estão residentes no AEM Forms. Pressupõe-se que as funções padrão não possam ser excluídas ou modificadas pelo administrador e, portanto, sejam imutáveis. As funções personalizadas criadas pelo administrador, que podem posteriormente modificá-las ou excluí-las, são mutáveis.

As funções facilitam o gerenciamento de permissões. Quando uma função é atribuída a um principal, um conjunto de permissões é automaticamente atribuído a esse principal e todas as decisões específicas relacionadas ao acesso do principal são baseadas nesse conjunto geral de permissões atribuídas.

### Resumo das etapas {#summary_of_steps-4}

Para gerenciar funções e permissões, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente AuthorizationManagerService.
1. Chame a função ou as operações de permissão apropriadas.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente AuthorizationManagerService**

Antes de poder executar programaticamente uma operação User Management AuthorizationManagerService, tem de criar um cliente AuthorizationManagerService. Com a API Java, isso é feito criando um objeto `AuthorizationManagerServiceClient`.

**Chamar a função ou as operações de permissão apropriadas**

Depois de criar o cliente de serviço, você pode invocar as operações de função ou permissão. O cliente de serviço permite atribuir, remover e determinar funções e permissões.

**Consulte também:**

[Gerenciamento de funções e permissões usando a API do Java](users.md#managing-roles-and-permissions-using-the-java-api)

[Gerenciamento de funções e permissões usando a API de serviço da Web](users.md#managing-roles-and-permissions-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Gerenciador de usuários](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Gerenciamento de funções e permissões usando a API Java {#managing-roles-and-permissions-using-the-java-api}

Para gerenciar funções e permissões usando a API do Serviço do Gerenciador de Autorização (Java), execute as seguintes tarefas:

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente AuthorizationManagerService.

   Crie um objeto `AuthorizationManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Chame a função ou as operações de permissão apropriadas.

   Para atribuir uma função a um principal, chame o método `AuthorizationManagerServiceClient` do objeto e transmita os seguintes valores:`assignRole`

   * Um objeto `java.lang.String` que contém o identificador da função
   * Uma matriz de objetos `java.lang.String` contendo os identificadores principais.

   Para remover uma função de um principal, chame o método `AuthorizationManagerServiceClient` do objeto e transmita os seguintes valores:`unassignRole`

   * Um objeto `java.lang.String` que contém o identificador da função.
   * Uma matriz de objetos `java.lang.String` contendo os identificadores principais.


**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Início rápido (modo SOAP): Gerenciamento de funções e permissões usando a API do Java](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gerenciamento de funções e permissões usando a API do serviço da Web {#managing-roles-and-permissions-using-the-web-service-api}

Gerencie funções e permissões usando a API do Serviço do Gerenciador de Autorizações (serviço da Web):

1. Inclua arquivos de projeto.

   Crie um projeto do Microsoft .NET que use MTOM. Certifique-se de usar a seguinte definição de WSDL: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Substitua `localhost` pelo endereço IP do servidor que hospeda o AEM Forms.

1. Crie um cliente AuthorizationManagerService.

   * Crie um objeto `AuthorizationManagerServiceClient` usando seu construtor padrão.
   * Crie um objeto `AuthorizationManagerServiceClient.Endpoint.Address` usando o construtor `System.ServiceModel.EndpointAddress`. Passe um valor de string que especifica o WSDL para o serviço do AEM Forms (por exemplo, `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`.) Você não precisa usar o atributo `lc_version`. Esse atributo é usado ao criar uma referência de serviço.
   * Crie um objeto `System.ServiceModel.BasicHttpBinding` obtendo o valor do campo `AuthorizationManagerServiceClient.Endpoint.Binding`. Converta o valor de retorno em `BasicHttpBinding`.
   * Defina o campo `System.ServiceModel.BasicHttpBinding` `MessageEncoding` do objeto para `WSMessageEncoding.Mtom`. Esse valor garante que o MTOM seja usado.
   * Ative a autenticação HTTP básica executando as seguintes tarefas:

      * Atribua o nome de usuário dos formulários AEM ao campo `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName`.
      * Atribua o valor correspondente da senha ao campo `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password`.
      * Atribua o valor constante `HttpClientCredentialType.Basic` ao campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Atribua o valor constante `BasicHttpSecurityMode.TransportCredentialOnly` ao campo `BasicHttpBindingSecurity.Security.Mode`.

1. Chame a função ou as operações de permissão apropriadas.

   Para atribuir uma função a um principal, chame o método `AuthorizationManagerServiceClient` do objeto e transmita os seguintes valores:`assignRole`

   * Um objeto `string` que contém o identificador da função
   * Um objeto `MyArrayOf_xsd_string` que contém os identificadores principais.

   Para remover uma função de um principal, chame o método `AuthorizationManagerServiceService` do objeto e transmita os seguintes valores:`unassignRole`

   * Um objeto `string` que contém o identificador da função.
   * Uma matriz de objetos `string` contendo os identificadores principais.


**Consulte também:**

[Resumo das etapas](users.md#summary-of-steps)

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Autenticando usuários {#authenticating-users}

Este tópico descreve como você pode usar a API do Serviço do Gerenciador de Autenticação (Java) para permitir que seus aplicativos cliente autenticem usuários programaticamente.

A autenticação do usuário pode ser necessária para interagir com um banco de dados corporativo ou outros repositórios corporativos que armazenam dados protegidos.

Considere, por exemplo, um cenário em que um usuário insere um nome de usuário e senha em uma página da Web e envia os valores a um servidor de aplicativos J2EE que hospeda o Forms. Um aplicativo personalizado do Forms pode autenticar o usuário com o serviço do Gerenciador de autenticação.

Se a autenticação for bem-sucedida, o aplicativo acessa um banco de dados corporativo seguro. Caso contrário, uma mensagem será enviada ao usuário informando que ele não é um usuário autorizado.

O diagrama a seguir mostra o fluxo lógico do aplicativo.

![au_au_umauth_process](assets/au_au_umauth_process.png)

A tabela a seguir descreve as etapas neste diagrama

<table> 
 <thead> 
  <tr> 
   <th><p>Etapa</p></th> 
   <th><p>Descrição</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>3</p></td> 
   <td><p>O usuário acessa um site e especifica um nome de usuário e senha. Essas informações são enviadas para um servidor de aplicativos J2EE que hospeda a AEM Forms.</p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>As credenciais do usuário são autenticadas com o serviço do Gerenciador de Autenticação. Se as credenciais do usuário forem válidas, o fluxo de trabalho prosseguirá para a etapa 3. Caso contrário, uma mensagem será enviada ao usuário informando que ele não é um usuário autorizado.</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>As informações do usuário e um design de formulário são recuperadas de um banco de dados corporativo seguro. </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>As informações do usuário são unidas a um design de formulário e o formulário é renderizado para o usuário. </p></td> 
  </tr> 
 </tbody> 
</table>

### Resumo das etapas {#summary_of_steps-5}

Para autenticar um usuário programaticamente, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente AuthenticationManagerService.
1. Chame a operação de autenticação.
1. Se necessário, recupere o contexto para que o aplicativo cliente possa encaminhá-lo para outro serviço da AEM Forms para autenticação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente AuthenticationManagerService**

Antes de poder autenticar programaticamente um usuário, você deve criar um cliente AuthenticationManagerService . Ao usar a API do Java, crie um objeto `AuthenticationManagerServiceClient` .

**Chamar a operação de autenticação**

Depois de criar o cliente de serviço, você pode invocar a operação de autenticação. Essa operação precisará de informações sobre o usuário, como o nome e a senha do usuário. Se o usuário não autenticar, uma exceção será lançada.

**Recuperar o contexto de autenticação**

Depois de autenticar o usuário, você pode criar um contexto com base no usuário autenticado. Em seguida, você pode usar o conteúdo para chamar outros serviços da AEM Forms. Por exemplo, você pode usar o contexto para criar um `EncryptionServiceClient` e criptografar um documento PDF com uma senha. Certifique-se de que o usuário que foi autenticado tenha a função chamada `Services User` que é necessária para chamar um serviço do AEM Forms.

**Consulte também:**

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Gerenciador de usuários](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[Criptografar documentos PDF com uma senha](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Autentique um usuário usando a API Java {#authenticate-a-user-using-the-java-api}

Autentique um usuário usando a API do Serviço do Gerenciador de Autenticação (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente AuthenticationManagerServices.

   Crie um objeto `AuthenticationManagerServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Chame a operação de autenticação.

   Chame o método `AuthenticationManagerServiceClient` do objeto `authenticate` e passe os seguintes valores:

   * Um objeto `java.lang.String` que contém o nome do usuário.
   * Uma matriz de bytes (um objeto `byte[]`) contendo a senha do usuário. Você pode obter o objeto `byte[]` chamando o método `java.lang.String` do objeto `getBytes`.

   O método authentication retorna um objeto `AuthResult`, que contém informações sobre o usuário autenticado.

1. Recupere o contexto de autenticação.

   Chame o método `ServiceClientFactory` do objeto `getContext`, que retornará um objeto `Context`.

   Em seguida, chame o método `Context` do objeto e passe `AuthResult`.`initPrincipal`

### Autenticar um usuário usando a API do serviço da Web {#authenticate-a-user-using-the-web-service-api}

Autentique um usuário usando a API do Serviço do Gerenciador de Autenticação (serviço da Web):

1. Inclua arquivos de projeto.

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Gerenciador de Autenticação. (Consulte [Chamar AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Faça referência ao assembly do cliente Microsoft .NET. (Consulte &quot;Fazendo referência ao assembly do cliente .NET&quot; em [Chamando o AEM Forms usando a codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Crie um cliente AuthenticationManagerService.

   Crie um objeto `AuthenticationManagerServiceService` usando o construtor da classe proxy.

1. Chame a operação de autenticação.

   Chame o método `AuthenticationManagerServiceClient` do objeto `authenticate` e passe os seguintes valores:

   * Um objeto `string` que contém o nome do usuário
   * Uma matriz de bytes (um objeto `byte[]`) contendo a senha do usuário. Você pode obter o objeto `byte[]` convertendo um objeto `string` contendo a senha em uma matriz `byte[]` usando a lógica mostrada no exemplo abaixo.
   * O valor retornado será um objeto `AuthResult`, que pode ser usado para recuperar informações sobre o usuário. No exemplo abaixo, as informações do usuário são recuperadas obtendo primeiro o campo `AuthResult` do objeto `authenticatedUser` e obtendo subsequentemente os campos `canonicalName` e `domainName` do objeto resultante.`User`

**Consulte também:**

[Chamar o AEM Forms usando MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chamar o AEM Forms usando SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Sincronizando Usuários Programaticamente {#programmatically-synchronizing-users}

Você pode sincronizar usuários por programação usando a API de gerenciamento de usuários. Ao sincronizar usuários, você está atualizando o AEM Forms com dados de usuários localizados no repositório de usuários. Por exemplo, suponha que você adicione novos usuários ao repositório de usuários. Após executar uma operação de sincronização, os novos usuários se tornarão usuários AEM formulários. Além disso, os usuários que não estão mais em seu repositório de usuários são removidos do AEM Forms.

O diagrama a seguir mostra a sincronização do AEM Forms com um repositório de usuários.

![ps_ps_umauth_sync](assets/ps_ps_umauth_sync.png)

A tabela a seguir descreve as etapas neste diagrama

<table> 
 <thead> 
  <tr> 
   <th><p>Etapa</p></th> 
   <th><p>Descrição</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>3</p></td> 
   <td><p>Um aplicativo cliente solicita que o AEM Forms execute uma operação de sincronização.</p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>O AEM Forms executa uma operação de sincronização.</p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>As informações do usuário são atualizadas.</p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>Um usuário pode exibir as informações atualizadas do usuário. </p></td> 
  </tr> 
 </tbody> 
</table>

### Resumo das etapas {#summary_of_steps-6}

Para sincronizar usuários programaticamente, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente UserManagerUtilServiceClient .
1. Especifique o domínio empresarial.
1. Chame a operação de autenticação.
1. Determine se a operação de sincronização foi concluída

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente UserManagerUtilServiceClientclient**

Antes de sincronizar programaticamente os usuários, você deve criar um objeto `UserManagerUtilServiceClient`.

**Especificar o domínio empresarial**

Antes de executar uma operação de sincronização usando a API de gerenciamento de usuários, especifique o domínio corporativo ao qual os usuários pertencem. Você pode especificar um ou vários domínios corporativos. Antes de executar uma operação de sincronização programaticamente, é necessário configurar um domínio corporativo usando o Console de Administração. (Consulte [ajuda de administração](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Chamar a operação de sincronização**

Após especificar um ou mais domínios corporativos, é possível executar a operação de sincronização. O tempo necessário para executar essa operação depende do número de registros de usuário localizados no repositório de usuários.

**Determine se a operação de sincronização foi concluída**

Após executar uma operação de sincronização programaticamente, você pode determinar se a operação foi concluída.

**Consulte também:**

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Gerenciador de usuários](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[Criptografar documentos PDF com uma senha](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Sincronização programática de usuários usando a API Java {#programmatically-synchronizing-users-using-the-java-api}

Sincronize usuários usando a API de gerenciamento de usuários (Java):

1. Inclua arquivos de projeto.

   Inclua arquivos JAR do cliente, como adobe-usermanager-client.jar e adobe-usermanager-util-client.jar, no caminho de classe do seu projeto Java.

1. Crie um cliente UserManagerUtilServiceClient .

   Crie um objeto `UserManagerUtilServiceClient` usando seu construtor e transmitindo um objeto `ServiceClientFactory` que contenha propriedades de conexão.

1. Especifique o domínio empresarial.

   * Chame o método `UserManagerUtilServiceClient` do objeto `scheduleSynchronization` para iniciar a operação de sincronização do usuário.
   * Crie uma instância `java.util.Set` usando um construtor `HashSet`. Certifique-se de especificar `String` como o tipo de dados. Essa instância `Java.util.Set` armazena os nomes de domínio aos quais a operação de sincronização se aplica.
   * Para cada nome de domínio a ser adicionado, chame o método de adição do objeto `java.util.Set` e passe o nome de domínio.

1. Chame a operação de sincronização.

   Chame o método `ServiceClientFactory` do objeto `getContext`, que retornará um objeto `Context`.

   Em seguida, chame o método `Context` do objeto e passe `AuthResult`.`initPrincipal`

**Consulte também:**

[Sincronização programática de usuários](users.md#programmatically-synchronizing-users)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
