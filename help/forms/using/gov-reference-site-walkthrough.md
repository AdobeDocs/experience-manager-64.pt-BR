---
title: Apresentação do site de referência We.Gov
seo-title: We.Gov reference site walkthrough
description: Consulte a apresentação do site de referência We.Gov para entender como o AEM Forms ajuda os governos a gerenciar informações individuais.
seo-description: See the We.Gov reference site walkthrough to understand how AEM Forms helps governments manage individual information.
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
exl-id: c8ebd18b-fa24-4264-bd17-f553a2a784d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2753'
ht-degree: 0%

---

# Apresentação do site de referência We.Gov {#we-gov-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Pré-requisitos {#pre-requisite}

Configure seu site de referência We.Gov conforme descrito no [Configurar e configurar sites de referência do AEM Forms](/help/forms/using/setup-reference-sites.md).

## Cenário do site de referência {#reference-site-scenario}

We.Gov é uma organização estatal que permite que pais adotivos se inscrevam para receber apoio infantil caso tenham adotado uma criança. O site gerencia o seguinte:

* Elegibilidade do candidato, da empresa-mãe adotiva
* Dados pessoais e profissionais do requerente (se este for elegível para apoio à criança)
* Dados pessoais da criança adotada

   O requerente pode fornecer detalhes relativamente a mais de uma criança
* Dados da conta bancária do requerente em que este pode receber prestações de assistência a crianças
* Cobrança da taxa de pedido
* Avaliação do pedido
* Aprovação do pedido
* Comunicação automatizada ao requerente

Uma vez apresentado o pedido e paga a sua taxa, o requerente recebe um e-mail da organização com o aviso de recepção do pedido apresentado.

A organização We.Gov recebe o aplicativo. A organização avalia a aplicação e aprova as aplicações genuínas.

Após a aprovação do pedido, o requerente recebe um email do site We.Gov. O **Exibir documento** na opção email vincula-se a um documento com os detalhes de inscrição do candidato.

O infográfico abaixo mostra o fluxo de trabalho passo a passo do cenário do site de referência We.Gov .

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

O cenário envolve as seguintes personas:

* Sarah Rose, a mãe adotiva que pede apoio para crianças
* Joe, a criança adotada
* Gloria Rios, chefe da divisão de aprovação, We.Gov
* Conard Simms, o agente de campo que cuida da avaliação de aplicativos

## Sarah inicia sua verificação de elegibilidade {#sarah-initiates-her-eligibility-check}

Um candidato pode verificar a elegibilidade para solicitar benefícios de suporte filho. O site permite que os usuários respondam perguntas para permitir que determinem se seu aplicativo está qualificado para benefícios. Sarah, uma mãe adotiva, é candidata potencial para isso. O formulário de elegibilidade faz parte dos serviços de Aplicativo de Suporte à Criança do site We.Gov . Para verificar sua qualificação, Sarah clica em **[!UICONTROL Suporte à Criança]** no site We.Gov . Na página Suporte à Criança, Sarah clica em **[!UICONTROL Verificar sua qualificação]**.

Além da abordagem acima, Sarah pode clicar em **[!UICONTROL Introdução]** na página inicial. Sarah é navegada até a página Todos os aplicativos, onde ela pode clicar em Aplicar em **[!UICONTROL Aplicativo para Serviços de Suporte à Criança]**. Sarah é levada ao cheque de elegibilidade.

Na página Verificar Elegibilidade para Suporte à Criança, à Sarah é feito um conjunto de perguntas para determinar sua elegibilidade para benefícios de suporte à criança. Através do conjunto de perguntas, ela é questionada:

* Se for a pessoa que guarda a criança
* Se ela e a criança viverem no estado de GX
* A faixa etária da criança e a educação da criança.

Sarah responde essas perguntas, e sua qualificação é validada. Suas respostas determinam se ela é elegível para apoio infantil.

Sarah é informada de que ela está qualificada para apoio infantil, e a taxa de inscrição é de US$ 25.

### Como funciona {#how-it-works}

A qualificação de Sarah é validada por meio de uma barreira de elegibilidade criada usando o editor de regras. O editor de regras permite que você especifique as condições que são cumpridas antes que um candidato possa preencher o formulário de solicitação. Quando Sarah, a candidata, preenche todas as condições de elegibilidade, acessa o formulário de candidatura.

A verificação de elegibilidade faz parte do formulário adaptável do aplicativo de suporte para filhos. A regra valida a qualificação quando:

* O requerente é um responsável pela custódia
* O requerente e a criança permanecem no estado de GX
* O requerente tem o principal cuidado diário da criança
* A idade da criança receber cobertura de serviços de apoio está abaixo dos 16 anos.

