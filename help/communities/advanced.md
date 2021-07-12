---
title: Pontuação avançada e emblemas
seo-title: Pontuação avançada e emblemas
description: Configuração de pontuação avançada
seo-description: Configuração de pontuação avançada
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
role: Admin
exl-id: c9406aae-288e-4cdf-ac01-cb26b423639e
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---

# Pontuação avançada e emblemas {#advanced-scoring-and-badges}

## Visão geral {#overview}

A pontuação avançada permite a atribuição de selos para identificar membros como especialistas. A pontuação avançada atribui pontos com base na quantidade *e* qualidade do conteúdo criado por um membro, enquanto a pontuação básica atribui pontos simplesmente com base na quantidade de conteúdo criado.

Essa diferença é devido ao mecanismo de pontuação usado para calcular as pontuações. O mecanismo básico de pontuação aplica matemática simples. O mecanismo de pontuação avançado é um algoritmo adaptável que recompensa os membros ativos que contribuem com conteúdo valioso e relevante, deduzido pelo processamento de linguagem natural (NLP) de um tópico.

Além da relevância do conteúdo, os algoritmos de pontuação levam em consideração as atividades dos membros, como votação e porcentagem de respostas. Embora a pontuação básica os inclua quantitativamente, a pontuação avançada os usa algoricamente.

