---
title: 'Notas de versão do AEM 6.4 Service Pack '
seo-title: 'Notas de versão do AEM 6.4 Service Pack '
description: Notas de versão específicas do Adobe Experience Manager 6.4 Service Packs.
seo-description: Notas de versão específicas do Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
translation-type: tm+mt
source-git-commit: ba2dec27319c1c7094db9f08130a50164c8e9713
workflow-type: tm+mt
source-wordcount: '21534'
ht-degree: 24%

---


# Notas de versão do AEM 6.4 Service Pack {#aem-service-pack-release-notes}

## Informações da versão {#release-information}

| Produtos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versão | 6.4.8.0 |
| Tipo | Lançamento do Service Pack |
| Data | 05 de março de 2020 |
| URL de download | AEM 6.4.8.0 sobre distribuição [de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## O que está incluído no AEM 6.4.8.0 {#what-s-included-in-aem}

O AEM 6.4.8.0 é uma atualização importante que inclui novos recursos, melhorias importantes solicitadas pelo cliente e desempenho, estabilidade, melhorias de segurança, lançadas desde a disponibilização geral do AEM 6.4 em **abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.8.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns destaques principais desta versão do Service pack:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.20.

* A funcionalidade de quebra automática de texto é compatível com sites japoneses no WCM-RTE.

* O processamento de quebra de texto e quebra de linha é compatível com sites japoneses.

* Adicionado suporte para usar o método BUNSETSU para quebrar a frase e as linhas do idioma japonês nas posições apropriadas.

* A interface de usuário CCR para gerenciamento de correspondência agora suporta valores decimais para a localidade alemã.

* A integração do modelo de dados de formulário usando o serviço da Web SOAP agora oferece suporte a grupos de escolha ou atributos em elementos.

* O AEM Assets agora está configurado com o Brand Portal por meio da E/S da Adobe.

* Atualização da versão jQuery fornecida no ContextHub para 3.2.1.

## Lista de alterações {#list-of-changes}

### Sites {#sites}

* Quando um URL de uma página de AEM Sites contém um sinal de dois pontos ou de porcentagem, o navegador subjacente para de responder e os ciclos da CPU mostram um pico (NPR-32368, NPR-31917).
* Quando uma página de AEM Sites é aberta para edição e um componente é copiado, a ação de colar permanece indisponível para alguns espaços reservados (NPR-32328).
* O fluxo de trabalho de solicitação de ativação não inclui ativos referenciados (NPR-32304).
* Quando um Blueprint é criado, se o número de registros for superior a 80, somente os primeiros 80 registros serão exibidos. O Blueprint exibe linhas em branco para o restante dos registros (NPR-32058).
* Os usuários podem salvar um Fragmento de conteúdo sem fornecer informações nos campos obrigatórios (NPR-31988).
* A navegação automática não funciona para o caminho configurado em um Componente de fragmento de experiência principal (NPR-31921).
* Quando você altera o tipo de uma célula de tabela no Editor de Rich Text (RTE), o erro abaixo ocorre:
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Quando o conteúdo é movido dentro da mesma pasta, a opção de movimentação da página é desativada (NPR-31841).
* Adicionado suporte para dividir frases em japonês usando o método BUNSETSU e linhas de quebra na posição apropriada (NPR-31836).
* Ao editar um hiperlink no Editor de Rich Text (RTE), o caminho recém-selecionado não é salvo (NPR-31659).
* Ao excluir um componente de vários campos e desfazer a exclusão, o componente é restaurado, mas os dados não são restaurados (NPR-31617).

### Assets {#assets}

* Uma pasta sem nome é criada no SPS (Scene7 Publishing System) ao mover um ativo de uma pasta para outra no Experience Manager com a configuração do Dynamic Media Scene7 (NPR-32440).

* A página de detalhes de ativos de arquivos PDF não mostra botões de ação no Experience Manager em execução no modo Dynamic Media Scene7 (NPR-32316).

* As representações de ativos e vídeos não podem ser excluídas (NPR-32213).

* O ícone de calendário para ativação programada não é exibido na coluna Status (na interface clássica da lista de ativos DAM) para ativos cuja ativação está programada para uma data e hora posteriores (NPR-32198).

* A relação entre ativos é substituída quando os ativos estão relacionados a mais de um ativo usando Outros (NPR-32196).

* O botão Salvar não importa o Conjunto Remoto quando o usuário não tiver feito nenhuma alteração no Set Editor no Dynamic Media Client (NPR-32178).

* A ingestão de ativos PSD causa um pico na CPU e uma instância de autor de Experience Manager não responsivo (NPR-32165).

* Exceção de falta de memória observada quando um arquivo ZIP grande é carregado no Experience Manager DAM (NPR-32155).

* Os URLs do histórico de versões são exibidos no campo Referenciado por na página Propriedade dos ativos (NPR-31889).

* Cancelar a publicação do Brand Portal, na página Gerenciar publicação, falha em subpastas de uma pasta publicada (NPR-31835).

* O upload das codificações de vídeo do Dynamic Media falha quando a Configuração da nuvem do Scene7 é colocada em uma pasta privada `/conf` em vez de `/conf/global` (NPR-31779).

* A imagem não é vista na linha do tempo após a adição de anotações, no Experience Manager que está sendo executado no modo de execução Dynamic Media Scene7 (NPR-31754).

* O arquivo ZIP baixado do DAM não pode ser aberto usando o WinZip (NPR-31745).

### Integrações {#integrations-6480}

* Os menus suspensos **Empresa** e Conjunto de **Relatórios** ficam ocultos assim que a Origem **do** Relatórios é selecionada ao configurar o Adobe Analytics nos serviços em nuvem do Experience Manager (NPR-31729).

* As propriedades do Adobe Campaign não são limpas quando é feita uma cópia de idioma de um boletim informativo vinculado a um Adobe Campaign, enquanto a limpeza acontece quando um boletim informativo vinculado a um Adobe Campaign é copiado ou colado (NPR-32540).

* ReportSuitesServlet está vulnerável a SSRF (NPR-32161).

### Sling {#sling-6480}

* A sombreamento não determinístico da observação de recursos não está funcionando (CQ-4286466).

### Projetos {#projects-6480}

* O botão Criar não estará visível para o usuário mesmo se ele tiver permissão para criar um projeto na subpasta (NPR-31831).

* A funcionalidade para alternar entre Visualização de cartão, Visualização de Lista e Visualização de calendário não funciona após selecionar visualização de calendário em projetos (NPR-31829).

### Tradução {#translation-6480}

* A criação de projetos de tradução para vários idiomas gera o projeto somente para alguns idiomas em vez de todos e um erro (o resolvedor de recursos já está fechado) é observado no log (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Problemas de permissão levam à exibição de erros ao mover páginas em um blueprint (NPR-32610).

### Editor de página WCM {#wcm-page-editor-6480}

* O navegador para de responder ao tentar adicionar um componente a uma página com um formato de URL específico (NPR-32368, NPR-31917).

### Interface do usuário administrador do WCM {#wcm-admin-ui-6480}

* Gerenciar publicação não inclui ativos referenciados na solicitação de fluxo de trabalho de ativação (NPR-32304).

### Communities {#communities}

* Não é possível atualizar a imagem em miniatura do grupo para grupos (NPR-32603).

### Brand Portal {#brand-portal}

* Cancelar a publicação do schema de metadados no AEM Assets preenche uma mensagem de erro, embora o schema seja removido no backend (CQ-4286871).

### Interface do usuário do Foundation {#foundations-ui-6480}

* Caracteres inválidos são exibidos no URL adicionado a um componente Botão (NPR-32684).

### Forms {#forms}

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Designer: Se a opção de marcação estiver ativada, a borda do subformulário desaparecerá na saída PDF gerada (NPR-32546, NPR-32322).

* Designer: Se houver células unidas em uma tabela, o teste de acessibilidade falhará para o arquivo PDF de saída convertido de um formulário XDP usando o serviço de saída (NPR-32079).

* Segurança do Documento: Um arquivo PDF protegido falha ao abrir offline com a opção DisableGlobalOfflineSynchronizationData definida como True (NPR-32080).

* Segurança do Documento: Problemas ao abrir um arquivo PDF protegido após a atualização do ES4 para o AEM 6.3 (NPR-32170).

* Serviços do Documento: Uma mensagem de erro é exibida ao tentar converter um arquivo PDF em um documento PDF/A usando o método de conversão toPDFA (NPR-32663).

* Serviços do Documento: Uma exceção é exibida ao aplicar o serviço Reader Extensions em um arquivo PDF (NPR-32639).

* Serviços do Documento: Uma mensagem de erro é exibida ao montar e converter arquivos XDP em arquivos PDF (NPR-31821).

* A Analytics não exibe os resultados apropriados ao enviar ou abandonar formulários em uma página Sites (NPR-31359).

### Correções e Feature Packs incluídos em Pacotes de serviço anteriores {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.7.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.7.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.17.
* Adicionado suporte para definir a versão de uma página Sites ao excluí-la.
* A nova coluna para a data criada, que é classificável, foi adicionada na visualização de lista **** DAM e nos resultados da pesquisa de ativos na visualização de **Lista** (NPR-31311).
* A classificação de ativos com base na coluna **Nome** foi permitida na visualização da **Lista** .
* O tamanho do lote e o tempo limite da etapa do fluxo de trabalho para Reprocessar e Carregar em lote agora são configuráveis da interface do usuário no Dynamic Media.
* O `pdfBrochure` foi definido como falso na configuração de nuvem do Scene 7 para salvar memória no IPS.

##### Assets {#assets-6470}

**Aprimoramentos do produto**

* A versão de exportação do pacote da API `package com.day.cq.dam.handler.standard.msoffice` compatível com o `dam-handler` pacote é atualizada para 6.0.0 (CQ-4279059).
Se você estiver usando o pacote `com.day.cq.dam.handler.standard.msoffice` em sua implementação personalizada, recomendamos que você compile o `dam-handler` pacote com o uber jar mais recente.

* A nova coluna para a data criada, que é classificável, foi adicionada na visualização de lista DAM e nos resultados da pesquisa de ativos na visualização de lista (NPR-31311).

* A classificação de ativos com base na coluna Nome foi permitida na visualização da Lista (NPR-31299).

**Correções**

* Os metadados de alguns documentos PDF não são atualizados e salvos no PDF ao modificar seu título (NPR-31575).

* Os ativos com o símbolo &#39;+&#39; no nome de arquivo não podem ser excluídos (NPR-30588).

* As propriedades da pasta DAM não mostram os usuários ou grupos adicionados (criados pela sincronização LDAP) em Grupos de usuários fechados (NPR-30555).

* Caracteres especiais que ocorrem na linha Assunto de Modelos de e-mail não são exibidos corretamente (NPR-30547).

* Os nomes dos ativos são alterados para letras minúsculas ao mover ativos de uma pasta para outra no AEM em execução no modo de execução do Dynamic Media Scene 7 (NPR-31631).

* Os nomes do conjunto de imagens são alterados para minúsculas na Cena 7, quando o conjunto de imagens (ou conjunto de imagens) é criado e nomeado com a convenção de nomenclatura apropriada no DAM (NPR-31576).

* O fluxo de trabalho do Dynamic Media Encode Video está falhando ao gerar miniatura para o vídeo que é migrado do Scene 7 para o Dynamic Media - modo de execução do Scene 7 (NPR-31523).

* Erro interno do servidor é observado ao usar o filtro para pesquisar por Conjuntos, no AEM em execução no Dynamic Media - modo de execução Scene 7 (NPR-31388).

* Ocorreu um erro ao editar um conjunto de imagens remoto, para a imagem que reside na pasta com o mesmo nome de empresa do Scene 7 (NPR-31347).

* Os ativos que contêm referências não estão sendo publicados (DM) (NPR-31179).

* O valor de expiração (tempo de funcionamento do cache do cliente) configurado para o modo Híbrido do Dynamic Media não é replicado no ambiente de entrega do Dynamic Media (NPR-31126).

* Os uploads do AEM Dynamic Media - modo de execução do Scene 7 para o Scene 7 estão demorando muito para serem concluídos (NPR-30926).

* Depois de criar uma página com o componente Dynamic Media ao publicar o mesmo, a partir da instância do autor em execução no Dynamic Media - modo de execução Scene 7, o usuário é solicitado a publicar a configuração dmsceno7 (NPR-30880).

* O valor do parâmetro &quot;asset&quot; no código incorporado do visualizador permanece inalterado após alterar os valores no campo &quot;Título após a mudança&quot; e &quot;Nome após a mudança&quot; no Dynamic Media - Scene 7 (NPR-30745).

* A página de resultados da pesquisa de interface de toque (feita pelo Omnisearch) rola automaticamente para cima e perde a posição de rolagem do usuário (NPR-31306).

* A Expurgação do Evento DAM exclui os dados mais recentes do evento (maxSavedActivities) e retém os dados criados anteriormente (NPR-30870).

* A alteração do título e nome do ativo não persistiu após a operação de mover para uma pasta de destino que aciona a rolagem infinita ao selecioná-la (NPR-30647).

* As coleções são removidas da visualização ao aplicar qualquer filtro em AEM Assets acessados do Adobe Asset Link (CQ-4280534).

* O tamanho do lote e o tempo limite da etapa do fluxo de trabalho para Reprocessar e Carregar em lote não são configuráveis da interface do usuário, e precisam ser definidos no CRXDE e o fluxo de trabalho precisa ser sincronizado duas vezes (CQ-4281254).

* O nome da etapa do fluxo de trabalho para upload em lote e etapa de upload simples é o mesmo no Scene 7, o que resulta em confusão (CQ-4281176).

* O fluxo de trabalho de reprocessamento no Scene 7 fica travado se um ativo estiver faltando no nó de metadados (CQ-4281170).

* A etapa BatchUpload no fluxo de trabalho de reprocessamento não funciona para a pasta que possui o ativo de vídeo (CQ-4280630).

* As opções de PDF enviadas para DM têm extractKeywords definidas como true por padrão (CQ-4280101).

* Exceção de Ponto Nulo é observada ao executar o fluxo de trabalho de Reprocessamento do Scene 7 em uma pasta que contém ativos não-DM (CQ-4279555).

* A renomeação de ativos no AEM não é sincronizada à cena 7, quando um ativo com um nome de duplicado já existe no Scene 7 (CQ-4276763).

* O arquivo zip enviado por email para download de ativos falha ao descompactar quando um usuário com permissões de leitura tenta abri-lo (CQ-4277925).

* O Fluxo de trabalho de execução de PPT falha ao gerar execuções dos arquivos PPT carregados, pois o AEM 6.4 não consegue atualizar para com.adobe.granite.poi versão 2.0.28 (CQ-4279059).

* Os arquivos PDF não são indexados e o conteúdo não é pesquisável (CQ-4278916).

##### Sites {#sites-6470}

* Quando as inicializações são promovidas somente com páginas Modificadas do Promote e as inicializações do Promote com páginas modificadas são feitas, somente as páginas modificadas aparecem para serem promovidas. Além disso, quando a lista a ser promovida estiver correta, as páginas não modificadas ainda serão exibidas na parte inferior da lista (NPR-31314).

* Quando uma página de AEM Sites é movida para um local diferente, suas propriedades não são atualizadas adequadamente para refletir seu novo local (NPR-31265).

* Para um novo Blueprint, se o número de registros for superior a 40, somente os primeiros 40 registros serão exibidos. O Blueprint exibe linhas em branco para o restante dos registros (NPR-31182).

* Quando o número de LiveCopies é grande, a visão geral do LiveCopy demora muito para renderizar a pré-visualização (NPR-30945).

* Adição de suporte para definir uma versão de uma página ao excluí-la. Se o controle de versão estiver desativado para a página excluída, o AEM Sites não poderá restaurar essas páginas (NPR-30891).

* Quando um usuário adiciona caracteres japoneses ou coreanos na propriedade de descrição de um menu, o menu exibe caracteres distorcidos para o texto em japonês e coreano (NPR-31331).

* Quando um usuário foca nos campos do painel à esquerda e usa um atalho do teclado para colar o conteúdo, ele cola o conteúdo da área de transferência do editor de páginas em vez do conteúdo copiado dos campos do painel à esquerda (NPR-31169).

* Quando um usuário edita um fragmento de conteúdo, a variação já excluída do fragmento de conteúdo é restaurada (NPR-31178).

* O query Content Fragment Models é ineficiente. É muito lento se a instância tiver muitas páginas e resultar em um erro (NPR-30666).

* Ao salvar o modelo de fragmento de conteúdo, o tempo no campo de data e hora é definido como 00:00 (NPR-30540).

##### Integrações {#integrations-6470}

* Ao configurar o Adobe Launch, uma barra (/) é prefixada no URL da biblioteca (NPR-30700).

* O desempenho do ContextHub diminui após a publicação (NPR-30884).

##### Sling {#sling-6470}

* Atualize a versão do pacote do provedor de segurança do console da Web para 1.2.4 para remover a dependência da api de inicialização do aplicativo de inicialização do webconsolesecurityprovider (NPR-30885).

##### Plataforma {#platform-6470}

* As atualizações na configuração de tamanho do buffer do serviço HTTP baseado em Java não são salvas (NPR-30925).

* O QueryBuilder agora oferece suporte a order by fn:name() em query xpath (NPR-31322).

* Atualizado o administrador do evento distribuído Sling para a versão 1.1.4, melhorando a qualidade dos registros em um ambiente agrupado (NPR-29256).

##### Interface do usuário do Foundation {#foundation-6470}

* A rolagem até o final da página de resultados com um grande número de resultados de pesquisa faz com que o navegador falhe (NPR-31332).

* Ao alternar da visualização de cartão para a visualização de Lista em uma página de resultados de pesquisa, há um atraso antes que a página possa ser rolada (NPR-31280).

##### Oak {#oak-6470}

* Os arquivos do MS Office com extensões de arquivos .docx e .xlsx contendo imagens JPEG não são analisados usando o analisador Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* A integração do Livefyre com a atualização do AEM 6.4 oferece uma exceção de ponto nulo quando a integração é feita usando o plug-in DITA para recursos sintéticos. A integração, no entanto, funciona quando os componentes são adicionados manualmente (FYR-11066).

##### Tradução {#translation-6470}

* O caminho para o fragmento da experiência de destino não está sendo atualizado ao promover uma página de inicialização (NPR-30830).

##### Communities {#communities-6470}

* A funcionalidade de email não está funcionando corretamente em alguns casos, mesmo quando as mensagens de email estão ativadas nas configurações de notificação, o sistema lança uma exceção em NotificationsActivityStreamProvider (NPR-31521).
* Não é possível criar novos membros, a tela em branco é exibida na tela Criar membro na instância do autor de AEM (NPR-30951).
* O usuário não consegue postar um comentário em um blog no Internet Explorer 11 (NPR-30927).
* O administrador de um grupo restrito não consegue visualização no cartão de grupo, não consegue executar nenhuma operação de link rápido (Editar/Publicar/Excluir grupos) na instância do autor de AEM (NPR-30810).
* As informações de grupos/membros não estão visíveis na criação de um novo site na instância de autor de AEM (NPR-28840).

##### Forms {#forms-6470}

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**Pacote complementar do Forms**

**Formulários adaptáveis**

* As strings contêm a chave do dicionário ao localizar formulários adaptáveis (NPR-31109).

* As caixas de seleção e as listas suspensas no Forms falham nas verificações de acessibilidade (NPR-31282).

**Formulários HTML5**

* Gerar a visualização HTML5 de um formulário XDP mostra uma oscilação ao adicionar instâncias de um formulário secundário (NPR-30907).

**Serviços de Documento para OSGi**

* A execução de vários processos simultâneos para montar os formulários usando o método com.adobe.fd.assembler.service.AssemblerService.invoke() exibe uma mensagem de erro (NPR-31164).

* Os arquivos temporários criados pelo Serviço de Montagem não são excluídos automaticamente e exigem a reinicialização do AEM (NPR-30846).

* A aplicação do Reader Extension Rights ao PDF resulta em uma mensagem de erro (NPR-30930).

**Fluxo de trabalho**

* O fluxo de trabalho do OSGi falha devido à utilização de 100% da CPU (NPR-31234).

**Instalador do Forms JEE**

**Serviços de documentação**

* O serviço Convert PDF falha ao converter documentos PDF em PostScript e exibe uma mensagem de erro (NPR-31267).

* A configuração do ponto de extremidade SOAP é redefinida após a aplicação de um patch para corrigir a falha de HTML em PDF (NPR-31309).

**Serviço PDFG**

* Não é possível carregar o arquivo de configurações do Adobe PDF baixado usando a interface do usuário do administrador (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.6.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.6.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.15.
* Adicionado suporte para rastrear estados dinâmicos de interface do usuário no evento de rastreamento na API de base.
* Adição do suporte de execução ao componente principal da imagem.

**Assets**

* Asset share link of a folder with space and `&` character in the name displays blank gray cards for some assets. NPR-29934: Hotfix do CQ-4270187
* O fluxo de trabalho do DAM falha ao criar ativos MP4 para o AEM. NPR-30031: Hotfix do CQ-4271352
* Problema de conectividade com o Adobe Smart Tag por meio do Datapower. NPR-30026: Hotfix do CQ-4269457
* O PDF não pode ser encontrado usando o OmniSearch. NPR-30046: Hotfix do GRANITE-26290
* Os caminhos de ativos nos metadados de URLs e de pastas gerados pela API ACP não são codificados por URL.  GRANITE-26198: Hotfix do CQ-4271814
* A funcionalidade Criar tarefa de Revisão não funciona devido à carga indefinida. NPR-30469: Hotfix CQ-4274263
* A capacidade de alternar a visualização da visualização do cartão para a visualização da lista e vice-versa desaparece depois de fazer um OmniSearch no seletor de ativos. NPR-29852: Hotfix do CQ-4269369
* (Interface do usuário para toque) Durante o assistente de gerenciamento de publicação, os ativos são adicionados à fila de replicação após a adição das páginas, fazendo com que alguns dos ativos apareçam após alguns segundos. NPR-29985: Hotfix do CQ-4270724
* A classificação da consulta de pesquisa por relevância retorna documentos do InDesign junto com modelos do InDesign. Hotfix do CQ-4273864
* Se o usuário tiver uma ID de email em letras maiúsculas, os usuários não poderão fazer check-in nos ativos cujo check-out foi feito anteriormente. Hotfix do CQ-4276575
* Configuring Dynamic Media Cloud Services in `DMHybrid` mode results in multiple empty report suites created in Analytics with no report suite id stored on AEM resulting in report suite duplication. Hotfix do CQ-4276855
* A caixa de diálogo de aviso não é exibida durante a promoção na página &quot;Tag gerenciada&quot;. Hotfix do CQ-4252851
* Ao usar o carrossel para gerenciar tags, o botão de navegação não funciona. Hotfix do CQ-4275499
* A funcionalidade de ativos de movimentação em massa é dividida, resultando em não movimentação de ativos. Hotfix do CQ-4272987

**Sites**

* `pageinfo.json` as solicitações são extremamente lentas e demoram muito para carregar. NPR-29709: Hotfix do CQ-4269560
* `onTime` ou `offTime` as propriedades de metadados salvas em ativos não são recuperadas se o servidor AEM for reiniciado. NPR-30413: Hotfix do CQ-4272784
* Devido ao comportamento incorreto da classe ConfigPostProcessor, suspender a página pai remove cq: Tipo de mixagem do LiveRelationship a partir da página secundária. NPR-30536, NPR-30510: Hotfix do CQ-4254113
* Scripts entre sites (XSS) na caixa de diálogo de fluxo de trabalho no Start na página de edição de Campanhas. NPR-29747: Hotfix do CQ-4271067
* (Interface clássica) A etapa de bloqueio de fluxo de trabalho desativa a guia de fluxo de trabalho até que o bloqueio seja liberado. NPR-30356: Hotfix do CQ-4237557
* (IE11) Ao colar conteúdo HTML em um componente Editor de Rich Text com defaultPasteMode = texto simples, o HTML é colado com a formatação, portanto, defaultPasteMode não tem efeito. NPR-30045: Hotfix do GRANITE-26094
* (Interface clássica) Quando a página de administração do site é recarregada, todos os itens suspensos no menu &quot;Novo&quot; são desativados. NPR-29980: Hotfix do CQ-4272044
* Não é possível adicionar estilos ao texto nem editar os estilos existentes criados no conteúdo. NPR-29712: Hotfix do CQ-4266249
* (Interface clássica) Ativos sem dc: o valor do título é listado sem título no navegador de diálogo do campo de caminho. NPR-30166: Solicitação de backport para CQ-88858
* O cq: o ouvinte não funciona com componentes aninhados mesmo após a adição do componente parsys. NPR-30422: Hotfix do CQ-4274863
* Erro ContextHub durante a integração do AEM e do Campaign. NPR-30625: Hotfix do CQ-4250790
* O valor do parâmetro de solicitação resourceType é copiado no valor de um atributo de marca HTML entre aspas duplas. NPR-29832: Hotfix do CQ-4255365
* Uma atualização de página é necessária depois que os componentes são copiados e colados de uma página para outra. NPR-29982: Hotfix do CQ-4256019
* Publicar/Cancelar publicação de um alias de página não é suportado e deve ser removido. NPR-30062: Hotfix do CQ-4271249
* Aviso do ResourceResolver não fechado em ExperienceFragmentsReplicationListener que leva a problemas de estabilidade ao longo do tempo, forçando a reiniciar instâncias do AEM. NPR-30416: Hotfix do CQ-4257521
* Os fragmentos de experiência de movimento referenciados em mais de 150 páginas não modificam o fragmentPath nas páginas em que são referenciados. NPR-30556: Hotfix do CQ-4274900
* Erro de análise ao abrir um Fragmento de conteúdo com caracteres em dólar ($) e chave aberta ({) um após o outro. Hotfix do CQ-4270266
* VersionPreviewServlet está falhando em NullPointerException ao tentar exibir uma versão de um Fragmento de experiência na linha do tempo. NPR-30074: Hotfix do CQ-4271881
* Não é possível bloquear fragmentos de conteúdo por meio do recurso de check-in. NPR-29923: Hotfix do CQ-4258785

**Replicação**

* A Sessão JCR / Resolvedor de recursos vazou durante a implementação do OAuth em cada replicação para MAC / Portal de marcas. NPR-30000: Hotfix do Granite-26196

**Sling**

* A ordem dos filhos afetados usando sobreposição e ordem antes está causando IndexOutOfBoundException. NPR-30408: Hotfix para Sling-8296 e Sling-7375
* InativeBundlesHealthCheck está lendo a configuração MissingPackagesHealthCheck depois que as configurações InativeBundlesHealthCheck são salvas. NPR-30084: Hotfix do CQ-4272644

**Comércio**

* Não é possível executar o blueprint do catálogo no console Sites. NPR-29829: Hotfix do CQ-4271461
* O ativo usado no produto não mostra nenhuma referência ao produto na seção &quot;Referências&quot; do ativo, nem o caminho do ativo é atualizado se o ativo for movido. NPR-30542: Hotfix do CQ-4270247

**Plataforma**

* O remetente de email padrão do AEM não pode enviar emails para um servidor SMTP remoto por TLS v1.2. NPR-30476: Hotfix do GRANITE-26605

**Comunidades**

* Os grupos excluídos no autor não estão sincronizados com todos os editores. NPR-29987: Hotfix do CQ-4268738
* Os usuários excluídos removidos do campo Administradores da comunidade não estão em sincronia com o grupo Membros. NPR-30389: Hotfix do CQ-4274339
* Os usuários que fazem parte do grupo de administradores não têm links rápidos para o grupo. NPR-30546: Hotfix do CQ-4275579
* Atualizar qualquer grupo da Comunidade recém-criado e existente substitui a propriedade no jcr: nó de conteúdo e altera seu nome para o título da primeira página. NPR-30109: Hotfix do CQ-4273719
* A pesquisa rápida e a pesquisa por localização e endereço não funcionam quando a comunidade está definida para trabalhar com o Provedor de Recursos de Armazenamento de Banco de Dados (DSRP). NPR-26737: Hotfix do CQ-4258493

**Tradução**

* A execução automática da Tradução não funciona. NPR-30499: Hotfix do CQ-4276288
* O usuário pode criar uma cópia de idioma no caminho de conteúdo restrito a somente leitura. NPR-29937: Hotfix do CQ-4270708
* Problema de tradução - somente alguns componentes são traduzidos pela tradução automática. NPR-30079: Hotfix do CQ-4273764

**Integração**

* O conteúdo personalizado não é exibido corretamente na instância de publicação até a reinicialização da instância. NPR-30421: Hotfix do CQ-4273706

**Projetos**

* Os valores dam:folderThumbnailPaths não são atualizados e exibem miniaturas antigas mesmo depois de excluir os ativos dentro da pasta. NPR-30424: Hotfix do CQ-4273667

**Consoles da interface do usuário**

* Scripts entre sites (XSS) nas propriedades da página Sites na guia miniatura. NPR-30048: Hotfix do Granite-26200

**UI-Foundation**

* Adicionado suporte para rastrear estados dinâmicos de interface do usuário no evento de rastreamento na API de base. NPR-30742, GRANITE-26322: Hotfix para GRANITE-26036

**Forms**

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**Pacote complementar do Forms**

**Formulários adaptáveis**

* O arquivo .css vazio leva mais tempo para ser obtido do editor, causando problemas de desempenho. NPR-30558: Hotfix do CQ-4274399
* Os formulários que são modificados após a publicação não são publicados novamente na publicação do site. NPR-30411: Hotfix do CQ-4236566

**Forms - Integração de backend**

* Um erro é emitido ao criar o Modelo de dados de formulário com a Linguagem de definição de serviço da Web (WSDL). NPR-30388: Hotfix do CQ-4272921

**Forms - Gerenciamento de correspondência**

* Caracteres especiais, como menor que (&lt;), maior que (>) e E comercial (&amp;), são codificados na interface do usuário do agente. NPR-30410: Hotfix do CQ-4273887
* Ao acionar fragmento de texto que contém valores do Dicionário de dados, a interface do usuário do agente fica sem resposta. NPR-30098, NPR-30083: Hotfix do CQ-4272204
* A opção Criar interface de usuário de correspondência (CCR UI) falha intermitentemente com a variável de erro (objeto). NPR-29983: Hotfix do CQ-4273874
* O recarregamento do rascunho da carta falha com uma exceção quando a descrição dos Fragmentos do Documento contém caracteres especiais como menor que (&lt;), maior que (>) e E comercial (&amp;) nas propriedades. NPR-29930: Hotfix do CQ-4252762

**Formulários HTML5**

* Ao usar o NonVisual Desktop Access no modo Procurar para ler um formulário HTML5, o navegador Chrome lê &quot;gráfico&quot; antes de cada Gráfico de vetor escalonável (SVG) no design do formulário. NPR-30450: Hotfix do CQ-4274732

**Instalador do Forms JEE**

**Forms - Foundation JEE**

* Adicionar ou editar uma conexão de serviço da Web chamando serviços da Web do Workbench de formulários AEM emite um erro: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix do CQ-4273217

**Forms - Serviços de documentos**

* Erro de falta de etiqueta PDF/A na comprovação do Acrobat. NPR-30594: Hotfix do CQ-4276032
* Os vínculos de dados de caractere único no PDF fazem com que o Reader Extensions falhe com um erro &quot;java.lang.StringIndexOutOfBoundsException: Índice de cadeia fora do intervalo: 1&quot;. NPR-30128: Hotfix do CQ-4273878
* Quando um teste de carregamento é executado no serviço de HTML para PDF, ele falha com um erro e as configurações de tipo de arquivo são removidas do servidor AEM Forms. NPR-30085: Hotfix do CQ-4272631
* O achatamento de um PDF com o Adobe Acrobat 9.1 (XFA versão 3.0) não mantém o estado do formulário PDF: Os elementos invisíveis no formulário são retornados para um estado visível. NPR-29978: Hotfix do CQ-4270888

**Forms - Segurança de documentos**

* A aplicação de uma assinatura com carimbo de data e hora falha com erro: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: erro de chamada. NPR-30696, NPR-30537: Hotfix do CQ-4273778
* O Configuration Manager não insere strings japonesas para colunas de tabela localizadas. NPR-30496: Hotfix do CQ-4274868

**Serviço PDFG**

* Erro de conexão ao tentar converter o documento do Word em PDF no Windows Server 2016. NPR-30597: Hotfix do CQ-4275652
* Exceção negada de permissão ao tentar usar o serviço de back-end HTML para PDF por meio da biblioteca &quot;phantomjs&quot;. NPR-30456: Hotfix do CQ-4258077
* O serviço maxReuseCount para HTML em PDF não é exibido com o console de gerenciamento JBoss. NPR-30303, NPR-30135: Hotfix do CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.5.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.5.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.13.
* Foi adicionado o tempo limite de soquete e o tempo limite de conexão nos agentes de replicação do Brand Portal.
* Aprimoramentos do Omnisearch - Aumento do limite de paginação do resultado da pesquisa para 100 páginas.
* Desativado o componente `AssetDownloadServlet` OSGi por padrão nas instâncias de publicação do AEM. Para obter mais informações, consulte [Baixar ativos do AEM](/help/assets/download-assets-from-aem.md).
* Ativação do suporte Multi-Site Manager no Assets. For more information, see [Reuse assets using MSM for Assets](/help/assets/reuse-assets-using-msm.md).

**Assets**

* Os ativos com um apóstrofo no nome do arquivo não são sincronizados com o Dynamic Media. NPR-29538: Hotfix do CQ-4270592
* Atualização da interface DAM DMGGateway para oferecer suporte a várias peças S3. NPR-29740: Hotfix do CQ-4226303
* A caixa de diálogo de download de ativos exibe um tamanho de arquivo incorreto ao baixar representações de um vídeo no Dynamic Media. NPR-29642: Hotfix do CQ-4246202
* Os ativos tornam-se inutilizáveis depois que o serviço de tipo MIME Day CQ DAM aplica texto para m3u8. NPR-29276: Hotfix do CQ-4264052
* O ajuste de referência do ativo não salvará a sessão se algum dos ativos movidos/renomeados fizer parte das coleções de Recursos de sling. NPR-29143: Hotfix para /CQ-4252605
* Não é possível rastrear ou localizar ativos pesquisando os valores de metadados. NPR-29141: Hotfix do CQ-4260215
* Ao usar o filtro de pesquisa para salvar uma coleção inteligente, a ação de clique no painel não mantém o foco. NPR-29000: Hotfix do CQ-4240323
* Mover uma pasta permite a criação de uma pasta com nomes de maiúsculas ou minúsculas misturados. NPR-28945: Hotfix do CQ-4265234
* Resultados em branco exibidos no Omnisearch se o nome da coleção tiver espaço. NPR-29001: Hotfix do CQ-4236729
* Renomear um arquivo usando alguns caracteres especiais não suportados, como o E comercial (&amp;), cria uma pasta inválida. NPR-29196: Hotfix do CQ-4265037
* O arquivo de extração de DAM para funcionalidade de arquivo zip está quebrado. NPR-29187: Hotfix do CQ-4254421
* A importação de metadados deve permitir a importação de metadados sem o registro de namespaces. NPR-29425, NPR-28132: Hotfix do CQ-4269445
* Salvar alterações de metadados não funciona para ativos cujo nome contém um caractere de citação. NPR-29395: Hotfix do CQ-4254305
* Não é possível mover um ativo DAM se o nome do arquivo contiver espaços em branco. NPR-29270: Hotfix do CQ-4266403
* Não é possível baixar arquivos ZIP compactados com algoritmo Deflate64. NPR-29225: Hotfix do CQ-4253995
* As miniaturas de ativos são exibidas lentamente ao abrir uma pasta que contém ativos com muitas versões. NPR-29833: Hotfix do CQ-4271629
* Não é possível inserir a coleção realçada se a tecla Enter for pressionada depois de selecionar a coleção. NPR-29723: Hotfix do CQ-4261607
* Ataque de script entre sites (XSS) pela janela de alerta restrito. NPR-29671: Hotfix do CQ-4270133
* A adição de relações a ativos está falhando para usuários sem permissões de exclusão. NPR-29640: Hotfix do CQ-4269196
* Depois de adicionar o título do ativo na página de propriedades, quando o usuário tentar fechar a página, o AEM abre a página de propriedades novamente. NPR-29628: Hotfix do CQ-4264929
* Criar um grande número de relações no ativo resulta em um erro. NPR-28779: Hotfix do CQ-4250708
* A ingestão de ativos é lenta no modo de execução do Scene7 Connect. NPR-28658: Hotfix do CQ-4263007
* Um erro TypeError não detectado: Não é possível ler a propriedade &#39;split&#39; de undefined é exibida ao tentar visualização dos resultados da pesquisa. NPR-28803: Hotfix do CQ-4248371
* A replicação do AEM para o Brand Portal está travada por longos períodos. NPR-28914: Hotfix do CQ-4254932
* Mover ativos no DAM não resulta em uma mudança semelhante no Scene7. NPR-28957: Hotfix do CQ-4264974
* As atualizações de metadados não são passadas para o IPS se o campo de metadados for atualizado no AEM. NPR-28961: Hotfix do CQ-4255393
* VersioningTimelineEventProvider deve fornecer a versão raiz juntamente com o comentário da versão. Hotfix do GRANITE-26063
* A injeção de dados leva à execução do código no lado do servidor. Hotfix do CQ-4270246
* Ativação do suporte Multi-Site Manager no Assets. Hotfix do CQ-4271453, CQ-4268621, CQ-4257491
* A interface do AEM deve exibir uma entrada adicional para a versão atual do ativo no histórico da linha do tempo, exibindo o comentário de check-in mais recente do Adobe Asset Link. Hotfix do CQ-4262864
* A amostra de vídeo não é carregada ao criar ou editar um MixedMediaSet. Hotfix do CQ-4244889
* Desativar as permissões para excluir conteúdo no lado do AEM impede que o usuário publique no Portal de marcas. Hotfix do CQ-4270426
* Problemas relacionados ao limite de Query com relatórios de ativos após a atualização para o AEM 6.4.3. NPR-28588: Hotfix para CQ-4262022, CQ-4260697
* A funcionalidade de download aproveita AEM Assets por meio do servlet de download de ativos, permitindo que usuários anônimos baixem todos os ativos. NPR-27315, Hotfix para CQ-4254732

**Sites**

* O nome da tag de reclamação do JCR deve ser preenchido automaticamente com base no título da tag. NPR-28990: Hotfix do CQ-4199411
* O botão Cancelar herança não está visível em alguns dos campos adicionados nas propriedades da página. NPR-29079: Hotfix do CQ-4265686
* A ação de pré-visualização de lançamento não deve tentar recriar a cópia ativa ou mostrá-la na lista de páginas de roll-out. NPR-29151: Hotfix do CQ-4266213
* (Editor de modelos) Regressão de política de estilo no modo de estrutura. NPR-28981: Hotfix do CQ-4264400
* Cópias ativas aninhadas mostram entradas de duplicado durante o lançamento. NPR-29300: Hotfix do CQ-4268664
* A publicação de uma Live Copy que contém um componente do Importador de design falha ao recuperar referências para a página selecionada. NPR-28944: Hotfix do CQ-4265014
* A CoralUI, quando usada com Multifield, armazena o fileReferenceParameter no nível de componente em vez de no nível de vários campos. NPR-29536: Hotfix do CQ-4266129
* A referência de design não é replicada na publicação após cancelar a herança no Importador de design. NPR-29648, NPR-29721: Hotfix do CQ-4269270, CQ-4271087
* O campo de caminho no Editor de Rich Text é aberto no caminho raiz, independentemente do caminho especificado para pesquisa. NPR-29483: Hotfix do CQ-4268997
* (IE11) Copiar colar conteúdo HTML em um componente RTE com defaultPasteMode = texto simples não cola o conteúdo como um texto simples. NPR-29432, NPR-29171: Hotfix para GRANITE-24941
* A verificação ortográfica do Editor de Rich Text não funciona mais em outros idiomas. NPR-29506: Hotfix do CQ-4264990
* Scripts entre sites (XSS) na página de Campanha. NPR-29614: Hotfix do CQ-4269322
* Minimizar o Editor de Rich Text da tela cheia enquanto no modo de edição de origem leva a perda de conteúdo. NPR-29574: Hotfix do CQ-4260584
* (Interface clássica) Navegar até a última guia nem sempre é possível quando há um grande número de tags. NPR-29544: Hotfix do CQ-4264548
* (Interface clássica) O menu de navegação do Admin Console desaparece e a página não é carregada completamente. NPR-29571: Hotfix do CQ-4264585
* O alerta de erro é gerado ao adicionar componentes à página WCM quando a minificação está ativa na instância. NPR-29396: Hotfix do CQ-4266196
* Um problema com a herança dos nós do Sistema de estilo do pai. NPR-29296: Hotfix do CQ-4266041
* A página restaurada com o Timewarp deve se referir à imagem correta no momento do controle de versão.  NPR-29431: Hotfix do CQ-4262638
* Página em branco com erros de Javascript no editor depois de instalar a versão mais recente do snapshot 6.4.5. NPR-29475: Hotfix do CQ-4266196
* Ao adicionar um componente a um parsys, a propriedade de lista do componente de design não é respeitada e é resolvida para um nome de nó de modelo diferente com uma estrutura parsys semelhante. NPR-29509: Hotfix do CQ-4269044
* a zona cq:dropTargets cobre todo o componente em vez do tamanho da imagem, dificultando a definição de metas com componentes incorporados. NPR-29738: Hotfix do CQ-4268912
* O componente de imagem não chama o ouvinte &quot;pós-edição&quot; depois que a imagem no editor é usada. Hotfix NPR-29616 para CQ-4268065
* Um problema na configuração da postagem social no Facebook. NPR-29212: Hotfix do CQ-4266630
* Ao promover inicializações de páginas modificadas, as modificações nas ramificações de origem e de inicialização são consideradas. NPR-29308: Hotfix do CQ-4266746
* A miniatura renderizada no Fragmento do conteúdo mostra a representação interna do calendário do campo Data e hora. NPR-29531: Hotfix do CQ-4269362
* Não é possível adicionar uma tag em massa a páginas com tags diferentes existentes. NPR-28729: Hotfix do CQ-4262922
* O ícone de Ativação agendada não é exibido no administrador do site. NPR-28725: Hotfix do CQ-4263917

**Replicação**

* Vulnerabilidade de divulgação de informações confidenciais no componente Agente de Replicação. NPR-29612, NPR-24951: Hotfix para GRANITE-25070
* Os dados fornecidos pelo usuário não são escapados na saída no componente cq/Replication/components/agent, resultando em uma vulnerabilidade de script entre sites (XSS). Hotfix do CQ-4266263

**Fragmentos de experiência**

* Não é possível exportar os Fragmentos de experiência para o destino quando a imagem inteligente é usada. Hotfix do CQ-4269606

**Social - Relatórios**

* Os relatórios da Comunidade do AEM não são exibidos na instância do autor do AEM. Hotfix do CQ-4266294

**Plataforma**

* Scripts entre sites (XSS) no gerenciador de pacotes ao instalar um pacote. NPR-29734, NPR-29713, NPR-29630: Hotfix para GRANITE-26161, GRANITE-
* Vários scripts armazenados e refletidos entre sites (XSS) no CRXDE Lite. NPR-29634: Hotfix do GRANITE-26049
* A funcionalidade de logon para Compartilhamento de pacotes usa a solicitação GET em vez da solicitação POST, fazendo com que a senha fique visível na guia rede. NPR-29631: Hotfix do GRANITE-26048

**Felix**

* Scripts entre sites (XSS) observados no console do sistema. A página é carregada e o pop-up é exibido quando o mouse passa o mouse sobre o campo de texto. NPR-29853, NPR-29633: Hotfix para GRANITE-26188, GRANITE-26050

**Granite**

* A Configuração do Apache Sling Logging Logger não filtra o script inserido.  NPR-29775: Hotfix do GRANITE-26051

**Comunidades**

* Os grupos excluídos no autor devem ser removidos das instâncias de publicação. NPR-28933: Hotfix do CQ-4264645
* O segredo do aplicativo deve ser protegido com um campo de senha, para não ser exibido em texto simples para ferramentas de conexão social. NPR-29728: Hotfix do CQ-4270480
* Visitantes e membros, sem privilégios de moderador, podem visualizar postagens não aprovadas/pendentes colando o URL. NPR-29726: Hotfix do CQ-4271124, CQ-4271441
* É observado um tempo de resposta alto de 40 a 50 segundos no logon do usuário na Comunidade. NPR-29678: Hotfix do CQ-4269444

**Tradução**

* Os usuários sem acesso ao recurso de conversão na navegação não devem poder acessar suas subpáginas. NPR-29644: Hotfix do CQ-4269979
* Permissões de usuário não mantidas como assistente permitem a criação da cópia de tradução em um local somente leitura. NPR-29375: Hotfix do CQ-4265877

**IU - Foundation**

* Aumento do limite de paginação do resultado da pesquisa para 100 páginas para a visualização do cartão e 200 para a visualização da lista. NPR-29332: Hotfix do GRANITE-24644
* Devido ao carregamento lento de tags, nada é exibido na página da coleção. NPR-29267: Hotfix do GRANITE-24902
* Alterar o limite de paginação para 100 em vez de 40 aciona uma carga com preguiça extra sem solicitação de paginação. NPR-29246: Hotfix do GRANITE-25027
* O campo de senha do AEM granite não está sendo preenchido após a criptografia. NPR-29245: Hotfix do GRANITE-24908

**Integração**

* Uma mensagem de exceção é exibida ao tentar editar e salvar a configuração de inicialização do AEM. NPR-29086: Hotfix do CQ-4266153
* As credenciais do BrightEdge falham com erro de conexão.  NPR-29167: Hotfix do CQ-4265872
* A caixa de seleção herdada da exibição no nível raiz em Configurações de Cloud Service deve ser removida. NPR-27856: Hotfix do CQ-4259676

**Sling**

* O tempo limite da conexão HTTP não está sendo lido das configurações. NPR-29264: Hotfix para SLING-7902
* O write-back do instalador do JCR faz com que a configuração do OSGi use um formato inválido e bloqueie a reimplantação. NPR-29027: Hotfix do CQ-4264694

**Projetos**

* Os usuários não conseguem concluir o fluxo de trabalho do projeto. NPR-29621: Hotfix do CQ-4258791
* A lista Fluxo de trabalho do projeto mostra linhas vazias além de 40 workflows. NPR-28739: Hotfix do CQ-4264005
* Escolher a opção Renderização dinâmica no Brand Portal baixa um arquivo .zip vazio. NPR-29420: Hotfix do CQ-4268826
* Publicar ativos da pasta /content/dam/mac do autor de AEM no Brand Portal não funciona. NPR-29820: Hotfix do CQ-4271118
* A pontuação no nome causa problemas com o botão Publicar. NPR-29573: Hotfix do CQ-4269317
* Não é possível criar uma cópia de idioma do ativo por meio do painel de referência. Hotfix do CQ-4269535

**Fluxo de trabalho**

* A atualização da versão 6.4.2 para a 6.4.4 quebra o campo do seletor de calendário do participante da caixa de diálogo. NPR-29727: Hotfix do CQ-4270423

**WCM - IU do administrador**

* Abrir a guia de permissões na implementação do Coral2 não mostra os botões. Hotfix do CQ-4269419

**WCM - MSM**

* A exclusão de um nó secundário na live copy deve desanexar o liveRelationship. Hotfix do CQ-4270395
* A atualização para o AEM 6.4.3 faz com que o Multi-Site Manager leve muito tempo para ser iniciado. Hotfix do CQ-4271410

**Vulnerabilidade**

* A estrutura de proteção do CSRF não está funcionando com formulários fundamentais do AEM. NPR-28612: Hotfix do GRANITE-22231

**WCM - Editor de páginas**

* Script entre sites (XSS) refletido ao usar um seletor inválido. Hotfix do CQ-4270397

**Forms**

Os principais destaques dos formulários do AEM 6.4.5.0 são:

**Pacote complementar do Forms**

**Formulários adaptáveis**

* (Interface do usuário para toque) A opção de fluxo de trabalho do Start não abre a caixa de diálogo para configuração. NPR-29521: Hotfix do CQ-4269050

**Forms - Integração de backend**

* Ativação de suporte para o Ative Diretory Federation Services (ADFS) v3.0 para integração local do Microsoft Dynamics. NPR-30003, NPR-29484: Hotfix do CQ-4270586
* Falha no serviço de pré-preenchimento devido ao tempo de resposta prolongado do módulo de Integração de Dados do AEM Forms. NPR-28997: Hotfix do CQ-4265988
* A solicitação SOAP Webservice está malformada em AEM Forms. NPR-29013: Hotfix do CQ-4265443
* Nenhuma mensagem de erro é exibida durante o teste do serviço SOAP, no caso de um valor de data incorreto. Hotfix do CQ-4265445

**Formulários - Comunicação interativa e formulários - Gerenciamento de correspondência**

* Falha ao criar interface de usuário de correspondência (CCR UI) ao manipular um número flutuante.  NPR-29210: Hotfix do CQ-4254201
* A dica de ferramenta definida em uma variável não está visível na interface de usuário Criar correspondência (CCR UI). NPR-29739: Hotfix do CQ-4250533
* Não é possível copiar ou colar do Omnisearch em letras. NPR-29808: Hotfix do CQ-4270783

**Formulários HTML5**

* Quando adicionamos um espaço dentro do texto, o campo de texto não permite preencher até o final. NPR-28844: Hotfix do CQ-4260239

**Instalador do Forms JEE**

**Forms - Foundation JEE**

* O componente de serviço da Web no AEM Forms Workbench não pode invocar um serviço da Web, que requer autenticação SSL bidirecional. NPR-29485: Hotfix do CQ-4246794
* O gerenciador de configuração JEE do AEM Forms não funciona com várias placas NIC. NPR-29236: Hotfix do CQ-4268598
* Erro de inicialização do AEM vindo do GemFire: java.lang.IllegalStateException: Somente uma conexão AdminDistributedSystem pode ser feita todas de uma vez. NPR-29524: Hotfix do CQ-4266295
* NoClassDefFoundError devido a incompatibilidade de versão jar. NPR-28834: Hotfix do NPR-28834

**Forms - Serviços de documentos**

* Arquivo PDF/A inválido é reportado como PDF/A válido usando a operação isPDFA. NPR-29076: Hotfix do CQ-4261541
* Falha na conversão de PDF em PDF/A-1b com o campo Formulário sem dict de aparência. NPR-29534: Hotfix do CQ-4269618
* A conversão de PDF/A de PDF produzido com o Serviço de saída não passa a validação com o Acrobat DC. NPR-29647: Hotfix do CQ-4270448
* O pacote POI do Apache falha com uma exceção. NPR-27861, NPR-28048: Hotfix do CQ-4245898, CQ-4244778

**Forms - Designer**

* Adição de suporte PDF/UA a formulários XML Forms Architecture (XFA) gerados com o Designer e o Serviço de saída. NPR-23022

**Forms - Fluxo de trabalho**

* Os envios do espaço de trabalho falham com o caractere Umlaut. NPR-29087: Hotfix do CQ-4263172

**Feature Packs incluídos**

**Assets**

* Ativação do suporte Multi-Site Manager no Assets. For more information, see [Reuse assets using MSM for Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix do CQ-4259922

**Pacotes OSGI e pacotes de conteúdo incluídos**

O texto seguinte documentos a lista dos pacotes OSGI e dos pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.5.0

[Obter arquivo](assets/6.4.5.0_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.5.0

[Obter arquivo](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.4.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.4.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.11.
* Adicionado suporte para a versão do serviço de cache para evitar solicitações HTTP frequentes de versão do serviço.
* Adicionado suporte para exclusão de tags automáticas.
* A rolagem sem fim foi implementada para o assistente de catálogo.
* Capacidade suportada para restringir permissões de acordo com os sites da comunidade.
* Correções de desempenho (cache, execução assíncrona, lista de exclusão) para Verificação de integridade de conteúdo do Sling Granite.
* Botão assetpicker adicionado à caixa de diálogo pagethumbnail.
* Nova propriedade adicionada para permitir o posicionamento da dica de ferramenta nos campos.
* Aprimorado o suporte do ColorPicker dentro do Multicampo.
* Adicionada uma verificação para ignorar valores vazios para vários campos de entrada de número nas clientlibs do fragmento de conteúdo.
* Suporte habilitado para Microsoft Translator Text API v3.

**Assets**

* Migrar integração de ACP e Stock para o AEM 6.4.4.0 NPR-27632
* Publicar mais tarde pasta de ativos vazios com subpastas faz com que as subpastas desapareçam. NPR-27558: Hotfix do CQ-4254701
* A adição de uma única propriedade String não namespaced\[\] causa o write-back XMP incompleto. NPR-26805: Hotfix do CQ-4254142
* Depois de rasterizar o pdf de entrada, a saída produzida possui imagens ausentes. NPR-27929: Hotfix do CTG-4150481
* O Assistente para mover ativos está mostrando uma contagem incorreta de páginas de referência para páginas publicadas. NPR-27833: Hotfix do CQ-4258014
* O AssetPicker pesquisa apenas a primeira tag para filtrar o resultado ao filtrar com tags. NPR-27778: Hotfix do CQ-4257705
* O manipulador de PDF OOTB do AEM fica preso no processamento de PDFs com caracteres estrangeiros. NPR-28778: Hotfix do CQ-4254234
* Quando um arquivo CSV tem um valor que é separado por vírgula em uma única coluna, o editor CSV de AEM não escapa à vírgula e a trata como uma coluna separada. NPR-28801: Hotfix do CQ-4261694
* Problema com o Editor de Schemas de metadados ao usar o Navegador de caminhos para selecionar dados. NPR-28674: Hotfix do CQ-4263005
* Muitos ativos são processados no Serviço de conteúdo inteligente, resultando em um tempo enorme para concluir o processo de marcação periódica. NPR-28640: Hotfix do CQ-4262661, CQ-4262644, CQ-4263234
* As ações da área de trabalho não funcionam para os resultados do Omnisearch da `aem/start.html` página. NPR-27242: Hotfix do CQ-4248176
* A API Assets não permite o upload de arquivos > 2 GB que causam falha no upload. NPR-27629: Hotfix do Granite-23590
* Os metadados não são salvos no ativo baixado na primeira tentativa caso o Dynamic Media esteja habilitado na instância. NPR-28233: Hotfix do CQ-4260759
* O resolvedor de serviços não está fechado na configuração do SiteCatalyst. NPR-28015: Hotfix do CQ-4259397
* Mover ativos no DAM não resulta em uma movimentação semelhante no Scene7 (configuração p2p). NPR-28313: Hotfix do CQ-4261091

**Sites**

* (Interface clássica) Uma fração das cópias online é exibida na lista de lançamento. NPR-28598, NPR-28574: Hotfix do CQ-4263410
* O LiveRelationshipManagerImpl lança exceções quando cq:principal está vazio ou é inválido. NPR-28590: Hotfix do CQ-4263115
* O fluxo de trabalho &quot;Solicitar exclusão&quot; da caixa não exclui as páginas corretamente. NPR-28668: Hotfix do CQ-4263195
* A interface do usuário de status de relacionamento não mostra os valores adequados de ano ou carimbo de data e hora para os campos coral-datepicker relacionados. NPR-28666: Hotfix do CQ-4263661
* Script entre sites (XSS) no SuggestionHandler para 6.4. NPR-28693: Hotfix do CQ-4253821
* Mover a pasta do siteadmin termina sem memória e torna o AEM indisponível. NPR-28346: Hotfix do CQ-4261398
* As configurações de implantação do MSM LiveCopy são perdidas após a atualização. NPR-28311: Hotfix do CQ-4258705
* Não é possível rolar além de 40 configurações blueprint. NPR-27640: Hotfix do CQ-4239166
* O uso de SyntheticResource como referência lança uma exceção de ponteiro nulo e bloqueia a movimentação das páginas.  NPR-27576: Hotfix do CQ-4258262
* O PushOnModify não funciona na exclusão na instância atualizada 6.1 para 6.4. NPR-28108: Hotfix do CQ-4259833
* (Interface clássica) O botão Cancelar herança está ausente e o componente pode ser editado em uma página de cópia online. NPR-28256: Hotfix do CQ-4260161
* OakState0001: Conflitos não resolvidos na implantação. NPR-27982: Hotfix do CQ-4259548
* Ao copiar/colar uma estrutura que contém referências de SyntheticResource, o processo termina com um erro 500. NPR-27709: Hotfix do CQ-4259179
* Não é possível encerrar workflows em execução quando as cargas são ativadas. NPR-27672: Hotfix do CQ-4258520
* A implantação mostra os caminhos de implantação do duplicado após a atualização da versão 6.1 para a 6.4. NPR-27845: Hotfix para CQ-4259487
* Integre o modal dam assetpicker no componente de miniatura da página. NPR-28131: Hotfix do CQ-108042
* (Interface clássica) Não é possível abrir Diálogos com o widget Tags. NPR-28575: Hotfix do CQ-4262680
* O upload de arquivos de vários campos não mostra a área de destino. NPR-28676: Hotfix do CQ-4263516
* Erro de &#39;Valor inválido do seletor de recursão&#39; ao migrar um componente do AEM 6.0 para o AEM 6.2. NPR-28609: Hotfix para CQ-4241258
* O Editor de Rich Text na caixa de diálogo está oscilando quando o posicionamento de um plug-in é superior à área de texto, portanto, bloqueando qualquer criação adicional. NPR-27579: Hotfix do CQ-4257440
* (Interface clássica) cq:action editannotate não funciona. NPR-28232: Hotfix do CQ-4257703
* A remoção de tags do painel de pesquisa de ativos de filtro de tags do editor de páginas não atualiza a lista corretamente. NPR-27983: Hotfix do CQ-4245567
* Se os valores do número de vários campos estiverem vazios, clicar em Salvar resultará em um prompt de carregamento infinito sem concluir.  NPR-28400, NPR-28393: Hotfix do CQ-4244058, CQ-4244349
* Com permissão de leitura, os usuários/grupos não conseguem selecionar um XF e não têm opção para visualização do XF e suas propriedades de página. NPR-28341: Hotfix do CQ-4260412
* Os dados JSON recebidos do Público alvo têm vários caracteres de escape fazendo com que a página do aplicativo quebre. NPR-28318: Hotfix do CQ-4252043
* Não é possível editar nenhum componente após a instalação do AEM 6.4.3. NPR-28125: Hotfix para CQ-4261216
* A exclusão de todas as tags de um campo de tag não é persistente para um fragmento de conteúdo estruturado. NPR-28133: Hotfix do CQ-4247241
* Ao editar uma propriedade &quot;jcr:lastmodifiedby&quot; e &quot;jcr:lastmodified&quot; do Fragmento de conteúdo, os valores são atualizados sem que o usuário faça alterações. NPR-27847: Hotfix do CQ-4257138
* O controle de versão de Fragmentos de conteúdo compara as melhorias de diff para o AEM 6.4. NPR-27764
* Se não houver nenhum cq:allowTemplates definido em /content/experience-fragments e allowPaths for usado no modelo do Experience Fragement, um erro será lançado quando o Experience Fragement for movido/copiado. NPR-27487: Hotfix do CQ-4257489
* O botão Criar é exibido ao atualizar para o novo usuário. NPR-27335: Hotfix do CQ-4255360
* Ao tentar mover uma página publicada, a contagem &quot;Páginas de referência&quot; que aparece na primeira página do assistente &quot;Mover página&quot; está incorreta. NPR-28111: Hotfix do CQ-4259663
* (Interface de usuário de toque) O painel Referências não mostra os links de entrada. NPR-28529: Hotfix do CQ-4262306
* Não é possível editar qualquer componente e propriedades de página após a instalação do AEM 6.4.3. NPR-27998: Hotfix para CQ-4261216, CQ-4260441
* Migre o contexthub para jquery 3. NPR-28397: Hotfix do GRANITE-19902

**Comércio**

* Não é possível selecionar o catálogo se houver mais de 20 catálogos em uma pasta. NPR-27649: Hotfix do CQ-4258119
* visualizações de propriedades e assistentes comerciais estão quebrados devido à falta de header.referer. Hotfix do CQ-4261122

**Campaign - Direcionamento**

* com.day.cq.personalization.impl.TeaserResourceEventHandler entra em um loop infinito e causa atualizações em nós em instâncias públicas. Hotfix do CQ-4263096

**Replicação**

* Erro ao criar conteúdo de replicação com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix do CQ-4261401
* A sessão vazou quando a ID do agente do usuário está definida como admin no agente de replicação. NPR-28220: Hotfix do CQ-4255517

**DAM - Creative Cloud**

* Backport HTTP API para localizar imagens semelhantes de dentro de AEM Assets. Hotfix do CQ-4254091
* Aprimore a API ACP para permitir que os resultados de um query sejam restritos aos membros de uma coleção. Hotfix do CQ-4258708

**DAM - Formatos**

* Depois que a exportação de metadados é acionada, a página é redirecionada para uma página 404. Hotfix do CQ-4262447

**DAM - Geral**

* (Integração do Adobe Stock) O modal de erros do servidor é exibido com um erro Oauth no arquivo error.log. Hotfix do CQ-4260406
* A integração do Adobe Stock não funciona se a versão 6.4.4 for aplicada à versão 6.4.3. Hotfix para CQ-4266009
* O Link para o Modelo CF está ausente mesmo após a aplicação do patch SP3. Hotfix do CQ-4259029

**Plataforma**

* (Interface clássica) O botão de edição não está disponível no componente Relatório básico após a atualização para a versão 6.4.2. NPR-28560: Hotfix para CQ-4262825
* Ao usar um query que combina property.operation=like e property.depth, ele acaba em InvalidQueryException. NPR-28570: Hotfix do CQ-4262652
* Erro interno do servidor quando o nó de idioma recém-adicionado é removido do nó de idioma sobreposto. NPR-28661: Hotfix do CQ-4239194
* Exceção de ponteiro nulo em stderr.log no thread sling-oak-1 em start aleatórios. NPR-28665: Hotfix do CQ-4237845

**Felix**

* webconsole.plugins.memory usage causa um bloqueio na atualização. NPR-27895: Hotfix do GRANITE-20715

**Granite**

* A Verificação de integridade do Sling Content Access realiza validação excessiva /libs para o caminho de pesquisa do resolvedor de recursos personalizado. NPR-28113: Hotfix do GRANITE-23529

**Gerenciamento de fragmentos de conteúdo**

* Aprimoramentos de usabilidade e paridade de recursos com Ativos para Fragmentos de conteúdo. Hotfix do CQ-4253883

**Comunidades**

* Atualize o bootstrap vulnerável para as bibliotecas 3.4 e ckeditor para a versão 4.5.11. NPR-28490: Hotfix para CQ-4257511
* O cancelamento dos modos de edição não restaura o anexo excluído. NPR-27902: Hotfix do CQ-4255150
* A composição em nome da caixa deve ser visível apenas para os membros privilegiados. NPR-27900: Hotfix do CQ-4251235
* Adicione rep:cache em nós ignoráveis no AEM Communities User Sync Listener em instâncias de publicação. NPR-27842: Hotfix do CQ-4247234
* A caixa de pesquisa mostra o caractere de escape no nível da interface. NPR-27838: Hotfix do CQ-4259757
* O erro é gerado ao procurar caracteres especiais como ( , +,? em busca rápida. NPR-28213: Hotfix do CQ-4260969
* Crie um grupo de &quot;administradores específicos da comunidade&quot; para que os usuários possam editar e criar o site da comunidade relevante. NPR-27731
* Adicionada lógica para o evento do teclado para abrir o vídeo. NPR-27726: Hotfix do CQ-4254026
* Ativação da navegação por teclado para componentes de ativação do AEM Communities em Publicar. NPR-27728: Hotfix do CQ-4254028
* Rótulo cardíaco adicionado para lista e botão de visualização da placa. NPR-27727: Hotfix do CQ-4254027
* Manuseio de sessões abertas do solucionador de recursos no Social - Comunidades. NPR-27721: Hotfix do CQ-4258714

**Tradução**

* Forneça suporte para Microsoft Translator Text API v3. NPR-28366: Hotfix do CQ-4249755
* jcr:language &amp; cq:language não são automaticamente atualizados no idioma traduzido. NPR-28338: Hotfix do CQ-4256046
* Referências cíclicas causam StackOverflowError ao criar uma cópia de idioma. NPR-27596: Hotfix do CQ-4255621
* Em um projeto de tradução em vários idiomas, clicar em salvar e fechar resultados em páginas subsequentes adicionadas ao projeto resultará na criação de novos projetos em vez de novas tarefas de tradução serem criadas no projeto existente. NPR-28219, NPR-28236: Hotfix do CQ-4261276, CQ-4260731
* Sequência de erro muito longa ao adicionar fragmento de conteúdo com dados em massa devido à limitação do número de caracteres permitidos. NPR-28722: Hotfix do CQ-4262362

**Social**

* O comentário publicado na próxima página é destacado em amarelo toda vez que um novo comentário é publicado. Hotfix do CQ-4261359
* Não é possível excluir comentários no Conteúdo gerado pelo usuário usando a API. NPR-28075: Hotfix do CQ-4261135
* AbstractNotificationOperationService causa ClassCastException. Hotfix do CQ-4260456
* Remova a referência à Nuvem do modelo de referência de objeto do conteúdo compartilhável (SCORM) no reprodutor. Hotfix do CQ-4260779

**IU - Foundation**

* O recurso &quot;Cache de saída do sistema de arquivos&quot; integrado no HTML Client Library Manager quebra o recurso &quot;debugClientLibs&quot; para scripts compilados como arquivos LESS. NPR-27249: Hotfix do Granite-23313
* O número de ativos exibidos quando o modo de depuração é ativado é sempre 1 e muitos erros JS são lançados no console do navegador.  NPR-27575: Hotfix do GRANITE-23750
* Salvar e fechar as propriedades da página não retorna à página correta no AEM WAR com Tomcat. NPR-27566: Hotfix do GRANITE-23671

**Integração**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` entra em um loop infinito e causa atualizações para nós em instâncias de publicação. NPR-28561: Hotfix do CQ-4263096
* As ações cq:não são consideradas para um componente direcionado. NPR-27616: Hotfix do CQ-4257497
* O cancelamento da herança do LiveCopy não funciona corretamente em container direcionados. NPR-28129: Hotfix do CQ-4259813
* (Configurações de Cloud Service) A caixa de seleção &quot;herdado de&quot; que aparece no nível raiz deve ser removida. NPR-27856: Hotfix do CQ-4259676

**Sling**

* Atualização para a API Sling Models 1.3.8, Impl 1.4.10. NPR-27636: Hotfix para GRANITE-23537

**OAK - Persistência do segmento**

* SegmentBufferWriter não liberado após OnRC. NPR-27464

**Projetos**

* O projeto de tradução de vários idiomas não está criando vários trabalhos de idioma para os usuários que não fazem parte do grupo de administradores. NPR-28508: Hotfix do CQ-4262023
* O ProjectTaskListServlet está vazando um ResourceResolver sempre que getTaskRenderers é chamado durante a inicialização do serviço. NPR-27590: Hotfix do CQ-4258011
* Se um diretório tiver mais subdiretórios do que o tamanho da página e a ordem for por data ou tamanho, um erro impedirá que a página se mova para além da primeira. NPR-28867: Hotfix do CQ-4265039
* Correções de script entre sites (XSS) de backport nos visualizadores DAM. NPR-28106: Hotfix do CQ-4253215
* Não é possível adicionar páginas ao projeto de tradução por administradores de projeto, pois o link para adicionar novas páginas ao projeto de tradução não está visível. Hotfix do CQ-4266334

**Fluxo de trabalho**

* Quando abrimos a caixa de diálogo de item de trabalho completo na notificação do fluxo de trabalho que tem um campo de tag , clicar em uma marca cruzada adiciona uma propriedade de tag a ela. NPR-28304: Hotfix do CQ-4261321
* O botão Alternar seleção de usuário na caixa de diálogo Reatribuir Tarefa não está funcionando. NPR-28963: Hotfix do CQ-4264206

**Forms**

Os principais destaques dos formulários do AEM 6.4.4.0 são:

* Adicionado suporte para registrar APIs de segurança de documentos para assinatura e certificação como transações.

**Pacote complementar do Forms**

**Integração do Adobe Sign**

* O AEM 6.4 Forms Client SDK não contém o pacote adobesign-recipent. NPR-27735: Hotfix do CQ-4259372

**Formulários adaptáveis**

* Quando o formulário adaptável Wan é criado com um modelo em branco, os clientes não conseguem criar painéis filho no painel raiz do formulário. NPR-28758: Hotfix do CQ-4264157
* Quando o valor do campo de ano do componente de data é 9999, o script de validação falha. NPR-28580: Hotfix do CQ-4262620
* Quando um formulário adaptável é criado com um modelo em branco, os clientes não podem criar painéis filho no painel raiz do formulário. NPR-28758: Hotfix do CQ-4264157
* Não é possível definir o valor entre os campos de fragmentos carregados lento de um formulário adaptável. NPR-27758: Hotfix do CQ-4259703
* O formulário adaptável não usa o Editor de Rich Text, mas carrega suas bibliotecas.  NPR-27759: Hotfix do CQ-4259193
* Redirecionar para URL não está funcionando para formulários adaptáveis incorporados em uma página de AEM Sites. NPR-27620: Hotfix do CQ-4239287
* Não é possível definir o valor entre os campos de fragmentos carregados lento de um formulário adaptável. NPR-28320: Hotfix do CQ-4262345
* O formulário adaptável não usa o Editor de Rich Text, mas carrega suas bibliotecas.  NPR-28001: Hotfix do CQ-4259703, CQ-4259193
* A assinatura de script não funciona para o aplicativo AEM Forms em execução no Apple iOS 12.1. NPR-28497: Hotfix para CQ-4261765
* Enviar ação usando os problemas de criação do &quot;Fluxo de trabalho do Forms&quot; Classic em 6.4. Hotfix para CQ-4252740
* Erro ao manipular remoção de bloco e armazenamento tmp. NPR-28806: Hotfix do CQ-4264441

**Forms - Gerenciamento de correspondência**

* Falha na interface do agente ao manter o tamanho original da imagem. NPR-28800: Hotfix do CQ-4259767
* Interface do agente/CCR: Os campos Rótulos de data foram deslocados na guia Dados. Hotfix do CQ-4255499

**Formulários - Relatórios de transação**

* Adicionado suporte para contar usando assinaturas digitais ou certificando um documento como transações faturáveis. NPR-28495: Hotfix do CQ-4260236
* Assinatura digital adicionada e certificado à API faturável. Hotfix do CQ-4260236

**Gerenciamento de formulários**

Adicionado suporte para substituir o uso da biblioteca de cliente handlebars pelo underscore no assistente de revisão de start do Forms Manager e no assistente de movimentação de ativos. NPR-27643: Hotfix do CQ-4246536.
Um pacote permanece no estado instalado após a instalação do pacote de gerenciamento de formulários na ramificação release/640. Hotfix para CQ-4265410Formulários enviados com anexos não aparecem no fluxo de trabalho com a ação de envio &quot;Chamar fluxo de trabalho do AEM Forms&quot; e habilitar envio do portal marcado. Hotfix do CQ-4263110

**Forms - Integração de backend**

* Não é possível fazer testes de pré/pós-processador e envio personalizado usando o SDK do cliente, Hotfix para CQ-4238469

**Instalador do Forms JEE**

**Forms - Segurança de documentos**

* Ao usar o serviço updatepolicy, ocorre o erro de objeto não pode ser sobreposto. NPR-28751: Hotfix do CQ-4252287
* Falha na criação de assinatura com a versão mais antiga do commons-pkg. Hotfix do CQ-4265535

**Forms - Foundation JEE**

* Quando o AEM Forms está instalado no IBM WebSphere, a criação de um Modelo de dados de formulário com base no SOAP falha. NPR-27923: Hotfix do CQ-4251134
* A ferramenta SRT do Gerador de PDF não detecta a versão instalada do Adobe Acrobat. NPR-27971

**Forms - Designer**

* Algumas imagens JPEG em um modelo XDP não são renderizadas corretamente.  NPR-26702: Hotfix do LC-3917457

**Formulários - OBSOLETOS**

* O serviço de captura de papel falha ao processar arquivos TIFF. NPR-28079: Hotfix do CQ-4240649

**Forms - Fluxo de trabalho**

* Os formulários HTML5 com processo de envio padrão em an.lca não funcionam no JBoss 7. NPR-28675: Hotfix do CQ-4243928
* Não é possível enviar PDF forms na área de trabalho HTML. NPR-28058: Hotfix do CQ-4260373
* Os dados do cliente são impressos em registros de informações usando o Fluxo de trabalho Invocar formulários de serviço do FDM. Hotfix do CQ-4260385

**Feature Packs incluídos**

**Sites**

* O controle de versão de Fragmentos de conteúdo compara as melhorias de diferença para o AEM 6.4.  NPR-26760: FP para CQ-4248839
* Melhorias na diferença de fragmentos de conteúdo para o AEM 6.4.  NPR-27866: FP para CQ-4248839
* Recurso ativado na configuração do OSGI **AEM Workflow Retirar recurso Sinalizador**. A ação de retirada deve encerrar a instância do fluxo de trabalho depois de definir o sinalizador. NPR-26451: Hotfix do CQ-4259090

**Plataforma**

* A Extração de faceta aprimorada do Construtor de Query aproveita a API Oak para 6.4. NPR-26674: FP para CQ-4230337

**Pacotes OSGI e pacotes de conteúdo incluídos**

O texto seguinte documentos a lista dos pacotes OSGI e dos pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.4.0

[Obter arquivo](assets/bundles_6_4_4_0.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.4.0

[Obter arquivo](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

O AEM 6.4.3.0 é uma atualização importante que inclui correções e melhorias de desempenho, estabilidade, segurança e essenciais para o cliente lançadas desde a disponibilização geral do AEM 6.4 em abril de 2018.

Ele também é cumulativo, o que significa que a versão 6.4.3.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.3.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.9.
* Adicionado suporte para a propriedade allowPaths nos modelos de formulários adaptáveis.
* Pesquisa aprimorada baseada em painel para ativos no AEM
* Correções de script entre sites (XSS) na página Login.
* Melhoria na instrumentação da interface do usuário.
* Melhorias no gerenciamento de FormData.
* Manuseio aprimorado da nomeação de item dentro de um Vários campos.
* Manuseio aprimorado de itens de espaço reservado (Visualização de cartão e Visualização de Lista) durante a seleção.
* Adicionada a Autenticação IMS da Adobe e o suporte da Admin Console para Serviços gerenciados.

**Assets**

* O fluxo de trabalho do Ativo de atualização de DAM não extrai referências de arquivos INDD se a opção Desduplicação de IDS estiver ativada. NPR-26243; Hotfix para CQ-4250933
* A mensagem de sucesso não é exibida quando os ativos são publicados com o Editor de itens em massa. NPR-26252; Correção para CQ-4251688.
* Ao observar um ativo a partir de um resultado de pesquisa, se você clicar no botão Voltar no navegador, a mensagem de erro &quot;Solicitação incorreta&quot; será exibida com o código de erro 400. NPR 26578; Hotfix para CQ-4253741
* Os metadados do ativo mostram um erro de namespace inválido após a instalação de um service pack. NPR-22341; Quickfix para CQ-4237202
* A opção para reordenar pastas e fragmentos de conteúdo na visualização de lista não é exibida para as pastas aplicáveis. NPR-27153; Hotfix para CQ-4255873
* Os usuários não podem adicionar ativos a uma nova coleção, pois isso resulta em uma mensagem de erro com uma imagem quebrada na caixa de diálogo pop-up de erro. NPR-22431; Hotfix para CQ-4237086
* A lista suspensa em cascata não é compatível com listas suspensas dinâmicas. NPR-27043; Hotfix para CQ-4252564
* Se os usuários definirem um valor não padrão para a &#39;Pasta raiz de Empresa&#39; na configuração da nuvem do DMS7, a predefinição do visualizador não funcionará como esperado. NPR-26360; Hotfix para CQ-4249505
* O relatórios do ativo está falhando em casos com um número muito grande de ativos. NPR-27278; Hotfix para CQ-4256748
* As subpastas não herdam o perfil de imagem SmartCrop da pasta pai. NPR-27197; Hotfix para CQ-4256273
* Quando a integração com o Dynamic Media é ativada, algumas propriedades de metadados do Assets são modificadas. Os atributos de largura, altura e local não são exibidos. NPR-27203; Hotfix para CQ-4256258
* A Dynamic Media não usa o proxy configurado para alguns tipos de ativos. NPR-25211; Hotfix para CQ-4244871
* A página do Editor de metadados contém Exceção de ponteiro nulo para parâmetro de item inválido. NPR-26169; Correção para CQ-4241368.
* Se uma lista suspensa tiver uma regra de escolha e uma regra obrigatória for aplicada a ela, a regra necessária não poderá ser cumprida no editor de metadados. NPR-27479; Correção do CQ-4251428

**Sites**

* Um usuário pode controlar os recursos do editor de rich text no modo de tela cheia em linha usando políticas de conteúdo, mas não pode controlar os recursos do editor de rich text da caixa de diálogo Editar com políticas de conteúdo. NPR-26750: Hotfix do CQ-4241130
* O editor de Rich Text se torna inutilizável quando alternado de tela cheia para caixa de diálogo flutuante. A visualização flutuante contém dois editores de rich text. NPR-25589: Hotfix do CQ-4206008
* Quando a tecla de retorno (Enter key) é pressionada em um campo de texto, o editor de Rich Text muda para o modo de tela cheia. NPR-26204: Hotfix do CQ-4245893
* O plug-in de Lista do editor de Rich Text é desativado automaticamente e não permite modificações. NPR-26507: Hotfix do CQ-4239387
* Quando um caractere especial é adicionado à janela do editor de Rich Text, a janela é rolada para a parte superior. NPR-26435: Hotfix do CQ-4249869
* Perguntas sobre o armazenamento em cache segment.js do Client Context vs. O não armazenamento em cache. NPR-26622: Hotfix do CQ-4253486
* Quando uma regra secundária é ativada da instância do autor para a instância de publicação, a instância de publicação para de funcionar. NPR-26601: Hotfix do CQ-4253588
* Quando o editor de rich text é combinado com vários campos, ocorre o erro Uncaught TypeError: fieldAPI.getName is not a function at foundation.js. NPR-27146: Hotfix do CQ-4253155
* A integração do Salesforce não pode usar a configuração de proxy. NPR-27244: Hotfix do CQ-4245300
* Quando você agendar uma página para ativação usando a opção Gerenciar publicação para uma data posterior e alternar para a visualização de lista, o ícone de calendário estará ausente. NPR-26974: Hotfix do CQ-4239206
* Os usuários não podem editar permissões de grupo de usuários fechados nas propriedades da página. NPR-27138: Hotfix para CQ-4256089Não é possível editar tags por meio de marcação. NPR-26957: Hotfix do CQ-4254858
* Quando uma tag referenciada a partir de um modelo de fragmento de conteúdo estruturado é movida, as referências existentes à tag dentro de um fragmento de conteúdo não são atualizadas. Isso acontece na tela de edição do modelo de fragmento do conteúdo. NPR-26776: Hotfix do CQ-4251805
* Quando você cria e promove uma inicialização com várias páginas, várias versões para cada página são criadas. NPR-26917: Hotfix do CQ-4254663
* O administrador do site do AEM não lida com caminhos digitados na barra de endereços do navegador. NPR-26780: Hotfix do CQ-4254097
* Quando uma página é movida para um novo local sem renomeá-la, o histórico de versão da página é perdido. NPR-26706: Hotfix do CQ-4254025
* Os URLs no editor de administração de fragmentos de experiência não permitem sobreposições. NPR-26319: Hotfix do CQ-4252156
* Quando uma página é criada com um modelo contendo um fragmento de experiência vazio e publicada, a página falha ao abrir e ocorre um erro de DefaultSlingScript. NPR-26305: Hotfix do CQ-4252460
* Quando o uso inteligente de dados é usado com classes com nome idêntico, o código não compatível é produzido. NPR-27282: Hotfix do Sling-7581
* Após a instalação da controladora de upgrade, os sites têm uma configuração de implantação de blueprint em branco. NPR-27609: Hotfix do CQ-4257078

**DAM - Portal da marca**

* Os predicados de tag não são publicados quando o formulário de schema de metadados é publicado no Brand Portal. Hotfix do CQ-4256218
* Quando uma pasta de terceiro nível é publicada do AEM para o Brand Portal, sem publicar as pastas pai, o nome da pasta muda. Hotfix do CQ-4255423
* O predicado do navegador de caminho é publicado do AEM Assets para o Brand Portal, conforme esperado. No entanto, o caminho publicado na BP permanece /content/dam, que deve ser atualizado. Hotfix do CQ-4256240

**DAM - Creative Cloud**

* O ícone &quot;Pesquisar ativos Adobe&quot; está ausente na navegação principal do AEM. Hotfix do CQ-4254343

**DAM - Cliente DM**

* Depois de assimilar vídeos em uma pasta associada ao Perfil AVS Video Processing, a janela do navegador é atualizada repetidamente. Hotfix do CQ-4253563
* A publicação do YouTube falha ao usar uma tag ad hoc que inclui caracteres em maiúsculas. Hotfix do CQ-4252477
* Quando uma anotação é criada em um ativo como PDF, a interface do usuário start um loop de atualização de página infinito. NPR-27052: Hotfix do CQ-4255396

**DAM - Serviços DM**

* A Dynamic Media não usa o proxy configurado para alguns tipos de ativos. NPR-10727; Hotfix para CQ-4244871

**Plataforma**

* Problemas de desempenho com org.apache.sling.i18n. NPR-26812: Hotfix para SLING-7543
* Não é possível ver as propriedades do nó quando o XML de entrada é formatado e implantado. NPR-26198: Hotfix do CQ-4250448
* IndexOutOfBoundsException em ResourceProviderTracker. NPR-26968: Hotfix do GRANITE-23310
* O console JMX acumula várias sessões administrativas e uma nova sessão é aberta a cada 5 minutos. NPR-26958: Hotfix do CQ-4251090
* Após a atualização da versão 6.2 para a 6.4, o arquivo de log mostra o rastreamento da pilha para o resolvedor de recursos não fechado com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176: Hotfix do Granite-21734
* Quando um agente despachante pronto para uso é configurado para atualizar aliases, a operação falha com StackOverflowError. NPR-26373: Hotfix do CQ-4242928
* A replicação usa o token OAuth expirado até que falhe. NPR-25894
* Página restrita (página Grupo de usuários fechado) com sling: o alias não redireciona o usuário para a página de logon. NPR-25715: Hotfix para Granite=22263
* Nas tags de publicação, nenhuma atividade é exibida na interface do usuário. Hotfix do CQ-4255961
* Não é possível editar tags na interface clássica. Hotfix do CQ-4258697
* Atualização de org.apache.felix.http.bridge para a versão 4.0.4. NPR-27038: Backport for Granite - 23334
* Os registros de atividades do gerenciador de pacotes devem ser extraídos em um arquivo de registro separado. NPR-27323: Hotfix do Granite-14866
* O validador de pacote não informa sobreposições no CFP. NPR-27119: Hotfix do GRANITE-22825

**Projetos**

* A API ACP manipula incorretamente a paginação somente com filhos do subdiretório. NPR-27617: Hotfix do CQ-4258639

**OAK**

* Não é possível fazer logon no repositório após a instalação do AEM 6.4 Service Pack 2. NPR-27171: Hotfix do Granite-23317

**Replicação**

* O Log de auditoria permanece aberto com sessões ativas que continuam aumentando constantemente com ~750 a cada dia. NPR-27062: Hotfix do CQ-4241350

**Comunidades**

* As publicações e respostas do Fórum são adicionadas à parte superior da segunda página e, quando atualizadas, a publicação é movida para o local correto na parte superior da primeira página. NPR-27342: Hotfix do CQ-4247338
* Os links para todos os recursos soltam o caminho de contexto (/aempublish) após a rolagem. NPR-26982: Hotfix do CQ-4254345
* Os grupos adicionados não estão visíveis no menu suspenso Gerentes da comunidade, Moderadores da comunidade e membros privilegiados ao editar um site publicado. NPR-27190: Hotfix do CQ-4258574
* Somente 10 grupos são listados na página de recursos de ativação, mesmo se a paginação estiver ativada para a listagem de grupos. NPR-26934: Hotfix do CQ-4252985
* A opção para habilitar/desabilitar a pesquisa para o componente Publicação agendada no journal é fornecida no ConfigMgr, e o trabalho SearchScheduledPosts é otimizado. NPR-26923: Hotfix do CQ-4250463
* A pesquisa por palavras-chave no endereço não funciona na página do componente de calendário quando a comunidade AEM está definida para trabalhar com DSRP. NPR-26737: Hotfix do CQ-4258493
* Foi implementado um link direto para o comentário, em vez da publicação principal nos detalhes do comentário, para a interface do usuário de moderação e recursos de ativação. NPR-26704: Hotfix do CQ-4251381
* O conteúdo moderado por meio da seleção múltipla no console de moderação não aparece no Fluxo de Atividades. NPR-26695: Hotfix do CQ-4253244
* A pesquisa com nome e sobrenome no campo Mensagens de comunidades em Para não retorna o resultado esperado. NPR-26385: Hotfix do CQ-4248673
* Erro observado ao carregar um anexo diferente de imagem (por exemplo, .pdf) no Fórum. NPR-27360: Hotfix do CQ-4257753
* Desfixar ou cancelar o recurso de uma publicação do fórum não funcionará se a opção Autor-Publicação estiver definida com o MySQL DSRP. NPR-26125; Hotfix para CQ-4251520
* Os componentes da coleção (fóruns, blogs, calendário, ideação, QnA) agora têm uma propriedade na caixa de diálogo do componente para ativar/desativar &quot;Bloquear UGC no modo de edição do autor&quot;, para permitir/negar o carregamento UGC no modo de edição do WCM. NPR-26978: Hotfix do CQ-4248161
* A pesquisa de tags não funciona para termos de pesquisa localizados. NPR-26171: Hotfix do CQ-4249926
* O botão Voltar ignora uma página na pesquisa do fórum. NPR-26950: Hotfix do CQ-4254804
* A instância AEM em execução na porta Http padrão (80) não pode acessar imsmanifest.xml. NPR-27173: Hotfix do CQ-4252211
* Desmarcar comentário como uma resposta para QnA não funcionará se AEM Communities forem definidos com DSRP. NPR-26247: Hotfix do CQ-4252232
* Não é possível chamar o Armazenamento da Adobe: Erro 414 - URI GET longo observado quando os usuários pesquisam /content/community-components/en/search.html e selecionam o campo autor como um dos filtros para esse termo de pesquisa. NPR-26643: Hotfix do CQ-4251303
* O valor suspenso para DataCenterURL na configuração ASRP foi alterado de Dallas para Virginia (para VA6). NPR-26936: Hotfix do CQ-4254434
* Caracteres especiais na pesquisa de fórum retornam erros ou nenhum resultado. NPR-26930: Hotfix do CQ-4247744
* O número exibido para &quot;Número de resultados&quot; na pesquisa no fórum usa delimitador incorreto para localidades em inglês e alemão. NPR-27050: Hotfix do CQ-4248939
* As notificações não lidas não aumentam para além de 21. NPR-26946, NPR-27480: Hotfix do CQ-4252829, CQ-4256939
* A paginação na seção de comentários de qualquer componente faz com que os usuários rolem para cima para ver o conteúdo da página, ao acessar uma página por meio da paginação. NPR-27032: Hotfix do CQ-4251228
* A pasta do site da comunidade não pode ser clicada na imagem em miniatura ao exibir do console de administração na instância do AEM Author. NPR-26986: Hotfix do CQ-4254036
* A opção &quot;marcar todas as leituras&quot; marca somente as primeiras 10 notificações como lidas e outras permanecem não lidas até que uma página seja atualizada. NPR-27037: Hotfix do CQ-4254058
* A paginação não é acionada para Ideação e a lista de tópicos (ou respostas) fica mais longa a menos que seja recarregada. NPR-26193: Hotfix do CQ-4252104
* atividades de outros usuários e UGC excluído visíveis ao fazer logon com credenciais de moderador e adicionar &quot;#social-atividades&quot; ou &quot;#tabs-2&quot; ao final do URL do perfil do moderador. Hotfix do CQ-4251355
* Não é possível remover todas as tags atribuídas de um artigo de blog. NPR-26851: Hotfix do CQ-4253359
* As relações com o UGC não são excluídas na exclusão do UGC. NPR-27630: Hotfix do CQ-4258706
* O link para respostas não funciona em um clique de linha nas respostas do fórum. NPR-27623: Hotfix do CQ-4256138
* O limite de assinatura do usuário é limitado a 1000. NPR-27614: Hotfix do CQ-4254689
* Editar um site e editar funções nas configurações de função cria uma Exceção de Ponteiro Nulo. NPR-27377; Hotfix para CQ-4255909

**Tradução**

* A pré-visualização de tradução não funciona com o conteúdo de amostra we.retail. NPR-26727: Hotfix do CQ-4241179

**IU - Foundation**

* Uma NullPointerException é retornada ao tentar baixar configurações após a atualização para o AEM 6.4. NPR-27310: Hotfix para Granite-23573
* Backport pró-ativo para correções granite.platform.login. NPR-26941
* Backport Pró-ativo para granite.ui.coções do Intent. NPR-26294
* O componente de campo numérico não valida números negativos no Internet Explorer 11. NPR-26701
* Backport pró-ativo para correções granite.ui.coralui3. NPR-26662
* Backport pró-ativa para correções granite.ui.coralui3-eon. NPR-26666
* Backport pró-ativo para correções granite.ui.foundation.components. NPR-27313
* Backport pró-ativo para correções granite.ui.commons. NPR-26753
* Backports proativos da interface do usuário do Foundation. NPR-26248

**Integração**

* As modificações em experiências do AEM criadas por meio do mecanismo de definição de metas não são publicadas. NPR-24869: Hotfix do CQ-4247832
* Não é possível criar várias atividades e experiências se seus nomes incluírem caracteres japoneses. NPR-27271: Hotfix do CQ-4256857
* Atualizar ponto de extremidade da API de inicialização. NPR-26790: Hotfix do CQ-4254380
* (Personalização) BrandsRetriever anda a árvore inteira. NPR-27060: Hotfix do CQ-4255790

**WCM - IU do administrador**

* Adicionado o teste HTTP para publicar/desfazer a publicação de uma página com referências e um teste de interface do usuário para Live Copy. Hotfix do CQ-4256894

**WCM - Editor de páginas**

* A barra de ferramentas Editar é desativada para componentes na primeira edição. Hotfix do CQ-4253270

**Forms**

Os principais destaques dos formulários do AEM 6.4.3.0 são:

* Ativado o suporte para uma matriz/lista de objetos com Substituição de entidade dinâmica.
* Habilitada conformidade com FIPS para fluxo de trabalho do Reader Extended em Assinatura Digital, Extensões do Reader, CryptoProvider e TrustStore.
* Adicionado suporte PDF/UA a formulários XFA gerados com o Designer ou Serviço de saída.
* Ativado o suporte para a propriedade allowPaths em modelos de formulários adaptáveis.
* Adicionado suporte JBoss 7.1.4 para AEM Forms 6.4.

**Pacote complementar do Forms**

**Integração de backend**

* Não é possível preencher mapeamentos de modelo de dados de formulário com base em entidades dinâmicas na resposta SOAP. NPR-26428: Hotfix do CQ-4250639
* O valor para _elementNamespace no modelo de dados de formulário, dados adicionais inseridos usando a interface do usuário de teste, não é refletido corretamente na solicitação SOAP. Hotfix do CQ-4255373
* Uma restrição de propriedade anulável é inicializada com um valor padrão e não pode ser sincronizada com o FDM. Hotfix do CQ-4253873
* O valor padrão da propriedade anulável não está definido como True para a fonte de dados OData. Hotfix do CQ-4253870

**Formulários adaptáveis**

* Não é possível carregar sites e editor de formulários. NPR-26977; Hotfix para CQ-4249170
* Problemas ao adicionar um anexo a um formulário adaptável usando o teclado. NPR-25913; Hotfix para CQ-4249456

**Forms - Comunicação interativa**

* Não é possível mover um painel que foi adicionado usando a opção Adicionar painel filho na árvore de conteúdo no canal Web de Interative Communication e em formulários adaptáveis. Hotfix do CQ-4253915
* Os nomes de tabelas são exibidos em vez do título da associação FDM na seção Fontes de dados do canal Imprimir. Hotfix do CQ-4253669
* A função isUseXFABullets() não está desativada na classe PrintChannelRenderOptions e está disponível no SDK do cliente. Hotfix do CQ-4246583, CQ-4252700

**Gerenciamento de correspondência**

* O Javadocs para 6.4 não contém o com.adobe.dbforms.* e as classes correspondentes. Hotfix do CQ-4253200
* A interface do usuário do CCR exibe um valor de lixo padrão para o campo de data, caso não haja nenhuma entrada do XML de dados de teste. Hotfix do CQ-4252041
* Se uma letra contiver um módulo de lista, o espaço entre o marcador e o texto será perdido ao gerar PDF a partir da letra. Hotfix do CQ-4250588

**Gerenciador do Forms**

* Ativado o suporte para a propriedade allowPaths em modelos de formulários adaptáveis. NPR-26598: Hotfix do CQ-4255892

**Forms - Fluxo de trabalho**

* Se houver chaves incluídas no nome da tarefa durante a execução do fluxo de trabalho do Forms , uma exceção será exibida nos logs. Hotfix do CQ-4256626
* Não é possível abrir um modelo de Pesquisa na área de trabalho do AEM Forms. Hotfix do CQ-4255651

**Formulários móveis**

* A notificação de saída não é exibida ao sair do campo de data em AEM Forms renderizados como HTML no Internet Explorer ou Chrome. NPR-26483: Hotfix do CQ-4239352
* Datas contidas no XML quando o processamento é iniciado faz com que os formulários exibam um erro de validação quando o usuário tenta sair do formulário. NPR-26787: Hotfix do CQ-4251211

**Instalador do Forms JEE**

**Serviço do Gerador de PDF**

* Não é possível exibir as configurações de Relatórios de padrões e conformidade para o Gerador de PDF. NPR-26715: Hotfix do CQ-4253384
* o arquivo binário convertpdf está ausente no pacote complementar AIX Forms, o que causa falha ao chamar o serviço PDFA. Hotfix do CQ-4257873

**Serviços de documentação**

* Adicione conformidade com FIPS para fluxo de trabalho RE em Assinatura Digital, Extensões do Reader, CryptoProvider e TrustStore. NPR-27495: Hotfix do CQ-4257572
* A conversão falha ao executar o serviço AssemblerService.toPDFA em um loop. NPR-26354: Hotfix do CQ-4248656
* Não é possível validar a conformidade dos PDFs corretamente com base nos padrões PDF/A-1b. NPR-26286: Hotfix do CQ-4227539
* Problemas de memória insuficiente ao atualizar AEM Forms do 6.1 SP2 CFP5 para CFP13. NPR-26285: Hotfix do CQ-4244379
* Não é possível validar a conformidade dos PDFs corretamente com base nos padrões PDF/A. NPR-26272: Hotfix do CQ-4248823

**Forms - Foundation JEE**

* Adicionado suporte JBoss 7.1.4 para AEM Forms 6.4. NPR-27331; Hotfix para CQ-4255601

**Feature Packs incluídos**

* Ativado o suporte para uma matriz/lista de objetos com Substituição de entidade dinâmica. NPR-26590: Hotfix do CQ-4254655

**Pacotes de conteúdo e pacotes OSGI incluídos**

Lista de pacotes OSGi incluídos no AEM 6.4.3.0

[Obter arquivo](assets/6.4.3.0_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.3.0

[Obter arquivo](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**
Ele também é cumulativo, o que significa que a versão 6.4.2.0 inclui todos os service packs do AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.2.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.7.
* Adicionado suporte para recursos da Especificação 1.4 da Linguagem de Modelo HTML (HTL)
* Adição de suporte ao MongoDB Enterprise 3.6.
* O Editor de páginas de sites adiciona suporte para edição e composição no contexto com componentes do cliente criados no React ou Angular em combinação com o SDK <a href="../sites-developing/spa-walkthrough.md">JS do Editor SPA do</a>AEM.
* Aprimoramentos de fragmentos de conteúdo: foi adicionada a capacidade de anotar em campos de texto e comparações lado a lado de versões.
* Adicionada [integração com o Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que os usuários possam pesquisar, pré-visualização, salvar e licenciar ativos do Adobe Stock diretamente da interface do usuário do AEM. Para obter informações mais detalhadas, consulte [Uso de ativos do Adobe Stock com AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/stock-assets-feature-video-use.md).
* Os ativos adicionaram suporte para metasesquema condicional dinâmico e a capacidade de definir um schema de metadados para pastas de ativos.
* Adicionada configuração em cada componente para ativar/desativar a funcionalidade de criação/atualização de miniaturas de pastas.
* Aprimoramentos do Editor de imagens na criação de páginas.
* Correção de regressão em Comunidades para o evento de pontuação que não é processado corretamente em caso de resposta selecionada ser excluída.
* Limite máximo de resultados da pesquisa revisado para solr para MAX_INT-10000.
* O trabalho de Liberação de Transação é iniciado somente na primeira chamada para storeTransaction.
* O botão &quot;Selecionar tudo&quot; agora está disponível em Visualização de cartão e Visualização de coluna.
* Aprimoramentos de acessibilidade na CoralUI.
* Funcionamento de Coral.Keys aprimorado.
* Atualização de Momento.js para 2.2.2
* Jquery atualizado para 1.12.1
* Introduzido o componente de status do fluxo de trabalho da fundação.
* Atualização do GCC para a versão mais recente.
* Mova o SAML para a nova sincronização externa do IDP.

**Assets**

* A geração de subativos para o arquivo pptx não contém imagens e miniaturas. NPR-24286: Hotfix do CQ-4217986
* migrateAllAssets - adicione suporte ao processamento em lote e aprimore o método AEM que adiciona UUID aos ativos antigos. NPR-24861: Hotfix do CQ-4242863 e CQ-4247874
* Problema de desempenho com a geração de miniaturas. NPR-24693: Hotfix do CQ-4246960
* (Interface do usuário para toque) O componente &quot;predicado de opções&quot; permanece em branco quando adicionado à página do editor de compartilhamento de ativos. NPR-24643: Hotfix do CQ-4245295
* (Fluxo de trabalho) Os ativos Smart Tag não são processados pela configuração de proxy. NPR-25840: Hotfix do CQ-4248202
* (Omnisearch) remover filetype:image dos critérios de pesquisa não remove o tipo de imagem. NPR-25232: Hotfix do CQ-4248280
* Ao tentar mover um arquivo para uma pasta diferente, as pastas com apóstrofo em seu nome não são exibidas. NPR-25125: Hotfix do CQ-4248660
* O controle deslizante na página Subasset não funciona corretamente quando a preferência do idioma é definida para outro idioma que não o inglês. NPR-25274: Hotfix do CQ-4248489
* Problema com o arquivo csv de exportação de metadados quando aberto em máquinas com formato de número europeu. NPR-26009: Hotfix do CQ-4250677
* O botão Criar não está disponível na seleção da pasta do ativo sem a permissão &quot;excluir&quot;. NPR-25788: Hotfix do CQ-4250140
* (Backport) Aprimoramentos de acessibilidade: ID do Duplicado: o valor do atributo id deve ser exclusivo, Rótulo: Os elementos de formulário devem ter rótulos e Nome do link: Os links devem ter um texto perceptível. NPR-24252: Hotfix do CQ-4250905, CQ-4250906, CQ-4250907
* Fazer upload de um csv com campos separados por &quot;&quot; falha para países europeus. NPR-25549: Hotfix do CQ-4249931
* (Portal de marcas) Os subativos de um arquivo pdf de várias páginas não são publicados quando um ativo é publicado. NPR-25991: Hotfix do CQ-4245162
* Publique a funcionalidade posterior para a replicação do AEM para o Brand Portal. NPR-25911: Hotfix do CQ-109139
* Publicar e cancelar a publicação da coleção privada por usuários não administradores resulta em um NPE. NPR-25906: Hotfix do CQ-4250594
* Desative a publicação de fragmentos de conteúdo e schemas de formulário no Brand Portal. NPR-24176, NPR-26004: Hotfix do CQ-4251592, CQ-4252026
* (Dynamic Media) Visualizadores DM atualizados para a versão 5.10.1, que permite a verificação de nomes de duplicados na página Predefinição de imagem. Consulte Atualizar visualizadores do Dynamic Media (5.10.1). NPR-24403: Hotfix do CQ-4247554
* Erro de JavaScript no console do navegador na visualização da coluna ao selecionar um ativo ou pasta. NPR-25939: Hotfix do CQ-4250228
* (visualização de coluna) Não é possível identificar tarefas como o arquivo de chave é exibido como uma entrada em branco. NPR-25903: Hotfix do CQ-4246307

**Sites**

* O Query de datasource.jsp no AEM 6.2 é diferente do AEM 6.4. NPR-24968: Hotfix para CQ-4244235
* (Interface clássica) Não é possível adicionar tags a páginas. NPR-25255, NPR-25612: Hotfix do CQ-4249615
* Recursos da Especificação de linguagem de modelo HTML 1.4 suportados para o AEM 6.4.2.0 NPR-24585
* Herança incorreta no componente local após copiar uma página de cópia online. NPR-25920: Hotfix do CQ-4236737, CQ-4248957
* O tempo ON/OFF é armazenado em crx/de, mas não é obtido o mesmo no console da interface do usuário das propriedades da página. NPR-25154: Hotfix do CQ-4243431
* Estilos O sistema quebra os valores iniciais das propriedades da caixa de diálogo. NPR-25648: Hotfix do CQ-4250073
* Ao definir uma propriedade cq:tagName em um nó cq:htmlTag, o nome da tag não será considerado se o componente for incluído via JSP. NPR-24154: Hotfix do CQ-4244120
* Para componentes parsys aninhados, sempre o primeiro (com caminho menos aninhado) design satisfatório é aplicado de vários componentes disponíveis. Para obter mais informações, consulte Resolução [do caminho de](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/page-templates-static.html)design. NPR-24973: Hotfix do CQ-4246276
* Ao colar texto em um componente RTE, uma caixa de diálogo pop-up é exibida, mas não é renderizada corretamente. NPR-24895: Hotfix do CQ-4245901
* (RTE) Problemas de desempenho com indicador de campo obrigatório. NPR-24894: Hotfix do CQ-4241895
* (Componente de página) Adicionar um componente ao Parsys é cortado da direita e sai da largura do quadro do dispositivo. NPR-25536: Hotfix do CQ-4238224
* O editor de texto simples envia dados não aparados e adiciona espaços extras. NPR-25312: Hotfix do CQ-4249006
* Ao abrir o componente usando o modo de inversão, os plug-ins carregados anteriormente não ficam visíveis na segunda vez. NPR-24610: Hotfix do CQ-4236850
* Carregar um XF na visualização do editor copiando/colando não carrega a variação principal automaticamente. NPR-24841: Hotfix do CQ-4248037
* Estrutura HTML incorreta no siteadmin / damadmin quebra o IE11. NPR-24686: Hotfix do CQ-4246363, CQ-4248402
* (Assistente de gerenciamento de publicação) O calendário para a data de ativação na etapa Opções não é aberto após algumas ações na etapa Escopo. NPR-25681: Hotfix do CQ-4250205
* A interface do usuário clássica não funciona para editar o CUG pois está obsoleta. NPR-25075: Hotfix do 4241823
* Opção Criar indisponível para criar fragmentos de experiência. NPR-26053: Hotfix do CQ-4249923
* A variação XF está sendo ativada duas vezes, gerando IDs de duplicado para o mesmo item. NPR-24179: Hotfix do CQ-4245093
* A tabela do Foundation é vulnerável a Scripts armazenados entre sites. NPR-25185: Hotfix do CQ-4240760
* Erro de &#39;valor inválido do seletor de recursão&#39; ao migrar um componente do AEM 6.2.1.13 para o AEM 6.4. NPR-24146

**WCM - Editor de páginas**

* Vários Parsys empilhados devido a consultas de longa duração (mais de 6) deixam o AEM lento. Hotfix do CQ-4240247
* Erro de JS ao adicionar cq:tagName vazio no nó cq:htmlTag. Hotfix do CQ-4251852
* Atualize EditableActions com base na realocação columnClassNames. Hotfix do CQ-4250781
* Exponha os caminhos de recurso e modelo usando uma única propriedade e atributo. Hotfix do CQ-4251255
* Reverter as alterações de quebra da API export.json. Hotfix do CQ-4251854
* (SPA editável) Candidato à versão para 1.0.0. Hotfix para CQ-4251991
* A barra de ferramentas Editar é desativada para outros componentes ao editar qualquer componente. Hotfix do CQ-4253270

**Integração**

* Os campos Biblioteca e URL de download devem ser editáveis. NPR-24804: Hotfix do CQ-4246864
* Problema com várias configurações de DTM. NPR-24685: Hotfix do CQ-4247293
* Adicionado suporte para implantação assíncrona para bibliotecas de clientes hospedados. NPR-25716: Hotfix do CQ-4245745
* O componente direcionado com a oferta correspondente ausente renderiza a página inteira e, em vez de um componente direcionado vazio, outra representação completa da página é adicionada. NPR-25273: Hotfix do CQ-4248003
* O mecanismo do Target (mbox.js, at.js) não usa URLs danificados e usa URLs que contêm dois pontos, que podem falhar em determinadas implantações. NPR-25339: Hotfix do CQ-4237854
* (Iniciar)LibraryDownloadProcess armazena o valor de libraryUri errado. NPR-25330: Hotfix do CQ-4250006

**Plataforma**

* Ciclo de reindexação | NPE ao executar BinaryTextExtraction durante a atualização no local de 6.3 para 6.4. Hotfix para Granite - 21677
* Substituição transfronteiras do caminho marcado interno /libs/cq/cloudserviceconfigs/models/configpage/jcr:content - Problema ao executar o detector de padrões. NPR-25036: Hotfix do CQ-4248597
* Entradas de registro não gravadas devido ao NPE no LogEntryImpl. NPR-25627: Hotfix do Granite-22383
* A replicação do evento delete não verifica se há direitos. NPR-25679: Hotfix do CQ-4241234
* Adição do suporte STARTTLS no &quot;Day CQ Mail Service&quot;. NPR-25611: Hotfix do CQ-4249924
* Suporte pró-ativo para correções granite.platform.login para melhorar a acessibilidade. NPR-25176: Hotfix para Granite 21746 e Granite-21309
* (AEM 6.4) Erro ao recriar o pacote e reinstalá-lo. NPR-25173: Hotfix do CQ-4247939
* Remoção do padrão MERGE_PRESERVE aclHandling. NPR-24593: Hotfix do Granite-21889
* Content-Type não é proposto e está ausente na resposta após aplicar ContentDispositionFilter duas vezes. NPR-24175: Hotfix do Sling-7525
* O status do Gerenciador de pacotes está incorreto após a atualização para a ramificação AEM 6.4. NPR-24551: Hotfix do Granite-21750
* Instância do AMS - análise de registros de erros. Hotfix do CQ-4249567

**Segurança**

* O SAML redireciona o logon para a página de logout usando o Okta IDP. NPR-25523: Hotfix do GRANITE-22364
* A autenticação IMS por meio das configurações OAuth do provedor OAuth IDE externo OAK desativa o usuário criado no AEM. NPR-25301: Hotfix do Granite-22363

**MAC - Integração do Test&amp;Target**

* (Definição de metas) Erro do componente de texto durante a definição de metas. Hotfix do CQ-4233343

**Comunidades**

* (Biblioteca de arquivos) Baixar ativos com espaços em branco resulta em problemas de formato. NPR-24260: Hotfix do CQ-4245159
* Correções de vários problemas do Adobe Social. NPR-24247: Hotfix do CQ-4245054, CQ-4245120, CQ-4245296
* A rolagem infinita para o console de membros e grupos falha caso a publicação do autor seja executada em caminhos de contexto diferentes. NPR-24437: Hotfix do CQ-4246013
* A postagem não retorna ao estado não atendido mesmo ao remover do estado respondido e a pontuação não diminui. NPR-24419: Hotfix do CQ-4245797, CQ-4245932
* Eventos adicionados usando a funcionalidade de calendário em comunidades gera valores errados. NPR-24883: Hotfix do CQ-4244056
* (Fórum das comunidades) Problemas com o comportamento de clique na paginação e carregamento da página. NPR-24880: Hotfix do CQ-4246109
* (Chrome) As conversões de fuso horário falham nos eventos das comunidades. NPR-24881: Hotfix do CQ-4247115
* Não é possível renderizar o objeto incorporado no Email. NPR-24999: Hotfix do CQ-4248022
* A sequência de automoção deve ser executada na atualização do UGC, além da criação do UGC. NPR-25892: Hotfix do CQ-4251399
* Resposta da caixa de diálogo modal em Grupos. NPR-25623: Hotfix do CQ-4248805
* A exceção Solr é lançada na exclusão de conteúdo. NPR-25869: Hotfix do CQ-4248908
* Os links paginados para threads com muitas postagens não funcionam em Notificações. NPR-25678: Hotfix do CQ-4243038
* Os valores de tempo no resultado da pesquisa exibem a hora do servidor em vez do fuso horário do cliente. NPR-25594: Hotfix do CQ-4248986
* (Comentários do fórum) O botão Voltar do navegador não está funcionando como esperado. NPR-25205: Hotfix do CQ-4248573
* (Resultados da pesquisa) O botão Voltar do navegador não está funcionando como esperado. NPR-25214: Hotfix do CQ-4248574
* Nulo é retornado ao sobrepor o componente communitygroupmemberlist. NPR-25228: Hotfix do CQ-4248523
* (Calendário de comunidades) ClassCastException é gerado ao salvar o evento com a nova imagem de Capa. NPR-25167: Hotfix do CQ-4248662
* (Comunidades) Mensagens sendo truncadas. NPR-25326
* (AEM Publish) O Recurso de Pontuação falha com o caminho de contexto e mostra a tela em branco. NPR-26155: Hotfix do CQ-4251942
* (MSRP) O calendário recém-criado é salvo, lançando parcialmente o NPE no registro de erros. NPR-26071: Hotfix do CQ-4250531
* A paginação do fórum/tópico só é atualizada quando a página é atualizada. NPR-26070, NPR-25965: Hotfix do CQ-4249509
* (Fórum de P&amp;R) Não é possível navegar até a página anterior ao abrir um link direto para um comentário. NPR-26069: Hotfix do CQ-4251699
* Carregar imagem no grupo Criar não funciona em dispositivos móveis. NPR-26172: Hotfix do CQ-4251703
* (Mensagens) Ao usar o DSRP, o nome do receptor de mensagem é sempre exibido como &quot;Desconhecido&quot;. NPR-26056: Hotfix do CQ-4251397
* O rótulo de status de conclusão do recurso de ativação do Scorm aparece vazio na interface do usuário. NPR-26034: Hotfix do CQ-4249994
* Ao criar um novo grupo da comunidade, um grupo da comunidade do duplicado é criado em um cluster mongoMK ativo/ativo. NPR-26032: Hotfix do CQ-4245884
* (Autor) O assistente de criação de grupo demora muito para carregar/criar um grupo no assistente. NPR-26031: Hotfix do CQ-4244966
* Parsys desaparece ao adicionar uma declaração include no script hbs. NPR-25908: Hotfix do CQ-4250489
* Ao habilitar &quot;Permitir privilegiados&quot;, os membros com privilégios só devem poder compor para usuários que sejam membros da comunidade. NPR-25877: Hotfix do CQ-4248450
* Deeplinks bloqueados para ativação. NPR-25966: Hotfix do CQ-4251478
* A paginação do fórum não é atualizada dinamicamente na remoção de respostas. NPR-25970: Hotfix do CQ-4248975, CQ-4252843
* A Rolagem automática e o realce não funcionam em eventos de calendário e de filelib no caso de comentários aninhados. NPR-25958: Hotfix do CQ-4251471
* (DSRP) Desempenho de Direct/Deep Link degradando com grandes quantidades de Conteúdo gerado pelo usuário. NPR-25957: Hotfix do CQ-4251470
* Não é possível modificar as propriedades de Permitir Membros Privilegiados e Membros Privilegiados. NPR-26014: Hotfix do CQ-4244592
* Marcar todos como lidos redefine os contadores de notificação para todas as páginas da comunidade. NPR-25931: Hotfix do CQ-4248612
* Edite falhas de TI para DSRP. NPR-25929: Hotfix do CQ-4251382
* As TIs de e-mail falham devido ao NPE ao criar modelos de e-mail. NPR-26039: Hotfix do CQ-4250962
* Problemas de encadeamento do fórum ao incorporar imagens com resolução muito alta. NPR-26037: Hotfix do CQ-4244453, CQ-4253099
* A hora exibe opções quando o fuso horário do servidor é diferente do fuso horário do usuário. NPR-26036: Hotfix do CQ-4248751
* Anexar um arquivo duas vezes com o mesmo nome a uma publicação do fórum resulta em erro de servidor. NPR-24172: Hotfix do CQ-4244367
* Correções de desempenho de backport - agrupe a paginação no autor e na publicação, Pesquisa em grupo no autor, Evitando a serialização das respostas para o journal, calendário e ideação e carregamento lento para obter o botão de associação ao grupo (convidar/desconvidar) para cada grupo enquanto exibe a página de listagem do grupo. NPR-24538: Hotfix do CQ-4246515
* Os Recursos de ativação não estão visíveis no autor. Hotfix do CQ-4252618
* As notificações não são geradas para thread a partir do usuário desconhecido. Hotfix do CQ-4245132
* A pesquisa em grupo não é exibida no painel esquerdo. Hotfix do CQ-4252621
* (Autor) A paginação não está funcionando para o Console de grupos. Hotfix do CQ-4242786
* Atualização da interface do usuário do jQuery. Hotfix do CQ-4248894
* Atualize para a versão mais recente do SCORM 2017.1. NPR-25675: Hotfix do CQ-4240671
* Os campos &quot;Compor em nome&quot; estão visíveis para usuários não comunitários. NPR-25331: Hotfix do CQ-4247858
* A postagem ainda está visível na interface do usuário mesmo após a exclusão e apresenta erro no console. NPR-26290: Hotfix do CQ-4252803
* (Configurações do site) Não é possível salvar as alterações feitas em Funções. NPR-26274: Hotfix do CQ-4252187
* (Vulnerabilidade de segurança) Tomada de conta devido à configuração incorreta do token JSON Web. NPR-26458: Hotfix do CQ-4253314
* A paginação não é redefinida após a remoção das respostas. NPR-26326: Hotfix do CQ-4252997
* A imagem de anexo não é exibida em Rascunhos durante a edição. Hotfix do CQ-4253360
* A página não está atualizando ao anexar anexo no banco de dados relacional (DSRP). Hotfix do CQ-4253084
* Os grupos não estão funcionando dentro do recurso Ativar site. Hotfix do CQ-4252975
* Os Pré-requisitos dos Caminhos de aprendizado não são persistentes em Ativação. Hotfix do CQ-4252948

**Fluxo de trabalho**

* A interface do usuário do iniciador de fluxo de trabalho não exibe configurações anteriores a 41 iniciadores e aciona um erro de javascript no console. NPR-25028: Hotfix do CQ-4247604
* Editar um fluxo de trabalho legado sem editar seu iniciador faz com que vários workflows sejam criados em qualquer fluxo de trabalho que contenha uma etapa Ativar página/ativo. NPR-25870: Hotfix do CQ-4250896
* Link incorreto na carga do fluxo de trabalho se a página tiver um nó de metadados. NPR-25916: Hotfix do CQ-4250733

**Tradução**

* Correção de que importar projeto traduzido faz duas solicitações POST simultâneas, causando, portanto, erro. NPR-24889: Hotfix do CQ-4247638
* Correção de que ao criar um projeto de tradução para vários idiomas, todas as páginas do mesmo idioma são adicionadas ao mesmo trabalho. NPR-25091: Hotfix do CQ-4246112
* Correção de que, em alguns casos, o trabalho de tradução só lista as 40 páginas principais. NPR-25974: Hotfix do CQ-4248661
* O componente DataPicker (Coral2) não muda o ano. NPR-24466: Hotfix do Granite-21893

**IU - Foundation**

* Backports proativos da interface do usuário do Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-259 35, NPR-25976
* (Importador de design) Importar uma página não importa o js,css. NPR-25203: Hotfix do Granite-22236
* Backports da interface do usuário do Proactive Foundation para melhorar a estabilidade do produto. NPR-24334

**MAC - Integração do Test&amp;Target**

* A segunda página do Assistente de personalização ( iniciado pela &quot;Definição de metas do Start&quot; ) está em branco e lança erros no console. Hotfix do CQ-4253277

**Fragmentos de experiência**

* Integração de fragmentos de experiência/Público alvo mesclados com o AEM 6.4.2.0. Hotfix para CQ-4248653

**Gerenciamento de fragmentos de conteúdo**

* Anotações de Fragmentos de conteúdo e comparação lado a lado de versões de Fragmentos de conteúdo. Hotfix do CQ-4247148

**DAM - Geral**

* O filtro &quot;Check-out por&quot; não está funcionando corretamente na pesquisa. Hotfix do CQ-4247070
* Ao executar o fluxo de trabalho de atualização de ativos, a cópia do idioma do ativo e sua miniatura fica em branco. Hotfix do CQ-4250641
* ID do Duplicado: o valor do atributo id deve ser exclusivo. Hotfix do CQ-4250905
* Rótulo: Os elementos de formulário devem ter rótulos. Hotfix do CQ-4250906
* Nome do link: Os links devem ter um texto perceptível. Hotfix do CQ-4250907
* Migração de Modelo de Metadados de Pasta de Portas JMX e ServiceUserMapping. Hotfix do CQ-4252947
* WebdriverIO Testes não executados na ramificação release/640 do CQ/dam. Hotfix do CQ-4252749
* Os links para ativos movidos não são refatorizados se o link for publicado. Hotfix do CQ-4245756

**DAM - Visualizadores**

* Erro intermitente ao carregar vídeo com os novos visualizadores 5.10.1. Hotfix para CQ-4250562

**DAM Brand Portal**

* Falha ao cancelar a publicação da coleção do Brand Portal. Hotfix do CQ-4245990
* Não é possível cancelar a publicação de predefinições de imagens no Portal de marcas. Hotfix do CQ-4246140
* Os subativos de um arquivo pdf de várias páginas não são publicados quando um ativo é publicado. Hotfix do CQ-4245162

**DAM - DMClient**

* Ao publicar um ativo de vídeo no YouTube, as tags que resultam no YouTube incluem o caminho completo da tag. Hotfix do CQ-4245549
* (Atualizações de opção de não participação e não participação) Problema com o redirecionamento CSS do visualizador. Hotfix do CQ-4247854
* Não é possível criar/editar a predefinição do visualizador como não membro do grupo &#39;administradores&#39;. Hotfix do CQ-4247618
* (6.4.1.0) A adição de vários vídeos em vários parsys interrompe o player de vídeo. Hotfix do CQ-4248517
* Renomear e mover ativos dentro de um Conjunto de imagens torna a edição impossível. Hotfix do CQ-4248434
* Publicar vídeos grandes no YouTube emite mensagens de tempo limite. Hotfix do CQ-4237831
* (Visualização de Lista) A interface do usuário do Seletor de ativos/Seletor muda para todos os cinza e é desativada para o usuário. Hotfix do CQ-4237817
* (Zoom vertical) Falha ao carregar Css com um erro 404. Hotfix do CQ-4236508
* Tentar baixar um ativo com o caractere de porcentagem (%) no nome do ativo resulta em um arquivo vazio. Hotfix do CQ-4250558
* (Visualização da placa) Nenhum indicador de processamento é exibido ao usar Copiar e colar em um ativo de vídeo. Hotfix do CQ-4249037
* (Atualize de 6.3.2 para 6.4) As predefinições de imagem de pré-atualização são mostradas como &quot;Não publicado&quot; na página Representações, mas não fornecem o botão URL quando selecionadas. Hotfix do CQ-4240406
* Dívida Técnica/Melhorias Menores. Hotfix do CQ-4240648
* O Seletor de ativos (ou o Seletor de ativos) não mostra todos os ativos das pastas disponíveis. Hotfix do CQ-4218414
* A predefinição de imagem sem altura exibe imagens com tamanho incorreto. Hotfix do CQ-4246546
* (Ativos com várias páginas) A interface do usuário quebra ao clicar em anotações. Hotfix do CQ-4251434
* Ao atualizar da versão 6.3 para a 6.4 e posterior da predefinição do Analytics, uma nova predefinição de conjunto de relatórios e análises é criada, perdendo os dados mais antigos do relatórios do usuário. Hotfix do CQ-4244529
* (Assistente de gerenciamento de publicação) A Lista de ativos parece estar vazia ao tentar publicar ou cancelar a publicação. Hotfix do CQ-4251881
* Ao escolher Visualizadores depois de visualizar os membros definidos, os vídeos do AVS não são reproduzidos. Hotfix do CQ-4205308
* As predefinições de processamento de vídeo de pré-atualização não podem ter uma nova predefinição de codificação de vídeo adicionada nem editar as predefinições de codificação existentes. Hotfix do CQ-4240407
* As predefinições de imagens não são aplicadas a renderizações dinâmicas baixadas. Hotfix do CQ-4249862
* O botão selecionar tudo não funciona corretamente na página de listagem Predefinição do visualizador. Hotfix do CQ-4252462
* Perfis de vídeo: O botão Selecionar tudo não está funcionando. Hotfix do CQ-4253076, CQ-4251447
* Passagem de validação SP2 - Passagem de fumaça. Hotfix do CQ-4251639

**DAM - DMServices**

* Falha ao gerar representações do Dynamic Media para o arquivo EPS. Hotfix do CQ-4243688

**Granite**

* O erro de digitação em bundle SymbaticName leva ao conjunto de duplicados. Hotfix do Granite-22155
* CUGConfiguration pode não selecionar CugExclude. Hotfix do Granite-21109
* Reiniciar o Adobe Granite Workflow Core executa novamente as etapas do fluxo de trabalho a partir do meio, criando workflows desnecessários. NPR-25057: Hotfix do Granite-22218
* JcrResourceBundle não suporta corretamente vários nomes básicos. NPR-25245: Hotfix do Granite-22317
* Na instalação de pacotes de conteúdo, as ACLs são agrupadas por principal, portanto, quebrando o modelo de permissão. NPR-24583: Hotfix do Granite-21591
* Atualize Jetty para 9.4.11 para corrigir vulnerabilidades. NPR-25030: Hotfix do Granite-22120

**Forms**

Os principais destaques dos formulários do AEM 6.4.2.0 são:

* Adicionada uma nova propriedade para Filas a serem atualizadas sem atualizar o navegador.
* Foi adicionada a capacidade de o usuário usar o mesmo arquivo WSDL para vários serviços.
* O padrão de carimbo de data e hora não suportado foi removido da lista suspensa do datepicker.
* Adição de suporte para a criação de xfaf e pdf no OSGI.
* Adicionado suporte para usar o recurso [de relatórios de](https://helpx.adobe.com/experience-manager/6-4/forms/using/transaction-reports-overview.html) transação em implantações locais.
* Código adicionado para não exibir a var filho no editor de regras de condição.

**Pacote complementar do Forms**

**Relatórios de transação**

* Atualizar a configuração do Relatórios de transação com a importância da replicação reversa configurada em um servidor de publicação. NPR-26050: Hotfix do CQ-4246650
* Inicialização atrasada da Ordem de Produção de Liberação Periódica. NPR-25968: Hotfix do CQ-4245024
* Falha na Gravação da Transação com Exceção de Ponteiro Nulo. Hotfix do CQ-4247302

**Forms - Fluxo de trabalho**

* (Espaço de trabalho HTML) Quando um usuário reclama uma tarefa, a contagem de filas é atualizada para esse usuário específico, mas não para outros usuários, a menos que a página seja atualizada. Esse problema foi corrigido por uma nova propriedade. Para configurar essa nova propriedade para sua instância do AEM, consulte suas Configurações. NPR-24536: Hotfix do CQ-4233665
* Não é possível carregar um formulário grande no aplicativo AEM Forms em 6.4. NPR-24463: Hotfix para CQ-4245091
* Problema no aplicativo do Mobile Workspace ao tentar visualização da tarefa compartilhada. NPR-25177: Hotfix do CQ-4248733
* Comportamento de validação inconsistente entre Web e APK. NPR-25670: Hotfix do CQ-4248178
* Quando uma chamada para um serviço da Web é feita em um formulário HTML5 aberto no cliente, ela falha e uma mensagem de erro é retornada. NPR-26048: Hotfix do CQ-4244716
* Problema ao chamar o serviço em formulários AEM Aplicativo Windows 6.3. NPR-26468: Hotfix para CQ-4252341

**Formulários móveis**

* (Formset) Problema de validação de campo SSN e Mobile ao visualizá-lo. NPR-24458: Hotfix do CQ-4244983
* Os dados não são exibidos com o preenchimento prévio de campos de várias linhas na pré-visualização HTML. NPR-24549: Hotfix do CQ-4244212
* Os dados são perdidos quando o script é avaliado em um campo de várias linhas. NPR-25333, Hotfix para CQ-4249610

**Formulários - Gerenciamento interativo de comunicação e correspondência**

* A sincronização falha no IC com Modelo básico e Modelo de impressão IC de referência. NPR-24912
* (CCR) Os validadores não funcionam para campos/variáveis. Hotfix do CQ-4245047
* O ícone Objeto de modelo de dados desaparece intermitentemente na barra de ferramentas Edição de texto. Hotfix do CQ-4245122
* Os registros de exceção são exibidos na IC copiada se a IC original for excluída. Hotfix do CQ-4249378
* Na representação de letra, a condição não é avaliada como true mesmo quando os dados estão corretos. Hotfix do CQ-4245944
* Os componentes gerados automaticamente não são realçados ao selecionar na árvore de conteúdo. Hotfix do CQ-4246178
* Problemas ao abrir o editor de modelo de Canal da Web. Hotfix do CQ-4248182
* Não é possível alterar a ordem dos ativos adicionados à medida que as setas para cima/para baixo permanecem desativadas. Hotfix do CQ-4252042
* Não é possível atualizar as propriedades do módulo Condition. Hotfix do CQ-4247909
* O UX da caixa de diálogo &quot;Cancelar herança&quot; quando o usuário reorganiza um objeto no Canal da Web precisa ser melhorado. Hotfix do CQ-4241076
* Os dados na letra correspondente aos vínculos definidos no XDP não são preenchidos usando o URL da letra direta. Hotfix do CQ-4245833
* (Problema de cache) A sincronização do canal da Web não reflete as alterações feitas nos fragmentos de layout, no fragmento de texto do canal de impressão. Hotfix do CQ-4251460
* Não é possível atualizar as propriedades do fragmento de layout e do DD. Hotfix do CQ-4247830
* (CCR) O recarregamento de rascunho está falhando devido à análise XML. Hotfix do CQ-4250950
* (Editor IC) O botão &quot;Editar fragmento&quot; deve ser mais descoberto. Hotfix do CQ-4244694
* (XDP) Uma tela em branco é exibida ao adicionar um fragmento de layout no novo subformulário criado. Hotfix do CQ-4248810
* Falha no teste DocumentFragment-principal-DeployWithServerSideTests. Hotfix do CQ-4245496
* Variável de módulo de texto Instância duplicada no módulo Condição. Hotfix do CQ-4252128
* O URL de pré-visualização do PDF não mostra o relatórios de transação na publicação. Hotfix do CQ-4246158
* Problemas relacionados ao IC Sync com a sincronização do Canal de impressão com o Canal da Web. Hotfix do CQ-4251505
* Limpeza de código EXM: Remova LocalFunctionMapper. Hotfix do CQ-4243265
* Para corrigir o tipo de recurso TableHeader do componente de tabela webChannel do IC. Hotfix do CQ-4251821
* (Editor IC) Problemas de usabilidade. Hotfix do CQ-4241081
* O subformulário Imprimir canal não mostra a funcionalidade de inserção. Hotfix do CQ-4252994
* Falha na sincronização de manter alterações após a remoção do nó FDM ou do espaço reservado da variável. Hotfix do CQ-4253178
* (Editor de modelos) O modelo básico mostra o cabeçalho/rodapé de áreas de arrastar e soltar adicionais e a tela pisca ao abrir o Canal da Web. Hotfix do CQ-4253323
* Os componentes gerados automaticamente não são realçados ao selecionar na árvore de conteúdo. Hotfix do CQ-4246178

**Serviços de documentação**

* (Form Service) O OSGI não tem suporte para XFAF. NPR-25181, Hotfix para CQ-4251313
* Os caracteres no cabeçalho do arquivo PDF montado estão ficando ilegíveis. NPR-25113: Hotfix do CQ-4244682

**Formulários adaptáveis**

* Enviar ação como Enviar email lança uma exceção com campos CC/BC em branco. NPR-25019: Hotfix do CQ-4243039
* Não é possível usar o componente de formulário AEM OOTB devido ao query ineficiente. NPR-25065: Hotfix do CQ-4247256
* Remova sling:orderBefore dos nós de diálogo de guideImageChoiceComponent. Hotfix do CQ-4245013
* (Seletor de datas) O Padrão de edição não suporta dois tipos de padrão de carimbo de data e hora. Hotfix do CQ-4237982
* Enviar ação usando os problemas de criação do &#39;Fluxo de trabalho do Forms&#39; Classic. Hotfix do CQ-4236981
* (Canal da Web) O gráfico IC deve herdar a propriedade colspan do gráfico AF. Hotfix do CQ-4252143

**Integração de backend**

* (Solicitações SOAP) Grandes decimais (mais de 6 dígitos) são representados em notação exponencial, resultando em erro de validação. NPR-25283: Hotfix do CQ-4248100
* Validação incorreta de parâmetros opcionais definidos em tipos complexos. NPR-25070: Hotfix do CQ-4247107
* Foi adicionada a capacidade de o usuário usar o mesmo arquivo WSDL para vários serviços. NPR-24604, Hotfix para CQ-4247756
* O FDM embaralha a ordem dos parâmetros em suas chamadas SOAP. NPR-25069, Hotfix para CQ-4247180
* O FDM mescla entidades (em Lista/Matriz) na solicitação SOAP. NPR-25284: Hotfix do CQ-4248375

**Instalador do Forms JEE**

**Serviço PDFG**

* A função de criar/modificar configurações de segurança não funciona. NPR-24769: Hotfix do CQ-4246927
* Otimize PDFs ao desincorporar seletivamente fontes por meio de uma única chamada de API. NPR-23287

**Serviços de documentação**

* O Serviço de saída não fornece as tags corretas para o Reader de acessibilidade. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Correção para CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Segurança de documentos**

* Problema com a criação de Política usando o Documento Security. NPR-25586, NPR-25547: Hotfix do CQ-4247086

**Forms - Foundation JEE**

* Processos em execução como Conta de contexto do sistema intermitentemente. NPR-25289, NPR-25313: Hotfix do CQ-4249331
* AEM Forms JEE afetados pelo alerta de segurança de vínculo de dados Apache Struts e Jackson. NPR-25628: Hotfix do CQ-4242891
* O processo de ponto de start de email não funciona. NPR-25253: Hotfix do CQ-4248518

**Feature Packs incluídos**

**Assets**

* Adicionada [integração com o Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que os usuários possam pesquisar, pré-visualização, salvar e licenciar ativos do Adobe Stock diretamente da interface do usuário do AEM. Para obter informações mais detalhadas, consulte [Uso de ativos do Adobe Stock com ativos]AEM (https://helpx.adobe.com/experience-manager/kt/assets/using/stock-assets-feature-video-use.html). NPR-15779: Hotfix do CQ-30857
* Adicionado suporte para metaschema condicional dinâmico. For more information, see [Cascading Metadata](/help/assets/cascading-metadata.md). NPR-25189: Hotfix do CQ-4237413
* Opção &quot;Download de ativo&quot; ativada em Fragmentos de conteúdo. For more information, see [Asset Reports](/help/assets/asset-reports.md). NPR-25186: Hotfix do CQ-4237410
* Capacidade de definir um schema de metadados para pastas de ativos. Para obter mais informações, consulte Schema [Metadados da](/help/assets/folder-metadata-schema.md) pasta e consulte suas Configurações [](#configuration-settings-required-for-npr) de configuração após a instalação do AEM 6.4.2.0. NPR-21268: Hotfix do CQ-4221574

**Sites**

* Permitir a edição de um fragmento de conteúdo sem permissões de exclusão. Para obter mais informações, consulte [Personalização e extensão de fragmentos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/customizing-content-fragments.html#AssetPermissions)de conteúdo. NPR-25793: Hotfix do CQ-4248750
* Adição da capacidade de anotar Fragmentos de conteúdo. For more information, see [Variations-Authoring Fragments](https://helpx.adobe.com/experience-manager/6-4/assets/using/content-fragments-variations.html#AnnotatingaContentFragment). NPR-25188: Hotfix do CQ-4235336
* Controle de versão: Comparar fragmentos de conteúdo lado a lado. Para obter mais informações, consulte [Gerenciamento de fragmentos](https://helpx.adobe.com/experience-manager/6-4/assets/using/content-fragments-managing.html#ComparingFragmentVersions)de conteúdo. NPR-25187: Hotfix do CQ-4237412
* Aprimoramentos do editor de imagens suportados para o AEM 6.4.2.0. Para obter mais informações, consulte Editor [de](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/image-editor.html)imagens. NPR-24467

**Pacotes de conteúdo e pacotes OSGI incluídos**

Lista de pacotes OSGi incluídos no AEM 6.4.2.0

[Obter arquivo](assets/6.4.2.0_bundle-list.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.2.0

[Obter arquivo](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

O AEM 6.4.1.0 é uma atualização importante que inclui correções e melhorias de desempenho, estabilidade, segurança e essenciais para o cliente lançadas desde a disponibilização geral do AEM 6.4 em abril de 2018.

O AEM 6.4.1.0 pode ser instalado no AEM 6.4 GA. Alguns dos principais destaques do service pack são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.3.
* Tags inteligentes aprimoradas.
* Correções no Seletor de design, no Seletor de tags (altere a VM de origem e a VM de público alvo para auto.)
* Adicionado suporte para typeHint para salvar valores como string.
* Adicionado suporte para SMTP sobre TLS no Serviço de e-mail.
* Correção de tratamento de proxy para encaminhador HTTP no DMS7.
* Atualize para /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js versão 1.3.
* Correções nos pacotes de opção de não participação e não participação do DMHybrid.
* Correções no Smart Crop.
* Valores de configuração OTB migrados para o novo local (de /etc para /conf).
* Adicionados perfis coloridos às configurações do cliente nos servidores do delivery.
* Migração das configurações do Servidor de imagens de /etc —&amp;gt; /conf.
* Fragmento de conteúdo de origem adicionado para tradução.
* Adicionado o suporte ARIA para Print e PrintDialog.
* Adição do suporte ARIA para validação de email.
* Backport pró-ativo para correções platform.clientlibs.
* Prevenção da execução automática de scripts quando não há entrada para o dataType explícito (resolve CVE-2015-9251).

**Assets**

* O valor suspenso em cascata mostra em branco ao reabrir a página de propriedades do ativo. NPR-23042: Hotfix do CQ-4238761
* Links compartilhados na página mylinkshare e links para a página não estão disponíveis para o usuário não administrador NPR-23044: Hotfix para CQ-4239004
* Para evitar uma exceção de ponteiro nulo no fluxo de trabalho de atualização de ativos DAM na versão 6.4.0. NPR-24134: Hotfix para CQ-4244972
* A página WCM publicada mostra ícones de espaço reservado para hotspot, arquivos CSS ausentes com erro 403 para visualizadores OOTB. NPR-23041: Hotfix do CQ-4233716
* (Visualização de detalhes) O recurso Navegação próxima/traseira deixa uma sobreposição DIV na área de pré-visualização de representação dinâmica bloqueando o acesso ao visualizador. NPR-23043: Hotfix do CQ-4238499
* A representação de imagem CMYK tem saturação incorreta. NPR-23048: Hotfix do CQ-4235470
* A extração de metadados XMP por Scene7ListInfoProvider consome muitos recursos. NPR-23754
* (delivery de barragem) O encaminhador Http não respeita as configurações de proxy HTTP. NPR-24002: Hotfix do CQ-4244140

**Sites**

* Quando renomeamos a página enquanto movemos, a movimentação da página é bem-sucedida, mas a funcionalidade de renomeação não funciona. NPR-22923: Hotfix do CQ-4235907
* Erro ao publicar uma página de Live Copy que aponta para uma página do Importador no Adobe Campaign. NPR-23053: Hotfix do CQ-4237164
* Falha ao mover/renomear na interface clássica com o erro &quot;Ocorreu um erro ao mover a página&quot; e não foi renomeado. NPR-23051: Hotfix do CQ-4235907
* Alternar o conteúdo de visualização de coluna para visualização de lista renderiza uma página em branco e aciona uma Exceção de ponteiro nulo para páginas com OffTime definido e OnTime como em branco. NPR-22968, NPR-23052: Hotfix do CQ-4238940

**Comércio**

* Corrigir o teste principal de hobbes com falha (CQ/Commerce Module). Hotfix do CQ-4253494

**Vulnerabilidade**

* A integração do Salesforce está vulnerável à Falsificação de solicitação do lado do servidor (SSRF). NPR-24289: Hotfix do CQ-4245277
* SSRF (Server Side Request Forgery) e XSS (Cross-Site Scripting) em ReportingServicesProxyServlet. NPR-24657: Hotfix do CQ-4246880
* Scripts entre sites (XSS): Refletido na criação comercialwizard.html/content. NPR-24642: Hotfix do CQ-4237017
* Scripts entre sites (XSS) nos links de Projeto da interface do usuário do administrador. NPR-23272: Hotfix do CQ-4241795

**WCM - Componentes do Foundation**

* Abrir o seletor de Design resulta em uma exceção de ponteiro nulo. NPR-23047: Hotfix do CQ-4238736

**Interface do usuário**

* (Coral3 Datepicker) Adicione suporte para typeHint para salvar valores como &quot;String&quot;. NPR-23398: Hotfix do Granite-21194
* A tradução para internacionalização não funciona no nível da língua. NPR-22967, NPR-23046: Hotfix para Granite-21111
* Backport pró-ativo para correções granite.ui.commons. NPR-23537
* Backport Pró-ativo para granite.ui.coções do Intent. NPR-23535
* Backport pró-ativo para correções granite.ui.coralui. NPR-23538
* Não é possível remover vários usuários do grupo ao mesmo tempo. NPR-23846
* (OMEGA) Reportar &quot;Recurso&quot; somente em inglês. NPR-23989: Hotfix do Granite-21231
* (Importador de design) Importar uma página não importa o js, css. NPR-25203: Hotfix do Granite-22236

**Integração**

* ResourceResolver não bloqueado em com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix do CQ-4236515
* O TargetContentImpl deixa o AEM lento durante consultas de longa duração. NPR-22359: Hotfix do CQ-4236907
* O mecanismo do Target (mbox.js, at.js) não usa URLs danificados e usa URLs que contêm dois pontos, que podem falhar em determinadas implantações. NPR-22434: Hotfix do CQ-4237854
* No modo Target, os autores podem modificar um componente herdado do blueprint sem cancelar a herança. NPR-22865: Hotfix do CQ-4237907
* (Personalização) Os ícones são deformados ao alternar para a visualização da placa. NPR-23373, NPR-23374: Hotfix do CQ-4240018, CQ-4240019
* (Personalização) O console de Audiência não mostra os tipos nt:folder. NPR-23375: Hotfix do CQ-4242293
* Quando um componente é direcionado para a instância de publicação, a oscilação é exibida mostrando a experiência padrão antes da experiência direcionada. NPR-23415: Hotfix do CQ-4242038
* (Console do Adobe IMS) A configuração do serviço AccessTokenProvider OSGi é exibida novamente após a exclusão. NPR-23520: Hotfix do CQ-4208250
* A replicação de referência de configuração falha com a estrutura de pasta intermediária. NPR-23485: Hotfix do CQ-4242751
* (Personalização) clientlib bloqueado pelo servlet proxy. NPR-23521: Hotfix do CQ-4240995
* (Console do Adobe IMS) As soluções da nuvem registrada não são coletadas no assistente de configuração. NPR-23977: Hotfix do CQ-4244549
* Loop infinito ao carregar conteúdo direcionado em páginas sem uma extensão HTML. NPR-23522: Hotfix do CQ-4223600
* Falha na Ativação de uma página com referências de configuração herdadas do Gerenciamento dinâmico de tags. NPR-23485: Hotfix do CQ-4242751

**Plataforma**

* (Interface clássica)(Interface de usuário de toque) O seletor de tags não é exibido e lança uma exceção ao tentar procurar tags por um predicado de tags no schema de Pesquisa de ativos. NPR-23049: Hotfix do CQ-4239371
* (Interface clássica) Os componentes que usam xtype=tags retornam nulo e não podem ser selecionados da lista de tags eth. NPR-23050: Hotfix do CQ-4239937
* (Marca) A caixa de diálogo Aceitar menciona o Adobe Marketing Cloud em vez da Adobe Experience Cloud. NPR-23210: Hotfix do CQ-4237799
* A opção Filtro torna o AEM lento após a atualização da versão 6.3 para a 6.4. NPR-23260: Hotfix para CQ-4239847 (a ser verificado)
* Backport pró-ativo para correções granite.omnisearch.core. NPR-23536
* Backport pró-ativo para correções platform.clientlibs. NPR-23569
* Herança de configuração de Cloud Service quebrada ao editar outras propriedades da página. NPR-23216: Hotfix do CQ-4239782
* Habilitado o suporte STARTTLS no serviço Day CQ Mail. NPR-23941: Hotfix do CQ-4240397

**Projetos**

* (Fragmento do conteúdo) A cópia do idioma para o ativo incorporado não é criada enquanto o ativo em inglês é adicionado à tradução. Hotfix do CQ-4243477
* A lista suspensa de configuração msft mostra a configuração de /libs(6.4 configs) em vez de /etc(6.3 configs) no modo herdado. Hotfix do CQ-4243475
* Promover e excluir automaticamente inicializações de tradução em projetos de tradução. Hotfix do CQ-4243474
* O fragmento de conteúdo dentro de sites não está sendo traduzido. Hotfix do CQ-4243482, CQ-4243483, CQ-4245687
* Erro do servidor ao abrir o filtro de pesquisa de trabalho de tradução. Hotfix do CQ-4236813
* A lista suspensa de configuração de credenciais fica em branco mesmo depois que tif está presente em /conf/we-retail. Hotfix do CQ-4236315
* Abrir KPI do Projeto: degradação do desempenho à medida que mais projetos são criados. NPR-23840: Hotfix do CQ-4238392
* O Workflow Starter não pode aceitar o valor TypeHint de String. NPR-23863: Hotfix do CQ-4238356

**Comunidades**

* Vulnerabilidades de segurança na versão 1.0 do Handlebars. NPR-23636: Hotfix do CQ-4243055
* A permissão em massa de mensagens sinalizadas não está funcionando. NPR-23867: Hotfix do CQ-4243962
* O valor padrão não é exibido no botão de classificação no componente do fórum. NPR-23882: Hotfix do CQ-4243375
* Problemas com o delivery de mensagens de sites da comunidade para grupos. NPR-23935

**Fluxo de trabalho**

* O Serviço de Notificação por E-mail do Fluxo de Trabalho do Day CQ aciona um e-mail por nó Mongo para notificações WorkflowCompleted e WorkflowAborted. NPR-22515: Hotfix do CQ-4238172
* A execução do fluxo de trabalho de ativos de atualização do DAM lança uma NullPointerException. NPR-23010: Hotfix do Granite-21096
* A etapa Processo de fluxo de trabalho não exibe scripts de /etc/workflow/scripts. NPR-23263: Hotfix do Granite-20775
* A Etapa dinâmica do participante do fluxo de trabalho não exibe scripts de /apps/workflow/scripts. NPR-23464: Hotfix do Granite-21276
* Não é possível editar qualquer fluxo de trabalho depois de editá-lo uma vez. NPR-23742: Hotfix do CQ-4238526
* (Interface clássica) Ao editar os iniciadores do fluxo de trabalho, as condições desaparecem, fazendo com que os workflows sejam iniciados sem condições. NPR-23835: Hotfix do CQ-4239153
* Caixa de entrada do projeto: a alternância para a visualização do calendário mostra o conteúdo principal da caixa de entrada. NPR-23947: Hotfix do CQ-4241236
* É necessário expor os detalhes da carga no pacote para que o componente HTL possa exibir o valor na visualização da lista. NPR-23948: Hotfix do CQ-4240953
* Não é possível armazenar dados de diálogo na etapa Participante da caixa de diálogo. NPR-23965: Hotfix do CQ-4234123
* (Interface do usuário para toque) Ao salvar um modelo de fluxo de trabalho, o botão &quot;Sincronizar&quot; muda para &quot;Sincronizado&quot;, resultando em erro ortográfico. Hotfix do CQ-4244843
* Caixa de entrada do projeto: a alternância para a visualização do calendário mostra o conteúdo principal da caixa de entrada. Hotfix do CQ-4244436
* Não é possível selecionar Diálogos na etapa Participante da caixa de diálogo. Hotfix do CQ-4244532
* Backport pró-ativo para correções granite.omnisearch.core. NPR-23536
* Problema no aplicativo Mobile Workspace 6.4 com Tarefa compartilhada. NPR-26383

**WCM - Tradução**

* (Painel de referência) As tarefas de tradução não estão sendo executadas durante a criação do projeto. Hotfix do CQ-4245327

**WCM - MSM**

* (MSM) Melhoria no desempenho da implantação. Hotfix do CQ-4231488
* (MSM) Intervalo de tempo na Escuta de Eventos entre o evento que está realmente acontecendo e a manipulação de eventos. Hotfix do CQ-4227766

**Telas**

* A página de tela falha com o erro devido a dependências ausentes para screens-core-pkg:1.4.42. Hotfix para CQ-4245918

**Projetos - Tradução**

* (Fragmento do conteúdo) A cópia do idioma para o ativo incorporado não é criada enquanto o ativo em inglês é adicionado à tradução. Hotfix do CQ-4243477
* A lista suspensa de configuração msft mostra a configuração de /libs(6.4 configs) em vez de /etc(6.3 configs) no modo herdado. Hotfix do CQ-4243475
* Promover e excluir automaticamente inicializações de tradução em projetos de tradução. Hotfix do CQ-4243474
* O fragmento de conteúdo dentro de sites não está sendo traduzido. Hotfix do CQ-4243482, CQ-4243483, CQ-4245687
* Erro do servidor ao abrir o filtro de pesquisa de trabalho de tradução. Hotfix do CQ-4236813
* A lista suspensa de configuração de credenciais fica em branco mesmo depois que tif está presente em /conf/we-retail. Hotfix do CQ-4236315

**Gerenciamento de fragmentos de conteúdo**

* A exclusão do componente preenche os logs com rastreamentos de pilha. Hotfix do CQ-4242315

**DAM - Geral**

* Fechar a visualização detalhada de um ativo retorna à página de resultados de pesquisa incorreta. Hotfix do CQ-4240960
* (Camera Raw) A opção de ajuste de imagem está ausente. Hotfix do CQ-4246121
* IndexOutOfBoundsException: Relatório de Modificação de Ativo OOTB. Hotfix do CQ-4239744
* Remova a pontuação de confiança do relatório csv. Hotfix do CQ-4241491
* delivery de e-mail de compartilhamento de link quebrado para remetente que não seja &quot;administrador&quot;. Hotfix do CQ-4240357
* Correção de falhas de TI. Hotfix do CQ-4249891

**DAM - Portal da marca**

* As propriedades do ativo listas somente 3 propriedades na primeira guia, e todas as guias ficam vazias. Hotfix do CQ-4242503
* Os predicados de tipo de arquivo e tamanho de arquivo não estão disponíveis no formulário de pesquisa publicado. Hotfix do CQ-4242026
* A pesquisa no predicado de diretório deve ser filtrada/não exibida nos filtros de pesquisa. Hotfix do CQ-4241386
* A pesquisa padrão de deve existir após a despublicação. Hotfix do CQ-4241383, CQ-4241113
* O gesto Publicar no portal da marca não funciona para predefinições de imagens. Hotfix do CQ-4241074
* Publicar no Brand Portal não está funcionando para coleções. Hotfix do CQ-4241122, CQ-4246558

**DAM - Cliente DM**

* Atualizar para 6.4 remove perfis de codificação de vídeo criados anteriormente. Hotfix do CQ-4244067
* O atributo Texto alternativo está quebrado no componente Dynamic Media. Hotfix do CQ-4244081
* (DMS7) A edição de conjuntos remotos no AEM não é substituída no Scene7. Hotfix do CQ-4243430
* Verificação da versão 6.4 SP1 baseada no DM Hybrid. Hotfix do CQ-4244623
* (DMS7-UA) Ao clicar no botão Incorporar para um ativo de vídeo publicado, nada parece acontecer. Espera-se que a caixa de diálogo Incorporar seja exibida com o código HTML. Hotfix do CQ-4245237
* (DM Hybrid) A URL de cópia para ativos de vídeo publicados ou conjuntos de mídia mista obtém &quot;[objeto[de]objeto&quot; na caixa de diálogo URL. Hotfix do CQ-4245236, CQ-4245451
* (DMHybrid) A página de Visualização Detalhes do vídeo não contém a pré-visualização da exibição Ativo de vídeo e gera uma mensagem de erro no console. Hotfix do CQ-4244320
* Codificação automática S7 do conteúdo we.retail. Hotfix do CQ-4242253
* As predefinições de processamento de vídeo de pré-atualização não podem ter uma nova predefinição de codificação de vídeo adicionada nem editar as predefinições de codificação existentes. Hotfix do CQ-4240407
* As predefinições de imagem de pré-atualização são mostradas como Não publicadas na página Representações e não produzem URL. Hotfix do CQ-4240406
* (CSS) Os ativos são exibidos, mas os visualizadores usados são padrão e não os visualizadores OOTB. Hotfix do CQ-4239839
* Desativada a etapa de limpeza desativa a execução manual e usada de classes de corais particulares. Hotfix do CQ-4239729
* O visualizador de imagens está gerando um erro e falha ao exibir o recorte inteligente correto. Hotfix do CQ-4237564
* A predefinição legada em /etc parece estar quebrada e não migrada para o local em /conf ao salvar. Hotfix do CQ-4237416
* Regressão no OOB VideoViewer 5.8.x - o visualizador expande o iframe para a direita, quebrando o layout da página. Hotfix do CQ-4235465
* (DMS7) O URL de execução de Recorte inteligente e os botões Incorporar estão ativos para imagens que não foram publicadas. Hotfix do CQ-4233696
* (DMHybrid) Restaure o recurso de recorte/rotação anterior. Hotfix do CQ-4239489
* Ao visualizar um vídeo na visualização do cartão, o botão Reproduzir não alterna para pausar. Hotfix do CQ-4238592
* Ao executar uma atualização de aceitação, a configuração do YouTube não é movida/copiada de seu antigo local para o novo local. Hotfix do CQ-4238590
* DropDois Perfis OOTB AVS Video Processing são listados em Propriedades da pasta e apenas um contém codificações definidas. Hotfix do CQ-4238096
* (DMS7) Recorte inteligente: Visualização de detalhes: O botão URL é identificado como botão Copiar para renderizações. Hotfix do CQ-4237804
* A página de listagem Predefinição do visualizador permanece em branco mesmo após a execução dos comandos de ondulação. Hotfix do CQ-4243246
* Desativada a etapa de limpeza desativa a execução manual e o uso de classes de corais particulares. Hotfix do CQ-4239729
* A página Detalhes do relatório de vídeo não mostra o ativo de vídeo. Hotfix do CQ-4246208

**DAM - DMServices**

* (DMS7) Configuração da nuvem: Não é possível sincronizar o novo conteúdo com o Scene7 após a atualização para o SP1. Hotfix do CQ-4244437
* (DMHybrid) perfis coloridos e configurações de catálogo não estão se registrando em uma chamada debug_info=Catalog. Hotfix do CQ-4242346
* Adicione perfis coloridos às configurações do cliente nos servidores do delivery. Hotfix do CQ-4241818, CQ-4241819
* (DMHybrid) Após 6,3 &amp;gt; 6.4 atualização, as configurações de catálogo são movidas para o nó incorreto. Hotfix do CQ-4239974, CQ-4239975
* O script pushviewerpresets (DMHybrid) não cria os nós necessários para modificar as configurações do catálogo. Hotfix do CQ-4240076
* Ao usar a seleção suspensa &quot;Formato&quot; e selecionar formatos PNG ou JPG, o arquivo baixado é exibido como supersaturado e mais escuro que o ativo original. Hotfix do CQ-4240073
* (DMS7) Remova o mapeamento de Tipo MIME: image_x-eps. Hotfix do CQ-4240394
* (DMS7) Os parâmetros de carregamento para o plano de fundo de separação não passam no ipsApiService.log e, portanto, não funcionam. Hotfix do CQ-4240686
* A atualização de Perfis de processamento de imagem criados em uma instância 6.3 a 6.4 divide a propriedade &quot;Tipo de corte&quot;. Hotfix do CQ-4237739
* (Dynamic Media) Falha no carregamento regular de ativos fora da pasta smartcut. Hotfix do CQ-4237670
* Ajuste o código de fallback do perfil para o nome do perfil &quot;Codificação de vídeo adaptável&quot; para &quot;Adaptive_Video_Encoding&quot;. Hotfix do CQ-4237666
* Os dados EmbedXMP são sempre definidos como &quot;ativos&quot; para o processo de geração de Ptiff. Hotfix do CQ-4234498
* A representação de imagem CMYK tem saturação incorreta. Hotfix do CQ-4235470
* As configurações do Servidor de imagens não são replicadas para o delivery enquanto os logs de replicação as marcam com êxito. Hotfix do CQ-4239480, CQ-4239046
* (DMS7) Não é possível criar conjuntos usando referências antigas/novas à Configuração da nuvem. Hotfix do CQ-4238078
* A etapa do fluxo de trabalho do Scene7 só lê Scene7 no nome e na descrição, mas não esclarece a etapa do fluxo de trabalho no fluxo de trabalho de Atualização do DAM. Hotfix do CQ-4237865

**DAM - Tags inteligentes**

* Tags inteligentes aprimoradas. NPR-21951

**Forms**

As correções do AEM Forms são entregues por meio de pacotes complementares e outros instaladores de patches fornecidos com a versão. Para obter detalhes, consulte Versões do AEM Forms.

Os principais destaques do AEM Forms são:

* O AEM Forms apresenta o recurso [de relatórios de](https://helpx.adobe.com/experience-manager/6-4/forms/using/transaction-reports-overview.html) transação para rastrear e manter a contagem de transações, como formulários enviados, documentos processados e documentos renderizados, na implantação do AEM Forms. Ele fornece informações sobre o uso do produto e ajuda os usuários empresariais a compreender os volumes de processamento digital.
* Ativado o suporte a PDF/UA para formulários XML.
* Adicionado allowProxy = true para Clientlib **aemfd.ccm.canal.contentpage**
* Código atualizado para fazer pesquisa de título avançada como contém em vez de igual.
* Atualize para a nova versão do NPM (Node Package Manager) no Computador de Integração Contínua.

**Pacote complementar do Forms**

**Integração de backend**

* Um erro é gerado ao fornecer um valor nulo como um valor para um campo opcional. NPR-24397
* A chamada WSDL está falhando quando o elemento tem namespace diferente da namespace global. NPR-24281
* (FDM WSDL) Obtendo DermisException: Exceção de dados de lista no caso de matriz de tipo de propriedade. NPR-24265
* (FDM WSDL) Obtendo DermisException: java.lang.Exception: createSOAPParam: Params Inválidos. NPR-24264
* (SDK do cliente FDM) Não é possível fazer testes do pré/pós-processador e da ação de envio personalizada. Hotfix do CQ-4238469
* Correções para problemas de Javadoc em Dermis. Hotfix do CQ-4244250
* Entrada aprimorada em WSDL (Web Services Description Language). Hotfix do CQ-4244133
* O teste de autenticação básica para WSDL resulta em erro diferente para a mesma configuração no AEM 6.3 e AEM 6.4. Hotfix para CQ-4244132
* Solicitação para incluir ValueUtil no client-sdk e javadocs. Hotfix do CQ-4242803
* (Configuração da nuvem do FDM) Não é possível configurar a Autenticação baseada em SOAP a partir da configuração da nuvem. Hotfix do CQ-4238462
* Dermis - adicione pacotes ausentes em Javadocs. Hotfix do CQ-4242815
* WSDLInvokerParams a ser incluído no sdk do cliente Add-On do Forms. NPR-23381: Hotfix do CQ-4240233

**Formulários adaptáveis**

* A execução do Documento (IC) deve ser registrada como uma transação usando o Serviço de Registro de Transação. Hotfix do CQ-4245333
* Durante a execução do UAT5, uma entrada está ausente no pdf gerado no estágio de verificação. Hotfix do CQ-4243184
* Caso de teste para obter uma cópia detalhada de guideContext. Hotfix do CQ-4242924
* O campo de tipo de Prova está ausente ao executar o UAT3 no servidor atualizado mais recente. Hotfix do CQ-4243120
* No servidor atualizado, o formulário enviado não possui os valores de Estado/Província/Região e País presentes no servidor de pré-atualização. Hotfix do CQ-4241444
* (ExpressionEditor) Erro ao navegar para Verificar estágio durante o envio do formulário. Hotfix do CQ-4241384
* Os valores estão ausentes no estágio de verificação no servidor pré-atualizado e atualizado para o formulário enviado. Hotfix do CQ-4241896
* O botão Sair e salvar na parte inferior da página não está funcionando. Hotfix do CQ-4240112
* Número de contato ausente na configuração atualizada. Hotfix do CQ-4239870
* Na `ACTION TAKEN` seção na guia Tipo de litígio, &quot;documentos adicionais para suportar minha solicitação&quot; tem um campo de Prova Tipo salvo &quot;nela&quot;. Hotfix do CQ-4239873
* Erro &quot;getDataAPI&quot; encontrado na etapa verifyPdf. Hotfix do CQ-4239865
* Erros nos registros de migração para a instância de autor e publicação. Hotfix do CQ-4239365
* Erros nos registros de migração para a instância de autor e publicação. Hotfix do CQ-4239635
* Erro de desserialização como &quot;Deserialização não permitida para a classe sun.util.day.ZoneInfo&quot; em registros de erros após o envio de um Formulário adaptável. Hotfix do CQ-4240419
* O campo de estado não está sendo preenchido na execução de formulário móvel. Hotfix do CQ-4240597
* Remova o uso de referência de componentes em modelos da lista anti-padrão. Hotfix do CQ-4239217
* Caixa numérica HTML5 definida como Flutuante ou Decimal fornece resultados de validação diferentes em navegadores diferentes. NPR-23528: Hotfix do CQ-4244097
* (Carregamento de imagem) Imagem não sendo exibida na pré-visualização DOR. Hotfix do CQ-4243178
* O servidor JEE emite um erro ao tentar enviar o formulário adaptável com &quot;PDF de email&quot; e &quot;Incluir anexos&quot;. Hotfix do CQ-4239894
* O gráfico não é traçado no tempo de execução usando a tabela/painel. Hotfix do CQ-4240010
* O envio do formulário adaptativo não está funcionando e nenhuma alteração na contagem de transações devido a falha no envio. Hotfix do CQ-4246125
* (Opção de imagem) O Documento das opções de registro não está visível. Hotfix do CQ-4236976
* A interface do usuário do editor de modelo não é estável. Hotfix do CQ-4241497
* Os AFs não são exibidos usando a guia ativos do painel lateral enquanto são mostrados usando a opção de navegação para a caixa de diálogo de propriedade do componente de formulário AEM. Hotfix do CQ-4236751
* A ID de fluxo de trabalho gerada para conversão de formulário deve estar disponível no Formulário adaptável gerado. Hotfix do CQ-4240014
* Não é possível selecionar modelo para criar uma página em sites na Atualização direta: Livecycle para o servidor 6.4. Hotfix do CQ-4241300

**Serviço de Assembler**

* Registro de transações nos Serviços do Assembler. Hotfix do CQ-4245018, CQ-4245017, CQ-4245016.
* A transação não é relatada quando a conversão de PDF/A é feita usando DDX. Hotfix do CQ-4246039

**Gerenciador do Forms**

* lista do botão FM CREATE para ser classificada alfabeticamente. Hotfix do CQ-4242307

**Portal do Forms**

* Os rascunhos salvos no servidor de pré-atualização não são abertos corretamente no servidor atualizado. Hotfix do CQ-4243303
* Atualização da versão para 7.1 para adobe-formsmanager-core-module. Hotfix do CQ-4245753
* Os rascunhos salvos no servidor de pré-atualização não são abertos corretamente no servidor atualizado. Hotfix do CQ-4243303
* Os cenários de anexo estão se quebrando ao substituir/adicionar/remover anexos em uma nova instância/mesma instância do rascunho. Hotfix do CQ-4243165
* A contagem de rascunhos recuperados da consulta ao banco de dados é superior à contagem de rascunhos presentes no portal. Hotfix do CQ-4241489
* Os formulários enviados no servidor de pré-atualização não estão presentes no servidor atualizado. Hotfix do CQ-4241490
* O formulário exibido na interface do usuário na guia Envios está no estado Não submetido, apesar da mensagem de envio bem-sucedida. Hotfix do CQ-4241487
* O guideContext deve ser formado copiando profundamente os campos, já que o guideContext contém customPropertyMap que é um objeto. Hotfix do CQ-4240126
* Erro ao tentar salvar um formulário. Hotfix do CQ-4240763
* A entrada para formulários salvos e enviados está sendo preenchida em crx/de, apesar de termos a configuração do banco de dados fornecida na Configuração de rascunho e envio do Portal do Forms. Hotfix do CQ-4240726
* (Pesquisar e Lister) O valor fixo do título de pesquisa avançado deve funcionar como contém em vez de igual. Hotfix do CQ-4245499

**Formulários móveis**

* O campo de data está sobreposto no Mobile Forms. Hotfix do CQ-4242256
* O envio de formulário para Formulários móveis deve ser registrado como uma transação usando o Serviço de registro de transação. Hotfix do CQ-4246166
* A submissão de formulário no Formset deve ser registrada como uma transação usando o Serviço de registro de transação. Hotfix do CQ-4246165

**Aplicativo AEM Forms**

* (Aplicativo Windows) Não é possível renderizar o formulário. Hotfix do CQ-4238005

**OSGI de fluxo de trabalho**

* Logon de transação no Workflow Atribuir Tarefa. Hotfix do CQ-4244440
* (Etapa do FDM) Não é possível usar valores dos metadados do fluxo de trabalho quando uma etapa Atribuir Tarefa é inserida entre a etapa do processo e a etapa do fdm. Hotfix do CQ-4241472
* A delegação da tarefa de atribuição não funciona na Integração do Forms em Workflows OSGI. NPR-23709: Hotfix do CQ-4243700
* (Editor de modelos de fluxo de trabalho) Alguns modelos de fluxo de trabalho não são editáveis pelo editor de modelo WF ClassicUI. Hotfix do CQ-4241151

**Documento MultiChannel**

* O campo Data no Modelo está sobrepondo o subformulário na criação IC. Hotfix do CQ-4240110
* O cabeçalho não deve ser excluído ou movido para cima e para baixo na criação de canais da Web IC. Hotfix do CQ-4243358
* (Editor IC) Linhas padrão a serem definidas como 1 para componentes de Tabela. Hotfix do CQ-4244848
* Área do Público alvo para permanecer visível mesmo depois que o conteúdo for arrastado e solto nele. Hotfix do CQ-4244534
* O canal da Web não reconhece o espaço das guias nos Fragmentos do Documento de texto. Hotfix do CQ-4244481
* A representação (IC) do Documento (Imprimir canal) deve ser registrada como uma transação usando o Serviço de Registro de Transação. Hotfix do CQ-4245335
* A representação (IC) do Documento (canal da Web) deve ser registrada como uma transação usando o Serviço de Registro de Transação. Hotfix do CQ-4245334
* A pesquisa de Documento Container ou Árvore do modelo de dados deve ser unificada para a pesquisa de filtro Ativo. Hotfix do CQ-4242305
* (Fragmento do Documento) A propriedade de recuo recua o texto pelo número de unidades que não podem ser compreendidas. Hotfix do CQ-4241082, CQ-4240643
* (Editor IC) O ícone Editar fragmento no bloco do fragmento do documento listado na guia Ativos não é facilmente detectável e compreensível. Hotfix do CQ-4241047
* Permitir acesso anônimo à biblioteca de cliente inacessível do IC Anonymous. Hotfix do CQ-4245588
* (canal da Web) Os dados não são resolvidos em nenhuma tabela na pré-visualização da Web e são exibidos como em branco. Hotfix do CQ-4244476
* Os cabeçalhos de tabela são mostrados como variáveis no canal da Web na geração automática. Hotfix do CQ-4244242
* (Editor IC) O conteúdo de um fragmento de Documento usado em um IC deve ser redimensionado automaticamente para ajustar à largura da área do Público alvo. Hotfix do CQ-4244094
* O nome do canal mostrado na parte superior central deve ser consistente com o título IC para WEB / IMPRESSÃO. Hotfix do CQ-4242498
* Editor de texto Painel de objetos de dados deve lista somente para entidades de nível superior, Hotfix para CQ-4244121
* O nome padrão não é atribuído ao adicionar um novo componente no editor. Hotfix do CQ-4244691
* Adicionando a configuração Colspan em todos os componentes do canal da Web. Hotfix do CQ-4244946
* A propriedade Largura da tabela do fragmento de layout não está sendo redefinida e honrada em Canal de impressão Carta ou Comunicação do cliente. Hotfix do CQ-4241574

**Gerenciamento de correspondência**

* Legendas removidas do modelo de carta após editar um ativo de texto que contém espaços reservados. NPR-24196
* O arquivo XDP, quando carregado e usado como um layout para modelos de carta, falha ao pré-visualização ou editar os modelos. NPR-24143: Hotfix do CQ-4244407
* A seleção de atribuição é selecionada por padrão no fragmento de lista. Hotfix do CQ-4240097
* Editor de condições - A avaliação de vários resultados deve ser ativada por padrão. Hotfix do CQ-4240096
* A imagem quando excluída da Lista ainda mostra a imagem na pré-visualização. Hotfix do CQ-4239909
* O conjunto de regras no módulo de condição é definido como &#39;Padrão&#39; para todos os módulos. Hotfix do CQ-4239878
* A criação do Dicionário de dados falha com o erro &quot;Exceção JCR desconhecida&quot;. Hotfix do CQ-4244122
* Lacunas em JavaDocs de conteúdo 6.3. Hotfix do CQ-4213586

**Instalador do Forms JEE**

**Núcleo**

* (Espaço de trabalho HTML) Detalhes de rastreamento ausentes para aplicativos com símbolo de parênteses no nome. NPR-23402

**Serviço PDFG**

* Registro de transações em serviços PDFG. Hotfix do CQ-4244951, CQ-4244586
* Redução de PDFs ao desincorporar seletivamente fontes por meio de uma única chamada de API. NPR-23287
* As configurações do PDFG atualizam o problema na atualização do AEM. Hotfix do CQ-4241176
* Registro de transações no serviço PDFUtilment. Hotfix do CQ-4245014

**Gerenciamento de processos**

* (Espaço de trabalho HTML) Os Pontos de partida do processo não são classificados em ordem alfanumérica. Hotfix do CQ-4239629
* (Espaço de trabalho HTML) Prepare a chamada de dados que aparece duas vezes quando o rascunho é aberto pela primeira vez. Hotfix do CQ-4243280
* (Espaço de trabalho HTML) O processo de preparação de dados é acionado ao fechar um formulário. Hotfix do CQ-4239456
* O espaço de trabalho trava quando atravessado entre duas tarefas. Hotfix do CQ-4237125

**Workbench**

* Gerenciar Perfil de açãoO processo de preparação de dados falha quando a configuração do processo de renderização padrão está definida como HTML. Hotfix do CQ-4244292

**Designer do Forms**

* Adicione suporte PDF/UA a formulários XML gerados pelo Designer e pelo Serviço de saída. NPR-23022
* Os hiperlinks em linha definidos no Designer não são marcados nem têm texto alternativo quando salvos como PDF a partir do Designer. NPR-23023

**Feature Packs incluídos**

**Assets**

* Adição da capacidade para Tags inteligentes aprimoradas. Para obter mais informações, consulte Tags [inteligentes](https://helpx.adobe.com/experience-manager/6-4/assets/using/enhanced-smart-tags.html)aprimoradas. NPR-21951: Hotfix do CQ-4234883
* Referências de AEM Assets introduzidas no InDesign. Para obter mais informações, consulte Referências de [AEM Assets no InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Criação de página) Melhorias no Editor de imagens. Para obter mais informações, consulte Editor [de](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/image-editor.html)imagens. NPR-24267: Hotfix do CQ-4245502

**Pacotes OSGI e pacotes de conteúdo incluídos**

O texto seguinte documentos a lista dos pacotes OSGI e dos pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.1.0

[Obter arquivo](assets/6_4_1_0_bundle-list.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.1.0

[Obter arquivo](assets/6_4_1_0_content-package-list.txt)

### Install 6.4.8.0 {#install}

#### Requisitos de configuração {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para clientes com Pacotes de recursos instalados no AEM 6.4. Os Pacotes de recursos opcionais fornecidos pela Adobe têm dependências na versão de lançamento e no service pack. Se você tiver algum Feature Pack instalado, entre em contato com a equipe de Atendimento ao cliente do AEM para validar a compatibilidade desses pacotes de recursos com este Service Pack para o AEM 6.4.

* O AEM 6.4.8.0 requer o AEM 6.4. Para obter detalhes, consulte a documentação [de](../sites-deploying/upgrade.md)atualização.
* O download do Service Pack está disponível no portal [de distribuição de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) software para download.
* Em uma implantação com MongoDB e várias instâncias, instale o AEM 6.4.8.0 em uma das instâncias do autor usando o Gerenciador de pacotes.
* Antes de instalar o Service pack, verifique se você tem um instantâneo ou um backup atualizado da sua instância do AEM.
* Reinicie a instância antes da instalação. Embora isso seja necessário apenas quando a instância ainda está no modo de atualização (e esse é o caso quando a instância foi atualizada de uma versão anterior), geralmente é recomendado se a instância estava sendo executada por um período de tempo maior.

>[!NOTE]
>
>A Adobe não recomenda remover ou desinstalar o pacote AEM 6.4.8.0.

### Install the Service Pack via Package Manager {#install-the-service-pack-via-package-share}

Execute as seguintes etapas para instalar o Service Pack em uma instância do AEM 6.4 existente:

1. Baixe o pacote da Distribuição de software.

1. No AEM, faça logon no Package Manager e adicione o pacote baixado do AEM 6.4.8.0. Selecione o pacote carregado e clique em **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**A caixa de diálogo na interface do usuário do Gerenciador de pacotes às vezes sai imediatamente durante a instalação da versão 6.4.8.0**
>
>Portanto, é recomendável aguardar a estabilização dos registros de erros antes de acessar a instância. O usuário deve aguardar os registros específicos relacionados à desinstalação do pacote do atualizador antes de ter certeza de que as instalações foram bem-sucedidas. Geralmente isso acontece no Safari, mas pode acontecer intermitentemente em qualquer navegador.

### Instalação automática {#auto-installation}

Há duas maneiras de instalar automaticamente o AEM 6.4.8.0 em uma instância em execução:

A. Coloque a embalagem em ..*/crx-quickstart/install* enquanto o servidor estiver em execução. O pacote é instalado automaticamente.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/pt/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>O AEM 6.4.8.0 não oferece suporte à instalação do Bootstrap.

### Validar instalação {#validate-install}

1. A página Informações do produto (*/system/console/ productinfo *) agora deve mostrar a string da versão atualizada &quot;Adobe Experience Manager, Versão 6.4.8.0&quot; em Produtos instalados.
1. Todos os pacotes OSGI são ATIVOS ou FRAGMENTOS no Console OSGi (Use o console da Web: /system/console/bundles).
1. O pacote OSGI org.apache.Jackrabbit.oak-core está na versão 1.8.17 ou superior (Use o console da Web: /system/console/bundles).

Para determinar a plataforma certificada para execução com esta versão do AEM Sites e do Assets, consulte Requisitos [](../sites-deploying/technical-requirements.md)técnicos.

>[!Nnota]
>On successful installation of the package, an >informational message appears indicating that the content >package has installed successfully,  such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Atualizar visualizadores do Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">O AEM 6.4.8.0 contém uma nova versão dos visualizadores do Dynamic Media (5.10.1) que permite a verificação de nomes de duplicados na página Predefinição de imagem. Os clientes da Dynamic Media devem executar o seguinte comando para exibir as predefinições do visualizador de caixa para um estado atualizado.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará novas predefinições do visualizador para o local /conf.

### Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

#### Instalar complemento do AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms. As correções do AEM Forms são entregues por meio de um pacote complementar separado.

>[!NOTE]
>
>O AEM 6.4.8.0 inclui uma nova versão do [Pacote de compatibilidade do AEM Forms](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/AEM-FORMS-6.4.7.0-COMPAT). Se você estiver usando uma versão anterior do Pacote de compatibilidade do AEM Forms e estiver atualizando para o AEM 6.4.8.0, instale a versão mais recente do pacote de compatibilidade do AEM Forms após a instalação do Pacote complementar do Forms.

1. Verifique se você instalou o AEM Service Pack.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://helpx.adobe.com/experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html#InstallAEMFormsaddonpackage).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms no JEE. As correções no JEE do AEM Forms são entregues por meio de um instalador separado.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0015](https://helpx.adobe.com/br/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Configurações necessárias para o NPR-21268 {#configuration-settings-required-for-npr}

Se você estiver usando a interface clássica (antiga) e tiver criado modelos de metadados usando-a, siga as etapas para executar o script JMX para preservá-las -

1. Vá para /system/console/jmx.
1. Clique em &quot;Migrar modelos de metadados&quot;.
1. Clique em &quot;migrateMetadataTemplatesAtPath&quot; e forneça o caminho da pasta em que deseja que os modelos de metadados sejam preservados.

#### Configurações necessárias para o NPR-24536 {#configuration-settings-required-for-npr-1}

A contagem de filas compartilhadas não é atualizada, por padrão, para outros usuários quando um usuário reclama uma tarefa. Para isso, introduzimos uma nova propriedade. Siga as etapas abaixo para configurar essa propriedade na sua instância do AEM:

1. Vá para IU administrativa -> Serviços -> Espaço de trabalho -> Administração global.
1. Exportar configurações globais.
1. No arquivo XML baixado, adicione a tag &lt;client_TasksPollingInterval>10&lt;/client_TasksPollingInterval> Aqui, 10 é o valor de exemplo em segundos. É possível modificá-la de acordo.
1. Salve o arquivo.
1. Volte para IU administrativa -> Serviços -> Espaço de trabalho -> Administração global.
1. Importe o arquivo xml na seção Importar configurações globais.
1. Agora você pode fazer logout do sistema e login novamente.
1. A contagem de start da fila compartilhada que são atualizados para outros usuários na área de trabalho.
1. Para desativar a pesquisa, altere o valor para 0 e importe o arquivo XML novamente.

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Recursos removidos/obsoletos {#removed-deprecated-features}

Esta seção lista os recursos e funcionalidades removidos ou descontinuados do AEM 6.4.

| Área | Recurso | Substituição | Versão |
|---|---|---|---|
| Ativos | Gerenciar ação de tag para subativos | Nenhuma substituição | AEM 6.4.2.0 |
| Integração do Assets e da Adobe Creative Cloud | [O AEM para compartilhamento](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/creative-cloud.html) de pastas da Creative Cloud foi introduzido no AEM 6.2 como uma forma de fornecer aos usuários criativos acesso aos ativos do AEM. Uma nova funcionalidade lançada no aplicativo da Creative Cloud, o Adobe Asset Link, fornece uma experiência de usuário melhor e acesso avançado a ativos do AEM diretamente do Photoshop, InDesign e Illustrator. A Adobe não fará mais aprimoramentos no recurso de compartilhamento de pastas. Embora o recurso esteja incluído no AEM, os clientes são aconselhados a usar a substituição. | Adobe Asset Link ou aplicativo de desktop. Para obter mais informações, consulte o artigo [Integração da AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problemas conhecidos {#known-issues}

* Os seguintes erros e avisos podem ser exibidos durante a instalação:

   * Erros ao criar instância de componente e o Service Fatory retornado nulo ocorrem devido à reinicialização do repositório:

      * com.day.cq.cq-personalization \[com.day.cq.personalization.impl.DefaultProfileProvider(938)\] Não é possível criar a instância do componente devido a uma falha ao vincular reference profileManager
      * org.apache.sling.commons.FrameworkEvent ERROR (org.osgi.framework.ServiceException: A fábrica de serviços retornou nulo. (Componente: com.day.cq.tagging.impl.TagGarbageCollector (1687))
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Tempo limite aguardando a conclusão do registro da alteração reg.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Nenhuma janela de manutenção encontrada no granito/operações/manutenção
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: O método unbindEmenda lançou uma exceção (java.lang.IllegalStateException: Serviço já não registrado).
Esses erros não exigem nenhuma ação, pois não afetam sua instância do AEM.


### Problemas resolvidos {#resolved-issues}

**AEM 6.4.4.0**

* Nenhum erro de recurso encontrado é observado ao importar/exportar metadados. CQ-4253263
* Não é possível editar qualquer componente de imagem e propriedades de página depois de aplicar 6.4.3.0 sobre a 6.4.2.0. CQ-4260316 e CQ-4260441Para contornar esse problema:
   * Ir para o Gerenciador de pacotes
   * Reinstale o pacote &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * Recompile todos os JSPs `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` OU Reinicie a instância.

### Pacotes de conteúdo e pacotes OSGi incluídos {#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de conteúdo incluídos no AEM 6.4.8.0.

Lista de pacotes OSGi incluídos no AEM 6.4.8.0

[Obter arquivo](assets/6.4.8.0_osgi_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.8.0

[Obter arquivo](assets/6.4.8.0_content_packages.txt)

### Recursos úteis {#helpful-resources}

* [Notas de versão do AEM 6.4](../release-notes/release-notes.md)
* [Página do produto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentação do AEM 6.4](https://helpx.adobe.com/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

### Sites restritos {#restricted-sites-new}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Entre em contato com o Suporte ao cliente](https://daycare.day.com/)
