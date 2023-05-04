---
title: Fundamentos da votação
seo-title: Voting Essentials
description: Visão geral do componente de votação
seo-description: Voting component overview
uuid: ed0a771d-1c14-4fbf-ab6a-a028e5ee2e2a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 1a947a06-6a5c-4be9-b2fa-e5fa809ff3b8
exl-id: f2ecd59c-a311-4e4a-b1a8-2bc3afe0599d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 3%

---

# Fundamentos da votação {#voting-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A componente de votação, a [tally](tally.md) subclasse, é uma ferramenta útil que permite aos membros classificar um conteúdo específico simplesmente selecionando setas para cima ou para baixo para indicar sua opinião.

É permitido colocar várias instâncias de um componente de votação na mesma página; cada instância deve ser configurada com um `tally name` propriedade.

Não há apoio para o envio anônimo de um voto. Os visitantes do site devem se registrar e fazer logon para participar da votação apenas uma vez. O visitante conectado (membro) pode alterar o voto a qualquer momento.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/components/hbs/votar</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Sim - as propriedades podem ser editadas em <i>projeto </i>modo</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.voting</td> 
  </tr> 
  <tr> 
   <td> <strong>modelos</strong></td> 
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>propriedades</strong></td> 
   <td><p>Consulte <a href="voting.md">Usar votação</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [Tally APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Endpoints Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

### Acesso à Votação Publicada (UGC) {#accessing-posted-voting-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM 6.1 Comunidades, uso de um [loja comum](working-with-srp.md) O para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - diretrizes de codificação
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais
