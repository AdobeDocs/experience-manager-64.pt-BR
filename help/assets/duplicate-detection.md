---
title: Ativar a detecção de duplicatas
description: Saiba como habilitar a detecção de ativos duplicados no AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Ativando a Detecção de Duplicatas {#enabling-duplicate-detection}

Se você tentar fazer upload de um ativo que existe no Adobe Experience Manager (AEM) Assets, o recurso de detecção de duplicatas o identificará como duplicado. A detecção de duplicados está desabilitada por padrão. Para ativar o recurso, execute as seguintes etapas:

1. Abra a página **[!UICONTROL Configuração do Adobe Experience Manager Web Console]** em `https://[server]:[port]/system/console/configMgr`.
1. Edite a configuração do servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecione a opção **[!UICONTROL detect duplicate]** e clique/toque em **[!UICONTROL Save]**.

   ![Selecione a opção detectar duplicata no servlet](assets/chlimage_1-377.png)

O recurso detectar duplicata agora está ativado no AEM Assets. Quando um usuário tenta fazer upload de um ativo que existe no AEM, o sistema verifica se há conflito e o indica. Os ativos são identificados usando o hash SHA-1 armazenado em `jcr:content/metadata/dam:sha1`, o que significa que os ativos duplicados são detectados independentemente dos nomes de arquivo.

>[!MORELIKETHIS]
>
>* [Duplicar ativos no repositório existente (um tutorial do membro da comunidade)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

