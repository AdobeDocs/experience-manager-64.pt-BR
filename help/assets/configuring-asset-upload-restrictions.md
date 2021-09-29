---
title: Configurar restrições de upload de ativos
description: Saiba como configurar o Adobe Experience Manager Assets para restringir o tipo de ativos (arquivos) que os usuários podem fazer upload.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 31%

---

# Configurar restrições de upload de ativos {#configuring-asset-upload-restrictions}

Você pode configurar o Adobe Experience Manager Assets para restringir o tipo de ativos (arquivos) que os usuários podem fazer upload. Esse recurso ajuda a eliminar a possibilidade de usuários fazerem upload de ativos em um formato indesejado ou fazerem upload de arquivos mal-intencionados. O serviço `Day CQ DAM Asset Upload Restriction` permite controlar o tipo de arquivos que os usuários podem fazer upload. Por padrão, [!DNL Experience Manager] o Assets permite que os usuários façam upload de ativos de todos os tipos MIME. No entanto, você pode configurar o serviço para restringir usuários a fazerem upload de arquivos apenas de tipos MIME específicos.

1. Para abrir o console da Web do Configuration Manager, acesse `https://[AEM_server]:[port]/system/console/configMgr`.
1. Abra o serviço **[!UICONTROL Day CQ DAM Asset Upload Restriction]** no modo de Edição. Por padrão, a opção **Allow all MIME** é selecionada, o que permite que os usuários façam upload de arquivos de todos os tipos MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Para impedir que usuários façam upload de arquivos apenas de determinados tipos MIME, desmarque a opção **[!UICONTROL Permitir todos os tipos MIME]** e especifique os tipos MIME permitidos nos campos **[!UICONTROL MIMEs de ativos permitidos (regex)]** usando expressões regulares.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Clique/toque em **[!UICONTROL Salvar]** para salvar as alterações. Se você especificar cadeias de caracteres MIME para os tipos MIME permitidos, a operação de upload falhará todos os ativos de tipo MIME que não correspondam às cadeias de caracteres MIME configuradas nesses campos.
