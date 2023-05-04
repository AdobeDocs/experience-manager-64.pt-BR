---
title: Fundamentos do fluxo de atividade
seo-title: Activity Stream Essentials
description: Lista de atividades recentes executadas por um membro ou uma lista de atividades recentes em um único thread de conteúdo
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# Fundamentos do fluxo de atividade {#activity-stream-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

As atividades de um membro da comunidade assinado, como postar em um fórum ou blog, são coletadas em um fluxo que pode ser filtrado e exibido de várias maneiras pela configuração do componente fluxos de atividade.

A capacidade de seguir adiciona outro conjunto de atividades quando os membros da comunidade seguem postagens de interesse ou outros membros da comunidade.

Todos [sites da comunidade](overview.md#communitiessites) inclua uma página de perfil de usuário para o membro conectado que exibirá as atividades do membro da mesma maneira.

## Conceitos  {#concepts}

Um *fluxo de atividades* é a lista de atividades recentes executadas por um membro ou uma lista de atividades recentes em um único thread de conteúdo, como um tópico ou blog do fórum.

Um membro pode seguir um fluxo de atividade seguindo outro indivíduo ou conteúdo.

A *feed de notícias* é uma mesclagem dos fluxos de atividade que estão sendo seguidos por um membro em um único fluxo.

A [gráfico social](essentials-socialgraph.md) captura os seguintes relacionamentos de um membro para outro.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystreams</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte <a href="activities.md">Recurso Fluxos de atividade</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [API de fluxos de atividade](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API do ouvinte de fluxos de atividade](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personalizações do lado do servidor](server-customize.md)

### Função de fluxo de atividades {#activity-stream-function}

Uma estrutura de site da comunidade que inclui a variável [Função de fluxo de atividade](functions.md#activity-stream-function), inclui um `activity streams` componente.
