---
title: Externalização de URLs
seo-title: Externalização de URLs
description: O Externalizer é um serviço OSGI que permite transformar programaticamente um caminho de recurso em um URL externo e absoluto
seo-description: O Externalizer é um serviço OSGI que permite transformar programaticamente um caminho de recurso em um URL externo e absoluto
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Externalização de URLs{#externalizing-urls}

No AEM, o **Externalizador** é um serviço OSGI que permite transformar programaticamente um caminho de recurso (por exemplo, `/path/to/my/page`) em um URL externo e absoluto (por exemplo, `https://www.mycompany.com/path/to/my/page`) ao prefixar o caminho com um DNS pré-configurado.

Como uma instância não pode saber seu URL visível externamente se estiver sendo executado atrás de uma camada da Web e como, às vezes, um link precisa ser criado fora do escopo da solicitação, esse serviço fornece um local central para configurar esses URLs externos e criá-los.

Esta página explica como configurar o serviço **Externalizer** e como usá-lo. Para obter mais detalhes, consulte os [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configuração do serviço Externalizer {#configuring-the-externalizer-service}

O serviço **Externalizer** permite definir centralmente vários domínios que podem ser usados para prefixar programaticamente caminhos de recursos. Cada domínio é identificado por um nome exclusivo que é usado para fazer referência programaticamente ao domínio.

Para definir um mapeamento de domínio para o serviço **Externalizer** :

1. Navegue até o gerenciador de configuração por meio das **Ferramentas**, em seguida, no Console **** da Web ou digite `https://<host>:<port>/system/console/configMgr.`
1. Clique em Externalizador **de links do CQ de** dia para abrir a caixa de diálogo de configuração.

   >[!NOTE]
   >
   >O link direto para a configuração é `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Defina um mapeamento de domínio: um mapeamento consiste em um nome exclusivo que pode ser usado no código para referenciar o domínio, um espaço e o domínio:

   `<unique-name> [scheme://]server[:port][/contextpath]`, em que:

   * **o esquema** geralmente é http ou https, mas também pode ser ftp etc.; use https para aplicar links https, se desejar; será usado se o código do cliente não substituir o esquema ao solicitar a externalização de um URL.
   * **server** é o nome do host (pode ser um nome de domínio ou endereço IP).
   * **porta** (opcional) é o número da porta.
   * **o caminho de contexto** (opcional) só é definido se AEM é instalado como um aplicativo da Web em um caminho de contexto diferente.

   Por exemplo: `production https://my.production.instance`

   Os seguintes nomes de mapeamento são predefinidos e devem ser sempre definidos como AEM depende deles:

   * **local** - a instância local
   * **autor** - o DNS do sistema de criação
   * **publicar** - DNS do site público

   >[!NOTE]
   >
   >Uma configuração personalizada permite que você adicione uma nova categoria, como &quot;produção&quot;, &quot;armazenamento temporário&quot; ou até mesmo sistemas externos não AEM, como &quot;meu serviço da Web interno&quot;, e é útil para evitar a codificação desses URLs em diferentes locais na base de códigos de um projeto.

1. Click **Save** to save your changes.

>[!NOTE]
>
>O Adobe recomenda que você [adicione a configuração ao repositório](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Uso do serviço Externalizer {#using-the-externalizer-service}

Esta seção mostra alguns exemplos de como o serviço **Externalizer** pode ser usado.

**Para obter o serviço Externalizer em um JSP:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Para externalizar um caminho com o domínio &#39;publicar&#39;:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Supondo que o mapeamento de domínio &quot; `publish https://www.website.com`&quot;, myExternalizedUrl termine com o valor &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Para externalizar um caminho com o domínio &#39;autor&#39;:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Supondo que o mapeamento de domínio &quot; `author https://author.website.com`&quot;, myExternalizedUrl termine com o valor &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Para externalizar um caminho com o domínio &#39;local&#39;:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Supondo que o mapeamento de domínio &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl termine com o valor &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Você pode encontrar mais exemplos nos [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
