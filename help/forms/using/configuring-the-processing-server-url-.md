---
title: Definir configurações AEM DS
seo-title: Definir configurações AEM DS
description: Você precisa especificar o URL do servidor de processamento antes de enviar um formulário.
seo-description: Você precisa especificar o URL do servidor de processamento antes de enviar um formulário.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Definir AEM configurações do DS {#configuring-aem-ds-settings}

Este artigo descreve como configurar o **AEM Serviço de Definições do DS**. Essa configuração pode ser usada em vários cenários, por exemplo:

* Em gerenciamento de correspondência

   * Para configurar o Fluxo de trabalho do AEM Forms
   * Ao usar o portal de formulários para salvar remotamente o rascunho/envio

* Em Formulários adaptáveis para casos em que o formulário adaptável é enviado da instância de publicação

A seguir estão as etapas para configurar as **[!UICONTROL AEM Configurações do DS]**:

1. Abra o Configuration Manager na instância de publicação usando o URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Na janela **[!UICONTROL Adobe Experience Manager Web Console Configuration]**, localize e clique na opção **[!UICONTROL AEM DS Settings]**.

   ![ds_settings](assets/ds_settings.png)

1. A janela **[!UICONTROL AEM DS Settings Service]** exibe as definições de configuração comuns para AEM componentes DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Adicione as seguintes informações nos respectivos campos:

   **[!UICONTROL URL]** do servidor de processamento: O Servidor de processamento é o servidor no qual o fluxo de trabalho do Forms ou AEM precisa ser acionado. Isso pode ser igual ao URL da instância do autor do AEM ou do outro URL do Servidor (ou seja, http:// localhost:port/).

   **[!UICONTROL Nome]** de usuário do servidor de processamento: Nome de usuário do usuário do workflow  [com base no URL do servidor que está sendo usado]

   **[!UICONTROL Senha]** do servidor de processamento: Senha do usuário do fluxo de trabalho

   >[!NOTE]
   >
   >* Ao usar workflows do Forms ou AEM, antes de fazer qualquer envio do servidor de publicação, é necessário configurar o serviço de configurações do DS. Caso contrário, a apresentação do formulário não será válida.

