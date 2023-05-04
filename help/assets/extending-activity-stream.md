---
title: Integração de ativos ao fluxo de atividade
description: Descreve os recursos de gravação de [!DNL Experience Manager] e como configurar [!DNL Experience Manager] para registrar eventos específicos.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

---

# Integração de ativos ao fluxo de atividade {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os usuários do Adobe Experience Manager Assets executam várias ações, como criar, carregar e excluir Ativos. Essas ações podem ser registradas para que você possa fornecer um histórico do que foi feito por um usuário. Esta seção descreve os recursos de gravação de [!DNL Experience Manager] e como configurar [!DNL Experience Manager] para registrar eventos específicos.

## Considerações de desempenho e comportamento padrão {#performance-considerations-and-default-behavior}

Essa integração pode consumir CPU e espaço em disco, por exemplo, ao fazer importação em massa. Por estas razões, o [!DNL Experience Manager] A integração do Assets com o Fluxo de atividade é desativada por padrão.

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

## Configuração [!DNL Assets] Registro de eventos {#configuring-aem-assets-events-recording}

O [Console da Web](/help/sites-deploying/configuring-osgi.md) fornece acesso ao [!DNL Assets] Ajuste do Gravador de Eventos. Para configurar o [!DNL Assets] Gravador de eventos, proceda da seguinte maneira:

1. Navegue até o **[!UICONTROL Console da Web]**

1. Clique em **[!UICONTROL Configuração]**.

1. Clique duas vezes **[!UICONTROL Gravador de eventos CQ DAM]**.

1. Verificar **[!UICONTROL Habilita este serviço]**.

1. Verificar **[!UICONTROL Tipos de evento]** você deseja ser registrado no fluxo de atividade do usuário.

1. Clique em **[!UICONTROL Salvar]**.

## Lendo eventos gravados {#reading-recorded-events}

Os eventos gravados são armazenados como atividades. Você pode lê-las programaticamente usando o [API do ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
