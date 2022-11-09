---
title: Fragmentos de conteúdo - Considerações sobre a exclusão
seo-title: Content Fragments - Delete Considerations
description: Fragmentos de conteúdo - Considerações sobre a exclusão
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 75%

---

# Fragmentos de conteúdo - Considerações sobre a exclusão {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Algumas funcionalidades do Fragmento de conteúdo exigem a aplicação de [AEM 6.4 Service Pack 2 (6.4.2.0) ou posterior](/help/release-notes/sp-release-notes.md).

## Permissões — Excluir ou não excluir {#permissions-delete-or-not-delete}

A capacidade de excluir conteúdo é uma ferramenta poderosa, mas também perigosa, com muitos setores precisando restringir e controlar a distribuição desses privilégios.

Com relação às permissões de exclusão, os Fragmentos de conteúdo devem ser considerados em dois níveis:

1. **O fragmento do conteúdo como uma única entidade.**

   * **Caso de uso**: um usuário que precisa editar/atualizar um fragmento de conteúdo **e excluir um fragmento inteiro**.
   * **Permissões**[](/help/sites-administering/security.md#actions)[: a permissão de exclusão pode ser atribuída por meio do gerenciamento de usuários e/ou de grupos](/help/sites-administering/security.md#managing-permissions).

1. **As várias entidades secundárias que compõem um fragmento de conteúdo; por exemplo, variações, nós secundários.**

   A operação básica do editor de fragmentos de conteúdo requer que esses elementos transitórios secundários possam ser excluídos. Por exemplo, ao manipular variações; também ao editar metadados ou gerenciar conteúdo associado.

   * **Caso de uso**: um usuário que precisa editar/atualizar um fragmento de conteúdo, mas **sem ter permissão para excluir um fragmento inteiro**.
   * **Permissões**: consulte [Permissões necessárias somente para funcionalidade de edição](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Quando um usuário não tem [Excluir](/help/sites-administering/security.md#actions) permissões, o editor de Fragmento de conteúdo opera em *somente leitura* modo.

>[!NOTE]
>
>Consulte também [Como auditar operações de gerenciamento de usuários no AEM](/help/sites-administering/audit-user-management-operations.md).

## Permissões necessárias somente para funcionalidade de edição {#permissions-required-for-editor-functionality-only}

Para usuários que precisam editar/atualizar um fragmento de conteúdo, **sem permitir que excluam um fragmento inteiro**, permissões específicas devem ser atribuídas, já que a operação básica do editor de fragmentos de conteúdo requer que elementos transitórios secundários possam ser excluídos.

Por exemplo, ao manipular variações; também ao editar metadados ou gerenciar conteúdo associado.

>[!NOTE]
>
>As permissões de exclusão, necessárias para editar/atualizar um Fragmento de conteúdo, estão incluídas na permissão de exclusão [atribuído por meio do Gerenciamento de usuários e/ou grupos](/help/sites-administering/security.md#managing-permissions).

As permissões necessárias para editar/atualizar um fragmento precisam ser aplicadas ao nó que contém o fragmento de conteúdo ou a um nó principal apropriado (em qualquer nível no `/content/dam`). Quando atribuídas a esse nó principal, as permissões serão aplicadas a todos os nós dentro dessa ramificação.

Por exemplo, uma pasta que manterá todos os fragmentos de conteúdo, como:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Definir as permissões em `/content/dam` também é possível, pois todos os fragmentos de conteúdo são armazenados aqui.
>
>No entanto, essa ação aplica as mesmas permissões de exclusão a *todos* os outros tipos de ativos também.

Os pré-requisitos de permissões para permitir que um usuário e/ou grupo específico edite/atualize um fragmento de conteúdo são:

>[!NOTE]
>
>Esta lista mostra todos os privilégios necessários, não apenas os privilégios de exclusão.

* Para os nós ou pastas do fragmento de conteúdo:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Para o nó `jcr:content` de todos os fragmentos de conteúdo:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`

* Para todos os nós abaixo de `jcr:content` de todos os fragmentos de conteúdo:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`, `jcr:removeNode`

Esses `remove` os privilégios devem [administrado usando Listas de Controle de Acesso, no CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

O `add` e `modify` privilégios também podem ser administrados no CRXDE Lite ou usando o console de Gerenciamento de usuários.

Por exemplo, a definição da variável `remove` privilégios de um grupo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
