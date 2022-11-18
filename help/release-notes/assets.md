---
title: Notas de versão do AEM Assets
seo-title: AEM Assets
description: Notas de versão específicas dos ativos Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 2%

---

# Notas de versão do AEM Assets {#aem-assets-release-notes}

Os principais recursos, destaques e aprimoramentos feitos no AEM 6.4 Assets são abordados nas notas de versão. Para obter informações detalhadas, siga os links fornecidos.

## Adobe Asset Link {#adobe-asset-link}

O Adobe Asset Link no Creative Cloud for enterprise simplifica a colaboração entre criadores e profissionais de marketing no processo de criação de conteúdo. É um novo recurso nativo no Creative Cloud para empresas, que fornece uma conexão com o AEM Assets diretamente da Adobe Photoshop, Adobe Illustrator ou Adobe InDesign, sem deixar essas ferramentas.

Para saber mais sobre o recurso, os pré-requisitos e como acessá-lo, consulte o [Adobe Asset Link](https://helpx.adobe.com/br/enterprise/using/adobe-asset-link.html) página.

## Tags inteligentes aprimoradas (viabilizadas pelo Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

O AEM 6.4 apresenta o recurso de Tags inteligentes aprimoradas com base em inteligência artificial, além das Tags inteligentes que foram lançadas no AEM 6.3.

* O Serviço de conteúdo inteligente aprende a taxonomia comercial do cliente e a usa para marcar ativos digitais automaticamente com tags relevantes do cliente, além de tags genéricas. Melhora significativamente a capacidade de descoberta de ativos e reduz o tempo de comercialização.
* O Adobe Sensei capacita o Serviço de conteúdo inteligente, que permite que você treine o algoritmo de reconhecimento de imagem em sua taxonomia comercial. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em ativos semelhantes.

Para usar as Tags inteligentes aprimoradas do AEM Assets, instale o [service pack mais recente do AEM 6.4](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html).

## Pesquisa de tradução inteligente (fornecida pelo Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

O AEM 6.4 apresenta o recurso Pesquisa de tradução inteligente para oferecer suporte a cenários de pesquisa multilíngues. Clientes com equipes distribuídas globalmente em várias localidades agora têm acesso à pesquisa em diferentes idiomas sem precisar passar por fluxos de trabalho de tradução dispendiosos e demorados.

* A consulta de pesquisa é traduzida sem intervenção manual.
* As Tags inteligentes são geradas em inglês e são traduzidas por máquina para outros idiomas.
* A pesquisa multilíngue é criada usando a biblioteca de código aberto Apache Joshua, que oferece suporte a mais de 50 idiomas.

## Experiência do usuário {#user-experience}

O AEM 6.4 oferece aprimoramentos significativos à experiência do usuário em áreas de navegação, pesquisa, ativos de várias páginas e ferramentas de administração. Detalhes abaixo:

Melhorias na navegação

* Novo painel Árvore de conteúdo para navegar rapidamente por uma hierarquia de ativos. Em combinação com a exibição em lista, isso restaura o modelo de interação da interface clássica para navegar pelas hierarquias de ativos.
* Novos atalhos de teclado, como m para mover ativos, p para abrir a página de propriedades, Ctrl + C para copiar a operação e muito mais.
* Melhoria na rolagem e na experiência de carregamento lento na exibição de cartão e lista para a navegação de um grande número de ativos.
* Melhoria na exibição de cartão com suporte para diferentes cartões de tamanho com base na configuração da exibição.
* Melhoria na experiência de detalhes do ativo com a capacidade de visualizar, navegar até o ativo &quot;anterior&quot; ou &quot;próximo&quot;, juntamente com o número de ativos, o ativo atual.

Melhorias na pesquisa

* Novo botão Pesquisar de volta com a capacidade de navegar para um item de pesquisa e voltar à mesma posição nos resultados da pesquisa sem executar a consulta de pesquisa novamente.
* Novos resultados da pesquisa contam para exibir o número de resultados da pesquisa.
* Filtro de pesquisa do tipo de arquivo aprimorado com capacidade de filtrar resultados de pesquisa com base em tipos MIME refinados, como JPG, PNG e PSD, em comparação às opções anteriores de imagem, documento, multimídia.
* Filtros de pesquisa aprimorados com carimbos de data e hora precisos em vez da funcionalidade de controle deslizante de hora anterior.

Aprimoramentos de ativos de várias páginas

* Melhoria na experiência de navegação de ativos de várias páginas com um número reduzido de cliques.
* Suporte aprimorado a comentários e anotações com todos eles agrupados no nível do ativo em vez de na página.

Melhorias nas ferramentas administrativas

* O seletor de propriedades foi aprimorado nas ferramentas de administração para Metadados, Pesquisa e relatórios com Tipo com antecedência e capacidade de navegação para simplificar a experiência de administração.

Catálogos

* Melhoria na experiência do usuário, alinhamento com a interface do usuário de Modelos . Para obter mais informações, consulte [Produtor do Catálogo](../sites-administering/catalog-producer.md).

## Metadados {#metadata}

O AEM 6.4 inclui vários recursos avançados de gerenciamento de metadados para gerenciar metadados em escala e reforçar a integridade dos metadados por meio de regras e validações. Estes são os principais recursos:

* Novo recurso de Exportação de metadados em massa para exportar (tudo, seletivo) metadados para um grande número de ativos no formato CSV para edição, compartilhamento e integração de terceiros.
* Novo recurso de importação de metadados em massa para importar arquivo CSV para adicionar novos metadados, atualizando os metadados existentes para vários ativos de uma só vez. Essa operação é assíncrona e não dificulta o desempenho do sistema. Depois de concluído, o usuário é notificado por meio AEM sistema de notificação.
* Novos metadados em cascata e contextuais usando a ferramenta Esquema de metadados. Agora é possível definir cadeias de dependências e mapeamentos de valor entre campos. Você também pode definir o contexto em que os campos de formulário de metadados são exibidos/ocultos. Dessa forma, você pode exibir apenas campos relevantes a qualquer momento, dependendo dos valores em outros campos.

## Relatórios {#reports}

O AEM 6.4 oferece aprimoramentos significativos no relatório de Ativos:

* Nova estrutura de relatórios escalável e de nível empresarial (para repositórios grandes) que aplica trabalhos do Sling para processar solicitações de relatório de forma assíncrona. Você pode programar um relatório em uma data e hora específicas. Você também pode adicionar colunas personalizadas a um relatório.
* Novos relatórios OOTB mais comumente solicitados pelos clientes, como Uso de disco, Arquivos, Compartilhamentos de link, Publicar no Brand Portal e Treinamento em Tags inteligentes.
* Nova interface de criação e gerenciamento de relatórios com opções otimizadas, capacidade de acessar relatórios arquivados, consulte o status de execução do relatório (sucesso, falha, enfileiramento e assim por diante).

## Brand Portal {#brand-portal}

* **Atualização da plataforma 6.3**: O Brand Portal foi atualizado do AEM 6.0 para o AEM 6.3, com novos recursos e melhorias de desempenho.
* **Publicação paralela**: Até replicações podem ocorrer entre o AEM Assets e o Brand Portal (anteriormente 1), o que melhora significativamente o desempenho da publicação
* **Publicação de Aspecto de Esquema e Pesquisa**: Capacidade de publicar esquemas de metadados e aspectos de pesquisa personalizados no Brand Portal, o que elimina a duplicação de esforços.
* **Publicação de tags em massa**: Capacidade de publicar taxonomia (junto com hierarquia) no Brand Portal, o que elimina a duplicação de esforços.
* **Autoassinatura ou Solicitar acesso**: Fluxo de trabalho para usuários não registrados no Brand Portal.
* **Notificação de manutenção no aplicativo (na tela)**: As notificações são exibidas com bastante antecedência para evitar interrupção nos negócios.
* **Melhorias nos relatórios**: Três relatórios OOTB estão disponíveis: downloads, publicação e compartilhamentos de link.
* **Restrições baseadas em DRM**: Depois que um ativo licenciado expira, ele não está mais disponível para download na Brand Portal.

## Aplicativo de desktop do AEM {#aem-desktop-app}

AEM aplicativo de desktop é atualizado para a versão 1.8, que é compatível com a AEM 6.4. A lista completa de alterações para AEM aplicativo de desktop é fornecida em um aplicativo dedicado [Notas de versão do aplicativo de desktop do AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) documento.\
Esta é uma lista de AEM destaques do aplicativo de desktop desde o lançamento do AEM 6.3:

* Capacidade de fazer upload de pastas hierárquicas em segundo plano.
* Interface do usuário para monitorar os uploads de ativos em segundo plano.
* Melhorias no cache, incluindo uma interface do usuário para gerenciar parâmetros de cache.
* Suporte mais amplo para configurações de autenticação de AEM (SAML/SSO) e proxy de rede.
* Suporte: acesso fácil a registros a partir da interface do usuário.
* Melhora da estabilidade e correções para problemas dos clientes.

Para facilitar o acesso à documentação e às práticas recomendadas, a seguinte documentação está disponível:

* [Guia do usuário](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html), destinado aos usuários finais que trabalham com o aplicativo.
* [Guia de instalação](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/install-upgrade.html)destinado aos administradores que configuram AEM e AEM aplicativo de desktop para trabalhar em conjunto

## Armazenamento hierárquico {#tiered-storage}

O AEM 6.4 inclui um conjunto de recursos que oferecem suporte a várias preferências de armazenamento hierárquico e implementam regras de ciclo de vida. As opções de armazenamento também suportam (mas não são limitadas) nuvens públicas - AWS ou Azure.

* A capacidade de os usuários selecionarem e alterarem posteriormente a classe de armazenamento à vontade e definirem regras para o armazenamento de ativos de uma classe para outra ou gerenciarem o ciclo de vida de seus ativos.
* A capacidade de os usuários reduzirem seus custos de armazenamento selecionando um AWS ou Azure diferente.

Para obter uma visão geral das plataformas compatíveis, consulte a seção [Documentação de requisitos técnicos](../sites-deploying/technical-requirements.md).

## Grupo de usuário fechado {#closed-user-group}

* No AEM 6.4, Closed User Group ou CUG fornece uma maneira de restringir o acesso à pasta na instância de publicação, é uma opção da interface do usuário de toque adicionar entidades por meio da página de propriedades da pasta no nível da pasta e são aplicadas a todas as pastas e subpastas/ativos dentro dela.
* No modo de publicação, se um CUG estiver configurado e a autorização estiver ativada em uma pasta, os usuários serão redirecionados para uma página de logon quando tentarem acessar a pasta. Portanto, os usuários autorizados podem acessar a pasta e seus ativos somente após o logon bem-sucedido. Portanto, o CUG restringe o acesso de leitura a uma determinada árvore no repositório de conteúdo para todos, exceto entidades selecionadas.

## Complemento do Dynamic Media {#dynamic-media-add-on}

O Dynamic Media na 6.4 é compatível com um novo modo - onde o ativo principal é carregado e gerenciado com a interface do usuário da Web do AEM Assets, e as representações dinâmicas e outros recursos de mídia dinâmica são manipuladas em segundo plano pelo serviço de entrega da nuvem do Dynamic Media.

Nesse modo (introduzido primeiro com o lançamento de [AEM 6.3 Pacotes de recursos 14410 e 18912](https://helpx.adobe.com/br/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), os usuários se beneficiam do gerenciamento completo de ativos e dos recursos de mídia dinâmica usando a interface moderna da Web do AEM Assets e ainda aproveitam os serviços de delivery que são compatíveis com o Dynamic Media Classic (Scene7), incluindo URLs de entrega, que permanecem inalterados.

Além disso, o AEM 6.4 apresenta novos recursos fornecidos pelo Adobe Sensei, melhorias para mídia emergente, como VR e 3D, visualizadores Dynamic Media e suporte para Fragmentos de experiência em imagens interativas e banners de carrossel.

### Recorte inteligente (fornecido pela Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* O Recorte inteligente fornece automaticamente recortes não destrutivos de imagens para preservar o ponto de interesse para um design responsivo. Você pode visualizar sugestões cortadas e ajustá-las manualmente, se necessário.
* Esse recurso também permite a geração automatizada de amostras para imagens de produtos. A geração automatizada de amostras ajuda a adicionar amostras de cores, amostras de padrões ou ambas a imagens de produtos automaticamente.

Consulte [Perfis de imagem](../assets/image-profiles.md) documentação para saber mais.

Consulte também [Adicionar ativos Dynamic Media às páginas](../assets/adding-dynamic-media-assets-to-pages.md) documentação para saber mais sobre como usar o Recorte inteligente com o componente do Dynamic Media.

### Imagem inteligente {#smart-imaging}

* A geração de imagens inteligentes aproveita as características de exibição exclusivas de cada usuário para fornecer automaticamente imagens otimizadas para sua experiência, resultando em melhor desempenho e envolvimento.
* As imagens são convertidas automaticamente em diferentes formatos com base nos recursos do navegador.
* As configurações de qualidade da imagem são determinadas no navegador e aplicadas respectivamente. Essa inteligência mantém o desempenho de carregamento de imagem aceitável para largura de banda limitada e velocidades de conexão lentas.

Consulte [Imagem inteligente](../assets/imaging-faq.md) documentação para saber mais.

### Melhorias emergentes de mídia e visualizador {#emerging-media-amp-viewer-enhancements}

* Novos visualizadores são compatíveis, fornecendo experiências melhores e imersivas para o usuário.
* O Visualizador de panorâmica ajuda a envolver o usuário e a oferecer a capacidade de experimentar melhor as cenas, propriedades, locais e paisagens da sala. Consulte [Imagens panorâmicas](../assets/panoramic-images.md) documentação para aprender.

* O Visualizador VR fornece experiência imersiva para propriedades, locais e paisagens.
* Visualizador de imagem vertical otimizado para imagens de produto.
* Melhorias na acessibilidade do teclado.
