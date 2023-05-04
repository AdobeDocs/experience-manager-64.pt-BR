---
title: Configurar fontes de dados
seo-title: Configure data sources
description: Saiba como configurar diferentes tipos de fontes de dados e aproveitar para criar modelos de dados de formulário.
seo-description: Learn how to configure different types of data sources and leverage to create form data models.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 1%

---

# Configurar fontes de dados {#configure-data-sources}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como configurar diferentes tipos de fontes de dados e aproveitar para criar modelos de dados de formulário.

![](do-not-localize/data-integeration.png)

A Integração de dados do AEM Forms permite configurar e se conectar a fontes de dados diferentes. Os seguintes tipos são suportados prontos para uso. No entanto, com pouca personalização, também é possível integrar outras fontes de dados.

* Bancos de dados relacionais - MySQL, Microsoft SQL Server, IBM DB2 e Oracle RDBMS
* Perfil de usuário AEM
* Serviços Web RESTful
* Serviços Web baseados em SOAP
* Serviços OData

A integração de dados oferece suporte aos tipos de autenticação OAuth2.0, Basic Authentication e API Key prontos para uso e permite implementar autenticação personalizada para acessar serviços da Web. Embora os serviços RESTful, baseados em SOAP e OData sejam configurados nos Serviços da nuvem AEM, o JDBC para bancos de dados relacionais e o conector para AEM perfil de usuário são configurados AEM console da Web.

## Configurar banco de dados relacional {#configure-relational-database}

Você pode configurar bancos de dados relacionais usando AEM Configuração do Console da Web. Faça o seguinte:

1. Vá para AEM console da Web em `https://[server]:[host]/system/console/configMgr`.
1. Procure por **[!UICONTROL Fonte de dados agrupada da conexão Apache Sling]** configuração. Toque em para abrir a configuração no modo de edição.
1. Na caixa de diálogo de configuração, especifique os detalhes do banco de dados que deseja configurar, como:

   * Nome da fonte de dados
   * Propriedade do serviço da fonte de dados que armazena o nome da fonte de dados
   * Nome da classe Java para o driver JDBC
   * URI de conexão JDBC
   * Nome de usuário e senha para estabelecer conexão com o driver JDBC

   >[!NOTE]
   >
   >Certifique-se de criptografar informações confidenciais como senhas antes de configurar a fonte de dados. Para criptografar:
   >
   >1. Ir para `https://[server]:[port]/system/console/crypto`.
   >1. No **[!UICONTROL Texto sem formatação]** , especifique a senha ou qualquer string a ser criptografada e clique em **[!UICONTROL Protect]**.

   >
   >O texto criptografado aparece no campo Texto protegido que pode ser especificado na configuração.

1. Habilitar **[!UICONTROL Teste em linha de crédito]** ou **[!UICONTROL Testar no retorno]** para especificar que os objetos sejam validados antes de serem emprestados ou retornados de e para o pool, respectivamente.
1. Especifique uma consulta SQL SELECT no **[!UICONTROL Consulta de validação]** para validar conexões do pool. A consulta deve retornar pelo menos uma linha. Com base no seu banco de dados, especifique um dos seguintes:

   * SELECT 1 (MySQL e MS SQL)
   * SELECIONE 1 de duplo (Oracle)

1. Toque **[!UICONTROL Salvar]** para salvar a configuração.

## Configurar AEM perfil de usuário {#configure-aem-user-profile}

Você pode configurar AEM perfil de usuário usando a configuração do Conector de perfil de usuário AEM console da Web. Faça o seguinte:

1. Vá para AEM console da Web em `https://[server]:[host]/system/console/configMgr`.
1. Procure por **[!UICONTROL Integrações de dados do AEM Forms - Configuração do conector do perfil de usuário]** e toque para abrir a configuração no modo de edição.
1. Na caixa de diálogo Configuração do conector do perfil do usuário, é possível adicionar, remover ou atualizar as propriedades do perfil do usuário. As propriedades especificadas estarão disponíveis para uso no modelo de dados de formulário. Use o seguinte formato para especificar as propriedades do perfil de usuário:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Exemplos:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >O **&amp;ast;** no exemplo acima significa todos os nós sob o `profile/empLocation/` no AEM perfil do usuário na estrutura CRXDE. Isso significa que o modelo de dados de formulário pode acessar a variável `city` propriedade do tipo `string` presente em qualquer nó sob o `profile/empLocation/` nó . No entanto, os nós que contêm a propriedade especificada devem seguir uma estrutura consistente.

1. Toque **[!UICONTROL Salvar]** para salvar a configuração.

## Configurar pasta para configurações do serviço de nuvem {#cloud-folder}

>[!NOTE]
>
>A configuração da pasta de serviços em nuvem é necessária para configurar os serviços em nuvem para os serviços RESTful, SOAP e OData.

Todas as configurações do serviço em nuvem no AEM são consolidadas no `/conf` pasta no repositório AEM. Por padrão, a variável `conf` A pasta contém o `global` pasta onde você pode criar configurações do serviço de nuvem. No entanto, é necessário ativá-lo manualmente para configurações de nuvem. Você também pode criar pastas adicionais em `conf` para criar e organizar configurações do serviço de nuvem.

Para configurar a pasta das configurações do serviço de nuvem:

