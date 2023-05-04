---
title: Apresentação do site de referência de autoatendimento do funcionário
seo-title: Employee self-service
description: O site de referência do AEM Forms mostra como as organizações podem aproveitar os recursos do AEM Forms para implementar o recrutamento de funcionários e os fluxos de trabalho de autoatendimento.
seo-description: AEM Forms reference site showcases how organizations can leverage AEM Forms features to implement employee recruitment and self-service workflows.
uuid: ecc98e0d-c964-44dc-b219-9ebe92632d22
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d2695f71-5126-477c-ae6b-a964fb55728b
exl-id: 7fbdd976-5a70-4af4-b449-7c2d6bcfd915
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1659'
ht-degree: 0%

---

# Apresentação do site de referência de autoatendimento do funcionário {#employee-self-service-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Pré-requisitos {#prerequisite}

Configure os sites de referência conforme descrito em [Configurar e configurar sites de referência do AEM Forms](/help/forms/using/setup-reference-sites.md).

## Visão geral {#overview}

Os sistemas de autoatendimento dos funcionários, geralmente hospedados na Intranet da empresa, dão aos funcionários acesso a uma variedade de informações e serviços que eles podem aproveitar de suas mesas. Ele capacita e dá controle total aos funcionários para executar ações, como acessar seus detalhes de emprego, solicitar licença e enviar relatórios de despesas. Por outro lado, ajuda as organizações a melhorar a eficiência dos processos e a reduzir os custos, mantendo os funcionários informados e envolvidos.

O site de referência de autoatendimento do funcionário mostra como você pode aproveitar o AEM Forms para implementar o sistema de autoserviços do funcionário em sua organização.

>[!NOTE]
>
>Os casos de uso de autoatendimento do funcionário estão disponíveis nos sites de referência We.Finance e We.Gov . Os exemplos, imagens e descrições usados nas orientações usam o site de referência We.Finance. No entanto, você também pode executar esses casos de uso e revisar artefatos usando We.Gov. Para isso, é necessário substituir **cofinanciamento** com **we-gov** nos URLs mencionados.

## Apresentação do questionário de conflito de interesses {#conflict-of-interest-questionnaire-walkthrough}

Organizações de tempos em tempos pedem aos funcionários que enviem um questionário do Conflito de Interesses para identificar atividades externas ou relações pessoais de seus funcionários que podem potencialmente entrar em conflito com a organização.

O Departamento de Conformidade da organização de Sarah pediu aos funcionários que enviassem o questionário Conflict of Interest .

### Sarah submete o questionário Conflict of Interest {#sarah-submits-the-conflict-of-interest-questionnaire}

Sarah vai ao portal de sua organização, faz logon e clica em Funcionário para acessar o painel do funcionário. Ela encontra o questionário Conflict of Interest no painel de funcionários e clica em **[!UICONTROL Aplicar]**.

![we-finance-home](assets/we-finance-home.png)
**Figura:** *Portal da organização*

![employee-dashboard](assets/employee-dashboard.png)
**Figura:** *Painel de funcionários*

Sarah navega o formulário usando o botão Next e lê as seções Introdução e Definição. Responde às perguntas da seção Perguntas. Por último, assina e envia o questionário.

O portal da organização e o questionário são responsivos e amigáveis para dispositivos móveis. O fluxo de trabalho a seguir mostra como Sarah navega e envia o questionário para seu dispositivo móvel.

![conflict-form-on-mobile](assets/conflict-form-on-mobile.png)

**Como funciona**

O portal da organização e o painel do funcionário são páginas do AEM Sites. O painel lista várias opções de autoatendimento, como o questionário Conflict of Interest . O botão Aplicar é vinculado a um formulário adaptável.

