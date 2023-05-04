---
title: Campaign Management
seo-title: Campaign Management
description: O gerenciamento de campanhas fornece aos profissionais de marketing digital a oportunidade de fornecer conteúdo personalizado e, portanto, criar experiências dedicadas para os visitantes. Ela permite orquestrar suas campanhas de marketing por toda a Web, e-mail e serviços móveis e assim engajar seus visitantes.
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: 2980ec6d-cdd4-4fbd-b4a4-5e45e4508903
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 3%

---

# Campaign Management{#campaign-management}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O gerenciamento de campanhas fornece aos profissionais de marketing digital a oportunidade de fornecer conteúdo personalizado e, portanto, criar experiências dedicadas para os visitantes.

Ela permite orquestrar suas campanhas de marketing por toda a Web, e-mail e serviços móveis e assim engajar seus visitantes. Você pode criar conteúdo, segmentar visitantes, enviar e promover conteúdo direcionado para perfis de usuário específicos e gerenciar campanhas em vários canais.

Este documento descreve os vários elementos que compõem campanhas. Informações mais detalhadas estão disponíveis nos seguintes documentos:

* [Teasers e estratégias](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [Email Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Landing Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Ofertas do Target](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Trabalhar com o Gerenciador de campanha de marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Noções sobre segmentação](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Configuração da sua campanha](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

O gerenciamento de campanhas é composto de vários elementos:

* **Marcas**
Em AEM, as marcas são a unidade de nível superior e formam uma coleção de 
**Campanhas**.

* **Campanhas**
Uma campanha é uma coleção de indivíduos 
**Experiências**.

* **Experiências**
O conteúdo focalizado forma as várias experiências, apresentadas ao visitante em 
**Touchpoints**. Há vários tipos de experiência disponíveis:

   * **Teasers**
      [Páginas/parágrafos do Teaser](#teasers) são usadas para direcionar visitantes específicos **Segmentos** para conteúdo que esteja focado em seus interesses.

      As páginas de Teaser podem:

      * apresentar um intervalo de opções para o visitante escolher
      * mostrar apenas um parágrafo de teaser baseado no segmento específico do visitante; por exemplo, o parágrafo de teaser mostrado pode depender da idade do visitante.

      Normalmente, uma página de teaser é uma ação temporária que durará por um período específico, até ser substituída pela próxima página de teaser.

   * **Boletins informativos**

      [Comunicações por email](#emailmarketing) são usadas para envolver os usuários e incentivá-los a visitar seu site. Em geral, eles assumem o formato de um informativo, enviado para o seu **Clientes potenciais** , normalmente agrupadas em **Listas**). **Observação:** O Adobe não planeja aprimorar mais esse recurso. Recomendação para [aproveitar o Adobe Campaign e a integração para AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

      Isso permite a integração com o Adobe Target (antigo Test&amp;Target), que fornece aos profissionais de marketing uma ferramenta de otimização para a conversão de sites com os recursos necessários para tornar o conteúdo online mais relevante aos clientes — gerando uma conversão maior. O Adobe Target oferece uma interface intuitiva para projetar e executar testes, criar segmentos de público-alvo e direcionar conteúdo — tudo isso a partir de um único aplicativo.


* **Touchpoints**

   Esses são os pontos de contato entre o visitante e sua campanha. Os pontos de contato são conectados às experiências que você criou.

   Por exemplo, para teasers, é a página de conteúdo onde o parágrafo de teaser está localizado. Para um informativo, é a lista de discussão.

* **Clientes em potencial**

   As informações que você coletou sobre seus visitantes e como contatá-los formam a base para seus leads. **Observação:** O Adobe não planeja aprimorar mais esse recurso.

   Recomendação para [aproveitar o Adobe Campaign e a integração para AEM](/help/sites-administering/campaign.md).

* **Listas**

   Geralmente, os leads são agrupados em listas, para que você possa realizar uma ação coletiva neles. Observação: **Observação:** O Adobe não planeja aprimorar mais esse recurso.

   Recomendação para [utilize o Adobe Campaign e a integração a AEM.](/help/sites-administering/campaign.md)

* **Segmentos**

   Os visitantes têm interesses e objetivos diferentes quando chegam a um site. Analisar isso de acordo com fatores como atividade no site, informações de perfil registradas e atividades em outros sites ajuda a definir segmentos. O conteúdo pode então ser direcionado especificamente para as necessidades e os interesses do visitante, de acordo com os segmentos aos quais ele corresponde.

* **MCM**

   O Gerenciador de campanha de marketing (MCM) é um console que permite acessar todas as funcionalidades necessárias para criar e controlar campanhas, marcas, experiências, pontos de contato, leads, listas, segmentos e relatórios.

   Ele pode ser acessado de vários locais (rotulado como **Campanhas**), ou com, por exemplo, o URL:

   `http://localhost:4502/libs/mcm/content/admin.html`
