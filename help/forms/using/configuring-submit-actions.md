---
title: Configuração da ação Enviar
seo-title: Configuração da ação Enviar
description: O AEM Forms permite configurar uma ação de envio para definir como um formulário adaptável é processado após o envio. Você pode usar as ações de envio incorporadas ou escrever suas próprias ações do zero.
seo-description: O AEM Forms permite configurar uma ação de envio para definir como um formulário adaptável é processado após o envio. Você pode usar as ações de envio incorporadas ou escrever suas próprias ações do zero.
uuid: aa261e65-a1ec-402b-80de-0ba8a294e315
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: fea76f90-22d5-4836-9901-a35229401eb0
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 1%

---


# Configurar a ação Enviar {#configuring-the-submit-action}

## Introdução ao envio de ações {#introduction-to-submit-actions}

Uma ação Enviar é acionada quando um usuário clica no botão Enviar em um formulário adaptável. É possível configurar a ação de envio no formulário adaptável. Os formulários adaptáveis fornecem algumas ações de envio prontas para uso. Você pode copiar e estender as ações de envio padrão para criar sua própria ação de envio. No entanto, com base em suas necessidades, você pode gravar e registrar sua própria ação de envio para processar dados no formulário enviado.

Quando um formulário é pré-preenchido ou submetido, os dados enviados são encaminhados por AEM para o massacre de dados para formatos intermediários. Os dados não são salvos em uma instância do AEM, exceto quando o formulário adaptável usa Adobe Sign, verify, forms portal rascunho ou envio ou AEM Workflows

Você pode configurar uma ação de envio na seção **[!UICONTROL Submission]** das propriedades do Contêiner de formulário adaptável, na barra lateral.

![Configurar ](assets/thank-you-setting.png)
**ação de envioFigura:** *Configurar ação de envio*

As ações de envio padrão disponíveis com formulários adaptáveis são:

* Enviar para ponto de extremidade REST
* Enviar e-mail
* Enviar PDF por email
* Chamar um Forms Workflow
* Enviar usando modelo de dados do formulário
* Ação de envio do portal do Forms
* Chamar um fluxo de trabalho AEM

>[!NOTE]
>
>A ação Enviar PDF por envio de email é aplicável somente a formulários adaptáveis que usam o modelo XFA como modelo de formulário.

>[!NOTE]
>
>Certifique-se de que o [AEM_Installation_Diretory]\crx-quickstart\temp\datamanager\ASM folder exists. O diretório é necessário para armazenar anexos temporariamente. Se o diretório não existir, crie-o.

>[!CAUTION]
>
>Se você [preencher previamente](/help/forms/using/prepopulate-adaptive-form-fields.md) um modelo de formulário, modelo de dados de formulário ou formulário adaptável baseado em esquema com reclamação de dados XML ou JSON para um esquema (esquema XML, esquema JSON, modelo de formulário ou modelo de dados de formulário) que seja de dados não conterá &lt;afData>, &lt;afBoundData> e &lt;/afUnboundData> tags, os dados dos campos não vinculados (Unbound campos limitados são campos de formulário adaptáveis sem a propriedade [bindref](/help/forms/using/prepopulate-adaptive-form-fields.md)) do formulário adaptável é perdida.

Você pode escrever uma ação de envio personalizada para formulários adaptáveis para atender ao seu caso de uso. Para obter mais informações, consulte [Gravando ação de ação de Enviar personalizado para formulários adaptáveis](/help/forms/using/custom-submit-action-form.md).

## Enviar para o ponto final REST {#submit-to-rest-endpoint}

A opção de envio **[!UICONTROL Enviar para o endpoint REST]** passa os dados preenchidos no formulário para uma página de confirmação configurada como parte da solicitação HTTP GET. É possível adicionar o nome dos campos a serem solicitados. O formato da solicitação é:

`{fieldName}={request parameter name}`

Conforme mostrado na imagem abaixo, `param1` e `param2` são passados como parâmetros com valores copiados dos campos **[!UICONTROL textbox]** e **[!UICONTROL numericbox]** para a próxima ação.

Você também pode **[!UICONTROL Ativar a solicitação do POST]** e fornecer um URL para postar a solicitação. Para enviar dados para o servidor AEM que hospeda o formulário, use um caminho relativo correspondente ao caminho raiz do servidor AEM. Por exemplo, /content/forms/af/SampleForm.html. Para enviar dados para qualquer outro servidor, use o caminho absoluto.

