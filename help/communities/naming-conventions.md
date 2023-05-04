---
title: Convenções de nomenclatura
seo-title: Naming Conventions
description: Hifens no nome do pacote Java
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Convenções de nomenclatura {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Hifens no nome do pacote Java {#hyphens-in-java-package-name}

Ao criar um local para uma classe Java, esteja ciente de que o nome do pacote deve corresponder ao do local da pasta do repositório com quaisquer hifens no caminho escapado corretamente.

Embora o uso de hifens nos nomes dos itens do repositório seja uma prática recomendada AEM desenvolvimento, os hifens são ilegais nos nomes dos pacotes Java.

A plataforma CRX subjacente deve ser capaz de distinguir entre um sublinhado real &quot;_&#39; e um hífen &#39;-&#39;. Assim, no JCR, o hífen deve ser substituído pelo seu valor unicode (u002d) e escapado com um sublinhado &#39;_&quot;.

Por exemplo, se o caminho do repositório for **/apps/my-example/component/info/Info.java**, o nome do pacote deve ser `java package apps.my_002dexample.component.info;`

Observe que um sublinhado deve ser evitado de forma semelhante, de modo que `_` become `_005f`.
