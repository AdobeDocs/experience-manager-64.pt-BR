---
title: Sincronização de usuários das comunidades
seo-title: Sincronização de usuários das comunidades
description: Como a sincronização de usuários funciona
seo-description: Como a sincronização de usuários funciona
uuid: 5b9bb7b6-9238-41f6-81da-84b9a303b9e2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 32b56b48-75cb-4cc9-a077-10e335f01a35
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2508'
ht-degree: 0%

---


# Sincronização de usuários das comunidades {#communities-user-synchronization}

## Introdução {#introduction}

No AEM Communities, no ambiente de publicação (dependendo das permissões configuradas), *visitantes do site* podem se tornar *membros*, criar *grupos de usuários* e editar seu *perfil de membro*.

*Os* dados do usuário são um termo usado para se referir a  *usuários*, perfis  *de usuários e grupos* de usuários **.

** Membro é um termo usado para se referir a  ** usuários registrados no ambiente de publicação, em vez de usuários registrados no ambiente de criação.

Para obter mais informações sobre os dados do usuário, visite [Gerenciar usuários e grupos de usuários](users.md).

## Sincronizando usuários em um farm de publicação {#synchronizing-users-across-a-publish-farm}

Por design, os dados do usuário criados no ambiente de publicação não aparecem no ambiente de criação.

A maioria dos dados do usuário criados no ambiente de criação tem o objetivo de permanecer no ambiente de criação e não é sincronizada nem replicada para publicar instâncias.

Quando [topology](topologies.md) é um [farm de publicação](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), o registro e as modificações feitas em uma instância de publicação precisam ser sincronizadas com outras instâncias de publicação. Os membros precisam fazer logon e ver seus dados em qualquer nó de publicação.

Quando a sincronização do usuário é ativada, os dados do usuário são sincronizados automaticamente entre as instâncias de publicação no farm.

### Instruções de configuração da sincronização de usuários {#user-sync-setup-instructions}

Para obter instruções detalhadas, passo a passo, sobre como habilitar a sincronização em um farm de publicação, consulte

* [Sincronização de usuários](../../help/sites-administering/sync.md)

## Sincronização do usuário em segundo plano {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **Pacote** VLT: é um arquivo zip de todas as alterações feitas em um editor, que precisam ser distribuídas entre editores. As alterações em um editor geram eventos que são escolhidos pelo ouvinte de eventos de alteração. Isso cria um pacote vlt que contém todas as alterações.

* **Pacote** de distribuição: contém informações de distribuição do Sling. Essas são informações sobre onde o conteúdo precisa ser distribuído e quando foi distribuído por último.

## O que acontece quando ... {#what-happens-when}

### Publicar site a partir do console Sites das Comunidades {#publish-site-from-communities-sites-console}

Na criação, quando um site da comunidade é publicado a partir do [console Sites das Comunidades](sites-console.md), o efeito é [replicar](../../help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) as páginas associadas e o Sling distribuir os grupos de usuários da comunidade criados dinamicamente, incluindo sua associação.

### O usuário é criado ou edita o perfil na publicação {#user-is-created-or-edits-profile-on-publish}

Por design, os usuários e perfis criados no ambiente de publicação (como por autoregistro, logon social, autenticação LDAP) não aparecem no ambiente do autor.

Quando a topologia é um [publish farm](topologies.md) e a sincronização do usuário foi configurada corretamente, o *user* e *user profile* são sincronizados no farm de publicação usando a distribuição do Sling.

### Novo grupo da comunidade é criado em Publicar {#new-community-group-is-created-on-publish}

Embora tenha sido iniciado a partir de uma instância de publicação, a criação do grupo da comunidade, que resulta em novas páginas do site e em um novo grupo de usuários, ocorre na instância do autor.

Como parte do processo, as novas páginas do site são replicadas para todas as instâncias de publicação. O grupo de usuários da comunidade criado dinamicamente e sua associação são Sling distribuídos para todas as instâncias de publicação.

### Usuários ou grupos de usuários são criados usando o Console de segurança {#users-or-user-groups-are-created-using-security-console}

Por design, os dados do usuário criados no ambiente de publicação não aparecem no ambiente de criação e vice-versa.

