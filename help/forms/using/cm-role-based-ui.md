---
title: NÃO PUBLIQUE A interface do usuário baseada em Função no Gerenciamento de Correspondência
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: NÃO PUBLIQUE A interface do usuário baseada em Função no Gerenciamento de Correspondência
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---


# NÃO PUBLIQUE A interface do usuário baseada em Função no Gerenciamento de Correspondência {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

No AEM, o Administrador pode fornecer acesso com base em funções a diferentes grupos de usuários e executar várias ações em diferentes recursos. Por exemplo, a funcionalidade para criar ou editar dicionários de dados pode estar disponível somente para usuários em um grupo de usuários específico, enquanto outros usuários só podiam exibir e usar os dicionários de dados.

A interface de AEM exibe as opções, como criar ou editar um tipo de ativo, com base no nível de acesso de um usuário. Por exemplo, se um usuário não tiver as permissões para criar um dicionário de dados, a opção para criar um dicionário de dados não aparecerá na interface do usuário.

Embora o CRX permita configurar os direitos de acesso para contas de usuários e grupos, este artigo é sobre direitos de acesso baseados em função ou grupo de usuários.

Para obter mais informações sobre grupos, permissões, listas de controle de acesso e gerenciamento de usuários e grupos, consulte [Administração e segurança do usuário](/help/sites-administering/security.md).

## Gerenciamento de permissões {#managing-permissions}

1. Certifique-se de que o usuário para o qual você deseja gerenciar as permissões seja adicionado ao grupo de usuários relevante.

   Por exemplo, o usuário John Doe é adicionado aos grupos `agents` e `cm-creditcard`. Para obter mais informações, consulte Adicionar usuários ou grupos a um grupo. Para obter mais informações, consulte [Gerenciar usuários e grupos de usuários](/help/communities/users.md).

   ![]()

1. Crie as pastas como adequadas para permitir as permissões desejadas.

   Por exemplo, se uma empresa tiver hipoteca, cartão de crédito e divisões de seguro, poderá criar pastas nomeadas `HomeMortgage`, `CreditCard,`e `Insurance` Manter os ativos relevantes e conceder aos agentes o acesso seletivo aos ativos que apenas sejam relevantes para os respectivos departamentos.

1. Para acessar AEM segurança WCM, siga um destes procedimentos:

   1. Na tela Bem-vindo ou em vários locais no AEM, clique no ícone de segurança:

   1. Navegue diretamente para `https://[server]:[port]/useradmin`. Certifique-se de fazer logon no AEM como administrador.

      ![]()
   A árvore da esquerda lista todos os usuários e grupos que estão atualmente no sistema. Você pode selecionar as colunas que deseja exibir, classificar o conteúdo das colunas e até mesmo alterar a ordem em que as colunas são exibidas, arrastando o cabeçalho da coluna para uma nova posição.

   As guias fornecem acesso a várias configurações:

1. Na lista de árvore da esquerda, toque duas vezes no nome do grupo relevante e selecione a guia Permissions .

   Para localizar o nome do grupo, você pode digitar o nome do grupo no espaço fornecido.

1. Na guia permissões , navegue até o caminho ao qual deseja adicionar permissões. As pastas Gerenciamento de correspondência estão no `content/apps/cm/` pasta.

   Marque a caixa de seleção na coluna Membro para os membros que você deseja que tenham permissões para esse caminho. Desmarque a caixa de seleção do membro para o qual deseja remover permissões. Um triângulo vermelho aparece na célula na qual você fez alterações.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >As permissões especificadas em uma pasta substituem as permissões especificadas em suas subpastas.

1. Toque em Salvar.
1. Texto da etapa
1. Texto da etapa
1. Texto da etapa