Portanto, o mecanismo de pontuação avançado requer dados suficientes para fazer a análise significativa. O limite de realização para se tornar um especialista é constantemente reavaliado, pois o algoritmo se ajusta continuamente ao volume e à qualidade do conteúdo criado. Também há um conceito de *decay* de publicações mais antigas de um membro. Se um membro especialista deixar de participar do assunto em que ganhou status de especialista, em um ponto predeterminado (consulte [configuração do mecanismo de pontuação](#configurable-scoring-engine)), ele poderá perder seu status de especialista.

Configurar a pontuação avançada é praticamente o mesmo que a pontuação básica:

* As regras básicas e avançadas de pontuação e marcação são [aplicadas ao conteúdo](implementing-scoring.md#apply-rules-to-content) da mesma maneira
   * Regras básicas e avançadas de pontuação e marcação podem ser aplicadas ao mesmo conteúdo
* [Ativar emblemas para componentes ](implementing-scoring.md#enable-badges-for-component) é genérico

As diferenças na configuração das regras de pontuação e marcação são:

* Mecanismo de pontuação avançado configurável
* Regras avançadas de pontuação:
   * `scoringType` definido como  **[!UICONTROL avançado]**
   * Requer palavras de interrupção

* Regras avançadas de marcação:
   * `badgingType` definido como  **[!UICONTROL avançado]**
   * `badgingLevels` definir para o número de peritos a atribuir
   * Requer `badgingPaths` matriz de emblemas em vez de limites de pontos de mapeamento de matriz para emblemas

>[!NOTE]
>
>Para usar recursos avançados de pontuação e marcação, instale o [pacote de identificação de especialista](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg).

## Mecanismo de pontuação configurável {#configurable-scoring-engine}

O mecanismo de pontuação avançado fornece uma configuração OSGi com parâmetros que afetam o algoritmo de pontuação avançado.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Pontuação de]**
pesosPara um tópico, especifique o verbo que deve receber a prioridade mais alta ao calcular a pontuação. Um ou mais tópicos podem ser inseridos, mas limitados a **um verbo por tópico**. Consulte [Tópicos e Verbos](implementing-scoring.md#topics-and-verbs).

   Inserido como `topic,verb` com a vírgula escapada. Por exemplo:

   `/social/forum/hbs/social/forum\,ADD`

   O padrão é definido como ADD verb para componentes de QnA e de fórum.


* **[!UICONTROL Intervalo de pontuação]**

   O intervalo para pontuações avançadas é definido por esse valor (pontuação máxima possível) e 0 (pontuação mais baixa possível).

   O valor padrão é 100, de modo que o intervalo de pontuação seja 0-100.


* **[!UICONTROL Intervalo de tempo de declínio da entidade]**

   Esse parâmetro representa o número de horas após as quais todas as pontuações de entidade são descartadas. Isso é necessário para não incluir mais o conteúdo antigo nas pontuações de um site da comunidade.

   O valor padrão é 216000 horas (~24 anos).


* **[!UICONTROL Taxa de crescimento de pontuação]**

   Especifica a pontuação. entre 0 e o intervalo de pontuação, para além do qual o crescimento diminui para limitar o número de peritos.

   O valor padrão é 50.

## Regras avançadas de pontuação {#advanced-scoring-rules}

Na pontuação básica, é conhecida a quantidade necessária para ganhar um selo.

Na pontuação avançada, a quantidade necessária é ajuste constantemente com base na quantidade de dados de qualidade no sistema. A pontuação é continuamente calculada de forma semelhante a uma curva em forma de sino.

Se um membro ganhou um selo de especialista em um tópico que não está mais ativo, há a possibilidade de ele perder o selo devido a um declínio no tempo.

### Tipo de pontuação {#scoringtype}

Uma regra de pontuação é um conjunto de sub-regras de pontuação, cada uma das quais declara o `scoringType`.

Para chamar o mecanismo de pontuação avançado, o `scoringType`deve ser definido como `advanced`.

Consulte [Subregras de pontuação](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Palavras-limite {#stopwords}

O pacote de pontuação avançado instala uma pasta de configuração que contém um arquivo de palavras de interrupção:

* `/etc/community/scoring/configuration/stopwords`

O algoritmo de pontuação avançado usa a lista de palavras contidas no arquivo de palavras limites para identificar palavras em inglês comuns que são ignoradas durante o processamento de conteúdo.

Não há expectativa de que esse arquivo seja modificado.

Se o arquivo de palavras de interrupção estiver ausente, o mecanismo de pontuação avançado emitirá um erro.

## Regras avançadas de marcação {#advanced-badging-rules}

As propriedades avançadas da regra de marcação diferem das [propriedades básicas da regra de marcação](implementing-scoring.md#badging-rules).

Em vez de associar pontos a uma imagem de selo, é necessário identificar o número de especialistas permitidos e a imagem do selo a ser premiada.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Propriedade** | **Tipo** | **Descrição do valor** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Sequência de caracteres[] | (Obrigatório) Uma sequência de vários valores de imagens de selo até o número de badgingLevels. Os caminhos de imagem do selo devem ser solicitados para que o primeiro seja concedido ao especialista mais alto. Se houver menos emblemas do que o indicado por badgingLevels, o último emblema no array preencherá o restante do array. Exemplo de entrada:/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | Longo | (Opcional) Especifica os níveis de especialização a serem concedidos. Por exemplo, se houver um especialista e um quase especialista (dois distintivos), o valor deve ser definido como 2. O badgingLevel deve corresponder ao número de imagens de selo relacionadas a especialistas listadas para a propriedade badgingPath. O padrão é 1. |
| badgingType | Sequência de caracteres | (Obrigatório) Identifica o mecanismo de pontuação como &quot;básico&quot; ou &quot;avançado&quot;. Definido como &quot;avançado&quot;; caso contrário, o padrão é &quot;básico&quot;. |
| regras de pontuação | Sequência de caracteres[] | (Opcional) Uma string com vários valores para restringir a regra de selo aos eventos de pontuação identificados pela(s) regra(s) de pontuação listada(s). Exemplo:/etc/community/scoring/rules/-comments-scoringDefault não é restrição. |

## Regras e emblema incluídos {#included-rules-and-badge}

### Símbolo incluído {#included-badge}

Incluído nesta versão beta, há um selo de especialista baseado em recompensa:

* especialista

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Para que o selo de especialista apareça como uma recompensa pela atividade, há duas coisas que devem acontecer:

* `badges` deve estar habilitado para o recurso, como um fórum ou componente de QnA
* regras avançadas de pontuação e marcação devem ser aplicadas à página (ou ancestral) na qual o componente é colocado

Consulte as informações básicas para:

* [Ativar a marcação para um componente](implementing-scoring.md#enable-badges-for-component)
* [Aplicar regras](implementing-scoring.md#apply-rules-to-content)

### Regras e subregras de pontuação incluídas {#included-scoring-rules-and-sub-rules}

Incluídas na versão beta estão duas regras de pontuação avançadas para a [função de fórum](functions.md#forum-function) (uma para cada componente do fórum e comentários do recurso de fórum):

1. /etc/community/scoring/rules/-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/-comments-rule

      /etc/community/scoring/rules/sub-rules/key-vote-rule-owner

      /etc/community/scoring/rules/sub-rules/chave-votação-regra

2. /etc/community/scoring/rules/-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/chave-forums-rule

      /etc/community/scoring/rules/sub-rules/-comments-rule

      /etc/community/scoring/rules/sub-rules/key-vote-rule-owner

**Notas:**

* Os nós `rules`e `sub-rules` são do tipo `cq:Page`
* `subRules` é um atributo do tipo [] String no  `jcr:content` nó da regra
* `sub-rules` pode ser compartilhado entre várias regras de pontuação
* `rules` deve estar localizado em um local de repositório com permissão de leitura para todos
   * os nomes das regras devem ser exclusivos, independentemente da localização

### Regras de marcação incluídas {#included-badging-rules}

Incluídas na versão estão duas regras de classificação avançadas que correspondem aos [fóruns avançados e regras de pontuação de comentários](#included-scoring-rules-and-sub-rules).

* /etc/community/badging/rules/-comments-badging
* /etc/community/badging/rules/-forums-badging

**Notas:**

* `rules` nós são do tipo  `cq:Page`
* `rules`deve estar localizado em um local de repositório com permissão de leitura para todos
   * os nomes das regras devem ser exclusivos, independentemente da localização
