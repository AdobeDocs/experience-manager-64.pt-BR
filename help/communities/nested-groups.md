---
title: Criação de grupos aninhados
seo-title: Authoring Nested Groups
description: Criar grupos aninhados
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 4%

---

# Criação de grupos aninhados {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Criação de grupos no autor {#creating-groups-on-author}

Na criação, na navegação global

* Selecionar **[!UICONTROL Comunidades > Sites]**
* Selecionar **[!UICONTROL pasta de engajamento]** para abri-lo
* Selecione o cartão para o **[!UICONTROL Tutorial de introdução]**  Site em inglês
   * Selecione a imagem do cartão
   * Do *not* selecionar um ícone

O resultado é alcançar a variável [Console Grupos](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

A função groups será exibida como uma pasta na qual instâncias de grupos são criadas. Selecione a pasta Grupos para abri-la. O grupo criado na publicação está visível.

![chlimage_1-54](assets/chlimage_1-54.png)

## Criar grupo principal de artes {#create-main-arts-group}

Esse grupo pode ser criado porque a estrutura do site para engajamento inclui uma função de grupos. A configuração da função no `Reference Template` O padrão é permitir a seleção de qualquer modelo de grupo habilitado. Assim, o modelo escolhido para esse novo grupo será o `Reference Group`.

Esses consoles são muito semelhantes ao console Sites das Comunidades .

* Selecionar **[!UICONTROL Criar grupo]**
* `1 Community Group Template`:
   * Título do grupo da comunidade: Artes
   * Descrição do grupo da comunidade: Um grupo pai para vários grupos artísticos.
   * Raiz do grupo da comunidade: *deixar como padrão*
   * Idioma(s) adicional(is) disponível(is) do grupo da comunidade: use o menu suspenso para selecionar os idiomas disponíveis do grupo da comunidade. O menu exibe todos os idiomas nos quais o site da comunidade pai é criado. Os usuários podem selecionar entre esses idiomas para criar grupos em várias localidades nesta única etapa. O mesmo grupo é criado em vários idiomas especificados no console Grupos dos respectivos sites da comunidade.
   * Nome do grupo da comunidade: artes
   * Modelo: selecione `Reference Group`
   * Selecionar `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

Continue nos outros painéis com estas configurações:

* **2 Design**
   * Você pode alterar o design ou permitir que o padrão seja o design do site pai
   * Selecione **[!UICONTROL Próximo]**
* **3 Configurações**
   * **Moderação**
      * Deixar vazio (herdar do site pai)
   * **Associação**
      * usar padrão `Optional Membership`
   * **Miniatura**
      * `optional`
   * Selecionar `Next`
* Selecione **[!UICONTROL Criar]**

### Aninhamento de grupos no grupo Artes {#nesting-groups-within-arts-group}

O `groups` A pasta agora deve conter dois grupos (pode ser necessário atualizar a página).

![createcommunitygroup](assets/createcommunitygroup.png)

#### Publicar grupo {#publish-group}

Antes de criar grupos aninhados na `arts`, passe o mouse sobre `arts` e selecione o ícone publicar para publicá-lo.

![chlimage_1-55](assets/chlimage_1-55.png)

Aguarde a confirmação de que o grupo foi publicado.

![chlimage_1-56](assets/chlimage_1-56.png)

O `arts` grupo também deve conter um `groups` , mas uma que está vazia e na qual novos grupos podem ser criados. Navegue até a pasta do grupo artístico e crie 3 grupos aninhados, cada um com uma configuração de associação diferente:

1. Visível
   * Título: `Visual Arts`
   * Nome: `visual`
   * Modelo: `Reference Group`
   * Associação: select `Optional Membership`
Um grupo público, aberto a todos os membros
1. Auditório
   * Título: `Auditory Arts`
   * Nome: `auditory`
   * Modelo: `Reference Group`
   * Associação: select `Required Membership`
Um grupo aberto, disponível para membros participarem

1. História

   * Título: `Art History`
   * Nome: `history`
   * Modelo: `Reference Group`
   * Associação: select `Restricted Membership`
Um grupo secreto, visível somente para membros convidados como exemplo, convidar 
[usuário de demonstração](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Atualize a página para ver todos os três grupos aninhados (subcomunidades).

Se necessário, para navegar até os grupos aninhados do console Sites das Comunidades:

* Selecionar **[!UICONTROL pasta de engajamento]**
* Selecionar **[!UICONTROL Tutorial de introdução]** cartão
* Selecionar **[!UICONTROL Pasta Grupos]**
* Selecionar **[!UICONTROL cartão de artes]**
* Selecionar **[!UICONTROL Pasta Grupos]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Grupos de publicação {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Depois de publicar o site principal da comunidade, é necessário

* Publicar cada grupo individualmente
   * Aguardando confirmação de que o grupo foi publicado
* Publicar grupo pai antes de publicar quaisquer grupos aninhados no
   * Todos os grupos devem ser publicados de cima para baixo.

![chlimage_1-59](assets/chlimage_1-59.png)

## Experiência na publicação {#experience-on-publish}

É possível experimentar os diferentes grupos quando ele está conectado, por exemplo, com a variável [usuários de demonstração](tutorials.md#demo-users) usado para

* Membro do grupo Arte/História: emily.andrews@mailinator.com/password
   * O grupo restrito (secreto), artes/história, estará visível
   * Pode ver grupos opcionais (públicos)
   * Pode ingressar em grupos restritos (abertos)
* Gerente de grupo: aaron.mcdonald@mailinator.com/password
   * Pode ver grupos opcionais (públicos)
   * pode ingressar em grupos restritos (abertos)
   * Não verá grupos restritos (secretos)

Acesse as Comunidades [Consoles Membros e grupos](members.md) em autor para adicionar outros usuários a vários grupos de membros que correspondem aos grupos da comunidade.
