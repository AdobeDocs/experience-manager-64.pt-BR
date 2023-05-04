---
title: Experimente o site publicado
seo-title: Experience the Published Site
description: Navegue até um site publicado
seo-description: Browse to a published site
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
exl-id: 8f716a59-1116-4855-baeb-3997de71b55f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 1%

---

# Experimente o site publicado {#experience-the-published-site}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Navegue até o novo site na publicação {#browse-to-new-site-on-publish}

Agora que o site de comunidades recém-criado foi publicado, navegue até o URL exibido ao criar o site, mas no servidor de publicação, por exemplo

* URL do autor = http://localhost:4502/content/sites/engage/en.html
* URL de publicação = http://localhost:4503/content/sites/engage/en.html

Para minimizar a confusão sobre qual membro está conectado ao autor e à publicação, sugerimos usar navegadores diferentes para cada instância.

Ao chegar pela primeira vez ao site publicado, o visitante do site normalmente não estaria conectado e seria anônimo.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## Visitante Anônimo do Site {#anonymous-site-visitor}

Um visitante anônimo do site vê o seguinte na interface do usuário:

* Título do site. Tutorial de introdução
* Nenhum link de perfil
* Sem link de mensagens
* Sem link de notificações
* Campo de pesquisa
* Link de logon
* O banner da marca
* Links de menu para os componentes incluídos no Modelo de site de referência

Se você selecionar vários links, eles estarão no modo somente leitura.

## Impedir acesso anônimo no JCR {#prevent-anonymous-access-on-jcr}

Uma limitação conhecida expõe o conteúdo do site da comunidade para visitantes anônimos por meio de conteúdo jcr e json , embora **permitir acesso anônimo** está desativado para o conteúdo do site. No entanto, esse comportamento pode ser controlado usando Restrições do Sling como uma solução alternativa.

Para proteger o conteúdo do site da comunidade do acesso de usuários anônimos por meio de conteúdo jcr e json , siga estas etapas:

1. Na instância do autor do AEM, acesse https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Não vá para o site localizado.

1. Ir para **[!UICONTROL Propriedades da página]**.

   ![autenticação de site](assets/site-authentication.png)

1. Ir para **[!UICONTROL Avançado]** guia .

   ![propriedades de página](assets/page-properties.png)

1. Habilitar **[!UICONTROL Requisito de autenticação]**.
1. Adicione o caminho da página de logon. Por exemplo, `/content/......./GetStarted`.
1. Publique a página.

## Membro da Comunidade Confiável {#trusted-community-member}

