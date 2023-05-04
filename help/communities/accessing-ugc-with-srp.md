---
title: Acesso ao UGC com SRP
seo-title: Accessing UGC with SRP
description: Quando um site é configurado para usar o ASRP ou o MSRP, o UGC real não é armazenado AEM armazenamento de nós (JCR)
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---

# Acesso ao UGC com SRP {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sobre SRP {#about-srp}

Todos os componentes e recursos do AEM Communities são criados na [quadro de componentes sociais (SCF)](scf.md), que chama a API SocialResourceProvider para acessar todo o conteúdo gerado pelo usuário (UGC).

Antes de criar um site da comunidade, a variável [provedor de recursos de armazenamento (SRP)](working-with-srp.md) deve ser configurado para selecionar uma implementação consistente com o subjacente [topologia](topologies.md). As implementações de SRP são baseadas em três opções de armazenamento:

1. [ASRP](asrp.md) - Adobe on Demand Storage
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Sobre o armazenamento UGC {#about-ugc-storage}

O que é importante saber sobre o armazenamento do UGC é que, quando um site é configurado para usar o ASRP ou o MSRP, o UGC real não é armazenado no AEM [armazenamento de nó](../../help/sites-deploying/data-store-config.md) (JCR).

Embora possa haver nós no JCR que somem o UGC para fornecer metadados úteis, esses nós não devem ser confundidos com o UGC real.

Consulte [Visão geral do provedor de recursos de armazenamento.](srp.md)

## Prática recomendada {#best-practice}

Ao desenvolver componentes personalizados, os desenvolvedores devem ter cuidado para codificar independentemente da topologia escolhida atualmente, mantendo assim a flexibilidade para migrar para uma nova topologia no futuro.

### Suponha que o JCR não esteja disponível {#assume-jcr-not-available}

Os métodos específicos do JCR devem ser evitados.

Métodos a utilizar:

* API Sling (Recurso Sling)
   * Não suponha que haja nós JCR

* Eventos OSGi
   * Não suponha que haja eventos JCR

* [Utilitários de recursos sociais](socialutils.md#socialresourceutilities-package)
* [Utilitários SCF](socialutils.md#scfutilities-package)

Métodos para evitar:

* API de nó
* Eventos JCR
* Iniciadores de fluxo de trabalho (que usam eventos JCR)

### Usar Coleções de Pesquisa {#use-search-collections}

Diferentes SRPs podem ter diferentes linguagens de consulta nativas. É recomendável usar métodos do [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) pacote para invocar o idioma de consulta apropriado.

Para obter mais informações, consulte [Fundamentos da pesquisa](search-implementation.md).

## Recursos {#resources}

* [Armazenamento de conteúdo da comunidade](working-with-srp.md) - discute as opções de SRP disponíveis para uma loja comum UGC
* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Fundamentos da pesquisa](search-implementation.md) - informações essenciais para a pesquisa de UGC
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais
