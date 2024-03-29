---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guia de implementação do AEM 6.4
breadcrumb-title: Guia de implementação
user-guide-description: Saiba mais sobre a instalação, implantação e arquitetura do Adobe Experience Manager 6.4, incluindo a implantação do Adobe Managed Services na nuvem.
feature: Deploying
role: Architect
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 13%

---


# Guia do usuário de implantação do AEM 6.4 {#deploying}

+ [Guia de implantação do usuário](home.md)
+ Introdução à plataforma de AEM {#introduction}
   + [Introdução à plataforma de AEM](platform.md)
   + [Requisitos técnicos](technical-requirements.md)
   + [Elementos de armazenamento no AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM com MongoDB](aem-with-mongodb.md)
+ Implantação de AEM {#deploying}
   + [Implantação e manutenção](deploy.md)
   + [Implantações recomendadas](recommended-deploys.md)
   + [Instalação do servidor de aplicativos](application-server-install.md)
   + [Instalação independente personalizada](custom-standalone-install.md)
   + [Início e interrupção da linha de comando](command-line-start-and-stop.md)
   + [Configuração de armazenamentos de nó e armazenamentos de dados no AEM 6](data-store-config.md)
   + [Limpeza de revisão](revision-cleanup.md)
   + [Como executar AEM com o TarMK Cold Standby](tarmk-cold-standby.md)
   + [Suporte RDBMS no AEM 6.4](rdbms-support-in-aem.md)
   + [Consultas e indexação do Oak](queries-and-indexing.md)
   + [Indexação via Jar Oak-run](indexing-via-the-oak-run-jar.md)
   + [Casos de uso da indexação Oak-run.jar](oak-run-indexing-usecases.md)
   + [Solução de problemas de índices do Oak](troubleshooting-oak-indexes.md)
   + [Aceitação Em Coleta De Estatísticas De Uso Agregado](opt-in-aggregated-usage-statistics.md)
   + [Resolução de problemas](troubleshooting.md)
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
   + [Limpeza de versão](version-purging.md)
   + [Monitorar e manter sua instância do AEM](monitoring-and-maintaining.md)
   + [Descarregamento de Tarefas](offloading.md)
   + [Logon único](single-sign-on.md)
   + [Mapeamento de recursos](resource-mapping.md)
   + [Habilitar HTTP por SSL](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/ssl-by-default.html)
   + [Verificações de consistência e passagem](consistency-check.md)
   + [Diretrizes de desempenho](performance-guidelines.md)
   + [Otimização de desempenho](configuring-performance.md)
   + [Guia de desempenho de ativos](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html)
   + [Artigos explicativos de configuração](ht-deploy.md)
   + [Remover os sites do Geometrixx](removing-the-geometrixx-sites.md)
   + [Configuração do Console da Web](configuring-web-console.md)
+ Atualização para o AEM 6.4 {#upgrading}
   + [Atualização para o AEM 6.4](upgrade.md)
   + [Planejamento da atualização](upgrade-planning.md)
   + [Avaliação da complexidade da atualização com o Detector de padrões](pattern-detector.md)
   + [Compatibilidade com versões anteriores no AEM 6.4](backward-compatibility.md)
   + [Procedimento de atualização](upgrade-procedure.md)
   + [Usar a reindexação offline para reduzir o tempo de inatividade durante uma atualização](upgrade-offline-reindexing.md)
   + [Execução de uma atualização no local](in-place-upgrade.md)
   + [Migração de conteúdo ocioso](lazy-content-migration.md)
   + [Uso da ferramenta de migração CRX2Oak](using-crx2oak.md)
   + [Tarefas de manutenção de pré-atualização](pre-upgrade-maintenance-tasks.md)
   + [Verificação e solução de problemas da pós-atualização](post-upgrade-checks-and-troubleshooting.md)
   + [Atualizar o Forms de pesquisa personalizada](upgrading-custom-search-forms.md)
   + [Atualizações sustentáveis](sustainable-upgrades.md)
   + [Atualização de código e personalizações](upgrading-code-and-customizations.md)
   + [Etapas de atualização para instalações do servidor de aplicativos](app-server-upgrade.md)
   + [Lista de pacotes obsoletos desinstalados após a atualização](obsolete-bundles.md)
+ Reestruturação do repositório {#restructuring}
   + [Reestruturação do repositório no AEM 6.4](repository-restructuring.md)
   + [Reestruturação comum de repositório no AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Restruturação do repositório de sites no AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório de ativos no AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=pt-BR)
   + [Reestruturação do repositório Dynamic Media no AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório Forms no AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório de comércio eletrônico no AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Reestruturação do repositório para AEM Communities no 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ eCommerce {#ecommerce}
   + [Visão geral do eCommerce](ecommerce.md)
   + [Commerce Cloud SAP](sap-commerce-cloud.md)
   + [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Práticas recomendadas     {#practices}
   + [Práticas recomendadas de implantação](best-practices.md)
   + [Árvore de desempenho](performance-tree.md)
   + [Práticas recomendadas para testes de desempenho](best-practices-for-performance-testing.md)
   + [Práticas recomendadas para consultas e indexação](best-practices-for-queries-and-indexing.md)
   + [Recommendations da interface do usuário para clientes](ui-recommendations.md)
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
