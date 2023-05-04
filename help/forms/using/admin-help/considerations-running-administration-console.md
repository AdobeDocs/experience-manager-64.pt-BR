---
title: Considerações ao executar o AdministrationConsole
seo-title: Considerations when running AdministrationConsole
description: Este documento lista alguns pontos a serem considerados ao executar o Console de Administração.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Considerações ao executar o Console de administração {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Essas são algumas coisas a serem consideradas ao executar o Console de administração:

* Se você acessar o console de administração usando o URL `https://*[hostname]*:*[port]*/adminui`, o nome de host especificado não pode conter caracteres sublinhados. Caso contrário, os links para algumas áreas do console de administração podem não funcionar corretamente.
* Se você executar o console de administração no Windows Explorer em um SO japonês, poderá enfrentar estes problemas:

   * Clicar em um link o retorna à página de logon em vez do link esperado.
   * Clicar em um link exibe um erro de permissão.

   A prática recomendada é executar o console de administração a partir de outro navegador, como o Mozilla Firefox, para garantir que nenhum link falhe.

* Não use caracteres de barra invertida () ao realizar pesquisas no console de administração.
