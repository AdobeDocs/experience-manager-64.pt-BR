---
title: Estrutura de marcação do AEM
seo-title: AEM Tagging Framework
description: Adicionar tags ao conteúdo e aproveitar a infraestrutura de marcação de AEM
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: 381e760d1634dec6c6cdb933fd4da6b4652e6ff7
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 0%

---

# Estrutura de marcação do AEM{#aem-tagging-framework}

Para marcar o conteúdo e aproveitar a infraestrutura de marcação de AEM :

* A tag deve existir como um nó do tipo [`cq:Tag`](#tags-cq-tag-node-type) nos termos do [nó raiz da taxonomia.](#taxonomy-root-node)
* O nó de conteúdo marcado `NodeType` deve incluir o [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mistura.
* O [TagID](#tagid) é adicionado ao nó de conteúdo [`cq:tags`](#tagged-content-cq-tags-property) e resolve para um nó do tipo [`cq:Tag`.](#tags-cq-tag-node-type)

## Tags : cq:Tag Node Type  {#tags-cq-tag-node-type}

A declaração de uma tag é capturada no repositório em um nó do tipo `cq:Tag.`

Uma tag pode ser uma palavra simples (por exemplo, `fruit`) ou representar uma taxonomia hierárquica (por exemplo, `fruit/apple`, ou seja, frutos em geral e maçã mais específica).

As tags são identificadas por uma TagID exclusiva.

Uma tag tem meta informações opcionais, como um título, títulos localizados e uma descrição. O título deve ser exibido nas interfaces do usuário em vez de `TagID`, quando presente.

A estrutura de marcação também fornece a capacidade de restringir autores e visitantes do site a usar somente tags específicas e predefinidas.

### Características da tag {#tag-characteristics}

* O tipo de nó é `cq:Tag`.
* O nome do nó é um componente do [`TagID`.](#tagid)
* O [`TagID`](#tagid) sempre inclui uma [namespace.](#tag-namespace)
* Opcional `jcr:title` propriedade (o título a ser exibido na interface do usuário)
* Opcional `jcr:description` propriedade
* Ao conter nós filho, ele é chamado de [tag container.](#container-tags)
* Ele é armazenado no repositório abaixo de um caminho base chamado [nó raiz da taxonomia.](#taxonomy-root-node)

### TagID {#tagid}

A `TagID` identifica um caminho que resolve um nó de tag no repositório.

Normalmente, a variável `TagID` é um encurtamento que começa com o namespace ou pode ser absoluto a partir do [nó raiz da taxonomia](#taxonomy-root-node).

Quando o conteúdo é marcado, se ainda não existir, a variável [`cq:tags`](#tagged-content-cq-tags-property) é adicionada ao nó de conteúdo e a variável `TagID` é adicionado ao valor da matriz da string da propriedade.

O `TagID` consiste em um [namespace](#tag-namespace) seguido pelo `TagID`. [Tags do contêiner](#container-tags) têm subtags que representam uma ordem hierárquica na taxonomia. As subtags podem ser usadas para referenciar tags da mesma forma que qualquer `TagID`. Por exemplo, marcar conteúdo com `fruit` é permitido, mesmo que seja uma tag container com subtags , como `fruit/apple` e `fruit/banana`.

### Nó raiz da taxonomia {#taxonomy-root-node}

O nó raiz da taxonomia é o caminho base para todas as tags no repositório. O nó raiz da taxonomia não deve ser do tipo `cq:Tag`.

Em AEM, o caminho base é `/content/cq:tags` e o nó raiz é do tipo `cq:Folder`.

### Namespace de tag {#tag-namespace}

Os namespaces permitem agrupar itens. O caso de uso mais comum é ter um namespace por site (por exemplo, público, interno e portal) ou por aplicativo maior (por exemplo, Sites, Assets, Forms), mas os namespaces podem ser usados para várias outras necessidades. Os namespaces são usados na interface do usuário para mostrar apenas o subconjunto de tags (ou seja, tags de um determinado namespace) que é aplicável ao conteúdo atual.

O namespace da tag é o primeiro nível na subárvore da taxonomia, que é o nó imediatamente abaixo do [nó raiz da taxonomia](#taxonomy-root-node). Um namespace é um nó do tipo `cq:Tag` cujo pai não é um `cq:Tag` tipo de nó.

Todas as tags têm um namespace. Se nenhum namespace for especificado, a tag será atribuída ao namespace padrão, que é `TagID` `default` (o título é `Standard Tags`) que `/content/cq:tags/default`.

### Tags do contêiner {#container-tags}

Uma tag container é um nó do tipo `cq:Tag` contendo qualquer número e tipo de nós filhos, o que possibilita aprimorar o modelo de tags com metadados personalizados.

Além disso, tags de contêiner (ou supertags) em uma taxonomia servem como subsoma de todas as subtags. Por exemplo, conteúdo marcado com `fruit/apple` é considerado como marcado com `fruit` também. Isso significa que a pesquisa de conteúdo foi apenas marcada com `fruit` também encontraria o conteúdo marcado com `fruit/apple`.

### Resolvendo TagIDs {#resolving-tagids}

Se a ID da tag contiver dois pontos `:`, o sinal de dois pontos separa o namespace da tag ou da subtaxonomia, que são então separadas por barras normais `/`. Se a ID da tag não tiver dois pontos, o namespace padrão será implícito.

O local padrão e único das tags está abaixo `/content/cq:tags`.

Tag que faz referência a caminhos ou caminhos não existentes que não apontam para um `cq:Tag` são considerados inválidos e são ignorados.

A tabela a seguir mostra algumas amostras `TagIDs`, seus elementos e como a função `TagID` resolve para um caminho absoluto no repositório.

| `TagID` | Namespace | ID local | Tags do contêiner | Tag Folha | Caminho absoluto do repositório |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Nenhum | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Nenhum | Nenhum | Nenhum | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localização do título da tag {#localization-of-tag-title}

Quando a tag inclui a string de título opcional (`jcr:title`) é possível localizar o título para exibição ao adicionar a propriedade `jcr:title.<locale>`.

Para obter mais detalhes, consulte:

* [Tags em diferentes idiomas,](/help/sites-developing/building.md#tags-in-different-languages) que descreve o uso das APIs.
* [Gerenciamento de tags em diferentes idiomas,](/help/sites-administering/tags.md#managing-tags-in-different-languages) que descreve o uso do console Marcação .

### Controle de acesso {#access-control}

As tags existem como nós no repositório no [nó raiz da taxonomia.](#taxonomy-root-node) Permitir ou negar aos autores e visitantes do site a capacidade de criar tags em um determinado namespace pode ser obtido definindo ACLs apropriadas no repositório.

Além disso, negar permissões de leitura para determinadas tags ou namespaces controlará a capacidade de aplicar tags a conteúdo específico.

Uma configuração típica inclui:

* Permitir o `tag-administrators` acesso de gravação de grupo/função para todos os namespaces (adicionar/modificar em `/content/cq:tags`).
   * Este grupo vem com AEM pronto para uso.
* Permitir que usuários/autores leiam o acesso a todos os namespaces que devem ser legíveis a eles (em sua maioria, todos).
* Permitir que usuários/autores gravem acesso aos namespaces, onde as tags devem ser livremente definidas por usuários/autores (`add_node` under `/content/cq:tags/some_namespace`)

## Conteúdo marcável : cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

Para que os desenvolvedores de aplicativos anexem tags a um tipo de conteúdo, o registro do nó ([CND](https://jackrabbit.apache.org/node-type-notation.html)) deve incluir o `cq:Taggable` mistura ou o `cq:OwnerTaggable` mistura.

O `cq:OwnerTaggable` mixin, que herda de `cq:Taggable`, destina-se a indicar que o conteúdo pode ser classificado pelo proprietário/autor. No AEM, é apenas um atributo do `cq:PageContent` nó . O `cq:OwnerTaggable` a mixin não é exigida pela estrutura de marcação.

>[!NOTE]
>
>Recomenda-se ativar somente as tags no nó de nível superior de um item de conteúdo agregado (ou em seu `jcr:content` nó ). Os exemplos incluem:
>
>* Páginas ( `cq:Page`) em que `jcr:content`o nó é do tipo `cq:PageContent` que inclui `cq:Taggable` mistura.
>* Ativos ( `cq:Asset`) em que `jcr:content/metadata` o nó sempre tem o `cq:Taggable` mistura.


### Notação de tipo de nó (CND) {#node-type-notation-cnd}

As definições de Tipo de nó existem no repositório como arquivos CND. A notação CND é definida como parte da documentação JCR. [here](https://jackrabbit.apache.org/node-type-notation.html).

As definições essenciais para os Tipos de nó incluídos no AEM são as seguintes:

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Conteúdo marcado: cq:tags Propriedade {#tagged-content-cq-tags-property}

O `cq:tags` é uma matriz de string usada para armazenar um ou mais `TagID`s quando forem aplicadas ao conteúdo por autores ou visitantes do site. A propriedade só tem significado quando adicionada a um nó que é definido com a variável [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mistura.

>[!NOTE]
>
>Para aproveitar AEM funcionalidade de marcação, os aplicativos desenvolvidos e personalizados não devem definir outras propriedades de tag além de `cq:tags`.

## Mover e mesclar tags {#moving-and-merging-tags}

Veja a seguir uma descrição dos efeitos no repositório ao mover ou mesclar tags usando o [Console de marcação](/help/sites-administering/tags.md):

* Quando uma tag A é movida ou unida na tag B em `/content/cq:tags`:

   * A tag A não é excluída e obtém uma `cq:movedTo` propriedade.
   * A tag B é criada (no caso de uma movimentação) e obtém um `cq:backlinks` propriedade.

* `cq:movedTo` aponta para a tag B.

   * Essa propriedade significa que a tag A foi movida ou mesclada na tag B.
   * A tag B movida atualizará essa propriedade de acordo. A tag A é então oculta e é mantida somente no repositório para resolver IDs de tag em nós de conteúdo que apontam para a tag A.
   * O coletor de lixo da tag remove tags como a tag A, uma vez que mais nós de conteúdo apontam para elas.
   * Um valor especial para a variável `cq:movedTo` a propriedade é `nirvana`: ela é aplicada quando a tag é excluída, mas não pode ser removida do repositório porque há subtags com uma `cq:movedTo` isso tem de ser mantido.

      >[!NOTE]
      >
      >O `cq:movedTo` só será adicionada à tag movida ou unida se uma dessas condições for atendida:
      >
      >1. A tag é usada no conteúdo (o que significa que ela tem uma referência).
      >1. A tag tem filhos que já foram movidos.


* `cq:backlinks` mantém as referências na outra direção, ou seja, mantém uma lista de todas as tags que foram movidas para ou mescladas com a tag B.

   * Isso é necessário principalmente para manter `cq:movedTo`propriedades atualizadas quando a tag B for movida/mesclada/excluída também ou quando a tag B for ativada, nesse caso todas as tags de backlinks também deverão ser ativadas.

>[!NOTE]
>
>O `cq:backlinks` só será adicionada à tag movida ou unida se uma dessas condições for atendida:
>
>1. A tag é usada no conteúdo (o que significa que ela tem uma referência).
>1. A tag tem filhos que já foram movidos.


* Ler um `cq:tags` a propriedade de um nó de conteúdo envolve a seguinte resolução:

   1. Se não houver correspondência em `/content/cq:tags`, nenhuma tag é retornada.
   1. Se a tag tiver uma `cq:movedTo` do conjunto de propriedades, a ID da tag referenciada é seguida.

      * Essa etapa é repetida, desde que a tag seguida tenha uma `cq:movedTo` propriedade.
   1. Se a tag seguida não tiver uma `cq:movedTo` , a tag será lida.


* Para publicar a alteração quando uma tag tiver sido movida ou mesclada, a variável `cq:Tag` e todos os seus backlinks devem ser replicados.
   * Isso é feito automaticamente quando a tag é ativada no console de administração de tags.

* Atualizações posteriores no `cq:tags` limpa automaticamente as referências &quot;antigas&quot;.
   * Isso é acionado porque a resolução de uma tag movida pela API retorna a tag de destino, fornecendo a ID da tag de destino.

## Migração de tags {#tags-migration}

No Adobe Experience Manager 6.4 em diante, as tags são armazenadas em `/content/cq:tags`. No entanto, em cenários em que o Adobe Experience Manager foi atualizado da versão anterior, as tags ainda estão presentes no local antigo `/etc/tags`. Em sistemas atualizados, as tags precisam ser migradas para `/content/cq:tags`.

>[!NOTE]
>
>Na página Propriedades da página de tags, é recomendável usar a ID da tag (por exemplo, `geometrixx-outdoors:activity/biking`) em vez de codificar o caminho base da tag (por exemplo, `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Para listar tags, `com.day.cq.tagging.servlets.TagListServlet` pode ser usada.

>[!NOTE]
>
>É recomendável usar a API do gerenciador de tags como recurso.

### Se a instância AEM atualizada suportar a API do TagManager**

1. No início do componente, a API do TagManager detecta se é uma instância de AEM atualizada. No sistema atualizado, as tags são armazenadas em `/etc/tags`.

1. A API do TagManager é executada no modo de compatibilidade anterior, o que significa que a API usa `/etc/tags` como o caminho base. Caso contrário, ele usará uma nova localização `/content/cq:tags`.

1. Atualize o local das tags.

1. Depois de migrar as tags para o novo local, execute o script a seguir.

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

O script busca todas as tags que têm `/etc/tags` no valor de `cq:movedTo/cq:backLinks` propriedade. Em seguida, ele repete por meio do conjunto de resultados buscados e resolve a variável `cq:movedTo` e `cq:backlinks` valores de propriedade para `/content/cq:tags` caminhos (no caso em que `/etc/tags` é detectado no valor).

### Se a atualização da instância AEM for executada na interface clássica**

>[!NOTE]
>
>A interface do usuário clássica não é compatível com tempo de inatividade zero e não é compatível com o novo caminho de base de tags. Se você quiser usar a interface clássica do que `/etc/tags` precisa ser criada, seguido de `cq-tagging` reinicialização do componente.

Caso as instâncias de AEM atualizadas sejam compatíveis com a API do TagManager e sejam executadas na interface clássica:

1. Uma vez, referências ao caminho base da tag antiga `/etc/tags` são substituídos por tagId ou nova localização de tag `/content/cq:tags`, você pode migrar tags para o novo local `/content/cq:tags` no CRX DE, seguido pela reinicialização do componente.

1. Depois de migrar as tags para o novo local, execute o script acima mencionado.