### Veja você mesmo {#see-it-yourself}

No seu navegador, abra `https://<hostname>:<PublishPort>/content/we-gov/en.html`. No site We.Gov, clique em Suporte ao filho. Na página Suporte à criança, clique em Verificar sua elegibilidade.

Para ver as regras:

1. Abra o formulário no modo de edição na instância do autor. URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. Selecione um componente e clique em ![editar regras](assets/edit-rules.png).

   O Editor de regras é aberto listando todas as regras aplicadas no formulário.

1. No painel lateral esquerdo, clique em Regras `passMsg` e `failMsg` para entender como a verificação de qualificação funciona.

## Sarah dá início ao seu pedido de apoio a crianças {#sarah-starts-her-application-for-child-support}

Sarah clica **[!UICONTROL Iniciar Aplicativo]** depois de ter sido informada da sua elegibilidade para apoio a crianças.\
Na página Application For Child Support Services , Sarah fornece detalhes nas seguintes seções:

* **[!UICONTROL Sobre o Candidato]**: Deixe Sarah fornecer seus detalhes nesta seção.

* **[!UICONTROL Informações sobre filhos]**: Deixe Sarah fornecer a informação da criança, que está coberta por serviços de apoio.

* **[!UICONTROL Pagamento]**: Deixe Sarah fornecer seus detalhes bancários nos quais We.Gov pode depositar uma compensação mensal de apoio.

* **[!UICONTROL Pagamento de taxa]**: Deixe Sarah fornecer os detalhes do cartão de crédito para pagar a taxa do pedido.

Por padrão, Sarah é levada ao **[!UICONTROL Sobre o Candidato]** seção.

![Aplicativo de suporte para crianças no desktop](assets/desktop.png)

A qualquer momento, Sarah pode clicar em **[!UICONTROL Volte mais tarde]** e retome com o seu pedido. Quando ela clica **[!UICONTROL Volte mais tarde]**, seu progresso é salvo como um rascunho e ela tem a opção de enviar o rascunho por email.

Quando ela clica **[!UICONTROL Enviar Email]**, ela receberá um email com um link para o rascunho de seu formulário.

O formulário de suporte para filhos no site We.Gov usa formulários adaptáveis. Ela pode usar o link em seu email e preencher o formulário no dispositivo móvel.

>[!NOTE]
>
>O fluxo de trabalho resume-from-email funciona somente com usuários conectados. Na situação do site de referência, verifique se a usuário Sarah Rose está adicionada. As credenciais de login da Sarah são `srose/password`.

![mob1](assets/mob1.png)

Sarah pode fornecer detalhes em qualquer seção, mas a taxa do aplicativo é aceita somente após fornecer as informações necessárias em todas as seções. Uma aplicação está incompleta sem pagamento de taxa e são necessários campos marcados com um asterisco.

### <strong>Sarah fornece informações.</strong> {#strong-sarah-provides-her-information-strong}

Depois que Sarah clicar **[!UICONTROL Iniciar Aplicativo]**, é encaminhada para a seção Informações do Requerente da página de Serviços de Apoio à Criança. Em Informações do Candidato, Sarah navega pelas guias e fornece suas informações pessoais para o aplicativo. Ela clica **[!UICONTROL Próximo]** para navegar pelas guias.

Em Informações sobre o Requerente, solicita-se-lhe que forneça informações detalhadas nos seguintes guias:

* **[!UICONTROL Informações básicas]**

Em Basic Information (Informações básicas), Sarah fornece a prova de identificação e suas informações pessoais. As informações pessoais de Sarah incluem o nome, a ID de email e o número da segurança social.

* **[!UICONTROL Relação]**

   Sob o Relacionamento, Sarah insere informações sobre seu estado civil.

* **[!UICONTROL Informações adicionais]**

   Em Additional Information (Informações adicionais), Sarah insere um número de ID, sua data de nascimento e endereço atual e número de telefone.

### Sarah fornece informações sobre crianças {#sarah-provides-child-information}

Depois que Sarah fornecer suas informações pessoais e cliques **[!UICONTROL Próximo]**, ela é levada à seção Informações da Criança .

Na seção Informações sobre crianças , ela fornece os seguintes detalhes:

* Número de filhos a reclamar serviços de apoio a crianças
* Nome do filho, número da segurança social, data de nascimento e local de nascimento

Se Sarah escolher mais de uma criança, ela recebe formulários extras habilitados com os mesmos detalhes para preencher.\
Sarah escolhe seu único filho, Joe, e digita seu nome.

