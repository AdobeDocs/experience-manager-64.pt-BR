---
title: Ativar a detecção de duplicatas
description: Saiba como habilitar a detecção de ativos duplicados no AEM.
contentOwner: AG
feature: Gerenciamento de ativos,Relatórios de ativos
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Ativar a detecção de duplicatas {#enabling-duplicate-detection}

Se você tentar fazer upload de um ativo que existe no Adobe Experience Manager (AEM) Assets, o recurso de detecção de duplicatas o identificará como duplicado. A detecção de duplicados está desabilitada por padrão. Para ativar o recurso, execute as seguintes etapas:

1. Abra a página **[!UICONTROL Configuração do Adobe Experience Manager Web Console]** em `https://[server]:[port]/system/console/configMgr`.
1. Edite a configuração do servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecione a opção **[!UICONTROL detect duplicate]** e clique/toque em **[!UICONTROL Save]**.

   ![Selecione a opção detectar duplicata no servlet](assets/chlimage_1-377.png)

O recurso detectar duplicata agora está ativado no AEM Assets. Quando um usuário tenta fazer upload de um ativo que existe no AEM, o sistema verifica se há conflito e o indica. Os ativos são identificados usando o hash SHA-1 armazenado em `jcr:content/metadata/dam:sha1`, o que significa que os ativos duplicados são detectados independentemente dos nomes de arquivo.

>[!MORELIKETHIS]
>
>* [Duplicar ativos no repositório existente (um tutorial do membro da comunidade)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

