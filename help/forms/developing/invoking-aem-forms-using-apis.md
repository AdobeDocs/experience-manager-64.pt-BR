---
title: Chamar o AEM Forms usando APIs
seo-title: Invoking AEM Forms using APIs
description: O Adobe Experience Manager Forms é um software corporativo baseado em J2EE que consiste em serviços que operam dentro de uma infraestrutura compartilhada. Saiba como usar aplicativos clientes para chamar o AEM Forms programaticamente usando uma API Java, serviços da Web, Remoting e REST API.
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---

# Chamar o AEM Forms usando APIs {#invoking-aem-forms-using-apis}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager Forms é um software corporativo baseado em J2EE que consiste em serviços que operam dentro de uma infraestrutura compartilhada. As operações de serviço normalmente consomem ou produzem documentos. Ao usar o AEM Forms, é possível combinar o fluxo de trabalho de formulários com formulários eletrônicos, segurança de documentos e geração de documentos em um conjunto de serviços integrado e coeso. Esses serviços podem ser acessados dentro e fora do firewall.

Aplicativos clientes podem invocar programaticamente os serviços da AEM Forms usando uma API Java, serviços da Web, Remota e REST. Usando o console de administração, é possível configurar um serviço para expor um terminal que permite aos serviços da AEM Forms por chamada programática. Por padrão, a maioria dos serviços é pré-configurada para expor pontos de extremidade de Remota, Java e serviço da Web.

Seus requisitos comerciais determinam qual método de invocação usar. Por exemplo, usando a API Java, é possível integrar a funcionalidade AEM Forms em seus aplicativos empresariais Java, como Java Entity e Message beans. Da mesma forma, é possível integrar a funcionalidade do AEM Forms em projetos do .NET (ou outros projetos desenvolvidos com ambientes de desenvolvimento que suportam padrões de serviço da Web) usando serviços da Web.

Os serviços exigem que um contêiner de serviço seja executado, de modo semelhante a como o Enterprise JavaBeans™ (EJBs) requer um contêiner J2EE. O AEM Forms inclui apenas uma implementação de um contêiner de serviço. O contêiner de serviço é responsável pelo gerenciamento da duração de um serviço, incluindo sua implantação e garantia de que todas as solicitações sejam enviadas para o serviço correto. Ele também gerencia documentos que um serviço consome ou produz.

>[!NOTE]
>
>A programação com formulários AEM não inclui informações sobre como invocar o AEM Forms usando pastas vigiadas ou email.
