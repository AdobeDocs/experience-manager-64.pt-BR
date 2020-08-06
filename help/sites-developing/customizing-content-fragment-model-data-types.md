---
title: NÃO PUBLICAR, MAS NÃO DELETE Personalizar tipos de dados para modelos de fragmento de conteúdo
seo-title: Personalização de tipos de dados para modelos de fragmento de conteúdo
description: Os tipos de dados usados em Modelos de fragmento de conteúdo podem ser personalizados.
seo-description: Os tipos de dados usados em Modelos de fragmento de conteúdo podem ser personalizados.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# NÃO PUBLICAR, MAS NÃO DELETE Personalizar tipos de dados para modelos de fragmento de conteúdo{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Os fragmentos](/help/assets/content-fragments.md) de conteúdo são baseados em modelos [de fragmento de](/help/assets/content-fragments-models.md)conteúdo. Esses modelos são construídos a partir de [elementos](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) de diferentes tipos de dados.

Vários tipos de dados estão disponíveis prontamente, incluindo texto de uma única linha, rich text de várias linhas, campos numéricos, seletores booleanos, opções de menu suspenso, data e hora e outros. AEM usuários podem selecionar tipos de dados com base no propósito editorial dos fragmentos correspondentes. Isso permite que você atenda a modelos de texto simples até modelos complexos com vários tipos diferentes de conteúdo, e à experiência associada de criação de fragmentos.

