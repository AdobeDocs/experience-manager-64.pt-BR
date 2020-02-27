---
title: Princípios básicos do fluxo de atividade
seo-title: Princípios básicos do fluxo de atividade
description: Lista de atividades recentes executadas por um membro ou lista de atividades recentes em um único segmento de conteúdo
seo-description: Lista de atividades recentes executadas por um membro ou lista de atividades recentes em um único segmento de conteúdo
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Princípios básicos do fluxo de atividade {#activity-stream-essentials}

As atividades de um membro da comunidade conectado, como postar em um fórum ou blog, são coletadas em um fluxo que pode ser filtrado e exibido de várias maneiras pela configuração do componente de fluxos de atividade.

A capacidade de seguir adiciona outro conjunto de atividades quando os membros da comunidade seguem postagens de interesse ou outros membros da comunidade.

Todos os sites [da](overview.md#communitiessites) comunidade incluem uma página de perfil de usuário para o membro conectado que exibirá as atividades do membro da mesma maneira.

## Conceitos {#concepts}

Um fluxo *de* atividades é a lista de atividades recentes executadas por um membro ou uma lista de atividades recentes em um único segmento de conteúdo, como um tópico do fórum ou blog.

Um membro pode seguir um fluxo de atividade seguindo outro indivíduo ou conteúdo.

Um feed *de* notícias é uma união dos fluxos de atividade que estão sendo seguidos por um membro em um único fluxo.

Um gráfico [](essentials-socialgraph.md) social captura os seguintes relacionamentos de um membro para outro.

## Essenciais para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ative streams/components/hbs/ativitystreams</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusivo</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.ativitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte Recurso <a href="activities.md">de fluxos de atividade</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do cliente](client-customize.md)

## Fundamentos para servidor {#essentials-for-server-side}

* [API de fluxo de atividade](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API de ouvinte de fluxo de atividade](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personalizações do servidor](server-customize.md)

### Função de fluxo de atividades {#activity-stream-function}

Uma estrutura de site da comunidade que inclui a função [de Fluxo de](functions.md#activity-stream-function)atividade inclui um `activity streams` componente configurado.
