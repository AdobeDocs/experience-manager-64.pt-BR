---
title: Upgrade para o AEM 6.4 Forms
seo-title: Upgrade para o AEM 6.4 Forms
description: 'Você pode fazer uma atualização direta do AEM 6.1 Forms, AEM 6.2 Forms e do LiveCycle ES4 SP1 para AEM 6.3 Forms. '
seo-description: 'Você pode fazer uma atualização direta do AEM 6.1 Forms, AEM 6.2 Forms e do LiveCycle ES4 SP1 para AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 3%

---


# Atualize para o AEM 6.4 Forms no OSGi {#upgrade-to-aem-forms-osgi}

Use um dos seguintes caminhos de atualização, conforme apropriado para o seu ambiente.

## AEM 6.2 Forms ou AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Você pode fazer uma atualização direta do AEM 6.2 Forms ou AEM 6.3 Forms para o AEM 6.4 Forms. Faça o seguinte:

1. Atualize a instância AEM existente para AEM 6.4. As etapas estão listadas abaixo:

   1. Instale o service pack e os patches mais recentes para AEM 6.2 Forms ou AEM 6.3 Forms. Para obter detalhes, consulte:

      * [Notas de versão do AEM 6.2](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
      * [Notas de versão do AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [Hub de AEM](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html)
   1. Prepare a instância de origem para a atualização. Para obter etapas detalhadas, consulte [Atualização para AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Baixe o [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Somente instalações baseadas em Unix/Linux)** Se você estiver usando UNIX ou Linux como o sistema operacional subjacente, abra a janela do terminal, navegue até a pasta que contém crx-quickstart e execute o seguinte comando:

      `chmod -R 755 ../crx-quickstart`

   1. Atualize sua instância AEM para AEM 6.3. Para obter instruções passo a passo, consulte [Atualização para AEM 6.4](/help/sites-deploying/upgrade.md).

      Antes de continuar com as próximas etapas, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Depois que o servidor estiver funcionando, alguns pacotes da AEM Forms permanecerão no estado de instalação. O número de pacotes pode variar para cada instalação. É possível ignorar com segurança o estado desses pacotes. Os pacotes estão listados em `https://[server]:[port]/system/console/`.


1. Instale o pacote suplementar do AEM Forms. As etapas estão listadas abaixo:

   1. Distribuição [de](https://experience.adobe.com/downloads)software aberta. Você precisa de uma Adobe ID para fazer logon na Software Distribution (Distribuição de software).
   1. Toque em **[!UICONTROL Adobe Experience Manager]** disponível no menu de cabeçalho.
   1. Na seção **[!UICONTROL Filtros]** :
      1. Selecione **[!UICONTROL Forms]** na lista suspensa **[!UICONTROL Solução]** .
      1. Selecione a versão e o tipo do pacote. Você também pode usar a opção **[!UICONTROL Pesquisar downloads]** para filtrar os resultados.
   1. Toque no nome do pacote aplicável ao seu sistema operacional, selecione **[!UICONTROL Aceitar termos]** do EULA e toque em **[!UICONTROL Download]**.
   1. Abra o Gerenciador [de](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) pacotes e clique em **[!UICONTROL Carregar pacote]** para fazer upload do pacote.
   1. Select the package and click **[!UICONTROL Install]**.

      Você também pode baixar o pacote usando o link direto listado no artigo de versões [do](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) AEM Forms.

      >[!NOTE]
      >
      >Depois que o pacote for instalado, você será solicitado a reiniciar a instância AEM. **Não interrompa imediatamente o servidor.** Antes de parar o servidor AEM Forms, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo &lt;crx-repository>/error.log e o log esteja estável. Observe também que alguns pacotes podem permanecer no estado instalado. É possível ignorar com segurança o estado desses pacotes.

   1. Pare a instância AEM e exclua os seguintes arquivos:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Start da instância AEM.


1. Execute atividades pós-instalação.

   * **Executar utilitário de migração**

      O utilitário de migração torna os formulários adaptáveis e os ativos de gerenciamento de correspondência das versões anteriores compatíveis com os formulários AEM 6.4. Você pode fazer o download do utilitário AEM Distribuição de software. Para obter informações detalhadas sobre como configurar e usar o utilitário de migração, consulte o utilitário [de](/help/forms/using/migration-utility.md)migração.

      Se você estiver usando o [Exemplo para integrar o componente](integrate-draft-submission-database.md) de rascunhos e envios ao banco de dados e atualizar de uma versão anterior, execute os seguintes query SQL após executar a atualização:

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

   * **(Se estiver atualizando do AEM 6.2 Forms ou versões anteriores apenas) Reconfigure o Adobe Sign**

      Se você tiver o Adobe Sign configurado na versão anterior do AEM Forms, reconfigure o Adobe Sign dos serviços da AEM Cloud. Para obter mais detalhes, consulte [Integrar o Adobe Sign ao AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Se estiver atualizando do AEM 6.2 Forms ou versões anteriores apenas) Reconfigure análises e relatórios**

      No AEM 6.4 Forms, a variável de tráfego para o evento de origem e sucesso para impressão não está disponível. Portanto, ao atualizar do AEM 6.2 Forms ou versões anteriores, a AEM Forms deixa de enviar dados para o servidor Adobe Analytics e os relatórios de análise para formulários adaptáveis não estão disponíveis. Além disso, a AEM 6.4 Forms apresenta uma variável de tráfego para a versão de análise de formulário e evento bem-sucedido pelo tempo gasto em um campo. Portanto, reconfigure as análises e os relatórios do seu ambiente AEM Forms. Para obter etapas detalhadas, consulte [Configuração de análises e relatórios](/help/forms/using/configure-analytics-forms-documents.md).

1. Verifique se o servidor foi atualizado com êxito, se todos os dados também foram migrados com êxito e se podem funcionar normalmente.

   * **Verifique o status dos pacotes:** Verifique se todos os pacotes estão no estado ativo.
   * **Verificar replicação e replicação reversa:** Publique, preencha e envie alguns formulários migrados. Verifique também os dados enviados.
   * **Verifique o acesso às interfaces de usuário do administrador e do desenvolvedor:** Faça logon AEM instância de uma conta de administrador e verifique se você tem acesso aos seguintes URLs:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para os formulários AEM 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa dos caminhos alterados, consulte Reestruturação do repositório [Forms no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms e AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

O caminho de atualização direta do **AEM 6.0 Forms** e **AEM 6.1 Forms** para AEM 6.4 Forms não está disponível. Faça uma [atualização intermediária para AEM Forms](/help/forms/using/upgrade.md) 6.2 ou [atualize para AEM Forms](/help/forms/using/upgrade.md) 6.3 e faça a atualização de AEM 6.2 Forms ou AEM 6.3 Forms para AEM 6.4 Forms.
