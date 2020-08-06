---
title: 'Autenticação Adobe IMS e suporte Admin Console para AEM Managed Services '
seo-title: 'Autenticação Adobe IMS e suporte Admin Console para AEM Managed Services '
description: Saiba como usar o Admin Console no AEM.
seo-description: Saiba como usar o Admin Console no AEM.
uuid: 3f5b32c7-cf62-41a4-be34-3f71bbf224eb
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: f6112dea-a1eb-4fd6-84fb-f098476deab7
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 16%

---


# Autenticação Adobe IMS e suporte Admin Console para AEM Managed Services {#adobe-ims-authentication-and-admin-console-support-for-aem-managed-services}

>[!NOTE]
>
>Observe que esse recurso está disponível somente para clientes do Adobe Managed Services.

## Introdução {#introduction}

O AEM 6.4.3.0 apresenta suporte a Admin Console para instâncias AEM e autenticação baseada no Adobe IMS (Identity Management System) para **AEM clientes Managed Services** .

AEM a integração com o Admin Console permitirá que AEM clientes Managed Services gerenciem todos os usuários do Experience Cloud em um único console. Usuários e grupos podem ser atribuídos a perfis de produtos associados a instâncias AEM, permitindo que eles façam logon em uma instância específica.

## Destaques principais {#key-highlights}

* O suporte à autenticação AEM IMS é somente para autores, administradores ou desenvolvedores do AEM, e não para usuários finais externos de visitantes do site como  do site do cliente
* O Admin Console representará AEM clientes Managed Services como Organizações IMS e suas Instâncias como Contextos de produtos. Os administradores de sistemas e produtos do cliente poderão gerenciar o acesso às instâncias
* AEM Managed Services sincronizará as topologias do cliente com o Admin Console. Haverá uma instância AEM Contexto de produto Managed Services por instância no Admin Console.
* Os Perfis de produtos no Admin Console determinarão quais instâncias um usuário pode acessar
* A autenticação federada usando provedores de identidade compatíveis com SAML 2 dos próprios clientes é suportada
* Somente Enterprise ID ou Federated ID(para logon único do cliente) serão suportadas, não as IDs de Adobe pessoais.
* O gerenciamento de usuários (no Adobe Admin Console) continuará sendo de propriedade dos administradores do cliente.

## Arquitetura {#architecture}

A Autenticação IMS funciona usando o protocolo OAuth entre o AEM e o terminal Adobe IMS. Depois que um usuário é adicionado ao IMS e tem uma Adobe Identity, ele pode fazer logon nas instâncias do AEM Managed Services usando as credenciais do IMS.

O fluxo de logon do usuário é mostrado abaixo, o usuário será redirecionado para o IMS e, opcionalmente, para o IDP do cliente para validação SSO e, em seguida, redirecionado para o AEM.

![image2018-9-23_23-55-8](assets/image2018-9-23_23-55-8.png)

## How To Set Up {#how-to-set-up}

### Integração de organizações ao Admin Console {#onboarding-organizations-to-admin-console}

O cliente que se conecta ao Admin Console é um pré-requisito para usar o Adobe IMS para autenticação AEM.