O formulário adaptável usa regras para mostrar informações ocultas com base na resposta fornecida na guia Perguntas . Além disso, o formulário usa o componente Scribble para assinar na guia Declaração. Revise o formulário adaptável em `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/conflict-of-interest.html`.

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` e fazer logon usando `srose/srose` como nome de usuário/senha para Sarah. Clique em **[!UICONTROL Funcionário]** para acessar o painel e, em seguida, clique em **[!UICONTROL Aplicar]** sobre o questionário sobre conflitos de interesses. Revisar e enviar o questionário.

### Gloria analisa e aprova a apresentação do questionário Conflict of Interest {#gloria-reviews-and-approves-the-conflict-of-interest-questionnaire-submission}

O questionário Conflict of Interest apresentado por Sarah é atribuído à Gloria Rios para reexame. Gloria trabalha como oficial de conformidade na organização. Gloria entra em sua Caixa de entrada de AEM e analisa as tarefas atribuídas a ela. Ela aprova o questionário enviado por Sarah e completa a tarefa.

![caixa de entrada de conflitos](assets/conflict-inbox.png)
**Figura:** *Caixa de entrada de Gloria*

![aprovado por conflito](assets/conflict-approved.png)
**Figura:** *Abrir tarefa*

**Como funciona**

A ação de envio no questionário Conflito de interesse aciona um fluxo de trabalho que cria uma tarefa na caixa de entrada de Gloria para aprovação. Revise o Forms Workflow em `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-conflict-of-interest.html`

![funcionário-autoatendimento-site de referência](assets/employee-self-service-reference-site.png)

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` e fazer logon usando `grios/password` como nome de usuário/senha para Gloria Rios. Abra a tarefa criada para o questionário Conflict of Interest e aprove-a.

## Apresentação do aplicativo de cartão corporativo {#corporate-card-application-walkthrough}

Sarah viaja muito por negócios e precisa de um cartão de crédito corporativo para pagar suas contas em movimento. Ela se candidata a um cartão corporativo por meio do portal de funcionários de sua organização.

### Sarah submete o pedido de cartão corporativo {#sarah-submits-the-corporate-card-application}

Sarah vai ao portal de sua organização, faz login e clica **[!UICONTROL Funcionário]** para acessar o painel de funcionários. Ela encontra o aplicativo Cartões corporativos no painel do funcionário e clica em **[!UICONTROL Aplicar]**.

![we-finance-home-1](assets/we-finance-home-1.png)
**Figura:** *Portal da organização*

![employee-dashboard-1](assets/employee-dashboard-1.png)
**Figura:** *Painel de funcionários*

Ela clica **[!UICONTROL Aplicar]** no aplicativo Cartões corporativos. Um aplicativo de página única é aberto. Ela preenche todos os detalhes e clica **[!UICONTROL Aplicar]** apresentar o pedido.

![forma de cartão](assets/card-form.png)

**Como funciona**

O portal da organização e o painel do funcionário são páginas do AEM Sites. O painel lista várias opções de autoatendimento, como o aplicativo de cartão corporativo. O botão Aplicar no aplicativo está vinculado a um formulário adaptável.

O formulário adaptável para aplicativos de cartão corporativo é um formulário adaptável simples, de uma página e responsivo. Ele usa componentes básicos de formulário adaptável, como texto, telefone, caixa numérica e etapa numérica. Revise o formulário adaptável em:\
`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/corporate-card.html`.

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` e fazer logon usando `srose/srose` como nome de usuário/senha para Sarah. Clique em **[!UICONTROL Funcionário]** para acessar o painel e, em seguida, clique em **[!UICONTROL Aplicar]** no aplicativo de cartão corporativo. Preencha os detalhes e envie o pedido.

### Gloria revisa e aprova o aplicativo de cartão corporativo {#gloria-reviews-and-approves-the-corporate-card-application}

O pedido de cartão corporativo enviado por Sarah é atribuído à Gloria Rios para revisão. Gloria entra em sua Caixa de entrada de AEM e analisa as tarefas atribuídas a ela. Ela aprova o pedido enviado por Sarah e conclui a tarefa.

![caixa de entrada do cartão corporativo](assets/corporate-card-inbox.png)
**Figura:** *Caixa de entrada de Gloria*

![cartão corporativo aprovado](assets/corporate-card-approved.png)
**Figura:** *Abrir tarefa*

**Como funciona**

O fluxo de trabalho de envio no aplicativo de Cartão corporativo aciona um fluxo de trabalho Forms que cria uma tarefa na caixa de entrada de Gloria para aprovação. Revise o Forms Workflow em `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-corporate-card.html`

![modelo de fluxo de trabalho do cartão corporativo](assets/corporate-card-workflow-model.png)

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` e fazer logon usando `grios/password` como nome de usuário/senha para Gloria Rios. Abra a tarefa criada para o aplicativo Corporate Card e aprove-a.

