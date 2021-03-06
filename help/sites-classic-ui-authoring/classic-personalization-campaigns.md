---
title: Gerenciamento de campanhas
seo-title: Gerenciamento de campanhas
description: O gerenciamento de campanhas fornece aos profissionais de marketing digital a oportunidade de fornecer conteúdo personalizado e, dessa forma, criar experiências dedicadas para os visitantes. Ele permite orquestrar campanhas de marketing por toda a web e em serviços móveis e de email, envolvendo assim os seus visitantes.
seo-description: O gerenciamento de campanhas fornece aos profissionais de marketing digital a oportunidade de fornecer conteúdo personalizado e, dessa forma, criar experiências dedicadas para os visitantes. Ele permite orquestrar campanhas de marketing por toda a web e em serviços móveis e de email, envolvendo assim os seus visitantes.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
translation-type: tm+mt
source-git-commit: 02aee2202a570320cd7eb40c2e566d886af4e163
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 85%

---


# Gerenciamento de campanhas{#campaign-management}

O gerenciamento de campanhas fornece aos profissionais de marketing digital a oportunidade de fornecer conteúdo personalizado e, dessa forma, criar experiências dedicadas para os visitantes.

Ele permite orquestrar campanhas de marketing por toda a web e em serviços móveis e de email, envolvendo assim os seus visitantes. Você pode criar conteúdo, segmentar visitantes, enviar e promover conteúdo direcionado para perfis de usuário específicos e gerenciar campanhas em vários canais.

Esse documento descreve os vários elementos que compõem as campanhas. Informações mais detalhadas estão disponíveis nos seguintes documentos:

* [Teasers e estratégias](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [Email Marketing](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Páginas de aterrissagem](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Ofertas de direcionamento](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Trabalhar com o Marketing Campaign Manager](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Noções sobre segmentação](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Configuração da sua campanha](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

O gerenciamento de campanhas é composto de vários elementos:

* ****
MarcasNo AEM, as marcas são a unidade de nível superior e formam uma coleção de 
**Campanhas**.

* ****
CampanhasUma campanha é uma coleção de 
**Experiências**.

* ****
ExperiênciasO conteúdo direcionado forma as várias experiências, apresentadas ao visitante em 
**Pontos de contato**. Existem vários tipos de experiências disponíveis:

   * **Teasers**
      [Página de teaser/Parágrafos](#teasers) são usados para direcionar **Segmentos** específicos de visitantes para conteúdos concentrados em seus interesses.

      Páginas de teaser podem:

      * apresentar uma gama de opções para o visitante escolher
      * mostrar somente um parágrafo de teaser baseado no segmento de visitantes específico; por exemplo, o parágrafo de teaser mostrado pode depender da idade do visitante.

      Geralmente, uma página de teaser é uma ação temporária que durará por um período específico, até ser substituída pela próxima página de teaser.

   * **Boletins informativos**

      [As ](#emailmarketing) Comunicações por email são usadas para engajar os usuários e incentivá-los a visitar seu site. Elas geralmente assumem o formato de um informativo, enviado aos seus **Leads** (que geralmente estão agrupados em **Listas**). **Observação:** a Adobe não planeja aprimorar mais esse recurso. A recomendação é [aproveitar o Adobe Campaign e a integração com o AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

      Permite a integração com o Adobe Target (o antigo Test&amp;Target), que fornece aos profissionais de marketing uma ferramenta de otimização para a conversão de sites com os recursos necessários para tornar o conteúdo online mais relevante aos clientes — gerando uma conversão maior. O Adobe Target fornece uma interface intuitiva para projetar e executar testes, criar segmentos de públicos-alvo e direcionar conteúdo, tudo isso em um único aplicativo.


* **Pontos de contato**

   Estes são os pontos de contato entre o visitante e sua campanha. Os pontos de interação estão conectados às experiências que você criou.

   Por exemplo, para teasers, é a página de conteúdo em que o parágrafo de teaser está localizado. Para um informativo, é a lista de discussão.

* **Leads**

    As informações que você coletou sobre seus visitantes e como contatá-los formam a base para os seus leads. **Observação:** a Adobe não planeja aprimorar mais esse recurso.

   A recomendação é [aproveitar o Adobe Campaign e a integração com o AEM](/help/sites-administering/campaign.md).

* **Listas**

   Os clientes em potencial são normalmente agrupados em listas para que você possa realizar ações coletivas neles. **Observação:** a Adobe não planeja aprimorar mais esse recurso.

   A recomendação é [aproveitar o Adobe Campaign e a integração com o AEM.](/help/sites-administering/campaign.md)

* **Segmentos**

   Os visitantes têm interesses e objetivos diferentes quando chegam a um site. Analisar esse conteúdo de acordo com fatores como a atividade no site, as informações de perfil registradas e as atividades em outros sites, ajuda você a definir segmentos. O conteúdo pode então ser direcionado especificamente para as necessidades e os interesses do visitante, de acordo com os segmentos aos quais ele corresponde.

* **MCM**

   O Marketing Campaign Manager (MCM) é um console que permite acessar todas as funcionalidades necessárias para criar e controlar campanhas, marcas, experiências, pontos de interação, leads, listas, segmentos e relatórios.

   Ele pode ser acessado de vários locais (rotulado como **Campanha**) ou com, por exemplo, o URL:

   `http://localhost:4502/libs/mcm/content/admin.html`

