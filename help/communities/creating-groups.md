---
title: Grupos de comunidades
seo-title: Community Groups
description: Criação de grupos de comunidade
seo-description: Creating community groups
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
exl-id: 4b663228-9cb6-45c0-99dd-8dd7fc2aa4a6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 2%

---

# Grupos de comunidades {#community-groups}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O recurso de grupos da comunidade é a capacidade de uma subcomunidade ser criada dinamicamente em um site da comunidade por usuários autorizados (membros da comunidade e autores) dos ambientes de publicação e autor.

Essa capacidade ocorre quando a variável [função de grupos](functions.md#groups-function) está presente no [site da comunidade](sites-console.md) estrutura.

A [modelo de grupo da comunidade](tools-groups.md) O fornece o design da página de grupo da comunidade quando um grupo da comunidade é criado dinamicamente.

Um ou mais modelos de grupo são selecionados para a função de grupos quando a função é adicionada à estrutura de um site da comunidade ou a um modelo de site da comunidade. Essa lista de modelos de grupo é apresentada ao membro ou autor que cria dinamicamente um novo grupo no site da comunidade.

## Criação de um novo grupo {#creating-a-new-group}

A capacidade de criar um novo grupo da comunidade depende da existência de um site da comunidade que inclui a função de grupos, como um criado a partir do ` [Reference Site Template](sites.md)`.

Os exemplos a seguir usam o site da comunidade criado a partir do `Reference Site Template` conforme descrito no [Introdução ao AEM Communities](getting-started.md) tutorial.

Essa é a página que carrega na publicação quando a variável **[!UICONTROL Grupos]** item de menu selecionado:

![chlimage_1-236](assets/chlimage_1-236.png)

Ao selecionar a variável **[!UICONTROL Novo grupo]** , uma caixa de diálogo de edição é aberta.

Em **[!UICONTROL Configurações]** , forneça os recursos básicos do grupo:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nome do grupo]**
O título do grupo a ser exibido no site da comunidade.

* **[!UICONTROL Descrição]**
Uma descrição do grupo a ser exibido no site da comunidade.

* **[!UICONTROL Convidar]**
Uma lista de membros para convidar para entrar no grupo. A pesquisa antecipada fornecerá sugestões de membros da comunidade a serem convidados.

* **[!UICONTROL Nome do URL do grupo]**
O nome da página de grupo que se torna parte do URL.

* **[!UICONTROL Abrir grupo]**
Selecionar 
`Open Group` indica que qualquer visitante anônimo do site pode visualizar o conteúdo e desmarcará a seleção `Member Only Group`.

* **[!UICONTROL Grupo Somente Membros]**
Selecionar 
`Member Only Group` indica que somente os membros do grupo podem visualizar o conteúdo e desmarcará a seleção `Open Group`.

Em **[!UICONTROL Modelo]** guia é a capacidade de selecionar na lista de modelos de grupo da comunidade que foram especificados quando a função de grupos foi incluída na estrutura do site da comunidade ou em um modelo de site da comunidade.

![chlimage_1-238](assets/chlimage_1-238.png)

Em **[!UICONTROL Imagem]** é a capacidade de carregar uma imagem para exibir para o grupo na página Grupos do site da comunidade. A folha de estilos padrão dimensionará a imagem para 170 x 90 pixels.

![chlimage_1-239](assets/chlimage_1-239.png)

Ao selecionar a variável **[!UICONTROL Criar grupo]** , as páginas do grupo são criadas com base no modelo escolhido e um grupo de usuários é criado para associação e a página Grupos é atualizada para mostrar a nova subcomunidade.

Por exemplo, a página Grupos com uma nova subcomunidade denominada &quot;Grupo de foco&quot;, para a qual uma miniatura de imagem foi carregada, será exibida da seguinte maneira (ainda conectado como administrador de grupo da comunidade):

![chlimage_1-240](assets/chlimage_1-240.png)

Selecionar o `Focus Group` O link abrirá a página Grupo de foco no navegador, que tem uma aparência inicial com base no modelo escolhido, e inclui um submenu abaixo do menu principal do site da comunidade:

![chlimage_1-241](assets/chlimage_1-241.png)

## Componente Lista de membros do grupo da comunidade {#community-group-member-list-component}

O `Community Group Member List` O componente destina-se ao uso por desenvolvedores de modelos de grupo.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos do grupo comunitário](essentials-groups.md) página para desenvolvedores.

Para obter outras informações relacionadas aos grupos da comunidade, visite [Gerenciar usuários e grupos de usuários](users.md).
