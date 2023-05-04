---
title: Configurar o Microsoft Dynamics 365 para o fluxo de trabalho de hipoteca residencial do site de referência We.Finance
seo-title: Configure Microsoft Dynamics 365 for the home mortgage workflow of the We.Finance reference site
description: Saiba como aproveitar os serviços do Microsoft® Dynamics 365 por meio de formulários adaptáveis para o fluxo de trabalho de hipoteca residencial do site de referência We.Finance
seo-description: Learn how to leverage the Microsoft® Dynamics 365 services through adaptive forms for the home mortgage workflow of the We.Finance Reference site
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
exl-id: 7e1f417e-6a6b-4ef2-a453-866331fe3e96
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 2%

---

# Configurar o Microsoft Dynamics 365 para o fluxo de trabalho de hipoteca residencial do site de referência We.Finance {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como aproveitar os serviços do Microsoft® Dynamics 365 por meio de formulários adaptáveis para o fluxo de trabalho de hipoteca residencial do site de referência We.Finance

## Visão geral {#overview}

O Microsoft® Dynamics 365 é um software de CRM (relacionamento com o cliente) e ERP (Enterprise Resource Planning, planejamento de recursos empresariais) que fornece soluções empresariais para criar e gerenciar contas, contatos, clientes potenciais, oportunidades e casos de clientes.

O AEM Forms fornece um serviço em nuvem para integrar o Dynamics 365 com o [Integração de dados do Forms](/help/forms/using/data-integration.md) módulo. O cenário [Apresentação do aplicativo para medidores domésticos com o Microsoft® Dynamics](/help/forms/using/finance-reference-site-walkthrough.md#home-mortgage-application-walkthrough-with-microsoft-dynamics) mostra como um cliente usa o site de referência We.Finance para solicitar um empréstimo quando o site está usando o Microsoft® Dynamics for Forms Data Integration. Antes de usar a apresentação do aplicativo Home Mortgauge com o cenário Microsoft® Dynamics, você precisa configurar o Microsoft® Dynamics 365 para ser usado com o site de referência We.Finance.

## Pré-requisitos {#prerequisites}

Antes de começar a configurar e configurar o Dynamics 365, verifique se você:

* [Configurar e configurar sites de referência do AEM Forms](/help/forms/using/setup-reference-sites.md).

* AEM 6.3 Forms Service Pack 1 e posterior
* Conta do Microsoft® Dynamics 365
* Aplicativo registrado para o serviço Dynamics 365 com o Microsoft® Azure Ative Diretory
* ID do cliente e segredo do cliente para o aplicativo registrado

## Vincule a calculadora de hipotecas da página inicial à página inicial do site {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Na instância do autor, vá para a seguinte página:

   https://[derramador]:[porta]/editor.html/content/we-finance/global/en/loan-landing-page.html

1. Role para baixo até a Calculadora do Hipoteca Inicial.
1. Realce o painel da coluna direita (da calculadora) e toque para exibir o menu pop-up. No menu pop-up, toque em Configurar. A caixa de diálogo Editar contêiner do AEM Forms é exibida.

   ![calculatorconfigurepanel](assets/calculatorconfigurepanel.png)

1. Na caixa de diálogo Editar contêiner do AEM Forms , navegue pelo caminho do ativo e selecione a calculadora de hipotecas domésticas no seguinte caminho e toque em **Confirmar**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![seletassetpath](assets/selectassetpath.png)

1. Toque **Concluído**.
1. Publique a página editada.

   >[!NOTE]
   >
   >O vínculo dos campos da calculadora com o FDM é pré-configurado por meio do pacote do site de referência We.Finance . Para exibir o vínculo, abra o formulário no modo de criação e veja as referências de vínculo de campo.

1. Para criar uma entidade personalizada para armazenar o registro do candidato para o aplicativo de hipoteca, importe o pacote de solução AEMFormsFSIRefsite_1_0.zip para a instância do Microsoft® Dynamics:

   1. Baixe o pacote de:

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importe o pacote de solução para a instância do Microsoft® Dynamics. Na sua instância do Microsoft® Dynamics, acesse **Configurações** > **Soluções** em seguida, toque em **Importar**.

1. Para configurar os detalhes de contato do usuário usados no refsite, importe o pacote Sarah Rose Contact.CSV para sua instância do Microsoft® Dynamics:

   1. Baixe o pacote de:

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importe o pacote para a instância do Microsoft® Dynamics. Na sua instância do Microsoft® Dynamics, acesse **Vendas** > **Contatos** em seguida, toque em **Importar dados**.
