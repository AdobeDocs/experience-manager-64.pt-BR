---
title: Integração com o Salesforce
seo-title: Integrating with Salesforce
description: Saiba mais sobre a integração de AEM com o Salesforce.
seo-description: Learn about integrating AEM with Salesforce.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
exl-id: 4c09699a-c7ae-48ee-9423-87ff35b1e9d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 1%

---

# Integração com o Salesforce{#integrating-with-salesforce}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A integração do Salesforce com o AEM fornece recursos de gerenciamento de clientes potenciais e aproveita os recursos existentes fornecidos imediatamente pelo Salesforce. Você pode configurar AEM para publicar leads no Salesforce e criar componentes que acessam dados diretamente do Salesforce.

A integração bidirecional e extensível entre o AEM e o Salesforce permite:

* Organizações para usar e atualizar totalmente os dados e aprimorar a experiência do cliente.
* Envolvimento do marketing para atividades de vendas.
* Organizações para transmitir e receber dados automaticamente de um armazenamento de dados do Salesforce.

Este documento descreve o seguinte:

* como configurar o Salesforce Cloud Services (configurar AEM para integrar com o Salesforce).
* como usar as informações de lead/contato do Salesforce no ClientContext e para personalização.
* como usar o modelo de fluxo de trabalho do Salesforce para publicar AEM usuários como leva ao salesforce.
* como criar um componente que mostre dados do Salesforce.

## Configuração de AEM para integração com o Salesforce {#configuring-aem-to-integrate-with-salesforce}

Para configurar AEM para integrar com o Salesforce, primeiro é necessário configurar um aplicativo de acesso remoto no Salesforce. Em seguida, configure o serviço de nuvem do salesforce para apontar para esse aplicativo de acesso remoto.

>[!NOTE]
>
>Você pode criar uma conta gratuita de desenvolvedor no Salesforce.

Para configurar AEM para integrar com o Salesforce:

1. Em AEM, navegue até **Cloud Services**. Em Serviços de terceiros, clique em **Configurar agora** em **Salesforce**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Crie uma nova configuração, por exemplo, **desenvolvedor**.

   >[!NOTE]
   >
   >A nova configuração redireciona para uma nova página: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Esse é exatamente o mesmo valor que você precisa especificar no URL de retorno ao criar o aplicativo de acesso remoto no Salesforce. Esses valores devem corresponder.

