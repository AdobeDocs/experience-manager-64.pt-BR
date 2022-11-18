---
title: Notas de versão do AEM 6.4 Cumulative Fix Pack
description: Notas de versão específicas dos Pacotes de correção cumulativos do Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '4681'
ht-degree: 16%

---

# Notas de versão do AEM 6.4 Cumulative Fix Pack  {#aem-cumulative-fix-pack-release-notes}

## Informações da versão {#release-information}

<!-- TBD: Update the SD URL. -->

| Produtos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versão | 6.4.8.4 |
| Tipo | Cumulative Fix Pack |
| Data | 25 de fevereiro de 2021 |
| Pré-requisitos | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de download | [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## O que está incluído no AEM 6.4.8.4 {#what-s-included-in-aem}

O AEM Cumulative Fix Pack 6.4.8.4 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0), em março de 2020.

O AEM 6.4.8.4 é um Cumulative Fix Pack (CFP) que depende do AEM 6.4 Service Pack 8. Instale o CFP após instalar o AEM 6.4 Service Pack 8.

Os principais recursos e aprimoramentos introduzidos no [!DNL Adobe Experience Manager] 6.4.8.4 são:

* Capacidade de ativar ou desativar o [!DNL Experience Manager Forms] alterações no registro ao executar uma conversão de PDFG.

* Autenticação com certificado X-509 para serviços da Web baseados em SOAP no modelo de dados de formulário.

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.24.

