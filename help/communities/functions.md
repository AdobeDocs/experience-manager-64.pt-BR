---
title: Funções da comunidade
seo-title: Community Functions
description: Saiba como acessar o console Funções da comunidade
seo-description: Learn how to access the Community Functions console
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 2%

---

# Funções da comunidade {#community-functions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O tipo de recursos esperados de uma experiência da comunidade são bem conhecidos. Os recursos da comunidade estão disponíveis como funções da comunidade. Essencialmente, elas são uma ou mais páginas pré-conectadas para implementar um recurso da comunidade, o que requer mais do que simplesmente adicionar um componente a uma página no modo de criação. Eles são os blocos de construção usados para definir a estrutura de um [modelo de site da comunidade](sites.md) de onde os sites da comunidade são [criado](sites-console.md).

Depois que um site da comunidade é criado, o conteúdo pode ser adicionado às páginas resultantes usando o padrão [Modo de criação de AEM](../../help/sites-authoring/editing-content.md).

Várias funções da comunidade são imediatamente disponibilizadas, como visto no console de funções da comunidade. Mais funções da comunidade serão fornecidas em versões futuras e também poderão ser criadas funções personalizadas.

>[!NOTE]
>
>Os consoles para a criação de [sites da comunidade](sites-console.md), [modelos de site da comunidade](sites.md), [modelos de grupo da comunidade](tools-groups.md) e [funções da comunidade](functions.md) são para uso somente no ambiente do autor.

## Console Funções da Comunidade {#community-functions-console}

No ambiente de criação, para acessar o console de funções da comunidade

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Funções da comunidade]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Funções pré-criadas {#pre-built-functions}

Veja a seguir uma breve descrição das funções fornecidas com o AEM Communities. Cada função é composta de uma ou mais páginas de AEM contendo componentes de Comunidades conectadas em um recurso que é facilmente incorporado em um [modelo de site da comunidade](sites.md).

Um modelo de site da comunidade fornece a estrutura para um site da comunidade, incluindo logon, perfis de usuário, notificações, mensagens, menu do site, pesquisa, tema e recursos de marca.

### Configurações de título e URL {#title-and-url-settings}

**Título** e **URL** são propriedades comuns a todas as funções da comunidade.

Quando uma função da comunidade é adicionada a um modelo de site da comunidade ou adicionada quando [modificação](sites-console.md#modifying-site-properties) Na estrutura de um site da comunidade, a caixa de diálogo da função é aberta para que o Título e o URL possam ser configurados.

#### Detalhes da função de configuração {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Título]**
(
*obrigatório*) O texto que aparece no menu de recursos do site

* **[!UICONTROL URL]**
(*obrigatório*) O nome usado para gerar o URI. O nome deve estar em conformidade com a [convenções de nomenclatura](../../help/sites-developing/naming-conventions.md) impostas pelo AEM e JCR.

Por exemplo, usar o site criado a partir do seguinte [Introdução](getting-started.md) tutorial, se

* Título = Página da Web
* URL = página

Em seguida, o URL da página é http://local_host:4503/content/sites/engage/en/page.html e o link do menu da página é exibido como:

![chlimage_1-381](assets/chlimage_1-381.png)

### Função de fluxo de atividades {#activity-stream-function}

A função de fluxo de atividade é uma página com uma [Componente Fluxos de atividade](activities.md) com todas as exibições selecionadas (todas as atividades, atividades do usuário e seguintes). Consulte também [Fundamentos do fluxo de atividade](essentials-activities.md) para desenvolvedores.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

#### Detalhes da função de configuração {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Mostrar a exibição &quot;Minhas atividades&quot;]**
Se marcada, a página Atividades incluirá uma guia que filtra as atividades com base nas geradas na comunidade pelo membro atual. O padrão está marcado.

* **[!UICONTROL Mostrar exibição &quot;Todas as atividades&quot;]**
Se marcada, a página Atividades incluirá uma guia que inclui todas as atividades geradas na comunidade às quais o membro atual tem acesso. O padrão está marcado.

* **[!UICONTROL Mostrar exibição do &quot;Feed de notícias&quot;]**
Se marcada, a página Atividades incluirá uma guia que filtra as atividades com base nas atividades que o membro atual está seguindo. O padrão está marcado.

### Função das atribuições {#assignments-function}

A função de atribuições é o recurso básico que define uma [site da comunidade para ativação](overview.md#enablement-community). Ela permite a atribuição de recursos de ativação a membros da comunidade. Consulte também [Fundamentos das Atribuições](essentials-assignments.md) para desenvolvedores.

Essa função está disponível como um recurso do [complemento de ativação](enablement.md). O complemento de ativação requer licenciamento adicional para uso em um ambiente de produção.

Quando adicionada a um template, a única configuração é para a variável [Configurações de título e URL](#title-and-url-settings).

### Função do blog {#blog-function}

A função do blog é uma página com um [Componente de blog](blog-feature.md) configurado para marcação, uploads de arquivo, a seguir, membros para autoeditar, votar e moderar. Consulte também [Blog Essentials](blog-developer-basics.md) para desenvolvedores.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-383](assets/chlimage_1-383.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o blog permitirá que membros privilegiados criem artigos permitindo a seleção de um [grupo de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão criar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, o blog incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se não for marcada, o blog permitirá respostas (comentários) a um artigo, mas as respostas aos comentários não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está marcado.

### Função do calendário {#calendar-function}

A função de calendário é uma página com uma [Componente de calendário](calendar.md) configurado para permitir marcação. Consulte também [Fundamentos do calendário](calendar-basics-for-developers.md) para desenvolvedores.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-384](assets/chlimage_1-384.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir Prender]**
Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista de comentários. O padrão está marcado.

* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o blog permitirá que membros privilegiados criem artigos permitindo a seleção de um [grupo de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão criar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, o blog incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se não for marcada, o blog permitirá respostas (comentários) a um artigo, mas as respostas aos comentários não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está marcado.

### Função do catálogo {#catalog-function}

A função de catálogo fornece a capacidade de [comunidade de capacitação](overview.md#enablement-community) membros para navegar pelos recursos de ativação que não estão atribuídos a eles. Consulte [Marcar recursos de ativação](tag-resources.md) e [Fundamentos do catálogo](catalog-developer-essentials.md) para desenvolvedores.

Todos os recursos de ativação e caminhos de aprendizagem para o site da comunidade serão mostrados em todos os catálogos se sua propriedade, ` [Show in Catalog](resources.md)`, está definido como verdadeiro. Para incluir explicitamente os recursos e os caminhos de aprendizado, é necessário aplicar uma [pré-filtro](catalog-developer-essentials.md#pre-filters) ao catálogo.

Quando adicionada a um modelo, a configuração permite especificar namespace de tag usado para configurar o filtro de tag apresentado aos visitantes do site:

![catalogfunc](assets/catalogfunc.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Selecionar todos os namespaces]**

   * Os namespaces de tags selecionados definem quais tags podem ser selecionadas pelos visitantes para filtrar a lista de recursos de ativação listados no catálogo.
   * Se marcada, todos os namespaces de tags permitidos para o site da comunidade estarão disponíveis.
   * Se estiver desmarcado, é possível selecionar um ou mais namespaces permitidos para o site da comunidade.
   * O padrão está marcado.

### Função de conteúdo em destaque {#featured-content-function}

A função de conteúdo em destaque é uma página com uma [Componente Conteúdo em destaque](featured.md) configurado para permitir que comentários sejam adicionados e excluídos.

A capacidade de incluir conteúdo pode ser permitida ou não permitida por componente (consulte [Função do blog](#blog-function), [Função de calendário](#calendar-function), [Função do fórum](#forum-function), [Função de Ideação](#ideation-function)e [Função QnA](#qna-function)).

Quando adicionada a um template, a única configuração é para a variável [Configurações de título e URL](#title-and-url-settings).

### Função da biblioteca de arquivo {#file-library-function}

A função da biblioteca de arquivos é uma página com um [Componente Biblioteca de arquivos](file-library.md) configurado para permitir que comentários sejam adicionados e excluídos.

Quando adicionada a um template, a única configuração é para a variável [Configurações de título e URL](#title-and-url-settings).

### Função do fórum {#forum-function}

A função do fórum é uma página com um [Componente de fórum](forum.md) configurado para marcação, uploads de arquivo, a seguir, membros para autoeditar, votar e moderar.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

#### Detalhes da função de configuração {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir Prender]**
Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista de comentários. O padrão está marcado.

* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o fórum só permitirá que membros privilegiados publiquem tópicos permitindo a seleção de um [grupo de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, o fórum incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se não for marcada, o fórum permitirá comentários sobre um tópico, mas as respostas a esses comentários não serão permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está marcado.

### Função de grupos {#groups-function}

>[!CAUTION]
>
>A função de grupos deve *not* ser *primeiro nem o único* na estrutura de um site ou em um modelo de site da comunidade.
>
>Qualquer outra função, como a [função de página](#page-function), deve ser incluída e listada primeiro.

A função de grupos oferece a capacidade de membros da comunidade criarem subcomunidades dentro do site da comunidade no ambiente de publicação.

Dependendo de [configurações](sites-console.md#groupmanagement) quando a função Grupos estiver incluída em um [modelo de site da comunidade](sites.md), os grupos podem ser públicos ou privados e um ou mais modelos de grupos da comunidade podem ser configurados para fornecer uma escolha de modelos quando o grupo da comunidade é realmente criado (como a partir do ambiente de publicação). A [modelo de grupo da comunidade](tools-groups.md) especifica quais recursos do Communities são criados para as páginas de grupo, como fóruns e calendários.

Quando um grupo de comunidade é criado, um grupo de membros é criado dinamicamente para o novo grupo, ao qual os membros podem ser atribuídos ou unidos. Para obter mais informações, consulte [Gerenciar usuários e grupos de usuários](users.md).

Comunidades [pacote de recursos 1](deploy-communities.md#latestfeaturepack), os grupos da comunidade são criados no ambiente de criação usando o [Console de grupos do Sites de comunidades](groups.md)e podem ser criadas no ambiente de publicação quando ativadas.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-386](assets/chlimage_1-386.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Selecionar modelos de grupo]**
Um menu suspenso que permite a seleção de um ou mais modelos de grupo ativados a partir dos quais o futuro criador de um novo grupo de comunidade (no ambiente de publicação) pode escolher.

* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o fórum só permitirá que membros privilegiados publiquem tópicos permitindo a seleção de um [grupo de segurança de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir criação de publicação]**
Se marcada, é possível que membros autorizados da comunidade criem um grupo no ambiente de publicação. Se estiver desmarcado, novos grupos (subcomunidades) só poderão ser criados no ambiente do autor a partir do console Grupos do Sites das Comunidades.

   O padrão é `checked`.

### Função de ideação {#ideation-function}

A função de idealização é uma página com uma [Componente de ideação](ideation-feature.md).

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta, que especifica o Título e os nomes de URL padrão, bem como as configurações de exibição padrão do modelo:

![chlimage_1-387](assets/chlimage_1-387.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o fórum só permitirá que membros privilegiados publiquem tópicos permitindo a seleção de um [grupo de segurança de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, a ideia incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se não for marcada, a ideia permitirá respostas (comentários) a um tópico, mas as respostas aos comentários não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está marcado.

### Função do Placar de líderes {#leaderboard-function}

A função de quadro de liderança é uma página com uma [Componente de quadro de líderes](enabling-leaderboard.md).

**OBSERVAÇÃO**: o componente do Quadro de líderes precisará de mais configuração *after* um site da comunidade é criado a partir de um modelo da comunidade que inclui a função de Quadro de líderes. O componente do Quadro de líderes [regras](enabling-leaderboard.md#rules-tab) precisará ser especificado, que dependem da configuração de [pontuação e emblemas](implementing-scoring.md) para o site da comunidade.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta, que especifica o Título e os nomes de URL padrão, bem como as configurações de exibição padrão do modelo:

![chlimage_1-388](assets/chlimage_1-388.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Exibir emblema]**
Se marcada, uma coluna para ícones de selo é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Exibir nome do emblema]**
Se marcada, uma coluna para o nome do símbolo é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Exibir Avatar]**
Se marcada, a imagem de avatar do membro é incluída no quadro de líderes, ao lado de seu link de nome para seu perfil de membro.

   O padrão está desmarcado.

### Função da página {#page-function}

A função de página adiciona uma página em branco ao site da comunidade que está conectada aos recursos do site da comunidade: login, menu, notificações, mensagens, tema e marca. O conteúdo pode ser adicionado à página usando o [modo de criação de AEM padrão](../../help/sites-authoring/editing-content.md).

Quando adicionada a um template, a única configuração é para a variável [Configurações de título e URL](#title-and-url-settings).

### Função QnA {#qna-function}

A função QnA é uma página com um [Componente QnA](working-with-qna.md) configurado para marcação, uploads de arquivo, a seguir, membros para autoeditar, votar e moderar.

Quando adicionada a um template, a configuração permite restrição a membros privilegiados:

![chlimage_1-389](assets/chlimage_1-389.png)

* Consulte [Configurações de título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir Prender]**
Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista de comentários. O padrão está marcado.

* **[!UICONTROL Permitir Membros Privados]**
Se marcada, o fórum QnA só permitirá que membros privilegiados postem perguntas permitindo a seleção de um [grupo de membros privilegiados](users.md#privileged-members-group). Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, o fórum QnA incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se não estiver marcado, o fórum QnA permitirá comentários (respostas) a uma pergunta postada, mas as respostas às respostas não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está marcado.

## Criar função da comunidade {#create-community-function}

A capacidade de criar uma função da comunidade é alcançada ao selecionar a variável `Create Community Function` ícone localizado na parte superior do console Funções da comunidade. Várias funções baseadas no mesmo AEM Blueprint podem ser criadas e personalizadas exclusivamente ao abrir no modo de edição do autor.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nome da função da comunidade {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

No painel Nome da função da comunidade, um nome, uma descrição e se a função está habilitada ou desabilitada são configurados:

* **[!UICONTROL Nome da função da comunidade]**
O nome da função usado para exibição e armazenamento

* **[!UICONTROL Descrição da função da comunidade]**
A descrição da função para exibição

* **[!UICONTROL Desativado/Ativado]**
Um switch de alternância que controla se a função é referenciável

### Blueprint AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

No `AEM Blueprint` , é possível selecionar o blueprint que é a implementação subjacente da função da comunidade.

A função da comunidade é um mini site composto de uma ou mais páginas, pré-conectado para inclusão em um site da comunidade, incluindo logon, perfis de usuário, notificações, mensagens, menu do site, pesquisa, tema e recursos de marca. Depois que a função é criada, é possível [abra a função](#open-community-function) no modo de edição de criação e personalize as configurações de página e/ou componente.

Como a função da comunidade é implementada como uma [live copy](../../help/sites-administering/msm.md#live-copies) de [blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint), é possível implantar alterações feitas em uma função que afeta todas as páginas do site da comunidade criadas a partir do [modelo de site da comunidade](sites.md) ou [modelo de grupo da comunidade](tools-groups.md) que incluiu a função . Também é possível desassociar uma página de seu blueprint pai para fazer modificações no nível da página.

Consulte também [Gerenciador de vários sites](../../help/sites-administering/msm.md).

### Miniatura  {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

No painel Miniatura, uma imagem pode ser carregada para ser exibida no [Console Funções da comunidade](#community-functions-console).

## Abrir função da comunidade {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Selecione o `Open Community Function` ícone para entrar no modo de edição do autor para a criação do conteúdo da página e modificar a configuração do(s) componente(s) do recurso.

### Configuração de componentes {#configuring-components}

Uma função da comunidade é implementada como uma Live Copy de um Blueprint AEM, cujos detalhes estão documentados em [Gerenciador de vários sites](../../help/sites-administering/msm.md).

É possível não apenas criar conteúdo de página, mas configurar componentes.

Ao configurar um componente em uma página de um site de comunidade criado, pode ser necessário cancelar [herança](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) para configurar o componente. A herança deve ser restabelecida quando a configuração for concluída.

Para obter detalhes de configuração, visite [Componentes das comunidades](author-communities.md) para autores.

## Editar função da comunidade {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Selecione o `Edit Community Function` ícone para editar as propriedades da função usando os mesmos painéis como [criação de uma função da comunidade](#create-community-function), incluindo a ativação ou desativação da função .