1. Ir para **[!UICONTROL Ferramentas > Geral > Navegador de configuração]**.
   * Consulte a [Documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.
1. Faça o seguinte para habilitar a pasta global para configurações de nuvem ou ignore esta etapa para criar e configurar outra pasta para configurações do serviço de nuvem.

   1. No **[!UICONTROL Navegador de configuração]**, selecione o `global` pasta e toque **[!UICONTROL Propriedades]**.
   1. No **[!UICONTROL Propriedades da configuração]** caixa de diálogo, habilitar **[!UICONTROL Configurações da nuvem]**.
   1. Toque **[!UICONTROL Salvar e fechar]** para salvar a configuração e sair da caixa de diálogo.

1. No **[!UICONTROL Navegador de configuração]**, toque em **[!UICONTROL Criar]**.
1. No **[!UICONTROL Criar configuração]** , especifique um título para a pasta e habilite **[!UICONTROL Configurações da nuvem]**.
1. Toque **[!UICONTROL Criar]** para criar a pasta habilitada para as configurações do serviço de nuvem.

## Configurar serviços Web RESTful {#configure-restful-web-services}

O serviço Web RESTful pode ser descrito usando [Especificações do Swagger](https://swagger.io/specification/) no formato JSON ou YAML em um arquivo de definição Swagger. Para configurar o serviço Web RESTful nos serviços em nuvem do AEM, verifique se você tem o arquivo Swagger no sistema de arquivos ou o URL onde o arquivo está hospedado.

Faça o seguinte para configurar os serviços RESTful:

1. Ir para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do cloud service.

1. Toque **[!UICONTROL Criar]** para abrir o **[!UICONTROL Caixa de diálogo Criar configuração da fonte de dados]**. Especificar um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL Serviço RESTful]** do **[!UICONTROL Tipo de serviço]** como opção, navegue e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Próximo]**.
1. Especifique os seguintes detalhes para o serviço RESTful:

   * Selecione URL ou Arquivo na lista suspensa Fonte do Swagger e especifique o URL do Swagger correspondente para o arquivo de definição do Swagger ou faça o upload do arquivo Swagger do sistema de arquivos local.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica, Chave da API ou Autenticação Personalizada — para acessar o serviço RESTful e, de acordo, fornecer detalhes para autenticação.

1. Toque **[!UICONTROL Criar]** para criar a configuração de nuvem para o serviço RESTful.

## Configurar serviços Web SOAP {#configure-soap-web-services}

Os serviços da Web baseados em SOAP são descritos usando [Especificações de WSDL (Web Services Description Language)](https://www.w3.org/TR/wsdl). Para configurar o serviço da Web baseado em SOAP nos serviços em nuvem do AEM, verifique se você tem o URL WSDL para o serviço da Web e faça o seguinte:

1. Ir para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do cloud service.

1. Toque **[!UICONTROL Criar]** para abrir o **[!UICONTROL Caixa de diálogo Criar configuração da fonte de dados]**. Especificar um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL Serviço Web SOAP]** do **[!UICONTROL Tipo de serviço]** como opção, navegue e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Próximo]**.
1. Especifique o seguinte para o serviço Web SOAP:

   * URL WSDL do serviço da Web.
   * Terminal de serviço. Especifique um valor nesse campo para substituir o ponto de extremidade de serviço mencionado no WSDL.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica, Autenticação Personalizada ou Token X509 — para acessar o serviço SOAP e, portanto, forneça os detalhes para autenticação.

      Se você selecionar X509 Token como o tipo de Autenticação, configure o certificado X509. Para obter mais informações, consulte [Configurar certificados](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Especifique o alias do KeyStore para o certificado X509 no **[!UICONTROL Alias da chave]** campo. Especifique o tempo, em segundos, até que a solicitação de autenticação permaneça válida, no **[!UICONTROL Tempo de vida]** campo. Como opção, selecione para assinar o corpo da mensagem ou o cabeçalho do carimbo de data e hora ou ambos.

1. Toque **[!UICONTROL Criar]** para criar a configuração de nuvem para o serviço da Web SOAP.

## Configurar serviços OData {#config-odata}

Um serviço OData é identificado por seu URL raiz do serviço. Para configurar um serviço OData nos serviços em nuvem do AEM, verifique se você tem o URL raiz do serviço para o serviço e faça o seguinte:

>[!NOTE]
>
>Para obter o guia passo a passo para configurar o Microsoft Dynamics 365, online ou no local, consulte [Configuração do Microsoft Dynamics OData](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Ir para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do cloud service.

1. Toque **[!UICONTROL Criar]** para abrir o **[!UICONTROL Caixa de diálogo Criar configuração da fonte de dados]**. Especificar um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL Serviço OData]** do **[!UICONTROL Tipo de serviço]** como opção, navegue e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Próximo]**.
1. Especifique os seguintes detalhes para o serviço OData:

   * URL raiz do serviço do serviço OData a ser configurado.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica ou Autenticação Personalizada — para acessar o serviço OData e fornecer os detalhes para autenticação.

   >[!NOTE]
   >
   >Você deve selecionar o tipo de autenticação OAuth 2.0 para se conectar aos serviços do Microsoft Dynamics usando o ponto de extremidade OData como a raiz do serviço.

1. Toque **Criar** para criar a configuração de nuvem para o serviço OData.

## Próximas etapas {#next-steps}

As fontes de dados foram configuradas. Em seguida, é possível criar um modelo de dados de formulário ou, se já tiver criado um modelo de dados de formulário sem uma fonte de dados, associá-lo às fontes de dados recém-configuradas. Consulte [Criar modelo de dados de formulário](/help/forms/using/create-form-data-models.md) para obter detalhes.
