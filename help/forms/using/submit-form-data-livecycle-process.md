---
title: Configurar o AEM Forms para enviar dados de formulário para um processo AEM Forms no JEE
seo-title: Configurar o AEM Forms para enviar dados de formulário para um processo AEM Forms no JEE
description: O AEM Forms permite integrar formulários adaptáveis com o AEM Forms em processos JEE para processamento de dados de formulários.
seo-description: O AEM Forms permite integrar formulários adaptáveis com o AEM Forms em processos JEE para processamento de dados de formulários.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18

---


# Configurar o AEM Forms para enviar dados de formulário para um processo AEM Forms no JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Formulários adaptáveis oferecem suporte ao envio de dados para um processo AEM Forms no JEE para processamento adicional. Ele permite acionar um processo AEM Forms no JEE com os dados disponíveis no formulário enviado. Execute as seguintes etapas para permitir que sua instância do AEM Forms envie um formulário adaptável para o processo AEM Forms no JEE:

## Configurar o servidor do AEM Forms {#configure-your-aem-forms-server}

Execute as seguintes etapas para permitir que o servidor de formulários AEM envie dados para um servidor AEM Forms no JEE:

1. Vá para o console de configuração da Web do AEM em https://[*host*]:[*port*]/system/console/configMgr.

1. Localize e clique no componente de Configuração **do SDK do** Adobe LiveCycle Client.
1. Clique para editar o URL do servidor de configuração, o nome de usuário e a senha dos formulários AEM no servidor JEE.
1. Revise as configurações e clique em **Salvar**.

![Configuração do SDK do Adobe LiveCycle Client](assets/clientsdkconfiguration.jpg)

## Mapear dados com campos de processo {#map-data-with-process-fields}

Depois que o AEM Forms for configurado, mapeie o XML de dados e os anexos do formulário enviado para os campos no processo AEM Forms no JEE. Para fazer isso:

1. No console de configuração da Web do AEM, clique para editar a configuração do **Guia LiveCycle Process Locator e do Invocador** .
1. Especifique os seguintes parâmetros:

   * **Nome do parâmetro** xml de dados (obrigatório): Especifique o arquivo de propriedade XML do processo AEM Forms em JEE que precisa processar os dados enviados. The default value is **dataxml**.
   * **Nome do parâmetro** de anexos de arquivo (opcional): Especifique a lista de objetos de documento que o processo AEM Forms em JEE precisa processar. The default value is **fileAttachmentsList**.

1. Revise as configurações e clique em **Salvar**.

![Diretrizes do LiveCycle Process Locator e do Invocador](assets/test3.jpg)

Depois de configurada, a ação de envio Enviar para o fluxo de trabalho do Forms lista os processos do servidor AEM que contêm o parâmetro xml de dados especificado.
