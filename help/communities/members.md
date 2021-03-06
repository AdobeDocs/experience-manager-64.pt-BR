---
title: Consoles de gerenciamento de membros e grupos
seo-title: Consoles de gerenciamento de membros e grupos
description: Como acessar os consoles Gerenciamento de membros e grupos
seo-description: Como acessar os consoles Gerenciamento de membros e grupos
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
role: Admin
exl-id: 2d0154b3-4cd7-439a-869d-cb116f60b69d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 3%

---

# Consoles de gerenciamento de membros e grupos {#members-groups-management-consoles}

## Visão geral {#overview}

Os recursos do AEM Communities geralmente exigem que os visitantes do site sejam registrados e conectados antes de participar de uma comunidade no ambiente de publicação. Seu registro de usuário só precisa existir no ambiente de publicação e eles são comumente chamados de *membros* para diferenciá-los de *usuários* registrados no ambiente de criação.

### Membros (usuários) na publicação {#members-users-on-publish}

Usando os consoles Membros e Grupos do Communities, membros e grupos de membros registrados no ambiente *publish* podem ser criados e gerenciados no ambiente *author*. Isso só é possível quando o [túnel service](deploy-communities.md#tunnel-service-on-author) está ativado.

### Usuários no autor {#users-on-author}

Para gerenciar usuários e grupos registrados no ambiente *author*, é necessário usar o console de segurança da plataforma:

* Na navegação global, selecione `Tools, Security, Users`
* Na navegação global, selecione `Tools, Security, Groups`

>[!NOTE]
>
>Com o conteúdo de amostra implantado e ativado, muitos usuários de amostra existem nos ambientes de autor e publicação. Esses usuários não estarão presentes ao executar com [nosamplecontent runmode](../../help/sites-administering/production-ready.md).

## Console de membros {#members-console}

No ambiente de criação, para acessar o console Membros para gerenciar membros registrados no ambiente de publicação:

* Na navegação global: **[!UICONTROL Navegação > Comunidades > Membros]**

>[!CAUTION]
>
>Não será possível usar o console Membros se o [túnel service](deploy-communities.md#tunnel-service-on-author) não estiver habilitado.

![chlimage_1-119](assets/chlimage_1-119.png)

### Pesquisar   {#search-features}

Selecione o ícone do painel lateral no lado esquerdo do cabeçalho `Members` para alternar e abrir o painel lateral de pesquisa.

![chlimage_1-120](assets/chlimage_1-120.png) ![chlimage_1-121](assets/chlimage_1-121.png)

Selecione o ícone de pesquisa no lado esquerdo do cabeçalho `Members` para fechar o painel lateral de pesquisa.

### Estatísticas do Membro {#member-statistics}

As colunas que exibem `Views`, `Posts`, `Follows`e `Likes` são atualizadas quando o usuário é membro de um ou mais sites da comunidade com Adobe Analytics [enabled](sites-console.md#analytics).

### Exportar CSV {#export-csv}

Selecionar o link `Export CSV` resulta no download de todos os membros como uma lista de valores separados por vírgula, adequados para importação em uma planilha.

Os cabeçalhos da coluna são

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Criar novo membro {#create-new-member}

Selecione `Create Member` para criar um usuário no ambiente de publicação.

![chlimage_1-122](assets/chlimage_1-122.png)

### GERAL - Detalhes do Membro {#general-member-details}

A maioria dos campos são campos opcionais que o membro pode preencher posteriormente no perfil.

* **[!UICONTROL ID]**
(
*obrigatório*) A ID autorizável é a ID de logon do membro.
Por padrão, a ID é definida com o valor do endereço de email necessário.
   *Depois de criada, a ID não pode ser modificada.*

* **[!UICONTROL Endereço de email]**
(
*obrigatório*) O endereço de email do membro.
O membro pode alterar seu endereço de email ao atualizar seu perfil.I
Se a ID tiver sido padronizada para o endereço de email, a ID *not* será alterada quando o endereço de email for alterado.

* **[!UICONTROL Senha]**
(
*obrigatório*) A senha de logon.

* **[!UICONTROL Digite a senha novamente]**
(
*obrigatório*) Digite novamente a senha para verificação.

* **[!UICONTROL Adicionar membro aos Sites]**
(
*opcional*) selecione dentre sites da comunidade existentes para adicionar o membro ao grupo de membros do site da comunidade.

* **[!UICONTROL Adicionar membro aos grupos]**
(
*opcional*) selecione de grupos de membros existentes para adicionar o membro a esse grupo.

* Selecione **[!UICONTROL Salvar]**

### GERAL - Configurações de conta {#general-account-settings}

Em Configurações de conta , é possível que um administrador da comunidade

* **[!UICONTROL Status]**
   * Proibido\
      Um membro não consegue fazer logon, impedindo que visualize páginas ou participe de atividades que exigem o logon. Eles ainda podem visitar anonimamente um site aberto da comunidade.

   * Não Banido
Um membro tem acesso total ao site da comunidade.

   O padrão é `Not Banned`.

* **[!UICONTROL Limites]**
de contribuição Se marcada, a capacidade do membro de publicar conteúdo é limitada.
O padrão depende da configuração dos limites de contribuição.
Consulte [Limites de contribuição do membro](limits.md).

* **[!UICONTROL Alterar]**
Senha Um link que está presente ao modificar um membro existente. Fornece a capacidade de um administrador da comunidade redefinir uma senha para um membro.

### GERAL - Foto {#general-photo}

Para fornecer um avatar para o membro, comece selecionando **[!UICONTROL Fazer upload da imagem]** e escolha uma imagem do tipo .jpg, .png, .tif ou .gif. O tamanho preferencial de uma imagem é 240 x 240 pixels a 72 dpi.

### GERAL - Adicionar Membro aos Sites {#general-add-member-to-sites}

O membro pode ser adicionado a um ou mais grupos de membros do site da comunidade. Comece inserindo texto na caixa de texto.

### GERAL - Adicionar Membro a Grupos {#general-add-member-to-groups}

O membro pode ser acrescentado a um ou mais grupos de membros. Comece inserindo texto na caixa de texto.

### Guia BADGES {#badges-tab}

O painel `BADGES` fornece a capacidade de atribuir manualmente os emblemas, bem como de revogá-los. Os emblemas podem ser para funções atribuídas, bem como emblemas normalmente ganhos.

Consulte também [Pontuação e emblema](implementing-scoring.md).

![chlimage_1-123](assets/chlimage_1-123.png)

* **[!UICONTROL Adicionar emblemas]**
   * Comece a digitar para selecionar de [badges disponíveis](badges.md). Depois que um selo for selecionado, escolha cada site, ou todos os sites, nos quais o selo deve ser exibido junto com o avatar do membro.
   * Vários emblemas e sites podem ser escolhidos.
* **[!UICONTROL Remover emblemas]**
   * Selecione o ícone da lixeira ao lado de um selo para removê-lo

## Console Grupos {#groups-console}

O console Grupos , disponível no ambiente de criação, permite a criação e o gerenciamento de grupos de membros registrados no ambiente de publicação. É particularmente útil para:
* [Grupos de membros privilegiados](users.md#privilegedmembersgroups)
* Atribuição baseada em grupo de [recursos de ativação](resources.md)

Para acessar o console Grupos :
* Na navegação global: **[!UICONTROL Navegação > Comunidades > Grupos]**

>[!CAUTION]
>
>Não será possível usar o console Grupos se o [túnel service](deploy-communities.md#tunnel-service-on-author) não estiver habilitado.

### Criar novo grupo {#create-new-group}

Selecione `Add Group` para criar um grupo no ambiente de publicação.

![chlimage_1-124](assets/chlimage_1-124.png)

Os campos necessários para criar um novo grupo de membros do lado da publicação são:

* **[!UICONTROL ID]**
(
*obrigatório*) a ID exclusiva do grupo.
   *Depois de criada, a ID não pode ser modificada.*

* **[!UICONTROL Nome]**
(
*opcional*) o nome de exibição do grupo.

   O valor padrão é a ID.

* **[!UICONTROL Descrição]**
(
*opcional*) uma descrição da finalidade e das permissões do grupo.

* **[!UICONTROL Adicionar membros ao grupo]**
(
*opcional*) Selecione os membros do lado da publicação a serem incluídos como membros iniciais do grupo.

* Selecione **[!UICONTROL Salvar]**

## Administradores autorizados {#authorized-administrators}

Ao trabalhar com membros no console de membros das Comunidades, é necessário fazer logon como um usuário com as permissões apropriadas e para que o agente de replicação usado pelo [túnel service](deploy-communities.md#tunnel-service-on-author) seja configurado corretamente.

Se não tiver feito logon como `admin`, o usuário conectado deverá ser membro do grupo de usuários `administrators`.

Consulte também [Agentes de Replicação no Autor](deploy-communities.md#replication-agents-on-author).
