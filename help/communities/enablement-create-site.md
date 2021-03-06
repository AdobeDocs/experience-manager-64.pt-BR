---
title: Criar um novo site da comunidade para habilitação
seo-title: Criar um novo site da comunidade para habilitação
description: Criar um site da comunidade para ativação
seo-description: Criar um site da comunidade para ativação
uuid: 6822cc99-e272-4661-bddf-aa0800b88c41
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: aff8b79f-dd4e-486e-9d59-5d09dfe34f27
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '1744'
ht-degree: 2%

---


# Crie um novo site da comunidade para a ativação {#author-a-new-community-site-for-enablement}

## Criar site da comunidade {#create-community-site}

[A ](sites-console.md) criação do site da comunidade emprega um assistente que o orienta pelas etapas da criação de um site da comunidade. É possível ir para a etapa `Next`ou `Back`para a etapa anterior antes de confirmar o site na etapa final.

Para começar a criar um novo site da comunidade:

Usando a instância [autor](http://localhost:4502/)

* Fazer logon com privilégios de administrador
* Navegue até **[!UICONTROL Comunidades > Sites]**

* Selecione **[!UICONTROL Criar]**

### Etapa 1: Modelo do site {#step-site-template}

![enablementsitetemplate](assets/enablementsitetemplate.png)

Na etapa **Modelo de site**, insira um título, uma descrição, o nome do URL e selecione um modelo de site da comunidade, por exemplo:

* **Título do site da comunidade**: `Enablement Tutorial`

* **Descrição do site da comunidade**: `A site for enabling the community to learn.`

* **Raiz** do site da comunidade: (deixe em branco para a raiz padrão  `/content/sites`)

* **Configurações** da nuvem: (deixe em branco se nenhuma configuração de nuvem for especificada) forneça o caminho para as configurações de nuvem especificadas.
* **Idioma** base do site da comunidade: (deixe intocado para uma única língua: Inglês) use o menu suspenso para escolher um  *ou* mais idiomas base dos idiomas disponíveis - alemão, italiano, francês, japonês, espanhol, português (Brasil), chinês (tradicional) e chinês (simplificado). Um site da comunidade será criado para cada idioma adicionado e existirá na mesma pasta do site seguindo a melhor prática descrita em [Traduzindo conteúdo para sites multilíngues](../../help/sites-administering/translation.md). A página raiz de cada site conterá uma página secundária nomeada pelo código de idioma de um dos idiomas selecionados, como &quot;en&quot; para inglês ou &quot;fr&quot; para francês.

* **[!UICONTROL Nome do site da comunidade]**: `enable`

   * o URL inicial será exibido abaixo do Nome do site da comunidade
   * para um URL válido, acrescente um código de idioma base + &quot;.html&quot;

      *por exemplo*, http://localhost:4502/content/sites/  `enable/en.html`

* **[!UICONTROL Modelo]** de site de referência: menu suspenso para escolher  `Reference Structured Learning Site Template`

Selecione **[!UICONTROL Próximo]**

### Etapa 2: Design {#step-design}

A etapa de design é apresentada em duas seções para selecionar o tema e o banner de marca:

#### TEMA DO SITE DA COMUNIDADE {#community-site-theme}

Selecione o estilo desejado a ser aplicado ao modelo. Quando selecionado, o tema será sobreposto com uma marca de seleção.

![ativlementsitetema](assets/enablementsitetheme.png)

#### MARCA DO SITE DA COMUNIDADE {#community-site-branding}

(opcional) Faça upload de uma imagem de banner para ser exibida nas páginas do site. O banner é fixado na borda esquerda do navegador, entre o cabeçalho e o menu do site da comunidade (links de navegação). A altura do banner é cortada em 120 pixels. Não há redimensionamento do banner para ajustar à largura do navegador e à altura de 120 pixels.

![chlimage_1-284](assets/chlimage_1-284.png) ![chlimage_1](assets/chlimage_1.jpeg)

Selecione **[!UICONTROL Próximo]**.

### Etapa 3: Configurações {#step-settings}

Na etapa Configurações, antes de selecionar `Next`, observe que há sete seções fornecendo acesso às configurações que envolvem gerenciamento de usuários, marcação, funções, moderação, análise, tradução e ativação.

#### GERENCIAMENTO DE USUÁRIOS {#user-management}

Recomenda-se que [as comunidades de ativação](overview.md#enablement-community) sejam privadas.

Um site da comunidade é privado quando visitantes anônimos do site têm acesso negado, podem não se inscrever e podem não usar o login social.

Verifique se a maioria das caixas de seleção está desmarcada para [Gerenciamento de usuários](sites-console.md#user-management):

* NÃO permitir que os visitantes do site se registrem automaticamente
* NÃO permitir que visitantes anônimos do site visualizações
* Opcional se permite ou não mensagens entre membros da comunidade
* NÃO permitir logon com o Facebook
* NÃO permitir logon com o Twitter

![chlimage_1-285](assets/chlimage_1-285.png)

#### MARCANDO {#tagging}

As tags que podem ser aplicadas ao conteúdo da comunidade são controladas selecionando AEM namespaces previamente definidas por meio do [Console de marcação](../../help/sites-administering/tags.md#tagging-console) (como [namespace do tutorial](enablement-setup.md#create-tutorial-tags)).

Além disso, selecionar Namespaces de tags para o site da comunidade limita a seleção apresentada ao definir catálogos e recursos de ativação. Consulte [Marcando recursos de ativação](tag-resources.md) para obter informações importantes.

Encontrar namespaces é fácil usando a pesquisa antecipada por tipo. Por exemplo,

* Digite &#39;tut&#39;
* Selecionar `Tutorial`

![chlimage_1-286](assets/chlimage_1-286.png)

### ROLES {#roles}

[As ](users.md) funções dos membros da comunidade são atribuídas pelas configurações na seção Funções.

Para permitir que um membro da comunidade (ou grupo de membros) experimente o site como o gerente da comunidade, use a pesquisa de tipo antecipada e selecione o nome do membro ou grupo nas opções no menu suspenso.

Por exemplo,

* Digite &quot;q&quot;
* Selecione [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[O ](deploy-communities.md#tunnel-service-on-author) serviço de túnel permite a seleção de membros e grupos existentes apenas no ambiente publish.

![community_role](assets/community_roles.png)

#### MODERAÇÃO {#moderation}

Aceite as configurações globais padrão para [moderar](sites-console.md#moderation) conteúdo gerado pelo usuário (UGC).

![chlimage_1-287](assets/chlimage_1-287.png)

#### ANALYTICS {#analytics}

No menu suspenso, selecione a estrutura de serviço em nuvem do Analytics configurada para este site da comunidade.

A seleção vista na captura de tela, `Communities`, é o exemplo de estrutura da documentação de configuração [.](analytics.md#aem-analytics-framework-configuration)

![chlimage_1-288](assets/chlimage_1-288.png)

#### TRADUÇÃO {#translation}

As [Configurações de tradução](sites-console.md#translation) especificam se o UGC pode ou não ser traduzido e em qual idioma, se assim for.

* Marque **[!UICONTROL Permitir tradução automática]**
* Usar as configurações padrão

![chlimage_1-289](assets/chlimage_1-289.png)

#### ATIVAÇÃO {#enablement}

Para uma comunidade de ativação, é necessário identificar um ou mais Gerentes de habilitação da comunidade.

* **[!UICONTROL Gerentes]**
 de ativação (obrigatório) Membros do 
`Community Enablement Managers` estão disponíveis para serem selecionados para gerenciar este site da comunidade.

   * Digite &quot;s&quot;
   * Selecionar `Sirius Nilson`

* **[!UICONTROL ID]**
 de organização do Marketing Cloud (opcional) A ID de uma conta Adobe Analytics que é necessária ao incluir a  [Análise do Video Heartbeat ](analytics.md#video-heartbeat-analytics) no relatórios de ativação.

![chlimage_1-290](assets/chlimage_1-290.png)

Selecione **[!UICONTROL Próximo]**.

### Etapa 4: Criar site da comunidade {#step-create-community-site}

Selecione **[!UICONTROL Criar]**.

![chlimage_1-291](assets/chlimage_1-291.png)

Quando o processo for concluído, a pasta do novo site será exibida no console Comunidades - Sites.

![enablementsitecreated](assets/enablementsitecreated.png)

### Publicar o novo site da comunidade {#publish-the-new-community-site}

O site criado deve ser gerenciado a partir do console Comunidades - Sites, o mesmo console de onde os novos sites podem ser criados.

Depois de selecionar a pasta do site da comunidade, passe o mouse sobre o ícone do site para que quatro ícones de ação sejam exibidos:

![siteactionicons](assets/siteactionicons.png)

Ao selecionar o ícone de elipses (ícone Mais ações), as opções Exportar site e Excluir site aparecem.

![siteactionsnew](assets/siteactionsnew.png)

Da esquerda para a direita estão:

* **Abrir o**
SiteSelecione o ícone de lápis para abrir o site da comunidade no modo de edição do autor, para adicionar e/ou configurar os componentes da página

* **Editar**
siteSelecione o ícone de propriedades para abrir o site da comunidade para modificação de propriedades, como o título ou para alterar o tema

* **Publicar**
siteSelecione o ícone do mundo para publicar o site da comunidade (para localhost:4503 por padrão)

* **Exportar**
siteSelecione o ícone de exportação para criar um pacote do site da comunidade que esteja armazenado no  [gerenciador de ](../../help/sites-administering/package-manager.md) pacotes e baixado.

   Observe que o UGC não está incluído no pacote do site.

* **Excluir**
sitePara excluir o site da comunidade, selecione o ícone Excluir site exibido ao passar o mouse sobre o site no Console do site das Comunidades. Esta ação remove todos os itens associados ao site, como UGC, grupos de usuários, ativos e registros de banco de dados.

![ativesiteactions](assets/enablesiteactions.png)

#### Selecione Publicar {#select-publish}

Selecione o ícone do mundo para publicar o site da comunidade.

![chlimage_1-292](assets/chlimage_1-292.png)

Haverá uma indicação de que o site foi publicado.

![chlimage_1-293](assets/chlimage_1-293.png)

## Usuários da comunidade e grupos de usuários {#community-users-user-groups}

### Aviso aos novos grupos de usuários da comunidade {#notice-new-community-user-groups}

Juntamente com o novo site da comunidade, novos grupos de usuários são criados, que têm as permissões apropriadas definidas para várias funções administrativas. Para obter detalhes, visite [Grupos de usuários para sites da comunidade](users.md#usergroupsforcommunitysites).

Para este novo site da comunidade, dado o nome do site &quot;enable&quot; na Etapa 1, os novos grupos de usuários que existem no ambiente de publicação podem ser vistos no [console Membros e grupos das Comunidades](members.md#groups-console):

![chlimage_1-294](assets/chlimage_1-294.png)

### Atribuir membros ao grupo Habilitar membros da comunidade {#assign-members-to-community-enable-members-group}

Em autor, com o serviço de túnel ativado, é possível atribuir [usuários criados durante a Configuração Inicial](enablement-setup.md#publishcreateenablementmembers) ao grupo Membros da Comunidade para o site da comunidade recém-criado.

Usando o console Grupos da comunidade, os membros podem ser adicionados individualmente ou adicionados por meio da associação em um grupo.

Neste exemplo, o grupo `Community Ski Class` é adicionado como membro do grupo `Community Enable Members`, bem como membro `Quinn Harper`.

* Navegue até o console **[!UICONTROL Comunidades > Grupos]**
* Selecione o grupo **[!UICONTROL Membros habilitados da comunidade]**
* Digite `ski` na caixa de pesquisa **[!UICONTROL Adicionar membros ao grupo]**
* Selecione **[!UICONTROL Classe de Esqui da Comunidade]** (grupo de alunos)
* Digite `quinn` na caixa de pesquisa
* Selecione **[!UICONTROL Quinn Harper]** (ativação do contato de recursos)

* Selecione **[!UICONTROL Salvar]**

![chlimage_1-295](assets/chlimage_1-295.png)

## Configurações em Publicar {#configurations-on-publish}

### http://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}

![chlimage_1-296](assets/chlimage_1-296.png)

### Configurar para erro de autenticação {#configure-for-authentication-error}

Depois que um site é configurado e enviado para publicação, [configure o mapeamento de logon](sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) na instância de publicação. O benefício é que quando as credenciais de logon não forem inseridas corretamente, o erro de autenticação exibirá novamente a página de logon do site da comunidade com uma mensagem de erro.

Adicionar um `Login Page Mapping` como

* /content/sites/enable/en/sign:/content/sites/enable/en

### (Opcional) Alterar o Home page padrão {#optional-change-the-default-home-page}

Ao trabalhar com o site de publicação para fins de demonstração, pode ser útil alterar o home page padrão para o novo site.

Para fazer isso, é necessário usar [CRX|DE](http://localhost:4503/crx/de) Lite para editar a tabela [mapeamento de recursos](../../help/sites-deploying/resource-mapping.md) na publicação.

Para começar

1. Ao publicar, acesse o CRXDE e faça logon com privilégios de administrador

   * Por exemplo, navegue até [http://localhost:4503/crx/de](http://localhost:4503/crx/de) e faça logon com `admin/admin`

1. No navegador do projeto, expanda `/etc/map`
1. Selecione o nó `http`

   * Selecione **[!UICONTROL Criar Nó]**

      * **** Namelocalhost.4503

         (Não *utilize* `:`)

      * **** [Digitação:Mapeamento](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Com o nó `localhost.4503` recém-criado selecionado

   * Adicionar propriedade

      * **** Nomeação:correspondência
      * **** TypeString
      * **** Valuelocalhost.4503/\$

         (Deve terminar com o caractere &#39;$&#39;)
   * Adicionar propriedade

      * **** Nomeação:internalRedirect
      * **** TypeString
      * **Valor** /content/sites/enable/en.html


1. Selecione **[!UICONTROL Salvar tudo]**
1. (opcional) Excluir o histórico de navegação
1. Navegue até http://localhost:4503/

   * Chegar em http://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Para desativar, basta anexar o valor da propriedade `sling:match` a um valor &#39;x&#39; - `xlocalhost.4503/$` - e **[!UICONTROL Salvar tudo]**.

![chlimage_1-297](assets/chlimage_1-297.png)

#### Solução de problemas: Erro ao salvar mapa {#troubleshooting-error-saving-map}

Se não for possível salvar as alterações, verifique se o nome do nó é `localhost.4503`, com um separador &#39;dot&#39; e não `localhost:4503` com um separador &#39;colon&#39;, pois `localhost`não é um prefixo de namespace válido.

![chlimage_1-298](assets/chlimage_1-298.png)

#### Solução de problemas: Falha ao redirecionar {#troubleshooting-fail-to-redirect}

A string &#39;**$**&#39; no final da expressão regular `sling:match`é crucial, de modo que apenas `http://localhost:4503/` seja mapeado, caso contrário, o valor de redirecionamento será anexado a qualquer caminho que possa existir após server:port no URL. Dessa forma, quando AEM tentar redirecionar para a página de logon, isso falhará.

## Modificando o Site da Comunidade {#modifying-the-community-site}

Após a criação inicial do site, os autores podem usar o [ícone Abrir site](sites-console.md#authoring-site-content) para executar atividades de criação padrão AEM.

Além disso, os administradores podem usar o [ícone Editar site](sites-console.md#modifying-site-properties) para modificar as propriedades do site, como o título.

Depois de qualquer modificação, lembre-se de **Salvar** e recrie **Publicar** o site.

>[!NOTE]
>
>Se não estiver familiarizado com o AEM, visualização a documentação em [manuseio básico](../../help/sites-authoring/basic-handling.md) e um [guia rápido para criar páginas](../../help/sites-authoring/qg-page-authoring.md).

### Adicionar um catálogo {#add-a-catalog}

O modelo de site da comunidade escolhido para este site da comunidade deve conter o recurso de catálogo.

Caso contrário, a função de catálogo pode ser facilmente adicionada. Isso permitiria que outros membros da comunidade, não atribuídos a recursos de ativação ou a um caminho de aprendizado, selecionassem recursos de ativação de um catálogo.

Se a estrutura do site já contiver o recurso de catálogo, seu Título poderá ser alterado.

Para modificar a estrutura do site, navegue até o console **[!UICONTROL Communities, Sites]**, abra a pasta `enable` e selecione o ícone **Editar site** para acessar as propriedades de `Enablement Tutorial`.

Selecione o painel ESTRUTURA para adicionar um catálogo ou modificar um catálogo existente:

* **Título**: `Ski Catalog`

* **URL**: `catalog`

* **Selecione Todas as Namespaces**: deixe como padrão.
* Selecione **[!UICONTROL Salvar]**

![chlimage_1-299](assets/chlimage_1-299.png)

Use o ícone Posição para mover a função Catálogo para a segunda posição, após Atribuições.

![chlimage_1-300](assets/chlimage_1-300.png)

Selecione **[!UICONTROL Salvar]** no canto superior direito para salvar as alterações no site da comunidade.

Em seguida, recrie o site **Publish**.