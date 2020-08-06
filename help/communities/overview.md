---
title: Visão geral do AEM Communities
seo-title: Visão geral do AEM Communities
description: Uma visão geral dos recursos e da configuração do AEM Communities
seo-description: Uma visão geral dos recursos e da configuração do AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 4%

---


# Visão geral do AEM Communities {#aem-communities-overview}

O Adobe Experience Manager (AEM) Communities oferece a capacidade de criar rapidamente um site local da comunidade com o melhor desempenho, gerenciamento de site, e estimula a conversão de visitantes do site em membros de alto valor da Comunidade.

Entre em contato com seu representante de conta para obter informações sobre o licenciamento da AEM Communities, além de licenças adicionais para recursos de ativação e Adobe Analytics.

## Recursos das comunidades {#communities-features}

A AEM Communities permite o desenvolvimento de uma relação com visitantes do site que informa por meio de blogs, P&amp;R e calendários de eventos, além de obter insights por meio de fóruns, comentários e outros conteúdos da comunidade, geralmente chamados de conteúdo gerado pelo usuário (UGC).

Além disso, a AEM Communities permite a moderação por membros confiáveis no ambiente de publicação, login social com o Twitter e o Facebook, tradução em linha do conteúdo da comunidade, criação de grupos da comunidade do site da comunidade publicado, pontuação para prêmios, compartilhamento de arquivos, notificações e fluxos de atividade.

Os recursos das Comunidades podem ser demonstrados usando a Máquina [de demonstração](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) AEM disponível publicamente em GitHub.com ou com a nova implementação de referência We.Retail.

## Sites da comunidade {#community-sites}

Um site da comunidade é um site AEM criado usando um assistente simples que resulta em um site com muitos recursos comuns pré-conectados ao site.

O assistente [de criação de](sites-console.md)site:

