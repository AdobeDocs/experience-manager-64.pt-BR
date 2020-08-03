---
title: Notas de versão do AEM Sites
seo-title: AEM Sites
description: Notas de versão específicas do Adobe Experience Manager 6.4 Sites.
seo-description: Notas de versão específicas do Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 13%

---


# AEM Sites Notas de versão {#aem-sites-release-notes}

## Sites {#sites}

Consulte o seguinte para aprimoramentos do AEM Sites 6.4 em detalhes:

### Administração de site {#site-administration}

* Novo painel da Árvore de conteúdo para navegar rapidamente em uma hierarquia de site. Em combinação com a visualização da lista, isso restaura o modelo de interação da interface clássica para navegar em um site.
* Melhoria na rolagem no cartão e na visualização de lista de pastas grandes.
* Interação aprimorada com os resultados da pesquisa - o botão Voltar restaura o resultado da pesquisa anterior.
* Atalhos de teclado adicionais, para as ações mais comuns, como abrir um painel específico, editar, mover e excluir páginas ou abrir propriedades.
* Capacidade de desativar atalhos do teclado (ativar/desativar em Preferências).
* Parar de mostrar carimbos de data e hora em toda a interface do usuário em relação após 7 dias (defina o padrão em Preferências).

### Editor de página {#page-editor}

* Atualização da lista do dispositivo para pré-visualização responsiva do site, agora incluindo Apple iPhone 8, 8 Plus e X e Samsung S7
* O local padrão para informações de design de modelo foi movido de /etc/design para suportar configurações específicas de sites em /conf. Os clientes que atualizam de AEM anteriores podem continuar usando /etc/design.

### Desenvolvimento de componentes e modelos {#component-amp-template-development}

