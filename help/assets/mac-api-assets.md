---
title: API HTTP de ativos em [!DNL Adobe Experience Manager].
description: Criar, ler, atualizar, excluir, gerenciar ativos digitais usando a API HTTP em [!DNL Adobe Experience Manager Assets].
contentOwner: AG
feature: APIs,Assets HTTP API,Developer Tools
role: Developer
exl-id: 3d7d078c-5046-489a-a8e0-258acaea7191
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 1%

---

# API HTTP de ativos {#assets-http-api}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A API HTTP de ativos permite operações de criação-leitura-atualização-exclusão (CRUD) em ativos digitais, incluindo em metadados, em representações e em comentários, juntamente com conteúdo estruturado usando [!DNL Experience Manager] Fragmentos de conteúdo. É exposto em `/api/assets` e é implementado como REST API.

Para acessar a API:

1. Abra o documento do serviço de API em `https://[hostname]:[port]/api.json`.
1. Siga o link do Serviço de ativos que leva a `https://[hostname]:[server]/api/assets.json`.

A resposta da API é um arquivo JSON para alguns tipos MIME e um código de resposta para todos os tipos MIME. A resposta JSON é opcional e pode não estar disponível, por exemplo, para arquivos PDF. Confie no código de resposta para mais análises ou ações.

Depois que a variável [!UICONTROL Hora de desligar], um ativo e suas representações não estão disponíveis por meio do [!DNL Assets] interface da Web e por meio da API HTTP. A API retornará uma mensagem de erro 404 se a variável [!UICONTROL Hora de ligar] está no futuro ou [!UICONTROL Hora de desligar] está no passado.