Quando o console [Administração e segurança do usuário](../../help/sites-administering/security.md) é usado para adicionar novos usuários no ambiente de publicação, a sincronização do usuário sincronizará os novos usuários e sua associação de grupo com outras instâncias de publicação, se necessário. A sincronização de usuários também sincronizará os grupos de usuários criados pelo console de segurança.

### O usuário publica conteúdo na publicação {#user-posts-content-on-publish}

Para conteúdo gerado pelo usuário (UGC), os dados inseridos em uma instância de publicação são acessados por meio do [SRP configurado](srp-config.md).

## Práticas recomendadas {#bestpractices}

Por padrão, a sincronização do usuário é **disabled**. A ativação da sincronização do usuário envolve a modificação das configurações *existentes* OSGi. Nenhuma nova configuração deve ser adicionada como resultado da ativação da sincronização do usuário.

A sincronização de usuários depende do ambiente do autor para gerenciar as distribuições de dados do usuário, mesmo que os dados do usuário não sejam criados no autor .

**Pré-requisitos**

1. Se usuários e grupos de usuários já tiverem sido criados em um editor, é recomendável sincronizar [manualmente](../../help/sites-administering/sync.md#manually-syncing-users-and-user-groups) os dados do usuário para todos os editores antes de configurar e ativar a sincronização do usuário.

   Quando a sincronização do usuário estiver ativada, somente os usuários e grupos recém-criados serão sincronizados .

1. Verifique se o código mais recente foi instalado:

   * [Atualizações da plataforma AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=pt-BR)
   * [Atualizações do AEM Communities](deploy-communities.md#latestfeaturepack)

As seguintes configurações são necessárias para habilitar a sincronização de usuários no AEM Communities. Certifique-se de que essas configurações estejam corretas para impedir que a distribuição de conteúdo do sling falhe.

### Apache Sling Distribution Agent - Sync Agents Fatory {#apache-sling-distribution-agent-sync-agents-factory}

Essa configuração busca o conteúdo a ser sincronizado entre os editores. A configuração é na instância do autor. O autor deve acompanhar todos os editores que estão lá e onde sincronizar todas as informações.

Os valores padrão na configuração são para uma única instância de publicação. Como a sincronização do usuário é útil para sincronizar várias instâncias de publicação, como para um farm de publicação, outras instâncias de publicação precisam ser adicionadas à configuração.

**Como o conteúdo é sincronizado?**

A instância de autor consulta o endpoint de exportador de editores. Sempre que um usuário é criado ou atualizado em editores específicos (n), o Autor obtém o conteúdo dos pontos de extremidade do exportador e [empurra o conteúdo](sync.md#main-pars-image-1413756164) para outros editores (n-1, ou seja, é diferente dos editores a partir dos quais o conteúdo é buscado).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar a configuração dos agentes de sincronização do Apache Sling

Na instância AEM autor:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localize **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Fatory]**.

   * Selecione a configuração existente a ser aberta para edição (ícone de lápis).
   * Verificar nome: **`socialpubsync`.**
   * Marque a caixa de seleção **[!UICONTROL Enabled]**.
   * Selecione **[!UICONTROL Usar várias filas]**.
   * Especifique **[!UICONTROL Endpoints do exportador]** e **[!UICONTROL Endpoints do importador]** (é possível adicionar mais endpoints de exportador e importador).

      Esses endpoints definem de onde você deseja obter o conteúdo e de onde deseja enviar o conteúdo. O autor busca o conteúdo do endpoint do exportador especificado e o envia para os editores (diferente do editor do qual buscou o conteúdo).
   ![sync-agent-fact](assets/sync-agent-fact.png)

### Distribuição de Adobe Granite - Provedor secreto de transporte de senha criptografado {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Ela permite que o autor identifique o usuário autorizado, como tendo permissão para sincronizar dados do usuário do autor para publicar.

O [usuário autorizado criado](../../help/sites-administering/sync.md#createauthuser) em todas as instâncias de publicação ajuda os editores a se conectarem ao autor e a configurar a distribuição do Sling no autor. Este usuário autorizado tem todas as ACLs [necessárias](../../help/sites-administering/sync.md#howtoaddacl).

Sempre que os dados devem ser instalados ou obtidos de editores, o autor se conecta com os editores usando as credenciais (nome de usuário e senha) definidas nessa configuração.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para conectar o autor com editores usando usuário autorizado

Na instância AEM autor:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md).

   Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localize **[!UICONTROL Distribuição de Adobe Granite - Provedor secreto de transporte de senha criptografado]**.
1. Selecione a configuração existente a ser aberta para edição (ícone de lápis).

   Verifique a propriedade `name:` **`socialpubsync`\- `publishUser` .**
1. Defina o nome de usuário e a senha para o [usuário autorizado](../../help/sites-administering/sync.md#createauthorizeduser).

   Por exemplo, **`usersync`\-admin**

   ![granite-pasword-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent - Fábrica de Agentes da Fila {#apache-sling-distribution-agent-queue-agents-factory}

Essa configuração é usada para configurar os dados que você deseja sincronizar entre editores. Quando os dados são criados/atualizados em caminhos especificados em **[!UICONTROL Raízes permitidas]**, &quot;var/community/distribution/diff&quot; é ativado e o replicador criado obtém os dados de um editor e os instala em outros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar os dados (caminhos de nó) para sincronizar

Em AEM instância de publicação:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize **[!UICONTROL Apache Sling Distribution Agent - Queue Agents Fatory]**.
1. Selecione a configuração existente a ser aberta para edição (ícone de lápis).

   Verificar nome: `socialpubsync` \-inverso.
1. Marque a caixa de seleção **[!UICONTROL Enabled]** e salve.
1. Especifique os caminhos de nó que devem ser replicados em **[!UICONTROL Raízes permitidas]**.
1. Repita para cada instância `publish`.

   ![queue-agents-fact](assets/queue-agents-fact.png)

### Distribuição de Adobe Granite - Fábrica de Observadores Diff {#adobe-granite-distribution-diff-observer-factory}

Essa configuração sincroniza a associação de grupo entre editores.\
Se alterar a associação de um grupo em um editor não atualizar sua associação em outros editores, verifique se **ref:Members** é adicionado a **nomes de propriedades pesquisadas**.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir a sincronização de membros

Em cada instância de publicação de AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize **[!UICONTROL Distribuição de Granito do Adobe - Fábrica de Observador Diff]**.
1. Selecione a configuração existente a ser aberta para edição (ícone de lápis).

   Verifique **[!UICONTROL nome do agente]**: `socialpubsync` \-inverso&amp;ast;&amp;ast;.
1. Marque a caixa de seleção **[!UICONTROL Enabled]**.
1. Especifique **rep`:members`** como `description` para propertyName em **[!UICONTROL nomes de propriedades pesquisadas]** e Salve.

   ![diff-obs](assets/diff-obs.png)

### Acionador de distribuição do Apache Sling - Acionadores agendados de fábrica {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Essa configuração permite que você configure o intervalo de pesquisa (após o qual os editores são colocados em ping e as alterações são obtidas pelo autor) para sincronizar as alterações nos editores.

O autor pesquisa os editores a cada 30 segundos (padrão). Se algum pacote estiver presente na pasta */var/sling/distribution/packages/ socialpubsync - vlt /shared*, ele buscará esses pacotes e os instalará em outros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para alterar o intervalo de sondagem

Na instância AEM autor:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md), por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Localize **[!UICONTROL Acionador de distribuição do Apache Sling - Acionadores agendados de fábrica]**

   * Selecione a configuração existente a ser aberta para edição (ícone de lápis)
   * Verifique `Name:` **`socialpubsync`\-scheduled-trigger**
   * Defina o Intervalo em Segundos para o intervalo desejado e salve.

   ![acionador agendado](assets/scheduled-trigger.png)

### Ouvinte de sincronização de usuários do AEM Communities {#aem-communities-user-sync-listener}

Para problemas na distribuição do Sling em que há uma discrepância nas assinaturas e seguintes, verifique se as seguintes propriedades nas configurações **[!UICONTROL AEM Communities User Sync Listener]** estão definidas:

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* Pastas Distribuídas

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para sincronizar assinaturas, seguidores e notificações

Em cada instância de publicação de AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md). Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize **[!UICONTROL Ouvinte de Sincronização de Usuário do AEM Communities]**.
1. Selecione a configuração existente a ser aberta para edição (ícone de lápis).

   Verificar nome: **`socialpubsync`\-scheduled-trigger**
1. Defina o seguinte **`NodeTypes`** :

   rep:User

   `nt` : não estruturado

   `nt` :recurso

   rep:ACL

   sling:Folder

   sling:OrderedFolder

   Os tipos de nó especificados nessa propriedade serão sincronizados, e as informações de notificações (blogs e configurações seguidas) serão sincronizadas entre diferentes editores.
1. Adicione todas as pastas para sincronizar em **[!UICONTROL DistributedFolders]**. Por exemplo,

   segmentos/pontuação

   relações sociais

   atividades

1. Defina **`ignorablenodes`** para:

   .tokens

   sistema

   rep `:cache` (como usamos sessões aderentes, não precisamos sincronizar esse nó para diferentes editores)

   ![listner de sincronização de usuário](assets/user-sync-listner.png)

### ID exclusiva do Sling {#unique-sling-id}

AEM instância do autor usa o Sling ID para identificar de onde os dados estão vindo e para quais editores precisa (ou não) enviar o pacote de volta.

Certifique-se de que todos os editores em um farm de publicação tenham uma ID do Sling exclusiva. Se a ID do Sling for a mesma para várias instâncias de publicação em um farm de publicação, ocorrerá falha na sincronização do usuário. Como o autor não saberá de onde buscar o pacote e de onde instalar o pacote.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir a ID de sling exclusiva dos editores no farm de publicação

Em cada instância de publicação:

1. Navegue até [https://_host:port_/system/console/status-slingsettings](http://localhost:4503/system/console/status-slingsettings).
1. Verifique o valor de **[!UICONTROL Sling ID]**.

   ![slingid](assets/slingid.png)

   Se a ID do Sling de uma instância de publicação corresponder à ID do Sling de qualquer outra instância de publicação, então:

1. Pare uma das instâncias de publicação que tenha uma ID do Sling correspondente.
1. No diretório `crx-quickstart/launchpad/felix`, procure e exclua o arquivo chamado _sling.id.file.

   *por exemplo, em um sistema Linux:*

   `rm -i $(find . -type f -name sling.id.file)`

   *por exemplo, em um sistema Windows:*

   `use windows explorer and search for _sling.id.file_`

1. Inicie a instância de publicação. Na inicialização, será atribuído um novo Sling ID.
1. Valide se o **[!UICONTROL Sling ID]** agora é exclusivo.

Repita essas etapas até que todas as instâncias de publicação tenham uma ID do Sling exclusiva.

### Compilador de pacote de cofre de fábrica {#vault-package-builder-factory}

Para que as atualizações sejam sincronizadas corretamente, é necessário modificar o construtor de pacotes de cofre para sincronização do usuário.\
Em `/home/users`, um nó `/rep:cache` é criado. É um cache usado para descobrir que, se consultarmos o nome principal de um nó, esse cache poderá ser usado diretamente.

A sincronização do usuário pode parar se os nós `rep:cache `estiverem sincronizados entre os editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir que as atualizações sejam sincronizadas corretamente entre os editores

Em cada instância de publicação de AEM:

1. Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md), por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize o **[!UICONTROL Apache Sling Distribution Packaging - Compilador de pacote de cofre Nome do construtor de fábrica]**: socialpubsync-vlt.
1. Selecione o ícone de edição.
1. Adicione dois filtros de pacote:

   * `/home/users|-.\*/.tokens`
   * `/home/users|**+**.\*/rep:cache`
1. Tratamento de políticas
   * Para substituir os nós rep `:policy` existentes por novos, adicione um terceiro Filtro de Pacote:

      `/home/users|**+**.\*/rep:policy`
   * Para evitar que as políticas sejam distribuídas, defina

      Manuseio De Acl: IGNORAR

![vault-package-builder-fatory](assets/vault-package-builder-factory.png)

## Solucionar problemas de distribuição do Sling no AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Se a distribuição do Sling falhar, tente as seguintes etapas de depuração:

1. **Verifique se há configurações adicionadas  [incorretamente](../../help/sites-administering/sync.md#improperconfig).** Certifique-se de que várias configurações não sejam adicionadas ou editadas, em vez disso, as configurações padrão existentes devem ser editadas.
1. **Verificar configurações**. Certifique-se de que todas as [configurações](sync.md#bestpractices) estejam definidas adequadamente na instância do autor do AEM, conforme mencionado em [Práticas recomendadas](sync.md#main-pars-header-863110628).
1. **Verifique as permissões** do usuário autorizado. Se os pacotes não estiverem instalados corretamente, verifique se o [usuário autorizado](../../help/sites-administering/sync.md#createauthuser) criado na primeira instância de Publicação possui as ACLs corretas.

   Para validar isso, em vez da configuração [created authorized user](../../help/sites-administering/sync.md#createauthuser) altere o [Adobe Granite Distribution - Encrypted Password Transport Secret Provider](../../help/sites-administering/sync.md#adobegraniteencpasswrd) na instância do autor para usar credenciais de usuário administrador. Agora tente instalar os pacotes novamente. Se a sincronização do usuário funcionar bem com credenciais de administrador, significa que o usuário de publicação criado não tinha ACLs apropriadas.

1. **Verifique a configuração** da Fábrica do Observador Diff. Se apenas nós específicos não forem sincronizados no farm de publicação - por exemplo, os membros do grupo não são sincronizados - em seguida, verifique se a configuração [Distribuição de Adobe Granite - Fábrica de Observador Diff](../../help/sites-administering/sync.md#diffobserver) está ativada e **rep:Members** está definida em **nomes de propriedades pesquisadas**.
1. **Verifique a configuração do Ouvinte de sincronização de usuário do AEM Communities.** Se os usuários criados forem sincronizados, mas as assinaturas e seguintes não estiverem funcionando, verifique se a configuração do Ouvinte de sincronização de usuários do AEM Communities tem:

   * Tipos de nó- definidos como **rep:User, nt:unstructured**, **nt:resource**, **rep:ACL**, **sling:Folder** e **sling:OrderedFolder**
   * Nós ignoráveis- definidos como **.tokens**, **sistema** e **rep:cache**
   * Pastas distribuídas - defina para as pastas que deseja distribuir

1. **Verifique os logs gerados na criação do usuário na instância** de publicação. Se as configurações acima estiverem adequadamente definidas, mas a sincronização do usuário não estiver funcionando, verifique os logs gerados na criação do usuário.

   Verifique se a ordem dos logs é a mesma, da seguinte maneira:

   ```shell
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ2: ADD paths=[/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK], user=communities-user-admin
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ3: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy], user=communities-user-admin
   15.05.2016 18:33:01.757 *INFO* [sling-oak-observation-7431] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_ebb27ad9-a861-4405-9342-d64c916654e2:0.0.1
   15.05.2016 18:33:01.820 *INFO* [sling-oak-observation-7422] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_58811273-5861-48fe-95d2-4aff367b99c3:0.0.1
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK/profile]
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ4: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK/profile], user=communities-user-admin
   15.05.2016 18:33:02.273 *INFO* [sling-oak-observation-7430] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337182039_f34f4fa6-10b9-42eb-8740-4da9d4d38f99:0.0.1
   ```

   Para depurar:

   1. Desativar a sincronização de usuários:
   1. Na instância AEM autor, faça logon com privilégios de administrador.

      1. Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md). Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
      1. Localize o **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Fatory]** de configuração.

      1. Desmarque a caixa de seleção **[!UICONTROL Enabled]**.
      Ao desabilitar a sincronização do usuário na instância do autor, os endpoints (exportador e importador) são desabilitados e a instância do autor é estática. Os pacotes **[!UICONTROL vlt]** não são pingados nem buscados pelo autor.

      Agora, se um usuário for criado na instância de publicação, o pacote **[!UICONTROL vlt]** será criado no nó */var/sling/distribution/packages/ socialpubsync - vlt /data*. E se esses pacotes forem encaminhados pelo autor para outro serviço. Você pode baixar e extrair esses dados para verificar quais propriedades são enviadas para outros serviços.

   1. Vá para um editor e crie um usuário no editor. Como resultado, os eventos são criados.
   1. Verifique a [ordem dos logs](sync.md#troubleshoot-sling-distribution-in-aem-communities), criada na criação do usuário.
   1. Verifique se um pacote **[!UICONTROL vlt]** foi criado em `/var/sling/distribution/packages/socialpubsync-vlt/data`.
   1. Agora, ative a sincronização do usuário AEM instância do autor.
   1. No editor, altere os endpoints do exportador ou importador no **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Fatory]**.

      Podemos baixar e extrair dados do pacote para verificar quais propriedades são enviadas para outros editores e quais dados são perdidos.


