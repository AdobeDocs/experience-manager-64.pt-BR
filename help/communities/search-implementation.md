---
title: Search Essentials
seo-title: Search Essentials
description: Pesquisar em comunidades
seo-description: Pesquisar em comunidades
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 5%

---


# Search Essentials {#search-essentials}

## Visão geral {#overview}

O recurso de pesquisa é um recurso essencial do AEM Communities. Além dos recursos [AEM pesquisa de plataforma](../../help/sites-deploying/queries-and-indexing.md), a AEM Communities fornece a [API de pesquisa UGC](#ugc-search-api) para fins de pesquisa de conteúdo gerado pelo usuário (UGC). O UGC tem propriedades exclusivas à medida que é inserido e armazenado separadamente de outro conteúdo AEM e dados do usuário.

Para Comunidades, as duas coisas geralmente pesquisadas são:

* Conteúdo postado por membros da comunidade

   * Usa a API de pesquisa UGC do AEM Communities

* Usuários e grupos de usuários (dados do usuário)

   * Usa os recursos de pesquisa da plataforma AEM

Esta seção da documentação é de interesse para desenvolvedores que estão criando componentes personalizados que criam ou gerenciam o UGC.

## Nós de segurança e sombra {#security-and-shadow-nodes}

Para um componente personalizado, é necessário usar os métodos [SocialResourceUtilities](socialutils.md#socialresourceutilities-package). Os métodos de utilitários que criam e pesquisam por UGC estabelecerão os [nós de sombra](srp.md#about-shadow-nodes-in-jcr) necessários e garantirão que o membro tenha as permissões corretas para a solicitação.

O que não é gerenciado pelos utilitários SRP são propriedades relacionadas à moderação.

Consulte [SRP e UGC Essentials](srp-and-ugc.md) para obter informações sobre métodos de utilitários usados para acessar nós de sombra UGC e ACL.

## API de pesquisa UGC {#ugc-search-api}

O [repositório comum UGC](working-with-srp.md) é fornecido por um dos provedores de recursos de armazenamentos (SRPs), cada um com possivelmente uma linguagem de query nativa diferente. Portanto, independentemente do SRP escolhido, o código personalizado deve usar métodos do [pacote da API UGC](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) que chamarão a linguagem do query apropriada para o SRP escolhido.

### Pesquisas ASRP {#asrp-searches}

Para [ASRP](asrp.md), o UGC é armazenado na nuvem do Adobe. Embora o UGC não esteja visível no CRX, [moderação](moderate-ugc.md) está disponível nos ambientes de autor e publicação. O uso da [API de pesquisa UGC](#ugc-search-api) funciona para o ASRP da mesma forma que para outros SRPs.

Atualmente, não existem ferramentas para gerenciar pesquisas ASRP.

Ao criar propriedades personalizadas que podem ser pesquisadas, é necessário seguir os [requisitos de nomenclatura](#naming-of-custom-properties).

### Pesquisas do MSRP {#msrp-searches}

Para [MSRP](msrp.md), o UGC é armazenado no MongoDB configurado para usar o Solr para pesquisa. O UGC não estará visível no CRX, mas [moderação](moderate-ugc.md) está disponível nos ambientes de autor e publicação.

Relativamente ao MSRP e ao Solr:

* A Solr integrada para a plataforma AEM não é usada para MSRP
* Se estiver usando um Solar remoto para a plataforma AEM, ele poderá ser compartilhado com o MSRP, mas deverá usar coleções diferentes
* O Solr pode ser configurado para pesquisa padrão ou para pesquisa multilíngue (MLS)
* Para obter detalhes sobre a configuração, consulte [Configuração Solr](msrp.md#solr-configuration) para MSRP

Os recursos de pesquisa personalizados devem usar a [API de pesquisa UGC](#ugc-search-api).

Ao criar propriedades personalizadas que podem ser pesquisadas, é necessário seguir os [requisitos de nomenclatura](#naming-of-custom-properties).

### Pesquisas do JSRP {#jsrp-searches}

Para [JSRP](jsrp.md), o UGC é armazenado em [Oak](../../help/sites-deploying/platform.md) e está visível apenas no repositório da instância de autor ou publicação AEM na qual foi inserido.

Como o UGC normalmente é inserido no ambiente de publicação, para sistemas de produção de vários editores, é necessário configurar um [cluster de publicação](topologies.md), não um farm de publicação, para que o conteúdo inserido seja visível de todos os editores.

Para JSRP, o UGC inserido no ambiente de publicação nunca estará visível no ambiente do autor. Assim, todas as tarefas [moderação](moderate-ugc.md) ocorrem no ambiente de publicação.

Os recursos de pesquisa personalizados devem usar a [API de pesquisa UGC](#ugc-search-api).

#### Indexação Oak {#oak-indexing}

Embora os índices Oak não sejam criados automaticamente para a pesquisa da plataforma AEM, a partir do AEM 6.2 eles foram adicionados à AEM Communities para melhorar o desempenho e fornecer suporte para paginação ao apresentar resultados de pesquisa UGC.

Se as propriedades personalizadas estiverem em uso e as pesquisas estiverem lentas, será necessário criar índices adicionais para que as propriedades personalizadas sejam mais eficientes. Para manter a portabilidade, siga os [requisitos de nomenclatura](#naming-of-custom-properties) ao criar propriedades personalizadas que podem ser pesquisadas.

Para modificar índices existentes ou criar índices personalizados, consulte [Query Oak e Indexação](../../help/sites-deploying/queries-and-indexing.md).

O [Oak Index Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) está disponível no ACS AEM Commons. Ele fornece:

* Uma visualização de índices existentes
* A capacidade de iniciar a reindexação

Para visualização dos índices Oak existentes em [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md), o local é:

* `/oak:index/socialLucene`

![chlimage_1-235](assets/chlimage_1-235.png)

## Propriedades de pesquisa indexadas {#indexed-search-properties}

### Propriedades de pesquisa padrão {#default-search-properties}

Veja a seguir algumas das propriedades pesquisáveis usadas para vários recursos das Comunidades:

| **Propriedade** | **Tipo de dados** |
|---|---|
| isFlagged | *Booleano* |
| isSpam | *Booleano* |
| leitura | *Booleano* |
| influência | *Booleano* |
| anexos | *Booleano* |
| sentimento | *Longo* |
| sinalizado | *Booleano* |
| adicionado | *Data* |
| modifiedDate | *Data* |
| estado | *Sequência de caracteres* |
| userIdentifier | *Sequência de caracteres* |
| response | *Longo* |
| jcr:title | *Sequência de caracteres* |
| jcr:description | *Sequência de caracteres* |
| sling:resourceType | *Sequência de caracteres* |
| allowThreadedReply | *Booleano* |
| isDraft | *Booleano* |
| publishDate | *Data* |
| publishJobId | *Sequência de caracteres* |
| respondido | *Booleano* |
| escolhido | *Booleano* |
| tag | *Sequência de caracteres* |
| cq:Tag | *Sequência de caracteres* |
| author_display_name | *Sequência de caracteres* |
| location_t | *Sequência de caracteres* |
| parentPath | *Sequência de caracteres* |
| parentTitle | *Sequência de caracteres* |

### Nomeação de propriedades personalizadas {#naming-of-custom-properties}

Ao adicionar propriedades personalizadas, para que essas propriedades fiquem visíveis para as classificações e pesquisas criadas com a [API de pesquisa UGC](#ugc-search-api), é *obrigatório *adicionar um sufixo ao nome da propriedade.

O sufixo é para idiomas de query que usam um schema:

* Ela identifica a propriedade como pesquisável
* Identifica o tipo de dados

Solr é um exemplo de uma linguagem de query que usa um schema.

| **Sufixo** | **Tipo de dados** |
|---|---|
| _b | *Booleano* |
| _dt | *Calendário* |
| _d | *Duplo* |
| _tl | *Longo* |
| _s | *Sequência de caracteres* |
| _t | *Texto* |

**Notas:**

* *O* texto é uma string tokenizada,  ** Stringis não. Use *Texto* para pesquisas difusas (mais parecidas com esta).

* Para tipos de valores múltiplos, adicione &quot;s&quot; ao sufixo, por exemplo:

   * `viewDate_dt`: propriedade de data única
   * `viewDates_dts`: propriedade lista de datas

## Filtros {#filters}

Os componentes que incluem o [sistema de comentários](essentials-comments.md) suportam a adição do parâmetro de filtro aos respectivos pontos finais.

A sintaxe de filtro para a lógica E e OU é expressa da seguinte forma (mostrada antes de ser codificada para URL):

* Para especificar OU use um parâmetro de filtro com valores separados por vírgula:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* Para especificar E usar vários parâmetros de filtro:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

A implementação padrão do [componente de pesquisa](search.md) usa essa sintaxe, como pode ser visto no URL que abre a página Resultados da pesquisa no [guia Componentes da comunidade](components-guide.md). Para experimentar, navegue até [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

Os operadores de filtro são:

| EQ | igual |
|---|---|
| NE | não é igual |
| LT | menor que |
| LTE | menor que ou igual a |
| GE | maior que |
| GTE | maior que ou igual a |
| CURTIR | correspondência difusa |

É importante que o URL faça referência ao componente Comunidades (recurso) e não à página na qual o componente é colocado:

* Correto: componente do fórum
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Incorreto: página do fórum
   * `/content/community-components/en/forum.social.json`

## Ferramentas SRP {#srp-tools}

Existe um projeto Adobe Marketing Cloud GitHub que contém:

[Ferramentas do AEM Communities SRP](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Esse repositório contém ferramentas para gerenciar dados no SRP.

Atualmente, existe um servlet que oferece a capacidade de excluir todo o UGC de qualquer SRP.

Por exemplo, para excluir todo o UGC no ASRP:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Resolução de problemas {#troubleshooting}

### Query Solr {#solr-query}

Para ajudar a solucionar problemas com um query Solr, ative o registro DEBUG para

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

O query Solr real será exibido no URL codificado no log de depuração:

O query a ser resolvido é: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

O valor do parâmetro `q` é o query. Depois que a codificação do URL é decodificada, o query pode ser passado para a ferramenta Solr Admin Query para depuração adicional.

## Recursos relacionados {#related-resources}

* [Armazenamento](working-with-srp.md)  de conteúdo da comunidade - discute as opções de SRP disponíveis para uma loja comum UGC
* [Visão geral](srp.md)  do provedor de recursos do armazenamento - Introdução e visão geral de uso do repositório
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md)  - Diretrizes de codificação
* [Refatoração](socialutils.md)  SocialUtilitários - Métodos de utilitário para SRP que substituem o SocialUtils
* [Componentes](search.md)  de Pesquisa e Resultados de Pesquisa - Adicionar recurso de pesquisa UGC a um modelo

