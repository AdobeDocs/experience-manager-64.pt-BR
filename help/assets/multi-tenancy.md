---
title: Multilocação para coleções, trechos e modelos de trecho
description: Segmente o conteúdo no repositório CRX com base na organização do cliente para impedir o acesso não autorizado.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 4%

---

# Multilocação para coleções, trechos e modelos de trecho {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O recurso Multilocação permite separar o conteúdo no CRX com base no prefixo da organização e na ID da organização para proteger o conteúdo do acesso não autorizado por usuários de outras organizações.

O Adobe Experience Manager (AEM) Assets armazena dados para cada organização em um caminho diferente. Cada caminho específico da organização é identificado pelo prefixo da organização e pela ID da organização.
que está incluído no local tradicional em que diferentes tipos de ativos são armazenados no CRX.

Por exemplo, se você criar uma pasta chamada `Demo`, AEM ativos por padrão armazena a pasta em `../content/dam/Demo` no CRX. Com o recurso de multilocação ativado, é possível armazenar os dados em `../content/dam/<organization prefix>/<organization id>Demo`.

Por exemplo, para usuários do Adobe Marketing Cloud do AEM Assets (sob demanda) atribuídos a `aodpremium` , você pode usar o recurso de multilocação para configurar o seguinte caminho para `../content/dam/mac/aodpremiumDemo`, separe o conteúdo. Neste exemplo `mac` é o prefixo da organização e `aodpremium` é a ID da organização.

Com base na organização e na ID do usuário, esse caminho qualificado é exibido na interface do AEM Assets e em vários assistentes, incluindo os assistentes de criação Mover e Snippet para impor a segmentação.

O recurso de multilocação permite segmentar os seguintes tipos de ativos e componentes:

* Coleções
* Coleções públicas
* Catálogos (incluindo o assistente Adicionar/Selecionar página )
* Modelos
* Modelos de trecho
* Lightbox
