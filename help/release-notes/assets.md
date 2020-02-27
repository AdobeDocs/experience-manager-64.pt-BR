---
title: Notas de versão do AEM Assets
seo-title: Ativos AEM
description: Notas de versão específicas dos ativos Adobe Experience Manager 6.4.
seo-description: Notas de versão específicas dos ativos Adobe Experience Manager 6.4.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: 2411f1aa2853a161603d15917102d5cf1a8139b6

---


# Notas de versão do AEM Assets {#aem-assets-release-notes}

Os principais recursos, destaques e aprimoramentos feitos nos ativos AEM 6.4 são abordados nessas notas de versão. Para obter informações detalhadas, siga os links fornecidos.

## Adobe Asset Link {#adobe-asset-link}

O Adobe Asset Link na Creative Cloud para empresas simplifica a colaboração entre criadores e comerciantes no processo de criação de conteúdo. É um novo recurso nativo na Creative Cloud para empresas, que fornece uma conexão aos ativos AEM diretamente do Adobe Photoshop, Adobe Illustrator ou Adobe InDesign. sem deixar essas ferramentas.

Para saber mais sobre o recurso, os pré-requisitos e como acessá-lo, consulte a página [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) .

## Tags inteligentes aprimoradas (fornecidas pelo Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

O AEM 6.4 apresenta o recurso de Tags inteligentes aprimoradas baseadas em inteligência artificial, além das Tags inteligentes que foram lançadas no AEM 6.3.

* O Smart Content Service aprende a taxonomia comercial do cliente e a usa para marcar automaticamente ativos digitais com tags relevantes para o cliente, além de tags genéricas. Melhora significativamente a descoberta de ativos e reduz o tempo de comercialização.
* O Adobe Sensei capacita o Serviço de conteúdo inteligente, que permite que você treine o algoritmo de reconhecimento de imagem na taxonomia de sua empresa. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em ativos semelhantes.

