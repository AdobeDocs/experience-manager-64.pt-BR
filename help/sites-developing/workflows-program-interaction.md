---
title: Interação com fluxos de trabalho programaticamente
description: Saiba mais sobre como gerenciar Workflows e interagir programaticamente com Workflows usando APIs e scripts.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: da06850a-c4d5-44dd-b572-771e3b2a66c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2051'
ht-degree: 1%

---

# Interação com fluxos de trabalho programaticamente{#interacting-with-workflows-programmatically}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

When [personalização e extensão dos workflows](/help/sites-developing/workflows-customizing-extending.md) é possível acessar objetos de fluxo de trabalho:

* [Uso da API Java de fluxo de trabalho](#using-the-workflow-java-api)
* [Obter objetos de fluxo de trabalho em scripts ECMA](#obtaining-workflow-objects-in-ecma-scripts)
* [Uso da API REST do fluxo de trabalho](#using-the-workflow-rest-api)

## Uso da API Java de fluxo de trabalho {#using-the-workflow-java-api}

A API Java do fluxo de trabalho consiste na variável [`com.adobe.granite.workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/package-summary.html) e vários subpacotes. O membro mais importante da API é o `com.adobe.granite.workflow.WorkflowSession` classe . O `WorkflowSession` A classe fornece acesso a objetos de fluxo de trabalho de tempo de design e de tempo de execução:

* modelos de fluxo de trabalho
* itens de trabalho
* instâncias de fluxo de trabalho
* dados do workflow
* itens da caixa de entrada

A classe também fornece vários métodos para intervir em ciclos de vida do workflow.

A tabela a seguir fornece links para a documentação de referência de vários objetos principais do Java a serem usados ao interagir programaticamente com fluxos de trabalho. Os exemplos a seguir demonstram como obter e usar os objetos de classe no código.

| Recursos | Objetos |
|---|---|
| Acesso a um workflow | [`WorkflowSession`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html) |
| Execução e consulta de uma instância de workflow | [`Workflow`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/Workflow.html)</br>[`WorkItem`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkItem.html)</br>[`WorkflowData`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/exec/WorkflowData.html) |
| Gerenciamento de um modelo de fluxo de trabalho | [`WorkflowModel`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowModel.html)</br>[`WorkflowNode`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowNode.html)</br>[`WorkflowTransition`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/model/WorkflowTransition.html) |
| Informações para um nó que está no workflow (ou não) | [`WorkflowStatus`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) |

## Obter objetos de fluxo de trabalho em scripts ECMA {#obtaining-workflow-objects-in-ecma-scripts}

Conforme descrito em [Localização do script](/help/sites-developing/the-basics.md#locating-the-script), AEM (via Apache Sling) fornece um mecanismo de script ECMA que executa scripts ECMA do lado do servidor. O [`org.apache.sling.scripting.core.ScriptHelper`](https://sling.apache.org/apidocs/sling5/org/apache/sling/scripting/core/ScriptHelper.html) A classe está imediatamente disponível para seus scripts como `sling` variável.

O `ScriptHelper` fornece acesso à `SlingHttpServletRequest` que você pode usar para obter o `WorkflowSession` objeto; por exemplo:

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

## Uso da API REST do fluxo de trabalho {#using-the-workflow-rest-api}

O console Fluxo de trabalho utiliza pesadamente a REST API; assim, esta página descreve a REST API para fluxos de trabalho.

>[!NOTE]
>
>A ferramenta de linha de comando curl permite usar a API REST do fluxo de trabalho para acessar objetos do fluxo de trabalho e gerenciar ciclos de vida da instância. Os exemplos nesta página demonstram o uso da REST API através da ferramenta de linha de comando curl.

As seguintes ações são compatíveis com a REST API:

* iniciar ou parar um serviço de workflow
* criar, atualizar ou excluir modelos de fluxo de trabalho
* [iniciar, suspender, retomar ou encerrar instâncias de fluxo de trabalho](/help/sites-administering/workflows.md#workflow-status-and-actions)
* concluir ou delegar itens de trabalho

>[!NOTE]
>
>Ao usar o Firebug, uma extensão do Firefox para desenvolvimento na Web, é possível seguir o tráfego HTTP quando o console é operado. Por exemplo, você pode verificar os parâmetros e os valores enviados para o servidor de AEM com uma `POST` solicitação.

Nesta página, presume-se que AEM seja executado em localhost na porta `4502` e que o contexto de instalação é &quot; `/`&quot; (raiz). Se não for o caso de sua instalação, os URIs, aos quais as solicitações HTTP se aplicam, precisam ser adaptados adequadamente.

A renderização suportada para `GET` solicitações é a renderização JSON. Os URLs para `GET` deve ter `.json` , por exemplo:

`http://localhost:4502/etc/workflow.json`

### Gerenciamento de instâncias de fluxo de trabalho {#managing-workflow-instances}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/etc/workflow/instances`

<table> 
 <tbody> 
  <tr> 
   <td>método de solicitação HTTP</td> 
   <td>Ações</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>Lista as instâncias de fluxo de trabalho disponíveis.</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td><p>Cria uma nova instância de workflow. Os parâmetros são:<br /> - <code>model</code>: a ID (URI) do respectivo modelo de fluxo de trabalho<br /> - <code>payloadType</code>: contendo o tipo de carga (por exemplo, <code>JCR_PATH</code> ou URL).<br /> A carga é enviada como parâmetro <code>payload</code>. A <code>201</code> (<code>CREATED</code>) é enviada de volta com um cabeçalho de localização contendo o URL do novo recurso de instância de fluxo de trabalho.</p> </td> 
  </tr> 
 </tbody> 
</table>

#### Gerenciando uma Instância de Workflow pelo Estado {#managing-a-workflow-instance-by-its-state}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/etc/workflow/instances.{state}`

| método de solicitação HTTP | Ações |
|---|---|
| `GET` | Lista as instâncias de fluxo de trabalho disponíveis e seus estados ( `RUNNING`, `SUSPENDED`, `ABORTED` ou `COMPLETED`) |

#### Gerenciamento de uma instância de fluxo de trabalho pela ID {#managing-a-workflow-instance-by-its-id}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/etc/workflow/instances/{id}`

<table> 
 <tbody> 
  <tr> 
   <td>método de solicitação HTTP</td> 
   <td>Ações</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>Obtém os dados de instâncias (definição e metadados), incluindo o link para o respectivo modelo de fluxo de trabalho.</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>Altera o estado da instância. O novo estado é enviado como parâmetro <code>state</code> e devem ter um dos seguintes valores: <code>RUNNING</code>, <code>SUSPENDED</code>ou <code>ABORTED</code>.<br /> Se o novo estado não puder ser alcançado (por exemplo, ao suspender uma instância terminada), uma <code>409</code> (<code>CONFLICT</code>) é enviada de volta ao cliente.</td> 
  </tr> 
 </tbody> 
</table>

### Gerenciamento de modelos de fluxo de trabalho {#managing-workflow-models}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/etc/workflow/models`

<table> 
 <tbody> 
  <tr> 
   <td>método de solicitação HTTP</td> 
   <td>Ações</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>Lista os modelos de fluxo de trabalho disponíveis.</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>Cria um novo modelo de fluxo de trabalho. Se o parâmetro <code>title</code> for enviado, um novo modelo será criado com o título especificado. Anexar uma definição de modelo JSON como parâmetro <code>model</code> cria um novo modelo de fluxo de trabalho de acordo com a definição fornecida.<br /> A <code>201</code> resposta (<code>CREATED</code>) é enviada de volta com um cabeçalho de localização contendo o URL do novo recurso de modelo de fluxo de trabalho.<br /> O mesmo acontece quando uma definição de modelo é anexada como um parâmetro de arquivo chamado <code>modelfile</code>.<br /> Em ambos os casos do <code>model</code> e <code>modelfile</code> parâmetros, um parâmetro adicional chamado <code>type</code> é necessário para definir o formato de serialização. Novos formatos de serialização podem ser integrados usando a API OSGI. Um serializador JSON padrão é fornecido com o mecanismo de workflow. Seu tipo é JSON. Veja abaixo um exemplo do formato .</td> 
  </tr> 
 </tbody> 
</table>

Exemplo: no navegador, uma solicitação para `http://localhost:4502/etc/workflow/models.json` gera uma resposta json semelhante ao seguinte:

```
[
    {"uri":"/var/workflow/models/activationmodel"}
    ,{"uri":"/var/workflow/models/dam/adddamsize"}
    ,{"uri":"/var/workflow/models/cloudconfigs/dtm-reactor/library-download"}
    ,{"uri":"/var/workflow/models/ac-newsletter-workflow-simple"}
    ,{"uri":"/var/workflow/models/dam/dam-create-language-copy"}
    ,{"uri":"/var/workflow/models/dam/dam-create-and-translate-language-copy"}
    ,{"uri":"/var/workflow/models/dam-indesign-proxy"}
    ,{"uri":"/var/workflow/models/dam-xmp-writeback"}
    ,{"uri":"/var/workflow/models/dam-parse-word-documents"}
    ,{"uri":"/var/workflow/models/dam/process_subasset"}
    ,{"uri":"/var/workflow/models/dam/dam_set_last_modified"}
    ,{"uri":"/var/workflow/models/dam/dam-autotag-assets"}
    ,{"uri":"/var/workflow/models/dam/update_asset"}
    ,{"uri":"/var/workflow/models/dam/update_asset_offloading"}
    ,{"uri":"/var/workflow/models/dam/dam-update-language-copy"}
    ,{"uri":"/var/workflow/models/dam/update_from_lightbox"}
    ,{"uri":"/var/workflow/models/cloudservices/DTM_bundle_download"}
    ,{"uri":"/var/workflow/models/dam/dam_download_asset"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-encode-video"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-thumbnail-replacement"}
    ,{"uri":"/var/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail"}
    ,{"uri":"/var/workflow/models/newsletter_bounce_check"}
    ,{"uri":"/var/workflow/models/projects/photo_shoot_submission"}
    ,{"uri":"/var/workflow/models/projects/product_photo_shoot"}
    ,{"uri":"/var/workflow/models/projects/approval_workflow"}
    ,{"uri":"/var/workflow/models/prototype-01"}
    ,{"uri":"/var/workflow/models/publish_example"}
    ,{"uri":"/var/workflow/models/publish_to_campaign"}
    ,{"uri":"/var/workflow/models/screens/publish_to_author_bin"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_publish_to_youtube"}
    ,{"uri":"/var/workflow/models/projects/request_copy"}
    ,{"uri":"/var/workflow/models/projects/request_email"}
    ,{"uri":"/var/workflow/models/projects/request_landing_page"}
    ,{"uri":"/var/workflow/models/projects/request_launch"}
    ,{"uri":"/var/workflow/models/request_for_activation"}
    ,{"uri":"/var/workflow/models/request_for_deactivation"}
    ,{"uri":"/var/workflow/models/request_for_deletion"}
    ,{"uri":"/var/workflow/models/request_for_deletion_without_deactivation"}
    ,{"uri":"/var/workflow/models/request_to_complete_move_operation"}
    ,{"uri":"/var/workflow/models/reverse_replication"}
    ,{"uri":"/var/workflow/models/salesforce-com-export"}
    ,{"uri":"/var/workflow/models/scene7"}
    ,{"uri":"/var/workflow/models/scheduled_activation"}
    ,{"uri":"/var/workflow/models/scheduled_deactivation"}
    ,{"uri":"/var/workflow/models/screens/screens-update-asset"}
    ,{"uri":"/var/workflow/models/translation"}
    ,{"uri":"/var/workflow/models/s7dam/request_to_remove_from_youtube"}
    ,{"uri":"/var/workflow/models/wcm-translation/create_language_copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/prepare_translation_project"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-i18n-dictionary"}
    ,{"uri":"/var/workflow/models/wcm-translation/sync_translation_job"}
    ,{"uri":"/var/workflow/models/wcm-translation/translate-language-copy"}
    ,{"uri":"/var/workflow/models/wcm-translation/update_language_copy"}
]
```

#### Gerenciar um modelo de fluxo de trabalho específico {#managing-a-specific-workflow-model}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502*{uri}*`

Onde `*{uri}*` é o caminho para o nó modelo no repositório.

<table> 
 <tbody> 
  <tr> 
   <td>método de solicitação HTTP</td> 
   <td>Ações</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>Obtém a <code>HEAD</code> versão do modelo (definição e metadados).</td> 
  </tr> 
  <tr> 
   <td><code>PUT</code></td> 
   <td>Atualiza o <code>HEAD</code> versão do modelo (cria uma nova versão).<br /> A definição completa do modelo para a nova versão do modelo deve ser adicionada como parâmetro chamado <code>model</code>. Adicionalmente a <code>type</code> é necessário como ao criar novos modelos e precisa ter o valor <code>JSON</code>.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>Mesmo comportamento que com PUT. Necessário porque AEM widgets não são compatíveis <code>PUT</code> operações.</td> 
  </tr> 
  <tr> 
   <td><code>DELETE</code></td> 
   <td>Exclui o modelo. Para resolver problemas de firewall/proxy, uma <code>POST</code> que contém um <code>X-HTTP-Method-Override</code> entrada de cabeçalho com valor <code>DELETE</code> será também aceita como <code>DELETE</code> solicitação.</td> 
  </tr> 
 </tbody> 
</table>

Exemplo: no navegador, uma solicitação para `http://localhost:4502/var/workflow/models/publish_example.json` retorna um `json` que é semelhante ao seguinte código:

```shell
{
  "id":"/var/workflow/models/publish_example",
  "title":"Publish Example",
  "version":"1.0",
  "description":"This example shows a simple review and publish process.",
  "metaData": 
  {
    "multiResourceSupport":"true",
    "tags":"wcm,publish"
  },
  "nodes":
  [{
    "id":"node0",
    "type":"START",
    "title":"Start",
    "description":"The start node of the workflow.",
    "metaData":
    {
    }
  },
  {
    "id":"node1",
    "type":"PARTICIPANT",
    "title":"Validate Content",
    "description":"Validate the modified content.",
    "metaData":
    {
      "PARTICIPANT":"admin"
    }
  },
  {
    "id":"node2",
    "type":"PROCESS",
    "title":"Publish Content",
    "description":"Publish the modified content.",
    "metaData":
    {
      "PROCESS_AUTO_ADVANCE":"true",
      "PROCESS":"com.day.cq.wcm.workflow.process.ActivatePageProcess"
    }
  },
  {
    "id":"node3",
    "type":"END",
    "title":"End",
    "description":"The end node of the workflow.",
    "metaData":
    {
    }
  }],
  "transitions":
  [{
    "from":"node0",
    "to":"node1",
    "metaData":
    {
    }
  },
  {
    "from":"node1",
    "to":"node2",
    "metaData":
    {
    }
  },
  {
    "from":"node2",
    "to":"node3",
    "metaData":
    {
    }
  }
]}
```

#### Gerenciar um modelo de fluxo de trabalho por sua versão {#managing-a-workflow-model-by-its-version}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/etc/workflow/models/{id}.{version}`

| método de solicitação HTTP | Ações |
|---|---|
| `GET` | Obtém os dados do modelo na versão especificada (se existir). |

### Gerenciar caixas de entrada (usuário) {#managing-user-inboxes}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/bin/workflow/inbox`

<table> 
 <tbody> 
  <tr> 
   <td>método de solicitação HTTP</td> 
   <td>Ações</td> 
  </tr> 
  <tr> 
   <td><code>GET</code></td> 
   <td>Lista os itens de trabalho que estão na caixa de entrada do usuário, que é identificado pelos cabeçalhos de autenticação HTTP.</td> 
  </tr> 
  <tr> 
   <td><code>POST</code></td> 
   <td>Completa o item de trabalho cujo URI é enviado como parâmetro <code>item</code> e avança a instância de workflow correspondente para o(s) próximo(s) nó(s), que é definido pelo parâmetro <code>route</code> ou <code>backroute</code> no caso de dar um passo para trás.<br /> Se o parâmetro <code>delegatee</code> for enviado, o item de trabalho identificado pelo parâmetro <code>item</code> é delegado no participante especificado.</td> 
  </tr> 
 </tbody> 
</table>

#### Gerenciando uma Caixa de Entrada (Usuário) pela ID de Item de Trabalho {#managing-a-user-inbox-by-the-workitem-id}

Os seguintes métodos de solicitação HTTP se aplicam a:

`http://localhost:4502/bin/workflow/inbox/{id}`

| método de solicitação HTTP | Ações |
|---|---|
| `GET` | Obtém os dados (definição e metadados) da caixa de entrada `WorkItem` identificado por sua ID. |

## Exemplos {#examples}

### Como obter uma lista de todos os fluxos de trabalho em execução com suas IDs {#how-to-get-a-list-of-all-running-workflows-with-their-ids}

Para obter uma lista de todos os workflows em execução, faça um GET para:

`http://localhost:4502/etc/workflow/instances.RUNNING.json`

#### Como obter uma lista de todos os fluxos de trabalho em execução com suas IDs - REST usando curl {#how-to-get-a-list-of-all-running-workflows-with-their-ids-rest-using-curl}

Exemplo usando curl:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/instances.RUNNING.json
```

O `uri` exibidos nos resultados podem ser usados como a instância `id` Em outros comandos; por exemplo:

```shell
[
    {"uri":"/etc/workflow/instances/server0/2017-03-08/request_for_activation_1"}
]
```

>[!NOTE]
>
>Essa `curl` pode ser usado com qualquer [status do workflow](/help/sites-administering/workflows.md#workflow-status-and-actions) em vez de `RUNNING`.

### Como alterar o título do fluxo de trabalho {#how-to-change-the-workflow-title}

Para alterar o **Título do fluxo de trabalho** exibido no **Instâncias** do console do fluxo de trabalho, envie um `POST` comando:

* para: `http://localhost:4502/etc/workflow/instances/{id}`

* com os seguintes parâmetros:

   * `action`: O seu valor deve ser: `UPDATE`
   * `workflowTitle`: o título do fluxo de trabalho

#### Como alterar o título do fluxo de trabalho - REST usando curl {#how-to-change-the-workflow-title-rest-using-curl}

Exemplo usando curl:

```shell
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/{id}

# for example

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
curl -u admin:admin -d "action=UPDATE&workflowTitle=myWorkflowTitle" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
```

### Como listar todos os modelos de fluxo de trabalho {#how-to-list-all-workflow-models}

Para obter uma lista de todos os modelos de fluxo de trabalho disponíveis, faça uma GET para:

`http://localhost:4502/etc/workflow/models.json`

#### Como listar todos os modelos de fluxo de trabalho - REST usando curl {#how-to-list-all-workflow-models-rest-using-curl}

Exemplo usando curl:

```shell
curl -u admin:admin http://localhost:4502/etc/workflow/models.json
```

>[!NOTE]
>
>Consulte também [Gerenciamento de modelos de fluxo de trabalho](#managing-workflow-models).

### Obter um objeto WorkflowSession {#obtaining-a-workflowsession-object}

O `com.adobe.granite.workflow.WorkflowSession` classe é adaptável a partir de um `javax.jcr.Session` objeto ou um `org.apache.sling.api.resource.ResourceResolver` objeto.

#### Obter um objeto WorkflowSession - Java {#obtaining-a-workflowsession-object-java}

Em um script JSP (ou código Java para uma classe de servlet), use o objeto de solicitação HTTP para obter um `SlingHttpServletRequest` que fornece acesso a um `ResourceResolver` objeto. Adapte o `ResourceResolver` objeto para `WorkflowSession`.

```java
<%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" 
    import="com.adobe.granite.workflow.WorkflowSession,
  org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
%>
```

#### Obter um objeto WorkflowSession - Script ECMA {#obtaining-a-workflowsession-object-ecma-script}

Use o `sling` para obter a variável `SlingHttpServletRequest` objeto usado para obter um `ResourceResolver` objeto. Adapte o `ResourceResolver` para `WorkflowSession` objeto.

```
var wfsession = sling.getRequest().getResource().getResourceResolver().adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
```

### Como criar, ler ou excluir modelos de fluxo de trabalho {#creating-reading-or-deleting-workflow-models}

Os exemplos a seguir mostram como acessar modelos de fluxo de trabalho:

* O código para Java e ECMA script usa a variável `WorkflowSession.createNewModel` método .
* O comando curl acessa o modelo diretamente usando seu URL.

Os exemplos usados:

1. Criar um modelo (com a ID `/var/workflow/models/mymodel/jcr:content/model`).
1. Exclua o modelo.

>[!NOTE]
>
>A exclusão do modelo define o `deleted` propriedade do modelo `metaData` nó filho para `true`.
>
>A exclusão não remove o nó modelo.

Ao criar um novo modelo:

* O editor de modelo de fluxo de trabalho requer que os modelos usem uma estrutura de nó específica abaixo `/var/workflow/models`. O nó pai do modelo deve ser do tipo `cq:Page` ter um `jcr:content` nó com os seguintes valores de propriedade:

   * `sling:resourceType`: `cq/workflow/components/pages/model`
   * `cq:template`: `/libs/cq/workflow/templates/model`

   Ao criar um modelo, você deve primeiro criar `cq:Page` nó e use seu `jcr:content` como o pai do nó modelo.

* O `id` O argumento que alguns métodos exigem para identificar o modelo é o caminho absoluto do nó do modelo no repositório:

   `/var/workflow/models/<*model_name>*/jcr:content/model`

   >[!NOTE]
   >
   >Consulte [Como listar todos os modelos de fluxo de trabalho](#how-to-list-all-workflow-models).

#### Criação, leitura ou exclusão de modelos de fluxo de trabalho - Java {#creating-reading-or-deleting-workflow-models-java}

```java
<%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" import="com.adobe.granite.workflow.WorkflowSession,
                 com.adobe.granite.workflow.model.WorkflowModel,
             org.apache.sling.api.SlingHttpServletRequest"%><%

SlingHttpServletRequest slingReq = (SlingHttpServletRequest)request;
WorkflowSession wfSession = slingReq.getResourceResolver().adaptTo(WorkflowSession.class);
/* Create the parent page */
String modelRepo = new String("/var/workflow/models");
String modelTemplate = new String ("/libs/cq/workflow/templates/model");
String modelName = new String("mymodel");
Page modelParent = pageManager.create(modelRepo, modelName, modelTemplate, "My workflow model");

/* create the model */
String modelId = new String(modelParent.getPath()+"/jcr:content/model")
WorkflowModel model = wfSession.createNewModel("Made using Java",modelId);

/* delete the model */
wfSession.deleteModel(modelId);
%>
```

#### Criação, Leitura ou Exclusão de Modelos de Fluxo de Trabalho - Script ECMA {#creating-reading-or-deleting-workflow-models-ecma-script}

```
var resolver = sling.getRequest().getResource().getResourceResolver();
var wfSession = resolver.adaptTo(Packages.com.adobe.granite.workflow.WorkflowSession);
var pageManager = resolver.adaptTo(Packages.com.day.cq.wcm.api.PageManager);

//create the parent page node
var workflowPage = pageManager.create("/var/workflow/models", "mymodel", "/libs/cq/workflow/templates/model", "Created via ECMA Script");
var modelId = workflowPage.getPath()+ "/jcr:content/model";
//create the model
var model = wfSession.createNewModel("My Model", modelId);
//delete the model
var model = wfSession.deleteModel(modelId);
```

#### Exclusão de um modelo de fluxo de trabalho - REST usando curl {#deleting-a-workflow-model-rest-using-curl}

```shell
# deleting the model by its id

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
curl -u admin:admin -X DELETE http://localhost:4502/etc/workflow/models/{id}
```

>[!NOTE]
>
>Devido ao nível de detalhes necessário, o curl não é considerado prático para criar e/ou ler um modelo.

### Filtrar workflows do sistema ao verificar o status do workflow {#filtering-out-system-workflows-when-checking-workflow-status}

Você pode usar o [API WorkflowStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/status/WorkflowStatus.html) para recuperar informações sobre o status do workflow de um nó.

Vários métodos têm o parâmetro :

`excludeSystemWorkflows`

Esse parâmetro pode ser definido como `true` para indicar que os fluxos de trabalho do sistema devem ser excluídos dos resultados relevantes.

Você [pode atualizar a configuração do OSGi](/help/sites-deploying/configuring-osgi.md) **Fluxo de trabalho do Adobe Granite PayloadMapCache** que especifica o workflow `Models` para ser considerado como workflows do sistema. Os modelos de fluxo de trabalho padrão (tempo de execução) são:

* `/var/workflow/models/scheduled_activation/jcr:content/model`
* `/var/workflow/models/scheduled_deactivation/jcr:content/model`

### Avançar automaticamente etapa do participante após um tempo limite {#auto-advance-participant-step-after-a-timeout}

Se você precisar avançar automaticamente um **Participante** etapa que não foi concluída em um tempo predefinido, é possível:

1. Implemente um ouvinte de evento OSGI para acompanhar a criação e a modificação da tarefa.
1. Especifique um tempo limite (prazo) e crie um trabalho de sling agendado para ser disparado nesse momento.
1. Escreva um manipulador de tarefas que seja notificado quando o tempo limite expirar e acione o trabalho.

   Esse manipulador executará a ação necessária na tarefa se ela ainda não estiver concluída

>[!NOTE]
>
>As medidas a tomar devem ser claramente definidas para poderem utilizar esta abordagem.

### Interação com instâncias de fluxo de trabalho {#interacting-with-workflow-instances}

Os seguintes fornecem exemplos básicos de como interagir (programaticamente) com instâncias de fluxo de trabalho.

#### Interação com instâncias de fluxo de trabalho - Java {#interacting-with-workflow-instances-java}

```java
// starting a workflow
WorkflowModel model = wfSession.getModel(workflowId);
WorkflowData wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
Workflow[] workflows workflows = wfSession.getAllWorkflows();
Workflow workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interagir com instâncias de fluxo de trabalho - Script ECMA {#interacting-with-workflow-instances-ecma-script}

```
// starting a workflow
var model = wfSession.getModel(workflowId);
var wfData = wfSession.newWorkflowData("JCR_PATH", repoPath);
wfSession.startWorkflow(model, wfData);

// querying and managing a workflow
var workflows = wfSession.getWorkflows(“RUNNING“);
var workflow= wfSession.getWorkflow(id);
wfSession.suspendWorkflow(workflow);
wfSession.resumeWorkflow(workflow);
wfSession.terminateWorkflow(workflow);
```

#### Interagir com instâncias de fluxo de trabalho - REST usando curl {#interacting-with-workflow-instances-rest-using-curl}

* **Iniciar um workflow**

   ```shell
   # starting a workflow
   curl -d "model={id}&payloadType={type}&payload={payload}" http://localhost:4502/etc/workflow/instances
   
   # for example:
   curl -u admin:admin -d "model=/var/workflow/models/request_for_activation&payloadType=JCR_PATH&payload=/content/we-retail/us/en/products" http://localhost:4502/etc/workflow/instances
   ```

* **Listar as instâncias**

   ```shell
   # listing the instances
   curl -u admin:admin http://localhost:4502/etc/workflow/instances.json
   ```

   Isso listará todas as instâncias; por exemplo:

   ```shell
   [
       {"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_1"}
       ,{"uri":"/var/workflow/instances/server0/2018-02-26/prototype-01_2"}
   ]
   ```

   >[!NOTE]
   >
   >Consulte [Como obter uma lista de todos os fluxos de trabalho em execução](#how-to-get-a-list-of-all-running-workflows-with-their-ids) com suas IDs para listar instâncias com um status específico.

* **Suspensão de um fluxo de trabalho**

   ```shell
   # suspending a workflow
   curl -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=SUSPENDED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Retomar um workflow**

   ```shell
   # resuming a workflow
   curl -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=RUNNING" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

* **Encerrar uma instância de fluxo de trabalho**

   ```shell
   # terminating a workflow
   curl -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/{id}
   
   # for example:
   curl -u admin:admin -d "state=ABORTED" http://localhost:4502/etc/workflow/instances/server0/2017-03-08/request_for_activation_1
   ```

### Interagir com Itens de Trabalho {#interacting-with-work-items}

Os seguintes fornecem exemplos básicos de como interagir (programaticamente) com itens de trabalho.

#### Interagir com itens de trabalho - Java {#interacting-with-work-items-java}

```java
// querying work items
WorkItem[] workItems = wfSession.getActiveWorkItems();
WorkItem workItem = wfSession.getWorkItem(id);

// getting routes
List<Route> routes = wfSession.getRoutes(workItem);

// delegating
Iterator<Participant> delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interagir com itens de trabalho - Script ECMA {#interacting-with-work-items-ecma-script}

```
// querying work items
var workItems = wfSession.getActiveWorkItems();
var workItem = wfSession.getWorkItem(id);

// getting routes
var routes = wfSession.getRoutes(workItem);

// delegating
var delegatees = wfSession.getDelegatees(workItem);
wfSession.delegateWorkItem(workItem, delegatees.get(0));

// completing or advancing to the next step
wfSession.complete(workItem, routes.get(0));
```

#### Interagir com Itens de Trabalho - REST usando curl {#interacting-with-work-items-rest-using-curl}

* **Listar itens de trabalho da caixa de entrada**

   ```shell
   # listing the work items
   curl -u admin:admin http://localhost:4502/bin/workflow/inbox
   ```

   Os detalhes dos itens de trabalho que estão na Caixa de entrada serão listados; por exemplo:

   ```shell
   [{
       "uri_xss": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "uri": "/var/workflow/instances/server0/2018-02-26/prototype-01_2/workItems/node2_var_workflow_instances_server0_2018-02-26_prototype-01_2",
       "currentAssignee_xss": "workflow-administrators",
       "currentAssignee": "workflow-administrators",
       "startTime": 1519656289274,
       "payloadType_xss": "JCR_PATH",
       "payloadType": "JCR_PATH",
       "payload_xss": "/content/we-retail/es/es",
       "payload": "/content/we-retail/es/es",
       "comment_xss": "Process resource is null",
       "comment": "Process resource is null",
       "type_xss": "WorkItem",
       "type": "WorkItem"
     },{
       "uri_xss": "configuration/configure_analyticstargeting",
       "uri": "configuration/configure_analyticstargeting",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/securitychecklist",
       "uri": "configuration/securitychecklist",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/enable_collectionofanonymoususagedata",
       "uri": "configuration/enable_collectionofanonymoususagedata",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     },{
       "uri_xss": "configuration/configuressl",
       "uri": "configuration/configuressl",
       "currentAssignee_xss": "administrators",
       "currentAssignee": "administrators",
       "type_xss": "Task",
       "type": "Task"
     }
   ```

* **Delegar itens de trabalho**

   ```xml
   # delegating
   curl -d "item={item}&delegatee={delegatee}" http://localhost:4502/bin/workflow/inbox
   
   # for example: 
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_act_1&delegatee=administrators" http://localhost:4502/bin/workflow/inbox
   ```

   >[!NOTE]
   >
   >O `delegatee` deve ser uma opção válida para a etapa do fluxo de trabalho.

* **Concluir ou avançar itens de trabalho para a próxima etapa**

   ```xml
   # retrieve the list of routes; the results will be similar to {"results":1,"routes":[{"rid":"233123169","label":"End","label_xss":"End"}]}
   http://localhost:4502/etc/workflow/instances/<path-to-the-workitem>.routes.json
   
   # completing or advancing to the next step; use the appropriate route ID (rid value) from the above list
   curl -d "item={item}&route={route}" http://localhost:4502/bin/workflow/inbox
   
   # for example:
   curl -u admin:admin -d "item=/etc/workflow/instances/server0/2017-03-08/request_for_activation_1/workItems/node1_etc_workflow_instances_server0_2017-03-08_request_for_activation_1&route=233123169" http://localhost:4502/bin/workflow/inbox
   ```

### Acompanhamento de eventos de fluxo de trabalho {#listening-for-workflow-events}

Use a estrutura de evento OSGi para acompanhar eventos que a variável [ `com.adobe.granite.workflow.event.WorkflowEvent`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/event/WorkflowEvent.html) classe define. Essa classe também fornece vários métodos úteis para obter informações sobre o assunto do evento. Por exemplo, a variável `getWorkItem` método retorna `WorkItem` para o item de trabalho envolvido no evento.

O código de exemplo a seguir define um serviço que escuta eventos de fluxo de trabalho e executa tarefas de acordo com o tipo de evento.

```java
package com.adobe.example.workflow.listeners;

import org.apache.sling.event.jobs.JobProcessor;
import org.apache.sling.event.jobs.JobUtil;

import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;

import com.adobe.granite.workflow.event.WorkflowEvent;
import com.adobe.granite.workflow.exec.WorkItem;

/**
 * The <code>WorkflowEventCatcher</code> class listens to workflow events. 
 */
@Component(metatype=false, immediate=true)
@Service(value=org.osgi.service.event.EventHandler.class)
public class WorkflowEventCatcher implements EventHandler, JobProcessor {

 @Property(value=com.adobe.granite.workflow.event.WorkflowEvent.EVENT_TOPIC)
 static final String EVENT_TOPICS = "event.topics";

 private static final Logger logger = LoggerFactory.getLogger(WorkflowEventCatcher.class);

 public void handleEvent(Event event) {
  JobUtil.processJob(event, this);
 }

 public boolean process(Event event) {
  logger.info("Received event of topic: " + event.getTopic());
  String topic = event.getTopic();

  try {
   if (topic.equals(WorkflowEvent.EVENT_TOPIC)) {
    WorkflowEvent wfevent = (WorkflowEvent)event;
    String eventType = wfevent.getEventType();
    String instanceId = wfevent.getWorkflowInstanceId();

    if (instanceId != null) {
     //workflow instance events
     if (eventType.equals(WorkflowEvent.WORKFLOW_STARTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_RESUMED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_SUSPENDED_EVENT)) {
      // your code comes here...
     } else if (
       eventType.equals(WorkflowEvent.WORKFLOW_ABORTED_EVENT) ||
       eventType.equals(WorkflowEvent.WORKFLOW_COMPLETED_EVENT)) {
      // your code comes here...
     }
     // workflow node event
     if (eventType.equals(WorkflowEvent.NODE_TRANSITION_EVENT)) {
      WorkItem currentItem = (WorkItem) event.getProperty(WorkflowEvent.WORK_ITEM);
      // your code comes here...
     }
    }
   }
  } catch(Exception e){
   logger.debug(e.getMessage());
   e.printStackTrace();
  }
  return true;
 }
}
```
