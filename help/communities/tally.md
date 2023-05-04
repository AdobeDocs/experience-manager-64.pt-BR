---
title: Tally Essentials
seo-title: Tally Essentials
description: Visão geral da classe Tally
seo-description: Tally class overview
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Tally Essentials {#tally-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Tally é uma classe abstrata que fornece um método padrão para coletar feedback dos membros sobre como eles valorizam produtos e serviços específicos. Não há suporte para feedback anônimo. O visitante do site deve se registrar e fazer logon para participar e fazer logon para alterar seus comentários. O requisito para fazer logon facilita a moderação e melhora o valor do feedback, impedindo várias publicações.

Um componente tally personalizado pode ser criado ao estender a classe tally abstrata.

[Curtir](essentials-liking.md) é uma implementação da tally que é uma forma simples de expressar uma opinião positiva.

[Votação](essentials-voting.md) é uma implementação de uma tally que é uma forma simples de expressar uma opinião positiva ou negativa.

[Classificação](rating-basics.md) é uma implementação de uma contagem que utiliza um sistema estelar para expressar uma gama de opiniões de positiva para negativa.

A partir do AEM 6.1, a variável *enquete* não está mais disponível.

[Resenhas](reviews-basics.md) é um componente do SCF que é híbrido de [comentários](essentials-comments.md) e [classificação](rating-basics.md).

## Fundamentos para o lado do cliente {#essentials-for-client-side}

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [Tally APIs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Endpoints Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

### Acesso a Listas Publicadas (UGC) {#accessing-posted-tallies-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM 6.1 Comunidades, uso de um [loja comum](working-with-srp.md) O para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - diretrizes de codificação
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais
