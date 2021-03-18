---
title: Configurar o AEM Assets com o Brand Portal
description: 'Saiba como configurar o AEM Assets com o Brand Portal para publicar ativos e coleções no Brand Portal. '
contentOwner: VG
feature: Brand Portal
role: Administrador
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1650'
ht-degree: 41%

---


# Configurar o AEM Assets com o Brand Portal {#configure-integration-64}

O Adobe Experience Manager (AEM) Assets é configurado com o Brand Portal por meio de [!DNL Adobe I/O], que obtém um token IMS para autorização do locatário do Brand Portal.

>[!NOTE]
>
>A configuração do AEM Assets com o Brand Portal via [!DNL Adobe I/O] é compatível com o AEM 6.4.8.0 e superior.
>
>Anteriormente, o Brand Portal era configurado na interface clássica por meio do Gateway OAuth herdado, que usa a troca de token JWT para obter um token de acesso IMS para autorização.

>[!TIP]
>
>***Somente para clientes existentes***
>
>É recomendável continuar usando a configuração existente do Gateway OAuth. Caso encontre problemas com a configuração herdada do Gateway OAuth, exclua a configuração existente e crie uma nova configuração por meio de [!DNL Adobe I/O].

Esta ajuda descreve os dois casos de uso a seguir:

* [Nova configuração](#configure-new-integration-64): Se você for um novo usuário do Brand Portal e quiser configurar a instância de autor do AEM Assets com o Brand Portal, poderá criar uma nova configuração no  [!DNL Adobe I/O].
* [Atualizar configuração](#upgrade-integration-64): Se você for um usuário existente do Brand Portal com sua instância de autor do AEM Assets configurada com o Brand Portal no Gateway OAuth herdado, é recomendável excluir as configurações existentes e criar nova configuração no  [!DNL Adobe I/O].

As informações fornecidas baseiam-se no pressuposto de que qualquer pessoa que leia esta Ajuda está familiarizada com as seguintes tecnologias:

* Instalação, configuração e administração de pacotes Adobe Experience Manager e AEM

* Usando sistemas operacionais Linux e Microsoft Windows

## Pré-requisitos {#prerequisites}

Você precisa do seguinte para configurar o AEM Assets com o Brand Portal:

* Uma instância de autor do AEM Assets ativa e em execução com o Service Pack mais recente.
* URL do locatário do Brand Portal.
* Um usuário com privilégios de administrador do sistema na organização IMS do locatário do Brand Portal.

[Baixe e instale o AEM 6.4](#aemquickstart)

[Baixe e instale o AEM Service Pack mais recente](#servicepack)

### Baixe e instale o AEM 6.4 {#aemquickstart}

É recomendável ter o AEM 6.4 para configurar uma instância de autor AEM. Se você não tiver o AEM ativado e em execução, baixe-o dos seguintes locais:

* Se você for um cliente AEM existente, baixe o AEM 6.4 do [site de licenciamento do Adobe](http://licensing.adobe.com).

* Se você for um parceiro de Adobe, use [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar AEM 6.4.

Depois de baixar o AEM, para obter instruções sobre como configurar uma instância de autor de AEM, consulte [implantar e manter](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall).

### Baixe e instale AEM Service Pack mais recente {#servicepack}

Para obter instruções detalhadas, consulte

* [Notas de versão do AEM 6.4 Service Pack ](https://helpx.adobe.com/br/experience-manager/6-4/release-notes/sp-release-notes.html)

**Entre em contato com o** Atendimento ao cliente se não conseguir encontrar o pacote de AEM ou o Service Pack mais recente.

## Criar configuração {#configure-new-integration-64}

Execute as seguintes etapas na sequência listada se estiver configurando o AEM Assets com o Brand Portal pela primeira vez:

1. [Obter certificado público](#public-certificate)
1. [ [!DNL Adobe I/O] Criar integração](#createnewintegration)
1. [Criar configuração de conta IMS](#create-ims-account-configuration)
1. [Configurar o serviço em nuvem](#configure-the-cloud-service)
1. [Testar configuração](#test-integration)

>[!NOTE]
>
>Uma instância de autor do AEM Assets só deve ser configurada com um locatário do Brand Portal.

### Criar configuração IMS {#create-ims-configuration}

A configuração IMS autentica seu locatário do Brand Portal com a instância do autor do AEM Assets.

A configuração IMS inclui duas etapas:

* [Obter certificado público](#public-certificate)
* [Criar configuração de conta IMS](#create-ims-account-configuration)

### Obter certificado público {#public-certificate}

O certificado público permite autenticar seu perfil em [!DNL Adobe I/O].

1. Faça logon na instância do autor do AEM Assets
URL padrão: http:// localhost:4502/aem/start.html
1. No painel **Ferramentas** ![Ferramentas](assets/tools.png), navegue até **[!UICONTROL Segurança]** >> **[!UICONTROL Configurações do Adobe IMS]**.

   ![Interface do usuário de configuração de conta do Adobe IMS](assets/ims-config1.png)

1. A página Configurações do Adobe IMS é aberta.

   Clique em **[!UICONTROL Criar]**.

   Isso o levará à página **[!UICONTROL Configuração técnica de conta do Adobe IMS]**.

1. Por padrão, a guia **Certificado** é aberta.

   Em **Solução da nuvem**, selecione **[!UICONTROL Adobe Brand Portal]**.

1. Marque a caixa de seleção **[!UICONTROL Criar novo certificado]** e especifique um **alias** para o certificado. O alias atua como nome da caixa de diálogo.

1. Clique em **[!UICONTROL Criar certificado]**. Uma caixa de diálogo é exibida. Clique em **[!UICONTROL OK]** para gerar o certificado público.

   ![Criar certificado](assets/ims-config2.png)

1. Clique em **[!UICONTROL Baixar chave pública]** e salve o arquivo de certificado *AEM-Adobe-IMS.crt* no computador. O arquivo de certificado é usado para [criar [!DNL Adobe I/O] integração](#createnewintegration).

   ![Baixar certificado](assets/ims-config3.png)

1. Clique em **[!UICONTROL Avançar]**.

   Na guia **Conta**, crie a conta do Adobe IMS, mas para isso você precisará dos detalhes de integração. Mantenha esta página aberta por enquanto.

   Abra uma nova guia e [Create [!DNL Adobe I/O] integration](#createnewintegration) para obter os detalhes de integração das configurações da conta IMS.

### Criar [!DNL Adobe I/O] integração {#createnewintegration}

[!DNL Adobe I/O]A integração do gera a chave da API, o segredo do cliente e a carga (JWT), que são necessários para configurar as configurações da conta do IMS.

1. Faça logon no Console [!DNL Adobe I/O] com privilégios de administrador de sistema na organização IMS do locatário do Brand Portal.

   URL padrão: [https://console.adobe.io/](https://console.adobe.io/)

1. Clique em **[!UICONTROL Criar integração]**.

1. Selecione **[!UICONTROL Acessar uma API]** e clique em **[!UICONTROL Continuar]**.

   ![Criar nova integração](assets/create-new-integration1.png)

1. Uma nova página de integração é exibida.

   Selecione sua organização na lista suspensa.

   Em **[!UICONTROL Experience Cloud]**, selecione **[!UICONTROL AEM Brand Portal]** e clique em **[!UICONTROL Continuar]**.

   Se a opção Brand Portal estiver desativada para você, verifique se selecionou a organização correta na caixa suspensa acima da opção **[!UICONTROL Serviços da Adobe]**. Se não souber sua organização, entre em contato com o administrador.

   ![Criar integração](assets/create-new-integration2.png)

1. Especifique um nome e uma descrição para a integração. Clique em **[!UICONTROL Selecionar um arquivo do seu computador]** e faça upload do arquivo `AEM-Adobe-IMS.crt` baixado na seção [obter certificados públicos](#public-certificate).

1. Selecione o perfil da organização.

   Ou selecione o **[!UICONTROL Assets Brand Portal]** e clique em **[!UICONTROL Criar integração]**. A integração é criada.

1. Clique em **[!UICONTROL Continuar para obter detalhes de integração]** para visualizar as informações de integração.

   Copie a **[!UICONTROL chave da API]**

   Clique em **[!UICONTROL Recuperar segredo do cliente]** e copie a chave Segredo do cliente.

   ![Chave da API, segredo do cliente e informações de carga de uma integração](assets/create-new-integration3.png)

1. Navegue até a guia **[!UICONTROL JWT]** e copie a carga **[!UICONTROL JWT]**.

   As informações da chave da API, da chave Segredo do cliente e da carga JWT serão usadas para criar a configuração da conta do IMS.

### Criar configuração de conta IMS {#create-ims-account-configuration}

Verifique se você executou as seguintes etapas:

* [Obter certificado público](#public-certificate)
* [ [!DNL Adobe I/O] Criar integração](#createnewintegration)

**Etapas para criar a configuração da conta IMS:**

1. Abra a página Configuração IMS, guia **[!UICONTROL Contas]**. Você manteve a página aberta no final da seção, [Obter certificado público](#public-certificate).

1. Especifique um **[!UICONTROL Título]** para a conta IMS.

   No **[!UICONTROL Servidor de autorização]**, insira o URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Cole a chave da API, o segredo do cliente e a carga JWT copiados no final de [Create [!DNL Adobe I/O] integration](#createnewintegration).

   Clique em **[!UICONTROL Criar]**.

   A integração é criada.

   ![Configurar a conta IMS](assets/create-new-integration6.png)

1. Selecione a configuração IMS e clique em **[!UICONTROL Verificar integridade]**. Uma caixa de diálogo é exibida.

   Clique em **[!UICONTROL Verificar]**. Ao se conectar com êxito, a mensagem *Token recuperado com êxito* é exibida.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Você deve ter apenas uma configuração IMS. Não crie várias configurações IMS.
>
>A configuração IMS deve ser aprovada na verificação de integridade. Se a configuração não for aprovada na verificação de integridade, ela será inválida. Você deve excluí-la e criar uma configuração nova e válida.

### Configurar o serviço em nuvem {#configure-the-cloud-service}

Execute as seguintes etapas para criar a configuração do serviço em nuvem do Brand Portal:

1. Faça logon na instância do autor do AEM Assets

   URL padrão: http:// localhost:4502/aem/start.html
1. No painel **Ferramentas** ![Ferramentas](assets/tools.png), navegue até **[!UICONTROL Cloud Services > AEM Brand Portal]**.

   A página Configurações do Brand Portal é aberta.

1. Clique em **[!UICONTROL Criar]**.

1. Especifique um **[!UICONTROL Título]** para a configuração.

   Selecione a Configuração IMS criada na etapa e [crie a configuração da conta IMS](#create-ims-account-configuration).

   No **[!UICONTROL URL de serviço]**, insira o URL do locatário do Brand Portal.

   ![](assets/create-cloud-service.png)

1. Clique em **[!UICONTROL Salvar e fechar]**. A configuração da nuvem é criada. A instância do autor do AEM Assets agora está integrada ao locatário do Brand Portal.

### Testar configuração{#test-integration}

1. Faça logon na instância do autor do AEM Assets

   URL padrão: http:// localhost:4502/aem/start.html

1. No painel **Ferramentas** ![Ferramentas](assets/tools.png), navegue até **[!UICONTROL Implantação > Replicação]**.

   ![](assets/test-integration1.png)

1. A página Replicação é aberta.

   Clique em **[!UICONTROL Agentes no autor]**.

   ![](assets/test-integration2.png)

1. Quatro agentes de replicação são criados para cada locatário.

   Localize os agentes de replicação do locatário do Brand Portal.

   Clique no URL do agente de replicação.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Os agentes de replicação trabalham em paralelo e compartilham a distribuição de tarefas igualmente, aumentando assim a velocidade de publicação em quatro vezes a velocidade original. Depois que o serviço de nuvem é configurado, não é necessária configuração adicional para habilitar os agentes de replicação que são ativados por padrão para habilitar a publicação paralela de vários ativos.

1. Para verificar a conexão entre o autor do AEM Assets e o Brand Portal, clique em **[!UICONTROL Testar Conexão]**.

   ![](assets/test-integration4.png)

1. Examine a parte inferior dos resultados do teste para verificar se a replicação foi bem-sucedida.

   ![](assets/test-integration5.png)


1. Verifique os resultados do teste em todos os quatro agentes de replicação um por um.

   >[!NOTE]
   >
   >Evite desativar qualquer um dos agentes de replicação, pois isso pode causar falha na replicação de alguns ativos.
   >
   >Certifique-se de que todos os quatro agentes de replicação estejam configurados para evitar o erro de tempo limite. Consulte [solucionar problemas na publicação paralela no Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).

O Brand Portal foi configurado com êxito com a instância do autor do AEM Assets. Agora você pode:

* [Publicar ativos do AEM Assets no Brand Portal](../assets/brand-portal-publish-assets.md)
* [Publicar pastas do AEM Assets no Brand Portal](../assets/brand-portal-publish-folder.md)
* [Publicar coleções do AEM Assets no Brand Portal](../assets/brand-portal-publish-collection.md)
* [Configurar a ](https://docs.adobe.com/content/help/pt-BR/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) origem dos ativos, permitindo que os usuários do Brand Portal contribuam e publiquem ativos no AEM Assets.

## Atualizar configuração {#upgrade-integration-64}

Execute as seguintes etapas na sequência listada para atualizar as configurações existentes:
1. [Verificar trabalhos em execução](#verify-jobs)
1. [Excluir configurações existentes](#delete-existing-configuration)
1. [Criar configuração](#configure-new-integration-64)

### Verificar tarefas em execução {#verify-jobs}

Certifique-se de que nenhum trabalho de publicação esteja em execução na instância do autor do AEM Assets antes de fazer qualquer modificação. Para isso, você pode verificar todos os quatro agentes de replicação e garantir que a fila seja ideal/vazia.

1. Faça logon na instância do autor do AEM Assets

   URL padrão: http:// localhost:4502/aem/start.html

1. No painel **Ferramentas** ![Ferramentas](assets/tools.png), navegue até **[!UICONTROL Implantação > Replicação]**.

1. A página Replicação é aberta.

   Clique em **[!UICONTROL Agentes no autor]**.

   ![](assets/test-integration2.png)

1. Localize os agentes de replicação do locatário do Brand Portal.

   Certifique-se de que a **Fila esteja inativa** para todos os agentes de replicação, nenhum trabalho de publicação está ativo.

   ![](assets/test-integration3.png)

### Excluir configurações existentes {#delete-existing-configuration}

Você deve executar a seguinte lista de verificação ao excluir a configuração existente.
* Excluir todos os quatro agentes de replicação
* Excluir serviço em nuvem
* Excluir usuário MAC

Execute as seguintes etapas para excluir a configuração existente:

1. Faça logon na instância de autor do AEM Assets e abra o CRX Lite como administrador.

   URL padrão: http:// localhost:4502/crx/de/index.jsp

1. Navegue até `/etc/replications/agents.author` e exclua todos os quatro agentes de replicação do locatário do Brand Portal.

   ![](assets/delete-replication-agent.png)

1. Navegue até `/etc/cloudservices/mediaportal` e exclua a **configuração do Cloud Service**.

   ![](assets/delete-cloud-service.png)

1. Navegue até `/home/users/mac` e exclua o **usuário MAC** do locatário do Brand Portal.

   ![](assets/delete-mac-user.png)


Agora você pode [criar configuração](#configure-new-integration-64) na instância do autor do AEM 6.4 em [!DNL Adobe I/O].



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Depois que a replicação for bem-sucedida, você poderá publicar ativos, pastas e coleções no Brand Portal. Para obter detalhes, consulte:

* [Publicar ativos no Brand Portal](brand-portal-publish-assets.md)
* [Publicar ativos e pastas no Brand Portal](brand-portal-publish-folder.md)
* [Publicar coleções no Brand Portal](brand-portal-publish-collection.md)
