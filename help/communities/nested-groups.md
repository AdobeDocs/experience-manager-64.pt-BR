---
title: Criação de grupos aninhados
seo-title: Criação de grupos aninhados
description: Criar grupos aninhados
seo-description: Criar grupos aninhados
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 3%

---


# Criação de grupos aninhados {#authoring-nested-groups}

## Criação de grupos no autor {#creating-groups-on-author}

No autor, na navegação global

* Selecionar **[!UICONTROL comunidades > Sites]**
* Selecione a pasta **** de participação para abri-la
* Selecione o cartão para o site em inglês do Tutorial de **[!UICONTROL Introdução]**
   * Selecione a imagem do cartão
   * Não *selecionar* um ícone

O resultado é alcançar o console [](groups.md)Grupos:

![chlimage_1-53](assets/chlimage_1-53.png)

A função groups será exibida como uma pasta na qual as instâncias de grupos são criadas. Selecione a pasta Grupos para abri-la. O grupo criado na publicação está visível.

![chlimage_1-54](assets/chlimage_1-54.png)

## Criar grupo de artes principais {#create-main-arts-group}

Esse grupo pode ser criado porque a estrutura do site para engajamento inclui uma função de grupos. A configuração da função no padrão do site `Reference Template` permite a seleção de qualquer modelo de grupo habilitado. Assim, o modelo escolhido para esse novo grupo será o `Reference Group`.

Esses consoles são muito semelhantes ao console Sites das Comunidades.

* Selecionar **[!UICONTROL Criar grupo]**
* `1 Community Group Template`:
   * Título do grupo da comunidade: Artes
   * Descrição do grupo da comunidade: Um grupo pai para vários grupos artísticos.
   * Raiz do grupo da comunidade: *sair como padrão*
   * Idioma(s) adicional(is) disponível(is) do grupo da comunidade:use o menu suspenso para selecionar os idiomas disponíveis do grupo da comunidade. O menu exibe todos os idiomas nos quais o site da comunidade pai foi criado. Os usuários podem selecionar entre esses idiomas para criar grupos em várias localidades nesta única etapa. O mesmo grupo é criado em vários idiomas especificados no console Grupos dos respectivos sites da comunidade.
   * Nome do grupo da comunidade: artes
   * Modelo: puxe para baixo para selecionar `Reference Group`
   * Selecionar `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Continue pelos outros painéis com estas configurações:

* **2 Design**
   * Você pode alterar o design ou permitir que o padrão seja alterado para o design do site pai
   * Selecione **[!UICONTROL Próximo]**
* **3 Configurações**
   * **Moderação**
      * Deixar vazio (herdar do site pai)
   * **Associação**
      * use default `Optional Membership`
   * **Miniatura**
      * `optional`
   * Selecionar `Next`
* Selecione **[!UICONTROL Criar]**

### Aninhamento de grupos no grupo Artes {#nesting-groups-within-arts-group}

A `groups` pasta agora deve conter dois grupos (pode ser necessário atualizar a página).

![createcommunitgroup](assets/createcommunitygroup.png)

#### Publicar grupo {#publish-group}

Antes de criar grupos aninhados dentro do `arts`grupo, passe o mouse sobre o `arts` cartão e selecione o ícone de publicação para publicá-lo.

![chlimage_1-55](assets/chlimage_1-55.png)

Aguarde a confirmação de que o grupo foi publicado.

![chlimage_1-56](assets/chlimage_1-56.png)

O `arts` grupo também deve conter uma `groups` pasta, mas que esteja vazia e na qual novos grupos possam ser criados. Navegue até a pasta do grupo artístico e crie 3 grupos aninhados, cada um com uma configuração de associação diferente:

1. Visível
   * Título: `Visual Arts`
   * Nome: `visual`
   * Modelo: `Reference Group`
   * Associação: selecionar `Optional Membership`Um grupo público, abrir para todos os membros
1. Auditoria
   * Título: `Auditory Arts`
   * Nome: `auditory`
   * Modelo: `Reference Group`
   * Associação: selecionar `Required Membership`Um grupo aberto, disponível para os membros participarem

1. História

   * Título: `Art History`
   * Nome: `history`
   * Modelo: `Reference Group`
   * Associação: selecionar `Restricted Membership`Um grupo secreto, visível somente para membros convidados como exemplo, convidar 
[usuário de demonstração](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Atualize a página para ver os três grupos aninhados (subcomunidades).

Se necessário, para navegar até os grupos aninhados no console Sites das Comunidades:

* Selecionar pasta **[!UICONTROL de participação]**
* Selecione o cartão Tutorial **[!UICONTROL de]** Introdução
* Selecionar pasta **[!UICONTROL Grupos]**
* Selecionar cartão **[!UICONTROL artístico]**
* Selecionar pasta **[!UICONTROL Grupos]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Grupos de publicação {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Depois de publicar o site da comunidade principal, é necessário

* Publicar cada grupo individualmente
   * Aguardando confirmação de que o grupo foi publicado
* Publicar grupo pai antes de publicar quaisquer grupos aninhados em
   * Todos os grupos devem ser publicados de cima para baixo.

![chlimage_1-59](assets/chlimage_1-59.png)

## Experiência de publicação {#experience-on-publish}

É possível experimentar os diferentes grupos ao fazer logon, por exemplo, com os usuários [da](tutorials.md#demo-users) demonstração usados para

* Membro do grupo Arte/Histórico: emily.andrews@mailinator.com/senha
   * O grupo restrito (secreto), artes/história, estará visível
   * Pode ver grupos opcionais (públicos)
   * Pode ingressar em grupos restritos (abertos)
* Gerente de grupo: aaron.mcdonald@mailinator.com/senha
   * Pode ver grupos opcionais (públicos)
   * pode ingressar em grupos restritos (abertos)
   * Não verá grupos restritos (secretos)

Acesse os consoles [](members.md) Membros e Grupos das Comunidades no autor para adicionar outros usuários a vários grupos de membros que correspondam aos grupos da comunidade.
