---
title: Criando Configuração de Exportação de Artigo
seo-title: Criando Configuração de Exportação de Artigo
description: Siga esta página para saber mais sobre como exportar conteúdo do Adobe Experience Manager (AEM) para upload para o AEM Mobile.
seo-description: Siga esta página para saber mais sobre como exportar conteúdo do Adobe Experience Manager (AEM) para upload para o AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
translation-type: tm+mt
source-git-commit: 622e613d556acda7cd98d4b3d20a20133756fd92
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Criando Configuração de Exportação de Artigo{#creating-article-export-configuration}

>[!NOTE]
>
>A Adobe recomenda o uso do Editor SPA para projetos que exigem renderização do cliente baseada em estrutura de aplicativo de página única (por exemplo, Reagir). [Saiba mais](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Pré-requisitos**:
>
>Antes de aprender sobre como criar e modificar recursos compartilhados, consulte [Sincronização](/help/mobile/mobile-ondemand-contentsync.md) de conteúdo para entender os conceitos básicos.

Os usuários do AEM Mobile usam o Content Sync para exportar conteúdo ao vivo para conteúdo estático para uso em aplicativos móveis e essa exportação ocorre quando o conteúdo é carregado nos Mobile On-Demand Services da AEM Mobile.

A propriedade ***dps-exportTemplate*** mencionada na tabela acima define o caminho para as configurações de exportação do aplicativo. Defina essa propriedade para criar e modificar recursos compartilhados.

Os recursos a seguir descrevem como exportar conteúdo do Adobe Experience Manager (AEM) para upload para o AEM Mobile.

Os artigos têm conteúdo que precisa ser exportado e carregado. Alguns desse conteúdo podem ser compartilhados entre Artigos.

Use o [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) para coletar o conteúdo e criar um pacote de Recursos ****** compartilhados.

A configuração ContentSync encontrada em **&lt;dps-exportTemplate>/dps-article>** deve ser configurada para exportar todo o conteúdo que um artigo requer para renderização estática de propriedade no dispositivo.

>[!CAUTION]
>
>Você pode executar as etapas abaixo para visualização de recursos compartilhados de amostra, somente se você tiver:
>
>* instalou o conteúdo da amostra
>* executando instância AEM
>* nenhum contexto personalizado configurado ou uma porta diferente

>



Para visualização de um recurso compartilhado de amostra, consulte as etapas abaixo:

1. Abra o CRXDE Lite no servidor AEM.
1. Navegue até esse caminho [/etc/contentsync/models/dps-we-ilimitado-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article)para visualização dos recursos compartilhados de amostra.

   Você pode visualização todas as propriedades necessárias para criar seus recursos compartilhados, conforme mostrado na figura abaixo:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Os artigos devem ser carregados ou exportados para o AEM Mobile On-demand Services quando o conteúdo dos artigos for alterado.

