---
title: Limpeza de dados do processo
seo-title: Purging process data
description: Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho AEM formulários e no uso de espaço em disco desnecessário. Veja como você pode limpar os dados do processo.
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 3%

---

# Limpeza de dados do processo {#purging-process-data}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho AEM formulários e no uso de espaço em disco desnecessário. É uma boa prática limpar dados do processo quando os registros não forem mais necessários. Os formulários AEM fornecem vários meios de limpar os dados do processo:

* Você pode usar o console de administração para executar uma limpeza única de registros obsoletos relacionados a processos de longa duração ou para programar purgas automáticas regulares. (Consulte [Limpar registros do banco de dados do Gerenciador de Jobs](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* Você pode usar a API Java dos formulários AEM e a API do serviço da Web para limpar programaticamente os dados do processo relacionados a processos de longa duração. (Consulte &quot;Limpando dados do processo&quot; em [Programação com formulários AEM](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Use a ferramenta de limpeza de processos para limpar processos com base no nome do processo e outros parâmetros. Para obter detalhes, consulte o arquivo readme da ferramenta de limpeza de processos, localizado em *[raiz aem_forms]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.
