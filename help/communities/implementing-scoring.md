---
title: Pontuação e emblemas de comunidades
seo-title: Pontuação e emblemas de comunidades
description: A pontuação e os emblemas do AEM Communities permitem identificar e recompensar membros da comunidade
seo-description: A pontuação e os emblemas do AEM Communities permitem identificar e recompensar membros da comunidade
uuid: ca6f22d6-f25d-4f26-b589-81d1f2c830f9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b19b3c24-82a0-468c-a077-9f3edb96afc9
tagskeywords: scoring, badging, badges, gamification
role: Admin
exl-id: 54a4a053-ca44-451a-9a31-f1c1e8cb7002
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2885'
ht-degree: 2%

---

# Pontuação e emblemas de comunidades {#communities-scoring-and-badges}

## Visão geral {#overview}

O recurso de pontuação e selo do AEM Communities oferece a capacidade de identificar e recompensar membros da comunidade.

Os principais aspectos da pontuação e dos emblemas são:

* [Atribuir ](#assign-and-revoke-badges) símbolo identifica a função de um membro na comunidade

* [Atribuição básica de membros do ](#enable-scoring) badgesto para incentivar sua participação (quantidade de conteúdo criada)
* [Atribuição avançada de ](advanced.md) emblema identifica membros como especialistas (qualidade do conteúdo criado)

**** Observe que a concessão de emblemas  [não está habilitada por padrão](implementing-scoring.md#main-pars-text-237875536).

>[!CAUTION]
>
>A estrutura de implementação visível no CRXDE Lite está sujeita a alterações assim que a interface do usuário estiver disponível.

## Selos {#badges}

Os emblemas são colocados sob o nome de um membro para indicar sua função ou sua posição na comunidade. Os emblemas podem ser exibidos como uma imagem ou como um nome. Quando exibido como uma imagem, o nome é incluído como texto alternativo para acessibilidade.

Por padrão, os rótulos estão localizados no repositório em

* /etc/community/badging/images

Se armazenados em um local diferente, eles devem ser lidos e acessíveis a todos.

Os emblemas são diferenciados no UGC quanto ao fato de terem sido atribuídos ou terem sido obtidos de acordo com as regras. No momento, os emblemas atribuídos são exibidos como texto e os emblemas recebidos são exibidos como uma imagem.

### Interface do usuário do gerenciamento de emblemas {#badge-management-ui}

O console Comunidades [Badges](badges.md) fornece a capacidade de adicionar emblemas personalizados que podem ser exibidos para um membro quando ganhados (atribuídos) ou quando assumem uma função específica na comunidade (atribuídos).

### Símbolos atribuídos {#assigned-badges}

Os emblemas baseados em funções são atribuídos por um administrador aos membros da comunidade com base em sua função na comunidade.

Os rótulos atribuídos (e avisados) são armazenados no [SRP](srp.md) selecionado e não são diretamente acessíveis. Até que uma GUI esteja disponível, o único meio para atribuir emblemas baseados em função é fazer isso com código ou cURL. Para obter instruções de cURL, consulte a seção intitulada [Atribuir e Revogar emblemas](#assign-and-revoke-badges).

Incluídos na versão, há três distintivos com base em funções:

* Moderador

   `/etc/community/badging/images/moderator/jcr:content/moderator.png`

* Gerente de grupo

   `/etc/community/badging/images/group-manager/jcr:content/group-manager.png`

* Membro privilegiado

   `/etc/community/badging/images/privileged-member/jcr:content/privileged-member.png`

![chlimage_1-366](assets/chlimage_1-366.png)

### Símbolos atribuídos {#awarded-badges}

Os emblemas baseados em recompensa são concedidos pelo serviço de pontuação aos membros da comunidade com base nas regras aplicadas à sua atividade na comunidade.

Para que os emblemas apareçam como recompensa pela atividade, há duas coisas que devem acontecer:

* A marcação deve ser [enabled](#enable-badges-for-component) para o componente de recurso
* As regras de pontuação e selo devem ser [aplicadas](#apply-rules-to-content) à página (ou ancestral) na qual o componente é colocado

Incluídos na versão, há três selos baseados em recompensa:

* Ouro

   `/etc/community/badging/images/gold-badge/jcr:content/gold.png`

* Prata

   `/etc/community/badging/images/silver-badge/jcr:content/silver.png`

* Bronze

   `/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

![chlimage_1-367](assets/chlimage_1-367.png)

>[!NOTE]
>
>As regras de pontuação podem ser configuradas para atribuir pontos negativos para publicações sinalizadas como inadequadas e, portanto, afetar o valor da pontuação. No entanto, uma vez obtido o selo, ele não será removido automaticamente devido à redução do ponto de pontuação ou alterações na regra de pontuação.
>
>Os emblemas concedidos podem ser revogados da mesma forma que os emblemas atribuídos. Consulte a seção [Atribuir e Revogar emblemas](#assign-and-revoke-badges) . As melhorias futuras incluirão uma interface do usuário para gerenciar os emblemas dos membros.

### Símbolos personalizados {#custom-badges}

Os emblemas personalizados podem ser instalados usando o [Console dos emblemas](badges.md) e atribuídos ou especificados nas regras de marcação.

Quando instalados a partir do console Badges, os emblemas personalizados são replicados automaticamente para o ambiente de publicação.

## Ativar Pontuação {#enable-scoring}

A pontuação não está ativada por padrão. As etapas básicas para a configuração e a habilitação da pontuação e da atribuição de emblemas são:

* Identificar regras para pontos de ganhos ([regras de pontuação](#scoring-rules))
* Para pontos acumulados por regras de pontuação, atribua [emblemas](#badges) ([regras de marcação](#badging-rules))

* [Aplicar as regras de pontuação e marcação a um site da comunidade](#apply-rules-to-content)
* [Ativar a marcação para recursos da comunidade](#enable-badges-for-component)

Consulte a seção [Teste rápido](#quick-test) para ativar a pontuação para um site da comunidade usando as regras de pontuação e marcação padrão para fóruns e comentários.

### Aplicar regras ao conteúdo {#apply-rules-to-content}

Para ativar a pontuação e os emblemas, adicione as propriedades `scoringRules` e `badgingRules`a qualquer nó na árvore de conteúdo do site.

Se o site já estiver publicado, depois de aplicar todas as regras e ativar os componentes, publique-o novamente.

As regras que se aplicam a um componente habilitado para marcação são as do nó atual ou seu ancestral.

Se o nó for do tipo `cq:Page` (recomendado), em seguida, usando o CRXDE|Lite, adicione as propriedades ao seu nó `jcr:content`.

| **Propriedade** | **Tipo** | **Descrição** |
|---|---|---|
| badgingRules | Sequência de caracteres[] | uma lista de matriz de [regras de notificação](#badging-rules) |
| regras de pontuação | Sequência de caracteres[] | uma lista de matriz de [regras de pontuação](#scoring-rules) |

>[!NOTE]
>
>Se uma regra de pontuação parecer não ter efeito na atribuição de emblemas, verifique se a regra de pontuação não foi bloqueada pela propriedade scoringRules da regra de marcação. Consulte a seção intitulada [Regras de emblema](#badging-rules).

### Ativar emblemas para componente {#enable-badges-for-component}

As regras de pontuação e sombreamento estão em vigor apenas para instâncias de componentes que habilitaram a marcação ao editar a configuração do componente no [modo de criação](author-communities.md).

Uma propriedade booleana, `allowBadges`, ativa/desativa a exibição de emblemas para uma instância de componente. Ele é configurável na caixa de diálogo [edição de componente](author-communities.md) para componentes do fórum, QnA e comentário por meio de uma caixa de seleção denominada **Exibir emblemas**.

#### Exemplo: allowBadges para a instância do componente Forum {#example-allowbadges-for-forum-component-instance}

![chlimage_1-368](assets/chlimage_1-368.png)

>[!NOTE]
>
>Qualquer componente pode ser sobreposto para exibir emblemas usando o código HBS encontrado em fóruns, QnA e comentários como exemplo.

## Regras de pontuação {#scoring-rules}

As regras de pontuação são a base da pontuação para fins de concessão de emblemas.

Muito simplesmente, cada regra de pontuação é uma lista de uma ou mais subregras. As regras de pontuação são aplicadas ao conteúdo do site da comunidade para identificar as regras a serem aplicadas quando os rótulos estiverem ativados.

As regras de pontuação são herdadas, mas não aditivas. Por exemplo:

* Se a página 2 contém a regra de pontuação 2 e sua página ancestral 1 contém a regra de pontuação 1
* Uma ação em um componente de página 2 chamará a regra1 e a regra2
* Se ambas as regras contiverem subregras aplicáveis para o mesmo `topic/verb`:

   * Somente a subregra da regra 2 afetará a pontuação
   * As pontuações de ambas as subregras não são adicionadas juntas

Quando há mais de uma regra de pontuação, as pontuações são mantidas separadamente para cada regra.

As regras de pontuação são nós do tipo `cq:Page` com propriedades no seu nó `jcr:content`que especificam a lista de subregras que a definem.

As pontuações são armazenadas no SRP.

>[!NOTE]
>
>Prática recomendada: nomeie exclusivamente cada regra de pontuação.
>
>Os nomes de regras de pontuação devem ser globais exclusivas; eles não devem terminar com o mesmo nome.
>
>Um exemplo do que *not* fazer:\
>/etc/community/pontuação/rules/site1/forums-scoring\
>/etc/community/pontuação/rules/site2/forums-scoring

### Subregras de pontuação {#scoring-sub-rules}

As sub-regras de pontuação contêm as propriedades que detalham os valores para participar da comunidade.

Cada subregra de pontuação identifica

* Quais atividades estão sendo rastreadas
* Que função comunitária específica está envolvida
* Quantos pontos são atribuídos

Por padrão, os pontos são atribuídos ao membro que está tomando a ação, a menos que a subregra especifique o proprietário do conteúdo como recebendo os pontos ( `forOwner`).

Cada subregra pode ser incluída em uma ou mais regras de pontuação.

O nome da subregra normalmente segue o padrão de uso de um *assunto, objeto* e *verb*. Por exemplo:

* membro-comentário-criar
* membro-receberá-voto

Sub-regras são nós do tipo `cq:Page` com propriedades no nó `jcr:content`que especificam os [verbos e tópicos](#topics-and-verbs) .

<table> 
 <tbody> 
  <tr> 
   <th>Propriedade</th> 
   <th>Tipo</th> 
   <th> Valor Descrição</th> 
  </tr> 
  <tr> 
   <td><i><code>VERB</code></i></td> 
   <td>Longo</td> 
   <td> 
    <ul> 
     <li>Obrigatório; o verbo corresponde a uma ação de evento</li> 
     <li>deve haver pelo menos uma propriedade verb</li> 
     <li>o verbo deve ser inserido em todas as letras maiúsculas</li> 
     <li>pode haver várias propriedades de verbo, mas nenhuma duplicação</li> 
     <li>o valor é a pontuação a ser aplicada para esse evento</li> 
     <li>o valor pode ser positivo ou negativo</li> 
     <li>uma lista de verbos suportados na versão está na seção <a href="#topics-and-verbs">Tópicos e Verbos</a></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>topics</code></td> 
   <td>Sequência de caracteres[]</td> 
   <td> 
    <ul> 
     <li>facultativo; restringe a subregra aos componentes da comunidade identificados por tópicos de evento</li> 
     <li>se especificado: é uma string de vários valores com tópicos de evento</li> 
     <li>uma lista de tópicos na versão está na seção <a href="#topics-and-verbs">Tópicos e Verbos</a></li> 
     <li>o padrão é aplicar a todos os tópicos associados ao(s) verbo(s)</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>forOwner</code></td> 
   <td>Booleano</td> 
   <td> 
    <ul> 
     <li>facultativo; não é relevante quando o membro age com base no conteúdo que possui</li> 
     <li>se verdadeiro, aplique pontuação ao proprietário do conteúdo que está sendo tratado</li> 
     <li>se falso, aplique pontuação ao membro que está tomando a ação</li> 
     <li>o padrão é false</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>scoringType</code></td> 
   <td>Sequência de caracteres</td> 
   <td> 
    <ul> 
     <li>facultativo; identifica o mecanismo de pontuação</li> 
     <li>se "básico", especifica o mecanismo de pontuação com base na quantidade 
      <ul> 
       <li>incluído na versão</li> 
      </ul> </li> 
     <li>se "avançado", especifica o mecanismo de pontuação com base na qualidade e quantidade 
      <ul> 
       <li>requer <a href="advanced.md">pacote adicional</a></li> 
      </ul> </li> 
     <li>o padrão é "básico"</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

### Regras e subregras de pontuação incluídas {#included-scoring-rules-and-sub-rules}

Estão incluídas na versão duas regras de pontuação para a [Função do fórum](functions.md#forum-function) (uma para os componentes Fórum e Comentários do recurso Fórum):

1. /etc/community/scoring/rules/comments-scoring

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/member-comment-create

      /etc/community/scoring/rules/sub-rules/member-receive-vote

      /etc/community/scoring/rules/sub-rules/member-don

      /etc/community/scoring/rules/sub-rules/member-is-moderated

1. /etc/community/pontuação/rules/forums-scoring

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/member-forum-create

      /etc/community/scoring/rules/sub-rules/member-receive-vote

      /etc/community/scoring/rules/sub-rules/member-don

      /etc/community/scoring/rules/sub-rules/member-is-moderated

**Notas:**

* Os nós `rules`e `sub-rules` são do tipo cq:Page

* `subRules`é um atributo do tipo [] String no  `jcr:content` nó da regra

* `sub-rules` pode ser compartilhado entre várias regras de pontuação
* `rules`deve estar localizado em um local de repositório com permissão de leitura para todos

   * Os nomes das regras devem ser exclusivos, independentemente da localização

### Ativar regras de pontuação personalizadas {#activating-custom-scoring-rules}

Quaisquer alterações ou adições feitas às regras de pontuação ou subregras feitas no ambiente de criação precisam ser instaladas na publicação.

## Regras de marcação {#badging-rules}

Regras de atribuição de rótulo vinculam regras de pontuação a rótulos especificando:

* Qual regra de pontuação
* A pontuação necessária para receber um símbolo específico

As regras de marcação são nós do tipo `cq:Page` com propriedades em seu nó `jcr:content`que correlacionam as regras de pontuação a pontuações e distinções.

As regras para a marcação consistem em uma propriedade `thresholds`obrigatória que é uma lista ordenada de pontuações mapeadas para emblemas. As pontuações devem ser ordenadas em maior valor. Por exemplo:

* `1|/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Selo de bronze é visto para ganhar 1 ponto

* `60|/etc/community/badging/images/silver-badge/jcr:content/silver.png`

   * Um emblema de prata é concedido quando há 60 pontos acumulados

* `80|/etc/community/badging/images/gold-badge/jcr:content/gold.png`

   * Um selo de ouro é avisado quando 80 pontos são acumulados

As regras de marcação são emparelhadas com regras de pontuação, que determinam como os pontos são acumulados. Consulte a seção intitulada [Aplicar regras ao conteúdo](#apply-rules-to-content).

A propriedade `scoringRules`em uma regra de marcação simplesmente restringe quais regras de pontuação podem ser pareadas com essa regra de marcação específica.

>[!NOTE]
>
>Prática recomendada: crie imagens de selo exclusivas para cada site de AEM.

![chlimage_1-369](assets/chlimage_1-369.png)

<table> 
 <tbody> 
  <tr> 
   <th>Propriedade</th> 
   <th>Tipo</th> 
   <th>Valor Descrição</th> 
  </tr> 
  <tr> 
   <td>limites</td> 
   <td>Sequência de caracteres[]</td> 
   <td><em>(obrigatório)</em> Uma string com vários valores do formulário 'number|path' 
    <ul> 
     <li>número = pontuação</li> 
     <li>| = barra vertical (U+007C)</li> 
     <li>caminho = caminho completo para o recurso de imagem de selo</li> 
    </ul> As cadeias de caracteres devem ser ordenadas de forma que os números aumentem em valor e nenhum espaço em branco deve aparecer entre o número e o caminho.<br /> Exemplo de entrada:<br /> <code>80|/etc/community/badging/images/gold-badge/jcr:content/gold.png</code></td> 
  </tr> 
  <tr> 
   <td>badgingType</td> 
   <td>Sequência de caracteres</td> 
   <td><em>(opcional) </em> Identifica o mecanismo de pontuação como "básico" ou "avançado". Se desejar o mecanismo de pontuação avançado, consulte <a href="advanced.md">Pontuação avançada e Aviso de erro</a>. O padrão é "básico".</td> 
  </tr> 
  <tr> 
   <td> 
    <code>scoringRules </code></td> 
   <td>Sequência de caracteres[]</td> 
   <td>(<em>opcional</em>) Uma string de vários valores para restringir a regra de selo a eventos de pontuação identificados pelas regras de pontuação</td> 
  </tr> 
 </tbody> 
</table>

### Regras de marcação incluídas {#included-badging-rules}

Estão incluídas na versão duas Regras de emblema que correspondem às [Fóruns e Regras de pontuação de comentários](#includedscoringrules).

* /etc/community/badging/rules/comments-badging
* /etc/community/badging/rules/forums-badging

**Notas:**

* `rules` nós são do tipo cq:Page
* `rules`deve estar localizado em um local de repositório com permissão de leitura para todos

   * Os nomes das regras devem ser exclusivos, independentemente da localização

### Ativando regras de marcação personalizadas {#activating-custom-badging-rules}

Quaisquer alterações ou adições feitas às regras de marcação ou imagens feitas no ambiente de criação precisam ser instaladas na publicação.

## Atribuir e Revogar Símbolos {#assign-and-revoke-badges}

Os emblemas podem ser atribuídos aos membros usando o [console de membros](members.md#badges-tab) ou programaticamente usando comandos cURL.

Os seguintes comandos cURL mostram o que é necessário para uma solicitação HTTP para atribuir e revogar emblemas. O formato básico é:

cURL -i -X POST -H *header* -u *sign * -F * operation * -F *badge * *member-profile-url*

*header* = &quot;Accept:application/json&quot;\
cabeçalho personalizado a ser enviado para o servidor (obrigatório)

*sign* = administrador-id:senha\
por exemplo: admin:admin

*operation*  = &quot;:operation=social:assignBadge&quot; OU &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file*  = o local do arquivo de imagem do selo no repositório\
por exemplo: /etc/community/badging/images/moderator/jcr:content/moderator.png

*member-profile-url*  = o endpoint do perfil do membro na publicação\
por exemplo: https://&lt;server>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>O *member-profile-url*
>
>* Pode se referir a uma instância do autor se o [Tunnel Service](users.md#tunnel-service) estiver ativado
>* Pode ser um nome obscuro e aleatório - consulte [Lista de verificação de segurança](../../help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) em relação à ID autorizável

>



### Exemplos: {#examples}

#### Atribuir um símbolo de moderador {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Revogar um símbolo de prata atribuído {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/etc/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>Usar cURL para atribuir e revogar emblemas funciona para qualquer imagem de emblema, mas quando atribuído em vez de ganho, eles são marcados como emblemas atribuídos e manipulados de acordo.

## Pontuação e emblemas para componentes personalizados {#scoring-and-badges-for-custom-components}

As regras de pontuação e marcação podem ser criadas para componentes personalizados ao associar os tópicos de evento criados para o componente aos verbos.

## Tópicos e verbos {#topics-and-verbs}

Quando os membros interagem com os recursos das comunidades, os eventos são enviados e podem acionar ouvintes assíncronos, como notificações e pontuação.

A instância SocialEvent de um componente registra os eventos como `actions`que ocorrem para um `topic`. O SocialEvent inclui um método para retornar um `verb`associado à ação. Existe uma relação *n-1* entre `actions`e `verbs`.

Para os componentes de comunidades entregues, as tabelas a seguir descrevem o `verbs`definido para cada `topic`disponível para uso em [subregras de pontuação](#scoring-sub-rules).

>[!NOTE]
>
>Uma nova propriedade booleana, `allowBadges`, ativa/desativa a exibição de emblemas para uma instância de componente. Ele poderá ser configurado nas [caixas de diálogo de edição de componente](author-communities.md) atualizadas por meio de uma caixa de seleção denominada **Exibir emblemas**.

**[Calendar](calendar.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/calendar

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um evento de calendário |
| ADICIONAR | comentários do membro em um evento de calendário |
| ATUALIZAR | evento ou comentário do calendário do membro é editado |
| EXCLUIR | o evento ou comentário do calendário do membro é excluído |

**[Comentários](comments.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um comentário |
| ADICIONAR | membro responde ao comentário |
| ATUALIZAR | o comentário do membro é editado |
| EXCLUIR | o comentário do membro é excluído |

**[Biblioteca de arquivos](file-library.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria uma pasta |
| ANEXAR | membro carrega um arquivo |
| ATUALIZAR | membro atualiza uma pasta ou arquivo |
| EXCLUIR | membro exclui uma pasta ou arquivo |

**[Forum](forum.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria tópico do fórum |
| ADICIONAR | membro responde ao tópico do fórum |
| ATUALIZAR | o tópico ou a resposta do fórum do membro é editada |
| EXCLUIR | o tópico ou resposta do fórum do membro é excluído |

**[Journal](blog-feature.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/journal

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria um artigo de blog |
| ADICIONAR | membro comenta em um artigo do blog |
| ATUALIZAR | artigo ou comentário do blog do membro é editado |
| EXCLUIR | artigo ou comentário do blog do membro é excluído |

**[QnA](working-with-qna.md)**
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria uma pergunta QnA |
| ADICIONAR | membro cria uma resposta QnA |
| ATUALIZAR | pergunta ou resposta QnA do membro é editada |
| SELECIONAR | a resposta do membro é selecionada |
| CANCELAR SELEÇÃO | a resposta do membro é desmarcada |
| EXCLUIR | pergunta ou resposta QnA do membro é excluída |

**[Revisões](reviews.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verbo** | **Descrição** |
|---|---|
| POST | membro cria revisão |
| ATUALIZAR | a revisão do membro é editada |
| EXCLUIR | a revisão do membro é eliminada |

**[Classificação](rating.md)**
de componente socialEvent  `topic`= com/adobe/cq/social/tally/rating

| **Verbo** | **Descrição** |
|---|---|
| ADICIONAR CLASSIFICAÇÃO | o conteúdo do membro foi atualizado |
| REMOVER CLASSIFICAÇÃO | o conteúdo do membro foi reduzido |

**[Voting](voting.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/vote

| **Verbo** | **Descrição** |
|---|---|
| ADICIONAR VOTAÇÃO | o conteúdo do membro foi votado |
| REMOVER VOTAÇÃO | o conteúdo do membro foi rejeitado |

****
Componentes habilitados para moderaçãoSocialEvent  `topic`= com/adobe/cq/social/moderação

| **Verbo** | **Descrição** |
|---|---|
| NEGAR | o conteúdo do membro é negado |
| SINALIZADOR COMO INADEQUADO | o conteúdo do membro é sinalizado |
| INADEQUADO | o conteúdo do membro não está sinalizado |
| ACEITAR | o conteúdo do membro é aprovado pelo moderador |
| FECHAR | membro fecha comentário a edições e respostas |
| ABRIR | membro reabre comentário |

### Eventos de componente personalizado {#custom-component-events}

Para um componente personalizado, um SocialEvent é instanciado para registrar os eventos do componente como `actions`que ocorrem para um `topic`.

Para oferecer suporte à pontuação, o SocialEvent precisaria substituir o método `getVerb()` para que um `verb`apropriado seja retornado para cada `action`. O `verb` retornado para uma ação pode ser um usado comumente (como `POST`) ou um especializado para o componente (como `ADD RATING`). Existe uma relação *n-1* entre `actions`e `verbs`.

## Resolução de problemas {#troubleshooting}

### Os emblemas não estão aparecendo {#badges-are-not-appearing}

Se as regras de pontuação e selo tiverem sido aplicadas ao conteúdo do site, mas os emblemas não estiverem sendo avisados para nenhuma atividade, verifique se os emblemas foram ativados para a instância desse componente.

Consulte [Ativar emblemas para o componente](#enable-badges-for-component).

### A regra de pontuação não tem efeito {#scoring-rule-has-no-effect}

Se as regras de pontuação e selo tiverem sido aplicadas ao conteúdo do site, e os emblemas tiverem sido atribuídos para algumas ações, mas não para outras, verifique se a regra de selo não restringiu as regras de pontuação às quais se aplica.

Consulte a propriedade `scoringRules`de [Regras de emblema](#badging-rules).

### Tipo sensível a maiúsculas e minúsculas {#case-sensitive-typo}

A maioria das propriedades e valores, especialmente os verbos, diferencia maiúsculas de minúsculas. Os verbos devem ser todos MAIÚSCULAS quando usados em uma subregra de pontuação.

Se o recurso não estiver funcionando como esperado, verifique se os dados foram inseridos corretamente.

## Teste rápido {#quick-test}

É possível tentar rapidamente a pontuação e o selo usando o [Tutorial de introdução](getting-started.md) (engajamento) site:

* Acessar o CRXDE Lite no autor
* Navegue até a página base:

   * /content/sites/engagement/en/jcr:content

* Adicione a propriedade badgingRules:

   * **Nome**: `badgingRules`
   * **Tipo**: `String`
   * Selecione **[!UICONTROL Multi]**
   * Selecione **[!UICONTROL Adicionar]**
   * Insira `/etc/community/badging/rules/forums-badging`
   * Selecionar `+`
   * Insira `/etc/community/badging/rules/comments-badging`
   * Selecione **[!UICONTROL OK]**

* Adicione a propriedade scoringRules:

   * **Nome**: `scoringRules`
   * **Tipo**: `String`
   * Selecione **[!UICONTROL Multi]**
   * Selecione **[!UICONTROL Adicionar]**
   * Insira `/etc/community/scoring/rules/forums-scoring`
   * Selecionar `+`
   * Insira `/etc/community/scoring/rules/comments-scoring`
   * Selecione **[!UICONTROL OK]**

* Selecione **[!UICONTROL Salvar tudo]**

![chlimage_1-370](assets/chlimage_1-370.png)

Em seguida, verifique se os componentes de fórum e comentários permitem a exibição de emblemas:

* Novamente usando o CRXDE Lite
* Navegue até o componente de fórum

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Adicione a propriedade booleana allowBadges, se necessário, e verifique se ela é verdadeira

   * **Nome**: `allowBadges`
   * **Tipo**: `Boolean`
   * **Valor**:  `true`

![chlimage_1-371](assets/chlimage_1-371.png)

Em seguida, [republique](sites-console.md#publishing-the-site) o site da comunidade.

Por último,

* Navegue até o componente na instância de publicação
* Fazer logon como membro da comunidade (por exemplo: weston.mccall@dodgit.com / password)
* Publicar um novo tópico do fórum
* A página deve ser atualizada para que o símbolo seja exibido

   * Faça logoff e login como um membro da comunidade diferente (por exemplo: aaron.mcdonald@mailinator.com / password)

* Selecionar o fórum

Isso deve gerar para o membro da comunidade um selo de bronze visível em sua publicação no fórum, devido ao primeiro limite da regra de selo de fóruns ser uma pontuação de 1.

![bronzebadge](assets/bronzebadge.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Scoring and Badges Essentials](configure-scoring.md) para desenvolvedores.

Para obter informações sobre o mecanismo de pontuação avançado, consulte [Pontuação Avançada e Aviso de Intervalo](advanced.md).

O Quadro de líderes configurável [componente](enabling-leaderboard.md) e [função](functions.md#leaderboard-function) simplifica a exibição de membros e suas pontuações em um site da comunidade.