1. Faça logon na conta do salesforce (ou, se não tiver uma), crie uma em [https://developer.force.com](https://developer.force.com).)
1. No Salesforce, navegue até **Criar** > **Aplicativos** para obter **Aplicativos conectados** (em versões anteriores do salesforce, o fluxo de trabalho era **Implantar** > **Acesso remoto**).
1. Clique em **Novo** para conectar AEM com o Salesforce.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Insira o **Nome do aplicativo conectado**, **Nome da API** e **E-mail de contato**. Selecione o **Ativar as configurações do OAuth** e digite o **URL de retorno** e adicionar um escopo OAuth (por exemplo, acesso completo). A URL de retorno de chamada é semelhante a: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Altere o nome do servidor/número da porta e o nome da página para corresponder à sua configuração.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Clique em **Salvar** para salvar a configuração do salesforce. O Salesforce cria um **consumer key** e **consumer secret**, que você precisa para AEM configuração.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Talvez seja necessário aguardar vários minutos (até 15 minutos) para que o aplicativo de acesso remoto no Salesforce seja ativado.

1. Em AEM, navegue até **Cloud Services** e navegue até a configuração do salesforce criada anteriormente (por exemplo, **desenvolvedor**). Clique em **Editar** e insira a chave do cliente e o segredo do cliente em salesforce.com.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | URL de login | Este é o Ponto de Extremidade da Autorização do Salesforce. Seu valor é pré-preenchido e serve a maioria dos casos. |
   |---|---|
   | Chave do cliente | Insira o valor obtido na página Registro de aplicativo de acesso remoto em salesforce.com |
   | Segredo do cliente | Insira o valor obtido na página Registro de aplicativo de acesso remoto em salesforce.com |

1. Clique em **Conectar-se ao Salesforce** para se conectar. O Salesforce solicita que você permita que sua configuração se conecte ao salesforce.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   No AEM, uma caixa de diálogo de confirmação é aberta informando que você se conectou com êxito.

1. Navegue até a página raiz do seu site e clique em **Propriedades da página**. Em seguida, selecione **Cloud Services** e adicionar **Salesforce** e selecione a configuração correta (por exemplo, **desenvolvedor**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   Agora você pode usar o modelo de fluxo de trabalho para publicar leads no Salesforce e criar componentes que acessam dados do Salesforce.

## Exportar usuários AEM como leads do Salesforce {#exporting-aem-users-as-salesforce-leads}

Se quiser exportar um usuário AEM como um cliente potencial do salesforce, é necessário configurar o fluxo de trabalho para publicar leads no salesforce.

Para exportar AEM usuários como o Salesforce leva:

1. Navegue até o fluxo de trabalho do Salesforce em `http://localhost:4502/workflow` clicando com o botão direito do mouse no workflow **Exportação do Salesforce.com** e clicando em **Iniciar**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Selecione o usuário AEM que deseja criar como lead como **Carga** para este workflow (inicial -> usuários). Certifique-se de selecionar o nó do perfil do usuário, pois ele contém informações como **givenName**, **familyName** e assim por diante, que são mapeados para o lead do Salesforce **FirstName** e **LastName** campos.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Antes de iniciar esse workflow, há determinados campos obrigatórios que um nó de lead no AEM deve ter antes de ser publicado no Salesforce. Estes **givenName**, **familyName**, **empresa** e **email**. Para ver uma lista completa de mapeamento entre AEM usuário e o lead do Salesforce, consulte [Configuração de mapeamento entre AEM usuário e o cliente potencial do Slaesforce.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Clique em **OK**. As informações do usuário são exportadas para o salesforce.com. Você pode verificá-lo em salesforce.com.

   >[!NOTE]
   >
   >Os registros de erro mostrarão se um lead é importado. Verifique o log de erros para obter mais informações.

### Configuração do fluxo de trabalho de exportação do Salesforce.com {#configuring-the-salesforce-com-export-workflow}

Talvez seja necessário configurar o fluxo de trabalho de exportação do Salesforce.com para corresponder à configuração correta do Salesforce.com ou fazer outras alterações.

Para configurar o workflow de exportação do Salesforce.com:

1. Vá até `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Abra a etapa Exportação do Salesforce.com , selecione o **Argumentos** e selecione a configuração correta que está selecionada e clique em **OK**. Além disso, se desejar que o workflow recrie um lead que foi excluído no Salesforce, marque a caixa de seleção .

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Clique em **Salvar** para salvar as alterações.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Configuração de mapeamento entre AEM usuário e líder do Salesforce {#mapping-configuration-between-aem-user-and-salesforce-lead}

Para exibir ou editar a configuração de mapeamento atual entre um usuário AEM e um lead do Salesforce, abra o Gerenciador de Configuração: `https://<hostname>:<port>/system/console/configMgr` e procurar **Configuração de mapeamento de leads do Salesforce**.

1. Abra o Configuration Manager clicando em **Console da Web** ou ir diretamente para `https://<hostname>:<port>/system/console/configMgr.`
1. Procurar por **Configuração de mapeamento de leads do Salesforce**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Altere os mapeamentos, conforme necessário. O mapeamento padrão segue o padrão** aemUserAttribute=sfLeadAttribute**. Clique em **Salvar** para salvar as alterações.

## Configuração do Salesforce Client Context Store {#configuring-salesforce-client-context-store}

O repositório de contexto do cliente do salesforce mostra informações adicionais sobre o usuário conectado no momento em relação ao que já está disponível no AEM. Ele extrai essas informações adicionais do Salesforce, dependendo da conexão do usuário com o Salesforce.

Para fazer isso, você precisa configurar o seguinte:

1. Vincule um usuário do AEM com uma ID do Salesforce por meio do componente Conexão do Salesforce .
1. Adicione os Dados de perfil do Salesforce na página de contexto do cliente para configurar quais propriedades você deseja ver.
1. (Opcional) Crie um segmento que use os dados do Salesforce Client Context Store.

### Vincular um usuário do AEM com uma ID do Salesforce {#linking-an-aem-user-with-a-salesforce-id}

Você precisa mapear um usuário AEM com uma ID do Salesforce para carregá-la no contexto do cliente. Em um cenário real, você estaria vinculando com base em dados conhecidos do usuário com a validação. Para fins de demonstração, neste procedimento, você usa a variável **Salesforce Connect** componente.

1. Navegue até um site da Web em AEM, faça logon e arraste e solte o **Salesforce Connect** componente do sidekick.

   >[!NOTE]
   >
   >Se a variável **Salesforce Connect** não está disponível, vá para **Design** e selecione-o para torná-lo disponível em **Editar** exibir.

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   Quando você arrasta o componente para a página, ele é exibido **Link para Salesforce=Off**.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >Este componente é somente para fins de demonstração. Para cenários do mundo real, haveria outro processo para vincular/combinar usuários com leads.

1. Depois de arrastar o componente na página, abra-o para configurá-lo. Selecione a configuração, o tipo de contato e o lead ou contato do Salesforce e clique em **OK**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM vincula o usuário ao contato ou ao cliente potencial do Salesforce.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Adicionar dados do Salesforce ao contexto do cliente {#adding-salesforce-data-to-client-context}

Você pode carregar dados do usuário do Salesforce no Contexto do Cliente para usar na personalização:

1. Abra o contexto de cliente que deseja estender navegando até ele, por exemplo, `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. Arraste o **Dados de perfil do Salesforce** para o contexto do cliente.

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. Clique duas vezes no componente para abri-lo. Selecionar **Adicionar item** e selecione uma propriedade na lista suspensa. Adicione quantas propriedades desejar e selecione **OK**.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Agora, você vê propriedades específicas do Salesforce exibidas no contexto do cliente.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Criar um segmento usando dados do Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}

Você pode criar um segmento que usa dados do Salesforce Client Context Store. Para fazer isso:

1. Navegue até a segmentação no AEM acessando **Ferramentas** > **Segmentação** ou indo para [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Crie ou atualize um segmento para incluir dados do Salesforce. Para obter mais informações, consulte [Segmentação](/help/sites-administering/campaign-segmentation.md).

## Pesquisando leads {#searching-leads}

AEM vem com um componente de pesquisa de amostra que pesquisa leads no Salesforce de acordo com os critérios especificados. Esse componente mostra como usar a API REST do Salesforce para procurar objetos do salesforce. Você precisa vincular uma página com uma configuração do Salesforce para acionar uma chamada para salesforce.com.

>[!NOTE]
>
>Este é um componente de amostra que mostra como usar a API REST do Salesforce para consultar objetos do Salesforce. Use-o como exemplo para criar componentes mais complexos com base em suas necessidades.

Para usar este componente:

1. Navegue até a página onde deseja usar essa configuração. Abra as propriedades da página e selecione **Cloud Services.** Clique em **Adicionar serviços** e selecione **Salesforce** e a configuração apropriada e clique em **OK**.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Arraste o componente de pesquisa do Salesforce para a página (desde que ele tenha sido ativado). Para habilitá-lo, vá para o modo Design e adicione-o à área apropriada).

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. Abra o componente de Pesquisa , especifique os parâmetros de pesquisa e clique em **Ok.**

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM exibe os leads especificados em seu componente de pesquisa que correspondem aos critérios especificados.

   ![chlimage_1-101](assets/chlimage_1-101.png)
