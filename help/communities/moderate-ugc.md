---
title: Moderação de conteúdo da comunidade
seo-title: Moderação de conteúdo da comunidade
description: Conceitos e ações de moderação
seo-description: Conceitos e ações de moderação
uuid: a24d09e7-3260-4eec-844e-97e6849c94d8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d11b8fc8-5e98-4a77-a536-d445ac88e1b3
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 2%

---


# Moderação do conteúdo da comunidade {#moderating-community-content}

## Visão geral {#overview}

O conteúdo da comunidade, também conhecido como conteúdo gerado pelo usuário (UGC), é criado quando um membro (visitante conectado do site) publica conteúdo de um site da comunidade publicado por meio da interação com um dos seguintes componentes da comunidade:

* [Blog](blog-feature.md): membros postam um artigo ou comentário no blog
* [Calendário](calendar.md): membros postam um evento de calendário ou comentário
* [Comentários](comments.md): membros postam um comentário ou respondem a um comentário
* [Fórum](forum.md): os membros postam um novo tópico ou respondem a um tópico
* [Ideação](ideation-feature.md): membros postam uma ideia ou comentário
* [QnA](working-with-qna.md): membros criam uma pergunta ou respondem uma pergunta
* [Revisões](reviews.md): membros postam um comentário ao classificar um item

A moderação do UGC é útil para reconhecer contribuições positivas, bem como limitar as negativas (como spam e linguagem abusiva). O UGC pode ser moderado de vários ambientes:

* [Console de moderação em massa](moderation.md)

   O console Moderação é acessível pelos administradores e [moderadores da comunidade](users.md) no ambiente público, bem como pelos administradores no ambiente de criação. Isso é possível quando o conteúdo da comunidade é armazenado em um [armazenamento comum](working-with-srp.md).

* [Moderação no contexto](in-context.md)

   A moderação no ambiente de publicação pode ser executada pelos administradores e moderadores da comunidade diretamente na página em que o conteúdo foi publicado.

## Ações de moderação {#moderation-actions}

As ações que podem ser executadas no conteúdo publicado (UGC) variam de acordo com a identidade do usuário e o ambiente. A tabela abaixo usa a seguinte terminologia para descrever as várias funções de acordo com a identidade do usuário:

* `Admin`\
   Um usuário que é membro do grupo [community-administrators](users.md)
