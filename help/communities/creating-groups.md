---
title: Grupos de comunidades
seo-title: Grupos de comunidades
description: Criação de grupos de comunidade
seo-description: Criação de grupos de comunidade
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---


# Grupos de comunidades {#community-groups}

O recurso de grupos da comunidade é a capacidade de uma subcomunidade ser criada dinamicamente em um site da comunidade por usuários autorizados (membros da comunidade e autores) dos ambientes de publicação e autor.

Essa capacidade está presente quando a função [groups](functions.md#groups-function) está presente na estrutura [site da comunidade](sites-console.md).

Um [modelo de grupo da comunidade](tools-groups.md) fornece o design da página de grupo da comunidade quando um grupo da comunidade é criado dinamicamente.

Um ou mais modelos de grupo são selecionados para a função de grupos quando a função é adicionada à estrutura de um site da comunidade ou a um modelo de site da comunidade. Esta lista de modelos de grupo é apresentada ao membro ou autor que cria dinamicamente um novo grupo a partir do site da comunidade.

## Criando um Novo Grupo {#creating-a-new-group}

A capacidade de criar um novo grupo da comunidade depende da existência de um site da comunidade que inclui a função de grupos, como um criado a partir de ` [Reference Site Template](sites.md)`.

Os exemplos a seguir usam o site da comunidade criado a partir de `Reference Site Template`, conforme descrito no tutorial [Introdução ao AEM Communities](getting-started.md).

Esta é a página que carrega na publicação quando o item de menu **[!UICONTROL Grupos]** é selecionado:

![chlimage_1-236](assets/chlimage_1-236.png)

Quando você seleciona o ícone **[!UICONTROL Novo grupo]**, uma caixa de diálogo de edição é aberta.

Na guia **[!UICONTROL Settings]**, você fornece os recursos básicos do grupo:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nome]**
do grupoO título do grupo a ser exibido no site da comunidade.

* ****
DescriçãoUma descrição do grupo a ser exibido no site da comunidade.

* ****
ConvidarUma lista de membros para convidar para entrar no grupo. A pesquisa antecipada fornecerá sugestões de membros da comunidade a serem convidados.

* **[!UICONTROL Nome]**
do URL do grupoO nome da página do grupo que se torna parte do URL.

* **[!UICONTROL Abrir]**
Seleção de Grupo 
`Open Group` indica que qualquer visitante anônimo do site pode visualização no conteúdo e desmarcará a seleção  `Member Only Group`.

* **[!UICONTROL Seleção de]**
grupo somente membro 
`Member Only Group` indica que somente os membros do grupo podem visualização no conteúdo e serão desmarcados  `Open Group`.

Na guia **[!UICONTROL Modelo]** é a capacidade de selecionar na lista de modelos de grupos da comunidade que foram especificados quando a função de grupos foi incluída na estrutura do site da comunidade ou em um modelo de site da comunidade.

![chlimage_1-238](assets/chlimage_1-238.png)

Na guia **[!UICONTROL Image]** está a capacidade de carregar uma imagem para ser exibida para o grupo na página Grupos do site da comunidade. A folha de estilos padrão dimensionará a imagem para 170 x 90 pixels.

![chlimage_1-239](assets/chlimage_1-239.png)

Ao selecionar o botão **[!UICONTROL Criar grupo]**, as páginas do grupo são criadas com base no modelo escolhido, e um grupo de usuários é criado para associação e a página Grupos será atualizada para mostrar a nova subcomunidade.

Por exemplo, a página Grupos com uma nova subcomunidade chamada &quot;Grupo de foco&quot;, para a qual uma miniatura de imagem foi carregada, será exibida da seguinte forma (ainda conectado como um administrador de grupo da comunidade):

![chlimage_1-240](assets/chlimage_1-240.png)

Selecionar o link `Focus Group` abrirá a página Grupo de Foco no navegador, que tem uma aparência inicial com base no modelo escolhido, e inclui um submenu abaixo do menu principal do site da comunidade:

![chlimage_1-241](assets/chlimage_1-241.png)

## Componente de Lista de membro do grupo da comunidade {#community-group-member-list-component}

O componente `Community Group Member List` destina-se ao uso por desenvolvedores de modelos de grupo.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Community Group Essentials](essentials-groups.md) para desenvolvedores.

Para obter outras informações relacionadas a grupos da comunidade, visite [Gerenciar usuários e grupos de usuários](users.md).
