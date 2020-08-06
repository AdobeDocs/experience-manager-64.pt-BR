---
title: Criação e gerenciamento de revisões de ativos em formulários
seo-title: Criação e gerenciamento de revisões de ativos em formulários
description: 'Uma revisão é um mecanismo que permite que um ou mais revisores comentem sobre um ativo disponível em um formulário. '
seo-description: 'Uma revisão é um mecanismo que permite que um ou mais revisores comentem sobre um ativo disponível em um formulário. '
uuid: 6b1aa54f-d03c-483a-a398-6522b285194c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 43fd720f-2a5a-47fb-b9d9-d19f866cd0a0
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---


# Criação e gerenciamento de revisões de ativos em formulários {#creating-and-managing-reviews-for-assets-in-forms}

## Análise {#review}

Uma revisão é um mecanismo que permite que um ou mais revisores comentem sobre um ativo disponível em um formulário.

## Configuração de uma revisão {#setting-up-a-review}

1. Navegue até a guia Forms e selecione um formulário.
1. Se o ativo não tiver uma revisão em andamento, um ícone de Revisão de Start ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) será exibido na barra Ação. Clique no ícone Start Review ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) .
1. Digite as seguintes informações:

   * Review name: Mandatory, can contain alphanumeric characters, hyphen, or underscore.
   * Descrição da análise: Opcional, descrição da finalidade/conteúdo para análise.
   * Prazo de revisão: Opcional, a data em que a revisão termina. Quando ultrapassado o prazo, a tarefa aparece como &quot;Vencida&quot;.
   * Revisores: Um mínimo de um é obrigatório. Use a caixa de combinação para adicionar revisores. Digitar um nome lista todos os nomes correspondentes; selecione um nome e clique em Adicionar.

1. Preencha todos os detalhes restantes e clique em Start.

### Ações que ocorrem quando uma revisão é configurada {#actions-that-occur-when-a-review-is-set-up}

Esta seção descreve o que acontece quando uma revisão é criada ou configurada.

1. Uma nova tarefa de revisão é criada e atribuída ao iniciador da revisão.
1. Todos os revisores recebem uma tarefa de revisão. A tarefa é exibida na seção Notificações. Um revisor pode clicar em uma notificação ou ir para a Caixa de entrada para visualização da tarefa. Um revisor pode clicar para abrir a tarefa de revisão, para visualização do formulário e para adicionar comentários ao start.

   ![Alerta de notificação do revisor](assets/noti.png)
   **Figura:** *Alerta de notificação do revisor*

1. A caixa de comentários está disponível para o iniciador e os revisores do ativo. Outros podem visualização os comentários, mas não podem escrever comentários.

## Gerenciar uma revisão {#managing-a-review}

>[!NOTE]
>
>Only reviews that are in progress can be modified. As revisões concluídas não podem ser modificadas.

1. Navigate to the Forms tab and select a form.

1. Se um ativo tiver uma revisão em andamento e você for o iniciador da revisão, um ícone Gerenciar revisão ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) aparecerá na barra Ação. Somente o iniciador de revisão pode gerenciar (atualizar/encerrar) a revisão.

   Clique em Gerenciar ![aem6forms_review_chat_](assets/aem6forms_review_chat_comment.png)comentticon.

   For user other than initiator the Manage Review icon is disabled.

1. Você obtém uma tela que exibe informações:

   * **Nome** da revisão: Não é possível editar.
   * **Descrição** da revisão: Disponível para edição.
   * **Prazo** de revisão: Disponível para edição. É possível modificar o prazo para qualquer data e hora além da data e hora atuais.
   * **Revisores**: Disponível para edição. Você pode adicionar ou remover revisores. Se uma tarefa estiver atrasada, você poderá adicionar revisores somente depois de estender o prazo para além da data atual.

1. Edite os campos necessários e clique em Atualizar.

   ![Revisar estado atualizado no Gerenciador de Tarefas](assets/tskmgr.png)
   **Figura:** *Revisar estado atualizado no Gerenciador de Tarefas*

1. Para encerrar a revisão, clique em Encerrar.

### Actions that occur when a review is modified {#actions-that-occur-when-a-review-is-modified}

This section describes, what happens on Review end / modification:

1. Se a descrição de Revisão for modificada, a tarefa correspondente de revisores e o iniciador será atualizada.
1. Se o prazo de revisão for modificado, a tarefa correspondente para os revisores será atualizada com a nova data.

1. Se um revisor for removido:

   ![Remoção de um revisor](assets/removeduser.png)
   **Figura:** *Remoção de um revisor*

   1. Se estiver incompleta, a tarefa atribuída será encerrada.
   1. O revisor não pode mais comentar o ativo.

1. Se um revisor for adicionado:

   ![Adicionar um revisor](assets/addedreviewer.png)
   **Figura:** *Adicionar um revisor*

   1. Uma tarefa de revisão é criada e atribuída ao revisor recém-adicionado.
   1. O revisor recém-adicionado pode adicionar comentários para o ativo.

1. Quando uma revisão terminar:

   1. **Revisores**: Para cada revisor, a tarefa incompleta relacionada com o reexame é encerrada. A tarefa não aparece mais como &quot;Pendente&quot; na seção Notificações do revisor.
   1. **Iniciador**: A tarefa atribuída ao iniciador da revisão está marcada como concluída. A tarefa é removida da seção Notificação do iniciador da revisão.
   1. **Todos**: A revisão é exibida na seção Análises anteriores. Não podem ser acrescentadas outras observações.

