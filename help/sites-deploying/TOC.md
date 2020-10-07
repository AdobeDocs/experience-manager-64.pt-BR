---
cloud: experience-cloud
product: adobe experience manager
audience: end-user
user-guide-title: Guia de implantação do AEM 6.4
breadcrumb-title: Deploying Guide
user-guide-description: Learn more about installing, deploying, and the architecture of Adobe Experience Manager 6.4, including our Adobe Managed Services cloud deployment.
translation-type: tm+mt
source-git-commit: e7da0bb7906c3ad3d04531db0abfbc658646f6e4
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 11%

---


# Guia do usuário para implantação do AEM 6.4 {#deploying}

+ [Implantação do Guia do Usuário](home.md)
+ Introdução à plataforma AEM {#introduction}
   + [Introdução à plataforma AEM](platform.md)
   + [Requisitos técnicos](technical-requirements.md)
   + [Elementos do armazenamento no AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM com MongoDB](aem-with-mongodb.md)
+ Implantar AEM {#deploying}
   + [Implantação e manutenção](deploy.md)
   + [Implantações recomendadas](recommended-deploys.md)
   + [Instalação do servidor de aplicativos](application-server-install.md)
   + [Instalação independente personalizada](custom-standalone-install.md)
   + [Início e interrupção da linha de comando](command-line-start-and-stop.md)
   + [Configuração de armazenamentos de nó e armazenamentos de dados no AEM 6](data-store-config.md)
   + [Limpeza de revisão](revision-cleanup.md)
   + [Como executar AEM com o modo de espera refrigerado TarMK](tarmk-cold-standby.md)
   + [Suporte a RDBMS no AEM 6.4](rdbms-support-in-aem.md)
   + [Query Oak e indexação](queries-and-indexing.md)
   + [Indexação via Jar Oak-run](indexing-via-the-oak-run-jar.md)
   + [Casos de uso da indexação Oak-run.jar](oak-run-indexing-usecases.md)
   + [Solução de problemas de índices Oak](troubleshooting-oak-indexes.md)
   + [Optar Pela Coleta De Estatísticas De Uso Agregado](opt-in-aggregated-usage-statistics.md)
   + [Resolução de Problemas](troubleshooting.md)
+ Configuração de AEM {#configuring}
   + [Conceitos básicos de configuração](configuring.md)
   + [Logs](configure-logging.md)
   + [Configuração do OSGi](configuring-osgi.md)
   + [Configurações do OSGi](osgi-configuration-settings.md)
   + [Modos de execução](configure-runmodes.md)
   + [Console da Web](web-console.md)
   + [Replicação](replication.md)
   + [Replicação usando SSL mútuo](mssl-replication.md)
   + [Solução de problemas de replicação](troubleshoot-rep.md)
   + [Expiração de objetos estáticos](expiration-static-objects.md)
   + [Expurgação de versão](version-purging.md)
   + [Monitorando e Mantendo sua instância AEM](monitoring-and-maintaining.md)
   + [Descarregamento de tarefas](offloading.md)
   + [Logon único](single-sign-on.md)
   + [Mapeamento de recursos](resource-mapping.md)
   + [Habilitando HTTP por SSL](/help/sites-administering/ssl-by-default.md)
   + [Verificações de consistência e transversal](consistency-check.md)
   + [Diretrizes de desempenho](performance-guidelines.md)
   + [Otimização do desempenho](configuring-performance.md)
   + [Guia de desempenho de ativos](assets-performance-sizing.md)
   + [Artigos sobre procedimentos de configuração](ht-deploy.md)
   + [Remoção dos sites de Geometrixx](removing-the-geometrixx-sites.md)
   + [Configurando o Console da Web](configuring-web-console.md)
+ Upgrading to AEM 6.4 {#upgrading}
   + [Atualização para o AEM 6.4](upgrade.md)
   + [Planejamento da atualização](upgrade-planning.md)
   + [Avaliação da complexidade da atualização com o detector de padrões](pattern-detector.md)
   + [Compatibilidade com versões anteriores no AEM 6.4](backward-compatibility.md)
   + [Procedimento de atualização](upgrade-procedure.md)
   + [Uso da reindexação offline para reduzir o tempo de inatividade durante uma atualização](upgrade-offline-reindexing.md)
   + [Execução de uma atualização no local](in-place-upgrade.md)
   + [Migração de conteúdo ociosa](lazy-content-migration.md)
   + [Uso da ferramenta de migração CRX2Oak](using-crx2oak.md)
   + [Tarefas de manutenção pré-atualização](pre-upgrade-maintenance-tasks.md)
   + [Verificações e solução de problemas da pós-atualização](post-upgrade-checks-and-troubleshooting.md)
   + [Atualização do Forms de pesquisa personalizada](upgrading-custom-search-forms.md)
   + [Atualizações sustentáveis](sustainable-upgrades.md)
   + [Atualização de código e personalizações](upgrading-code-and-customizations.md)
   + [Etapas de atualização para instalações do servidor de aplicativos](app-server-upgrade.md)
   + [Lista de pacotes obsoletos desinstalados após a atualização](obsolete-bundles.md)
+ Reestruturação do repositório {#restructuring}
   + [Reestruturação dos repositórios no AEM 6.4](repository-restructuring.md)
   + [Reestruturação comum dos repositórios no AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório Sites no AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório de ativos no AEM 6.4](assets-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório de Dynamic Media no AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório Forms no AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório de comércio eletrônico no AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório para AEM Communities no 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ eCommerce {#ecommerce}
   + [Visão geral do eCommerce](ecommerce.md)
   + [COMMERCE CLOUD SAP](sap-commerce-cloud.md)
   + [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Práticas recomendadas     {#practices}
   + [Práticas recomendadas de implantação](best-practices.md)
   + [Árvore de desempenho](performance-tree.md)
   + [Práticas recomendadas para testes de desempenho](best-practices-for-performance-testing.md)
   + [Práticas recomendadas para Query e indexação](best-practices-for-queries-and-indexing.md)
   + [Interface do usuário Recommendations para clientes](ui-recommendations.md)
   + [Desempenho e escalabilidade](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->