* Project Archetype 13+, consulte [Github para obter as notas](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)de versão.
* HTL versão 1.3.1, consulte o [Github para obter notas de versão](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componentes principais 2.0.4+, consulte o [Github para obter notas de versão](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema de estilos

   * Foi adicionado um novo conceito para atribuir classes CSS aos componentes e permitir que os usuários no Editor de páginas selecionem a partir de um subconjunto de estilos por meio da interface do usuário
   * Adição da capacidade de definir o nome do elemento HTML renderizado ao redor do componente, por exemplo, &lt;main>, &lt;aside>

* Sistema de grade para Contêiner de layout, consulte o [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor de modelo e políticas

   * As políticas agora suportam configurações de Sistema de estilo por componente, por container, por modelo.
   * Suporte aprimorado para a definição de layout em modelos em componentes editáveis

* We.Retail 3.0 de referência do Site, consulte o [Github para obter notas de versão](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM inclui a versão 1.12.4 da biblioteca do jQuery para fornecer compatibilidade máxima com o código personalizado existente. As modificações foram feitas pela Adobe para solucionar problemas de segurança conhecidos.

### Fragmentos de conteúdo e editor {#content-fragments-amp-editor}

* Modelos de conteúdo estruturados introduzidos como base para fragmentos de conteúdo

   * Interface do usuário do editor de modelos
   * Elementos de dados pré-configurados para modelos de fragmento de conteúdo (texto de linha única, texto de várias linhas, número, booleano, data e hora, lista discriminada, referência de conteúdo, tags)

* Aprimoramento da utilização do editor de Fragmento de conteúdo AEM

   * Visão geral da Visualização de todos os elementos
   * Edição em tela cheia para elementos únicos
   * Recursos aprimorados de edição de rich text (listas com marcadores, listas numeradas, recuo, hiperlinks, tabelas, localizar e substituir, verificação ortográfica)

* Adicionadas opções de saída aprimoradas para AEM Fragmentos de conteúdo

   * Novo componente de Fragmento de conteúdo, como parte dos Componentes principais. [Consulte o código no GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Suporte aos Serviços de conteúdo com saída JSON via Sling Model Exporter

### Fragmentos de experiência {#experience-fragments}

* Introduziu os blocos componentes do fragmento de experiência para facilitar a reutilização do conteúdo entre variações de fragmentos de experiência ao agrupar componentes e permitir a fácil referência em variações.
* Adicionada a capacidade de adicionar Fragmentos de experiência a projetos de tradução por meio do painel de referência
* Adicionada a capacidade de start de workflows com Fragmentos de experiência por meio do trilho da linha do tempo
* O painel de referência agora mostra onde um Fragmento de experiência está sendo usado em AEM
* A configuração de locais de modelo agora permite que os autores definam em nível global ou de pasta quais modelos de Fragmento de experiência podem usar
* A pesquisa facetada agora suporta filtragem avançada, como publicada/não publicada, exportada para redes sociais e Adobe Target
* Adição de logon único de mídia social ao exportar Fragmentos de experiência para Pinterest ou Facebook
* Fragmentos de experiência integrados AEM com o Adobe Target. A sincronização dos Fragmentos de experiência com o Público alvo criará ofertas no Adobe Target que podem ser usadas com o Visual Experience Composer do Público alvo para incorporá-lo a qualquer experiência habilitada pelo Público alvo.

### Tradução {#translation}

* Aprimoramento da usabilidade de projetos de tradução AEM:

   * Suporte para vários idiomas de público alvo em um projeto
   * Opção para promover e excluir automaticamente inicializações de tradução
   * Opção para programar a execução recorrente de projetos de tradução (diário, semanal, mensal, anual)
   * Mosaicos de projetos de tradução aprimorados com informações de status mais detalhadas

* Atualização da memória de tradução reversa introduzida para atualizar a memória de tradução no sistema de gerenciamento de tradução de terceiros após as edições de conteúdo local no AEM
* Os workflows de tradução agora suportam raízes de idiomas agrupados
* Foi adicionada a capacidade de atribuir nomes arbitrários a raízes de idioma e usar a propriedade JCR para mapear para código ISO
* As atualizações de tradução inteligente agora reconhecem novas páginas que foram adicionadas a uma ramificação principal de idioma
* relatórios de status de tradução introduzido na visualização de lista de administração do Sites

### Gerenciamento de vários sites (MSM) {#multi-site-management-msm}

* Maior escalabilidade MSM usando um índice baseado em Oak vs na memória (LiveCopyIndex)

### Lançamentos {#launches}

* Desempenho aprimorado de inicializações que contêm uma grande árvore de sites e se houver muitas Inicializações ativas ativas
* Melhoria na promoção automática e na publicação de inicializações com várias páginas raiz.
* Correção de um problema que impedia que a pré-visualização responsiva do dispositivo funcionasse com páginas editadas no contexto de uma inicialização.

### Direcionamento e simulação de conteúdo {#content-targeting-simulation}

* Pastas de suporte para organizar segmentos com base no site/contexto (CQ-94620)
* O local padrão dos segmentos foi movido para /conf para ter listas de segmento específicas do site/contexto.

### AEM &amp; Adobe Target  {#aem-amp-adobe-target-nbsp}

* Fragmentos de experiência integrados AEM com o Adobe Target. A sincronização dos Fragmentos de experiência com o Público alvo criará ofertas no Adobe Target que podem ser usadas com o Visual Experience Composer do Público alvo para incorporá-lo a qualquer experiência habilitada pelo Público alvo.
* Adobe Target mbox.js versão 63 agora incluído. A Adobe recomenda mudar a implementação para at.js.
* at.js versão 1.2.2 agora incluída. O Adobe recomenda usar o Gerenciamento dinâmico de tags (DTM) ou o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para provisionar o at.js no site.

### AEM &amp; Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 agora incluído. O Adobe recomenda mudar a implementação para AppMeasurement.js
* AppMeasurement.js 1.8.0 agora incluído. O Adobe recomenda usar o Gerenciamento dinâmico de tags (DTM) ou o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) para provisionar o AppMeasurement.js no site.

## Complemento do Communities {#communities-add-on}

Consulte a página [Notas de versão do Communities](/help/release-notes/communities-release-notes.md)

## Complemento do Screens {#screens-add-on}

* Adição de suporte para players de telas que se conectam a servidores de publicação AEM para downloads de comando e controle e canais (em vez de diretamente para AEM autor).
* Adição da capacidade de agrupar atribuições de canais em Programações
* As atribuições de Canais agora têm start e data de término
* O Painel do dispositivo agora mostra a shell do player e a versão do firmware
* A lista de Painel do dispositivo mostra o status da conexão do player
* Adicionado suporte do Google Chrome OS para AEM Screens Player
* Adicionado o Microsoft Windows 10 para AEM Screens Player