Para usar Tags inteligentes aprimoradas do AEM Assets, instale o service pack [mais recente do AEM 6.4](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

## Pesquisa de tradução inteligente (capacitada pelo Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

O AEM 6.4 apresenta a capacidade de pesquisa de tradução inteligente para suportar cenários de pesquisa multilíngues. Clientes com equipes distribuídas globalmente em várias localidades agora têm acesso à pesquisa em diferentes idiomas sem precisar passar por fluxos de trabalho de tradução dispendiosos e demorados.

* A consulta de pesquisa é traduzida sem intervenção manual.
* As Tags inteligentes são geradas em inglês e são traduzidas por computador para outros idiomas.
* A pesquisa multilíngue é criada usando a biblioteca de código aberto Apache Joshua, que suporta mais de 50 idiomas.

## Experiência do usuário {#user-experience}

O AEM 6.4 oferece melhorias significativas na experiência do usuário em áreas de navegação, pesquisa, ativos de várias páginas e ferramentas administrativas. Detalhes abaixo:

Aprimoramentos de navegação

* Novo painel Árvore de conteúdo para navegar rapidamente em uma hierarquia de ativos. Em combinação com a exibição de lista, isso restaura o modelo de interação da interface clássica para navegar pelas hierarquias de ativos.
* Novos atalhos de teclado, como m para mover ativos, p para abrir a página de propriedades, Ctrl + C para copiar a operação e muito mais.
* Experiência de rolagem aprimorada e carregamento lento no cartão e exibição de lista para navegar em um grande número de ativos.
* Aprimoramento da exibição de cartão com suporte para diferentes cartões de tamanho com base na configuração de exibição.
* Experiência de detalhes de ativos aprimorada com capacidade de visualizar, navegar até o ativo &quot;anterior&quot; ou &quot;próximo&quot; junto com o número de ativos, o ativo atual.

Aprimoramentos de pesquisa

* Novo botão Pesquisar novamente com a capacidade de navegar até um item de pesquisa e voltar à mesma posição nos resultados da pesquisa sem executar a consulta de pesquisa novamente.
* Os novos resultados da pesquisa contam para exibir o número de resultados da pesquisa.
* O Filtro de pesquisa de tipo de arquivo foi aprimorado com a capacidade de filtrar os resultados da pesquisa com base em tipos MIME refinados, como JPG, PNG e PSD, em comparação com as opções anteriores de imagem, documento e multimídia.
* Filtros de pesquisa aprimorados com carimbos de data e hora precisos em vez da funcionalidade do controle deslizante de hora anterior.

Melhorias nos ativos de várias páginas

* Experiência de navegação de ativos de várias páginas aprimorada com um número reduzido de cliques.
* Suporte aprimorado a comentários e anotações com todos eles agrupados no nível do ativo em vez de na página.

Melhorias nas ferramentas administrativas

* Aprimorado o Seletor de propriedades nas ferramentas administrativas para Metadados, Pesquisa e Relatórios com o Tipo à frente e capacidade de navegação para simplificar a experiência do administrador.

Catálogos

* Experiência do usuário aprimorada, alinhamento com a interface do usuário Modelos. Para obter mais informações, consulte [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadados {#metadata}

O AEM 6.4 inclui vários recursos avançados de gerenciamento de metadados para gerenciar metadados em escala e impor a integridade dos metadados por meio de regras e validações. Estes são os principais recursos:

* Novo recurso de Exportação de metadados em massa para exportar (todos, seletivos) metadados para um grande número de ativos no formato CSV para edição, compartilhamento e integração de terceiros.
* Novo recurso de importação de metadados em massa para importar um arquivo CSV para adicionar novos metadados, atualizando os metadados existentes para vários ativos de uma só vez. Esta operação é assíncrona e não prejudica o desempenho do sistema. Após a conclusão, o usuário é notificado pelo sistema de notificação do AEM.
* Novos metadados em cascata e contextuais usando a ferramenta Esquema de metadados. Agora é possível definir cadeias de dependências e mapeamentos de valor entre campos. Também é possível definir o contexto no qual os campos do formulário de metadados são exibidos/ocultos. Dessa forma, você pode exibir somente campos relevantes a qualquer momento, dependendo dos valores em outros campos.

## Relatórios {#reports}

O AEM 6.4 oferece melhorias significativas nos relatórios de ativos:

* Nova estrutura de relatórios dimensionável e de nível empresarial (para repositórios grandes) que aplica jobs Sling para processamento assíncrono de solicitações de relatório. Você pode agendar um relatório em uma data e hora específicas. Você também pode adicionar colunas personalizadas a um relatório.
* Novos relatórios OOTB mais comumente solicitados por clientes, como Uso de disco, Arquivos, Compartilhamentos de link, Publicar no Portal de marca e Treinamento em Tags inteligentes.
* Nova interface de usuário de criação e gerenciamento de relatórios com opções de granulação fina, capacidade de acessar relatórios arquivados, ver o status de execução do relatório (sucesso, falha, enfileiramento e assim por diante).

## Brand Portal {#brand-portal}

* **6.3 Atualização** da plataforma: O Brand Portal foi atualizado do AEM 6.0 para o AEM 6.3, com novos recursos e melhorias de desempenho.
* **Publicação** paralela: Até replicações podem ocorrer entre os ativos AEM e o Portal de marcas (anteriormente 1), o que melhora significativamente o desempenho da publicação
* **Publicação** de Aspectos de Esquema e Pesquisa: Capacidade de publicar esquemas de metadados e aspectos de pesquisa personalizados no Brand Portal, o que elimina a duplicação de esforços.
* **Publicação** de tags em massa: Capacidade de publicar taxonomia (junto com hierarquia) no Brand Portal, o que elimina a duplicação de esforços.
* **Autoinscrição ou acesso** de solicitação: Fluxo de trabalho para usuários não registrados no Brand Portal.
* **Notificação** de manutenção no aplicativo (na tela): As notificações são exibidas com bastante antecedência para evitar interrupções nos negócios.
* **Melhorias** nos relatórios: Três relatórios OOTB estão disponíveis: baixa, publica e compartilha de links.
* **Restrições** baseadas em DRM: Depois que um ativo licenciado expira, ele não está mais disponível para download no Portal da Marca.

## Aplicativo de desktop do AEM {#aem-desktop-app}

O aplicativo de desktop AEM é atualizado para a versão 1.8, que é compatível com o AEM 6.4. A lista completa de alterações para o aplicativo de desktop do AEM é fornecida em um documento dedicado de notas [de versão do aplicativo de desktop do](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html) AEM.\
Esta é uma lista de destaques do aplicativo de desktop do AEM desde que o AEM 6.3 foi lançado:

* Capacidade de carregar pastas hierárquicas em segundo plano.
* IU para monitorar os uploads de ativos em segundo plano.
* Melhorias no cache, incluindo uma interface para gerenciar parâmetros de cache.
* Suporte mais amplo para configurações de autenticação do AEM (SAML/SSO) e proxy de rede.
* Suporte: fácil acesso aos registros da interface do usuário.
* Estabilidade e correções aprimoradas para problemas do cliente.

Para facilitar o acesso à documentação e às práticas recomendadas, a seguinte documentação está disponível:

* [Guia](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)do usuário, destinado aos usuários finais que trabalham com o aplicativo
* [Guia](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)de práticas recomendadas, destinado aos usuários finais e administradores
* [Guia](https://helpx.adobe.com/experience-manager/desktop-app/install-configure-aem-desktop-app.html)de instalação, destinado aos administradores que configuram o aplicativo de desktop AEM e AEM para trabalhar em conjunto

## Armazenamento hierárquico {#tiered-storage}

O AEM 6.4 inclui um conjunto de recursos que oferecem suporte a várias preferências de armazenamento hierárquico e implementam regras de ciclo de vida. As opções de armazenamento também suportam (mas não são limitadas) nuvens públicas - AWS ou Azure.

* A capacidade de os usuários selecionarem e alterarem posteriormente a classe de armazenamento à vontade e definirem regras para o armazenamento de ativos de uma classe para outra ou gerenciarem o ciclo de vida de seus ativos.
* A capacidade de os usuários reduzirem seus custos de armazenamento selecionando um AWS ou Azure diferente.

Para obter uma visão geral das plataformas suportadas, consulte a Documentação [dos requisitos](../sites-deploying/technical-requirements.md)técnicos.

## Grupo de usuário fechado {#closed-user-group}

* No AEM 6.4, Closed User Group ou CUG fornece uma maneira de restringir o acesso da pasta na instância de publicação, é uma opção de interface de toque para adicionar principais por meio da página de propriedades da pasta no nível da pasta e são aplicados a todas as pastas e subpastas/ativos dentro dela.
* No modo de publicação, se um CUG estiver configurado e a autorização estiver ativada em uma pasta, os usuários serão redirecionados para uma página de logon quando tentarem acessar a pasta. Portanto, os usuários autorizados podem acessar a pasta e seus ativos somente após o login bem-sucedido. Portanto, o CUG restringe o acesso de leitura a uma determinada árvore no repositório de conteúdo para todos, exceto os principais selecionados.

## Dynamic Media add-on {#dynamic-media-add-on}

O Dynamic Media na versão 6.4 é compatível com um novo modo - onde o ativo mestre é carregado e gerenciado com a interface do usuário da Web do AEM Assets, e as representações dinâmicas e outros recursos de mídia dinâmica são manipulados em segundo plano pelo serviço de entrega do Dynamic Media Cloud.

Nesse modo (introduzido primeiro com o lançamento do [AEM 6.3 Feature Packs 14410 e 18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), os usuários se beneficiam do gerenciamento de ativos completo e dos recursos de mídia dinâmica usando a interface moderna da Web do AEM Assets e ainda aproveitam os serviços de entrega que são compatíveis com o Dynamic Media Classic (Scene7) — incluindo URLs de entrega, que são inalterado.

Além disso, o AEM 6.4 apresenta novos recursos capacitados pelo Adobe Sensei, melhorias para mídias emergentes como VR e 3D, visualizadores de Mídia dinâmica e suporte para Fragmentos de experiência em imagens interativas e banners de carrossel.

### Recorte inteligente (desenvolvido pelo Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* O Smart Crop fornece automaticamente recorte não destrutivo de imagens para preservar o ponto de interesse do design responsivo. Você pode visualizar as sugestões recortadas e ajustá-las manualmente, se necessário.
* Esse recurso também permite a geração automática de amostras para imagens de produtos. A geração automatizada de amostras ajuda a adicionar amostras de cores, amostras de padrões ou ambas automaticamente às imagens do produto.

Consulte a documentação Perfis [de](../assets/image-profiles.md) imagem para saber mais.

Consulte também a documentação [Adicionar ativos de mídia dinâmica a páginas](../assets/adding-dynamic-media-assets-to-pages.md) para saber mais sobre o uso do Smart Crop com o componente de Mídia dinâmica.

### Imagem inteligente {#smart-imaging}

* A geração de imagens inteligentes aproveita as características de exibição exclusivas de cada usuário para fornecer automaticamente imagens otimizadas para sua experiência, resultando em melhor desempenho e envolvimento.
* As imagens são convertidas automaticamente em formatos diferentes com base nos recursos do navegador.
* As configurações de qualidade de imagem são determinadas no navegador e aplicadas respectivamente. Essa inteligência mantém o desempenho de carregamento de imagem aceitável para largura de banda limitada e velocidades de conexão lentas.

Consulte a documentação de [Smart Imaging](../assets/imaging-faq.md) para saber mais.

### Aprimoramentos de mídia e visualizador emergentes {#emerging-media-amp-viewer-enhancements}

* Novos visualizadores são suportados, proporcionando experiências melhores e imersivas para o usuário.
* O Visualizador panorâmico ajuda a envolver o usuário e a oferecer a capacidade de experimentar melhor cenas, propriedades, locais e paisagens da sala. Consulte a documentação Imagens [](../assets/panoramic-images.md) panorâmicas para saber mais.

* O VR Viewer fornece experiência imersiva para propriedades, locais e paisagens.
* Visualizador de imagem vertical otimizado para imagens de produto.
* Melhorias na acessibilidade do teclado.

### 3D e integração com o Dimension CC {#d-and-integration-with-dimension-cc}

A integração com o [Adobe Dimension CC](https://www.adobe.com/products/dimension.html) para um fluxo de trabalho 3D mais integrado foi introduzida. Para saber mais, consulte [Trabalhar com a documentação de ativos](../assets/assets-3d.md) 3D.