---
title: NÃO PUBLICAR, MAS NÃO DELETE Personalizar tipos de dados para modelos de fragmentos de conteúdo
seo-title: Customizing Data Types for Content Fragment Models
description: Os tipos de dados usados nos Modelos de fragmentos de conteúdo podem ser personalizados.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 1%

---


# NÃO PUBLICAR, MAS NÃO DELETE Personalizar tipos de dados para modelos de fragmentos de conteúdo{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Fragmentos de conteúdo](/help/assets/content-fragments.md) são baseados em [modelos de fragmento de conteúdo](/help/assets/content-fragments-models.md). Esses modelos são criados a partir de [elementos](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de diferentes tipos de dados.

Vários tipos de dados estão disponíveis prontamente, incluindo texto de uma única linha, rich text de várias linhas, campos numéricos, seletores booleanos, opções de menu suspenso, data e hora e outros. AEM usuários podem selecionar tipos de dados com base na intenção editorial dos fragmentos correspondentes. Isso permite que você atenda a modelos de texto simples até modelos complexos com vários tipos diferentes de conteúdo e a experiência de criação de fragmentos associada.

Os tipos de dados são definidos por uma [combinação das propriedades do nó](#properties) detido em [locais específicos no repositório](#locations-in-the-repository). Você também pode criar seu próprio [tipos de dados](#creating-your-data-type) e [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Locais no Repositório {#locations-in-the-repository}

Todos os tipos de dados prontos para uso são declarados em:

`/libs/settings`

Você pode adicionar novos tipos de dados sobrepondo a estrutura do nó da seguinte maneira em `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Você não deve alterar nada na variável `/libs` caminho.
>
>Qualquer coisa pode mudar na próxima atualização ou instalação de um serviço ou pacote de correções.

## Propriedades {#properties}

As propriedades do nó são usadas para definir os tipos de dados:

* [Propriedades de tipos de dados](#data-type-properties)
* e [fieldProperties](#fieldproperties)

### Propriedades do tipo de dados {#data-type-properties}

Todos os tipos de dados são representados em uma estrutura de nó como em:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Cada nó em `/items` O tem propriedades que definem como esse tipo de dados deve ser representado no editor de modelo.

Todas as seguintes propriedades devem estar presentes para que o tipo de dados esteja presente no editor de modelo:

* `fieldIcon`

   [Ícone CoralUI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) para representar o tipo de dados na interface do editor de modelos.

* ` [fieldProperties](#fieldproperties)`

   Uma matriz que representa as propriedades de configuração para cada tipo de dados.

* `fieldResourceType`

   O tipo de recurso Sling usado para renderizar o tipo de dados em um fragmento de conteúdo. Para tipos de dados que podem ser renderizados de diferentes maneiras (por exemplo, como entrada de texto simples e/ou entrada de texto de várias linhas), essa propriedade deve ser criada como uma matriz, contendo todos os tipos de recursos. O `renderasfield` será adicionada automaticamente a `fieldProperties` para permitir que o usuário escolha o tipo de recurso que precisa ser adicionado ao modelo,

* `fieldPropResourceType`

   O tipo de recurso Sling usado para renderizar a propriedade padrão para o tipo de dados.

   Por exemplo, para o tipo de dados:

   * Texto de linha única, a variável `fieldPropResourceType` seria um `textfield` componente
   * Booleano, a variável `fieldPropResourceType` seria um `checkbox` componente

* `fieldViewResourceType`

   O tipo de recurso Sling usado para renderizar o tipo de dados na visualização, ao construir o modelo. Quando o usuário arrasta o tipo de dados para o lado esquerdo do editor de modelo, a variável `fieldViewResourceType` representa o componente que é renderizado lá. Isso é usado para casos em que você não deseja renderizar o componente completo, mas deseja apenas renderizar um substituto que minimize a sobrecarga para o editor de modelo.

* `fieldTitle`

   Propriedade que define o título desse tipo de dados. Por exemplo, **Texto de linha única** para um `textfield` componente, **Texto de várias linhas** para um componente de vários campos.

* `valueType`

   Esse é o tipo de valor que o tipo de dados retorna quando é armazenado internamente. Consulte [Mapeamentos](#mappings).

* `renderType`

   Essa é uma representação interna do tipo de dados. Ele conecta o `valueType` para um componente da interface do usuário. Consulte [Mapeamentos](#mappings).

* `listOrder`

   Cada tipo de dados precisa de um valor que represente sua ordem na lista. Isso é usado para garantir a ordem correta dos vários campos (adicionados/movidos por arrastar e soltar) ao salvar o editor de modelo. Esse valor deve ser um número inteiro, e é recomendável atribuir o número de forma crescente e ordenada. Ao criar um novo tipo de dados, é melhor atribuir o valor com base no último tipo de dados na lista (o valor mais alto de `listOrder` presente nos tipos de dados).

#### Mapeamentos {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>Tipo de dados<br /> </td> 
   <td>Tipo de valor<br /> </td> 
   <td>Tipo de renderização</td> 
  </tr> 
  <tr> 
   <td>Texto em linha única</td> 
   <td>sequência de caracteres</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Texto multilinha</td> 
   <td>string, com tipo de conteúdo<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Number (número inteiro/longo)<br /> </td> 
   <td>long</td> 
   <td>número</td> 
  </tr> 
  <tr> 
   <td>Número (duplo/flutuante)</td> 
   <td>double</td> 
   <td>número</td> 
  </tr> 
  <tr> 
   <td>Booleano</td> 
   <td>booleano</td> 
   <td>booleano</td> 
  </tr> 
  <tr> 
   <td>Data e hora</td> 
   <td>calendário</td> 
   <td>time</td> 
  </tr> 
  <tr> 
   <td>Enumeração</td> 
   <td>string/long</td> 
   <td>enumeração</td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>sequência de caracteres</td> 
   <td>tags</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alguns tipos (por exemplo, `string`, `long`, entre outros) pode ter vários valores. Nesse caso, o componente usado para renderização e edição normalmente é encapsulado por um componente de vários campos ( `granite/ui/components/coral/foundation/form/multifield`). A exceção são tags, onde o componente de edição é responsável pela renderização correta.

### fieldProperties {#fieldproperties}

As propriedades de configuração de cada tipo de dados. Valores para `fieldProperties`:

* `base`

   Esta é a base para todos `fieldProperties` componentes. A definição situa-se no `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Ele contém a variável `fieldRoot`, que posteriormente `fieldProperties` pode usar ao criar entradas para recuperar o caminho correto.

   Exemplo: para obter o caminho correto para um **Rótulo do campo** será necessário a chave para identificar o componente ao qual pertence, a entrada desse campo deve ser `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Esse componente adiciona a caixa de seleção padrão da variável `Boolean` tipo de dados, bem como os parâmetros do Sling `checked@Delete` e `checked@TypeHint`.

* `datepickerfields`

   Componente que adiciona as entradas ocultas necessárias para que o componente do seletor de datas funcione. Inclui a criação das propriedades `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` e `maxDate`.

* `datetimepickerfields`

   Isso adiciona um campo de seleção para `Date&Time` tipo de dados para distinguir entre `Date` e `Date&Time` opções.

* `datevaluefield`

   Isso adiciona um datepicker às propriedades, para que um usuário possa selecionar um padrão para a variável `Date&Time` tipo de dados.

* `descriptionfield`

   Esse componente adiciona um campo de texto de várias linhas que representa a descrição do componente atualmente selecionado no editor de várias linhas. Ele é adicionado automaticamente pelo renderizador do Editor de modelo ao final de cada propriedade de tipo de dados.

* `labelfield`

   Componente que adiciona um `textfield` entrada que adiciona o rótulo do campo para um tipo de dados que pode ter rótulos de campo.

* `maptopropertyfield`

   Esse componente adiciona a variável `Name` nas propriedades, fornecendo um identificador para o componente selecionado de um tipo de dados. Ela deve estar presente em todos os tipos de dados.

* `maxlengthfield`

   É usado para adicionar a variável `maxLength` para uso com tipos de dados que aceitam essa propriedade. Por exemplo, com **Texto de linha única**, **Número**, etc.

* `multieditorfield`

   Isso adiciona todo o campo oculto necessário para que o editor de várias linhas funcione, que é representado pela variável **Texto de várias linhas** tipo de dados.

* `mvfields`

   Componente que adiciona todos os campos ocultos necessários para que um componente de vários campos funcione. Por exemplo, para a segunda opção de um **Texto de linha única** tipo de dados. Isso deve ser adicionado para qualquer componente renderizado como um multicampo.

* `numbertypefield`

   Selecione a opção para o **Número** tipo de dados que seleciona entre **Número inteiro** ou **Fração** para **Número** tipo de dados.

* `numbervaluefield`

   A `numberfield` seletor de valor padrão para o **Número** `type.options` Isso adiciona a entrada de opções para a variável **Enumeração** tipo de dados, usado para determinar os valores do componente de caixa de seleção.

* `placeholderfield`

   Este é um campo de texto que atua como entrada para a variável `emptyText` de um componente. Isso deve ser usado por todos os tipos de dados que aceitam um espaço reservado (o que não é muito complicado; por exemplo **Texto de linha única**, **Número**, etc).

* `renderasfield`

   Este é o componente que é renderizado automaticamente quando vários `fieldResourceTypes` estão presentes na propriedade do nó de tipo de dados .

* `requiredfield`

   Esta é uma caixa de seleção que representa a variável `required` para um componente. Como a maioria dos componentes aceita a variável `required` , esse campo pode ser usado para a maioria dos tipos de dados.

* `tagsfields`

   Componentes que adicionam as entradas necessárias para um `tagfield` componente a ser renderizado, usado pela variável **Tags** tipo de dados.

* `tagsroot`

   Um seletor de caminho usado pela variável **Tags** tipo de dados para definir o caminho raiz para `tagsfield` componente.

* `textfield`

   Usado pela `Boolean` tipo de dados para definir o rótulo do campo da caixa de seleção definida por esse tipo de dados.

* `textvaluefield`

   A propriedade de valor padrão para **Texto de linha única** tipo de dados.

## Criar seu tipo de dados {#creating-your-data-type}

Para criar seu próprio tipo de dados, é necessário:

* [Criar a estrutura do nó](#creating-the-node-structure)
* [Definir as propriedades do tipo de dados](#defining-the-properties-for-your-data-type)

Você pode [usar seu tipo de dados](#using-your-data-type).

Você também pode [crie seu próprio `fieldProperties`](#creating-your-own-fieldproperties-property).

### Criar a estrutura do nó {#creating-the-node-structure}

A estrutura do nó deve ser criada em `/apps` para sobrepor os tipos de dados. Se ainda não existir, você deve criar:

1. Se ainda não existir, você deve criar:

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` já deve existir.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` pode precisar ser criado com os tipos de nó especificados.

1. Em `/items` é possível adicionar novos nós para representar seus novos tipos de dados:

   * Tipo de nó: `nt:unstructured`
   * &quot;Propriedades: see [Definição das propriedades para o tipo de dados](#defining-the-properties-for-your-data-type)

### Definição das propriedades para o tipo de dados {#defining-the-properties-for-your-data-type}

1. Determine os valores para o seguinte [propriedades do tipo de dados](#data-type-properties) que são necessários para o seu tipo de dados:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Eles definem como os componentes do seu tipo de dados serão renderizados. Podem ser qualquer componente; incluindo seus próprios componentes personalizados (é necessário um conjunto correspondente de ` [fieldProperties](#fieldproperties)`).

   Defina essas propriedades, com os valores adequados, no nó para o tipo de dados.

1. Determine o ` [fieldProperties](#fieldproperties)` a ser usado. Isso depende dos atributos ou propriedades que `fieldResourceType` necessidades.

   Por exemplo, um `granite/ui/components/coral/foundation/form/textfield`deve ter uma **Nome do rótulo**, a **Comprimento máximo**, a **Texto de espaço reservado** e **Valor padrão** propriedade.

   Você pode escolher entre [fieldProperties](#fieldproperties)ou [criar suas próprias propriedades](#creating-your-own-fieldproperties-property).

   Defina essas propriedades, com os valores adequados, no nó para o tipo de dados.

1. Determine os valores para o seguinte [propriedades do tipo de dados](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Defina essas propriedades, com os valores adequados, no nó para o tipo de dados.

### Uso do tipo de dados {#using-your-data-type}

Depois de salvar essa estrutura de nó, com todas as propriedades aplicadas, você pode abrir qualquer modelo com o editor de modelo e ver e usar seu novo tipo de dados.

## Criação da sua própria propriedade fieldProperties {#creating-your-own-fieldproperties-property}

Você pode escolher entre [fieldProperties](#fieldproperties)ou criar o seu próprio:

1. Crie um componente em:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Se o caminho não existir, você pode criá-lo usando `nt:folder` nós.

   1. Para ter acesso às variáveis, esse componente deve estender:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. O componente deve poder ser incluído por meio de:

      `sling:include`

   1. Esse componente deve renderizar um campo (se um usuário precisar inserir dados) ou uma entrada oculta com as propriedades necessárias para o tipo de dados. Por exemplo, um componente de vários campos requer um nó filho com o tipo de campo que deve duplicar, portanto, deve haver uma entrada que possa criar (por meio da mecânica do POST sling) um nó filho de um tipo específico.

1. O nome base desse componente deve ser adicionado a `fieldProperties`.
1. Repita o procedimento para todas as propriedades necessárias.

