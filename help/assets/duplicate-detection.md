---
title: Ativação da detecção de Duplicados
description: Saiba como ativar a detecção de ativos de duplicado no AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Ativação da detecção de Duplicados {#enabling-duplicate-detection}

Se você tentar fazer upload de um ativo que existe no Adobe Experience Manager (AEM) Assets, o recurso de detecção de duplicados o identificará como duplicado. A detecção de Duplicados está desativada por padrão. Para ativar o recurso, execute as seguintes etapas:

1. Abra a página Configuração **[!UICONTROL do console da Web do]** Adobe Experience Manager em `https://[server]:[port]/system/console/configMgr`.
1. Edite a configuração para o **[!UICONTROL Dia do servlet CQ DAM Criar ativo]**.
1. Selecione a opção **[!UICONTROL detectar duplicado]** e clique/toque em **[!UICONTROL Salvar]**.

   ![Selecione a opção detectar duplicado no servlet](assets/chlimage_1-377.png)

O recurso de detecção de duplicado agora está ativado no AEM Assets. Quando um usuário tenta carregar um ativo que existe no AEM, o sistema verifica se há conflito e o indica. Os ativos são identificados usando o hash SHA-1 armazenado em `jcr:content/metadata/dam:sha1`, o que significa que os ativos do duplicado são detectados independentemente dos nomes dos arquivos.

>[!MORELIKETHIS]
>
>* [Ativos do Duplicado no repositório existente (um tutorial de um membro da comunidade)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