>[!CAUTION]
>
>[A API HTTP atualiza as propriedades dos metadados](#update-asset-metadata) no `jcr` namespace. No entanto, a interface do usuário do Experience Manager atualiza as propriedades dos metadados no `dc` namespace.

## Modelo de dados {#data-model}

A API HTTP de ativos expõe dois elementos principais, pastas e ativos (para ativos padrão).

### Pastas {#folders}

Pastas são como diretórios em sistemas de arquivos tradicionais. São contêineres para outras pastas ou asserções. As pastas têm os seguintes componentes:

**Entidades**: As entidades de uma pasta são seus elementos filho, que podem ser pastas e ativos.

**Propriedades**:

* `name` é o nome da pasta. É o mesmo que o último segmento no caminho do URL sem a extensão.
* `title` é um título opcional da pasta que pode ser exibido em vez de seu nome.

>[!NOTE]
>
>Algumas propriedades de pasta ou ativo são mapeadas para um prefixo diferente. O `jcr` prefixo de `jcr:title`, `jcr:description`e `jcr:language` são substituídas por `dc` prefixo. Portanto no JSON retornado, `dc:title` e `dc:description` contém os valores de `jcr:title` e `jcr:description`, respectivamente.

**Links** As pastas expõem três links:

* `self`: Vincular a si mesmo.
* `parent`: Link para a pasta principal.
* `thumbnail`: (Opcional) link para uma imagem em miniatura de pasta.

### Assets {#assets}

No Experience Manager, um ativo contém os seguintes elementos:

* As propriedades e os metadados do ativo.
* Várias representações, como a representação original (que é o ativo originalmente carregado), uma miniatura e várias outras representações. As representações adicionais podem ser imagens de tamanhos diferentes, codificações de vídeo diferentes ou páginas extraídas de arquivos PDF ou Adobe InDesign.
* Comentários opcionais.

Em [!DNL Experience Manager] uma pasta tem os seguintes componentes:

* Entidades: Os filhos dos ativos são suas representações.
* Propriedades.
* Links.

A API HTTP de ativos inclui os seguintes recursos:

* [Recuperar uma listagem de pastas](#retrieve-a-folder-listing).
* [Criar uma pasta](#create-a-folder).
* [Criar um ativo](#create-an-asset).
* [Atualizar binário de ativo](#update-asset-binary).
* [Atualizar metadados de ativos](#update-asset-metadata).
* [Criar uma representação de ativo](#create-an-asset-rendition).
* [Atualizar uma representação de ativo](#update-an-asset-rendition).
* [Criar um comentário de ativo](#create-an-asset-comment).
* [Copiar uma pasta ou um ativo](#copy-a-folder-or-asset).
* [Mover uma pasta ou um ativo](#move-a-folder-or-asset).
* [Excluir uma pasta, ativo ou representação](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Para facilitar a legibilidade, os exemplos a seguir omitem a notação completa de cURL. Na verdade, a notação correlaciona-se com [Restaurar](https://github.com/micha/resty) que é um wrapper de scripts para `cURL`.

**Pré-requisitos**

* Acesso `https://[aem_server]:[port]/system/console/configMgr`.
* Navegar para **[!UICONTROL Filtro CSRF do Adobe Granite]**.
* Certifique-se de que a propriedade **[!UICONTROL Métodos de filtro]** inclui: `POST`, `PUT`, `DELETE`.

## Recuperar uma listagem de pastas {#retrieve-a-folder-listing}

Recupera uma representação Siren de uma pasta existente e de suas entidades filhas (subpastas ou ativos).

**Solicitação**: `GET /api/assets/myFolder.json`

**Códigos de resposta**: Os códigos de resposta são:

* 200 - OK - sucesso.
* 404 - NÃO ENCONTRADO - a pasta não existe ou não está acessível.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

**Resposta**: A classe da entidade retornada é um ativo ou uma pasta. As propriedades das entidades contidas são um subconjunto do conjunto completo de propriedades de cada entidade. Para obter uma representação completa da entidade, os clientes devem recuperar o conteúdo do URL apontado pelo link com uma `rel` de `self`.

## Crie uma pasta  {#create-a-folder}

Cria um novo `sling`: `OrderedFolder` no caminho determinado. Se uma `*` é fornecido em vez de um nome de nó, o servlet usa o nome do parâmetro como nome do nó. Aceito como dados de solicitação é uma representação Siren da nova pasta ou um conjunto de pares de nome-valor, codificado como `application/www-form-urlencoded` ou `multipart`/ `form`- `data`, útil para criar uma pasta diretamente de um formulário HTML. Além disso, as propriedades da pasta podem ser especificadas como parâmetros de consulta de URL.

Uma chamada de API falha com uma `500` código de resposta se o nó pai do caminho fornecido não existir. Uma chamada retorna um código de resposta `409` se a pasta já existir.

**Parâmetros**: `name` é o nome da pasta.

**Solicitar**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CRIADO - na criação bem-sucedida.
* 409 - CONFLICT - se a pasta já existir.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Criar um ativo {#create-an-asset}

Coloque o arquivo fornecido no caminho fornecido para criar um ativo no repositório DAM. Se uma `*` é fornecido em vez de um nome de nó, o servlet usa o nome do parâmetro ou o nome do arquivo como nome do nó.

**Parâmetros**: Os parâmetros são `name` para o nome do ativo e `file` para a referência do arquivo.

**Solicitar**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CRIADO - se o Ativo tiver sido criado com êxito.
* 409 - CONFLITO - se o ativo já existir.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Atualizar um binário de ativo {#update-asset-binary}

Atualiza o binário de um ativo (representação com o nome original). Uma atualização aciona o fluxo de trabalho de processamento de ativos padrão para execução, se estiver configurado.

**Solicitação**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Códigos de resposta**: Os códigos de resposta são:

* 200 - OK - se Ativo tiver sido atualizado com êxito.
* 404 - NÃO ENCONTRADO - se o Ativo não puder ser encontrado ou acessado no URI fornecido.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Atualizar metadados de ativos {#update-asset-metadata}

Atualiza as propriedades de metadados do ativo. Se você atualizar qualquer propriedade no `dc:` namespace, a API atualiza a mesma propriedade no `jcr` namespace. A API não sincroniza as propriedades nos dois namespaces.

**Solicitação**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**Códigos de resposta**: Os códigos de resposta são:

* 200 - OK - se Ativo tiver sido atualizado com êxito.
* 404 - NÃO ENCONTRADO - se o Ativo não puder ser encontrado ou acessado no URI fornecido.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

### Sincronizar atualização de metadados entre `dc` e `jcr` namespace {#sync-metadata-between-namespaces}

O método da API atualiza as propriedades dos metadados no `jcr` namespace. As atualizações feitas usando a interface sensível ao toque alteram as propriedades dos metadados no `dc` namespace. Para sincronizar os valores de metadados entre `dc` e `jcr` namespace, é possível criar um fluxo de trabalho e configurar o Experience Manager para executar o fluxo de trabalho na edição de ativos. Use um script ECMA para sincronizar as propriedades de metadados necessárias. O script de amostra a seguir sincroniza a cadeia de caracteres de título entre `dc:title` e `jcr:title`.

```javascript
var workflowData = workItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH")
{
 var path = workflowData.getPayload().toString();
 var node = workflowSession.getSession().getItem(path);
 var metadataNode = node.getNode("jcr:content/metadata");
 var jcrcontentNode = node.getNode("jcr:content");
if (jcrcontentNode.hasProperty("jcr:title"))
{
 var jcrTitle = jcrcontentNode.getProperty("jcr:title");
 metadataNode.setProperty("dc:title", jcrTitle.toString());
 metadataNode.save();
}
}
```

## Criar uma representação de ativo {#create-an-asset-rendition}

Crie uma nova representação de ativo para um ativo. Se o nome do parâmetro da solicitação não for fornecido, o nome do arquivo será usado como nome da representação.

**Parâmetros**: Os parâmetros são `name` em nome da representação e `file` como referência de arquivo.

**Solicitar**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CREATED - se a Representação tiver sido criada com êxito.
* 404 - NÃO ENCONTRADO - se o Ativo não puder ser encontrado ou acessado no URI fornecido.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Atualizar uma representação de ativo {#update-an-asset-rendition}

As atualizações substituem, respectivamente, uma representação de ativo pelos novos dados binários.

**Solicitação**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Códigos de resposta**: Os códigos de resposta são:

* 200 - OK - se a Representação tiver sido atualizada com êxito.
* 404 - NÃO ENCONTRADO - se o Ativo não puder ser encontrado ou acessado no URI fornecido.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Adicionar um comentário em um ativo {#create-an-asset-comment}

Cria um novo comentário de ativo.

**Parâmetros**: Os parâmetros são `message` para o corpo da mensagem do comentário e `annotationData` para os dados de anotação no formato JSON.

**Solicitação**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CRIADO - se o Comentário tiver sido criado com êxito.
* 404 - NÃO ENCONTRADO - se o Ativo não puder ser encontrado ou acessado no URI fornecido.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Copiar uma pasta ou um ativo {#copy-a-folder-or-asset}

Copia uma pasta ou ativo disponível no caminho fornecido para um novo destino.

**Cabeçalhos de solicitação**: Os parâmetros são:

* `X-Destination` - um novo URI de destino no escopo da solução de API para copiar o recurso.
* `X-Depth` - quer `infinity` ou `0`. Usando `0` copia somente o recurso e suas propriedades, e não seus filhos.
* `X-Overwrite` - Uso `F` para impedir a substituição de um ativo no destino existente.

**Solicitação**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CREATED - se a pasta/ativo tiver sido copiada para um destino não existente.
* 204 - NO CONTENT - se a pasta/ativo tiver sido copiada para um destino existente.
* 412 - PRECONDITION FAILED - se um cabeçalho de solicitação estiver ausente.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Mover uma pasta ou um ativo {#move-a-folder-or-asset}

Move uma pasta ou um ativo no caminho especificado para um novo destino.

**Cabeçalhos de solicitação**: Os parâmetros são:

* `X-Destination` - um novo URI de destino no escopo da solução de API para copiar o recurso.
* `X-Depth` - quer `infinity` ou `0`. Usando `0` copia somente o recurso e suas propriedades, e não seus filhos.
* `X-Overwrite` - Use `T` para forçar a exclusão de recursos existentes ou `F` para evitar a substituição de um recurso existente.

**Solicitação**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Códigos de resposta**: Os códigos de resposta são:

* 201 - CREATED - se a pasta/ativo tiver sido copiada para um destino não existente.
* 204 - NO CONTENT - se a pasta/ativo tiver sido copiada para um destino existente.
* 412 - PRECONDITION FAILED - se um cabeçalho de solicitação estiver ausente.
* 500 - INTERNAL SERVER ERROR - se algo der errado.

## Excluir uma pasta, um ativo ou uma representação {#delete-a-folder-asset-or-rendition}

Exclui um recurso (-tree) no caminho fornecido.

**Solicitar**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Códigos de resposta**: Os códigos de resposta são:

* 200 - OK - se a pasta tiver sido excluída com êxito.
* 412 - PRECONDITION FAILED - se a coleção raiz não puder ser encontrada ou acessada.
* 500 - INTERNAL SERVER ERROR - se algo der errado.
