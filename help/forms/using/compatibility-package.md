---
title: Pacote de compatibilidade
seo-title: Pacote de compatibilidade
description: 'A instalação do pacote Compatibilidade no AEM Forms 6.4 permite que você use os ativos de Gerenciamento de correspondência do AEM Forms 6.3 e as páginas e modelos de formulários adaptáveis obsoletos '
seo-description: A instalação do pacote Compatibilidade no AEM Forms 6.4 permite que você use os ativos de Gerenciamento de correspondência do AEM Forms 6.3 e as páginas e modelos de formulários adaptáveis obsoletos
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---


# Instalar pacote de compatibilidade {#compatibility-package}

A instalação do pacote Compatibilidade no AEM Forms 6.4 permite que você use os ativos de Gerenciamento de correspondência do AEM Forms 6.3 e as páginas e modelos de formulários adaptáveis obsoletos

## Visão geral {#overview}

A comunicação interativa é a abordagem padrão e recomendada para criar comunicações com o cliente no AEM Forms 6.4. Para continuar usando as letras AEM 6.3 Forms e AEM 6.2 Forms, é necessário instalar o pacote [de compatibilidade do](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)AEMFD.

O pacote Compatibilidade do AEMFD permite que você use os seguintes ativos do AEM Forms 6.3 e 6.2 no AEM Forms 6.4:

* Fragmentos de documento criados no AEM Forms 6.3 e 6.2
* Cartas
* Dicionários de dados
* Formulários adaptáveis modelos e páginas obsoletos

Para obter mais informações, consulte [Ativos compatíveis com o AEM Forms 6.4 instalando o pacote](/help/forms/using/compatibility-package.md#assetsmadecompatible)Compatibilidade.

## Adicione suporte para ativos AEM Forms 6.3 e 6.2 no AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Após executar uma atualização, faça o seguinte para instalar o pacote de compatibilidade do AEMFD e tornar seus ativos compatíveis com o 6.4:

Verifique se você tem [AEM pacote](/help/sites-deploying/backward-compatibility.md) de compatibilidade pré-instalado.

1. Instale o pacote [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)compatibilidade.

   Para obter mais informações sobre como carregar e instalar o pacote, consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md).

1. Depois que os registros estiverem estabilizados, reinicie o servidor.
1. Use o utilitário de migração para tornar seus ativos compatíveis com a versão 6.4.

   Para obter mais informações, consulte Utilitário [de](/help/forms/using/migration-utility.md)migração.

## Ativos compatíveis com o AEM Forms 6.4 ao instalar o pacote de compatibilidade {#assetsmadecompatible}

Ao instalar o pacote de compatibilidade, você pode tornar os seguintes ativos e modelos compatíveis com o AEM Forms 6.4:

* Ativos do AEM 6.3 e anteriores do Correspondent Management

   * [Cartas](/help/forms/using/create-letter.md)
   * [Dicionários de dados](/help/forms/using/data-dictionary.md)
   * Fragmentos do documento

* Modelos de formulário adaptável obsoletos

   * /libs/fd/af/models/blankTemplate2
   * /libs/fd/af/models/simpleEnrollmentTemplate
   * /libs/fd/af/models/simpleEnrollmentTemplate2
   * /libs/fd/af/models/surveyTemplate
   * /libs/fd/af/models/surveyTemplate2
   * /libs/fd/af/models/tabbedEnrollmentTemplate
   * /libs/fd/af/models/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/models/advancedEnrollmentTemplate
   * /libs/fd/afaddon/models/advancedEnrollmentTemplate2

* Páginas obsoletas para formulários adaptativos:

   * /libs/fd/af/components/page/pesquisa
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment

