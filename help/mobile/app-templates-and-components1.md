---
title: Modelos e componentes do aplicativo
seo-title: App Templates and Components
description: Siga esta página para saber mais sobre Modelos e componentes do aplicativo. Ele fornece informações detalhadas sobre a estrutura dos modelos.
seo-description: Follow this page to learn about App Templates and Components. It provides detailed information on the structure of templates.
uuid: ba2fd91b-de5a-4f39-a976-5455f9983669
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 7f31c6a7-92d5-4a87-a9f0-68a82b834d5a
exl-id: 5480ac38-f651-4211-94f6-c588fb44ad55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 3%

---

# Modelos e componentes do aplicativo{#app-templates-and-components}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

Um Modelo é usado para criar uma Página e define quais componentes podem ser usados dentro do escopo selecionado. Um modelo é uma hierarquia de nós que tem a mesma estrutura que a página a ser criada, mas sem nenhum conteúdo real.

Cada modelo apresentará a você uma seleção de componentes disponíveis para uso.

* Os modelos são criados de [Componentes](/help/sites-developing/components.md);
* Os componentes usam e permitem acesso a widgets, e eles são usados para renderizar o Conteúdo.

>[!NOTE]
>
>Para saber como desenvolver seu aplicativo AEM usando o CRXDE Lite, consulte [Desenvolvimento com o CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

Um modelo é a base de uma página.

Para criar uma página, o modelo deve ser copiado (árvore de nó) **/apps/&lt;myapp>/templates/&lt;mytemplate>**) para a posição correspondente na árvore do site: isso é o que acontece se uma página é criada usando o **Sites** guia .

Essa ação de cópia também fornece à página o conteúdo inicial (geralmente somente Conteúdo de nível superior) e a propriedade sling:resourceType, o caminho para o componente de página que é usado para renderizar a página (tudo no nó filho jcr:content).

## Estrutura de um modelo {#structure-of-a-template}

Há dois aspectos a considerar:

* a estrutura do próprio modelo
* a estrutura do conteúdo produzido quando um modelo é usado

Um Modelo é criado em um nó do tipo **cq:Template**.

Várias propriedades podem ser definidas, em particular:

* **jcr:title** - título do modelo; aparece na caixa de diálogo ao criar uma página.
* **jcr:description** - descrição do modelo; aparece na caixa de diálogo ao criar uma página.

Este nó contém *a jcr:content (cq:PageContent)* nó que pode ser usado como a base para o nó de conteúdo das páginas resultantes; esta referência, usando *sling:resourceType*, o componente a ser usado para renderizar o conteúdo real de uma nova página.

>[!NOTE]
>
>Para saber mais sobre as noções básicas de modelos e componentes no AEM, consulte os recursos abaixo:
>
>* [Modelos](/help/sites-developing/templates.md)
>* [Componentes](/help/sites-developing/components.md)
>


Depois de ter a compreensão básica dos Modelos e Componentes, consulte os seguintes recursos:

* [Criação e adição de modelos e componentes](/help/mobile/mobile-ondemand-app-templates.md)
* [Uso das propriedades de conteúdo para exportar conteúdo](/help/mobile/on-demand-content-properties-exporting.md)
* [Práticas recomendadas    ](/help/mobile/best-practices-aem-mobile.md)
* [Desenvolvimento dos serviços de conteúdo da AEM Mobile](/help/mobile/developing-content-services.md)

### Recursos adicionais {#additional-resources}

Para saber mais sobre tópicos adicionais em aplicativos móveis, consulte os links abaixo:

* [Móvel com sincronização de conteúdo](/help/mobile/mobile-ondemand-contentsync.md)
* [Testar aplicativos móveis](/help/mobile/develop-mobile-apps-testing.md)
