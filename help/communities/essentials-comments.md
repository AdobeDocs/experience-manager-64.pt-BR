---
title: Comentários essenciais
seo-title: Comentários essenciais
description: Visão geral do componente Comentários
seo-description: Visão geral do componente Comentários
uuid: 58b7bb58-f598-4bcb-93ae-b7795cab51cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 18f54a1c-52aa-414d-b494-1f19b5c10345
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 4%

---


# Comentários essenciais {#comments-essentials}

Esta página fornece os fundamentos de trabalhar com o sistema de comentários (componente de comentários) e as opções para gerenciar o conteúdo gerado pelo usuário (UGC) produzido quando os membros postam comentários ou respostas.

O componente comments estabelece um sistema de comentários de forma que cada publicação seja representada por um componente de comentário (singular). É o sistema de comentários incluído na página. O sistema de comentários criará os comentários individuais quando chamados.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td> social/commons/components/hbs/comments</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusivo</strong></a></td> 
   <td>Sim - as propriedades são editáveis no modo <i>design </i></td> 
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>Clientlibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.comments<br /> cq.social.hbs.vote</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/commons/components/hbs/comments/comments.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>CSS</strong></td> 
   <td> /libs/social/commons/components/hbs/comments/clientlibs/commentsystem.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td> Consulte <a href="comments.md">Usando Comentários</a></td> 
  </tr>
 </tbody>
</table>

[Personalizações do cliente](client-customize.md)

### Uma instância por página {#one-instance-per-page}

A paginação e o uso de URLs para armazenamento em cache e vinculação exigem que o URL seja exclusivo por sistema de comentários. Portanto, somente uma instância de um sistema de comentários é permitida por página.

Outros recursos já incluem o sistema de comentários. São eles:

* [Blog](blog-developer-basics.md)
* [Calendário](calendar-basics-for-developers.md)
* [Biblioteca de arquivos](essentials-file-library.md)
* [Fórum](essentials-forum.md)
* [Perguntas e respostas](qna-essentials.md)
* [Revisões](reviews-basics.md)

### Sinalizar lista de motivo {#flag-reason-list}

A lista do motivo de sinalização pode ser personalizada adicionando flagrazoavelmente list.hbs ao seu aplicativo para substituir o que está em

* /libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs

Isso se aplica a qualquer componente que estende um sistema de comentários.

## Essentials for Server-Side {#essentials-for-server-side}

* [API de comentários](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [Pontos finais de comentários](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Personalizações do servidor](server-customize.md)

### Acessar Comentários Publicados (UGC) {#accessing-posted-comments-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM Comunidades 6.1, o uso de uma [loja comum](working-with-srp.md) para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral](srp.md)  do provedor de recursos do armazenamento - Introdução e visão geral de uso do repositório
* [SRP e UGC Essentials](srp-and-ugc.md)  - métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md)  - Diretrizes de codificação
* [Refatoração](socialutils.md)  do SocialUtils - Mapeamento de métodos de utilitário obsoletos para os métodos atuais do utilitário SRP

