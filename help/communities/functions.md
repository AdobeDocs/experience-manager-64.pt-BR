---
title: Funções da comunidade
seo-title: Funções da comunidade
description: Saiba como acessar o console Funções da comunidade
seo-description: Saiba como acessar o console Funções da comunidade
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 2%

---


# Funções da comunidade {#community-functions}

O tipo de recursos esperados de uma experiência da comunidade são bem conhecidos. Os recursos da comunidade estão disponíveis como funções da comunidade. Basicamente, elas são uma ou mais páginas pré-conectadas para implementar um recurso da comunidade que requer mais do que simplesmente adicionar um componente a uma página no modo de autor. Eles são os elementos básicos usados para definir a estrutura de um modelo [de site da](sites.md) comunidade a partir do qual os sites da comunidade são [criados](sites-console.md).

Depois que um site da comunidade é criado, o conteúdo pode ser adicionado às páginas resultantes usando o modo [de criação padrão](../../help/sites-authoring/editing-content.md)AEM.

Várias funções da comunidade estão imediatamente disponíveis, como visto no console de funções da comunidade. Mais funções da comunidade serão disponibilizadas em versões futuras e funções personalizadas também poderão ser criadas.

>[!NOTE]
>
>Os consoles para a criação de sites [da](sites-console.md)comunidade, modelos [de site da](sites.md)comunidade, modelos [de grupos da](tools-groups.md) comunidade e funções [da](functions.md) comunidade são para uso somente no ambiente do autor.

## Console de funções da comunidade {#community-functions-console}

No ambiente do autor, para acessar o console de funções da comunidade