Essa experiência assume [Aaron McDonald](tutorials.md#demo-users) recebeu as funções de [gerente e moderador da comunidade](create-site.md#roles). Caso contrário, retorne ao ambiente de criação para [modificar as configurações do site](sites-console.md#modifying-site-properties) e selecione Aaron McDonald como gerente da comunidade e moderador.

No canto superior direito, selecione `Log in`e assine com o nome de usuário &quot;aaron.mcdonald@mailinator.com&quot; e senha &quot;senha&quot;. Observe a capacidade de fazer logon com credenciais do Twitter ou Facebook.

![chlimage_1-312](assets/chlimage_1-312.png)

Depois de entrar, observe que há um novo item de menu, `Administration`, que aparece porque o membro recebeu a função de Moderador. Agora, selecionar vários links é mais interessante.

![chlimage_1-313](assets/chlimage_1-313.png)

Observe que a página Calendário é a página inicial, pois o Modelo de site de referência escolhido incluiu a função Calendário primeiro, seguido pela função Fluxo de atividade, função do Fórum e assim por diante. Essa estrutura é visível do [Modelo do site](sites.md#edit-site-template) ou ao modificar as propriedades do site no ambiente do autor:

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Para obter mais informações sobre componentes e funções do Communities, visite
>
>* [Componentes das comunidades](author-communities.md) (para autores)
>* [Componentes, funções e recursos essenciais](essentials.md) (para desenvolvedores)
>


## Link do fórum {#forum-link}

Visualize o recurso básico do fórum selecionando o link Forum .

Os membros podem postar um novo tópico ou seguir um tópico.

Os visitantes do site podem visualizar postagens e classificá-las de várias maneiras.

![chlimage_1-315](assets/chlimage_1-315.png)

## Link Grupos {#groups-link}

Como Aaron é um administrador de grupo, selecionar o link Grupos permitirá que Aaron crie um novo grupo da comunidade selecionando um modelo de grupo, uma imagem, se o grupo está aberto ou secreto e convidando membros.

Este é um exemplo em que um grupo é criado no ambiente de publicação.

Os grupos também podem ser criados no ambiente de criação e gerenciados no site da comunidade no ambiente de criação (o [Console de grupos da comunidade](groups.md)). A experiência de [criação de grupos no autor](nested-groups.md) é o próximo neste tutorial.

![chlimage_1-316](assets/chlimage_1-316.png)

Criar um grupo de referência:

1. Selecionar **[!UICONTROL Novo grupo]**
1. **[!UICONTROL Guia Configurações]**
   * Nome do grupo: `Sports`
   * Descrição: `A parent group for various sporting groups`
   * Nome do URL do grupo: `sports`
   * select `Open Group` (permitir a participação de qualquer membro da comunidade através da sua adesão)
1. **[!UICONTROL Guia Modelo]**
   * Selecionar `Reference Group` (contém uma função de grupos em sua estrutura para permitir grupos aninhados)
1. Selecionar **[!UICONTROL Criar grupo]**

![chlimage_1-317](assets/chlimage_1-317.png)

Após a criação de um novo grupo, **selecione o novo grupo Esportes** para criar dois grupos (aninhados) dentro dele. Como uma estrutura de site não pode começar com a função de grupos , após abrir o grupo Esportes, é necessário selecionar o link Grupos :

![chlimage_1-318](assets/chlimage_1-318.png)

O segundo conjunto de links, começando com `Blog`pertencer ao grupo selecionado no momento, a variável `Sports`grupo. Selecionando os Esportes `Groups` link , é possível aninhar dois grupos no grupo Esportes .

Como exemplo, adicione dois n `ew groups.`

* Um nome `Baseball`
   * Deixe-a configurada como uma `Open Group` (associação obrigatória)
   * Na guia Modelos , selecione `Conversational Group`
* Um nome `Gymnastics`
   * Alterar a configuração para `Member Only Group` (associação restrita)
   * Na guia Modelos , selecione `Conversational Group`

**Aviso**:

* Uma atualização da página pode ser necessária antes que ambos os grupos sejam exibidos
* Esse modelo *não *inclui a função de grupos, portanto, nenhum aninhamento adicional de grupos será possível
* No autor, o [Console Grupos](groups.md) fornece uma terceira opção - uma `Public Group` (associação opcional)

Depois que ambos os grupos forem criados, selecione o grupo Beisebol, um grupo aberto e observe seus links: `Discussions` `What's New` `Members`
Os links do grupo são exibidos abaixo dos links do site principal e resultam na seguinte exibição:

![chlimage_1-319](assets/chlimage_1-319.png)

Ao criar - com privilégios administrativos, navegue até o [Console de grupos de comunidades](members.md) e adicione Weston McCall ao `Community Engage Gymnastics <uid> Members` grupo.

Continuando a publicar, saia como Aaron McDonald e veja os grupos no Sports Group como um visitante anônimo do site:

* Da página inicial
* Selecionar `Groups`link
* Selecionar `Sports`link
* Selecionar os Esportes&#39; `Groups`link

Somente o grupo Beisebol será visível.

Faça logon como Weston McCall (weston.mccall@dodgit.com / senha) e navegue até o mesmo local. Observe que o Weston é capaz de `Join` abrir `Baseball` e `enter or Leave` privado `Gymnastics`grupo.

![chlimage_1-320](assets/chlimage_1-320.png)

## Link da página da Web {#web-page-link}

Visualize a página da Web básica incluída no site selecionando o link Página da Web. As ferramentas de criação de AEM padrão podem ser usadas para adicionar conteúdo a esta página no ambiente de criação.

Por exemplo, acesse **autor** , abra o `engage` na pasta [Console de sites das comunidades](sites-console.md), selecione o **Abrir Site** ícone para entrar no modo de edição do autor. Em seguida, selecione o modo de visualização para selecionar o `Web Page`e, em seguida, selecione o modo de edição para adicionar componentes Título e Texto . Por último, publique novamente apenas a página ou o site inteiro.

![chlimage_1-321](assets/chlimage_1-321.png)

## Link de administração {#administration-link}

Quando o membro da comunidade tiver privilégios de moderação, o link Administração ficará visível e a seleção exibirá o conteúdo da comunidade publicado e permitirá que ele seja [moderado](moderate-ugc.md) de forma semelhante à [console de moderação](moderation.md) no ambiente de criação.

Use o botão Voltar do navegador para retornar ao site publicado. A maioria dos consoles não é acessível a partir da navegação global no ambiente de publicação.

![chlimage_1-322](assets/chlimage_1-322.png)

## Autoregistro {#self-registration}

Depois de fazer logoff, é possível criar um novo registro de usuário.

* Selecionar `Log In`
* Selecionar `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

Por padrão, o endereço de email é a id de logon. Se estiver desmarcado, o visitante poderá inserir sua própria ID de logon (nome de usuário). O nome de usuário deve ser exclusivo no ambiente de publicação.

Após especificar o nome do usuário, email e senha, selecione `Sign Up`O criará o usuário e permitirá que ele assine.

Depois de conectado, a primeira página apresentada é sua `Profile`, que podem personalizar.

![chlimage_1-325](assets/chlimage_1-325.png)

Se o membro esquecer a id de logon, será possível recuperar o usando seu endereço de email.

![chlimage_1-326](assets/chlimage_1-326.png)