## Apresentação do relatório de despesas {#expense-report-submission-walkthrough}

Como Sarah gasta durante viagens de negócios, ela precisa enviar relatórios de despesas para aprovação. A opção de autoatendimento em sua organização permite que ela envie o relatório de despesas online.

### Sarah submete a aplicação Relatório de Despesas {#sarah-submits-the-expense-report-application}

Sarah vai ao portal de sua organização, faz login e clica **[!UICONTROL Funcionário]** para acessar o painel de funcionários. Ela encontra o aplicativo Relatório de Despesas no painel do funcionário e clica em **[!UICONTROL Aplicar]**.

![we-finance-home-2](assets/we-finance-home-2.png)
**Figura:** *Portal da organização*

![employee-dashboard-2](assets/employee-dashboard-2.png)
**Figura:** *Painel de funcionários*

Ela clica **[!UICONTROL Aplicar]** no aplicativo Relatório de Despesas. Um formulário de aplicativo é aberto, com duas guias: Nome do relatório e Detalhes do relatório. O **+** na guia Detalhes do relatório permite que ela adicione mais de despesas em um relatório.

O portal da organização e os aplicativos são responsivos e compatíveis com dispositivos móveis. O fluxo de trabalho a seguir mostra como Sarah navega e envia o relatório de despesas para seu dispositivo móvel.

![relatório de despesas em dispositivos móveis](assets/expense-report-on-mobile.png)

**Como funciona**

O portal da organização e o painel do funcionário são páginas do AEM Sites. O painel lista várias opções de autoatendimento, como o aplicativo Relatório de Despesas. O botão Aplicar é vinculado a um formulário adaptável.

As guias Nome do relatório e Detalhes do relatório no formulário adaptável são componentes do Painel. O painel Detalhes do relatório contém o painel Despesas. É um painel repetível que permite adicionar vários dispêndios no relatório. Revise o formulário adaptável e suas configurações em `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/expense-report.html`.

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` e fazer logon usando `srose/srose` como nome de usuário/senha para Sarah. Clique em **[!UICONTROL Funcionário]** para acessar o painel e, em seguida, clique em **[!UICONTROL Aplicar]** no aplicativo Relatório de Despesas. Preencha os detalhes e envie o pedido.

### Gloria revisa e aprova o relatório de despesas {#gloria-reviews-and-approves-the-expense-report}

O relatório de despesas enviado por Sarah é atribuído a Gloria Rios para revisão. Gloria entra em sua Caixa de entrada de AEM e analisa as tarefas atribuídas a ela. Ela aprova o pedido enviado por Sarah e conclui a tarefa.

![caixa de entrada do relatório de despesas](assets/expense-report-inbox.png)
**Figura:** *Caixa de entrada de Gloria*

![relatório de despesas aprovado](assets/expense-report-approved.png)
**Figura:** *Abrir tarefa*

**Como funciona**

O fluxo de trabalho de envio no aplicativo Relatório de despesas aciona um fluxo de trabalho Forms que cria uma tarefa na caixa de entrada de Gloria para aprovação. Revise o Forms Workflow em `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-expense-report-workflow.html`

![modelo de fluxo de trabalho de relatório de despesas corporativas](assets/corporate-card-expense-report-workflow-model.png)

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` e fazer logon usando `grios/password` como nome de usuário/senha para Gloria Rios. Abra a tarefa criada para o aplicativo Relatório de Despesas e aprove-a.

