---
title: Criar um novo site da comunidade
seo-title: Author a New Community Site
description: Como criar um novo site do AEM Communities
seo-description: How to author a new AEM Communities site
uuid: b8557416-cae4-489e-ab3b-e94d56686b7a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: bf182bb7-e305-45be-aadb-d71efd70f8cb
exl-id: 5d58f9c5-3210-48ef-94a3-805a1a57e3af
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1672'
ht-degree: 2%

---

# Criar um novo site da comunidade {#author-a-new-community-site}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Criar um novo site da comunidade {#create-a-new-community-site}

Use a instância de autor para criar um novo site da comunidade

* Fazer logon com privilégios de administrador
* Na navegação global: **[!UICONTROL Navegação > Comunidades > Sites]**

O console Sites das Comunidades fornece um assistente para guiá-lo pelas etapas de criação de um site da comunidade. É possível avançar para a `Next`etapa ou `Back`para a etapa anterior antes de confirmar o site na etapa final.

Para começar a criar um novo site de comunidade:

* Selecione o `Create` botão

![createcommunitysite](assets/createcommunitysite.png)

### Etapa 1: Modelo do site {#step-site-template}

![createsitetemplate63](assets/createsitetemplate63.png)

No [Etapa do modelo de site](sites-console.md#step2013asitetemplate), insira um título, descrição, o nome do URL e selecione um modelo de site da comunidade, por exemplo:

* **[!UICONTROL Título do site da comunidade]**: `Getting Started Tutorial`

* **[!UICONTROL Descrição do site da comunidade]**: `A site for engaging with the community.`

* **[!UICONTROL Raiz do site da comunidade]**: (deixe em branco para a raiz padrão `/content/sites`)

* **[!UICONTROL Configurações da nuvem]**: (deixe em branco se nenhuma configuração de nuvem for especificada) forneça o caminho para as configurações de nuvem especificadas.
* **[!UICONTROL Idioma base do site da comunidade]**: (deixar intocado para uma única língua: inglês) use o menu suspenso para escolher um *ou mais* Idiomas de base dos idiomas disponíveis: alemão, italiano, francês, japonês, espanhol, português (Brasil), chinês (tradicional) e chinês (simplificado). Um site da comunidade será criado para cada idioma adicionado e existirá na mesma pasta do site seguindo a prática recomendada descrita em [Tradução de conteúdo para sites multilíngues](../../help/sites-administering/translation.md). A página raiz de cada site conterá uma página filho chamada pelo código de idioma de um dos idiomas selecionados, como &quot;en&quot; para inglês ou &quot;fr&quot; para francês.

* **[!UICONTROL Nome do site da comunidade]**: engajamento

   * Verifique novamente o nome, pois ele não é facilmente alterado após a criação do site
   * O URL inicial será exibido abaixo do Nome do site da comunidade
   * Para um URL válido, anexe um código de idioma base + &quot;.html&quot;
   * *Por exemplo*, http://localhost:4502/content/sites/ `engage/en.html`

* **[!UICONTROL Modelo]**: puxe para baixo para escolher `Reference Site`

Selecione **[!UICONTROL Próximo]**

### Etapa 2: Design {#step-design}

A etapa Design é apresentada em duas seções para selecionar o tema e o banner de marca:

#### TEMA DO SITE DA COMUNIDADE {#community-site-theme}

Selecione o estilo desejado para aplicar ao modelo. Quando selecionado, o tema será sobreposto com uma marca de verificação.

![sitetheme](assets/sitetheme.png)

#### MARCA DO SITE DA COMUNIDADE {#community-site-branding}

(Opcional) Faça upload de uma imagem de banner para exibição nas páginas do site. O banner é fixado à borda esquerda do navegador, entre o cabeçalho do site da comunidade e o menu (links de navegação). A altura do banner é cortada para 120 pixels. Não há redimensionamento do banner para ajustar a largura do navegador e a altura de 120 pixels.

![chlimage_1-353](assets/chlimage_1-353.png) ![chlimage_1-354](assets/chlimage_1-354.png)

Selecione **[!UICONTROL Próximo]**.

### Etapa 3: Configurações {#step-settings}

Na etapa Configurações , antes de selecionar `Next`, observe que há sete seções fornecendo acesso às configurações que envolvem gerenciamento de usuários, marcação, moderação, gerenciamento de grupos, análise, tradução e ativação.

Visite o [Introdução ao AEM Communities para ativação](getting-started-enablement.md) tutorial para experimentar o trabalho com os recursos de ativação.

#### GERENCIAMENTO DE USUÁRIOS {#user-management}

Marque todas as caixas de seleção para [Gerenciamento de usuários](sites-console.md#user-management)

* Para permitir que os visitantes do site se registrem automaticamente
* Para permitir que os visitantes do site vejam o site sem fazer logon
* Para permitir que membros enviem e recebam mensagens de outros membros da comunidade
* Para permitir o logon com o Facebook em vez de registrar e criar um perfil
* Para permitir o logon com o Twitter em vez de registrar e criar um perfil

>[!NOTE]
>
>Para um ambiente de produção, é necessário criar aplicativos Facebook e Twitter personalizados. Consulte [Logon no Social com Facebook e Twitter](social-login.md).

![createsitesetsettings](assets/createsitesettings.png)

#### MARCAÇÃO {#tagging}

As tags que podem ser aplicadas ao conteúdo da comunidade são controladas selecionando AEM namespaces definidos anteriormente por meio da variável [Console de marcação](../../help/sites-administering/tags.md#tagging-console) (como [Namespace do tutorial](setup.md#create-tutorial-tags)).

Encontrar namespaces é fácil usando a pesquisa antecipada por tipo. Por exemplo,

* Digite &#39;tut&#39;
* Selecionar `Tutorial`

![chlimage_1-355](assets/chlimage_1-355.png)

#### FUNÇÕES {#roles}

[Funções dos membros da comunidade](users.md) são atribuídas pelas configurações na seção Funções .

Para permitir que um membro da comunidade (ou grupo de membros) experiencie o site como o gerente da comunidade, use a pesquisa do tipo para frente e selecione o nome do membro ou grupo nas opções do menu suspenso.

Por exemplo,

* Digite &quot;q&quot;
* Selecionar [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Serviço de túnel](https://helpx.adobe.com/experience-manager/6-3/communities/using/deploy-communities.html#tunnel-service-on-author) permite a seleção de membros e grupos existentes somente no ambiente de publicação.

![community_funções-1](assets/community_roles-1.png)

#### MODERAÇÃO {#moderation}

Aceite as configurações globais padrão para [moderação](sites-console.md#moderation) conteúdo gerado pelo usuário (UGC).

![chlimage_1-356](assets/chlimage_1-356.png)

#### ANALYTICS {#analytics}

Se o Adobe Analytics estiver licenciado e um serviço e uma estrutura de nuvem do Analytics tiverem sido configurados, será possível ativar o Analytics e selecionar a estrutura.

Consulte [Configuração do Analytics para recursos das Comunidades](analytics.md).

![chlimage_1-357](assets/chlimage_1-357.png)

#### TRADUÇÃO {#translation}

O [Configurações de tradução](sites-console.md#translation) especifique o idioma base do site, bem como se o UGC pode ser traduzido ou não e em qual idioma, se assim for.

* Verificar **[!UICONTROL Permitir tradução automática]**
* Deixe os idiomas padrão selecionados para tradução pelo serviço de Tradução Automática padrão
* Deixar provedor e configuração de tradução padrão
* Não há necessidade de uma loja global porque não há cópias de idioma
* Selecionar **[!UICONTROL Traduzir página inteira]**
* Deixe a opção de persistência padrão

![chlimage_1-358](assets/chlimage_1-358.png)

#### ATIVAÇÃO {#enablement}

Deixe em branco ao criar uma comunidade de envolvimento.

Para obter um tutorial semelhante, crie rapidamente um [comunidade de capacitação](overview.md#enablement-community), consulte [Introdução ao AEM Communities para ativação](getting-started-enablement.md).

Selecione **[!UICONTROL Próximo]**.

### Etapa 4: Criar Site de Comunidades {#step-create-communities-site}

Selecione **[!UICONTROL Criar]**.

![chlimage_1-359](assets/chlimage_1-359.png)

Quando o processo for concluído, a pasta do novo site será exibida no console Comunidades - Sites .

![console comunidades](assets/communitiessitesconsole.png)

## Publicar o novo site da comunidade {#publish-the-new-community-site}

O site criado deve ser gerenciado no console Comunidades - Sites , o mesmo console de onde novos sites podem ser criados.

Depois de selecionar a pasta do site da comunidade para abri-lo, passe o mouse sobre o ícone do site para que quatro ícones de ação sejam exibidos:

![siteactionicons-1](assets/siteactionicons-1.png)

Ao selecionar o quarto ícone de elipses (Mais ações), as opções Exportar site e Excluir site são exibidas.

![siteactionsnew-1](assets/siteactionsnew-1.png)

Da esquerda para a direita, são:

* **Abrir Site**
Selecione o ícone de lápis para abrir o site da comunidade no modo de edição do autor, para adicionar e/ou configurar os componentes da página

* **Editar Site**
Selecione o ícone de propriedades para abrir o site da comunidade para modificação de propriedades, como o título ou para alterar o tema

* **Publicar site**
Selecione o ícone do mundo para publicar o site da comunidade (por exemplo, se o servidor de publicação estiver em execução no computador local, em seguida, para localhost:4503 por padrão)

* **Exportar Site**
Selecione o ícone de exportação para criar um pacote do site da comunidade que está armazenado em [gerenciador de pacotes](../../help/sites-administering/package-manager.md) e baixado.

   Observe que o UGC não está incluído no pacote do site.

* **Excluir site**

   selecione o ícone excluir para excluir o site da comunidade de dentro **[!UICONTROL Comunidades > Console Sites]**. Essa ação remove todos os itens associados ao site, como UGC, grupos de usuários, ativos e registros de banco de dados.

![siteactions-1](assets/siteactions-1.png)

>[!NOTE]
>
>Se não estiver usando a porta padrão 4503 para a instância de publicação, edite o agente de replicação padrão para definir o número da porta com o valor correto.
>
>Na instância do autor, no menu principal
>
>1. Navegar para **[!UICONTROL Ferramentas > Operações > Replicação]** menu
>1. Selecionar **[!UICONTROL Agentes do autor]**
>1. Selecionar **[!UICONTROL Agente padrão (publicar)]**
>1. Próximo a **[!UICONTROL Configurações]** select **[!UICONTROL Editar]**
>1. Na caixa de diálogo pop-up Configurações do agente, selecione a guia Transporte
>1. No URI, altere o número da porta, 4503, para o número da porta desejado

>
>Por exemplo, para usar a porta 6103: `http://localhost:6103/bin/receive?sling:authRequestLogin=1`
>
>1. Selecionar **[!UICONTROL OK]**
>1. (Opcional) Selecione `Clear` ou `Force Retry` para redefinir a fila de replicação


### Selecionar publicação {#select-publish}

Depois de garantir que o servidor de publicação está em execução, selecione o ícone do mundo para publicar o site da comunidade.

![chlimage_1-360](assets/chlimage_1-360.png)

Quando o site da comunidade tiver sido publicado com sucesso, uma mensagem será exibida brevemente:

![chlimage_1-361](assets/chlimage_1-361.png)

### Avisar novos grupos de usuários da comunidade {#notice-new-community-user-groups}

Junto com o novo site da comunidade, novos grupos de usuários são criados com as permissões apropriadas definidas para várias funções administrativas. Para obter detalhes, visite [Grupos de usuários para sites da comunidade](users.md#usergroupsforcommunitysites).

Para este novo site da comunidade, dado o nome do site &quot;engajar&quot; na Etapa 1, os quatro novos grupos de usuários podem ser vistos no [Console Grupos](members.md) (navegação global: Comunidades, Grupos):

* Gestores da Comunidade em matéria de compromissos
* Grupos de envolvimento da comunidade
* Membros do Envolvimento da Comunidade
* Moderadores de participação na comunidade
* Membros privilegiados do Community Engage
* Community Engage Sitecontentmanager

Observe que [Aaron McDonald](tutorials.md#demo-users) é membro de

* Gestores da Comunidade em matéria de compromissos
* Moderadores de participação na comunidade
* Membros do Community Engage (indiretamente como membro do grupo Moderators)

![chlimage_1-362](assets/chlimage_1-362.png)

#### http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-363](assets/chlimage_1-363.png)

## Configurar para Erro de Autenticação {#configure-for-authentication-error}

Depois que um site é configurado e enviado para publicação, [configurar o mapeamento de logon](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) na instância de publicação. A vantagem é que, quando as credenciais de logon não são inseridas corretamente, o erro de autenticação exibirá novamente a página de logon do site da comunidade com uma mensagem de erro.

Adicione um `Login Page Mapping` as

* /content/sites/engagement/en/sign:/content/sites/engagement/en

## Etapas opcionais {#optional-steps}

### Alterar a página inicial padrão {#change-the-default-home-page}

Ao trabalhar com o site de publicação para fins de demonstração, pode ser útil alterar a página inicial padrão para o novo site.

Para fazer isso, é necessário usar [CRXDE](http://localhost:4503/crx/de) Lite para editar o [mapeamento de recursos](../../help/sites-deploying/resource-mapping.md) tabela em publicar.

Para começar:

1. Ao publicar, faça logon com privilégios de administrador
1. Navegue até [http://localhost:4503/crx/de](http://localhost:4503/crx/de)
1. No navegador do projeto, expanda `/etc/map`
1. Selecione o `http` nó

   * Selecionar **[!UICONTROL Criar nó]**

      * **Nome** localhost.4503

         (do *not* use `:`)

      * **Tipo** [sling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Com recém-criado `localhost.4503` nó selecionado

   * Adicionar propriedade

      * **Nome** sling:match
      * **Tipo** String
      * **Valor** localhost.4503/\$

         (deve terminar com &#39;$&#39; char)
   * Adicionar propriedade

      * **Nome** sling:internalRedirect
      * **Tipo** String
      * **Valor** /content/sites/engage/en.html


1. Selecionar **[!UICONTROL Salvar tudo]**
1. (opcional) Excluir o histórico de navegação
1. Navegue até http://localhost:4503/

   * Acesse http://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Para desativar, basta anexar o `sling:match` valor da propriedade com um &#39;x&#39; - `xlocalhost.4503/$` - e **[!UICONTROL Salvar tudo]**.

![chlimage_1-364](assets/chlimage_1-364.png)

#### Solução de problemas: Erro ao salvar o mapa {#troubleshooting-error-saving-map}

Se não conseguir salvar as alterações, verifique se o nome do nó é `localhost.4503`, com um separador de &quot;ponto&quot;, e não `localhost:4503` com um separador de &quot;dois pontos&quot;, como `localhost`não é um prefixo de namespace válido.

![chlimage_1-365](assets/chlimage_1-365.png)

#### Solução de problemas: Falha ao redirecionar {#troubleshooting-fail-to-redirect}

O &quot;**$**&#39; no final da expressão regular `sling:match`é crucial, de modo que somente `http://localhost:4503/` estiver mapeado, caso contrário, o valor de redirecionamento será anexado a qualquer caminho que possa existir após server:port no URL. Dessa forma, quando o AEM tenta redirecionar para a página de logon, ela falha.

### Modificar o site {#modify-the-site}

Após a criação inicial do site, os autores podem usar a variável [Ícone Abrir site](sites-console.md#authoring-site-content) para executar atividades de criação de AEM padrão.

Além disso, os administradores podem usar o [Ícone Editar site](sites-console.md#modifying-site-properties) para modificar as propriedades do site, como o título.

Depois de qualquer modificação, lembre-se de **salvar** e **publicar novamente** o site.

>[!NOTE]
>
>Se não estiver familiarizado com AEM, visualize a documentação em [tratamento básico](../../help/sites-authoring/basic-handling.md) e [guia rápido para a criação de páginas](../../help/sites-authoring/qg-page-authoring.md).
