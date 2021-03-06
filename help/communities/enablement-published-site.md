---
title: Experimente o site publicado
seo-title: Experimente o site publicado
description: Navegue até um site publicado para ativar
seo-description: Navegue até um site publicado para ativar
uuid: 1bfefa8a-fd9c-4ca8-b2ff-add79776c8ae
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 26715b94-e2ea-4da7-a0e2-3e5a367ac1cd
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 1%

---



# Experimente o site publicado {#experience-the-published-site}


**[⇐ Criar e atribuir recursos de habilitação](resource.md)**

## Navegue até Novo site na publicação {#browse-to-new-site-on-publish}

Agora que o site da comunidade recém-criado e seus recursos de ativação e caminho de aprendizado foram publicados, é possível experimentar o site Tutorial de ativação.

Comece navegando até o URL exibido ao criar o site, mas no servidor de publicação, por exemplo

* URL do autor = [http://localhost:4502/content/sites/enable/en.html](http://localhost:4502/content/sites/enable/en.html)
* URL de publicação = [http://localhost:4503/content/sites/enable/en.html](http://localhost:4503/content/sites/enable/en.html)

Se o home page padrão [estiver definido](enablement-create-site.md#changethedefaulthomepage), basta navegar para [http://localhost:4503/](http://localhost:4503/) iniciar o site.

Ao chegar ao site publicado pela primeira vez, o visitante do site normalmente não estaria conectado e seria anônimo.

**http://localhost:4503/content/sites/enable/en.html**

![chlimage_1-433](assets/chlimage_1-433.png)

## Visitante de site anônimo {#anonymous-site-visitor}

Um visitante de site anônimo é imediatamente apresentado com a página de logon deste site privado da comunidade de ativação. Observe que não há nenhuma opção para se registrar automaticamente nem fazer login no Facebook ou Twitter.

Observe que este home page mostra quatro itens de menu: `Assignments, Ski Catalog, What's New` e `Discussions`, mas nenhum pode ser alcançado sem fazer logon.

>[!NOTE]
>
>É possível conceder acesso anônimo a um site de ativação sem permitir que os visitantes do site se registrem automaticamente.\
>Se um recurso de ativação estiver definido como `show in catalog` e `allow anonymous access`, será possível que visitantes anônimos do site visualizações recursos no catálogo.

### Impedir acesso anônimo no JCR {#prevent-anonymous-access-on-jcr}

Uma limitação conhecida expõe o conteúdo do site da comunidade a visitantes anônimos por meio de conteúdo jcr e json , embora **[!UICONTROL permita acesso anônimo]** esteja desabilitado para o conteúdo do site. No entanto, esse comportamento pode ser controlado usando Restrições de Sling como uma solução alternativa.

Para proteger o conteúdo do site da sua comunidade do acesso de usuários anônimos por meio de conteúdo jcr e json , siga estas etapas:

1. Na instância do autor de AEM, vá para https://&lt;host>:&lt;porta>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Não vá para o site localizado.

1. Vá para **[!UICONTROL Propriedades da página]**.

   ![page-properties-1](assets/page-properties-1.png)

1. Vá para a guia **[!UICONTROL Avançado]**.
1. Ative **[!UICONTROL Requisito de autenticação]**.

   ![site-authentication-1](assets/site-authentication-1.png)

1. Adicione o caminho da página de logon. Por exemplo, `/content/......./GetStarted`.
1. Publique a página.

## Membro inscrito {#enrolled-member}

Esta experiência depende de os usuários `Riley Taylor` e `Sidney Croft` serem [criados](enablement-setup.md#publishcreateenablementmembers) e [atribuídos](resource.md#settings) ao caminho de aprendizagem *Leções de Esqui* através da sua associação ao grupo *Classe de Esqui da Comunidade*.

Logon com

* `Username: riley`
* `Password: password`

Se o perfil do usuário não tiver sido criado por meio de autoinscrição, na primeira vez que um membro fizer logon, sua página do Perfil será exibida para que possa ser verificada e modificada conforme necessário.

Na próxima vez que o membro entrar, o home page, identificado pelo primeiro item do menu, será exibido.

![chlimage_1-434](assets/chlimage_1-434.png)

### Atribuições {#assignments}

A página Atribuições é onde o membro é mostrado para todos os caminhos de aprendizado e recursos de ativação atribuídos especificamente a ele.

Cada atribuição fornece informações básicas sobre

* O tipo de Atribuição
* Se é uma nova Atribuição
* O nome
* Detalhes relevantes para o tipo de atribuição
* Contato de atribuição, especialista e autor (se fornecido)

O tipo de Atribuição é indicado por um ícone no canto superior esquerdo do cartão. A imagem de uma estrada é para um caminho de aprendizagem com o número de recursos de ativação incluídos.

![chlimage_1-435](assets/chlimage_1-435.png)

Selecionar *Lições de esqui* exibirá os dois recursos de ativação referenciados pelo caminho de aprendizado.

![chlimage_1-436](assets/chlimage_1-436.png)

Selecionar *Lição de esqui 1* abrirá a página de detalhes do recurso de ativação.

Na página de detalhes, o membro pode aprender [classificar](rating.md) a lição e adicionar [comentários](comments.md). Qualquer atividade de membro será refletida na seção Novidades do site.

As interações com o recurso de ativação serão anotadas na seção Relatório, acessível no ambiente do autor.

![chlimage_1-437](assets/chlimage_1-437.png)

### Catálogo de esqui {#ski-catalog}

A página Catálogo de esqui é o catálogo de recursos de ativação marcados com tags da namespace `Tutorial`. Os dois recursos *Lição de esqui* são marcados com a tag `Skiing`, de modo que, se qualquer tag diferente de `All` ou `Tutorial: Sports / Skiing` for selecionada, nada será exibido.

Quando os recursos de ativação não foram atribuídos a um membro, diretamente ou por meio de um caminho de aprendizado, é possível interagir com os recursos de ativação localizados em um catálogo e fornecer feedback por meio de comentários e classificações.

![chlimage_1-438](assets/chlimage_1-438.png)

### Debates {#discussions}

Além de classificar e comentar sobre recursos de ativação ([quando ativado](enablement-create-site.md#step33asettings)), o modelo de site da comunidade a partir do qual `Enablement Tutorial` foi criado inclui a [função do fórum](functions.md#forum-function) (o título é `Discussions)`.

Selecione o link `Discussions`e poste um tópico.

Faça logout e login como Sidney Croft (lateral/senha) e responda à pergunta, bem como Siga o tópico.

Observe que, além da moderação em linha, há opções para compartilhar o tópico nas redes sociais ou para enviar o tópico por email.

![chlimage_1-439](assets/chlimage_1-439.png)

### Novidades {#what-s-new}

O item de menu `What's New` é o título dado à [função de fluxo de atividade](functions.md#activity-stream-function) na estrutura deste site da comunidade.

Ainda conectado como Sidney, selecione o link `What's New` para mostrar a atividade.

![chlimage_1-440](assets/chlimage_1-440.png)

## Membro da comunidade confiável {#trusted-community-member}

Essa experiência supõe que ` [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)` recebeu as funções de [moderador](enablement-create-site.md#moderation) e [contato de recursos](resource.md#settings).

Logon com

* `Username: quinn`
* `Password: password`

Depois de conectado, observe que há um novo item de menu, `Administration`, que é exibido porque o membro recebeu a função de moderador.

![chlimage_1-441](assets/chlimage_1-441.png)

O home page é identificado pelo primeiro item de menu, Atribuições. Quinn é o contato de recursos de moderador e ativação e não estava inscrito em nenhum recurso de ativação ou caminhos de aprendizado, portanto não há nada para exibir.

### Administração {#administration}

O que há, é atividade pelos dois alunos, `Riley Taylor` e `Sidney Croft. By s`ao selecionar o link `Administration`para acessar o console de moderação, o Quinn é capaz de usar o [console de moderação em massa](moderation.md) para moderar suas publicações.

Selecionar o ícone do painel lateral alterna para abrir os filtros usados para pesquisar o conteúdo da comunidade.

Passar o mouse sobre um cartão de comentários exibe ações de moderação.

![chlimage_1-442](assets/chlimage_1-442.png)

## Relatórios sobre o autor {#reports-on-author}

Há duas maneiras de acessar o relatórios nos alunos e os recursos de ativação.

No autor, navegue até **Communities, [Resources console](resources.md)**, onde os recursos de ativação são gerenciados, e depois de selecionar um site da comunidade, é possível gerar relatórios para

* Todos os recursos de ativação e caminhos de aprendizado
* Um recurso de ativação ou caminho de aprendizado específico

Navegue até **Comunidades, [console Relatórios](reports.md)** e gere relatórios de acordo com

* Atribuições para ativar recursos e caminhos de aprendizado
* Postagens em um site da comunidade durante um período específico
* Visualizações (visitas ao site) de um site da comunidade durante um período específico

* As postagens e visualizações podem ser para todo o conteúdo ou para conteúdo específico:

   * Fórum
   * Tópico do fórum
   * Perguntas e respostas
   * Perguntas QnA
   * Blog
   * Artigo do blog
   * Calendário
   * Evento do calendário

### Console de recursos {#resources-console}

Com uma certa atividade e interação com os Recursos na publicação, a exibição dos relatórios do autor vale a pena.

* Sobre o autor
* Fazer logon com privilégios administrativos
* Navegue do menu principal até **[!UICONTROL Comunidades > Recursos]**
* Selecione o site `Enablement Tutorial`
* Selecione o ícone `Report`para obter um resumo de todos os Recursos
* Selecione um Recurso e, em seguida, o ícone `Report`para um relatório sobre esse Recurso

Observe que provavelmente é muito cedo para mostrar dados da Adobe Analytics, que podem levar de 1 a 12 horas para serem exibidos. No entanto, o relatórios SCORM básico já está disponível.

#### Relatório de recursos de lições de esqui {#ski-lessons-resource-report}

![chlimage_1-443](assets/chlimage_1-443.png)

#### Relatório do usuário de lições de esqui {#ski-lessons-user-report}

* Selecione **[!UICONTROL Comunidades > Recursos]**

* Abrir cartão `Enablement Tutorial`
* Abrir cartão `Ski Lessons`
* `select Report, User Report`

![chlimage_1-444](assets/chlimage_1-444.png)

### Console de relatórios {#reports-console}

O console Relatórios permite a geração de relatórios em

* **Atribuições** para qualquer site de comunidade de ativação
* **** Visualizações para qualquer site da comunidade
* **** Postagens para qualquer site da comunidade

Para relatórios em atribuições:

* Sobre o autor
* Fazer logon com privilégios administrativos
* Navegue até **[!UICONTROL Comunidades > Relatórios > Relatório de atribuições]**
* Selecione um **[!UICONTROL Site]** no menu suspenso (selecione `Enablement Tutorial`)

* Selecione **[!UICONTROL Grupo]** (selecione `Community Ski Class`)

* Selecione um **[!UICONTROL Atribuição]** (selecione `Ski Lessons`)

* Selecione **[!UICONTROL Gerar]**

![chlimage_1-445](assets/chlimage_1-445.png)

Para relatórios sobre visualizações:

* Sobre o autor
* Fazer logon com privilégios administrativos
* Navegue até **[!UICONTROL Comunidades > Relatórios > Relatório do Visualização]**
* Selecione um **[!UICONTROL Site]** no menu suspenso (selecione `Enablement Tutorial`)

* Selecione **[!UICONTROL Tipo de Conteúdo]** (selecione `all`)

* Selecione um **[!UICONTROL intervalo de datas]** (selecione `Last 7 days`)

* Selecione **[!UICONTROL Gerar]**

![chlimage_1-446](assets/chlimage_1-446.png)

**[⇐ Criar e atribuir recursos de habilitação](resource.md)**
