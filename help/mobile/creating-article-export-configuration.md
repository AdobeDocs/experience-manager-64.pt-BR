---
title: Criação da configuração de exportação de artigo
seo-title: Creating Article Export Configuration
description: Siga esta página para saber mais sobre como exportar conteúdo do Adobe Experience Manager (AEM) para upload para o AEM Mobile.
seo-description: Follow this page to learn about exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
exl-id: d6e8412d-09d4-4cac-a691-71703ebaa374
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 3%

---

# Criação da configuração de exportação de artigo{#creating-article-export-configuration}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Pré-requisitos**:
>
>Antes de saber mais sobre como criar e modificar recursos compartilhados, consulte [Sincronização de conteúdo](/help/mobile/mobile-ondemand-contentsync.md) para compreender os conceitos básicos.

Os usuários do AEM Mobile usam a Sincronização de conteúdo para exportar conteúdo ao vivo para conteúdo estático, para uso em aplicativos móveis, e essa exportação ocorre quando o conteúdo é carregado nos Mobile On-Demand Services da AEM Mobile.

A propriedade ***dps-exportTemplate*** mencionado na tabela acima, define o caminho para as configurações de exportação do aplicativo. Defina essa propriedade para criar e modificar recursos compartilhados.

Os recursos a seguir descrevem como exportar conteúdo do Adobe Experience Manager (AEM) para upload para o AEM Mobile.

Os artigos têm conteúdo que precisa ser exportado e carregado. Parte desse conteúdo pode ser compartilhada entre artigos.

Use [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) para coletar o conteúdo e criar um ***Recursos compartilhados*** pacote.

A configuração do ContentSync foi encontrada em **&lt;dps-exporttemplate>/dps-article>** deve ser configurado para exportar todo o conteúdo que um artigo requer para a renderização estática da propriedade no dispositivo.

>[!CAUTION]
>
>Você pode executar as etapas abaixo para exibir os recursos compartilhados de amostra, somente se tiver:
>
>* instalado o conteúdo da amostra
>* executando AEM instância
>* sem contexto personalizado configurado ou uma porta diferente
>


Para exibir o exemplo de recurso compartilhado, consulte as etapas abaixo:

1. Abra o CRXDE Lite no servidor AEM.
1. Navegue até este caminho [/etc/contentsync/templates/dps-we-ilimitado-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), para exibir a amostra de recursos compartilhados.

   Você pode exibir todas as propriedades necessárias para criar seus recursos compartilhados, conforme mostrado na figura abaixo:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Os artigos devem ser carregados ou exportados para o AEM Mobile On-demand Services quando um conteúdo de artigos for alterado.
