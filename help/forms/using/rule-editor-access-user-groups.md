---
title: Conceder acesso ao editor de regras para grupos de usuários selecionados
seo-title: Grant rule editor access to select user groups
description: Conceda acesso restrito ao editor de regras para grupos de usuários selecionados.
seo-description: Grant restricted access to rule editor to select user groups.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
feature: Adaptive Forms
exl-id: 5e2960f2-b172-48a7-bba3-4561a5f9c7bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 7%

---

# Conceder acesso ao editor de regras para grupos de usuários selecionados {#grant-rule-editor-access-to-select-user-groups}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Você pode ter diferentes tipos de usuários com habilidades variadas que trabalham com o Adaptive Forms. Embora os usuários especialistas tenham o conhecimento certo para trabalhar com scripts e regras complexas, pode haver usuários básicos que precisam trabalhar somente com o layout e as propriedades básicas dos formulários adaptáveis.

O AEM Forms permite limitar o acesso do editor de regras aos usuários com base em sua função ou função. Nas configurações do serviço de configuração adaptável Forms, você pode especificar a variável [grupos de usuários](/help/sites-administering/security.md) que pode visualizar e acessar o editor de regras.

## Especificar grupos de usuários que podem acessar o editor de regras {#specify-user-groups-that-can-access-rule-editor}

1. Faça logon no AEM Forms como administrador.
1. Na instância do autor, clique em ![adobeexperiencemanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Ferramentas ![martelo](assets/hammer.png) > Operações > Console da Web. O Console da Web é aberto em uma nova janela.

   ![1](assets/1.png)

1. Na Janela do Console da Web, localize e clique em **[!UICONTROL Configuração do canal Web de comunicação interativa e formulário adaptável]**. **[!UICONTROL Configuração do canal Web de comunicação interativa e formulário adaptável]** será exibida. Não altere nenhum valor e clique em **[!UICONTROL Salvar]**.

   Ele cria um arquivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config no CRX-repository.

1. Faça logon no CRXDE como administrador. Abra o arquivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config para edição.
1. Use a seguinte propriedade para especificar o nome de um grupo que pode acessar o editor de regras (por exemplo, RuleEditorsUserGroup) e clique em **Salvar tudo**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Para habilitar o acesso de vários grupos, especifique uma lista de valores separados por vírgula:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Agora, quando um usuário que não faz parte do grupo de usuários especificado (aqui RuleEditorsUserGroup) tocar em um campo, o ícone Editar Regra ( ![edit-rules1](assets/edit-rules1.png)) não está disponível para ela na barra de ferramentas de componentes:

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   Barra de ferramentas Componentes visível para um usuário com acesso ao editor de regras

   ![componentstoolbarwithultre](assets/componentstoolbarwithoutre.png)

   Barra de ferramentas Componentes visível para um usuário sem acesso ao editor de regras

   Para obter instruções sobre como adicionar usuários a grupos, consulte [Administração e segurança do usuário](/help/sites-administering/security.md).