Para obter informações sobre o CFP e outros tipos de versões, consulte [AEM Atualizar Definições do Veículo de Liberação](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.4 fornece correções para os seguintes problemas.

### Sites {#sites-6484}

* Depois de instalar o Experience Manager Service Pack 6.4.8.2, os usuários não podem editar modelos de fragmento de conteúdo e experimentar o seguinte erro:

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Quando um usuário clica no botão de logout, ele não é desconectado do Gerenciador de Pacotes. (NPR-35161)
* Após a atualização do Experience Manager 6.4.x para o Experience Manager 6.4.8.3, os usuários não podem publicar uma página por meio da opção Gerenciar publicação. (CQ-4312511)
* Quando você move uma página secundária do blueprint de volta ao local original, a configuração cq:liveSyncConfig não é removida de uma página secundária da live copy. (NPR-35900)
* Quando você move um blueprint que tem live-copies para frente e para trás, somente a primeira movimentação funciona, então ela falha e nenhuma mensagem de erro é exibida. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` causes `OutOfMemoryError` erro, pois a funcionalidade de marcação inteligente cria grandes `/oak:index/lucene` e `/oak:index/ntBaseLucene` índices (NPR-35650).
* Os usuários não podem fazer check-in de ativos depois de editá-los em [!DNL Adobe InDesign] e receber erro sobre falta de permissões (NPR-35340).
* Quando uma nova versão de um ativo existente é criada após resolver o conflito de nomes, os metadados do ativo original são substituídos (NPR-35939).
* Os grupos gerados automaticamente por pasta privada não são mantidos e não são removidos ao excluir a pasta ou ao atualizar a pasta com o [!UICONTROL Remover restrições de pasta privada] conjunto de opções (NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* O erro intermitente do ImageServer causa a resposta 403 e a consequente falha de algumas funcionalidades do [!DNL Experience Manager]. (CQ-4308565)

### Integrações {#integrations-6484}

* Ao abrir as propriedades de uma página após a atualização para o Experience Manager 6.4.8.3, os erros de JavaScript começam a aparecer no console (NPR-35649).

### Forms {#forms-6484}

>[!NOTE]
>
>O [!DNL Experience Manager Forms] lança os pacotes complementares uma semana após a data programada de lançamento do [!DNL Experience Manager] Cumulative Fix Pack.

**Gerenciamento de correspondência**

* Ao editar uma carta, os módulos com condições levam mais tempo para serem carregados (NPR-35326).

* Ao editar uma carta, os vínculos de conteúdo e dados não são exibidos na interface do usuário (CQ-4312905).

**Serviços de documento**

* Não é possível montar PDF após a atualização [!DNL JAVA] para [!DNL JDK1.8.0_261] (NPR-35761, NPR-35848)

**Foundation JEE**

* Ao editar uma notificação de tarefa em [!DNL Forms] não é possível salvá-lo (CQ-4315055).

**Problemas corrigidos no AEMForms-6.4.0-0027**

* (Somente JEE) Vulnerabilidades críticas de segurança (CVE-2021-44228 e CVE-2021-45046) relatadas para o Apache Log4j2.

Para obter informações sobre atualizações de segurança, consulte [Página de boletins de segurança do Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Correções e Feature Packs incluídos em Cumulative Fix Packs anteriores {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0), em março de 2020.

O AEM 6.4.8.3 é um Cumulative Fix Pack (CFP) que depende do AEM 6.4 Service Pack 8. Instale o CFP após instalar o AEM 6.4 Service Pack 8.

No AEM 6.4.8.3, o repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.23.

Para obter informações sobre o CFP e outros tipos de versões, consulte [AEM Atualizar Definições do Veículo de Liberação](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.3 fornece correções para os seguintes problemas.

#### Sites {#sites-6483}

* Ao atualizar o texto de uma variação de um fragmento de conteúdo, o conteúdo do fragmento de conteúdo principal é atualizado em vez da variação (NPR-35080).

* Ao definir um valor numérico para a propriedade de rótulo do tipo String de um componente, exclua o componente e use a opção de desfazer para trazê-lo de volta, o tipo de propriedade de rótulo muda automaticamente de String para Long (NPR-34738).

* Quando você adiciona um componente de Upload de arquivo a vários campos, o caminho da imagem é armazenado no nó do componente, em vez do nó Vários campos (NPR-34423).

* No assistente para Mover página, mesmo se nenhum destino estiver selecionado, o botão seguinte permanecerá ativado (NPR-34460).

* Quando o componente pai inclui a variável `cq:isContainer` , o componente herdado não inclui automaticamente a propriedade (CQ-4308409).

* Ao usar minificação de CSS usando `calc()` , os espaços em branco ao redor da função `+` são removidos (NPR-34991).

* Quando você inicia uma instância AEM, a variável `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` e `com.adobe.granite.maintenance.impl.TaskScheduler` os componentes não são exibidos em `Active` (NPR-34952).

#### [!DNL Assets] {#assets-6483}

* Ao criar uma versão de um ativo existente, as atualizações de usuário nos metadados não persistem se um perfil de metadados for aplicado à pasta (NPR-34833).
* Ao usar [!DNL Adobe Asset Link] com [!DNL Adobe InDesign], os resultados da pesquisa não contêm pastas e coleções, mas contêm apenas ativos (NPR-34700).
* Ao arrastar um ativo em uma pasta para movê-lo, a interface do usuário também exibe a opção para [!UICONTROL Soltar no Lightbox] e [!UICONTROL Quebra na coleção]. Mesmo que a operação de movimentação seja cancelada, a interface do usuário continua exibindo as duas últimas opções (NPR-34525).
* Quando a interface Gerenciar publicação é aberta, a opção de publicação não está disponível e, ao selecionar a opção de cancelamento da publicação, a página de escopo fica em branco (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* Nas configurações de Predefinição de imagem, quando a opção [!UICONTROL Ativar a redução da amostragem do JPG Chrominance] está desmarcado em [!DNL Experience Manager], a alteração não sincroniza com [!DNL Dynamic Media] (NPR-34284)
* No [!UICONTROL Editor de predefinições do visualizador]ao editar [!UICONTROL PanorâmicaImage/PanorâmicaImage_VR] predefinição, no `PanoramicView` componente, o `PANORAMICVIEW_AUTOROTATE` O rótulo do modificador não está disponível (CQ-4302043).
* Desfazer a publicação de um vídeo de [!DNL Experience Manager] não cancela a publicação do Adaptive Video Set no Dynamic Media Classic configurado. (CQ-4304405).

#### Plataforma {#platform-6483}

* O `emitUseStrict` é adicionado um sinalizador à função de processador Google Closure Compiler (GCC) `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. O sinalizador suprime a saída do `use strict` (NPR-34830).
* A `NullPointerException` é retornado ao iniciar tarefas de manutenção diárias ou semanais (NPR-34702).
* O [!DNL Apache Sling Health Check] A ferramenta está obsoleta. Em vez disso, use [Detector de padrões](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) para detectar violações de conteúdo (NPR-33929).

#### Integrações {#integrations-6483}

* O [!UICONTROL Criar] é exibido no [!UICONTROL Públicos-alvo] ao navegar de uma pasta para a [!UICONTROL Públicos-alvo] página (NPR-35152).

#### Interface do usuário {#ui-6483}

* O [!UICONTROL Filtros] painel de pesquisa em [!UICONTROL Omnisearch] a interface do usuário também retorna resultados de locais diferentes de onde a pesquisa é executada (NPR-34877).
* Ao fechar o [!UICONTROL Filtros] no painel [!UICONTROL Omnisearch] interface do usuário, o painel esquerdo não é redefinido para [!UICONTROL Conteúdo] , o que impede a reabertura da variável [!UICONTROL Filtros] painel (NPR-34483).
* A `NullPointerException` é retornado ao acessar as propriedades da página (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Todas as instâncias de terminologia não equitativa no produto são substituídas por equivalentes aceitos (NPR-34506).

#### Commerce {#commerce-6483}

* Quando há mais de 15 produtos em uma coleção, a coleção exibe apenas os primeiros 15 produtos (NPR-34494).

#### Forms {#forms-6483}

>[!NOTE]
>
>O [!DNL Experience Manager Forms] lança os pacotes complementares uma semana após a data programada de lançamento do [!DNL Experience Manager] Cumulative Fix Pack.

>[!NOTE]
>
>[!DNL Experience Manager] O Cumulative Fix Pack não inclui correções para [!DNL Experience Manager Forms]. Eles são entregues usando um [!DNL Forms] pacote complementar. Além disso, é lançado um instalador cumulativo que inclui correções para [!DNL Experience Manager Forms] no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulários adaptáveis**

* Não é possível editar um formulário adaptável usando a interface clássica depois de aplicar a variável [!DNL Experience Manager] Cumulative Fix Pack (NPR-35127).

* Os fragmentos levam mais tempo para carregar em um formulário adaptável devido à invalidação do cache (NPR-34655).

* Acessibilidade: A navegação por guias não funciona adequadamente para leitores de tela em um formulário adaptável (NPR-34550).

**Gerenciamento de correspondência**

* Ao migrar os ativos do ES3, os ativos incluem duas condições padrão não editáveis (NPR-34971).

**Foundation JEE**

* Migrar [!DNL AEM Forms] usuários do Flash para o HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

O AEM Cumulative Fix Pack 6.4.8.2 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0), em março de 2020.

O AEM 6.4.8.2 é um Cumulative Fix Pack (CFP) que depende do AEM 6.4 Service Pack 8. Instale o CFP após instalar o AEM 6.4 Service Pack 8.

No AEM 6.4.8.2, o repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.22.

Para obter informações sobre o CFP e outros tipos de versões, consulte [AEM Atualizar Definições do Veículo de Liberação](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.2 fornece correções para os seguintes problemas.

#### Sites {#sites-6482}

* Se a variável `RolloutConfigManagerFactoryImpl` não é possível carregar uma configuração de implementação, ela não tenta carregar as configurações ausentes. Retorna as configurações em cache (NPR-34091).
* No componente principal de Texto, depois de usar a opção de edição de HTML de origem, a classe de `em` for removida (NPR-34080).
* Ao atualizar do Experience Manager 6.2 para o Experience Manager 6.5, o componente Parsys de modelos estáticos não é exibido corretamente. A altura do componente Parsys é definida como 0 e os componentes dentro dele não ficam visíveis (NPR-34044).
* As informações do rótulo não são exibidas dos componentes permitidos no Editor de modelo (NPR-33908).

   ![Rótulos ausentes no contêiner de layout](assets/33908_missing_labels.png)

* Os usuários não podem adicionar ou editar componentes ao parsys após o quarto nível de componentes aninhados (NPR-33873).
* Se o conteúdo inicial de um modelo editável for alterado e o modelo for publicado, quaisquer novas páginas criadas com esse modelo mostrarão a data de publicação do modelo, mesmo que as páginas não sejam publicadas (NPR-33822).
* O `cq:acLinks` e `cq:acUUID` propriedades para [!DNL Adobe Campaign] na cópia são removidas durante a operação de copiar e colar (NPR-33793).
* No [!UICONTROL Uso em tempo real] , somente 49 resultados são exibidos. Não mostra todo o uso do componente (NPR-33710).
* Uma página da Web com `/` no URL fica sem resposta durante a criação. Quando um componente é adicionado durante a criação, o uso da CPU aumenta e o navegador para de responder (NPR-33625).
* No modo de edição em linha no [!DNL RTE], arrastar uma imagem não funciona para o componente de Texto (NPR-33579).
* É possível criar um componente em uma página do blueprint com o mesmo nome do nome da página. Durante a implantação, esse componente é renomeado por sufixo `_msm_moved`. No entanto, o componente é movido para o final do [!UICONTROL Sistema de parágrafo] (NPR-33534)
* A promoção do Launch não publica páginas quando [!UICONTROL incluir subpáginas] não está marcada na primeira raiz de conteúdo (NPR-33533).
* Redirecionar para [!DNL Experience Manager] página com âncora não funciona na instância Autor como `PageRedirectServlets` O coloca a string de consulta após um fragmento de URL ou uma âncora (NPR-34287).
* `PageRedirectServlet` appends `.html` após o mapeamento do Sling, resultando em falhas de link (NPR-34271).
* Você pode suspender o [!DNL Live Copy] de uma página e a herança são quebradas no modo Editor . No entanto, nas propriedades da Página, o ícone que representa a herança indica incorretamente que a herança existe e não está quebrada (NPR-34096).
* Problema com a exibição de componentes permitidos na página Editar modelo (CQ-4297295).
* Depois de atualizar o Chrome e o Firefox, os menus pop-up não estão funcionando como esperado. Ao carregar as propriedades da página, ele não exibe o painel quando há dados nele (CQ-4292995).
* Várias instâncias de script entre sites em [!DNL Experience Manager Sites] componentes (NPR-33926).
* As entradas do usuário não são adequadamente codificadas para vários componentes ao enviar informações para o cliente (NPR-33696).
* Um URL que termina com `childrenlist.html` exibe uma HTML page em vez de uma resposta 404. Esses URLs são vulneráveis a scripts entre sites (NPR-33441).

#### Assets {#assets-6482}

* A extração de texto para os arquivos PDF carregados não funciona e a pesquisa de texto completo por algumas palavras em um arquivo PDF não consegue buscar esse arquivo PDF (NPR-34165).

   >[!NOTE]
   >Para fazer essa correção funcionar, reinicie a instância do Adobe Experience Manager após instalar o Service Pack 6.4.8.2.

* As barras invertidas são adicionadas antes de caracteres especiais nas sugestões de pesquisa de ativos, que têm caracteres especiais em seu nome (NPR-33833).

* Os filtros personalizados salvos como coleções inteligentes não são aplicados corretamente a ativos, portanto, os resultados da pesquisa não são precisos (NPR-33725).

* A linha do tempo de um ativo em uma pasta que foi reordenada mostra que o ativo foi movido (NPR-33580).

* Cancelar a publicação dos ativos em massa de [!DNL Brand Portal] resulta em `Request-URI Too Long` erro (NPR-34158).

* Na exibição de coluna se o usuário selecionar [!UICONTROL Filtro] após selecionar um conjunto de ativos (os ativos são desmarcados) e, em seguida, selecionar um conjunto diferente de ativos para mover, os ativos selecionados anteriormente também serão movidos para o novo local (NPR-34018).

* A barra de rolagem não está visível na exibição em lista, mesmo se houver vários ativos para caber na página (NPR-34156).

* O [!UICONTROL Gerenciar publicação] A página de ativos está quebrada e as opções nela não estão funcionando (CQ-4302509).

**Dynamic Media**

* A funcionalidade Recorte inteligente falha com um erro quando o perfil de imagem é adicionado a uma pasta com várias (por exemplo, 11) proporções (NPR-34083).

* Alterações nas predefinições de imagens em [!UICONTROL Adobe Experience Manager] não sincronizar com o Dynamic Media Classic (NPR-34284, CQ-4299713).

* O [!UICONTROL PANORAMICVIEW_AUTOROTATE] o rótulo do modificador está ausente no [!UICONTROL Comportamento] em [!UICONTROL Editor de predefinições do visualizador] página (CQ-4302043).

#### Plataforma {#platform-6482}

* Os valores padrão da variável **[!UICONTROL Tempo limite da conexão]** e **[!UICONTROL Tempo limite do soquete]** as configurações para a configuração do Agente padrão (publicar) não foram especificadas (NPR-33708).
* O programador de tarefas de manutenção inicia e interrompe as tarefas de manutenção com demasiada frequência do que o configurado (NPR-33520).
* Não é possível baixar logs usando a ferramenta Diagnosis em uma instância do Experience Manager atualizada (NPR-34419).

#### Integrações {#integrations-6482}

* O valor de `library_path` não é considerado ao gerar [!DNL Adobe Launch] URL da biblioteca para bibliotecas migradas do [!DNL Adobe Dynamic Tag Management]. Além disso, as bibliotecas migradas usam um prefixo diferente do [!DNL Adobe Launch] bibliotecas. (NPR-34238).
* As propriedades herdadas de um serviço de nuvem não persistem na atualização das propriedades da página (NPR-33865).

#### Interface do usuário {#ui-6482}

* A exibição da contagem de ativos selecionados em uma página de pesquisa está incorreta (NPR-33540).

#### Comunidades {#communities-6482}

* Os usuários existentes de um grupo da comunidade adicionados pelo Admin Console são removidos da lista de usuários em qualquer modificação no console de grupo da comunidade (NPR-34312).

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] O Cumulative Fix Pack não inclui correções para [!DNL Experience Manager Forms]. Eles são entregues usando um [!DNL Forms] pacote complementar. Além disso, é lançado um instalador cumulativo que inclui correções para [!DNL Experience Manager Forms] no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Formulários adaptáveis**

* Quando há um fragmento de formulário adaptável ausente, o formulário adaptável não é renderizado (NPR-34303).

* A descrição do conteúdo da ajuda para campos de formulário adaptáveis exibe uma tag HTML de parágrafo (NPR-34117).

* Ao adicionar um contêiner Forms em um [!DNL Experience Manager Sites] , a página exibe a seguinte mensagem de erro e não permite adicionar novos componentes (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Ao selecionar a variável **[!UICONTROL Revalidar no servidor]** e carregar vários anexos, o formulário adaptável não é enviado (NPR-33701).

* Ao selecionar a variável **[!UICONTROL Usar idioma da página]** e **[!UICONTROL O formulário cobre a largura inteira da página]** opções em [!DNL Experience Manager Forms] em um [!DNL Experience Manager Sites] a página não é traduzida (NPR-33641).

* Ao enviar um formulário adaptável habilitado para análise incorporado em um [!DNL Experience Manager Sites] , o analytics não funciona corretamente (NPR-31359).

* Remoção de dependências em [!DNL Lodash] e [!DNL backbone] bibliotecas (NPR-33458).

* O **[!UICONTROL Enviar para ponto de extremidade REST]** a ação de envio não funciona para um formulário adaptável (NPR-34513).

* Acessibilidade: Ao tentar enviar um formulário adaptável sem fazer upload de um anexo para um campo obrigatório, o foco não é alternado para o campo de anexo automaticamente (NPR-34511).

* As entradas do usuário não são adequadamente codificadas para [!DNL Forms] componentes ao enviar informações para o cliente (NPR-33611).

**Fluxo de trabalho**

* [!DNL Experience Manager] A operação de limpeza de workflow falha e exibe a seguinte mensagem de erro (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Ao instalar [!DNL Experience Manager] 6.4.8.1. [!UICONTROL A fazer] lista de itens não é exibida como links. O texto para a [!UICONTROL A fazer] os itens incluem tags HTML (NPR-34318).

**BackendIntegration**

* Não é possível configurar um modelo de dados de formulário em um AWS hospedado [!DNL Experience Manager Forms Linux] ambiente (NPR-33617).

**Designer**

* When [!DNL Acrobat DC] está instalado em um [!DNL Experience Manager] servidor Forms, o **[!UICONTROL Distribuir formulário]** não está disponível em [!DNL Experience Manager Designer] versão 6.x (NPR-34325).

**Segurança de documentos**

* Não é possível executar a operação Assinar com certificados baseados em HSM em um arquivo de PDF após a instalação [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Atualização**

* Ao atualizar o [!DNL JBoss] versão para 7.0.9 para [!DNL Experience Manager Forms] com segurança de documentos em um [!DNL Linux] , resulta em um erro (CQ-4300546).

Para obter informações sobre atualizações de segurança, consulte [Página de boletins de segurança do Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

O AEM Cumulative Fix Pack 6.4.8.1 é uma atualização importante que inclui várias correções internas e de clientes desde a disponibilização geral do AEM 6.4 Service Pack 8 (6.4.8.0), em março de 2020.

O AEM Cumulative Fix Pack 6.4.8.1 é dependente do AEM 6.4 Service Pack 8. Portanto, você deve instalar o pacote AEM Cumulative Fix Pack 6.4.8.1 após instalar AEM 6.4 Service Pack 8.

Alguns dos principais destaques do AEM 6.4.8.1 são:

* O acesso anônimo ao CRXDE Lite não tem permissão para melhorar a segurança. Em vez disso, os usuários são direcionados para a tela de logon. Consulte [desenvolvimento com o CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Remoção da integração de Compartilhamento de pacotes com a Adobe Experience Manager.
* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.21.

Para obter informações sobre o CFP e outros tipos de versões, consulte [AEM Atualizar Definições do Veículo de Liberação](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

O Adobe Experience Manager 6.4.8.1 fornece correções para os seguintes problemas.

#### Sites {#sites-6481}

* Usuários anônimos podem acessar os recursos do CRX DE Lite (NPR-33522).
* Quando o nome de um componente local em uma LiveCopy é idêntico ao nome de um componente no blueprint e o componente é implementado a partir do blueprint, o termo _msm_moved não é adicionado ao nome do componente local (NPR-33207).
* Os parâmetros anexados à solicitação original não são incluídos no URL de redirecionamento (NPR-33174).
* Quando a opção Coral.Select define emptyOption=true ou contém um item padrão com valor = &quot;&quot;, o arquivo dropdownshowhide.js encontra um erro: TypeError não captado: component.getValue não é uma função (NPR-33163).
* Quando um componente inclui outro componente como recurso de sly de dados, o espaço reservado do componente do contêiner pai é substituído pelo espaço reservado dos componentes internos (NPR-33119).
* Ao basear um Fragmento de conteúdo em um esquema e ele contiver uma área de texto obrigatória ou um campo de caminho, o Fragmento de conteúdo não será salvo (NPR-33007)
* Ao criar um componente personalizado usando o componente de fragmento de experiência pronto para uso e usá-lo nas páginas do AEM Sites, o AEM não exibe referências (uso) para o componente personalizado (NPR-32852).
* Quando uma página do AEM Sites faz parte de um grande conjunto de conteúdo com várias live-copies, a visualização do histórico da versão da página não é carregada (NPR-32772).
* Quando você promove um lançamento, ele adiciona a combinação &quot;cq:LiveRelationship&quot; a cada componente adicionado ao lançamento. Isso afeta todas as inicializações independentemente de uma inicialização ser criada com ou sem selecionar a opção — Herdar dados online da página de origem — (NPR-32664).
* Quando a paginação é iniciada, o Seletor de fragmentos de experiência não carrega todos os itens (NPR-32605).
* Não é possível criar um lançamento para uma página do AEM Sites. A criação do Launch resulta em um erro (NPR-32544).
* Gerenciar publicação não inclui ativos referenciados no fluxo de trabalho de solicitação de ativação (NPR-32463).
* Exibição da verificação de integridade do Dispatcher `Invalid cookie header` mensagem de aviso nos arquivos de log (NPR-33630).
* A integração do Salesforce é vulnerável ao SSRF (NPR-32671).
* XSS refletido em PreferencesServlet (NPR-33439).

#### Ativos {#assets-6481}

* A contagem de ativos não é alterada de acordo com a alteração na seleção na Exibição de lista (NPR-33285).

* O botão Avançar não é ativado ao selecionar o nó pai (onde uma única pasta filho está visível) e, em seguida, selecionar a pasta filho (NPR-33284).

* A interface do usuário de toque não é renderizada (com erro) para usuários que não têm acesso de leitura na raiz do repositório, quando o DMS7 ou o modo Híbrido está ativado (NPR-33175).

* Os caracteres GB18030 que ocorrem em pastas e nomes de ativos mudam para branco nos arquivos zip baixados (NPR-33150).

* A pasta extra é criada ao recortar inteligente um ativo que está dentro de uma pasta principal com ponto `.` em seu nome (NPR-32755).

* O carregamento lento não é acionado e não mais de 100 ativos são exibidos ao selecionar para revisar as tarefas da caixa de entrada de notificações (NPR-32749).

* A página de link para compartilhar a coleção está quebrada devido a alterações no coral-info (NPR-32510).

* O processamento de ativos enquanto o upload em massa fica preso (CQ-4293916).

* Vulnerabilidade SSRF no Experience Manager (NPR-33437).

#### Plataforma {#platform-6481}

* O [!DNL Sling] não é chamado se a variável `sling:match` a entrada do mapa é criada em `/etc/maps` (NPR-33308)
* Todos os agentes de limpeza são acionados ao desativar uma página (NPR-32941).
* Quando você usar a variável `ScriptProcessor` Para minimizar uma biblioteca JavaScript, o arquivo de log exibe uma mensagem de erro indicando que o código JavaScript não é compatível com o modo restrito. A API não fornece a opção para ativar ou desativar o modo estrito. (NPR-32746).
* Quando uma consulta SQL é executada por um tempo mais longo, por exemplo, 7 horas, AEM pára de responder (NPR-33043).

#### Interface do usuário {#ui-6481}

* Ao pesquisar ou navegar por um caminho usando uma caixa de diálogo de seleção, a caixa de diálogo de seleção exibe todo o conteúdo do nó JCR selecionado em vez de exibir somente as imagens (NPR-32712).

#### Projetos de tradução {#tranlation-6481}

* A `NullPointerException` é visto nos logs em execução de um trabalho de tradução (NPR-32220).

#### Integrações {#integrations-6481}

* Script entre sites para JSON (NPR-32745).

#### Comunidades {#communities-6481}

* Após criar um novo grupo, os autores não são redirecionados para a variável [!UICONTROL Grupo da comunidade] seção sobre [!DNL Internet Explorer] 11 (NPR-33202).
* Ocorre um erro ao acessar a variável [!UICONTROL Fluxo de atividade] página (NPR-33152).
* Edição de um [!DNL Communities] agrupar e alterar a imagem em miniatura não atualiza a imagem em miniatura do grupo (NPR-32603).
* Ao criar uma versão de notificações e assinaturas de Conteúdo gerado pelo usuário (UGC), uma ID incorreta da página de origem é armazenada (CQ-4289703).
* Problema de script entre sites (NPR-33212).

#### Fluxo de trabalho {#workflow-6481}

* Alguns componentes não são exibidos na caixa de diálogo que aparece quando um usuário conclui um fluxo de trabalho que inclui um [!UICONTROL Etapa da caixa de diálogo Participante] (NPR-32989)

* O [!UICONTROL Linha do tempo] no painel à esquerda, a opção leva mais tempo para carregar do que o esperado (NPR-32850).

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

* Gerenciamento de correspondência: Quando um usuário cola o conteúdo de um [!DNL Word] documento, o fragmento do documento de texto não retém a formatação (NPR-33213).
* Forms adaptável: Uma nova linha em uma sequência de caracteres em um dicionário de formulários adaptáveis adiciona `&#xa;` caracteres no dicionário (NPR-33265).
* Forms adaptável: O usuário não pode salvar um formulário adaptável com mais de um anexo (NPR-33214).
* Forms adaptável: `AddInstance` e `RemoveInstance` métodos para a classe do Gerenciador de Instâncias não adicionam um número dinâmico de instâncias para fragmentos de carregamento lento em [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptável: Analytics ativado em um formulário adaptável incorporado em um [!DNL Sites] não registram dados para eventos Enviar e Abandonar (NPR-31359).
* Forms adaptável: Quando um usuário cola o conteúdo de um [!DNL Word] para um formulário adaptável e enviá-lo, o formulário adaptável enviado inclui caracteres unicode. Além disso, a conversão de PDF para PDF/A falha devido a caracteres unicode (NPR-33348).
* BackendIntegration: As solicitações do modelo de dados de formulário falham, pois o token de atualização expira devido ao estado inativo incorreto (NPR-33168).
* Serviços de documento: A conversão do serviço PDF falha ao converter documentos PDF para PostScript devido à falta de jars Gibson para [!DNL WebLogic] no [!DNL Linux] server (NPR-33515, CQ-4292239).
* Serviços de documento: Quando um usuário converte um arquivo de texto em um PDF, os caracteres japoneses não são renderizados corretamente (NPR-33239).
* XSS armazenado com o GuideSOMProviderServlet (NPR-32701).

## Instalar 6.4.8.4 {#install}

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
>Para clientes com Feature Packs instalados no AEM 6.4. Os Feature Packs opcionais fornecidos pelo Adobe têm dependências da versão de lançamento e dos service packs. Se você tiver algum Feature Pack instalado, entre em contato com a equipe de Atendimento ao cliente da AEM para validar a compatibilidade desses pacotes de recursos com este fix pack cumulativo para o AEM 6.4.

* AEM 6.4.8.4 exige o AEM 6.4.8.0. Visite [documentação de atualização](../sites-deploying/upgrade.md) para obter instruções detalhadas.
* Em uma implantação com MongoDB e várias instâncias, instale o AEM 6.4.8.4 em uma das instâncias do autor usando o Gerenciador de pacotes.
* Antes de instalar o Cumulative Fix Pack, verifique se você tem um instantâneo ou um backup atualizado de sua instância de AEM.
* Reinicie a instância antes da instalação. Embora isso seja necessário apenas quando a instância ainda está no modo de atualização (e esse é o caso quando a instância acabou de ser atualizada de uma versão anterior), geralmente é recomendável se a instância estava em execução por um período de tempo mais longo.

>[!NOTE]
>
>A Adobe não recomenda remover ou desinstalar o pacote AEM 6.4.8.4.

### Instale o Cumulative Fix Pack {#install-cumulative-fix-pack}

Execute as seguintes etapas para instalar o Cumulative Fix Pack em uma instância do AEM 6.4.8.0 existente:

1. Clique no link [Distribuição de softwares](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) para baixar o pacote.

1. Abra [Gerenciador de pacotes](http://localhost:4502/crx/packmgr/index.jsp) e clique em **[!UICONTROL Fazer upload de pacote]** para fazer upload do pacote.

1. Selecione o nome do pacote e clique em **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**A caixa de diálogo na interface do usuário do Gerenciador de pacotes às vezes sai imediatamente durante a instalação da versão 6.4.8.4**
>
>Portanto, é recomendável aguardar a estabilização dos registros de erros antes de acessar a instância. O usuário precisa aguardar registros específicos relacionados à desinstalação do pacote do atualizador antes de ter certeza de que a instalação foi bem-sucedida. Geralmente isso acontece no Safari, mas pode acontecer intermitentemente em qualquer navegador.

### Instalação automática {#auto-installation}

Há duas maneiras de instalar automaticamente o AEM 6.4.8.4 em uma instância em execução:

A. Coloque o pacote em ..*/crx-quickstart/install* enquanto o servidor estiver em execução. O pacote é instalado automaticamente.

B. Use o [API HTTP do Gerenciador de pacotes](https://docs.adobe.com/content/docs/pt/crx/2-3/how_to/package_manager.html) - certifique-se de usar `cmd=install&recursive=true` - para que o pacote aninhado seja instalado.

>[!NOTE]
>
>O AEM 6.4.8.4 não oferece suporte à instalação do Bootstrap.

### Validar instalação {#validate-install}

1. A página Informações do produto (*/system/console/productinfo*) agora deve mostrar a cadeia de caracteres de versão atualizada do &quot;Adobe Experience Manager, versão 6.4.8.4&quot; em Produtos instalados.
1. Todos os pacotes OSGI são ATIVOS ou FRAGMENTOS no Console OSGi (Use o console da Web: /system/console/bundles).
1. O pacote OSGI org.apache.jackrabbit.oak-core é na versão 1.8.17 ou superior (Use o Console da Web: /system/console/bundles).

Para determinar a plataforma certificada para execução com esta versão do AEM Sites e do Assets, consulte [Requisitos técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Após a instalação bem-sucedida do pacote, uma mensagem informativa é exibida, indicando que o pacote de conteúdo foi instalado com êxito, como **&quot;Pacote de Conteúdo AEM-6.4-Service-Pack-8 instalado com êxito.&quot;**

### Atualizar visualizadores do Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

O AEM 6.4.8.4 contém uma nova versão dos visualizadores do Dynamic Media (5.10.1) que permite a verificação de nomes duplicados na página Predefinição de imagem. Os clientes do Dynamic Media são aconselhados a executar o seguinte comando para trazer as predefinições do visualizador prontas para o estado atualizado.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará novas predefinições do visualizador para o local /conf.

### Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>O [!DNL Experience Manager Forms] lança os pacotes complementares uma semana após a data programada de lançamento do [!DNL Experience Manager] Cumulative Fix Pack.

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms. As correções do AEM Forms são entregues por meio de um pacote complementar separado.

1. Certifique-se de ter instalado o Pacote de Correção Cumulativo AEM.
1. Baixe o pacote complementar de formulários correspondente listado em [Versões do AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) para seu sistema operacional.
1. Instale o pacote complementar de formulários conforme descrito em [Instalação de pacotes complementares AEM formulários](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Instalar o instalador do AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms no JEE. As correções no JEE do AEM Forms são entregues por meio de um instalador separado.

Para obter informações sobre como instalar o instalador cumulativo para AEM Forms JEE e configuração pós-implantação, consulte [Instalador de patches do AEM Forms JEE](jee-patch-installer-64.md).

>[!NOTE]
>
>Depois de instalar o instalador cumulativo do Experience Manager Forms no JEE, instale o pacote complementar mais recente do Forms, exclua o pacote do complemento Forms do `crx-repository\install` e reinicie o servidor.

### Uber Jar {#uber-jar}

O Uber Jar para AEM 6.4.8.4 está disponível na seção [Repositório central Maven](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

Para usar o Uber Jar em um projeto Maven, consulte o artigo [Como usar o Uber jar](../sites-developing/ht-projects-maven.md) e inclua a seguinte dependência no POM do projeto:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>O UberJar e outros artefatos relacionados estão disponíveis no Repositório Central Maven em vez do repositório Maven Adobe Public (repo.adobe.com). O arquivo UberJar principal é renomeado para `uber-jar-<version>.jar`. Como resultado, não há `classifier`, com `apis` como o valor, para a variável `dependency` .

## Recursos removidos/obsoletos {#removed-deprecated-features}

Esta seção lista os recursos e funcionalidades removidos ou descontinuados do AEM 6.4.

| Área | Recurso | Substituição | Versão |
|---|---|---|---|
| Ativos | Gerenciar ação de tag para subativos | Nenhuma substituição | AEM 6.4.2.0 |
| Integração do Assets e da Adobe Creative Cloud | [O compartilhamento de pastas do AEM para a Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) foi introduzido no AEM 6.2 como uma forma de fornecer aos usuários criativos acesso aos ativos do AEM. Uma nova funcionalidade lançada no aplicativo da Creative Cloud, o Adobe Asset Link, fornece uma experiência de usuário melhor e acesso avançado a ativos do AEM diretamente do Photoshop, InDesign e Illustrator. A Adobe não fará mais aprimoramentos no recurso de compartilhamento de pastas. Embora o recurso esteja incluído no AEM, os clientes são recomendados a usar a substituição. | Adobe Asset Link ou aplicativo de desktop. Para obter mais informações, consulte o artigo [Integração da AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problemas conhecidos {#known-issues}

* Se você atualizar de [!DNL Experience Manager] 6.4 a [!DNL Experience Manager] 6.5, alguns dos pacotes podem não exibir seu status como `Active`. Instale o mais recente [!DNL Experience Manager] 6.5 Service Pack para resolver o problema.

Para obter informações sobre os problemas conhecidos do AEM 6.4.8.0 Service Pack, consulte [Notas de versão do AEM 6.4.8.0 Service Pack](sp-release-notes.md).

## Pacotes OSGi e pacotes de conteúdo incluídos {#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de conteúdo incluídos no AEM 6.4.8.4.

Lista de pacotes OSGi incluídos no AEM 6.4.8.4

[Obter arquivo](assets/6.4.8.4_osgi_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.8.4

[Obter arquivo](assets/6.4.8.4_content_packages.txt)

## Recursos úteis {#helpful-resources}

* [Notas de versão do AEM 6.4](../release-notes/release-notes.md)
* [Página do produto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentação do AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=pt-BR)
* Inscreva-se em [Atualizações de produtos de prioridade da Adobe](https://www.adobe.com/subscription/priority-product-update.html)

## Sites restritos {#restricted-sites-new}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Entre em contato com o Suporte ao cliente](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
