---
title: Fluxo de trabalho centrado na Forms no OSGi
seo-title: Crie rapidamente processos baseados em formulários adaptáveis, automatize as operações dos serviços de documento e use o Adobe Sign com workflows AEM
description: Use o AEM Forms Workflow para automatizar e criar rapidamente revisões e aprovações, para os serviços de documentos de start (por exemplo, para converter um documento PDF em outro formato), integrar-se ao fluxo de trabalho de assinatura da Adobe Sign e muito mais.
seo-description: Use o AEM Forms Workflow para automatizar e criar rapidamente revisões e aprovações, para os serviços de documentos de start (por exemplo, para converter um documento PDF em outro formato), integrar-se ao fluxo de trabalho de assinatura da Adobe Sign e muito mais.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '2916'
ht-degree: 1%

---


# Fluxo de trabalho centrado na Forms no OSGi {#forms-centric-workflow-on-osgi}

![](do-not-localize/header.png)

As empresas coletam dados de centenas e milhares de formulários, vários sistemas back-end e fontes de dados on-line ou off-line. Eles também têm um conjunto dinâmico de usuários para tomar decisões sobre os dados, o que envolve processos iterativos de revisão e aprovação.

Juntamente com workflows de revisão e aprovação de audiências internas e externas, grandes organizações e empresas têm tarefas repetitivas. Por exemplo, converter um documento PDF em outro formato. Quando feitas manualmente, essas tarefas demoram muito tempo e recursos. As empresas também têm requisitos legais para assinar digitalmente um documento e arquivar dados de formulário para uso posterior em formatos predefinidos.

## Introdução ao fluxo de trabalho centrado na Forms no OSGi {#introduction-to-forms-centric-workflow-on-osgi}

Você pode usar AEM Workflows para criar rapidamente workflows adaptáveis baseados em formulários. Esses workflows podem ser usados para revisão e aprovações, fluxos de processos de negócios, para serviços de documentos de start, integração com fluxo de trabalho de assinatura da Adobe Sign e operações semelhantes. Por exemplo, o processamento de aplicativos de cartão de crédito, os funcionários deixam workflows de aprovação, salvando um formulário como um documento PDF. Além disso, esses workflows podem ser usados dentro de uma organização ou através de um firewall de rede.

Com o fluxo de trabalho centrado na Forms no OSGi, você pode criar e implantar rapidamente workflows para várias tarefas na pilha OSGi, sem precisar instalar o recurso completo de Gerenciamento de processos na pilha JEE. O desenvolvimento e o gerenciamento de workflows usam os recursos familiares Fluxo de trabalho AEM e Caixa de entrada AEM. Os workflows são a base para automatizar os processos de negócios reais que abrangem vários sistemas de software, redes, departamentos e até mesmo organizações.

