---
title: Configurar fontes de dados
seo-title: Configurar fontes de dados
description: Saiba como configurar diferentes tipos de fontes de dados e aproveitar para criar modelos de dados de formulário.
seo-description: Saiba como configurar diferentes tipos de fontes de dados e aproveitar para criar modelos de dados de formulário.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 0%

---


# Configurar fontes de dados {#configure-data-sources}

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
1. Procure a configuração **[!UICONTROL Apache Sling Connection Pool DataSource]**. Toque em para abrir a configuração no modo de edição.
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
   >1. No campo **[!UICONTROL Texto simples]**, especifique a senha ou qualquer sequência de caracteres a ser criptografada e clique em **[!UICONTROL Protect]**.

   >
   >O texto criptografado aparece no campo Texto protegido que pode ser especificado na configuração.

1. Habilite **[!UICONTROL Testar em linha de crédito]** ou **[!UICONTROL Testar em retorno]** para especificar que os objetos são validados antes de serem emprestados ou retornados de e para o pool, respectivamente.
1. Especifique uma consulta SQL SELECT no campo **[!UICONTROL Validation Query]** para validar conexões do pool. A consulta deve retornar pelo menos uma linha. Com base no seu banco de dados, especifique um dos seguintes:

   * SELECT 1 (MySQL e MS SQL)
   * SELECIONE 1 de duplo (Oracle)

1. Toque em **[!UICONTROL Salvar]** para salvar a configuração.

## Configurar AEM perfil do usuário {#configure-aem-user-profile}

Você pode configurar AEM perfil de usuário usando a configuração do Conector de perfil de usuário AEM console da Web. Faça o seguinte:

1. Vá para AEM console da Web em `https://[server]:[host]/system/console/configMgr`.
1. Procure por **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** e toque para abrir a configuração no modo de edição.
1. Na caixa de diálogo Configuração do conector do perfil do usuário, é possível adicionar, remover ou atualizar as propriedades do perfil do usuário. As propriedades especificadas estarão disponíveis para uso no modelo de dados de formulário. Use o seguinte formato para especificar as propriedades do perfil de usuário:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Exemplos:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >O **&amp;ast;** no exemplo acima denota todos os nós sob o nó `profile/empLocation/` em AEM perfil de usuário na estrutura CRXDE. Isso significa que o modelo de dados de formulário pode acessar a propriedade `city` do tipo `string` presente em qualquer nó sob o nó `profile/empLocation/`. No entanto, os nós que contêm a propriedade especificada devem seguir uma estrutura consistente.

1. Toque em **[!UICONTROL Salvar]** para salvar a configuração.

## Configurar pasta para configurações do serviço de nuvem {#cloud-folder}

>[!NOTE]
>
>A configuração da pasta de serviços em nuvem é necessária para configurar os serviços em nuvem para os serviços RESTful, SOAP e OData.

Todas as configurações do serviço de nuvem no AEM são consolidadas na pasta `/conf` no repositório AEM. Por padrão, a pasta `conf` contém a pasta `global` onde você pode criar configurações do serviço de nuvem. No entanto, é necessário ativá-lo manualmente para configurações de nuvem. Você também pode criar pastas adicionais em `conf` para criar e organizar as configurações do serviço de nuvem.

Para configurar a pasta das configurações do serviço de nuvem:

1. Vá para **[!UICONTROL Tools > General > Configuration Browser]**.
   * Consulte a [documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.
1. Faça o seguinte para habilitar a pasta global para configurações de nuvem ou ignore esta etapa para criar e configurar outra pasta para configurações do serviço de nuvem.

   1. No **[!UICONTROL Navegador de configuração]**, selecione a pasta `global` e toque em **[!UICONTROL Propriedades]**.
   1. Na caixa de diálogo **[!UICONTROL Configuration Properties]**, ative **[!UICONTROL Cloud Configurations]**.
   1. Toque em **[!UICONTROL Salvar e fechar]** para salvar a configuração e sair da caixa de diálogo.

1. No **[!UICONTROL Navegador de configuração]**, toque em **[!UICONTROL Criar]**.
1. Na caixa de diálogo **[!UICONTROL Criar configuração]**, especifique um título para a pasta e habilite **[!UICONTROL Configurações de nuvem]**.
1. Toque em **[!UICONTROL Criar]** para criar a pasta ativada para as configurações do serviço de nuvem.

## Configurar serviços Web RESTful {#configure-restful-web-services}

O serviço Web RESTful pode ser descrito usando [Especificações do Swagger](https://swagger.io/specification/) no formato JSON ou YAML em um arquivo de definição do Swagger. Para configurar o serviço Web RESTful nos serviços em nuvem do AEM, verifique se você tem o arquivo Swagger no sistema de arquivos ou o URL onde o arquivo está hospedado.

Faça o seguinte para configurar os serviços RESTful:

1. Vá para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do serviço de nuvem.

1. Toque em **[!UICONTROL Criar]** para abrir a caixa de diálogo **[!UICONTROL Criar configuração da fonte de dados]**. Especifique um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL RESTful Service]** no menu suspenso **[!UICONTROL Service Type]**, procure e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Next]**.
1. Especifique os seguintes detalhes para o serviço RESTful:

   * Selecione URL ou Arquivo na lista suspensa Fonte do Swagger e especifique o URL do Swagger correspondente para o arquivo de definição do Swagger ou faça o upload do arquivo Swagger do sistema de arquivos local.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica, Chave da API ou Autenticação Personalizada — para acessar o serviço RESTful e, de acordo, fornecer detalhes para autenticação.

