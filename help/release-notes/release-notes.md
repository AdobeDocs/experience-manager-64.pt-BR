---
title: Notas de versão gerais do Adobe Experience Manager 6.4
seo-title: Notas de versão
description: 'Notas de Adobe Experience Manager 6.4 descrevendo as informações da versão, novidades, como instalar e alterar detalhadamente as listas. '
seo-description: 'Notas de Adobe Experience Manager 6.4 descrevendo as informações da versão, novidades, como instalar e alterar detalhadamente as listas. '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '2844'
ht-degree: 26%

---


# Notas de versão gerais do Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

## Informações da versão {#release-information}

| Produto | Adobe Experience Manager |
|---|---|
| Versão | 6.4 |
| Tipo | Versão Principal |
| Data de disponibilidade geral | 4 de abril de 2018 |
| Atualizações recomendadas | See [AEM releases and updates](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html) |

### Trívia {#trivia}

O ciclo de lançamento desta versão do Adobe Experience Manager começou em 27 de abril de 2017, passou por 22 iterações de garantia de qualidade e correção de problemas, terminando em 22 de março de 2018. O número total de problemas relatados por clientes incluindo melhorias e novos recursos corrigidos nesta versão é de 704.

O Adobe Experience Manager 6.4 está disponível por completo desde 4 de abril de 2018.

>[!NOTE]
>
>A Adobe recomenda instalar o service pack mais recente, pois todos os novos service packs só são entregues via [Service Packs](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html).

## Novidades {#what-s-new}

O Adobe Experience Manager 6.4 é uma versão de atualização para o código de base do Adobe Experience Manager 6.3. Ele fornece funcionalidades novas e melhoradas, correções essenciais para o cliente, melhorias de alta prioridade para o cliente e correções gerais de bugs voltadas para a estabilização do produto. Ele também inclui a maioria dos pacotes de recursos do Adobe Experience Manager 6.3, hot fix e versões de service pack.

A lista abaixo fornece uma visão geral - enquanto as páginas subsequentes listas os detalhes completos.

### Base do Experience Manager {#experience-manager-foundation}

Lista completa de alterações em [Base do AEM](wcm-platform.md).

A plataforma do Adobe Experience Manager 6.4 integrada na parte superior das versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e o repositório de conteúdo do Java: Apache Jackrabbit Oak 1.8.2.

O Quickstart usa o Eclipse Jetty 9.3.22 como mecanismo servlet.

#### Interface do usuário {#user-interface}

Vários aprimoramentos foram feitos à interface do usuário para torná-la mais produtiva e fácil de usar.

