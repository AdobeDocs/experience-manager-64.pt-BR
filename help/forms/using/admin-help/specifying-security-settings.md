---
title: Especificação das configurações de segurança
seo-title: Specifying security settings
description: Saiba como especificar configurações de segurança.
seo-description: Learn how to specify security settings.
uuid: 63ba7819-e4eb-4d28-8463-142ff4233a1e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 36a7e16f-d09d-4cc5-babd-1ccadba76e16
exl-id: 0bda2e58-9470-48fa-a60b-04a1a32689bb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 9%

---

# Especificação das configurações de segurança {#specifying-security-settings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Forms permite controlar se entidades externas em entradas XML são resolvidas. Por padrão, eles são resolvidos, mas você pode alterar esse comportamento para aumentar a segurança do sistema de formulários AEM.

**Impedir o processamento de arquivos de dados XML que contêm referências a entidades externas**

1. No console de administração, clique em **[!UICONTROL Serviços > Forms]**.
1. Desmarque a caixa de seleção Resolver entidades externas .
1. Clique em **[!UICONTROL Salvar]**.
