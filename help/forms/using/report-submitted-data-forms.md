---
title: APIs para trabalhar com formulários enviados no portal de formulários
seo-title: APIs para trabalhar com formulários enviados no portal de formulários
description: 'O AEM Forms fornece APIs que você pode usar para consultar e realizar ações nos dados de formulários enviados no portal de formulários. '
seo-description: 'O AEM Forms fornece APIs que você pode usar para consultar e realizar ações nos dados de formulários enviados no portal de formulários. '
uuid: c47c8392-e5a9-4c40-b65e-4a7f379a6b45
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish, developer-reference
discoiquuid: 9457effd-3595-452f-a976-ad9eda6dc909
feature: Forms Portal
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 7%

---


# APIs para trabalhar com formulários enviados no portal de formulários {#apis-to-work-with-submitted-forms-on-forms-portal}

O AEM Forms fornece APIs que podem ser usadas para consultar dados de formulários enviados pelo portal de formulários. Além disso, você pode postar comentários ou atualizar propriedades de formulários enviados usando as APIs explicadas neste documento.

>[!NOTE]
>
>Os usuários que chamarão as APIs devem ser adicionados ao grupo de revisores, conforme descrito em [Associando revisores de envio a um formulário](/help/forms/using/adding-reviewers-form.md).

## GET /content/forms/portal/submission.review.json?func=getFormsForSubmissionReview {#get-content-forms-portal-submission-review-json-func-getformsforsubmissionreview-br}

Retorna uma lista de todos os formulários elegíveis.

### Parâmetros de URL {#url-parameters}

Essa API não requer parâmetros adicionais.

### Resposta {#response}

O objeto response contém uma matriz JSON que inclui nomes de formulários e seu caminho de repositório. A estrutura da resposta é a seguinte:

```
[
 {formName: "<form name>", 
 formPath: "<path to the form>" }, 
 {.....}, 
 ......]
```

### Exemplo {#example}

**URL da solicitação**

```
https://[host]:[port]/content/forms/portal/submission.review.json?func=getFormsForSubmissionReview
```

**Resposta**

```java
[{"formPath":"/content/dam/formsanddocuments/forms-review/form2","formName":"form2"},{"formPath":"/content/dam/formsanddocuments/forms-review/form1","formName":"form1"}]
```

## GET /content/forms/portal/submission.review.json?func=getAllSubmissions {#get-content-forms-portal-submission-review-json-func-getallsubmissions}

Retorna detalhes de todos os formulários enviados. No entanto, você pode usar parâmetros de URL para limitar os resultados.

### Parâmetros de URL {#url-parameters-1}

Especifique os seguintes parâmetros no URL da solicitação:

<table> 
 <tbody> 
  <tr> 
   <th>Parâmetro</th> 
   <th>Descrição</th> 
  </tr> 
  <tr> 
   <td><code>formPath</code></td> 
   <td>Especifica o caminho do repositório CRX no qual o formulário reside. Se você não especificar o caminho do formulário, ele retornará uma resposta vazia.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>offset</code> (opcional)</td> 
   <td>Especifica o ponto inicial no índice do conjunto de resultados. O valor padrão é <strong>0</strong>.</td> 
  </tr> 
  <tr> 
   <td><code>limit</code> (opcional)</td> 
   <td>Limita o número de resultados. O valor padrão é <strong>30</strong>.</td> 
  </tr> 
  <tr> 
   <td><code>orderby</code> <br /> (opcional)</td> 
   <td>Especifica a propriedade para classificar resultados. O valor padrão é <strong>jcr:lastModified</strong>, que classifica os resultados com base no último horário modificado.</td> 
  </tr> 
  <tr> 
   <td><code>sort</code> <br /> (opcional)</td> 
   <td>Especifica a ordem para classificar resultados. O valor padrão é <strong>desc</strong>, que classifica os resultados em ordem decrescente. Você pode especificar <code>asc</code> para classificar os resultados em ordem crescente.</td> 
  </tr> 
  <tr> 
   <td><code>cutPoints</code> <br /> (opcional)</td> 
   <td>Especifica uma lista separada por vírgulas de propriedades de formulário a serem incluídas nos resultados. As propriedades padrão são:<br /> <code>formName</code>, <code>formPath</code>, <code>submitID</code>, <code>formType</code>, <code>jcr:lastModified</code>, <code>owner</code></td> 
  </tr> 
  <tr> 
   <td><code>search</code> <br /> (opcional)</td> 
   <td>Pesquisa o valor especificado nas propriedades do formulário e retorna formulários com valores correspondentes. O valor padrão é <strong>""</strong>.</td> 
  </tr> 
 </tbody> 
