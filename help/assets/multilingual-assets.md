---
title: Ativos multilíngues
description: Saiba como automatizar fluxos de trabalho para tradução de ativos, incluindo binários, metadados e tags em vários idiomas.
contentOwner: AG
feature: Asset Management
role: Admin
exl-id: 8e065137-3599-48af-a040-6923b7b5e1d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 6%

---

# Ativos multilíngues {#multilingual-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os ativos Adobe Experience Manager (AEM) permitem automatizar os fluxos de trabalho de tradução em ativos (incluindo binários, metadados e tags) para gerar ativos em outros idiomas para usar em projetos multilíngues.

Para automatizar workflows de tradução, você integra provedores de serviços de tradução a [!DNL Experience Manager] e criar projetos para traduzir ativos em vários idiomas. [!DNL Experience Manager]O permite workflows de tradução humana e de máquina.

Tradução humana: Os ativos traduzidos são retornados e importados para o AEM. Quando seu provedor de tradução é integrado ao AEM, os ativos são automaticamente enviados entre [!DNL Experience Manager] e o provedor de tradução.

Tradução da máquina: O serviço de tradução automática traduz imediatamente os metadados e as tags para os ativos.

A tradução de ativos inclui o seguinte:

1. [Conexão [!DNL Experience Manager] com o provedor de serviços de tradução](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Criar configurações da estrutura de integração de tradução](/help/sites-administering/tc-tic.md)
1. [Preparação de ativos para tradução](preparing-assets-for-translation.md)
1. [Aplicação de serviços da nuvem de tradução a pastas](transition-cloud-services.md)
1. [Criar projetos de tradução](translation-projects.md)

Se o seu provedor de serviços de tradução não fornecer um conector para integrar com o AEM, use um [processo alternativo](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Consulte também [Criação de projetos de tradução para fragmentos de conteúdo](creating-translation-projects-for-content-fragments.md).
