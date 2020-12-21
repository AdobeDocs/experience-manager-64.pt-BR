---
title: Clientlibs para componentes de comunidades
seo-title: Clientlibs para componentes de comunidades
description: Bibliotecas do cliente para Comunidades
seo-description: Bibliotecas do cliente para Comunidades
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 1%

---


# Componentes do Clientlibs para Comunidades {#clientlibs-for-communities-components}

## Introdução {#introduction}

Esta seção da documentação descreve como adicionar bibliotecas do lado do cliente (clientlibs) a uma página para componentes do Communities.

Para obter informações básicas, visite:

* [Usar ](../../help/sites-developing/clientlibs.md) bibliotecas do lado do cliente, que fornecem detalhes de uso e ferramentas de depuração
* [Clientlibs para ](client-customize.md#clientlibs) SCF, que fornece informações úteis ao personalizar componentes SCF
* [Blog: Bibliotecas AEM clientes explicadas por exemplo](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Por que os clientlibs são obrigatórios {#why-clientlibs-are-required}

Clientlibs são necessários para o funcionamento correto (JavaScript) e o estilo (CSS) de um componente.

Quando houver uma [função da comunidade](functions.md) para um recurso, todos os componentes e configurações necessários, incluindo os clientlibs necessários, estarão presentes no site da comunidade. Somente se componentes adicionais estiverem disponíveis para os autores precisariam ser adicionados clientlibs adicionais.

Quando faltam os clientlibs necessários, a adição de um componente Comunidades a uma página[ pode resultar em erros de javascript, bem como em uma aparência inesperada.](author-communities.md)

### Exemplo: Revisões feitas sem Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Exemplo: Revisões colocadas com Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificando Clientlibs Necessários {#identifying-required-clientlibs}

As informações de recursos essenciais para desenvolvedores identificam os clientlibs necessários.

Além disso, de uma instância AEM, navegar até [Community Components Guide](components-guide.md) fornece acesso a uma lista de categorias clientlib necessárias para um componente.

Por exemplo, na parte superior da [página de revisões](http://localhost:4502/content/community-components/en/reviews.html) os clientlibs necessários listados são

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Adicionando Clientlibs Necessários {#adding-required-clientlibs}

Quando for desejado adicionar um componente Comunidades a uma página, será necessário adicionar os clientlibs necessários para o componente, caso ainda não estejam presentes.

Use [CRXDE|Lite](#using-crxde-lite) para modificar uma clientlibslist existente para uma página do site da comunidade.

Para adicionar uma clientlib para um site da comunidade usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Navegue até [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Localize o nó `clientlibslist` da página na qual deseja adicionar o componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Com o nó `clientlibslist` selecionado

   * Localize a propriedade String[] `scg:requiredClientLibs`
   * Selecione `Value` para acessar a caixa de diálogo String array

      * Role para baixo se necessário
      * Selecione `+` para inserir uma nova biblioteca de cliente

         * Repita o procedimento para adicionar mais bibliotecas de clientes
      * Selecione **[!UICONTROL OK]**
   * Selecione **[!UICONTROL Salvar tudo]**



>[!NOTE]
>
>Se o site não for um site da comunidade, a existência ou o local das bibliotecas clientes em uso para o site precisará ser descoberto.

Usando o exemplo [Introdução ao AEM Communities](getting-started.md), onde `site-name` é *engajar*, esta é a forma como a clientliblist aparecerá se o componente de revisão for adicionado:

![chlimage_1-247](assets/chlimage_1-247.png)

