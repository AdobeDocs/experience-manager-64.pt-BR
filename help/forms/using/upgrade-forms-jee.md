---
title: Atualizar para o AEM 6.4 Forms
seo-title: Atualizar para o AEM 6.4 Forms
description: 'É possível fazer uma atualização direta do AEM 6.1 Forms, AEM 6.2 Forms e LiveCycle ES4 SP1 para AEM 6.3 Forms. '
seo-description: 'É possível fazer uma atualização direta do AEM 6.1 Forms, AEM 6.2 Forms e LiveCycle ES4 SP1 para AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: f234d368163f4260563d69230a2cbda37b6d315a
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# Atualizar para AEM 6.4 Forms no JEE {#upgrade-to-aem-forms-jee}

Use um dos seguintes caminhos de atualização, conforme apropriado para o seu ambiente.

## AEM 6.2 Forms em JEE ou AEM 6.3 Forms em JEE > AEM 6.4 Forms em JEE {#aem-forms-jee-62-63-to-64}

Execute o seguinte procedimento para atualizar os formulários AEM 6.2 existentes em JEE ou AEM 6.3 Forms em JEE para AEM 6.4 Forms em JEE:

1. Baixe o instalador do AEM 6.4 Forms em JEE do site de licenciamento da [Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de manutenção e suporte para baixar o instalador.
1. Consulte Lista de verificação de [atualização e planejamento](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) para saber mais sobre as verificações a serem feitas para garantir uma atualização bem-sucedida.
1. Consulte [Preparar para atualizar para o AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) para saber e executar as tarefas que garantem que a atualização seja executada corretamente com o mínimo de tempo de inatividade do servidor.
1. Dependendo do seu ambiente e servidor de aplicativos existentes, escolha um dos seguintes documentos e siga as instruções.

   * [Atualize de AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para JBoss](assets/upgrade-jboss.pdf)
   * [Atualize de AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [Atualize de AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Atualize de AEM 6.2 ou AEM 6.3 Forms para AEM 6.4 Forms para JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms em JEE > AEM 6.3 Forms em JEE {#aem-forms-jee-60-to-63}

A atualização direta do LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms para AEM 6.4 Forms não está disponível. Você pode fazer uma atualização intermediária para uma ou mais versões do LiveCycle ou AEM Forms e, em seguida, atualizar do AEM 6.4 Forms. Para obter a lista de versões intermediárias e as instruções de atualização correspondentes, consulte [Escolher um caminho](upgrade.md)de atualização.

## LiveCycle ES4 SP1 > AEM 6.4 Forms em JEE {#livecycle-es4sp1-forms-jee}

A atualização do LiveCycle ES4 SP1 para o AEM 6.4 Forms no JEE é uma atualização fora do local, pois envolve a migração de ativos e dados de versões anteriores para novas instâncias (novas versões) de servidores de aplicativos, sistemas operacionais e bancos de dados suportados.

Veja a seguir uma visão geral do procedimento para atualizar um servidor LiveCycle ES4 SP1 existente para o AEM 6.4 Forms. Para obter instruções detalhadas, consulte os documentos listados no final do procedimento.

1. Antes de atualizar:

   1. Baixe o instalador do AEM 6.4 Forms em JEE do site de licenciamento da [Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de manutenção e suporte para baixar o instalador.
   1. Decida o tipo Repositório de conteúdo (Repositório CRX) a ser usado. Somente alguns formulários AEM em recursos JEE usam a persistência do Repositório de conteúdo para armazenar conteúdo e ativos. Instale e configure o Repositório de conteúdo somente se planeja usar esses formulários AEM nos recursos JEE:

      * No LiveCycle ES4 SP1, os recursos de Gerenciamento de correspondência, Portal de formulários, Espaço de trabalho HTML e Relatórios de processo usam o Repositório de conteúdo. Se você não usou esses recursos no LiveCycle ES4 e planeja não usá-los no AEM Forms, o Repositório de conteúdo não é necessário.
      * Em Formulários AEM, Formulários adaptáveis, Gerenciamento de correspondência, Formulários HTML5 (conhecidos como Formulários móveis no LiveCycle ES4 SP1), Portal de formulários, Espaço de trabalho HTML, Relatórios de processos, workflows centrados no Forms no OSGi, os recursos usam o Repositório de conteúdo. Se você planeja usar o AEM Forms para esses recursos, o Repositório de conteúdo é necessário.
      * Não é necessário o Repositório de conteúdo para a segurança do Documento do AEM Forms.

      Além disso, os tipos de repositório do LiveCycle e do AEM Forms são diferentes. Para obter os tipos de repositório disponíveis e informações relacionadas, consulte [Escolhendo um tipo de persistência para uma instalação](/help/forms/using/choosing-persistence-type-for-aem-forms.md)do AEM Forms.

   1. Crie um backup de dados e conteúdo do LiveCycle ES4 SP1:

      Crie um backup do banco de dados do LiveCycle ES4 SP1, do Global Data Armazenamento (GDS) e do repositório do crx (não é necessário para a segurança do documento). Se você estiver atualizando para persistência MongoMK ou RDBMK, exporte ativos de gerenciamento de correspondência do LiveCycle ES4 SP1 em um arquivo .cmp e forme ativos como um pacote AEM.

   1. Certifique-se de que sua plataforma existente (ou seja, servidor de aplicativos, banco de dados, sistema operacional, Adobe Acrobat, aplicativos de terceiros e hardware) seja compatível com o AEM 6.4 Forms no JEE. Para obter informações sobre hardware e software suportados, consulte o documento [Suported Platform Combinations](/help/forms/using/aem-forms-jee-supported-platforms.md) .

      Se você criar uma nova instância do banco de dados, importe os dados cujo backup foi feito na etapa 3 para o banco de dados. Para obter informações sobre como importar dados para um banco de dados, consulte a documentação do fornecedor do banco de dados correspondente.

      >[!NOTE]
      >
      >Se você estiver usando o formato de persistência RDBMK, use um único banco de dados para a persistência do repositório e para os serviços de documento em execução no AEM Forms no JEE.


1. Execute a atualização:

   1. Instale o AEM 6.4 Forms no JEE em um novo servidor executando o programa de instalação. O instalador coloca todos os arquivos necessários em seu computador, dentro de uma estrutura de diretório de instalação.
   1. Depois que a instalação for concluída, execute o **Configuration Manager** para configurar vários módulos AEM Forms e definir as configurações apropriadas. Juntamente com a configuração de configurações, permite especificar o caminho do Armazenamento de dados globais (GDS) e do repositório crx.

      >[!NOTE]
      >
      >Na tela Atualizar seleção de Tarefa, selecione a opção **[!UICONTROL Atualizar do Adobe Experience Manager Forms 6.2.0]** . A opção **[!UICONTROL Atualizar do Adobe Experience Manager Forms 6.2.0]** permite que o gerenciador de configuração atualize do LiveCycle ES4 SP1 para o AEM 6.4 Forms.

   1. (Não é necessário para o módulo de segurança do documento do AEM Forms) Importe conteúdo para o repositório de conteúdo (CRX-Repository) para o servidor de formulários do AEM 6.4.

      >[!NOTE]
      >
      >* Depois que o repositório crx for atualizado e o conteúdo for migrado, altere a senha da conta do administrador. Para obter instruções detalhadas, consulte [Alteração da senha para um usuário](/help/sites-administering/granite-user-group-admin.md)existente.


1. Execute as tarefas pós-implantação para verificar as credenciais de logon, configurar os serviços do documento, o gerenciamento de correspondência, a segurança do documento e muito mais, dependendo do caso de uso.
1. Verifique se o servidor foi atualizado com êxito:

   Execute algumas operações de rotina no servidor AEM Forms atualizado para garantir que o servidor seja atualizado com êxito. Você pode preencher e enviar alguns formulários migrados ou proteger documentos para garantir uma atualização bem-sucedida.

   >[!NOTE]
   >
   >No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para formulários do AEM 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte Reestruturação do repositório de [formulários no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Dependendo do seu ambiente e servidor de aplicativos existentes, escolha um dos seguintes documentos e siga as instruções detalhadas:**

* [Atualizar do LiveCycle ES4 SP1 para o AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Atualizar do LiveCycle ES4 SP1 para o AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Atualize do LiveCycle ES4 SP1 para o AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Atualize do LiveCycle ES4 SP1 para o AEM 6.4 Forms usando o JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms em JEE {#livecycle-es3-forms-jee}

A atualização do LiveCycle ES3 para o AEM 6.4 Forms no JEE é uma atualização fora do local, pois envolve a migração de ativos e dados de versões anteriores para novas instâncias (novas versões) de servidores de aplicativos, sistemas operacionais e bancos de dados suportados.

A seguir está uma visão geral do procedimento para atualizar um servidor LiveCycle ES3 existente para o AEM 6.4 Forms. Para obter instruções detalhadas, consulte os documentos listados no final do procedimento.

1. Antes de atualizar:

   1. Baixe o instalador do AEM 6.4 Forms em JEE do site de licenciamento da [Adobe (LWS)](https://licensing.adobe.com/). Você precisa de um contrato válido de manutenção e suporte para baixar o instalador.
   1. Decida o tipo Repositório de conteúdo (Repositório CRX) a ser usado. Somente alguns formulários AEM em recursos JEE usam a persistência do Repositório de conteúdo para armazenar conteúdo e ativos. Instale e configure o Repositório de conteúdo somente se planeja usar esses formulários AEM nos recursos JEE:

      * Em Formulários AEM, Formulários adaptáveis, Gerenciamento de correspondência, Formulários HTML5, Portal de formulários, Espaço de trabalho HTML, Relatórios de processos e workflows centrados em formulários em recursos OSGi usam Repositório de conteúdo. Se você planeja usar o AEM Forms para esses recursos, o Repositório de conteúdo é necessário.
      * Não é necessário o Repositório de conteúdo para a segurança do Documento do AEM Forms.

      Além disso, os tipos de repositório do LiveCycle e do AEM Forms são diferentes. Para obter os tipos de repositório disponíveis e informações relacionadas, consulte [Escolhendo um tipo de persistência para uma instalação](/help/forms/using/choosing-persistence-type-for-aem-forms.md)do AEM Forms.

   1. Crie um backup do banco de dados LiveCycle ES3, do Armazenamento de dados global (GDS) e do repositório de conteúdo (não é necessário para a segurança do documento). Se você estiver atualizando para persistência MongoMK ou RDBMK, exporte ativos de gerenciamento de correspondência do LiveCycle ES3 como um arquivo.
   1. Certifique-se de que sua plataforma existente (ou seja, servidor de aplicativos, banco de dados, sistema operacional, Adobe Acrobat, aplicativos de terceiros e hardware) seja compatível com o AEM 6.4 Forms no JEE. Para obter informações sobre hardware e software suportados, consulte o documento [Suported Platform Combinations](/help/forms/using/aem-forms-jee-supported-platforms.md) .

      Se você criar uma nova instância do banco de dados, importe os dados cujo backup foi feito na etapa 3 para o banco de dados. Para obter informações sobre como importar dados para um banco de dados, consulte a documentação do fornecedor do banco de dados correspondente.

      >[!NOTE] Se você estiver usando o formato de persistência RDBMK, use um único banco de dados para a persistência do repositório e para os serviços de documento em execução no AEM Forms no JEE.


1. Execute a atualização:

   1. Instale o AEM 6.4 Forms no JEE em um novo servidor executando o programa de instalação. O instalador coloca todos os arquivos necessários em seu computador, dentro de uma estrutura de diretório de instalação.
   1. Depois que a instalação for concluída, execute o **Configuration Manager** para configurar vários módulos AEM Forms e definir as configurações apropriadas. Juntamente com a configuração de configurações, permite especificar o caminho do Armazenamento de dados globais (GDS) e do repositório crx.

      >[!NOTE] Na tela Atualizar seleção de Tarefa, selecione a opção **[!UICONTROL Atualizar do Adobe Experience Manager Forms 6.2.0]** . A opção **[!UICONTROL Atualizar do Adobe Experience Manager Forms 6.2.0]** permite que o gerenciador de configuração atualize do LiveCycle ES3 para o AEM 6.4 Forms.

   1. (Não é necessário para o módulo de segurança do documento do AEM Forms) Atualize e importe o repositório do CRX para o servidor do AEM 6.4 Forms.

      >[!NOTE] Depois que o repositório crx for atualizado e o conteúdo for migrado, altere a senha da conta do administrador. Para obter instruções detalhadas, consulte [Alteração da senha para um usuário](/help/sites-administering/granite-user-group-admin.md)existente.
1. Execute as tarefas pós-implantação para verificar as credenciais de logon, configurar os serviços do documento, o gerenciamento de correspondência, a segurança do documento e muito mais, dependendo do caso de uso.
1. Verifique se o servidor foi atualizado com êxito:

   Execute algumas operações de rotina no servidor AEM Forms atualizado para garantir que o servidor seja atualizado com êxito. Você pode preencher e enviar alguns formulários migrados ou proteger documentos para garantir uma atualização bem-sucedida.

   >[!NOTE] No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para formulários do AEM 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte Reestruturação do repositório de [formulários no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Dependendo do seu ambiente e servidor de aplicativos existentes, escolha um dos seguintes documentos e siga as instruções detalhadas:**

* [Atualizar do LiveCycle ES3 para o AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Atualize do LiveCycle ES3 para o AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Atualize do LiveCycle ES3 para o AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Atualize do LiveCycle ES3 para o AEM 6.4 Forms usando o recurso JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
