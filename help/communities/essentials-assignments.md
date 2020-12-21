---
title: Essenciais de atribuições
seo-title: Essenciais de atribuições
description: Visão geral do recurso Atribuições para comunidades de ativação
seo-description: Visão geral do recurso Atribuições para comunidades de ativação
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 13%

---


# Essenciais de Atribuições {#assignments-essentials}

Esta página fornece as informações essenciais para trabalhar com o recurso de atribuições dos sites [comunidade de ativação](overview.md#enablement-community).

O recurso de atribuições é a capacidade de atribuir recursos de ativação e caminhos de aprendizado aos membros das comunidades de ativação.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/capacitação/componentes/hbs/myassign</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusivo</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.ativlement.hbs.breadcrumbs<br /> cq.social.ativlement.hbs.myassign<br /> cq.social.ativlement.hbs.resource<br /> cq.social.ativlement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte <a href="assignments.md">Recurso Atribuições</a></td> 
  </tr>
 </tbody>
</table>

### Status de conclusão e sucesso {#completion-and-success-status}

O status de conclusão e sucesso é usado em relatórios, bem como em banners de status em Atribuições.

Status de conclusão:

* Não atribuído
* Não Iniciado (Novo)
* Em andamento
* Concluir

Status de sucesso:

* Desconhecido
* Aprovado
* Falha

As únicas combinações possíveis de Conclusão e Status de sucesso são:

| **Conclusão** | **Sucesso** |
|---|---|
| Não iniciado | Desconhecido |
| Em andamento | Desconhecido |
| Concluir | Aprovado |
| Concluir | Falha |

## Essentials for Server-Side {#essentials-for-server-side}

### Função das atribuições {#assignments-function}

Uma estrutura de site da comunidade que inclui a função [Atribuições](functions.md#assignments-function), inclui um componente ` [assignments](assignments.md)` configurado.

### APIs de referência {#reference-apis}

* [API de ativação](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API do relatórios](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API do Relatórios Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)