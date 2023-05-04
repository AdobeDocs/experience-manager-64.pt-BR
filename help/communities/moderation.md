---
title: Console de moderação
seo-title: Moderation Console
description: Como acessar o console Moderação
seo-description: How to access the Moderation console
uuid: 920124b9-af6f-4622-adb6-b8e294c5607d
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6c405543-e339-4916-aa0f-b61d0b798cf3
role: Admin
exl-id: ded38cee-fbce-46cc-974f-38d3a293a55d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 4%

---

# Console de moderação {#moderation-console}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

No AEM Communities, em massa [moderação do conteúdo da comunidade](moderate-ugc.md) O é possível nos ambientes de criação e publicação por administradores e moderadores da comunidade (membros confiáveis da comunidade atribuídos como moderadores).

Os administradores e os moderadores da comunidade também podem executar [moderação no contexto](in-context.md) no ambiente de publicação.

Um recurso de todos [sites da comunidade](sites-console.md) é um `Administration`item de menu disponível para usuários que fazem logon com privilégios administrativos. O `Administration`fornece acesso ao console Moderação .

No console Moderação, os administradores e os moderadores da comunidade terão acesso a todo o conteúdo gerado pelo usuário (UGC) para o qual têm permissão para moderar. Se for permitido moderar vários sites, é possível visualizar postagens em todos os sites ou filtrar por sites de comunidades selecionadas.

Para obter informações mais detalhadas, visite [Gerenciar usuários e grupos de usuários](users.md).

O console Moderação é compatível com:
* Execução de tarefas de moderação em massa
* Pesquisar UGC
* Visualização de detalhes do UGC
* Visualização de detalhes do autor do UGC

Somente quando conectado como administrador ou como um membro com ` [moderator permissions](in-context.md#identifyingtrustedmembers)`, podem ser realizadas tarefas de moderação.

## Publicar acesso ao ambiente {#publish-environment-access}

O acesso ao console Moderação de um site da comunidade publicado é feito por meio de um link de Administração que é exibido quando um moderador da comunidade é conectado.

![publishweretail](assets/publishweretail.png)

Ao selecionar o link Administração , o console Moderação é exibido:

![moderationconsole-publish](assets/moderationconsole-publish.png)

## Acesso ao ambiente do autor {#author-environment-access}

No ambiente de criação, para acessar o console Moderação

* Na navegação global: **[!UICONTROL Navegação > Comunidades > Moderação]**

Somente quando conectado como administrador ou como membro com ` [moderator permissions](in-context.md#identifyingtrustedmembers)`, podem ser realizadas tarefas de moderação. O único conteúdo da comunidade exibido é aquele que o membro conectado tem permissão para moderar.

>[!NOTE]
>
>O UGC do ambiente de publicação só será visível no autor se o SRP escolhido implementar uma loja comum. Por exemplo, por padrão, o armazenamento é o JSRP, que não é um armazenamento comum para autor e publicação. Consulte [Armazenamento de conteúdo da comunidade](working-with-srp.md).

![moderationconsoleauthor](assets/moderationconsoleauthor.png)

## Interface do usuário do console de moderação {#moderation-console-ui}

Além do painel de navegação esquerdo (que aparece no autor, mas não na publicação), a interface do usuário de moderação tem as seguintes áreas principais:

