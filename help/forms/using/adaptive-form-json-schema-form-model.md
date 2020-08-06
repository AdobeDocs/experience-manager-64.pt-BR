---
title: Criação de formulários adaptáveis usando o Schema JSON
seo-title: Criação de formulários adaptáveis usando o Schema JSON
description: 'Formulários adaptáveis podem usar o schema JSON como modelo de formulário, permitindo que você aproveite schemas JSON existentes para criar formulários adaptáveis. '
seo-description: 'Formulários adaptáveis podem usar o schema JSON como modelo de formulário, permitindo que você aproveite schemas JSON existentes para criar formulários adaptáveis. '
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 4%

---


# Criação de formulários adaptáveis usando o Schema JSON {#creating-adaptive-forms-using-json-schema}

## Pré-requisitos {#prerequisites}

A criação de um formulário adaptável usando um Schema JSON como seu modelo de formulário requer uma compreensão básica do Schema JSON. É recomendável ler o seguinte conteúdo antes deste artigo.

* [Criação de um formulário adaptável](/help/forms/using/creating-adaptive-form.md)
* [Schema JSON](https://json-schema.org/)

## Uso de um Schema JSON como modelo de formulário  {#using-a-json-schema-as-form-model}

A AEM Forms suporta a criação de um formulário adaptável usando um Schema JSON existente como modelo de formulário. Este Schema JSON representa a estrutura na qual os dados são produzidos ou consumidos pelo sistema de back-end em sua organização. O Schema JSON que você usa deve estar em conformidade com as especificações [](https://json-schema.org/draft-04/schema)v4.

Os principais recursos do uso de um Schema JSON são:

* A estrutura do JSON é exibida como uma árvore na guia Localizador de conteúdo no modo de criação de um formulário adaptável. Você pode arrastar e adicionar elementos da hierarquia JSON ao formulário adaptável.
* É possível pré-preencher o formulário usando JSON compatível com o schema associado.
* No envio, os dados inseridos pelo usuário são enviados como JSON que se alinha ao schema associado.

Um Schema JSON consiste em tipos de elementos simples e complexos. Os elementos têm atributos que adicionam regras ao elemento. Quando esses elementos e atributos são arrastados para um formulário adaptável, eles são mapeados automaticamente para o componente de formulário adaptável correspondente.

Esse mapeamento de elementos JSON com componentes de formulário adaptáveis é o seguinte:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Elemento, propriedades ou atributos JSON</strong></th> 
   <th><strong>Componente de formulário adaptável</strong></th> 
  </tr> 
  <tr> 
   <td><p>Propriedades de string com as restrições enum e enumNames.</p> <p>Sintaxe,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td><p>Componente suspenso:</p> 
    <ul> 
     <li>Os valores listados em enumNames são exibidos na caixa suspensa.</li> 
     <li>Os valores listados na enumeração são usados para o cálculo.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Propriedade String com restrição de formato. Por exemplo, email e data.</p> <p>Sintaxe,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>O componente de email é mapeado quando o tipo é string e o formato é email.</li> 
     <li>O componente da caixa de texto com validação é mapeado quando o tipo é string e o formato é nome do host.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"Tipo": "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Campo de texto<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade number<br /> </td> 
   <td>Campo numérico com subtipo definido como flutuante<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade integer<br /> </td> 
   <td>Campo numérico com subtipo definido como inteiro<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade booleana<br /> </td> 
   <td>Alternar<br /> </td> 
  </tr> 
  <tr> 
   <td>object property<br /> </td> 
   <td>Painel<br /> </td> 
  </tr> 
  <tr> 
   <td>propriedade array</td> 
   <td>Painel repetível com min e max iguais a minItems e maxItems respectivamente. Somente matrizes homogêneas são suportadas. Portanto, a restrição de itens deve ser um objeto e não uma matriz.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Propriedades de schemas comuns {#common-schema-properties}

O Formulário adaptável usa as informações disponíveis no Schema JSON para mapear cada campo gerado. Nomeadamente:

* A propriedade title serve como rótulo para os componentes de formulário adaptáveis.
* A propriedade description é definida como descrição longa para um componente de formulário adaptável.
* A propriedade padrão serve como valor inicial de um campo de formulário adaptável.
* A propriedade maxLength é definida como atributo maxlength do componente de campo de texto.
* As propriedades mínima, máxima, exclusivaMinimum e exclusivaMaximum são usadas para o componente de caixa Numérico.
* Para suportar o intervalo do componente DatePicker, são fornecidas propriedades adicionais do Schema JSON minDate e maxDate.
* As propriedades minItems e maxItems são usadas para restringir o número de itens/campos que podem ser adicionados ou removidos de um componente de painel.
* A propriedade readOnly define o atributo readonly de um componente de formulário adaptável.
* A propriedade necessária marca o campo de formulário adaptável como obrigatório, enquanto no caso de panel (onde type é object), os dados JSON enviados finais têm campos com valor vazio correspondente a esse objeto.
* A propriedade pattern é definida como o padrão de validação (expressão normal) na forma adaptável.
* A extensão do arquivo de Schema JSON deve ser mantida .schema.json. Por exemplo, &lt;nome_do_arquivo>.schema.json.

## Schema JSON de exemplo {#sample-json-schema}

Aqui está um exemplo de um Schema JSON.

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

### Definições de schemas reutilizáveis {#reusable-schema-definitions}

As chaves de definição são usadas para identificar schemas reutilizáveis. As definições de schema reutilizáveis são usadas para criar fragmentos. É semelhante a identificar tipos complexos no XSD. Um exemplo de Schema JSON com definições é fornecido abaixo:

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

O exemplo acima define um registro de cliente, no qual cada cliente tem um endereço de entrega e de cobrança. A estrutura de ambos os endereços é a mesma - os endereços têm endereço, cidade e estado - então é uma boa ideia não duplicado os endereços. Além disso, facilita a adição e exclusão de campos para qualquer alteração futura.

## Pré-configuração de campos na definição de Schema JSON {#pre-configuring-fields-in-json-schema-definition}

Você pode usar a propriedade **aem:afProperties** para pré-configurar o campo de Schema JSON para mapear para um componente de formulário adaptável personalizado. Um exemplo está listado abaixo:

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

É possível adicionar as seguintes restrições aos elementos do Schema JSON para limitar os valores aceitáveis para um componente de formulário adaptável:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> propriedade Schema</strong></p> </td> 
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
   <td><p>Se verdadeiro, o valor numérico ou a data especificada no componente do formulário deve ser menor que o valor numérico ou a data especificada para a propriedade máxima.</p> <p>Se falso, o valor numérico ou a data especificada no componente do formulário deve ser menor ou igual ao valor numérico ou à data especificada para a propriedade máxima.</p> </td> 
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
   <td><p>Especifica a sequência dos caracteres. Um componente aceita os caracteres se eles estiverem em conformidade com o padrão especificado.</p> <p>A propriedade pattern mapeia para o padrão de validação do componente de formulário adaptável correspondente.</p> </td> 
   <td> 
    <ul> 
     <li>Todos os componentes de formulários adaptáveis que estão mapeados para um schema XSD </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Sequência de caracteres</td> 
   <td>Especifica o número máximo de itens em uma matriz. Os itens máximos devem ser iguais ou superiores a zero.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Sequência de caracteres</td> 
   <td>Especifica o número mínimo de itens em uma matriz. Os itens mínimos devem ser iguais ou superiores a zero.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## Construção sem suporte  {#non-supported-constructs}

Os formulários adaptativos não suportam as seguintes construções de Schema JSON:

* Tipo nulo
* tipos de Uniões, como qualquer, e
* OneOf, AnyOf, AllOf e NOT
* Somente matrizes homogêneas são suportadas. Portanto, a restrição de itens deve ser um objeto e não uma matriz.

## Perguntas frequentes {#frequently-asked-questions}

**Por que não consigo arrastar elementos individuais de um subformulário (estrutura gerada a partir de qualquer tipo complexo) para subformulários repetitivos (os valores minOccours ou maxOccurs são maiores que 1)?**

Em um subformulário repetível, é necessário usar o subformulário completo. Se você quiser apenas campos seletivos, use a estrutura inteira e exclua os não desejados.

**Tenho uma estrutura longa e complexa no Localizador de conteúdo. Como posso encontrar um elemento específico?**

Você tem duas opções:

* Percorrer a estrutura em árvore
* Use a caixa Pesquisar para localizar um elemento

