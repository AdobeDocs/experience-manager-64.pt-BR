---
title: Conceder acesso ao editor de regras para grupos de usuários selecionados
seo-title: Conceder acesso ao editor de regras para grupos de usuários selecionados
description: Conceda acesso restrito ao editor de regras para selecionar grupos de usuários.
seo-description: Conceda acesso restrito ao editor de regras para selecionar grupos de usuários.
uuid: 3d982858-b2b5-4370-a9d7-5a95842a7897
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6bd58e37-085e-4057-8200-1404d54f41cc
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Conceder acesso ao editor de regras para grupos de usuários selecionados {#grant-rule-editor-access-to-select-user-groups}

## Visão geral {#overview}

Você pode ter diferentes tipos de usuários com habilidades variadas que funcionam com o Adaptive Forms. Embora os usuários especialistas possam ter o conhecimento certo para trabalhar com scripts e regras complexas, pode haver usuários de nível básico que precisam trabalhar somente com o layout e as propriedades básicas de formulários adaptáveis.

A AEM Forms permite limitar o acesso do editor de regras aos usuários com base em sua função ou função. Nas configurações do Adaptive Forms Configuration Service, você pode especificar os [grupos de usuários](/help/sites-administering/security.md) que podem visualização e acessar o editor de regras.

## Especificar grupos de usuários que podem acessar o editor de regras {#specify-user-groups-that-can-access-rule-editor}

1. Faça logon na AEM Forms como administrador.
1. Na instância do autor, clique em ![adobeexperience emanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Ferramentas ![martelo](assets/hammer.png) > Operações > Console da Web. O Console da Web é aberto em uma nova janela.

   ![1](assets/1.png)

1. Na janela Console da Web, localize e clique em **Serviço de configuração de formulário adaptável**. **A caixa** de diálogo Adaptive Form Configuration Service é exibida. Não altere nenhum valor e clique em **Salvar**.

   Ele cria um arquivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config no repositório CRX.

1. Faça logon no CRXDE como administrador. Abra o arquivo /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config para edição.
1. Use a seguinte propriedade para especificar o nome de um grupo que pode acessar o editor de regras (por exemplo, RuleEditorsUserGroup) e clique em **Salvar tudo**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Para habilitar o acesso para vários grupos, especifique uma lista de valores separados por vírgulas:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![create-user](assets/create-user.png)

   Agora, quando um usuário que não faz parte do grupo de usuários especificado (aqui RuleEditorsUserGroup) toca em um campo, o ícone Editar regra ( ![edit-rules1](assets/edit-rules1.png)) não está disponível para ela na barra de ferramentas de componentes:

   ![componentstoolbarwither](assets/componentstoolbarwithre.png)

   Barra de ferramentas Componentes como visível a um usuário com acesso ao editor de regras

   ![componentstoolbarwithoutre](assets/componentstoolbarwithoutre.png)

   Barra de ferramentas Componentes como visível a um usuário sem acesso ao editor de regras

   Para obter instruções sobre como adicionar usuários a grupos, consulte [Administração e segurança do usuário](/help/sites-administering/security.md).

