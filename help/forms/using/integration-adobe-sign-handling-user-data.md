---
title: Integração com o Acrobat Sign | Tratamento de dados de utilizadores
seo-title: Integration with Acrobat Sign | Handling user data
description: O AEM Forms integra-se com o Acrobat Sign para permitir fluxos de trabalho de assinatura eletrônica em formulários adaptáveis para processar formulários ou contratos para fluxos de trabalho legais, de vendas, de folha de pagamento e de gerenciamento de recursos humanos. Saiba mais sobre os dados do usuário, armazenamentos de dados e acesso e exclusão de dados do usuário.
seo-description: AEM Forms integrates with Acrobat Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Acrobat Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 2%

---

# Integração com o Acrobat Sign | Tratamento de dados de utilizadores {#integration-with-adobe-sign-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM Forms integra-se com o Acrobat Sign para permitir fluxos de trabalho de assinatura eletrônica em formulários adaptáveis para processar formulários ou contratos para fluxos de trabalho legais, de vendas, de folha de pagamento e de gerenciamento de recursos humanos. Ele permite a assinatura única e multiusuário, fluxos de trabalho de assinatura sequenciais e simultâneos, a assinatura de formulários como um usuário anônimo ou conectado e várias maneiras de autenticar usuários.

Quando um assinante ou vários signatários assinam e enviam um formulário adaptável, é gerado um contrato de Acrobat Sign que inclui informações sobre os signatários.

Para obter mais informações sobre a integração do AEM Forms com o Acrobat Sign, consulte [Uso do Acrobat Sign em um formulário adaptável](/help/forms/using/working-with-adobe-sign.md).

## Armazenamento de dados e dados do usuário {#data}

O formulário adaptável habilitado para Acrobat Sign inclui informações sobre os signatários e pode incluir outros dados do usuário coletados pelo formulário adaptável. O serviço Acrobat Sign salva os dados do usuário com a assinatura no contrato. O contrato é salvo no servidor Acrobat Sign configurado nos serviços em nuvem da AEM Forms. Além disso, se o formulário adaptável estiver configurado para usar a ação de envio do Portal Forms, os dados do contrato serão salvos no armazenamento de dados do portal de formulários junto com os dados do formulário.

## Acessar e excluir dados do usuário {#access-and-delete-user-data}

Os dados do usuário são coletados dentro do contrato, mas não são salvos em nenhuma das tabelas de serviço. O Acrobat Sign permite que os administradores façam suas próprias escolhas no gerenciamento de dados que controlam no serviço. Os administradores de privacidade no serviço Acrobat Sign podem listar ou remover contratos com base no endereço de email de um solicitante.

O Acrobat Sign oferece uma aplicação web que permite a pesquisa de contratos por participantes e, se necessário, a exclusão deles. Para obter mais informações, consulte [Acrobat Sign - Recurso: Excluir informações do usuário](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Os dados de contratos para formulários adaptáveis configurados para usar a ação de envio do Portal Forms também são salvos no armazenamento de dados do portal de formulários. Para acessar e excluir dados do armazenamento de dados do portal de formulários, consulte [Portal Forms | Tratamento de dados de utilizadores](/help/forms/using/forms-portal-handling-user-data.md).