### Sarah fornece informações sobre pagamento {#sarah-provides-payment-information}

Depois que Sarah fornece informações sobre a criança adotada (ou crianças) e os cliques **[!UICONTROL Próximo]**, ela é levada ao **[!UICONTROL Informações de Pagamento]** seção.

Na seção Informações sobre o Pagamento, ela fornece os detalhes da conta bancária na qual pode receber os benefícios do apoio filho.\
Ela insere seu número de conta bancária de 10 dígitos.

## Sarah paga a taxa de inscrição e assina o formulário {#sarah-pays-the-application-fee-and-signs-the-form}

Depois que Sarah concordar com os termos e condições do pedido, ela paga a taxa de 25 dólares. É necessária uma taxa de candidatura para processar o seu pedido.\
Sarah digita os detalhes e cliques do cartão de crédito **[!UICONTROL Pagar Agora]**. Depois de pagar as tarifas, uma versão PDF do aplicativo é exibida com um campo de assinatura.

![sinal de sarah-1](assets/sarah-sign-1.png)

Sarah pode optar por digitar, usar draw para escrever à mão, inserir uma imagem de assinatura ou usar a tela sensível ao toque de seu celular para desenhar sua assinatura. Sarah digita o nome e clica em Clicar para assinar.

Seu pedido é enviado para o site We.Gov .

### <strong>Sarah recebe um e-mail de confirmação</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Depois que Sarah paga a taxa de inscrição, ela recebe um e-mail de confirmação do site We.Gov .\
We.Gov processa o pedido, e Sarah é informada que ela receberá uma compensação mensal após a aprovação de seu pedido.

![sarah-ack-email](assets/sarah-ack-email.png)

### Como funciona {#how-it-works-1}

O aplicativo de suporte secundário usa uma combinação de layouts de painel, como a guia superior, o assistente e a opção de acordo para criar a experiência. Ele usa um modelo de formulário chamado Modelo Filho We.Gov.

O candidato pode se mover entre seções para preencher diferentes componentes do formulário. Quando o requerente preenche o formulário, o apresenta, concorda com os termos e condições e paga a taxa, é iniciado um fluxo de trabalho personalizado. O fluxo de trabalho personalizado envia um email automatizado ao candidato confirmando o envio do aplicativo. O pedido é transmitido ao serviço competente da organização para verificação e aprovação.

O layout do formulário é especificado no Tema de Serviço de Suporte a Filho do Governador. O estilo inclui o estilo do componente, o plano de fundo da página, a formatação do estado de erro dos componentes e os estilos de fonte.

A verificação de elegibilidade usa regras especificadas no formulário. Ele usa as verificações de validade especificadas abaixo:

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### Veja você mesmo {#see-it-yourself-1}

No seu navegador, abra `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` e preencha as informações necessárias. Ao enviar o pedido após preencher as informações necessárias, pagar as taxas e assinar o documento, você receberá o email de confirmação.

Consulte o modelo filho We.Gov aqui: `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

Veja o tema aqui: `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

Para ver todas as regras, execute as seguintes etapas:

1. Abra o formulário no modo de criação.

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. Selecione um componente e toque em ![editar regras](assets/edit-rules.png). Todas as regras são listadas no editor de regras, incluindo as regras listadas acima.

## Gloria recebe o pedido {#gloria-receives-the-application}

Gloria, chefe de aprovações em We.Gov, pode visualizar, aprovar ou rejeitar os aplicativos enviados. AEM Caixa de entrada permite que ela veja todos os aplicativos enviados em um único local.

### Como funciona {#how-it-works-2}

Quando Sarah preenche e envia o aplicativo de suporte para crianças, um PDF ou Documento de registro do aplicativo é criado e enviado para a caixa de entrada de Gloria Rios. Gloria pode exibir o aplicativo enviado e aceitá-lo ou rejeitá-lo.

### Veja você mesmo {#see-it-yourself-2}

