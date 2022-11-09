---
title: Fluxo de trabalho centrado na Forms no OSGi - Referência em etapas
seo-title: Forms-centric workflow on OSGi - Step Reference
description: O fluxo de trabalho centrado no Forms nas etapas do OSGi permite que você crie rapidamente fluxos de trabalho baseados em formulários adaptáveis.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '4637'
ht-degree: 0%

---

# Fluxo de trabalho centrado na Forms no OSGi - Referência em etapas {#forms-centric-workflow-on-osgi-step-reference}

## Etapas do Forms Workflow {#forms-workflow-steps}

As etapas do fluxo de trabalho do Forms executam operações específicas do AEM Forms em um fluxo de trabalho AEM. Essas etapas permitem que você crie rapidamente formulários adaptáveis com base no fluxo de trabalho centrado no Forms no OSGi. Esses fluxos de trabalho podem ser usados para desenvolver fluxos de trabalho básicos de revisão e aprovação, internos e outros processos de negócios por firewall. Você também pode usar as etapas do Forms Workflow para iniciar serviços de documento, integrar com o fluxo de trabalho de assinatura do Acrobat Sign e executar outras operações do AEM Forms. Você precisa [Complemento do AEM Forms](https://www.adobe.com/go/learn_aemforms_documentation_63) para usar essas etapas em um workflow.

## Atribuir etapa da tarefa {#assign-task-step}

A etapa Atribuir tarefa cria uma tarefa e a atribui a um usuário ou grupo. Ao atribuir a tarefa, o componente também especifica o formulário adaptável ou o PDF não interativo para a tarefa. O formulário adaptável é necessário para aceitar a entrada de usuários e o PDF não interativo ou um formulário adaptável somente leitura é usado para fluxos de trabalho de revisão somente.

Você também pode usar o componente para controlar o comportamento da tarefa. Por exemplo, criar um documento automático de registro, atribuir a tarefa a um usuário ou grupo específico, especificar o caminho dos dados enviados, especificar o caminho dos dados a serem preenchidos previamente e especificar ações padrão. A etapa Atribuir tarefa tem as seguintes propriedades:

* **Título:** Título da tarefa. O título é exibido AEM Caixa de entrada.
* **Descrição:** Explicação das operações que estão sendo executadas na tarefa. Essas informações são úteis para outros desenvolvedores de processos quando você está trabalhando em um ambiente de desenvolvimento compartilhado.

* **Caminho da miniatura:** Caminho da miniatura da tarefa. Se nenhum caminho for especificado, para uma miniatura padrão de formulário adaptável será exibida e para Documento de registro, um ícone padrão será exibido.
* **Estágio do fluxo de trabalho:** Um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada de AEM. É possível definir esses estágios nas propriedades do modelo (Sidekick > Página > Propriedades da página > Estágios).
* **Prioridade:** A prioridade selecionada é exibida na Caixa de entrada de AEM. As opções disponíveis são Alto, Médio e Baixo. O valor padrão é Médio.
* **Data de Vencimento:** Especifique o número de dias ou horas após as quais a tarefa está marcada vencida. Se você selecionar **Desligado**, a tarefa nunca será marcada como atrasada. Você também pode especificar um manipulador de tempo limite para executar tarefas específicas depois que a tarefa estiver vencida.

* **Dias:** O número de dias antes do qual a tarefa deve ser concluída. O número de dias é contado após a tarefa ser atribuída a um usuário. Se uma tarefa não estiver concluída e cruzar o número de dias especificado no campo Dias , então, se selecionado, um manipulador de tempo limite será acionado após a data de vencimento.
* **Horas:** O número de horas antes do qual a tarefa deve ser concluída. O número de horas é contado após a tarefa ser atribuída a um usuário. Se uma tarefa não estiver concluída e cruzar o número de horas especificado no campo Horas , então, se selecionado, um manipulador de tempo limite será acionado após as horas de vencimento.
* **Tempo limite após a data de vencimento:** Selecione esta opção para ativar o campo de seleção Manipulador de tempo limite.
* **Manipulador de tempo limite:** Selecione o script a ser executado quando a etapa Atribuir tarefa atravessar a data de vencimento. Scripts colocados no repositório CRX em [aplicativos]/fd/dashboard/scripts/timeoutHandler estão disponíveis para seleção. O caminho especificado não existe no repositório crx. Um administrador cria o caminho antes de usá-lo.
* **Destaque a ação e o comentário da última tarefa em Detalhes da tarefa:** Selecione esta opção para exibir a última ação executada e o comentário recebido na seção de detalhes da tarefa de uma tarefa.
* **Tipo:** Escolha o tipo de documento a ser preenchido quando o workflow for iniciado. Você pode escolher um formulário adaptável, um formulário adaptável somente leitura ou um documento PDF não interativo.
* **Use o formulário adaptável:** Especifique o método para localizar o formulário adaptável de entrada. Você pode usar o formulário adaptável disponível em um caminho absoluto, enviado como carga para o workflow ou disponível em um caminho calculado usando uma variável. Você pode usar uma variável do tipo String para especificar o caminho.
* **Caminho do formulário adaptável**: Especifique o caminho do formulário adaptável. O campo estará disponível quando a opção Usar formulário adaptável ou formulário adaptável somente leitura for usada no campo Tipo , juntamente com a opção de caminho absoluto, for usada no campo Usar formulário adaptável .
* **PDF Path:** Especifique o caminho de um documento PDF não interativo. O campo fica disponível ao escolher um documento de PDF não interativo no campo Tipo. O caminho é sempre relativo à carga útil. Por exemplo, [Diretório_de_carga]/Workflow/PDF/credit-card.pdf. O caminho não existe no repositório crx. Um administrador cria o caminho antes de usá-lo. Você precisa de uma opção Documento de registro ativada ou formulários adaptáveis baseados em modelo de formulário para usar a opção PDF Path.
* **Para tarefas concluídas, renderize o formulário adaptável como**: Quando uma tarefa é marcada como concluída, é possível renderizar o formulário adaptável como um formulário adaptável somente leitura ou um documento PDF. É necessário ativar uma opção Documento de registro ou formulários adaptáveis baseados em modelo de formulário para renderizar o formulário adaptável como Documento de registro.
* **Informações a preencher previamente:** Os seguintes campos listados abaixo servem como entradas para a tarefa:

   * **Caminho do arquivo de dados:** Caminho do arquivo de dados de entrada (.json ou .xml). O caminho é sempre relativo à carga útil. Por exemplo, o arquivo contém os dados enviados para o formulário por meio de um aplicativo AEM Caixa de entrada. Um caminho de exemplo é [Diretório_de_carga]/workflow/data.
   * **Caminho do anexo:** Os anexos disponíveis no local são anexados ao formulário associado à tarefa. O caminho é sempre relativo à carga útil. Um caminho de exemplo é [Diretório_de_carga]/anexos/

* **Informações enviadas:** Os seguintes campos listados abaixo servem como locais de saída para a tarefa:

   * **Caminho do arquivo de dados:** Caminho do arquivo de dados (.json ou .xml). O arquivo de dados contém informações enviadas por meio do formulário associado. O caminho é sempre relativo à carga útil. Por exemplo, [Diretório_de_carga]/Workflow/data, onde os dados são um arquivo.
   * **Caminho do anexo:** O caminho para salvar os anexos do formulário é fornecido em uma tarefa.
   * **Caminho do Documento de Registro:** Caminho para salvar um arquivo de Documento de registro. Por exemplo, [Diretório_de_carga]/DocumentofRecord/credit-card.pdf. O Documento de registro não é gerado se o campo de caminho for deixado em branco. O caminho é sempre relativo à carga útil.

* **Atribuir opções:** Especifique o método para atribuir a tarefa a um usuário. Você pode atribuir dinamicamente a tarefa a um usuário ou grupo usando o script do Seletor de Participante ou atribuir a tarefa a um usuário ou grupo de AEM específico.
* **Seletor de participante:** A opção está disponível quando a variável **Dinamicamente para um usuário ou grupo** está selecionada no campo Assign options . Você pode usar um ECMAScript ou um serviço para selecionar dinamicamente um usuário ou grupo. Para obter mais informações, consulte [Atribuir dinamicamente um fluxo de trabalho aos usuários](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) e [Criando uma etapa personalizada do Adobe Experience Manager Dynamic Participant.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Participantes:** O campo está disponível quando a variável **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** é selecionada no campo Seletor de participante . O campo permite selecionar usuários ou grupos para a opção RandomParticipantChooser.

* **Argumentos:** O campo fica disponível quando um script diferente do script RandomParticipantChoose é selecionado no campo Seletor de Participante. O campo permite fornecer uma lista de argumentos separados por vírgula para o script selecionado no campo Seletor de participante.

* **Usuário ou grupo:** A tarefa é atribuída ao usuário ou grupo selecionado. A opção está disponível quando a variável **Para um usuário ou grupo específico** está selecionada no campo Assign options . O campo lista todos os usuários e grupos do grupo de usuários do fluxo de trabalho.

* **Notificar o destinatário por email:** Selecione essa opção para enviar notificações por email ao destinatário. Essas notificações são enviadas quando uma tarefa é atribuída a um usuário. Antes de usar a opção , ative as notificações AEM console da Web. Para obter instruções passo a passo, consulte [configurar notificações por email para a etapa atribuir tarefa](/help/forms/using/aem-forms-workflow.md)

* **Modelo de email do HTML**: Selecione o modelo de email para o email de notificação. Para editar um modelo, modifique o arquivo localizado em /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt no crx-repository.
* **Permitir delegação para:** AEM Caixa de entrada fornece uma opção para o usuário conectado delegar o fluxo de trabalho atribuído a outro usuário. Você pode delegar no mesmo grupo ou no usuário de workflow de outro grupo. Se a tarefa for atribuída a um único usuário e a variável **permitir delegação aos membros do grupo de destinatários** estiver selecionada, então não é possível delegar a tarefa a outro usuário ou grupo.

* **Ações padrão:** As ações Enviar, Salvar e Redefinir estão disponíveis e estão prontas para uso. Todas as ações padrão são habilitadas, por padrão.
* **Variável de rota:** Nome da variável de rota. A variável de rota captura ações personalizadas que um usuário seleciona AEM Caixa de entrada.
* **Rotas:** Uma tarefa pode ramificar para rotas diferentes. Quando selecionada em AEM Caixa de entrada, a rota retorna um valor e o workflow ramifica com base na rota selecionada.
* **Título**: Especifique o título da rota. Exibido em AEM Caixa de entrada.
* **Ícone Coral**: Especifique o atributo HTML de um ícone de coral. Adobe A biblioteca CorelUI fornece um vasto conjunto de ícones de toque primeiro. Você pode escolher e usar um ícone para a rota. Ele é exibido junto com o título em AEM Caixa de entrada.
* **Permitir ao destinatário adicionar comentário**: Selecione esta opção para habilitar comentários para a tarefa. Um destinatário pode adicionar os comentários de dentro AEM Caixa de entrada no momento do envio da tarefa.
* **Permitir que o destinatário adicione anexos à tarefa**: Selecione esta opção para ativar anexos para a tarefa. Um destinatário pode adicionar os anexos de dentro AEM Caixa de entrada no momento do envio da tarefa.
* **Caminho de saída dos anexos da tarefa**: Especifique a localização da pasta de anexos. O local é relativo à carga.
* **Usar metadados personalizados:** Selecione essa opção para ativar o campo de metadados personalizado. Os metadados personalizados são usados em modelos de email.
* **Metadados personalizados:** Selecione metadados personalizados para os modelos de email. Os metadados personalizados estão disponíveis no repositório crx em apps/fd/dashboard/scripts/metadataScripts. O caminho especificado não existe no repositório crx. Um administrador cria o caminho antes de usá-lo. Você também pode usar um serviço para os metadados personalizados. Você também pode estender o `WorkitemUserMetadataService` para fornecer metadados personalizados.

* **Mostrar dados das etapas anteriores**: Selecione esta opção para permitir que os destinatários visualizem os destinatários anteriores, a ação já executada na tarefa, os comentários adicionados à tarefa e o documento de registro da tarefa concluída, se disponível.
* **Mostrar dados de etapas subsequentes:** Selecione essa opção para permitir que o destinatário atual visualize a ação executada e os comentários adicionados à tarefa pelos destinatários subsequentes. Também permite que o destinatário atual exiba um documento de registro da tarefa concluída, se disponível.
* **Visibilidade do tipo de dados:** Por padrão, um destinatário pode visualizar um Documento de registro, destinatários, ação tomada e comentários que destinatários anteriores e subsequentes adicionaram. Use a opção visibility of data type para limitar o tipo de dados visível para os destinatários.

## Etapa Enviar Email {#send-email-step}

Use a etapa de email para enviar um email, por exemplo, um email com um documento de registro, link de um formulário adaptável, link de uma comunicação interativa ou com um documento de PDF anexado. Enviar suporte à etapa de email [HTML email](https://en.wikipedia.org/wiki/HTML_email). Os emails do HTML são responsivos e adaptam-se ao cliente de email e ao tamanho da tela dos recipients. Você pode usar um modelo de email do HTML para definir a aparência, o esquema de cores e o comportamento do email.

A etapa de email usa o Day CQ Mail Service para enviar emails. Antes de usar a etapa de email, verifique se a variável [serviço de email](/help/forms/using/aem-forms-workflow.md) está configurado. A etapa de email tem as seguintes propriedades:

**Título:** O título da etapa ajuda a identificar a etapa no editor de fluxo de trabalho.

**Descrição:** Explicação é útil para outros desenvolvedores de processos quando você está trabalhando em um ambiente de desenvolvimento compartilhado.

**Assunto do email:** O assunto pode ser recuperado de metadados de fluxo de trabalho ou especificado manualmente. Selecione o **Literal** para especificar um assunto manualmente ou selecionar a opção **Recuperar dos metadados do fluxo de trabalho** para recuperar o assunto de uma propriedade de metadados.

**Modelo de email do HTML**: modelo HTML para o email. Você pode especificar variáveis em um modelo de email. A Etapa de email extrai e exibe todas as variáveis incluídas em um modelo para entradas.

**Metadados de modelo de email:** O valor das variáveis do modelo de email pode ser um valor especificado pelo usuário, o caminho de um ativo no autor ou no servidor de publicação, a imagem ou uma propriedade de metadados de workflow.

* **Literal:** Use a opção quando souber o valor exato a ser especificado. Por exemplo, [example@example.com](mailto:example@example.com).

* **Metadados do fluxo de trabalho:** Use a opção quando o valor a ser usado for salvo em uma propriedade de metadados de workflow. Depois de selecionar a opção , insira o nome da propriedade de metadados na caixa de texto vazia abaixo da opção Metadados do fluxo de trabalho . Por exemplo, emailAddress.
* **URL do ativo:** Use a opção para incorporar um link da Web de uma comunicação interativa ao email. Após selecionar a opção , navegue e escolha a comunicação interativa a ser incorporada. O ativo pode residir no autor ou no servidor de publicação.
* **Imagem:** Use a opção para incorporar uma imagem ao email. Depois de selecionar a opção , navegue e escolha a imagem. A opção de imagem está disponível somente para as tags de imagem (&lt;img src=&quot;&amp;ast;&quot; />) disponíveis no modelo de email.

**Endereço de email do remetente/destinatário:** Selecione o **Literal** para especificar manualmente um endereço de email ou selecionar a opção **Recuperar dos metadados do fluxo de trabalho** para recuperar o endereço de email de uma propriedade de metadados. Também é possível especificar uma lista de matrizes de propriedades de metadados para a variável **Recuperar dos metadados do fluxo de trabalho** opção.

**Caminho do anexo do arquivo:** O ativo disponível no local especificado é anexado ao email. O caminho do ativo pode ser relativo à carga ou ao caminho absoluto. Um caminho de exemplo é [Diretório_de_carga]/anexos/

**Nome do arquivo:** Nome do arquivo de anexo de email. A Etapa de email altera o nome de arquivo original do anexo para o nome de arquivo especificado. O nome pode ser especificado manualmente ou recuperado de uma propriedade de metadados de workflow. Use o **Literal** quando você souber o valor exato a ser especificado. Use o **Recuperar de metadados de fluxo de trabalho** quando o valor a ser usado for salvo em uma propriedade de metadados de workflow.

## Etapa Gerar Documento de Registro {#generate-document-of-record-step}

Quando um formulário é preenchido ou enviado, é possível manter um registro do formulário, em formato impresso ou documento. Isso é chamado de Documento de Registro (DoR). Você pode usar a etapa Gerar documento de registro para criar uma versão de PDF somente leitura ou interativa de um formulário adaptável. A versão PDF contém informações preenchidas para o formulário junto com o layout do formulário adaptável.

A etapa Documento de registro tem as seguintes propriedades:

**Usar formulário adaptável**: Especifique o método para localizar o formulário adaptável de entrada. Você pode usar o formulário adaptável disponível em um caminho absoluto, enviado como carga para o workflow ou disponível em um caminho calculado usando uma variável. Você pode usar uma variável do tipo String para especificar o caminho.

**Caminho do formulário adaptável**: Especifique o caminho do formulário adaptável. O campo estará disponível quando a opção Usar formulário adaptável ou formulário adaptável somente leitura for usada no campo Tipo , juntamente com a opção de caminho absoluto, for usada no campo Usar formulário adaptável .

**Caminho de dados de entrada:** Caminho dos dados de entrada para o formulário adaptável. Você pode manter os dados em um local relativo à carga ou especificar um caminho absoluto dos dados. Os dados de entrada são unidos ao formulário adaptável para criar um documento de registro.

**Caminho do anexo de entrada:** Caminho do anexo de entrada: Caminho dos anexos. Esses anexos estão incluídos no Documento de registro. Você pode manter os anexos em um local relativo à carga ou especificar um caminho absoluto dos anexos.

Se você especificar o caminho de uma pasta, por exemplo, anexos, todos os arquivos diretamente disponíveis na pasta serão anexados ao Documento de registro. Se algum arquivo estiver disponível nas pastas diretamente disponíveis no caminho de anexo especificado, os arquivos serão incluídos no Documento de registro como anexos. Se houver pastas em pastas diretamente disponíveis, elas serão ignoradas.

**Caminho do Documento de Registro Gerado:** Especifique o local para manter um documento de arquivo de registro. Você pode optar por substituir a pasta de carga útil ou colocar o documento de registro em um local dentro do diretório de carga útil.

**Localidade**: Especifique o idioma do documento de registro.

## Invoque a etapa Serviço do Modelo de Dados de Formulário {#invoke-form-data-model-service-step}

Você pode usar [Integração de dados do AEM Forms](/help/forms/using/data-integration.md) para configurar e conectar-se a fontes de dados diferentes. Essas fontes de dados podem ser um banco de dados, serviço da Web, serviço REST, serviço OData e solução CRM. A Integração de dados do AEM Forms permite criar um modelo de dados de formulário que abrange vários serviços para executar operações de recuperação de dados, além de atualizar no banco de dados configurado. Você pode usar o **Invoque a etapa Serviço do Modelo de Dados** para selecionar um modelo de dados de formulário (FDM) e usar os serviços do FDM para recuperar, atualizar ou adicionar dados a fontes de dados diferentes.

Para explicar entradas para campos da etapa, a tabela de banco de dados a seguir e o arquivo JSON são usados como exemplo :

**Tabela de detalhes do cliente de exemplo**

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
   <td>Customer ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Endereço de email<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Arquivo JSON de exemplo**

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
* **Descrição:** Explicação útil para outros desenvolvedores de processos quando você está trabalhando em um ambiente de desenvolvimento compartilhado.

* **Caminho do modelo de dados de formulário**: Procure e selecione um modelo de dados de formulário presente no servidor.

* **Serviço**: Lista dos serviços fornecidos pelo modelo de dados de formulário selecionado.
* **Entrada para serviços > Fornecer dados de entrada usando literal, metadados de fluxo de trabalho e um arquivo JSON**: Um serviço pode ter vários argumentos. Selecione a opção para obter o valor dos argumentos de serviço de uma propriedade de metadados de workflow, um objeto JSON ou insira diretamente o valor na caixa de texto fornecida:

   * **Literal:** Use a opção quando souber o valor exato a ser especificado. Por exemplo, srose@we.info.
   * **Recuperar dos metadados do fluxo de trabalho:** Use a opção quando o valor a ser usado for salvo em uma propriedade de metadados de workflow. Por exemplo, emailAddress.
   * **Notação de ponto JSON:** Use a opção quando o valor a ser usado estiver em um arquivo JSON. Por exemplo, Insurance.customerDetails.emailAddress.A opção Notação de pontos JSON só estará disponível se a opção Mapear campos de entrada do JSON de entrada estiver selecionada.
   * **Mapear campos de entrada do JSON de entrada:** Especifique o caminho de um arquivo JSON para obter o valor de entrada de alguns argumentos de serviço do arquivo JSON. O caminho do arquivo JSON pode ser relativo à carga ou a um caminho absoluto.

* **Entrada para serviços > Fornecer dados de entrada usando um arquivo JSON:** Selecione a opção para obter valores para todos os argumentos de um arquivo JSON.
* **Caminho do arquivo JSON de entrada**: Caminho do arquivo JSON que contém valores para todos os argumentos de serviço. O caminho do arquivo JSON pode ser **relativo à carga** ou **caminho absoluto**.

* **Notação de ponto JSON:** Deixe o campo em branco para usar todos os objetos do arquivo JSON especificado como entrada para argumentos de serviço. Para ler um objeto JSON específico do arquivo JSON especificado como entrada para argumentos de serviço, especifique a notação de pontos para o objeto JSON, por exemplo, Se você tiver um JSON semelhante ao listado no início da seção, especifique Insurance.customerDetails para fornecer todos os detalhes de um cliente como entrada para o serviço.
* **Saída do serviço > Mapear e gravar valores de saída em metadados:** Selecione a opção para salvar os valores de saída como propriedades do nó de metadados da instância de fluxo de trabalho no crx-repository. Especifique o nome da propriedade de metadados e selecione o atributo de saída de serviço correspondente a ser mapeado com a propriedade de metadados; por exemplo, mapeie o phone_number retornado pelo serviço de saída com a propriedade phone_number dos metadados do fluxo de trabalho.
* **Saída do serviço > Salvar saída como JSON:** Selecione a opção para salvar os valores de saída em um arquivo JSON.
* **Caminho do arquivo JSON de saída:** Caminho para salvar o arquivo JSON de saída. O caminho do arquivo JSON de saída pode ser relativo à carga ou a um caminho absoluto.

## Etapa Assinar documento {#sign-document-step}

A etapa Assinar documento permite usar o Acrobat Sign para assinar documentos. A etapa Assinar documento tem as seguintes propriedades:

* **Nome do Contrato:** Especifique o título do contrato. O nome do contrato se torna parte do assunto e do texto do corpo do email enviado aos signatários.
* **Localidade:** Especifique o idioma para as opções de email e verificação.
* **Configuração da Acrobat Sign Cloud**: Escolha uma Configuração da Acrobat Sign Cloud. Se você não tiver configurado o Acrobat Sign para AEM Forms, consulte [Integrar o Acrobat Sign ao AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento a assinar:** Você pode escolher um documento de um local relativo à carga, usar carga como documento ou especificar um caminho absoluto do documento.
* **Caminho do anexo de entrada:** Selecione um anexo. Esses anexos estão incluídos no Documento de assinatura. Você pode manter os anexos em um local relativo à carga ou especificar um caminho absoluto dos anexos.

   Se você especificar o caminho de uma pasta, por exemplo, anexos, todos os arquivos diretamente disponíveis na pasta serão anexados ao Documento de registro. Se algum arquivo estiver disponível nas pastas diretamente disponíveis no caminho de anexo especificado, os arquivos serão incluídos no Documento de assinatura como anexos. Se houver pastas em pastas diretamente disponíveis, elas serão ignoradas.
* **Dias até o prazo:** Um documento é marcado como vencido (prazo vencido) depois que não há atividade na tarefa para o número de dias especificado na **Dias até o final do prazo** campo. O número de dias é contado depois que o documento é atribuído a um usuário para assinatura.

* **Frequência de email do lembrete:** Você pode enviar um email de lembrete diariamente ou semanalmente. A semana é contada a partir do dia em que o documento foi atribuído a um usuário para assinatura.
* **Processo de assinatura:** Você pode optar por assinar um documento em uma ordem sequencial ou paralela. Em ordem sequencial, um assinante recebe o documento por vez para assinatura. Depois que o primeiro assinante concluir a assinatura do documento, o documento será enviado para o segundo assinante e assim por diante. Em ordem paralela, vários signatários podem assinar um documento de cada vez.

* **URL de redirecionamento:** Especifique um URL de redirecionamento. Depois que o documento for assinado, você poderá redirecionar o destinatário para um URL. Normalmente, este URL contém uma mensagem de agradecimento ou mais instruções.
* **Estágio do fluxo de trabalho:** Um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada de AEM. É possível definir esses estágios nas propriedades do modelo (Sidekick > Página > Propriedades da página > Estágios).
* **Selecionar Assinantes:** Especifique o método para escolher os signatários do documento. Você pode atribuir dinamicamente o fluxo de trabalho a um usuário ou grupo ou adicionar manualmente detalhes de um assinante.
* **Script ou serviço para selecionar signatários:** A opção estará disponível somente se a opção Dinamicamente estiver selecionada no campo Selecionar signatários . Você pode especificar um ECMAScript ou um serviço para escolher assinantes e opções de verificação para um documento.

* **Detalhes do assinante:** A opção só estará disponível se a opção Manualmente estiver selecionada no campo Selecionar signatários . Especifique o endereço de email e escolha um mecanismo de verificação opcional. Antes de selecionar um mecanismo de verificação de duas etapas, verifique se a opção de verificação correspondente está habilitada para a conta do Acrobat Sign configurada.
* **Variável de status:** Um documento habilitado para Acrobat Sign armazena o status de assinatura do documento em uma variável. Especifique o nome da variável de status (adobeSignStatus). Uma variável de status de uma instância está disponível no CRXDE em /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData contém o status de uma variável.
* **Caminho do Documento Assinado:** Especifique o local para manter documentos assinados. Você pode optar por substituir o arquivo de carga útil ou colocar o documento assinado em um local dentro do diretório de carga útil.

## Etapas dos Serviços de documento {#document-services-steps}

AEM serviços de documento são um conjunto de serviços para criar, montar e proteger documentos do PDF. O AEM Forms fornece uma etapa AEM fluxo de trabalho separada para cada serviço de documento:

### Aplicar etapa Carimbo de data/hora do documento {#apply-document-time-stamp-step}

Adicionar carimbo de data/hora a um documento. Você fornece detalhes do documento, como caminho do documento de entrada, nome do documento de entrada, local para armazenar dados exportados. Você pode optar por substituir o arquivo de carga útil existente ou escolher um nome de arquivo diferente para armazenar dados em um arquivo diferente na pasta de carga útil.

### Converter em etapa da imagem {#convert-to-image-step}

Converte um documento PDF em um arquivo de imagem. Os formatos de imagem suportados são JPEG, JPEG2000, PNG e TIFF. As seguintes informações se aplicam às conversões de imagens de TIFF:

* Um arquivo TIFF de várias páginas é gerado.
* Algumas anotações não são incluídas em imagens TIFF. As anotações que exigem que o Acrobat gere sua aparência não são incluídas.

### Converter em etapa PDF/A {#convert-to-pdf-a-step}

Converte um documento PDF em formato PDF/A usando as opções fornecidas. A versão PDF/A do Portable Document Format (PDF) é especializada no arquivamento e na preservação de documentos a longo prazo.

### Etapa Converter em PS {#convert-to-ps-step}

Converta documentos PDF para PostScript. Ao converter para PostScript, você pode usar a operação de conversão para especificar o documento de origem e se deve ser convertido para o nível 2 ou 3 do PostScript. O documento do PDF que você converte em um arquivo PostScript deve ser não interativo.

### Criar PDF a partir da etapa de tipo especificada {#create-pdf-from-specified-type-step}

Gere um documento PDF a partir de um arquivo de entrada. O documento de entrada pode ser relativo à carga, ter um caminho absoluto ou pode ser a própria carga.

### Criar PDF a partir de URL/HTML/etapa ZIP {#create-pdf-from-url-html-zip-step}

Gera um documento PDF a partir do URL, HTML e arquivo ZIP fornecidos.

### Etapa Exportar dados {#export-data-step}

Exporta dados de um arquivo PDF forms ou XDP. Ele requer que você insira o caminho de arquivo do Documento de entrada e o Formato de dados de exportação. As opções para Exportar formato de dados são Auto, XDP e XmlData.

### Export PDF para a etapa de tipo especificada {#export-pdf-to-specified-type-step}

Converte um documento PDF em um formato selecionado.

### Gerar etapa PDF não interativa {#generate-non-interactive-pdf-step}

Gere um PDF não interativo. Ele fornece várias opções de personalização.

### Etapa Importação de dados {#import-data-step}

Une os dados do formulário em um formulário PDF. É possível importar dados de formulário para um formulário PDF.

### Invocar etapa DDX {#invoke-ddx-step}

Executa o arquivo DDX no mapa especificado de documentos de entrada e retorna os documentos PDF manipulados.

### Optimize PDF step {#optimize-pdf-step}

Otimiza arquivos PDF, reduzindo seu tamanho. O resultado dessa conversão são arquivos PDF que podem ser menores do que suas versões originais. Essa operação também converte documentos PDF para a versão PDF especificada nos parâmetros de otimização.

As configurações de otimização especificam como os arquivos são otimizados. Estas são as configurações de exemplo:

* Versão do Target PDF
* Descartar objetos, como ações do JavaScript e miniaturas de página incorporadas
* Descartar dados do usuário, como comentários e anexos de arquivo
* Descartar configurações inválidas ou não usadas
* Compactação de dados descompactados ou uso de algoritmos de compactação mais eficientes
* Remoção de fontes incorporadas
* Configuração de valores de transparência

### Etapa de formulário PDF de renderização {#render-pdf-form-step}

Renderiza um formulário criado no Form Designer (XDP) em um formulário PDF.

### Etapa do Documento Seguro {#secure-document-step}

Criptografar, assinar e certificar um documento. O AEM Forms suporta criptografia baseada em senha e certificado. Você também pode escolher entre vários algoritmos para assinar documentos. Por exemplo, SHA-256 e SH-512. Você também pode usar a etapa do fluxo de trabalho para o leitor estender documentos do PDF. A etapa do fluxo de trabalho fornece a opção para habilitar a decodificação do código de barras, assinaturas digitais, importação e exportação de dados do PDF e outras opções.

### Enviar para etapa da impressora {#send-to-printer-step}

Envie um documento diretamente para uma impressora. Ele suporta os seguintes mecanismos de acesso de impressão:

* **Impressora acessível diretamente**: Uma impressora instalada no mesmo computador é chamada de impressora acessível diretamente e o computador é nomeado host da impressora. Esse tipo de impressora pode ser uma impressora local conectada diretamente ao computador.
* **Impressora direta acessível**: A impressora instalada em um servidor de impressão é acessada de outros computadores. Tecnologias como o CUPS (Common UNIX® Printer System) e o protocolo LPD (Line Printer Daemon) estão disponíveis para se conectar a uma impressora de rede. Para acessar uma impressora indireta acessível, especifique o IP ou o nome do host do servidor de impressão. Usando esse mecanismo, você pode enviar um documento para um URI LPD quando a rede tiver um LPD em execução. O mecanismo permite rotear o documento para qualquer impressora conectada à rede com um LPD em execução.
