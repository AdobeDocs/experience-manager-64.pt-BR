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
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 9%

---

# Atualizar para AEM 6.4 Forms no OSGi {#upgrade-to-aem-forms-osgi}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Use um dos seguintes caminhos de atualização, conforme apropriado para seu ambiente.

## AEM 6.2 Forms ou AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Você pode fazer uma atualização direta do AEM 6.2 Forms ou AEM 6.3 Forms para AEM 6.4 Forms. Faça o seguinte:

1. Atualize a instância de AEM existente para AEM 6.4. As etapas estão listadas abaixo:

   1. Instale o service pack e os patches mais recentes para o AEM 6.2 Forms ou AEM 6.3 Forms. Para obter detalhes, consulte:

      * [Notas de versão do AEM 6.2](https://helpx.adobe.com/br/experience-manager/6-2/release-notes.html)
      * [Notas de versão do AEM 6.3](https://helpx.adobe.com/br/experience-manager/6-3/release-notes.html)
      * [Hub de AEM](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html)
   1. Prepare a instância de origem para a atualização. Para obter etapas detalhadas, consulte [Atualização para o AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Baixe o [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Somente instalações baseadas em Unix/Linux)** Se você estiver usando UNIX ou Linux como o sistema operacional subjacente, abra a janela do terminal, navegue até a pasta que contém crx-quickstart e execute o seguinte comando:

      `chmod -R 755 ../crx-quickstart`

   1. Atualize sua instância do AEM para AEM 6.3. Para obter instruções passo a passo, consulte [Atualização para o AEM 6.4](/help/sites-deploying/upgrade.md).

      Antes de continuar com as próximas etapas, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no &lt;crx-repository>/error.log .

      >[!NOTE]
      >
      >Depois que o servidor estiver funcionando, alguns pacotes do AEM Forms permanecerão no estado de instalação. O número de pacotes pode variar para cada instalação. Você pode ignorar com segurança o estado desses pacotes. Os pacotes estão listados em `https://[server]:[port]/system/console/`.


1. Instale o pacote complementar do AEM Forms. As etapas estão listadas abaixo:

   1. Abra a [Distribuição de softwares](https://experience.adobe.com/downloads). Você precisa de uma Adobe ID para fazer logon na Distribuição de softwares.
   1. Clique em **[!UICONTROL Adobe Experience Manager]** disponível no menu de cabeçalho.
   1. No **[!UICONTROL Filtros]** seção:
      1. Selecionar **[!UICONTROL Forms]** do **[!UICONTROL Solução]** lista suspensa.
      1. Selecione a versão e o tipo do pacote. Também é possível usar a variável **[!UICONTROL Pesquisar downloads]** para filtrar os resultados.
   1. Toque no nome do pacote aplicável ao seu sistema operacional e selecione **[!UICONTROL Aceitar termos do EULA]** e toque em **[!UICONTROL Baixar]**.
   1. Abra [Gerenciador de pacotes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=pt-BR) e clique em **[!UICONTROL Fazer upload de pacote]** para fazer upload do pacote.
   1. Selecione o pacote e clique em **[!UICONTROL Instalar]**.

      Você também pode baixar o pacote usando o link direto listado em [Versões do AEM Forms](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) artigo 10. o

      >[!NOTE]
      >
      >Depois que o pacote for instalado, você será solicitado a reiniciar a instância do AEM. **Não pare imediatamente o servidor.** Antes de parar o servidor do AEM Forms, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no &lt;crx-repository>/error.log e o log é estável. Observe também que alguns pacotes podem permanecer no estado instalado. Você pode ignorar com segurança o estado desses pacotes.

   1. Pare a instância de AEM e exclua os seguintes arquivos:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Inicie a instância do AEM.


1. Execute atividades pós-instalação.

   * **Executar Utilitário de Migração**

      O utilitário de migração torna os ativos de gerenciamento de correspondência e formulários adaptáveis das versões anteriores compatíveis com AEM formulários 6.4. Você pode baixar o utilitário da Distribuição de software AEM. Para obter informações passo a passo sobre como configurar e usar o utilitário de migração, consulte [utilitário de migração](/help/forms/using/migration-utility.md).

      Se estiver usando [Amostra para integrar componentes de rascunhos e envios](integrate-draft-submission-database.md) com o banco de dados e atualizando de uma versão anterior, execute as seguintes consultas SQL após executar a atualização:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Se estiver atualizando do AEM 6.2 Forms ou versões anteriores apenas) Reconfigure o Acrobat Sign**

      Se tiver o Acrobat Sign configurado na versão anterior do AEM Forms, reconfigure o Acrobat Sign a partir dos serviços da AEM Cloud. Para obter mais detalhes, consulte [Integrar o Acrobat Sign ao AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Se estiver atualizando do AEM 6.2 Forms ou versões anteriores somente) Reconfigure análises e relatórios**

      No AEM 6.4 Forms, a variável de tráfego para origem e evento bem-sucedido para impressão não estão disponíveis. Portanto, quando você atualiza do AEM 6.2 Forms ou versões anteriores, o AEM Forms para de enviar dados para o servidor Adobe Analytics e os relatórios de análise para formulários adaptáveis não estão disponíveis. Além disso, o AEM 6.4 Forms apresenta variáveis de tráfego para a versão de análise de formulário e evento bem-sucedido pela quantidade de tempo gasto em um campo. Assim, reconfigure análises e relatórios para o seu ambiente AEM Forms. Para obter etapas detalhadas, consulte [Configuração de análises e relatórios](/help/forms/using/configure-analytics-forms-documents.md).

1. Verifique se o servidor foi atualizado com êxito, se todos os dados também foram migrados com êxito e se podem operar normalmente.

   * **Verifique o status dos pacotes:** Certifique-se de que todos os pacotes estejam no estado ativo.
   * **Verificar replicação e replicação inversa:** Publique, preencha e envie alguns formulários migrados. Verifique também os dados enviados.
   * **Verifique o acesso às interfaces de usuário do administrador e desenvolvedor:** Faça logon AEM instância em uma conta de administrador e verifique se você tem acesso aos seguintes URLs:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para AEM formulários 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte [Reestruturação do repositório Forms no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms e AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

Caminho de atualização direta de **Forms do AEM 6.0** e **AEM 6.1 Forms** para AEM 6.4 o Forms não está disponível. Executar uma [atualização para o AEM 6.2 Forms](/help/forms/using/upgrade.md) ou [atualização para o AEM 6.3 Forms](/help/forms/using/upgrade.md) e atualize do AEM 6.2 Forms ou AEM 6.3 Forms para AEM 6.4 Forms.
