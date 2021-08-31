---
title: Configurar e configurar sites de referência do AEM Forms
seo-title: Set up and configure AEM Forms reference sites
description: Os sites de referência da AEM Forms mostram como você pode usar o AEM Forms para implementar um fluxo de trabalho completo em uma organização.
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 2%

---

# Configurar e configurar sites de referência do AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

A AEM Forms fornece a implementação de referência do site para demonstrar como a AEM Forms ajuda as organizações do setor de serviços financeiros e do governo a transformar suas transações complexas em experiências digitais simples e envolventes, em qualquer lugar, a qualquer momento, em qualquer dispositivo.

Os sites de referência We.Finance e We.Gov extraem casos de uso reais para interagir com clientes atuais e potenciais, desde o primeiro contato até o gerenciamento de correspondências e transações de forma personalizada e econômica.

Os sites de referência permitem explorar e mostrar os seguintes recursos principais do AEM Forms.

* Experiência de criação simplificada de formulários adaptáveis e comunicações interativas responsivas.
* Comunicações interativas para criar comunicações interativas, personalizadas e responsivas do cliente que se adaptam à configuração e ao layout do dispositivo.
* Integração de dados para se conectar a fontes de dados diferentes para preencher previamente e enviar dados de formulário por meio de um modelo de dados de formulário.
* Fluxo de trabalho do Forms para automatizar processos e fluxos de trabalho de negócios.
* Recursos avançados de gerenciamento e processamento de dados do usuário.
* Integração com o Adobe Sign para assinar e enviar formulários adaptáveis com segurança.
* Integração com o Adobe Target para fornecer recomendações direcionadas e realizar testes A/B para maximizar o ROI de um formulário.
* Integração com o Adobe Analytics para medir o desempenho de um formulário ou campanha e tomar decisões informadas.
* Experiência aprimorada de preenchimento de formulários.

Os sites de referência fornecem ativos reutilizáveis que podem ser usados como modelos para criar seus próprios ativos.

* Integração com o Adobe Sign para assinar e enviar formulários adaptáveis com segurança.

* Integração com o Adobe Sign para assinar e enviar formulários adaptáveis com segurança.

## Pré-requisitos e etapas para configurar sites de referência {#prerequisites-and-steps-to-set-up-reference-sites}

Antes de configurar o site de referência, verifique se você tem o seguinte:

* **AEM essenciais**

   AEM QuickStart, pacote do complemento AEM Forms e pacotes do site de referência. Consulte [Versões do AEM Forms](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) para obter detalhes sobre pacotes de complementos e sites de referência.

* **Um**
serviço SMTPé possível usar qualquer serviço SMTP.

* **Conta de desenvolvedor do Adobe Sign e aplicativo da API do Adobe Sign**

   Para usar recursos de assinatura digital, é necessária uma conta de desenvolvedor do Adobe Sign. Consulte [Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html).

* Uma instância em execução do Microsoft Dynamics 365 para integrar com o AEM Forms. Para executar o site de referência, importe os dados de amostra para a instância do Microsoft Dynamics para preencher previamente a comunicação interativa usada no site de referência.
* Uma instância em execução do AEM 6.4 com o pacote do complemento Forms. Para obter mais informações, consulte [Instalar e configurar o AEM Forms](installing-configuring-aem-forms-osgi.md).

