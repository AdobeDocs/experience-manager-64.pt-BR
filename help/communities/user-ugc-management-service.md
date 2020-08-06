---
title: Serviço de gerenciamento de usuário e UGC no AEM Communities
seo-title: Serviço de gerenciamento de usuário e UGC no AEM Communities
description: 'Use as APIs para excluir e exportar em massa o conteúdo gerado pelo usuário e desativar a conta do usuário. '
seo-description: 'Use as APIs para excluir e exportar em massa o conteúdo gerado pelo usuário e desativar a conta do usuário. '
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Serviço de gerenciamento de usuário e UGC no AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>O RGPD é utilizado como exemplo nas seções abaixo, mas os detalhes abrangidos são aplicáveis a todas as normas de proteção de dados e privacidade; como o RGPD, o CCPA, etc.

A AEM Communities expõe as APIs prontas para gerenciar perfis de usuários e o conteúdo gerado pelo usuário (UGC) em massa. Depois de habilitado, o serviço **UserUgcManagement** permite que os usuários privilegiados (administradores e moderadores da comunidade) desativem perfis de usuários e excluam ou exportem em massa o UGC para usuários específicos. Essas APIs também permitem que os controladores e processadores de dados do cliente atendam às Regras Gerais de Proteção de Dados (RGPD) da União e a outras regras de privacidade inspiradas no RGPD.

Para obter mais informações, consulte a página do [RGPD no Centro](https://www.adobe.com/privacy/general-data-protection-regulation.html)de privacidade do Adobe.

>[!NOTE]
>
>Se você configurou o [Adobe Analytics no site da AEM Communities](analytics.md) , os dados do usuário capturados são enviados para o servidor da Adobe Analytics. A Adobe Analytics fornece APIs que permitem acessar, exportar e excluir dados do usuário e estão em conformidade com o RGPD. Para obter mais informações, consulte [Enviar acesso e excluir solicitações](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Para colocar essas APIs em uso, é necessário ativar o `/services/social/ugcmanagement` endpoint ativando o serviço UserUgcManagement. Para ativar este serviço, instale o servlet [de](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) amostra disponível em [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet). Em seguida, pressione o endpoint na instância de publicação do site de suas comunidades com os parâmetros apropriados usando uma solicitação http, semelhante a:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

No entanto, você também pode criar uma interface do usuário (interface do usuário) para gerenciar perfis de usuários e conteúdo gerado pelo usuário no sistema.

Essas APIs permitem executar as seguintes funções.

## Recuperar o UGC de um usuário {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` ajuda a exportar todo o UGC de um usuário do sistema.

* **usuário**: ID autorizável de um usuário.
* **outputStream**: o resultado é retornado como fluxo de saída, que é um arquivo zip que inclui o conteúdo gerado pelo usuário (como arquivo json) e anexos (que incluem imagens ou vídeos carregados pelo usuário).

Por exemplo, para exportar o UGC de um usuário chamado Weston McCall, que usa weston.mccall@dodgit.com como ID autorizável para fazer logon no site de comunidades, você pode enviar uma solicitação de GET http semelhante a:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Excluir o UGC de um usuário {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, usuário de string)** ajuda a excluir todo o UGC de um usuário do sistema.

* **usuário**: ID autorizável do usuário.

Por exemplo, para excluir o UGC de um usuário que tenha uma ID autorizada weston.mccall@dodgit.com por meio de uma solicitação http-POST, use os seguintes parâmetros:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Excluir UGC do Adobe Analytics {#delete-ugc-from-analytics}

Para excluir os dados do usuário do Adobe Analytics, siga o fluxo de trabalho do RGPD Analytics; como a API não exclui dados do usuário da Adobe Analytics.

Para os mapeamentos de variáveis do Adobe Analytics usados pelo AEM Communities, consulte a seguinte imagem:

![Mapeamento variável de comunidades AEM para Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Desativar uma conta de usuário {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, usuário String)** ajuda a desativar uma conta de usuário.

* **usuário**: ID autorizável do usuário.

>[!NOTE]
>
>A desativação de um usuário exclui todo o conteúdo gerado pelo usuário no servidor.

Por exemplo, para excluir o perfil de um usuário que tenha uma ID autorizada weston.mccall@dodgit.com por meio de uma solicitação http-POST, use os seguintes parâmetros:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>deleteUserAccount() API só desativa um perfil de usuário no sistema e remove o UGC. No entanto, para excluir um perfil de usuário do sistema, navegue até **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), localize o nó do usuário e exclua-o.
