---
title: Integração de ativos com o fluxo de atividade
description: Descreve os recursos de gravação do AEM e como configurar o AEM para gravar eventos específicos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Integração de ativos com o fluxo de atividade {#integrating-assets-with-activity-stream}

Os usuários do Adobe Experience Manager (AEM) Assets executam várias ações, como criar, carregar e excluir ativos. Essas ações podem ser registradas para que você possa fornecer um histórico do que foi feito por um usuário. Esta seção descreve os recursos de gravação do AEM e como configurar o AEM para gravar eventos específicos.

## Considerações sobre desempenho e comportamento padrão {#performance-considerations-and-default-behavior}

Essa integração pode ser de CPU e de consumo de espaço em disco, por exemplo, ao fazer a importação em massa. Por esses motivos, a integração do AEM Assets com o Fluxo de Atividades é desativada por padrão.

## Eventos de Ação Suportados {#supported-action-events}

Os seguintes eventos podem ser configurados para serem gravados:

* Licença aceita (ACEITE)
* Ativo criado (ASSET_CREATED)
* Ativo movido (ASSET_MOVED)
* Ativo removido (ASSET_REMOVED)
* Licença rejeitada (REJEITADA)
* Ativo baixado (BAIXADO)
* Versão do ativo (VERSÃO)
* Versão do ativo restaurada (RESTAURADA)
* Metadados do ativo atualizados (METADATA_UPDATED)
* Ativo publicado no sistema externo (PUBLISHED_EXTERNAL)
* Atualização original do ativo (ORIGINAL_UPDATED)
* Renderização de ativo atualizada (RENDITION_UPDATED)
* Renderização de ativo removida (RENDITION_REMOVED)
* Subativo atualizado (SUBASSET_UPDATED)
* Subativo removido (SUBASSET_REMOVED)

## Configuração da gravação de Eventos AEM Assets {#configuring-aem-assets-events-recording}

O [console Web](/help/sites-deploying/configuring-osgi.md) fornece acesso ao ajuste do Gravador de Eventos AEM Assets. Para configurar o Gravador de Eventos AEM Assets, proceda da seguinte maneira:

1. Navegue até **[!UICONTROL console da Web]**

1. Clique em **[!UICONTROL Configuração]**.

1. Clique no duplo **[!UICONTROL Gravador de Evento do Day CQ DAM]**.

1. Marcar **[!UICONTROL Habilita este serviço]**.

1. Verifique quais **[!UICONTROL Tipos de evento]** você deseja que sejam gravados no fluxo de atividade do usuário.

1. Clique em **[!UICONTROL Salvar]**.

## Lendo eventos gravados {#reading-recorded-events}

Os eventos gravados são armazenados como atividades. Você pode lê-los de forma programática usando a [API do Activity Manager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
