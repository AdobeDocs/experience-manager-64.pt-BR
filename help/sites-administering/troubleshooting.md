---
title: Trabalhar com logs
seo-title: Working with Logs
description: Saiba como solucionar problemas de AEM trabalhando com logs.
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 6%

---

# Trabalhar com logs{#working-with-logs}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta seção inclui informações detalhadas sobre logs disponíveis para ajudar você a solucionar problemas.

O CRX registra registros detalhados. Depois de descompactar e iniciar o Quickstart, você poderá encontrar logs nos seguintes locais:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Ativando o Nível de Log DEBUG {#activating-the-debug-log-level}

O nível de log padrão é INFO, ou seja, as mensagens DEBUG não são registradas.

Para ativar o nível de log DEBUG, use o explorador CRX para definir a variável

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

propriedade a ser depurada. Não deixe o log no nível de log DEBUG por mais tempo do que o necessário, pois ele gera muitos logs.

Uma linha no arquivo de depuração geralmente começa com DEBUG e, em seguida, fornece o nível de log, a ação do instalador e a mensagem de log. Por exemplo:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Os níveis de log são os seguintes:

| 0 | Erro fatal | A ação falhou e o instalador não pode continuar. |
|---|---|---|
| 1 | Erro | A ação falhou. A instalação continua, mas uma parte do CRX não foi instalada corretamente e não funcionará. |
| 2 | Aviso | A ação foi bem-sucedida, mas encontrou problemas. O CRX pode ou não funcionar corretamente. |
| 3 | Info | A ação foi bem sucedida. |

## Opção detalhada usada para solução de problemas {#verbose-option-used-for-troubleshooting}

Ao iniciar o CRX, é possível adicionar a opção -v (verboso) à linha de comando como em: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Use a opção detalhada para solução de problemas, pois essa opção exibe parte da saída do log de início rápido no console.
