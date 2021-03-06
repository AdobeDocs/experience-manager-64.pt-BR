---
title: Conceito de criação
seo-title: Conceito de criação
description: Conceitos de criação no AEM
seo-description: Conceitos de criação no AEM
uuid: 824c8b91-07c7-471b-b3aa-5a73d6d48414
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 72ee013a-7a60-41ee-9421-2846e4c6bc68
translation-type: tm+mt
source-git-commit: b009abd8b3d55bd7dd030d7b4828aec72d9fa9ff
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 86%

---


# Conceito de criação e publicação{#authoring}

O AEM oferece dois ambientes:

* Autor
* Publicação

Eles interagem para permitir a você tornar conteúdo disponível no website, para que os visitantes possam lê-lo.

O ambiente de criação oferece os mecanismos para criação, atualização e análise desse conteúdo, antes de realmente publicá-lo:

* Um autor cria e analisa o conteúdo (que pode ser de vários tipos; por exemplo, páginas, ativos, publicações etc)
* que será, em algum ponto, publicado no website.

![chlimage_1-289](assets/chlimage_1-289.png)

No ambiente de criação, a funcionalidade do AEM é disponibilizada por meio de duas interfaces de usuário. Para o ambiente de publicação, você projeta toda a aparência e comportamento da interface disponível para os usuários.

## Ambiente de criação {#author-environment}

O autor trabalha no que é conhecido como **[ambiente do autor](/help/sites-authoring/home.md)**. Isso oferece uma interface fácil de usar (interface gráfica do usuário (GUI ou UI)) para criar o conteúdo. Em geral, ele está localizado atrás do firewall de uma empresa que oferece proteção total e exige que o autor faça login, usando uma conta que recebeu os direitos de acesso apropriados.

>[!NOTE]
>
>Sua conta precisa dos direitos de acesso apropriados para criar, editar ou publicar conteúdos.

Dependendo do modo como sua instância e seus direitos de acesso pessoais estão configurados, você pode executar muitas tarefas no seu conteúdo, incluindo (dentre outras):

* gerar conteúdo novo ou editar no conteúdo existente em uma página
* usar modelos predefinidos para criar novas páginas de conteúdo
* criar, editar e gerenciar seus ativos e coleções
* criar, editar e gerenciar seus aplicativos
* desenvolver suas campanhas e os recursos relacionados
* desenvolver e administrar sites da comunidade
* mover, copiar ou excluir páginas de conteúdo, ativos etc
* publicar (ou desfazer a publicação de) páginas, ativos etc

Além disso, há tarefas administrativas que o ajudam a gerenciar seu conteúdo:

* fluxos de trabalho que controlam como as alterações são gerenciadas; por exemplo, impor uma análise antes da publicação
* projetos que coordenam tarefas individuais

>[!NOTE]
>
>O AEM também é [administrado](/help/sites-administering/home.md) (para uma grande parte das tarefas) no ambiente do autor.

## Ambiente de publicação {#publish-environment}

Quando pronto, o conteúdo do site AEM é publicado no ambiente **publish**. Aqui, as páginas do site são disponibilizadas para o público desejado de acordo com a aparência da interface projetada.

Normalmente, o ambiente de publicação está localizado dentro da zona desmilitarizada; em outras palavras, disponível para a Internet, mas não mais sob a proteção total da rede interna.

Quando o site do AEM é um [site da comunidade](/help/communities/overview.md), ou inclui [ componentes do Communities](/help/communities/author-communities.md), visitantes do site que fizeram logon (membros) podem interagir com recursos do Communities. Por exemplo, eles podem postar em um fórum, postar um comentário ou seguir outros membros. Os membros podem receber permissão para executar atividades normalmente limitadas para o ambiente de criação, como criar novas páginas (grupos da comunidade), artigos de blog e moderar publicações de outros membros.

>[!NOTE]
>
>Infelizmente, há uma sobreposição na terminologia usada. Isso pode acontecer ao:
>
>* **Publicar/Desfazer a publicação**
   >  Esses são os termos principais para as ações que tornam o conteúdo publicamente disponível no ambiente de publicação (ou não).
   >
   >
* **Ativar / Desativar**
   >  Estes termos são sinônimos de publicar/desfazer a publicação. Eles são mais comuns na interface clássica.
   >
   >
* **Replicar / Replicação**
   >  Estes são os termos técnicos usados para indicar a movimentação de dados (por exemplo, conteúdo da página, arquivos, código, comentários do usuário) de um ambiente para outro; Ou seja, ao publicar ou reverter a replicação de comentários do usuário.
>



## Dispatcher {#dispatcher}

Para otimizar o desempenho para os visitantes do seu site, o **[dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) implementa o balanceamento de carga e o cache.**
