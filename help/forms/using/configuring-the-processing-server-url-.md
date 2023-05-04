---
title: Definir configurações AEM DS
seo-title: Configuring AEM DS settings
description: Você precisa especificar o URL do servidor de processamento antes de enviar um formulário.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---

# Definir configurações AEM DS {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Este artigo descreve como configurar **Serviço de Definições do AEM DS**. Essa configuração pode ser usada em vários cenários, por exemplo:

* Em gerenciamento de correspondência

   * Para configurar o Fluxo de trabalho do AEM Forms
   * Ao usar o portal de formulários para salvar remotamente o rascunho/envio

* Em Formulários adaptáveis para casos em que o formulário adaptável é enviado da instância de publicação

Veja a seguir as etapas para configurar o **[!UICONTROL Definições do AEM DS]**:

1. Abra o Configuration Manager na instância de publicação usando o URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. No **[!UICONTROL Configuração do Console da Web do Adobe Experience Manager]** , localize e clique na guia **[!UICONTROL Definições do AEM DS]** opção.

   ![ds_settings](assets/ds_settings.png)

1. O **[!UICONTROL Serviço de Definições do AEM DS]** exibe as configurações comuns dos componentes AEM DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Adicione as seguintes informações nos respectivos campos:

   **[!UICONTROL URL do servidor de processamento]**: O Servidor de processamento é o servidor no qual o fluxo de trabalho do Forms ou AEM precisa ser acionado. Isso pode ser igual ao URL da instância do autor do AEM ou do outro URL do Servidor (ou seja, http:// localhost:port/).

   **[!UICONTROL Nome de usuário do servidor de processamento]**: Nome de usuário do usuário do fluxo de trabalho [com base no URL do servidor que está sendo usado]

   **[!UICONTROL Senha do servidor de processamento]**: Senha do usuário do fluxo de trabalho

   >[!NOTE]
   >
   >* Ao usar workflows do Forms ou AEM, antes de fazer qualquer envio do servidor de publicação, é necessário configurar o serviço de configurações do DS. Caso contrário, a apresentação do formulário não será válida.

