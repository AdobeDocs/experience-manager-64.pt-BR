---
title: Princípios básicos do painel de líderes
seo-title: Leaderboard Essentials
description: Visão geral de recursos do Painel de líderes
seo-description: Leaderboard feature overview
uuid: 815a6928-b147-496d-9751-13159ad1304d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7449f99e-77d7-4c0f-96d5-b67d5e1f124a
exl-id: 20c16e96-2ba8-4f2d-8cfa-8cd804e3441f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 9%

---

# Princípios básicos do painel de líderes {#leaderboard-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta página fornece as informações essenciais para trabalhar com o recurso de quadro de líderes.

Antes de incluir o componente de quadro de liderança em uma página, é necessário configurar [Pontuação e emblemas de comunidades](implementing-scoring.md). Consulte também [Fundamentos de pontuação e emblemas](configure-scoring.md).

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/gama/componentes/hbs/liderança</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.gamification.hbs.leaderboard</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte <a href="enabling-leaderboard.md">Recurso de quadro de líderes</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

### Função da biblioteca de arquivo {#file-library-function}

Uma estrutura de site da comunidade que inclui a variável [Função de quadro de líderes](functions.md#leaderboard-function), inclui um `leaderboard` componente.
