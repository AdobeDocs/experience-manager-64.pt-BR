---
title: Modelos de grupo
seo-title: Group Templates
description: Como acessar o console Modelos de grupo
seo-description: How to access the Group Templates console
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 3%

---

# Modelos de grupo {#group-templates}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O console Modelos de grupo é muito semelhante ao [Modelos de site](sites.md) console. Ambos são blueprints para um conjunto de páginas e recursos pré-conectados que formam um site da comunidade. A diferença é que um modelo de site é para a comunidade principal e um modelo de grupo é para um grupo da comunidade, uma subcomunidade aninhada dentro da comunidade principal.

Um grupo da comunidade é incorporado em um modelo de site ao incluir a variável [Função Grupos](functions.md#groups-function) (que pode não ser a primeira nem a única função no template).

Comunidades [pacote de recursos 1](deploy-communities.md#latestfeaturepack), é possível aninhar grupos incluindo a função Grupos em um modelo de grupo.

No momento em que a ação é executada para criar um novo grupo da comunidade, o modelo (estrutura) do grupo é selecionado. A seleção depende de como a função Grupos foi configurada quando adicionada ao modelo de site ou grupo.

>[!NOTE]
>
>Os consoles para a criação de [sites da comunidade](sites-console.md), [modelos de site da comunidade](sites.md), [modelos de grupo da comunidade](tools-groups.md) e [funções da comunidade](functions.md) são para uso somente no ambiente do autor.

## Console Modelos de Grupo {#group-templates-console}

No ambiente de criação, para acessar o console modelos de grupos

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Modelos de grupo]**

Esse console exibe os modelos a partir dos quais uma [site da comunidade](sites-console.md) podem ser criados e permitem a criação de novos modelos de grupo.

![groupstemplate](assets/groupstemplate.png)

## Criar modelo de grupo {#create-goup-template}

Para começar a criar um novo modelo de grupo, selecione **[!UICONTROL Criar]**

Isso exibirá o painel Editor de sites , que contém três subpainéis:

### Informações básicas {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

No painel Informações básicas , um nome, uma descrição e se o modelo está ativado ou desativado são configurados:

* **[!UICONTROL Novo nome do modelo de grupo]**
A ID do nome do modelo

* **[!UICONTROL Descrição]**
A descrição do modelo

* **[!UICONTROL Desativado/Ativado]**
Um switch de alternância que controla se o modelo é referenciável

### Miniatura  {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Opcional) Selecione o ícone Fazer upload da imagem para exibir uma miniatura junto com o Nome e a Descrição para os criadores de sites da comunidade.

### Estrutura {#structure}

>[!CAUTION]
>
>Se estiver trabalhando com AEM 6.1 Communities FP4 ou anterior, não adicione uma função de grupos a um modelo de grupo.
>
>O recurso de grupos aninhados está disponível a partir de Comunidades [FP1](communities.md#latestfeaturepack).
>
>Ainda não é permitido adicionar uma função Grupos como a primeira ou única função em um modelo.

![grptemplateeditor](assets/grptemplateeditor.png)

Para adicionar funções de comunidade, arraste do lado direito para a esquerda na ordem em que os links de menu do site devem aparecer. Os estilos serão aplicados ao modelo durante a criação do site.

Por exemplo, se você quiser um fórum, arraste a função de fórum da biblioteca e solte no construtor de modelo. Isso resultará na abertura da caixa de diálogo de configuração do fórum. Consulte a [console funções](functions.md) para obter informações sobre as caixas de diálogo de configuração.

Continue arrastando e soltando quaisquer outras funções da comunidade desejadas para um site da subcomunidade (grupo) com base nesse modelo.

![dragfunções](assets/dragfunctions.png)

Depois que todas as funções desejadas forem soltas na área do construtor de modelos e configuradas, selecione **[!UICONTROL Salvar]** no canto superior direito.

## Editar modelo do grupo {#edit-group-template}

Ao visualizar grupos da comunidade no [Console Modelos de grupo](#group-templates-console), é possível selecionar um modelo de grupo existente para edição.

Editar um modelo de grupo não afetará os sites da comunidade já criados a partir do modelo. É possível diretamente [editar um site da comunidade](sites-console.md#modify-structure)Em vez disso, a estrutura do .

Esse processo fornece os mesmos painéis que [criação de um modelo de grupo](#create-goup-template).
