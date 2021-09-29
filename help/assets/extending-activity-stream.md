---
title: Integração de ativos ao fluxo de atividade
description: Descreve os recursos de gravação de [!DNL Experience Manager] and how to configure [!DNL Experience Manager] para registrar eventos específicos.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Integração de ativos ao fluxo de atividade {#integrating-assets-with-activity-stream}

Os usuários do Adobe Experience Manager Assets executam várias ações, como criar, carregar e excluir Ativos. Essas ações podem ser registradas para que você possa fornecer um histórico do que foi feito por um usuário. Esta seção descreve os recursos de gravação de [!DNL Experience Manager] e como configurar [!DNL Experience Manager] para registrar eventos específicos.

## Considerações de desempenho e comportamento padrão {#performance-considerations-and-default-behavior}

Essa integração pode consumir CPU e espaço em disco, por exemplo, ao fazer importação em massa. Por esses motivos, a integração do [!DNL Experience Manager] Assets com o Fluxo de atividade é desabilitada por padrão.

## Eventos de ação suportados {#supported-action-events}

Os seguintes eventos podem ser configurados para serem registrados:

* Licença aceita (ACEITE)
* Ativo criado (ASSET_CREATED)
* Ativo movido (ASSET_MOVED)
* Ativo removido (ASSET_REMOVED)
* Licença rejeitada (REJEITADA)
* Ativo baixado (BAIXADO)
* Versão do ativo (VERSIONED)
* Versão do ativo restaurada (RESTAURADA)
* Metadados de ativos atualizados (METADATA_UPDATED)
* Ativo publicado no sistema externo (PUBLISHED_EXTERNAL)
* Atualização original do ativo (ORIGINAL_UPDATED)
* Representação de ativo atualizada (RENDITION_UPDATED)
* Representação de ativo removida (RENDITION_REMOVED)
* Subativo atualizado (SUBASSET_UPDATED)
* Subativo removido (SUBASSET_REMOVED)

## Configurar o registro de eventos [!DNL Assets] {#configuring-aem-assets-events-recording}

O [console da Web](/help/sites-deploying/configuring-osgi.md) fornece acesso ao ajuste [!DNL Assets] do Gravador de Eventos. Para configurar o Gravador de Eventos [!DNL Assets], proceda da seguinte maneira:

1. Navegue até **[!UICONTROL Console da Web]**

1. Clique em **[!UICONTROL Configuração]**.

1. Clique duas vezes em **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Marque **[!UICONTROL Habilita este serviço]**.

1. Verifique quais **[!UICONTROL Tipos de evento]** você deseja registrar no fluxo de atividade do usuário.

1. Clique em **[!UICONTROL Salvar]**.

## Lendo eventos gravados {#reading-recorded-events}

Os eventos gravados são armazenados como atividades. Você pode lê-las programaticamente usando a [API do ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
