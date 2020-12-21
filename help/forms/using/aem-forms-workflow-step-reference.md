---
title: Fluxo de trabalho centrado na Forms no OSGi - Referência de etapas
seo-title: Fluxo de trabalho centrado na Forms no OSGi - Referência de etapas
description: O fluxo de trabalho centrado na Forms nas etapas do OSGi permite que você crie rapidamente workflows baseados em formulários adaptáveis.
seo-description: O fluxo de trabalho centrado na Forms nas etapas do OSGi permite que você crie rapidamente workflows baseados em formulários adaptáveis.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: aheimoz
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '4561'
ht-degree: 0%

---


# Fluxo de trabalho centrado na Forms no OSGi - Referência da etapa {#forms-centric-workflow-on-osgi-step-reference}

## Etapas de Forms Workflow {#forms-workflow-steps}

As etapas do fluxo de trabalho do Forms executam operações específicas do AEM Forms em um fluxo de trabalho AEM. Essas etapas permitem que você crie formulários adaptáveis rapidamente com base no fluxo de trabalho centralizado no Forms no OSGi. Esses workflows podem ser usados para desenvolver workflows básicos de revisão e aprovação, processos de negócios internos e externos ao firewall. Você também pode usar as etapas do Forms Workflow para os serviços de documento do start, fazer a integração com o fluxo de trabalho de assinatura do Adobe Sign e executar outras operações do AEM Forms. Você precisa de [AEM Forms add-on](https://www.adobe.com/go/learn_aemforms_documentation_63) para usar essas etapas em um fluxo de trabalho.

## Atribuir etapa de tarefa {#assign-task-step}

A etapa Atribuir tarefa cria uma tarefa e a atribui a um usuário ou grupo. Juntamente com a atribuição da tarefa, o componente também especifica o formulário adaptável ou PDF não interativo para a tarefa. O formulário adaptável é necessário para aceitar a entrada de usuários e um PDF não interativo ou um formulário adaptável somente leitura é usado apenas para workflows de revisão.

Você também pode usar o componente para controlar o comportamento da tarefa. Por exemplo, criar um documento automático de registro, atribuir a tarefa a um usuário ou grupo específico, especificar o caminho dos dados enviados, especificar o caminho dos dados a serem pré-preenchidos e especificar ações padrão. A etapa Atribuir Tarefa tem as seguintes propriedades:

* **Título:** Título da tarefa. O título é exibido AEM Caixa de entrada.
* **Descrição:** Explicação das operações que estão sendo executadas na tarefa. Essas informações são úteis para outros desenvolvedores de processos quando você trabalha em um ambiente de desenvolvimento compartilhado.

* **Caminho da miniatura:** Caminho da miniatura da tarefa. Se nenhum caminho for especificado, para uma miniatura padrão de formulário adaptável será exibida e para o Documento de Registro, um ícone padrão será exibido.
* **Etapa do fluxo de trabalho:** um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada AEM. É possível definir esses estágios nas propriedades do modelo (Sidekick > Página > Propriedades da página > Estágios).
* **Prioridade: a prioridade** selecionada é exibida na Caixa de entrada AEM. As opções disponíveis são Alto, Médio e Baixo. O valor padrão é Médio.
* **Data de Vencimento:** Especifique o número de dias ou horas após as quais a tarefa está marcada como vencida. Se você selecionar **Off**, a tarefa nunca será marcada como atrasada. Você também pode especificar um manipulador de tempo limite para executar tarefas específicas depois que a tarefa estiver atrasada.

* **Dias:** O número de dias antes dos quais a tarefa deve ser concluída. O número de dias é contado após a tarefa ser atribuída a um usuário. Se uma tarefa não for concluída e ultrapassar o número de dias especificado no campo Dias, então, se selecionado, um manipulador de tempo limite será acionado após a data de vencimento.
* **Horas:** O número de horas antes das quais a tarefa deve ser concluída. O número de horas é contado após a tarefa ser atribuída a um usuário. Se uma tarefa não for concluída e ultrapassar o número de horas especificado no campo Horas, então, se selecionado, um manipulador de tempo limite será acionado após as horas de vencimento.
* **Tempo limite após a data de vencimento:** selecione essa opção para ativar o campo de seleção Manipulador de tempo limite.
* **Manipulador de tempo limite:** selecione o script a ser executado quando a etapa de atribuição de tarefa ultrapassar a data de vencimento. Os scripts colocados no repositório CRX em [apps]/fd/painel/scripts/timeoutHandler estão disponíveis para seleção. O caminho especificado não existe no repositório crx. Um administrador cria o caminho antes de usá-lo.
* **Realce a ação e o comentário da última tarefa em Detalhes da Tarefa:** Selecione essa opção para exibir a última ação executada e o comentário recebido na seção de detalhes da tarefa de uma tarefa.
* **Tipo:** Escolha o tipo de documento a ser preenchido quando o fluxo de trabalho for iniciado. É possível escolher um formulário adaptável, um formulário adaptável somente leitura ou um documento PDF não interativo.
* **Usar formulário adaptável:** Especifique o método para localizar o formulário adaptável de entrada. Você pode usar o formulário adaptável disponível em um caminho absoluto, enviado como carga para o fluxo de trabalho ou disponível em um caminho calculado usando uma variável. Você pode usar uma variável do tipo String para especificar o caminho.
* **Caminho** do formulário adaptável: Especifique o caminho do formulário adaptável. O campo estará disponível quando você usar uma opção de formulário adaptável ou somente leitura adaptável no campo Tipo, juntamente com a opção de caminho absoluto, no campo Usar formulário adaptável.
* **Caminho do PDF:** especifique o caminho de um documento PDF não interativo. O campo está disponível quando você escolhe um documento PDF não interativo no campo Tipo. O caminho é sempre relativo à carga. Por exemplo, [Diretório_de_carga]/Workflow/PDF/credit-card.pdf. O caminho não existe no repositório crx. Um administrador cria o caminho antes de usá-lo. É necessário ativar uma opção Documento de registro ou formulários adaptáveis baseados em modelo de formulário para usar a opção Caminho do PDF.
* **Para a tarefa concluída, renderize o formulário adaptável como**: Quando uma tarefa está marcada como concluída, é possível renderizar o formulário adaptável como um formulário adaptável somente leitura ou um documento PDF. É necessário ativar uma opção Documento de registro ou formulários adaptáveis baseados em modelo de formulário para renderizar o formulário adaptável como Documento de registro.
* **Informações a serem pré-preenchidas:** Os seguintes campos listados abaixo servem como entradas para a tarefa:

   * **Caminho do arquivo de dados:** Caminho do arquivo de dados de entrada (.json ou .xml). O caminho é sempre relativo à carga. Por exemplo, o arquivo contém os dados enviados para o formulário por meio de um aplicativo AEM Caixa de entrada. Um caminho de exemplo é [Payload_Diretory]/workflow/data.
   * **Caminho do anexo:** os anexos disponíveis no local são anexados ao formulário associado à tarefa. O caminho é sempre relativo à carga. Um caminho de exemplo é [Diretório_de_carga]/attachments/

* **Informações enviadas:** Os seguintes campos listados abaixo servem como locais de saída para a tarefa:

   * **Caminho do arquivo de dados:** Caminho do arquivo de dados (.json ou .xml). O arquivo de dados contém informações enviadas por meio do formulário associado. O caminho é sempre relativo à carga. Por exemplo, [Diretório_de_carga]/Fluxo de trabalho/dados, onde os dados são um arquivo.
   * **Caminho do anexo:** caminho para salvar os anexos do formulário fornecido em uma tarefa.
   * **Documento de Caminho do registro:** Caminho para salvar um Documento de arquivo de registro. Por exemplo, [Diretório_de_carga]/DocumentofRecord/credit-card.pdf. O Documento de Registro não é gerado se o campo de caminho ficar vazio. O caminho é sempre relativo à carga.

* **Opções de atribuição:** especifique o método para atribuir a tarefa a um usuário. Você pode atribuir dinamicamente a tarefa a um usuário ou grupo usando o script do Seletor de participantes ou atribuir a tarefa a um usuário ou grupo AEM específico.
* **Seletor de participantes:** a opção está disponível quando a opção  **Dinamicamente para um usuário ou** grupo é selecionada no campo Atribuir opções. Você pode usar um ECMAScript ou um serviço para selecionar dinamicamente um usuário ou grupo. Para obter mais informações, consulte [Atribuir dinamicamente um fluxo de trabalho aos usuários](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) e [Criando uma etapa personalizada do Adobe Experience Manager Dynamic Participant.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Participantes:** O campo está disponível quando a opção  **[!UICONTROL com.adobe.granite.workflow.core.process.]** RandomParticipantChooseroption está selecionada no campo Seletor de participantes. O campo permite selecionar usuários ou grupos para a opção RandomParticipantChooser.

* **Argumentos:** O campo fica disponível quando um script diferente do script RandomParticipantChoose é selecionado no campo Seletor de participantes. O campo permite fornecer uma lista de argumentos separados por vírgula para o script selecionado no campo Seletor de participantes.

* **Usuário ou grupo:** a tarefa é atribuída ao usuário ou grupo selecionado. A opção está disponível quando **Para um usuário ou grupo específico** está selecionada no campo Atribuir opções. O campo lista todos os usuários e grupos do grupo de usuários do fluxo de trabalho.

* **Notificar o destinatário por email:** selecione esta opção para enviar notificações por email ao destinatário. Essas notificações são enviadas quando uma tarefa é atribuída a um usuário. Antes de usar a opção, ative as notificações AEM Web Console. Para obter instruções passo a passo, consulte [configurar notificações por email para a etapa de atribuição da tarefa](/help/forms/using/aem-forms-workflow.md)

* **Modelo** de email HTML: Selecione o modelo de e-mail para o e-mail de notificação. Para editar um modelo, modifique o arquivo localizado em /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt no repositório crx.
* **Permitir delegação para:** AEM A caixa de entrada fornece uma opção para o usuário conectado para delegar o fluxo de trabalho atribuído a outro usuário. Você pode delegar dentro do mesmo grupo ou ao usuário do fluxo de trabalho de outro grupo. Se a tarefa for atribuída a um único usuário e a opção **permitir delegação para membros do grupo designado** for selecionada, então não será possível delegar a tarefa a outro usuário ou grupo.

* **Ações padrão:** as ações Enviar, Salvar e Redefinir estão disponíveis. Todas as ações padrão são ativadas, por padrão.
* **Variável de rota:** Nome da variável de rota. A variável de rota captura ações personalizadas que um usuário seleciona AEM Caixa de entrada.
* **Rotas:** uma tarefa pode ramificar para rotas diferentes. Quando selecionada em AEM Caixa de entrada, a rota retorna um valor e o fluxo de trabalho ramifica com base na rota selecionada.
* **Título**: Especifique o título da rota. É exibido em AEM Caixa de entrada.
* **Ícone** Coral: Especifique o atributo HTML de um ícone de coral. A biblioteca de Adobe CorelUI fornece um vasto conjunto de ícones touch-first. Você pode escolher e usar um ícone para a rota. É exibido junto com o título AEM Caixa de entrada.
* **Permitir que o destinatário adicione comentário**: Selecione essa opção para ativar comentários para a tarefa. Um destinatário pode adicionar os comentários de dentro AEM Caixa de entrada no momento do envio da tarefa.
* **Permitir que o destinatário adicione anexos à tarefa**: Selecione essa opção para ativar anexos para a tarefa. Um destinatário pode adicionar os anexos de dentro AEM Caixa de entrada no momento do envio da tarefa.
* **Caminho de saída dos anexos** de tarefa: Especifique o local da pasta de anexos. O local é relativo à carga.
* **Usar metadados personalizados:** Selecione essa opção para ativar o campo de metadados personalizado. Os metadados personalizados são usados em modelos de email.
* **Metadados personalizados:** selecione um metadados personalizado para os modelos de email. Os metadados personalizados estão disponíveis no repositório crx em apps/fd/painel/scripts/metadataScripts. O caminho especificado não existe no repositório crx. Um administrador cria o caminho antes de usá-lo. Você também pode usar um serviço para os metadados personalizados. Você também pode estender a interface `WorkitemUserMetadataService` para fornecer metadados personalizados.

* **Mostrar dados das etapas** anteriores: Selecione essa opção para habilitar os destinatários a visualização de destinatários anteriores, ação já tomada na tarefa, comentários adicionados à tarefa e documento do registro da tarefa concluída, se disponível.
* **Mostrar dados de etapas subsequentes:** Selecione essa opção para permitir que o destinatário atual visualização a ação tomada e os comentários adicionados à tarefa pelos destinatários subsequentes. Também permite que o destinatário atual visualização um documento de registro da tarefa concluída, se disponível.
* **Visibilidade do tipo de dados:** Por padrão, um destinatário pode visualização um Documento de Registro, destinatários, ação tomada e comentários que os destinatários anteriores e subsequentes adicionaram. Use a opção de visibilidade do tipo de dados para limitar o tipo de dados visível para os destinatários.

## Enviar Etapa de Email {#send-email-step}

Use a etapa de email para enviar um email, por exemplo, um email com um documento de registro, link de um formulário adaptável, link de uma comunicação interativa ou com um documento PDF anexado. A etapa Enviar email suporta [email HTML](https://en.wikipedia.org/wiki/HTML_email). Os emails HTML respondem e se adaptam ao cliente de email e ao tamanho da tela do recipient. Você pode usar um modelo de e-mail HTML para definir a aparência, o esquema de cores e o comportamento do e-mail.

A etapa de email usa o serviço Day CQ Mail para enviar emails. Antes de usar a etapa de email, verifique se o [serviço de email](/help/forms/using/aem-forms-workflow.md) está configurado. A etapa de email tem as seguintes propriedades:

**Título:O** título da etapa ajuda a identificar a etapa no editor de fluxo de trabalho.

**Descrição:** a explicação é útil para outros desenvolvedores de processos quando você trabalha em um ambiente de desenvolvimento compartilhado.

**Assunto do email:** O assunto pode ser recuperado de metadados de fluxo de trabalho ou especificado manualmente. Selecione a opção **Literal** para especificar manualmente um assunto ou selecione a opção **Recuperar dos metadados do fluxo de trabalho** para recuperar o assunto de uma propriedade de metadados.

**Modelo** de email HTML: Modelo HTML para o email. Você pode especificar variáveis em um modelo de email. A Etapa de email extrai e exibe todas as variáveis incluídas em um modelo para entradas.

**Metadados de modelo de e-mail: o** valor das variáveis de modelo de e-mail pode ser um valor especificado pelo usuário, o caminho de um ativo no autor ou no servidor de publicação, imagem ou uma propriedade de metadados de fluxo de trabalho.

* **Literal:** Use a opção quando souber o valor exato a ser especificado. Por exemplo, [example@example.com](mailto:example@example.com).

* **Metadados do fluxo de trabalho:** use a opção quando o valor a ser usado for salvo em uma propriedade de metadados do fluxo de trabalho. Depois de selecionar a opção, digite o nome da propriedade de metadados na caixa de texto vazia abaixo da opção Metadados do fluxo de trabalho. Por exemplo, emailAddress.
* **URL do ativo:** use a opção para incorporar um link da Web de uma comunicação interativa ao email. Depois de selecionar a opção, procure e escolha a comunicação interativa a ser incorporada. O ativo pode residir no autor ou no servidor de publicação.
* **Imagem:** Use a opção para incorporar uma imagem ao email. Depois de selecionar a opção, navegue e escolha a imagem. A opção de imagem está disponível somente para as tags de imagem (&lt;img src=&quot;&amp;ast;&quot;/>) disponíveis no modelo de email.

**Endereço de email do remetente/Recipient:** selecione a opção  **** Literalpara especificar manualmente um endereço de email ou selecione a opção  **Recuperar dos** metadados do fluxo de trabalho para recuperar o endereço de email de uma propriedade de metadados. Você também pode especificar uma lista de matrizes de propriedade de metadados para a opção **Recuperar dos metadados do fluxo de trabalho**.

**Caminho do anexo do arquivo:** o ativo disponível no local especificado é anexado ao email. O caminho do ativo pode ser relativo à carga ou ao caminho absoluto. Um caminho de exemplo é [Diretório_de_carga]/attachments/

**Nome do arquivo:** nome do arquivo de anexo de email. A Etapa de e-mail altera o nome do arquivo original do anexo para o nome do arquivo especificado. O nome pode ser especificado manualmente ou recuperado de uma propriedade de metadados do fluxo de trabalho. Use a opção **Literal** quando souber o valor exato a ser especificado. Use a opção **Recuperar de metadados de fluxo de trabalho** quando o valor a ser usado for salvo em uma propriedade de metadados de fluxo de trabalho.

## Gerar Documento da etapa de registro {#generate-document-of-record-step}

Quando um formulário é preenchido ou enviado, é possível manter um registro do formulário, em formato impresso ou em formato de documento. Isso é conhecido como Documento de registro (DoR). Você pode usar a etapa Gerar Documento de registro para criar uma versão PDF somente leitura ou interativa de um formulário adaptável. A versão PDF contém informações preenchidas no formulário juntamente com o layout do formulário adaptável.

A etapa Documento de registro tem as seguintes propriedades:

**Usar formulário** adaptável: Especifique o método para localizar o formulário adaptável de entrada. Você pode usar o formulário adaptável disponível em um caminho absoluto, enviado como carga para o fluxo de trabalho ou disponível em um caminho calculado usando uma variável. Você pode usar uma variável do tipo String para especificar o caminho.

**Caminho** do formulário adaptável: Especifique o caminho do formulário adaptável. O campo estará disponível quando você usar uma opção de formulário adaptável ou somente leitura adaptável no campo Tipo, juntamente com a opção de caminho absoluto, no campo Usar formulário adaptável.

**Caminho dos dados de entrada:** Caminho dos dados de entrada para o formulário adaptável. É possível manter os dados em um local relativo à carga ou especificar um caminho absoluto dos dados. Os dados de entrada são unidos ao formulário adaptável para criar um documento de registro.

**Caminho do anexo de entrada:Caminho do anexo** de entrada: Caminho dos anexos. Esses anexos estão incluídos no Documento de registro. É possível manter os anexos em um local relativo à carga ou especificar um caminho absoluto dos anexos.

Se você especificar o caminho de uma pasta, por exemplo, anexos, todos os arquivos diretamente disponíveis na pasta serão anexados ao Documento de registro. Se algum arquivo estiver disponível nas pastas diretamente disponíveis no caminho de anexo especificado, os arquivos serão incluídos no Documento de Registro como anexos. Se houver pastas em pastas diretamente disponíveis, elas serão ignoradas.

**Documento gerado do caminho de registro:** especifique o local para manter um documento do arquivo de registro. Você pode optar por substituir a pasta de carga ou colocar o documento de registro em um local dentro do diretório de carga.

**Local**: Especifique o idioma do documento de registro.

## Invoque a etapa do serviço de Modelo de Dados de Formulário {#invoke-form-data-model-service-step}

Você pode usar [AEM Forms Data Integration](/help/forms/using/data-integration.md) para configurar e conectar-se a fontes de dados diferentes. Essas fontes de dados podem ser uma solução de banco de dados, serviço da Web, serviço REST, serviço OData e CRM. A Integração de dados da AEM Forms permite criar um modelo de dados de formulário abrangendo vários serviços para executar operações de recuperação de dados, adição e atualização no banco de dados configurado. Você pode usar a **etapa Chamar serviço do modelo de dados** para selecionar um modelo de dados de formulário (FDM) e usar os serviços do FDM para recuperar, atualizar ou adicionar dados a fontes de dados diferentes.

Para explicar entradas para campos da etapa, a tabela do banco de dados a seguir e o arquivo JSON são usados como exemplo:

**Exemplo de tabela CustomerDetails**

<table> 
 <tbody> 
  <tr> 
   <td>Propriedade</td> 
   <td>Valor<br /> </td> 
  </tr> 
  <tr> 
   <td>Nome<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Sobrenome</td> 
   <td>Rosa</td> 
  </tr> 
  <tr> 
   <td>ID do cliente</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Endereço de email<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Exemplo de arquivo JSON**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

A etapa Invocar serviço de modelo de dados de formulário tem os campos listados abaixo para facilitar as operações do modelo de dados de formulário:

* **Título:** Título da etapa. Ajuda a identificar a etapa no editor de fluxo de trabalho.
* **Descrição:** Explicação útil para outros desenvolvedores de processos quando você trabalha em um ambiente de desenvolvimento compartilhado.

* **Caminho** do modelo de dados de formulário: Procure e selecione um modelo de dados de formulário presente no servidor.

* **Serviço**: Lista dos serviços fornecidos pelo modelo de dados de formulário selecionado.
* **Entrada para serviços > Forneça dados de entrada usando literal, metadados de fluxo de trabalho e um arquivo** JSON: Um serviço pode ter vários argumentos. Selecione a opção para obter o valor dos argumentos de serviço a partir de uma propriedade de metadados de fluxo de trabalho, um objeto JSON ou insira diretamente o valor na caixa de texto fornecida:

   * **Literal:** Use a opção quando souber o valor exato a ser especificado. Por exemplo, srose@we.info.
   * **Recuperar dos metadados do fluxo de trabalho:** use a opção quando o valor a ser usado for salvo em uma propriedade de metadados do fluxo de trabalho. Por exemplo, emailAddress.
   * **Notação de ponto JSON:** use a opção quando o valor a ser usado estiver em um arquivo JSON. Por exemplo, Insurance.customerDetails.emailAddress.A opção JSON Dot Notation estará disponível somente se a opção Mapear campos de entrada da JSON de entrada estiver selecionada.
   * **Mapear campos de entrada do JSON de entrada:** especifique o caminho de um arquivo JSON para obter o valor de entrada de alguns argumentos de serviço do arquivo JSON. O caminho do arquivo JSON pode ser relativo à carga ou a um caminho absoluto.

* **Entrada para serviços > Fornecer dados de entrada usando um arquivo JSON:** Selecione a opção para obter valores para todos os argumentos de um arquivo JSON.
* **Caminho** do arquivo JSON de entrada: Caminho do arquivo JSON que contém valores para todos os argumentos de serviço. O caminho do arquivo JSON pode ser **relativo à carga** ou um **caminho absoluto**.

* **JSON Dot Notation:** Deixe o campo em branco para usar todos os objetos do arquivo JSON especificado como entrada para argumentos de serviço. Para ler um objeto JSON específico do arquivo JSON especificado como entrada para argumentos de serviço, especifique a notação de pontos para o objeto JSON, por exemplo, se você tiver um JSON semelhante ao listado no start da seção, especifique Insurance.customerDetails para fornecer todos os detalhes de um cliente como entrada para o serviço.
* **Saída do serviço > Mapear e gravar valores de saída em metadados:** Selecione a opção para salvar os valores de saída como propriedades do nó de metadados da instância do fluxo de trabalho no repositório crx. Especifique o nome da propriedade de metadados e selecione o atributo de saída do serviço correspondente a ser mapeado com a propriedade de metadados; por exemplo, mapeie o phone_number retornado pelo serviço de saída com a propriedade phone_number dos metadados do fluxo de trabalho.
* **Saída do serviço > Salvar saída como JSON:** Selecione a opção para salvar os valores de saída em um arquivo JSON.
* **Caminho do arquivo JSON de saída:** Caminho para salvar o arquivo JSON de saída. O caminho do arquivo JSON de saída pode ser relativo à carga ou a um caminho absoluto.

## Etapa do Documento de assinatura {#sign-document-step}

A etapa Assinar Documento permite que você use o Adobe Sign para assinar documentos. A etapa Assinar Documento tem as seguintes propriedades:

* **Nome do Contrato:** especifique o título do contrato. O nome do contrato se torna parte do assunto e do texto do corpo do email enviado aos signatários.
* **Local:** especifique o idioma para as opções de e-mail e verificação.
* **Configuração** da Adobe Sign Cloud: Escolha uma configuração da Adobe Sign Cloud. Se você não tiver configurado o Adobe Sign para AEM Forms, consulte [Integrar o Adobe Sign ao AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento a ser assinado:** você pode escolher um documento de um local relativo à carga, usar a carga como documento ou especificar um caminho absoluto do documento.
* **Dias até o término:** um documento é marcado como vencido (prazo vencido) depois que não há atividade na tarefa pelo número de dias especificado no campo  **Dias até o** término. O número de dias é contado depois que o documento é atribuído a um usuário para assinatura.

* **Frequência de email do lembrete:** você pode enviar um email de lembrete em intervalos diários ou semanais. A semana é contada a partir do dia em que o documento é atribuído a um usuário para assinatura.
* **Processo de assinatura:** você pode optar por assinar um documento em uma ordem sequencial ou paralela. Em ordem sequencial, um assinante recebe o documento por vez para assinatura. Depois que o primeiro assinante concluir a assinatura do documento, o documento será enviado para o segundo assinante e assim por diante. Em ordem paralela, vários signatários podem assinar um documento de cada vez.

* **URL de redirecionamento:** especifique um URL de redirecionamento. Depois que o documento for assinado, você poderá redirecionar o destinatário para um URL. Normalmente, este URL contém uma mensagem de agradecimento ou instruções adicionais.
* **Etapa do fluxo de trabalho:** um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada AEM. É possível definir esses estágios nas propriedades do modelo (Sidekick > Página > Propriedades da página > Estágios).
* **Selecionar signatários:** especifique o método para escolher os signatários do documento. Você pode atribuir dinamicamente o fluxo de trabalho a um usuário ou grupo ou adicionar manualmente detalhes de um assinante.
* **Script ou serviço para selecionar signatários:** A opção está disponível somente se a opção Dinamicamente estiver selecionada no campo Selecionar signatários. Você pode especificar um ECMAScript ou um serviço para escolher assinantes e opções de verificação para um documento.

* **Detalhes do assinante:** a opção estará disponível somente se a opção Manualmente estiver selecionada no campo Selecionar signatários. Especifique o endereço de email e escolha um mecanismo de verificação opcional. Antes de selecionar um mecanismo de verificação de 2 etapas, verifique se a opção de verificação correspondente está ativada para a conta Adobe Sign configurada.
* **Variável de status:** um documento habilitado pela Adobe Sign armazena o status de assinatura do documento em uma variável. Especifique o nome da variável de status (adobeSignStatus). Uma variável de status de uma instância está disponível no CRXDE em /etc/workflow/instance/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData contém o status de uma variável.
* **Caminho do Documento assinado:** especifique o local para manter documentos assinados. Você pode optar por substituir o arquivo de carga ou colocar o documento assinado em um local dentro do diretório de carga.

## Etapas do Documento Services {#document-services-steps}

AEM serviços de Documento são um conjunto de serviços para criar, montar e proteger Documentos PDF. A AEM Forms fornece uma etapa AEM Fluxo de trabalho separada para cada serviço de documento:

### Aplicar etapa de carimbo de data e hora do Documento {#apply-document-time-stamp-step}

Adicione um carimbo de data/hora a um documento. Você fornece detalhes do documento, como caminho do documento de entrada, nome do documento de entrada, local para armazenar dados exportados. Você pode optar por substituir o arquivo de carga existente ou escolher um nome de arquivo diferente para armazenar dados em um arquivo diferente na pasta de carga.

### Converter em etapa de imagem {#convert-to-image-step}

Converte um documento PDF em um arquivo de imagem. Os formatos de imagem suportados são JPEG, JPEG2000, PNG e TIFF. As seguintes informações se aplicam às conversões em imagens TIFF:

* Um arquivo TIFF de várias páginas é gerado.
* Algumas anotações não são incluídas em imagens TIFF. As anotações que exigem que o Acrobat gere sua aparência não são incluídas.

### Converter em etapa PDF/A {#convert-to-pdf-a-step}

Converte um documento PDF em formato PDF/A usando as opções fornecidas. A versão PDF/A do PDF (Portable Documento Format) é especializada para arquivamento e preservação de documentos a longo prazo.

### Converter para a etapa PS {#convert-to-ps-step}

Converta documentos PDF em PostScript. Ao converter para PostScript, você pode usar a operação de conversão para especificar o documento de origem e se deve ser convertida para PostScript nível 2 ou 3. O documento PDF convertido em um arquivo PostScript deve ser não interativo.

### Criar PDF a partir da etapa de tipo especificada {#create-pdf-from-specified-type-step}

Gere um documento PDF a partir de um arquivo de entrada. O documento de entrada pode ser relativo à carga, ter um caminho absoluto ou pode ser a própria carga.

### Criar PDF a partir da etapa URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Gera um documento PDF a partir do URL fornecido, do HTML e do arquivo ZIP.

### Etapa Exportar dados {#export-data-step}

Exporta dados de um arquivo PDF forms ou XDP. É necessário inserir o caminho de arquivo do Documento de entrada e o Formato de dados de exportação. As opções para Formato de dados de exportação são Auto, XDP e XmlData.

### Export PDF para a etapa de tipo especificada {#export-pdf-to-specified-type-step}

Converte um documento PDF em um formato selecionado.

### Gerar etapa de PDF não interativo {#generate-non-interactive-pdf-step}

Gerar um PDF não interativo. Fornece várias opções de personalização.

### Etapa de importação de dados {#import-data-step}

Une dados de formulário em um formulário PDF. É possível importar dados de formulário para um formulário PDF.

### Invocar etapa DDX {#invoke-ddx-step}

Executa o arquivo DDX no mapa especificado de documentos de entrada e retorna os documentos PDF manipulados.

### Optimize PDF Step {#optimize-pdf-step}

Otimiza arquivos PDF reduzindo seu tamanho. O resultado dessa conversão são arquivos PDF que podem ser menores que suas versões originais. Essa operação também converte documentos PDF na versão PDF especificada nos parâmetros de otimização.

As configurações de otimização especificam como os arquivos são otimizados. Estas são configurações de exemplo:

* Versão PDF do público alvo
* Descartar objetos como ações JavaScript e miniaturas de página incorporadas
* Descartar dados do usuário, como comentários e anexos de arquivo
* Descartar configurações inválidas ou não usadas
* Compactação de dados descompactados ou uso de algoritmos de compactação mais eficientes
* Remoção de fontes incorporadas
* Configuração de valores de transparência

### Renderizar etapa do formulário PDF {#render-pdf-form-step}

Renderiza um formulário criado no Form Designer (XDP) em um formulário PDF.

### Etapa do Documento seguro {#secure-document-step}

Criptografe, assine e certifique um documento. A AEM Forms oferece suporte à criptografia com base em senha e certificado. Você também pode escolher entre vários algoritmos para assinar documentos. Por exemplo, SHA-256 e SH-512. Também é possível usar a etapa de fluxo de trabalho para o leitor estender documentos PDF. A etapa do fluxo de trabalho fornece opções para ativar a decodificação de códigos de barras, assinaturas digitais, importação e exportação de dados PDF e outras opções.

### Etapa Enviar para impressora {#send-to-printer-step}

Envie um documento diretamente para uma impressora. Ele suporta os seguintes mecanismos de acesso de impressão:

* **Impressora** acessível diretamente: Uma impressora instalada no mesmo computador é chamada de impressora acessível diretamente e o computador é nomeado host da impressora. Esse tipo de impressora pode ser uma impressora local que está conectada diretamente ao computador.
* **Impressora** acessível indiretamente: A impressora instalada em um servidor de impressão é acessada de outros computadores. Tecnologias como o CUPS (Common UNIX® Print System) e o protocolo LPD (Line Printer Daemon) estão disponíveis para conexão com uma impressora de rede. Para acessar uma impressora acessível indiretamente, especifique o IP ou o nome do host do servidor de impressão. Usando esse mecanismo, você pode enviar um documento para um URI LPD quando a rede tiver um LPD em execução. O mecanismo permite direcionar o documento para qualquer impressora conectada à rede que tenha um LPD em execução.

