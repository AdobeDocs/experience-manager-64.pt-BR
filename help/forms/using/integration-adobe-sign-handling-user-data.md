---
title: Integração com o Adobe Sign | Tratamento de dados de utilizadores
seo-title: Integração com o Adobe Sign | Tratamento de dados de utilizadores
description: O AEM Forms integra-se com o Adobe Sign para permitir fluxos de trabalho de assinatura eletrônica em formulários adaptáveis para processar formulários ou contratos para fluxos de trabalho legais, de vendas, de folha de pagamento e de gerenciamento de recursos humanos. Saiba mais sobre os dados do usuário, armazenamentos de dados e acesso e exclusão de dados do usuário.
seo-description: O AEM Forms integra-se com o Adobe Sign para permitir fluxos de trabalho de assinatura eletrônica em formulários adaptáveis para processar formulários ou contratos para fluxos de trabalho legais, de vendas, de folha de pagamento e de gerenciamento de recursos humanos. Saiba mais sobre os dados do usuário, armazenamentos de dados e acesso e exclusão de dados do usuário.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Integração com o Adobe Sign | Tratamento de dados do usuário {#integration-with-adobe-sign-handling-user-data}

O AEM Forms integra-se com o Adobe Sign para permitir fluxos de trabalho de assinatura eletrônica em formulários adaptáveis para processar formulários ou contratos para fluxos de trabalho legais, de vendas, de folha de pagamento e de gerenciamento de recursos humanos. Ele permite a assinatura única e multiusuário, fluxos de trabalho de assinatura sequenciais e simultâneos, a assinatura de formulários como um usuário anônimo ou conectado e várias maneiras de autenticar usuários.

Quando um assinante ou vários signatários assinam e enviam um formulário adaptável, é gerado um contrato de Adobe Sign que inclui informações sobre os signatários.

Para obter mais informações sobre a integração do AEM Forms com o Adobe Sign, consulte [Uso do Adobe Sign em um formulário adaptável](/help/forms/using/working-with-adobe-sign.md).

## Os dados e armazenamentos de dados do usuário {#data}

O formulário adaptável habilitado para Adobe Sign inclui informações sobre os signatários e pode incluir outros dados do usuário coletados pelo formulário adaptável. O serviço Adobe Sign salva os dados do usuário com a assinatura no contrato. O contrato é salvo no servidor Adobe Sign configurado nos serviços em nuvem da AEM Forms. Além disso, se o formulário adaptável estiver configurado para usar a ação de envio do Portal Forms, os dados do contrato serão salvos no armazenamento de dados do portal de formulários junto com os dados do formulário.

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Os dados do usuário são coletados dentro do contrato, mas não são salvos em nenhuma das tabelas de serviço. O Adobe Sign permite que os administradores façam suas próprias escolhas no gerenciamento de dados que controlam no serviço. Os administradores de privacidade no serviço Adobe Sign podem listar ou remover contratos com base no endereço de email de um solicitante.

O Adobe Sign oferece uma aplicação web que permite a pesquisa de contratos por participantes e, se necessário, a exclusão deles. Para obter mais informações, consulte [Adobe Sign - Recurso: Excluir informações do usuário](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Os dados de contratos para formulários adaptáveis configurados para usar a ação de envio do Portal Forms também são salvos no armazenamento de dados do portal de formulários. Para acessar e excluir dados do armazenamento de dados do portal de formulários, consulte [Portal do Forms | Manipulação de dados do usuário](/help/forms/using/forms-portal-handling-user-data.md).
