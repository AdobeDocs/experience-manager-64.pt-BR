---
title: Atualização para o AEM 6.4 Communities
seo-title: Upgrading to AEM 6.4 Communities
description: Como atualizar de uma versão anterior para AEM Comunidades 6.4
seo-description: How to upgrade from an earlier version to AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: 0f82e82cf6e09a2734893a98d67ed1a84b1fec5e
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---

# Atualização para o AEM 6.4 Communities {#upgrading-to-aem-communities}

Dependendo da topologia e dos recursos de cada site, as seguintes ações podem ser necessárias ao atualizar para o AEM Communities 6.4 ou instalar o pacote de recursos mais recente.

Esta seção é específica para Comunidades e complementa as informações fornecidas em [Atualização para AEM 6.4](../../help/sites-deploying/upgrade.md) (plataforma).

## Atualização do AEM 6.1 ou posterior {#upgrading-from-aem-or-later}

### Reindexar Solr {#reindex-solr}

Ao instalar um novo pacote de recursos das Comunidades em uma implantação configurada com MSRP, será necessário:

1. Instale o [pacote de recursos mais recente](deploy-communities.md#latestfeaturepack)
2. Instale os [arquivos de configuração Solr mais recentes](msrp.md#upgrading)
3. Reindexar MSRP

   consulte a seção [Ferramenta MSRP Reindex](msrp.md#msrp-reindex-tool)

### Ativação 2.0 {#enablement}

A partir do AEM 6.3, os recursos de ativação não armazenarão mais informações de relatórios no MySQL. A dependência MySQL está lá apenas para rastrear conteúdo SCORM.

Entre em contato com o [atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) para obter assistência na migração de conteúdo do Enablement 1.0.

## Atualização do AEM 6.0 {#upgrading-from-aem}

Se o UGC preexistente precisar ser retido, o meio para fazer isso dependerá se a implantação armazenou o UGC [no local](#on-premise-storage) ou na [nuvem de Adobe](#adobe-cloud-storage).

### Armazenamento Adobe Cloud {#adobe-cloud-storage}

Se o site atualizado foi configurado para usar o armazenamento na nuvem do Adobe, ele pode aparecer (incorretamente) como se todo o UGC tivesse sido perdido, pois os métodos do SRP não conseguirão localizar o UGC pré-existente no local antigo.

Portanto, há a capacidade de instruir o ASRP a usar `AEM 6.0 compatability-mode` para acessar o UGC.

Para todas as instâncias de autor e publicação do AEM 6.3:

1. Faça logon com privilégios de administrador e configure [ASRP](asrp.md).
1. Siga estas etapas para tornar o UGC existente visível:

   i. Navegue até o console da Web. O URL padrão é
   `https://localhost:4502/system/console/configMgr`.

   ii. Localize a configuração **[!UICONTROL AEM Communities Utilities]** e selecione para expandir o painel de configuração.

   iii. Desmarque **[!UICONTROL Cloud Storage]** e clique em **[!UICONTROL Salvar]**.

![chlimage_1-126](assets/chlimage_1-126.png)

### Armazenamento local {#on-premise-storage}

Se o site atualizado não tiver usado o armazenamento em nuvem, qualquer UGC pré-existente deverá ser convertido para estar em conformidade com a nova estrutura introduzida no AEM 6.1 Communities em suporte da loja comum.

Para essa finalidade, uma ferramenta de migração de código aberto está disponível no GitHub:\
[Ferramenta de migração UGC da AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### APIs Java {#java-apis}

Ao atualizar do AEM 6.0 para AEM Comunidades sociais 6.3, esteja ciente de que muitas APIs foram reorganizadas em pacotes diferentes. A maioria deve ser facilmente resolvida ao usar um IDE para personalização dos recursos das Comunidades.

Para obter detalhes sobre o pacote SocialUtils obsoleto, visite [SocialUtils Refactoring](socialutils.md).

Consulte também [Usando Maven para Comunidades](maven.md).

### Nenhum modelo de componente JSP {#no-jsp-component-templates}

A [estrutura do componente social](scf.md) (SCF) usa a linguagem de modelo [HandlebarsJS](https://handlebarsjs.com/) (HBS) no lugar de Java Server Pages (JSP) usada antes do AEM 6.0.

No AEM 6.0, os componentes do JSP permaneceram junto com os novos componentes da estrutura do HBS no mesmo local, com os componentes do HBS normalmente localizados em subpastas chamadas &quot;hbs&quot;.

A partir AEM 6.1, os componentes do JSP foram completamente removidos. Para Comunidades, é recomendável substituir todo o uso de componentes JSP por componentes SCF.

## Ferramenta de migração UGC da AEM Communities {#aem-communities-ugc-migration-tool}

A [Ferramenta de Migração UGC do AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) é uma ferramenta de migração de código aberto, disponível no GitHub, que pode ser personalizada para exportar o UGC de versões anteriores de comunidades sociais AEM e importar para o AEM Communities 6.1 ou posterior.

Além de mover o UGC de versões anteriores, também é possível usar a ferramenta para mover o UGC de um [SRP](working-with-srp.md) para outro, como do MSRP para o DSRP.

## Atualização do AEM 5.6.1 ou anterior {#upgrading-from-aem-or-earlier}

Conceitualmente, há três gerações de componentes de comunidades:

**1**. Aproximadamente o CQ 5.4 até o AEM 5.6.0 - esses são os  **** componentes de colaboração que armazenaram o UGC no repositório local usando a replicação como um meio de sincronizar o UGC entre plataformas. Outras diferenças envolvem a implementação usando o Java Server Pages (JSP), bem como o recurso de blog que consiste na criação apenas no ambiente do autor.

**Classe 2**: do AEM 5.6.1 até o AEM 6.1 - é uma combinação de componentes  **** colaterais  **** sociais. O AEM 6.0 introduziu o novo [social component framework](scf.md) (SCF) e o AEM 6.2 introduziu um [loja UGC comum](working-with-srp.md), onde o UGC é acessado usando um [provedor de recursos de armazenamento](srp.md) (SRP).

**Gen 3**: a partir do AEM 6.2, há apenas componentes  **** sociais, implementados no SCF como componentes do Handlebars (HBS) que exigem uma escolha de SRP para UGC.
