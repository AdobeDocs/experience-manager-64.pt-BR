---
title: Traduzindo conteúdo para sites multilíngues
seo-title: Traduzindo conteúdo para sites multilíngues
description: Saiba como traduzir conteúdo para sites multilíngues.
seo-description: Saiba como traduzir conteúdo para sites multilíngues.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Traduzindo conteúdo para sites multilíngues{#translating-content-for-multilingual-sites}

Automatize a tradução de conteúdo da página, ativos e conteúdo gerado pelo usuário para criar e manter sites multilíngues. Para automatizar workflows de tradução, você integra provedores de serviço de tradução ao AEM e cria projetos para traduzir conteúdo em vários idiomas. AEM apoia workflows de tradução automática e humana.

* Tradução humana: O conteúdo é enviado ao seu provedor de tradução e traduzido por tradutores profissionais. Quando concluído, o conteúdo convertido é retornado e importado para o AEM. Quando seu provedor de tradução está integrado ao AEM, o conteúdo é enviado automaticamente entre o AEM e o provedor de tradução.
* Tradução automática: O serviço de tradução automática traduz imediatamente seu conteúdo.

A tradução de conteúdo envolve as seguintes etapas:

1. [Conecte AEM com seu provedor de serviço](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) de tradução e [crie configurações](/help/sites-administering/tc-tic.md)de estrutura de integração de tradução.

1. [Associe as páginas do seu idioma principais](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) às configurações do serviço de tradução e da estrutura.
1. [Identifique o tipo de conteúdo](/help/sites-administering/tc-rules.md) a ser traduzido.
1. [Prepare o conteúdo para tradução](/help/sites-administering/tc-prep.md) criando o idioma principal e as páginas raiz das cópias de idioma.
1. [Crie projetos](/help/sites-administering/tc-manage.md) de tradução para coletar o conteúdo para traduzir e preparar o processo de tradução.
1. Use os projetos de tradução para [gerenciar o processo](/help/sites-administering/tc-manage.md)de tradução de conteúdo.

Se o seu provedor de serviço de tradução não fornecer um conector para integração com o AEM, o AEM oferece suporte à extração manual e à reinserção do conteúdo de tradução no formato XML.

>[!NOTE]
>
>Seu usuário precisa ser membro do grupo de administradores do projeto para usar os recursos de Cópia de idioma.

## Práticas recomendadas     {#best-practices}

A página Práticas recomendadas [de](/help/sites-administering/tc-bp.md) tradução contém informações importantes sobre sua implementação.
