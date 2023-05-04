---
title: Visão geral do eCommerce
seo-title: eCommerce Overview
description: AEM eCommerce genérico está disponível como parte da instalação padrão e oferece a você a funcionalidade completa da estrutura do eCommerce.
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
feature: Commerce Integration Framework
exl-id: d84cd0ec-4586-45c1-a07a-a4d50fcbb629
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 5%

---

# Visão geral do eCommerce{#ecommerce-overview}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

AEM eCommerce genérico está disponível como parte de uma instalação padrão e oferece a você toda a funcionalidade da estrutura do eCommerce.

O Adobe fornece duas versões da Estrutura de integração de comércio:

|  | CIF no local | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versões compatíveis do AEM | AEM no local ou AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integração monolítica, mapeamento pré-criado (modelo)<br> - Repositório JCR | - Magento <br>- Java e Javascript <br>- Nenhum dado do Commerce armazenado no repositório JCR |
| Front-end | AEM páginas renderizadas do lado do servidor | Aplicativo de página mista (renderização híbrida) |
| Catálogo de produtos | - Importador de produto, editor, armazenamento em cache em AEM <br>- Catálogos regulares com páginas de AEM ou proxy | - Nenhuma importação de produto <br>- Modelos genéricos <br>- Dados sob demanda via conector |
| Escalabilidade | - Pode suportar até alguns milhões de produtos (depende do caso de uso) <br> - Armazenamento em cache no Dispatcher | - Sem limitação de volume <br>- Armazenamento em cache no Dispatcher ou CDN |
| Modelo de dados padronizado | Não | Sim, esquema Magento GraphQL |
| Disponibilidade | Sim:<br> - SAP Commerce Cloud (Extensão atualizada para oferecer suporte ao AEM 6.4 e Hybris 5 (padrão) e mantém compatibilidade com Hybris 4 <br>- Salesforce Commerce Cloud (Conector de software aberto para suporte ao AEM 6.4) | Sim por meio do código aberto via GitHub. <br> Magento Commerce (Suporta Magento 2.3.2 (padrão) e compatível com o Magento 2.3.1). |
| Quando usar | Casos de uso limitados: Para cenários em que catálogos pequenos e estáticos podem precisar ser importados | Solução preferencial na maioria dos casos de uso |


## Implantar Outras Implementações {#deploying-other-implementations}

* [Commerce Cloud SAP](/help/sites-deploying/sap-commerce-cloud.md)
* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Para obter informações sobre conceitos e como administrar implementações de comércio eletrônico, consulte [Administração de comércio eletrônico](/help/sites-administering/ecommerce.md).
>
>Para obter informações sobre como estender os recursos de comércio eletrônico, consulte [Desenvolvimento do comércio eletrônico](/help/sites-developing/ecommerce.md).