* Reúne os recursos do site, com base no modelo [de site da](sites.md) comunidade selecionado que é
   * Criado a partir de funções [da comunidade](#community-functions)
   * Recurso de grupos [](#communitygroups) da comunidade opcional
* Usa as configurações para configurar:
   * Moderação
   * Logon
   * Tradução
* Fornece recursos essenciais:
   * Design responsivo: Usa temas de Bootstrap [do Twitter](https://getbootstrap.com)
   * Logon: Autoinscrição, login [](social-login.md)social, perfis do usuário
   * Notificações: Os deputados veem eventos relevantes para eles
   * Mensagens: Os membros podem enviar ou receber mensagens no site da comunidade
   * Pesquisar: Capacidade de pesquisar no site da comunidade
   * Mudança de idioma: Capacidade de selecionar um idioma para um site [multilíngue](../../help/sites-administering/translation.md)
   * Administração: Acesso de membros autorizados para moderar e gerenciar usuários no site da comunidade
* Elimina várias etapas de criação no nível da página:
   * Marca: Carregamento opcional de uma imagem de banner para exibição em todas as páginas do site da comunidade
   * Menu de navegação: Links de navegação são fornecidos para os recursos incluídos no modelo de site da comunidade

Para experimentar a facilidade de criar rapidamente um novo site da comunidade, visite [Introdução ao AEM Communities](getting-started.md).

## Persistência do conteúdo da comunidade {#community-content-persistence}

Para melhorar o desempenho e a sincronização do conteúdo da comunidade, a AEM Communities exige uma loja comum especificamente para o conteúdo gerado pelo usuário (UGC) compartilhado entre todas as instâncias de AEM (autor e publicação).

O conteúdo da comunidade é facilmente acessado por meio do SRP (armazenamento Resource Provider, provedor de recursos do ), que fornece uma camada para separar o acesso da topologia subjacente e oferece suporte a uma loja comum para UGC.

Para saber mais sobre a persistência do conteúdo da comunidade e as implantações recomendadas, visite:

* [Armazenamento](working-with-srp.md)de conteúdo da comunidade: discute as opções disponíveis de armazenamento SRP para UGC
* [Topologias](topologies.md)recomendadas: discute topologias com base no caso de uso e na escolha do SRP
* [Atualizando para AEM 6.3 Comunidades](upgrade.md): fornece informações úteis sobre o UGC ao mudar para o AEM 6.3.

## Consoles de comunidades {#communities-consoles}

No ambiente do autor, o console de navegação global fornece acesso ao console [](consoles.md)Comunidades, que contém:

* [Console de sites](sites-console.md)

   * Criação de sites
   * Edição de site
   * Gerenciamento de sites
   * [Console de grupos](groups.md) da comunidade

* [Console de moderação](moderation.md)

   * Interface comum de usuário de moderação em massa para ambientes de autor e publicação
   * Novos critérios de filtragem

* [Consoles de gerenciamento de membros e grupos](members.md)

   * Fornece a capacidade de criar e gerenciar usuários do lado da publicação (membros) a partir do ambiente do autor
   * Permite proibir membros
   * Fornece a capacidade de criar e gerenciar grupos de usuários do lado da publicação (grupos de membros) a partir do ambiente do autor

* [Console de relatórios](reports.md)

   * Fornece a capacidade de gerar relatórios em atribuições, publicações e visualizações

* [Console de recursos](resources.md)

   * Fornece a capacidade de criar recursos de ativação e caminhos de aprendizado
   * Fornece acesso a relatórios sobre recursos de ativação e caminhos de aprendizado

O console de ferramentas globais fornece acesso às seguintes ferramentas de Comunidades:

* [Console de Modelos](tools.md#sitetemplatesconsole) de site

   * Criar e gerenciar modelos de site da comunidade

* [Console Modelos](tools.md#grouptemplatesconsole) de grupo

   * Criar e gerenciar modelos de grupos da comunidade

* [Console de funções](tools.md#communityfunctionsconsole) da comunidade

   * Criar e gerenciar funções da comunidade

* [Console de configuração](tools.md#storageconfiguratonconsole) do Armazenamento

   * Selecionar e configurar a loja [](working-with-srp.md) comum do site

* [Guia do componente](components-guide.md)

   * Um site de amostra, [Community Components](http://localhost:4502/editor.html/content/community-components/en.html), que fornece uma amostra de todos os componentes das Comunidades com sua configuração padrão e a capacidade de experimentar com eles

## Modelos do site da comunidade {#community-site-templates}

A criação de site da comunidade é baseada na seleção de um modelo de site da comunidade para configurar rapidamente um site da comunidade que é independente de qualquer site de amostra.

Um modelo de site da comunidade, composto de funções da comunidade e modelos de grupo da comunidade, fornece a estrutura para um site da comunidade, incluindo login, perfis do usuário, mensagens, menu do site, pesquisa, temas e recursos de marca.

Consulte o console [Modelos de](sites.md)site.

## Funções da comunidade {#community-functions}

Os recursos esperados de uma experiência da comunidade são bem conhecidos. Com a AEM Communities, esses recursos estão disponíveis como blocos de construção, conhecidos como funções da comunidade.

As funções da comunidade são páginas normais AEM compostas de componentes conectados em conjunto em um recurso que é facilmente incorporado em um modelo de site da comunidade.

Consulte o console [Funções da](functions.md)comunidade.

## Grupos da comunidade e modelos de grupo {#community-groups-and-group-templates}

O recurso de grupos da comunidade é a capacidade de uma subcomunidade ser criada dinamicamente em um site da comunidade por usuários autorizados e membros da comunidade do autor e publicar ambientes.

No ambiente do autor, grupos da comunidade (subcomunidades) podem ser criados dentro de um site da comunidade existente ou aninhados dentro de um grupo existente, quando a estrutura do modelo contém a função [](functions.md#groups-function)Grupos.

A criação de um grupo da comunidade requer a seleção de um modelo de grupo da comunidade que forneça o design das páginas de grupo da comunidade. Quando uma função Grupos é adicionada a uma estrutura de modelo, ela é configurada para especificar um modelo de grupo ou para fornecer uma opção de modelos no momento em que um novo grupo da comunidade é criado.

Consulte também:

* [Console](groups.md) de grupos de sites - criar subcomunidades no ambiente do autor
* [Console](tools-groups.md) de modelos de grupo - criar estrutura de site para grupos
* [Introdução ao AEM Communities](getting-started.md) - tutorial para criar rapidamente um site da comunidade incluindo grupos aninhados

## Componentes da comunidade {#community-components}

Os componentes [da](author-communities.md) comunidade a partir dos quais um site da comunidade é criado podem ser usados para adicionar recursos das Comunidades a qualquer Site AEM.

O guia [de componentes da](components-guide.md) comunidade está disponível para exploração interativa dos componentes.

## Tipos de comunidades {#types-of-communities}

### Comunidade de envolvimento {#engagement-community}

Uma comunidade de envolvimento é um site da comunidade focado em envolver os clientes a informar, solicitar feedback e permitir que eles interajam como membros da comunidade.

Os recursos de uma comunidade de envolvimento podem incluir:

* Logon
* Mensagens
* Fóruns
* Comentários
* Revisões
* Classificações
* Votação
* Blogs
* Grupos
* Calendários
* Tradução
* Moderação
* Notificações
* Pontuação e emblemas
* relatórios do Analytics

Para experimentar a facilidade de criar rapidamente uma nova comunidade de envolvimento, visite [Introdução à AEM Communities](getting-started.md).

### Comunidade de ativação {#enablement-community}

Uma comunidade de capacitação é um site da comunidade que inclui recursos para aprendizado online.

Os recursos de uma comunidade de ativação podem incluir:

* Todos os recursos de uma comunidade de [envolvimento](#engagement-community)
* Capacidade de atribuir conteúdo e recursos de aprendizado a membros e grupos membros
* Suporta conteúdo SCORM, como testes e testes
* Rastreamento da conclusão das atribuições
* Acesso a relatórios e análises
* A capacidade de conversar sobre um recurso de aprendizado através de fóruns, mensagens, comentários e classificações

Uma comunidade de ativação pode ser criada quando o complemento [Ativação é configurado](enablement.md), o que requer licenciamento adicional para uso em um ambiente de produção. Um site de comunidade de ativação incluirá a função [de](#community-functions)atribuições.

Para experimentar a facilidade de criar uma nova comunidade de ativação, visite [Introdução à AEM Communities para Ativação](getting-started-enablement.md).

## Máquina de demonstração AEM {#aem-demo-machine}

A [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gerencia e executa demonstrações para AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Ativos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Comunidades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Aplicativos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)e Forms, que geralmente exigem mais configuração do que simplesmente iniciar uma instância do QuickStart. A máquina de demonstração AEM irá configurar [infraestrutura](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) adicional, como MongoDB, Solr, MySQL, FFmpeg e servidores de e-mail.

A máquina de demonstração AEM consiste em

* Uma interface [gráfica do usuário](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts do Apache ANT com [propriedades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) e [públicos alvos configuráveis](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pacotes para instalarA máquina de demonstração AEM foi testada com êxito com CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 e AEM 6.3 no Windows, MacOS e Linux.

A máquina de demonstração AEM requer uma licença AEM válida.

>[!NOTE]
>
>Visualização uma introdução [de](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) vídeo à máquina de demonstração AEM (13:26).

## Documentação do AEM Communities {#aem-communities-documentation}

* Visite [Implantação de comunidades](deploy-communities.md) para saber mais sobre implantações recomendadas.

* Visite [Administrando sites](administer-landing.md) de comunidades para saber mais sobre como criar um site da comunidade, adicionar grupos da comunidade, configurar modelos de site da comunidade, moderar conteúdo da comunidade, gerenciar membros, marcar, notificações, pontuação e emblemas.

* Visite Comunidades [em desenvolvimento](communities.md) para saber mais sobre a estrutura de componentes sociais (SCF) e como personalizar componentes e recursos das Comunidades.

* Visite Componentes [de comunidades de](author-communities.md) criação para saber como criar e configurar componentes de Comunidades.

