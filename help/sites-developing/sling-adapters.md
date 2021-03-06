---
title: Uso de adaptadores Sling
seo-title: Using Sling Adapters
description: O Sling oferece um padrão de Adaptador para traduzir convenientemente objetos que implementam a interface Adaptável
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: 31d6111a82a3cbfef22970d05280b0d3fd1c0de7
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 14%

---

# Uso de adaptadores Sling{#using-sling-adapters}

[](https://sling.apache.org) O Slingoffer oferece um  [padrão de ](https://sling.apache.org/site/adapters.html) Adaptador para traduzir convenientemente objetos que implementam a interface  [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) Adaptável. Essa interface fornece um método genérico [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) que traduzirá o objeto para o tipo de classe que está sendo passado como argumento.

Por exemplo, para traduzir um objeto de Recurso para o objeto Nó correspondente, basta fazer:

```java
Node node = resource.adaptTo(Node.class);
```

## Casos de uso {#use-cases}

Há os seguintes casos de uso:

* Obter objetos específicos de implementação.

   Por exemplo, uma implementação baseada em JCR da interface genérica [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) fornece acesso ao JCR subjacente [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Criação de atalhos de objetos que exigem que objetos de contexto internos sejam passados.

   Por exemplo, o [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) baseado em JCR contém uma referência para o [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) da solicitação, que, por sua vez, é necessário para muitos objetos que funcionarão com base na sessão da solicitação, como o [`PageManager`](https://helpx.adobe.com/br/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) ou [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Atalho para serviços.

   Um caso raro - `sling.getService()` também é simples.

### Valor de Retorno Nulo {#null-return-value}

`adaptTo()` pode retornar nulo.

Há várias razões para isso, incluindo:

* a implementação não suporta o tipo de alvo
* uma fábrica de adaptadores que manipula este caso não está ativa (por exemplo, devido à falta de referências de serviço)
* falha na condição interna
* serviço não disponível

É importante lidar com o caso nulo normalmente. Para renderizações de jsp, pode ser aceitável ter a falha de jsp se isso resultar em um conteúdo vazio.

### Armazenamento em cache {#caching}

Para melhorar o desempenho, as implementações podem armazenar em cache o objeto retornado de uma chamada `obj.adaptTo()`. Se `obj` for o mesmo, o objeto retornado será o mesmo.

Esse armazenamento em cache é executado para todos os casos baseados em `AdapterFactory`.

No entanto, não há regra geral - o objeto pode ser uma nova instância ou uma existente. Isso significa que você não pode depender de nenhum dos comportamentos. Portanto, é importante, especialmente dentro de `AdapterFactory`, que os objetos sejam reutilizáveis neste cenário.

### Como funciona {#how-it-works}

Há várias maneiras de implementar `Adaptable.adaptTo()`:

* Pelo próprio objeto; implementação do próprio método e mapeamento para determinados objetos.
* Por um [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), que pode mapear objetos arbitrários.

   Os objetos ainda devem implementar a interface `Adaptable` e devem estender [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (que passa a chamada `adaptTo` para um gerenciador central de adaptadores).

   Isso permite que os ganchos sejam conectados ao mecanismo `adaptTo` para classes existentes, como `Resource`.

* Uma combinação de ambos.

No primeiro caso, o javadocs pode indicar o que `adaptTo-targets` é possível. No entanto, para subclasses específicas, como o Recurso baseado em JCR, geralmente isso não é possível. No último caso, as implementações de `AdapterFactory` normalmente fazem parte das classes privadas de um pacote e, portanto, não são expostas em uma API do cliente, nem listadas em javadocs. Teoricamente, seria possível acessar todas as implementações `AdapterFactory` do tempo de execução do serviço [OSGi](/help/sites-deploying/configuring-osgi.md) e examinar suas configurações &quot;adaptáveis&quot; (fontes e alvos), mas não mapeá-las umas às outras. No fim, isso depende da lógica interna, que deve ser documentada. Daí esta referência.

## Referência {#reference}

### Sling {#sling}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) O recurso se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nó</a></td> 
   <td>Se esse for um recurso baseado em nó JCR ou uma propriedade JCR que faz referência a um nó.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Propriedade</a></td> 
   <td>Se esse for um recurso baseado em propriedade do JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td> 
   <td>Se esse for um recurso baseado em JCR (nó ou propriedade).</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Mapa</a></td> 
   <td>Retorna um mapa das propriedades, se este for um recurso baseado em nó JCR (ou outro recurso que suporta mapas de valor).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>Retorna um mapa conveniente das propriedades, se for um recurso baseado em nó JCR (ou outro recurso que suporta mapas de valor). Também pode ser alcançado (mais simplesmente) usando<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (lida com letras maiúsculas e minúsculas, etc.).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td> 
   <td>Extensão de <a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> que permite que a hierarquia de recursos seja levada em conta ao procurar propriedades.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>Se esse for um recurso baseado em nó JCR e o usuário tiver permissões para modificar propriedades nesse nó.<br /> Observação: vários mapas persistentes não compartilham seus valores.</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>Retorna o conteúdo binário de um "arquivo"<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) ResourceResolveradapts a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessão</a></td> 
   <td>A sessão JCR da solicitação, se for um resolvedor de recursos baseado em JCR (padrão).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>Com base na sessão JCR, se este for um resolvedor de recursos baseado em JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>Com base na sessão JCR, se este for um resolvedor de recursos baseado em JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>Com base na sessão JCR, se este for um resolvedor de recursos baseado em JCR e se o usuário tiver permissões para acessar o UserManager.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Autorizável</a> </td> 
   <td>O usuário atual.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">Usuário</a><br /> </td> 
   <td>O usuário atual.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">PrivilegeManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">Preferências</a></td> 
   <td>Preferências do usuário atual (com base na sessão JCR, se este for um resolvedor de recursos baseado em JCR).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">PreferencesService</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">Externalizador</a></td> 
   <td>Para exteriorizar URLs absolutos, mesmo sem o objeto de solicitação.<br /> </td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequestadapts a:

Nenhum destino ainda, mas implementa Adaptável e pode ser usado como fonte em um AdapterFactory personalizado.

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponseadapts para:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br />  (XML)</td> 
   <td>Se esta for uma resposta de gravação de sling.</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) Pageadapts para:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Recurso</a><br /> </td> 
   <td>Recurso da página.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">RotuladoRecurso</a></td> 
   <td>Rótulo de recurso (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nó</a></td> 
   <td>Nó da página.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Tudo que o recurso da página pode ser adaptado.</td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/br/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) Os componentes se adaptam a:

| [Recurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso do componente. |
|---|---|
| [RotuladoRecurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Rótulo de recurso (== this). |
| [Nó](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nó do componente. |
| ... | Tudo que o recurso do componente pode ser adaptado. |

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) O modelo se adapta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Recurso</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>Recurso do modelo.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">RotuladoRecurso</a></td> 
   <td>Rótulo de recurso (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nó</a></td> 
   <td>Nó desse template.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Tudo que o recurso do modelo pode ser adaptado.</td> 
  </tr> 
 </tbody> 
</table>

#### Segurança {#security}

[**Autorizável**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html),  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) Utilizador e  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) Agrupamento

| [Nó](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Retorna o nó inicial do usuário/grupo. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Retorna o status de replicação do nó inicial do usuário/grupo. |

#### DAM {#dam}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) O ativo se adapta a:

| [Recurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso do ativo. |
|---|---|
| [Nó](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nó do ativo. |
| ... | Tudo o que o recurso do ativo pode ser adaptado. |

#### Marcação com tags {#tagging}

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) As tags se adaptam a:

| [Recurso](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Recurso da tag. |
|---|---|
| [Nó](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nó da tag. |
| ... | Tudo que o recurso da tag pode ser adaptado. |

#### Outro {#other}

Além disso, Sling / JCR / OCM também fornece um ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` para objetos MAC personalizados ([Mapeamento de conteúdo do objeto](https://jackrabbit.apache.org/object-content-mapping.html)).
