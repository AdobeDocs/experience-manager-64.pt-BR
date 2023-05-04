---
title: API para chamar o serviço de modelo de dados de formulário a partir de formulários adaptáveis
seo-title: API to invoke form data model service from adaptive forms
description: Explica a API invokeWebServices que pode ser usada para invocar serviços da Web escritos em WSDL a partir de um campo de formulário adaptável.
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---

# API para chamar o serviço de modelo de dados de formulário a partir de formulários adaptáveis {#api-to-invoke-form-data-model-service-from-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O AEM Forms permite que os autores de formulários simplifiquem e aprimorem ainda mais a experiência de preenchimento de formulários, chamando serviços configurados em um modelo de dados de formulário de um campo de formulário adaptável. Para chamar um serviço de modelo de dados, você pode criar uma regra no editor visual ou especificar um JavaScript usando o `guidelib.dataIntegrationUtils.executeOperation` API no editor de código do [editor de regras](/help/forms/using/rule-editor.md).

Este documento se concentra em escrever um JavaScript usando o `guidelib.dataIntegrationUtils.executeOperation` API para chamar um serviço.

## Uso da API {#using-the-api}

O `guidelib.dataIntegrationUtils.executeOperation` A API chama um serviço de dentro de um campo de formulário adaptável. A sintaxe da API é a seguinte:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

A API exige os seguintes parâmetros.

| Parâmetro | Descrição |
|---|---|
| `operationInfo` | Estrutura para especificar o identificador do modelo de dados de formulário, o título da operação e o nome da operação |
| `inputs` | Estrutura para especificar objetos de formulário cujos valores são inseridos para a operação de serviço |
| `outputs` | Estrutura para especificar objetos de formulário que serão preenchidos com os valores retornados pela operação de serviço |

A estrutura do `guidelib.dataIntegrationUtils.executeOperation` A API especifica detalhes sobre a operação do serviço. A sintaxe da estrutura é a seguinte.

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

A estrutura da API especifica os seguintes detalhes sobre a operação do serviço.

<table> 
 <tbody> 
  <tr> 
   <th>Parâmetro</th> 
   <th>Descrição</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>Especifique o caminho do repositório para o modelo de dados de formulário, incluindo seu nome</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>Especificar o nome da operação de serviço a ser executada</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>Mapear um ou mais objetos de formulário para os argumentos de entrada para a operação de serviço</td> 
  </tr> 
  <tr> 
   <td>Saída</td> 
   <td>Mapear um ou mais objetos de formulário para valores de saída da operação de serviço para preencher campos de formulário<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Exemplo de script para chamar um serviço {#sample-script-to-invoke-a-service}

O script de amostra a seguir usa a variável `guidelib.dataIntegrationUtils.executeOperation` API para chamar a `getAccountById` operação de serviço configurada no `employeeAccount` modelo de dados de formulário.

O `getAccountById` A operação recebe o valor na variável `employeeID` campo de formulário como entrada para a variável `empId` argumento e retorna o nome do funcionário, o número da conta e o saldo da conta do funcionário correspondente. Os valores de saída são preenchidos nos campos de formulário especificados. Por exemplo, o valor em `name` for preenchida na variável `fullName` elemento de formulário e valor para `accountNumber` argumento em `account` elemento de formulário.

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```