![Configurar a ação de envio do ponto de extremidade restante](assets/action-config.png)

Configurar a ação de envio do ponto de extremidade restante

>[!NOTE]
Para transmitir os campos como parâmetros em um URL REST, todos os campos devem ter nomes de elemento diferentes, mesmo se os campos forem colocados em painéis diferentes.

### Postar dados enviados para um recurso ou ponto final de repouso externo  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Use a ação **[!UICONTROL Submit to REST Endpoint]** para postar os dados enviados em um URL restante. O URL pode ser de um servidor interno (o servidor no qual o formulário é renderizado) ou externo.

Para postar dados em um servidor interno, forneça o caminho do recurso. Os dados são postados no caminho do recurso. Por exemplo, /content/restEndPoint. Para essas solicitações de publicação, as informações de autenticação da solicitação de envio são usadas.

Para postar dados em um servidor externo, forneça um URL. O formato do URL é https:// host:port/path_to_rest_end_point. Certifique-se de configurar o caminho para lidar com a solicitação POST anonimamente.

![Mapeamento para valores de campo passados como parâmetros da Página de agradecimento](assets/post-enabled-actionconfig.png)

No exemplo acima, as informações inseridas pelo usuário em `textbox` são capturadas usando o parâmetro `param1`. A sintaxe para postar dados capturados usando `param1` é:

`String data=request.getParameter("param1");`

Da mesma forma, os parâmetros que você usa para publicar dados e anexos XML são `dataXml` e `attachments`.

Por exemplo, esses dois parâmetros são usados no script para analisar os dados em um ponto de extremidade de repouso. Use a seguinte sintaxe para armazenar e analisar os dados:

`String data=request.getParameter("dataXml");`\
`String att=request.getParameter("attachments");`

Neste exemplo, `data` armazena os dados XML e `att` armazena os dados do anexo.

## Enviar e-mail {#send-email}

A ação de envio de **[!UICONTROL Email]** envia um email para um ou mais recipients após o envio bem-sucedido do formulário. O email gerado pode conter dados de formulário em um formato predefinido.

>[!NOTE]
Todos os campos de formulário devem ter nomes de elemento diferentes, mesmo que sejam colocados em painéis diferentes), para incluir dados de formulário em um email.

## Enviar PDF por email {#send-pdf-via-email}

A ação de envio **[!UICONTROL Enviar PDF por email]** envia um email com um PDF contendo dados de formulário para um ou mais recipients após o envio bem-sucedido do formulário.

**Observação:** *essa ação de envio está disponível para formulários adaptáveis baseados em XFA e formulários de adaptação baseados em XSD que têm o modelo Documento de registro.*

## Chamar um fluxo de trabalho de formulários {#invoke-a-forms-workflow}

A opção de envio **[!UICONTROL Enviar para o Forms workflow]** envia um xml de dados e anexos de arquivo (se houver) para um LiveCycle Adobe ou AEM Forms no processo JEE.

Para obter informações sobre como configurar a ação de envio do fluxo de trabalho Enviar para formulários, consulte [Enviar e processar os dados do formulário usando fluxos de trabalho de formulários](/help/forms/using/submit-form-data-livecycle-process.md).

## Enviar usando modelo de dados do formulário {#submit-using-form-data-model}

A ação **[!UICONTROL Enviar usando o Modelo de dados de formulário]** envia dados de formulário adaptáveis enviados para o objeto de modelo de dados especificado em um modelo de dados de formulário para a fonte de dados. Ao configurar a ação de envio, você pode escolher um objeto de modelo de dados cujos dados enviados deseja gravar de volta em sua fonte de dados.

Além disso, é possível enviar um anexo de formulário usando um modelo de dados de formulário e um Documento de registro (DoR) para a fonte de dados.

Para obter informações sobre o modelo de dados de formulário, consulte [AEM Forms Data Integration](/help/forms/using/data-integration.md).

## Ação de envio do portal do Forms {#forms-portal-submit-action}

A opção **[!UICONTROL Ação de envio do portal do Forms]** disponibiliza os dados do formulário por meio de um portal do AEM Forms.

Para obter mais informações sobre o Portal do Forms e enviar a ação, consulte [Componentes de rascunhos e envios](/help/forms/using/draft-submission-component.md).

