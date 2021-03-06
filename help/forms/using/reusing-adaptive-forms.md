---
title: Reutilização de formulários adaptáveis
seo-title: Reutilização de formulários adaptáveis
description: 'É possível reutilizar um formulário adaptável existente para criar novos formulários adaptáveis. '
seo-description: 'É possível reutilizar um formulário adaptável existente para criar novos formulários adaptáveis. '
uuid: f1d0fb70-e255-4dd9-8e6d-fd65eaf2e81a
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Reutilizar formulários adaptáveis {#reusing-adaptive-forms}

## Introdução {#introduction}

Se você quiser usar algumas das propriedades de um formulário adaptável existente para gerar um novo formulário, basta usar a funcionalidade copiar e colar. Além disso, é possível colar o novo formulário adaptável no caminho de pasta desejado. Todas as propriedades de metadados são replicadas e os XFA e os XSDs para formulários adaptáveis baseados em XFA e XSD também são copiados.

>[!NOTE]
>
>O status e os detalhes da revisão não são copiados. Por exemplo, se o formulário adaptável for publicado e, ao copiá-lo, o formulário adaptável colado estará no estado não publicado. Da mesma forma, se um ativo copiado estiver sob revisão, o ativo colado não estará sob a mesma revisão.

### Copiar um formulário adaptável {#copy-an-adaptive-form}

Copie um formulário adaptável usando uma das seguintes abordagens:

1. Clique no ícone copiar ![aem6forms_copy](assets/aem6forms_copy.png) das ações rápidas.

   >[!NOTE]
   >
   >As ações rápidas são itens de ação exibidos em uma miniatura ao passar o mouse.

1. Selecione o formulário adaptável. O processo de seleção é diferente para diferentes exibições.

   Se você estiver na exibição de cartão, vá para o modo de seleção clicando no ícone de seleção ![aem6forms_check-círculo](assets/aem6forms_check-circle.png) e clique em todos os formulários adaptáveis que deseja copiar.

   Se você estiver na exibição em lista, clique nas caixas de seleção de todos os formulários adaptáveis para selecioná-los.

   >[!NOTE]
   >
   >Todos os ativos selecionados devem ser formulários adaptáveis, pois a funcionalidade copiar-colar é suportada somente para formulários adaptáveis e todos os ativos selecionados devem estar presentes na mesma pasta.

   Depois de selecionar os ativos, clique no ícone copiar ![aem6forms_copy](assets/aem6forms_copy.png) presente na barra de ferramentas para copiar o formulário adaptável selecionado.

### Colar um formulário adaptável {#paste-an-adaptive-form}

Clicar na ação de cópia sai automaticamente do modo de seleção e torna visível o ícone de colar ![aem6forms_paste](assets/aem6forms_paste.png). Agora vá para o caminho da pasta desejada e clique no ícone colar ![aem6forms_paste](assets/aem6forms_paste.png) para colar o formulário adaptável copiado.

Se você estiver colando na mesma pasta ou em outro arquivo com o mesmo nome de nó (com o qual está armazenado no repositório CRX) existir nessa pasta de destino, 1 será anexado ao sufixo (por exemplo, myaf se torna myaf1 e se myaf1 existir no mesmo local, myaf se torna myaf2. Todas as outras propriedades permanecem iguais ao formulário adaptável original.

Depois de clicar no ícone de colar ![aem6forms_paste](assets/aem6forms_paste.png), ele ficará novamente oculto. De uma vez, você só pode colar uma vez. Para criar novamente uma cópia do mesmo ativo, copie-o novamente.

### Alterar o conteúdo do novo formulário adaptável {#change-contents-of-new-adaptive-form}

O conteúdo de um formulário adaptável colado pode ser alterado usando as seguintes abordagens para torná-lo diferente do formulário copiado:

1. **Alterar propriedades de metadados:**

   É possível alterar as propriedades de metadados do formulário adaptável, por exemplo, título e descrição. Para obter mais detalhes sobre as propriedades de metadados e como eles podem ser alterados, consulte [Gerenciar metadados do formulário](/help/forms/using/manage-form-metadata.md)

1. **Altere o XFA/XSD para o Forms adaptável baseado em XFA/XSD:**

   Você pode alterar o XFA/XSD usado em formulários adaptáveis. Para saber como esses formulários adaptáveis podem ser alterados, consulte [Gerenciar metadados do formulário](/help/forms/using/manage-form-metadata.md)

1. **Publicar novamente:**

   O ativo colado é diferente do copiado. Você pode publicá-lo como um novo ativo para torná-lo disponível para os usuários finais. Para saber como publicar um ativo, consulte [Publicar e desfazer a publicação de formulários](/help/forms/using/publishing-unpublishing-forms.md)

