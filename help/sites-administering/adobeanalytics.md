---
title: Integração ao Adobe Analytics
seo-title: Integração ao Adobe Analytics
description: Saiba como integrar AEM com a Adobe Analytics.
seo-description: Saiba como integrar AEM com a Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 21%

---


# Integração ao Adobe Analytics{#integrating-with-adobe-analytics}

Integrar o Adobe Analytics e o AEM permite rastrear a atividade da página da Web:

* Uma configuração do Adobe Analytics permite que o AEM se autentique com o Adobe Analytics.
* Uma estrutura identifica os dados enviados para o conjunto de relatórios da Adobe Analytics.

Os dados incluem dados da página e do utilizador; por exemplo:

* dados que AEM componentes coletam
* cliques em links
* informações de uso do vídeo
* o número de visitas de página do Adobe Analytics

As páginas a seguir ajudam a configurar a integração:

* [Conectando-se ao Adobe Analytics e criando estruturas](/help/sites-administering/adobeanalytics-connect.md)
* [Configuração do rastreamento de links para Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Mapeamento de dados de componente com propriedades do Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Configuração do rastreamento de vídeo para Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

Você também pode usar o assistente [de](/help/sites-administering/opt-in.md) aceitação para executar facilmente a integração.

>[!NOTE]
>
>Consulte também o artigo de instruções: [Integração de AEM com Adobe Target e Adobe Analytics usando o DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Informações adicionais {#further-information}

Consulte:

* [Estendendo a integração](/help/sites-developing/extending-analytics.md) Adobe Analytics para obter informações sobre o desenvolvimento de componentes que coletam dados de usuários e personalizam a estrutura do Adobe Analytics.
* O artigo da base de conhecimento, Integração com o [Adobe Analytics - solução de problemas](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), para obter informações sobre como solucionar problemas da integração com o Adobe Analytics.

>[!NOTE]
>
>Se estiver usando o Adobe Analytics com uma configuração de proxy personalizada, precisará [configurar dois pacotes OSGi](/help/sites-deploying/configuring-osgi.md) (por exemplo, com o console da Web) necessários para as configurações de proxy do **Apache HTTP Client**. Ambos são necessários, pois algumas funcionalidades do AEM usam as APIs 3.x, enquanto outros usam as APIs 4.x. Configurar:
>
>* **Day Commons HTTP Client 3.1** para configurar a API 3.x;\
   >  por exemplo, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Configuração** de proxy de componentes HTTP do Apache para configurar a API 4.x;
>
>  
por exemplo, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

