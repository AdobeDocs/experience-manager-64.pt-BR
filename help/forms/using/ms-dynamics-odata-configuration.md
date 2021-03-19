---
title: Configuração do Microsoft Dynamics OData
seo-title: Configuração do Microsoft Dynamics ODtata
description: Aproveite, integre e trabalhe com serviços do Microsoft Dynamics online e local por meio de um modelo de dados de formulário.
seo-description: Saiba como aproveitar a integração e o trabalho com serviços do Microsoft Dynamics online e local por meio de um modelo de dados de formulário.
uuid: c9b2764f-9127-4a99-a469-b6ebcdee8fdf
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 62f9d1de-c397-46b5-964e-19777ddd130c
feature: Modelo de dados do formulário
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 0%

---


# Configuração do Microsoft Dynamics OData {#microsoft-dynamics-odata-configuration}

Aproveite, integre e trabalhe com serviços do Microsoft Dynamics online e local por meio de um modelo de dados de formulário.

![integração de dados](assets/data-integeration.png)

O Microsoft Dynamics é um software de CRM (Customer Relationship Management, gerenciamento de relacionamento com o cliente) e ERP (Enterprise Resource Planning, planejamento de recursos empresariais) que fornece soluções corporativas para criar e gerenciar contas, contatos, clientes potenciais, oportunidades e casos de clientes. [A ](/help/forms/using/data-integration.md) integração de dados do AEM Forms fornece uma configuração de serviço de nuvem OData para integrar o Forms ao servidor do Microsoft Dynamics online e local. Ele permite criar um modelo de dados de formulário com base nas entidades, atributos e serviços definidos no serviço Microsoft Dynamics. O modelo de dados de formulário pode ser usado para criar formulários adaptáveis que interagem com o servidor do Microsoft Dynamics para habilitar fluxos de trabalho de negócios. Por exemplo:

* Consultar o servidor do Microsoft Dynamics para dados e pré-preencher formulários adaptáveis
* Gravar dados no Microsoft Dynamics no envio de formulário adaptável
* Gravar dados no Microsoft Dynamics por meio de entidades personalizadas definidas no modelo de dados de formulário e vice-versa

O pacote complementar do AEM Forms também inclui a configuração de referência de OData que você pode aproveitar para integrar rapidamente o Microsoft Dynamics ao AEM Forms.

Quando o pacote é instalado, as seguintes entidades e serviços estão disponíveis na sua instância do AEM Forms:

* MS Dynamics OData Cloud Service (Serviço OData)
* Modelo de dados de formulário com entidades e serviços pré-configurados do Microsoft Dynamics.

