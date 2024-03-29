---
title: Avaliação da complexidade da atualização com o Detector de padrões
seo-title: Assessing the Upgrade Complexity with the Pattern Detector
description: Saiba como usar o Detector de padrões para avaliar a complexidade de sua atualização.
seo-description: Learn how to use the Pattern Detector to assess the complexity of your upgrade.
uuid: 4fcfdb16-3183-442a-aa5b-5f9c4fb7e091
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 8cdcfd3a-7003-4cce-97f4-da7a1a887d1b
feature: Upgrading
exl-id: 375e202c-21d4-41f1-a2d5-592ac95c8f25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 4%

---

# Avaliação da complexidade da atualização com o Detector de padrões{#assessing-the-upgrade-complexity-with-the-pattern-detector}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Esse recurso permite verificar instâncias de AEM existentes para sua capacidade de atualização, detectando padrões em uso que:

1. Violar certas regras e são feitas em áreas que serão afetadas ou substituídas pela atualização
1. Use um recurso AEM 6.x ou uma API que não seja compatível com versões anteriores do AEM 6.4 e possa ser interrompida após a atualização.

Tal poderia servir de avaliação do esforço de desenvolvimento que está envolvido na modernização para o AEM 6.4.

## Como configurar {#how-to-set-up}

O Detector de padrões é lançado separadamente como um [um pacote](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/pd-all-aem65)  trabalhar em qualquer versão de AEM de origem de 6.1 para 6.5, direcionando AEM atualização 6.5. Ele pode ser instalado usando o [Gerenciador de pacotes](https://helpx.adobe.com/br/experience-manager/6-5/sites/administering/using/package-manager.html).

## Como usar {#how-to-use}

>[!NOTE]
>
>O Detector de padrões pode ser executado em qualquer ambiente, incluindo instâncias de desenvolvimento local. No entanto, para:
>
>* aumentar a taxa de detecção
>* evitar qualquer lentidão em instâncias críticas para os negócios\
   >ao mesmo tempo, é recomendável executá-lo **em ambientes de preparo** que estejam o mais próximo possível dos de produção nas áreas de aplicativos, conteúdo e configurações do usuário.


Você pode usar vários métodos para verificar a saída do Detector de padrões:

* **Através do console Felix Inventory:**

1. Vá para o Console da Web AEM navegando até: https://<i></i>serveraddress:serverport/system/console/configMgr
1. Selecionar **Status - Detector de padrões** conforme mostrado na imagem abaixo:

   ![captura de tela-2018-2-5detector de padrões](assets/screenshot-2018-2-5pattern-detector.png)

* **Por meio de um texto reativo com base em uma interface JSON regular**

* **Por meio de uma interface de linhas JSON reativa**, que gera um documento JSON separado em cada linha.

Ambos os métodos estão detalhados abaixo:

## Interface reativa {#reactive-interface}

A interface reativa permite o processamento do relatório de violação assim que uma suspeita é detectada.

A saída está disponível atualmente em 2 URLs:

1. Interface de texto sem formatação
1. Interface JSON

## Manipular a interface de texto simples {#handling-the-plain-text-interface}

As informações na saída são formatadas como uma série de entradas de evento. Há dois canais: um para violações de publicação e outro para a publicação do progresso atual.

Eles podem ser obtidos usando os seguintes comandos:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep SUSPICION
```

A saída terá esta aparência:

```
2018-02-13T14:18:32.071+01:00 [SUSPICION] The pattern=ECU/extraneous.content.usage was found by detector=ContentAccessDetector with id=a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f message="Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid". More info at=https://www.adobe.com/go/aem6_EC
```

O progresso pode ser filtrado usando o `grep` comando:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.txt | tee patterns-report.log | grep PROGRESS
```

O que resulta na seguinte saída:

```
2018-02-13T14:19:26.909+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=45780/16 MB items, found=0 suspicions so far in period=PT5.005S (throughput=34667 items/sec)
2018-02-13T14:19:31.904+01:00 [PROGRESS] emitted=127731/52 MB patterns (from=6.4), analysed=106050/39 MB items, found=0 suspicions so far in period=PT10S (throughput=23378 items/sec)
2018-02-13T14:19:35.685+01:00 [PROGRESS] Finished in period=PT13.782
```

## Manipular a interface JSON {#handling-the-json-interface}

Da mesma forma, o JSON pode ser processado usando o [ferramenta jq](https://stedolan.github.io/jq/) assim que for publicado.

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == true)'
```

Com a saída:

```
{
  "timestamp": "2018-02-13T14:20:18.894+01:00",
  "suspicion": true,
  "pattern": {
    "code": "ECU",
    "type": "extraneous.content.usage",
    "detective": "ContentAccessDetector",
    "moreInfo": "https://www.adobe.com/go/aem6_ECU"
  },
  "item": {
    "id": "a07fd94318f12312c165e06d890cbd3c2c8b8dad0c030663db8b4c800dd7c33f",
    "message": "Cross-boundary overlay of internal marked path /libs/granite/operations/components/commons/commons.jsp/jcr:content referenced at /apps/granite/operations/components/commons/commons.jsp/jcr:content with properties redefined: jcr:lastModifiedBy, jcr:mimeType, jcr:data, jcr:lastModified, jcr:uuid"
  }
}
```

O progresso é relatado a cada 5 segundos e pode ser obtido excluindo outras mensagens além daquelas marcadas como suspeitas:

```shell
curl -Nsu 'admin:admin' http://localhost:4502/system/console/status-pattern-detector.json | tee patterns-report.json | jq --unbuffered -C 'select(.suspicion == false)'
```

Com a saída:

```
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:17.279+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 57209,
    "itemsAnalysedSize": "26 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT5.003S",
    "elapsedTimeMilliseconds": 5003,
    "itemsPerSecond": 36965
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:22.276+01:00",
  "type": "PROGRESS",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 113194,
    "itemsAnalysedSize": "46 MB",
    "suspicionsFound": 0
  },
  "progress": {
    "elapsedTime": "PT10S",
    "elapsedTimeMilliseconds": 10000,
    "itemsPerSecond": 24092
  }
}
{
  "suspicion": false,
  "timestamp": "2018-02-13T14:21:25.762+01:00",
  "type": "FINISHED",
  "database": {
    "patternsEmitted": 127731,
    "patternsEmittedSize": "52 MB",
    "databasesEmitted": [
      "6.4"
    ]
  },
  "state": {
    "itemsAnalysed": 140744,
    "itemsAnalysedSize": "63 MB",
    "suspicionsFound": 1
  },
  "progress": {
    "elapsedTime": "PT13.486S",
    "elapsedTimeMilliseconds": 13486,
    "itemsPerSecond": 19907
  }
}
{
  "suspicion": false,
  "type": "SUMMARY",
  "suspicionsFound": 1,
  "totalTime": "PT13.487S"
}
```

>[!NOTE]
>
>A abordagem recomendada é salvar toda a saída do curl no arquivo e processá-la por meio de `jq` ou `grep` para filtrar o tipo de informação.

## Escopo de detecção {#scope}

Atualmente, o Detector de padrões permite verificar:

* Incompatibilidade de exportações e importações de pacotes OSGi
* Tipos de recursos Sling e supertipos (com sobreposições de conteúdo de caminho de pesquisa)
* definições de índices Oak (compatibilidade)
* Pacotes VLT (utilização excessiva)
* rep:Compatibilidade de nós do usuário (no contexto da configuração OAuth)