Execute as etapas a seguir na sequência recomendada para configurar e configurar os sites de referência.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Etapa</strong></th> 
   <th><strong>Configurar</strong></th> 
   <th><strong>Notas</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Instalar e configurar o AEM Forms</a></td> 
   <td>Autor e publicação</td> 
   <td>Instale e configure as instâncias de criação e publicação do AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">Configurar SSL</a></td> 
   <td>Autor e publicação<br /> </td> 
   <td>Ative HTTP por SSL para comunicações seguras com o Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Configurar o Day CQ Link Externalizer</a></p> </td> 
   <td>Autor e publicação<br /> </td> 
   <td><p>Casos de uso de referência do site enviam emails para transações diferentes. Essa configuração é necessária para o delivery do boletim informativo por email. Isso garante que URLs e imagens apontem para a instância de publicação. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Configurar o Day CQ Mail Service</a></td> 
   <td>Autor e publicação</td> 
   <td>Necessário para comunicação por email.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Substituir configuração XSS padrão</a></td> 
   <td>Publicação</td> 
   <td>Usado para substituir caracteres $, { e } bloqueados pela segurança xss.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Definir configurações AEM DS</a></td> 
   <td>Autor</td> 
   <td>Configure AEM DS para envio de formulário na instância de publicação e fluxos de trabalho de processamento na instância do autor.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Implantar pacotes de sites de referência</a></td> 
   <td>Autor</td> 
   <td>Implante pacotes de sites de referência na instância do autor do AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importar dados de amostra para o Microsoft Dynamics</a></td> 
   <td>Autor e publicação</td> 
   <td>Importar dados de amostra para o aplicativo de cartão de crédito, o aplicativo de hipoteca de casa e a apresentação do aplicativo de seguro de casa</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurar o serviço em nuvem OAuth para o Microsoft Dynamics</a></td> 
   <td>Autor e publicação</td> 
   <td>Configure o serviço de nuvem OAuth no AEM Forms para permitir a comunicação entre o AEM Forms e o Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configurar o Adobe Sign Scheduler</a></td> 
   <td>Autor e publicação<br /> </td> 
   <td>Altere a configuração do agendador para verificar o status a cada dois minutos.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configurar o Cloud Service Adobe Sign do site de referência</a></td> 
   <td>Autor e publicação<br /> </td> 
   <td>Uma configuração que vem com pacotes de sites de referência e precisa ser reconfigurada com credenciais válidas.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configurar o Forms Common Configuration Service para usuários anônimos</a></td> 
   <td>Publicação</td> 
   <td>A configuração permite a geração de envio, sinal e Documento de registro para usuários anônimos.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modificar o arquivo Rest Service Swagger para o Modelo de dados de formulário</a></td> 
   <td>Autor e publicação<br /> </td> 
   <td>Modifique o serviço para seu ambiente.</td> 
  </tr> 
 </tbody> 
</table>

## Instalar e configurar o AEM Forms {#install-and-configure-aem-forms}