* **[Barra de navegação superior](#top-navigation-bar)**
* **[Barra de ferramentas](#toolbar)**
* **[Área de conteúdo](#content-area)**

### Barra de navegação superior {#top-navigation-bar}

A barra de navegação superior é constante para todos os consoles. Para obter mais informações, consulte [Manuseio básico](../../help/sites-authoring/basic-handling.md).

### Barra de ferramentas {#toolbar}

A barra de ferramentas, localizada abaixo da barra de navegação superior, fornece o seguinte switch de alternância no lado esquerdo:

* [Filtrar painel](moderation.md#filter-rail) abre um painel que permite escolher as propriedades nas quais filtrar o conteúdo.

A barra de ferramentas, localizada abaixo da barra de navegação superior, fornece o seguinte switch de alternância no lado esquerdo:

![toggleswitch](assets/toggleswitch.png)

[Filtrar painel](moderation.md#filter-rail)\
Abre um painel, ao selecionar Pesquisa, que permite escolher as propriedades nas quais filtrar o conteúdo.

![filterral](assets/filterrail.png)

### Área de conteúdo {#content-area}

A área de conteúdo contém informações para o UGC publicado:

* O UGC publicado
* Nome do membro
* Avatar do membro
* Localização do lugar
* Quando foi postado
* Número de respostas à publicação
* [Sentimento](moderate-ugc.md#sentiment) associado à publicação
* Se aprovada, uma marca de seleção é exibida
* Se houver um anexo, um clipe de papel será exibido

>[!NOTE]
>
>A área de conteúdo apresenta uma *rolagem infinita*, o que significa que permitirá continuar a rolagem até atingir o fim do conteúdo. A barra de ferramentas permanece em uma posição fixa e visível acima da área de conteúdo, mesmo durante a rolagem.

### Filtrar painel {#filter-rail}

![chlimage_1-472](assets/chlimage_1-472.png)

O ícone do painel lateral abre o painel filtro. O painel de filtro, que aparece à esquerda da área de conteúdo, fornece filtros diferentes, cada um com um efeito imediato no UGC referenciado que aparece na área de conteúdo.

Os filtros em cada categoria são **OU** ed juntos e os filtros em categorias diferentes são **E** riz.

Por exemplo, se você marcar ambos **Pergunta** e **Resposta**, você verá um conteúdo que é um **Pergunta** *ou* um **Resposta**.

No entanto, se você marcar **Pergunta** e **Pending**, você verá somente o conteúdo que é um **Pergunta** e **Pending**.

>[!NOTE]
>
>Os moderadores da comunidade podem marcar os filtros predefinidos na interface do usuário do console de moderação. Como esses filtros são anexados ao final do URL (como parâmetros de cadeias de caracteres de consulta), os moderadores podem retornar aos filtros marcados posteriormente e também compartilhar esses links.

![searchicon](assets/searchicon.png)

Quando o painel de filtro estiver aberto, o ícone Pesquisar alterna o painel lateral para fechado. No entanto, para fechar o painel de filtros e exibir somente o conteúdo gerado pelo usuário, clique no ícone Pesquisar e selecione a opção Somente conteúdo .

#### Caminho do conteúdo {#content-path}

O Caminho do conteúdo limita o UGC de referência exibido nas publicações colocadas no repositório de conteúdo especificado.

![caminho do conteúdo](assets/content-path.png)

#### Pesquisa de texto {#text-search}

A pesquisa de texto limita o UGC referenciado exibido em publicações nas quais o texto foi inserido.

![chlimage_1-473](assets/chlimage_1-473.png)

#### Site {#site}

O site limita o UGC referenciado exibido para postagens em sites da comunidade selecionados. Se nenhum site estiver marcado, então todas as referências ao UGC serão exibidas.

![chlimage_1-474](assets/chlimage_1-474.png)

>[!NOTE]
>
>Quando o console de moderação em massa é acessado por um administrador, todas as referências ao UGC são mostradas, incluindo sites não criados com o [assistente de criação de sites](sites-console.md), como as amostras de Geometrixx.
>
>Quando o console de moderação em massa é acessado ao publicar por um membro da comunidade confiável, somente as referências ao UGC criado para sites da comunidade que o membro está autorizado a moderar são mostradas e podem ser filtradas com o filtro Site .

#### Tipo de conteúdo {#content-type}

O Tipo de conteúdo limita o UGC referenciado exibido para postagens do tipo de recurso selecionado. Um ou mais dos seguintes tipos podem ser selecionados. Todos os tipos são mostrados se nenhum estiver selecionado.

* **Comentar**
* **Tópico do fórum**
* **Resposta do fórum**
* **Perguntas QnA**
* **Resposta QnA**
* **Artigo do blog**
* **Comentário do blog**
* **Evento do calendário**
* **Comentário do calendário**
* **Pasta da biblioteca de arquivos**
* **Documento da biblioteca de arquivos**
* **Ideia**
* **Comentário da ideação**

![tipos de conteúdo](assets/content-types.png)

#### Tipos de conteúdo adicionais {#additional-content-types}

Para adicionar recursos adicionais sobre os quais filtrar:

* Em uma instância do autor
* Fazer logon como administrador
* Abrir [Console da Web](http://localhost:4502/system/console/configMgr)
* Localizar `AEM Communities Moderation Dashboard Filters`
* Selecione a configuração a ser aberta no modo de edição
* Insira o ResourceType de um componente no qual filtrar
   * Por exemplo, para filtrar nos componentes de Votação incluídos, insira:\
      `Voting=social/tally/components/hbs/voting`

![chlimage_1-475](assets/chlimage_1-475.png)

* Selecione Salvar
* Atualizar as Comunidades - Console de moderação

O resultado é um novo filtro selecionável para `Voting`nos termos do `Content Type` grupo de filtros.

Quando esse filtro for selecionado, o conteúdo do painel mostrará o UGC que corresponde a qualquer um dos ResourceTypes inseridos.

#### Status {#status}

O Status limita o UGC referenciado exibido em postagens do status selecionado, que pode ser uma ou mais de Pendente, Aprovado, Negado ou Fechado, assim como Rascunho ou Programado para Artigos de Blog e Respondido ou Não Respondido para Perguntas QnA. Se nenhum estiver selecionado, então todos serão exibidos.

>[!NOTE]
>
>Se apenas o status Não respondido for selecionado, o moderador visualizará todo o conteúdo (para todos os tipos de conteúdo) exceto as perguntas respondidas. Isso ocorre porque a propriedade responsável pela Pergunta Respondida não existe no caso de perguntas não respondidas e outro conteúdo, como tópico do fórum, artigo do blog ou comentários.

![status](assets/statuses.png)

#### Sinalização {#flagging}

A sinalização limita o UGC referenciado exibido a postagens que estão sinalizadas ou ocultas.

Depois que um conteúdo é sinalizado, ele permanece sinalizado até que você cancele a sinalização desse conteúdo único selecionando o **[!UICONTROL Sinalizador]** novamente. Observe que não há níveis de sinalização, como importante ou de acompanhamento.

![chlimage_1-476](assets/chlimage_1-476.png)

#### Membros {#members}

Os membros limitam o UGC referenciado exibido ao UGC publicado pelo nome do membro inserido.

![chlimage_1-477](assets/chlimage_1-477.png)

#### Publicado nos últimos {#posted-in-the-last}

Publicado em Últimos limites, o UGC referenciado é exibido para postagens feitas na última hora, dia, semana, mês ou ano.

![chlimage_1-478](assets/chlimage_1-478.png)

#### Sentimento {#sentiment}

[Sentimento](moderate-ugc.md#sentiment) limita o UGC referenciado exibido em publicações com um valor de sentimento positivo, negativo ou neutro.

![chlimage_1-479](assets/chlimage_1-479.png)

## Ações de moderação {#moderation-actions}

[Ações de moderação](moderate-ugc.md#moderation-actions) pode ser executado em uma ou mais seleções feitas na área de conteúdo ou durante a visualização dos detalhes do conteúdo.

Para moderar as publicações em massa, na área de conteúdo, clique no botão Selecionar ( ![seletor](assets/selecticon.png)) em uma publicação, que aparece ao passar o mouse sobre ela (desktop) ou pressionando e segurando um dedo na publicação (móvel). Ao fazer isso, você insere o modo de seleção múltipla e agora pode selecionar as publicações subsequentes para moderação em massa ao simplesmente clicar nelas. Use os botões exibidos na barra de ferramentas para executar ações de moderação nas publicações selecionadas. Todas as ações solicitarão confirmação.

Para moderar uma única publicação na área de conteúdo, passe o mouse sobre ela (desktop) ou pressione e segure o dedo na publicação (móvel) de modo que os botões apareçam na publicação. Ao operar em um único detalhe de conteúdo, somente uma ação de exclusão solicitará a confirmação.

### Moderação de várias publicações {#moderating-multiple-posts}

Entre no modo de seleção em massa clicando no botão `Select` ícone em uma publicação:

![ícone de seleção](assets/select-icon.png)

Para sair do modo de seleção em massa, selecione o ícone cancelar (x) na barra de ferramentas:

As ações de moderação que podem ser executadas em várias publicações são:

* Negar 
* Excluir
* Fechar/reabrir as publicações

Os ícones que permitem essas ações só aparecem na barra de ferramentas quando várias publicações são selecionadas.

![bulkmoderate](assets/bulkmoderate.png)

### Moderação de uma única publicação {#moderating-a-single-post}

No modo de seleção única, é possível

* Visualizar detalhes do usuário selecionando o nome do usuário
* Visualize a publicação no contexto selecionando o link para a publicação
* [Responder](#reply)
* [Permitir](#allow)
* [Negar ](#deny)
* [Excluir](#delete)
* [Fechar](#close)
* Exibir [Histórico de moderação](#moderation-history)
* [Exibir Detalhes](#viewdetails)

Apresentado na exibição de cartão acima dos ícones de ação de moderação é o texto da publicação e abaixo estão os dados que indicam

* Se tiver respondido e, em caso afirmativo, precedido do número de respostas
* Se tiver sido sinalizado
* Se tiver sido aprovado
* Quando o UGC foi postado

![singleselectmode](assets/singleselectmode.png)

#### Responder {#reply}

![chlimage_1-480](assets/chlimage_1-480.png)

Ao trabalhar com uma única publicação, um ícone de Resposta será exibido se o tipo UGC suportar respostas e estiver configurado para permitir respostas.

#### Permitir {#allow}

![chlimage_1-481](assets/chlimage_1-481.png)

Ao trabalhar com uma única publicação, o ícone Permitir será exibido quando a publicação tiver sido sinalizada ou negada. Se estiver sinalizado, selecionar Permitir apagará todos os sinalizadores.

#### Negar  {#deny}

![chlimage_1-482](assets/chlimage_1-482.png)

O **Negar** a ação de moderação está disponível somente para conteúdo moderado e não é exibido em conteúdo não moderado, exceto no modo de multiseleção.

O conteúdo que não é moderado é sempre aprovado.

O conteúdo moderado insere inicialmente um estado Pendente e pode ser modificado posteriormente para ser aprovado ou negado.

O conteúdo que deixa o estado pendente nunca pode retornar a um estado pendente. O conteúdo marcado como aprovado ou negado pode ser alterado para um estado diferente a qualquer momento.

#### Excluir {#delete}

![chlimage_1-483](assets/chlimage_1-483.png)

Em uma única seleção ou modo em massa, você pode selecionar itens e excluí-los. A ação de exclusão resulta em uma caixa de diálogo de confirmação. Depois de excluídos, esses itens desaparecem imediatamente da área de conteúdo. **Depois que o UGC é excluído, ele é removido permanentemente do repositório e não pode ser recuperado posteriormente.**

#### Fechar {#close}

![chlimage_1-484](assets/chlimage_1-484.png)

Ao trabalhar com uma única publicação, um ícone Fechar será exibido se o tipo UGC suportar a capacidade de impedir outras publicações para esse recurso.

#### Histórico de moderação {#moderation-history}

![chlimage_1-485](assets/chlimage_1-485.png)

Ao trabalhar com uma única publicação, um ícone Histórico de moderação será exibido ao passar o mouse sobre ele. Selecionar o ícone exibirá um painel contendo um histórico de ações tomadas em relação à publicação do UGC.

Para retornar à exibição da área de conteúdo de várias publicações UGC, selecione o X no canto superior direito do painel de detalhes da exibição.

Por exemplo:

![chlimage_1-486](assets/chlimage_1-486.png)

#### Exibir detalhe {#view-detail}

![chlimage_1-487](assets/chlimage_1-487.png)

Ao trabalhar com uma única publicação, mais detalhes podem ser visualizados ao abrir o UGC no modo de detalhes.

Para fazer isso, passe o mouse sobre a publicação para exibir a variável `View Detail` e selecione-o para exibir um painel contendo mais detalhes da publicação.

Para retornar à exibição da área de conteúdo de várias publicações UGC, selecione o X no canto superior direito do painel de detalhes da exibição.

Por exemplo:

![chlimage_1-488](assets/chlimage_1-488.png)
