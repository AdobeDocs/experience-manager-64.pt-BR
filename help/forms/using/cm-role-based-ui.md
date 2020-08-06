---
title: NÃO PUBLICAR interface do usuário com base na Função no Gerenciamento de Correspondência
seo-title: NÃO PUBLICAR interface do usuário com base na Função no Gerenciamento de Correspondência
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 1%

---


# NÃO PUBLICAR interface do usuário com base na Função no Gerenciamento de Correspondência {#do-not-publish-role-based-user-interface-in-correspondence-management}

Em AEM, o administrador pode fornecer acesso baseado em funções a grupos de usuários diferentes e executar várias ações em recursos diferentes. Por exemplo, a funcionalidade para criar ou editar dicionários de dados pode estar disponível somente para usuários em um grupo de usuários específico, enquanto outros usuários podem apenas visualização e usar os dicionários de dados.

A interface AEM exibe as opções, como criar ou editar um tipo de ativo, com base no nível de acesso do usuário. Por exemplo, se um usuário não tiver as permissões para criar um dicionário de dados, a opção para criar um dicionário de dados não será exibida na interface do usuário.

Embora o CRX permita que você configure os direitos de acesso para contas de usuários e grupos, este artigo trata-se de direitos de acesso baseados em funções ou grupos de usuários.

Para obter mais informações sobre grupos, permissões, listas de controles de acesso e gerenciamento de usuários e grupos, consulte Administração e segurança [](/help/sites-administering/security.md)do usuário.

## Gerenciando permissões {#managing-permissions}

1. Certifique-se de que o usuário para o qual você deseja gerenciar as permissões seja adicionado ao grupo de usuários relevante.

   Por exemplo, o usuário John Doe é adicionado aos grupos `agents` e `cm-creditcard`. Para obter mais informações, consulte Adicionar usuários ou grupos a um grupo. Para obter mais informações, consulte [Gerenciamento de usuários e grupos](/help/communities/users.md)de usuários.

   ![]()

1. Crie as pastas adequadas para permitir as permissões desejadas.

   Por exemplo, se uma empresa tiver hipoteca doméstica, cartão de crédito e divisões de seguro, poderá criar pastas nomeadas `HomeMortgage`e `CreditCard,``Insurance` manter os ativos relevantes e dar acesso seletivo aos agentes por ativos relevantes apenas para os seus departamentos.

1. Para acessar AEM segurança WCM, execute um dos procedimentos a seguir:

   1. Na tela Bem-vindo ou em vários locais no AEM, clique no ícone de segurança:

   1. Navegue diretamente para `https://[server]:[port]/useradmin`. Certifique-se de fazer logon no AEM como administrador.

      ![]()
   A árvore esquerda lista todos os usuários e grupos atualmente no sistema. Você pode selecionar as colunas que deseja exibir, classificar o conteúdo das colunas e até mesmo alterar a ordem em que as colunas são exibidas arrastando o cabeçalho da coluna para uma nova posição.

   As guias fornecem acesso a várias configurações:

1. Na lista da árvore esquerda, toque no duplo do nome do grupo relevante e selecione a guia Permissões.

   Para localizar o nome do grupo, digite o nome do grupo no espaço fornecido.

1. Na guia Permissões, navegue até o caminho ao qual deseja adicionar permissões. As pastas Gerenciamento de correspondência estão sob a `content/apps/cm/` pasta.

   Marque a caixa de seleção na coluna Membro para os membros que você deseja que tenham permissões para esse caminho. Desmarque a caixa de seleção do membro para o qual deseja remover permissões. Um triângulo vermelho aparece na célula à qual você fez alterações.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >As permissões especificadas em uma pasta substituem as permissões especificadas em suas subpastas.

1. Toque em Salvar.
1. Texto da etapa
1. Texto da etapa
1. Texto da etapa