* [Novo painel](/help/sites-authoring/basic-handling.md#content-tree) da Árvore de conteúdo para navegar rapidamente em uma hierarquia. Em combinação com a visualização da lista, isso restaura o modelo de interação da interface clássica.
* Experiência de rolagem aprimorada na visualização de cartão e lista de pastas grandes.
* [Interação aprimorada com os resultados](/help/sites-authoring/search.md) da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* [Atalhos](/help/sites-authoring/keyboard-shortcuts.md)de teclado adicionais, para a maioria das ações comuns, como abrir um trilho específico, editar, mover e excluir um item ou abrir propriedades.
* [Capacidade de desativar atalhos](/help/sites-authoring/user-properties.md) do teclado (ativar/desativar em Preferências).
* [Parar de mostrar carimbos de data e hora em toda a interface do usuário](/help/sites-authoring/user-properties.md) em relação após 7 dias (defina o padrão em Preferências).

Consulte a documentação [de](/help/sites-authoring/home.md) criação para obter mais informações sobre esses recursos.

>[!CAUTION]
>
>A Adobe não planeja fazer aprimoramentos adicionais à interface do usuário clássica. O AEM 6.4 tem a interface do usuário clássica incluída, e os clientes que atualizam de versões anteriores podem continuar a usando da mesma forma. Observe que a interface do usuário clássica permanece completamente compatível mesmo enquanto obsoluta. [Leia mais](/help/sites-deploying/ui-recommendations.md).

#### Repositório de conteúdo {#content-repository}

* Compactação mais rápida e eficiente por meio da Online Revision Cleanup. Os testes internos mostram que a nova compactação de cauda é até 10 vezes mais rápida e pode recuperar mais espaço em disco com menos IOPS em comparação com AEM 6.3. Isso resulta em menos impacto no desempenho enquanto a Limpeza de revisão online está em execução. Para obter mais informações, consulte [a página](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)de documentação.

* A Limpeza de revisão contínua do MongoMK substitui a manutenção de limpeza agendada
* Eficiência aprimorada para a limpeza de revisão em notebooks Documentos

#### Pesquisar e indexar {#search-indexing}

* Suporte aprimorado para operações de indexação via CLI (oak-run):

   * Verificação de consistência do índice
   * Estatísticas de indexação
   * Importação ou exportação de configuração de índice
   * Reindexação

* Redução do crescimento do repositório relacionado à Lucene para um desempenho geral melhorado do sistema

Para obter mais informações, visite [esta página](/help/sites-deploying/indexing-via-the-oak-run-jar.md)de documentação.

#### Monitoramento {#monitoring}

* Uma nova Visão geral [do](/help/sites-administering/operations-dashboard.md#system-overview) sistema fornece uma visualização de instantâneos sobre todos os status e atividades do sistema relacionados ao desempenho.
* Um novo conjunto de verificações [de](/help/sites-administering/operations-dashboard.md#health-checks) integridade em torno de Indexação, Query e Manutenção

#### Projetos e fluxos de trabalho {#projects-and-workflows}

* Novo Editor [de fluxo de trabalho para criar e editar modelos](/help/sites-developing/workflows-models.md)de fluxo de trabalho.

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Atualizar da versão anterior {#upgrade-from-earlier-version}

* [Compatibilidade](/help/sites-deploying/backward-compatibility.md)com versões anteriores: Os recursos compatíveis com versões anteriores da versão 6.4 ajudam seu código personalizado a permanecer compatível na maioria dos casos e reduzem o esforço de atualização.
* [Avaliação](/help/sites-deploying/pattern-detector.md)da complexidade da atualização: Nova ferramenta de Detector de padrão para avaliar a complexidade de suas atualizações, antes de atualizar.
* [Reestruturação](/help/sites-deploying/repository-restructuring.md)do repositório: reestruturação significativa (principalmente /etc.) para facilitar as atualizações e promover as práticas recomendadas de implementação
* Para obter informações mais gerais sobre atualizações, consulte [esta página](/help/sites-deploying/upgrade.md) para obter mais detalhes.

### Sites do Experience Manager {#experience-manager-sites}

Full list of changes in [AEM Sites and Add-ons](sites.md).

#### Experiências fluidas {#fluid-experiences}

A introdução de Experiências fluidas em start de 2017, respaldada por Fragmentos de conteúdo, Fragmentos de experiência e Serviços de conteúdo, foi o start de evoluir para uma gestão de conteúdo com vários canais. AEM 6.4 alarga significativamente cada uma das áreas:

**[Fragmentos de conteúdo](/help/assets/content-fragments.md)**

As novidades da versão 6.4 são um editor de modelo [de](/help/assets/content-fragments-models.md) conteúdo visual e um novo componente [](https://docs.adobe.com/content/help/pt-BR/experience-manager-core-components/using/components/content-fragment-component.html) configurável para fornecer saída HTML flexível e JSON para incluir no Content Services.

**Fragmentos de experiência**

A criação de variações em um fragmento com o mesmo conteúdo, mas com layout diferente, agora é mais eficiente, graças ao recurso de blocos de construção. Além de enviar Fragmentos de experiência para o Facebook e o Pinterest, agora é possível enviá-los para o Adobe Target como oferta.

**Content Services**

Várias melhorias no Sling Model Exporter e nos Componentes Principais foram incluídas para fornecer uma saída JSON robusta para incorporar conteúdo em aplicativos móveis e experiências criadas com aplicativos de página única.

#### Obtendo sites criados mais rapidamente {#gettings-sites-built-quicker}

AEM 6.4 completa a transformação para o modelo de componente da próxima geração. O conceito dos componentes principais introduzido no AEM 6.3 e agora associado pelo Sistema de estilo oferece uma maneira eficiente de criar novos sites e estender os existentes.

Tutorial recomendado para saber como aproveitar melhor o novo modelo de componente: [Introdução aos AEM Sites - Tutorial da WKND](https://docs.adobe.com/content/help/br/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### Complemento do Screens {#screens-add-on}

Fornecer uma mensagem consistente em todos os canais de marketing, incluindo redes de cartazes digitais e quiosques, é o que os AEM Screens significam. AEM 6.4 adiciona suporte para executar o Player de cartazes no hardware do Microsoft Windows e do Google Chrome OS. Além disso, estão disponíveis melhorias no gerenciamento remoto de dispositivos e programações (grupos de canais).

Para obter mais informações sobre as atualizações do Screens, consulte o Guia [do Usuário do](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)AEM Screens.

### Comunidades do Experience Manager {#experience-manager-communities}

O AEM 6.4 adiciona muitos novos recursos e melhorias às Comunidades. A lista completa das alterações está disponível em [AEM Communities](communities-release-notes.md). Os destaques desta versão são:

#### Melhorias na moderação {#enhancements-to-moderation}

**Detecção automática de spam**

Foi fornecido um novo mecanismo de detecção de spam para filtrar conteúdo indesejado gerado pelo usuário em sites e grupos da comunidade. Depois de habilitado do sistema/console/configMgr, ele marca um conteúdo gerado pelo usuário como spam com base em um conjunto predefinido de palavras de spam. Para saber mais sobre o mecanismo de detecção de spam, consulte [automatizando a geração de conteúdo](/help/communities/moderate-ugc.md#spam-detection)pelo usuário da comunidade.

![detecção de spam](assets/spamdetection.png)

**Novos filtros para QnA**

Novos filtros, chamados Respondidos e Não Respondidos, foram adicionados ao console de moderação em massa para filtrar perguntas de QnA. Para saber como os filtros de status Respondido e Não Respondido funcionam, consulte a moderação [em massa do conteúdo](/help/communities/moderation.md#main-pars-note-521961797)gerado pelo usuário.

**filtros de moderação de marcadores**

A capacidade de marcar os filtros de moderação predefinidos no console de moderação foi fornecida. Esses filtros são anexados ao final da string do URL, portanto, podem ser compartilhados, reutilizados e revisitados posteriormente. Saiba como marcar filtros no console [de moderação em](/help/communities/moderation.md#main-pars-note-429176623)massa.

#### Excluir UGC e perfis de usuário {#delete-ugc-and-user-profiles}

AEM 6.4 Comunidades expõe APIs [predefinidas e](/help/communities/user-ugc-management-service.md) servlet [](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) de amostra para permitir que os usuários finais tenham controle sobre seus dados. Essas APIs também permitem que as organizações de processamento de dados e controle de dados atendam às solicitações de conformidade com o RGPD da UE.

#### Melhorias no gerenciamento de site e de grupos {#enhancements-to-site-and-group-management}

**Criar grupos de várias localidades em uma única etapa**

A capacidade de criar grupos multilíngues em uma única operação foi fornecida. Para criar esses grupos, os usuários podem navegar até Coleção de grupos do site de comunidades desejado no console Sites. Crie um grupo e especifique os idiomas desejados na página Modelo de grupo da comunidade. Para saber mais sobre essa funcionalidade, consulte o console [de grupos da](/help/communities/groups.md)comunidade.

![multilinguismo](assets/multilingualgroup.png)

**[Excluir sites e grupos da comunidade em um clique](/help/communities/groups.md)**

O ícone Excluir agora está disponível nos respectivos sites e grupos, enquanto navega a partir da navegação global. O uso desse ícone exclui todos os itens e conteúdos associados ao site ou grupo e remove todas as associações de usuários. Para saber mais sobre essa funcionalidade, consulte [gerenciar sites](/help/communities/create-site.md#main-pars-text-fe17) da comunidade e [gerenciar grupos](/help/communities/groups.md#main-pars-text-5e8c)da comunidade.

#### Enhancements to Enablement {#enhancements-to-enablement}

As funções de Atribuição e Catálogo agora estão disponíveis em grupos. Isso permite que o conteúdo de aprendizado seja criado, gerenciado e publicado para um conjunto específico de membros da comunidade direcionados. Para saber mais sobre como ativar grupos da comunidade, consulte [Gerenciamento de recursos](/help/communities/resource.md)de ativação.

![catálogo de atribuições](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

O AEM 6.4 traz vários novos recursos e aprimoramentos aos Ativos, incluindo integração nova e aprimorada à Creative Cloud, inovações importantes da Inteligência artificial, gerenciamento aprimorado de metadados, melhorias no relatórios e melhorias gerais na experiência do usuário. A lista completa das alterações disponíveis no [AEM Assets](assets.md). Os destaques da versão são:

**Adobe Asset Link**

Adobe Asset Link no Creative Cloud para empresas simplifica a colaboração entre criativos e profissionais de marketing no processo de criação de conteúdo. É um novo recurso nativo no Creative Cloud para empresas que conecta o Photoshop CC, o Illustrator CC e o InDesign CC ao AEM. sem que os criativos tenham que deixar suas ferramentas de escolha.

Para saber mais sobre esse recurso, os pré-requisitos e como acessá-lo, consulte Link [do ativo do](https://www.adobe.com/br/creativecloud/business/enterprise/adobe-asset-link.html)Adobe.

![adobe_asset_link](assets/adobe_asset_link.png)

**Aplicativo de desktop do AEM**

AEM aplicativo desktop foi atualizado para a versão 1.8, que é compatível com a AEM 6.4. A lista completa de alterações para AEM aplicativo desktop é fornecida em um documento dedicado às notas [de versão do aplicativo desktop](https://docs.adobe.com/content/help/pt-BR/experience-manager-desktop-app/using/release-notes.html) AEM.

As melhorias introduzidas desde a versão AEM 6.3 incluem a capacidade de fazer upload de pastas hierárquicas em segundo plano, uma nova interface do usuário para monitorar operações em segundo plano de ativos, cache aprimorado, operação em rede e login, bem como melhorias gerais na estabilidade. A documentação também inclui um guia [de práticas](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)recomendadas.

**Serviços Adobe Sensei**

Os novos recursos incluem Smart Tags aprimoradas, com a capacidade de aprender a taxonomia comercial do cliente, marcar automaticamente os ativos digitais com tags específicas do cliente e Smart Translation Search, o que melhora a descoberta em vários idiomas ao traduzir os termos de pesquisa dinamicamente. Para saber mais sobre esse recurso, consulte Tags [inteligentes](/help/assets/enhanced-smart-tags.md)aprimoradas.

![advanced_smart_tags2](assets/enhanced_smart_tags2.png)

**Metadados**

Vários aprimoramentos incluem a capacidade de importar e exportar metadados simultaneamente para grandes números de ativos e construções avançadas de metadados, como Metadados em [cascata](/help/assets/cascading-metadata.md).

**Relatórios**

O relatórios de ativos sofreu uma grande revisão no AEM 6.4 com a nova estrutura do relatórios, a experiência do usuário e mais relatórios OOTB para casos de uso do cliente. Para saber como gerar vários relatórios, consulte Relatórios [de](/help/assets/asset-reports.md)ativos.

**Experiência do usuário**

Vários aprimoramentos para melhorar a navegação, a pesquisa e a experiência administrativa para usuários do Assets, como experiência de rolagem, botão de pesquisa, filtros de pesquisa aprimorados e muito mais. A lista completa disponível em [AEM Assets](assets.md).

**Brand Portal**

Vários aprimoramentos em áreas de metadados, relatórios, direitos digitais, experiência de logon e desempenho de publicação para distribuição de ativos. Para saber mais sobre os novos aprimoramentos e recursos, consulte [Novidades do Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html)de marcas do AEM Assets.

#### Dynamic Media Add-on {#dynamic-media-add-on}

O AEM 6.4 inclui muitos novos recursos e melhorias para o Dynamic Media. A lista completa está disponível em [AEM Assets](assets.md). Os principais destaques incluem:

**Corte inteligente**

O Smart Crop, desenvolvido pela Adobe Sensei, fornece automaticamente recorte não destrutivo de imagens, preservando o ponto de interesse para um design responsivo. Você pode pré-visualização sugestões de imagens recortadas e ajustá-las manualmente, se necessário. Esse recurso também permite a geração automática de amostras para imagens de produtos.

Consulte a documentação de Perfis [](/help/assets/image-profiles.md) de imagem para saber mais sobre o uso do Smart Crop.

Consulte [Adicionar ativos Dynamic Media às páginas](/help/assets/adding-dynamic-media-assets-to-pages.md) para saber mais sobre como trabalhar com o Smart Crop no componente Dynamic Media.

**Imagem inteligente**

A geração de imagens inteligentes aproveita as características de exibição exclusivas de cada usuário para fornecer automaticamente imagens otimizadas para sua experiência, resultando em melhor desempenho e envolvimento.

Consulte a documentação de [Smart Imaging](/help/assets/imaging-faq.md) para saber mais.

![smart_cut](assets/smart_crop.png)

**Aprimoramentos novos de mídia e visualizador**

Os novos visualizadores, incluindo Panorâmica e VR, permitem que você forneça experiências mais imersivas.

Consulte a documentação Imagens [](/help/assets/panoramic-images.md) panorâmicas para saber mais.

**Ativos 3D**

Nova integração com o [Adobe Dimension CC](https://www.adobe.com/products/dimension.html), um aplicativo Creative Cloud para criar experiências 3D.

Consulte [Trabalhar com a documentação de ativos](/help/assets/assets-3d.md) 3D para saber mais.

![do-not-localize/3d](assets/do-not-localize/3d.png)

### Formulários do Experience Manager {#experience-manager-forms}

O AEM 6.4 Forms traz vários novos recursos e melhorias. Os destaques incluem:

* Comunicações interativas com vários canais
* Preencher previamente comunicações interativas a partir de aplicativos comerciais
* Modernização do fluxo de trabalho e suporte ao trabalhador móvel
* Fragmentos de carregamento lento
* Atualização de hop único do LiveCycle para o Experience Manager Forms 6.4

Mais detalhes sobre a página de notas de versão do [AEM Forms](forms.md) . Also, see the [Summary of new features and enhancements in AEM 6.4 Forms](/help/forms/using/whats-new.md) for information about new and improved features and documentation resources.

### Experience Manager Livefyre {#experience-manager-livefyre}

É possível integrar o Livefyre com sua instância do AEM 6.4. As informações sobre como integrar o Livefyre com o AEM estão localizadas aqui:

* [Integração do Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### Aproveite o desenvolvimento voltado ao cliente {#leverage-customer-focused-development}

A Adobe está usando um modelo de desenvolvimento focado no cliente que permite aos clientes contribuir para todos os estágios do processo de desenvolvimento, durante a especificação, o desenvolvimento e o teste. Agradecemos a todos os clientes e parceiros neste processo.

A Adobe tem os procedimentos e processos estabelecidos para permitir a coleta, priorização e rastreamento de resolução de erros com foco no cliente e desenvolvimento de solicitação de melhoria. The [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/br/contact/enterprise-support.ec.html) is integrated with the Adobe Enhancement &amp; Defect Tracking System. As perguntas do cliente são identificadas e resolvidas pelo Atendimento do cliente sempre que possível. Ao ser dimensionada ao P&amp;D, todas as informações do cliente são coletadas e usada para fins de priorização e relatório. A prioridade é concedida durante o processo de desenvolvimento para problemas de suporte pago e de garantia, além de e aprimoramentos do cliente pago.

Esse processo de priorização gerou a correção de mais de 500 alterações focadas no cliente no AEM 6.4.

## Lista de arquivos que fazem parte da versão {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Quickstart independente: cq-quickstart-6.4.0.jar
* Início rápido do servidor de aplicativos: cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 ou mais recente para vários servidores e plataformas da Web. Consulte link [de](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)download.
* Plug-in for Eclipse IDE. [Read more and download](/help/sites-developing/aem-eclipse.md).

* Extension for Brackets Code Editor. [Read more and download](/help/sites-developing/aem-brackets.md).
* Dependências de Maven/Gradle. Consulte link [de](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)download.

**Sites**

* Componentes principais ([projeto do GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* Implementação de referência We.Retail ([leia mais](/help/sites-developing/we-retail.md))
* Arquétipo de projeto Blueprint (projeto[](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)GitHub)
* Reprodutores do AEM Screens para várias plataformas de destino ([download](https://download.macromedia.com/screens/))
* Modelos de linguagem de conteúdo inteligente. O inglês está pré-instalado - mais idiomas podem ser baixados

   * [Alemão](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Espanhol](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiano](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Francês](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [Ferramenta](/help/sites-developing/dialog-conversion.md) de conversão de diálogo para migrar componentes da interface clássica para o Coral 3

**Assets**

* Aplicativo para desktop Adobe Experience Manager ([leia mais](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) e [baixe](https://docs.adobe.com/content/help/pt-BR/experience-manager-desktop-app/using/release-notes.html))

* Package to add enhanced PDF Rasterizer ([read more](/help/assets/aem-pdf-rasterizer.md) and [download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* Pacote para adicionar suporte de imagem RAW estendido ([leia mais](/help/assets/camera-raw.md))

**Forms**

* Pacotes para recursos do AEM Forms:

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

## Idiomas {#languages}

A interface de usuário está disponível nos idiomas a seguir:

* Inglês
* Alemão
* Francês
* Espanhol
* Italiano
* Português do Brasil
* Japonês
* Chinês simplificado
* Chinês tradicional (suporte limitado)
* Coreano

O Experience Manager 6.4 foi certificado para GB18030-2005 CITS para usar o Padrão de codificação chinês.

## Instalar e atualizar {#install-update}

Consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md) para obter os requisitos de instalação.

Consulte a [documentação de atualização](/help/sites-deploying/upgrade.md) para obter instruções detalhadas.

## Plataformas compatíveis {#supported-platforms}

Consulte a matriz completa de plataformas suportadas, incluída. Nível de suporte nos [Requisitos técnicos do AEM 6.4](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>O Oracle migrou para um modelo de &quot;Suporte de longo prazo&quot; (LTS) dos produtos Oracle Java SE. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). A adobe fornecerá apenas o suporte para versões LTS do Java para executar o AEM na produção. Portanto, o Java 8 é a versão recomendada para usar com o AEM 6.4.

## Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe avalia constantemente as funcionalidades do produto e planeja substituí-las por versões mais potentes, ou decide reimplementar partes selecionadas para serem melhor preparadas para as expectativas ou extensões futuras.

Para o Adobe Experience Manager 6.4, [leia a lista de recursos obsoletos e funcionalidades removidas](deprecated-removed-features.md). A página também contém o pré-anúncio de mudanças em 2019 e um aviso importante para os clientes que atualizam de lançamentos anteriores.

## Listas de alterações detalhadas {#detailed-changes-lists}

[AEM Sites](sites.md)

[Ativos AEM](assets.md)

[AEM Communities](communities-release-notes.md)

[Formulários AEM](forms.md)

[AEM Foundation](wcm-platform.md)

## Problemas conhecidos {#known-issues}

[Lista de problemas conhecidos](known-issues.md)

### Download e suporte ao produto (sites restritos) {#product-download-and-support-restricted-sites}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/).
* Atualizações, patches e pacotes de produtos para funcionalidade adicional na Distribuição [de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)software.
* [Suporte ao cliente via Admin Console](https://adminconsole.adobe.com/). Para obter mais informações, consulte [Nova experiência](https://docs.adobe.com/content/help/en/customer-one/using/home.html)de suporte ao cliente do Adobe.
