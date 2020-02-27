---
title: Sincronização de usuários das comunidades
seo-title: Sincronização de usuários das comunidades
description: Como a sincronização do usuário funciona
seo-description: Como a sincronização do usuário funciona
uuid: 5b9bb7b6-9238-41f6-81da-84b9a303b9e2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 32b56b48-75cb-4cc9-a077-10e335f01a35
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Sincronização de usuários das comunidades {#communities-user-synchronization}

## Introdução {#introduction}

No AEM Communities, a partir do ambiente de publicação (dependendo das permissões configuradas), os visitantes *do* site podem se tornar *membros*, criar grupos *de* usuários e editar seus perfis *de* membros.

*Os dados* do usuário são um termo usado para se referir a *usuários*, perfis *de* usuário e grupos *de* usuários.

*Membros* é um termo usado para se referir a *usuários* registrados no ambiente de publicação, em vez de usuários registrados no ambiente do autor.

Para obter mais informações sobre os dados do usuário, visite [Gerenciar usuários e grupos](users.md)de usuários.

## Sincronizando usuários em um farm de publicação {#synchronizing-users-across-a-publish-farm}

Por padrão, os dados do usuário criados no ambiente de publicação não aparecem no ambiente do autor.

A maioria dos dados do usuário criados no ambiente do autor deve permanecer no ambiente do autor e não é sincronizada nem replicada para publicar instâncias.

Quando a [topologia](topologies.md) é um farm [de](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)publicação, o registro e as modificações feitas em uma instância de publicação precisam ser sincronizados com outras instâncias de publicação. Os membros precisam fazer logon e ver seus dados em qualquer nó de publicação.

Quando a sincronização do usuário é ativada, os dados do usuário são sincronizados automaticamente entre as instâncias de publicação no farm.

### Instruções de configuração de sincronização do usuário {#user-sync-setup-instructions}

Para obter instruções detalhadas, passo a passo, sobre como ativar a sincronização em um farm de publicação, consulte

* [Sincronização do usuário](../../help/sites-administering/sync.md)

## Sincronização do usuário em segundo plano {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **Embalagem** VLT: é um arquivo zip de todas as alterações feitas em um editor, que precisam ser distribuídas entre os editores. As alterações em um editor geram eventos que são selecionados pelo ouvinte de eventos de alteração. Isso cria um pacote vlt que contém todas as alterações.

* **Embalagem** de distribuição: contém informações de distribuição para Sling. Essas são informações sobre onde o conteúdo precisa ser distribuído e quando foi distribuído por último.

## O Que Acontece Quando... {#what-happens-when}

### Publicar site do console Sites de comunidades {#publish-site-from-communities-sites-console}

No autor, quando um site da comunidade é publicado no console [Sites da](sites-console.md)Comunidade, o efeito é [replicar](../../help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) as páginas associadas e o Sling distribuir os grupos de usuários da comunidade criados dinamicamente, incluindo sua associação.

### O usuário é criado ou edita o perfil ao publicar {#user-is-created-or-edits-profile-on-publish}

Por padrão, os usuários e perfis criados no ambiente de publicação (por exemplo, por autoregistro, login social, autenticação LDAP) não aparecem no ambiente do autor.

Quando a topologia é um farm [de](topologies.md) publicação e a sincronização do usuário foi configurada corretamente, o perfil *de* usuário *e* usuário é sincronizado no farm de publicação usando a distribuição Sling.

### Novo grupo da comunidade é criado na publicação {#new-community-group-is-created-on-publish}

Embora tenha sido iniciado a partir de uma instância de publicação, a criação de grupo da comunidade, que resulta em novas páginas do site e em um novo grupo de usuários, na verdade ocorre na instância do autor.

Como parte do processo, as novas páginas do site são replicadas para todas as instâncias de publicação. O grupo de usuários da comunidade criado dinamicamente e sua associação são Sling distribuídos para todas as instâncias de publicação.

### Usuários ou grupos de usuários são criados usando o console de segurança {#users-or-user-groups-are-created-using-security-console}

Por padrão, os dados do usuário criados no ambiente de publicação não aparecem no ambiente do autor e vice-versa.

Quando o console Administração e segurança [do](../../help/sites-administering/security.md) usuário for usado para adicionar novos usuários no ambiente de publicação, a sincronização do usuário sincronizará os novos usuários e sua associação de grupo com outras instâncias de publicação, se necessário. A sincronização do usuário também sincronizará os grupos de usuários criados pelo console de segurança.

### O usuário publica conteúdo na publicação {#user-posts-content-on-publish}

Para conteúdo gerado pelo usuário (UGC), os dados inseridos em uma instância de publicação são acessados por meio do SRP [](srp-config.md)configurado.

## Best practices {#bestpractices}

Por padrão, a sincronização do usuário é **desativada**. A ativação da sincronização do usuário envolve a modificação das configurações *existentes* do OSGi. Nenhuma nova configuração deve ser adicionada como resultado da ativação da sincronização do usuário.

A sincronização do usuário depende do ambiente do autor para gerenciar as distribuições de dados do usuário, mesmo que os dados do usuário não sejam criados no autor.

**Pré-requisitos**

1. Se usuários e grupos de usuários já tiverem sido criados em um editor, é recomendável sincronizar [](../../help/sites-administering/sync.md#manually-syncing-users-and-user-groups) manualmente os dados do usuário com todos os editores antes de configurar e ativar a sincronização do usuário.

   Quando a sincronização do usuário estiver ativada, somente os usuários e grupos recém-criados serão sincronizados.

1. Verifique se o código mais recente foi instalado:

   * [Atualizações da plataforma AEM](https://helpx.adobe.com/experience-manager/kb/aem62-available-hotfixes.html)
   * [Atualizações do AEM Communities](deploy-communities.md#latestfeaturepack)

As seguintes configurações são necessárias para permitir a sincronização do usuário no AEM Communities. Certifique-se de que essas configurações estejam corretas para evitar que a distribuição do conteúdo seja reprovada.

### Apache Sling Distribution Agent - Fábrica de agentes de sincronização {#apache-sling-distribution-agent-sync-agents-factory}

Essa configuração busca o conteúdo a ser sincronizado entre os editores. A configuração está na instância Autor. O autor deve acompanhar todos os editores que estão lá e onde sincronizar todas as informações.

Os valores padrão na configuração são para uma única instância de publicação. Como a sincronização do usuário é útil para sincronizar várias instâncias de publicação, como para um farm de publicação, outras instâncias de publicação precisam ser adicionadas à configuração.

**Como o conteúdo é sincronizado?**

A instância do autor faz o ping do ponto de extremidade do exportador dos editores. Sempre que um usuário é criado ou atualizado em editores específicos (n), o Autor obtém o conteúdo dos pontos de extremidade do exportador e [envia o conteúdo](sync.md#main-pars-image-1413756164) para outros editores (n-1, ou seja, além dos editores a partir dos quais o conteúdo é obtido).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar a configuração dos Apache Sling Sync Agents

Na instância do autor do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o Console [da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localize o **[!UICONTROL Apache Sling Distribution Agent - Fábrica]** de agentes de sincronização.

   * Selecione a configuração existente para abrir para edição (ícone de lápis).
   * Verificar nome: **`socialpubsync`.**
   * Marque a caixa de seleção **[!UICONTROL Ativado]** .
   * Selecione **[!UICONTROL Usar várias filas]**.
   * Especifique os Endpoints **[!UICONTROL de]** Exportador e os Endpoints **[!UICONTROL de]** Importador (você pode adicionar mais pontos finais de exportador e importador).

      Esses pontos de extremidade definem de onde você deseja obter o conteúdo e de onde deseja encaminhar o conteúdo. O autor busca o conteúdo do ponto de extremidade do exportador especificado e o envia para os editores (diferente do editor a partir do qual o conteúdo foi obtido).
   ![sync-agent-actual](assets/sync-agent-fact.png)

### Distribuição do Adobe Granite - Provedor secreto de transporte de senha criptografado {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Ela permite que o autor identifique o usuário autorizado, como tendo permissão para sincronizar os dados do usuário do autor para publicar.

O usuário [autorizado criado](../../help/sites-administering/sync.md#createauthuser) em todas as instâncias de publicação ajuda os editores a se conectar ao autor e configurar a distribuição Sling no autor. Esse usuário autorizado tem todas as [ACLs](../../help/sites-administering/sync.md#howtoaddacl)necessárias.

Sempre que os dados devem ser instalados ou obtidos de editores, o autor se conecta aos editores usando as credenciais (nome de usuário e senha) definidas nesta configuração.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para conectar o autor a editores usando um usuário autorizado

Na instância do autor do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o Console [da Web](../../help/sites-deploying/configuring-osgi.md).

   Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localize a distribuição **[!UICONTROL do Adobe Granite - Provedor]** secreto de transporte de senha criptografado.
1. Selecione a configuração existente para abrir para edição (ícone de lápis).

   Verifique a propriedade `name:` \- **`socialpubsync``publishUser`.**
1. Defina o nome de usuário e a senha para o usuário [](../../help/sites-administering/sync.md#createauthorizeduser)autorizado.

   Por exemplo, **`usersync`\-admin **

   ![granito-pasword-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent - Fábrica de agentes da fila {#apache-sling-distribution-agent-queue-agents-factory}

Essa configuração é usada para configurar os dados que você deseja sincronizar entre os editores. Quando os dados são criados/atualizados em caminhos especificados em Raízes **** permitidas, a variável &quot;var/community/distribution/diff&quot; é ativada e o replicador criado obtém os dados de um editor e os instala em outros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar os dados (caminhos de nó) para sincronizar

Na instância de publicação do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o Console [da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize o **[!UICONTROL Apache Sling Distribution Agent - Fábrica]** de agentes da fila.
1. Selecione a configuração existente para abrir para edição (ícone de lápis).

   Verificar nome: `socialpubsync` \-reverter.
1. Marque a caixa de seleção **[!UICONTROL Ativado]** e salve.
1. Especifique os caminhos de nó que devem ser replicados nas raízes **** permitidas.
1. Repita o procedimento para cada `publish` instância.

   ![agentes de fila-fato](assets/queue-agents-fact.png)

### Distribuição do Adobe Granite - Fábrica de Observadores Diff {#adobe-granite-distribution-diff-observer-factory}

Essa configuração sincroniza a associação de grupo entre editores.\
Se alterar a associação de um grupo em um editor não atualizar sua associação em outros editores, verifique se **ref:Members** foi adicionado aos nomes **de propriedades** aparentes.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir a sincronização de membros

Em cada instância de publicação do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o Console [da Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize **[!UICONTROL Adobe Granite Distribution - Fábrica]** de Observadores Diff.
1. Selecione a configuração existente para abrir para edição (ícone de lápis).

   Verifique o nome **[!UICONTROL do]** agente: `socialpubsync` \-reverso&amp;ast;&amp;ast;.
1. Marque a caixa de seleção **[!UICONTROL Ativado]** .
1. Especifique **rep`:members`**como`description`para propertyName em nomes **[!UICONTROL de propriedades]**procuradas e Salvar.

   ![diff-obs](assets/diff-obs.png)

### Apache Sling Distribution Trigger - Fábrica de Acionadores Programados {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Essa configuração permite que você configure o intervalo de sondagem (após o qual os editores são pingados e as alterações são feitas pelo autor) para sincronizar as alterações entre os editores.

O autor pesquisa os editores a cada 30 segundos (padrão). Se houver algum pacote na pasta */var/sling/distribution/packages/ socialpubsync - vlt /shared*, ele irá buscar esses pacotes e instalá-los em outros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Alteração do intervalo de polling

Na instância do autor do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o console [da](../../help/sites-deploying/configuring-osgi.md)Web, por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Localize o Apache Sling Distribution Trigger - Fábrica de acionadores programados ****

   * Selecione a configuração existente para abrir para edição (ícone de lápis)
   * Verificar `Name:` **`socialpubsync`\-agendado-trigger **
   * Defina o intervalo em segundos para o intervalo desejado e salve.
   ![acionador agendado](assets/scheduled-trigger.png)

### Ouvinte de sincronização de usuário do AEM Communities {#aem-communities-user-sync-listener}

Para problemas na distribuição Sling em que há uma discrepância nas assinaturas e seguintes, verifique se as seguintes propriedades nas configurações do **[!UICONTROL AEM Communities User Sync Listener]** estão definidas:

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para sincronizar assinaturas, seguidores e notificações

Em cada instância de publicação do AEM:

1. Faça logon com privilégios de administrador.
1. Acesse o Console [da Web](../../help/sites-deploying/configuring-osgi.md). Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize o ouvinte **[!UICONTROL de sincronização do usuário do]** AEM Communities.
1. Selecione a configuração existente para abrir para edição (ícone de lápis).

   Verificar nome: **`socialpubsync`\-agendado-trigger **
1. Defina o seguinte **`NodeTypes`** :

   rep:User

   `nt` :não estruturado

   `nt` :recurso

   rep:ACL

   sling:Folder

   sling:OrderedFolder

   Os tipos de nó especificados nesta propriedade serão sincronizados e as informações de notificações (blogs e configurações seguidas) serão sincronizadas entre diferentes editores.
1. Adicione todas as pastas para sincronizar em **[!UICONTROL DistributedFolders]**. Por exemplo,

   segmentos/pontuação

   social/relações

   atividades

1. Defina **`ignorablenodes`** como:

   .tokens

   sistema

   rep `:cache` (como usamos sessões aderentes, não precisamos sincronizar esse nó com diferentes editores)

   ![user-sync-listner](assets/user-sync-listner.png)

### ID de Sling exclusiva {#unique-sling-id}

A instância do autor do AEM usa a ID de Sling para identificar de onde os dados estão vindo e para quais editores precisa enviar o pacote de volta (ou não precisa).

Verifique se todos os editores em um farm de publicação têm uma Sling ID exclusiva. Se a Sling ID for a mesma para várias instâncias de publicação em um farm de publicação, a sincronização do usuário falhará. Como o autor não saberá de onde buscar o pacote e de onde instalar o pacote.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir uma ID de Sling exclusiva de editores no farm de publicação

Em cada instância de publicação:

1. Navegue até [https://_host:port_/system/console/status-slingsettings](http://localhost:4503/system/console/status-slingsettings).
1. Verifique o valor da **[!UICONTROL Sling ID]**.

   ![slingid](assets/slingid.png)

   Se a Sling ID de uma instância de publicação corresponder à Sling ID de qualquer outra instância de publicação, então:

1. Pare uma das instâncias de publicação com uma ID de Sling correspondente.
1. No `crx-quickstart/launchpad/felix` diretório, procure e exclua o arquivo chamado _sling.id.file.

   *por exemplo, em um sistema Linux:*

   `rm -i $(find . -type f -name sling.id.file)`

   *por exemplo, em um sistema Windows:*

   `use windows explorer and search for _sling.id.file_`

1. Inicie a instância de publicação. Na inicialização, será atribuída uma nova ID de Sling.
1. Valide se a **[!UICONTROL Sling ID]** agora é exclusiva.

Repita essas etapas até que todas as instâncias de publicação tenham uma Sling ID exclusiva.

### Fábrica do Criador de pacotes Vault {#vault-package-builder-factory}

Para que as atualizações sejam sincronizadas corretamente, é necessário modificar o construtor de pacote do cofre para sincronização do usuário.\
Em `/home/users`, um `/rep:cache` nó é criado. É um cache que é usado para descobrir que, se consultarmos o nome principal de um nó, esse cache poderá ser usado diretamente.

A sincronização do usuário pode parar se `rep:cache `os nós forem sincronizados entre os editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantir que as atualizações sejam sincronizadas corretamente entre os editores

Em cada instância de publicação do AEM:

1. Acesse o console [da](../../help/sites-deploying/configuring-osgi.md)Web, por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localize o Apache Sling Distribution Packaging - Nome **** do construtor de fábrica do Package Builder: socialpubsync-vlt.
1. Selecione o ícone de edição.
1. Adicionar dois filtros de pacote:

   * `/home/users|-.\*/.tokens`
   * `/home/users|**+**.\*/rep:cache`
1. Manuseio de políticas
   * Para substituir os nós de `:policy` preparação existentes por novos, adicione um terceiro Filtro de pacote:

      `/home/users|**+**.\*/rep:policy`
   * Para impedir que as políticas sejam distribuídas, defina

      Tratamento De Acl: IGNORAR

![fábrica-fábrica-pacote-construtor](assets/vault-package-builder-factory.png)

## Solução de problemas de distribuição Sling em AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Se a distribuição Sling falhar, tente as seguintes etapas de depuração:

1. **Verifique se há configurações[adicionadas](../../help/sites-administering/sync.md#improperconfig)incorretamente.** Verifique se várias configurações não foram adicionadas ou editadas, em vez disso, as configurações padrão existentes devem ser editadas.
1. **Verifique as configurações**. Certifique-se de que todas as [configurações](sync.md#bestpractices) estejam adequadamente definidas na instância do autor de AEM, conforme mencionado nas [Práticas recomendadas](sync.md#main-pars-header-863110628).
1. **Verifique as permissões** do usuário autorizado. Se os pacotes não estiverem instalados corretamente, verifique se o usuário [](../../help/sites-administering/sync.md#createauthuser) autorizado criado na primeira instância de Publicação possui as ACLs corretas.

   Para validar isso, em vez da configuração do usuário [autorizado](../../help/sites-administering/sync.md#createauthuser) criado, altere a Distribuição do [Adobe Granite - Distribuição criptografada do provedor](../../help/sites-administering/sync.md#adobegraniteencpasswrd) secreto de transporte de senha na instância do autor para usar as credenciais do usuário administrador. Agora tente instalar os pacotes novamente. Se a sincronização do usuário funcionar bem com as credenciais de administrador, isso significa que o usuário de publicação criado não tinha ACLs apropriadas.

1. **Verifique a configuração** da Fábrica de Observadores Diff. Se apenas nós específicos não forem sincronizados no farm de publicação - por exemplo, os membros do grupo não serão sincronizados -, verifique se a configuração [Adobe Granite Distribution - Fábrica](../../help/sites-administering/sync.md#diffobserver) do Observador de Comparação está ativada e **rep:membros** estão definidos em nomes **de propriedades** procuradas.
1. **Verifique a configuração do ouvinte de sincronização do usuário do AEM Communities.** Se os usuários criados estiverem sincronizados, mas as assinaturas e seguintes não estiverem funcionando, verifique se a configuração do AEM Communities User Sync Listener possui:

   * Tipos de nó - definidos como **rep:User, nt:unstructure**, **nt:resource**, **rep:ACL**, **sling:Folder** e **sling:OrderedFolder**
   * Nós ignoráveis - definidos como **.tokens**, **sistema** e **rep:cache**
   * Pastas distribuídas - definidas para as pastas que você deseja que sejam distribuídas

1. **Registros de verificação gerados na criação do usuário na instância** Publicar. Se as configurações acima estiverem adequadamente definidas e a sincronização do usuário não estiver funcionando, verifique os logs gerados na criação do usuário.

   Verifique se a ordem dos registros é a mesma, como segue:

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

   1. Desativar a sincronização do usuário:
   1. Na instância do autor de AEM, faça logon com privilégios de administrador.

      1. Acesse o Console [da Web](../../help/sites-deploying/configuring-osgi.md). Por exemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
      1. Localize a configuração **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Fatory]**.

      1. Desmarque a caixa de seleção **[!UICONTROL Ativado]** .
      Ao desativar a sincronização do usuário na instância do autor, os pontos finais (exportador e importador) são desativados e a instância do autor é estática. Os pacotes **[!UICONTROL vlt]** não são pingados ou buscados pelo autor.

      Agora, se um usuário for criado na instância de publicação, o pacote **[!UICONTROL vlt]** será criado no nó */var/sling/distribution/packages/ socialpubsync - vlt /data* . E se esses pacotes forem encaminhados pelo autor para outro serviço. Você pode baixar e extrair esses dados para verificar quais propriedades são enviadas para outros serviços.

   1. Vá até um editor e crie um usuário no editor. Como resultado, os eventos são criados.
   1. Verifique a [ordem dos logs](sync.md#troubleshoot-sling-distribution-in-aem-communities)criados na criação do usuário.
   1. Verifique se um pacote **[!UICONTROL vlt]** foi criado em `/var/sling/distribution/packages/socialpubsync-vlt/data`.
   1. Agora, ative a sincronização do usuário na instância do autor de AEM.
   1. No editor, altere os pontos de extremidade do exportador ou importador no **[!UICONTROL Apache Sling Distribution Agent - Sync Agents Fatory]**.

      Podemos baixar e extrair dados do pacote para verificar quais propriedades são enviadas para outros editores e quais dados são perdidos.


