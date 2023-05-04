---
title: Especificar configurações de segurança
seo-title: Specify security settings
description: Saiba como especificar configurações de segurança.
seo-description: Learn how to specify security settings.
uuid: c86ba195-010d-40d6-9f9d-4cb4c364d104
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3c017f9a-aa7f-4d12-ba8b-9fd92c029157
exl-id: 3cc39a24-dbdf-4a4c-9c96-4d39d8cff20d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 9%

---

# Especificar configurações de segurança {#specify-security-settings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Output permite controlar se entidades externas em entradas XML são resolvidas. Por padrão, eles são resolvidos, mas você pode alterar esse comportamento para aumentar a segurança do sistema de formulários AEM.

**Impedir o processamento de arquivos de dados XML que contêm referências a entidades externas**

1. No console de administração, clique em Serviços > saída.
1. Desmarque a caixa de seleção Resolver entidades externas .
1. Clique em Salvar.
