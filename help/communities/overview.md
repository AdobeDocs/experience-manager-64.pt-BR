---
title: Visão geral da AEM Communities
seo-title: AEM Communities Overview
description: Uma visão geral dos recursos e da configuração do AEM Communities
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---

# Visão geral da AEM Communities {#aem-communities-overview}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager (AEM) Communities fornece a capacidade de criar rapidamente um site local da comunidade que melhorou o desempenho, melhorou o gerenciamento do site e incentiva a conversão de visitantes do site em membros valiosos da comunidade.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Recursos das comunidades {#communities-features}

O AEM Communities permite o desenvolvimento de uma relação com visitantes do site que informa por meio de blogs, P&amp;A e calendários de eventos, além de obter insights por meio de fóruns, comentários e outros conteúdos da comunidade, geralmente chamados de conteúdo gerado pelo usuário (UGC).

Além disso, o AEM Communities permite a moderação por membros confiáveis no ambiente de publicação, o logon social com o Twitter e o Facebook, a tradução em linha do conteúdo da comunidade, a criação de grupos da comunidade do site da comunidade publicado, a pontuação para prêmios, o compartilhamento de arquivos, notificações e fluxos de atividade.

Os recursos das comunidades podem ser demonstrados usando o [Máquina de demonstração AEM](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponível publicamente em GitHub.com ou com a nova implementação de referência We.Retail.

## Sites da comunidade {#community-sites}

Um site da comunidade é um site AEM criado por meio de um assistente simples que resulta em um site com muitos recursos comuns pré-conectados ao site.

O [assistente de criação de sites](sites-console.md):

* Reúne recursos do site, com base no [modelo de site da comunidade](sites.md) que
   * Criado de [funções da comunidade](#community-functions)
   * Opcional [grupos da comunidade](#communitygroups) recurso
* Usa configurações para configurar:
   * Moderação
   * Logon
   * Tradução
* Fornece recursos essenciais:
   * Design responsivo: Usos [Temas do Bootstrap twitter](https://getbootstrap.com)
   * Logon: Autoregistro, [logon social](social-login.md), perfis de usuário
   * Notificações: Membros veem eventos relevantes para eles
   * Mensagens: Os membros podem enviar ou receber mensagens no site da comunidade
   * Pesquisar: Capacidade de pesquisar no site da comunidade
   * Comutação de idioma: Capacidade de selecionar um idioma para um [site multilíngue](../../help/sites-administering/translation.md)
   * Administração: Acesso de membros autorizados para moderar e gerenciar usuários no site da comunidade
* Elimina muitas etapas de criação no nível da página:
   * Identidade visual: Carregamento opcional de uma imagem de banner para exibição em todas as páginas do site da comunidade
   * Menu de navegação: Os links de navegação são fornecidos para os recursos incluídos no modelo de site da comunidade

Para experimentar a facilidade de criar rapidamente um novo site da comunidade, visite [Introdução ao AEM Communities](getting-started.md).

## Persistência do conteúdo da comunidade {#community-content-persistence}

Para melhorar o desempenho e a sincronização do conteúdo da comunidade, o AEM Communities exige uma loja comum especificamente para o conteúdo gerado pelo usuário (UGC) compartilhado entre todas as instâncias de AEM (autor e publicação).

O conteúdo da comunidade é facilmente acessado por meio do SRP (Storage Resource Provider, provedor de recursos de armazenamento), que fornece uma camada para separar o acesso da topologia subjacente e oferece suporte a uma loja comum para UGC.

Para saber mais sobre a persistência do conteúdo da comunidade e as implantações recomendadas, visite:

* [Armazenamento de conteúdo da comunidade](working-with-srp.md): discute as opções disponíveis de armazenamento SRP para UGC
* [Topologias recomendadas](topologies.md): discute topologias com base no caso de uso e na escolha da SRP
* [Atualização para AEM Comunidades 6.3](upgrade.md): fornece informações úteis sobre o UGC ao migrar para o AEM 6.3.

## Consoles de comunidades {#communities-consoles}

No ambiente de criação, o console de navegação global fornece acesso ao [Console de comunidades](consoles.md), que contém:

* [Sites](sites-console.md) console

   * Criação do site
   * Edição do site
   * Gerenciamento do site
   * [Grupos da comunidade](groups.md) console

* [Moderação](moderation.md) console

   * Interface comum de moderação em massa para ambientes de criação e publicação
   * Novos critérios de filtragem

* [Membros e grupos](members.md) consoles de gerenciamento

   * Fornece a capacidade de criar e gerenciar usuários do lado da publicação (membros) do ambiente do autor
   * Fornece a capacidade de proibir membros
   * Fornece a capacidade de criar e gerenciar grupos de usuários do lado da publicação (grupos de membros) a partir do ambiente do autor

* [Relatórios](reports.md) console

   * Fornece a capacidade de gerar relatórios sobre atribuições, postagens e visualizações

* [Recursos](resources.md) console

   * Fornece a capacidade de criar recursos de capacitação e caminhos de aprendizado
   * Fornece acesso aos relatórios sobre recursos de ativação e caminhos de aprendizado

O console de ferramentas globais fornece acesso às seguintes ferramentas do Communities:

* [Modelos de site](tools.md#sitetemplatesconsole) console

   * Criar e gerenciar modelos de site da comunidade

* [Modelos de grupo](tools.md#grouptemplatesconsole) console

   * Criar e gerenciar modelos de grupo da comunidade

* [Funções da comunidade](tools.md#communityfunctionsconsole) console

   * Criar e gerenciar funções da comunidade

* [Configuração de armazenamento](tools.md#storageconfiguratonconsole) console

   * Selecione e configure o [loja comum](working-with-srp.md) para o site

* [Guia do componente](components-guide.md)

   * Um site de exemplo, [Componentes da comunidade](http://localhost:4502/editor.html/content/community-components/en.html), que fornece uma amostra de todos os componentes das Comunidades com sua configuração padrão e a capacidade de experimentar com eles

## Modelos do site da comunidade {#community-site-templates}

A criação de site da comunidade é baseada na seleção de um modelo de site da comunidade para configurar rapidamente um site da comunidade que não seja independente de nenhum site de amostra.

Um modelo de site da comunidade, composto por funções da comunidade e modelos de grupo da comunidade, fornece a estrutura para um site da comunidade, incluindo logon, perfis de usuário, mensagens, menu do site, pesquisa, tema e recursos de marca.

Consulte a [Console de modelos de site](sites.md).

## Funções da comunidade {#community-functions}

Os recursos esperados de uma experiência da comunidade são bem conhecidos. Com o AEM Communities, esses recursos estão disponíveis como blocos de construção, conhecidos como funções da comunidade.

As funções da comunidade são páginas de AEM normais compostas por componentes conectados a um recurso que é facilmente incorporado a um modelo de site da comunidade.

Consulte a [Console Funções da comunidade](functions.md).

## Grupos da comunidade e modelos de grupo {#community-groups-and-group-templates}

O recurso de grupos da comunidade é a capacidade de uma subcomunidade ser criada dinamicamente em um site da comunidade por usuários autorizados e membros da comunidade dos ambientes de criação e publicação .

No ambiente de criação, os grupos da comunidade (subcomunidades) podem ser criados em um site da comunidade existente ou aninhados em um grupo existente, quando a estrutura do modelo contém a variável [Função Grupos](functions.md#groups-function).

A criação de um grupo da comunidade requer a seleção de um modelo de grupo da comunidade que fornece o design da(s) página(s) do grupo da comunidade. Quando uma função Grupos é adicionada a uma estrutura de modelo, ela é configurada para especificar um modelo de grupo ou para fornecer uma escolha de modelos no momento em que um novo grupo de comunidade é criado.

Consulte também:

* [Console de grupos de sites](groups.md) - criação de subcomunidades no ambiente de criação
* [Console Modelos de grupo](tools-groups.md) - criação da estrutura do site para grupos
* [Introdução ao AEM Communities](getting-started.md) - tutorial para criar rapidamente um site da comunidade incluindo grupos aninhados

## Componentes da comunidade {#community-components}

O [componentes da comunidade](author-communities.md) do qual um site da comunidade é criado pode ser usado para adicionar recursos do Communities a qualquer Site AEM.

O [guia de componentes da comunidade](components-guide.md) está disponível para exploração interativa dos componentes.

## Tipos de comunidades {#types-of-communities}

### Comunidade de envolvimento {#engagement-community}

Uma comunidade de engajamento é um site da comunidade com foco em envolver os clientes para informar, solicitar feedback e permitir que eles interajam como membros da comunidade.

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
* Relatórios do Analytics

Para experimentar a facilidade de criar rapidamente uma nova comunidade de envolvimento, visite [Introdução ao AEM Communities](getting-started.md).

### Comunidade de ativação {#enablement-community}

Uma comunidade de capacitação é um site da comunidade que inclui recursos para aprendizado online.

Os recursos de uma comunidade de ativação podem incluir:

* Todos os recursos de um [comunidade de engajamento](#engagement-community)
* Capacidade de atribuir conteúdo e recursos de aprendizagem aos membros e grupos de membros
* Suporta conteúdo SCORM, como testes e testes
* Rastreamento da conclusão das atribuições
* Acesso a relatórios e análises
* A capacidade de conversar sobre um recurso de aprendizado por meio de fóruns, mensagens, comentários e classificações

Uma comunidade de ativação pode ser criada quando a variável [O complemento de ativação está configurado](enablement.md), que requer licenciamento adicional para uso em um ambiente de produção. Um site da comunidade de ativação incluirá a variável [função atribuições](#community-functions).

Para experimentar a facilidade de criar uma nova comunidade de ativação, visite [Introdução ao AEM Communities para ativação](getting-started-enablement.md).

## Máquina de demonstração AEM {#aem-demo-machine}

O [Máquina de demonstração AEM](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gerencia e executa demonstrações para AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Ativos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Comunidades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Aplicativos](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) e [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), que geralmente requer mais configuração do que simplesmente iniciar uma instância do QuickStart. A Máquina de Demonstração de AEM irá configurar mais [infraestrutura](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) Como MongoDB, Solr, MySQL, FFmpeg e servidores de email.

A máquina de demonstração de AEM consiste em

* A [interface gráfica do usuário](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Scripts Apache ANT com configurável [propriedades](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) e [targets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pacotes para instalar A máquina de demonstração do AEM foi testada com êxito com o CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 e AEM 6.3 no Windows, MacOS e Linux.

A máquina de demonstração AEM requer uma licença de AEM válida.

>[!NOTE]
>
>Exibir um [introdução ao vídeo](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) à máquina de demonstração AEM (13:26).

## Documentação do AEM Communities {#aem-communities-documentation}

* Visita [Implantação de comunidades](deploy-communities.md) para saber mais sobre implantações recomendadas.

* Visita [Administrar sites das comunidades](administer-landing.md) para saber mais sobre como criar um site da comunidade, adicionar grupos da comunidade, configurar modelos de site da comunidade, moderar conteúdo da comunidade, gerenciar membros, marcação, notificações, pontuação e emblemas.

* Visita [Desenvolvimento de comunidades](communities.md) para saber mais sobre a estrutura de componentes sociais (SCF) e personalizar os componentes e recursos das Comunidades.

* Visita [Componentes de comunidades de criação](author-communities.md) para saber como criar e configurar componentes do Communities.
