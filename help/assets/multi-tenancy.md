---
title: Várias tendências para coleções, snippets e modelos de snippet
description: Segregue o conteúdo no repositório CRX com base na organização do cliente para impedir o acesso não autorizado.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 1%

---


# Multicêntrico para coleções, fragmentos e modelos de fragmento {#multi-tenancy-for-collections-snippets-and-snippet-templates}

O recurso Multi-tenancy permite separar o conteúdo no CRX com base no prefixo da organização e na ID da organização para proteger o conteúdo do acesso não autorizado por usuários de outras organizações.

O Adobe Experience Manager (AEM) Assets armazena dados para cada organização em um caminho diferente. Cada caminho específico da organização é identificado pelo prefixo da organização e pela ID da organização.
que está incluído no local tradicional onde diferentes tipos de ativos são armazenados no CRX.

Por exemplo, se você criar uma pasta chamada `Demo`, AEM ativos por padrão armazena a pasta no local `../content/dam/Demo` no CRX. Com o recurso de multitendência ativado, é possível armazenar os dados em `../content/dam/<organization prefix>/<organization id>Demo`.

Por exemplo, para usuários do Adobe Marketing Cloud do AEM Assets (sob demanda) que são atribuídos à `aodpremium` organização, você pode usar o recurso de multitendência para configurar o seguinte caminho para `../content/dam/mac/aodpremiumDemo`, separar o conteúdo. Neste exemplo, `mac` é o prefixo da organização e `aodpremium` é a ID da organização.

Com base na organização e na ID do usuário, esse caminho qualificado é exibido na interface do AEM Assets e em vários assistentes, incluindo os assistentes de criação Mover e Snippet para aplicar a segmentação.

O recurso de multitendência permite que você segmente os seguintes tipos de ativos e componentes:

* Coleções
* Coleções públicas
* Catálogos (incluindo o assistente para Adicionar/Selecionar página)
* Modelos
* Modelos de fragmento
* Lightbox
