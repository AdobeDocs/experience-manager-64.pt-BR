---
title: Criação de formulários adaptáveis usando o esquema JSON
seo-title: Criação de formulários adaptáveis usando o esquema JSON
description: 'Os formulários adaptáveis podem usar o esquema JSON como modelo de formulário, permitindo aproveitar os esquemas JSON existentes para criar formulários adaptáveis. '
seo-description: 'Os formulários adaptáveis podem usar o esquema JSON como modelo de formulário, permitindo aproveitar os esquemas JSON existentes para criar formulários adaptáveis. '
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
feature: Formulários adaptáveis
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 4%

---


# Criação de formulários adaptáveis usando o esquema JSON {#creating-adaptive-forms-using-json-schema}

## Pré-requisitos {#prerequisites}

A criação de um formulário adaptável usando um Esquema JSON como seu modelo de formulário requer compreensão básica do Esquema JSON. É recomendável ler o seguinte conteúdo antes deste artigo.

* [Criação de um formulário adaptável](/help/forms/using/creating-adaptive-form.md)
* [Esquema JSON](https://json-schema.org/)

## Uso de um Esquema JSON como modelo de formulário {#using-a-json-schema-as-form-model}

O AEM Forms suporta a criação de um formulário adaptável usando um Esquema JSON existente como o modelo de formulário. Esse Esquema JSON representa a estrutura na qual os dados são produzidos ou consumidos pelo sistema de back-end na organização. O Esquema JSON que você usa deve ser compatível com [v4 Specification](https://json-schema.org/draft-04/schema).

Os principais recursos do uso de um Esquema JSON são:

* A estrutura do JSON é exibida como uma árvore na guia Localizador de conteúdo no modo de criação de um formulário adaptável. Você pode arrastar e adicionar elemento da hierarquia JSON ao formulário adaptável.
* É possível preencher previamente o formulário usando JSON compatível com o schema associado.
* Ao enviar, os dados inseridos pelo usuário são enviados como JSON que se alinha ao schema associado.

Um Esquema JSON consiste em tipos de elementos simples e complexos. Os elementos têm atributos que adicionam regras ao elemento. Quando esses elementos e atributos são arrastados para um formulário adaptável, eles são mapeados automaticamente para o componente de formulário adaptável correspondente.

Esse mapeamento de elementos JSON com componentes de formulário adaptáveis é o seguinte:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Elemento, propriedades ou atributos JSON</strong></th> 
   <th><strong>Componente de formulário adaptável</strong></th> 
  </tr> 
  <tr> 
   <td><p>Propriedades de string com a restrição enum e enumNames.</p> <p>Sintaxe,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td><p>Componente suspenso:</p> 
    <ul> 
     <li>Os valores listados em enumNames são exibidos na caixa suspensa.</li> 
     <li>Os valores listados no enum são usados para o cálculo.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Propriedade String com restrição de formato. Por exemplo, email e data.</p> <p>Sintaxe,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>O componente de email é mapeado quando o tipo é string e o formato é email.</li> 
     <li>O componente de caixa de texto com validação é mapeado quando o tipo é string e o formato é nome do host.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Campo de texto<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade number<br /> </td> 
   <td>Campo numérico com subtipo definido para float<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade integer<br /> </td> 
   <td>Campo numérico com subtipo definido como integer<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade booleana<br /> </td> 
   <td>Alternar<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade de objeto<br /> </td> 
   <td>Painel<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade array</td> 
   <td>Painel repetível com mín. e máx. iguais a minItems e maxItems, respectivamente. Somente arrays homogêneos são compatíveis. Portanto, a restrição de itens deve ser um objeto e não uma matriz.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Propriedades comuns do schema {#common-schema-properties}

O Formulário adaptável usa as informações disponíveis no Esquema JSON para mapear cada campo gerado. Em especial:

* A propriedade title serve como rótulo para os componentes de formulário adaptáveis.
* A propriedade description é definida como descrição longa para um componente de formulário adaptável.
* A propriedade padrão serve como valor inicial de um campo de formulário adaptável.
* A propriedade maxLength é definida como atributo maxlength do componente de campo de texto.
* As propriedades mínima, máxima, exclusivaMinimum e exclusivaMaximum são usadas para o componente Caixa numérica .
* Para oferecer suporte ao intervalo do componente DatePicker, são fornecidas propriedades adicionais do Esquema JSON minDate e maxDate.
* As propriedades minItems e maxItems são usadas para restringir o número de itens/campos que podem ser adicionados ou removidos de um componente de painel.
* A propriedade readOnly define o atributo somente leitura de um componente de formulário adaptável.
* A propriedade necessária marca o campo do formulário adaptável como obrigatório, enquanto no caso de painel (onde o tipo é objeto), os dados JSON enviados finais têm campos com valor vazio correspondente a esse objeto.
* A propriedade pattern é definida como o padrão de validação (expressão regular) em forma adaptável.
* A extensão do arquivo Esquema JSON deve ser mantida .schema.json. Por exemplo, &lt;filename>.schema.json.

## Exemplo de esquema JSON {#sample-json-schema}

Aqui está um exemplo de um Esquema JSON.

```
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Definições de esquema reutilizáveis {#reusable-schema-definitions}

As chaves de definição são usadas para identificar esquemas reutilizáveis. As definições de esquema reutilizáveis são usadas para criar fragmentos. É semelhante a identificar tipos complexos no XSD. Um exemplo de Esquema JSON com definições é fornecido abaixo:

```
{
  "$schema": "https://json-schema.org/draft-04/schema#",
 
  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },
 
  "type": "object",
 
  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

O exemplo acima define um registro de cliente, em que cada cliente tem um endereço de envio e de faturamento. A estrutura de ambos os endereços é a mesma — os endereços têm um endereço de rua, cidade e estado — portanto, é uma boa ideia não duplicar os endereços. Também facilita a adição e exclusão de campos para qualquer alteração futura.

## Pré-configuração de campos na Definição de esquema JSON {#pre-configuring-fields-in-json-schema-definition}

Você pode usar a propriedade **aem:afProperties** para pré-configurar o campo Esquema JSON para mapear para um componente de formulário adaptável personalizado. Um exemplo é listado abaixo:

```
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Limitar valores aceitáveis para um componente de formulário adaptável {#limit-acceptable-values-for-an-adaptive-form-component}

Você pode adicionar as seguintes restrições aos elementos do Esquema JSON para limitar os valores aceitáveis para um componente de formulário adaptável:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Propriedade do esquema</strong></p> </td> 
   <td><p><strong>Tipo de dados</strong></p> </td> 
   <td><p><strong>Descrição</strong></p> </td> 
   <td><p><strong>Componente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>maximum</code></p> </td> 
   <td><p>Sequência de caracteres</p> </td> 
   <td><p>Especifica o limite superior para valores numéricos e datas. Por padrão, o valor máximo é incluído.</p> </td> 
   <td> 
    <ul> 
     <li>Caixa numérica</li> 
     <li>Escalonador Numérico<br /> </li> 
     <li>Seletor de datas</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minimum</code></p> </td> 
   <td><p>Sequência de caracteres</p> </td> 
   <td><p>Especifica o limite inferior para valores numéricos e datas. Por padrão, o valor mínimo é incluído.</p> </td> 
   <td> 
    <ul> 
     <li>Caixa numérica</li> 
     <li>Escalonador Numérico</li> 
     <li>Seletor de datas</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMaximum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Se verdadeiro, o valor numérico ou a data especificada no componente do formulário deve ser menor que o valor numérico ou a data especificada para a propriedade máxima.</p> <p>Se falso, o valor numérico ou a data especificada no componente do formulário deve ser menor ou igual ao valor numérico ou à data especificada para a propriedade maximum .</p> </td> 
   <td> 
    <ul> 
     <li>Caixa numérica</li> 
     <li>Escalonador Numérico</li> 
     <li>Seletor de datas</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMinimum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Se verdadeiro, o valor numérico ou a data especificada no componente do formulário deve ser maior que o valor numérico ou a data especificada para a propriedade mínima.</p> <p>Se falso, o valor numérico ou a data especificada no componente do formulário deve ser maior ou igual ao valor numérico ou à data especificada para a propriedade mínima.</p> </td> 
   <td> 
    <ul> 
     <li>Caixa numérica</li> 
     <li>Escalonador Numérico</li> 
     <li>Seletor de datas</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minLength</code></p> </td> 
   <td><p>Sequência de caracteres</p> </td> 
   <td><p>Especifica o número mínimo de caracteres permitidos em um componente. O comprimento mínimo deve ser igual ou superior a zero.</p> </td> 
   <td> 
    <ul> 
     <li>Caixa de texto</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>maxLength</code></td> 
   <td>Sequência de caracteres</td> 
   <td>Especifica o número máximo de caracteres permitidos em um componente. O comprimento máximo deve ser igual ou superior a zero.</td> 
   <td> 
    <ul> 
     <li>Caixa de texto</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>Sequência de caracteres</p> </td> 
   <td><p>Especifica a sequência de caracteres. Um componente aceita os caracteres se eles estiverem em conformidade com o padrão especificado.</p> <p>A propriedade pattern mapeia para o padrão de validação do componente de formulário adaptável correspondente.</p> </td> 
   <td> 
    <ul> 
     <li>Todos os componentes de formulários adaptáveis que estão mapeados para um esquema XSD </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Sequência de caracteres</td> 
   <td>Especifica o número máximo de itens em uma matriz. Os itens máximos devem ser iguais ou maiores que zero.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Sequência de caracteres</td> 
   <td>Especifica o número mínimo de itens em uma matriz. Os itens mínimos devem ser iguais ou maiores que zero.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## Construções não suportadas {#non-supported-constructs}

Os formulários adaptáveis não são compatíveis com as seguintes construções do Esquema JSON:

* Tipo nulo
* Tipos de União como qualquer, e
* OneOf, AnyOf, AllOf e NOT
* Somente arrays homogêneos são compatíveis. Portanto, a restrição de itens deve ser um objeto e não uma matriz.

## Perguntas frequentes {#frequently-asked-questions}

**Por que não consigo arrastar elementos individuais de um subformulário (estrutura gerada de qualquer tipo complexo) para subformulários repetíveis (os valores minOccours ou maxOccurs são maiores que 1)?**

Em um subformulário repetível, é necessário usar o subformulário completo. Se quiser apenas campos seletivos, use toda a estrutura e exclua os não desejados.

**Tenho uma estrutura complexa longa no Localizador de conteúdo. Como posso encontrar um elemento específico?**

Você tem duas opções:

* Rolar pela estrutura de árvore
* Use a caixa Pesquisar para localizar um elemento

