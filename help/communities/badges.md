---
title: Console de símbolos
seo-title: Console de símbolos
description: O console Caracteres das comunidades permite que você adicione emblemas personalizados que podem ser exibidos para membros quando ganhados (premiados) ou quando assumem uma função específica na comunidade (atribuídos)
seo-description: O console Caracteres das comunidades permite que você adicione emblemas personalizados que podem ser exibidos para membros quando ganhados (premiados) ou quando assumem uma função específica na comunidade (atribuídos)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# Console de símbolos {#badges-console}

## Sobre os emblemas {#about-badges}

O console Distintos de comunidades fornece a capacidade de adicionar emblemas personalizados que podem ser exibidos para um membro quando obtidos (concedidos) ou quando assumem uma função específica na comunidade (atribuídos).

### Visibilidade do selo {#badge-visibility}

Atualmente, os emblemas que um membro da comunidade recebe ou está atribuído serão exibidos junto com seu nome e avatar nos seguintes locais:

* Perfis
* [Fóruns](forum.md)
* [Perguntas e respostas](working-with-qna.md)
* [Quadros de líderes](enabling-leaderboard.md)
* [Ideação](ideation-feature.md)

No ambiente do autor, para acessar o console Badges

* Da navegação global: **[!UICONTROL Ferramentas > Comunidades > Crachás]**

Esse console exibe os emblemas disponíveis no momento e a partir dos quais novos emblemas podem ser adicionados.

![chlimage_1-242](assets/chlimage_1-242.png)

## Criar selo {#create-badge}

Um crachá é criado fazendo upload de uma imagem bem pequena (72 dpi com uma altura entre 26 e 32 pixels) e fornecendo um nome. A imagem do crachá é armazenada no repositório em `/etc/community/badging/images` e é replicada automaticamente para o ambiente de publicação.

Se o ambiente publish for um farm de editores, será necessário configurar a sincronização [](sync.md)do usuário.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Carregar imagem]**

   (*Obrigatório*) Uma imagem de emblema com um tamanho recomendado de 32 x 32 pixels em 72 dpi no formato JPEG ou PNG.

* **[!UICONTROL Nome]**

   (*Obrigatório*) O nome do crachá. É o nome padrão `Display Name` e o nome do nó do repositório. Se o nome do nó do repositório não `Name` for válido, ele será modificado.

* **[!UICONTROL Nome para exibição]**

   (*Opcional*) O nome a ser exibido para o crachá na interface do usuário. Padrão é o texto inalterado inserido para o `Name`.

* **[!UICONTROL Descrição]**

   (*Opcional*) Uma descrição para o crachá.

## Informações adicionais {#additional-information}

Para obter detalhes sobre como configurar regras de pontuação e marcação, consulte [Pontuação e Distintos](implementing-scoring.md).

Para gerenciar emblemas para membros, consulte Console [](members.md)Membros.
