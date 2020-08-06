---
title: AEM perguntas frequentes
seo-title: AEM 6.4 perguntas frequentes
description: Use essas Perguntas frequentes para entender, configurar e solucionar problemas de workflows ou problemas comuns em AEM.
seo-description: Use essas Perguntas frequentes para entender, configurar e solucionar problemas de workflows ou problemas comuns em AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---


# AEM perguntas frequentes{#aem-faqs}

Siga esta página para obter respostas para alguns problemas AEM de solução de problemas e configuração.

## Sites {#sites}

### Como configurar a distribuição sem binários? {#how-do-i-configure-binary-less-distribution}

A distribuição sem binários é suportada para implantações em um armazenamento de dados compartilhado e envolve agentes que aproveitam o exportador de pacotes de Distribuição baseado em Cofre (PID de fábrica: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) do construtor de pacotes.

Com o modo sem binários ativado, os pacotes de conteúdo distribuídos contêm referências a binários em vez dos binários reais.

### Como ativar a distribuição sem binários? {#how-do-i-enable-binary-less-distribution}

Para ativar a distribuição sem binários, implante com um armazenamento de blob compartilhado.\
Verifique a `useBinaryReferences` propriedade na configuração OSGI com o PID de fábrica ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*que seu agente está usando.

### Como posso personalizar as mensagens de erro ao navegar pela hierarquia de páginas no console de sites AEM? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Verifique o painel Rede (do navegador Chrome) onde uma configuração pessoal (JS não foi minimizada).

Visualização a `Initiator` coluna para determinar qual foi o iniciador de uma solicitação. Fornece os arquivos e os números de linha de onde as chamadas de AJAX são feitas. Posteriormente, você pode rastrear a função de tratamento de erros e alterar a mensagem de erro de acordo com suas necessidades.

### Como ativar permissões ao criar uma Cópia de idioma para autores de conteúdo no AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Para criar o recurso de cópia de idioma, os autores de conteúdo precisam de permissões no `/content/projects` local.

Se for necessário que os autores gerenciem projetos também, a solução alternativa é adicionar o autor ao `project-administrators` grupo.

### Como alterar o formato ao criar a Cópia de idioma para um projeto? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Crie uma raiz de idioma e uma cópia de idioma dentro da raiz, antes de criar um projeto de tradução.

Por exemplo,\
Crie uma raiz de idioma `/content/geometrixx` com o nome `fr_LU` (e o título como francês (Luxemburgo)). Subsequentemente, crie uma cópia de idioma da página no painel de referências e navegue até a `Create structure only` opção em `Create & Translate`. Finalmente, crie um projeto de tradução e adicione a cópia de idioma ao trabalho de tradução.

Para obter detalhes, consulte os recursos adicionais abaixo:

* [Preparação de conteúdo para tradução](/help/sites-administering/tc-prep.md)
* [Gerenciamento de projetos de tradução](/help/sites-administering/tc-manage.md)

### Como auditar recursos AEM como tentativas de login e ACL ou alterações de permissão? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM introduziu a capacidade de registrar alterações administrativas para obter uma melhor solução de problemas e auditoria. Por padrão, as informações são registradas no `error.log` arquivo. Para facilitar o monitoramento, é recomendável que eles sejam redirecionados para um arquivo de log separado.\
Para redirecionar a saída para um arquivo de log separado, consulte [Como auditar as operações de gerenciamento de usuários no AEM](/help/sites-administering/audit-user-management-operations.md).

### Como ativar o SSL por padrão? {#how-to-enable-ssl-by-default}

A Adobe Experience Manager (AEM) 6.4 é fornecida com o assistente SSL e oferta uma interface de usuário para configurar o suporte a Jetty e Granite Jetty SSL.

Para ativar o SSL por padrão, consulte [SSL por padrão](/help/sites-administering/ssl-by-default.md).

### Qual é a arquitetura recomendada ao usar o Content Services da AEM em um aplicativo móvel, idealmente Reagir nativo? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Os Serviços de conteúdo são baseados nos Modelos Sling e os desenvolvedores AEM devem fornecer um pojo Sling Model para cada componente exportado.

Para entender como consumir AEM serviços de conteúdo de um aplicativo React, consulte [Introdução ao AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) tutorial.

