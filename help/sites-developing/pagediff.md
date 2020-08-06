---
title: Desenvolvendo e comparação de páginas
seo-title: Desenvolvendo e comparação de páginas
description: 'null'
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 7%

---


# Desenvolvendo e comparação de páginas{#developing-and-page-diff}

## Visão geral do recurso {#feature-overview}

A criação de conteúdo é um processo iterativo. Criar com eficiência exige poder ver o que mudou de uma iteração para outra. Visualizar uma versão da página e, em seguida, a outra é um processo ineficiente e propenso a erros. Um autor deseja comparar a página atual com uma versão anterior lado a lado com as diferenças destacadas.

O diff da página permite que um usuário compare a página atual com inicializações, versões anteriores etc. Para obter detalhes sobre esse recurso do usuário, consulte Diferença de [página](/help/sites-authoring/page-diff.md).

## Detalhes da operação {#operation-details}

Ao comparar versões de uma página, a versão anterior que o usuário deseja comparar é recriada por AEM em segundo plano para facilitar a diferença. Isso é necessário para que o conteúdo seja renderizado [para comparação](/help/sites-authoring/page-diff.md#presentation-of-differences)lado a lado.

Esta operação de recriação é feita por AEM interna e é transparente para o usuário e não requer intervenção. No entanto, um administrador que visualiza o repositório, por exemplo, no CRX DE Lite, veria essas versões recriadas dentro da estrutura de conteúdo.

Dependendo do nível de correção AEM, o comportamento é diferente e pode exigir determinadas permissões para funcionar corretamente.

### Antes do AEM 6.4.3 {#prior-to-aem}

Quando o conteúdo é comparado, a árvore inteira até a página a ser comparada é recriada no seguinte local:

`/content/versionhistory/<userId>/<site structure>`

Como ao usar o mecanismo de diff de página, AEM recria a versão anterior da página, para usar o recurso, o usuário deve ter certas permissões de JCR.

>[!CAUTION]
>
>Para usar o recurso de diff de página, o usuário precisa ter a permissão **Modificar/Criar/Excluir** no nó `/content/versionhistory`.

### AEM 6.4.3 {#as-of-aem}

Quando o conteúdo é comparado, a árvore inteira até a página a ser comparada é recriada no seguinte local:

`/tmp/versionhistory/`

Este conteúdo é criado por um usuário de serviço com permissões que limitam a visibilidade ao usuário atual. Por isso, nenhuma permissão especial é necessária.

Uma tarefa de limpeza é executada automaticamente para limpar esse conteúdo temporário.

## Limitações do desenvolvedor {#developer-limitations}

Anteriormente, na interface clássica, era necessário considerar um desenvolvimento especial para facilitar a difusão AEM (como o uso da `cq:text` `DiffService` tag lib ou a integração personalizada do serviço OSGi nos componentes). Isso não é mais necessário para o novo recurso diff, pois o diff ocorre no cliente por meio da comparação DOM.

No entanto, há várias limitações que precisam ser consideradas pelo desenvolvedor.

* Este recurso usa classes CSS que não têm nomes espaçados para o Produto AEM. Se outras classes CSS personalizadas ou classes CSS de terceiros com os mesmos nomes forem incluídas na página, a exibição do diff pode ser afetada.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Como o diff é do lado do cliente e é executado no carregamento da página, todos os ajustes no DOM após a execução do serviço de comparação do lado do cliente não serão contabilizados. Este fato pode afetar

   * Componentes que usam AJAX para incluir conteúdo
   * Aplicativos de página única
   * Componentes baseados em JavaScript que manipulam o DOM na interação do usuário.

