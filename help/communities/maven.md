---
title: Uso do Maven para comunidades
seo-title: Uso do Maven para comunidades
description: jar de API da AEM Communities e jar de API Uber AEM
seo-description: jar de API da AEM Communities e jar de API Uber AEM
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: 5affffac6f953bcf1d436d8492ad6dd2a041b3b4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Usando o Maven para Comunidades {#using-maven-for-communities}

## Visão geral {#overview}

Esta seção da documentação da AEM Communities é complementar a:

* [Construção AEM projetos usando o Apache Maven](../../help/sites-developing/ht-projects-maven.md).

Há apenas um artefato &quot;uber&quot; que substitui artefatos individuais:

* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>A partir AEM 6.4, as APIs das Comunidades não são lançadas explicitamente. Todas as APIs das Comunidades agora estão incluídas no próprio pod Uber.
>
>É recomendável manter-se atualizado com a versão mais recente das Comunidades.
>
>Consulte a seção [Versões mais recentes](deploy-communities.md#latest-releases) para identificar a versão mais recente.

## Exemplo de Dependência Maven {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.4.8.3</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Consulte [AEM repositório Uber jar](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar) para identificar o artefato Uber jar mais recente.

<!--
# Using Maven for Communities {#using-maven-for-communities}

## Overview {#overview}

This section of the AEM Communities documentation is in addition to:

* [How to Build AEM Projects using Apache Maven](../../help/sites-developing/ht-projects-maven.md)

There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Login with adminstrative privileges.
2. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. locate the package *cq-socialcommunities-pkg-1.x.xxx*
4. extract the version from the package name
    * first version for AEM 6.3 is version 1.11.170
    * feature packs will be versions 1.12.xxx
    
>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
-->