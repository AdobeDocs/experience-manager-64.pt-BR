---
title: Perguntas frequentes sobre AEM
seo-title: AEM 6.4 perguntas frequentes
description: Use essas perguntas frequentes para entender, configurar e solucionar problemas comuns de fluxos de trabalho ou problemas no AEM.
seo-description: Use essas perguntas frequentes para entender, configurar e solucionar problemas comuns de fluxos de trabalho ou problemas no AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# AEM perguntas frequentes{#aem-faqs}

Siga esta página para obter respostas para alguns problemas AEM de solução de problemas e configuração.

## Sites {#sites}

### Como configurar a distribuição sem código binário? {#how-do-i-configure-binary-less-distribution}

A distribuição sem binários é compatível com implantações em um armazenamento de dados compartilhado e envolve agentes que aproveitam o exportador de pacotes de distribuição baseado em Vault (PID de fábrica: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) construtor de pacotes.

Com o modo sem binário ativado, os pacotes de conteúdo distribuídos contêm referências a binários em vez dos binários reais.

### Como ativar a distribuição sem código binário? {#how-do-i-enable-binary-less-distribution}

Para ativar a distribuição sem binário, implante com um repositório de blobs compartilhado.\
Verifique a propriedade `useBinaryReferences` na configuração OSGI com o PID de fábrica ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* que seu agente está usando.

### Como posso personalizar as mensagens de erro ao navegar pela hierarquia de página AEM console de sites? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Verifique o painel Rede (do navegador Chrome), onde uma configuração pessoal (JS não foi minimizado).

Visualize a coluna `Initiator` para determinar o que foi o iniciador de uma solicitação. Ele fornece os arquivos e os números de linha de onde as chamadas de AJAX são feitas. Posteriormente, é possível rastrear a função de tratamento de erros e alterar a mensagem de erro de acordo com seu requisito.

### Como ativar permissões ao criar uma Cópia de idioma para autores de conteúdo no AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Para criar o recurso de cópia de idioma, os autores de conteúdo precisam de permissões no local `/content/projects`.

Se for necessário que os autores gerenciem projetos também, a solução alternativa é adicionar o autor ao grupo `project-administrators`.

### Como alterar o formato ao criar a Cópia de idioma para um projeto? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Crie uma raiz de idioma e uma cópia de idioma dentro da raiz, antes de criar um projeto de tradução.

Por exemplo,\
Crie uma raiz de idioma em `/content/geometrixx` com o nome `fr_LU` (e o título como francês (Luxemburgo)). Posteriormente, crie uma cópia de idioma da página no painel de referências e navegue até a opção `Create structure only` em `Create & Translate`. Por fim, crie um projeto de tradução e adicione a cópia de idioma ao trabalho de tradução.

Para obter detalhes, consulte os recursos adicionais abaixo:

* [Preparação do conteúdo para tradução](/help/sites-administering/tc-prep.md)
* [Gerenciamento de projetos de tradução](/help/sites-administering/tc-manage.md)

### Como auditar AEM recursos como, tentativas de logon e alterações de ACL ou permissão? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM introduziu a capacidade de registrar alterações administrativas para obter uma melhor solução de problemas e auditoria. Por padrão, as informações são registradas no arquivo `error.log`. Para facilitar o monitoramento, é recomendável que ele seja redirecionado para um arquivo de log separado.\
Para redirecionar a saída para um arquivo de log separado, consulte [Como auditar operações de gerenciamento de usuários em AEM](/help/sites-administering/audit-user-management-operations.md).

### Como habilitar o SSL por padrão? {#how-to-enable-ssl-by-default}

O Adobe Experience Manager (AEM) 6.4 é fornecido com o assistente SSL e oferece uma interface de usuário para configurar o suporte a Jetty e Granite Jetty SSL.

Para ativar o SSL por padrão, consulte [SSL por padrão](/help/sites-administering/ssl-by-default.md).

### Qual é a arquitetura recomendada ao usar os Serviços de conteúdo da AEM de um aplicativo móvel, idealmente React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Os Serviços de conteúdo são baseados nos Modelos do Sling e os desenvolvedores de AEM devem fornecer um trabalho de Modelo do Sling para cada componente que é exportado.

Para entender como consumir AEM serviços de conteúdo de um aplicativo React, consulte o tutorial [Introdução aos AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) .

