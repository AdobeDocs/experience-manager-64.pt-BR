---
title: Fundamentos das Atribuições
seo-title: Assignments Essentials
description: Visão geral do recurso Atribuições para comunidades de ativação
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 14%

---

# Fundamentos das Atribuições {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta página fornece as informações essenciais para trabalhar com o recurso de atribuições de [comunidade de capacitação](overview.md#enablement-community) sites.

O recurso de atribuições é a capacidade de atribuir recursos de ativação e caminhos de aprendizado aos membros das comunidades de ativação.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ativation/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
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

Status de conclusão e sucesso são usados em relatórios, bem como em banners de status em Atribuições.

Status de conclusão:

* Não atribuído
* Não Iniciado (Novo)
* Em andamento
* Concluir

Status de sucesso:

* Desconhecido
* Aprovado
* Falha

As únicas combinações possíveis de Conclusão e Status de Sucesso são:

| **Conclusão** | **Sucesso** |
|---|---|
| Não iniciado | Desconhecido |
| Em andamento | Desconhecido |
| Concluir | Aprovado |
| Concluir | Falha |

## Fundamentos para o lado do servidor {#essentials-for-server-side}

### Função das atribuições {#assignments-function}

Uma estrutura de site da comunidade que inclui a variável [Função de atribuições](functions.md#assignments-function), inclui um ` [assignments](assignments.md)` componente.

### APIs de referência {#reference-apis}

* [API de ativação](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API de relatórios](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API de relatórios do Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