Os tipos de dados são definidos por uma [combinação de propriedades](#properties) de nós mantidas em locais [específicos no repositório](#locations-in-the-repository). Você também pode criar seus próprios tipos [de](#creating-your-data-type) dados e [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Locais no repositório {#locations-in-the-repository}

Todos os tipos de dados prontos para uso são declarados em:

`/libs/settings`

Você pode adicionar novos tipos de dados sobrepondo a estrutura do nó da seguinte maneira em `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Você não deve alterar nada no `/libs` caminho.
>
>Qualquer coisa que possa mudar na próxima atualização ou na instalação de um serviço ou pacote de correções.

## Propriedades {#properties}

As propriedades do nó são usadas para definir os tipos de dados:

* [Propriedades de tipos de dados](#data-type-properties)
* e dentro desses [fieldProperties](#fieldproperties)

### Propriedades do tipo de dados {#data-type-properties}

Todos os tipos de dados são representados em uma estrutura de nó como em:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Cada nó em `/items` tem propriedades que definem como esse tipo de dados deve ser representado dentro do editor de modelo.

Todas as seguintes propriedades devem estar presentes para que o tipo de dados esteja presente no editor de modelo:

* `fieldIcon`

   [Ícone](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) CoralUI para representar o tipo de dados na interface do editor de modelo.

* ` [fieldProperties](#fieldproperties)`

   Uma matriz que representa as propriedades de configuração para cada tipo de dados.

* `fieldResourceType`

   O tipo de recurso Sling usado para renderizar o tipo de dados em um fragmento de conteúdo. Para tipos de dados que podem ser renderizados de maneiras diferentes (por exemplo, como entrada de texto simples e/ou entrada de texto de várias linhas), essa propriedade deve ser criada como uma matriz, contendo todos os tipos de recursos. A `renderasfield` propriedade será adicionada automaticamente `fieldProperties` para permitir que o usuário escolha o tipo de recurso que precisa adicionar ao modelo,

* `fieldPropResourceType`

   O tipo de recurso Sling usado para renderizar a propriedade padrão para o tipo de dados.

   Por exemplo, para o tipo de dados:

   * Texto de linha única, o `fieldPropResourceType` seria um `textfield` componente
   * Booliano, o `fieldPropResourceType` seria um `checkbox` componente

* `fieldViewResourceType`

   O tipo de recurso Sling usado para renderizar o tipo de dados na pré-visualização, ao construir o modelo. Quando o usuário arrasta o tipo de dados para o lado esquerdo do editor de modelo, a `fieldViewResourceType` propriedade representa o componente que é renderizado lá. Isso é usado para casos em que você não deseja renderizar o componente completo, mas apenas renderizar um substituto que minimize a sobrecarga para o editor de modelo.

* `fieldTitle`

   Propriedade que define o título desse tipo de dados. Por exemplo, texto **de linha** única para um `textfield` componente, texto **de** várias linhas para um componente de vários campos.

* `valueType`

   Esse é o tipo de valor que o tipo de dados retorna quando é armazenado internamente. Consulte [Mapeamentos](#mappings).

* `renderType`

   Esta é uma representação interna do tipo de dados. Ele conecta o componente `valueType` a uma interface do usuário. Consulte [Mapeamentos](#mappings).

* `listOrder`

   Cada tipo de dados precisa de um valor que represente sua ordem na lista. Isso é usado para garantir a ordem correta dos vários campos (adicionados/movidos por arrastar e soltar) ao salvar o editor de modelo. Esse valor deve ser um número inteiro e é recomendável atribuir o número de forma crescente e ordenada. Ao criar um novo tipo de dados, é melhor atribuir o valor com base no último tipo de dados na lista (o valor mais alto do `listOrder` valor presente nos tipos de dados).

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
   <td>string</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Texto multilinha</td> 
   <td>string, com tipo de conteúdo<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Número (inteiro/longo)<br /> </td> 
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
   <td>boolean</td> 
   <td>boolean</td> 
  </tr> 
  <tr> 
   <td>Data e hora</td> 
   <td>calendário</td> 
   <td>time</td> 
  </tr> 
  <tr> 
   <td>Enumeração</td> 
   <td>string/long</td> 
   <td>lista discriminada</td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>string</td> 
   <td>tags</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alguns tipos (por exemplo, `string`, `long`, entre outros) podem ter vários valores. Nesse caso, o componente usado para renderização e edição normalmente é encapsulado por um componente de vários campos ( `granite/ui/components/coral/foundation/form/multifield`). A exceção são tags, nas quais o componente de edição é responsável pela renderização correta.

### fieldProperties {#fieldproperties}

As propriedades de configuração para cada tipo de dados. Valores para `fieldProperties`:

* `base`

   Esta é a base para todos os `fieldProperties` componentes. A definição situa-se em `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Ele contém a variável `fieldRoot`, que `fieldProperties` pode ser usada posteriormente ao criar entradas para recuperar o caminho correto.

   Exemplo: para obter o caminho correto para um Rótulo **de** campo, você precisará da chave para identificar o componente ao qual ele pertence, a entrada desse campo deve ser `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Esse componente adiciona a caixa de seleção padrão para o tipo de `Boolean` dados, bem como os parâmetros Sling `checked@Delete` e `checked@TypeHint`.

* `datepickerfields`

   Componente que adiciona as entradas ocultas necessárias para que o componente do seletor de datas funcione. Inclui a criação das propriedades `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`e `minDate` `maxDate`.

* `datetimepickerfields`

   Isso adiciona um campo selecionado para o tipo de `Date&Time` dados para distinguir entre `Date` e `Date&Time` opções.

* `datevaluefield`

   Isso adiciona um datepicker às propriedades, para que um usuário possa selecionar um padrão para o tipo de `Date&Time` dados.

* `descriptionfield`

   Este componente adiciona um campo de texto de várias linhas que representa a descrição do componente atualmente selecionado no editor de várias linhas. Ela é adicionada automaticamente pelo renderizador do Editor de modelos no final de cada propriedade de tipo de dados.

* `labelfield`

   Componente que adiciona uma `textfield` entrada que adiciona o rótulo do campo para um tipo de dados que pode ter rótulos de campo.

* `maptopropertyfield`

   Esse componente adiciona o `Name` campo nas propriedades, dando um identificador ao componente selecionado de um tipo de dados. Deve estar presente em todos os tipos de dados.

* `maxlengthfield`

   Ela é usada para adicionar a `maxLength` propriedade para uso com tipos de dados que aceitam essa propriedade. Por exemplo, com Texto **de linha**&#x200B;única, **Número** etc.

* `multieditorfield`

   Isso adiciona todo o campo oculto necessário para que o editor de várias linhas funcione, que é representado pelo tipo de dados Texto **de** várias linhas.

* `mvfields`

   Componente que adiciona todos os campos ocultos necessários para que um componente de vários campos funcione. Por exemplo, para a segunda opção de um tipo de dados de Texto **de linha** única. Isso deve ser adicionado para qualquer componente que seja renderizado como um multicampo.

* `numbertypefield`

   Selecione a opção para o tipo de dados **Número** que seleciona entre **Inteiro** ou **Fração** para o tipo de dados **Número** .

* `numbervaluefield`

   Um seletor de valor `numberfield` padrão para o **Número** `type.options` Isso adiciona as opções de entrada para o tipo de dados de **Lista discriminada** , que é usado para determinar os valores para o componente de caixa de seleção.

* `placeholderfield`

   Este é um campo de texto que atua como a entrada para a `emptyText` propriedade de um componente. Isso deve ser usado por todos os tipos de dados que aceitam um espaço reservado (o que não é muito complicado); por exemplo, Texto **de linha**&#x200B;única, **Número** etc.).

* `renderasfield`

   Esse é o componente que é renderizado automaticamente quando vários `fieldResourceTypes` estão presentes na propriedade do nó do tipo de dados.

* `requiredfield`

   Esta é uma caixa de seleção que representa a `required` propriedade de um componente. Como a maioria dos componentes aceita o `required` campo, esse campo pode ser usado para a maioria dos tipos de dados.

* `tagsfields`

   Componentes que adicionam as entradas necessárias para que um `tagfield` componente seja renderizado, usados pelo tipo de dados **Tags** .

* `tagsroot`

   Um seletor de caminho usado pelo tipo de dados **Tags** para definir o caminho raiz para o `tagsfield` componente.

* `textfield`

   Usado pelo tipo de `Boolean` dados para definir o rótulo do campo da caixa de seleção definida por esse tipo de dados.

* `textvaluefield`

   A propriedade de valor padrão para o tipo de dados Texto **de linha** única.

## Criação de seu tipo de dados {#creating-your-data-type}

Para criar seu próprio tipo de dados, é necessário:

* [Criar a estrutura do nó](#creating-the-node-structure)
* [Definir as propriedades para seu tipo de dados](#defining-the-properties-for-your-data-type)

Você pode então [usar seu tipo](#using-your-data-type)de dados.

Você também pode [criar seu próprio `fieldProperties`](#creating-your-own-fieldproperties-property).

### Criação da estrutura do nó {#creating-the-node-structure}

A estrutura do nó deve ser criada `/apps` para sobrepor os tipos de dados. Se ele ainda não existir, é necessário criar:

1. Se ele ainda não existir, é necessário criar:

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
   >`/apps/settings/dam` já deveria existir.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` pode precisar ser criado com os tipos de nó especificados.

1. Em `/items` você pode adicionar novos nós para representar seus novos tipos de dados:

   * Tipo de nó: `nt:unstructured`
   * &quot;Propriedades: consulte [Definição das propriedades para seu tipo de dados](#defining-the-properties-for-your-data-type)

### Definição das propriedades para seu tipo de dados {#defining-the-properties-for-your-data-type}

1. Determine os valores para as seguintes propriedades [de tipo de](#data-type-properties) dados que são necessários para o seu tipo de dados:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Eles definem como os componentes para seu tipo de dados serão renderizados. Podem ser qualquer componente; incluindo seus próprios componentes personalizados (requer um conjunto correspondente de ` [fieldProperties](#fieldproperties)`).

   Defina essas propriedades, com os valores adequados, no nó para o seu tipo de dados.

1. Determine o que ` [fieldProperties](#fieldproperties)` será usado. Isso depende dos atributos ou propriedades que você `fieldResourceType` precisa.

   Por exemplo, um `granite/ui/components/coral/foundation/form/textfield`deve ter um Nome **de** rótulo, um Comprimento **** máximo, um Texto **de** espaço reservado e uma propriedade Valor **** padrão.

   Você pode escolher dentre as [fieldProperties](#fieldproperties)predefinidas ou [criar suas próprias propriedades](#creating-your-own-fieldproperties-property).

   Defina essas propriedades, com os valores adequados, no nó para o seu tipo de dados.

1. Determine os valores para as seguintes propriedades [de tipo de](#data-type-properties)dados:

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Defina essas propriedades, com os valores adequados, no nó para o seu tipo de dados.

### Como usar seu tipo de dados {#using-your-data-type}

Depois de salvar essa estrutura de nó, com todas as propriedades aplicadas, você pode abrir qualquer modelo com o editor de modelo e ver e usar seu novo tipo de dados.

## Criando sua própria propriedade fieldProperties {#creating-your-own-fieldproperties-property}

Você pode escolher dentre as [fieldProperties](#fieldproperties)predefinidas ou criar suas próprias:

1. Crie um componente em:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Se o caminho não existir, você poderá criá-lo usando `nt:folder` nós.

   1. Para ter acesso às variáveis, este componente deve estender:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. O componente deve poder ser incluído por meio de:

      `sling:include`

   1. Esse componente deve renderizar um campo (se um usuário precisar inserir dados) ou uma entrada oculta com as propriedades necessárias ao seu tipo de dados. Por exemplo, um componente de vários campos requer um nó filho com o tipo de campo que deve ser duplicado, portanto, deve haver uma entrada que possa criar (por meio da mecânica de POST sling) um nó filho de um tipo específico.

1. O nome base deste componente deve ser adicionado ao `fieldProperties`.
1. Repita o procedimento para todas as propriedades necessárias.

