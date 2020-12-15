---
title: Configurar restrições de upload de ativos
description: Saiba como configurar os ativos Adobe Experience Manager (AEM) para restringir o tipo de ativos (arquivos) que os usuários podem carregar.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 30%

---


# Configurar restrições de upload de ativos {#configuring-asset-upload-restrictions}

Você pode configurar os ativos Adobe Experience Manager (AEM) para restringir o tipo de ativos (arquivos) que os usuários podem carregar. Este recurso ajuda a eliminar a possibilidade de os usuários carregarem ativos em um formato indesejado ou carregarem arquivos mal-intencionados. O serviço `Day CQ DAM Asset Upload Restriction` permite controlar o tipo de arquivos que os usuários podem carregar. Por padrão, a AEM Assets permite que os usuários façam upload de ativos de todos os tipos MIME. No entanto, você pode configurar o serviço para restringir usuários a carregarem somente arquivos de tipos MIME específicos.

1. Para abrir o console da Web do Configuration Manager, acesse `https://[AEM_server]:[port]/system/console/configMgr`.
1. Abra o serviço **[!UICONTROL Day CQ DAM Asset Upload Restriction]** no modo Editar. Por padrão, a opção **Permitir todos os MIME** está selecionada, o que permite que os usuários carreguem arquivos de todos os tipos MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Para impedir que usuários façam upload de arquivos apenas de determinados tipos MIME, desmarque a opção **[!UICONTROL Permitir todos os tipos MIME]** e especifique os tipos MIME permitidos nos campos **[!UICONTROL MIMEs de ativos permitidos (regex)]** usando expressões regulares.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Clique/toque em **[!UICONTROL Salvar]** para salvar as alterações. Se você especificar cadeias de caracteres MIME para os tipos MIME permitidos, a operação de upload falhará todos os ativos de tipo MIME que não correspondam às cadeias de caracteres MIME configuradas nesses campos.
