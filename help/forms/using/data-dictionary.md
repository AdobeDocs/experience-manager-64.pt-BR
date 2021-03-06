---
title: Dicionários de dados
seo-title: Dicionários de dados
description: O dicionário de dados no Gerenciamento de correspondência permite integrar dados de back-end a cartas como entradas para uso na correspondência do cliente.
seo-description: O dicionário de dados no Gerenciamento de correspondência permite integrar dados de back-end a cartas como entradas para uso na correspondência do cliente.
uuid: cc976dff-f243-4807-a92c-81b78476a744
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 53595ac8-ca7e-4adc-9214-5d0b7cdf71a0
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '3868'
ht-degree: 1%

---


# Dicionário de dados {#data-dictionary}

## Introdução {#introduction}

Um dicionário de dados permite que usuários corporativos usem informações de fontes de dados de back-end sem conhecer detalhes técnicos sobre seus modelos de dados subjacentes. Um dicionário de dados é composto por elementos de dicionário de dados (DDEs). Esses elementos de dados são usados para integrar dados de back-end às cartas como entrada para uso em uma correspondência do cliente.

Um dicionário de dados é uma representação independente dos metadados que descreve as estruturas de dados subjacentes e seus atributos associados. Um dicionário de dados é criado usando o vocabulário de negócios. Ele pode ser mapeado para um ou mais modelos de dados subjacentes.

O dicionário de dados é composto de elementos de três tipos: Elementos simples, composto e coleção. DDEs simples são elementos primitivos, como sequências, números, datas e valores booleanos que contêm informações como o nome de uma cidade. Um DDE composto contém outros DDEs, que podem ser do tipo primitivo, composto ou coleção. Por exemplo, um endereço, que consiste em um endereço de rua, cidade, província, país e código postal. Uma Coleção é uma lista de DDEs Simples ou Compostos semelhantes. Por exemplo, um cliente com vários locais ou endereços de faturamento e envio diferentes.

O Gerenciamento de correspondência usa o back-end, o cliente, `` ``ou os dados específicos do recipient armazenados de acordo com a estrutura do dicionário de dados para criar correspondência destinada a clientes diferentes. Por exemplo, um documento pode ser criado com nomes amigáveis, como &quot;Caro {Nome}&quot;,&quot;Sr. {Sobrenome}&quot;.

Normalmente, os usuários corporativos não exigem conhecimento de representações de metadados, como XSD (esquema XML) e classes Java. No entanto, elas geralmente exigem acesso a essas estruturas de dados e atributos para criar soluções.

### Fluxo de trabalho do Dicionário de dados {#data-dictionary-workflow}

