---
title: Atualização para o AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: Você pode executar uma atualização direta do AEM 6.1 Forms, AEM 6.2 Forms e LiveCycle ES4 SP1 para AEM 6.3 Forms.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 1%

---

# Atualizar para o AEM 6.4 Forms no JEE {#upgrade-to-aem-forms-jee}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Use um dos seguintes caminhos de atualização, conforme apropriado para seu ambiente.

## AEM 6.2 Forms no JEE ou AEM 6.3 Forms no JEE > AEM 6.4 Forms no JEE {#aem-forms-jee-62-63-to-64}

Execute o seguinte procedimento para atualizar o AEM 6.2 Forms existente no JEE ou o AEM 6.3 Forms no JEE para AEM 6.4 Forms no JEE:

1. Baixe o AEM 6.4 Forms no JEE no instalador [Site de Licenciamento de Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de Manutenção e Suporte para baixar o instalador.
1. Consulte [Atualizar lista de verificação e planejamento](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) para saber mais sobre as verificações a serem executadas para garantir uma atualização bem-sucedida.
1. Consulte [Preparação para atualizar para o AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) para aprender e executar as tarefas que garantem que a atualização seja executada corretamente com o mínimo de tempo de inatividade do servidor.
1. Dependendo do ambiente e do servidor de aplicativos existentes, escolha um dos documentos a seguir e siga as instruções.

   * [Atualização do AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para JBoss](assets/upgrade-jboss.pdf)
   * [Atualização do AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic.pdf)
   * [Atualização do AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para WebSphere](assets/upgrade-websphere.pdf)
   * [Atualização do AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms em JEE > AEM 6.3 Forms no JEE {#aem-forms-jee-60-to-63}

A atualização direta do LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms para AEM 6.4 Forms não está disponível. Você pode executar uma atualização intermediária para uma ou mais versões do LiveCycle ou AEM Forms e, em seguida, atualizar do AEM 6.4 Forms. Para obter a lista de versões intermediárias e as instruções de atualização correspondentes, consulte [Escolha um caminho de atualização](upgrade.md).

## LiveCycle ES4 SP1 > AEM 6.4 Forms no JEE {#livecycle-es4sp1-forms-jee}

Atualizar o LiveCycle ES4 SP1 para AEM 6.4 Forms no JEE é uma atualização pronta para uso, pois envolve a migração de ativos e dados de versões anteriores para as novas instâncias (novas versões) dos servidores de aplicativos, sistemas operacionais e bancos de dados compatíveis.

Veja a seguir uma visão geral do procedimento para atualizar um servidor LiveCycle ES4 SP1 existente para AEM 6.4 Forms. Para obter instruções detalhadas, consulte os documentos listados no final do procedimento.

1. Antes da atualização:

   1. Baixe o AEM 6.4 Forms no JEE no instalador [Site de Licenciamento de Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de Manutenção e Suporte para baixar o instalador.
   1. Decida o tipo de Repositório de Conteúdo (Repositório CRX) a ser usado. Somente alguns recursos AEM Forms em JEE usam a persistência do Repositório de conteúdo para armazenar conteúdo e ativos. Instale e configure o Repositório de Conteúdo somente se planeja usar esse AEM Forms nos recursos do JEE:

      * No LiveCycle ES4 SP1, os recursos de Gerenciamento de correspondência, Portal Forms, Espaço de trabalho HTML e Relatórios de processos usam o Repositório de conteúdo. Se você não tiver usado esses recursos no LiveCycle ES4 e planejar não usá-los no AEM Forms, o Repositório de Conteúdo não será necessário.
      * No AEM Forms, Adaptive Forms, Correspondence Management, HTML5 Forms (conhecido como Mobile Forms no LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Process Reporting, Forms fluxos de trabalho centrados no OSGi, os recursos usam o Repositório de Conteúdo. Se você planeja usar o AEM Forms para esses recursos, é necessário o Repositório de Conteúdo.
      * Não é necessário o Repositório de Conteúdo para a Segurança de Documentos do AEM Forms.

      Além disso, os tipos de repositório do LiveCycle e do AEM Forms são diferentes. Para obter os tipos de repositório disponíveis e informações relacionadas, consulte [Como escolher um tipo de persistência para uma instalação do AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Crie um backup do conteúdo e dos dados do LiveCycle ES4 SP1:

      Crie um backup do banco de dados LiveCycle ES4 SP1, do Armazenamento de dados global (GDS) e do repositório crx (não é necessário para segurança de documentos). Se estiver atualizando para a persistência de MongoMK ou RDBMK, exporte os ativos de gerenciamento de correspondência do LiveCycle ES4 SP1 em um arquivo .cmp e forme os ativos como um pacote de AEM.

   1. Certifique-se de que a plataforma existente (ou seja, servidor de aplicativos, banco de dados, sistema operacional, Adobe Acrobat, aplicativos de terceiros e hardware) seja compatível com AEM 6.4 Forms no JEE. Para obter informações sobre hardware e software compatíveis, consulte [Combinações de plataforma compatíveis](/help/forms/using/aem-forms-jee-supported-platforms.md) documento.

      Se você criar uma nova instância do banco de dados, importe os dados do backup na etapa 3 para o banco de dados. Para obter informações sobre como importar dados para um banco de dados, consulte a documentação do fornecedor do banco de dados correspondente.

      >[!NOTE]
      >
      >Se você estiver usando o formato de persistência RDBMK, use um único banco de dados para a persistência do repositório e serviços de documento em execução no AEM Forms no JEE.


1. Execute a atualização:

   1. Instale o AEM 6.4 Forms no JEE em um novo servidor executando o programa de instalação. O instalador coloca todos os arquivos necessários em seu computador, dentro de uma estrutura de diretório de instalação.
   1. Após a conclusão da instalação, execute o **Gerenciador de configuração** para configurar vários módulos AEM Forms e definir as configurações apropriadas. Juntamente com as configurações de configuração, ele permite especificar o caminho do Armazenamento de dados global (GDS) e do repositório crx.

      >[!NOTE]
      >
      >Na tela Atualizar seleção de tarefa , selecione o **[!UICONTROL Atualização do Adobe Experience Manager Forms 6.2.0]** opção. O **[!UICONTROL Atualização do Adobe Experience Manager Forms 6.2.0]** permite que o gerenciador de configuração atualize do LiveCycle ES4 SP1 para AEM 6.4 Forms.

   1. (Não é necessário para o módulo de segurança de documentos do AEM Forms) Importe o conteúdo para o Repositório de Conteúdo (CRX-Repository) para AEM servidor Forms 6.4.

      >[!NOTE]
      >
      >* Depois que o crx-repository for atualizado e o conteúdo for migrado, altere a senha da conta de administrador. Para obter instruções detalhadas, consulte [Alterar a senha de um usuário existente](/help/sites-administering/granite-user-group-admin.md).


1. Execute as tarefas pós-implantação para verificar as credenciais de logon, configurar os serviços de documento, o gerenciamento de correspondência, a segurança do documento e muito mais, dependendo do caso de uso.
1. Verifique se o servidor foi atualizado com êxito:

   Execute algumas operações de rotina no servidor AEM Forms atualizado para garantir que o servidor seja atualizado com êxito. Você pode preencher e enviar alguns formulários migrados ou proteger documentos para garantir uma atualização bem-sucedida.

   >[!NOTE]
   >
   >No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para AEM formulários 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte [Reestruturação do repositório Forms no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Dependendo do ambiente e do servidor de aplicativos existentes, escolha um dos seguintes documentos e siga as instruções detalhadas:**

* [Atualização do LiveCycle ES4 SP1 para AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Atualização do LiveCycle ES4 SP1 para AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Atualização do LiveCycle ES4 SP1 para AEM 6.4 Forms para WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Atualizar do LiveCycle ES4 SP1 para o AEM 6.4 Forms usando o JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms no JEE {#livecycle-es3-forms-jee}

Atualizar o LiveCycle ES3 para AEM 6.4 Forms no JEE é uma atualização pronta para uso, pois envolve a migração de ativos e dados de versões anteriores para as novas instâncias (novas versões) dos servidores de aplicativos, sistemas operacionais e bancos de dados compatíveis.

Veja a seguir uma visão geral do procedimento para atualizar um servidor LiveCycle ES3 existente para AEM 6.4 Forms. Para obter instruções detalhadas, consulte os documentos listados no final do procedimento.

1. Antes da atualização:

   1. Baixe o AEM 6.4 Forms no JEE no instalador [Site de Licenciamento de Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de Manutenção e Suporte para baixar o instalador.
   1. Decida o tipo de Repositório de Conteúdo (Repositório CRX) a ser usado. Somente alguns recursos AEM Forms em JEE usam a persistência do Repositório de conteúdo para armazenar conteúdo e ativos. Instale e configure o Repositório de Conteúdo somente se planeja usar esse AEM Forms nos recursos do JEE:

      * No AEM Forms, a Adaptive Forms, o Correspondence Management, o HTML5 Forms, o Forms Portal, o HTML Workspace, o Process Reporting e os workflows centrados no Forms nos recursos OSGi usam o Repositório de Conteúdo. Se você planeja usar o AEM Forms para esses recursos, é necessário o Repositório de Conteúdo.
      * Não é necessário o Repositório de Conteúdo para a Segurança de Documentos do AEM Forms.

      Além disso, os tipos de repositório do LiveCycle e do AEM Forms são diferentes. Para obter os tipos de repositório disponíveis e informações relacionadas, consulte [Como escolher um tipo de persistência para uma instalação do AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Crie um backup do banco de dados LiveCycle ES3, do Armazenamento de dados global (GDS) e do Repositório de conteúdo (não é necessário para segurança de documentos). Se estiver atualizando para a persistência de MongoMK ou RDBMK, exporte ativos de gerenciamento de correspondência do LiveCycle ES3 como um arquivo.
   1. Certifique-se de que a plataforma existente (ou seja, servidor de aplicativos, banco de dados, sistema operacional, Adobe Acrobat, aplicativos de terceiros e hardware) seja compatível com AEM 6.4 Forms no JEE. Para obter informações sobre hardware e software compatíveis, consulte [Combinações de plataforma compatíveis](/help/forms/using/aem-forms-jee-supported-platforms.md) documento.

      Se você criar uma nova instância do banco de dados, importe os dados do backup na etapa 3 para o banco de dados. Para obter informações sobre como importar dados para um banco de dados, consulte a documentação do fornecedor do banco de dados correspondente.

      >[!NOTE]
      >
      >Se você estiver usando o formato de persistência RDBMK, use um único banco de dados para a persistência do repositório e serviços de documento em execução no AEM Forms no JEE.


1. Execute a atualização:

   1. Instale o AEM 6.4 Forms no JEE em um novo servidor executando o programa de instalação. O instalador coloca todos os arquivos necessários em seu computador, dentro de uma estrutura de diretório de instalação.
   1. Após a conclusão da instalação, execute o **Gerenciador de configuração** para configurar vários módulos AEM Forms e definir as configurações apropriadas. Juntamente com as configurações de configuração, ele permite especificar o caminho do Armazenamento de dados global (GDS) e do repositório crx.

      >[!NOTE]
      >
      >Na tela Atualizar seleção de tarefa , selecione o **[!UICONTROL Atualização do Adobe Experience Manager Forms 6.2.0]** opção. O **[!UICONTROL Atualização do Adobe Experience Manager Forms 6.2.0]** permite que o gerenciador de configuração atualize do LiveCycle ES3 para o AEM 6.4 Forms.

   1. (Não é necessário para o módulo de segurança de documento do AEM Forms) Atualize e importe o repositório CRX para AEM servidor Forms 6.4.

      >[!NOTE]
      >
      >Depois que o crx-repository for atualizado e o conteúdo for migrado, altere a senha da conta de administrador. Para obter instruções detalhadas, consulte [Alterar a senha de um usuário existente](/help/sites-administering/granite-user-group-admin.md).
1. Execute as tarefas pós-implantação para verificar as credenciais de logon, configurar os serviços de documento, o gerenciamento de correspondência, a segurança do documento e muito mais, dependendo do caso de uso.
1. Verifique se o servidor foi atualizado com êxito:

   Execute algumas operações de rotina no servidor AEM Forms atualizado para garantir que o servidor seja atualizado com êxito. Você pode preencher e enviar alguns formulários migrados ou proteger documentos para garantir uma atualização bem-sucedida.

   >[!NOTE]
   >
   >No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para AEM formulários 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte [Reestruturação do repositório Forms no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Dependendo do ambiente e do servidor de aplicativos existentes, escolha um dos seguintes documentos e siga as instruções detalhadas:**

* [Atualizar do LiveCycle ES3 para o AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Atualização do LiveCycle ES3 para o AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Atualizar do LiveCycle ES3 para o AEM 6.4 Forms para WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Atualize do LiveCycle ES3 para o AEM 6.4 Forms usando o JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
