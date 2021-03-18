---
title: Desenvolvimento e diff de página
seo-title: Desenvolvimento e diff de página
description: Desenvolvimento e diff de página
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 8%

---


# Desenvolvimento e diff de página{#developing-and-page-diff}

## Visão geral dos recursos {#feature-overview}

A criação de conteúdo é um processo iterativo. Criar com eficiência exige poder ver o que mudou de uma iteração para outra. Visualizar uma versão da página e, em seguida, a outra é um processo ineficiente e propenso a erros. Um autor deseja poder comparar a página atual com uma versão anterior lado a lado com as diferenças destacadas.

O diferencial de páginas permite que um usuário compare a página atual com inicializações, versões anteriores etc. Para obter detalhes sobre esse recurso do usuário, consulte [Diff de página](/help/sites-authoring/page-diff.md).

## Detalhes da Operação {#operation-details}

Ao comparar versões de uma página, a versão anterior que o usuário deseja comparar é recriada por AEM em segundo plano para facilitar o diferencial. Isso é necessário para poder renderizar o conteúdo [para comparação lado a lado](/help/sites-authoring/page-diff.md#presentation-of-differences).

Essa operação de recriação é feita por AEM internamente e é transparente para o usuário e não requer intervenção. No entanto, um administrador que visualiza o repositório, por exemplo, no CRX DE Lite, veria essas versões recriadas na estrutura de conteúdo.

Dependendo do nível de patch de AEM, o comportamento é diferente e pode exigir determinadas permissões para funcionar corretamente.

### Antes do AEM 6.4.3 {#prior-to-aem}

Quando o conteúdo é comparado, a árvore inteira até a página a ser comparada é recriada no seguinte local:

`/content/versionhistory/<userId>/<site structure>`

Como ao usar o mecanismo diff da página, AEM recria a versão anterior da página, para usar o recurso, o usuário deve ter certas permissões JCR.

>[!CAUTION]
>
>Para usar o recurso de diferencial de página, o usuário precisa ter a permissão **Modificar/Criar/Excluir** no nó `/content/versionhistory`.

### A partir AEM 6.4.3 {#as-of-aem}

Quando o conteúdo é comparado, a árvore inteira até a página a ser comparada é recriada no seguinte local:

`/tmp/versionhistory/`

Esse conteúdo é criado por um usuário de serviço com permissões limitando a visibilidade ao usuário atual. Por esse motivo, nenhuma permissão especial é necessária.

Uma tarefa de limpeza é executada automaticamente para limpar esse conteúdo temporário.

## Limitações do desenvolvedor {#developer-limitations}

Anteriormente, na interface do usuário clássica, era necessário considerar o desenvolvimento especial para facilitar a diferenciação AEM (como usar `cq:text` tag lib ou integrar o serviço `DiffService` OSGi em componentes). Isso não é mais necessário para o novo recurso de diferencial, pois o recurso de diferencial ocorre no lado do cliente por meio da comparação de DOM.

No entanto, há várias limitações que precisam ser consideradas pelo desenvolvedor.

* Esse recurso usa classes CSS que não são nomeadas espaçadas para o Produto AEM. Se outras classes CSS personalizadas ou classes CSS de terceiros com os mesmos nomes forem incluídas na página, a exibição do diferencial poderá ser afetada.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Como o diferencial é do lado do cliente e é executado no carregamento da página, os ajustes no DOM após a execução do serviço de comparação do lado do cliente não serão contabilizados. Pode afetar

   * Componentes que usam AJAX para incluir conteúdo
   * Aplicativos de página única
   * Componentes baseados em JavaScript que manipulam o DOM na interação do usuário.

