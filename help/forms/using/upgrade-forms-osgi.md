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
source-git-commit: d2657bc364b7a814fac9228afdec60f96faaf175

---


# Atualizar para o AEM 6.4 Forms no OSGi {#upgrade-to-aem-forms-osgi}

Use um dos seguintes caminhos de atualização, conforme apropriado para seu ambiente.

## Formulários AEM 6.2 ou AEM 6.3 > Formulários AEM 6.4 {#upgrade-aem-forms-62-63-to-64}

É possível fazer uma atualização direta do AEM 6.2 Forms ou AEM 6.3 Forms para AEM 6.4 Forms. Faça o seguinte:

1. Atualize a instância do AEM existente para o AEM 6.4. As etapas estão listadas abaixo:

   1. Instale o service pack e os patches mais recentes para o AEM 6.2 Forms ou AEM 6.3 Forms. Para obter detalhes, consulte:

      * [Notas de versão do AEM 6.2](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
      * [Notas de versão do AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
      * [Hub de sustentabilidade do AEM](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)
   1. Prepare a instância de origem para a atualização. Para obter etapas detalhadas, consulte [Atualização para o AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Baixe o QuickStart [do](/help/sites-deploying/deploy.md#getting%20the%20software)AEM 6.4.
   1. **(Somente instalações baseadas em Unix/Linux)** Se você estiver usando UNIX ou Linux como o sistema operacional subjacente, abra a janela do terminal, navegue até a pasta que contém crx-quickstart e execute o seguinte comando:

      `chmod -R 755 ../crx-quickstart`

   1. Atualize sua instância do AEM para o AEM 6.3. Para obter instruções passo a passo, consulte [Atualização para o AEM 6.4](/help/sites-deploying/upgrade.md).

      Antes de continuar com as próximas etapas, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Depois que o servidor estiver funcionando, alguns pacotes do AEM Forms permanecem no estado de instalação. O número de pacotes pode variar para cada instalação. É possível ignorar com segurança o estado desses pacotes. Os pacotes estão listados em `https://[server]:[port]/system/console/`.


1. Instale o pacote complementar do AEM Forms.  As etapas estão listadas abaixo:

   1. Faça logon no servidor AEM como administrador e abra o compartilhamento de pacote. O URL padrão do compartilhamento de pacote é `https://[server]:[port]/crx/packageshare`.
   1. No compartilhamento de pacotes, pesquise nos pacotes **[!UICONTROL complementares do]** AEM 6.4 Forms, clique no pacote aplicável ao seu sistema operacional e clique em **[!UICONTROL Download]**. Leia e aceite o contrato de licença e clique em **[!UICONTROL OK]**. O download é iniciado. Após o download, a palavra **[!UICONTROL Download]** é exibida ao lado do pacote.

      Como alternativa, você também pode usar os hiperlinks listados nas versões [do](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) AEM Forms para baixar manualmente um pacote.

   1. Depois que o download for concluído, clique em **[!UICONTROL Download]**. Você é redirecionado para o gerenciador de pacotes. No gerenciador de pacotes, pesquise o pacote baixado e clique em **[!UICONTROL Instalar]**.

      Se você baixar manualmente o pacote usando o link direto listado nas versões [do](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)AEM Forms, abra o Gerenciador de pacote AEM, clique em **[!UICONTROL Carregar pacote]**, selecione o pacote baixado e clique em Fazer upload. Depois que o pacote for carregado, clique no nome do pacote e clique em **[!UICONTROL Instalar]**.

      >[!NOTE]
      >
      >Depois que o pacote for instalado, você será solicitado a reiniciar a instância do AEM. **Não interrompa imediatamente o servidor.** Antes de parar o servidor de formulários AEM, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo &lt;crx-repository>/error.log e o log esteja estável. Observe também que alguns pacotes podem permanecer no estado instalado. É possível ignorar com segurança o estado desses pacotes.

   1. Pare a instância do AEM e exclua os seguintes arquivos:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Inicie a instância do AEM.


1. Execute atividades pós-instalação.

   * **Executar utilitário de migração**

      O utilitário de migração torna os formulários adaptáveis e os ativos de gerenciamento de correspondência das versões anteriores compatíveis com os formulários AEM 6.4. Você pode baixar o utilitário do compartilhamento de pacote do AEM. Para obter informações detalhadas sobre como configurar e usar o utilitário de migração, consulte o utilitário [de](/help/forms/using/migration-utility.md)migração.

      Se você estiver usando o [Exemplo para integrar o componente](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) de rascunhos e envios ao banco de dados e atualizar de uma versão anterior, execute as seguintes consultas SQL após executar a atualização:

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

   * **(Se estiver atualizando do AEM 6.2 Forms ou somente versões anteriores) Reconfigure o Adobe Sign**

      Se você tiver o Adobe Sign configurado na versão anterior do AEM Forms, reconfigure o Adobe Sign nos serviços da AEM Cloud. Para obter mais detalhes, consulte [Integrar o Adobe Sign a formulários](/help/forms/using/adobe-sign-integration-adaptive-forms.md)AEM.

   * **(Se estiver atualizando do AEM 6.2 Forms ou somente versões anteriores) Reconfigurar análises e relatórios**

      No AEM 6.4 Forms, a variável de tráfego para eventos de origem e sucesso para impressão não está disponível. Portanto, ao atualizar do AEM 6.2 Forms ou de versões anteriores, o AEM Forms interrompe o envio de dados para o servidor do Adobe Analytics e os relatórios de análise para formulários adaptáveis não estão disponíveis. Além disso, o AEM 6.4 Forms apresenta uma variável de tráfego para a versão de análise de formulário e evento bem-sucedido pelo tempo gasto em um campo. Portanto, reconfigure as análises e os relatórios para seu ambiente do AEM Forms. Para obter etapas detalhadas, consulte [Configuração de análises e relatórios](/help/forms/using/configure-analytics-forms-documents.md).

1. Verifique se o servidor foi atualizado com êxito, se todos os dados também foram migrados com êxito e se podem funcionar normalmente.

   * **** Verifique o status dos pacotes: Verifique se todos os pacotes estão no estado ativo.
   * **** Verificar replicação e replicação reversa: Publique, preencha e envie alguns formulários migrados. Verifique também os dados enviados.
   * **** Verifique o acesso às interfaces de usuário do administrador e desenvolvedor: Faça logon na instância do AEM a partir de uma conta de administrador e verifique se você tem acesso aos seguintes URLs:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Depois de atualizar para formulários do AEM 6.4, use os caminhos alterados para personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte Reestruturação do repositório de [formulários no AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## Formulários do AEM 6.0 e AEM 6.1 > Formulários do AEM 6.4 {#upgrade-aem-forms-60-61-to-64}

O caminho de atualização direta do **AEM 6.0 Forms** e do **AEM 6.1 Forms** para AEM 6.4 Forms não está disponível. Faça uma [atualização intermediária para o AEM 6.2 Forms](/help/forms/using/upgrade.md) ou [atualize para o AEM 6.3 Forms](/help/forms/using/upgrade.md) e atualize do AEM 6.2 Forms ou AEM 6.3 Forms para o AEM 6.4 Forms.
