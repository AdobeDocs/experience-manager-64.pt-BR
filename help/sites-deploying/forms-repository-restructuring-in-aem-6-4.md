---
title: Reestruturação do repositório de formulários no AEM 6.4
seo-title: Reestruturação do repositório de formulários no AEM 6.4
description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para o Forms.
seo-description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para o Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42

---


# Reestruturação do repositório de formulários no AEM 6.4{#forms-repository-restructuring-in-aem}

Conforme descrito na página principal [Reestruturação do repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md) , os clientes que atualizam para o AEM 6.4 devem usar esta página para avaliar o esforço de trabalho associado às alterações no repositório que afetam a solução AEM Forms. Algumas alterações exigem esforço de trabalho durante o processo de atualização do AEM 6.4, enquanto outras podem ser adiadas até uma atualização do AEM 6.5.

**Com atualização 6.4**

* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Antes da atualização do 6.5**

* [Configuração do serviço da Echosign Cloud](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configurações do serviço Recaptcha Cloud](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configurações do serviço em nuvem Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Com atualização 6.4 {#with-upgrade}

### Misc {#misc}

| **Localização anterior** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Novos locais** | `/libs/fd/fp/components` |
| **Orientação relativa à reestruturação** | Quaisquer referências explícitas no código personalizado ao local Herdado devem ser atualizadas para o novo local. |
| **Notas** | Essas bibliotecas de cliente não devem ser modificadas ou estendidas. |

| **Localização anterior** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Novos locais** | `/libs/fd/rte` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novos locais** | `/libs/fd/af/authoring/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Novos locais** | `/libs/fd/xfaforms/clientlibs/` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novos locais** | `/libs/fd/af/runtime/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novos locais** | `/libs/fd/af/runtime/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Novos locais** | `/libs/fd/expeditor/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas do cliente que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em ativos frescos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Novos locais** | `/libs/fd/fmaddon` |
| **Orientação relativa à reestruturação** | A alteração dessas clientlibs nunca foi recomendada ou suportada. Se modificações tiverem sido feitas nesses clientlibs, elas devem ser revertidas para usar o código fornecido pelo AEM. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/aep` |
|---|---|
| **Novos locais** | `/var/fd/content/annotations` |
| **Orientação relativa à reestruturação** | A alteração dessas clientlibs nunca foi recomendada ou suportada. Se modificações tiverem sido feitas nesses clientlibs, elas devem ser revertidas para usar o código fornecido pelo AEM. |
| **Notas** | N/A |

## Antes da atualização do 6.5 {#prior-to-upgrade}

### Configuração do serviço da Echosign Cloud {#echosign-cloud-service-configuration}

| **Localização anterior** | `/etc/cloudservices/echosign` |
|---|---|
| **Novos locais** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Orientação relativa à reestruturação** | O utilitário de Migração [de conteúdo](/help/sites-deploying/lazy-content-migration.md) preguiçoso a ser acionado da interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Configurações do serviço Recaptcha Cloud {#recaptcha-cloud-service-configurations}

| **Localização anterior** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Novos locais** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Orientação relativa à reestruturação** | O utilitário de Migração [de conteúdo](/help/sites-deploying/lazy-content-migration.md) preguiçoso a ser acionado da interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Configurações do serviço em nuvem Typekit {#typekit-cloud-service-configurations}

| **Localização anterior** | `/etc/cloudservices/typekit` |
|---|---|
| **Novos locais** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Orientação relativa à reestruturação** | O utilitário de Migração [de conteúdo](/help/sites-deploying/lazy-content-migration.md) preguiçoso a ser acionado da interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Misc {#misc-1}

| **Localização anterior** | `/etc/cloudservices/fdm` |
|---|---|
| **Novos locais** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Orientação relativa à reestruturação** | O utilitário de Migração [de conteúdo](/help/sites-deploying/lazy-content-migration.md) preguiçoso a ser acionado da interface do usuário de migração do Forms. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/designs/fd/fp` |
|---|---|
| **Novos locais** | `/libs/fd/fp` |
| **Orientação relativa à reestruturação** | Todas as referências aos modelos /etc devem ser atualizadas para apontar para suas `/libs` contrapartidas. |
| **Notas** | N/A |

