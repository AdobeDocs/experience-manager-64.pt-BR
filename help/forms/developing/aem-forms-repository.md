---
title: Trabalhar com o repositório do AEM Forms
seo-title: Working with AEM Forms Repository
description: Gerencie o repositório do AEM Forms para criar pastas, gravar, listar, ler, atualizar recursos e pesquisar recursos usando a API do Java e a API do serviço da Web. Além disso, saiba como criar relacionamentos de recursos, bloquear e excluir recursos.
seo-description: Manage AEM Forms repository to create folders, write, list, read, update resources, and search resources using the Java API and Web Service API. In addition, learn how to create resource relationships, lock and delete resources.
uuid: 6ead49f9-ca0d-4ee4-86a6-0a9ced6ec4f8
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: d2c95881-6c02-4e34-85af-84607df54287
role: Developer
exl-id: e006c32b-edff-40f2-8c0a-228008dcf03a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '9146'
ht-degree: 0%

---

# Trabalhar com o repositório do AEM Forms {#working-with-aem-forms-repository}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

**Sobre o Serviço de Repositório**

O serviço Repositório fornece serviços de armazenamento e gerenciamento de recursos para a AEM Forms. Quando os desenvolvedores criam uma *AEM Forms* , eles podem implantar os ativos no repositório em vez do sistema de arquivos. Os ativos podem incluir qualquer tipo de material adicional, incluindo formulários XML, PDF forms (incluindo formulários Acrobat), fragmentos de formulário, imagens, perfis, políticas, arquivos SWF, arquivos DDX, esquemas XML, arquivos WSDL e dados de teste.

