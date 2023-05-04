---
title: armadilhas de código
seo-title: Code pitfalls
description: Problemas comuns de codificação a serem evitados ao desenvolver para AEM
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 6%

---

# armadilhas de código{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Evite vínculos Sling no código Java {#avoid-sling-bindings-in-java-code}

Os Sling Bindings são uma maneira inadequada de obter acesso a um serviço em 90% dos casos. Em vez disso, você deve usar *@Reference* ou *@Inject* anotações.

## Evite Thread.interrupt no código Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* O é perigoso porque pode fechar arquivos, incluindo arquivos Lucene e arquivos de cache persistentes, quando chamados no momento errado.

## Evite misturar a sincronização Java com ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Isso pode levar a uma condição de corrida na qual o código eventualmente ficará bloqueado.
