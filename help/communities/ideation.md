---
title: Fundamentos da Ideação
seo-title: Ideation Essentials
description: Visão geral do recurso de ideação
seo-description: Ideation feature overview
uuid: abaf03ee-8bf4-4241-96c3-474c95a30a88
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9e4f2f0-d1ff-40c0-abcf-645e40586a84
exl-id: 7fb68293-c6e3-4793-b433-205bcfc23e20
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Fundamentos da Ideação {#ideation-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta página fornece as informações essenciais para trabalhar com o recurso de ideação, que é semelhante a um fórum, mas com a capacidade de salvar como rascunho e uma experiência mais colaborativa.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ideação/componentes/hbs/ideação</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.vote<br /> cq.social.hbs.liking<br /> cq.social.hbs.ideation</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/ideation.hbs<br /> /libs/social/ideation/components/hbs/ideation/ideationlists.hbs<br /> /libs/social/ideation/components/hbs/ideation/composer.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/clientlibs/ideation.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte <a href="ideation-feature.md">Recurso de idealização</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

### Função de ideação {#ideation-function}

Uma estrutura de site da comunidade que inclui a variável [Função de idealização](functions.md#ideation-function), inclui um `ideation` componente.
