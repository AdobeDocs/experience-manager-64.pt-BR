---
title: Filtro de Disposição de Conteúdo
seo-title: Filtro de Disposição de Conteúdo
description: Saiba como usar o Filtro de disposição de conteúdo para evitar ataques de XSS.
seo-description: Saiba como usar o Filtro de disposição de conteúdo para evitar ataques de XSS.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
translation-type: tm+mt
source-git-commit: 8cc85728be93d58e3aaee69c96f59ee98d5484a1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Filtro de Disposição de Conteúdo {#content-disposition-filter}

O filtro de disposição de conteúdo é um recurso de segurança contra ataques de XSS em arquivos SVG.

Depois de instalado, o filtro bloqueia o acesso a todos os ativos. Por exemplo, não era possível visualizar um PDF online. Esta seção descreve como configurar o filtro de acordo com suas necessidades.

## Configurar o filtro de disposição de conteúdo {#configure-content-disposition-filter}

Você pode visualizar o [Filtro de Disposição de Conteúdo do Apache Sling no GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

As opções de Filtro de disposição de conteúdo fornecem a seguinte funcionalidade:

* **Caminhos de disposição de conteúdo:** uma lista de caminhos em que o filtro será aplicado, seguida de uma lista de tipos MIME a serem excluídos nesse caminho. Esse caminho deve ser um caminho absoluto e pode conter um curinga (`*`) no final, para corresponder cada caminho de recurso ao prefixo de caminho especificado. Por exemplo: `/content/*:image/jpeg,image/svg+xml` aplicará o filtro a cada nó em `/content` exceto imagens jpg e svg

* **Caminhos de recursos excluídos:** uma lista de recursos excluídos, cada caminho de recurso deve ser fornecido como caminho absoluto e totalmente qualificado. Correspondência de prefixos/curingas não são compatíveis.

* **Ativar para todos os caminhos de recursos:** esse sinalizador controla se esse filtro deve ser ativado para todos os caminhos, exceto para os caminhos excluídos definidos pelos caminhos de recursos excluídos. Configurar como &#39;true&#39; leva a ignorar os Caminhos de disposição de conteúdo. Independentemente da configuração, somente os caminhos de recursos são cobertos que contêm uma propriedade chamada `jcr:data` ou
   `jcr:content jcr:data`.
