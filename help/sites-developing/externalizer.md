---
title: Exteriorização de URLs
seo-title: Externalizing URLs
description: O Externalizador é um serviço OSGI que permite transformar programaticamente um caminho de recurso em um URL externo e absoluto
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# Exteriorização de URLs{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Em AEM, a variável **Externalizador** é um serviço OSGI que permite transformar programaticamente um caminho de recurso (por exemplo, `/path/to/my/page`) em um URL externo e absoluto (por exemplo, `https://www.mycompany.com/path/to/my/page`) ao prefixar o caminho com um DNS pré-configurado.

Como uma instância não pode saber seu URL externamente visível se estiver em execução atrás de uma camada da Web e porque, às vezes, um link precisa ser criado fora do escopo da solicitação, esse serviço fornece um local central para configurar esses URLs externos e criá-los.

Esta página explica como configurar a variável **Externalizador** e como usá-lo. Para obter mais detalhes, consulte o [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configurar o serviço Externalizador {#configuring-the-externalizer-service}

O **Externalizador** permite definir centralmente vários domínios que podem ser usados para prefixar programaticamente caminhos de recursos. Cada domínio é identificado por um nome exclusivo usado para fazer referência programaticamente ao domínio.

Para definir um mapeamento de domínio para a variável **Externalizador** serviço:

1. Navegue até o gerenciador de configuração por meio de **Ferramentas**, em seguida **Console da Web** ou insira `https://<host>:<port>/system/console/configMgr.`
1. Clique em **Externalizador de links CQ do dia** para abrir a caixa de diálogo de configuração.

   >[!NOTE]
   >
   >O link direto para a configuração é `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Defina um mapeamento de domínio: um mapeamento consiste em um nome exclusivo que pode ser usado no código para fazer referência ao domínio, a um espaço e ao domínio:

   `<unique-name> [scheme://]server[:port][/contextpath]`, em que:

   * **esquema** geralmente é http ou https, mas também pode ser ftp etc.; use https para aplicar links https, se desejado; ele será usado se o código do cliente não substituir o esquema ao solicitar a externalização de um URL.
   * **server** é o nome do host (pode ser um nome de domínio ou endereço ip).
   * **porta** (opcional) é o número da porta.
   * **contextpath** (opcional) só será definido se AEM for instalado como um aplicativo web em um caminho de contexto diferente.

   Por exemplo: `production https://my.production.instance`

   Os seguintes nomes de mapeamento são predefinidos e devem sempre ser definidos conforme AEM dependem deles:

   * **local** - a instância local
   * **autor** - DNS do sistema de criação
   * **publicar** - DNS, o sítio web público

   >[!NOTE]
   >
   >Uma configuração personalizada permite adicionar uma nova categoria, como &quot;produção&quot;, &quot;armazenamento temporário&quot; ou até mesmo sistemas externos não AEM, como &quot;meu serviço interno da Web&quot;, e é útil para evitar a codificação dessas URLs em diferentes locais na base de código de um projeto.

1. Clique em **Salvar** para salvar as alterações.

>[!NOTE]
>
>O Adobe recomenda que você [adicionar a configuração ao repositório](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Uso do serviço Externalizador {#using-the-externalizer-service}

Esta seção mostra alguns exemplos de como a variável **Externalizador** pode ser usado.

**Para obter o serviço Externalizador em um JSP:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Para exteriorizar um caminho com o domínio &quot;publicar&quot;:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Considerando o mapeamento de domínio &quot; `publish https://www.website.com`&quot;, myExternalizedUrl acaba com o valor &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Para exteriorizar um caminho com o domínio &quot;autor&quot;:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Considerando o mapeamento de domínio &quot; `author https://author.website.com`&quot;, myExternalizedUrl acaba com o valor &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Para exteriorizar um caminho com o domínio &quot;local&quot;:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Considerando o mapeamento de domínio &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl acaba com o valor &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Você pode encontrar mais exemplos na [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
