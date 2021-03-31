---
title: Integração de ativos ao fluxo de atividade
description: Descreve os recursos de gravação do AEM e como configurar o AEM para gravar eventos específicos.
contentOwner: AG
feature: Gerenciamento de ativos
role: Desenvolvedor
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Integração de ativos com o fluxo de atividade {#integrating-assets-with-activity-stream}

Os usuários do Adobe Experience Manager (AEM) Assets executam várias ações, como criar, carregar e excluir Ativos. Essas ações podem ser registradas para que você possa fornecer um histórico do que foi feito por um usuário. Esta seção descreve os recursos de gravação do AEM e como configurar o AEM para gravar eventos específicos.

## Considerações de desempenho e comportamento padrão {#performance-considerations-and-default-behavior}

Essa integração pode consumir CPU e espaço em disco, por exemplo, ao fazer importação em massa. Por esses motivos, a integração do AEM Assets com o fluxo de atividade é desativada por padrão.

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

## Configuração da Gravação de Eventos do AEM Assets {#configuring-aem-assets-events-recording}

O [Console da Web](/help/sites-deploying/configuring-osgi.md) fornece acesso ao ajuste do Gravador de Eventos do AEM Assets. Para configurar o Gravador de eventos do AEM Assets, proceda da seguinte maneira:

1. Navegue até **[!UICONTROL Console da Web]**

1. Clique em **[!UICONTROL Configuração]**.

1. Clique duas vezes em **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Marque **[!UICONTROL Habilita este serviço]**.

1. Verifique quais **[!UICONTROL Tipos de evento]** você deseja registrar no fluxo de atividade do usuário.

1. Clique em **[!UICONTROL Salvar]**.

## Lendo eventos gravados {#reading-recorded-events}

Os eventos gravados são armazenados como atividades. Você pode lê-las programaticamente usando a [API do ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
