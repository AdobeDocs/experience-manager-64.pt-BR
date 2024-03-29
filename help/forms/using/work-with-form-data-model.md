---
title: Trabalhar com o modelo de dados de formulário
seo-title: Work with form data model
description: A Integração de dados fornece o editor de modelo de dados de formulário para configurar e trabalhar com modelos de dados de formulário.
seo-description: Data Integration provides form data model editor to configure and work with form data models.
uuid: cd123d42-f7cf-489d-8182-f3a01a2a4799
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 2ee45ac0-bc15-403a-93fc-c8592afb967d
feature: Form Data Model
exl-id: 2dcbc459-5fa3-4712-a72e-159bdbad0a61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3166'
ht-degree: 0%

---

# Trabalhar com o modelo de dados de formulário {#work-with-form-data-model}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A Integração de dados fornece o editor de modelo de dados de formulário para configurar e trabalhar com modelos de dados de formulário.

![](do-not-localize/data-integeration.png)

O editor de modelo de dados de formulário oferece uma interface de usuário intuitiva e ferramentas para editar e configurar um modelo de dados de formulário. Usando o editor, é possível adicionar e configurar objetos, propriedades e serviços do modelo de dados de fontes de dados associadas no modelo de dados de formulário. Além disso, permite criar objetos e propriedades do modelo de dados sem fontes de dados e vinculá-los aos respectivos objetos e propriedades do modelo de dados posteriormente. Também é possível gerar e editar dados de amostra para propriedades de objetos do modelo de dados que você pode usar para preencher previamente formulários adaptáveis e comunicações interativas ao visualizar. É possível testar objetos e serviços do modelo de dados configurados em um modelo de dados de formulário para garantir sua integração correta com as fontes de dados.

Se você nunca usou a integração de dados do Forms e não configurou uma fonte de dados ou criou um modelo de dados de formulário, consulte os seguintes tópicos:

* [Integração de dados do AEM Forms](/help/forms/using/data-integration.md)
* [Configurar fontes de dados](/help/forms/using/configure-data-sources.md)
* [Criar modelo de dados de formulário](/help/forms/using/create-form-data-models.md)

Leia para obter detalhes sobre várias tarefas e configurações que podem ser realizadas usando o editor de modelo de dados de formulário.

>[!NOTE]
>
>Você deve ser um membro de ambos **fdm-author** e **usuário de formulários** para criar e trabalhar com o modelo de dados de formulário. Entre em contato com o administrador do AEM para se tornar membro dos grupos.

## Adicionar objetos e serviços do modelo de dados {#add-data-model-objects-and-services}

Se um modelo de dados de formulário foi criado com fontes de dados, é possível usar o editor de modelo de dados de formulário para adicionar objetos e serviços de modelo de dados, configurar suas propriedades, criar associações entre objetos de modelo de dados e testar o modelo e os serviços de dados de formulário.

É possível adicionar objetos e serviços de modelo de dados de fontes de dados disponíveis no modelo de dados de formulário. Enquanto os objetos de modelo de dados adicionados aparecem na guia Modelo , os serviços adicionados aparecem na guia Serviços .

Para adicionar objetos e serviços do modelo de dados:

1. Faça logon na instância do autor do AEM, navegue até **[!UICONTROL Forms > Integrações de dados]** e abra o modelo de dados de formulário no qual deseja adicionar objetos de modelo de dados.
1. No painel Fontes de dados , expanda as fontes de dados para exibir os objetos e serviços disponíveis do modelo de dados.
1. Selecione objetos e serviços de modelo de dados que deseja adicionar ao modelo de dados de formulário e toque em **[!UICONTROL Adicionar Selecionado]**.

   ![objetos selecionados](assets/selected-objects.png)

   A guia Modelo exibe uma representação gráfica de todos os objetos do modelo de dados e suas propriedades adicionadas ao modelo de dados do formulário. Cada objeto de modelo de dados é representado por uma caixa no modelo de dados de formulário.

   ![guia modelo](assets/model-tab.png)

   >[!NOTE]
   >
   >É possível manter e arrastar as caixas de objetos do modelo de dados ao redor para organizá-las na área de conteúdo. Todos os objetos de modelo de dados adicionados ao modelo de dados de formulário são esmaecidos no painel Fontes de dados.

   A guia Serviços lista os serviços adicionados.

   ![guia serviços](assets/services-tab.png)

   >[!NOTE]
   >
   >Além de objetos e serviços de modelo de dados, o documento de metadados do serviço OData inclui propriedades de navegação que definem a associação entre dois objetos de modelo de dados. Para obter mais informações, consulte [Trabalhar com propriedades de navegação de serviços OData](#work-with-navigation-properties-of-odata-services).

1. Toque **[!UICONTROL Salvar]** para salvar o objeto de modelo de formulário.

   >[!NOTE]
   >
   >Você pode chamar os serviços configurados na guia Serviços de um modelo de dados de formulário usando as regras de formulário adaptável. Os serviços configurados estão disponíveis na ação Invocar serviços do editor de regras Para obter mais informações sobre como usar esses serviços em regras de formulário adaptáveis, consulte Invocar serviços e Definir valor de regras em [editor de regras](/help/forms/using/rule-editor.md).

## Criar objetos de modelo de dados e propriedades filho {#create-data-model-objects-and-child-properties}

### Criar objetos do modelo de dados {#create-data-model-objects}

Embora seja possível adicionar objetos de modelo de dados a partir de fontes de dados configuradas, também é possível criar objetos ou entidades de modelo de dados sem fontes de dados. Isso é útil principalmente se você não tiver configurado fontes de dados no modelo de dados de formulário.

Para criar um objeto de modelo de dados sem fontes de dados:

1. Faça logon na instância do autor do AEM, navegue até **[!UICONTROL Forms > Integrações de dados]** e abra o modelo de dados de formulário no qual deseja criar um objeto ou entidade de modelo de dados.
1. Toque **[!UICONTROL Criar entidade]**.
1. Na caixa de diálogo Criar modelo de dados, especifique um nome para o objeto de modelo de dados e toque em **[!UICONTROL Adicionar]**. Um objeto de modelo de dados é adicionado ao modelo de dados de formulário. Observe que o objeto de modelo de dados recém-adicionado não está vinculado a uma fonte de dados e não tem nenhuma propriedade, como mostrado na imagem a seguir.

   ![nova entidade](assets/new-entity.png)

Em seguida, é possível adicionar propriedades filho em objetos de modelo de dados não vinculados.

### Adicionar propriedades secundárias {#child-properties}

O editor de modelo de dados de formulário permite criar propriedades filho em um objeto de modelo de dados. A propriedade quando criada não está vinculada a nenhuma propriedade em uma fonte de dados. Posteriormente, é possível vincular a propriedade filho a outra propriedade no objeto de modelo de dados que a contém.

Para criar uma propriedade filho:

1. Em um modelo de dados de formulário, selecione um objeto de modelo de dados e toque em **[!UICONTROL Criar Propriedade Filho]**.
1. No **[!UICONTROL Criar Propriedade Filho]** , especifique um nome e tipo de dados para a propriedade no **[!UICONTROL Nome]** e **[!UICONTROL Tipo]** , respectivamente. Como opção, você pode especificar um título e uma descrição para a propriedade.
1. Habilite Calculado se a propriedade for uma propriedade calculada. O valor de uma propriedade calculada é avaliado com base em uma regra ou expressão. Para obter mais informações, consulte [Editar propriedades](#edit-properties).
1. Se o objeto de modelo de dados estiver vinculado a uma fonte de dados, a propriedade filho adicionada será vinculada automaticamente à propriedade do objeto de modelo de dados pai com o mesmo nome e tipo de dados.

   Para vincular manualmente uma propriedade filho a uma propriedade de objeto de modelo de dados, toque no ícone Procurar ao lado do **[!UICONTROL Referência de associação]** campo. O **[!UICONTROL Selecionar objeto]** lista todas as propriedades do objeto de modelo de dados pai. Selecione uma propriedade com a qual vincular e toque no ícone de marca de verificação. Observe que você só pode selecionar uma propriedade do mesmo tipo de dados que a propriedade filho.

1. Toque **[!UICONTROL Concluído]** para salvar a propriedade filho e tocar em **[!UICONTROL Salvar]** para salvar o modelo de dados de formulário. A propriedade filho agora é adicionada ao objeto de modelo de dados.

Depois de criar objetos e propriedades do modelo de dados, você pode continuar a criar formulários adaptáveis e comunicações interativas com base no modelo de dados de formulário. Posteriormente, quando houver fontes de dados disponíveis e configuradas, é possível vincular o modelo de dados de formulário às fontes de dados. O vínculo será atualizado automaticamente em formulários adaptáveis associados e comunicações interativas. Para obter mais informações sobre como criar formulários adaptáveis e comunicações interativas usando o modelo de dados de formulário, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md).

### Vincular objetos e propriedades do modelo de dados {#bind-data-model-objects-and-properties}

Quando as fontes de dados que você deseja integrar ao modelo de dados de formulário estiverem disponíveis, será possível adicioná-las ao modelo de dados de formulário conforme descrito em [Atualizar fontes de dados](/help/forms/using/create-form-data-models.md#update). Em seguida, faça o seguinte para vincular os objetos e as propriedades do modelo de dados não vinculados:

1. No modelo de dados de formulário, selecione a fonte de dados não vinculada que deseja vincular a uma fonte de dados.
1. Toque **[!UICONTROL Editar propriedades]**.
1. No **[!UICONTROL Editar propriedades]** toque no ícone de navegação ao lado do painel **[!UICONTROL Vínculo]** campo. Ele abre o **[!UICONTROL Selecionar objeto]** que lista as fontes de dados adicionadas no modelo de dados de formulário.

   ![select-object](assets/select-object.png)

1. Expanda a árvore de fontes de dados e selecione um objeto de modelo de dados com o qual vincular e toque no ícone de marca de verificação.
1. Toque **[!UICONTROL Concluído]** para salvar as propriedades e, em seguida, toque em **[!UICONTROL Salvar]** para salvar o modelo de dados de formulário. O objeto de modelo de dados agora está vinculado a uma fonte de dados. Observe que o objeto de modelo de dados não está mais marcado como Não vinculado.

   ![bound-model-object](assets/bound-model-object.png)

## Configurar serviços {#configure-services}

Para ler e gravar dados de um objeto de modelo de dados, faça o seguinte para configurar os serviços de leitura e gravação:

1. Marque a caixa de seleção na parte superior de um objeto de modelo de dados para selecioná-lo e tocar em **[!UICONTROL Editar propriedades]**.

   ![edit-properties](assets/edit-properties.png)

   Editar propriedades para configurar serviços de leitura e gravação para um objeto de modelo de dados

   A caixa de diálogo Editar propriedades é aberta.

   ![edit-properties-2](assets/edit-properties-2.png)

   Caixa de diálogo Editar propriedades

   >[!NOTE]
   >
   >Além de objetos e serviços de modelo de dados, o documento de metadados do serviço OData inclui propriedades de navegação que definem a associação entre dois objetos de modelo de dados. Quando você adiciona uma fonte de dados do serviço OData a um Modelo de dados de formulário, há um serviço disponível no Modelo de dados de formulário para todas as propriedades de navegação em um objeto de modelo de dados. Você pode usar esse serviço para ler as propriedades de navegação do objeto de modelo de dados correspondente.
   >
   >Para obter mais informações sobre como usar o serviço, consulte [Trabalhar com propriedades de navegação de serviços OData](#work-with-navigation-properties-of-odata-services).

1. Alternar **[!UICONTROL Objeto de nível superior]** para especificar se o objeto de modelo de dados é um objeto de modelo de nível superior.

   Os objetos do modelo de dados configurados em um modelo de dados de formulário estão disponíveis para uso na guia Objetos do modelo de dados no navegador Conteúdo de um formulário adaptável com base no modelo de dados de formulário. Quando você adiciona associação entre dois objetos de modelo de dados, o objeto de modelo de dados com o qual você está associado é aninhado sob o objeto de modelo de dados que está sendo associado na guia Objetos de Modelo de Dados. Se o modelo de dados aninhado for um objeto de nível superior, ele também será exibido separadamente na guia Objetos do Modelo de Dados. Portanto, você verá duas entradas, uma dentro e outra fora da hierarquia aninhada, que pode confundir os autores do formulário. Para fazer com que o objeto de modelo de dados associado apareça somente na hierarquia aninhada, desative a propriedade Objeto de nível superior.

1. Selecione Serviços de leitura e gravação para os objetos de modelo de dados selecionados. Os argumentos para os serviços são exibidos.

   ![serviços de leitura e gravação](assets/read-write-services.png)

   Serviços de leitura e gravação configurados para fonte de dados do funcionário

1. Toque ![aem_6_3_edit](assets/aem_6_3_edit.png) para que o argumento do serviço de leitura vincule o argumento a um Atributo de perfil de usuário, Atributo de solicitação ou valor literal e especifique o valor de vínculo. Ele vincula o argumento de serviço ao atributo de vínculo especificado ou ao valor literal, que é passado ao serviço como um argumento para buscar detalhes associados ao valor especificado na fonte de dados.

   Neste exemplo, a variável `id` O argumento usará o valor da variável `empid` do perfil do usuário e o transmita como um argumento para o serviço de leitura. Ele lerá e retornará valores das propriedades associadas da `employee` objeto de modelo de dados para o `empid`. Portanto, se você especificar 00250 na variável `empid` no formulário, o serviço de leitura lerá os detalhes do funcionário com a id do funcionário 00250.

   Além disso, é possível tornar um argumento obrigatório ou opcional.

   ![editar argumento](assets/edit-argument.png)

   Vínculo do argumento id ao atributo vazio de AEM Perfil de usuário

1. Toque **[!UICONTROL Concluído]** para salvar o argumento , **[!UICONTROL Concluído]** para salvar as propriedades e **[!UICONTROL Salvar]** para salvar o modelo de dados de formulário.

## Adicionar associações {#add-associations}

Normalmente, há associações criadas entre objetos de modelo de dados em uma fonte de dados. A associação pode ser um para um ou um para muitos. Por exemplo, pode haver vários dependentes associados a um funcionário. É conhecida como associação de um para muitos e representada por `1:n` na linha que conecta objetos de modelo de dados associados. No entanto, se uma associação retornar um nome de funcionário exclusivo para uma determinada ID de funcionário, ela será chamada de associação de um para um.

Ao adicionar objetos de modelo de dados associados em uma fonte de dados a um modelo de dados de formulário, suas associações são retidas e exibidas como conectadas por linhas de seta. É possível adicionar associações entre objetos de modelo de dados em diferentes fontes de dados em um modelo de dados de formulário.

>[!NOTE]
>
>Associações predefinidas em uma fonte de dados JDBC não são retidas no modelo de dados de formulário. Você deve criá-los manualmente.

Para adicionar uma associação:

1. Marque a caixa de seleção na parte superior de um objeto de modelo de dados para selecioná-lo e tocar em **[!UICONTROL Adicionar Associação]**. A caixa de diálogo Adicionar associação é aberta.

   ![associação suplementar](assets/add-association.png)

   >[!NOTE]
   >
   >Além de objetos e serviços de modelo de dados, o documento de metadados do serviço OData inclui propriedades de navegação que definem a associação entre dois objetos de modelo de dados. É possível usar essas propriedades de navegação ao adicionar associações no Modelo de dados de formulário. Para obter mais informações, consulte [Trabalhar com propriedades de navegação de serviços OData](#work-with-navigation-properties-of-odata-services).

   A caixa de diálogo Adicionar associação é aberta.

   ![add-Association-2](assets/add-association-2.png)

   Caixa de diálogo Adicionar associação

1. No painel Adicionar Associação:

   * Especifique um título para a associação.
   * Selecione o tipo de associação — Um para um ou Um para muitos.
   * Selecione o objeto de modelo de dados ao qual associar.
   * Selecione o serviço de leitura para ler dados a partir do objeto de modelo selecionado. O argumento read service é exibido. Edite para alterar o argumento, se necessário, e vincule-o à propriedade do objeto de modelo de dados a ser associado.

   No exemplo a seguir, o argumento padrão para o serviço de leitura do objeto de modelo de dados Dependentes é `dependentid`.

   ![add-Association-example](assets/add-association-example.png)

   O argumento padrão para o serviço de leitura de Dependentes é dependente

   No entanto, o argumento deve ser uma propriedade comum entre o objeto de modelo de dados associado, que neste exemplo é `Employeeid`. Por conseguinte, o `Employeeid` O argumento deve ser vinculado ao `id` propriedade do objeto de modelo de dados Funcionário para buscar os detalhes dos dependentes associados no objeto de modelo de dados Dependentes.

   ![add-Association-example-2](assets/add-association-example-2.png)

   Argumento e vínculo atualizados

   Toque **[!UICONTROL Concluído]** para salvar o argumento .

1. Toque **[!UICONTROL Concluído]** para salvar a associação e **[!UICONTROL Salvar]** para salvar o modelo de dados de formulário.
1. Repita as etapas para criar mais associações, conforme necessário.

>[!NOTE]
>
>A associação adicionada aparece na caixa de objeto de modelo de dados com o título especificado e uma linha que conecta os objetos de modelo de dados associados.
>
>É possível editar uma associação marcando a caixa de seleção e tocando em **[!UICONTROL Editar Associação]**.

![associação adicionada](assets/added-association.png)

## Editar propriedades {#properties}

É possível editar propriedades de objetos do modelo de dados, suas propriedades e serviços adicionados ao modelo de dados de formulário.

Para editar propriedades:

1. Marque a caixa de seleção ao lado de um objeto de modelo de dados, uma propriedade ou um serviço no modelo de dados de formulário.
1. Toque **[!UICONTROL Editar propriedades]**. O **[!UICONTROL Editar propriedades]** será aberto um painel para o objeto, propriedade ou serviço do modelo selecionado.

   * **Objeto do modelo de dados**: Especifique os serviços de leitura e gravação e edite os argumentos.
   * **Propriedade**: Especifique o tipo, o subtipo e o formato da propriedade. Você também pode especificar se a propriedade selecionada é a chave primária para o objeto de modelo de dados.
   * **Serviço**: Especifique o objeto do modelo de entrada, o tipo de saída e os argumentos para o serviço. Para um serviço Get, você pode especificar se é esperado que ele retorne uma matriz.

   ![edit-properties-service](assets/edit-properties-service.png)

   Caixa de diálogo Editar propriedades para um serviço get

1. Toque **[!UICONTROL Concluído]** para salvar as propriedades e **[!UICONTROL Salvar]** para salvar o modelo de dados de formulário.

### Criar propriedades calculadas {#computed}

Uma propriedade calculada é aquela cujo valor é calculado com base em uma regra ou expressão. Usando uma regra, é possível definir o valor de uma propriedade calculada como uma sequência literal, um número, o resultado de uma expressão matemática ou o valor de outra propriedade no modelo de dados de formulário.

Por exemplo, você pode criar uma propriedade calculada **FullName** cujo valor é resultado da concatenação do **FirstName** e **LastName** propriedades. Para fazer isso:

1. Criar uma nova propriedade com o nome `FullName` cujo tipo de dados é String.
1. Habilitar **[!UICONTROL Calculado]** e tocar **[!UICONTROL Concluído]** para criar a propriedade.

   ![computado](assets/computed.png)

   A propriedade computada FullName é criada. Observe o ícone ao lado da propriedade para descrever uma propriedade calculada.

   ![computed-prop](assets/computed-prop.png)

1. Selecione a propriedade FullName e toque em **[!UICONTROL Editar regra]**. Uma janela do editor de regras é aberta.
1. Na janela do editor de regras, toque em **[!UICONTROL Criar]**. A **[!UICONTROL Definir valor]** janela de regras é aberta.

   No menu suspenso Selecionar opção , selecione **[!UICONTROL Expressão matemática]**. Outras opções disponíveis são **[!UICONTROL Objeto de Modelo de Dados de Formulário]** e **[!UICONTROL String]**.

1. Na expressão matemática, selecione **[!UICONTROL FirstName]** e **[!UICONTROL LastName]** no primeiro e no segundo objetos, respectivamente. Selecionar **[!UICONTROL plus]** como operador.

   Toque **[!UICONTROL Concluído]** em seguida, toque em **[!UICONTROL Fechar]** para fechar a janela do editor de regras. A regra é semelhante ao seguinte.

   ![regra](assets/rule.png)

1. No modelo de dados de formulário, toque em **[!UICONTROL Salvar]**. A propriedade calculada é configurada.

## Trabalhar com propriedades de navegação de serviços OData {#work-with-navigation-properties-of-odata-services}

Nos serviços OData, as propriedades de navegação são usadas para definir associações entre dois objetos de modelo de dados. Essas propriedades são definidas em um tipo de entidade ou em um tipo complexo. Por exemplo, na extração a seguir do arquivo de metadados da amostra [TripPin](https://www.odata.org/blog/trippin-new-odata-v4-sample-service/) Os serviços de amostra OData contêm três propriedades de navegação: Amigos, Melhores Amigos e Percursos.

Para obter mais informações sobre propriedades de navegação, consulte [Documentação de OData](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part3-csdl/odata-v4.0-errata03-os-part3-csdl-complete.html#_Toc453752536).

```xml
<edmx:Edmx xmlns:edmx="https://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
<script/>
<edmx:DataServices>
<Schema xmlns="https://docs.oasis-open.org/odata/ns/edm" Namespace="Microsoft.OData.Service.Sample.TrippinInMemory.Models">
<EntityType Name="Person">
<Key>
<PropertyRef Name="UserName"/>
</Key>
<Property Name="UserName" Type="Edm.String" Nullable="false"/>
<Property Name="FirstName" Type="Edm.String" Nullable="false"/>
<Property Name="LastName" Type="Edm.String"/>
<Property Name="MiddleName" Type="Edm.String"/>
<Property Name="Gender" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.PersonGender" Nullable="false"/>
<Property Name="Age" Type="Edm.Int64"/>
<Property Name="Emails" Type="Collection(Edm.String)"/>
<Property Name="AddressInfo" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location)"/>
<Property Name="HomeAddress" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location"/>
<Property Name="FavoriteFeature" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature" Nullable="false"/>
<Property Name="Features" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature)" Nullable="false"/>
<NavigationProperty Name="Friends" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person)"/>
<NavigationProperty Name="BestFriend" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person"/>
<NavigationProperty Name="Trips" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Trip)"/>
</EntityType>
```

Ao configurar um serviço OData em um Modelo de dados de formulário, todas as propriedades de navegação em um contêiner de entidade são disponibilizadas por meio de um serviço no Modelo de dados de formulário. Neste exemplo do serviço TripPin OData, as três propriedades de navegação no `Person` contêiner de entidade pode ser lido usando um `GET LINK` no Modelo de dados de formulário.

O seguinte destaca o `GET LINK of Person /People` no Modelo de dados de formulário, que é um serviço combinado para as três propriedades de navegação no `Person` entidade do serviço OData do TripPin.

![nav-prop-service](assets/nav-prop-service.png)

Depois de adicionar o `GET LINK` para a guia Serviços no Modelo de dados de formulário, é possível editar as propriedades para escolher o objeto de modelo de saída e a propriedade de navegação a ser usada no serviço. Por exemplo, o seguinte `GET LINK of Person /People` No exemplo a seguir, o serviço usa Trip como o objeto de modelo de saída e a propriedade de navegação como Trips.

![edit-prop-nav-prop](assets/edit-prop-nav-prop.png)

>[!NOTE]
>
>Os valores disponíveis na variável **[!UICONTROL Valor padrão]** do **NavigationPropertyName** O argumento depende do estado da **[!UICONTROL Retornar matriz?]** botão de alternância. Quando ativado, mostra as propriedades de navegação do tipo Collection .

Neste exemplo, você também pode escolher o objeto de modelo de saída como Pessoa e argumento de propriedade de navegação como Amigos ou Melhor Amigo (dependendo se **[!UICONTROL Retornar matriz?]** está ativado ou desativado).

![edit-prop-nav-prop2](assets/edit-prop-nav-prop2.png)

Da mesma forma, é possível escolher uma `GET LINK` e configure suas propriedades de navegação ao adicionar associações no Modelo de dados de formulário. No entanto, para poder selecionar uma propriedade de navegação, verifique se a variável **[!UICONTROL Vínculo com campo]** está definida como **[!UICONTROL Literal]**.

![add-Association-nav-prop](assets/add-association-nav-prop.png)

## Gerar e editar dados de amostra {#sample}

O editor de modelo de dados de formulário permite gerar dados de amostra para todas as propriedades de objetos do modelo de dados, incluindo propriedades calculadas, em um modelo de dados de formulário. É um conjunto de valores aleatórios que está em conformidade com o tipo de dados configurado para cada propriedade. Também é possível editar e salvar dados, que são retidos mesmo se os dados de amostra forem gerados novamente.

Faça o seguinte para gerar e editar dados de amostra:

1. Abra um modelo de dados de formulário e toque em **[!UICONTROL Editar dados de amostra]**. Ele gera e exibe os dados de amostra na janela Editar dados de amostra .

   ![exemplo de dados](assets/sample-data.png)

1. Em **[!UICONTROL Editar dados de amostra]** janela, edite os dados, conforme necessário, e toque em **[!UICONTROL Salvar]**.

Em seguida, é possível usar os dados de amostra para preencher e testar as comunicações interativas com base no modelo de dados de formulário. Para obter mais informações, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md).

## Testar objetos e serviços do modelo de dados {#test-data-model-objects-and-services}

O modelo de dados de formulário está configurado, mas antes de colocá-lo em uso, convém testar se os objetos e serviços do modelo de dados estão funcionando conforme o esperado. Para testar objetos e serviços do modelo de dados:

1. Selecione um objeto de modelo de dados ou um serviço no modelo de dados de formulário e toque em **[!UICONTROL Objeto de Modelo de Teste]** ou **[!UICONTROL Serviço de teste]**, respectivamente.

   A janela Modelo de dados de formulário de teste é aberta.

   ![modelo de dados de teste](assets/test-data-model.png)

1. Na janela Testar Modelo de Dados de Formulário, selecione o objeto ou serviço de modelo de dados a ser testado no painel Entrada.

1. Especifique um valor de argumento no código de teste e toque em **[!UICONTROL Teste]**. Um teste bem-sucedido retorna a saída no painel Saída.

   ![test-data-model-2](assets/test-data-model-2.png)

Da mesma forma, é possível testar outros objetos e serviços do modelo de dados no modelo de dados de formulário.

## Próximas etapas {#next-steps}

Você tem um modelo de dados de formulário de trabalho que agora está pronto para uso em formulários adaptáveis e fluxos de trabalho de comunicações interativas. Para obter mais informações, consulte [Usar modelo de dados de formulário](/help/forms/using/using-form-data-model.md).