Por exemplo, considere o seguinte aplicativo Forms chamado *Aplicativos/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Observe que há um arquivo chamado Loan.xdp localizado na Pasta de formulários. Para acessar esse design de formulário, especifique o caminho completo (incluindo a versão): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Para obter informações sobre como criar um aplicativo do Forms usando o Workbench, consulte [Ajuda do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

O caminho para um recurso localizado no repositório do AEM Forms é:

`Applications/Application-name/Application-version/Folder.../Filename`

Os valores a seguir mostram alguns exemplos de valores de URI:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>Você pode navegar pelo AEM Forms Repository usando um navegador da Web. Para navegar pelo repositório, insira o seguinte URL em um navegador da Web https://[nome do servidor]:[porta do servidor]/repository. Você pode verificar os resultados de início rápido associados à seção Trabalhar com repositório do AEM Forms usando um navegador da Web. Por exemplo, se você adicionar conteúdo ao Repositório AEM Forms, poderá ver o conteúdo em um navegador da Web. (Consulte [Início rápido (modo SOAP): Gravação de um recurso usando a API Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

A API do repositório fornece várias operações que podem ser usadas para armazenar e recuperar informações do repositório. Por exemplo, você pode obter uma lista de recursos ou recuperar recursos específicos que são armazenados no repositório quando um recurso é necessário como parte do processamento de um aplicativo.

>[!NOTE]
>
>A API do repositório não pode ser usada para interagir com os Serviços de conteúdo (obsoleto). Para interagir com os serviços de conteúdo (obsoleto), use a API de gerenciamento de documentos.

Com a API do serviço de repositório, é possível realizar as seguintes tarefas:

* Criar pastas. Consulte [Criação de pastas](aem-forms-repository.md#creating-folders).
* Escreva recursos e suas propriedades. Consulte [Escrever recursos](aem-forms-repository.md#writing-resources).
* Listar recursos em uma determinada coleção ou relacionados a outros recursos. Consulte [Listando recursos](aem-forms-repository.md#listing-resources).
* Leia os recursos e suas propriedades. Consulte [Lendo recursos](aem-forms-repository.md#reading-resources).
* Atualize os recursos e suas propriedades. Consulte [Atualização de recursos](aem-forms-repository.md#updating-resources).
* Pesquise recursos, incluindo seu histórico, recursos relacionados e propriedades. Consulte [Pesquisar recursos](aem-forms-repository.md#searching-for-resources).
* Especifique as relações entre recursos. Consulte [Criando Relacionamentos de Recursos](aem-forms-repository.md#creating-resource-relationships).
* Gerencie o controle de acesso a recursos, incluindo o bloqueio e o desbloqueio de recursos e a leitura e gravação de ACLs (Listas de Controle de Acesso). Consulte [Bloquear recursos](aem-forms-repository.md#locking-resources).
* Exclua recursos e suas propriedades. Consulte [Exclusão de recursos](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Usando a API do repositório, não é possível gerenciar o controle de acesso a recursos, pesquisar recursos ou especificar relacionamentos de recursos usando um repositório ECM.

>[!NOTE]
>
>Quando um PDF criptografado é gravado no repositório, o recurso de extração de relacionamento automatizado não pode ser usado. Caso contrário, um PDF criptografado poderá ser armazenado no repositório e recuperado posteriormente. O recuperador pode optar por descriptografar o PDF depois que ele for recuperado do repositório.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Criação de pastas {#creating-folders}

Pastas (coleções de recursos) são usadas para armazenar objetos (arquivos ou recursos) em agrupamentos organizados. As pastas podem conter recursos e outras pastas, também conhecidas como subpastas. Os recursos só podem ser armazenados em uma pasta de cada vez.

Os arquivos herdam as listas de controle de acesso (ACLs) das pastas e as subpastas herdam as ACLs de suas pastas pai. Portanto, as pastas pai devem existir antes que você possa criar pastas filho. O IDE permite que você interaja somente com base em pastas, não com base em arquivos. Não é possível converter pastas e não é necessário fazer isso; uma pasta não contém dados propriamente dita. Em vez disso, é apenas um container para recursos que contêm dados. A ACL padrão é uma permissão de nível de sistema, o que significa que os usuários devem ter permissões de nível de sistema (ler, gravar, navegar, gerenciar ACLs) até que alguém dê a eles permissões para uma pasta específica. As ACLs só funcionam no IDE.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary-of-steps}

Para criar uma pasta, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie o cliente de serviço.
1. Crie a pasta .
1. Escreva a pasta no repositório.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de criar uma coleção de recursos de forma programática, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Criar a pasta**

Chame o método do serviço Repositório para criar a coleção de recursos e preencher a coleção de recursos com informações de identificação, incluindo UUID, nome da pasta e descrição.

**Escreva a pasta no repositório**

Chame o método do serviço Repositório para gravar a coleção de recursos, especificando o URI da pasta de destino.

**Consulte também**

[Criar pastas usando a API do Java](aem-forms-repository.md#create-folders-using-the-java-api)

[Criar pastas usando a API do serviço da Web](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Criar pastas usando a API do Java {#create-folders-using-the-java-api}

Crie uma pasta usando a API do serviço do repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos de projeto no caminho de classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Criar a pasta

   Para criar uma coleção de recursos, primeiro crie um `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` objeto.

   Chame o `repositoryInfomodelFactoryBean` do objeto `newResourceCollection` e transmitir os seguintes parâmetros:

   * A `com.adobe.repository.infomodel.Id` Identificador de UUID a ser atribuído ao recurso.
   * A `com.adobe.repository.infomodel.Lid` Identificador de UUID a ser atribuído ao recurso.
   * A `java.lang.String` contendo o nome da coleção de recursos. Por exemplo, `FormsFolder`.

   O método retorna um `com.adobe.repository.infomodel.bean.ResourceCollection` objeto que representa a nova pasta.

   Defina a descrição da pasta usando o `setDescription` e transmita no seguinte parâmetro:

   * A `String` que descreve a coleção de recursos. Neste exemplo, `"test Folder"` é usada `.`


1. Escreva a pasta no repositório

   Chame o `ResourceRepositoryClient` do objeto `writeResource` e transmita no URI da pasta e o `ResourceCollection` objeto. Por exemplo, o URI para a pasta pode ser o seguinte valor `/Applications/FormsApplication/1.0/`.

   O método retorna uma instância do recém-criado `com.adobe.repository.infomodel.bean.Resource` objeto. Você pode, por exemplo, recuperar o valor identificador do novo recurso chamando a função `com.adobe.repository.infomodel.bean.Resource` do objeto `getId` método .

**Consulte também**

[Criação de pastas](aem-forms-repository.md#creating-folders)

[Início rápido (modo SOAP): Criação de uma pasta usando a API do Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Criar pastas usando a API do serviço da Web {#create-folders-using-the-web-service-api}

Crie uma pasta usando a API do serviço do Repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório usando base64.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto que contém o nome de usuário e a senha.

1. Criar a pasta

   Crie a pasta usando o construtor padrão para a `ResourceCollection` classe e transmita nos seguintes parâmetros:

   * Um `Id` objeto , que é criado chamando o construtor padrão para o `Id` classe e atribuída à `Resource` do objeto `id` campo.
   * Um `Lid` objeto , que é criado chamando o construtor padrão para o `Lid` classe e atribuída à `Resource` do objeto `lid` campo.
   * Uma string contendo o nome da coleção de recursos, que é atribuída à variável `Resource` do objeto `name` campo. O nome usado neste exemplo é `"testfolder"`.
   * Uma string contendo a descrição da coleção de recursos, que é atribuída à variável `Resource` do objeto `description` campo. A descrição usada neste exemplo é `"test folder"`.

1. Escreva a pasta no repositório

   Chame o `RepositoryServiceService` do objeto `writeResource` e transmitir os seguintes parâmetros:

   * O caminho onde a pasta deve ser criada.
   * O `ResourceCollection` objeto que representa a pasta.
   * Passar `null` para os outros dois parâmetros.

**Consulte também**

[Criação de pastas](aem-forms-repository.md#creating-folders)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Escrever recursos {#writing-resources}

Você pode criar recursos em um determinado local no repositório. O tamanho do arquivo natural está sujeito às limitações do banco de dados e ao tempo limite da sessão. Para a configuração padrão, os arquivos são limitados a 25 MB. Para aumentar ou diminuir o tamanho máximo do arquivo, é necessário alterar a configuração do banco de dados.

A gravação de recursos é equivalente ao armazenamento de dados no repositório. Depois de gravar um recurso no repositório, ele se torna acessível a todos os clientes no ecossistema do repositório. Ao gravar recursos, como esquemas XML, arquivos XDP e arquivos XSD, no repositório, o conteúdo é analisado com base no tipo MIME. Se o tipo MIME for suportado, o analisador determinará se há uma relação implícita com outro conteúdo. Por exemplo, se uma folha de estilos em cascata (CSS) tiver um URL relativo que faça referência a um CSS comum, é esperado que você também envie o CSS comum para o repositório. A relação entre os dois recursos é armazenada como uma relação pendente por um período não ajustável de 30 dias. Ao enviar o CSS comum para o repositório no período de 30 dias, o relacionamento é formado.

Quando você cria um recurso, a lista de controle de acesso (ACL) é herdada da pasta pai. A pasta raiz tem permissões no nível do sistema até que um recurso ou pasta inicial seja criado, e nesse momento o recurso ou pasta recebe permissões ACL padrão.

Você pode gravar recursos programaticamente usando a API Java do serviço de repositório ou a API do serviço da Web.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-1}

Para gravar um recurso, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique o URI do recurso a ser lido.
1. Leia o recurso .

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar o URI da pasta de destino do recurso**

Crie uma cadeia de caracteres contendo o URI do recurso a ser lido. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*pasta*&quot;.

**Criar o recurso**

Chame o método do serviço Repositório para criar o recurso e preencha o recurso com informações de identificação, incluindo UUID, nome do recurso e descrição.

**Especificar o conteúdo do recurso**

Chame o método do serviço Repositório para criar conteúdo de recurso e armazenar esse conteúdo no recurso.

**Escreva o recurso na pasta de destino**

Chame o método do serviço Repositório para gravar o recurso, especificando o URI da pasta de destino.

**Consulte também**

[Gravar recursos usando a API Java](aem-forms-repository.md#write-resources-using-the-java-api)

[Gravar recursos usando a API de serviço da Web](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Gravar recursos usando a API Java {#write-resources-using-the-java-api}

Escreva um recurso usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar o URI da pasta de destino do recurso

   Especifique o URI da pasta de destino para o recurso. Nesse caso, porque o recurso chamado `testResource` será armazenado na pasta nomeada `testFolder`, o URI da pasta é `"/testFolder"`. O URI é armazenado como um `java.lang.String` objeto.

1. Criar o recurso

   Para criar um recurso, primeiro crie um `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` objeto.

   Chame o `RepositoryInfomodelFactoryBean` do objeto `newResource` , que cria um `com.adobe.repository.infomodel.bean.Resource` objeto. Neste exemplo, os seguintes parâmetros são fornecidos:

   * A `com.adobe.repository.infomodel.Id` objeto , que é criado chamando o construtor padrão para o `Id` classe .
   * A `com.adobe.repository.infomodel.Lid` objeto , que é criado chamando o construtor padrão para o `Lid` classe .
   * A `java.lang.String` contendo o nome do arquivo do recurso.

   Para especificar a descrição do recurso, chame o `Resource` do objeto `setDescription` e passe uma string contendo a descrição. Neste exemplo, a descrição é `"test resource"`.

1. Especificar o conteúdo do recurso

   Para criar conteúdo para o recurso, chame o `RepositoryInfomodelFactoryBean` do objeto `newResourceContent` , que retorna um `com.adobe.repository.infomodel.bean.ResourceContent` objeto. Adicione conteúdo ao `ResourceContent` objeto. Neste exemplo, isso é feito realizando as seguintes tarefas:

   * Chamar o `ResourceContent` do objeto `setDataDocument` e a transmissão de um `com.adobe.idp.Document` objeto
   * Chamar o `ResourceContent` do objeto `setSize` e transmitindo o tamanho em bytes do `Document` objeto

   Adicione o conteúdo ao recurso chamando o `Resource` do objeto `setContent` e a transmissão do `ResourceContent` objeto. Para obter mais informações, consulte [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Escreva o recurso na pasta de destino

   Chame o `ResourceRepositoryClient` do objeto `writeResource` e transmita no URI da pasta, bem como o `Resource` objeto.

**Consulte também**

[Escrever recursos](aem-forms-repository.md#writing-resources)

[Início rápido (modo SOAP): Gravação de um recurso usando a API Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gravar recursos usando a API de serviço da Web {#write-resources-using-the-web-service-api}

Escreva um recurso usando a API do serviço de repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório usando base64.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar o URI da pasta de destino do recurso

   Especifique o URI da pasta de destino para o recurso. Nesse caso, porque o recurso chamado `testResource` será armazenado na pasta nomeada `testFolder`, o URI da pasta é `"/testFolder"`. Ao usar um idioma compatível com o Microsoft .NET Framework (por exemplo, C#), armazene o URI em um `System.String` objeto.

1. Criar o recurso

   Para criar um recurso, chame o construtor padrão para o `Resource` classe . Neste exemplo, as informações a seguir são armazenadas na variável `Resource` objeto:

   * A `com.adobe.repository.infomodel.Id` objeto , que é criado chamando o construtor padrão para o `Id` classe e atribuída à `Resource` do objeto `id` campo.
   * A `com.adobe.repository.infomodel.Lid` objeto , que é criado chamando o construtor padrão para o `Lid` classe e atribuída à `Resource` do objeto `lid` campo.
   * Uma string contendo o nome do arquivo do recurso, que é atribuído à variável `Resource` do objeto `name` campo. O nome usado neste exemplo é `"testResource"`.
   * Uma string contendo a descrição do recurso, que é atribuída à variável `Resource` do objeto `description` campo. A descrição usada neste exemplo é `"test resource"`.

1. Especificar o conteúdo do recurso

   Para criar conteúdo para o recurso, chame o construtor padrão para a `ResourceContent` classe . Em seguida, adicione conteúdo à `ResourceContent` objeto. Neste exemplo, isso é feito realizando as seguintes tarefas:

   * Atribuir um `BLOB` objeto que contém um documento para a `ResourceContent` do objeto `dataDocument` campo.
   * Atribuição do tamanho em bytes da variável `BLOB` para `ResourceContent` do objeto `size` campo.

   Adicione o conteúdo ao recurso atribuindo a variável `ResourceContent` para `Resource` do objeto `content` campo.

1. Escreva o recurso na pasta de destino

   Chame o `RepositoryServiceService` do objeto `writeResource` e transmita no URI da pasta, bem como o `Resource` objeto. Passar `null` para os outros dois parâmetros.

**Consulte também**

[Escrever recursos](aem-forms-repository.md#writing-resources)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Listando recursos {#listing-resources}

Você pode descobrir recursos listando recursos. Um query é executado no repositório para localizar todos os recursos relacionados a uma determinada coleção de recursos.

Depois de organizar seus recursos, você pode inspecionar a estrutura criada ao ver uma ramificação específica da estrutura, como faria em um sistema operacional.

Os recursos de listagem operam por relacionamento: os recursos são membros de pastas. A associação é representada por uma relação do tipo &quot;membro de&quot;. Ao listar recursos em uma determinada pasta, você está consultando os recursos relacionados a uma determinada pasta pelo &quot;membro de&quot; do relacionamento. As relações são direcionais: um membro de um relacionamento tem uma origem que é membro do destino. A fonte é o recurso; o target é a pasta pai.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-2}

Para listar recursos, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie o cliente de serviço.
1. Especifique o caminho da pasta.
1. Recupere a lista de recursos.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de criar uma coleção de recursos de forma programática, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar o caminho da pasta**

Crie uma string contendo o caminho da pasta contendo os recursos. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*pasta*&quot;.

**Recuperar a lista de recursos**

Chame o método Repository service para recuperar a lista de recursos, especificando o caminho da pasta de destino.

**Consulte também**

[Listar recursos usando a API Java](aem-forms-repository.md#list-resources-using-the-java-api)

[Listar recursos usando a API de serviço da Web](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Listar recursos usando a API Java {#list-resources-using-the-java-api}

Listar recursos usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar o caminho da pasta

   Especifique o URI da coleção de recursos a ser consultada. Nesse caso, seu URI é `"/testFolder"`. O URI é armazenado como um `java.lang.String` objeto.

1. Recuperar a lista de recursos

   Chame o `ResourceRepositoryClient` do objeto `listMembers` e transmita no URI da pasta.

   O método retorna um `java.util.List` de `com.adobe.repository.infomodel.bean.Resource` objetos que são a origem de um `com.adobe.repository.infomodel.bean.Relation` de tipo `Relation.TYPE_MEMBER_OF` e ter o URI de coleção de recursos como destino. Você pode iterar por meio disso `List` para recuperar cada um dos recursos. Neste exemplo, o nome e a descrição de cada recurso são exibidos.

**Consulte também**

[Listando recursos](aem-forms-repository.md#listing-resources).

[Início rápido (modo SOAP): Listar recursos usando a API Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Listar recursos usando a API de serviço da Web {#list-resources-using-the-web-service-api}

Listar recursos usando a API do serviço de repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar o caminho da pasta

   Especifique uma cadeia de caracteres contendo o URI da pasta a ser consultada. Nesse caso, seu URI é `"/testFolder"`. Ao usar um idioma compatível com o Microsoft .NET Framework (por exemplo, C#), armazene o URI em um `System.String` objeto.

1. Recuperar a lista de recursos

   Chame o `RepositoryServiceService` do objeto `listMembers` e transmitir o URI da pasta como o primeiro parâmetro. Passar `null` para os outros dois parâmetros.

   O método retorna uma matriz de objetos que podem ser convertidos em `Resource` objetos. Você pode iterar pela matriz de objetos para recuperar cada um dos recursos relacionados. Neste exemplo, o nome e a descrição de cada recurso são exibidos.

**Consulte também**

[Listando recursos](aem-forms-repository.md#listing-resources).

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Lendo recursos {#reading-resources}

Você pode recuperar recursos de um determinado local no repositório para ler o conteúdo e os metadados. O fluxo de trabalho é front-end por um formulário de inicialização. O processo tem todas as permissões necessárias para ler o formulário. O sistema recupera o formulário de dados e lê o conteúdo do repositório. O repositório concede acesso ao conteúdo e aos metadados (a capacidade de até saber se o recurso existe).

O repositório tem os quatro tipos de permissão a seguir:

* **traverse**: permite listar recursos; ou seja, para ler metadados de recursos, mas não conteúdo de recursos
* **read**: permite ler o conteúdo do recurso
* **gravação**: permite gravar conteúdo de recurso
* **gerenciamento de listas de controle de acesso (ACLs)**: permite manipular ACLs em recursos

Os usuários só podem executar processos quando tiverem permissão para executar o processo. Os usuários do IDE precisam de permissões de leitura e percursos para sincronizar com o repositório. As ACLs se aplicam somente no momento do design porque o tempo de execução ocorre no contexto do sistema.

Você pode ler recursos programaticamente usando a API Java do serviço de repositório ou a API do serviço da Web.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-3}

Para ler um recurso, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique o URI do recurso a ser lido.
1. Leia o recurso .

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar o URI do recurso a ser lido**

Crie uma cadeia de caracteres contendo o URI do recurso a ser lido. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*recurso*&quot;.

**Ler o recurso**

Chame o método do serviço Repositório para ler o recurso, especificando o URI.

**Consulte também**

[Leia recursos usando a API do Java](aem-forms-repository.md#read-resources-using-the-java-api)

[Leitura de recursos usando a API de serviço da Web](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Leia recursos usando a API do Java {#read-resources-using-the-java-api}

Leia um recurso usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar o URI do recurso a ser lido

   Especifique um valor de string que represente o URI do recurso a ser recuperado. Por exemplo, supondo que o recurso seja nomeado *testResource* que está localizado em uma pasta nomeada *testFolder*, especifique `/testFolder/testResource`.

1. Ler o recurso

   Chame o `ResourceRepositoryClient` do objeto `readResource` e transmita o URI do recurso como um parâmetro. Esse método retorna um `Resource` que representa o recurso.

**Consulte também**

[Lendo recursos](aem-forms-repository.md#reading-resources)

[Início rápido (modo SOAP): Leitura de um recurso usando a API Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Leitura de recursos usando a API de serviço da Web {#reading-resources-using-the-web-service-api}

Leia um recurso usando a API do serviço de repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório. (Consulte [Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)
   * Faça referência ao assembly do cliente Microsoft .NET. (Consulte [Criando um assembly de cliente .NET que usa codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar o URI do recurso a ser lido

   Especifique uma cadeia de caracteres contendo o URI do recurso a ser recuperado. Nesse caso, porque o recurso chamado `testResource` está na pasta com o nome `testFolder`, seu URI é `"/testFolder/testResource"`. Ao usar um idioma compatível com o Microsoft .NET Framework (por exemplo, C#), armazene o URI em um `System.String` objeto.

1. Ler o recurso

   Chame o `RepositoryServiceService` do objeto `readResource` e transmita o URI do recurso como o primeiro parâmetro. Passar `null` para os outros dois parâmetros.

**Consulte também**

[Lendo recursos](aem-forms-repository.md#reading-resources)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Atualização de recursos {#updating-resources}

Você pode recuperar e atualizar o conteúdo dos recursos no repositório. Ao atualizar recursos, o controle de acesso a esses recursos permanece inalterado entre as versões. Ao executar uma atualização, você tem a opção de incrementar a versão principal. Se você não optar por incrementar a versão principal, a versão secundária será atualizada automaticamente.

Quando você atualiza um recurso, a nova versão é criada com base nos atributos de recurso especificados. Ao atualizar um recurso, você especifica dois parâmetros importantes: o URI de destino e uma instância de recurso contendo todos os metadados atualizados. É importante observar que se você não estiver alterando um determinado atributo (por exemplo, o nome), o atributo ainda será necessário na instância em que você passou. As relações criadas ao analisar o conteúdo são adicionadas à versão específica e não são antecipadas, a menos que especificado.

Por exemplo, se você atualizar um arquivo XDP e ele contiver referências a outros recursos, essas referências adicionais também serão registradas. Suponha que form.xdp versão 1.0 tenha duas referências externas: um logotipo e uma folha de estilos e, em seguida, atualize form.xdp para que ele agora tenha três referências: um logotipo, uma folha de estilos e um arquivo de esquema. Durante a atualização, o repositório adicionará o terceiro relacionamento (ao arquivo de esquema) à tabela de relação pendente. Quando o arquivo de esquema estiver presente no repositório, a relação será formada automaticamente. No entanto, se a versão 2.0 do form.xdp não usar mais o logotipo, a versão 2.0 do form.xdp não terá uma relação com o logotipo.

Todas as operações de atualização são atômicas e transacionais. Por exemplo, se dois usuários lerem o mesmo recurso e decidirem atualizar a versão 1.0 para a versão 2.0, um deles terá êxito e um deles falhará, a integridade do repositório será mantida e ambos receberão uma mensagem confirmando o sucesso ou a falha. Se a transação não for confirmada, ela será revertida em caso de falha no banco de dados e expirará ou será revertida dependendo do servidor de aplicativos.

Você pode atualizar recursos programaticamente usando a API Java do serviço de repositório ou a API do serviço da Web.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-4}

Para atualizar um recurso, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Recupere o recurso a ser atualizado.
1. Atualize o recurso.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Recuperar o recurso a ser atualizado**

Leia o recurso . Para obter mais informações, consulte [Lendo recursos](aem-forms-repository.md#reading-resources).

**Atualizar o recurso**

Defina as novas informações no recurso e chame o método do serviço Repositório para atualizar o recurso, especificando o URI, o recurso atualizado e como as informações da versão devem ser atualizadas.

**Consulte também**

[Atualizar recursos usando a API Java](aem-forms-repository.md#update-resources-using-the-java-api)

[Atualizar recursos usando a API de serviço da Web](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Atualizar recursos usando a API Java {#update-resources-using-the-java-api}

Atualize um recurso usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Recuperar o recurso a ser atualizado

   Especifique o URI do recurso para recuperar e ler o recurso. Neste exemplo, o URI do recurso é `"/testFolder/testResource"`.

1. Atualizar o recurso

   Atualize o `Resource` informações do objeto. Neste exemplo, para atualizar a descrição, chame a função `Resource` do objeto `setDescription` e passe a nova string de descrição como um parâmetro.

   Em seguida, chame o `ServiceClientFactory` do objeto `updateResource` e transmitir os seguintes parâmetros:

   * A `java.lang.String` objeto que contém o URI do recurso.
   * O `Resource` objeto que contém as informações atualizadas do recurso.
   * A `boolean` valor indicando se deseja atualizar a versão principal ou secundária. Neste exemplo, um valor de `true` é transmitido para indicar que a versão principal deve ser incrementada.

**Consulte também**

[Atualização de recursos](aem-forms-repository.md#updating-resources)

[Início rápido (modo SOAP): Atualização de um recurso usando a API do Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Atualizar recursos usando a API de serviço da Web {#update-resources-using-the-web-service-api}

Atualize um recurso usando a API do Repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Recuperar o recurso a ser atualizado

   Especifique o URI do recurso a ser recuperado e leia o recurso. Neste exemplo, o URI do recurso é `"/testFolder/testResource"`. Para obter mais informações, consulte [Lendo recursos](aem-forms-repository.md#reading-resources).

1. Atualizar o recurso

   Atualize o `Resource` informações do objeto. Neste exemplo, para atualizar a descrição, atribua um novo valor à variável `Resource` do objeto `description` campo.

1. Chame o `RepositoryServiceService` do objeto `updateResource` e transmitir os seguintes parâmetros:

   * A `System.String` objeto que contém o URI do recurso.
   * O `Resource` objeto que contém as informações atualizadas do recurso.
   * A `boolean` valor indicando se deseja atualizar a versão principal ou secundária. Neste exemplo, um valor de `true` é transmitido para indicar que a versão principal deve ser incrementada.
   * Passar `null` para os dois parâmetros restantes.

**Consulte também**

[Atualização de recursos](aem-forms-repository.md#updating-resources)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Pesquisar recursos {#searching-for-resources}

Você pode criar consultas usadas para pesquisar recursos no repositório, incluindo histórico, recursos relacionados e propriedades.

Você pode recuperar recursos relacionados para determinar dependências entre um formulário e seus fragmentos. Por exemplo, se você tiver um formulário, poderá determinar quais fragmentos ou recursos externos ele usa. Se você tiver uma imagem, também poderá descobrir quais formulários usam a imagem. Também é possível pesquisar recursos relacionados usando a filtragem com base nas propriedades. Por exemplo, você pode procurar todos os formulários que usam uma imagem com um nome especificado ou localizar qualquer imagem usada por um formulário com um nome especificado. Também é possível pesquisar usando as propriedades do recurso. Por exemplo, você pode realizar um query para localizar todos os formulários ou recursos cujo nome começa com uma determinada string que pode incluir curingas &quot;%&quot; e &quot;_&quot;. Lembre-se de que as pesquisas baseadas em propriedades não se baseiam em relacionamentos; essas pesquisas se baseiam na suposição de que você tem conhecimento específico sobre um determinado recurso.

**Declarações de consulta**

A *query* contém uma ou mais instruções que são logicamente unidas com condições. A *declaração* consiste em um operando à esquerda, um operador e um operando à direita. Além disso, você pode especificar a ordem de classificação a ser usada para os resultados da pesquisa. O *ordenar ordem* contém informações equivalentes a um SQL `ORDER BY` e é composto de elementos que contêm os atributos nos quais a pesquisa foi baseada, bem como um valor que indica se a ordem crescente ou decrescente deve ser usada.

Você pode pesquisar recursos programaticamente usando a API Java do serviço de repositório. No momento, não é possível usar a API do serviço da Web para pesquisar recursos.

**Ordenar comportamento**

A ordem de classificação não é respeitada ao invocar o `ResourceRepositoryClient` do objeto `searchProperties` e especificando uma ordem de classificação. Por exemplo, suponha que você crie um recurso com três propriedades personalizadas, onde os nomes dos atributos sejam `name`, `secondName`e `asecondName`. Em seguida, você cria um elemento de ordem de classificação no nome do atributo e define o `ascending` para `true`.

Em seguida, chame o `ResourceRepositoryClient` do objeto `searchProperties` e transmita na ordem de classificação. A pesquisa retorna o recurso correto, com as três propriedades. No entanto, as propriedades não são classificadas por nome de atributo. Eles são retornados na ordem em que foram adicionados: `name`, `secondName`e `asecondName`.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-5}

Para pesquisar recursos, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique a pasta de destino para a pesquisa.
1. Especifique os atributos usados na pesquisa.
1. Crie a consulta usada na pesquisa.
1. Crie a ordem de classificação para os resultados da pesquisa.
1. Procure os recursos.
1. Recupere os recursos do resultado da pesquisa.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar a pasta de destino da pesquisa**

Crie uma string contendo o caminho base do qual a pesquisa será realizada. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*pasta*&quot;.

**Especificar os atributos usados na pesquisa**

Você pode basear sua pesquisa nos atributos contidos nos recursos. Especifique os valores dos atributos nos quais realizar a pesquisa.

**Criar a consulta usada na pesquisa**

Construa uma consulta usando declarações e condições. Cada instrução especificará o atributo no qual basear a pesquisa, a condição a ser usada e o valor do atributo a ser usado na pesquisa.

**Criar a ordem de classificação para os resultados da pesquisa**

A ordem de classificação é composta de elementos, cada um dos quais contém um dos atributos usados na pesquisa e um valor que indica se a ordem crescente ou decrescente deve ser usada.

**Pesquise os recursos**

Procure os recursos usando a pasta, a consulta e a ordem de classificação. Além disso, indique a profundidade da pesquisa e um limite máximo no número de resultados a serem retornados.

**Recuperar os recursos do resultado da pesquisa**

Iterar pela lista de recursos retornada e extrair as informações para processamento adicional.

**Consulte também**

[Pesquise recursos usando a API do Java](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Pesquise recursos usando a API do Java {#search-for-resources-using-the-java-api}

Procure um recurso usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar a pasta de destino da pesquisa

   Especifique o URI do caminho base a partir do qual a pesquisa será executada. Neste exemplo, o URI do recurso é `/testFolder`.

1. Especificar os atributos usados na pesquisa

   Especifique os valores dos atributos nos quais a pesquisa deve ser realizada. Os atributos existem em um `com.adobe.repository.infomodel.bean.Resource` objeto. Neste exemplo, a pesquisa será realizada no atributo name; por conseguinte, `java.lang.String` contendo o `Resource` o nome do objeto é usado, que é `testResource` neste caso.

1. Criar a consulta usada na pesquisa

   Para criar um query, crie um `com.adobe.repository.query.Query` chamando o construtor padrão para o `Query` e adicionar instruções à query.

   Para criar uma instrução, chame o construtor para a `com.adobe.repository.query.Query.Statement` classe e transmita nos seguintes parâmetros:

   * Um operando esquerdo contendo a constante do atributo de recurso. Neste exemplo, como o nome do recurso é usado como a base para a pesquisa, o valor estático `Resource.ATTRIBUTE_NAME` é usada.
   * Um operador contendo a condição usada na pesquisa pelo atributo. O operador deve ser uma das constantes estáticas no `Query.Statement` classe . Neste exemplo, o valor estático `Query.Statement.OPERATOR_BEGINS_WITH` é usada.
   * Um operando direito contendo o valor do atributo no qual realizar a pesquisa. Neste exemplo, o atributo name , uma `String` contendo o valor `"testResource"`, é usado.

   Especifique o namespace do operando esquerdo, chamando o `Query.Statement` do objeto `setNamespace` e transmitindo um dos valores estáticos contidos no `com.adobe.repository.infomodel.bean.ResourceProperty` classe . Neste exemplo, `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` é usada.

   Adicione cada instrução ao query chamando o `Query` do objeto `addStatement` e a transmissão do `Query.Statement` objeto.

1. Criar a ordem de classificação para os resultados da pesquisa

   Para especificar a ordem de classificação usada nos resultados da pesquisa, crie uma `com.adobe.repository.query.sort.SortOrder` chamando o construtor padrão para o `SortOrder` e adicionar elementos à ordem de classificação.

   Para criar um elemento para a ordem de classificação, chame um dos construtores para a `com.adobe.repository.query.sort.SortOrder.Element` classe . Neste exemplo, como o nome do recurso é usado como a base para a pesquisa, o valor estático `Resource.ATTRIBUTE_NAME` é usado como o primeiro parâmetro e em ordem crescente (a `boolean` valor de `true`) é especificado como o segundo parâmetro.

   Adicione cada elemento à ordem de classificação chamando o `SortOrder` do objeto `addSortElement` e a transmissão do `SortOrder.Element` objeto.

1. Pesquise os recursos

   Para pesquisar por `resources` com base nas propriedades do atributo, chame a função `ResourceRepositoryClient` do objeto `searchProperties` e transmitir os seguintes parâmetros:

   * A `String` contendo o caminho base do qual a pesquisa será executada. Nesse caso, `"/testFolder"` é usada.
   * A consulta usada na pesquisa.
   * A profundidade da pesquisa. Nesse caso, `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` é usado para indicar que o caminho base e todas as suas pastas devem ser usadas.
   * Um `int` valor que indica a primeira linha a partir da qual selecionar o conjunto de resultados não paginados. Neste exemplo, `0` é especificado.
   * Um `int` valor que indica o número máximo de resultados a serem retornados. Neste exemplo, `10` é especificado.
   * A ordem de classificação usada na pesquisa.

   O método retorna um `java.util.List` de `Resource` objetos na ordem de classificação especificada.

1. Recuperar os recursos do resultado da pesquisa

   Para recuperar os recursos contidos no resultado da pesquisa, faça uma iteração por meio do `List` e converter cada objeto em um `Resource` para extrair as informações. Neste exemplo, o nome de cada recurso é exibido.

**Consulte também**

[Pesquisar recursos](aem-forms-repository.md#searching-for-resources)

[Início rápido (modo SOAP): Pesquisar recursos usando a API do Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Criando Relacionamentos de Recursos {#creating-resource-relationships}

Você pode especificar relacionamentos entre recursos no repositório. Existem três tipos de relacionamentos:

* **Dependência**: um relacionamento no qual um recurso depende de outros recursos, o que significa que todos os recursos relacionados são necessários no repositório.
* **Associação (sistema de arquivos)**: um relacionamento no qual um recurso está localizado em uma determinada pasta.
* **Personalizado**: uma relação especificada entre recursos. Por exemplo, se um recurso tiver sido substituído e outro recurso tiver sido introduzido no repositório, você poderá especificar seu próprio relacionamento de substituição.

Você pode criar seus próprios relacionamentos personalizados. Por exemplo, se você armazenar um arquivo HTML no repositório e ele usar uma imagem, você poderá especificar um relacionamento personalizado para relacionar o arquivo HTML com a imagem (já que normalmente apenas os arquivos XML são associados a imagens usando um relacionamento de dependência definido pelo repositório). Outro exemplo de relacionamento personalizado seria se você quisesse criar uma exibição diferente do repositório com uma estrutura de gráfico cíclico em vez de uma estrutura de árvore. Você poderia definir um gráfico circular junto com um visualizador para atravessar esses relacionamentos. Por fim, você pode indicar que um recurso substitui outro recurso, mesmo que os dois recursos sejam completamente diferentes. Nesse caso, você pode definir um tipo de relacionamento fora do intervalo reservado e criar uma relação entre esses dois recursos. Seu aplicativo seria o único cliente que poderia detectar e processar o relacionamento e poderia ser usado para realizar pesquisas nesse relacionamento.

Você pode especificar relações entre recursos de forma programática usando a API Java do serviço de repositório ou a API do serviço da Web.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-6}

Para especificar uma relação entre dois recursos, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique os URIs dos recursos a serem relacionados.
1. Crie a relação.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar os URIs dos recursos a serem relacionados**

Crie cadeias de caracteres contendo os URIs do recurso a ser relacionado. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*recurso*&quot;.

**Criar a relação**

Chame o método Repository service para criar e especificar o tipo de relacionamento.

**Consulte também**

[Criar recursos de relacionamento usando a API do Java](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Criar recursos de relacionamento usando a API do serviço da Web](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Criar recursos de relacionamento usando a API do Java {#create-relationship-resources-using-the-java-api}

Crie recursos de relacionamento usando a API Java do serviço de Repositório e execute as seguintes tarefas:

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar os URIs dos recursos a serem relacionados

   Especifique os URIs dos recursos a serem relacionados. Nesse caso, porque os recursos são nomeados `testResource1` e `testResource2` e estão localizados na pasta nomeada `testFolder`, seus URIs são `"/testFolder/testResource1"` e `"/testFolder/testResource2"`. Os URIs são armazenados como um `java.lang.String` objetos. Neste exemplo, os recursos são gravados primeiro no repositório e seus URIs são recuperados. Para obter mais informações sobre como gravar um recurso, consulte [Escrever recursos](aem-forms-repository.md#writing-resources).

1. Criar a relação

   Chame o `ResourceRepositoryClient` do objeto `createRelationship` e transmitir os seguintes parâmetros:

   * O URI do recurso de origem.
   * O URI do recurso de destino.
   * O tipo de relação, que é uma das constantes estáticas na variável `com.adobe.repository.infomodel.bean.Relation` classe . Neste exemplo, uma relação de dependência é estabelecida especificando o valor `Relation.TYPE_DEPENDANT_OF`.
   * A `boolean` valor indicando se o recurso de destino é atualizado automaticamente para a `com.adobe.repository.infomodel.Id`Identificador baseado no novo recurso de cabeçalho. Neste exemplo, devido à relação de dependência, o valor `true` é especificado.

   Você também pode recuperar uma lista de recursos relacionados para um determinado recurso, chamando a variável `ResourceRepositoryClient` do objeto `getRelated` e transmitindo os seguintes parâmetros:

   * O URI do recurso para o qual recuperar recursos relacionados. Neste exemplo, o recurso de origem ( `"/testFolder/testResource1"`) é especificada.
   * A `boolean` valor que indica se o recurso especificado é o recurso de origem na relação. Neste exemplo, o valor `true` é especificado porque é o caso.
   * O tipo de relacionamento, que é uma das constantes estáticas no `Relation` classe . Neste exemplo, uma relação de dependência é especificada usando o mesmo valor usado anteriormente: `Relation.TYPE_DEPENDANT_OF`.

   O `getRelated` método retorna um `java.util.List` de `Resource` objetos pelos quais você pode iterar para recuperar cada um dos recursos relacionados, designando os objetos contidos na variável `List` para `Resource` como o faz. Neste exemplo, `testResource2` deve estar na lista de recursos retornados.

**Consulte também**

[Criando Relacionamentos de Recursos](aem-forms-repository.md#creating-resource-relationships)

[Início rápido (modo SOAP): Criação de relações entre recursos usando a API do Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Criar recursos de relacionamento usando a API do serviço da Web {#create-relationship-resources-using-the-web-service-api}

Crie recursos de relacionamento usando a API do Repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar os URIs dos recursos a serem relacionados

   Especifique os URIs dos recursos a serem relacionados. Nesse caso, porque os recursos são nomeados `testResource1` e `testResource2` e estão localizados na pasta nomeada `testFolder`, seus URIs são `"/testFolder/testResource1"` e `"/testFolder/testResource2"`. Ao usar um idioma compatível com o Microsoft .NET Framework (por exemplo, C#), os URIs são armazenados como um `System.String` objetos. Neste exemplo, os recursos são gravados primeiro no repositório e seus URIs são recuperados. Para obter mais informações sobre como gravar um recurso, consulte [Escrever recursos](aem-forms-repository.md#writing-resources).

1. Criar a relação

   Chame o `RepositoryServiceService` do objeto `createRelationship` e transmitir os seguintes parâmetros:

   * O URI do recurso de origem.
   * O URI do recurso de destino.
   * O tipo de relacionamento. Neste exemplo, uma relação de dependência é estabelecida especificando o valor `3`.
   * A `boolean` valor indicando se o tipo de relacionamento foi especificado. Neste exemplo, o valor `true` é especificado.
   * A `boolean` valor indicando se o recurso de destino é atualizado automaticamente para a `Id`Identificador baseado no novo recurso de cabeçalho. Neste exemplo, devido à relação de dependência, o valor `true` é especificado.
   * A `boolean` valor indicando se o cabeçalho de destino foi especificado. Neste exemplo, o valor `true` é especificado.
   * Passar `null` para o último parâmetro.

   Você também pode recuperar uma lista de recursos relacionados para um determinado recurso, chamando a variável `RepositoryServiceService` do objeto `getRelated` e transmitindo os seguintes parâmetros:

   * O URI do recurso para o qual recuperar recursos relacionados. Neste exemplo, o recurso de origem ( `"/testFolder/testResource1"`) é especificada.
   * A `boolean` valor que indica se o recurso especificado é o recurso de origem na relação. Neste exemplo, o valor `true` é especificado porque é o caso.
   * A `boolean` valor indicando se o recurso de origem foi especificado. Neste exemplo, o valor `true` é fornecida.
   * Uma matriz de números inteiros contendo os tipos de relacionamento. Neste exemplo, uma relação de dependência é especificada usando o mesmo valor na matriz como foi usado anteriormente: `3`.
   * Passar `null` para os dois parâmetros restantes.

   O `getRelated` retorna uma matriz de objetos que podem ser convertidos em `Resource` objetos pelos quais você pode iterar para recuperar cada um dos recursos relacionados. Neste exemplo, `testResource2` deve estar na lista de recursos retornados.

**Consulte também**

[Criando Relacionamentos de Recursos](aem-forms-repository.md#creating-resource-relationships)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bloquear recursos {#locking-resources}

Você pode bloquear um recurso ou conjunto de recursos para uso exclusivo por um usuário específico ou uso compartilhado entre mais de um usuário. Um bloqueio compartilhado é uma indicação de que algo acontecerá com o recurso, mas não impede que mais ninguém tome ações com esse recurso. Um bloqueio compartilhado deve ser considerado um mecanismo de sinalização. Um bloqueio exclusivo significa que o usuário que bloqueou o recurso vai alterar o recurso e o bloqueio garante que ninguém mais possa fazer isso até que o usuário não precise mais acessar o recurso e tenha liberado o bloqueio. Se um administrador de repositório desbloquear um recurso, todos os bloqueios exclusivos e compartilhados nesse recurso serão automaticamente removidos. Esse tipo de ação destina-se a situações em que um usuário não está mais disponível e não desbloqueou o recurso.

Quando um recurso é bloqueado, um ícone de cadeado é exibido ao exibir a guia Recursos localizada no Workbench, como mostrado na ilustração a seguir.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

Você pode controlar programaticamente o acesso aos recursos usando a API Java do serviço de repositório ou a API do serviço da Web.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-7}

Para bloquear e desbloquear recursos, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique o URI do recurso a ser bloqueado.
1. Bloqueie o recurso.
1. Recupere os bloqueios do recurso.
1. Desbloquear o recurso

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar o URI do recurso a ser bloqueado**

Crie uma cadeia de caracteres contendo o URI do recurso a ser bloqueado. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*recurso*&quot;.

**Bloquear o recurso**

Chame o método do serviço Repositório para bloquear o recurso, especificando o URI, o tipo de bloqueio e a profundidade de bloqueio.

**Recuperar os bloqueios do recurso**

Chame o método do serviço Repositório para recuperar os bloqueios do recurso, especificando o URI.

**Desbloquear o recurso**

Chame o método do serviço Repositório para desbloquear o recurso, especificando o URI.

**Consulte também**

[Bloquear recursos usando a API do Java](aem-forms-repository.md#lock-resources-using-the-java-api)

[Bloquear recursos usando a API de serviço da Web](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bloquear recursos usando a API do Java {#lock-resources-using-the-java-api}

Bloquear recursos usando a API do serviço de repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar o URI do recurso a ser bloqueado

   Especifique o URI do recurso a ser bloqueado. Nesse caso, porque o recurso chamado `testResource` está na pasta com o nome `testFolder`, seu URI é `"/testFolder/testResource"`. O URI é armazenado como um `java.lang.String` objeto.

1. Bloquear o recurso

   Chame o `ResourceRepositoryClient` do objeto `lockResource` e transmitir os seguintes parâmetros:

   * O URI do recurso.
   * O escopo de bloqueio. Neste exemplo, como o recurso será bloqueado para uso exclusivo, o escopo de bloqueio é especificado como `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE`.
   * A profundidade da fechadura. Neste exemplo, como o bloqueio será aplicado somente ao recurso específico e nenhum de seus membros ou filhos, a profundidade do bloqueio será especificada como `Lock.DEPTH_ZERO`.

   >[!NOTE]
   >
   >A versão sobrecarregada do `lockResource` que requer quatro parâmetros aciona uma exceção. Certifique-se de usar o `lockResource` que requer três parâmetros, como mostrado nesta apresentação.

1. Recuperar os bloqueios do recurso

   Chame o `ResourceRepositoryClient` do objeto `getLocks` e transmita o URI do recurso como um parâmetro. O método retorna uma Lista de objetos de bloqueio pela qual você pode iterar. Neste exemplo, o proprietário do bloqueio, a profundidade e o escopo são impressos para cada objeto chamando cada objeto Bloquear `getOwnerUserId`, `getDepth`e `getType` métodos, respectivamente.

1. Desbloquear o recurso

   Chame o `ResourceRepositoryClient` do objeto `unlockResource` e transmita o URI do recurso como um parâmetro. Para obter mais informações, consulte o [Referência da API do AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Consulte também**

[Bloquear recursos](aem-forms-repository.md#locking-resources)

[Início rápido (modo SOAP): Bloquear um recurso usando a API Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bloquear recursos usando a API de serviço da Web {#lock-resources-using-the-web-service-api}

Bloquear recursos usando a API do serviço de repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório usando Base64.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar o URI do recurso a ser bloqueado

   Especifique uma string contendo o URI do recurso a ser bloqueado. Nesse caso, porque o recurso chamado `testResource` está na pasta `testFolder`, seu URI é `"/testFolder/testResource"`. Ao usar um idioma compatível com o Microsoft .NET Framework (por exemplo, C#), armazene o URI em um `System.String` objeto.

1. Bloquear o recurso

   Chame o `RepositoryServiceService` do objeto `lockResource` e transmitir os seguintes parâmetros:

   * O URI do recurso.
   * O escopo de bloqueio. Neste exemplo, como o recurso será bloqueado para uso exclusivo, o escopo de bloqueio é especificado como `11`.
   * A profundidade da fechadura. Neste exemplo, como o bloqueio será aplicado somente ao recurso específico e nenhum de seus membros ou filhos, a profundidade do bloqueio será especificada como `2`.
   * Um `int` valor que indica o número de segundos até o bloqueio expirar. Neste exemplo, o valor de `1000` é usada.
   * Passar `null` para o último parâmetro.

1. Recuperar os bloqueios do recurso

   Chame o `RepositoryServiceService` do objeto `getLocks` e transmita o URI do recurso como o primeiro parâmetro e `null` para o segundo parâmetro. O método retorna um `object` matriz contendo `Lock` objetos pelos quais você pode iterar. Neste exemplo, o proprietário do bloqueio, a profundidade e o escopo são impressos para cada objeto acessando cada um `Lock` do objeto `ownerUserId`, `depth`e `type` , respectivamente.

1. Desbloquear o recurso

   Chame o `RepositoryServiceService` do objeto `unlockResource` e transmita o URI do recurso como o primeiro parâmetro e `null` para o segundo parâmetro.

**Consulte também**

[Bloquear recursos](aem-forms-repository.md#locking-resources)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Exclusão de recursos {#deleting-resources}

Você pode excluir programaticamente recursos de um determinado local no repositório usando a API Java (SOAP) do serviço de repositório.

Quando você exclui um recurso, a exclusão normalmente é permanente, embora em alguns casos os repositórios ECM possam armazenar as versões do recurso de acordo com seus mecanismos de histórico. Portanto, ao excluir um recurso, é importante ter certeza de que você nunca precisará dele novamente. Os motivos comuns para excluir um recurso incluem a necessidade de aumentar o espaço disponível no banco de dados. É possível excluir uma versão de um recurso, mas se isso for feito, é necessário especificar o identificador de recurso, e não seu identificador lógico (LID) ou caminho. Se você excluir uma pasta, tudo nessa pasta, incluindo subpastas e recursos, será automaticamente excluído.

Os recursos relacionados não são excluídos. Por exemplo, se você tiver um formulário que usa o arquivo logo.gif e excluir logo.gif, um relacionamento será armazenado na tabela de relacionamento pendente. Como alternativa, para a desativação da versão, defina o status do objeto da versão mais recente como obsoleto.

Uma operação de exclusão não é segura para transações em sistemas ECM. Por exemplo, se você tentar excluir 100 recursos e a operação falhar no 50º recurso, as primeiras 49 instâncias serão excluídas, mas o restante não será. Caso contrário, o comportamento padrão será revertido (não comprometido).

>[!NOTE]
>
>Ao usar a variável `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` com o repositório ECM (EMC Documentum Content Server e IBM FileNet P8 Content Manager), a transação não será revertida se a exclusão falhar para um dos recursos especificados, o que significa que esses arquivos que foram excluídos não podem ser excluídos.

>[!NOTE]
>
>Para obter mais informações sobre o serviço Repositório, consulte [Referência de serviços para o AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Resumo das etapas {#summary_of_steps-8}

Para excluir um recurso, siga estas etapas:

1. Inclua arquivos de projeto.
1. Crie um cliente do Serviço de Repositório.
1. Especifique o URI do recurso a ser excluído.
1. Exclua o recurso.

**Incluir arquivos de projeto**

Inclua os arquivos necessários no projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, inclua os arquivos proxy.

**Criar o cliente de serviço**

Antes de ler programaticamente um recurso, você deve estabelecer uma conexão e fornecer credenciais. Isso é feito criando um cliente de serviço.

**Especificar o URI do recurso a ser excluído**

Crie uma cadeia de caracteres contendo o URI do recurso a ser excluído. A sintaxe inclui barras, como neste exemplo: &quot;/*caminho*/*recurso*&quot;. Se o recurso a ser excluído for uma pasta, a exclusão será recursiva.

**Excluir o recurso**

Chame o método do serviço Repositório para excluir o recurso, especificando o URI.

**Consulte também**

[Excluir recursos usando a API do Java](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Excluir recursos usando a API de serviço da Web](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Início rápido da API do Serviço de Repositório](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Excluir recursos usando a API do Java (SOAP) {#delete-resources-using-the-java-api-soap}

Exclua um recurso usando a API do repositório (Java):

1. Incluir arquivos de projeto

   Inclua arquivos JAR do cliente no caminho da classe do seu projeto Java.

1. Criar o cliente de serviço

   Crie um `ResourceRepositoryClient` usando seu construtor e transmitindo um `ServiceClientFactory` objeto que contém propriedades de conexão.

1. Especificar o URI do recurso a ser excluído

   Especifique o URI do recurso a ser recuperado. Nesse caso, como o recurso chamado testResourceToDelete está na pasta chamada testFolder, seu URI é `/testFolder/testResourceToBeDeleted`. O URI é armazenado como um `java.lang.String` objeto. Neste exemplo, o recurso é gravado primeiro no repositório e seu URI é recuperado. Para obter mais informações sobre como gravar um recurso, consulte [Escrever recursos](aem-forms-repository.md#writing-resources).

1. Excluir o recurso

   Chame o `ResourceRepositoryClient` do objeto `deleteResource` e transmita o URI do recurso como um parâmetro.

**Consulte também**

[Exclusão de recursos](aem-forms-repository.md#deleting-resources)

[Início rápido (modo SOAP): Pesquisar recursos usando a API do Java](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusão de arquivos da biblioteca Java do AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Configuração das propriedades de conexão](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Excluir recursos usando a API de serviço da Web {#delete-resources-using-the-web-service-api}

Exclua um recurso usando a API do Repositório (serviço da Web):

1. Incluir arquivos de projeto

   * Crie um assembly de cliente Microsoft .NET que consuma o WSDL do Repositório usando Base64.
   * Faça referência ao assembly do cliente Microsoft .NET.

1. Criar o cliente de serviço

   Usando o assembly do cliente Microsoft .NET, crie um `RepositoryServiceService` chamando seu construtor padrão. Defina suas `Credentials` propriedade usando um `System.Net.NetworkCredential` objeto contendo o nome de usuário e a senha.

1. Especificar o URI do recurso a ser excluído

   Especifique o URI do recurso a ser recuperado. Nesse caso, porque o recurso chamado `testResourceToBeDeleted` está na pasta com o nome `testFolder`, seu URI é `"/testFolder/testResourceToBeDeleted"`. Neste exemplo, o recurso é gravado primeiro no repositório e seu URI é recuperado. Para obter mais informações sobre como gravar um recurso, consulte [Escrever recursos](aem-forms-repository.md#writing-resources).

1. Excluir o recurso

   Chame o `RepositoryServiceService` do objeto `deleteResources` e passe um `System.String` matriz contendo o URI do recurso como o primeiro parâmetro. Passar `null` para o segundo parâmetro.

**Consulte também**

[Exclusão de recursos](aem-forms-repository.md#deleting-resources)

[Chamada de AEM Forms usando codificação Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