</table>

### Resposta {#response-1}

O objeto response contém uma matriz JSON que inclui detalhes dos formulários especificados. A estrutura da resposta é a seguinte:

```
{ 
 total: "<total number of submissions>",
 items: [{ formName: "<name of the form>", formPath: "<path to the form>", owner: "<owner of the form>"}, 
 ....]}
```

### Exemplo {#example-1}

**URL da solicitação**

```
https://[host]:[port]/content/forms/portal/submission.review.json?func=getAllSubmissions&formPath=/content/dam/formsanddocuments/forms-review/form2
```

**Resposta**

```java
{"total":1,"items":[{"formName":"form2","formPath":"/content/dam/formsanddocuments/forms-review/form2","submitID":"1403037413508500","formType":"af","jcr:lastModified":"2015-11-05T17:52:32.243+05:30","owner":"admin"}]}
```

## POST /content/forms/portal/submission.review.json?func=addComment {#post-content-forms-portal-submission-review-json-func-addcomment-br}

Adiciona um comentário à instância de envio especificada.

### Parâmetros de URL {#url-parameters-2}

Especifique os seguintes parâmetros no URL da solicitação:

| Parâmetro | Descrição |
|---|---|
| `submitID` | Especifica a ID de metadados associada a uma instância de envio. |
| `Comment` | Especifica o texto para comentário a ser adicionado à instância de envio especificada. |

### Resposta {#response-2}

Retorna uma ID de comentário sobre a postagem bem-sucedida de um comentário.

### Exemplo {#example-2}

**URL da solicitação**

```
https://[host:[port]/content/forms/portal/submission.review.json?func=addComment&submitID=1403037413508500&comment=API+test+comment
```

**Resposta**

```java
1403873422601300
```

## GET /content/forms/portal/submission.review.json?func=getComments   {#get-content-forms-portal-submission-review-json-func-getcomments-nbsp}

Retorna todos os comentários postados na instância de envio especificada.

### Parâmetros de URL {#url-parameters-3}

Especifique o seguinte parâmetro no URL da solicitação:

| Parâmetro | Descrição |
|---|---|
| `submitID` | Especifica a ID de metadados de uma instância de envio. |

### Resposta {#response-3}

O objeto response contém uma matriz JSON que inclui todos os comentários associados à ID de envio especificada. A estrutura da resposta é a seguinte:

```
[{
 owner: "<name of the commenter>", 
 comment: "<comment text>", 
 time: "<time when the comment was posted>"},
 { }......]
```

### Exemplo {#example-3}

**URL da solicitação**

```
https://[host]:[port]/content/forms/portal/submission.review.json?func=getComments&submitID=1403037413508500
```

**Resposta**

```java
[{"owner":"fr1","comment":"API test comment","time":1446726988250}]
```

## POST /content/forms/portal/submission.review.json?func=updateSubmission {#post-content-forms-portal-submission-review-json-func-updatesubmission-br}

Atualiza o valor da propriedade especificada da instância de formulário submetido especificada.

### Parâmetros de URL {#url-parameters-4}

Especifique os seguintes parâmetros no URL da solicitação:

| Parâmetro | Descrição |
|---|---|
| `submitID` | Especifica a ID de metadados associada a uma instância de envio. |
| `property` | Especifica a propriedade de formulário a ser atualizada. |
| `value` | Especifica o valor da propriedade de formulário a ser atualizada. |

### Resposta {#response-4}

Retorna um objeto JSON com informações sobre a atualização publicada.

### Exemplo {#example-4}

**URL da solicitação**

```
https://[host]:[port]/content/forms/portal/submission.review.json?func=updateSubmission&submitID=1403037413508500&value=sample_value&property=some_new_prop
```

**Resposta**

```java
{"formName":"form2","owner":"admin","jcr:lastModified":1446727516593,"path":"/content/forms/fp/admin/submit/metadata/1403037413508500.html","submitID":"1403037413508500","status":"submitted"}
```