* `Moderator`
Um membro de um grupo de  [moderadores da ](users.md#publishenvironmentusersandgroups) comunidade (tem permissões de  [moderador](in-context.md#moderatorpermissions))
* `Creator`\
   O usuário que postou o conteúdo
* `Member`\
   Um usuário conectado sem permissões especiais
* `Visitor`
Um usuário anônimo

<table> 
 <tbody>
  <tr>
   <td> </td> 
   <td><strong>Admin</strong></td> 
   <td><strong>Moderador</strong></td> 
   <td><strong>Criador</strong></td> 
   <td><strong>Membro</strong></td> 
   <td><strong>Visitante</strong></td> 
   <td><strong>Evento<br /> acionado</strong></td> 
   <td><strong>Remodado</strong></td> 
  </tr>
  <tr>
   <td><strong>Editar/<br /> Excluir</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Recortar</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Negar </strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Fechar/<br /> Reabrir</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X<br /> </td> 
  </tr>
  <tr>
   <td><strong>Sinalizar/<br /> Cancelar Sinalização</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Permitir</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X</td> 
  </tr>
 </tbody>
</table>

### Editar / Excluir {#edit-delete}

Depois que uma publicação é feita, ela pode ser editada ou excluída pelo criador, administrador ou moderador da comunidade.

Quando o UGC é excluído, ele é removido do repositório e pode não ser recuperado.

### Recortar {#cut}

Um administrador ou moderador de comunidade pode mover um ou mais tópicos do fórum ou perguntas de QnA de um local para outro. Isso inclui de um site da comunidade a outro site da comunidade, desde que o mesmo membro tenha privilégios de moderação em ambos os sites.

Ao selecionar a ação Cortar, o conteúdo é copiado para uma área de transferência. Várias publicações podem ser copiadas e movidas como um grupo para o novo local.

![](assets/cutugc.png) ![cutugcputbackugc](assets/putbackugc.png)

No outro local, quando o conteúdo está presente na área de transferência, um botão Colar fica visível ao lado da Nova publicação com um número identificando o número de publicações que serão coladas. O botão Colar inclui uma opção para limpar a área de transferência em vez de colar.

![chlimage_1-218](assets/chlimage_1-218.png) ![chlimage_1-219](assets/chlimage_1-219.png)

### Negar {#deny}

Um moderador pode impedir que o UGC permaneça visível no site publicado. Para administradores e moderadores da comunidade, a publicação ainda está disponível e é anotada como spam.

### Fechar / Reabrir {#close-reopen}

A ação Fechar opera em todo o thread de conversa (um tópico de fórum ou o comentário inicial) e inclui todas as postagens ou respostas subsequentes.

Quando fechado, não apenas não são possíveis mais respostas, como também não são permitidas ações de moderação.

Para executar qualquer operação, o tópico ou comentário deve ser Reaberto.

A ação Fechar/Reabrir pode ser executada pelos administradores ou moderadores da comunidade.

### Sinalizar / Cancelar sinalização {#flag-unflag}

Sinalizar é um meio para qualquer membro conectado, exceto pelo criador do conteúdo, para indicar que há um problema com o conteúdo de uma publicação. Depois de sinalizado, um ícone de cancelamento de sinalizador será exibido, permitindo que o mesmo membro desmarque o conteúdo.

A moderação no contexto pode ser configurada para permitir que os membros selecionem um motivo ao marcar uma publicação. A lista de motivos de sinalizador selecionáveis pode ser configurada, incluindo se um motivo personalizado pode ou não ser inserido. O motivo do sinalizador é salvo com o UGC, mas o motivo não aciona nenhuma ação específica. Somente o número de sinalizadores aciona uma notificação. O conteúdo sinalizado é anotado como tal, para que os moderadores possam agir com base nele.

O sistema rastreia todos os sinalizadores, que foram sinalizados, e o motivo do sinalizador e envia um evento quando o limite foi atingido. Se o UGC for Permitido por um moderador da comunidade, esses sinalizadores serão arquivados. Depois de permitir e arquivar, se houver sinalizadores subsequentes, eles serão arquivados como se não houvesse sinalizadores anteriores.

### Permitir {#allow}

A ação Permitir é uma opção para UGC que foi Sinalizado, Negado ou não foi aprovado em um sistema pré-moderado. A ação Permitir limpará qualquer status sinalizado ou negado/spam presente e arquivará quaisquer dados sinalizados.

## Conceitos comuns de moderação {#common-moderation-concepts}

### Premoderation {#premoderation}

Quando o UGC é pré-moderado, a publicação não será exibida no site publicado até ser aprovada por uma ação de moderação. Durante a criação de um [site da comunidade](sites-console.md), marcar a caixa ` [Content is Premoderated](sites-console.md#moderation)` habilitará a pré-moderação para todo o site. Depois que os componentes são colocados em uma página, os componentes que oferecem suporte à moderação podem ser configurados para pré-moderação usando uma configuração na caixa de diálogo de edição:

* [](comments.md) Comentários e  [revisões](reviews.md)

   na guia **[!UICONTROL Moderação do usuário]**, marque **[!UICONTROL Pré-moderação]**

* [Fórum](forum.md),  [ideação](ideation-feature.md),  [QnA](working-with-qna.md) e  [](calendar.md) guia  **** Configurações do calendário, marque  **[!UICONTROL Moderado]**

### Detecção de spam {#spam-detection}

A detecção de spam é uma funcionalidade de moderação automática, que filtra partes indesejadas do conteúdo gerado pelo usuário, marcando-as como spam. Depois de habilitado, ele identifica se o conteúdo gerado pelo usuário é spam ou não com base em uma coleção pré-configurada de palavras de spam. As palavras de spam padrão são fornecidas em

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`.

No entanto, para personalizar ou estender as palavras de spam padrão, crie um conjunto de palavras no diretório /apps seguindo a estrutura das palavras de spam padrão por meio de [overlay](overlay-comments.md).

Uma postagem gerada pelo usuário (em todos os tipos de conteúdo, por exemplo, blogs, fóruns e comentários) contendo palavras spam é marcada com o texto &quot;Essa postagem foi classificada como spam&quot; acima da postagem.

O moderador pode ver essa publicação e marcar a mesma para permitir ou negar a exibição no site. As ações de moderação nessas publicações podem ser executadas no contexto ou por meio da interface do usuário de moderação em massa.

![spam](assets/spamdetection.png)

Para ativar o mecanismo de detecção de spam, siga estas etapas:

1. Abra [Console da Web](http://localhost:4502/system/console/configMgr), acessando `/system/console/configMgr`.

1. Localize a configuração **[!UICONTROL Moderação automática do AEM Communities]** e edite-a.
1. Adicione a entrada `SpamProcess`.

![spamprocess](assets/spamprocess.png)

>[!NOTE]
>
>A detecção de spam só é implementada para o idioma inglês.

### Sentimento {#sentiment}

O sentimento é calculado com base no número de palavras-chave positivas e negativas ([watchwords](#configuringwatchwords)) presentes em uma publicação (UGC).

A análise de sentimento usa um conjunto de regras pré-configuradas e calcula o sentimento do UGC. As regras padrão estão localizadas em `/libs/cq/workflow/components/workflow/social/sentiments/rules.`

O valor gerado pelas regras é de 1 (todas negativas, nenhuma palavra positiva) a 10 (todas positivas, nenhuma negativa). Um valor de sentimento de 5 é um sentimento neutro e é o padrão.

As regras definidas no componente /libs são:

* Regra 1: defina o valor como 1 se não houver palavras positivas e pelo menos uma palavra negativa
* Regra 2: defina o valor como 10 se não houver palavras negativas e pelo menos uma palavra positiva
* Regra 3: defina o valor como 3 se houver mais palavras negativas do que palavras positivas
* Regra 4: defina o valor como 8 se houver mais palavras positivas do que palavras negativas

Para substituir ou adicionar regras, crie um conjunto de regras no diretório /apps seguindo a estrutura das regras padrão. Edite a configuração de sentimento para identificar o local das regras.

Depois de analisado, o sentimento é armazenado com o UGC.

No [console de moderação em massa](moderation.md), é possível filtrar e exibir o UGC com base no fato do sentimento ser negativo, neutro ou positivo.

#### Palavras de observação {#watchwords}

AEM comunidades fornece um *analisador de palavra de observação *como uma etapa no processo para avaliar o [sentimento](#sentiment). A contribuição para o valor do sentimento fornecido pelas palavras de ordem é devido a uma comparação de palavras de observação negativas e positivas usadas no conteúdo publicado, bem como de palavras proibidas.

#### Configurar o sentimento e as palavras de observação {#configure-sentiment-and-watchwords}

A lista de palavras de observação positivas e negativas pode ser personalizada como podem ser as regras de sentimento.

A lista padrão de palavras de ordem pode ser inserida como propriedades de um nó no repositório, semelhante ao padrão ou substituindo o padrão configurando o serviço OSGi `sentimentprocess.name`com a lista de palavras.

O **sentimentprocess.name** também pode ser modificado para fazer referência à localização de um conjunto personalizado de regras de sentimento.

Para configurar o sentimento e as palavras de observação:

* Em uma instância do autor
* Fazer logon como administrador
* Abra [Console da Web](http://localhost:4502/system/console/configMgr)
* Localizar `sentimentprocess.name`
* Selecione a configuração a ser aberta no modo de edição

![sentimentprocess](assets/sentimentprocess.png)

* ****
Palavras de observação positivasUma lista separada por vírgulas que contribui para um sentimento positivo e substitui os padrões. O padrão é uma lista vazia.

* **Palavras de**
observação negativasUma lista separada por vírgulas que contribui para um sentimento negativo que substitui os padrões. O padrão é uma lista vazia.

* **Caminho explícito para o**
nó de palavras de observação O local do repositório de um nó que contém o padrão 
`positive` e  `negative` especificar palavras de observação padrão. O padrão é `/libs/settings/community/watchwords/default`.

* ****
Regras de sentimentoO local do repositório das regras para calcular o sentimento com base em palavras de observação positivas e negativas. O padrão é 
`/libs/cq/workflow/components/workflow/social/sentiments/rules` (no entanto, não há mais nenhum workflow envolvido).

A seguir encontra-se um exemplo de uma entrada personalizada para as palavras de ordem padrão, quando `Explicit Path to Watchwords Node` está definido como `/libs/settings/community/watchwords/default`.

![crxde](assets/crxde.png)

### Permissões do moderador {#moderator-permissions}

As seguintes permissões, quando atribuídas ao mesmo recurso, são coletivamente chamadas de **`moderator permissions`**:

* `Read`
* **`Modify`**
* `Create`
* `Delete`
* `Replicate`