Além disso, se os desenvolvedores quiserem exportar uma árvore de componentes, eles também poderão implementar as interfaces `ComponentExporter` e `ContainerExporter` , bem como usar o `ModelFactory` para iterar sobre os componentes filhos e retornar sua representação de modelo. Consulte os recursos abaixo:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling : Modelos Sling](https://sling.apache.org/documentation/bundles/models.html)

### Como desativar AEM pop-up de pesquisa 6.4? {#how-to-disable-aem-survey-pop-up}

Você pode optar pela coleta de estatísticas de uso usando a interface de usuário de toque ou o console da Web. Para obter instruções detalhadas, consulte [Opting into agregated usage statistics collection](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Há um bom recurso que destaca os principais recursos para atualizar para o AEM 6.4? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Consulte [Entendendo os motivos para atualizar AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) que descrevem o detalhamento de alto nível dos principais recursos para clientes que consideram atualizar para a versão mais recente do Adobe Experience Manager.

### Como configurar uma instância AEM para usar o filtro PorterStem? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

O filtro PorterStem aplica o Porter Stemming Algorithm para inglês. Os resultados são semelhantes ao uso do Snowball Porter Stemmer com o argumento *language=&quot;English&quot;* . Mas esse mecanismo é codificado diretamente em Java e não se baseia em Snowball. Ele não aceita uma lista de palavras protegidas e é apropriado apenas para o texto em inglês.

O Oak expõe um conjunto de elementos de configuração do analisador que fornecem luceno para uso em AEM. Para saber como usar filtros, consulte **Apache Oak Analyzers** no guia [de implementação de pesquisa](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)Simples.

### Como executar uma reindexação completa? {#how-to-perform-a-full-re-indexing}

A reindexação deve ser sempre abordada com a devida consideração sobre o seu impacto no desempenho AEM geral e executada durante períodos de baixas atividades ou janelas de manutenção.

Consulte as Práticas [recomendadas para Query e indexação](/help/sites-deploying/best-practices-for-queries-and-indexing.md) para entender os motivos da reindexação.

### Suportamos libs de JS minified no Importador de design? {#do-we-support-minified-js-libs-in-design-importer}

É necessário alterar a propriedade de configuração padrão do processador JS do Gerenciador de biblioteca HTML Adobe Granite para ***min:gcc***. Para importar o Pacote de design com êxito, é recomendável incluir bibliotecas de terceiros pré-minimizadas nas Bibliotecas do lado do cliente.

## Assets {#assets}

### Por que o fluxo de trabalho de Ativos se repete ao fazer upload de arquivos MP4 (por exemplo, usando o método arrastar e soltar)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Se o usuário fizer upload dos arquivos de filme não tiver permissões de exclusão no nó do ativo, os nós de exclusão de bloco falharão e o upload será reiniciado.

### Qual é o número máximo de ativos digitais que podem ser operados com AEM 6.4 de cada vez? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

No momento, o Adobe Experience Manager (AEM) 6.4 permite fazer upload de até 2 GB de ativos por vez.

Para obter informações adicionais sobre o número máximo de ativos que podem ser operados com AEM 6.4, consulte o Guia [de dimensionamento de](/help/assets/assets-sizing-guide.md)ativos.

### Quais são as configurações padrão para configurações OOTB ao criar a Cópia de idioma? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Ao criar cópias de idioma por meio da interface clássica, os ativos não são movidos para a hierarquia do novo idioma, mas sim para o idioma principal.

Enquanto que, ao criar uma cópia de idioma por meio da interface de usuário de toque (**Referências** -> **Atualizar cópia** de idioma), uma nova pasta DAM é criada no novo idioma e os ativos são referenciados a partir daí.

Esta é a configuração padrão para configurações OOTB. Você pode definir **Traduzir ativos** da página = **Não traduzir** em configurações de Tradução.\
Para AEM 6.4, **Ferramentas** > **Cloud Services** > Serviços **da** Translation Cloud.

### Como desativar um componente AEM causando crescimento exponencial para o AEM SegmentStore (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Você pode desativar o OSGi Component Disabler. Para usar esse serviço, consulte Desabilitador de componentes [OSGi](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Como solução alternativa, você também pode desativar manualmente o componente por meio da interface do usuário ou por meio de um `curl` comando (exemplo abaixo), após cada reinicialização AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Como configurar o Asset Insights com a instância AEM 6.4? {#how-to-configure-asset-insights-with-aem-instance}

Para configurar e configurar o Asset Insights para Experience Manager implantado via Adobe Ativação (DTM), consulte [Configurar o Asset Insights com a AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Como personalizar consoles de administração? {#how-to-customize-admin-consoles}

AEM fornece vários mecanismos para permitir que você personalize os consoles e a funcionalidade de criação de página da sua instância de criação.
Para saber como criar um console personalizado e personalizar uma visualização padrão para um console, consulte [Personalizar os consoles](/help/sites-developing/customizing-consoles-touch.md).

### Qual é a diferença entre os componentes baseados em CoralUI 2 e CoralUI 3? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Um novo conjunto de componentes Sling da Granite UI Foundation é criado para Coral3 e está localizado em [/libs/granite/ui/components/coral/fundação.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Há um conjunto para componentes baseados em CoralUI 2 e um conjunto para componentes baseados em CoralUI 3. O novo conjunto não será apenas uma cópia colada do conjunto antigo, mas será limpo (por exemplo, simplificação, remoção de recurso obsoleto). Portanto, recomenda-se que uma página use somente o conjunto baseado em CoralUI 3 ou CoralUI 2.

Para saber mais detalhadamente, consulte o Guia [de migração para a CoralUI com base](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html)em 3.

### Como personalizar o componente de pesquisa no AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

Para saber mais sobre informações sobre otimização/classificação de pesquisa e implementação adicional, consulte o guia de implementação de pesquisa [simples.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

A implementação de pesquisa Simples são os materiais do laboratório Summit 2017 AEM Pesquisa Desmistificada.

### Se um cliente comprar somente a licença do Sites no AEM, ele ainda terá acesso aos Ativos? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Não, o cliente não pode acessar os Ativos (ou qualquer outra coisa além dos Sites). Mesmo que todos os componentes da Adobe Experience Manager (AEM) no local estejam incluídos no JAR, o cliente é autorizado a acessar apenas os componentes no JAR para os quais eles estão licenciados em seus contratos. Se quiserem explorar outros componentes, eles poderão usar o programa de avaliação AEM por até 45 dias ou assinar uma Ordem de Venda de US$ 0 que os autorize a avaliar (sem uso de produção) componentes nomeados, como o Assets.

Consulte os seguintes recursos para saber mais sobre AEM software local e serviços gerenciados da Adobe:

* [Software local Adobe Experience Manager](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Como um cliente pode estender as propriedades padrão de uma página ou de um ativo? {#how-to-extend-default-properties-page-or-asset}

Para saber mais sobre como estender as propriedades padrão de uma página ou de um ativo, consulte os recursos abaixo:

* [Schemas de metadados em ativos](/help/assets/metadata-schemas.md)
* [Personalização de Visualizações de propriedades da página](/help/sites-developing/page-properties-views.md)
