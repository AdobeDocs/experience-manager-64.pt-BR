---
title: Refatoração do SocialUtils
seo-title: SocialUtils Refactoring
description: O pacote com.adobe.cq.social.ugcbase.SocialUtils foi descontinuado no AEM 6.1
seo-description: The package com.adobe.cq.social.ugcbase.SocialUtils was deprecated in AEM 6.1
uuid: 54a0d98e-5ead-4c12-850f-8252ea9b3263
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4ade0d6b-041e-4a2f-98f8-3b8fcae0fb29
exl-id: ba23188b-a72a-4349-b3e5-0fb50fd6312f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---

# Refatoração do SocialUtils {#socialutils-refactoring}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Pacote SocialUtils obsoleto {#socialutils-package-deprecated}

O pacote **com.adobe.cq.social.ugcbase.SocialUtils** foi descontinuado no AEM 6.1.

As tabelas a seguir listam os métodos a serem usados no lugar dos métodos do SocialUtils .

## Pacote SocialResourceUtilities  {#socialresourceutilities-package}

| Métodos em com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities |
|---|
| Boolean checkPermission(Resolvedor de ResourceResolver, Caminho da string, ação da string) |  |
| SocialResourceProvider getSocialResourceProvider(recurso de recurso) |  |
| SocialResourceConfiguration getStorageConfig(recurso de recurso) |  |
| Recurso getUGCResource(Resource userResource) |  |
| Recurso getUGCResource(Resource userResource, ResourceResolverFactory rf) | novo |
| Recurso getUGCResource(Resource userResource, ResourceResolverFactory rf, String resourceTypeHint) | novo |
| Recurso getUGCResource(Resource userResource, String resourceTypeHint) |  |
| booleano hasModeratePermissions(Resource resource) |  |
| String resourceToACLPath(Resource resource) |  |
| String resourceToUGCStoragePath(recurso de recurso) | substitui String resourceToUGCPath(Resource resource) |
| Sequência UGCToResourcePath(Resource resource) |  |
| Sequência UGCToResourcePath(String ugcPath) | assinatura do método alterada |
| Sequência UGCToResourcePath(String ugcPath, ResourceResolver resolver) | novo |

| Métodos em `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider(recurso de recurso) | substitui SocialResourceProvider getConfizedProvider(recurso de recurso) |

## Pacote SCFUtilities {#scfutilities-package}

| Métodos em `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| Sequência getAvatar(UserProperties userProperties) |
| Sequência getAvatar(UserProperties userProperties, tamanho int) |
| Sequência getAvatar(UserProperties userProperties, String fixedDefaultAvatar) |
| Sequência getAvatar(UserProperties userProperties, String fixedDefaultAvatar, SocialUtils.AVATAR_SIZE size) |
| Página getContainsPage (recurso de recurso) |
| Sequência getSocialProfileURL(Nome de usuário da sequência, Resolvedor do recurso, Página) |
| UserProperties getUserProperties(Resolvedor do ResourceResolver, ID do usuário da string) |

## Apenas para uso interno {#for-internal-use-only}

| booleano canAddNode(Session session, String path) |
|---|
| Sequência de caracteres createUniqueNameHint(String message) |
| Sequência createUniqueNameHint(String message, int numRandomChars) |
| Sequência de caracteres generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| Página getPage(Caminho da string, Resolvedor de Recursos) |
| Sequência getPagePath(recurso de recurso) |
| Sequência getPagePath(String path) |
| Sequência getResourceTypeForIncludedResource(Resource component, String defaultResourceType, String designPropertyName) |
| Sequência getResourceTypeFromDesign(Resource resource, String styleProperty, String defaultValue) |
| booleano isResourceOwner(recurso de recurso) |
| String mapUGCPath(Recurso de recurso) |
| String mapUGCPath(String ugcPath, ResourceResolver resolver) |
| booleano mayPost(ResourceResolver resolver, recurso Recurso) |
| Sequência de caracteres prepareUserGeneratedContent(Resolvedor do ResourceResolver, caminho da string) |

## Métodos não estão mais disponíveis {#methods-no-longer-available}

| Nó createNode(ResourceResolver resolver, Caminho da string, String nodeType) |
|---|
| Recurso getResourceAtPath(ResourceResolver resolver, caminho da string) |
| Recurso getResourceAtPath(ResourceResolver resolver, caminho da string, String resourceType) |
| Configuração getStorageCloudServiceConfig (recurso Recurso) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| booleano mayAccessUGC(Resolvedor de ResourceResolver) |
