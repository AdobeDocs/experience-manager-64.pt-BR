---
title: Fundamentos de QnA
seo-title: QnA Essentials
description: Recurso do fórum de perguntas e respostas
seo-description: Questions and answers forum feature
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: 99f8afda-1771-471b-bd0c-99960a453bc9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 4%

---

# Fundamentos de QnA {#qna-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta página fornece as informações essenciais para trabalhar com o recurso de fórum de perguntas e respostas (QnA).

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">incondicional</a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> modelos</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> css</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> propriedades</td> 
   <td>Consulte <a href="working-with-qna.md">Recurso do Fórum QnA</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [API QnA](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [Endpoints de QnA](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

### Função QnA {#qna-function}

Uma estrutura de site da comunidade que inclui a variável [Função QnA](functions.md#qna-function) terá um `QnA` , bem como configurações que afetam a moderação e a marcação. A função QnA suporta a identificação de um [grupo de usuários membro privilegiado](users.md#privileged-members-group).

### Acesso às publicações do Fórum QnA (UGC) {#accessing-qna-forum-posts-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM 6.1 Comunidades, uso de um [loja comum](working-with-srp.md) O para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - diretrizes de codificação
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais
