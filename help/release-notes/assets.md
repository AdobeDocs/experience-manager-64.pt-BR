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
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 2%

---


# Notas de versão do AEM Assets {#aem-assets-release-notes}

Os principais recursos, destaques e aprimoramentos feitos nos ativos AEM 6.4 são abordados nessas notas de versão. Para obter informações detalhadas, siga os links fornecidos.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link no Creative Cloud para empresas simplifica a colaboração entre criativos e profissionais de marketing no processo de criação de conteúdo. É um novo recurso nativo no Creative Cloud para empresas, que fornece uma conexão para AEM Assets diretamente da Adobe Photoshop, Adobe Illustrator ou Adobe InDesign. sem deixar essas ferramentas.

Para saber mais sobre o recurso, os pré-requisitos e como acessá-lo, consulte a página Link [do ativo do](https://helpx.adobe.com/br/enterprise/using/adobe-asset-link.html) Adobe.

## Tags inteligentes aprimoradas (fornecidas pela Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 apresenta o recurso de Tags inteligentes aprimoradas com base em inteligência artificial, além das Tags inteligentes lançadas no AEM 6.3.

* Smart Content Service learns customer&#39;s business taxonomy and uses it to automatically tag digital assets with customer relevant tags in addition to generic tags. Melhora significativamente a descoberta de ativos e reduz o tempo de comercialização.
* A Adobe Sensei aciona o Smart Content Service, que permite que você treine o algoritmo de reconhecimento de imagem na taxonomia de sua empresa. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em ativos semelhantes.

Para usar Tags inteligentes aprimoradas do AEM Assets, instale o service pack [mais recente do AEM 6.4](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html).

## Pesquisa de tradução inteligente (capacitada pela Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 apresenta o recurso Smart Translation Search para suportar cenários de pesquisa multilíngues. Clientes com equipes distribuídas globalmente em várias localidades agora têm acesso à pesquisa em diferentes idiomas sem precisar passar por workflows de tradução dispendiosos e demorados.

* O query de pesquisa é traduzido sem intervenção manual.
* As Tags inteligentes são geradas em inglês e são traduzidas por computador para outros idiomas.
* A pesquisa multilíngue é criada usando a biblioteca de código aberto Apache Joshua, que suporta mais de 50 idiomas.

## Experiência do usuário {#user-experience}

AEM 6.4 oferece melhorias significativas na experiência do usuário em áreas de navegação, pesquisa, ativos de várias páginas e ferramentas administrativas. Detalhes abaixo:

Aprimoramentos de navegação

* Novo painel Árvore de conteúdo para navegar rapidamente em uma hierarquia de ativos. Em combinação com a visualização de lista, isso restaura o modelo de interação da interface clássica para navegar pelas hierarquias de ativos.
* Novos atalhos de teclado, como m para mover ativos, p para abrir a página de propriedades, Ctrl + C para copiar a operação e muito mais.
* Experiência de rolagem aprimorada e carregamento lento em cartão e visualização de lista para navegação em um grande número de ativos.
* Visualização de placa aprimorada com suporte para diferentes placas de tamanho com base na configuração de visualização.
* Experiência de detalhes de ativos aprimorada com capacidade de visualização, navegação até o ativo &quot;anterior&quot; ou &quot;próximo&quot; junto com o número de ativos, ativo atual.

Aprimoramentos de pesquisa

* Novo botão Pesquisar novamente com a capacidade de navegar até um item de pesquisa e voltar à mesma posição nos resultados da pesquisa sem executar o query de pesquisa novamente.
* Os novos resultados da pesquisa contam para exibir o número de resultados da pesquisa.
* Filtro de pesquisa de tipo de arquivo aprimorado com a capacidade de filtrar resultados de pesquisa com base em tipos MIME refinados, como JPG, PNG e PSD, em comparação com as opções anteriores de imagem, documento e multimídia.
* filtros de pesquisa aprimorados com carimbos de data e hora precisos em vez da funcionalidade do controle deslizante de hora anterior.

Melhorias nos ativos de várias páginas

* Experiência de navegação de ativos de várias páginas aprimorada com um número reduzido de cliques.
* Suporte aprimorado a comentários e anotações com todos eles agrupados no nível do ativo em vez de na página.

Melhorias nas ferramentas administrativas

* Aprimorado o Seletor de propriedades nas ferramentas administrativas para Metadados, Pesquisa e Relatórios com o Tipo à frente e capacidade de navegação para simplificar a experiência do administrador.

Catálogos

* Experiência do usuário aprimorada, alinhamento com a interface do usuário Modelos. Para obter mais informações, consulte [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadados {#metadata}

A AEM 6.4 inclui vários recursos avançados de gerenciamento de metadados para gerenciar metadados em escala e impor a integridade dos metadados por meio de regras e validações. Estes são os principais recursos:

* Novo recurso de Exportação de metadados em massa para exportar (todos, seletivos) metadados para um grande número de ativos no formato CSV para edição, compartilhamento e integração de terceiros.
* Novo recurso de importação de metadados em massa para importar um arquivo CSV para adicionar novos metadados, atualizando os metadados existentes para vários ativos de uma só vez. Esta operação é assíncrona e não prejudica o desempenho do sistema. Após a conclusão, o usuário é notificado por meio AEM sistema de notificação.
* Novos metadados em cascata e contextuais usando a ferramenta Schema de metadados. Agora é possível definir cadeias de dependências e mapeamentos de valor entre campos. Também é possível definir o contexto no qual os campos do formulário de metadados são exibidos/ocultos. Dessa forma, você pode exibir somente campos relevantes a qualquer momento, dependendo dos valores em outros campos.

## Relatórios {#reports}

AEM 6.4 oferece melhorias significativas no relatórios de ativos:

* Nova estrutura de relatórios dimensionável e de nível empresarial (para repositórios grandes) que aplica jobs Sling para processamento assíncrono de solicitações de relatório. Você pode agendar um relatório em uma data e hora específicas. Você também pode adicionar colunas personalizadas a um relatório.
* Novos relatórios OOTB mais comumente solicitados por clientes, como Uso de disco, Arquivos, Compartilhamentos de link, Publicar no Portal de marca e Treinamento em Tags inteligentes.
* Nova interface de usuário de criação e gerenciamento de relatórios com opções de granulação fina, capacidade de acessar relatórios arquivados, ver o status de execução do relatório (sucesso, falha, enfileiramento e assim por diante).

## Brand Portal {#brand-portal}

* **6.3 Atualização** do Platform: O Brand Portal foi atualizado do AEM 6.0 para o AEM 6.3, com novos recursos e melhorias de desempenho.
* **Publicação** paralela: Até replicações podem ocorrer entre o AEM Assets e o Brand Portal (anteriormente 1), o que melhora significativamente o desempenho da publicação
* **Publicação** de facetas de Schema e pesquisa: Capacidade de publicar schemas de metadados e aspectos de pesquisa personalizados no Brand Portal, o que elimina a duplicação de esforços.
* **Publicação** de tags em massa: Capacidade de publicar taxonomia (junto com hierarquia) no Brand Portal, o que elimina a duplicação de esforços.
* **Autoinscrição ou acesso** de solicitação: Fluxo de trabalho para usuários não registrados no Brand Portal.
* **Notificação** de manutenção no aplicativo (na tela): As notificações são exibidas com bastante antecedência para evitar interrupções nos negócios.
* **Melhorias** no Relatórios: Três relatórios OOTB estão disponíveis: baixa, publica e compartilha de links.
* **Restrições** baseadas em DRM: Depois que um ativo licenciado expira, ele não está mais disponível para download no Portal da Marca.

## Aplicativo de desktop do AEM {#aem-desktop-app}

AEM aplicativo de desktop é atualizado para a versão 1.8, que é compatível com a AEM 6.4. A lista completa de alterações para AEM aplicativo desktop é fornecida em um documento dedicado às notas [de versão do aplicativo desktop](https://docs.adobe.com/content/help/pt-BR/experience-manager-desktop-app/using/release-notes.html) AEM.\
Esta é uma lista de AEM destaques do aplicativo para desktop desde que AEM 6.3 foi lançado:

* Capacidade de carregar pastas hierárquicas em segundo plano.
* IU para monitorar os uploads de ativos em segundo plano.
* Melhorias no cache, incluindo uma interface para gerenciar parâmetros de cache.
* Suporte mais amplo para configurações de autenticação de AEM (SAML/SSO) e proxy de rede.
* Suporte: fácil acesso aos registros da interface do usuário.
* Estabilidade e correções aprimoradas para problemas do cliente.

Para facilitar o acesso à documentação e às práticas recomendadas, a seguinte documentação está disponível:

* [Guia](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)do usuário, destinado aos usuários finais que trabalham com o aplicativo.
* [Guia](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)de instalação, destinado aos administradores que configuram AEM e AEM aplicativo de desktop para trabalhar em conjunto

## Armazenamento hierárquico {#tiered-storage}

A AEM 6.4 inclui um conjunto de recursos que suporta várias preferências de armazenamento hierárquico e implementa regras de ciclo de vida. As opções de armazenamento também suportam (mas não são limitadas) nuvens públicas - AWS ou Azure.

* A capacidade de os usuários selecionarem e alterarem posteriormente a classe do armazenamento à vontade e definirem regras para o armazenamento de ativos de uma classe para outra ou gerenciarem o ciclo de vida de seus ativos.
* A capacidade de os usuários reduzirem seus custos de armazenamento selecionando um AWS ou Azure diferente.

Para obter uma visão geral das plataformas suportadas, consulte a Documentação [dos requisitos](../sites-deploying/technical-requirements.md)técnicos.

## Grupo de usuário fechado {#closed-user-group}

* No AEM 6.4, Closed User Group ou CUG fornece uma maneira de restringir o acesso da pasta na instância de publicação, é uma opção de interface de toque para adicionar principais por meio da página de propriedades da pasta no nível da pasta e são aplicados a todas as pastas e subpastas/ativos dentro dela.
* No modo de publicação, se um CUG estiver configurado e a autorização estiver ativada em uma pasta, os usuários serão redirecionados para uma página de logon quando tentarem acessar a pasta. Portanto, os usuários autorizados podem acessar a pasta e seus ativos somente após o login bem-sucedido. Portanto, o CUG restringe o acesso de leitura a uma determinada árvore no repositório de conteúdo para todos, exceto os principais selecionados.

## Dynamic Media add-on {#dynamic-media-add-on}

O Dynamic Media na versão 6.4 é compatível com um novo modo - onde o ativo principal é carregado e gerenciado com a interface do usuário da Web do AEM Assets, e as representações dinâmicas e outros recursos de mídia dinâmica são manipulados em segundo plano pelo serviço de delivery em nuvem da Dynamic Media.

Nesse modo (introduzido primeiro com o lançamento do [AEM 6.3 Feature Packs 14410 e 18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), os usuários se beneficiam do gerenciamento completo de ativos e dos recursos de mídia dinâmica usando a interface do usuário moderna da Web do AEM Assets e ainda aproveitam os serviços de delivery que são compatíveis com o Dynamic Media Classic (Scene7) — incluindo URLs de delivery, que não foram alterados.

Além disso, o AEM 6.4 apresenta novos recursos capacitados pela Adobe Sensei, melhorias para mídias emergentes como VR e 3D, visualizadores Dynamic Media e suporte para Fragmentos de experiência em imagens interativas e banners carrossel.

### Recorte inteligente (fornecido pela Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* O Smart Crop fornece automaticamente recorte não destrutivo de imagens para preservar o ponto de interesse do design responsivo. Você pode pré-visualização sugestões cortadas e ajustá-las manualmente, se necessário.
* Esse recurso também permite a geração automática de amostras para imagens de produtos. A geração automatizada de amostras ajuda a adicionar amostras de cores, amostras de padrões ou ambas automaticamente às imagens do produto.

Consulte a documentação de Perfis [](../assets/image-profiles.md) de imagem para saber mais.

Consulte também a documentação [Adicionar ativos Dynamic Media a páginas](../assets/adding-dynamic-media-assets-to-pages.md) para saber mais sobre o uso do Smart Crop com o componente Dynamic Media.

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

### 3D e integração com a Dimension CC {#d-and-integration-with-dimension-cc}

A integração com o [Adobe Dimension CC](https://www.adobe.com/products/dimension.html) para um fluxo de trabalho 3D mais integrado foi introduzida. Para saber mais, consulte [Trabalhar com a documentação de ativos](../assets/assets-3d.md) 3D.
