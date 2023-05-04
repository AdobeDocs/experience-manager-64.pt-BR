---
title: Verificações de consistência e passagem
seo-title: Consistency and Traversal Checks
description: Saiba como executar verificações de consistência e travessia.
seo-description: Learn how to perform consistency and traversal checks.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Configuring
exl-id: 67dfa0f7-24ac-41ae-83c9-3bb1a8656502
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Verificações de consistência e passagem{#consistency-and-traversal-checks}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao atualizar, pode haver problemas devido a inconsistências no espaço de trabalho. Você pode executar uma atualização de teste para ver se isso será um problema ou executar as verificações de consistência como ação preventiva.

Se você executar uma atualização de teste que falhar devido a inconsistências do espaço de trabalho, verá entradas semelhantes às seguintes em crx-quickstart/logs/crx/error.log:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Executar uma verificação de consistência {#perform-a-consistency-check}

Para executar uma verificação de consistência, navegue até a página de administração do JMX Mbean** com.adobe.granite (Repositório)**. Na tela principal do AEM, acesse:

**Ferramentas > Console da Web > Principal (na barra de menu) > JMX > com.adobe.granite (Repositório)**

Em uma instalação padrão, ela é encontrada aqui:  **[|Mostrar-me|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

No **Operações** na seção da página você encontrará dois métodos: **`traversalCheck`** e **`consistencyCheck`**. Para executar uma verificação, clique na operação e insira os parâmetros desejados.

![chlimage_1-117](assets/chlimage_1-117.png)