Depois de configurados, esses workflows podem ser acionados manualmente para concluir um processo definido ou executados de forma programática quando os usuários enviam um formulário ou [carta de gerenciamento de correspondência](/help/forms/using/cm-overview.md). Com esses recursos aprimorados AEM Fluxo de trabalho, a AEM Forms oferta dois recursos distintos, mas semelhantes. Como parte de sua estratégia de implantação, você precisa decidir qual funciona para você. Consulte uma [comparação](/help/forms/using/capabilities-osgi-jee-workflows.md) dos Workflows de AEM centrados na Forms no OSGi e no Process Management no JEE. Além disso, para a topologia de implantação, consulte [Arquitetura e topologias de implantação para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

O fluxo de trabalho centrado na Forms no OSGi estende [AEM Caixa de entrada](/help/sites-authoring/inbox.md) e fornece componentes adicionais (etapas) para AEM editor de fluxo de trabalho para adicionar suporte a workflows centrados na AEM Forms. A Caixa de entrada AEM estendida tem funcionalidades semelhantes a [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). Juntamente com o gerenciamento de workflows centrados em humanos (Aprovação, Revisão etc.), você pode usar AEM workflows para automatizar [operações relacionadas aos serviços de documento](/help/sites-developing/workflows-step-ref.md) (por exemplo, Gerar PDF) e documentos de assinatura eletrônica (Adobe Sign).

O diagrama a seguir descreve o procedimento completo para criar, executar e monitorar um fluxo de trabalho centrado na Forms no OSGi.

![fluxo de trabalho de introdução ao aem-forms](assets/introduction-to-aem-forms-workflow.jpg)

## Antes de você iniciar {#before-you-start}

* Um fluxo de trabalho é uma representação de um processo de negócios do mundo real. Mantenha o seu processo de negócios real e a lista dos participantes do processo de negócios prontos. Além disso, mantenha o material promocional (formulários adaptáveis, Documentos PDF e muito mais) pronto antes que o start crie um fluxo de trabalho.
* Um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada AEM e na ajuda para relatar o progresso do fluxo de trabalho. Divida seu processo de negócios em estágios lógicos.
* Você pode configurar a etapa de atribuição de tarefas AEM para enviar notificações por email aos usuários ou destinatários. Portanto, [ativar notificações por e-mail](#configure-email-service).
* Um fluxo de trabalho também pode usar o sinal de Adobe para assinaturas digitais. Se você planeja usar o Adobe Sign em um fluxo de trabalho, o [configure o Adobe Sign para o AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) antes de usá-lo em um fluxo de trabalho.

## Criar um modelo de fluxo de trabalho {#create-a-workflow-model}

Um modelo de fluxo de trabalho consiste em lógica e fluxo de um processo de negócios. É feita de uma série de etapas. Essas etapas são componentes AEM. Você pode estender as etapas do fluxo de trabalho com parâmetros e scripts para fornecer mais funcionalidade e controle, conforme necessário. A AEM Forms fornece algumas etapas além AEM etapas disponíveis na caixa. Para obter uma lista detalhada das etapas do AEM e do AEM Forms, consulte [AEM Workflow Step Reference](/help/sites-developing/workflows-step-ref.md) e [fluxo de trabalho centrado no Forms no OSGi - Step Reference](/help/forms/using/aem-forms-workflow.md).

AEM fornece uma interface de usuário intuitiva para criar um modelo de fluxo de trabalho usando as etapas de fluxo de trabalho fornecidas. Para obter instruções passo a passo sobre como criar um modelo de fluxo de trabalho, consulte [Criando Modelos de Fluxo de Trabalho](/help/sites-developing/workflows-models.md). O exemplo a seguir fornece instruções passo a passo para criar um modelo de fluxo de trabalho para um fluxo de trabalho de aprovação e revisão:

>[!NOTE]
>
>Você deve ser um membro do grupo editor de fluxo de trabalho para criar ou editar um modelo de fluxo de trabalho.

### Criar um modelo para um fluxo de trabalho de aprovação e revisão {#create-a-model-for-an-approval-and-review-workflow}

O fluxo de trabalho de aprovação e revisão é para as tarefas que exigem intervenção humana para tomar decisões. O exemplo a seguir cria um modelo de fluxo de trabalho para um aplicativo de empréstimo hipotecário a ser preenchido por um agente bancário de escritório. Depois que o aplicativo for preenchido, ele será enviado para aprovação. Posteriormente, o pedido aprovado será enviado ao requerente para assinatura eletrônica usando a Adobe Sign.

O exemplo está disponível como um pacote anexado abaixo. Importe e instale o exemplo usando o gerenciador de pacotes. Você também pode executar as seguintes etapas para criar manualmente o modelo de fluxo de trabalho para o aplicativo:

O exemplo cria um modelo de fluxo de trabalho e um aplicativo de hipoteca para ser preenchido por um agente bancário de front-office. Uma vez preenchido, o pedido é enviado para aprovação. Posteriormente, o aplicativo aprovado será enviado ao cliente para assinaturas eletrônicas usando a Adobe Sign. É possível importar e instalar o exemplo usando o gerenciador de pacotes.

[Obter arquivo](assets/example-mortgage-loan-application.zip)

1. Abra o console Modelos de fluxo de trabalho. O URL padrão é `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selecione **[!UICONTROL Criar]** e **[!UICONTROL Criar Modelo]**. A caixa de diálogo Adicionar modelo de fluxo de trabalho é exibida.
1. Insira **[!UICONTROL Title]** e **[!UICONTROL Nome]** (opcional). Por exemplo, um aplicativo de hipoteca. Toque em **[!UICONTROL Concluído]**.
1. Selecione o modelo de fluxo de trabalho recém-criado e toque em **Editar.** Agora, você pode adicionar etapas de fluxo de trabalho para criar lógica de negócios. Quando você cria um modelo de fluxo de trabalho pela primeira vez, ele contém:

   * As etapas: Start de fluxo e Fim de fluxo. Essas etapas representam o início e o fim do fluxo de trabalho. Essas etapas são obrigatórias e não podem ser editadas ou removidas.
   * Um exemplo de etapa Participante chamado Etapa 1. Esta etapa está configurada para atribuir um item de trabalho ao usuário administrador. Remova esta etapa.

1. Habilitar notificações por email. Você pode configurar o fluxo de trabalho centrado na Forms no OSGi para enviar notificações por email aos usuários ou destinatários. Execute as seguintes configurações para ativar notificações por email:

   1. Vá para AEM gerenciador de configuração em `https://[server]:[port]/system/console/configMgr`.
   1. Abra a configuração **[!UICONTROL Day CQ Mail Service]**. Especifique um valor para os campos **[!UICONTROL nome do host do servidor SMTP]**, **[!UICONTROL porta do servidor SMTP,]** e **[!UICONTROL &quot;From&quot; address]**. Clique em **[!UICONTROL Salvar]**.
   1. Abra a configuração **[!UICONTROL Externalizador de links Day CQ]**. No campo **[!UICONTROL Domínios]**, especifique o nome do host/endereço IP real e o número da porta para instâncias locais, de autor e de publicação. Clique em **[!UICONTROL Salvar]**.

1. Criar estágios de fluxo de trabalho. Um fluxo de trabalho pode ter vários estágios. Esses estágios são exibidos na Caixa de entrada AEM e no andamento do relatório do fluxo de trabalho.

   Para definir um estágio, toque no ícone ![info-círculo](assets/info-circle.png) para abrir as propriedades do modelo de fluxo de trabalho, abra a guia **[!UICONTROL Estágios]**, adicione estágios para o modelo de fluxo de trabalho e toque em **[!UICONTROL Salvar e fechar]**. Para o exemplo de aplicativo de hipoteca, crie estágios: solicitação de empréstimo, status de solicitação de empréstimo, a ser assinado pelos documentos e documento de empréstimo assinado.

1. Arraste e solte o navegador **[!UICONTROL Atribuir Tarefa]** para o modelo de fluxo de trabalho. Faça dele o primeiro passo do modelo.

   O componente de atribuição de tarefa atribui a tarefa, criada pelo fluxo de trabalho, a um usuário ou grupo. Juntamente com a atribuição da tarefa, é possível usar o componente para especificar um formulário adaptável ou um PDF não interativo para a tarefa. O formulário adaptável é necessário para aceitar a entrada de usuários e um PDF não interativo ou um formulário adaptável somente leitura é usado apenas para workflows de revisão.

   Você também pode usar a etapa para controlar o comportamento da tarefa. Por exemplo, criar um documento de registro automático, atribuir a tarefa a um usuário ou grupo específico, o caminho dos dados enviados, o caminho dos dados a serem pré-preenchidos e as ações padrão. Para obter informações detalhadas sobre as opções da etapa de atribuição de tarefa, consulte [fluxo de trabalho centrado na Forms no documento OSGi - Step Reference](/help/forms/using/aem-forms-workflow.md).

   ![editor de fluxo de trabalho](assets/workflow-editor.png)

   Para o exemplo do aplicativo de hipoteca, configure a etapa de atribuição de tarefa para usar um formulário adaptável somente leitura e exibir o Documento PDF quando a tarefa estiver concluída. Além disso, selecione para o grupo de usuários autorizado a aprovar a solicitação de empréstimo. Na guia **[!UICONTROL Ações]**, desative a opção **[!UICONTROL Enviar]**. Especifique uma **[!UICONTROL Variável de rota]**. Por exemplo, actionTaken. Além disso, adicione as rotas Aprovar e Rejeitar. As rotas são exibidas como ações separadas (botões) AEM Caixa de entrada. O fluxo de trabalho seleciona uma ramificação com base na ação (botão) que um usuário toca.

   É possível importar o pacote de exemplo, disponível para download no início da seção, para o conjunto completo de valores de todos os campos da etapa de atribuição de tarefa configurados como, por exemplo, aplicativo de hipoteca.

1. Arraste e solte o componente OU Dividir do navegador de etapas para o modelo de fluxo de trabalho. A Divisão OR cria uma divisão no fluxo de trabalho, após a qual apenas uma ramificação está ativa. Esta etapa permite que você introduza caminhos de processamento condicional no seu fluxo de trabalho. Você adiciona etapas de fluxo de trabalho a cada ramificação, conforme necessário.

   Abra as propriedades da Divisão OU e adicione os seguintes trechos de código à Ramificação1 e à Ramificação2. Esses trechos de código ajudam a escolher uma ramificação com base na ação do usuário AEM Caixa de entrada.

   **Trecho de código para a Ramificação 1**

   Quando um usuário toca em **[!UICONTROL Aprovar]** AEM Caixa de entrada, a Ramificação 1 é ativada.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **Trecho de código para a Ramificação 2**

   Quando um usuário toca em **[!UICONTROL Rejeitar]** AEM Caixa de entrada, a Ramificação 2 é ativada.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. Adicione outras etapas do fluxo de trabalho para criar a lógica comercial.

   Para o exemplo de hipoteca, adicione um documento de registro gerado, duas etapas de tarefa atribuídas e uma etapa de documento de sinal à Ramificação 1 do modelo, conforme exibido na imagem abaixo. Uma etapa de atribuição de tarefa é exibir e enviar **para serem documentos de empréstimo assinados ao candidato** e outro componente de atribuição de tarefa é **para exibir documentos assinados**. Além disso, adicione um componente de tarefa à ramificação 2. Ela é ativada quando um usuário toca em Rejeitar AEM Caixa de entrada.

   Para obter o conjunto completo de valores de todos os campos das etapas de atribuição de tarefa, documento da etapa de registro e etapa de assinatura de documento configuradas como, por exemplo, aplicativo de hipoteca, importe o pacote de exemplo, disponível para download no início desta seção.

   O modelo de fluxo de trabalho está pronto. Você pode iniciar o fluxo de trabalho por meio de vários métodos. Para obter detalhes, consulte [Iniciar um fluxo de trabalho centrado na Forms no OSGi](#launch).

   ![editor-de-fluxo-de-trabalho-hipoteca](assets/workflow-editor-mortgage.png)

## Criar um aplicativo de fluxo de trabalho centrado na Forms {#create-a-forms-centric-workflow-application}

O aplicativo é o formulário adaptável associado ao fluxo de trabalho. Quando um aplicativo é enviado por meio da Caixa de entrada, ele inicia o fluxo de trabalho associado. Para tornar um fluxo de trabalho do Forms disponível como um aplicativo AEM Caixa de entrada e AEM Forms App, faça o seguinte para criar um aplicativo de fluxo de trabalho:

>[!NOTE]
>
>Você deve ser um membro do grupo de administradores de fd para poder criar e gerenciar aplicativos de fluxo de trabalho.

1. Na instância do autor do AEM, vá para ![tools](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL Gerenciar aplicativo de fluxo de trabalho]** e toque em **[!UICONTROL Criar]**.
1. Na janela Criar aplicativo de fluxo de trabalho, forneça entradas para os seguintes campos e toque em **[!UICONTROL Criar]**. Um novo aplicativo é criado e está listado na tela Aplicativos de fluxo de trabalho.

<table> 
 <tbody> 
  <tr> 
   <td>Texto</td> 
   <td>Descrição</td> 
  </tr> 
  <tr> 
   <td>Título</td> 
   <td>O título é visível em AEM Caixa de entrada e ajuda os usuários a escolher um aplicativo. Mantenha-o descritivo. Por exemplo, Salva o Aplicativo de Abertura de Conta.<br /> </td> 
  </tr> 
  <tr> 
   <td>Nome </td> 
   <td>Especifique o nome do aplicativo. Todos os caracteres, exceto alfabetos, números, hífens e sublinhados, são substituídos por hífens. </td> 
  </tr> 
  <tr> 
   <td>Descrição</td> 
   <td>A descrição está visível em AEM Caixa de entrada. Forneça informações detalhadas sobre o aplicativo nos campos de descrição. Por exemplo, Finalidade do aplicativo.<br /> </td> 
  </tr> 
  <tr> 
   <td>Formulário adaptativo</td> 
   <td><p>Especifique o caminho de um formulário adaptável. Quando um usuário start um aplicativo, o formulário adaptativo especificado é exibido.</p> <p><strong>Observação</strong>: Os aplicativos de fluxo de trabalho não são compatíveis com formulários e documentos PDF que têm mais de uma página ou exigem rolagem no iPad da Apple. Quando um aplicativo é aberto no Apple iPad e o formulário adaptável ou o documento PDF é maior que uma página, os campos de formulário e o conteúdo da segunda página são perdidos.</p> </td> 
  </tr> 
  <tr> 
   <td>Grupo de acesso</td> 
   <td><p>Selecione um grupo. O aplicativo está visível em AEM Caixa de entrada somente para os membros do grupo selecionado. A opção de grupo de acesso disponibiliza para seleção todos os grupos do grupo de usuários do fluxo de trabalho. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>Preencher Serviço</td> 
   <td>Selecione um <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">serviço de preenchimento prévio</a> para o formulário adaptável.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modelo de fluxo de trabalho</td> 
   <td>Selecione um <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">modelo de fluxo de trabalho</a> para o aplicativo. Um modelo de fluxo de trabalho consiste em lógica e fluxo do processo de negócios. </td> 
  </tr> 
  <tr> 
   <td>Caminho do arquivo de dados</td> 
   <td>Especifique o caminho do arquivo de dados no repositório crx. O caminho é relativo à carga adaptável do formulário e contém o nome do arquivo de dados. Sempre inclua o nome completo do arquivo, incluindo a extensão, se aplicável. Por exemplo, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Caminho do anexo</td> 
   <td>Especifique o caminho da pasta de anexos no repositório crx. O caminho do anexo é relativo ao local da carga. Por exemplo, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Caminho do documento de registro</td> 
   <td>Especifique o caminho do Documento do arquivo de registro no repositório crx. O caminho é relativo ao local de carga do formulário adaptável. Sempre inclua o nome completo do arquivo, incluindo a extensão, se aplicável. Por exemplo, [payload]/DOR/creditcard.pdf.</td> 
  </tr> 
 </tbody> 
</table>

## Iniciar um fluxo de trabalho centrado na Forms no OSGi {#launch}

Você pode iniciar ou acionar um fluxo de trabalho centrado na Forms:

* [Envio de um aplicativo AEM Caixa de entrada](#inbox)
* [Enviar um aplicativo do aplicativo AEM Forms](#afa)

* [Enviar um formulário adaptável](#af)
* [Uso da pasta assistida](#watched)

* [Enviar uma comunicação interativa ou uma carta](#letter)

### Enviar um aplicativo AEM Caixa de entrada {#inbox}

O aplicativo de fluxo de trabalho criado está disponível como um aplicativo na Caixa de entrada. Os usuários que forem membros do grupo de usuários do fluxo de trabalho podem preencher e enviar o aplicativo que aciona o fluxo de trabalho associado. Para obter informações sobre como usar AEM Caixa de entrada para enviar aplicativos e gerenciar o tarefa, consulte [Gerenciar aplicativos e tarefas do Forms em AEM Caixa de entrada](/help/forms/using/manage-applications-inbox.md).

### Enviar um aplicativo do aplicativo AEM Forms {#afa}

O aplicativo AEM Forms sincroniza com um servidor AEM Forms e permite fazer alterações nos dados do formulário, tarefa, aplicativos de fluxo de trabalho e informações salvas (rascunhos/modelos) na sua conta. Para obter mais informações, consulte [Aplicativo AEM Forms](/help/forms/using/aem-forms-app.md) e artigos relacionados.

### Enviar um formulário adaptável {#af}

Você pode configurar as ações de envio de um formulário adaptável para start de um fluxo de trabalho ao enviar o formulário adaptável. Os formulários adaptativos fornecem a ação de envio **[!UICONTROL Invocar um fluxo de trabalho AEM]** para start de um fluxo de trabalho mediante o envio de um formulário adaptável. Para obter informações detalhadas sobre a ação de envio, consulte [Configuração da ação Enviar](/help/forms/using/configuring-submit-actions.md). Para enviar um formulário adaptável pelo aplicativo AEM Forms, ative Sincronizar com o aplicativo AEM Forms nas propriedades do formulário adaptável.

Você pode configurar um formulário adaptável para sincronizar, enviar e acionar um fluxo de trabalho do aplicativo AEM Forms. Para obter detalhes, consulte [trabalhar com um formulário](/help/forms/using/working-with-form.md).

### Usando uma pasta assistida {#watched}

Um administrador (um membro do grupo de administradores de fd) pode configurar uma pasta de rede para executar um fluxo de trabalho pré-configurado quando um usuário coloca um arquivo (como um arquivo PDF) na pasta. Depois que o fluxo de trabalho for concluído, ele poderá salvar o arquivo de resultado em uma pasta de saída especificada. Essa pasta é conhecida como [Pasta assistida](/help/forms/using/watched-folder-in-aem-forms.md). Execute o seguinte procedimento para configurar uma pasta assistida para iniciar um fluxo de trabalho:

1. Na instância do autor do AEM, vá para ![tools](assets/tools.png) **[!UICONTROL Forms > Configure Watched Folder]**. Uma lista de pastas monitoradas já configuradas é exibida.
1. Toque em **[!UICONTROL Novo]**. Uma lista de campos é exibida. Especifique um valor para os seguintes campos para configurar uma Pasta assistida para um fluxo de trabalho:

<table> 
 <tbody> 
  <tr> 
   <td>Texto</td> 
   <td>Descrição</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Nome</span></td> 
   <td>Especifique o nome da Pasta assistida. Este campo suporta apenas alfanuméricos.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Caminho</span></td> 
   <td>Especifique o local físico da Pasta assistida. Em um ambiente clusterizado, use uma pasta de rede compartilhada que esteja acessível AEM nó de cluster.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Processar arquivos usando</span></td> 
   <td>Selecione a opção <span class="uicontrol">Fluxo de trabalho </span>. </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modelo de fluxo de trabalho</span></td> 
   <td>Selecione um modelo de fluxo de trabalho.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Padrão do arquivo de saída</span></td> 
   <td>Especifique a estrutura de diretório para arquivos de saída e diretórios. Você também pode especificar um <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">padrão para arquivos de saída e diretórios</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. Toque em **[!UICONTROL Avançado]**. Especifique um valor para o campo a seguir e toque em **[!UICONTROL Criar]**. A Pasta assistida está configurada para iniciar um fluxo de trabalho. Agora, sempre que um arquivo é colocado no diretório de entrada da Pasta assistida, o fluxo de trabalho especificado é acionado.

   | Texto | Descrição |
   |---|---|
   | Filtro do mapeador de carga útil | Quando você cria uma pasta assistida, ela cria uma estrutura de pastas no repositório crx. A estrutura de pastas pode servir como carga para o fluxo de trabalho. Você pode gravar um script para mapear um Fluxo de trabalho AEM para aceitar entradas da estrutura de pastas assistida. Uma implementação pronta para uso está disponível e listada no Filtro do Mapeador de Carga. Se você não tiver uma implementação personalizada, selecione a implementação padrão. |

   A guia Avançado contém mais campos. A maioria desses campos contém um valor padrão. Para saber mais sobre todos os campos, consulte o artigo [Criar ou configurar uma pasta assistida](/help/forms/using/creating-configure-watched-folder.md).

### Enviando uma comunicação interativa ou uma letra {#letter}

Você pode associar e executar um fluxo de trabalho centrado na Forms no OSGi mediante o envio de uma comunicação interativa ou de uma carta. Os workflows de gerenciamento de correspondência são usados para o pós-processamento de comunicações e cartas interativas. Por exemplo, enviar emails, imprimir, enviar fax ou arquivar letras finais. Para obter etapas detalhadas, consulte [Pós-processamento de comunicações e cartas interativas](/help/forms/using/submit-letter-topostprocess.md).

## Configurações adicionais {#additional-configurations}

### Configurar o serviço de email {#configure-email-service}

Você pode usar as etapas Atribuir Tarefa e Enviar e-mail de Workflows AEM para enviar um e-mail. Execute as seguintes etapas para especificar os servidores de e-mail e outras configurações necessárias para enviar e-mail:

1. Vá para AEM gerenciador de configuração em `https://[server]:[port]/system/console/configMgr`.
1. Abra a configuração **[!UICONTROL Day CQ Mail Service]**. Especifique um valor para os campos **[!UICONTROL nome do host do servidor SMTP]**, **[!UICONTROL porta do servidor SMTP,]** e **[!UICONTROL &quot;From&quot; address]**. Clique em **[!UICONTROL Salvar]**.
1. Abra a configuração **[!UICONTROL Externalizador de links Day CQ]**. No campo **[!UICONTROL Domínios]**, especifique o nome do host/endereço IP real e o número da porta para instâncias locais, de autor e de publicação. Clique em **[!UICONTROL Salvar]**.

### Expurgar instâncias de fluxo de trabalho {#purge-workflow-instances}

Minimizar o número de instâncias do fluxo de trabalho aumenta o desempenho do motor de workflow, para que você possa expurgar regularmente as instâncias do fluxo de trabalho concluídas ou em execução do repositório. Para obter informações detalhadas, consulte [Expurgação Regular de Instâncias de Fluxo de Trabalho](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