Como primeira etapa, os clientes devem ter uma Organização provisionada no Adobe IMS. Os clientes Adobe Enterprise são representados como Organizações IMS na [Adobe Admin Console](https://helpx.adobe.com/br/enterprise/using/admin-console.html).

AEM clientes da Managed Services já devem ter uma organização provisionada e, como parte do provisionamento do IMS, as instâncias do cliente serão disponibilizadas na Admin Console para gerenciar direitos de usuário e acesso.

A mudança para o IMS para autenticação do usuário será um esforço conjunto entre o AMS e os clientes, cada um com suas workflows de conclusão.

Quando um cliente existe como uma Organização IMS e o AMS é feito com o provisionamento do cliente para o IMS, este é o resumo dos workflows de configuração necessários:

![image2018-9-23_23-33-25](assets/image2018-9-23_23-33-25.png)

1. O administrador do sistema designado recebe um convite para fazer logon no Admin Console
1. O administrador do sistema reclama o domínio para confirmar a propriedade do domínio (neste exemplo, acme.com)
1. O administrador do sistema configura os diretórios do usuário
1. O administrador do sistema configura o provedor de identidade (IDP) no Admin Console para configuração SSO.
1. O administrador do AEM gerencia os grupos, permissões e privilégios locais, como de costume. Consulte Sincronização de usuários e grupos

>[!NOTE]
>
>Para obter mais informações sobre as noções básicas sobre o Adobe Identity Management, incluindo a configuração do IDP, consulte o artigo [nesta página.](https://helpx.adobe.com/br/enterprise/using/set-up-identity.html)
>
>Para obter mais informações sobre a Administração corporativa e o Admin Console, consulte o artigo [nesta página](https://helpx.adobe.com/br/enterprise/managing/user-guide.html).

### Usuários integrados ao Admin Console {#onboarding-users-to-the-admin-console}

Existem três maneiras de os usuários integrados dependerem do tamanho do cliente e de suas preferências:

1. Criar manualmente usuários e grupos no Admin Console
1. Carregar um arquivo CSV com usuários
1. Sincronizar usuários e grupos do Ative Diretory corporativo do cliente.

#### Adição manual por meio da interface do usuário do Admin Console {#manual-addition-through-admin-console-ui}

Usuários e grupos podem ser criados manualmente na interface do usuário do Admin Console. Esse método pode ser usado se não tiver um grande número de usuários para gerenciar. Por exemplo, um número de usuários com menos de 50 AEM.

Os usuários também podem ser criados manualmente se o cliente já estiver usando esse método para administrar outros produtos do Adobe, como aplicativos do Analytics, do Público alvo ou do Creative Cloud.

![image2018-9-23_20-39-9](assets/image2018-9-23_20-39-9.png)

#### File Upload in the Admin Console UI {#file-upload-in-the-admin-console-ui}

Para facilitar a manipulação da criação do usuário, um arquivo CSV pode ser carregado para adicionar usuários em massa:

![image2018-9-23_18-59-57](assets/image2018-9-23_18-59-57.png)

#### Ferramenta de sincronização de usuários {#user-sync-tool}

A User Sync Tool (UST) permite que os clientes corporativos criem ou gerenciem usuários do Adobe usando o Ative Diretory ou outros serviços de diretório OpenLDAP testados. Os usuários do público alvo são administradores de identidade de TI (Enterprise Diretory e administradores de sistema) que poderão instalar e configurar a ferramenta. A ferramenta de código aberto é personalizável para que os clientes possam ter um desenvolvedor que a modifique de acordo com seus próprios requisitos específicos.

Quando a Sincronização de usuários é executada, ela obtém uma lista de usuários do Ative Diretory da organização (ou de qualquer outra fonte de dados compatível) e a compara com a lista de usuários no Admin Console. Em seguida, chama a API de gerenciamento de usuários da Adobe para que o Admin Console seja sincronizado com o diretório da organização. O fluxo de mudança é totalmente unidirecional; quaisquer edições feitas no Admin Console não são enviadas para o diretório.

A ferramenta permite que o administrador do sistema mapeie grupos de usuários no diretório do cliente com a configuração do produto e grupos de usuários no Admin Console, a nova versão UST também permite a criação dinâmica de grupos de usuários no Admin Console.

Para configurar a Sincronização de usuários, a organização precisa criar um conjunto de credenciais da mesma forma que usaria a [API de gerenciamento de usuários](https://www.adobe.io/apis/cloudplatform/usermanagement/docs/setup.html).

![image2018-9-23_13-36-56](assets/image2018-9-23_13-36-56.png)

A Sincronização do usuário é distribuída pelo repositório do Adobe Github neste local:

[https://github.com/adobe-apiplatform/user-sync.py/releases/latest](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)

Observe que uma versão de pré-lançamento 2.4RC1 está disponível com suporte à criação de grupos dinâmicos e pode ser encontrada aqui: [https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1)

Os principais recursos desta versão são a capacidade de mapear dinamicamente novos grupos LDAP para associação de usuários no Admin Console, bem como a criação dinâmica de grupos de usuários.

Mais informações sobre os novos recursos do grupo podem ser encontradas aqui:

[https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/br/user-manual/advanced_configuration.md#additional-group-options)

>[!NOTE]
>
>Para obter mais informações sobre a Ferramenta de sincronização do usuário, consulte a página [da](https://adobe-apiplatform.github.io/user-sync.py/br/)documentação.
>
>
>The User Sync Tool needs to register as an Adobe I/O client UMAPI using the procedure described [here](https://adobe-apiplatform.github.io/umapi-documentation/br/UM_Authentication.html).
>
>The Adobe I/O Console Documentation can be found [here](https://www.adobe.io/apis/cloudplatform/console.html).
>
>
>The User Management API that is used by the User Sync Tool is covered at this [location](https://www.adobe.io/apis/cloudplatform/umapi-new.html).

>[!NOTE]
>
>A configuração AEM IMS será gerenciada pela equipe de Serviços gerenciados da Adobe. No entanto, o administrador do cliente pode modificá-lo de acordo com seus requisitos (por exemplo, Associação de grupo automático ou Mapeamento de grupo). O cliente IMS também será registrado pela sua equipe Managed Services.

## Como usar {#how-to-use}

### Gerenciamento de produtos e acesso do usuário no Admin Console {#managing-products-and-user-access-in-admin-console}

Quando o Administrador de produto do cliente fizer logon no Admin Console, verá várias instâncias do Contexto de produto da Managed Services AEM, como mostrado abaixo:

![screen_shot_2018-09-17at105804pm](assets/screen_shot_2018-09-17at105804pm.png)

In this example, the org *AEM-MS-Onboard* has 32 instances spanning different topologies and environments like Stage, Prod, etc.

![screen_shot_2018-09-17at105517pm](assets/screen_shot_2018-09-17at105517pm.png)

Os detalhes da instância podem ser verificados para identificar a instância:

![screen_shot_2018-09-17at105601pm](assets/screen_shot_2018-09-17at105601pm.png)

Em cada instância do Contexto do produto, haverá um Perfil do Produto associado. Este perfil de produto é usado para atribuir acesso a usuários e grupos.

![image2018-9-18_7-48-50](assets/image2018-9-18_7-48-50.png)

Todos os usuários e grupos adicionados sob este perfil de produto poderão fazer logon nessa instância, como mostra o exemplo abaixo:

![screen_shot_2018-09-17at105623pm](assets/screen_shot_2018-09-17at105623pm.png)

### Efetuar login no AEM {#logging-into-aem}

#### Logon de administrador local {#local-admin-login}

AEM pode continuar a suportar logons locais para usuários administradores, já que a tela de logon tem uma opção para fazer logon localmente:

![screen_shot_2018-09-18at121056am](assets/screen_shot_2018-09-18at121056am.png)

#### Logon baseado no IMS {#ims-based-login}

Para outros usuários, o logon baseado no IMS pode ser usado assim que o IMS for configurado na instância. The user will first click on the **Sign in with Adobe** button as shown below:

![image2018-9-18_0-10-32](assets/image2018-9-18_0-10-32.png)

Eles serão redirecionados para a tela de login do IMS e inserirão suas credenciais:

![screen_shot_2018-09-17at115629pm](assets/screen_shot_2018-09-17at115629pm.png)

Se um IDP federado for configurado durante a instalação inicial do Admin Console, o usuário será redirecionado ao IDP do cliente para SSO.

O IDP é Okta no exemplo abaixo:

![screen_shot_2018-09-17at115734pm](assets/screen_shot_2018-09-17at115734pm.png)

Após a conclusão da autenticação, o usuário será redirecionado de volta para o AEM e conectado:

![screen_shot_2018-09-18at120124am](assets/screen_shot_2018-09-18at120124am.png)

### Migração de usuários existentes {#migrating-existing-users}

Para instâncias AEM existentes que estejam usando outro método de autenticação e que agora estejam sendo migradas para o IMS, é necessário uma etapa de migração.

Os usuários existentes no repositório AEM (originados localmente, via LDAP ou SAML) podem ser migrados para o IMS como o IDP usando o Utilitário de migração do usuário.

Este utilitário será executado pela equipe do AMS como parte do provisionamento de IMS.

### Gerenciando permissões e ACLs em AEM {#managing-permissions-and-acls-in-aem}

O Controle de acesso e as permissões continuarão a ser gerenciados no AEM, isso pode ser feito usando a separação dos Grupos de usuários provenientes do IMS (por exemplo, AEM-GRP-008 no exemplo abaixo) e dos grupos locais onde as permissões e o controle de acesso são definidos. Os grupos de usuários sincronizados do IMS podem ser atribuídos a grupos locais e herdar as permissões.

No exemplo abaixo, adicionamos grupos sincronizados ao grupo local *Dam_Users*, como exemplo.

Aqui, um usuário também foi atribuído a alguns grupos no Admin Console. (Observe que os usuários e grupos podem ser sincronizados do LDAP usando a ferramenta de sincronização do usuário ou criados localmente, consulte a seção Usuários **integrados na Admin Console** acima).

&amp;ast;Observe que grupos de usuários só são sincronizados quando os usuários fazem logon na instância, para clientes que têm um grande número de usuários e grupos, um utilitário de sincronização de grupo pode ser executado pelo AMS para obter previamente grupos para o gerenciamento de controles de acesso e permissões descrito acima.

![screen_shot_2018-09-17at94207pm](assets/screen_shot_2018-09-17at94207pm.png)

O usuário faz parte dos seguintes Grupos no IMS:

![screen_shot_2018-09-17at94237pm](assets/screen_shot_2018-09-17at94237pm.png)

Quando o usuário faz logon, as Associações de grupo são sincronizadas, como mostrado abaixo:

![screen_shot_2018-09-17at94033pm](assets/screen_shot_2018-09-17at94033pm.png)

Em AEM, os grupos de usuários sincronizados do IMS podem ser adicionados como membros a grupos locais existentes, por exemplo, Usuários do DAM.

![screen_shot_2018-09-17at95804pm](assets/screen_shot_2018-09-17at95804pm.png)

Como mostrado abaixo, o grupo *AEM-GRP_008* herda as Permissões e privilégios de usuários DAM. Essa é uma maneira eficaz de gerenciar permissões para grupos sincronizados e também é comumente usada em métodos de autenticação baseados em LDAP.

![screen_shot_2018-09-17at110505pm](assets/screen_shot_2018-09-17at110505pm.png)