## Deixar Apresentação do Aplicativo {#leave-application-walkthrough}

Sarah está planejando umas férias da família no mês que vem e quer se candidatar por uma semana de licença do trabalho.

### Sarah submete o pedido de licença {#sarah-submits-the-leave-application}

Sarah vai ao portal de sua organização, faz login e clica **[!UICONTROL Funcionário]** para acessar o painel de funcionários. Ela encontra o aplicativo de licença no painel do funcionário e clica em **[!UICONTROL Aplicar]**.

![we-finance-home-3](assets/we-finance-home-3.png)
**Figura:** *Portal da organização*

![employee-dashboard-3](assets/employee-dashboard-3.png)
**Figura:** *Painel de funcionários*

O aplicativo Leave é aberto com o nome da Sarah e a ID do funcionário pré-preenchido no formulário. Ele também mostra o equilíbrio e a história de suas férias. Ela preenche os detalhes da licença e submete o pedido de aprovação.

O portal da organização e os aplicativos são responsivos e compatíveis com dispositivos móveis. O fluxo de trabalho a seguir mostra como Sarah navega e envia o aplicativo para seu dispositivo móvel.

![forma livre em dispositivo móvel](assets/leave-form-on-mobile.png)

**Como funciona**

O portal da organização e o painel do funcionário são páginas do AEM Sites. O painel lista várias opções de autoatendimento, como o aplicativo de licença. O botão Aplicar é vinculado a um formulário adaptável.

O formulário adaptável para o aplicativo de licença é baseado no Modelo de Dados de Formulário de Folhas de Funcionário. Na seção Saldo de Saída, a tabela de saldo de saída é preenchida usando o `getLeavesOf` Serviço de Modelo de dados de formulário. Os campos Start e End dates usam regras para validar se os valores de data são iguais ou posteriores à data atual. A duração da licença é calculada usando o `calcBusinessDays` .

Você pode revisar o formulário adaptável e o Modelo de dados de formulário nos seguintes locais:

`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/leave-application.html`

`https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/db`

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` e fazer logon usando `srose/srose` como nome de usuário/senha para Sarah. Clique em **[!UICONTROL Funcionário]** para acessar o painel e, em seguida, clique em **[!UICONTROL Aplicar]** no Aplicativo de Sair. Preencha os detalhes e envie o pedido.

### Gloria revisa e aprova o pedido de licença {#gloria-reviews-and-approves-the-leave-application}

O pedido de licença enviado por Sarah é atribuído a Gloria Rios para revisão. Gloria entra em sua Caixa de entrada de AEM e analisa as tarefas atribuídas a ela. Ela aprova o pedido enviado por Sarah e conclui a tarefa.

![caixa de entrada](assets/leave-inbox.png)
**Figura:** *Caixa de entrada de Gloria*

![aprovada por licença](assets/leave-approved.png)
**Figura:** *Abrir tarefa*

**Como funciona**

O fluxo de trabalho de envio no aplicativo de licença aciona um fluxo de trabalho Forms que cria uma tarefa na caixa de entrada de Gloria para aprovação. Revise o Forms Workflow em `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-leave-application.html`

![modelo de fluxo de trabalho do modelo de fluxo de trabalho do cartão corporativo](assets/corporate-card-leave-application-workflow-model.png)

**Veja você mesmo**

Ir para `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` e fazer logon usando `grios/password` como nome de usuário/senha para Gloria Rios. Abra a tarefa criada para deixar o aplicativo e aprove-a.