Abrir página `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. Na página , toque em **[!UICONTROL Fazer logon]**, selecione o **[!UICONTROL Efetuar logon como representante]** , faça logon na caixa de entrada do AEM usando grios/password como nome de usuário/senha de Gloria Rios. O aplicativo de suporte filho é exibido. Para obter informações sobre como usar AEM Caixa de entrada para tarefas de fluxo de trabalho centradas em formulários, consulte [Gerenciar aplicativos e tarefas do Forms na Caixa de entrada AEM](/help/forms/using/manage-applications-inbox.md).

![Caixa de entrada de Gloria no site We.Gov](assets/gloria-inbox.png)

Gloria pode ver, aprovar ou rejeitar o aplicativo no painel do aplicativo.

### Como funciona {#how-it-works-3}

Gloria, chefe de aprovações no We.Gov, abre a AEM caixa de entrada. Ela vê uma tarefa de revisão em sua lista de tarefas. Ela abre e exibe a tarefa de revisão.

Ela vê um PDF do formulário preenchido com detalhes que Sarah inseriu junto com os documentos que Sarah carregou.\
Gloria pode aprovar ou rejeitar o pedido. No entanto, clique em Gloria **[!UICONTROL Avaliação necessária]** para avaliar o pedido.

![gloria-send-assessment](assets/gloria-sends-assessment.png)

O aplicativo da Sarah é um ponto de partida no fluxo de trabalho da AEM. Ele inicia o fluxo de trabalho AEM quando o formulário de aplicativo de suporte filho é enviado. O fluxo de trabalho do AEM cria uma tarefa para Gloria, que é mostrada em sua AEM caixa de entrada. Quando Gloria solicita uma avaliação no local, uma nova tarefa é criada para o agente de campo.

### Veja você mesmo {#see-it-yourself-3}

Se a configuração estiver concluída, o fluxo de trabalho AEM será iniciado imediatamente após o envio do formulário. Faça logon na caixa de entrada usando as credenciais de Gloria.

Acesse a caixa de entrada em https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-gov/en.html. Na página , toque em **[!UICONTROL Fazer logon]**, selecione o **[!UICONTROL Efetuar logon como representante]** caixa de seleção use as credenciais padrão de Gloria:

* Nome de usuário: grios
* Senha: senha

Em sua caixa de entrada de AEM, o aplicativo de Sarah é adicionado como uma tarefa de revisão. Selecione a tarefa e clique em **Avaliação necessária** para prosseguir para a próxima etapa.

### O Painel obtém a tarefa Avaliação {#conard-assessment-task}

Quando Gloria clicar **[!UICONTROL Avaliação necessária]**, o Conard obtém a tarefa de revisão na Caixa de entrada de AEM. A tarefa é a próxima etapa no fluxo de trabalho AEM definido no modelo de fluxo de trabalho. Ele vê a tarefa de revisão e a abre.

A placa obtém a tarefa de avaliação do candidato conforme mostrado abaixo.

![caixa de entrada de linha](assets/conrad-inbox.png)

A avaliação de suporte filho é um formulário associado à tarefa. Ele consegue os detalhes de Sarah, junto com os documentos de apoio (anexados em detalhes da tarefa). O Conard preenche o formulário de avaliação no campo em um dispositivo e envia para reavaliação.

O Conard verifica todos os detalhes fornecidos pela Sarah e Sarah assina a avaliação. O AEM Forms pode pegar a localização e o carimbo de data e hora e adicioná-los à assinatura.

![submeter a reavaliação](assets/submit-for-re-evaluation.png)

Cliques no cartão **[!UICONTROL Enviar para Reavaliação]** e o workflow AEM envia a avaliação para a organização We.Gov .

### Como funciona {#how-it-works-4}

Quando Gloria solicita uma avaliação, a próxima etapa AEM fluxo de trabalho é iniciada e a tarefa de avaliação é adicionada na caixa de entrada do Conard. O Painel de controle é a persona de trabalho de campo.

O Conard visita o local de Sarah, verifica se as informações fornecidas pela Sarah são genuínas e preenche o formulário de avaliação. O Conard pode acessar um PDF do formulário completo que Sarah preencheu.

### Veja você mesmo {#see-it-yourself-4}

Abra a caixa de entrada AEM em seu tablet e use as credenciais do Conard para fazer logon.

As credenciais padrão do Conard são:

* Nome de usuário: csimms
* Senha: senha

Você pode ver uma nova tarefa de Solicitação de Avaliação adicionada na caixa de entrada. Envie a avaliação concluída e prossiga para a próxima etapa.

### Gloria analisa a avaliação e aprova o pedido {#gloria-reviews-the-assessment-and-approves-the-application}

Depois que a Conard submete a avaliação, Gloria vê uma tarefa de Revisão em sua caixa de entrada. Ela seleciona e abre **[!UICONTROL Revisão]**.

![gloriainbox-1](assets/gloriainbox-1.png)

Em Detalhes da Tarefa, Gloria vê a Última Ação Tomada como &quot;Enviar para Reavaliação&quot; (pelo Conard). Gloria observa que a Conard Simms avaliou o pedido.

![gloriaaproves](assets/gloriaapproves.png)

### Como funciona {#how-it-works-5}

Depois que a Conard submete a avaliação, Gloria vê uma tarefa de Revisão em sua caixa de entrada. Ela seleciona e abre a opção Revisar. Em Detalhes da Tarefa, Gloria vê o comentário de avaliação feito pelo Conard, que é &quot;Tudo encontrado em ordem&quot;.

Gloria aprova o pedido.

### Veja você mesmo {#see-it-yourself-5}

Abra a caixa de entrada e faça logon usando as credenciais de Gloria. Uma nova tarefa chamada Revisar é exibida na caixa de entrada.

Abra a tarefa para ver o status da Última ação realizada. Com base na avaliação, aprove o pedido.

## Sarah recebe um email de aprovação {#sarah-receives-an-approval-email}

Depois que Gloria aprovar o aplicativo, Sarah recebe um email do We.Gov informando que seu aplicativo foi aprovado.

O **[!UICONTROL Exibir documento]** nos links de email para seus detalhes de inscrição. Sarah clica **[!UICONTROL Exibir documento.]**

![approval-enrolation-kit-email](assets/approval-enrolment-kit-email.png)

O documento de inscrição lista detalhes como a ID de referência, o filho coberto, a data de início, o número da conta bancária, a frequência de pagamento e a quantia de pagamento.

![sarah-enrollment-details](assets/sarah-enrollment-details.png)

Sarah pode visualizar os documentos que carregou na mesma página.

![documentos carregados](assets/uploaded-documents.png)

### Como funciona {#how-it-works-6}

Quando Gloria aprova o aplicativo, Sarah recebe um email automatizado com um link para o documento de inscrição.

O documento de inscrição é uma comunicação interativa e pode ser visualizado em qualquer dispositivo. Ele contém detalhes do serviço de apoio à criança e informações fornecidas pela Sarah.

### Veja você mesmo {#see-it-yourself-6}

Verifique o cliente de email configurado para o email automatizado com um link para o documento de inscrição.

Como alternativa, para ver o documento em seu navegador, abra: `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov analisa o desempenho do aplicativo {#we-gov-analyzes-the-performance-of-the-application}

O We.Gov, de tempos em tempos, analisa o desempenho do aplicativo de serviços de suporte para filhos para verificar se os clientes podem estar enfrentando problemas. Eles usam essa análise para tomar decisões informadas sobre as alterações necessárias no aplicativo de serviços de suporte à criança para melhorar a experiência do usuário, reduzir a taxa de abandono de formulários e, assim, melhorar a conversão. Eles aproveitam a integração do AEM Forms com o Adobe Analytics para análise. A imagem a seguir descreve o painel de análise.

![child-support-analytics-dashboard](assets/child-support-analytics-dashboard.png)

### Como funciona {#how-it-works-7}

As métricas de desempenho para o formulário de aplicativo dos serviços de suporte filho são rastreadas com o Adobe Analytics. Para obter mais informações sobre como configurar o Adobe Analytics e visualizar relatórios, consulte [Configuração do Analytics para formulários e documentos](/help/forms/using/configure-analytics-forms-documents.md).

### Veja você mesmo {#see-it-yourself-7}

Para visualizar e explorar o relatório de análise, estamos fornecendo dados de lançamento para o aplicativo de serviços de suporte para filhos no site de referência. Antes de usar os dados de propagação, consulte [Configurar o Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Execute as seguintes etapas na instância do autor para exibir o relatório com os dados de propagação:

1. Ir para **[!UICONTROL Forms &amp; Documents]** Interface do usuário em https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Clique para abrir o **We.Gov** Pasta.
1. Selecionar **[!UICONTROL Aplicativo para Serviços de Suporte à Criança]** formulário adaptável e clique em **[!UICONTROL Ativar o Analytics]** na barra de ferramentas.

1. Selecione o formulário novamente e clique em **[!UICONTROL Relatório do Analytics]** na barra de ferramentas para gerar o relatório. Você vê um relatório em branco inicialmente.

Para gerar relatórios de análise com dados de propagação:

1. No navegador de endereços do CRXDE lite, digite: **/apps/we-gov/demo-artifact/analyticsTestData/Child support service Dados de teste do Analytics**
1. Os dados seed são selecionados na estrutura do diretório do lado esquerdo.
1. Clique duas vezes no arquivo selecionado para abrir o conteúdo no painel lateral direito.
1. Copie todo o conteúdo do arquivo de dados de teste.
1. No CRXDE, navegue até: **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevendays**
1. No campo analytics data em Properties, cole o conteúdo copiado do arquivo de dados de teste.
1. Agora gere o relatório de análise novamente para **[!UICONTROL Aplicativo para Serviços de Suporte à Criança]**. Você pode ver os dados de propagação no relatório gerado.
