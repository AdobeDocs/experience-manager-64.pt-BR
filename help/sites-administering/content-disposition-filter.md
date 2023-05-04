---
title: Filtro de Disposição de Conteúdo
seo-title: Content Disposition Filter
description: Saiba como usar o Filtro de disposição de conteúdo para evitar ataques de XSS.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---

# Filtro de Disposição de Conteúdo {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O filtro de disposição de conteúdo é um recurso de segurança contra ataques de XSS em arquivos SVG.

Depois de instalado, o filtro bloqueia o acesso a todos os ativos. Por exemplo, não era possível visualizar um PDF online. Esta seção descreve como configurar o filtro de acordo com suas necessidades.

## Configurar filtro de disposição de conteúdo {#configure-content-disposition-filter}

Você pode visualizar o [Filtro de disposição de conteúdo do Apache Sling no GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

As opções de Filtro de disposição de conteúdo fornecem a seguinte funcionalidade:

* **Caminhos de disposição de conteúdo:** uma lista de caminhos em que o filtro será aplicado seguida de uma lista de tipos MIME a serem excluídos nesse caminho. Esse caminho deve ser um caminho absoluto e pode conter um curinga (`*`) no final, para corresponder cada caminho de recurso ao prefixo de caminho especificado. Por exemplo: `/content/*:image/jpeg,image/svg+xml` aplicará o filtro a cada nó no `/content` exceto imagens jpg e svg

* **Caminhos de recursos excluídos:** uma lista de recursos excluídos, cada caminho de recurso deve ser fornecido como caminho absoluto e totalmente qualificado. Correspondência de prefixos/curingas não são compatíveis.

* **Ativar Para Todos Os Caminhos De Recursos:** esse sinalizador controla se esse filtro deve ser ativado para todos os caminhos, exceto para os caminhos excluídos definidos pelos Caminhos de recursos excluídos. Configurar como &#39;true&#39; leva a ignorar os Caminhos de disposição de conteúdo. Independentemente da configuração, somente os caminhos de recursos são cobertos que contêm uma propriedade chamada `jcr:data` ou
   `jcr:content jcr:data`.
