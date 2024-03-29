---
title: Tag Essentials
seo-title: Tag Essentials
description: Visão geral das tags
seo-description: Tag overview
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
exl-id: 863ee5e3-daa7-4f7d-8897-291d367cf29d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 5%

---

# Tag Essentials {#tag-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Quando os componentes do AEM Communities são configurados com a marcação ativada, os membros da comunidade podem marcar o conteúdo publicado no ambiente de publicação.

A infraestrutura subjacente para as tags aplicadas no ambiente de publicação é a mesma para as tags aplicadas ao conteúdo no ambiente de criação, como páginas e ativos:

* Consulte [Administração de tags](../../help/sites-administering/tags.md) e [Marcação de conteúdo gerado pelo usuário](tag-ugc.md) (UGC) para obter informações sobre como criar e gerenciar tags.

* Consulte [Marcação para desenvolvedores](../../help/sites-developing/tags.md) para obter informações sobre o [estrutura de marcação](../../help/sites-developing/framework.md) bem como incluir e estender tags em [aplicativos personalizados](../../help/sites-developing/building.md).

* Consulte [Uso da Nuvem de tags sociais](tagcloud.md) para obter informações para autores sobre como adicionar um `social tag cloud` em uma página para realçar as tags aplicadas ao UGC no ambiente de publicação.

* Consulte [Marcar recursos de ativação](tag-resources.md) para obter informações sobre como marcar recursos de catálogos.

A marcação do UGC pode ser ativada ao configurar um [site da comunidade](sites-console.md#tagging) ou um dos seguintes recursos:

* [Blog](blog-feature.md)
* [Calendário](calendar.md)
* [Biblioteca de arquivos](file-library.md)
* [Fórum](forum.md)
* [QnA](working-with-qna.md)

## Fundamentos para o lado do cliente {#essentials-for-client-side}

### Tags em nuvem do Social {#social-tag-cloud}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/tagcloud</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.tagcloud</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td> 
  </tr>
  <tr>
   <td><strong>propriedades</strong></td> 
   <td>Consulte <a href="tagcloud.md">Uso da Nuvem de tags sociais</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [API da Nuvem de tags sociais](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Gerenciador de tags sociais](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

## Pesquisa de tag {#tag-searching}

Em [pacote de recursos 1](deploy-communities.md#latestfeaturepack) (FP1), a pesquisa de tag é realizada usando [títulos de tags](../../help/sites-developing/framework.md#tag-characteristics).

Antes do FP1, a pesquisa era realizada usando [ids de tag](../../help/sites-developing/framework.md#tagid).