* Da navegação global: **[!UICONTROL Ferramentas > Comunidades > Funções da comunidade]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Funções pré-criadas {#pre-built-functions}

Veja a seguir uma breve descrição das funções fornecidas com a AEM Communities. Cada função é composta de uma ou mais páginas AEM que contêm componentes Comunidades conectados em um recurso que é facilmente incorporado a um modelo [de site da](sites.md)comunidade.

Um modelo de site da comunidade fornece a estrutura para um site da comunidade, incluindo logon, perfis do usuário, notificações, mensagens, menu do site, pesquisa, tema e recursos de marca.

### Configurações de título e URL {#title-and-url-settings}

**Título** e **URL** são propriedades comuns a todas as funções da comunidade.

Quando uma função da comunidade é adicionada a um modelo de site da comunidade ou adicionada ao [modificar](sites-console.md#modifying-site-properties) a estrutura de um site da comunidade, a caixa de diálogo da função é aberta para que o Título e o URL possam ser configurados.

#### Detalhes da função de configuração {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Título]**
(
*(obrigatório*) O texto que aparece no menu de recursos do site

* **[!UICONTROL URL]**(*obrigatório*) O nome usado para gerar o URI. O nome deve estar em conformidade com as convenções [de](../../help/sites-developing/naming-conventions.md) nomenclatura impostas pela AEM e pelo JCR.

Por exemplo, usar o site criado a partir do acompanhamento do tutorial [Introdução](getting-started.md) , se

* Título = Página da Web
* URL = página

Em seguida, o URL da página é http://local_host:4503/content/sites/engage/en/page.html e o link do menu da página é exibido como:

![chlimage_1-381](assets/chlimage_1-381.png)

### Função de fluxo de atividades {#activity-stream-function}

A função de fluxo de atividade é uma página com um componente [de Fluxos de](activities.md) Atividade com todas as visualizações selecionadas (todas as atividades, atividades do usuário e seguintes). Consulte também [Atividade Stream Essentials](essentials-activities.md) para desenvolvedores.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

#### Detalhes da função de configuração {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Mostrar visualização]**&quot;Minhas Atividades&quot; Se marcada, a página Atividades incluirá uma guia que filtros atividades com base nas geradas na comunidade pelo membro atual. O padrão está marcado.

* **[!UICONTROL Mostrar visualização]**&quot;Todas as Atividades&quot; Se marcada, a página do Atividade incluirá uma guia que inclui todas as atividades geradas na comunidade à qual o membro atual tem acesso. O padrão está marcado.

* **[!UICONTROL Mostrar visualização]** do &quot;Feed de notícias&quot; Se marcada, a página do Atividade incluirá uma guia que filtros atividades com base nas  que o membro atual está seguindo. O padrão está marcado.

### Função das atribuições {#assignments-function}

A função de atribuições é o recurso básico que define um site da [comunidade para a ativação](overview.md#enablement-community). Permite a atribuição de recursos de ativação para membros da comunidade. Consulte também [Atribuições essenciais](essentials-assignments.md) para desenvolvedores.

Essa função está disponível como um recurso do complemento de [ativação](enablement.md). O complemento de ativação requer licenciamento adicional para uso em um ambiente de produção.

Quando adicionada a um modelo, a única configuração é para as Configurações [de](#title-and-url-settings)Título e URL.

### Função do blog {#blog-function}

A função de blog é uma página com um componente [de](blog-feature.md) Blog configurado para marcação, uploads de arquivos, a seguir, membros para autoeditar, votar e moderar. Consulte também [Blog Essentials](blog-developer-basics.md) for developers.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-383](assets/chlimage_1-383.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir membros]** privilegiados Se marcada, o blog permitirá que membros privilegiados criem artigos apenas permitindo a seleção de um grupo [de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão criar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivo Se marcada, o blog incluirá a capacidade de os membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas]** encadeadas Se não estiver marcada, o blog permitirá respostas (comentários) a um artigo, mas as respostas aos comentários não serão permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo]** em destaque Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está marcado.

### Função do calendário {#calendar-function}

A função de calendário é uma página com um componente [de](calendar.md) Calendário configurado para permitir marcação. Consulte também [Calendar Essentials](calendar-basics-for-developers.md) for developers.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-384](assets/chlimage_1-384.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir fixação]** Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista dos comentários. O padrão está marcado.

* **[!UICONTROL Permitir membros]** privilegiados Se marcada, o blog permitirá que membros privilegiados criem artigos apenas permitindo a seleção de um grupo [de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão criar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivo Se marcada, o blog incluirá a capacidade de os membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas]** encadeadas Se não estiver marcada, o blog permitirá respostas (comentários) a um artigo, mas as respostas aos comentários não serão permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo]** em destaque Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está marcado.

### Função do catálogo {#catalog-function}

A função de catálogo fornece a capacidade de [ativar membros da comunidade](overview.md#enablement-community) para navegar pelos recursos de ativação que não estão atribuídos a eles. Consulte [Marcação de recursos](tag-resources.md) de ativação e [catálogo essenciais](catalog-developer-essentials.md) para desenvolvedores.

Todos os recursos de ativação e caminhos de aprendizado do site da comunidade serão exibidos em todos os catálogos se sua propriedade ` [Show in Catalog](resources.md)`, estiver definida como true. Para incluir explicitamente recursos e caminhos de aprendizado, é necessário aplicar um [pré-filtro](catalog-developer-essentials.md#pre-filters) ao catálogo.

Quando adicionada a um modelo, a configuração permite especificar namespaces de tags usadas para configurar o filtro de tags apresentado aos visitantes do site:

![catalogfunc](assets/catalogfunc.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Selecionar todos os namespaces]**

   * As namespaces de tags selecionadas definem quais tags podem ser selecionadas por visitantes para filtrar a lista de recursos de ativação listados no catálogo.
   * Se marcada, todas as namespaces de tags permitidas para o site da comunidade estarão disponíveis.
   * Se desmarcada, é possível selecionar uma ou mais namespaces permitidas para o site da comunidade.
   * O padrão está marcado.

### Função de conteúdo em destaque {#featured-content-function}

A função de conteúdo em destaque é uma página com um componente [Conteúdo em](featured.md) destaque configurado para permitir que os comentários sejam adicionados e excluídos.

A capacidade de incluir conteúdo pode ser permitida ou não permitida por componente (consulte Função [do](#blog-function)blog, Função [do](#calendar-function)calendário, Função [do](#forum-function)fórum, Função [de](#ideation-function)ideia e Função [](#qna-function)QnA).

Quando adicionada a um modelo, a única configuração é para as Configurações [de](#title-and-url-settings)Título e URL.

### Função da biblioteca de arquivo {#file-library-function}

A função de biblioteca de arquivos é uma página com um componente [Biblioteca de](file-library.md) arquivos configurado para permitir que os comentários sejam adicionados e excluídos.

Quando adicionada a um modelo, a única configuração é para as Configurações [de](#title-and-url-settings)Título e URL.

### Função do fórum {#forum-function}

A função do fórum é uma página com um componente [do](forum.md) Fórum configurado para marcação, uploads de arquivos, a seguir, membros para autoeditar, votar e moderar.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

#### Detalhes da função de configuração {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir fixação]** Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista dos comentários. O padrão está marcado.

* **[!UICONTROL Permitir membros]** privilegiadosSe marcado, o fórum permitirá somente que membros privilegiados postem tópicos permitindo a seleção de um grupo [de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivo Se marcada, o fórum incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]** Se não estiver marcada, o fórum permitirá comentários sobre um tópico, mas as respostas a esses comentários não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo]** em destaque Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está marcado.

### Função Grupos {#groups-function}

>[!CAUTION]
>
>A função de grupos *não* deve ser a *primeira nem a única* função na estrutura de um site ou em um modelo de site da comunidade.
>
>Qualquer outra função, como a função [de](#page-function)página, deve ser incluída e listada primeiro.

A função de grupos fornece a capacidade de membros da comunidade criarem subcomunidades dentro do site da comunidade no ambiente de publicação.

Dependendo das [configurações](sites-console.md#groupmanagement) quando a função Grupos é incluída em um modelo [de site da](sites.md)comunidade, os grupos podem ser públicos ou privados e um ou mais modelos de grupo da comunidade podem ser configurados para fornecer uma escolha de modelos quando o grupo da comunidade é realmente criado (como a partir do ambiente de publicação). Um modelo [de grupo da](tools-groups.md) comunidade especifica quais recursos das Comunidades são criados para as páginas de grupo, como fóruns e calendários.

Quando um grupo da comunidade é criado, um grupo de membros é criado dinamicamente para o novo grupo, ao qual os membros podem ser atribuídos ou associados. Para obter mais informações, consulte [Gerenciamento de usuários e grupos](users.md)de usuários.

No pacote de [recursos Comunidades 1](deploy-communities.md#latestfeaturepack), os grupos da comunidade são criados no ambiente do autor usando o console [Grupos dos Sites](groups.md)das Comunidades e podem ser criados no ambiente de publicação quando ativados.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta:

![chlimage_1-386](assets/chlimage_1-386.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Selecionar modelos]** de grupoUm menu suspenso que permite a seleção de um ou mais modelos de grupo ativados a partir dos quais o futuro criador de um novo grupo de comunidade (no ambiente de publicação) pode escolher.

* **[!UICONTROL Permitir membros]** privilegiadosSe marcado, o fórum permitirá somente que membros privilegiados postem tópicos permitindo a seleção de um grupo [de segurança de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir criação de publicação]** Se marcada, é possível que membros autorizados da comunidade criem um grupo no ambiente de publicação. Se estiver desmarcada, novos grupos (subcomunidades) só poderão ser criados no ambiente do autor a partir do console Grupos do Sites das Comunidades.

   O padrão é `checked`.

### Função de ideação {#ideation-function}

A função de ideação é uma página com um componente [de](ideation-feature.md)Ideação.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta, que especifica os nomes padrão de Título e URL, bem como as configurações de exibição padrão do modelo:

![chlimage_1-387](assets/chlimage_1-387.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir membros]** privilegiadosSe marcado, o fórum permitirá somente que membros privilegiados postem tópicos permitindo a seleção de um grupo [de segurança de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivo Se marcada, a ideia incluirá a capacidade dos membros carregarem arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]** Se não estiver marcada, a ideia permitirá respostas (comentários) a um tópico, mas as respostas aos comentários não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo]** em destaque Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está marcado.

### Função do Placar de líderes {#leaderboard-function}

A função de quadro de líderes é uma página com um componente [de](enabling-leaderboard.md)Quadro de líderes.

**NOTA**: o componente de Quadro de líderes precisará de mais configuração *depois* que um site da comunidade for criado a partir de um modelo da comunidade que inclui a função de Quadro de líderes. As [regras](enabling-leaderboard.md#rules-tab) do componente do Quadro de líderes precisarão ser especificadas, que dependem da configuração da [pontuação e dos emblemas](implementing-scoring.md) para o site da comunidade.

Quando adicionada a um modelo, a seguinte caixa de diálogo é aberta, que especifica os nomes padrão de Título e URL, bem como as configurações de exibição padrão do modelo:

![chlimage_1-388](assets/chlimage_1-388.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Exibir emblema]** Se marcada, uma coluna para ícones de emblema é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Exibir nome]** do emblema Se marcada, uma coluna para o nome do emblema é incluída no quadro de líderes.

   O padrão está desmarcado.

* **[!UICONTROL Exibir avatar]** Se marcada, a imagem de avatar do membro é incluída no quadro de líderes, ao lado do link de nome para o perfil do membro.

   O padrão está desmarcado.

### Função da página {#page-function}

A função de página adiciona uma página em branco ao site da comunidade que é conectada aos recursos do site da comunidade: login, menu, notificações, mensagens, temas e marcas. O conteúdo pode ser adicionado à página usando o modo [de criação de AEM](../../help/sites-authoring/editing-content.md)padrão.

Quando adicionada a um modelo, a única configuração é para as Configurações [de](#title-and-url-settings)Título e URL.

### Função QnA {#qna-function}

A função QnA é uma página com um componente [](working-with-qna.md) QnA configurado para marcação, uploads de arquivos, a seguir, membros para autoeditar, votar e moderação.

Quando adicionada a um modelo, a configuração permite a restrição para membros privilegiados:

![chlimage_1-389](assets/chlimage_1-389.png)

* Consulte Configurações de [título e URL](#title-and-url-settings)
* **[!UICONTROL Permitir fixação]** Se marcada, o fórum permitirá que as respostas dos tópicos sejam fixadas no início da lista dos comentários. O padrão está marcado.

* **[!UICONTROL Permitir membros]** privilegiados Se marcada, o fórum QnA permitirá somente que membros privilegiados postem perguntas permitindo a seleção de um grupo [de membros](users.md#privileged-members-group)privilegiados. Se não estiver marcada, todos os membros da comunidade poderão publicar. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivo Se marcada, o fórum QnA incluirá a capacidade dos membros de carregar arquivos. O padrão está marcado.

* **[!UICONTROL Permitir respostas encadeadas]** Se não estiver marcada, o fórum de QnA permitirá comentários (respostas) a uma pergunta publicada, mas as respostas às respostas não são permitidas. O padrão está marcado.

* **[!UICONTROL Permitir conteúdo]** em destaque Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está marcado.

## Criar função da comunidade {#create-community-function}

A capacidade de criar uma função da comunidade é alcançada selecionando o `Create Community Function` ícone localizado na parte superior do console Funções da comunidade. Várias funções baseadas no mesmo AEM Blueprint podem ser criadas e personalizadas exclusivamente ao abrir no modo de edição do autor.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nome da função da comunidade {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

No painel Nome da função da comunidade, um nome, uma descrição e se a função está ativada ou desativada são configurados:

* **[!UICONTROL Nome]** da função da comunidade O nome da função usada para exibição e armazenamento

* **[!UICONTROL Descrição]** da função da comunidade A descrição da função para exibição

* **[!UICONTROL Desativado/Ativado]** Um interruptor que controla se a função é referenciável

### Blueprint AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

No `AEM Blueprint` painel, é possível selecionar o blueprint que é a implementação subjacente da função da comunidade.

A função da comunidade é um mini site composto de uma ou mais páginas, pré-conectado para inclusão em um site da comunidade, incluindo login, perfis do usuário, notificações, mensagens, menu do site, pesquisa, temas e recursos de marca. Depois que a função é criada, é possível [abrir a função](#open-community-function) no modo de edição do autor e personalizar as configurações da página e/ou do componente.

Como a função da comunidade é implementada como uma cópia [](../../help/sites-administering/msm.md#live-copies) ativa de um [blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint), é possível implementar alterações feitas em uma função que afeta todas as páginas do site da comunidade criadas a partir do modelo [de site da](sites.md) comunidade ou do modelo [de grupo da](tools-groups.md) comunidade que incluiu a função. Também é possível dissociar uma página do seu blueprint pai para fazer modificações no nível da página.

Consulte também [Gerenciador](../../help/sites-administering/msm.md)de vários sites.

### Miniatura  {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

No painel Miniaturas, uma imagem pode ser carregada para ser exibida no console [Funções da](#community-functions-console)comunidade.

## Abrir função da comunidade {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Selecione o `Open Community Function` ícone para entrar no modo de edição do autor para criar o conteúdo da página e modificar a configuração dos componentes do recurso.

### Configuração de componentes {#configuring-components}

Uma função da comunidade é implementada como uma Live Copy de um Blueprint AEM, cujos detalhes são documentados em [Multi Site Manager](../../help/sites-administering/msm.md).

É possível não apenas criar conteúdo de página, mas também configurar componentes.

Se você configurar um componente em uma página de um site da comunidade criado, talvez seja necessário cancelar a [herança](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) para configurar o componente. A herança deve ser restabelecida quando a configuração for concluída.

Para obter detalhes sobre a configuração, visite Componentes [de](author-communities.md) comunidades para autores.

## Editar função da comunidade {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Selecione o `Edit Community Function` ícone para editar as propriedades da função usando os mesmos painéis que [criar uma função](#create-community-function)da comunidade, incluindo ativar ou desativar a função.
