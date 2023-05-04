---
title: Ativar a detecção de duplicatas
description: Saiba como habilitar a detecção de ativos duplicados no AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# Ativar a detecção de duplicatas {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Se você tentar fazer upload de um ativo que existe no Adobe Experience Manager Assets, o recurso de detecção de duplicatas o identificará como duplicado. A detecção de duplicados está desabilitada por padrão. Para ativar o recurso, execute as seguintes etapas:

1. Abra o **[!UICONTROL Configuração do Console da Web do Adobe Experience Manager]** página em `https://[server]:[port]/system/console/configMgr`.
1. Editar a configuração do servlet **[!UICONTROL Criar ativo do DAM CQ do dia]**.
1. Selecione o **[!UICONTROL detectar duplicata]** e clicar/tocar **[!UICONTROL Salvar]**.

   ![Selecione a opção detectar duplicata no servlet](assets/chlimage_1-377.png)

O recurso detectar duplicata agora está ativado no [!DNL Experience Manager] Ativos. Quando um usuário tenta fazer upload de um ativo que existe no AEM, o sistema verifica se há conflito e o indica. Os ativos são identificados usando o hash SHA-1 armazenado em `jcr:content/metadata/dam:sha1`, o que significa que os ativos duplicados são detectados independentemente dos nomes de arquivo.

>[!MORELIKETHIS]
>
>* [Duplicar ativos no repositório existente (um tutorial do membro da comunidade)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