1. Um Autor [cria o Dicionário de dados](#createdatadictionary) carregando um esquema ou do zero.
1. O Autor cria cartas e Comunicações interativas com base no dicionário de dados e associa elementos do dicionário de dados em cartas e Comunicações interativas, sempre que necessário.
1. Um autor pode baixar arquivos XML de dados de amostra, com base em um esquema de dicionário de dados. O autor pode modificar o arquivo XML de dados de amostra, que pode ser associado como dados de teste com o dicionário de dados. O mesmo é usado durante a visualização da carta.
1. Enquanto [visualizando uma carta](/help/forms/using/create-letter.md#p-types-of-linkage-available-for-each-of-the-fields-p), um Autor opta por visualizar a carta com dados (Visualização personalizada). A carta é aberta pré-preenchida com os dados fornecidos pelo Autor. Isso é aberto na interface criar correspondência. O Agente que está visualizando esta carta pode modificar o conteúdo, os dados e os anexos desta carta e pode enviar a carta final. Para obter mais informações sobre como criar cartas, consulte [Criar correspondência](/help/forms/using/create-letter.md).

## Pré-requisitos {#prerequisite}

Instale o [Pacote de Compatibilidade](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/compatibility-package.html) para visualizar a opção **Dicionários de Dados** na página **Forms**.

## Criar um dicionário de dados {#createdatadictionary}

Você usa o Editor de dicionário de dados para criar um dicionário de dados ou pode fazer upload de um arquivo de esquema XSD para criar um dicionário de dados com base nele. É possível estender o dicionário de dados adicionando mais informações necessárias, incluindo campos. Independentemente de como o dicionário de dados foi criado, o proprietário do processo de negócios não precisa de conhecimento dos sistemas de back-end. O proprietário do processo de negócios precisa apenas do conhecimento dos objetos de domínio e de suas definições para o seu processo.

>[!NOTE]
>
>Para várias letras que exigem elementos semelhantes, você pode criar um dicionário de dados comum. Entretanto, um grande dicionário de dados com um grande número de elementos pode causar problemas de desempenho ao usar o dicionário de dados e carregar os elementos, como em letras e fragmentos de documento. Se tiver problemas de desempenho, tente criar dicionários de dados separados para letras diferentes.

1. Selecione **Forms** > **Dicionários de dados**.
1. Toque em **Criar dicionário de dados**.
1. Na tela Propriedades, adicione o seguinte:

   * **Título:** (opcional) insira o título do dicionário de dados. O título não precisa ser exclusivo e pode ter caracteres especiais e caracteres que não sejam inglês. Cartas e outros fragmentos de documento são referenciados com seu título (quando disponíveis), como em miniaturas e propriedades de ativos. Os dicionários de dados são referenciados com seus nomes e não com títulos.
   * **Nome:** o nome exclusivo do dicionário de dados. No campo Nome , é possível inserir somente caracteres, números e hifens em inglês. O campo Nome é automaticamente preenchido com base no campo Título e os caracteres especiais, espaços, números e caracteres que não estão em inglês inseridos no campo Título são substituídos por hifens. Embora o valor no campo Título seja copiado automaticamente para o Nome, você pode editar o valor.

   * **Descrição**: (Opcional) Descrição do dicionário de dados.
   * **Tags:** (Opcional) Para criar uma tag personalizada, insira o valor no campo de texto e pressione Enter. Você pode ver sua tag abaixo do campo de texto das tags. Ao salvar esse texto, as tags recém-adicionadas também são criadas.
   * **Propriedades** estendidas: (Opcional) Toque em  **Adicionar** campo para especificar atributos de metadados para seu dicionário de dados. Na coluna Nome da propriedade , insira um nome de propriedade exclusivo. Na coluna Value , insira um valor para associar à propriedade.

   ![Propriedades do dicionário de dados especificado em alemão](do-not-localize/1_ddproperties.png)

1. (Opcional) Para fazer upload de uma definição de esquema XSD para seu dicionário de dados, no painel Estrutura do dicionário de dados , toque em **Fazer upload do esquema XML**. Navegue até o arquivo XSD, selecione-o e toque em **Abrir**. Um Dicionário de dados é criado com base no esquema XML carregado. Você precisa ajustar os nomes de exibição e as descrições dos elementos no dicionário de dados. Para fazer isso, selecione os nomes dos elementos tocando neles e edite suas descrições, nomes de exibição e outros detalhes nos campos no painel direito.

   Para obter mais informações sobre Elementos de Dicionário Calculados, consulte [Elementos de Dicionário de Dados Calculados](#computedddelements).

   >[!NOTE]
   >
   >É possível ignorar o upload do arquivo de esquema e criar o dicionário de dados do zero usando a interface do usuário do . Para fazer isso, pule esta etapa e continue com as próximas etapas.

1. Toque em **Próximo**.
1. Na tela Adicionar propriedades , adicione os elementos ao dicionário de dados. Você também pode adicionar/excluir elementos e editar seus detalhes se tiver carregado um esquema para obter uma estrutura básica do dicionário de dados.

   Você pode tocar nos três pontos no lado direito de um elemento e adicionar um elemento à estrutura do dicionário de dados.

   ![1_2_createanelement](assets/1_2_createanelement.png)

   Selecione Elemento composto, Elemento de coleção ou Elemento primitivo.

   * Um DDE composto contém outros DDEs, que podem ser do tipo primitivo, composto ou coleção. Por exemplo, um endereço, que consiste em um endereço de rua, cidade, província, país e código postal.
   * Os DDEs primitivos são elementos como sequências, números, datas e valores booleanos que contêm informações como o nome de uma cidade.
   * Uma Coleção é uma lista de DDEs Simples ou Compostos semelhantes. Por exemplo, um cliente com vários locais ou endereços de faturamento e envio diferentes.

   A seguir estão algumas regras para criar um dicionário de dados:

   * Somente o tipo composto é permitido como DDE de nível superior em um dicionário de dados.
   * Nome, nome de referência e tipo de elemento são campos obrigatórios para um dicionário de dados e DDEs.
   * O nome de referência deve ser exclusivo.
   * Um DDE pai (composto) não pode ter dois filhos com o mesmo nome.
   * As enumerações contêm apenas tipos primitivos de Cadeia de caracteres.

   Para obter mais informações sobre elementos Compostos, Coleção e Primitivos e trabalhar com elementos do dicionário de dados, consulte [Mapeamento de elementos do dicionário de dados para o esquema XML](#mappingddetoschema).

   Para obter informações sobre validações no Dicionário de dados, consulte [Validações do Editor de dicionário de dados](#ddvalidations).

   ![2_adddpropertiesbasic](assets/2_addddpropertiesbasic.png)

1. (Opcional) Depois de selecionar um elemento, na guia Avançado , é possível adicionar propriedades (atributos). Também é possível tocar em **Adicionar campo** e estender as propriedades de um elemento DD.

   ![3_adddpropertiesadvanced](assets/3_addddpropertiesadvanced.png)

1. (Opcional) Você pode remover qualquer elemento tocando nos três pontos no lado direito de um elemento e selecionando **Excluir**.

   ![4_deleteelement](assets/4_deleteelement.png)

   >[!NOTE]
   >
   >A exclusão de um elemento composto/coleção com nós filhos também exclui seus nós filhos.

1. (Opcional) Selecione um elemento no painel Estrutura do dicionário de dados e no painel Campo e Lista de variáveis. Altere ou adicione quaisquer atributos necessários associados ao elemento.
1. Toque em **Salvar**.

### Criar cópias de um ou mais dicionários de dados {#create-copies-of-one-or-more-data-dictionary}

Para criar rapidamente um ou mais dicionários de dados com propriedades e elementos semelhantes aos dicionários de dados existentes, você pode copiá-los e colá-los.

1. Na lista de dicionários de dados, selecione os dicionários de dados apropriados. A interface do usuário exibe o ícone Copiar .
1. Toque em Copiar. A interface do usuário exibe o ícone Colar.
1. Toque em Colar. A caixa de diálogo Colar é exibida. O sistema atribui automaticamente nomes e títulos aos novos dicionários de dados.
1. Se necessário, edite o Título e o Nome com os quais deseja salvar a cópia do dicionário de dados.
1. Toque em Colar. A cópia do dicionário de dados é criada. Agora é possível fazer as alterações necessárias no dicionário de dados recém-criado.

## Consulte os fragmentos de documento ou documentos que se referem a um elemento de Dicionário de dados {#see-the-document-fragments-or-documents-that-refer-to-a-data-dictionary-element}

Ao editar ou exibir um dicionário de dados, você pode ver quais elementos no dicionário de dados são referenciados em quais Textos, Condições, Cartas e Comunicações interativas.

1. Siga um destes procedimentos para editar o dicionário de dados:

   * Passe o mouse sobre um dicionário de dados e toque em Editar.
   * Selecione um dicionário de dados e toque em Editar no cabeçalho.
   * Passe o mouse sobre um dicionário de dados e toque em Selecionar. Em seguida, toque em Editar no cabeçalho.

   Ou toque em um dicionário de dados para exibi-lo.

1. No dicionário de dados, toque em um elemento simples para selecioná-lo. Os elementos de composição e coleção não têm referências.

   Juntamente com as propriedades Básicas e Avançadas do elemento, o Conteúdo emprestado também é exibido.

1. Toque em Conteúdo emprestado.

   A guia Conteúdo emprestado é exibida com o seguinte: Textos, condições, letras e comunicações interativas. Cada um desses cabeçalhos também exibe o número de referências ao elemento selecionado.

1. Toque em um cabeçalho para ver o nome dos ativos que se referem ao elemento.

   ![lentcontent](assets/lentcontent.png)

1. Para exibir o conteúdo emprestado para outro elemento, toque no elemento .
1. Para exibir um ativo que se refere ao elemento, toque em seu nome. O navegador exibe o ativo, a letra ou a Comunicação interativa.

## Trabalhar com dados de teste {#working-with-test-data}

1. Na página Dicionários de dados , toque em **Selecionar**.
1. Toque em um dicionário de dados para o qual deseja baixar os dados de teste e toque em **Baixar dados XML de amostra**.
1. Toque em **OK** na mensagem de alerta. Um arquivo XML é baixado.
1. Abra o arquivo XML com o Bloco de notas ou outro editor XML. O arquivo XML tem a mesma estrutura que o dicionário de dados e as strings de espaço reservado nos elementos. Substitua as strings de espaço reservado pelos dados com os quais você deseja testar uma carta.

   ```xml
   <?xml version="1.0" encoding="UTF-8" standalone="no"?>
   <Company>
   <Name>string</Name>
   <Type>string</Type>
   <HeadOfficeAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </HeadOfficeAddress>
   <SalesOfficeAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </SalesOfficeAddress>
   <HeadCount>1.0</HeadCount>
   <CEO>
   <PersonName>
   <FirstName>string</FirstName>
   <MiddleName>string</MiddleName>
   <LastName>string</LastName>
   </PersonName>
   <DOB>string</DOB>
   <CurrAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </CurrAddress>
   <DOJ>14-04-1973</DOJ>
   <Phone>1.0</Phone>
   </CEO>
   </Company>
   ```

   >[!NOTE]
   >
   >Neste exemplo, XML cria espaço para três valores em um elemento de coleção, mas o número de valores pode ser aumentado/diminuído de acordo com o requisito.

1. Depois de fazer as entradas de dados, você pode usar esse arquivo XML ao visualizar uma carta com dados de teste.

   Você pode adicionar esses dados de teste com DD (selecione DD e toque em Fazer upload de dados de teste e fazer upload desse arquivo xml)

   Então, depois disso, quando você visualiza a carta normalmente (não personalizada), esses dados XML são usados na carta. Também é possível tocar em Personalizado e fazer upload desse XML.

## Amostras {#samples}

Os exemplos de código a seguir mostram detalhes de implementação do Dicionário de dados.

### Exemplo de esquema que pode ser carregado no Dicionário de dados {#sample-schema-that-can-be-uploaded-to-the-data-dictionary}

```xml
<?xml version="1.0" encoding="utf-8"?> 
<xs:schema xmlns="DCT" targetNamespace="DCT" xmlns:xs="https://www.w3.org/2001/XMLSchema" 
  elementFormDefault="qualified" attributeFormDefault="unqualified"> 
  <xs:element name="Company"> 
    <xs:complexType> 
      <xs:sequence> 
        <xs:element name="Name" type="xs:string"/> 
        <xs:element name="Type" type="xs:anySimpleType"/> 
        <xs:element name="HeadOfficeAddress" type="Address"/> 
        <xs:element name="SalesOfficeAddress" type="Address" minOccurs="0"/> 
        <xs:element name="HeadCount" type="xs:integer"/> 
        <xs:element name="CEO" type="Employee"/> 
        <xs:element name="Workers" type="Employee" maxOccurs="unbounded"/> 
      </xs:sequence> 
    </xs:complexType> 
  </xs:element> 
  <xs:complexType name="Employee"> 
    <xs:complexContent> 
      <xs:extension  base="Person"> 
        <xs:sequence> 
          <xs:element name="CurrAddress" type="Address"/> 
          <xs:element name="DOJ" type="xs:date"/> 
          <xs:element name="Phone" type="xs:integer"/> 
        </xs:sequence> 
      </xs:extension> 
    </xs:complexContent> 
  </xs:complexType> 
  <xs:complexType name="Person"> 
    <xs:sequence> 
      <xs:element name="PersonName" type="Name"/> 
      <xs:element name="DOB" type="xs:dateTime"/> 
    </xs:sequence> 
  </xs:complexType> 
  <xs:complexType name="Name"> 
    <xs:sequence> 
      <xs:element name="FirstName" type="xs:string"/> 
      <xs:element name="MiddleName" type="xs:string"/> 
      <xs:element name="LastName" type="xs:string"/> 
    </xs:sequence> 
  </xs:complexType> 
  <xs:complexType name="Address"> 
    <xs:sequence> 
      <xs:element name="Street" type="xs:string"/> 
      <xs:element name="City" type="xs:string"/> 
      <xs:element name="State" type="xs:string"/> 
      <xs:element name="Zip" type="xs:string"/> 
    </xs:sequence> 
  </xs:complexType> 
</xs:schema>
```

## Atributos comuns associados a um DDE {#common-attributes-associated-with-a-dde}

A tabela a seguir detalha os atributos comuns associados a um DDE:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Atributo</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>Nome</td> 
   <td>Sequência de caracteres</td> 
   <td>Obrigatório.<br /> Nome do DDE. Deve ser único.</td> 
  </tr> 
  <tr> 
   <td>Nome da referência<br /></td> 
   <td>Sequência de caracteres</td> 
   <td>Obrigatório. Nome de referência exclusivo para o DDE que permite referências ao DDE que são independentes de alterações na hierarquia ou na estrutura do dicionário de dados. Os módulos de texto são mapeados usando este nome</td> 
  </tr> 
  <tr> 
   <td>displayname</td> 
   <td>Sequência de caracteres</td> 
   <td>Um nome opcional amigável para o usuário do DDE.</td> 
  </tr> 
  <tr> 
   <td>descrição</td> 
   <td>Sequência de caracteres</td> 
   <td>Descrição do DDE.</td> 
  </tr> 
  <tr> 
   <td>elementType</td> 
   <td>Sequência de caracteres</td> 
   <td>Obrigatório. O tipo de DDE: STRING, NÚMERO, DATA, Booleano, COMPOSTO, COLEÇÃO.</td> 
  </tr> 
  <tr> 
   <td>elementSubType</td> 
   <td>Sequência de caracteres</td> 
   <td>O subtipo para DDE: ENUM. Somente permitido para STRING e NUMBER elementType.</td> 
  </tr> 
  <tr> 
   <td>Chave</td> 
   <td>Booleano</td> 
   <td>Um campo booleano para indicar se um DDE é um elemento chave.</td> 
  </tr> 
  <tr> 
   <td>Computado</td> 
   <td>Booleano</td> 
   <td>Um campo booleano para indicar se um DDE é calculado. Um valor DDE calculado é uma função de outros valores DDE. Por padrão, expressões jsp são compatíveis.</td> 
  </tr> 
  <tr> 
   <td>expressão</td> 
   <td>Sequência de caracteres</td> 
   <td>A expressão para o DDE "calculado". O serviço de avaliação de expressão enviado por padrão suporta expressões JSP EL. É possível substituir o serviço de expressão por uma implementação personalizada.</td> 
  </tr> 
  <tr> 
   <td>valueSet</td> 
   <td>Lista</td> 
   <td>Um conjunto de valores permitidos para um tipo Enum DDE. Por exemplo, o tipo de Conta pode ter apenas valores (Salvar, Atual).</td> 
  </tr> 
  <tr> 
   <td>extendedProperties</td> 
   <td>Objeto</td> 
   <td>Um mapa de propriedades personalizadas adicionado ao DDE (interface do usuário específica ou qualquer outra informação).</td> 
  </tr> 
  <tr> 
   <td>Obrigatório</td> 
   <td>Booleano</td> 
   <td>O sinalizador indica que a fonte de dados da instância correspondente ao dicionário de dados deve conter o valor desse DDE específico.</td> 
  </tr> 
  <tr> 
   <td>Vínculo</td> 
   <td>BindingElement</td> 
   <td>O vínculo XML ou Java do elemento.</td> 
  </tr> 
 </tbody> 
</table>

### Elementos do dicionário de dados calculados {#computedddelements}

Um dicionário de dados também pode incluir elementos calculados. Um elemento de dicionário de dados calculado é sempre associado a uma expressão. Essa expressão é avaliada para obter o valor de um elemento de dicionário de dados no tempo de execução. Um valor DDE calculado é uma função de outros valores DDE ou literais. Por padrão, as expressões da Linguagem de expressão JSP (EL) são compatíveis. As expressões EL usam os caracteres ${ } e expressões válidas podem incluir literais, operadores, variáveis (referências de elementos do dicionário de dados) e chamadas de função. Ao fazer referência a um elemento de dicionário de dados na expressão, o nome de referência do DDE é usado. O nome de referência é exclusivo para cada elemento de dicionário de dados em um dicionário de dados.

Um DDE PersonFullName calculado pode ser associado a uma expressão de concatenação EL, como ${PersonFirstName} ${PersonLastName}.

## Mapeamento de tipo de dados entre XSD e o dicionário de dados {#data-type-mapping-between-xsd-and-data-dictionary-br}

A exportação de um XSD requer mapeamento de dados específico, que é detalhado na tabela a seguir. A coluna DDI indica o tipo do valor DDE, conforme disponível no DDI.

<table> 
 <tbody> 
  <tr> 
   <td>XSD <br /> </td> 
   <td><p>Dicionário de dados <br /> </p> </td> 
   <td><p>DDI (Tipo de Dados de Valor da Instância)<br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>xs:elemento do tipo - Tipo composto<br /> </p> </td> 
   <td><p>DDE do tipo - COMPOSITE<br /> </p> </td> 
   <td>java.util.Map<br /> </td> 
  </tr> 
  <tr> 
   <td><p>xs:element onde maxOccurs &gt; 1<br /> </p> </td> 
   <td><p>DDE do tipo - COLLECTION-<br /> Um nó DDE é criado ao lado do DDE COLLECTION, que captura informações do nó principal COLLECTION. O mesmo é criado para a coleção de tipos de dados simples/compostos. Sempre que houver uma COLLECTION do tipo composto, a árvore do Dicionário de dados captura os campos constituintes nos filhos do DDE criado para capturar informações do tipo.<br /> - DDE (COLLECTION)<br />  - DDE(COMPOSITE para informações de tipo)<br />  - DDE(STRING) field1<br />  - DDE(STRING) field2<br /> <br /> </p> </td> 
   <td>java.util.List<br /> </td> 
  </tr> 
  <tr> 
   <td><p>Atributo do tipo - xs:id <br /> </p> </td> 
   <td>DDE do tipo - STRING <br /> </td> 
   <td>java.lang.String<br /> </td> 
  </tr> 
  <tr> 
   <td><p>xs:attribute /xs:element do tipo - xs:string</p> </td> 
   <td>DDE do tipo - STRING<br /> </td> 
   <td>java.lang.String<br /> </td> 
  </tr> 
  <tr> 
   <td>xs:attribute /xs:element do tipo - xs: booleano <br /> </td> 
   <td>DDE do tipo - Booleano <br /> </td> 
   <td>java.lang.Boolean<br /> </td> 
  </tr> 
  <tr> 
   <td>xs:attribute /xs:element do tipo - xs:date </td> 
   <td>DDE do tipo - DATE </td> 
   <td>java.lang.String</td> 
  </tr> 
  <tr> 
   <td>xs:attribute /xs:element do tipo - xs:integer </td> 
   <td>DDE do tipo - NÚMERO </td> 
   <td>java.lang.Double</td> 
  </tr> 
  <tr> 
   <td>xs:attribute /xs:element do tipo - xs:long</td> 
   <td>DDE do tipo - NÚMERO </td> 
   <td>java.lang.Double</td> 
  </tr> 
  <tr> 
   <td>xs:attribute /xs:element do tipo - xs:double</td> 
   <td>DDE do tipo - NÚMERO </td> 
   <td>java.lang.Double</td> 
  </tr> 
  <tr> 
   <td>Elemento do tipo enum e baseType - xs:string</td> 
   <td>DDE do tipo <br /> - subtipo STRING<br /> - ENUM<br /> valueSet - os valores permitidos para ENUM<br /> </td> 
   <td>java.lang.String</td> 
  </tr> 
 </tbody> 
</table>

## Baixe um arquivo de dados de amostra de um dicionário de dados {#download-a-sample-data-file-from-a-data-dictionary}

Depois de criar um dicionário de dados, você pode baixá-lo como um arquivo de dados de amostra XML para fazer entradas de texto nele.

1. Na página Dicionários de dados , toque em **Selecionar** e em um dicionário de dados para selecioná-lo.
1. Selecione **Baixar Dados XML de Amostra**.
1. Toque em **OK** na mensagem de alerta.

   O Gerenciamento de correspondência cria um arquivo XML com base na estrutura do dicionário de dados selecionado e o baixa em seu computador com o nome &lt;data-dictionary-name>-SampleData. Agora você pode editar esse arquivo em um editor de XML ou texto para fazer entradas de dados enquanto [cria uma carta](/help/forms/using/create-letter.md).

## Internacionalização de metadados {#internationalization-of-meta-data}

Quando quiser enviar a mesma carta em idiomas diferentes para os clientes, poderá localizar o nome de exibição, a descrição e os conjuntos de valores de enumeração do Dicionário de dados e dos Elementos do dicionário de dados.

### Localizar dicionário de dados {#localize-data-dictionary}

1. Na página Dicionários de dados , toque em **Selecionar** e toque em um dicionário de dados para selecioná-lo.
1. Toque em **Baixar dados de localização**.
1. Toque em **OK** no alerta. O Gerenciamento de correspondência baixa um arquivo zip em seu computador com o nome DataDictionary-&lt;DDname>.zip.
1. O arquivo Zip contém um arquivo .properties . Esse arquivo define o dicionário de dados baixado. O conteúdo do arquivo de propriedade é semelhante ao seguinte:

   ```
   #Wed May 20 16:06:23 BST 2015
   DataDictionary.EmployeeDD.description=
   DataDictionary.EmployeeDD.displayName=EmployeeDataDictionary
   DataDictionaryElement.name.description=
   DataDictionaryElement.name.displayName=name
   DataDictionaryElement.person.description=
   DataDictionaryElement.person.displayName=person
   ```

   A estrutura do arquivo de propriedades define uma linha cada para a descrição e o nome de exibição do dicionário de dados e cada elemento de dicionário de dados no dicionário de dados. Além disso, o arquivo de propriedades define uma linha para um valor enum definido para cada elemento de dicionário de dados. Como ocorre com um dicionário de dados, o arquivo de propriedades correspondente pode ter várias definições de elementos do dicionário de dados. Além disso, o arquivo pode conter as definições de um ou mais conjuntos de valores de enumeração.

1. Para atualizar o arquivo .properties em um local diferente, atualize o nome de exibição e os valores de descrição no arquivo. Crie mais instâncias do arquivo para cada idioma que deseja localizar. Somente os idiomas francês, alemão, japonês e inglês são compatíveis.

1. Salve os diferentes arquivos de propriedades atualizados com os seguintes nomes:

   _fr_FR.properties Francês

   _de_DE.properties Alemão

   _ja_JA.properties Japonês

   _en_EN.properties Inglês

1. Arquive o arquivo .properties (ou arquivos de várias localidades) em um único arquivo .zip.

1. Na página Dicionários de dados , selecione **Mais** > **Fazer upload de dados de localização** e selecione o arquivo zip com arquivos de propriedades localizados.
1. Para exibir as alterações de localização, altere o local do navegador.

## Validações do Dicionário de dados {#ddvalidations}

O Editor de dicionário de dados impõe as seguintes validações ao criar ou atualizar um dicionário de dados.

* Somente o tipo composto é permitido como Elemento de nível superior em um dicionário de dados.
* Não são permitidos elementos compósitos e Coleção no nível da folha. Somente elementos primitivos (cadeia de caracteres, data, número, booleano) são permitidos no nível da folha. Essa validação garante que não haja nenhum elemento composto e de coleção sem um DDE filho.
* Ao fazer upload de um arquivo XSD para criar um dicionário de dados, o Editor de dicionário de dados solicita um elemento de nível superior, se houver vários, para criar o dicionário de dados.
* O nome é o único parâmetro necessário para um dicionário de dados.
* Um DDE pai (composto) não pode ter dois filhos com o mesmo nome
* Garante que um DDE seja marcado como computado, somente se não for um parâmetro obrigatório. Um elemento necessário não pode ser calculado e um elemento calculado não pode ser necessário. Além disso, Coleção e Elemento composto não podem ser elementos calculados.
* Garante que um DDE seja marcado como obrigatório, somente quando não for calculado. Também garante que não seja o &quot;collectionElement&quot; que indica o tipo de Collection (que são os únicos filhos de um Elemento de coleção).
* Chaves vazias ou chaves Duplicate não são permitidas em ExtendedProperties para um dicionário de dados ou DDE.
* Não use os caracteres de dois pontos(:) ou barra vertical(|) dentro da chave ou do valor de uma propriedade estendida. Não há validação para usar esses caracteres proibidos.

Validações aplicadas no nível do dicionário de dados

* O nome do Dicionário de dados não deve ser nulo.
* O nome do Dicionário de dados deve conter somente caracteres alfanuméricos.
* A lista de elementos filho no Dicionário de dados não deve ser nula ou vazia.
* O Dicionário de dados não deve conter mais de um Elemento de dicionário de dados de nível superior.
* Somente o tipo composto é permitido como Elemento de nível superior em um Dicionário de dados.

Validações aplicadas no Nível de elemento do dicionário de dados.

* Todos os nomes DDE não devem ser nulos e não devem conter espaços.
* Todos os DDEs devem ter um tipo de elemento &quot;não nulo/não nulo&quot;.
* Todos os nomes de referência DDE não devem ser nulos.
* Todos os nomes de referência DDE devem ser exclusivos.
* Todas as referências de DDE devem conter apenas caracteres alfanuméricos e &quot;_&quot;.
* Todos os nomes para exibição de DDE devem conter somente caracteres alfanuméricos e &quot;_&quot;.
* Não são permitidos elementos compósitos e Coleção no nível da folha. Somente elementos primitivos (cadeia de caracteres, data, número, booleano) são permitidos no nível da folha. Essa validação garante que não haja nenhum elemento composto e de coleção sem um DDE filho.
* Um DDE pai composto não deve ter dois elementos filho com o mesmo nome.
* O subtipo ENUM é usado apenas para elementos String e Number.
* Não é possível calcular elementos de coleção e composto.
* Um DDE não pode ser calculado e obrigatório.
* Os DDEs calculados devem conter uma expressão válida.
* Os DDEs calculados não devem ter vínculo XML.
* Um DDE que indica o tipo para um DDE de coleção não pode ser calculado ou obrigatório.
* Os DDEs do subtipo ENUM não devem conter conjuntos de valores nulos ou vazios.
* O vínculo XML de um DDE de coleção não deve mapear para um atributo.
* A sintaxe de vínculo XML deve ser válida, como, por exemplo, apenas um @ aparece, o @ só é permitido quando seguido por um nome de atributo.

## Mapeamento de elementos do dicionário de dados para o esquema XML {#mappingddetoschema}

Você pode criar um dicionário de dados a partir de um Esquema XML ou criá-lo usando a interface do usuário do Dicionário de dados. Todos os Elementos do dicionário de dados (DDEs) em um dicionário de dados têm um campo Vínculo XML para armazenar o vínculo do DDE a um elemento no esquema XML. O vínculo em cada DDE é relativo ao DDE pai.

Os detalhes a seguir incluem modelos de amostra e amostras de código que mostram detalhes de implementação do Dicionário de dados.

## Mapeamento de elementos simples (primitivos) {#mapping-simple-primitive-elements}

Um DDE primitivo representa um campo ou atributo que é de natureza atômica. Os DDEs primitivos definidos fora do escopo de um tipo complexo (DDE composto) ou de um elemento repetitivo (DDE de coleção) podem ser armazenados em qualquer local dentro do Esquema XML. A localização dos dados correspondentes a um DDE primitivo não depende do mapeamento do DDE pai. O DDE primitivo usa as informações de mapeamento do campo Vínculo XML para determinar seu valor e os mapeamentos são traduzidos em um dos seguintes:

* um atributo
* um elemento
* um contexto de texto
* nada (um DDE ignorado)

O exemplo a seguir mostra um schema simples.

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<xs:schema xmlns:xs="https://www.w3.org/2001/XMLSchema"> 
  <xs:element name='age' type='integer'/> 
  <xs:element name='price' type='decimal'/> 
</xs:schema>
```

| **Elemento do dicionário de dados** | **Vínculo XML padrão** |
|---|---|
| age | /age |
| preço | /preço |

### Mapeamento de elementos compostos {#mapping-composite-elements}

O vínculo não é suportado para elementos Compostos, se o vínculo for fornecido, ele será ignorado. A ligação para todos os DDEs filhos constituintes de tipo primitivo deve ser absoluta. Permitir o mapeamento absoluto para elementos filho de um DDE composto fornece mais flexibilidade em termos de Vínculo XPath. Mapear um DDE composto para um elemento de tipo complexo no esquema XML limita o escopo do vínculo para seus elementos filho.

O exemplo a seguir mostra o esquema de uma nota.

```xml
<xs:element name="note"> 
    <xs:complexType> 
        <xs:sequence> 
            <xs:element name="to" type="xs:string"/> 
            <xs:element name="from" type="xs:string"/> 
            <xs:element name="heading" type="xs:string"/> 
            <xs:element name="body" type="xs:string"/> 
        </xs:sequence> 
    </xs:complexType> 
</xs:element> 
```

<table> 
 <tbody> 
  <tr> 
   <td><strong>Elemento do dicionário de dados</strong></td> 
   <td><strong>Vínculo XML padrão</strong></td> 
  </tr> 
  <tr> 
   <td>observação</td> 
   <td>empty(null)<br /> </td> 
  </tr> 
  <tr> 
   <td>para</td> 
   <td>/note/to</td> 
  </tr> 
  <tr> 
   <td>de</td> 
   <td>/note/from</td> 
  </tr> 
  <tr> 
   <td>cabeçalho</td> 
   <td>/nota/cabeçalho</td> 
  </tr> 
  <tr> 
   <td>corpo</td> 
   <td>/nota/corpo</td> 
  </tr> 
 </tbody> 
</table>

### Mapeamento de elementos de coleção {#mapping-collection-elements}

Um elemento de coleção só é mapeado para outro elemento de coleção que tenha cardinalidade > 1. Os DDEs filho de uma coleção DDE têm Vínculo XML relativo (local) em relação ao Vínculo XML do pai. Como os DDEs filhos de um elemento de coleção devem ter a mesma cardinalidade que os pais, a vinculação relativa é mandada para garantir a restrição de cardinalidade para que os DDEs filhos não apontem para um elemento Esquema XML não repetitivo. No exemplo abaixo, a cardinalidade de &quot;TokenID&quot; deve ser igual a &quot;Tokens&quot;, que é sua coleção pai DDE.

Ao mapear um DDE de coleção para um elemento de Esquema XML:

* o vínculo para o DDE correspondente ao elemento Collection deve ser o XPath absoluto

* Não forneça nenhum vínculo para o DDE que representa o tipo de elemento Collection . Se fornecido, o vínculo será ignorado.

* O vínculo para todos os DDEs filhos do elemento Collection deve ser relativo ao elemento primário Collection.

O Esquema XML abaixo declara um elemento com o nome Tokens e um atributo maxOccurs de &quot;não limitado&quot;. Assim, Tokens é um elemento de coleção.

```xml
<?xml version="1.0" encoding="utf-8"?> 
<Root> 
  <Tokens> 
    <TokenID>string</TokenID> 
    <TokenText> 
      <TextHeading>string</TextHeading> 
      <TextBody>string</TextBody> 
    </TokenText> 
  </Tokens> 
  <Tokens> 
    <TokenID>string</TokenID> 
    <TokenText> 
      <TextHeading>string</TextHeading> 
      <TextBody>string</TextBody> 
    </TokenText> 
  </Tokens> 
  <Tokens> 
    <TokenID>string</TokenID> 
    <TokenText> 
      <TextHeading>string</TextHeading> 
      <TextBody>string</TextBody> 
    </TokenText> 
  </Tokens> 
</Root> 
```

O Token.xsd associado a esta amostra seria:

```xml
<xs:element name="Root"> 
  <xs:complexType> 
    <xs:sequence> 
      <xs:element name="Tokens" type="TokenType" maxOccurs="unbounded"/> 
    </xs:sequence> 
  </xs:complexType> 
</xs:element> 
  
<xs:complexType name="TokenType"> 
  <xs:sequence> 
    <xs:element name="TokenID" type="xs:string"/> 
    <xs:element name="TokenText"> 
      <xs:complexType> 
        <xs:sequence> 
          <xs:element name="TextHeading" type="xs:string"/> 
          <xs:element name="TextBody" type="xs:string"/> 
        </xs:sequence> 
      </xs:complexType> 
    </xs:element> 
  </xs:sequence> 
</xs:complexType>
```

| **Elemento do dicionário de dados** | **Vínculo XML padrão** |
|---|---|
| Raiz | empty(null) |
| Tokens | /Raiz/Tokens |
| Composto | empty(null) |
| TokenID | TokenID |
| TokenText | empty(null) |
| TokenTitle | TokenText/TextCabeçalho |
| TokenBody | TokenText/TextBody |