O Cloud Service OData e o modelo de dados de formulário com entidades e serviços pré-configurados do Microsoft Dynamics só estarão disponíveis em sua instância do AEM Forms se o modo de execução da instância de AEM estiver definido como `samplecontent`(padrão). Para obter mais informações sobre como configurar modos de execução para uma instância de AEM, consulte [Executar modos](https://helpx.adobe.com/in/experience-manager/6-4/sites-deploying/configure-runmodes.html).

## Pré-requisitos {#prerequisites}

Antes de começar a configurar e configurar o Microsoft Dynamics, verifique se você:

* Instalado o [AEM pacote do complemento Forms 6.4](https://helpx.adobe.com//experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html)
* Configurado o Microsoft Dynamics 365 online ou instalado uma instância de uma das seguintes versões do Microsoft Dynamics:

   * Microsoft Dynamics 365 no local
   * Microsoft Dynamics 2016 no local

* [Registrado o aplicativo para o serviço online do Microsoft Dynamics com o Microsoft Azure Ative Diretory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Anote os valores para a ID do cliente (também chamada de ID do aplicativo) e o segredo do cliente para o serviço registrado. Esses valores são usados ao [configurar o serviço em nuvem para o serviço do Microsoft Dynamics](/help/forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service).

## Definir URL de resposta para aplicativo registrado do Microsoft Dynamics {#set-reply-url-for-registered-microsoft-dynamics-application}

Faça o seguinte para definir o URL de resposta para o aplicativo registrado do Microsoft Dynamics:

>[!NOTE]
>
>Use este procedimento apenas durante a integração do AEM Forms com o servidor online do Microsoft Dynamics.

1. Vá para a conta do Microsoft Azure Ative Diretory e adicione o seguinte URL de configuração do serviço de nuvem nas configurações de **[!UICONTROL URLs de resposta]** para seu aplicativo registrado:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![azure_diretory](assets/azure_directory.png)

1. Salve a configuração.

## Configurar o Microsoft Dynamics para IFD {#configure-microsoft-dynamics-for-ifd}

O Microsoft Dynamics usa autenticação baseada em afirmações para fornecer acesso aos dados no servidor do Microsoft Dynamics CRM para usuários externos. Para habilitar isso, faça o seguinte para configurar o Microsoft Dynamics para implantação com acesso à Internet (IFD) e definir as configurações de solicitação.

>[!NOTE]
>
>Use esse procedimento somente ao integrar o AEM Forms com o servidor Microsoft Dynamics local.

1. Configure a instância local do Microsoft Dynamics para IFD, conforme descrito em [Configurar IFD para Microsoft Dynamics](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Execute os seguintes comandos usando o Windows PowerShell para definir as configurações de afirmação no Microsoft Dynamics habilitado para IFD:

   ```
   Add-PSSnapin Microsoft.Crm.PowerShell 
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings 
    $ClaimsSettings.Enabled = $true 
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Consulte [Registro do aplicativo para CRM no local (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) para obter detalhes.

## Configurar o cliente OAuth na máquina AD FS {#configure-oauth-client-on-ad-fs-machine}

Faça o seguinte para registrar um cliente OAuth na máquina do Ative Diretory Federation Services (AD FS) e conceder acesso à máquina do AD FS:

>[!NOTE]
>
>Use esse procedimento somente ao integrar o AEM Forms com o servidor Microsoft Dynamics local.

1. Execute o seguinte comando:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Em que:

   * `Client-ID` é uma ID de cliente que você pode gerar usando qualquer gerador de GUID.
   * `redirect-uri` é o URL para o serviço de nuvem do Microsoft Dynamics OData no AEM Forms. O serviço em nuvem padrão instalado com o pacote AEM Forms é implantado no seguinte URL:

      ```
      http://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
      ```

1. Execute o seguinte comando para conceder acesso na máquina AD FS:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Em que:

   * `resource` é o URL da organização do Microsoft Dynamics.

1. O Microsoft Dynamics usa o protocolo HTTPS. Para chamar pontos de extremidade do AD FS do servidor do Forms, instale o certificado do site do Microsoft Dynamics no armazenamento de certificados Java usando o comando `keytool` no computador que executa o AEM Forms.

## Configurar o serviço em nuvem para o serviço do Microsoft Dynamics {#configure-cloud-service-for-your-microsoft-dynamics-service}

A configuração **MS Dynamics OData Cloud Service (OData Service)** vem com a configuração padrão de OData. Para configurá-lo para se conectar ao serviço do Microsoft Dynamics, faça o seguinte:

1. Navegue até **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]** e toque na pasta de configuração `global`.
1. Selecione a configuração **[!UICONTROL MS Dynamics OData Cloud Service (Serviço OData)]** e toque em **[!UICONTROL Propriedades]**. A caixa de diálogo da propriedade de configuração do serviço em nuvem é aberta.

   Na guia **[!UICONTROL Configurações de autenticação]** :

   1. Insira o valor do campo **[!UICONTROL Service Root]**. Vá para a instância Dynamics e navegue até **[!UICONTROL Developer Resources]** para exibir o valor do campo Service Root. Por exemplo, https://&lt;tenant-name>/api/data/v9.1/
   1. Substitua os valores padrão no **[!UICONTROL Client Id]** (também conhecido como **[!UICONTROL Application ID]**), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL Atualizar URL do Token]**, **[!UICONTROL Access Token URL&lt;a Campos 11/> e**[!UICONTROL  Resource ]**com valores da configuração do serviço Microsoft Dynamics.]** É obrigatório especificar o URL da instância dinâmica no campo **[!UICONTROL Resource]** para configurar o Microsoft Dynamics com um modelo de dados de formulário. Use o URL raiz do serviço para derivar o URL da instância dinâmica. Por exemplo, [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).
   1. Especifique **[!UICONTROL openid]** no campo **[!UICONTROL Escopo da Autorização]** para o processo de autorização no Microsoft Dynamics.

   ![dynamics_authentication_settings](assets/dynamics_authentication_settings.png)

1. Clique em **[!UICONTROL Conectar-se a OAuth]**. Você é redirecionado para a página de logon do Microsoft Dynamics.
1. Faça logon com as credenciais do Microsoft Dynamics e aceite permitir que a configuração do serviço de nuvem se conecte ao serviço do Microsoft Dynamics. É uma tarefa única estabelecer conexão entre o serviço de nuvem e o serviço.

   Em seguida, você é redirecionado para a página de configuração do serviço de nuvem, que exibe uma mensagem de que a configuração de OData foi salva com êxito.

O serviço em nuvem do MS Dynamics OData Cloud Service (Serviço OData) é configurado e conectado ao serviço de Dynamics.

## Criar modelo de dados de formulário {#create-form-data-model}

Ao instalar o pacote AEM Forms, um modelo de dados de formulário,**Microsoft Dynamics FDM**, é implantado em sua instância de AEM. Por padrão, o modelo de dados de formulário usa o serviço Microsoft Dynamics configurado no MS Dynamics OData Cloud Service (OData Service) como fonte de dados.

Ao abrir o modelo de dados de formulário pela primeira vez, ele se conecta ao serviço configurado do Microsoft Dynamics e busca entidades da instância do Microsoft Dynamics. As entidades &quot;contato&quot; e &quot;lead&quot; do Microsoft Dynamics já são adicionadas no modelo de dados de formulário.

Para revisar o modelo de dados de formulário, vá para **[!UICONTROL Forms > Integrações de dados]**. Selecione **[!UICONTROL Microsoft Dynamics FDM]** e clique em **[!UICONTROL Editar]** para abrir o modelo de dados de formulário no modo de edição. Como alternativa, você pode abrir o modelo de dados de formulário diretamente do seguinte URL:

`https://[*server*]:[*port*]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![default-fdm-1](assets/default-fdm-1.png)

Em seguida, é possível criar um formulário adaptável com base no modelo de dados de formulário e usá-lo em vários casos de uso de formulário adaptável, como:

* Preencha previamente o formulário adaptável consultando informações das entidades e serviços do Microsoft Dynamics
* Chamar operações do servidor do Microsoft Dynamics definidas em um modelo de dados de formulário usando regras de formulário adaptáveis
* Gravar dados de formulário enviados para entidades do Microsoft Dynamics

É recomendável criar uma cópia do modelo de dados de formulário fornecido com o pacote AEM Forms e configurar modelos e serviços de dados para atender aos seus requisitos. Ele garantirá que qualquer atualização futura no pacote não substitua o modelo de dados de formulário.

Para obter mais informações sobre como criar e usar o modelo de dados de formulário em workflows de negócios, consulte [Data Integration](/help/forms/using/data-integration.md).
