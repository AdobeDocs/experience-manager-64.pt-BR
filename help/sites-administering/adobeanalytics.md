---
title: Integração ao Adobe Analytics
seo-title: Integrating with Adobe Analytics
description: Saiba como integrar o AEM com o Adobe Analytics.
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 62%

---

# Integração ao Adobe Analytics{#integrating-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A integração do Adobe Analytics e do AEM permite rastrear a atividade da página da Web:

* Uma configuração do Adobe Analytics permite que o AEM faça autenticação com o Adobe Analytics.
* Uma estrutura identifica os dados enviados para o conjunto de relatórios do Adobe Analytics.

Os dados incluem página e dados do usuário; por exemplo:

* dados que os componentes do AEM coletam
* cliques em links
* informações de uso de vídeo
* o número de visitas à página do Adobe Analytics

As seguintes páginas ajudam a configurar a integração:

* [Conectar ao Adobe Analytics e Criar Frameworks](/help/sites-administering/adobeanalytics-connect.md)
* [Configuração do rastreamento de links para o Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Mapeamento de dados do componente com propriedades do Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Configuração do rastreamento de vídeo para o Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

Também é possível usar a variável [Assistente de opt-in](/help/sites-administering/opt-in.md) para realizar facilmente a integração.

>[!NOTE]
>
>Consulte também o artigo de instruções: [Integração de AEM com o Adobe Target e o Adobe Analytics usando o DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Informações adicionais {#further-information}

Consulte:

* [Estender a integração do Adobe Analytics](/help/sites-developing/extending-analytics.md) para obter informações sobre o desenvolvimento de componentes que coletam dados do usuário e personalização da estrutura do Adobe Analytics.
* O artigo da base de conhecimento, [Integração do Adobe Analytics - solução de problemas](https://helpx.adobe.com/br/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), para obter informações sobre como solucionar problemas de integração com o Adobe Analytics.

>[!NOTE]
>
>Se estiver usando o Adobe Analytics com uma configuração de proxy personalizada, precisará [configurar dois pacotes OSGi](/help/sites-deploying/configuring-osgi.md) (por exemplo, com o console da Web) necessários para as configurações de proxy do **Apache HTTP Client**. Ambos são necessários, pois algumas funcionalidades do AEM usam as APIs 3.x, enquanto outros usam as APIs 4.x. Configurar o:
>
>* **Day Commons HTTP Client 3.1** para configurar a API 3.x;\
   >  por exemplo, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Configuração de proxy de componentes HTTP do Apache** para configurar a API 4.x;
>
>  por exemplo, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