1. Toque em **[!UICONTROL Criar]** para criar a configuração de nuvem para o serviço RESTful.

## Configurar serviços Web SOAP {#configure-soap-web-services}

Os serviços da Web baseados em SOAP são descritos usando [Web Services Description Language (WSDL) Specification](https://www.w3.org/TR/wsdl). Para configurar o serviço da Web baseado em SOAP nos serviços em nuvem do AEM, verifique se você tem o URL WSDL para o serviço da Web e faça o seguinte:

1. Vá para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do serviço de nuvem.

1. Toque em **[!UICONTROL Criar]** para abrir a caixa de diálogo **[!UICONTROL Criar configuração da fonte de dados]**. Especifique um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL SOAP Web Service]** no menu suspenso **[!UICONTROL Service Type]**, navegue e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Next]**.
1. Especifique o seguinte para o serviço Web SOAP:

   * URL WSDL do serviço da Web.
   * Terminal de serviço. Especifique um valor nesse campo para substituir o ponto de extremidade de serviço mencionado no WSDL.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica, Autenticação Personalizada ou Token X509 — para acessar o serviço SOAP e, portanto, forneça os detalhes para autenticação.

      Se você selecionar X509 Token como o tipo de Autenticação, configure o certificado X509. Para obter mais informações, consulte [Configurar certificados](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Especifique o alias do KeyStore para o certificado X509 no campo **[!UICONTROL Key Alias]**. Especifique o tempo, em segundos, até que a solicitação de autenticação permaneça válida, no campo **[!UICONTROL Time To Live]**. Como opção, selecione para assinar o corpo da mensagem ou o cabeçalho do carimbo de data e hora ou ambos.

1. Toque em **[!UICONTROL Criar]** para criar a configuração de nuvem para o serviço Web SOAP.

## Configurar serviços OData {#config-odata}

Um serviço OData é identificado por seu URL raiz do serviço. Para configurar um serviço OData nos serviços em nuvem do AEM, verifique se você tem o URL raiz do serviço para o serviço e faça o seguinte:

>[!NOTE]
>
>Para obter o guia passo a passo para configurar o Microsoft Dynamics 365, online ou no local, consulte [Configuração do Microsoft Dynamics OData](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Vá para **[!UICONTROL Ferramentas > Cloud Services > Fontes de dados]**. Toque para selecionar a pasta onde deseja criar uma configuração de nuvem.

   Consulte [Configurar pasta para configurações do serviço de nuvem](/help/forms/using/configure-data-sources.md#cloud-folder) para obter informações sobre como criar e configurar uma pasta para configurações do serviço de nuvem.

1. Toque em **[!UICONTROL Criar]** para abrir a caixa de diálogo **[!UICONTROL Criar configuração da fonte de dados]**. Especifique um nome e, opcionalmente, um título para a configuração, selecione **[!UICONTROL OData Service]** no menu suspenso **[!UICONTROL Service Type]**, navegue e selecione uma imagem em miniatura para a configuração e toque em **[!UICONTROL Next]**.
1. Especifique os seguintes detalhes para o serviço OData:

   * URL raiz do serviço do serviço OData a ser configurado.
   * Selecione o tipo de autenticação — Nenhum, OAuth2.0, Autenticação Básica ou Autenticação Personalizada — para acessar o serviço OData e fornecer os detalhes para autenticação.

   >[!NOTE]
   >
   >Você deve selecionar o tipo de autenticação OAuth 2.0 para se conectar aos serviços do Microsoft Dynamics usando o ponto de extremidade OData como a raiz do serviço.

1. Toque em **Criar** para criar a configuração de nuvem para o serviço OData.

## Próximas etapas {#next-steps}

As fontes de dados foram configuradas. Em seguida, é possível criar um modelo de dados de formulário ou, se já tiver criado um modelo de dados de formulário sem uma fonte de dados, associá-lo às fontes de dados recém-configuradas. Consulte [Criar modelo de dados de formulário](/help/forms/using/create-form-data-models.md) para obter detalhes.