Instale e implante o AEM Forms conforme descrito em [Instalar e configurar o AEM Forms no OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configure os agentes de replicação inversa e de replicação se houver mais de uma instância de publicação ou instâncias de autor e publicação em máquinas diferentes.

## Configurar SSL {#ssl}

A configuração SSL é necessária para comunicação com os servidores da Adobe Sign. Para etapas detalhadas, consulte [Ativando HTTP sobre SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Não configure forçar SSL na pasta `/etc/map`.

## Configurar o Day CQ Link Externalizer {#externalizer}

Em AEM, o **Externalizador** é um serviço OSGI que permite transformar programaticamente um caminho de recurso (por exemplo, /path/to/my/page) em um URL externo e absoluto (por exemplo, https://www.mycompany.com/path/to/my/page) ao prefixar o caminho com um DNS pré-configurado. Consulte [Exteriorização de URLs](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Não externalize para URL HTTPS se estiver usando um certificado autoassinado para SSL.
>
>Além disso, use localhost em vez de seu nome de host para servidor local.

Execute as seguintes etapas nas instâncias de autor e de publicação:

1. Vá para Configuração OSGi em https://*hostname>*:&lt;*port>*/system/console/configMgr.
1. Localize e toque em **[!UICONTROL Configuração do Day CQ Link Externalizer]**.

   A caixa de diálogo Day CQ Link Externalizer é aberta para edição da configuração.

1. Na caixa de diálogo Day CQ Link Externalizer, no campo Domínios :

   * Na instância do autor, especifique um URL de publicação que possa ser acessado de um sistema externo. Por exemplo, um nome de host ou um servidor da Web de publicação.
   * Na instância de publicação, especifique os URLs de autor e publicação.

1. Em instâncias de criação e de publicação, verifique se o URL do servidor local está especificado no campo Domínios .
1. Toque em **[!UICONTROL Salvar]**. Aguarde um tempo para que todos os serviços sejam reiniciados.

## Configurar o Day CQ Mail Service {#cqmail}

A implementação do site de referência requer que os emails sejam enviados para usuários de exemplo quando eles preencherem e enviarem formulários. A configuração do Day CQ Mail Service permite fornecer detalhes do serviço SMTP para enviar emails automatizados aos clientes. Consulte [Configurar notificações por email](/help/sites-administering/notification.md).

Execute as seguintes etapas para configurar o serviço de email na instância de publicação:

1. Vá para Configuração OSGi em https://*hostname>*:&lt;*port>*/system/console/configMgr.
1. Localize e toque em **[!UICONTROL Day CQ Mail Service]** para abri-lo para configuração.
1. Forneça o nome do host do servidor SMTP e os valores da porta.
1. Toque em **[!UICONTROL Salvar]**.

>[!NOTE]
>
>Você pode usar seu serviço SMTP corporativo ou serviços públicos como o Gmail. Para configurar o serviço SMTP, consulte a documentação do serviço SMTP.

## Substituir configuração XSS padrão {#xss}

Os modelos de email para o site de referência We.Finance contêm links personalizados em emails. Esses links têm espaço reservado como `${placeholder}`. Esses espaços reservados são substituídos por valores reais antes de enviar emails. A configuração padrão de proteção XSS para AEM não permite chaves (**{ }**) no URL no conteúdo HTML. No entanto, é possível substituir a configuração padrão executando as seguintes etapas na instância de publicação:

1. Copie `/libs/cq/xssprotection/config.xml` para `/apps/cq/xssprotection/config.xml`.
1. Abrir `/apps/cq/xssprotection/config.xml`.
1. Na seção `common-regexps`, modifique a entrada `onsiteURL` da seguinte maneira e salve o arquivo.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Chaves curvas (**{ }**) são incluídas como caracteres aceitos no URL no conteúdo HTML.

Depois de configurar o servidor SMTP, tente preencher um formulário usando a persona Sarah Rose e salve-o como rascunho. Ao salvar como rascunho, você obtém uma opção para receber o rascunho por email. Ao tocar no botão **Enviar Email**, se você receber um email com um link para o rascunho do aplicativo, sua configuração de email será bem-sucedida. Faça logon usando as credenciais da Sarah para ver o rascunho.

## Definir configurações AEM DS {#aemds}

AEM configurações do Serviço DS são necessárias na instância Publicar para comunicações por email nos casos de uso do site de referência. Para obter etapas detalhadas para configurar AEM configuração do DS Service na instância de publicação, consulte [Definir configurações AEM do DS](/help/forms/using/configuring-the-processing-server-url-.md).

Para sites de referência do AEM Forms, no Serviço de configurações do AEM DS, especifique o URL do servidor de publicação em vez do URL do servidor de processamento.

>[!CAUTION]
>
>Não coloque `/lc` no URL do servidor de processamento se estiver configurando-o para AEM Forms OSGi.

## Implantar pacotes de sites de referência {#refsite}

Instale os seguintes pacotes de sites de referência usando a Distribuição de software.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Para saber mais sobre como usar pacotes, consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md).

Depois de ter instalado os pacotes e iniciado as instâncias de criação e publicação, visite os seguintes URLs em seu navegador:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Se a instalação for bem-sucedida, você poderá acessar as páginas de aterrissagem dos sites de referência We.Gov e We.Finance.

## (Opcional) Importação de dados de amostra para o Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Os sites de referência do aplicativo de hipoteca doméstica e do aplicativo de seguro automático estão configurados para usar registros do Microsoft Dynamics. O pacote do site de referência instala uma entidade personalizada e registros de amostra que você pode importar para o Microsoft Dynamics para executar o site de referência. Execute as seguintes etapas para migrar e configurar os dados de amostra:

Para importar a entidade personalizada para o aplicativo de seguro automático:

1. Baixe o pacote de solução **WeFinanceAutoInsurance_1_0.zip** de `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` na instância do autor do AEM.
1. Na instância do Microsoft Dynamics, vá para **[!UICONTROL Solutions]** no menu **[!UICONTROL Settings]** e clique em **[!UICONTROL Import]**. Selecione e importe o pacote.

Para importar a entidade personalizada para o aplicativo de seguro automático:

1. Baixe o pacote **AEMFormsFSIRefsite_1_0.zip** de https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Selecione e importe o pacote.

1. Na instância do Microsoft Dynamics, vá para **[!UICONTROL Solutions]** no menu **[!UICONTROL Settings]** e clique em **[!UICONTROL Import]**. Selecione e importe o pacote.

Para importar os registros do cliente e da apólice de seguro:

1. Baixe os arquivos de dados **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** e **home hipoteca** dos seguintes locais na instância do autor do AEM:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Na instância do Microsoft Dynamics, faça o seguinte:

   * Vá para **[!UICONTROL Sales > We.Finance Customers]** e clique em **[!UICONTROL Import]**.
   * Vá para **[!UICONTROL Sales > We.Finance Auto Insurance]** e clique em **[!UICONTROL Import]**.
   * Vá para **[!UICONTROL Sales > We.Finance Home Mortgauge]** e clique em **[!UICONTROL Import]**.

## Configurar o serviço em nuvem OAuth para o Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configure o serviço de nuvem OAuth no AEM Forms para permitir a comunicação entre o AEM Forms e o Microsoft Dynamics. Execute as seguintes etapas para configurar o OAuth Cloud Service em instâncias de criação e publicação AEM:

1. Na instância AEM autor, vá para **[!UICONTROL Tools > Cloud Services > Data Sources > global]**. Toque no ícone **[!UICONTROL Refsite Dynamics Integration]** e toque em **[!UICONTROL Properties]**.
1. Vá para a conta do Microsoft Azure Ative Diretory. Adicione o URL de configuração do serviço de nuvem copiado na configuração **[!UICONTROL Responder URL]** para seu aplicativo registrado. Salve a configuração.
1. Na guia Configurações de autenticação , especifique **[!UICONTROL Raiz do serviço]**, **[!UICONTROL ID do cliente]**, **[!UICONTROL Segredo do cliente]** e **[!UICONTROL URL do recurso]** para a instância do Microsoft Dynamics. Clique em **[!UICONTROL Connect to OAuth]** que redireciona para a página de logon do Microsoft Dynamics.
1. Forneça suas credenciais de logon. Depois de conectado, você é redirecionado para a página de configuração do serviço de nuvem da AEM Forms. Clique em **[!UICONTROL Salvar e fechar]**. A configuração do serviço de nuvem é salva.
1. Vá para **[!UICONTROL Forms > Integrações de dados > We.Finance]**. Selecione Seguro automático (Dynamics) e clique em Editar. As entidades do Microsoft Dynamics estão listadas na guia Fontes de dados. Aguarde até que todas as entidades sejam buscadas no Microsoft Dynamics e listadas na guia fontes de dados.
1. Selecione a entidade **[!UICONTROL AutoInsuranceRenewal]** e clique em **[!UICONTROL Test Model Object]**. Na seção de solicitação de entrada, especifique o valor para a ID do cliente como &quot;900001&quot; e clique em **[!UICONTROL Test]**. A seção Saída exibe os registros obtidos do Microsoft Dynamics para a ID de cliente 900001.
1. Na seção de solicitação de entrada, especifique o valor para a ID do cliente como &quot;900001&quot; e clique em **[!UICONTROL Test]**. A seção Saída exibe os registros obtidos do Microsoft Dynamics para a ID de cliente 900001.
1. Repita as etapas 1 a 6 na instância de publicação.

## Configurar o Adobe Sign Scheduler {#scheduler}

Faça o seguinte em instâncias de autor e publicação:

1. Vá para AEM console de configuração da Web em `https://[server]:[host]/system/console/configMgr`.
1. Localize e toque em **[!UICONTROL Adobe Sign Configuration Service]** para abri-lo para configuração.
1. Configure **[!UICONTROL Status Update Scheduler Expression]** como **0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >A configuração do programador acima verifica o status do serviço Adobe Sign a cada dois minutos.

1. Toque em **[!UICONTROL Salvar]**.

## Configurar o site de referência do serviço em nuvem Adobe Sign {#sign-service}

Faça o seguinte em instâncias de autor e publicação:

1. Vá para **[!UICONTROL Ferramentas > Cloud Services > Adobe Sign > global]**. Selecione **[!UICONTROL AEM Forms Reference Site Sign]** e toque em **[!UICONTROL Properties]**.

   >[!CAUTION]
   >
   >Certifique-se de que o URL https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html seja adicionado à lista de URL de redirecionamento da configuração OAuth do aplicativo da API do Adobe Sign.

1. Especifique a ID do cliente e o segredo da configuração OAuth do aplicativo Adobe Sign.
1. (Opcional) Selecione a opção **[!UICONTROL Ativar o Adobe Sign para anexos também]** e toque em **[!UICONTROL Conectar ao Adobe Sign]**. Ele anexa os arquivos anexados a um formulário adaptável ao documento Adobe Sign correspondente enviado para assinatura.
1. Toque em **[!UICONTROL Conectar-se ao Adobe Sign]** e faça logon com suas credenciais do Adobe Sign.

## Configurar o Serviço de Configuração Comum do Forms {#anonymous}

Faça o seguinte na instância de publicação para permitir acesso a usuários anônimos:

1. Vá para AEM console de configuração da Web em `https://[server]:[port]/system/console/configMgr`.
1. Localize e toque em **[!UICONTROL Forms Common Configuration Service]** para abri-lo para configuração.
1. Configure o campo **[!UICONTROL Allow]** para **[!UICONTROL All Users]**.
1. Toque em **[!UICONTROL Salvar]**.

## Modificar o serviço de restante do modelo de dados de formulário {#fdm}

Faça o seguinte em instâncias de autor e publicação:

1. Vá para o CRXDE em `https://[server]:[port]/crx/de/index.jsp`.
1. Navegue até **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** e abra o arquivo swagger.
1. Atualize as configurações de host e porta de acordo com seu ambiente.
1. Salve as configurações.
1. (**Instância de autor somente**) Vá para **[!UICONTROL Ferramentas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Fontes de Dados]** > **[!UICONTROL global]**. Selecione **[!UICONTROL roi-rest]** e toque em **[!UICONTROL Propriedades]**. Toque em **[!UICONTROL Configurações de autenticação]** e defina **[!UICONTROL Tipo de autenticação]** para **[!UICONTROL Autenticação básica]**. Especifique `admin`/ `admin`como o nome de usuário/senha para acessar o serviço. Toque em **[!UICONTROL Salvar e fechar]**.

## Integrar ao Marketing Cloud {#integrate-with-marketing-cloud}

É possível integrar a AEM Forms com a Adobe Analytics e a Adobe Target. Embora o Adobe Analytics ajude você a gerar relatórios e analisar o desempenho de formulários adaptáveis, o Adobe Target ajuda você a fornecer experiências personalizadas e a realizar testes A/B para formulários adaptáveis.

Faça o seguinte para configurar o Adobe Analytics e o Adobe Target no AEM Forms.

### Configurar o Adobe Analytics {#configure-adobe-analytics}

A integração do AEM Forms com o Adobe Analytics permite monitorar e analisar como seus clientes interagem com seus formulários e documentos. Ajuda a identificar e corrigir áreas problemáticas e a agir para aumentar a taxa de conversão.

Para ter essa funcionalidade no site de referência, configure sua conta do Analytics conforme descrito em [Configuração de análises e relatórios](/help/forms/using/configure-analytics-forms-documents.md).

Para gerar um relatório, os dados de propagação são agrupados com os sites de referência. Antes de usar os dados de propagação, faça o seguinte:

1. Certifique-se de que as configurações de análise We.Finance e We.Gov estejam disponíveis no AEM Cloud Services. Você pode encontrar serviços em nuvem de uma das seguintes maneiras:

   * Navegue até **[!UICONTROL Tools>Cloud Services>Legacy Cloud Services]** ou navegue até https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * Na página **[!UICONTROL Cloud Services]**, na seção **[!UICONTROL Adobe Analytics]**, clique em `Show Configurations`. Você pode ver as configurações We.Finance e We.Gov disponíveis. Clique em para abrir a configuração. Na página de configuração, clique em **[!UICONTROL Editar]**. Forneça Empresa, Nome de usuário, Segredo compartilhado (Senha) e Centro de dados válidos e clique em **[!UICONTROL Conectar ao Analytics]**. Depois de obter a caixa de diálogo Conexão bem-sucedida, clique em **[!UICONTROL OK]** na caixa de diálogo de configuração. Configure a estrutura na configuração do Analytics, conforme descrito em [Configuração do Analytics e Relatórios](/help/forms/using/configure-analytics-forms-documents.md).

1. Navegue até https://*host*:&lt;*port*>/system/console/configMgr e faça o seguinte:

   * Na página **[!UICONTROL Configuração do Console da Web]**, localize e clique em **[!UICONTROL Configuração do AEM Forms Analytics]**.
   * No campo **[!UICONTROL SiteCatalyst Framework]** da caixa de diálogo Configuração do AEM Forms Analytics, selecione we-finance(we-finance) ou we-gov(we-gov).
   * Clique em **[!UICONTROL Save]** e deixe a página atualizar.

1. Navegue até o gerenciador de formulários em https://&lt;host>:&lt;port>/aem/forms e faça o seguinte:

   * Abra a pasta We.Finance ou We.Gov e selecione o formulário para o qual deseja visualizar o relatório.
   * Clique em Ativar o Analytics na barra de ferramentas Ações. Depois de ativar o Analytics para o formulário, clique em Analytics Report. Você pode ver um relatório em branco gerado. Depois que um relatório em branco é gerado, é necessário fornecer dados de propagação enviados com um pacote de resite para gerar um relatório de análise para fins de demonstração.

   Os sites de referência fornecem relatórios analíticos com dados de propagação para cartão de crédito, hipoteca doméstica e casos de uso de suporte a crianças. Para configuração de dados de seed, consulte [Apresentação do site de referência We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) e [Apresentação do site de referência We.Gov](/help/forms/using/gov-reference-site-walkthrough.md).

### Configurar o Target {#configure-target}

O site de referência mostra a integração do AEM Forms com o Adobe Target, que permite incluir conteúdo direcionado e personalizado em documentos adaptáveis. Ela também permite criar testes A/B para formulários adaptáveis.

Para experimentar a integração no site de referência, faça o seguinte para configurar o Target no AEM:

1. Inicie o início rápido do autor com o argumento jvm `-Dabtesting.enabled=true` para ativar o teste A/B no servidor.

   **Observação**: Se a instância AEM estiver em execução no JBoss, que é iniciado como um serviço da instalação Turnkey, adicione o  `-Dabtesting.enabled=true` parâmetro na seguinte entrada no  `jboss\bin\standalone.conf.bat` arquivo , :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Acesse https://*hostname*:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Na seção **[!UICONTROL Adobe Target]**, clique em **[!UICONTROL Mostrar configurações]**. Você pode ver a Configuração de Direcionamento do We.Finance disponível. Clique em para abrir a configuração. Na página de configuração, clique em **[!UICONTROL Editar]**. A caixa de diálogo **[!UICONTROL Editar componente]** para a configuração é aberta.

1. Especifique o Código do cliente, Email e Senha associados à sua conta do Target. Selecione o tipo de API como **[!UICONTROL REST]**.
1. Clique em **[!UICONTROL Conectar ao Adobe target]**. Depois que a conta do Target for configurada com êxito, clique em **[!UICONTROL OK]**. Você pode ver que a configuração empacotada tem uma Estrutura do Target.

1. Vá para https://&lt;*hostname*:&lt;*port*>/system/console/configMgr.

1. Clique em **[!UICONTROL Configuração do AEM Forms Target]**.
1. Selecione uma estrutura do Target.
1. No campo **[!UICONTROL URLs do Target]**, especifique o URL para o AEM Forms. Por exemplo: https://&lt;*hostname*:&lt;*port*>.

1. Clique em **[!UICONTROL Salvar]**.

Os casos de uso do Aplicativo de cartão de crédito e do Aplicativo de medidor de crédito demonstram como executar o teste A/B e mostrar um relatório para fins de demonstração. Para obter instruções, consulte [Apresentação do site de referência We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Próxima etapa {#next-step}

Agora você está preparado para explorar o site de referência. Para obter mais informações sobre o fluxo de trabalho do site de referência e as etapas, consulte:

* [Apresentação do site de referência do We.Finance](/help/forms/using/finance-reference-site-walkthrough.md)
* [Apresentação do site de referência We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Apresentação do site de referência de autoatendimento do funcionário](/help/forms/using/employee-self-service-reference-site.md)
