---
title: Reestruturação do repositório Forms no AEM 6.4
seo-title: Forms Repository Restructuring in AEM 6.4
description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para Forms.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 8%

---

# Reestruturação do repositório Forms no AEM 6.4{#forms-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Conforme descrito no pai [Reestruturação do repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md) , os clientes que atualizam para o AEM 6.4 devem usar esta página para avaliar o esforço de trabalho associado às alterações do repositório que afetam a solução da AEM Forms. Algumas alterações exigem esforço de trabalho durante o processo de atualização do AEM 6.4, enquanto outras podem ser adiadas até uma atualização do 6.5.

**Com a atualização 6.4**

* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Antes da atualização do 6.5**

* [Configuração do Echosign Cloud Service](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configurações de Cloud Service Recaptcha](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configurações do Cloud Service do Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Com a atualização 6.4 {#with-upgrade}

### Misc {#misc}

| **Localização anterior** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Novas localizações** | `/libs/fd/fp/components` |
| **Orientação relativa à reestruturação** | Quaisquer referências explícitas no código personalizado ao local Herdado devem ser atualizadas para o Novo local. |
| **Notas** | Essas bibliotecas de clientes não devem ser modificadas ou estendidas. |

| **Localização anterior** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Novas localizações** | `/libs/fd/rte` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novas localizações** | `/libs/fd/af/authoring/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Novas localizações** | `/libs/fd/xfaforms/clientlibs/` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novas localizações** | `/libs/fd/af/runtime/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Novas localizações** | `/libs/fd/af/runtime/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Novas localizações** | `/libs/fd/expeditor/clientlibs` |
| **Orientação relativa à reestruturação** | Para os recursos nas bibliotecas de clientes que podem ser referenciados por caminhos absolutos, é necessário usar caminhos mais recentes em novos ativos. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Novas localizações** | `/libs/fd/fmaddon` |
| **Orientação relativa à reestruturação** | A alteração dessas clientlibs nunca foi recomendada ou suportada. Se as modificações tiverem sido feitas nessas clientlibs, elas deverão ser revertidas para usar o código fornecido pelo AEM. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/aep` |
|---|---|
| **Novas localizações** | `/var/fd/content/annotations` |
| **Orientação relativa à reestruturação** | A alteração dessas clientlibs nunca foi recomendada ou suportada. Se as modificações tiverem sido feitas nessas clientlibs, elas deverão ser revertidas para usar o código fornecido pelo AEM. |
| **Notas** | N/A |

## Antes da atualização do 6.5 {#prior-to-upgrade}

### Configuração do Echosign Cloud Service {#echosign-cloud-service-configuration}

| **Localização anterior** | `/etc/cloudservices/echosign` |
|---|---|
| **Novas localizações** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Orientação relativa à reestruturação** | O [Migração de conteúdo ocioso](/help/sites-deploying/lazy-content-migration.md) para ser acionado na interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Configurações de Cloud Service Recaptcha {#recaptcha-cloud-service-configurations}

| **Localização anterior** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Novas localizações** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Orientação relativa à reestruturação** | O [Migração de conteúdo ocioso](/help/sites-deploying/lazy-content-migration.md) para ser acionado na interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Configurações do Cloud Service do Typekit {#typekit-cloud-service-configurations}

| **Localização anterior** | `/etc/cloudservices/typekit` |
|---|---|
| **Novas localizações** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Orientação relativa à reestruturação** | O [Migração de conteúdo ocioso](/help/sites-deploying/lazy-content-migration.md) para ser acionado na interface do usuário de migração do Forms. |
| **Notas** | N/A |

### Misc {#misc-1}

| **Localização anterior** | `/etc/cloudservices/fdm` |
|---|---|
| **Novas localizações** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Orientação relativa à reestruturação** | O [Migração de conteúdo ocioso](/help/sites-deploying/lazy-content-migration.md) para ser acionado na interface do usuário de migração do Forms. |
| **Notas** | N/A |

| **Localização anterior** | `/etc/designs/fd/fp` |
|---|---|
| **Novas localizações** | `/libs/fd/fp` |
| **Orientação relativa à reestruturação** | Quaisquer referências aos modelos /etc devem eventualmente ser atualizadas para apontar para seus `/libs` Contrapartes. |
| **Notas** | N/A |
