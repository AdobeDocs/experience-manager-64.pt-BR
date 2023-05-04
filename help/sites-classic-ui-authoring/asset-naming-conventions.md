---
title: Convenções de nomenclatura para testes de ativos
seo-title: Naming conventions for assets
description: Os nós no repositório estão sujeitos às convenções de nomenclatura do Java Content Repository. No entanto, o Adobe Experience Manager impõe mais convenções para o nome dos nós de ativos.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 6%

---

# Convenções de nomenclatura para testes de ativos{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os nós no repositório estão sujeitos às convenções de nomenclatura da variável [Repositório de conteúdo Java](/help/sites-developing/the-basics.md#java-content-repository). No entanto, o Adobe Experience Manager impõe mais convenções para o nome dos nós de ativos.

## IU Clássica {#classic-ui}

A interface clássica impõe restrições mais severas:

* Valida o nome do ativo quando um nome de nó explícito é:

   * um título de ativo é fornecido para conversão no nome do nó
   * é fornecido um nome de nó explícito

* Caracteres válidos (somente esses caracteres são válidos quando um ativo é criado na interface clássica):

   * &#39;a&#39; a &#39;z&#39;
   * &#39;A&#39; a &#39;Z&#39;
   * &#39;0&#39; a &#39;9&#39;
   * _ (sublinhado)
   * `-` (traço/menos)
