---
title: Pacote de Compatibilidade
seo-title: Compatibility Package
description: 'A instalação do pacote Compatibilidade no AEM Forms 6.4 permite usar os ativos de Gerenciamento de correspondência do AEM Forms 6.3 e modelos e páginas de formulários adaptáveis obsoletos '
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# Instalar pacote de compatibilidade {#compatibility-package}

A instalação do pacote Compatibilidade no AEM Forms 6.4 permite usar os ativos de Gerenciamento de correspondência do AEM Forms 6.3 e modelos e páginas de formulários adaptáveis obsoletos

## Visão geral {#overview}

A comunicação interativa é a abordagem padrão e recomendada para criar comunicações com clientes no AEM Forms 6.4. Para continuar usando as cartas do AEM 6.3 Forms e do AEM 6.2 Forms, é necessário instalar o [Pacote de compatibilidade do AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

O pacote de compatibilidade do AEMFD permite usar os seguintes ativos do AEM Forms 6.3 e 6.2 no AEM Forms 6.4:

* Fragmentos de documento criados no AEM Forms 6.3 e 6.2
* Cartas
* Dicionários de dados
* Modelos e páginas obsoletas de formulários adaptáveis

Para obter mais informações, consulte [Ativos compatíveis com o AEM Forms 6.4 instalando o pacote Compatibilidade](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Adicionar suporte para os ativos AEM Forms 6.3 e 6.2 no AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Depois de executar uma atualização, faça o seguinte para instalar o pacote de compatibilidade do AEMFD e tornar seus ativos compatíveis com o 6.4:

Certifique-se de ter [AEM pacote de compatibilidade](/help/sites-deploying/backward-compatibility.md) pré-instalado.

1. Instale o [Pacote de Compatibilidade](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

   Para obter mais informações sobre como fazer upload e instalar o pacote, consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md).

1. Depois que os logs forem estabilizados, reinicie o servidor.
1. Use o utilitário de migração para tornar seus ativos compatíveis com a 6.4.

   Para obter mais informações, consulte [utilitário de migração](/help/forms/using/migration-utility.md).

## Ativos compatíveis com o AEM Forms 6.4 ao instalar o pacote Compatibilidade {#assetsmadecompatible}

Ao instalar o pacote de Compatibilidade, você pode tornar os seguintes ativos e modelos compatíveis com o AEM Forms 6.4:

* Ativos de gerenciamento de correspondência da AEM 6.3 e anteriores

   * [Cartas](/help/forms/using/create-letter.md)
   * [Dicionários de dados](/help/forms/using/data-dictionary.md)
   * Fragmentos do documento

* Modelos adaptáveis obsoletos de formulário

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Páginas obsoletas para formulários adaptáveis:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
