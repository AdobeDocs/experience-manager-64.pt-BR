---
title: Definição das configurações AEM DS
seo-title: Definição das configurações AEM DS
description: É necessário especificar o URL do servidor de processamento antes de enviar um formulário.
seo-description: É necessário especificar o URL do servidor de processamento antes de enviar um formulário.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Definição das configurações AEM DS {#configuring-aem-ds-settings}

Este artigo descreve como configurar o Serviço **de configurações do** AEM DS. Essa configuração pode ser usada em vários cenários, por exemplo:

* No gerenciamento de correspondência

   * Para configurar o AEM Forms Workflow
   * Ao usar o portal de formulários para salvar remotamente o rascunho/envio

* Em Formulários adaptáveis para casos em que o formulário adaptativo é enviado da instância de publicação

Veja a seguir as etapas para configurar as Configurações **[!UICONTROL do]** AEM DS:

1. Abra o Configuration Manager na instância de publicação usando o URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Na janela Configuração **[!UICONTROL do console da Web do]** Adobe Experience Manager, localize e clique na opção Configurações **[!UICONTROL do]** AEM DS.

   ![ds_settings](assets/ds_settings.png)

1. A janela Serviço **[!UICONTROL de configurações do]** AEM DS exibe as configurações comuns para AEM componentes do DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Adicione as seguintes informações nos respectivos campos:

   **[!UICONTROL URL]** do servidor de processamento: O Servidor de processamento é o servidor no qual o fluxo de trabalho do Forms ou do AEM precisa ser acionado. Isso pode ser igual ao URL da instância do autor AEM ou do outro URL do servidor (ou seja, http:// localhost:port/).

   **[!UICONTROL Nome]** de usuário do servidor de processamento: Nome de usuário do usuário do fluxo de trabalho [com base no URL do servidor que está sendo usado]

   **[!UICONTROL Senha]** do servidor de processamento: Senha do usuário do fluxo de trabalho

   >[!NOTE]
   >
   >* Ao usar workflows Forms ou AEM, antes de fazer qualquer envio do servidor de publicação, é necessário configurar o serviço de configurações do DS. Caso contrário, a apresentação do formulário não será efetuada.