Além disso, se os desenvolvedores quiserem exportar uma árvore de componentes, também poderão implementar as interfaces `ComponentExporter` e `ContainerExporter`, bem como usar `ModelFactory` para iterar os componentes filhos e retornar sua representação de modelo. Consulte os recursos abaixo:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling: Modelos Sling](https://sling.apache.org/documentation/bundles/models.html)

### Como desativar o pop-up de pesquisa do AEM 6.4? {#how-to-disable-aem-survey-pop-up}

Você pode aderir à coleção de estatísticas de uso usando a interface do usuário de toque ou o console da Web. Para obter instruções detalhadas, consulte [Aceitação na coleta de estatísticas de uso agregado](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Existe um bom recurso que destaca os principais recursos para atualizar para o AEM 6.4? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Consulte [Entendendo os motivos para atualizar o AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) que descreve o detalhamento de alto nível dos principais recursos para clientes que consideram atualizar para a versão mais recente do Adobe Experience Manager.

### Como configurar uma instância AEM para usar o filtro PorterStem? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

O filtro PorterStem aplica o Algoritmo de Emissão de Porter para inglês. Os resultados são semelhantes ao uso do Snowball Porter Stemmer com o argumento *language=&quot;English&quot;*. Mas esse provedor é codificado diretamente em Java e não se baseia no Snowball. Não aceita uma lista de palavras protegidas e só é adequada para o texto em inglês.

O Oak expõe um conjunto de elementos de configuração do lucene-fornece o analisador para uso no AEM. Para saber como usar filtros, consulte **Apache Oak Analyzers** em [Guia de implementação de pesquisa simples](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### Como executar uma reindexação completa? {#how-to-perform-a-full-re-indexing}

A reindexação deve ser sempre abordada com a devida consideração sobre o seu impacto no desempenho AEM geral e executada durante períodos de baixa atividade ou janelas de manutenção.

Consulte as [Práticas recomendadas para consultas e indexação](/help/sites-deploying/best-practices-for-queries-and-indexing.md) para entender os motivos para reindexação.

### Oferecemos suporte a libs JS minificadas no Importador de design? {#do-we-support-minified-js-libs-in-design-importer}

Você precisa alterar a propriedade de configurações padrão do processador JS do Gerenciador de biblioteca HTML do Adobe Granite para ***min:gcc***. Para importar o pacote de design com sucesso, é recomendável incluir bibliotecas de terceiros pré-minificadas em nossas bibliotecas do lado do cliente.

## Ativos {#assets}

### Por que o fluxo de trabalho de Ativos se repete ao fazer upload de arquivos MP4 (por exemplo, usando o método arrastar e soltar)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Se o usuário fizer upload dos arquivos de filme não tiver permissões de exclusão no nó do ativo, os nós de exclusão de segmento falharão e o upload será reiniciado.

### Qual é o número máximo de ativos digitais que podem ser operados com AEM 6.4 de cada vez? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

O Adobe Experience Manager (AEM) 6.4 atualmente permite fazer upload de até 2 GB de ativos de cada vez.

Para obter informações adicionais sobre o número máximo de ativos que podem ser operados com o AEM 6.4, consulte [Guia de dimensionamento de ativos](/help/assets/assets-sizing-guide.md).

### Quais são as configurações padrão para configurações OTB ao criar a Cópia de idioma? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Ao criar cópias de idioma por meio da interface clássica, os Ativos não são movidos para a hierarquia de novos idiomas, mas usados a partir do idioma principal.

Enquanto que, ao criar uma cópia de idioma por meio da interface de toque (**Referências** -> **Atualizar cópia de idioma**), uma nova pasta DAM é criada no novo idioma e os ativos são referenciados a partir daí.

Essa é a configuração padrão para configurações OTB. Você pode definir **Traduzir ativos da página** = **Não traduzir** nas configurações de Tradução.\
Para AEM 6.4, **Ferramentas** > **Cloud Services** > **Serviços da Nuvem de Tradução**.

### Como desabilitar um componente de AEM que causa crescimento exponencial para o AEM SegmentStore (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

Você pode desativar o Desativador do Componente OSGi. Para usar este serviço, consulte [Desabilitador de Componente OSGi](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Como solução alternativa, você também pode desativar manualmente o componente por meio da interface do usuário ou por meio de um comando `curl` (exemplo abaixo), após cada reinicialização AEM.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Como configurar o Assets Insights com a instância AEM 6.4? {#how-to-configure-asset-insights-with-aem-instance}

Para configurar e configurar o Assets Insights para o Experience Manager implantado via Adobe Ativation (DTM), consulte [Configurar o Assets Insights com o AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Como personalizar consoles de administração? {#how-to-customize-admin-consoles}

O AEM fornece vários mecanismos para permitir a personalização dos consoles e a funcionalidade de criação de página da sua instância de criação.
Para saber como criar um console personalizado e personalizar uma visualização padrão para um console, consulte [Personalização dos Consoles](/help/sites-developing/customizing-consoles-touch.md).

### Qual é a diferença entre os componentes baseados em CoralUI 2 e CoralUI 3? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Um novo conjunto de componentes Sling da Fundação de interface do usuário do Granite é criado para o Coral3 e está localizado em [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Há um conjunto para componentes baseados em CoralUI 2 e um conjunto para componentes baseados em CoralUI 3. O novo conjunto não será apenas uma cópia e uma colagem do conjunto antigo, mas será limpo (por exemplo, simplificação, remoção de recurso obsoleto). Portanto, é recomendável que uma página use somente o conjunto com base em CoralUI 3 ou CoralUI 2.

Para saber mais detalhes, consulte o [Guia de migração para CoralUI baseado em 3](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Como personalizar o componente de pesquisa no AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

Para saber mais sobre informações de reforço/classificação de pesquisa e implementação adicional, consulte [Guia de implementação de pesquisa simples.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

A implementação Simple search são os materiais do laboratório 2017 Summit AEM Search Demystified.

### Se um cliente comprar apenas a licença do Sites no AEM, ele ainda terá acesso ao Assets? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

Não, o cliente não pode acessar Ativos (ou qualquer outra coisa diferente de Sites). Embora todos os Adobe Experience Manager (AEM) no local estejam incluídos no JAR, o cliente está autorizado a acessar apenas os componentes no JAR para os quais está licenciado em seu contrato. Se quiser explorar outros componentes, eles poderão usar o programa de avaliação de AEM por até 45 dias ou assinar uma Ordem de vendas de US$ 0 que os autoriza a avaliar (nenhum uso de produção) componentes nomeados, como Ativos.

Consulte os seguintes recursos para saber mais sobre AEM software no local e Adobe Managed Services:

* [Software no local da Adobe Experience Manager](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Como um cliente pode estender as propriedades padrão de uma página ou de um ativo? {#how-to-extend-default-properties-page-or-asset}

Para saber mais sobre a extensão das propriedades padrão de uma página ou ativo, consulte os recursos abaixo:

* [Esquemas de metadados em ativos](/help/assets/metadata-schemas.md)
* [Personalização de exibições das propriedades da página](/help/sites-developing/page-properties-views.md)
