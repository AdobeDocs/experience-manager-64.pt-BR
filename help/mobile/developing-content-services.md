---
title: Content Services
seo-title: Content Services
description: Content Services
seo-description: null
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
exl-id: e900d93e-f7cd-4a0d-a866-7fc6c7882797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 5%

---

# Content Services{#content-services}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>O recurso Serviços de conteúdo é documentado apenas para fins de visualização.
>
>Ele está sujeito a alterações com o lançamento do 6.3 GA Service Pack 1.

O AEM Mobile Content Services é um recurso leve e leve para solicitar conteúdo gerenciado pelo AEM. Isso fornece a todos os desenvolvedores de aplicativos uma maneira de alto desempenho para recuperar conteúdo sem precisar ter profundo conhecimento AEM repositório de conteúdo (JCR) e estrutura da Web (Sling). Ela permite que os aplicativos de solicitação sejam dissociados do repositório de conteúdo.

Os Serviços de conteúdo apresentam várias novas construções de AEM que permitem que um desenvolvedor acesse AEM conteúdo gerenciado sem conhecer a estrutura do repositório desse conteúdo.

Essas construções são necessárias para manter a flexibilidade e permitir a expansão futura fornecendo uma camada de abstração entre o conteúdo gerenciado AEM e os aplicativos móveis que consomem o conteúdo. Isso permite que AEM Content Services funcione como uma camada de abstração entre os requisitos de conteúdo do aplicativo nativo e o repositório de conteúdo AEM.

Os Serviços de conteúdo podem fornecer o conteúdo como ativos, HTML empacotado (HTML/CSS/JS) ou como conteúdo independente de canal.

>[!CAUTION]
>
>**Pré-requisitos:**
>
>Antes de começar a usar os Serviços de conteúdo, ative o sinalizador de Serviços de conteúdo . Para habilitar a criação e o gerenciamento de modelos em seu aplicativo, é necessário habilitar modelos de dados no Navegador de configuração.
>
>Consulte **[Administração dos serviços de conteúdo](/help/mobile/developing-content-services.md)** para obter detalhes.
>
>Consulte a [Documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.

![chlimage_1-143](assets/chlimage_1-143.png)

Depois de definir o sinalizador de Serviços de conteúdo e os modelos de dados ativados no Navegador de configuração, consulte os recursos abaixo para começar a usar os Serviços de conteúdo da AEM Mobile, familiarizar-se com os Conceitos de serviços de conteúdo, como o gerenciamento de modelo, o gerenciamento de entidades seguido pela entrega/renderização de conteúdo para os Serviços de conteúdo da AEM Mobile.

* Modelos no Repositório
* Renderização e entrega
