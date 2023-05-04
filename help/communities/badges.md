---
title: Console de emblemas
seo-title: Badges Console
description: O console Símbolos de Comunidades permite que você adicione emblemas personalizados que podem ser exibidos para membros quando ganhados (atribuídos) ou quando assumem uma função específica na comunidade (atribuídos)
seo-description: The Communities Badges console lets you add custom badges that can be displayed for members when earned (awarded) or when they take on a specific role in the community (assigned)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 6%

---

# Console de emblemas {#badges-console}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sobre os emblemas {#about-badges}

O console Símbolos de Comunidades oferece a capacidade de adicionar emblemas personalizados que podem ser exibidos para um membro quando ganhados (atribuídos) ou quando assumem uma função específica na comunidade (atribuídos).

### Visibilidade do emblema {#badge-visibility}

Atualmente, os emblemas que um membro da comunidade recebe ou é atribuído serão exibidos junto com seu nome e avatar nos seguintes locais:

* Perfis
* [Fóruns](forum.md)
* [QnA](working-with-qna.md)
* [Painéis de líderes](enabling-leaderboard.md)
* [Ideação](ideation-feature.md)

No ambiente de criação, para acessar o console Selo

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Símbolos]**

Esse console exibe os emblemas disponíveis no momento e a partir dos quais novos emblemas podem ser adicionados.

![chlimage_1-242](assets/chlimage_1-242.png)

## Criar selo {#create-badge}

Um selo é criado fazendo o upload de uma imagem suficientemente pequena (72dpi com uma altura entre 26 e 32 pixels) e fornecendo um nome. A imagem do selo é armazenada no repositório em `/etc/community/badging/images` e é replicado automaticamente para o ambiente de publicação.

Se o ambiente de publicação for um farm de editores, será necessário configurar [sincronização de usuários](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Fazer upload de imagem]**

   (*Obrigatório*) Uma imagem de selo com um tamanho recomendado de 32 x 32 pixels a 72 dpi no formato JPEG ou PNG.

* **[!UICONTROL Nome]**

   (*Obrigatório*) O nome do selo. É o padrão `Display Name` assim como o nome do nó do repositório. Se a variável `Name` não é um nome de nó de repositório válido, ele será modificado.

* **[!UICONTROL Nome de exibição]**

   (*Opcional*) O nome a ser exibido para o símbolo na interface do usuário. O padrão é o texto inalterado inserido para a variável `Name`.

* **[!UICONTROL Descrição]**

   (*Opcional*) Uma descrição para o símbolo.

## Informações adicionais {#additional-information}

Para obter detalhes sobre a configuração de regras de pontuação e marcação, consulte [Pontuação e emblemas](implementing-scoring.md).

Para gerenciar emblemas para membros, consulte [Console de membros](members.md).