## Chamar um fluxo de trabalho AEM {#invoke-an-aem-workflow}

A ação de envio **[!UICONTROL Invoke an AEM Workflow]** associa um formulário adaptável a um AEM Workflow. Quando um formulário é enviado, o fluxo de trabalho associado é iniciado automaticamente no nó de processamento. Além disso, ele coloca o arquivo de dados, os anexos e o documento de registro, se aplicável, no local da carga do fluxo de trabalho.

Antes de usar a ação de envio **[!UICONTROL Invoke an AEM Workflow]**, [defina as configurações AEM DS](/help/forms/using/configuring-the-processing-server-url-.md). Para obter informações sobre como criar um Fluxo de trabalho AEM, consulte [Fluxos de trabalho centrados no formulário no OSGi](/help/forms/using/aem-forms-workflow.md).

## Revalidação do lado do servidor no formulário adaptável {#server-side-revalidation-in-adaptive-form}

Normalmente, em qualquer sistema de captura de dados online, os desenvolvedores colocam algumas validações de JavaScript no lado do cliente para impor algumas regras de negócios. Mas nos navegadores modernos, os usuários finais têm como ignorar essas validações e fazer envios manualmente usando várias técnicas, como o Console DevTools do navegador Web. Essas técnicas também são válidas para formulários adaptáveis. Um desenvolvedor de formulários pode criar várias lógicas de validação, mas tecnicamente os usuários finais podem ignorar essas lógicas de validação e enviar dados inválidos para o servidor. Dados inválidos quebrariam as regras de negócios que um autor de formulários executou.

O recurso de revalidação do lado do servidor também permite executar as validações fornecidas por um autor de formulários adaptáveis ao projetar um formulário adaptável no servidor. Impede qualquer possível comprometimento de envios de dados e violações de regras comerciais representadas em termos de validações de formulários.

### O que validar no Servidor? {#what-to-validate-on-server-br}

Todas as validações de campo prontas para uso (OOTB) de um formulário adaptável que são executadas novamente no servidor são:

* Obrigatório
* Cláusula de Imagem de Validação
* Expressão de validação

### Ativando a validação do lado do servidor {#enabling-server-side-validation-br}

Use o **Revalidar no servidor** em Contêiner de formulário adaptável na barra lateral para ativar ou desativar a validação do lado do servidor para o formulário atual.

![Ativação da ](assets/revalidate-on-server.png)
**validação do lado do servidorFigura:** *Ativação da validação do lado do servidor*

Se o usuário final ignorar essas validações e enviar os formulários, o servidor executará novamente a validação. Se a validação falhar no final do servidor, a transação de envio será interrompida. O usuário final é apresentado ao formulário original novamente. Os dados capturados e enviados são apresentados ao usuário como um erro.

### Suporte a funções personalizadas nas expressões de validação {#supporting-custom-functions-in-validation-expressions-br}

Às vezes, no caso de **regras de validação complexas**, o script de validação exato reside em funções personalizadas e o autor chama essas funções personalizadas da expressão de validação de campo. Para tornar essa biblioteca de função personalizada conhecida e disponível durante a execução de validações do lado do servidor, o autor do formulário pode configurar o nome AEM biblioteca do cliente na guia **[!UICONTROL Basic]** das propriedades do Contêiner de formulário adaptável, conforme mostrado abaixo.

![Suporte a funções personalizadas em ](assets/clientlib-cat.png)
**Expressões de validaçãoFigura:** *suporte a funções personalizadas em Expressões de validação*

O autor pode configurar uma biblioteca javascript personalizada por formulário adaptável. Na biblioteca, mantenha somente as funções reutilizáveis, que têm dependência em bibliotecas de terceiros jquery e underscore.js.

## Erro ao lidar com a ação de envio {#error-handling-on-submit-action}

Como parte AEM diretrizes de segurança e proteção, configure páginas de erro personalizadas, como 404.jsp e 500.jsp. Esses manipuladores são chamados quando um erro de formulário 404 ou 500 é enviado. Os manipuladores também são chamados quando esses códigos de erro são acionados no nó Publicar .

Para obter mais informações, consulte [Personalizando páginas mostradas pelo Manipulador de erros](/help/sites-developing/customizing-errorhandler-pages.md).
