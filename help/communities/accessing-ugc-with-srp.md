---
title: Acessar UGC com SRP
seo-title: Acessar UGC com SRP
description: Quando um site é configurado para usar ASRP ou MSRP, o UGC real não é armazenado AEM armazenamento de nós (JCR)
seo-description: Quando um site é configurado para usar ASRP ou MSRP, o UGC real não é armazenado AEM armazenamento de nós (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# Acessar UGC com SRP {#accessing-ugc-with-srp}

## Sobre SRP {#about-srp}

Todos os componentes e recursos do AEM Communities são criados na [estrutura de componentes sociais (SCF)](scf.md), que chama a API SocialResourceProvider para acessar todo o conteúdo gerado pelo usuário (UGC).

Antes de um site da comunidade ser criado, o [provedor de recursos do armazenamento (SRP)](working-with-srp.md) deve ser configurado para selecionar uma implementação consistente com a [topologia](topologies.md) subjacente. As implementações SRP são baseadas em três opções de armazenamento:

1. [ASRP](asrp.md)  - armazenamento por demanda Adobe
2. [MSRP](msrp.md)  - MongoDB
3. [JSRP](jsrp.md)  - JCR

## Sobre o Armazenamento UGC {#about-ugc-storage}

O que é importante saber sobre o armazenamento do UGC é que, quando um site é configurado para usar o ASRP ou o MSRP, o UGC real não é armazenado AEM [armazenamento de nó](../../help/sites-deploying/data-store-config.md) (JCR).

Embora possa haver nós no JCR que sombream o UGC para fornecer metadados úteis, esses nós não devem ser confundidos com o UGC real.

Consulte [Visão Geral do Fornecedor de Recursos de Armazenamento.](srp.md)

## Prática recomendada {#best-practice}

Ao desenvolver componentes personalizados, os desenvolvedores devem tomar cuidado para codificar independentemente da topologia atual escolhida, mantendo assim a flexibilidade para migrar para uma nova topologia no futuro.

### Considere que o JCR não está disponível {#assume-jcr-not-available}

Devem ser evitados métodos específicos para o JCR.

Métodos para usar:

* Sling API (Sling Resource)
   * Não suponha que haja nós JCR

* Eventos OSGi
   * Não suponha que haja eventos JCR

* [Utilitários de recursos sociais](socialutils.md#socialresourceutilities-package)
* [Utilitários SCF](socialutils.md#scfutilities-package)

Métodos para evitar:

* API de nó
* Eventos JCR
* Iniciadores de fluxo de trabalho (que usam eventos JCR)

### Usar coleções de pesquisa {#use-search-collections}

Diferentes SRPs podem ter diferentes idiomas de query nativos. É recomendável usar métodos do pacote [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) para chamar o idioma do query apropriado.

Para obter mais informações, consulte [Search Essentials](search-implementation.md).

## Recursos {#resources}

* [Armazenamento](working-with-srp.md)  de conteúdo da comunidade - discute as opções de SRP disponíveis para uma loja comum UGC
* [Visão geral](srp.md)  do provedor de recursos do armazenamento - introdução e visão geral do uso do repositório
* [SRP e UGC Essentials](srp-and-ugc.md)  - métodos e exemplos de utilitários SRP
* [Search Essentials](search-implementation.md)  - informações essenciais para a pesquisa no UGC
* [Refatoração](socialutils.md)  do SocialUtils - mapeamento de métodos de utilitário obsoletos para os métodos atuais do utilitário SRP
