---
title: Mapeamento de recursos
seo-title: Mapeamento de recursos
description: Saiba como definir redirecionamentos, URLs personalizadas e hosts virtuais para AEM usando o mapeamento de recursos.
seo-description: Saiba como definir redirecionamentos, URLs personalizadas e hosts virtuais para AEM usando o mapeamento de recursos.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---


# Mapeamento de recursos{#resource-mapping}

O mapeamento de recursos é usado para definir redirecionamentos, URLs personalizadas e hosts virtuais para AEM.

Por exemplo, você pode usar esses mapeamentos para:

* Coloque o prefixo `/content` em todas as solicitações para que a estrutura interna fique oculta dos visitantes do seu site.
* Defina um redirecionamento para que todas as solicitações para a página `/content/en/gateway` do site sejam redirecionadas para `https://gbiv.com/`.

Um mapeamento HTTP possível [prefixa todas as solicitações para localhost:4503 com /content](#configuring-an-internal-redirect-to-content). Um mapeamento como esse pode ser usado para ocultar a estrutura interna dos visitantes do site, conforme permite:

`localhost:4503/content/geometrixx/en/products.html`

a ser acessado usando:

`localhost:4503/geometrixx/en/products.html`

já que o mapeamento adicionará automaticamente o prefixo `/content` a `/geometrixx/en/products.html`.

>[!CAUTION]
>
>URLs personalizadas não suportam padrões regex.

>[!NOTE]
>
>Consulte a documentação do Sling e [Mapeamentos para Resolução de Recursos](https://sling.apache.org/site/resources.html) e [Recursos](https://sling.apache.org/site/mappings-for-resource-resolution.html) para obter mais informações.

## Exibindo Definições de Mapeamento {#viewing-mapping-definitions}

Os mapeamentos de duas listas que o Resolvedor de Recursos do JCR avalia (de cima para baixo) para encontrar uma correspondência.

Essas listas podem ser visualizadas (junto com informações de configuração) sob a opção **JCR ResourceResolver** do console Felix; por exemplo, `https://<host>:<port>/system/console/jcrresolver`:

* Configuração

   Mostra a configuração atual (conforme definido para [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Teste de configuração

   Isso permite inserir um URL ou caminho de recurso. Clique em **Resolver** ou **Mapa** para confirmar como o sistema transformará a entrada.

* ****
Entradas do Mapa do ResolvedorA lista de entradas usadas pelos métodos ResourceResolver.resolve para mapear URLs para Recursos.

* **Mapeamento de**
entradas do mapaA lista de entradas usadas pelos métodos ResourceResolver.map para mapear caminhos de recursos para URLs.

As duas listas mostram várias entradas, incluindo as definidas como padrões pelo(s) aplicativo(s). Geralmente, o objetivo é simplificar os URLs para o usuário.

As listas emparelham um **Padrão**, uma expressão regular correspondente à solicitação, com um **Substituição** que define o redirecionamento a ser imposto.

Por exemplo, o:

**Padrão** `^[^/]+/[^/]+/welcome$`

acionará o:

**Substituição** `/libs/cq/core/content/welcome.html`.

para redirecionar uma solicitação:

`http://localhost:4503/welcome`

para:

`http://localhost:4503/libs/cq/core/content/welcome.html`

Novas definições de mapeamento são criadas no repositório.

>[!NOTE]
>
>Há muitos recursos disponíveis que ajudam a explicar como definir expressões regulares; por exemplo [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Criando definições de mapeamento em AEM {#creating-mapping-definitions-in-aem}

Em uma instalação padrão de AEM, você pode encontrar a pasta:

`/etc/map/http`

Essa é a estrutura usada ao definir mapeamentos para o protocolo HTTP. Outras pastas ( `sling:Folder`) podem ser criadas em `/etc/map` para quaisquer outros protocolos que você deseja mapear.

### Configurar um redirecionamento interno para /content {#configuring-an-internal-redirect-to-content}

Para criar o mapeamento que prefixa qualquer solicitação para http://localhost:4503/ com `/content`:

1. Usando o CRXDE, navegue até `/etc/map/http`.

1. Crie um novo nó:

   * **Tipo** `sling:Mapping`

      Esse tipo de nó é destinado a esses mapeamentos, embora seu uso não seja obrigatório.

   * **Nome** `localhost_any`

1. Clique em **Salvar tudo**.
1. **** Adicione as seguintes propriedades a este nó:

   * **Nome** `sling:match`

      * **Tipo** `String`
      * **Valor** `localhost.4503/`
   * **Nome** `sling:internalRedirect`

      * **Tipo** `String`
      * **Valor** `/content/`


1. Clique em **Salvar tudo**.

Isso lidará com uma solicitação como:\
`localhost:4503/geometrixx/en/products.html`\
como se:\
`localhost:4503/content/geometrixx/en/products.html`\
tinham sido solicitados.

>[!NOTE]
>
>Consulte [Resources](https://sling.apache.org/site/mappings-for-resource-resolution.html) na Documentação do Sling para obter mais informações sobre as propriedades do sling disponíveis e como elas podem ser configuradas.

>[!NOTE]
>
>Você pode usar `/etc/map.publish` para manter as configurações do ambiente de publicação. Eles devem ser replicados e o novo local ( `/etc/map.publish`) configurado para o **Local de mapeamento** do [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) do ambiente de publicação.

