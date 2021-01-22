---
title: Notas de versão do AEM 6.4 Cumulative Fix Pack
description: Notas de versão específicas dos Pacotes de correção cumulativos do Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '4219'
ht-degree: 11%

---


# Notas de versão do AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Informações da versão {#release-information}

<!-- TBD: Update the SD URL. -->

| Produtos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versão | 6.4.8.3 |
| Tipo | Cumulative Fix Pack |
| Data | 26 de novembro de 2020 |
| Pré-requisitos | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de download | AEM 6.4.8.3 em [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip) |

## O que está incluído no AEM 6.4.8.3 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.3 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0) em março de 2020.

AEM 6.4.8.3 é um Cumulative Fix Pack (CFP) que depende do AEM 6.4 Service Pack 8. Instale o CFP após a instalação do AEM 6.4 Service Pack 8.

No AEM 6.4.8.3, o repositório integrado (Apache Jackrabbit Oak) é atualizado para a versão 1.8.23.

Para obter informações sobre CFP e outros tipos de versões, consulte [AEM Atualizar Definições de Veículo de Liberação](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.3 fornece correções para os seguintes problemas.

### Sites {#sites-6483}

* Quando você atualiza o texto de uma variação de um fragmento de conteúdo, o conteúdo do fragmento de conteúdo principal é atualizado em vez da variação (NPR-35080).

* Quando você define um valor numérico para a propriedade de rótulo do tipo String de um componente, exclui o componente e usa a opção desfazer para trazê-lo de volta, o tipo de propriedade label muda automaticamente de String para Long (NPR-34738).

* Quando você adiciona um componente de Upload de arquivo a vários campos, o caminho da imagem é armazenado no nó do componente em vez do nó Vários campos (NPR-34423).

* No assistente Mover página, mesmo se nenhum destino estiver selecionado, o botão seguinte permanece ativado (NPR-34460).

* Quando o componente pai inclui a propriedade `cq:isContainer`, o componente herdado não inclui automaticamente a propriedade (CQ-4308409).

* Quando você usa a miniificação de CSS usando a função `calc()`, os espaços em branco ao redor do sinal `+` são removidos (NPR-34991).

* Quando você start uma instância AEM, os componentes `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` e `com.adobe.granite.maintenance.impl.TaskScheduler` não são exibidos no estado `Active` (NPR-34952).

### [!DNL Assets] {#assets-6483}

* Ao criar uma versão de um ativo existente, o usuário atualiza os metadados se um perfil de metadados for aplicado à pasta (NPR-34833).
* Ao usar [!DNL Adobe Asset Link] com [!DNL Adobe InDesign], os resultados da pesquisa não contêm pastas e coleções, mas contêm apenas ativos (NPR-34700).
* Ao arrastar um ativo em uma pasta para movê-lo, a interface do usuário também exibe a opção para [!UICONTROL Lightbox] e [!UICONTROL Drop in Collection]. Mesmo se a operação de movimentação for cancelada, a interface do usuário continuará a exibir as duas últimas opções (NPR-34525).
* Quando a interface Gerenciar publicação é aberta, a opção de publicação não está disponível e, ao selecionar a opção de cancelamento de publicação, a página de escopo fica em branco (CQ-4302509).

#### [!DNL Dynamic Media] {#dynamic-media}

* Nas configurações da predefinição de imagem, quando a opção [!UICONTROL Ativar a redução da resolução do crominância JPG] estiver desmarcada em [!DNL Experience Manager], a alteração não será sincronizada com [!DNL Dynamic Media] (NPR-34284).
* No [!UICONTROL Editor de predefinições do visualizador], ao editar a predefinição [!UICONTROL PanorâmicaImage/PanorâmicaImage_VR], no componente `PanoramicView`, a etiqueta do modificador `PANORAMICVIEW_AUTOROTATE` não está disponível (CQ-4302043).
* Desfazer a publicação de um vídeo de [!DNL Experience Manager] não cancela a publicação do Conjunto de vídeos adaptáveis no Dynamic Media Classic configurado. (CQ-4304405).

### Plataforma {#platform-6483}

* O sinalizador `emitUseStrict` é adicionado à função Processador do Compilador de Fechamento do Google (GCC) `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. O sinalizador suprime a saída da instrução `use strict` (NPR-34830).
* Um `NullPointerException` é retornado ao iniciar tarefas de manutenção diárias ou semanais (NPR-34702).
* A ferramenta [!DNL Apache Sling Health Check] está obsoleta. Em vez disso, use [Detector de padrão](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) para detectar violações de conteúdo (NPR-33929).

### Integrações {#integrations-6483}

* O botão [!UICONTROL Criar] aparece na página [!UICONTROL Audiência] ao navegar de uma pasta para a página [!UICONTROL Audiência] (NPR-35152).

### Interface do usuário {#ui-6483}

* O painel de pesquisa [!UICONTROL Filtros] na [!UICONTROL interface de usuário do Omnisearch] também retorna resultados de locais diferentes de onde a pesquisa é executada (NPR-34877).
* Ao fechar o painel [!UICONTROL Filtros] na interface de usuário do [!UICONTROL Omnisearch], o painel esquerdo não é redefinido para a seleção [!UICONTROL Content], o que impede a reabertura do painel [!UICONTROL Filtros] (NPR-34483).
* Um `NullPointerException` é retornado ao acessar as propriedades da página (NPR-34509).

### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Todos os casos de terminologia não equitativa no produto são substituídos por equivalentes aceites (NPR-34506).

### Commerce {#commerce-6483}

* Quando há mais de 15 produtos em uma coleção, a coleção exibe apenas os primeiros 15 produtos (NPR-34494).

### Forms {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] libera os pacotes de complementos uma semana após a data de lançamento programada do Pacote de correções  [!DNL Experience Manager] cumulativas.

>[!NOTE]
>
>[!DNL Experience Manager] O Cumulative Fix Pack não inclui correções para  [!DNL Experience Manager Forms]. Eles são entregues usando um pacote complementar separado [!DNL Forms]. Além disso, é lançado um instalador cumulativo que inclui correções para [!DNL Experience Manager Forms] no JEE. Para obter mais informações, consulte [Instalar o pacote suplementar da AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulários adaptáveis**

* Não é possível editar um formulário adaptável usando a interface clássica depois de aplicar o [!DNL Experience Manager] Cumulative Fix Pack (NPR-35127).

* Os fragmentos levam mais tempo para carregar em um formulário adaptável devido à invalidação do cache (NPR-34655).

* Acessibilidade: A navegação por guias não funciona corretamente para leitores de tela em um formulário adaptável (NPR-34550).

**Gerenciamento de correspondência**

* Quando você migra os ativos do ES3, os ativos incluem duas condições padrão não editáveis (NPR-34971).

**Foundation JEE**

* Migre [!DNL AEM Forms] usuários de Flash para HTML (CQ-4304075).

Para obter informações sobre atualizações de segurança, consulte [página de marcadores de segurança do Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Correções e Feature Packs incluídos em Fix Cumulative Packs anteriores {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0) em março de 2020.

AEM 6.4.8.2 é um Cumulative Fix Pack (CFP) que depende do AEM 6.4 Service Pack 8. Instale o CFP após a instalação do AEM 6.4 Service Pack 8.

No AEM 6.4.8.2, o repositório integrado (Apache Jackrabbit Oak) é atualizado para a versão 1.8.22.

Para obter informações sobre CFP e outros tipos de versões, consulte [AEM Atualizar Definições de Veículo de Liberação](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.2 fornece correções para os seguintes problemas.

#### Sites {#sites-6482}

* Se `RolloutConfigManagerFactoryImpl` não conseguir carregar uma configuração de implementação, ele não tentará carregar as configurações ausentes. Ele retorna as configurações em cache (NPR-34091).
* No componente principal do texto, depois de usar a opção de edição HTML de origem, a classe da tag `em` é removida (NPR-34080).
* Quando você atualiza do Experience Manager 6.2 para o Experience Manager 6.5, o componente Parsys dos modelos estáticos não é exibido corretamente. A altura do componente Parsys está definida como 0 e os componentes dentro dele não estão visíveis (NPR-34044).
* As informações do rótulo não são exibidas dos componentes permitidos no Editor de modelos (NPR-33908).

   ![Rótulos ausentes no container de layout](assets/33908_missing_labels.png)

* Os usuários não podem adicionar ou editar componentes ao parsys após o quarto nível de componentes aninhados (NPR-33873).
* Se o conteúdo inicial de um modelo editável for alterado e o modelo for publicado, quaisquer novas páginas criadas com esse modelo mostrarão a data de publicação do modelo, mesmo que as páginas não sejam publicadas (NPR-33822).
* As propriedades `cq:acLinks` e `cq:acUUID` para [!DNL Adobe Campaign] na cópia são removidas durante a operação de cópia e colagem (NPR-33793).
* Na guia [!UICONTROL Uso ao vivo], somente 49 resultados são exibidos. Ele não mostra todo o uso do componente (NPR-33710).
* Uma página da Web com o caractere `/` no URL não responde durante a criação. Quando um componente é adicionado durante a criação, o uso da CPU aumenta e o navegador para de responder (NPR-33625).
* No modo de edição em linha em [!DNL RTE], arrastar uma imagem não funciona para o componente de Texto (NPR-33579).
* É possível criar um componente em uma página do blueprint com o mesmo nome do nome da página. Durante a implementação, esse componente é renomeado com o sufixo `_msm_moved`. No entanto, o componente é movido para o fim do [!UICONTROL Sistema de parágrafo] (NPR-33534).
* A promoção de inicialização não publica páginas quando a propriedade [!UICONTROL include subpages] não está marcada na primeira raiz de conteúdo (NPR-33533).
* O redirecionamento para a página [!DNL Experience Manager] com âncora não funciona na instância Autor, já que `PageRedirectServlets` coloca a string de query após um fragmento de URL ou uma âncora (NPR-34287).
* `PageRedirectServlet` é anexado  `.html` após o mapeamento Sling, resultando em falhas de link (NPR-34271).
* Você pode suspender o [!DNL Live Copy] de uma página e a herança será quebrada como visto no modo Editor. Entretanto, nas propriedades da Página, o ícone que representa a herança indica incorretamente que a herança existe e não está quebrada (NPR-34096).
* Problema com a exibição de componentes permitidos na página Editar modelo (CQ-4297295).
* Depois de atualizar o Chrome e o Firefox, os menus pop-up não funcionam como esperado. Ao carregar as propriedades da página, ele não exibe o painel quando há dados nele (CQ-4292995).
* Várias instâncias de script entre sites em [!DNL Experience Manager Sites] componentes (NPR-33926).
* As entradas do usuário não são corretamente codificadas para vários componentes ao enviar informações ao cliente (NPR-33696).
* Um URL que termina com `childrenlist.html` exibe uma página HTML em vez de uma resposta 404. Tais URLs são vulneráveis a scripts entre sites (NPR-33441).

#### Assets {#assets-6482}

* A extração de texto para os arquivos PDF carregados não funciona e a pesquisa de texto completo por algumas palavras em um arquivo PDF não consegue obter esse arquivo PDF (NPR-34165).

   >[!NOTE]
   >Para fazer essa correção funcionar, reinicie a instância do Adobe Experience Manager após instalar o Service Pack 6.4.8.2.

* As barras invertidas são adicionadas antes de caracteres especiais em sugestões de ativos de pesquisa, que têm caracteres especiais em seu nome (NPR-33833).

* Os filtros personalizados salvos como coleções inteligentes não são aplicados corretamente a ativos, portanto, os resultados da pesquisa não são precisos   (NPR-33725).

* A linha do tempo de um ativo dentro de uma pasta que foi reordenada mostra que o ativo foi movido (NPR-33580).

* Cancelar a publicação dos ativos em massa a partir de [!DNL Brand Portal] leva ao erro `Request-URI Too Long` (NPR-34158).

* Na visualização de colunas, se o usuário selecionar a opção [!UICONTROL Filtrar] depois de selecionar um conjunto de ativos (os ativos são desmarcados) e, em seguida, selecionar um conjunto diferente de ativos para mover, os ativos selecionados anteriormente também serão movidos para o novo local (NPR-34018).

* A barra de rolagem não fica visível na visualização da lista, mesmo se houver vários ativos para caber na página (NPR-34156).

* A página [!UICONTROL Gerenciar publicação] dos ativos está quebrada e as opções nela contidas não estão funcionando (CQ-4302509).

**Dynamic Media**

* A funcionalidade Recorte inteligente falha com erro quando o perfil de imagem é adicionado a uma pasta com várias (por exemplo, 11) proporções (NPR-34083).

* As alterações nas predefinições de imagens em [!UICONTROL Adobe Experience Manager] não são sincronizadas com o Dynamic Media Classic (NPR-34284, CQ-4299713).

* O rótulo do modificador [!UICONTROL PANORAMICVIEW_AUTOROTATE] está ausente na guia [!UICONTROL Comportamento] na página [!UICONTROL Editor de predefinições do visualizador] (CQ-4302043).

#### Plataforma {#platform-6482}

* Os valores padrão para as configurações **[!UICONTROL Tempo limite do Connect]** e **[!UICONTROL Tempo limite do soquete]** para a configuração do Agente padrão (publicação) não são especificados (NPR-33708).
* Os start da tarefa de manutenção e as tarefas de manutenção são interrompidas com muita frequência do que o configurado (NPR-33520).
* Não é possível baixar registros usando a ferramenta Diagnóstico em uma instância de Experience Manager atualizada (NPR-34419).

#### Integrações {#integrations-6482}

* O valor de `library_path` não é considerado ao gerar o URL da biblioteca [!DNL Adobe Launch] para bibliotecas migradas de [!DNL Adobe Dynamic Tag Management]. Além disso, as bibliotecas migradas usam um prefixo diferente das bibliotecas [!DNL Adobe Launch]. (NPR-34238).
* As propriedades herdadas de um serviço de nuvem não persistem na atualização das propriedades da página (NPR-33865).

#### Interface do usuário {#ui-6482}

* A exibição da contagem de ativos selecionados em uma página de pesquisa está incorreta (NPR-33540).

#### Comunidades {#communities-6482}

* Os usuários existentes de um grupo da comunidade adicionados por meio do Admin Console são removidos da lista do usuário em qualquer modificação no console do grupo da comunidade (NPR-34312).

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] O Cumulative Fix Pack não inclui correções para  [!DNL Experience Manager Forms]. Eles são entregues usando um pacote complementar separado [!DNL Forms]. Além disso, é lançado um instalador cumulativo que inclui correções para [!DNL Experience Manager Forms] no JEE. Para obter mais informações, consulte [Instalar o pacote suplementar da AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulários adaptáveis**

* Quando há um fragmento de formulário adaptável ausente, o formulário adaptável falha na renderização (NPR-34303).

* A descrição do conteúdo da ajuda para campos de formulário adaptáveis exibe uma tag HTML de parágrafo (NPR-34117).

* Quando você adiciona um container Forms em uma página [!DNL Experience Manager Sites], a página exibe a seguinte mensagem de erro e não permite adicionar novos componentes (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Quando você seleciona a propriedade **[!UICONTROL Revalidar no servidor]** e carrega vários anexos, o formulário adaptável falha ao enviar (NPR-33701).

* Quando você seleciona **[!UICONTROL Usar idioma da página]** e **[!UICONTROL O formulário cobre toda a largura das opções de Página]** no componente [!DNL Experience Manager Forms] em uma página [!DNL Experience Manager Sites], a página não consegue traduzir (NPR-33641).

* Quando você envia um formulário adaptável habilitado para análise incorporado em uma página [!DNL Experience Manager Sites], a análise não funciona corretamente (NPR-31359).

* Foram removidas dependências nas bibliotecas [!DNL Lodash] e [!DNL backbone] (NPR-33458).

* A ação de envio **[!UICONTROL Enviar para o ponto de extremidade REST]** não funciona para um formulário adaptável (NPR-34513).

* Acessibilidade: Quando você tenta enviar um formulário adaptável sem fazer upload de um anexo para um campo obrigatório, o foco não muda automaticamente para o campo de anexo (NPR-34511).

* As entradas do usuário não são corretamente codificadas para [!DNL Forms] componentes ao enviar informações ao cliente (NPR-33611).

**Fluxo de trabalho**

* [!DNL Experience Manager] Falha na operação de Expurgação do Fluxo de Trabalho e exibe a seguinte mensagem de erro (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Quando você instala [!DNL Experience Manager] 6.4.8.1, a lista [!UICONTROL Para fazer] dos itens não é exibida como links. O texto para os itens [!UICONTROL Para fazer] inclui tags HTML (NPR-34318).

**BackendIntegration**

* Não é possível configurar um modelo de dados de formulário em um ambiente AWS hospedado [!DNL Experience Manager Forms Linux] (NPR-33617).

**Designer**

* Quando [!DNL Acrobat DC] estiver instalado em um [!DNL Experience Manager] servidor Forms, a opção **[!UICONTROL Distribute Form]** não estará disponível na versão 6.x [!DNL Experience Manager Designer] (NPR-34325).

**Segurança de documentos**

* Não é possível executar a operação Assinar com certificados baseados em HSM em um arquivo PDF após a instalação de [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Atualização**

* Quando você atualiza a versão [!DNL JBoss] para 7.0.9 para [!DNL Experience Manager Forms] com o Documento Security em um ambiente [!DNL Linux], isso resulta em um erro (CQ-4300546).

Para obter informações sobre atualizações de segurança, consulte [página de marcadores de segurança do Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0) em março de 2020.

AEM Cumulative Fix Pack 6.4.8.1 depende do AEM 6.4 Service Pack 8. Portanto, você deve instalar o pacote AEM Cumulative Fix Pack 6.4.8.1 após instalar AEM 6.4 Service Pack 8.

Alguns dos principais destaques do AEM 6.4.8.1 são:

* O acesso anônimo ao CRXDE Lite não é permitido para melhorar a segurança. Em vez disso, os usuários são direcionados para a tela de logon. Consulte [desenvolvendo com CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Remoção da integração do Compartilhamento de pacotes com a Adobe Experience Manager.
* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.21.

Para obter informações sobre CFP e outros tipos de versões, consulte [AEM Atualizar Definições de Veículo de Liberação](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.1 fornece correções para os seguintes problemas.

#### Sites {#sites-6481}

* Os usuários anônimos podem acessar os recursos do CRX DE Lite (NPR-33522).
* Quando o nome de um componente local em um LiveCopy é idêntico ao nome de um componente no blueprint e o componente é lançado do blueprint, o termo _msm_move não é adicionado ao nome do componente local (NPR-33207).
* Os parâmetros anexados à solicitação original não são incluídos no URL de redirecionamento (NPR-33174).
* Quando a opção Coral.Select define emptyOption=true ou contém um item padrão com valor = &quot;&quot;, o arquivo dropdownshoide.js encontra um erro: TypeError não detectado: component.getValue não é uma função (NPR-33163).
* Quando um componente inclui outro componente como recurso de envio de dados, o espaço reservado do componente do container pai é substituído pelo espaço reservado dos componentes internos (NPR-33119).
* Quando você baseia um Fragmento de conteúdo em um schema e ele contém uma área de texto obrigatória ou um campo de caminho, o Fragmento de conteúdo não é salvo (NPR-33007)
* Quando você cria um componente personalizado usando o componente de fragmento de experiência out-of-the-box e o usa em páginas do AEM Sites, AEM não exibe referências (uso) para o componente personalizado (NPR-32852).
* Quando uma página do AEM Sites faz parte de um grande conjunto de conteúdo com várias cópias online, a pré-visualização do histórico de versão da página não é carregada (NPR-32772).
* Quando você promove uma inicialização, ele adiciona a combinação &quot;cq:LiveRelationship&quot; a cada componente adicionado na inicialização. Tem impacto em todas as inicializações, independentemente do fato de um lançamento ser criado com ou sem a seleção do —  Herdar dados ao vivo da página de origem —  (NPR-32664).
* Quando start de paginação, o Seletor de fragmentos de experiência não carrega todos os itens (NPR-32605).
* Não é possível criar uma inicialização para uma página do AEM Sites. A criação de inicialização resulta em um erro (NPR-32544).
* Gerenciar publicação não inclui ativos referenciados na solicitação de fluxo de trabalho de ativação (NPR-32463).
* A verificação de integridade do Dispatcher exibe a mensagem de aviso `Invalid cookie header` nos arquivos de log (NPR-33630).
* A integração do Salesforce é vulnerável ao SSRF (NPR-32671).
* XSS refletido em PreferencesServlet (NPR-33439).

#### Ativos {#assets-6481}

* A contagem de ativos não é alterada de acordo com a alteração na seleção na Visualização da Lista (NPR-33285).

* O botão Avançar não está ativado ao selecionar o nó pai (onde a pasta filho único está visível) e depois selecionar a pasta filho (NPR-33284).

* A interface de usuário de toque não é renderizada (com erro) para usuários que não têm acesso de leitura na raiz do repositório, quando o modo DMS7 ou Híbrido está ativado (NPR-33175).

* Os caracteres GB18030 que ocorrem em pastas e nomes de ativos mudam para em branco nos arquivos zip baixados (NPR-33150).

* A pasta extra é criada ao recortar inteligente um ativo que está dentro de uma pasta pai com o caractere ponto `.` em seu nome (NPR-32755).

* O carregamento lento não é acionado e não mais de 100 ativos são exibidos ao selecionar para revisar as tarefas na caixa de entrada de notificações (NPR-32749).

* A página de link para compartilhar a coleção está quebrada devido a alterações no coral-info (NPR-32510).

* O processamento de ativos enquanto o upload em massa fica travado (CQ-4293916).

* Vulnerabilidade SSRF no Experience Manager (NPR-33437).

#### Plataforma {#platform-6481}

* O filtro [!DNL Sling] não é chamado se a entrada do mapa `sling:match` for criada em `/etc/maps` (NPR-33308).
* Todos os agentes de liberação são acionados ao desativar uma página (NPR-32941).
* Quando você usa a API `ScriptProcessor` para minimizar uma biblioteca JavaScript, o arquivo de log exibe uma mensagem de erro indicando que o código JavaScript não é compatível com o modo restrito. A API não fornece opção para ativar ou desativar o modo restrito. (NPR-32746).
* Quando um query SQL é executado por um tempo maior, por exemplo, 7 horas, AEM pára de responder (NPR-33043).

#### Interface do usuário {#ui-6481}

* Quando você pesquisa ou navega por um caminho usando uma caixa de diálogo de seleção, a caixa de diálogo de seleção exibe todo o conteúdo do nó JCR selecionado em vez de exibir apenas as imagens (NPR-32712).

#### Projetos de tradução {#tranlation-6481}

* Um erro `NullPointerException` é visto nos registros em que é executado um trabalho de tradução (NPR-32220).

#### Integrações {#integrations-6481}

* Scripts entre sites para JSON (NPR-32745).

#### Comunidades {#communities-6481}

* Após criar um novo grupo, os autores não são redirecionados para a seção [!UICONTROL Community Group] em [!DNL Internet Explorer] 11 (NPR-33202).
* Ocorre um erro ao acessar a página [!UICONTROL Fluxo de Atividade] (NPR-33152).
* Editar um grupo [!DNL Communities] e alterar a imagem em miniatura não atualiza a imagem em miniatura do grupo (NPR-32603).
* Ao criar uma versão de notificações e subscrições de Conteúdo gerado pelo usuário (UGC), uma ID incorreta da página de origem é armazenada (CQ-4289703).
* Problema de script entre sites (NPR-33212).

#### Fluxo de trabalho {#workflow-6481}

* Alguns componentes não são exibidos na caixa de diálogo que aparece quando um usuário conclui um fluxo de trabalho que inclui uma [!UICONTROL etapa Participante da caixa de diálogo] (NPR-32989).

* A opção [!UICONTROL Linha do tempo] no painel esquerdo demora mais tempo para carregar do que o esperado (NPR-32850).

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack não inclui correções para AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. Para obter mais informações, consulte [Instalar o pacote suplementar da AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

* Gerenciamento de correspondência: Quando um usuário cola o conteúdo de um documento [!DNL Word], o fragmento do documento de texto não retém a formatação (NPR-33213).
* Forms adaptável: Uma nova linha de uma string em um dicionário de formulários adaptáveis adiciona `&#xa;` caracteres ao dicionário (NPR-33265).
* Forms adaptável: O usuário não pode salvar um formulário adaptável com mais de um anexo (NPR-33214).
* Forms adaptável: Os métodos `AddInstance` e `RemoveInstance` para a classe Instance Manager não adicionam um número dinâmico de instâncias para fragmentos de carregamento lento em [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptável: O Analytics ativado em um formulário adaptável incorporado em uma página [!DNL Sites] não registra dados para eventos Enviar e Abandonar (NPR-31359).
* Forms adaptável: Quando um usuário cola o conteúdo de um documento [!DNL Word] em um formulário adaptável e o envia, o formulário adaptativo enviado inclui caracteres unicode. Além disso, a conversão de PDF em PDF/A falha devido a caracteres unicode (NPR-33348).
* BackendIntegration: As solicitações do modelo de dados de formulário falham, pois o token de atualização expira devido ao estado inativo incorreto (NPR-33168).
* Serviços do documento: Falha do serviço de conversão de PDF ao converter documentos PDF em PostScript devido à ausência de jars Gibson para [!DNL WebLogic] no servidor [!DNL Linux] (NPR-33515, CQ-4292239).
* Serviços do documento: Quando um usuário converte um arquivo de texto em PDF, os caracteres japoneses não são renderizados corretamente (NPR-33239).
* XSS armazenado com o GuideSOMProviderServlet (NPR-32701).

## Instalar 6.4.8.3 {#install}

### Requisitos de configuração {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para clientes com Pacotes de recursos instalados no AEM 6.4. Os pacotes de recursos opcionais fornecidos pelo Adobe têm dependências na versão de lançamento e nos service packs. Se você tiver algum Feature Pack instalado, entre em contato com a equipe de Atendimento ao cliente da AEM para validar a compatibilidade desses pacotes de recursos com este pacote de correções cumulativas para AEM 6.4.

* AEM 6.4.8.3 requer AEM 6.4.8.0. Visite [documentação de atualização](../sites-deploying/upgrade.md) para obter instruções detalhadas.
* Em uma implantação com MongoDB e várias instâncias, instale o AEM 6.4.8.3 em uma das instâncias do autor usando o Gerenciador de pacotes.
* Antes de instalar o pacote de correção cumulativo, certifique-se de ter um instantâneo ou um backup atualizado da instância AEM.
* Reinicie a instância antes da instalação. Embora isso seja necessário apenas quando a instância ainda está no modo de atualização (e esse é o caso quando a instância foi atualizada de uma versão anterior), geralmente é recomendado se a instância estava sendo executada por um período de tempo maior.

>[!NOTE]
>
>A Adobe não recomenda remover ou desinstalar o pacote AEM 6.4.8.3.

### Instale o Cumulative Fix Pack {#install-cumulative-fix-pack}

Execute as seguintes etapas para instalar o Cumulative Fix Pack em uma instância do AEM 6.4.8.0 existente:

1. Clique no link [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip) para baixar o pacote.

1. Abra [Gerenciador de pacotes](http://localhost:4502/crx/packmgr/index.jsp) e clique em **[!UICONTROL Carregar pacote]** para fazer upload do pacote.

1. Selecione o nome do pacote e clique em **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**A caixa de diálogo na interface do usuário do Gerenciador de pacotes às vezes sai imediatamente durante a instalação da versão 6.4.8.3**
>
>Portanto, é recomendável aguardar a estabilização dos registros de erros antes de acessar a instância. O usuário deve aguardar registros específicos relacionados à desinstalação do pacote do atualizador antes de ter certeza de que a instalação foi bem-sucedida. Geralmente isso acontece no Safari, mas pode acontecer intermitentemente em qualquer navegador.

### Instalação automática {#auto-installation}

Há duas maneiras de instalar automaticamente o AEM 6.4.8.3 em uma instância em execução:

A. Coloque a embalagem em ..*/crx-quickstart/install* enquanto o servidor estiver em execução. O pacote é instalado automaticamente.

B. Use a [API HTTP do Package Manager](https://docs.adobe.com/content/docs/pt/crx/2-3/how_to/package_manager.html) - certifique-se de usar `cmd=install&recursive=true` - para que o pacote aninhado esteja instalado.

>[!NOTE]
>
>O AEM 6.4.8.3 não oferece suporte à instalação do Bootstrap.

### Validar instalação {#validate-install}

1. A página Informações do produto (*/system/console/productinfo*) agora deve mostrar a string da versão atualizada &quot;Adobe Experience Manager, Versão 6.4.8.3&quot; em Produtos instalados.
1. Todos os pacotes OSGI são ATIVOS ou FRAGMENTOS no Console OSGi (Use o console da Web: /system/console/bundles).
1. O pacote OSGI org.apache.Jackrabbit.oak-core está na versão 1.8.17 ou superior (Use o console da Web: /system/console/bundles).

Para determinar a plataforma certificada para execução com esta versão do AEM Sites e do Assets, consulte [Requisitos técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Na instalação bem-sucedida do pacote, uma mensagem informativa é exibida indicando que o pacote de conteúdo foi instalado com êxito, como **&quot;Content Package AEM-6.4-Service-Pack-8 instalado com êxito.&quot;**

### Atualizar visualizadores do Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.3 contém a nova versão dos visualizadores do Dynamic Media (5.10.1) que ativa a verificação de nomes de duplicados na página Predefinição de imagem. Os clientes da Dynamic Media devem executar o seguinte comando para exibir as predefinições do visualizador de caixa para um estado atualizado.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará novas predefinições do visualizador para o local /conf.

### Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] libera os pacotes de complementos uma semana após a data de lançamento programada do Pacote de correções  [!DNL Experience Manager] cumulativas.

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms. As correções do AEM Forms são entregues por meio de um pacote complementar separado.

1. Verifique se você instalou o AEM Cumulative Fix Pack.
1. Baixe o pacote suplementar de formulários correspondente listado em [Versões da AEM Forms](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) para seu sistema operacional.
1. Instale o pacote de complementos de formulários conforme descrito em [Instalar pacotes de suplementos de formulários AEM](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Instalar o instalador AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms no JEE. As correções no JEE do AEM Forms são entregues por meio de um instalador separado.

Para obter informações sobre como instalar o instalador cumulativo para AEM Forms JEE e configuração pós-implantação, consulte [AEM Forms JEE Patch Installer](jee-patch-installer-64.md).

### Uber Jar {#uber-jar}

A barra do usuário para AEM 6.4.8.3 está disponível no [repositório do Maven Central](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.3/).

Para usar o Uber Jar em um projeto Maven, consulte o artigo [Como usar o Uber jar](../sites-developing/ht-projects-maven.md) e inclua a seguinte dependência no POM do seu projeto:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.3</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>O UberJar e outros artefatos relacionados estão disponíveis no Repositório Central Maven em vez do repositório do Adobe Public Maven (repo.adobe.com). O arquivo UberJar principal é renomeado para `uber-jar-<version>.jar`. Como resultado, não há `classifier`, com `apis` como valor, para a tag `dependency`.

## Recursos removidos/obsoletos {#removed-deprecated-features}

Esta seção lista os recursos e funcionalidades removidos ou descontinuados do AEM 6.4.

| Área | Recurso | Substituição | Versão |
|---|---|---|---|
| Ativos | Gerenciar ação de tag para subativos | Nenhuma substituição | AEM 6.4.2.0 |
| Integração do Assets e da Adobe Creative Cloud | [O AEM para o compartilhamento de pastas do Creative Cloud ](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) foi introduzido no AEM 6.2 como uma forma de fornecer aos usuários criativos acesso aos ativos do AEM. Uma nova funcionalidade lançada no aplicativo da Creative Cloud, o Adobe Asset Link, fornece uma experiência de usuário melhor e acesso avançado a ativos do AEM diretamente do Photoshop, InDesign e Illustrator. A Adobe não fará mais aprimoramentos no recurso de compartilhamento de pastas. Embora o recurso esteja incluído no AEM, os clientes são aconselhados a usar a substituição. | Adobe Asset Link ou aplicativo de desktop. Para obter mais informações, consulte o artigo [Integração da AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problemas conhecidos {#known-issues}

* Se você atualizar de [!DNL Experience Manager] 6.4 para [!DNL Experience Manager] 6.5, alguns dos pacotes talvez não exibam seu status como `Active`. Instale o Service Pack mais recente do [!DNL Experience Manager] 6.5 para resolver o problema.

Para obter informações sobre os problemas conhecidos do AEM 6.4.8.0 Service Pack, consulte [AEM 6.4.8.0 Service Pack Release Notes](sp-release-notes.md).

## Pacotes de conteúdo e pacotes OSGi incluídos {#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de conteúdo incluídos no AEM 6.4.8.3.

Lista de pacotes OSGi incluídos no AEM 6.4.8.3

[Obter arquivo](assets/6.4.8.3_osgi_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.8.3

[Obter arquivo](assets/6.4.8.3_content_packages.txt)

## Recursos úteis {#helpful-resources}

* [Notas de versão do AEM 6.4](../release-notes/release-notes.md)
* [Página do produto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentação do AEM 6.4](https://helpx.adobe.com/support/experience-manager/6-4.html)
* Inscreva-se em [atualizações de produtos de prioridade de Adobe](https://www.adobe.com/subscription/priority-product-update.html)

## Sites restritos {#restricted-sites-new}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Entre em contato com o Suporte ao cliente](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
