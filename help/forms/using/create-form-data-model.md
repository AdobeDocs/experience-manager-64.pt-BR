---
title: '"Tutorial: Criar modelo de dados de formulário "'
seo-title: Tutorial de criação de modelo de dados de formulário
description: O módulo de integração de dados do AEM Forms permite criar um modelo de dados de formulário a partir de diferentes fontes de dados de backend, como AEM perfil de usuário, serviços Web RESTful, serviços Web baseados em SOAP, serviços OData e bancos de dados relacionais. Saiba como configurar o banco de dados do MySQL como fonte de dados, criar, configurar e testar um modelo de dados de formulário.
seo-description: O módulo de integração de dados do AEM Forms permite criar um modelo de dados de formulário a partir de diferentes fontes de dados de backend, como AEM perfil de usuário, serviços Web RESTful, serviços Web baseados em SOAP, serviços OData e bancos de dados relacionais. Saiba como configurar o banco de dados do MySQL como fonte de dados, criar, configurar e testar um modelo de dados de formulário.
page-status-flag: de-activated
uuid: 81d40278-4df9-4b61-93ad-eae2fce0a35c
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 31e97723-d637-4a18-999d-36e00fbd031a
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 1%

---


# Tutorial: Criar modelo de dados de formulário {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Este tutorial é uma etapa da série [Create Your First Adaptive Form](/help/forms/using/create-your-first-adaptive-form.md). É recomendável seguir a série em sequência cronológica para entender, executar e demonstrar o caso de uso tutorial completo.

## Sobre o tutorial {#about-the-tutorial}

O módulo de integração de dados do AEM Forms permite criar um modelo de dados de formulário a partir de diferentes fontes de dados de backend, como AEM perfil de usuário, serviços Web RESTful, serviços Web baseados em SOAP, serviços OData e bancos de dados relacionais. É possível configurar objetos e serviços do modelo de dados em um modelo de dados de formulário e associá-lo a um formulário adaptável. Os campos de formulário adaptável são vinculados às propriedades de objetos do modelo de dados. Os serviços permitem preencher previamente o formulário adaptável e gravar os dados de formulário enviados de volta no objeto de modelo de dados.

Para obter mais informações sobre a integração de dados de formulário e o modelo de dados de formulário, consulte [AEM Forms Data Integration](/help/forms/using/data-integration.md).

Este tutorial o orienta pelas etapas para preparar, criar, configurar e associar um modelo de dados de formulário a um formulário adaptável. Ao final deste tutorial, você poderá:

* [Configurar o banco de dados MySQL como fonte de dados](#config-database)
* [Criar modelo de dados de formulário usando o banco de dados MySQL](#create-fdm)
* [Configurar o modelo de dados de formulário](#config-fdm)
* [Modelo de dados do formulário de teste](#test-fdm)

O modelo de dados de formulário será semelhante ao seguinte:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Fontes de dados configuradas  **B.** Schemas de fonte de dados  **C.** Serviços disponíveis  **D.** Objetos de modelo de dados  **E.** Serviços configurados

## Pré-requisitos {#prerequisites}

Antes de começar, verifique se você tem o seguinte:

* Banco de dados MySQL com dados de amostra conforme declarado na seção Pré-requisitos de [Criar seu primeiro formulário adaptável](/help/forms/using/create-your-first-adaptive-form.md)
* Pacote OSGi para o driver JDBC do MySQL, conforme explicado em [Bundling the JDBC Database Driver](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* Formulário adaptável, conforme explicado no primeiro tutorial [Criar um formulário adaptável](/help/forms/using/create-adaptive-form.md)

## Etapa 1: Configurar o banco de dados MySQL como fonte de dados {#config-database}

Você pode configurar diferentes tipos de fontes de dados para criar um modelo de dados de formulário. Para este tutorial, configuraremos o banco de dados MySQL que você configurou e preencheu com dados de amostra. Para obter informações sobre outras fontes de dados compatíveis e como configurá-las, consulte [AEM Forms Data Integration](/help/forms/using/data-integration.md).

Faça o seguinte para configurar seu banco de dados MySQL:

1. Instale o driver JDBC para o banco de dados MySQL como um pacote OSGi:

   1. Faça logon na Instância do autor do AEM Forms como administrador e acesse AEM pacotes do console da Web. O URL padrão é [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

   1. Toque em **Instalar/atualizar**. Uma caixa de diálogo **Fazer upload / Instalar pacotes** é exibida.

   1. Toque em **Escolha Arquivo** para procurar e selecionar o pacote OSGi do driver JDBC do MySQL. Selecione **Iniciar Pacote** e **Atualizar Pacotes** e toque em **Instalar ou Atualizar**. Certifique-se de que o Driver JDBC da Oracle Corporation para MySQL está ativo. O driver está instalado.

1. Configurar o banco de dados MySQL como uma fonte de dados:

   1. Vá para AEM console da Web em [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
   1. Localize a configuração **Apache Sling Connection Pool DataSource**. Toque em para abrir a configuração no modo de edição.
   1. Na caixa de diálogo de configuração, especifique os seguintes detalhes:

      * **Nome da fonte de dados:** especifique qualquer nome. Por exemplo, especifique **WeRetailMySQL**.
      * **Nome** da propriedade do serviço DataSource: Especifique o nome da propriedade de serviço que contém o nome DataSource. Ele é especificado ao registrar a instância da fonte de dados como serviço OSGi. Por exemplo, **datasource.name**.
      * **Classe** de driver JDBC: Especifique o nome da classe Java do driver JDBC. Para o banco de dados MySQL , especifique **com.mysql.jdbc.Driver**.
      * **URI** de conexão JDBC: Especifique o URL de conexão do banco de dados. Para o banco de dados MySQL em execução na porta 3306 e o schema weretail, o URL é: `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Nome de usuário:** Nome de usuário do banco de dados. É necessário habilitar o driver JDBC para estabelecer uma conexão com o banco de dados.
      * **Senha:** senha do banco de dados. É necessário habilitar o driver JDBC para estabelecer uma conexão com o banco de dados.
      * **Testar em linha de crédito:** ative a opção  **Testar em** linha de crédito.
      * **Teste no retorno:** ative o  **teste no** retorno.
      * **Consulta de validação:** especifique uma consulta SQL SELECT para validar conexões do pool. A consulta deve retornar pelo menos uma linha. Por exemplo, **selecione &amp;ast; de detalhes do cliente**.
      * **Isolamento** da transação: Defina o valor como  **READ_COMPROMETIDO**.

      Deixe outras propriedades com os valores padrão [e toque em **Salvar**.](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html)
   Uma configuração semelhante ao seguinte é criada.

   ![relational-database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Etapa 2: Criar modelo de dados de formulário {#create-fdm}

O AEM Forms fornece uma interface de usuário intuitiva para [criar um modelo de dados de formulário](data-integration.md) a partir de fontes de dados configuradas. É possível usar várias fontes de dados em um modelo de dados de formulário. No nosso caso de uso, usaremos a fonte de dados configurada do MySQL.

Faça o seguinte para criar um modelo de dados de formulário:

1. Em AEM instância do autor, navegue até **Forms** > **Data Integration** s.
1. Toque em **Criar** > **Modelo de dados de formulário**.
1. Na caixa de diálogo Criar Modelo de Dados de Formulário , especifique um **name** para o modelo de dados de formulário. Por exemplo, **customer-Shipping-billing-details**. Toque em **Próximo**.
1. A tela selecionar fonte de dados lista todas as fontes de dados configuradas. Selecione a fonte de dados **WeRetailMySQL** e toque em **Criar**.

   ![seleção de fonte de dados](assets/data-source-selection.png)

O modelo de dados de formulário **customer-Shipping-billing-details** é criado.

## Etapa 3: Configurar o modelo de dados de formulário {#config-fdm}

A configuração do modelo de dados de formulário envolve:

* adição de objetos e serviços do modelo de dados
* configuração de serviços de leitura e gravação para objetos de modelo de dados

Faça o seguinte para configurar o modelo de dados de formulário:

1. Em AEM instância do autor, navegue até **Forms > Integrações de dados**. O URL padrão é [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. O modelo de dados de formulário **customer-Shipping-billing-details** que você criou anteriormente está listado aqui. Abra-o no modo de edição.

   A fonte de dados selecionada **WeRetailMySQL** é configurada no modelo de dados de formulário.

   ![default-fdm](assets/default-fdm.png)

1. Expanda a árvore da fonte de dados WeRailMySQL . Selecione os seguintes objetos e serviços de modelo de dados do esquema **weretail** > **customerdetails** para formar o modelo de dados:

   * **Objetos** do modelo de dados:

      * id
      * name
      * ShippingAddress
      * cidade
      * estado
      * zipcode
   * **Serviços:**

      * get
      * atualizar

   Toque em **Adicionar selecionados** para adicionar objetos e serviços de modelo de dados selecionados ao modelo de dados do formulário.

   ![weretail-schema](assets/weretail-schema.png)

   >[!NOTE]
   >
   >Os serviços padrão de obter, atualizar e inserir para fontes de dados JDBC são fornecidos prontos para uso com o modelo de dados de formulário .

1. Configure os serviços de leitura e gravação para o objeto de modelo de dados.

   1. Selecione o objeto de modelo de dados **customerdetails** e toque em **Editar propriedades**.
   1. Selecione **get** no menu suspenso Serviço de leitura. O argumento **id**, que é a chave primária no objeto de modelo de dados de detalhes do cliente, é adicionado automaticamente. Toque em ![aem_6_3_edit](assets/aem_6_3_edit.png) e configure o argumento da seguinte maneira.

      ![read-default](assets/read-default.png)

   1. Da mesma forma, selecione **update** como o Serviço de gravação. O objeto **customerdetails** é adicionado automaticamente como um argumento. O argumento é configurado da seguinte maneira.

      ![write-default](assets/write-default.png)

      Adicione e configure o argumento **id** da seguinte maneira.

      ![id-arg](assets/id-arg.png)

   1. Toque em **Concluído** para salvar as propriedades do objeto do modelo de dados. Em seguida, toque em **Save** para salvar o modelo de dados do formulário.

      Os serviços **get** e **update** são adicionados como serviços padrão para o objeto de modelo de dados.

      ![objeto de modelo de dados](assets/data-model-object.png)

1. Vá para a guia **Services** e configure **get** e **update** serviços.

   1. Selecione o serviço **get** e toque em **Editar propriedades**. A caixa de diálogo de propriedades é aberta.
   1. Especifique o seguinte na caixa de diálogo Editar propriedades:

      * **Título**: Especifique o título do serviço. Por exemplo: Recuperar Endereço de Entrega.
      * **Descrição**: Especifique a descrição que contém o funcionamento detalhado do serviço. Por exemplo:

         Esse serviço recupera o endereço de entrega e outros detalhes do cliente do banco de dados MySQL

      * **Objeto** do Modelo de Saída: Selecione o schema que contém os dados do cliente. Por exemplo:

         esquema customerdetail
      * **Matriz** de retorno: Desative a opção  **Return** array .
      * **Argumentos**: Selecione o argumento com nome  **ID**.

      Toque em **Concluído**. O serviço para recuperar detalhes do cliente do banco de dados do MySQL está configurado.

      ![shiiping-address-retrieval](assets/shiiping-address-retrieval.png)

   1. Selecione o serviço **update** e toque em **Editar propriedades**. A caixa de diálogo de propriedades é aberta.

   1. Especifique o seguinte na caixa de diálogo Editar propriedades:

      * **Título**: Especifique o título do serviço. Por exemplo, Atualizar Endereço de Entrega.

      * **Descrição**: Especifique a descrição que contém o funcionamento detalhado do serviço. Por exemplo:

         Este serviço atualiza o endereço de entrega e campos relacionados no banco de dados MySQL

      * **Objeto** do Modelo de Entrada: Selecione o schema que contém os dados do cliente. Por exemplo:

         esquema customerdetail

      * **Tipo** de saída: Selecione  **BOOLEANO**.
      * **Argumentos**: Selecione o argumento  **** IDs **e detalhes do** cliente.

      Toque em **Concluído**. O serviço **update** para atualizar os detalhes do cliente no banco de dados MySQL está configurado.

      ![shiiping-address-update](assets/shiiping-address-update.png)



O objeto e os serviços do modelo de dados no modelo de dados de formulário são configurados. Agora é possível testar o modelo de dados de formulário.

## Etapa 4: Testar modelo de dados de formulário {#test-fdm}

É possível testar o objeto e os serviços do modelo de dados para verificar se o modelo de dados do formulário está configurado corretamente.

Faça o seguinte para executar o teste:

1. Vá para a guia **Model**, selecione o objeto de modelo de dados **customerdetails** e toque em **Testar objeto de modelo**.
1. Na janela **Test Model / Service**, selecione **Read model object** no menu suspenso **Select Model / Service**.
1. Na seção **customerdetails**, especifique um valor para o argumento **id** que existe no banco de dados MySQL configurado e toque em **Test**.

   Os detalhes do cliente associados à id especificada são buscados e exibidos na seção **Output**, conforme mostrado abaixo.

   ![modelo de leitura-teste](assets/test-read-model.png)

1. Da mesma forma, é possível testar o objeto e os serviços do modelo Gravar.

   No exemplo a seguir, o serviço de atualização atualiza com êxito os detalhes do endereço da id 7102715 no banco de dados.

   ![modelo de gravação de teste](assets/test-write-model.png)

   Agora, se você testar o serviço do modelo de leitura novamente para a id 7107215, ele buscará e exibirá os detalhes atualizados do cliente, conforme mostrado abaixo.

   ![atualizado em leitura](assets/read-updated.png)

