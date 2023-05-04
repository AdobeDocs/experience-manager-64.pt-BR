---
title: Fornecimento de informações seguras de alto volume
seo-title: High-volume secure information delivery
description: A segurança de documentos oferece suporte à associação de licenças aos usuários, em vez de aos documentos em ambientes de produção em massa.
seo-description: Document security supports the association of licenses to users, rather than to the documents in mass production environments.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
feature: Document Security
exl-id: 78fc7c4a-a634-4628-927a-c9622bdc13fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 2%

---

# Fornecimento de informações seguras de alto volume {#high-volume-secure-information-delivery}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Em um ambiente de produção em massa, como o que gera faturas mensais seguras para uma empresa de telecomunicações, criar licenças específicas para cada documento pode se tornar um processo que consome muitos recursos. Nesses casos, a segurança dos documentos é compatível com a associação de licenças aos usuários, e não com os documentos. A licença gerada para um usuário é usada para todos os documentos protegidos para esse usuário.

Uma vantagem dessa abordagem é que o tamanho do banco de dados de segurança de documentos não aumenta linearmente com os documentos, em vez do número de usuários. Além disso, como é necessário criar a licença apenas uma vez para um usuário, a proteção subsequente dos documentos por meio dessas políticas se torna mais rápida. Recursos como acesso offline, expiração de documento e revogação são suportados em todos esses documentos.

A segurança de documentos também oferece suporte às Políticas abstratas. As políticas abstratas são modelos de política que contêm todos os atributos de política, como configurações de segurança de documento e direitos de uso, mas não contêm uma lista de principais. Os administradores podem criar qualquer número de políticas a partir da política abstrata com diferentes entidades que devem ter acesso aos documentos. As alterações introduzidas na política abstrata não afetam as políticas reais geradas pelas políticas abstratas.

No caso da geração mensal de faturas para uma empresa de telecomunicações, você cria uma política abstrata, cria usuários e gera licenças exclusivas para cada usuário. As licenças são posteriormente aplicadas a documentos de cada usuário.

A criação de uma política abstrata é compatível somente por meio do SDK Java de segurança de documento. No entanto, você pode administrar as políticas criadas a partir da política abstrata nas páginas da Web de segurança de documentos. As políticas que são criadas usando esse método são idênticas em comportamento às criadas nas páginas da Web de segurança de documentos.

Consulte [Programação com formulários AEM](https://www.adobe.com/go/learn_aemforms_programming_63) para obter mais informações.
