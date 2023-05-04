---
title: Notas de versão da AEM Sites
seo-title: AEM Sites
description: Notas de versão específicas do Adobe Experience Manager 6.4 Sites.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# Notas de versão da AEM Sites {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sites {#sites}

Veja o seguinte para as melhorias do AEM Sites 6.4 em detalhes:

### Administração do site {#site-administration}

* Novo painel Árvore de conteúdo para navegar rapidamente por uma hierarquia de site. Em combinação com a exibição em lista, isso restaura o modelo de interação da interface clássica para navegar em um site.
* Melhoria na rolagem na exibição de cartão e lista de pastas grandes.
* Interação aprimorada com os resultados da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* Atalhos adicionais do teclado, para as ações mais comuns, como abrir um painel específico, editar, mover e excluir páginas ou abrir propriedades.
* Capacidade de desativar atalhos do teclado (ativar/desativar em Preferências).
* Parar de mostrar carimbos de data e hora em toda a interface do usuário em relação após 7 dias (defina o padrão em Preferências).

### Editor de página {#page-editor}

* Lista de dispositivos atualizada para visualização responsiva do site, incluindo Apple iPhone 8, 8 Plus e X, e Samsung S7.
* O local padrão para informações de design de modelo foi movido de /etc/design para oferecer suporte a configurações específicas de sites em /conf. Os clientes que atualizam de versões anteriores do AEM podem continuar usando o /etc/design.

### Desenvolvimento de componentes e modelos {#component-amp-template-development}

