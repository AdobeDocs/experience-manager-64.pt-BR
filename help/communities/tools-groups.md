---
title: Modelos de grupo
seo-title: Modelos de grupo
description: Como acessar o console Modelos de grupo
seo-description: Como acessar o console Modelos de grupo
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# Modelos de grupo {#group-templates}

O console Modelos de grupo é muito semelhante ao console [Modelos de site](sites.md). Ambos são blueprints para um conjunto de páginas e recursos pré-conectados que formam um site da comunidade. A diferença é que um modelo de site é para a comunidade principal e um modelo de grupo é para um grupo da comunidade, uma subcomunidade aninhada na comunidade principal.

Um grupo da comunidade é incorporado a um modelo de site ao incluir a função [Grupos](functions.md#groups-function) (que pode não ser a primeira nem apenas a função no modelo).

A partir de Communities [feature pack 1](deploy-communities.md#latestfeaturepack), é possível aninhar grupos incluindo a função Groups dentro de um modelo de grupo.

No momento em que a ação é executada para criar um novo grupo da comunidade, o modelo do grupo (estrutura) é selecionado. A seleção depende de como a função Grupos foi configurada quando adicionada ao modelo do site ou grupo.

>[!NOTE]
>
>Os consoles para a criação de [sites da comunidade](sites-console.md), [modelos de site da comunidade](sites.md), [modelos de grupo da comunidade](tools-groups.md) e [funções da comunidade](functions.md) são para uso somente no ambiente do autor.

## Console de modelos de grupo {#group-templates-console}

No ambiente do autor, para acessar o console de modelos de grupos

* Da navegação global: **[!UICONTROL Ferramentas > Comunidades > Modelos de grupo]**

Este console exibe os modelos a partir dos quais um [site da comunidade](sites-console.md) pode ser criado e permite a criação de novos modelos de grupo.

![groupstemplate](assets/groupstemplate.png)

## Criar modelo de grupo {#create-goup-template}

Para começar a criar um novo modelo de grupo, selecione **[!UICONTROL Criar]**

Isso exibirá o painel do Editor de sites, que contém três subpainéis:

### Informações básicas {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

No painel Informações básicas, um nome, uma descrição e se o modelo está ativado ou desativado são configurados:

* **[!UICONTROL Novo]**
nome do modelo do grupoA ID do nome do modelo

* ****
DescriçãoA descrição do modelo

* **[!UICONTROL Desativado/]**
AtivadoUma opção de alternância que controla se o modelo é referenciável

### Miniatura  {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Opcional) Selecione o ícone Carregar imagem para exibir uma miniatura junto com o Nome e a Descrição para os criadores dos sites da comunidade.

### Estrutura {#structure}

>[!CAUTION]
>
>Se estiver trabalhando com AEM 6.1 Communities FP4 ou anterior, não adicione uma função de grupos a um modelo de grupo.
>
>O recurso de grupos aninhados está disponível a partir de Communities [FP1](communities.md#latestfeaturepack).
>
>Ainda não é permitido adicionar uma função de Grupos como a primeira função ou somente função em um modelo.

![grptemplateeditor](assets/grptemplateeditor.png)

Para adicionar funções de comunidade, arraste do lado direito para a esquerda na ordem em que os links de menu do site devem aparecer. Os estilos serão aplicados ao modelo durante a criação do site.

Por exemplo, se você quiser um fórum, arraste a função do fórum da biblioteca e solte sob o construtor de modelos. Isso resultará na abertura da caixa de diálogo de configuração do fórum. Consulte o console [funções](functions.md) para obter informações sobre as caixas de diálogo de configuração.

Continue arrastando e soltando quaisquer outras funções da comunidade desejadas para um site da subcomunidade (grupo) com base nesse modelo.

![dragfunções](assets/dragfunctions.png)

Depois que todas as funções desejadas forem soltas na área do construtor de modelos e configuradas, selecione **[!UICONTROL Salvar]** no canto superior direito.

## Editar modelo do grupo {#edit-group-template}

Ao exibir grupos de comunidade no console [Modelos de grupo ](#group-templates-console) principal, é possível selecionar um modelo de grupo existente para edição.

Editar um modelo de grupo não afetará os sites da comunidade já criados a partir do modelo. Em vez disso, é possível editar diretamente a estrutura de um site da comunidade[.](sites-console.md#modify-structure)

Esse processo fornece os mesmos painéis que [criar um modelo de grupo](#create-goup-template).
