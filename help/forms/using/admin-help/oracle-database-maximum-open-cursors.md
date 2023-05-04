---
title: Limite máximo de cursores abertos do banco de dados do Oracle
seo-title: Oracle database maximum open cursors threshold
description: Saiba mais sobre como configurar um valor máximo para cursores abertos no Oracle.
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 6%

---

# Limite máximo de cursores abertos do banco de dados do Oracle {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para configurar um valor máximo para cursores abertos no Oracle, talvez seja necessário ajustar esse valor para um número apropriado para seu aplicativo. É evidente que, sob uma carga moderada, o cursor médio aberto foi de 2700. É recomendável começar com um limite máximo de 3000. Para obter mais informações, acesse [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