* Arquétipo de projeto 13+, consulte [Github para notas de versão](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL versão 1.3.1, consulte [Github para notas de versão](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componentes principais 2.0.4+, consulte [Github para notas de versão](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema de estilos

   * Adição de um conceito totalmente novo para atribuir classes CSS a componentes e permitir que os usuários no Editor de páginas selecionem de um subconjunto de estilos por meio da interface do usuário
   * Adição da capacidade de definir o nome do elemento HTML renderizado em torno do componente, por exemplo &lt;main>, &lt;aside>

* Sistema de grade para Contêiner de layout, consulte [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor e políticas de modelos

   * As políticas agora oferecem suporte às configurações do Sistema de estilos por componente, por contêiner, por modelo.
   * Suporte aprimorado para definir o layout em modelos em componentes editáveis

* We.Retail 3.0 de referência do site, consulte [Github para notas de versão](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM inclui a versão 1.12.4 da biblioteca jQuery para fornecer compatibilidade máxima com o código personalizado existente. As modificações foram feitas pelo Adobe para solucionar problemas de segurança conhecidos.

### Fragmentos de conteúdo e editor {#content-fragments-amp-editor}

* Introdução aos Modelos de conteúdo estruturado como base para fragmentos de conteúdo

   * Interface do usuário do editor de modelos
   * Elementos de dados pré-configurados para modelos de fragmento de conteúdo (texto de linha única, texto de várias linhas, número, booleano, data&amp;hora, enumeração, referência de conteúdo, tags)

* Aprimoramento da usabilidade do editor de Fragmento de conteúdo do AEM

   * Visão geral de todos os elementos
   * Edição em tela cheia de elementos únicos
   * Recursos aprimorados de edição de rich text (listas com marcadores, listas numeradas, recuo, hiperlinks, tabelas, localizar e substituir, verificação ortográfica)

* Adicionadas opções aprimoradas de saída para Fragmentos de conteúdo AEM

   * Novo componente Fragmento de conteúdo , como parte dos Componentes principais. [Consulte o código no GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Suporte a serviços de conteúdo com saída JSON por meio do exportador do Modelo Sling

### Fragmentos de experiência {#experience-fragments}

* Introdução aos blocos de construção do fragmento de experiência para facilitar o reuso do conteúdo entre variações dos fragmentos de experiência, agrupando componentes e permitindo a fácil referência em variações.
* Adição da capacidade de adicionar Fragmentos de experiência a projetos de tradução por meio do painel de referência
* Adição da capacidade de iniciar fluxos de trabalho com Fragmentos de experiência por meio do painel da linha do tempo
* O painel de referência agora mostra onde um Fragmento de experiência está sendo usado em AEM
* A configuração de locais de modelo agora permite que os autores definam em nível global ou de pasta quais modelos de Fragmento de experiência podem usar
* A pesquisa de faceta agora oferece suporte à filtragem avançada, como publicada/não publicada, exportada para redes sociais e Adobe Target
* Adição de logon único de mídia social ao exportar Fragmentos de experiência para o Pinterest ou Facebook
* Fragmentos de experiência AEM integrados com o Adobe Target. A sincronização dos Fragmentos de experiência com o Target criará ofertas no Adobe Target que podem ser usadas com o Visual Experience Composer do Target para incorporá-las a qualquer experiência habilitada pelo Target.

### Tradução {#translation}

* Aprimoramento da usabilidade de projetos de Tradução AEM:

   * Suporte para vários idiomas de destino em um projeto
   * Opção para promover e excluir automaticamente lançamentos de tradução
   * Opção para programar a execução recorrente de projetos de tradução (diário, semanal, mensal, anual)
   * Mosaicos de projetos de tradução aprimorados com informações de status mais detalhadas

* Introdução da atualização da memória de tradução reversa, para atualizar a memória de tradução no sistema de gerenciamento de tradução de terceiros após as edições de conteúdo local no AEM
* Os workflows de tradução agora oferecem suporte a raízes de idioma agrupadas
* Adição da capacidade de atribuir nomes arbitrários às raízes de idioma e usar a propriedade JCR para mapear para código ISO
* As atualizações de tradução inteligente agora reconhecem novas páginas que foram adicionadas a uma ramificação principal de idioma
* Introdução do relatório de status de tradução na exibição da lista de administração do Sites

### Gerenciamento de vários sites (MSM) {#multi-site-management-msm}

* Melhoria na escalabilidade do MSM usando um índice baseado em Oak vs na memória (LiveCopyIndex)

### Lançamentos {#launches}

* Melhoria no desempenho de inicializações que contêm árvore de site grande e se houver muitas Inicializações ativas
* Melhoria na promoção automática e na publicação de inicializações com várias páginas raiz.
* Correção de um problema que impedia que a visualização responsiva do dispositivo funcionasse com páginas editadas no contexto de um lançamento.

### Direcionamento e simulação de conteúdo {#content-targeting-simulation}

* Pastas de suporte para organizar segmentos com base no site/contexto (CQ-94620)
* O local padrão dos segmentos foi movido para /conf para ter listas de segmentos específicas de site/contexto.

### AEM e Adobe Target  {#aem-amp-adobe-target-nbsp}

* Fragmentos de experiência AEM integrados com o Adobe Target. A sincronização dos Fragmentos de experiência com o Target criará ofertas no Adobe Target que podem ser usadas com o Visual Experience Composer do Target para incorporá-las a qualquer experiência habilitada pelo Target.
* A mbox.js do Adobe Target versão 63 agora está incluída. O Adobe recomenda alternar a implementação para at.js.
* A at.js versão 1.2.2 agora está incluída. O Adobe recomenda usar o Dynamic Tag Management (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para provisionar a at.js no site.

### AEM e Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 agora incluído. O Adobe recomenda alternar a implementação para AppMeasurement.js
* AppMeasurement.js 1.8.0 agora incluído. O Adobe recomenda usar o Dynamic Tag Management (DTM) ou [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para provisionar o AppMeasurement.js no site.

## Complemento do Communities {#communities-add-on}

Consulte [Página Notas de versão do Comunidades](/help/release-notes/communities-release-notes.md)

## Complemento do Screens {#screens-add-on}

* Adição de suporte para que os Players do Screens se conectem a servidores de publicação AEM para comando e controle e downloads de canal (em vez de diretamente AEM autor).
* Adição da capacidade de agrupar atribuições de canal em Agendamentos
* As atribuições de canal agora têm data inicial e final
* O Painel do dispositivo agora mostra o shell do reprodutor e a versão do firmware
* Lista Painel do dispositivo mostra o status da conexão do reprodutor
* Adição do suporte ao sistema operacional Google Chrome para o AEM Screens Player
* Adição do Microsoft Windows 10 para AEM Screens Player
