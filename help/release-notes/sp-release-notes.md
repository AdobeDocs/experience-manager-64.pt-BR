---
title: Notas de versão do AEM 6.4 Service Pack
seo-title: AEM 6.4 Service Pack Release Notes
description: Notas de versão específicas dos Service Packs do Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '21517'
ht-degree: 26%

---

# Notas de versão do AEM 6.4 Service Pack  {#aem-service-pack-release-notes}

## Informações da versão {#release-information}

| Produtos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versão | 6.4.8.0 |
| Tipo | Lançamento do Service Pack |
| Data | 5 de março de 2020 |
| URL de download | AEM 6.4.8.0 em [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## O que está incluído no AEM 6.4.8.0 {#what-s-included-in-aem}

O AEM 6.4.8.0 é uma atualização importante que inclui novos recursos, principais melhorias solicitadas pelo cliente e desempenho, estabilidade, aprimoramentos de segurança, lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.8.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns destaques principais desta versão do Service pack:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.20.

* A funcionalidade de quebra de texto é compatível com sites em japonês no WCM-RTE.

* O processamento de quebra de palavra e quebra de linha é compatível com sites em japonês.

* Adição de suporte para usar o método BUNSETSU para quebrar a frase e as linhas do idioma japonês nas posições apropriadas.

* A interface do usuário do CCR para gerenciamento de correspondência agora aceita valores decimais para a localidade alemã.

* A integração do modelo de dados de formulário usando o serviço da Web SOAP agora é compatível com grupos de opções ou atributos em elementos.

* O AEM Assets agora está configurado com o Brand Portal por meio de [!DNL Adobe I/O].

* Atualização da versão do jQuery fornecida no ContextHub para 3.2.1.

## Lista de alterações {#list-of-changes}

### Sites {#sites}

* Quando um URL de uma página do AEM Sites contém um sinal de dois pontos ou de porcentagem, o navegador subjacente para de responder e os ciclos da CPU mostram um pico (NPR-32368, NPR-31917).
* Quando uma página do AEM Sites é aberta para edição e um componente é copiado, a ação de colar permanece indisponível para alguns espaços reservados (NPR-32328).
* O fluxo de trabalho de solicitação de ativação não inclui ativos referenciados (NPR-32304).
* Quando um Blueprint é criado, se o número de registros for superior a 80, somente os primeiros 80 registros serão exibidos. Blueprint exibe linhas em branco para o resto dos registros (NPR-32058).
* Os usuários podem salvar um Fragmento de conteúdo sem fornecer informações nos campos obrigatórios (NPR-31988).
* A navegação automática não funciona para o caminho configurado em um Componente de fragmento de experiência principal (NPR-31921).
* Quando você altera o tipo de célula de tabela no Editor de Rich Text (RTE), o erro abaixo ocorre:
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Quando o conteúdo é movido dentro da mesma pasta, a opção de movimentação da página é desativada (NPR-31841).
* Adição de suporte para dividir frases em japonês usando o método BUNSETSU e linhas de quebra na posição apropriada (NPR-31836).
* Ao editar um hiperlink no Editor de Rich Text (RTE), o caminho recém-selecionado não é salvo (NPR-31659).
* Ao excluir um componente de vários campos e desfazer a exclusão, o componente é restaurado, mas os dados não são restaurados (NPR-31617).

### Assets {#assets}

* Uma pasta sem nome é criada no Dynamic Media Classic ao mover um ativo de uma pasta para outra no Experience Manager com a configuração do Dynamic Media Classic (NPR-32440).

* A página de detalhes dos ativos dos arquivos do PDF não mostra os botões de ação no Experience Manager que está sendo executado no modo Dynamic Media Scene7 (NPR-32316).

* As representações de ativos e vídeos não podem ser excluídas (NPR-32213).

* O ícone de calendário para ativação agendada não é exibido na coluna Status (na interface clássica da lista de ativos do DAM) para ativos cuja ativação está agendada para uma data e hora posteriores (NPR-32198).

* A relação de ativos é substituída quando os ativos estão relacionados a mais de um ativo usando Outros (NPR-32196).

* O botão Salvar não importa o Conjunto Remoto quando o usuário não tiver feito alterações no Editor de conjunto no Cliente Dynamic Media (NPR-32178).

* A assimilação de PSD asset causa o pico da CPU e a instância do Experience Manager Author que não responde (NPR-32165).

* Exceção de falta de memória observada quando um arquivo ZIP grande é carregado no Experience Manager DAM (NPR-32155).

* Os URLs do histórico de versão são exibidos no campo Referenciado por na página Propriedade de ativos (NPR-31889).

* Desfazer a publicação do Brand Portal, na página Gerenciar publicação, falha nas subpastas de uma pasta publicada (NPR-31835).

* Falha no upload de codificações de vídeo do Dynamic Media quando a Configuração da Scene7 Cloud é colocada em uma pasta privada `/conf` em vez de `/conf/global` (NPR-31779)

* A imagem não é vista na linha do tempo depois que as anotações são adicionadas, no Experience Manager que está sendo executado no modo de execução Dynamic Media Scene7 (NPR-31754).

* O arquivo ZIP baixado do DAM não pode ser aberto usando WinZip (NPR-31745).

### Integrações {#integrations-6480}

* O **Empresa** e **Relatório** Os menus suspensos do Suite são ocultos uma vez **Fonte de geração de relatórios** é selecionado ao configurar o Adobe Analytics nos serviços de nuvem do Experience Manager (NPR-31729).

* As propriedades do Adobe Campaign não são limpas quando a cópia de idioma de um boletim informativo vinculado a uma Adobe Campaign é feita, enquanto a limpeza acontece quando um boletim informativo vinculado a uma Adobe Campaign é copiado ou colado (NPR-32540).

* ReportSuitesServlet está vulnerável a SSRF (NPR-32161).

### Sling {#sling-6480}

* O sombreamento não determinístico da observação de recursos não está funcionando (CQ-4286466).

### Projetos {#projects-6480}

* O botão Criar não fica visível para o usuário, mesmo se ele tiver permissão para criar projeto na subpasta (NPR-31831).

* A funcionalidade para alternar entre exibição de cartão, exibição de lista e exibição de calendário não está funcionando após selecionar a exibição de calendário em Projetos (NPR-31829).

### Tradução {#translation-6480}

* A criação de projetos de tradução para vários idiomas gera o projeto apenas para alguns idiomas em vez de todos e um erro (o resolvedor de recursos já está fechado) é observado no log (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Problemas de permissão levam à exibição de erros ao mover páginas em um blueprint (NPR-32610).

### Editor de página WCM {#wcm-page-editor-6480}

* O navegador para de responder ao tentar adicionar um componente a uma página com um formato de URL específico (NPR-32368, NPR-31917).

### WCM-Interface do administrador {#wcm-admin-ui-6480}

* A publicação de gerenciamento não inclui ativos referenciados no fluxo de trabalho de solicitação de ativação (NPR-32304).

### Communities {#communities}

* Não é possível atualizar a imagem de miniatura do grupo para grupos (NPR-32603).

### Brand Portal {#brand-portal}

* Cancelar a publicação do esquema de metadados no AEM Assets preenche uma mensagem de erro, embora o esquema seja removido no backend (CQ-4286871).

### Interface do usuário do Foundation {#foundations-ui-6480}

* Caracteres inválidos são exibidos no URL adicionado a um componente de Botão (NPR-32684).

### Forms {#forms}

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

* Designer: Se a opção de marcação estiver ativada, a borda do subformulário desaparecerá na saída do PDF gerado (NPR-32546, NPR-32322).

* Designer: se houver células mescladas em uma tabela, o teste de acessibilidade falhará para o arquivo PDF de saída convertido de um formulário XDP usando o serviço de saída (NPR-32079).

* Segurança de documento: Um arquivo PDF protegido não abre offline com a opção DisableGlobalOfflineSynchronizationData definida como True (NPR-32080).

* Segurança de documento: Problemas ao abrir um arquivo PDF protegido após a atualização do ES4 para o AEM 6.3 (NPR-32170).

* Serviços de documento: Uma mensagem de erro é exibida ao tentar converter um arquivo PDF em um documento PDF/A usando o método de conversão toPDFA (NPR-32663).

* Serviços de documento: Uma exceção é exibida ao aplicar o serviço de extensões Reader em um arquivo PDF (NPR-32639).

* Serviços de documento: Uma mensagem de erro é exibida durante a montagem e conversão de arquivos XDP em arquivos PDF (NPR-31821).

* O Analytics não exibe resultados apropriados ao enviar ou abandonar formulários em uma página do Sites (NPR-31359).

### Correções e Feature Packs incluídos em Pacotes de serviço anteriores {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

O AEM 6.4.7.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.7.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.7.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.17.
* Adição de suporte para definir a versão de uma página Sites ao excluí-la.
* A nova coluna para a data criada, que é classificável, foi adicionada em **Lista DAM** exibir e nos resultados da pesquisa de ativos em **Lista** (NPR-31311).
* Classificação de ativos com base em **Nome** a coluna foi permitida em **Lista** exibir.
* O tamanho do lote e o tempo limite da etapa do fluxo de trabalho para Reprocessar e Upload em lote agora são configuráveis na interface do usuário no Dynamic Media.
* O `pdfBrochure` O foi definido como falso na configuração de nuvem do Scene7, para salvar memória no IPS.

##### Ativos {#assets-6470}

**Aprimoramentos do produto**

* A versão de exportação do pacote de API `package com.day.cq.dam.handler.standard.msoffice` suportado pela `dam-handler` O pacote é atualizado para 6.0.0 (CQ-4279059).
Se estiver usando o pacote `com.day.cq.dam.handler.standard.msoffice` na implementação personalizada, recomenda-se compilar o `dam-handler` pacote com o uber jar mais recente.

* A nova coluna para a data criada, que é classificável, foi adicionada na exibição de lista DAM e nos resultados da pesquisa de ativos na exibição de lista (NPR-31311).

* A classificação de ativos com base na coluna Nome foi permitida na exibição em Lista (NPR-31299).

**Correções**

* Os metadados de alguns documentos do PDF não são atualizados e salvos no PDF sobre como modificar seu título (NPR-31575).

* Os ativos com o símbolo &quot;+&quot; no nome do arquivo não podem ser excluídos (NPR-30588).

* As propriedades da pasta DAM não mostram os usuários ou grupos adicionados (criados pela sincronização LDAP) em Grupos de usuários fechados (NPR-30555).

* Caracteres especiais que ocorrem na linha Assunto dos Modelos de email não são mostrados corretamente (NPR-30547).

* Os nomes dos ativos são alterados para letras minúsculas ao mover ativos de uma pasta para outra em AEM em execução no modo de execução do Dynamic Media Scene 7 (NPR-31631).

* Os nomes do conjunto de imagens são alterados para letras minúsculas no Scene7, quando o conjunto de imagens (ou conjunto de mídia) é criado e nomeado com a convenção de nomenclatura apropriada no DAM (NPR-31576).

* O fluxo de trabalho Codificação de Vídeo do Dynamic Media está falhando ao gerar a miniatura do vídeo que foi migrado do Scene 7 para o Dynamic Media - Modo de execução do Scene 7 (NPR-31523).

* Erro Interno do Servidor é observado ao usar o filtro para procurar Conjuntos, em AEM em execução no Dynamic Media - Modo de execução do Scene7 (NPR-31388).

* Um erro é observado ao editar um conjunto de imagens remoto, para a imagem que reside na pasta nomeada como o nome da empresa Scene7 (NPR-31347).

* Os ativos que contêm referências não estão sendo publicados (DM) (NPR-31179).

* O valor de expiração (tempo de funcionamento do cache do cliente) configurado para o modo Híbrido do Dynamic Media não é replicado no ambiente de entrega do Dynamic Media (NPR-31126).

* Uploads de AEM Dynamic Media - modo de execução do Scene7 para o Scene7 estão demorando muito para serem concluídos (NPR-30926).

* Depois de criar uma página com o componente Dynamic Media enquanto publica o mesmo, a partir da instância do autor em execução no modo de execução Dynamic Media - Scene 7, o usuário é solicitado a publicar a configuração do dmscene7 (NPR-30880).

* O valor do parâmetro &quot;ativo&quot; no código incorporado do visualizador permanece inalterado após alterar os valores no campo &quot;Título após a movimentação&quot; e &quot;Nome após a movimentação&quot; no Dynamic Media - Scene 7 (NPR-30745).

* A pesquisa da interface do usuário de toque (feita pelo Omnisearch) resulta a rolagem automaticamente para cima e perde a posição de rolagem do usuário (NPR-31306).

* A limpeza de eventos do DAM exclui os dados de eventos mais recentes (maxSavedActivities) e retém os dados criados anteriormente (NPR-30870).

* O título e a alteração de nome do ativo não persistiram após a operação de movimentação para uma pasta de destino que aciona a rolagem infinita ao selecioná-lo (NPR-30647).

* As coleções são removidas da exibição ao aplicar qualquer filtro no AEM Assets acessado do Adobe Asset Link (CQ-4280534).

* O tamanho do lote e o tempo limite da etapa do fluxo de trabalho para Reprocessar e Upload em lote não são configuráveis na interface do usuário e precisam ser definidos no CRXDE e o fluxo de trabalho precisa ser sincronizado duas vezes (CQ-4281254).

* O nome da etapa do fluxo de trabalho para upload em lote e a etapa de upload simples é o mesmo no Scene7, o que resulta em confusão (CQ-4281176).

* O fluxo de trabalho de reprocessamento no Scene 7 fica travado se um ativo estiver ausente no nó de metadados (CQ-4281170).

* A etapa BatchUpload no fluxo de trabalho de reprocessamento não funciona para a pasta que tem o ativo de vídeo (CQ-4280630).

* As opções de PDF enviadas para o DM têm extractKeywords definido como true por padrão (CQ-4280101).

* Uma Exceção de Ponto Nulo é observada ao executar o fluxo de trabalho de Reprocessamento do Scene 7 em uma pasta que contém ativos não-DM (CQ-4279555).

* A renomeação de ativos no AEM não é sincronizada com a cena 7, quando um ativo com um nome duplicado já existe no Scene 7 (CQ-4276763).

* O arquivo zip enviado por email para download de ativos não é descompactado quando um usuário com permissões de leitura tenta abri-lo (CQ-4277925).

* O fluxo de trabalho de representação de PPT falha ao gerar representações dos arquivos PPT carregados, pois o AEM 6.4 não é atualizado para com.adobe.granite.poi versão 2.0.28 (CQ-4279059).

* Os arquivos PDF não são indexados e o conteúdo no não é pesquisável (CQ-4278916).

##### Sites {#sites-6470}

* Quando as inicializações são promovidas com apenas as páginas de promoção modificadas e as inicializações de promoção com páginas modificadas são feitas, somente as páginas modificadas são exibidas para serem promovidas. Além disso, quando a lista a ser promovida estiver correta, as páginas não modificadas ainda serão exibidas na parte inferior da lista (NPR-31314).

* Quando uma página do AEM Sites é movida para um local diferente, suas propriedades não são atualizadas adequadamente para refletir seu novo local (NPR-31265).

* Para um novo Blueprint, se o número de registros for superior a 40, somente os primeiros 40 registros serão exibidos. Blueprint exibe linhas em branco para o resto dos registros (NPR-31182).

* Quando o número de LiveCopies é grande, a visão geral da LiveCopy demora muito para renderizar a visualização (NPR-30945).

* Adição de suporte para definir a versão de uma página ao excluí-la. Se o controle de versão estiver desativado para a página excluída, o AEM Sites não poderá restaurar essas páginas (NPR-30891).

* Quando um usuário adiciona caracteres japoneses ou coreanos na propriedade de descrição de um menu, o menu exibe caracteres distorcidos para o texto em japonês e coreano (NPR-31331).

* Quando um usuário foca nos campos do painel à esquerda e usa um atalho do teclado para colar o conteúdo, ele cola o conteúdo da área de transferência do editor de páginas em vez do conteúdo copiado dos campos do painel à esquerda (NPR-31169).

* Quando um usuário edita um fragmento de conteúdo, a variação já excluída do fragmento de conteúdo é restaurada (NPR-31178).

* A consulta de Modelos de fragmento de conteúdo é ineficiente. É muito lento se a instância tiver muitas páginas e resultar em um erro (NPR-30666).

* Ao salvar o modelo de fragmento de conteúdo, a hora no campo de data e hora é definida como 00:00 (NPR-30540).

##### Integrações {#integrations-6470}

* Ao configurar o Adobe Launch, uma barra (/) é anexada ao URL da biblioteca (NPR-30700).

* O desempenho do ContextHub degrada após a publicação (NPR-30884).

##### Sling {#sling-6470}

* Atualize o pacote do provedor de segurança do console da Web para 1.2.4 para remover a dependência da api de inicialização da plataforma de lançamento do webconsolesecurityprovider (NPR-30885).

##### Plataforma {#platform-6470}

* As atualizações na configuração de tamanho do buffer do serviço HTTP baseado em Java não são salvas (NPR-30925).

* O QueryBuilder agora oferece suporte a orderby fn:name() em consultas xpath (NPR-31322).

* Atualização do administrador de eventos distribuídos do Sling para a versão 1.1.4, melhorando a qualidade dos logs em um ambiente em cluster (NPR-29256).

##### Interface do usuário do Foundation {#foundation-6470}

* Rolar para o final da página de resultados com um grande número de resultados de pesquisa causa falha no navegador (NPR-31332).

* Ao alternar da exibição de Cartão para a exibição de Lista em uma página de resultados de pesquisa, há um atraso antes que a página possa ser rolada (NPR-31280).

##### Oak {#oak-6470}

* Os arquivos do MS Office com extensões de arquivo .docx e .xlsx contendo imagens JPEG não são analisados usando o analisador Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* A integração do Livefyre com a atualização AEM 6.4 oferece uma exceção de ponto nulo, quando a integração é feita usando o plug-in DITA para recursos sintéticos. A integração, no entanto, funciona quando os componentes são adicionados manualmente (FYR-11066).

##### Tradução {#translation-6470}

* O caminho para o fragmento de experiência de destino não está sendo atualizado ao promover uma página de inicialização (NPR-30830).

##### Comunidades {#communities-6470}

* A funcionalidade de email não está funcionando corretamente em alguns casos, mesmo quando as mensagens de email estão ativadas nas configurações de notificação, o sistema lança uma exceção em NotificationsActivityStreamProvider (NPR-31521).
* Não é possível criar novos membros, uma tela em branco é exibida na tela Criar membro AEM instância do autor (NPR-30951).
* O usuário não pode postar um comentário em um blog no Internet Explorer 11 (NPR-30927).
* O Administrador de um Grupo Restrito não pode visualizar o Cartão de Grupo, não é possível executar nenhuma operação de Link Rápido (Editar/Publicar/Excluir grupos) AEM instância do autor (NPR-30810).
* Grupos de membros/As informações do grupo não estão visíveis na criação de um novo Site AEM instância do autor (NPR-28840).

##### Forms {#forms-6470}

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Pacote complementar do Forms**

**Formulários adaptáveis**

* As cadeias de caracteres contêm a chave do dicionário ao localizar formulários adaptáveis (NPR-31109).

* As caixas de seleção e as listas suspensas no Forms falham nas verificações de acessibilidade (NPR-31282).

**Formulários HTML5**

* Gerar a visualização HTML5 de um formulário XDP mostra uma oscilação ao adicionar instâncias de um formulário secundário (NPR-30907).

**Serviços de documento para OSGi**

* A execução de vários encadeamentos simultâneos para montar os formulários usando o método com.adobe.fd.assembler.service.AssemblerService.invoke() exibe uma mensagem de erro (NPR-31164).

* Os arquivos temporários criados pelo Assembler Service não são excluídos automaticamente e exigem AEM reinicialização (NPR-30846).

* Aplicar direitos de ReaderExtension ao PDF resulta em uma mensagem de erro (NPR-30930).

**Fluxo de trabalho**

* O fluxo de trabalho do OSGi falha devido à utilização da CPU em 100% (NPR-31234).

**Instalador do Forms JEE**

**Serviços de documento**

* O Serviço de conversão de PDF não consegue converter documentos do PDF em PostScript e exibe uma mensagem de erro (NPR-31267).

* A configuração de ponto de extremidade SOAP é redefinida após a aplicação de um patch para corrigir HTML para falha de PDF (NPR-31309).

**Serviço PDFG**

* Não é possível carregar o arquivo de configurações do Adobe PDF baixado usando a interface do usuário do administrador (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

O AEM 6.4.6.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.6.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.6.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.15.
* Adição de suporte para rastrear estados dinâmicos da interface do usuário no evento de rastreamento na API de base.
* Adição do suporte de representação ao componente principal da imagem.

**Assets**

* Link de compartilhamento de ativos de uma pasta com espaço e `&` no nome exibe cartões cinza em branco para alguns ativos. NPR-29934: Hotfix do CQ-4270187
* O fluxo de trabalho do DAM falha ao criar ativos MP4 para AEM. NPR-30031: Hotfix do CQ-4271352
* Problema de conectividade com o Adobe Smart Tag por meio do Datapower. NPR-30026: Hotfix do CQ-4269457
* Não é possível localizar o PDF utilizando OmniSearch. NPR-30046: Hotfix do GRANITE-26290
* Os caminhos de ativos nos metadados de URLs e de pastas gerados pela API ACP não são codificados por URL.  GRANITE-26198: Hotfix do CQ-4271814
* A funcionalidade Criar tarefa de revisão não funciona devido à carga indefinida. NPR-30469: Hotfix CQ-4274263
* A capacidade de alternar a exibição da exibição de cartão para a exibição de lista e vice-versa desaparece após fazer um OmniSearch no seletor de ativos. NPR-29852: Hotfix do CQ-4269369
* (Interface do usuário de toque) Durante o assistente de gerenciamento de publicação, os ativos são adicionados à fila de replicação após a adição das páginas, fazendo com que alguns dos ativos apareçam após alguns segundos. NPR-29985: Hotfix do CQ-4270724
* A classificação da consulta de pesquisa por relevância retorna documentos do InDesign junto com modelos do InDesign. Hotfix do CQ-4273864
* Se o usuário tiver uma ID de email em letras maiúsculas, os usuários não poderão fazer check-in nos ativos cujo check-out foi feito anteriormente. Hotfix do CQ-4276575
* Configuração do Dynamic Media Cloud Services em `DMHybrid` O modo resulta em vários conjuntos de relatórios vazios criados no Analytics sem uma ID de conjunto de relatórios armazenada em AEM resultando em duplicação de conjunto de relatórios. Hotfix do CQ-4276855
* A caixa de diálogo de aviso não é exibida ao promover na página &quot;Tag gerenciada&quot;. Hotfix do CQ-4252851
* Ao usar o carrossel para gerenciar tags, o botão de navegação não funciona. Hotfix do CQ-4275499
* A funcionalidade de ativo de movimentação em massa é dividida, resultando na não movimentação de ativos. Hotfix do CQ-4272987

**Sites**

* `pageinfo.json` As solicitações são extremamente lentas e demoram muito para serem carregadas. NPR-29709: Hotfix do CQ-4269560
* `onTime` ou `offTime` as propriedades de metadados salvas em ativos não são recuperadas se o servidor de AEM for reiniciado. NPR-30413: Hotfix do CQ-4272784
* Devido ao comportamento incorreto da classe ConfigPostProcessor , suspender a página pai remove o cq: Tipo de combinação do LiveRelationship a partir da página secundária. NPR-30536, NPR-30510: Hotfix do CQ-4254113
* Scripts entre sites (XSS) na caixa de diálogo do workflow de Início na página Edição de campanha . NPR-29747: Hotfix do CQ-4271067
* (Interface clássica) O estágio de bloqueio de workflow desativa a guia de workflow até que o bloqueio seja liberado. NPR-30356: Hotfix do CQ-4237557
* (IE11) Ao colar conteúdo HTML em um componente Rich Text Editor com defaultPasteMode = texto simples, o HTML é colado com a formatação, portanto, defaultPasteMode não tem efeito. NPR-30045: Hotfix do GRANITE-26094
* (Interface clássica) Quando a página de administrador do site é recarregada, todos os itens suspensos no menu &quot;Novo&quot; são desativados. NPR-29980: Hotfix do CQ-4272044
* Não é possível adicionar estilos ao texto ou editar qualquer estilo existente criado no conteúdo. NPR-29712: Hotfix do CQ-4266249
* (Interface clássica) Ativos sem dc: o valor do título é listado sem título no navegador de diálogo do campo de caminho. NPR-30166: Solicitação de backport para CQ-8858
* O cq: o ouvinte não funciona com componentes aninhados mesmo depois de adicionar o componente parsys. NPR-30422: Hotfix do CQ-4274863
* Erro ContextHub durante a integração do AEM e do Campaign. NPR-30625: Hotfix do CQ-4250790
* O valor do parâmetro de solicitação resourceType é copiado no valor de um atributo de marca HTML entre aspas duplas. NPR-29832: Hotfix do CQ-4255365
* Uma atualização de página é necessária após os componentes serem copiados e colados de uma página para outra. NPR-29982: Hotfix do CQ-4256019
* Publicar/Desfazer a publicação de um alias de página não é suportado e deve ser removido. NPR-30062: Hotfix do CQ-4271249
* Aviso do ResourceResolver não fechado em ExperienceFragmentsReplicationListener que leva a problemas de estabilidade ao longo do tempo, forçando a reinicialização AEM instâncias. NPR-30416: Hotfix do CQ-4257521
* Os Fragmentos de experiência móveis referenciados em mais de 150 páginas não modificam o fragmentPath nas páginas em que são referenciados. NPR-30556: Hotfix do CQ-4274900
* Erro de análise ao abrir um Fragmento de conteúdo com caracteres em dólar (`$`) e chave aberta (`{`) uma após a outra. Hotfix do CQ-4270266
* VersionPreviewServlet está falhando em NullPointerException ao tentar exibir uma versão de um Fragmento de experiência na linha do tempo. NPR-30074: Hotfix do CQ-4271881
* Não é possível bloquear fragmentos de conteúdo por meio do recurso de check-in. NPR-29923: Hotfix do CQ-4258785
* Falha na verificação de assinatura no manipulador de autenticação SAML. NPR-30379: Solicitação de backport para GRANITE-26567

**Replicação**

* Sessão JCR / Resolvedor de recursos vaza durante a implementação do OAuth em cada replicação para o MAC / Brand Portal. NPR-30000: Hotfix do Granite-26196

**Sling**

* A ordem dos filhos afetados usando sobreposição e ordem antes está causando IndexOutOfBoundException. NPR-30408: Hotfix do Sling-8296 e Sling-7375
* InativeBundlesHealthCheck está lendo a configuração MissingPackagesHealthCheck assim que as configurações InativeBundlesHealthCheck são salvas. NPR-30084: Hotfix do CQ-4272644

**Commerce**

* Não é possível executar o blueprint do catálogo no console Sites. NPR-29829: Hotfix do CQ-4271461
* O ativo usado no produto não mostra nenhuma referência ao produto na seção &quot;Referências&quot; do ativo, nem o caminho do ativo é atualizado se o ativo for movido. NPR-30542: Hotfix do CQ-4270247

**Plataforma**

* O remetente de email padrão do AEM não pode enviar emails para um servidor SMTP remoto por TLS v1.2. NPR-30476: Hotfix do GRANITE-26605

**Communities**

* Grupos excluídos no autor não estão sincronizados com todos os editores. NPR-29987: Hotfix do CQ-4268738
* Os usuários excluídos removidos do campo Administradores da comunidade não estão sincronizados com o grupo Associação. NPR-30389: Hotfix do CQ-4274339
* A parte Usuários do grupo de administradores não tem links rápidos para o grupo. NPR-30546: Hotfix do CQ-4275579
* A atualização de qualquer grupo da Comunidade recém-criado e existente substitui a propriedade no jcr: nó de conteúdo e altera o nome para o título da primeira página. NPR-30109: Hotfix do CQ-4273719
* A pesquisa rápida e a pesquisa por localização e endereço não funcionam quando a comunidade está configurada para trabalhar com o Provedor de Recursos de Armazenamento de Banco de Dados (DSRP). NPR-26737: Hotfix do CQ-4258493

**Tradução**

* A execução automática da Tradução não funciona. NPR-30499: Hotfix do CQ-4276288
* O usuário pode criar uma cópia de idioma no caminho do conteúdo restrito a somente leitura. NPR-29937: Hotfix do CQ-4270708
* Problema de tradução - somente alguns componentes são traduzidos pela tradução automática. NPR-30079: Hotfix do CQ-4273764

**Integração**

* O conteúdo personalizado não é exibido corretamente na instância de publicação até a reinicialização da instância. NPR-30421: Hotfix do CQ-4273706

**Projetos**

* Os valores dam:folderThumbnailPaths não são atualizados e exibem miniaturas antigas mesmo depois de excluir os ativos dentro da pasta. NPR-30424: Hotfix do CQ-4273667

**Consoles da interface do usuário**

* Script entre sites (XSS) nas propriedades da página Sites na guia de miniatura. NPR-30048: Hotfix do Granite-26200

**UI-Foundation**

* Adição de suporte para rastrear estados dinâmicos da interface do usuário no evento de rastreamento na API de base. NPR-30742, GRANITE-26322: Hotfix do GRANITE-26036

**Forms**

>[!NOTE]
>
>O AEM Service Pack não inclui correções para o AEM Forms. Eles são entregues usando um pacote complementar separado do Forms. Além disso, é lançado um instalador cumulativo que inclui correções para o AEM Forms no JEE. Para obter mais informações, consulte [Instalar o pacote complementar do AEM Forms](#install-aem-forms-add-on-package) e [Instalar o instalador do AEM Forms JEE](#install-aem-forms-jee-installer).

**Pacote complementar do Forms**

**Formulários adaptáveis**

* Arquivo .css vazio leva mais tempo para ser buscado do editor, causando problemas de desempenho. NPR-30558: Hotfix do CQ-4274399
* Os Forms que são modificados após a publicação não são publicados novamente ao publicar o site. NPR-30411: Hotfix do CQ-4236566

**Forms - Integração de backend**

* Um erro é lançado ao criar o Modelo de dados de formulário com a Linguagem de definição de serviço da Web (WSDL). NPR-30388: Hotfix do CQ-4272921

**Forms - Gerenciamento de correspondência**

* Caracteres especiais, como menor que (&lt;), maior que (>) e E comercial (&amp;), são codificados na interface do usuário do agente. NPR-30410: Hotfix do CQ-4273887
* Ao acionar fragmento de texto contendo valores do Dicionário de dados, a interface do usuário do agente fica sem resposta. NPR-30098, NPR-30083: Hotfix do CQ-4272204
* Criar interface de usuário de correspondência (CCR UI) falha intermitentemente com a variável de erro (objeto). NPR-29983: Hotfix do CQ-4273874
* O recarregamento do rascunho da carta falha com uma exceção quando a descrição dos Fragmentos do documento contém caracteres especiais como menos que (&lt;), maior que (>) e e comercial (&amp;) nas propriedades. NPR-29930: Hotfix do CQ-4252762

**Formulários HTML5**

* Ao usar o NonVisual Desktop Access no modo Procurar para ler um formulário HTML5, o navegador Chrome lê &quot;gráfico&quot; antes de cada Gráfico de vetor escalonável (SVG) no design do formulário. NPR-30450: Hotfix do CQ-4274732

**Instalador do Forms JEE**

**Forms - Foundation JEE**

* Adicionar ou editar uma conexão de Serviço da Web chamando serviços da Web AEM o Forms Workbench gera um erro: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix do CQ-4273217

**Forms - Serviços de documentos**

* Erro de ausência no rótulo PDF/A na comprovação do Acrobat. NPR-30594: Hotfix do CQ-4276032
* Os vínculos de dados de caractere único no PDF fazem com que as extensões de Reader falhem com um erro &quot;java.lang.StringIndexOutOfBoundsException: Índice de sequências fora do intervalo: 1&quot;. NPR-30128: Hotfix do CQ-4273878
* Quando um teste de carregamento é executado no serviço de HTML para PDF, ele falha com um erro e as configurações de tipo de arquivo são removidas do servidor AEM Forms. NPR-30085: Hotfix do CQ-4272631
* O nivelamento de um PDF com Adobe Acrobat 9.1 (XFA versão 3.0) não retém o estado do PDF form: Os elementos invisíveis no formulário são definidos novamente como um estado visível. NPR-29978: Hotfix do CQ-4270888

**Forms - Segurança de documentos**

* A aplicação de uma assinatura com carimbo de data e hora falha com erro: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: erro de chamada. NPR-30696, NPR-30537: Hotfix do CQ-4273778
* O Configuration Manager não insere cadeias de caracteres japonesas para colunas de tabela localizadas. NPR-30496: Hotfix do CQ-4274868

**Serviço PDFG**

* Erro de conexão ao tentar converter documento do Word em PDF no Windows Server 2016. NPR-30597: Hotfix do CQ-4275652
* Exceção de permissão negada ao tentar usar o serviço de back-end HTML para PDF por meio da biblioteca &quot;phantomjs&quot;. NPR-30456: Hotfix do CQ-4258077
* maxReuseCount para serviço HTML para PDF não é mostrado no Console de gerenciamento do JBoss. NPR-30303, NPR-30135: Hotfix do CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

O AEM 6.4.5.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.5.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.5.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.13.
* Adição do tempo limite de soquete e do tempo limite de conexão nos agentes de replicação do Brand Portal.
* Aprimoramentos do Omnisearch - Aumento do limite de paginação do resultado de pesquisa para 100 páginas.
* Desabilitado `AssetDownloadServlet` Componente OSGi por padrão em instâncias de publicação AEM. Para obter mais informações, consulte [Baixar ativos do AEM](/help/assets/download-assets-from-aem.md).
* Ativação do suporte Multi-Site Manager no Assets. Para obter mais informações, consulte [Reutilizar ativos usando o MSM para Assets](/help/assets/reuse-assets-using-msm.md).

**Ativos**

* Os ativos com um apóstrofo no nome do arquivo não são sincronizados com o Dynamic Media. NPR-29538: Hotfix do CQ-4270592
* Atualização da interface DAM DMGGateway para oferecer suporte a várias peças S3. NPR-29740: Hotfix do CQ-4226303
* A caixa de diálogo de download de ativos exibe um tamanho de arquivo incorreto ao baixar representações de um vídeo no Dynamic Media. NPR-29642: Hotfix do CQ-4246202
* Os ativos ficam inutilizáveis depois que o Day CQ DAM Mime Type Service aplica texto para m3u8. NPR-29276: Hotfix do CQ-4264052
* O ajuste de referência do ativo não salva a sessão se qualquer um dos ativos movidos/renomeados fizer parte das coleções de Recurso do Sling. NPR-29143: Hotfix do /CQ-4252605
* Não é possível rastrear ou localizar ativos pesquisando os valores de metadados. NPR-29141: Hotfix do CQ-4260215
* Ao usar o filtro de pesquisa para salvar uma coleção inteligente, a ação de clique no painel não mantém o foco. NPR-29000: Hotfix do CQ-4240323
* Mover uma pasta permite a criação de uma pasta com nomes de letras maiúsculas ou minúsculas misturadas. NPR-28945: Hotfix do CQ-4265234
* Resultados em branco são exibidos no Omnisearch se o nome da coleção tiver espaço. NPR-29001: Hotfix do CQ-4236729
* Renomear um arquivo usando alguns caracteres especiais não suportados, como o E comercial (&amp;), cria uma pasta inválida. NPR-29196: Hotfix do CQ-4265037
* A funcionalidade Arquivo de extração de DAM para arquivo zip está corrompida. NPR-29187: Hotfix do CQ-4254421
* A importação de metadados deve permitir a importação de metadados sem registrar namespaces. NPR-29425, NPR-28132: Hotfix do CQ-4269445
* Salvar alterações de metadados não funciona para ativos cujo nome contém um caractere de aspas. NPR-29395: Hotfix do CQ-4254305
* Não é possível mover um ativo DAM se o nome do arquivo contiver espaço em branco. NPR-29270: Hotfix do CQ-4266403
* Não é possível baixar arquivos ZIP compactados com o algoritmo Deflate64. NPR-29225: Hotfix do CQ-4253995
* As miniaturas de ativos são exibidas lentamente ao abrir uma pasta que contém ativos com muitas versões. NPR-29833: Hotfix do CQ-4271629
* Não é possível inserir a coleção realçada se a tecla Enter for pressionada depois de selecionar a coleção. NPR-29723: Hotfix do CQ-4261607
* Ataque de script entre sites (XSS) por meio da janela de alerta restrito. NPR-29671: Hotfix do CQ-4270133
* A adição de relações a ativos está falhando para usuários sem permissões de exclusão. NPR-29640: Hotfix do CQ-4269196
* Depois de adicionar o título do ativo na página de propriedades, quando o usuário tentar fechar a página, AEM abre a página de propriedades novamente. NPR-29628: Hotfix do CQ-4264929
* Criar um grande número de relações no ativo resulta em um erro. NPR-28779: Hotfix do CQ-4250708
* A assimilação de ativos é lenta no modo de execução do Scene7 Connect. NPR-28658: Hotfix do CQ-4263007
* Erro Uncaught TypeError: Não é possível ler a propriedade &#39;split&#39; de undefined é exibida ao tentar visualizar os resultados da pesquisa. NPR-28803: Hotfix do CQ-4248371
* A replicação do AEM para o Brand Portal fica paralisada por longos períodos. NPR-28914: Hotfix do CQ-4254932
* Mover ativos no DAM não resulta em uma mudança semelhante no Scene7. NPR-28957: Hotfix do CQ-4264974
* As atualizações de metadados não são passadas para o IPS se o campo de metadados for atualizado em AEM. NPR-28961: Hotfix do CQ-4255393
* VersioningTimelineEventProvider deve fornecer a versão raiz juntamente com o comentário da versão. Hotfix do GRANITE-26063
* A inserção de dados leva à execução do código no lado do servidor. Hotfix do CQ-4270246
* Ativação do suporte Multi-Site Manager no Assets. Hotfix do CQ-4271453, CQ-4268621, CQ-4257491
* A interface do AEM deve exibir uma entrada adicional para a versão atual do ativo no histórico da linha do tempo, exibindo o comentário de check-in mais recente do Adobe Asset Link. Hotfix do CQ-4262864
* O vídeo de exemplo não é carregado ao criar ou editar um MixedMediaSet. Hotfix do CQ-4244889
* Desativar as permissões para excluir conteúdo no AEM impede que o usuário publique no Brand Portal. Hotfix do CQ-4270426
* Problemas relacionados ao limite de query com relatórios de Ativo após a atualização para o AEM 6.4.3. NPR-28588: Hotfix do CQ-4262022, CQ-4260697
* A funcionalidade de download aproveita a AEM Assets por meio do assetdownload servlet, permitindo que usuários anônimos baixem todos os ativos. NPR-27315, Hotfix do CQ-4254732

**Sites**

* O nome da tag de reclamação do JCR deve ser preenchido automaticamente com base no título da tag. NPR-28990: Hotfix do CQ-4199411
* O botão Cancelar herança não está visível em alguns dos campos adicionados nas propriedades da página. NPR-29079: Hotfix do CQ-4265686
* A ação de visualização de implantação não deve tentar recriar a live copy ou exibi-la na lista de páginas de implantação. NPR-29151: Hotfix do CQ-4266213
* (Editor de modelo) Regressão de política de estilo no modo de estrutura. NPR-28981: Hotfix do CQ-4264400
* As cópias dinâmicas aninhadas mostram entradas duplicadas durante a implantação. NPR-29300: Hotfix do CQ-4268664
* Falha na publicação de uma Live Copy que contém um componente do Importador de design ao recuperar referências para a página selecionada. NPR-28944: Hotfix do CQ-4265014
* A CoralUI, quando usada com Multifield, armazena o fileReferenceParameter no nível de componente em vez de no nível de vários campos. NPR-29536: Hotfix do CQ-4266129
* A referência de design não é replicada na publicação após cancelar a herança no Importador de design. NPR-29648, NPR-29721: Hotfix do CQ-4269270, CQ-4271087
* O campo de caminho no Editor de Rich Text é aberto no caminho raiz independentemente do caminho especificado para pesquisa. NPR-29483: Hotfix do CQ-4268997
* (IE11) Copie e cole o conteúdo do HTML em um componente RTE com defaultPasteMode = o texto simples não cola o conteúdo como um texto simples. NPR-29432, NPR-29171: Hotfix do GRANITE-24941
* A verificação ortográfica do Editor de Rich Text não funciona mais em outros idiomas. NPR-29506: Hotfix do CQ-4264990
* Scripts entre sites (XSS) na página Campanha. NPR-29614: Hotfix do CQ-4269322
* Minimizar o Editor de Rich Text da tela cheia enquanto no modo de edição de origem leva a perda de conteúdo. NPR-29574: Hotfix do CQ-4260584
* (Interface do usuário clássica) Navegar até a última guia nem sempre é possível quando existe um grande número de tags. NPR-29544: Hotfix do CQ-4264548
* (Interface do usuário clássica) O menu de navegação do Admin Console desaparece e a página não é carregada completamente. NPR-29571: Hotfix do CQ-4264585
* O alerta de erro é gerado ao adicionar componentes à página WCM quando a minificação está ativa na instância. NPR-29396: Hotfix do CQ-4266196
* Um problema com a herança dos nós do Sistema de estilos do pai. NPR-29296: Hotfix do CQ-4266041
* A página restaurada com o Timewarp deve se referir à imagem correta no momento do controle de versão.  NPR-29431: Hotfix do CQ-4262638
* Página em branco com erros de Javascript no editor após instalar a versão mais recente do instantâneo 6.4.5. NPR-29475: Hotfix do CQ-4266196
* Ao adicionar um componente a um parsys, a propriedade de lista de componentes de design não é respeitada e é resolvida para um nome de nó de modelo diferente com uma estrutura parsys semelhante. NPR-29509: Hotfix do CQ-4269044
* a zona cq:dropTargets cobre todo o componente em vez do tamanho da imagem, dificultando o direcionamento com componentes incorporados. NPR-29738: Hotfix do CQ-4268912
* O componente de imagem não chama o ouvinte &quot;pós-edição&quot; depois que o editor de imagem no local é usado. NPR-29616 Hotfix do CQ-4268065
* Um problema ao configurar a publicação social no Facebook. NPR-29212: Hotfix do CQ-4266630
* Ao promover inicializações de páginas modificadas, as modificações nas ramificações de origem e de inicialização são consideradas. NPR-29308: Hotfix do CQ-4266746
* A miniatura renderizada no Fragmento do conteúdo mostra a representação interna do calendário do campo Data e hora. NPR-29531: Hotfix do CQ-4269362
* Não é possível adicionar uma tag em massa a páginas com tags diferentes existentes. NPR-28729: Hotfix do CQ-4262922
* O ícone Ativação agendada não é exibido no administrador do site. NPR-28725: Hotfix do CQ-4263917

**Replicação**

* Vulnerabilidade de divulgação de informações confidenciais no componente Agente de replicação. NPR-29612, NPR-24951: Hotfix do GRANITE-25070
* Os dados fornecidos pelo usuário não são escapados na saída no componente cq/Replication/components/agent, resultando em uma vulnerabilidade de script entre sites (XSS). Hotfix do CQ-4266263

**Fragmentos de experiência**

* Não é possível exportar os Fragmentos de experiência para o destino quando a imagem inteligente é usada. Hotfix do CQ-4269606

**Social - Relatórios**

* AEM relatórios da Comunidade não são exibidos AEM instância do autor. Hotfix do CQ-4266294

**Plataforma**

* Scripts entre sites (XSS) no gerenciador de pacotes ao instalar um pacote. NPR-29734, NPR-29713, NPR-29630: Hotfix do GRANITE-26161, GRANITE-
* Vários scripts armazenados e refletidos entre sites (XSS) no CRXDE Lite. NPR-29634: Hotfix do GRANITE-26049
* A funcionalidade de logon do Compartilhamento de pacotes usa a solicitação do GET em vez da solicitação do POST, fazendo com que a senha fique visível na guia Rede. NPR-29631: Hotfix do GRANITE-26048

**Felix**

* Script entre sites (XSS) observado no console do sistema. A página é carregada e o pop-up aparece quando o mouse é focalizado sobre o campo de texto. NPR-29853, NPR-29633: Hotfix do GRANITE-26188, GRANITE-26050

**Granite**

* A Configuração do Apache Sling Logging Logger não filtra o script inserido.  NPR-29775: Hotfix do GRANITE-26051

**Comunidades**

* Os grupos excluídos no autor devem ser removidos das instâncias de publicação. NPR-28933: Hotfix do CQ-4264645
* O segredo do aplicativo deve ser protegido com um campo de senha, não para ser exibido em texto simples para ferramentas de conexão social. NPR-29728: Hotfix do CQ-4270480
* Os visitantes e membros, sem privilégios de moderador, podem ver publicações não aprovadas/pendentes ao colar o URL. NPR-29726: Hotfix do CQ-4271124, CQ-4271441
* É observado um tempo de resposta alto de 40 a 50 segundos no logon do usuário na Comunidade. NPR-29678: Hotfix do CQ-4269444

**Tradução**

* Os usuários sem acesso ao recurso de tradução na navegação não devem poder acessar suas subpáginas. NPR-29644: Hotfix do CQ-4269979
* Permissões de usuário não mantidas como assistente permite a criação da cópia de tradução em um local somente leitura. NPR-29375: Hotfix do CQ-4265877

**IU - Foundation**

* Aumento do limite de paginação do resultado da pesquisa para 100 páginas para exibição de cartão e 200 para exibição de lista. NPR-29332: Hotfix do GRANITE-24644
* Devido ao carregamento lento de tags, nada é exibido na página da coleção. NPR-29267: Hotfix do GRANITE-24902
* Alterar o limite de paginação para 100 em vez de 40 aciona uma carga preguiçosa extra sem solicitação de paginação. NPR-29246: Hotfix do GRANITE-25027
* AEM campo de senha granite não está sendo preenchido após a criptografia. NPR-29245: Hotfix do GRANITE-24908

**Integração**

* Uma mensagem de exceção é exibida ao tentar editar e salvar a configuração de inicialização AEM. NPR-29086: Hotfix do CQ-4266153
* As credenciais do BrightEdge falham com erro de conexão.  NPR-29167: Hotfix do CQ-4265872
* A caixa de seleção herdada de que aparece no nível raiz em Configurações de Cloud Service deve ser removida. NPR-27856: Hotfix do CQ-4259676

**Sling**

* O tempo limite da conexão HTTP não está sendo lido nas configurações. NPR-29264: Hotfix do SLING-7902
* O write-back do instalador JCR faz com que a configuração OSGi use um formato inválido e bloqueie a reimplantação. NPR-29027: Hotfix do CQ-4264694

**Projetos**

* Os usuários não podem concluir o fluxo de trabalho do projeto. NPR-29621: Hotfix do CQ-4258791
* A lista Fluxo de trabalho do projeto mostra linhas vazias além de 40 fluxos de trabalho. NPR-28739: Hotfix do CQ-4264005
* A escolha da opção Representação dinâmica no Brand Portal baixa um arquivo .zip vazio. NPR-29420: Hotfix do CQ-4268826
* Publicar ativos da pasta /content/dam/mac do autor de AEM no Brand Portal não funciona. NPR-29820: Hotfix do CQ-4271118
* A pontuação no nome causa problemas com o botão de publicação. NPR-29573: Hotfix do CQ-4269317
* Não é possível criar a cópia do idioma do ativo por meio do painel de referência. Hotfix do CQ-4269535

**Fluxo de trabalho**

* Atualizar da versão 6.4.2 para a 6.4.4 quebra o campo do seletor de calendário do participante na caixa de diálogo. NPR-29727: Hotfix do CQ-4270423

**WCM - Interface do usuário do administrador**

* Abrir a guia de permissões na implementação do Coral2 não mostra os botões. Hotfix do CQ-4269419

**WCM - MSM**

* A exclusão de um nó secundário na live copy deve desanexar o liveRelationship. Hotfix do CQ-4270395
* A atualização para o AEM 6.4.3 faz com que o Multi-Site Manager leve muito tempo para ser iniciado. Hotfix do CQ-4271410

**Vulnerabilidade**

* A estrutura de proteção do CSRF não está funcionando com formulários fundamentais do AEM. NPR-28612: Hotfix do GRANITE-22231

**WCM - Editor de páginas**

* Script entre sites (XSS) refletido ao usar um seletor inválido. Hotfix do CQ-4270397

**Forms**

Os principais destaques dos AEM Forms 6.4.5.0 são:

**Pacote complementar do Forms**

**Formulários adaptáveis**

* (Interface do usuário de toque) A opção Iniciar fluxo de trabalho não abre a caixa de diálogo para configuração. NPR-29521: Hotfix do CQ-4269050

**Forms - Integração de backend**

* Ativação de suporte para o Ative Diretory Federation Services (ADFS) v3.0 para integração local do Microsoft Dynamics. NPR-30003, NPR-29484: Hotfix do CQ-4270586
* O serviço de pré-preenchimento falha devido ao tempo de resposta prolongado do módulo de Integração de dados da AEM Forms. NPR-28997: Hotfix do CQ-4265988
* A solicitação SOAP Webservice está malformada no AEM Forms. NPR-29013: Hotfix do CQ-4265443
* Nenhuma mensagem de erro é exibida durante o teste do serviço SOAP, no caso de um valor de data incorreto. Hotfix do CQ-4265445

**Forms - Comunicação interativa e Forms - Gerenciamento de correspondência**

* Criar interface de usuário de correspondência (CCR UI) não lida com um número flutuante.  NPR-29210: Hotfix do CQ-4254201
* A dica de ferramenta definida em uma variável não está visível na interface Criar correspondência (CCR UI). NPR-29739: Hotfix do CQ-4250533
* Não é possível copiar ou colar do Omnisearch em letras. NPR-29808: Hotfix do CQ-4270783

**Formulários HTML5**

* Quando um espaço é adicionado dentro do texto, o campo de texto não permite preencher até o fim. NPR-28844: Hotfix do CQ-4260239

**Instalador do Forms JEE**

**Forms - Foundation JEE**

* O componente de serviço da Web no AEM Forms Workbench não pode invocar um serviço da Web, que requer autenticação SSL bidirecional. NPR-29485: Hotfix do CQ-4246794
* O gerenciador de configuração JEE da AEM Forms não funciona com várias placas de NIC. NPR-29236: Hotfix do CQ-4268598
* AEM erro de inicialização proveniente do GemFire: java.lang.IllegalStateException: Somente uma conexão AdminDistributedSystem pode ser feita de uma só vez. NPR-29524: Hotfix do CQ-4266295
* NoClassDefFoundError devido à incompatibilidade da versão do jar. NPR-28834: Hotfix do NPR-28834

**Forms - Serviços de documentos**

* Arquivo PDF/A inválido é reportado como PDF/A válido usando a operação isPDFA. NPR-29076: Hotfix do CQ-4261541
* PDF falha na conversão para PDF/A-1b com o campo Formulário que não tem dict de aparência. NPR-29534: Hotfix do CQ-4269618
* A conversão de PDF/A do PDF produzido com o Serviço de saída não passa a validação com o Acrobat DC. NPR-29647: Hotfix do CQ-4270448
* O pacote POI do Apache falha com uma exceção. NPR-27861, NPR-28048: Hotfix do CQ-4245898, CQ-4244778

**Forms - Designer**

* Adição de suporte PDF/UA a formulários XML da Arquitetura Forms (XFA) gerados com o Designer e o Serviço de Saída. NPR-23022

**Forms - Fluxo de trabalho**

* Os envios do espaço de trabalho falham com o caractere Umlaut. NPR-29087: Hotfix do CQ-4263172

**Feature Packs incluídos**

**Ativos**

* Ativação do suporte Multi-Site Manager no Assets. Para obter mais informações, consulte [Reutilizar ativos usando o MSM para Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix do CQ-4259922

**Pacotes OSGi e pacotes de conteúdo incluídos**

O texto seguinte documenta a lista de pacotes OSGi e os pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.5.0

[Obter arquivo](assets/6.4.5.0_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.5.0

[Obter arquivo](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

O AEM 6.4.4.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**

Ele também é cumulativo, o que significa que a versão 6.4.4.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.4.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.11.
* Adição de suporte para armazenar a versão do serviço em cache para evitar solicitações HTTP frequentes de versão do serviço.
* Adição de suporte para exclusão de tags automáticas.
* Implementação da rolagem infinita para o assistente de catálogo.
* Capacidade de restringir permissões de acordo com sites da comunidade.
* Correções de desempenho (cache, execução assíncrona, lista de exclusão) para a Verificação de integridade do conteúdo do Sling Granite.
* Adição do botão assetpicker à caixa de diálogo pagethumbnail.
* Nova propriedade adicionada para permitir o posicionamento da dica de ferramenta nos campos.
* Aprimoramento do suporte do ColorPicker no Multifield.
* Foi adicionada uma verificação para ignorar valores vazios para vários campos de entrada de número nas bibliotecas de clientes do Fragmento de conteúdo.
* Ativação do suporte para a API de texto do Microsoft Translator v3.

**Ativos**

* Migrar a integração de ACP e Stock para o AEM 6.4.4.0 NPR-27632
* Publicar mais tarde uma pasta de ativos vazia com subpastas faz com que as subpastas desapareçam. NPR-27558: Hotfix do CQ-4254701
* A adição da propriedade Single non-namespaced String\[\] causa o write-back de XMP incompleto. NPR-26805: Hotfix do CQ-4254142
* Depois de rasterizar o pdf de entrada, a saída produzida tem imagens ausentes. NPR-27929: Hotfix do CTG-4150481
* O Assistente para Mover Ativo está mostrando uma contagem incorreta de páginas de Referência para páginas publicadas. NPR-27833: Hotfix do CQ-4258014
* O AssetPicker pesquisa apenas a primeira tag para filtrar o resultado ao filtrar com tags. NPR-27778: Hotfix do CQ-4257705
* AEM manipulador de PDF OTB fica preso no PDF de processamento com caracteres estrangeiros. NPR-28778: Hotfix do CQ-4254234
* Quando um arquivo CSV tem um valor que é separado por vírgula em uma única coluna, AEM editor CSV não esvazia a vírgula e a trata como uma coluna separada. NPR-28801: Hotfix do CQ-4261694
* Problema com o Editor de esquema de metadados ao usar o Navegador de caminho para selecionar dados. NPR-28674: Hotfix do CQ-4263005
* Muitos ativos são processados no Serviço de conteúdo inteligente, resultando em um período de tempo enorme para concluir o processo de marcação periódica. NPR-28640: Hotfix do CQ-4262661, CQ-4262644, CQ-4263234
* As ações da área de trabalho não funcionam para os resultados do Omnisearch de `aem/start.html` página. NPR-27242: Hotfix do CQ-4248176
* A API de ativos não permite o upload de arquivos > 2 GB que causam falha de upload. NPR-27629: Hotfix do Granite-23590
* Os metadados não são salvos no ativo baixado na primeira tentativa caso o Dynamic Media esteja habilitado na instância. NPR-28233: Hotfix do CQ-4260759
* O resolvedor de serviços não está fechado na configuração de SiteCatalyst. NPR-28015: Hotfix do CQ-4259397
* Mover ativos no DAM não resulta em uma movimentação semelhante no Scene7 (configuração p2p). NPR-28313: Hotfix do CQ-4261091

**Sites**

* (Interface clássica) Uma fração das cópias em tempo real é exibida na lista de implementação. NPR-28598, NPR-28574: Hotfix do CQ-4263410
* O LiveRelationshipManagerImpl lança exceções quando cq:principal está vazio ou é inválido. NPR-28590: Hotfix do CQ-4263115
* O fluxo de trabalho &quot;Solicitação de exclusão&quot; pronto para uso não exclui as páginas corretamente. NPR-28668: Hotfix do CQ-4263195
* A interface do usuário de status do relacionamento não mostra os valores adequados de ano ou carimbo de data e hora para os campos coral-datepicker relacionados. NPR-28666: Hotfix do CQ-4263661
* Script entre sites (XSS) no SuggestionHandler para 6.4. NPR-28693: Hotfix do CQ-4253821
* Mover a pasta de siteadmin termina sem memória e torna AEM indisponível. NPR-28346: Hotfix do CQ-4261398
* As configurações de implantação do MSM LiveCopy são perdidas após a atualização. NPR-28311: Hotfix do CQ-4258705
* Não é possível rolar além de 40 configurações do blueprint. NPR-27640: Hotfix do CQ-4239166
* O uso de SyntheticResource como referência aciona uma exceção de ponteiro nulo e bloqueia o movimento das páginas.  NPR-27576: Hotfix do CQ-4258262
* O PushOnModify não funciona na exclusão na instância atualizada 6.1 para 6.4. NPR-28108: Hotfix do CQ-4259833
* (Interface clássica) O botão Cancelar herança está ausente e o componente pode ser editado em uma página de Live Copy. NPR-28256: Hotfix do CQ-4260161
* OakState0001: Conflitos não resolvidos na implantação. NPR-27982: Hotfix do CQ-4259548
* Ao copiar/colar uma estrutura contendo referências SyntheticResource, o processo termina com um erro 500. NPR-27709: Hotfix do CQ-4259179
* Não é possível encerrar os fluxos de trabalho em execução quando as cargas são ativadas. NPR-27672: Hotfix do CQ-4258520
* A implantação mostra caminhos de implantação duplicados após a atualização da versão 6.1 para a 6.4. NPR-27845: Hotfix do CQ-4259487
* Integre o modal do dam assetpicker no componente de miniatura da página. NPR-28131: Hotfix do CQ-108042
* (Interface clássica) Não é possível abrir caixas de diálogo com o widget Tags. NPR-28575: Hotfix do CQ-4262680
* O upload de arquivo de vários campos não mostra a área de soltar. NPR-28676: Hotfix do CQ-4263516
* Erro &quot;Valor inválido do seletor de recursão&quot; ao migrar um componente do AEM 6.0 para o AEM 6.2. NPR-28609: Hotfix do CQ-4241258
* O Editor de Rich Text na caixa de diálogo está oscilando quando o posicionamento de um plug-in é superior à área do texto, bloqueando assim qualquer criação adicional. NPR-27579: Hotfix do CQ-4257440
* (Interface de usuário clássica) cq:action editannotate não funciona. NPR-28232: Hotfix do CQ-4257703
* A remoção de tags do painel de pesquisa de ativos do filtro de tags do editor de páginas não atualiza a lista corretamente. NPR-27983: Hotfix do CQ-4245567
* Se os valores do número de vários campos estiverem vazios, clicar em Salvar resultará em um prompt de carregamento infinito sem nunca concluir.  NPR-28400, NPR-28393: Hotfix do CQ-4244058, CQ-4244349
* Com a permissão apenas leitura, os usuários/grupos não podem selecionar um XF e não têm opção para exibir o XF e suas propriedades da página. NPR-28341: Hotfix do CQ-4260412
* Os dados JSON recebidos do Target têm vários caracteres de escape que causam a quebra da página do aplicativo. NPR-28318: Hotfix do CQ-4252043
* Não é possível editar nenhum componente após a instalação do AEM 6.4.3. NPR-28125: Hotfix do CQ-4261216
* A exclusão de todas as tags de um campo de tag não é persistente para um fragmento de conteúdo estruturado. NPR-28133: Hotfix do CQ-4247241
* Ao editar uma propriedade do Fragmento de conteúdo &quot;jcr:lastmodifiedby&quot; e &quot;jcr:lastmodified&quot;, os valores são atualizados sem que o usuário faça alterações. NPR-27847: Hotfix do CQ-4257138
* O controle de versão de Fragmentos de conteúdo compara aprimoramentos de diferenças no AEM 6.4. NPR-27764
* Se não houver cq:allowedTemplates definido em /content/experience-fragments e allowedPaths for usado no modelo do Experience Fragement, um erro será lançado quando o Experience Fragement for movido/copiado. NPR-27487: Hotfix do CQ-4257489
* O botão Criar é exibido ao atualizar para o novo usuário. NPR-27335: Hotfix do CQ-4255360
* Ao tentar mover uma página publicada, a contagem de &quot;Páginas de referência&quot; exibida na primeira página do assistente &quot;Mover página&quot; está incorreta. NPR-28111: Hotfix do CQ-4259663
* (Interface do usuário de toque) O painel Referências não mostra os links recebidos. NPR-28529: Hotfix do CQ-4262306
* Não é possível editar qualquer componente e propriedades da página após a instalação do AEM 6.4.3. NPR-27998: Hotfix do CQ-4261216, CQ-4260441
* Migração do contexthub para jquery 3. NPR-28397: Hotfix do GRANITE-19902

**Comércio**

* Não é possível selecionar o catálogo se houver mais de 20 catálogos em uma pasta. NPR-27649: Hotfix do CQ-4258119
* Os assistentes de comércio e as exibições de propriedades estão quebrados devido à falta de header.referer. Hotfix do CQ-4261122

**Campaign - Direcionamento**

* com.day.cq.personalization.impl.TeaserResourceEventHandler entra em um loop infinito e causa atualizações para nós em instâncias de publicação. Hotfix do CQ-4263096

**Replicação**

* Erro ao criar o conteúdo de replicação com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix do CQ-4261401
* Vazamento de sessão quando a ID do agente do usuário está definida como administrador no agente de replicação. NPR-28220: Hotfix do CQ-4255517

**DAM - Creative Cloud**

* Importe a API HTTP para localizar imagens semelhantes no AEM Assets. Hotfix do CQ-4254091
* Aprimore a API ACP para permitir que os resultados de uma consulta sejam restritos aos membros de uma coleção. Hotfix do CQ-4258708

**DAM - Formatos**

* Depois que a exportação de metadados é acionada, a página é redirecionada para uma página 404. Hotfix do CQ-4262447

**DAM - Geral**

* (Adobe Stock Integration) O modal de erros do servidor é exibido com um erro Oauth no arquivo error.log. Hotfix do CQ-4260406
* A integração do Adobe Stock não funciona se a 6.4.4 for aplicada à 6.4.3. Hotfix do CQ-4266009
* O Link para o Modelo CF está ausente mesmo após a aplicação do patch SP3. Hotfix do CQ-4259029

**Plataforma**

* (Interface clássica) O botão de edição não está disponível no componente de relatório básico após a atualização para a versão 6.4.2. NPR-28560: Hotfix do CQ-4262825
* Ao usar uma consulta combinando property.operation=like e property.depth, ela acaba em um InvalidQueryException. NPR-28570: Hotfix do CQ-4262652
* Erro interno do servidor quando o nó de idioma recém-adicionado é removido do nó de idioma sobreposto. NPR-28661: Hotfix do CQ-4239194
* Exceção de ponteiro nulo em stderr.log no thread sling-oak-1 em inicializações aleatórias. NPR-28665: Hotfix do CQ-4237845

**Felix**

* webconsole.plugins.memoryusage causa um impasse na atualização. NPR-27895: Hotfix do GRANITE-20715

**Granite**

* A Verificação de Integridade do Acesso ao Conteúdo do Sling executa uma validação excessiva de /libs longa para o caminho de pesquisa do resolvedor de recursos personalizado. NPR-28113: Hotfix do GRANITE-23529

**Gerenciamento de fragmentos de conteúdo**

* Melhorias de usabilidade e paridade de recursos com Ativos para fragmentos de conteúdo. Hotfix do CQ-4253883

**Comunidades**

* Atualize o bootstrap vulnerável para 3.4 e as bibliotecas do ckeditor para 4.5.11. NPR-28490: Hotfix do CQ-4257511
* O cancelamento dos modos de edição não restaura o anexo excluído. NPR-27902: Hotfix do CQ-4255150
* A composição em nome da caixa só deve ser visível para os membros privilegiados. NPR-27900: Hotfix do CQ-4251235
* Adicione rep:cache nos nós ignoráveis no Ouvinte de sincronização de usuário do AEM Communities nas instâncias de publicação. NPR-27842: Hotfix do CQ-4247234
* A caixa de pesquisa está mostrando o caractere de escape no nível da interface do usuário. NPR-27838: Hotfix do CQ-4259757
* O erro é gerado ao procurar caracteres especiais como ( , +,? em quicksearch. NPR-28213: Hotfix do CQ-4260969
* Crie um grupo de &quot;administradores específicos da comunidade&quot; para que os usuários possam editar e criar o site da comunidade relevante. NPR-27731
* Foi adicionada uma lógica para o evento do teclado para abrir o vídeo. NPR-27726: Hotfix do CQ-4254026
* Ativação da navegação por teclado para componentes de ativação do AEM Communities em Publicar. NPR-27728: Hotfix do CQ-4254028
* Adição do aria-label à lista e ao botão de exibição de cartão. NPR-27727: Hotfix do CQ-4254027
* Lidar com sessões abertas do resolvedor de recursos no Social - Comunidades. NPR-27721: Hotfix do CQ-4258714

**Tradução**

* Forneça suporte para Microsoft Translator Text API v3. NPR-28366: Hotfix do CQ-4249755
* jcr:language &amp; cq:language não são atualizadas automaticamente no idioma traduzido. NPR-28338: Hotfix do CQ-4256046
* Referências cíclicas causam StackOverflowError ao criar cópia de idioma. NPR-27596: Hotfix do CQ-4255621
* Em um projeto de tradução em vários idiomas, clicar em salvar e fechar resultados em páginas subsequentes adicionadas ao projeto resulta na criação de novos projetos em vez de novos trabalhos de tradução serem criados no projeto existente. NPR-28219, NPR-28236: Hotfix do CQ-4261276, CQ-4260731
* Sequência de erro muito longa ao adicionar fragmento de conteúdo com dados em massa devido à limitação do número de caracteres permitidos. NPR-28722: Hotfix do CQ-4262362

**Social**

* O comentário publicado na próxima página é destacado em amarelo sempre que um novo comentário é publicado. Hotfix do CQ-4261359
* Não é possível excluir comentários no Conteúdo gerado pelo usuário usando a API. NPR-28075: Hotfix do CQ-4261135
* AbstractNotificationOperationService causa ClassCastException. Hotfix do CQ-4260456
* Remova a referência à Nuvem do modelo de referência de objeto do conteúdo compartilhável (SCORM) no reprodutor. Hotfix do CQ-4260779

**IU - Foundation**

* O recurso &quot;Cache de saída do sistema de arquivos&quot; integrado no Gerenciador de biblioteca do cliente do HTML interrompe o recurso &quot;debugClientLibs&quot; para scripts compilados, como arquivos LESS. NPR-27249: Hotfix do Granite-23313
* O número de ativos exibidos quando o modo de depuração é ativado é sempre 1 e muitos erros JS são lançados no console do navegador.  NPR-27575: Hotfix do GRANITE-23750
* Salvar e fechar nas propriedades da página não retorna à página correta AEM WAR com Tomcat. NPR-27566: Hotfix do GRANITE-23671

**Integração**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` entra em um loop infinito e atualiza os nós em instâncias de publicação. NPR-28561: Hotfix do CQ-4263096
* As cq :actions não são consideradas para um componente direcionado. NPR-27616: Hotfix do CQ-4257497
* O cancelamento da herança da Live Copy não funciona corretamente em contêineres direcionados. NPR-28129: Hotfix do CQ-4259813
* (Configurações do Cloud Service) A caixa de seleção &quot;herdado de&quot; que aparece no nível raiz deve ser removida. NPR-27856: Hotfix do CQ-4259676

**Sling**

* Atualização para a API de Modelos do Sling 1.3.8, Impl 1.4.10. NPR-27636: Hotfix do GRANITE-23537

**OAK - Persistência do segmento**

* SegmentBufferWriter não liberado após OnRC. NPR-27464

**Projetos**

* O projeto de tradução em vários idiomas não está criando várias tarefas de idioma para os usuários que não fazem parte do grupo de administradores. NPR-28508: Hotfix do CQ-4262023
* O ProjectTaskListServlet está vazando um ResourceResolver sempre que getTaskRenderers é chamado durante a inicialização do serviço. NPR-27590: Hotfix do CQ-4258011
* Se um diretório tiver mais subdiretórios do que o tamanho da página e a ordem for por data ou tamanho, um erro impedirá que se mova para além da primeira página. NPR-28867: Hotfix do CQ-4265039
* Correções de script entre sites (XSS) de backport em visualizadores DAM. NPR-28106: Hotfix do CQ-4253215
* Não é possível adicionar páginas ao projeto de tradução por administradores de projeto, pois o link para adicionar novas páginas ao projeto de tradução não está visível. Hotfix do CQ-4266334

**Fluxo de trabalho**

* Quando abrimos uma caixa de diálogo de item de trabalho completo na notificação de fluxo de trabalho que tem um campo Tag , clicar em uma marca cruzada adiciona uma propriedade Tag a ela. NPR-28304: Hotfix do CQ-4261321
* O botão Alternar seleção de usuário na caixa de diálogo Atribuir tarefa não está funcionando. NPR-28963: Hotfix do CQ-4264206

**Forms**

Os principais destaques dos AEM Forms 6.4.4.0 são:

* Adição de suporte para registrar APIs de segurança de documentos para assinatura e certificação como transações.

**Pacote complementar do Forms**

**Integração do Acrobat Sign**

* AEM 6.4 Forms Client SDK não contém o pacote adobesign-recipient. NPR-27735: Hotfix do CQ-4259372

**Formulários adaptáveis**

* Quando um formulário adaptável Wan é criado com um modelo em branco, os clientes não podem criar painéis filhos no painel raiz do formulário. NPR-28758: Hotfix do CQ-4264157
* Quando o valor do campo de ano do componente de data é 9999, o script de validação falha. NPR-28580: Hotfix do CQ-4262620
* Quando um formulário adaptável é criado com um modelo em branco, os clientes não podem criar painéis filhos no painel raiz do formulário. NPR-28758: Hotfix do CQ-4264157
* Não é possível definir valor entre os campos de fragmentos carregados lentamente de um formulário adaptável. NPR-27758: Hotfix do CQ-4259703
* O formulário adaptável não usa o Editor de Rich Text, mas carrega suas bibliotecas.  NPR-27759: Hotfix do CQ-4259193
* O redirecionamento para URL não está funcionando para formulários adaptáveis incorporados em uma página do AEM Sites. NPR-27620: Hotfix do CQ-4239287
* Não é possível definir valor entre os campos de fragmentos carregados lentamente de um formulário adaptável. NPR-28320: Hotfix do CQ-4262345
* O formulário adaptável não usa o Editor de Rich Text, mas carrega suas bibliotecas.  NPR-28001: Hotfix do CQ-4259703, CQ-4259193
* A assinatura de rabisco não funciona para o aplicativo AEM Forms em execução no Apple iOS 12.1. NPR-28497: Hotfix do CQ-4261765
* Enviar ação usando problemas de criação do &quot;Forms Workflow&quot; Classic no 6.4. Hotfix do CQ-4252740
* Erro ao manipular remoção de armazenamento de bloco e tmp. NPR-28806: Hotfix do CQ-4264441

**Forms - Gerenciamento de correspondência**

* Falha na interface do usuário do agente ao manter o tamanho original da imagem. NPR-28800: Hotfix do CQ-4259767
* Interface do usuário do CCR/agente: Rótulos dos campos de Data alternados na guia Dados. Hotfix do CQ-4255499

**Forms - Relatórios de transação**

* Adição de suporte para contar usando assinaturas digitais ou certificar um documento como transações faturáveis. NPR-28495: Hotfix do CQ-4260236
* Assinatura digital adicionada e Certificado para API faturável. Hotfix do CQ-4260236

**Gerenciamento Forms**

Adição de suporte para substituir o uso da biblioteca do cliente handlebars por sublinhado no assistente de revisão inicial do Forms Manager e no assistente de movimentação de ativos. NPR-27643: Hotfix do CQ-4246536.
Um pacote permanece no estado instalado após a instalação do pacote Forms Management na ramificação release/640. O hotfix do CQ-4265410 Forms enviado com anexos não está aparecendo no fluxo de trabalho com a ação de envio &quot;Invoke AEM Forms Workflow&quot; e habilitar envio de portal marcado . Hotfix do CQ-4263110

**Forms - Integração de backend**

* Não é possível fazer testes de pré/pós-processador e envio personalizado usando o SDK do cliente, Hotfix do CQ-4238469

**Instalador do Forms JEE**

**Forms - Segurança de documentos**

* Ao usar o serviço updatepolicy, ocorre o erro de objeto não pode ser transmitido. NPR-28751: Hotfix do CQ-4252287
* Falha no Build de Assinatura com a versão mais antiga do commons-pkg. Hotfix do CQ-4265535

**Forms - Foundation JEE**

* Quando o AEM Forms é instalado no IBM WebSphere, a criação de um Modelo de dados de formulário com base no SOAP falha. NPR-27923: Hotfix do CQ-4251134
* A ferramenta SRT do PDF Generator falha ao detectar a versão instalada do Adobe Acrobat. NPR-27971

**Forms - Designer**

* Algumas imagens JPEG em um modelo XDP não são renderizadas corretamente.  NPR-26702: Hotfix do LC-3917457

**Forms - Fluxo de trabalho**

* HTML5 O Forms com processo de envio padrão em an.lca não funciona no JBoss 7. NPR-28675: Hotfix do CQ-4243928
* Não é possível enviar PDF forms no HTML Workspace. NPR-28058: Hotfix do CQ-4260373
* Os dados do cliente são impressos em registros de informações usando Invoke FDM Service Forms Workflow. Hotfix do CQ-4260385

**Feature Packs incluídos**

**Sites**

* O controle de versão dos Fragmentos de conteúdo compara as melhorias de diferença no AEM 6.4. NPR-26760: FP para CQ-4248839
* Melhorias na diferença da variação dos Fragmentos de conteúdo para o AEM 6.4. NPR-27866: FP para CQ-4248839
* Recurso ativado na configuração OSGI **Sinalizador de Recurso de Retirada do Fluxo de Trabalho AEM**. A ação de retirar deve encerrar a instância do fluxo de trabalho após definir o sinalizador . NPR-26451: Hotfix do CQ-4259090

**Plataforma**

* A Extração de faceta do Query Builder aprimorada aproveita a API do Oak para 6.4. NPR-26674: FP para CQ-4230337

**Pacotes OSGi e pacotes de conteúdo incluídos**

O texto seguinte documenta a lista de pacotes OSGi e os pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.4.0

[Obter arquivo](assets/bundles_6_4_4_0.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.4.0

[Obter arquivo](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

O AEM 6.4.3.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilização geral do AEM 6.4 em abril de 2018.

Ele também é cumulativo, o que significa que a versão 6.4.3.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.3.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.9.
* Adição de suporte para a propriedade allowedPaths em modelos de formulários adaptáveis.
* Pesquisa avançada baseada em painel para Ativos no AEM
* Correções de script entre sites (XSS) na página Logon .
* Aprimorada a instrumentação da interface do usuário.
* Melhorias no tratamento de FormData.
* Manuseio aprimorado da nomenclatura de itens dentro de um Multicampo.
* Manuseio aprimorado de itens de espaço reservado (Exibição de cartão e Exibição de lista) durante a seleção.
* Adição da Autenticação Adobe IMS e suporte Admin Console para Managed Services.

**Ativos**

* O fluxo de trabalho do Ativo de atualização DAM não extrai referências de arquivos INDD se a opção Decodificação de IDS estiver habilitada. NPR-26243; Hotfix do CQ-4250933
* A mensagem de sucesso não é exibida quando os ativos são publicados com o Editor de ativos em massa. NPR-26252; Hotfix do CQ-4251688.
* Tendo observado um ativo a partir de um resultado de pesquisa, se você clicar no botão Voltar no navegador, uma mensagem de erro de &quot;Solicitação inválida&quot; será exibida com o código de erro 400. NPR 26578; Hotfix do CQ-4253741
* Os metadados do ativo mostram um erro de namespace inválido após a instalação de um service pack. NPR-22341; Quickfix do CQ-4237202
* A opção para reorganizar pastas e fragmentos de conteúdo na exibição em lista não é exibida para as pastas aplicáveis. NPR-27153; Hotfix do CQ-4255873
* Os usuários não podem adicionar ativos a uma nova coleção, pois isso resulta em uma mensagem de erro com uma imagem quebrada na caixa de diálogo pop-up de erro. NPR-22431; Hotfix do CQ-4237086
* A lista suspensa em cascata não é compatível com listas suspensas dinâmicas. NPR-27043; Hotfix do CQ-4252564
* Se os usuários definirem um valor não padrão para a &quot;Pasta Raiz da Empresa&quot; na configuração de nuvem do DMS7, a Predefinição do Visualizador não funcionará conforme o esperado. NPR-26360; Hotfix do CQ-4249505
* O relatório de ativos está falhando em instâncias com um número muito grande de ativos. NPR-27278; Hotfix do CQ-4256748
* As subpastas não herdam o perfil de imagem SmartCrop da pasta principal. NPR-27197; Hotfix do CQ-4256273
* Quando a integração com o Dynamic Media é ativada, algumas propriedades de metadados do Assets são modificadas. A largura, a altura e os atributos de localização não são exibidos. NPR-27203; Hotfix do CQ-4256258
* A Dynamic Media não usa o proxy configurado para alguns tipos de ativos. NPR-25211; Hotfix do CQ-4244871
* A página Editor de metadados contém Exceção de ponteiro nulo para o parâmetro de item inválido. NPR-26169; Hotfix do CQ-4241368.
* Se um menu suspenso tiver uma regra de escolha e uma regra obrigatória for aplicada a ele, a regra necessária não poderá ser satisfeita no editor de metadados. NPR-27479; Hotfix do CQ-4251428

**Sites**

* Um usuário pode controlar os recursos do editor de rich text no modo de tela cheia em linha usando políticas de conteúdo, mas não pode controlar os recursos do editor de rich text da caixa de diálogo de edição com políticas de conteúdo. NPR-26750: Hotfix do CQ-4241130
* O editor de rich text torna-se inutilizável quando é alternado de tela cheia para caixa de diálogo flutuante. A exibição flutuante contém dois editores de rich text. NPR-25589: Hotfix do CQ-4206008
* Quando a tecla return (Enter key) é pressionada em um campo de texto, o editor de rich text alterna para o modo de tela cheia. NPR-26204: Hotfix do CQ-4245893
* O plug-in de lista do editor de rich text é desativado automaticamente e não permite modificações. NPR-26507: Hotfix do CQ-4239387
* Quando um caractere especial é adicionado à janela do editor de rich text, a janela rola para a parte superior. NPR-26435: Hotfix do CQ-4249869
* Perguntas sobre o armazenamento em cache segment.js do Client Context vs. O não armazenamento em cache. NPR-26622: Hotfix do CQ-4253486
* Quando uma regra filho é ativada da instância do autor para a instância de publicação, a instância de publicação para de funcionar. NPR-26601: Hotfix do CQ-4253588
* Quando o editor de rich text é combinado com vários campos, ocorre o erro Uncaught TypeError: fieldAPI.getName is not a function at foundation.js. NPR-27146: Hotfix do CQ-4253155
* A integração do Salesforce não pode usar a configuração de proxy. NPR-27244: Hotfix do CQ-4245300
* Quando você agenda uma página para ativação usando a opção Gerenciar publicação para uma data posterior e alterna para a exibição em lista, o ícone de calendário está ausente. NPR-26974: Hotfix do CQ-4239206
* Os usuários não podem editar permissões de grupo de usuários fechado nas propriedades da página. NPR-27138: Hotfix do CQ-4256089 Não é possível editar tags por meio de marcação. NPR-26957: Hotfix do CQ-4254858
* Quando uma tag referenciada de um modelo de fragmento de conteúdo estruturado é movida, as referências existentes à tag em um fragmento de conteúdo não são atualizadas. Isso acontece na tela de edição do modelo de fragmento de conteúdo. NPR-26776: Hotfix do CQ-4251805
* Ao criar e promover um lançamento com várias páginas, várias versões de cada página são criadas. NPR-26917: Hotfix do CQ-4254663
* AEM siteadmin não lida com caminhos digitados na barra de endereços do navegador. NPR-26780: Hotfix do CQ-4254097
* Quando uma página é movida para um novo local sem renomeá-la, o histórico de versões da página é perdido. NPR-26706: Hotfix do CQ-4254025
* Os URLs no editor administrativo do fragmento de experiência não permitem sobreposições. NPR-26319: Hotfix do CQ-4252156
* Quando uma página é criada com um modelo contendo um fragmento de experiência vazio e publicada, a página falha ao abrir e ocorre um erro DefaultSlingScript. NPR-26305: Hotfix do CQ-4252460
* Quando o data-sly-use é usado com classes com nome idêntico, o código não compatível é produzido. NPR-27282: Hotfix do Sling-7581
* Após a instalação do SP de atualização, os sites têm uma configuração de implementação do blueprint em branco. NPR-27609: Hotfix do CQ-4257078

**DAM - Brand Portal**

* Os predicados de tag não são publicados quando o formulário de esquema de metadados é publicado no Brand Portal. Hotfix do CQ-4256218
* Quando uma pasta de terceiro nível é publicada do AEM para o Brand Portal, sem publicar as pastas pai, o nome da pasta é alterado. Hotfix do CQ-4255423
* O predicado do navegador de caminho é publicado do AEM Assets para o Brand Portal conforme esperado. No entanto, o caminho publicado na BP permanece /content/dam, que deve ser atualizado. Hotfix do CQ-4256240

**DAM - Creative Cloud**

* O ícone &quot;Pesquisar ativos do Adobe&quot; está ausente na navegação principal do AEM. Hotfix do CQ-4254343

**DAM - Cliente DM**

* Depois de assimilar vídeos em uma pasta associada ao Perfil de processamento de vídeo AVS, a janela do navegador é atualizada repetidamente. Hotfix do CQ-4253563
* A publicação do YouTube falha ao usar uma tag ad hoc que inclui caracteres em maiúsculas. Hotfix do CQ-4252477
* Quando uma anotação é criada em um ativo como o PDF, a interface do usuário inicia um loop de atualização de página infinito. NPR-27052: Hotfix do CQ-4255396

**DAM - Serviços DM**

* A Dynamic Media não usa o proxy configurado para alguns tipos de ativos. NPR-10727; Hotfix do CQ-4244871

**Plataforma**

* Problemas de desempenho com org.apache.sling.i18n. NPR-26812: Hotfix do SLING-7543
* Não é possível ver as propriedades do nó quando o XML de entrada é formatado e implantado. NPR-26198: Hotfix do CQ-4250448
* IndexOutOfBoundsException em ResourceProviderTracker. NPR-26968: Hotfix do GRANITE-23310
* O console JMX acumula várias sessões de administrador e uma nova sessão é aberta a cada 5 minutos. NPR-26958: Hotfix do CQ-4251090
* Após a atualização da versão 6.2 para 6.4, o arquivo de log mostra o rastreamento de pilha do resolvedor de recursos não fechado com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176: Hotfix do Granite-21734
* Quando um agente de liberação do dispatcher pronto para uso é configurado para atualizar aliases, a operação falha com um StackOverflowError. NPR-26373: Hotfix do CQ-4242928
* A replicação usa o token OAuth expirado até que falhe. NPR-25894
* Página restrita (página Grupo de usuários fechado) com sling: o alias não redireciona o usuário para a página de logon. NPR-25715: Hotfix do Granite=22263
* Ao publicar tags, nenhuma atividade é exibida na interface do usuário. Hotfix do CQ-4255961
* Não é possível editar tags na interface do usuário clássica. Hotfix do CQ-4258697
* Atualização do org.apache.felix.http.bridge para a versão 4.0.4. NPR-27038: Backport do Granite - 23334
* Os registros de atividades do gerenciador de pacotes devem ser extraídos em um arquivo de registro separado. NPR-27323: Hotfix do Granite-14866
* O validador de pacotes não relata as sobreposições no CFP. NPR-27119: Hotfix do GRANITE-22825

**Projetos**

* A API ACP trata incorretamente a paginação com apenas filhos do subdiretório. NPR-27617: Hotfix do CQ-4258639

**OAK**

* Não é possível fazer logon no repositório após instalar o AEM 6.4 Service Pack 2. NPR-27171: Hotfix do Granite-23317

**Replicação**

* O Log de auditoria permanece aberto com sessões ativas, que continuam aumentando constantemente com ~750 a cada dia. NPR-27062: Hotfix do CQ-4241350

**Comunidades**

* As publicações e respostas do Fórum são adicionadas à parte superior da segunda página e, quando atualizadas, a publicação é movida para o local correto na parte superior da primeira página. NPR-27342: Hotfix do CQ-4247338
* Links para todos os recursos soltam o caminho de contexto (/aempublish) após a rolagem. NPR-26982: Hotfix do CQ-4254345
* Os grupos adicionados não estão visíveis na lista suspensa Gerentes da comunidade, Moderadores da comunidade e Membros privilegiados ao editar um site publicado. NPR-27190: Hotfix do CQ-4258574
* Somente 10 grupos estão listados na página de recursos de ativação, mesmo se a paginação estiver habilitada para a listagem de grupos. NPR-26934: Hotfix do CQ-4252985
* A opção para ativar/desativar a pesquisa para o componente Publicação agendada no diário é fornecida no ConfigMgr, e o trabalho SearchScheduledPosts é otimizado. NPR-26923: Hotfix do CQ-4250463
* A pesquisa por palavras-chave no endereço não funciona na página do componente de calendário quando AEM comunidade está definida para funcionar com o DSRP. NPR-26737: Hotfix do CQ-4258493
* Foi implementado um link direto para o comentário em vez da publicação principal nos detalhes de um comentário, para interface do usuário de moderação e recursos de ativação. NPR-26704: Hotfix do CQ-4251381
* O conteúdo moderado por meio de várias seleções no console de moderação não é exibido no Fluxo de atividade. NPR-26695: Hotfix do CQ-4253244
* Pesquisar com nome e sobrenome no campo Para das mensagens das comunidades não retorna o resultado esperado. NPR-26385: Hotfix do CQ-4248673
* Erro observado ao carregar um anexo diferente de imagem (por exemplo, .pdf) no Fórum. NPR-27360: Hotfix do CQ-4257753
* Desfixar ou cancelar a funcionalidade de uma publicação do fórum não funcionará se a opção Autor-Publicação estiver definida com o DSRP do MySQL. NPR-26125; Hotfix do CQ-4251520
* Os componentes da coleção (fóruns, blogs, calendário, ideação, QnA) agora têm uma propriedade na caixa de diálogo do componente para ativar/desativar &quot;Bloquear UGC no modo de edição do autor&quot;, para permitir/negar o carregamento UGC no modo de edição WCM. NPR-26978: Hotfix do CQ-4248161
* A Pesquisa de tags não funciona para termos de pesquisa localizados. NPR-26171: Hotfix do CQ-4249926
* O botão Voltar ignora uma página na pesquisa do fórum. NPR-26950: Hotfix do CQ-4254804
* AEM instância em execução na porta Http padrão (80) não pode acessar o imsmanifest.xml. NPR-27173: Hotfix do CQ-4252211
* Desmarque o comentário como uma resposta para QnA não funcionará se o AEM Communities estiver definido com DSRP. NPR-26247: Hotfix do CQ-4252232
* Não é possível chamar Adobe Storage: Erro 414 - URI de GET longo observado quando os usuários pesquisam /content/community-components/en/search.html e selecionam o campo de autor como um dos filtros desse termo de pesquisa. NPR-26643: Hotfix do CQ-4251303
* O valor suspenso para DataCenterURL na configuração ASRP é alterado de Dallas para Virginia (para VA6). NPR-26936: Hotfix do CQ-4254434
* Caracteres especiais na pesquisa do fórum retornam erros ou nenhum resultado. NPR-26930: Hotfix do CQ-4247744
* O número exibido para &quot;Número de resultados&quot; na pesquisa do fórum usa delimitador incorreto para localidades em inglês e alemão. NPR-27050: Hotfix do CQ-4248939
* As notificações não lidas não aumentam além de 21. NPR-26946, NPR-27480: Hotfix do CQ-4252829, CQ-4256939
* A paginação na seção comentários de qualquer componente faz com que os usuários rolem para cima para ver o conteúdo da página, ao acessar uma página por meio da paginação. NPR-27032: Hotfix do CQ-4251228
* A pasta do site da comunidade não é clicável na imagem em miniatura ao visualizar no console do administrador na instância do AEM Author. NPR-26986: Hotfix do CQ-4254036
* A opção &quot;marcar todas as leituras&quot; marca apenas as primeiras 10 notificações como lidas e outras permanecem não lidas até que uma página seja atualizada. NPR-27037: Hotfix do CQ-4254058
* A paginação não é acionada para Ideação e a lista de tópicos (ou respostas) fica mais longa a menos que seja recarregada. NPR-26193: Hotfix do CQ-4252104
* Atividades de outros usuários e UGC excluído visível ao fazer logon com credenciais de moderador e adicionar &quot;#social-activities&quot; ou &quot;#tabs-2&quot; no final do URL de perfil do moderador. Hotfix do CQ-4251355
* Todas as tags atribuídas não podem ser removidas de um artigo de blog. NPR-26851: Hotfix do CQ-4253359
* As relações com o UGC não são excluídas na exclusão do UGC. NPR-27630: Hotfix do CQ-4258706
* O link para respostas não funciona ao clicar na linha nas respostas do fórum. NPR-27623: Hotfix do CQ-4256138
* O limite de assinatura do usuário é limitado a 1000. NPR-27614: Hotfix do CQ-4254689
* Editar um site e editar funções nas configurações de função gera Exceção de ponteiro nulo. NPR-27377; Hotfix do CQ-4255909

**Tradução**

* A visualização de tradução não funciona com o conteúdo de amostra we.retail. NPR-26727: Hotfix do CQ-4241179

**IU - Foundation**

* Uma NullPointerException é retornada ao tentar baixar configurações após a atualização para o AEM 6.4. NPR-27310: Hotfix do Granite-23573
* Backport pró-ativo para correções granite.platform.login. NPR-26941
* Backport pró-ativo para granite.ui.content fixes. NPR-26294
* O componente de campo numérico não valida números negativos no Internet Explorer 11. NPR-26701
* Backport pró-ativo para correções do granite.ui.coralui3. NPR-26662
* Backport pró-ativa para as correções do granite.ui.coralui3-eon. NPR-26666
* Backport pró-ativo para granite.ui.foundation.components fixes. NPR-27313
* Backport pró-ativo para correções do granite.ui.commons. NPR-26753
* Backports proativos da interface do usuário do Foundation. NPR-26248

**Integração**

* As modificações em AEM experiências criadas por meio do mecanismo de direcionamento não são publicadas. NPR-24869: Hotfix do CQ-4247832
* Não é possível criar várias atividades e experiências se seus nomes incluírem caracteres japoneses. NPR-27271: Hotfix do CQ-4256857
* Atualize o endpoint da API do Launch. NPR-26790: Hotfix do CQ-4254380
* (Personalização) MarcaRetriever anda por toda a árvore. NPR-27060: Hotfix do CQ-4255790

**WCM - Interface do usuário do administrador**

* Adição de um teste HTTP para publicar/desfazer a publicação de uma página com referências e um teste de interface do usuário para Live Copy. Hotfix do CQ-4256894

**WCM - Editor de páginas**

* A barra de ferramentas Editar fica desativada para componentes na primeira edição. Hotfix do CQ-4253270

**Forms**

Os principais destaques dos AEM Forms 6.4.3.0 são:

* Ativação de suporte para uma matriz/lista de objetos com Substituição de Entidade Dinâmica.
* Ativação da conformidade com FIPS para fluxo de trabalho Reader Extended em Assinatura Digital, Extensões Reader, CryptoProvider e TrustStore.
* Adição de suporte PDF/UA a formulários XFA gerados com o Designer ou o Serviço de saída.
* Ativação do suporte para a propriedade allowedPaths em modelos de formulários adaptáveis.
* Adição do suporte JBoss 7.1.4 para AEM Forms 6.4.

**Pacote complementar do Forms**

**Integração de backend**

* Não é possível preencher mapeamentos de modelo de dados de formulário com base em entidades dinâmicas na resposta SOAP. NPR-26428: Hotfix do CQ-4250639
* O valor para _elementNamespace no modelo de dados de formulário de dados adicionais, inserido usando a interface de usuário de teste, não é refletido corretamente na solicitação SOAP. Hotfix do CQ-4255373
* Uma restrição de propriedade que pode ser nula é inicializada com um valor padrão e não pode ser sincronizada com o FDM. Hotfix do CQ-4253873
* O valor padrão da propriedade que pode ser nula não está definido como True para a fonte de dados OData. Hotfix do CQ-4253870

**Formulários adaptáveis**

* Não é possível carregar sites e editor de formulários. NPR-26977; Hotfix do CQ-4249170
* Problemas ao adicionar um anexo a um formulário adaptável usando o teclado. NPR-25913; Hotfix do CQ-4249456

**Forms - Comunicação interativa**

* Não é possível mover um painel que foi adicionado usando a opção Adicionar painel filho na árvore de conteúdo no canal da Web de Comunicação interativa e em formulários adaptáveis. Hotfix do CQ-4253915
* Os nomes das tabelas são exibidos em vez do título da associação do FDM na seção Fontes de dados do canal de Impressão. Hotfix do CQ-4253669
* A função isUseXFABullets() não está desativada na classe PrintChannelRenderOptions e está disponível no SDK do cliente. Hotfix do CQ-4246583, CQ-4252700

**Gerenciamento de correspondência**

* O Javadocs para 6.4 não contém o com.adobe.dbforms.* pacote e as classes correspondentes. Hotfix do CQ-4253200
* A interface do usuário do CCR exibe um valor de lixo padrão para o campo de data, caso não haja entrada do XML de dados de teste. Hotfix do CQ-4252041
* Se uma letra contiver um módulo de lista, o espaço entre o marcador e o texto será perdido ao gerar PDF da letra. Hotfix do CQ-4250588

**Gerenciador do Forms**

* Ativação do suporte para a propriedade allowedPaths em modelos de formulários adaptáveis. NPR-26598: Hotfix do CQ-4255892

**Forms - Fluxo de trabalho**

* Se as chaves forem incluídas no nome da tarefa durante a execução do workflow do Forms, uma exceção será exibida nos logs. Hotfix do CQ-4256626
* Não é possível abrir um modelo de Pesquisa no espaço de trabalho do AEM Forms. Hotfix do CQ-4255651

**Formulários para publicação de conteúdo para dispositivos móveis**

* A notificação de saída não é exibida ao sair do campo de data no AEM Forms renderizado como HTML no Internet Explorer ou Chrome. NPR-26483: Hotfix do CQ-4239352
* Datas contidas no XML quando o processamento começa faz com que os formulários exibam um erro de validação quando o usuário tenta sair do formulário. NPR-26787: Hotfix do CQ-4251211

**Instalador do Forms JEE**

**Serviço PDF Generator**

* Não é possível exibir configurações de Relatório de Padrões e Conformidade para o Gerador de PDF. NPR-26715: Hotfix do CQ-4253384
* o arquivo binário convertpdf está ausente no pacote do complemento AIX Forms, o que causa falha ao chamar o serviço PDFA. Hotfix do CQ-4257873
* O serviço de captura de papel falha ao processar arquivos TIFF. NPR-28079: Hotfix do CQ-4240649

**Serviços de documento**

* Adicione a conformidade com FIPS para o fluxo de trabalho RE em assinaturas digitais, extensões Reader, CryptoProvider e TrustStore. NPR-27495: Hotfix do CQ-4257572
* A conversão falha ao executar o serviço AssemblerService.toPDFA em um loop. NPR-26354: Hotfix do CQ-4248656
* Não é possível validar a conformidade do PDF corretamente com base nos padrões PDF/A-1b. NPR-26286: Hotfix do CQ-4227539
* Problemas de memória insuficiente ao atualizar o AEM Forms do 6.1 SP2 CFP5 para CFP13. NPR-26285: Hotfix do CQ-4244379
* Não é possível validar a conformidade do PDF corretamente com base nos padrões PDF/A. NPR-26272: Hotfix do CQ-4248823

**Forms - Foundation JEE**

* Adição do suporte JBoss 7.1.4 para AEM Forms 6.4. NPR-27331; Hotfix do CQ-4255601

**Feature Packs incluídos**

* Ativação de suporte para uma matriz/lista de objetos com Substituição de Entidade Dinâmica. NPR-26590: Hotfix do CQ-4254655

**Pacotes OSGI e de Conteúdo Incluídos**

Lista de pacotes OSGi incluídos no AEM 6.4.3.0

[Obter arquivo](assets/6.4.3.0_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.3.0

[Obter arquivo](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

O AEM 6.4.2.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilidade geral do AEM 6.4 em **Abril de 2018.**
Ele também é cumulativo, o que significa que a versão 6.4.2.0 inclui todos os service packs AEM 6.4 lançados antes dele.

Alguns dos principais destaques do AEM 6.4.2.0 são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.7.
* Suporte adicionado para recursos da Especificação 1.4 da linguagem de modelo HTML (HTL)
* Adição de suporte para MongoDB Enterprise 3.6.
* O Editor de página de sites adiciona suporte para edição e composição no contexto com componentes do lado do cliente criados no React ou no Angular em combinação com <a href="../sites-developing/spa-walkthrough.md">SDK JS do Editor SPA AEM</a>.
* Melhorias dos Fragmentos de conteúdo: adição da capacidade de anotar em campos de texto e comparação lado a lado de versões.
* Adicionado [integração com o Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que os usuários possam pesquisar, visualizar, salvar e licenciar ativos da Adobe Stock diretamente AEM interface do usuário. Para obter informações mais detalhadas, consulte [Uso do Adobe Stock Assets com a AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Os ativos adicionaram suporte para metasschema condicional dinâmico e a capacidade de definir um esquema de metadados para pastas de ativos.
* Configuração adicionada em cada componente para ativar/desativar a funcionalidade de criação/atualização de miniaturas de pastas.
* Melhorias no Editor de imagens na criação da página.
* Correção de regressão em Comunidades para eventos de pontuação que não são tratados corretamente no caso de a resposta selecionada ser excluída.
* Revisão do limite máximo de resultados da pesquisa para solr para MAX_INT-10000.
* O trabalho de Liberação de Transação é iniciado somente na primeira chamada para storeTransaction.
* O botão &quot;Selecionar tudo&quot; agora está disponível na Exibição de cartão e na Exibição de coluna.
* Melhorias de acessibilidade na CoralUI.
* Manuseio aprimorado de Coral.Keys.
* Atualização do arquivo current.js para 2.2.2.
* Atualização do jquery para 1.12.1
* Introduzido o componente foundation-workflowstatus.
* Atualização do GCC para a versão mais recente.
* Mova o SAML para a nova sincronização de IDP externa.

**Ativos**

* A geração de subativos para o arquivo pptx não contém imagens e miniaturas. NPR-24286: Hotfix do CQ-4217986
* migrateAllAssets - adicione suporte para processamento em lote e melhore AEM método que adicione UUID aos ativos antigos. NPR-24861: Hotfix do CQ-4242863 e CQ-4247874
* Problema de desempenho com a geração de miniaturas. NPR-24693: Hotfix do CQ-4246960
* (Interface do usuário de toque) O componente &quot;predicado de opções&quot; permanece em branco quando adicionado à página do editor de Compartilhamento de ativos . NPR-24643: Hotfix do CQ-4245295
* (Fluxo de trabalho) Os ativos de tag inteligente não processam pela configuração de proxy. NPR-25840: Hotfix do CQ-4248202
* (Omnisearch) remover filetype:image dos critérios de pesquisa não remove o tipo de imagem. NPR-25232: Hotfix do CQ-4248280
* Ao tentar mover um arquivo para uma pasta diferente, as pastas com apóstrofe no nome não são exibidas. NPR-25125: Hotfix do CQ-4248660
* O controle deslizante na página Subconjunto não funciona corretamente quando a preferência de idioma é definida como diferente do inglês. NPR-25274: Hotfix do CQ-4248489
* Problema com o arquivo csv de exportação de metadados quando aberto em máquinas com formato de número europeu. NPR-26009: Hotfix do CQ-4250677
* O botão Criar não está disponível na seleção da pasta de ativos sem a permissão &quot;excluir&quot;. NPR-25788: Hotfix do CQ-4250140
* Aprimoramentos de acessibilidade (Backport): ID duplicada: o valor do atributo id deve ser exclusivo, Label: Os elementos de formulário devem ter rótulos e Nome do link: Os links devem ter texto perceptível. NPR-24252: Hotfix do CQ-4250905, CQ-4250906, CQ-4250907
* O upload de um csv com campos separados por &quot;&quot; falha para países europeus. NPR-25549: Hotfix do CQ-4249931
* (Brand Portal) Os sub-ativos de um arquivo pdf de várias páginas não são publicados quando um ativo é publicado. NPR-25991: Hotfix do CQ-4245162
* Publique a funcionalidade posterior para AEM na replicação do Brand Portal. NPR-25911: Hotfix do CQ-109139
* Publicar e desfazer a publicação da coleção privada por usuários não administradores resulta em um NPE. NPR-25906: Hotfix do CQ-4250594
* Desative a publicação de fragmentos de conteúdo e esquemas de formulários no Brand Portal. NPR-24176, NPR-26004: Hotfix do CQ-4251592, CQ-4252026
* (Dynamic Media) Visualizadores do DM atualizados para a versão 5.10.1, que permite verificar nomes duplicados na página Predefinição de imagem. Consulte Atualizar visualizadores do Dynamic Media (5.10.1). NPR-24403: Hotfix do CQ-4247554
* Erro de JavaScript no console do navegador na exibição em coluna ao selecionar um ativo ou pasta. NPR-25939: Hotfix do CQ-4250228
* (Exibição de coluna) Não é possível identificar tarefas, pois o arquivo de chave é exibido como uma entrada branca em branco. NPR-25903: Hotfix do CQ-4246307

**Sites**

* A consulta de datasource.jsp no AEM 6.2 é diferente do AEM 6.4. NPR-24968: Hotfix do CQ-4244235
* (Interface clássica) Não é possível adicionar tags às páginas. NPR-25255, NPR-25612: Hotfix do CQ-4249615
* Especificação de linguagem de modelo de HTML 1.4 com suporte para AEM 6.4.2.0 NPR-24585
* Herança incorreta no componente local após copiar uma página de Live Copy. NPR-25920: Hotfix do CQ-4236737, CQ-4248957
* O tempo ON/OFF é armazenado em crx/de, mas não busca o mesmo no console da interface do usuário das propriedades da página. NPR-25154: Hotfix do CQ-4243431
* Estilos O sistema interrompe os valores iniciais das propriedades da caixa de diálogo. NPR-25648: Hotfix do CQ-4250073
* Ao definir uma propriedade cq:tagName em um nó cq:htmlTag , o nome da tag não será considerado se o componente for incluído por meio do JSP. NPR-24154: Hotfix do CQ-4244120
* Para os componentes de um parsys aninhado, sempre o primeiro (com caminho menos aninhado) design satisfatório é aplicado de vários componentes disponíveis. Para obter mais informações, consulte [Resolução do caminho de design](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973: Hotfix do CQ-4246276
* Ao colar o texto em um componente RTE, uma caixa de diálogo pop-up é exibida, mas não é renderizada corretamente. NPR-24895: Hotfix do CQ-4245901
* (RTE) Problemas de desempenho com o indicador de campo obrigatório. NPR-24894: Hotfix do CQ-4241895
* (Componente de página) A adição de um componente ao Parsys é cortada da direita e sai da largura do quadro do dispositivo. NPR-25536: Hotfix do CQ-4238224
* O editor de texto sem formatação envia dados não aparados e adiciona espaços extras. NPR-25312: Hotfix do CQ-4249006
* Ao abrir o componente usando o modo de entrada, os plug-ins carregados anteriormente não estarão visíveis na segunda vez. NPR-24610: Hotfix do CQ-4236850
* O carregamento de um XF na visualização do editor por copiar/colar não carrega a variação principal automaticamente. NPR-24841: Hotfix do CQ-4248037
* Estrutura de HTML incorreta no siteadmin / damadmin interrompe o IE11. NPR-24686: Hotfix do CQ-4246363, CQ-4248402
* (Assistente para Gerenciar Publicação) O Calendário para a data de ativação na etapa Opções não abre após algumas ações na etapa Escopo . NPR-25681: Hotfix do CQ-4250205
* A interface do usuário clássica não funciona para editar o CUG pois está obsoleta. NPR-25075: Hotfix do 4241823
* Opção Criar indisponível para criar fragmentos de experiência. NPR-26053: Hotfix do CQ-4249923
* A variação XF está sendo ativada duas vezes, gerando IDs duplicadas para o mesmo item. NPR-24179: Hotfix do CQ-4245093
* A tabela do Foundation é vulnerável a Scripts armazenados entre sites. NPR-25185: Hotfix do CQ-4240760
* Erro &quot;Valor inválido do seletor de recursão&quot; ao migrar um componente do AEM 6.2.1.13 para o AEM 6.4. NPR-24146

**WCM - Editor de páginas**

* Vários Parsys empilhados devido a consultas de longa duração (mais de 6) deixam o AEM lento. Hotfix do CQ-4240247
* Erro JS ao adicionar cq:tagName vazio no nó cq:htmlTag . Hotfix do CQ-4251852
* Atualizar Ações Editáveis com base na realocação columnClassNames. Hotfix do CQ-4250781
* Exponha caminhos de recursos e modelos usando uma única propriedade e atributo. Hotfix do CQ-4251255
* Reverter as alterações de quebra da API export.json. Hotfix do CQ-4251854
* (SPA editável) Candidato à versão para 1.0.0. Hotfix do CQ-4251991
* A barra de ferramentas Editar fica desativada para outros componentes ao editar qualquer componente. Hotfix do CQ-4253270

**Integração**

* Os campos Biblioteca e URL de download devem ser editáveis. NPR-24804: Hotfix do CQ-4246864
* Problema com várias configurações de DTM. NPR-24685: Hotfix do CQ-4247293
* Adição de suporte para implantação assíncrona de bibliotecas de clientes hospedadas. NPR-25716: Hotfix do CQ-4245745
* O componente direcionado com a oferta correspondente ausente renderiza a página inteira e, em vez de um componente direcionado vazio, outra representação completa da página é adicionada. NPR-25273: Hotfix do CQ-4248003
* O mecanismo do Target (mbox.js, at.js) não usa URLs danificados e usa URLs que contêm dois pontos, que podem falhar em determinadas implantações. NPR-25339: Hotfix do CQ-4237854
* (Launch)LibraryDownloadProcess armazena o valor libraryUri errado. NPR-25330: Hotfix do CQ-4250006

**Plataforma**

* Loop de reindexação | NPE ao executar o BinaryTextExtraction durante a atualização local de 6.3 para 6.4. Hotfix do Granite - 21677
* Substituição entre limites do caminho marcado interno /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problema ao executar o detector de padrões. NPR-25036: Hotfix do CQ-4248597
* Entradas de log não gravadas devido ao NPE em LogEntryImpl. NPR-25627: Hotfix do Granite-22383
* A replicação do evento de exclusão não verifica os direitos. NPR-25679: Hotfix do CQ-4241234
* Adição do suporte STARTTLS no &quot;Day CQ Mail Service&quot;. NPR-25611: Hotfix do CQ-4249924
* Backport pró-ativo para correções granite.platform.login para melhorar a acessibilidade. NPR-25176: Hotfix do Granite 21746 e Granite-21309
* (AEM 6.4) Erro ao reconstruir o pacote e reinstalá-lo. NPR-25173: Hotfix do CQ-4247939
* Remoção do padrão MERGE_PRESERVE aclHandling. NPR-24593: Hotfix do Granite-21889
* O Content-Type não é proposto e está ausente na resposta após aplicar o ContentDispositionFilter duas vezes. NPR-24175: Hotfix do Sling-7525
* Status do Gerenciador de pacotes incorreto após a atualização para AEM ramificação 6.4. NPR-24551: Hotfix do Granite-21750
* Instância do AMS - Análise de logs de erro. Hotfix do CQ-4249567

**Segurança**

* O SAML redireciona para a página de logout usando o Okta IDP. NPR-25523: Hotfix do GRANITE-22364
* A autenticação IMS por meio das configurações externas do Provedor OAuth do OAK IDP desativa o usuário criado no AEM. NPR-25301: Hotfix do Granite-22363

**MAC - Integração do Test&amp;Target**

* (Direcionamento) Erro do componente de texto durante o direcionamento. Hotfix do CQ-4233343

**Comunidades**

* (Biblioteca de arquivos) Baixar ativos com espaços em branco do causa problemas de formato. NPR-24260: Hotfix do CQ-4245159
* Correções de vários problemas do Adobe Social. NPR-24247: Hotfix do CQ-4245054, CQ-4245120, CQ-4245296
* Falha na rolagem infinita do console membros e grupos caso a publicação do autor seja executada em caminhos de contexto diferentes. NPR-24437: Hotfix do CQ-4246013
* A publicação não retorna ao estado não respondido mesmo ao remover do estado respondido e a pontuação não diminui. NPR-24419: Hotfix do CQ-4245797, CQ-4245932
* Eventos adicionados usando a funcionalidade de calendário em comunidades gera valores errados. NPR-24883: Hotfix do CQ-4244056
* (Fórum das comunidades) Problemas com o clique de paginação e o comportamento de carregamento de página. NPR-24880: Hotfix do CQ-4246109
* (Chrome) As conversões de fuso horário falham nos eventos das comunidades. NPR-24881: Hotfix do CQ-4247115
* Não é possível renderizar o objeto incorporado no Email. NPR-24999: Hotfix do CQ-4248022
* A sequência de personalização deve ser executada na atualização de UGC, além da criação de UGC. NPR-25892: Hotfix do CQ-4251399
* Resposta da caixa de diálogo modal em Grupos. NPR-25623: Hotfix do CQ-4248805
* Exceção de Solr é lançada na exclusão de conteúdo. NPR-25869: Hotfix do CQ-4248908
* Os links paginados para encadeamentos com muitas publicações não funcionam nas Notificações. NPR-25678: Hotfix do CQ-4243038
* Os valores de tempo no resultado da pesquisa exibem a hora do servidor em vez do fuso horário do cliente. NPR-25594: Hotfix do CQ-4248986
* (Comentários do fórum) O botão Voltar do navegador não está funcionando como esperado. NPR-25205: Hotfix do CQ-4248573
* (Resultados da pesquisa) O botão Voltar do navegador não está funcionando como esperado. NPR-25214: Hotfix do CQ-4248574
* Null é retornado ao sobrepor o componente communitygroupmemberlist. NPR-25228: Hotfix do CQ-4248523
* (Calendário das Comunidades) ClassCastException é gerado ao salvar o evento com a nova imagem de Capa. NPR-25167: Hotfix do CQ-4248662
* (Comunidades) Mensagens sendo truncadas. NPR-25326
* (Publicação AEM) O recurso de pontuação falha com o caminho de contexto e mostra a tela em branco. NPR-26155: Hotfix do CQ-4251942
* (MSRP) O calendário recém-criado é salvo parcialmente, lançando o NPE no log de erros. NPR-26071: Hotfix do CQ-4250531
* A paginação do Fórum/Tópico só é atualizada quando a página é atualizada. NPR-26070, NPR-25965: Hotfix do CQ-4249509
* (Fórum P&amp;R) Não é possível navegar para a página anterior ao abrir um link direto para um comentário. NPR-26069: Hotfix do CQ-4251699
* Carregar imagem no grupo Criar não funciona em dispositivos móveis. NPR-26172: Hotfix do CQ-4251703
* (Mensagens) Ao usar o DSRP, o nome do receptor da mensagem é sempre mostrado como &quot;Desconhecido&quot;. NPR-26056: Hotfix do CQ-4251397
* O rótulo de status de conclusão do recurso de ativação do Scorm aparece vazio na interface do usuário. NPR-26034: Hotfix do CQ-4249994
* Ao criar um novo grupo de comunidade, um grupo de comunidade duplicado é criado em um cluster mongoMK ativo/ativo. NPR-26032: Hotfix do CQ-4245884
* (Autor) O assistente de criação de grupo demora muito para carregar/criar um grupo no assistente. NPR-26031: Hotfix do CQ-4244966
* Parsys desaparece ao adicionar uma instrução include no script hbs. NPR-25908: Hotfix do CQ-4250489
* Ao habilitar &quot;Permitir privilegiados&quot;, os membros com privilégios só devem poder compor para usuários que sejam membros da comunidade. NPR-25877: Hotfix do CQ-4248450
* Deeplinks bloqueados para ativação. NPR-25966: Hotfix do CQ-4251478
* A paginação do fórum não é atualizada dinamicamente na remoção de respostas. NPR-25970: Hotfix do CQ-4248975, CQ-4252843
* A rolagem automática e o realce não funcionam em eventos de calendário e de bancada no caso de comentários aninhados. NPR-25958: Hotfix do CQ-4251471
* (DSRP) O desempenho do Direct/Deep Link se degrada com grandes quantidades de Conteúdo Gerado pelo Usuário. NPR-25957: Hotfix do CQ-4251470
* Não é possível modificar as propriedades de Permitir Membros Privados e Membros Privados. NPR-26014: Hotfix do CQ-4244592
* Marcar todas como lidas redefine os contadores de notificação para todas as páginas da comunidade. NPR-25931: Hotfix do CQ-4248612
* Edite as TIs com falha no DSRP. NPR-25929: Hotfix do CQ-4251382
* As TIs de email falham devido ao NPE ao criar modelos de email. NPR-26039: Hotfix do CQ-4250962
* Problemas de encadeamento do fórum ao incorporar imagens com resolução muito alta. NPR-26037: Hotfix do CQ-4244453, CQ-4253099
* A hora exibe opções quando o fuso horário do servidor é diferente do fuso horário do usuário. NPR-26036: Hotfix do CQ-4248751
* Anexar um arquivo duas vezes com o mesmo nome a uma publicação do fórum leva a um erro no servidor. NPR-24172: Hotfix do CQ-4244367
* Correções de desempenho do backport - Agrupe a paginação no autor e na publicação, Agrupe a pesquisa no autor, Evite a serialização de respostas para o diário, o calendário e a ideação e o carregamento lento para obter o botão de associação do grupo (convidar/desconvidar) para cada grupo enquanto exibe a página de listagem do grupo. NPR-24538: Hotfix do CQ-4246515
* Os recursos de ativação não estão visíveis no autor. Hotfix do CQ-4252618
* As notificações não são geradas para thread de usuário desconhecido. Hotfix do CQ-4245132
* A pesquisa de grupo não é exibida no painel esquerdo. Hotfix do CQ-4252621
* (Autor) A paginação não está funcionando para o Console de grupos. Hotfix do CQ-4242786
* Atualização da interface do usuário do jQuery. Hotfix do CQ-4248894
* Atualize para a versão mais recente do SCORM 2017.1. NPR-25675: Hotfix do CQ-4240671
* Os campos &quot;Compor em nome&quot; estão visíveis para usuários não comunitários. NPR-25331: Hotfix do CQ-4247858
* A publicação ainda está visível na interface do usuário, mesmo após a exclusão, e apresenta um erro no console. NPR-26290: Hotfix do CQ-4252803
* (Configurações do site) Não é possível salvar as alterações feitas em Funções. NPR-26274: Hotfix do CQ-4252187
* (Vulnerabilidade de Segurança) Tomada de Conta devido a Configuração Incorreta de Token Web JSON. NPR-26458: Hotfix do CQ-4253314
* A paginação não é redefinida após a remoção de respostas. NPR-26326: Hotfix do CQ-4252997
* A imagem do anexo não é exibida em Rascunhos durante a edição. Hotfix do CQ-4253360
* A página não está atualizando ao anexar anexo no banco de dados relacional (DSRP). Hotfix do CQ-4253084
* Os grupos não estão funcionando dentro do recurso de site Ativar. Hotfix do CQ-4252975
* Os pré-requisitos dos caminhos de aprendizado não são persistentes em Ativação. Hotfix do CQ-4252948

**Fluxo de trabalho**

* A interface do usuário do iniciador de fluxo de trabalho não exibe configurações do iniciador anteriores a 41 e aciona um erro de javascript no console. NPR-25028: Hotfix do CQ-4247604
* Editar um fluxo de trabalho herdado sem editar o iniciador faz com que vários fluxos de trabalho sejam criados em qualquer fluxo de trabalho que contenha uma etapa Ativar página/ativo . NPR-25870: Hotfix do CQ-4250896
* Link incorreto na carga do fluxo de trabalho se a página tiver um nó de metadados. NPR-25916: Hotfix do CQ-4250733

**Tradução**

* Correção de que a importação de projeto traduzido faz duas solicitações POST simultâneas, portanto, causando erro. NPR-24889: Hotfix do CQ-4247638
* Correção de que, ao criar um projeto de tradução para vários idiomas, todas as páginas do mesmo idioma eram adicionadas ao mesmo trabalho. NPR-25091: Hotfix do CQ-4246112
* Correção de que, em alguns casos, o trabalho de tradução listava apenas as 40 páginas principais. NPR-25974: Hotfix do CQ-4248661
* O componente DataPicker (Coral2) não altera o ano. NPR-24466: Hotfix do Granite-21893

**IU - Foundation**

* Backports proativos da interface do usuário do Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-2599 35, NPR-25976
* (Importador de design) A importação de uma página não importa o js, css. NPR-25203: Hotfix do Granite-22236
* Backports proativos da interface do usuário do Foundation para melhorar a estabilidade do produto. NPR-24334

**MAC - Integração do Test&amp;Target**

* A segunda página do PersonalizationWizard ( iniciada por &quot;Start Targeting&quot; ) está em branco e gera erros de console. Hotfix do CQ-4253277

**Fragmentos de experiência**

* Integração mesclada de fragmentos de experiência/Target ao AEM 6.4.2.0. Hotfix do CQ-4248653

**Gerenciamento de fragmentos de conteúdo**

* Anotações de Fragmentos de conteúdo e comparação lado a lado das versões do Fragmento de conteúdo. Hotfix do CQ-4247148

**DAM - Geral**

* O filtro &quot;Check-out por&quot; não está funcionando corretamente na pesquisa. Hotfix do CQ-4247070
* Ao executar o fluxo de trabalho de atualização de ativos, a cópia do idioma do ativo e sua miniatura ficam em branco. Hotfix do CQ-4250641
* ID duplicada: o valor do atributo id deve ser exclusivo. Hotfix do CQ-4250905
* Rótulo: Os elementos de formulário devem ter rótulos. Hotfix do CQ-4250906
* Nome do link: Os links devem ter texto perceptível. Hotfix do CQ-4250907
* Migração de modelos de metadados de pastas de portas JMX e ServiceUserMapping. Hotfix do CQ-4252947
* WebdriverIO Testes não executados na ramificação de lançamento/640 do CQ/dam. Hotfix do CQ-4252749
* Os links para ativos movidos não são refatorados se o link for publicado. Hotfix do CQ-4245756

**DAM - Visualizadores**

* Erro intermitente ao carregar vídeo com novos visualizadores 5.10.1. Hotfix do CQ-4250562

**DAM-Brand Portal**

* Falha ao cancelar a publicação da coleção do Brand Portal com o erro . Hotfix do CQ-4245990
* Não é possível cancelar a publicação de predefinições de imagens do Brand Portal. Hotfix do CQ-4246140
* Subativos de um arquivo pdf de várias páginas não são publicados quando um ativo é publicado. Hotfix do CQ-4245162

**DAM - DMClient**

* Ao publicar um ativo de vídeo no YouTube, as tags que resultam no YouTube incluem o caminho completo da tag. Hotfix do CQ-4245549
* (Atualizações de rejeição e aceitação) Problema com o redirecionamento de CSS do visualizador. Hotfix do CQ-4247854
* Não é possível criar/editar a predefinição do visualizador como não membro do grupo &#39;administradores&#39;. Hotfix do CQ-4247618
* (6.4.1.0) A adição de vários vídeos em vários parsys interrompe o reprodutor de vídeo. Hotfix do CQ-4248517
* Renomear e mover o ativo dentro de um Conjunto de imagens renderiza a edição impossível. Hotfix do CQ-4248434
* Publicar vídeos grandes no YouTube gera mensagens de tempo limite. Hotfix do CQ-4237831
* (Exibição de lista) A interface do usuário do Seletor/Seletor de ativos muda para todo o cinza e é desativada para o usuário. Hotfix do CQ-4237817
* (Zoom vertical) O Css não é carregado com um erro 404. Hotfix do CQ-4236508
* Tentar baixar um ativo com caractere de porcentagem (%) no nome do ativo resulta em um arquivo vazio. Hotfix do CQ-4250558
* (Exibição de cartão) Nenhum indicador de processamento é exibido ao usar Copiar e colar em um ativo de vídeo. Hotfix do CQ-4249037
* (Atualização da versão 6.3.2 para 6.4) As predefinições da imagem de pré-atualização são mostradas como &quot;Não publicado&quot; na página Representações, mas não produzem o botão URL quando selecionadas. Hotfix do CQ-4240406
* Dívida Técnica/Pequenas Melhorias. Hotfix do CQ-4240648
* O Seletor de ativos (ou o Seletor de ativos) não mostra todos os ativos das pastas disponíveis. Hotfix do CQ-4218414
* A predefinição de imagem sem altura exibe imagens com tamanho incorreto. Hotfix do CQ-4246546
* (Ativos de várias páginas) A interface do usuário é interrompida ao clicar em anotações. Hotfix do CQ-4251434
* Ao atualizar da versão 6.3 para a 6.4 e posterior da predefinição do Analytics, uma nova predefinição de conjunto de relatórios e análises é criada, perdendo os dados de relatório mais antigos do usuário. Hotfix do CQ-4244529
* (Assistente para gerenciar publicação) A lista de ativos parece estar vazia ao tentar publicar ou desfazer a publicação. Hotfix do CQ-4251881
* Ao escolher Visualizadores após visualizar o Definir membros, os vídeos AVS não são reproduzidos. Hotfix do CQ-4205308
* As predefinições de processamento de vídeo de pré-atualização não podem ter uma nova predefinição de codificação de vídeo adicionada nem editar as predefinições de codificação existentes. Hotfix do CQ-4240407
* As predefinições de imagens não são aplicadas às representações dinâmicas baixadas. Hotfix do CQ-4249862
* O botão selecionar tudo não funciona corretamente na página de listagem Predefinição do visualizador. Hotfix do CQ-4252462
* Perfis de vídeo: O botão Selecionar tudo não funciona. Hotfix do CQ-4253076, CQ-4251447
* Passagem da validação do SP2 - Passagem de fumaça. Hotfix do CQ-4251639

**DAM - DMServices**

* Falha ao gerar Representações do Dynamic Media para o arquivo EPS. Hotfix do CQ-4243688

**Granite**

* O Type no pacote SymbólicaName leva ao pacote duplicado. Hotfix do Granite-22155
* CUGConfiguration pode não selecionar CugExclude. Hotfix do Granite-21109
* Reiniciar o Adobe Granite Workflow Core executa novamente as etapas do fluxo de trabalho a partir do meio, criando fluxos de trabalho desnecessários. NPR-25057: Hotfix do Granite-22218
* JcrResourceBundle não suporta corretamente vários nomes básicos. NPR-25245: Hotfix do Granite-22317
* Na instalação de pacotes de conteúdo, as ACLs são agrupadas por principal, portanto, quebrando o modelo de permissão. NPR-24583: Hotfix do Granite-21591
* Atualize o Jetty para 9.4.11 para corrigir vulnerabilidades. NPR-25030: Hotfix do Granite-22120

**Forms**

Os principais destaques dos AEM Forms 6.4.2.0 são:

* Adição de uma nova propriedade para Filas a serem atualizadas sem atualizar o navegador.
* Adição da capacidade de o usuário usar o mesmo arquivo WSDL para vários serviços.
* Remoção do padrão de carimbo de data e hora não suportado da lista suspensa do datepicker.
* Suporte adicionado para subjacente de xfaf e pdf no OSGI.
* Adição de suporte para usar o [recurso de relatórios de transação](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) implantações locais.
* Código adicionado para não exibir a var filho no editor de regras de condição.

**Pacote complementar do Forms**

**Relatório de transação**

* Atualize a configuração do Relatório de Transação com a importância da replicação reversa configurada em um servidor de Publicação. NPR-26050: Hotfix do CQ-4246650
* Inicialização atrasada do Trabalho de Liberação Periódica. NPR-25968: Hotfix do CQ-4245024
* A Gravação de Transação falha com Exceção de Ponteiro Nulo. Hotfix do CQ-4247302

**Forms - Fluxo de trabalho**

* (Espaço de trabalho do HTML) Quando um usuário aceita uma tarefa, a contagem de filas é atualizada para esse usuário específico, mas não para outros usuários, a menos que a página seja atualizada. Esse problema foi corrigido por uma nova propriedade. Para configurar essa nova propriedade para a instância do AEM, consulte as Configurações. NPR-24536: Hotfix do CQ-4233665
* Não é possível carregar um formulário grande no aplicativo AEM Forms no 6.4. NPR-24463: Hotfix do CQ-4245091
* Problema no aplicativo Mobile Workspace ao tentar visualizar a tarefa compartilhada. NPR-25177: Hotfix do CQ-4248733
* Comportamento de validação inconsistente entre a Web e a APK. NPR-25670: Hotfix do CQ-4248178
* Quando uma chamada para um serviço da Web é feita em um formulário HTML5 aberto no cliente, ele falha e uma mensagem de erro é retornada. NPR-26048: Hotfix do CQ-4244716
* Problema ao chamar o serviço nos formulários AEM aplicativo Windows 6.3. NPR-26468: Hotfix do CQ-4252341

**Formulários para publicação de conteúdo para dispositivos móveis**

* (Conjunto de formulários) Problema de validação de campo SSN e móvel ao ser visualizado. NPR-24458: Hotfix do CQ-4244983
* Os dados não são mostrados com o preenchimento prévio de campos de várias linhas na visualização de HTML. NPR-24549: Hotfix do CQ-4244212
* Os dados são perdidos quando o script é avaliado em um campo de várias linhas. NPR-25333, Hotfix do CQ-4249610

**Forms - Comunicação interativa e gerenciamento de correspondência**

* A sincronização falha no IC com modelo básico e modelo de impressão IC de referência. NPR-24912
* (CCR) Os validadores não funcionam para campos/variáveis. Hotfix do CQ-4245047
* O ícone de Objeto do Modelo de Dados desaparece na barra de ferramentas Editar Texto intermitentemente. Hotfix do CQ-4245122
* Os registros de exceção são exibidos no IC copiado se o IC original for excluído. Hotfix do CQ-4249378
* Na representação da letra, a condição não é avaliada como true, mesmo quando os dados estão corretos. Hotfix do CQ-4245944
* Os componentes gerados automaticamente não são destacados na seleção na árvore de conteúdo. Hotfix do CQ-4246178
* Problemas ao abrir o editor de Modelo de canal da Web. Hotfix do CQ-4248182
* Não é possível alterar a ordem dos ativos adicionados à medida que as setas para cima/para baixo permanecem desativadas. Hotfix do CQ-4252042
* Não é possível atualizar as propriedades do módulo Condição. Hotfix do CQ-4247909
* O UX da caixa de diálogo &quot;Cancelar herança&quot; quando o usuário reorganiza um Objeto no Canal da Web precisa ser melhorado. Hotfix do CQ-4241076
* Os dados na correspondência que faz referência aos vínculos definidos no XDP não são preenchidos ao usar o URL da correspondência direta. Hotfix do CQ-4245833
* (Problema de cache) A sincronização do canal da Web não reflete as alterações feitas em fragmentos de layout, Fragmento de texto do canal de impressão. Hotfix do CQ-4251460
* Não é possível atualizar as propriedades do Fragmento de layout e do DDD. Hotfix do CQ-4247830
* (CCR) O recarregamento de rascunho está falhando devido à análise XML. Hotfix do CQ-4250950
* (Editor de IC) O botão &quot;Editar fragmento&quot; deve ser mais descoberto. Hotfix do CQ-4244694
* (XDP) Uma tela em branco é exibida ao adicionar um fragmento de layout no novo subformulário criado. Hotfix do CQ-4248810
* Falha no teste DocumentFragment-principal-DeployWithServerSideTests . Hotfix do CQ-4245496
* Variável de módulo de texto Instância duplicada no módulo Condição. Hotfix do CQ-4252128
* O URL de visualização do PDF não mostra o relatório de transação ao publicar. Hotfix do CQ-4246158
* Problemas relacionados ao IC Sync com o Print Channel para a sincronização de canal da Web. Hotfix do CQ-4251505
* Limpeza do código EXM: Remova LocalFunctionMapper. Hotfix do CQ-4243265
* Para corrigir o tipo de recurso de Cabeçalho de Tabela do componente de tabela do WebChannel do IC. Hotfix do CQ-4251821
* (Editor de IC) Problemas de usabilidade. Hotfix do CQ-4241081
* O subformulário de canal de impressão não mostra a funcionalidade de inserção. Hotfix do CQ-4252994
* A sincronização de Manter alterações falha após a remoção do nó FDM ou do espaço reservado de Variável. Hotfix do CQ-4253178
* (Editor de modelos) O modelo básico mostra as áreas de soltar de cabeçalho/rodapé adicionais e a tela cintila ao abrir o Canal da Web. Hotfix do CQ-4253323
* Os componentes gerados automaticamente não são realçados ao selecionar na árvore de conteúdo. Hotfix do CQ-4246178

**Serviços de documento**

* (Serviço de formulários) O OSGI não tem suporte para XFAF. NPR-25181, Hotfix do CQ-4251313
* Os caracteres no cabeçalho do arquivo de PDF montado estão vindo a ficar ilegíveis. NPR-25113: Hotfix do CQ-4244682

**Formulários adaptáveis**

* Enviar ação como Enviar Email lança uma exceção com campos CC/BC em branco. NPR-25019: Hotfix do CQ-4243039
* Não é possível usar o componente Formulário de AEM OOTB devido a uma consulta ineficiente. NPR-25065: Hotfix do CQ-4247256
* Remova sling:orderBefore dos nós de diálogo de guideImageChoiceComponent. Hotfix do CQ-4245013
* (Seletor de data) O Padrão de edição não suporta dois tipos de padrão de carimbo de data e hora. Hotfix do CQ-4237982
* Envie a ação usando os problemas de criação do &#39;Forms Workflow&#39; Classic. Hotfix do CQ-4236981
* (Canal da Web) O Gráfico IC deve herdar a propriedade colspan do gráfico AF. Hotfix do CQ-4252143

**Integração de backend**

* (Solicitações SOAP) Os decimais grandes (mais de 6 dígitos) são representados na notação exponencial, resultando em erro de validação. NPR-25283: Hotfix do CQ-4248100
* Validação incorreta de parâmetros opcionais definidos em tipos complexos. NPR-25070: Hotfix do CQ-4247107
* Adição da capacidade de o usuário usar o mesmo arquivo WSDL para vários serviços. NPR-24604, Hotfix do CQ-4247756
* O FDM omite a ordem dos parâmetros em suas chamadas SOAP. NPR-25069, Hotfix do CQ-4247180
* O FDM mescla entidades (em Lista/Matriz) na solicitação SOAP. NPR-25284: Hotfix do CQ-4248375

**Instalador do Forms JEE**

**Serviço PDFG**

* A função criar/modificar das configurações de segurança não funciona. NPR-24769: Hotfix do CQ-4246927
* Optimize PDF ao desincorporar seletivamente fontes por meio de uma única chamada de API. NPR-23287

**Serviços de documento**

* O Serviço de Saída não fornece as tags corretas para o Reader de acessibilidade. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Hotfix do CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Segurança de documentos**

* Problema com a criação de Política usando a Segurança de Documento. NPR-25586, NPR-25547: Hotfix do CQ-4247086

**Forms - Foundation JEE**

* Processos em execução como Conta de Contexto do Sistema intermitentemente. NPR-25289, NPR-25313: Hotfix do CQ-4249331
* AEM Forms JEE afetado pelo alerta de segurança de vinculação de dados do Apache Struts e Jackson. NPR-25628: Hotfix do CQ-4242891
* O processo do ponto de início do email não funciona. NPR-25253: Hotfix do CQ-4248518

**Feature Packs incluídos**

**Ativos**

* Adicionado [integração com o Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que os usuários possam pesquisar, visualizar, salvar e licenciar ativos da Adobe Stock diretamente AEM interface do usuário. Para obter informações mais detalhadas, consulte [Uso dos ativos Adobe Stock com AEM ativos](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779: Hotfix do CQ-30857
* Adição de suporte para metaschema condicional dinâmico. Para obter mais informações, consulte [Metadados em cascata](/help/assets/cascading-metadata.md). NPR-25189: Hotfix do CQ-4237413
* Ativação da opção &quot;Download de ativos&quot; em Fragmentos de conteúdo. Para obter mais informações, consulte [Relatórios de ativos](/help/assets/asset-reports.md). NPR-25186: Hotfix do CQ-4237410
* Capacidade de definir um esquema de metadados para pastas de ativos. Para obter mais informações, consulte [Esquema de metadados da pasta](/help/assets/folder-metadata-schema.md) e fazer referência à [Configurações](#configuration-settings-required-for-npr) após AEM instalação 6.4.2.0. NPR-21268: Hotfix do CQ-4221574

**Sites**

* Permitir editar um fragmento de conteúdo sem excluir permissões. Para obter mais informações, consulte [Personalização e extensão de fragmentos de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793: Hotfix do CQ-4248750
* Adição da capacidade de anotar Fragmentos do conteúdo. Para obter mais informações, consulte [Fragmentos de criação de variações](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188: Hotfix do CQ-4235336
* Controle de versão: Comparar fragmentos de conteúdo lado a lado. Para obter mais informações, consulte [Gerenciamento de fragmentos de conteúdo](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187: Hotfix do CQ-4237412
* Aprimoramentos do Editor de imagens enviados para o AEM 6.4.2.0. Para obter mais informações, consulte [Editor de imagens](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24467

**Pacotes OSGI e de Conteúdo Incluídos**

Lista de pacotes OSGi incluídos no AEM 6.4.2.0

[Obter arquivo](assets/6.4.2.0_bundle-list.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.2.0

[Obter arquivo](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

O AEM 6.4.1.0 é uma atualização importante que inclui correções e aprimoramentos de desempenho, estabilidade, segurança e essenciais para o cliente lançados desde a disponibilização geral do AEM 6.4 em abril de 2018.

AEM 6.4.1.0 pode ser instalado no AEM 6.4 GA. Alguns dos principais destaques do service pack são:

* O repositório integrado (Apache Jackrabbit Oak) foi atualizado para a versão 1.8.3.
* Introdução às Tags inteligentes aprimoradas.
* Correções no seletor de Design, no seletor de tags (altere a VM de origem e a VM de destino para auto.)
* Inclusão de suporte para typeHint para salvar valores como string.
* Adição de suporte para SMTP sobre TLS no Serviço de email.
* Correção de tratamento de proxy para o encaminhador HTTP no DMS7.
* Atualize para /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js versão 1.3.
* Correções nos pacotes DMHybrid Opt-OUT e Opt-IN.
* Correções no Recorte inteligente.
* Os valores de configuração do OOTB foram migrados para o novo local ( de /etc para /conf).
* Perfis de cores adicionados às configurações do cliente nos servidores de entrega.
* Migração de configurações do Servidor de Imagem de /etc —&amp;gt; /conf.
* Fragmento de conteúdo de origem adicionado para tradução.
* Adição do suporte ARIA para Print e PrintDialog.
* Adição do suporte ARIA para validação de email.
* Backport pró-ativo para correções de platform.clientlibs.
* Prevenção da execução automática de scripts quando não há entrada para o dataType explícito (resolve CVE-2015-9251).

**Ativos**

* O valor da lista suspensa em cascata mostra em branco na reabertura da página de propriedades do ativo. NPR-23042: Hotfix do CQ-4238761
* Links compartilhados na página mylinkshare e links para a página não estão disponíveis para o usuário não administrativo NPR-23044: Hotfix do CQ-4239004
* Para evitar uma exceção de ponteiro nulo no fluxo de trabalho de atualização de ativo do DAM no 6.4.0. NPR-24134: Hotfix do CQ-4244972
* A página WCM publicado mostra ícones de espaço reservado para hotspot, arquivos CSS ausentes com erro 403 para visualizadores OOTB. NPR-23041: Hotfix do CQ-4233716
* (Exibição de detalhes) O recurso Próxima navegação/Voltar deixa uma sobreposição DIV na área de visualização da representação dinâmica bloqueando o acesso ao visualizador. NPR-23043: Hotfix do CQ-4238499
* A representação de imagem CMYK tem saturação incorreta. NPR-23048: Hotfix do CQ-4235470
* XMP extração de metadados por Scene7ListInfoProvider consome muitos recursos. NPR-23754
* (dam-delivery) O encaminhador Http não respeita as configurações de proxy HTTP. NPR-24002: Hotfix do CQ-4244140

**Sites**

* Quando renomeamos a página enquanto movemos, a movimentação da página é bem-sucedida, mas a funcionalidade de renomeação não funciona. NPR-22923: Hotfix do CQ-4235907
* Erro ao publicar uma página de Live Copy que aponta para uma página de Importador no Adobe Campaign. NPR-23053: Hotfix do CQ-4237164
* Mover/renomear na interface clássica falha com o erro, &quot;Ocorreu um erro ao mover a página&quot; e não é renomeado. NPR-23051: Hotfix do CQ-4235907
* A alternância do conteúdo da exibição em Coluna para a exibição em lista renderiza uma página em branco e aciona uma Exceção de ponteiro nulo para páginas com OffTime definido e OnTime como em branco. NPR-22968, NPR-23052: Hotfix do CQ-4238940

**Comércio**

* Correção do teste de hobbes principal com falha (módulo CQ/Commerce). Hotfix do CQ-4253494

**Vulnerabilidade**

* A integração do Salesforce está vulnerável à Falsificação de solicitação do lado do servidor (SSRF). NPR-24289: Hotfix do CQ-4245277
* Falsificação de solicitação do lado do servidor (SSRF) e script entre sites (XSS) em ReportingServicesProxyServlet. NPR-24657: Hotfix do CQ-4246880
* Script entre sites (XSS): Refletido em commerce createwizard.html/content. NPR-24642: Hotfix do CQ-4237017
* Criação de script entre sites (XSS) nos links de Projeto da interface do usuário do administrador. NPR-23272: Hotfix do CQ-4241795

**WCM - Componentes do Foundation**

* Abrir o seletor de Design resulta em uma exceção de ponteiro nulo. NPR-23047: Hotfix do CQ-4238736

**Interface do usuário**

* (Coral3 Datepicker) Adicione suporte para typeHint para salvar valores como &quot;String&quot;. NPR-23398: Hotfix do Granite-21194
* A tradução internacionalizada não funciona no nível da língua. NPR-22967, NPR-23046: Hotfix do Granite-21111
* Backport pró-ativo para correções do granite.ui.commons. NPR-23537
* Backport pró-ativo para granite.ui.content fixes. NPR-23535
* Backport pró-ativo para correções do granite.ui.coralui. NPR-23538
* Não é possível remover vários usuários do grupo ao mesmo tempo. NPR-23846
* (OMEGA) Reportar &quot;Recurso&quot; somente em inglês. NPR-23989: Hotfix do Granite-21231
* (Importador de design) A importação de uma página não importa o js, o css. NPR-25203: Hotfix do Granite-22236

**Integração**

* ResourceResolver não bloqueado em com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix do CQ-4236515
* O TargetContentImpl deixa o AEM lento durante consultas de longa duração. NPR-22359: Hotfix do CQ-4236907
* O mecanismo do Target (mbox.js, at.js) não usa URLs danificados e usa URLs que contêm dois pontos, que podem falhar em determinadas implantações. NPR-22434: Hotfix do CQ-4237854
* No modo Target, os autores podem modificar um componente herdado do blueprint sem cancelar a herança. NPR-22865: Hotfix do CQ-4237907
* (Personalização) Os ícones são deformados ao alternar para a exibição de Cartão. NPR-23373, NPR-23374: Hotfix do CQ-4240018, CQ-4240019
* (Personalização) O console Público-alvo não mostra os tipos nt:folder . NPR-23375: Hotfix do CQ-4242293
* Quando um componente é direcionado na instância de publicação, a oscilação é exibida mostrando a experiência padrão antes da experiência direcionada. NPR-23415: Hotfix do CQ-4242038
* (Console do Adobe IMS) A configuração do serviço AccessTokenProvider OSGi é exibida novamente após a exclusão. NPR-23520: Hotfix do CQ-4208250
* A replicação de referência de configuração falha com a estrutura de pasta intermediária. NPR-23485: Hotfix do CQ-4242751
* (Personalização) clientlib bloqueado pelo servlet proxy. NPR-23521: Hotfix do CQ-4240995
* (Console do Adobe IMS) As Soluções da nuvem registradas não são selecionadas no assistente de configuração. NPR-23977: Hotfix do CQ-4244549
* Loop infinito ao carregar conteúdo direcionado em páginas sem uma extensão HTML. NPR-23522: Hotfix do CQ-4223600
* A ativação falha para uma página com referências de configuração do Dynamic Tag Management herdadas. NPR-23485: Hotfix do CQ-4242751

**Plataforma**

* (Interface do usuário clássica)(interface do usuário de toque) O seletor de tags não é exibido e gera uma exceção ao tentar procurar tags por meio de um predicado de tags no esquema Pesquisa de ativos. NPR-23049: Hotfix do CQ-4239371
* (Interface clássica) Os componentes que usam xtype=tags retornam nulo e não podem ser selecionados na lista de dentes de tags. NPR-23050: Hotfix do CQ-4239937
* (Marca) A caixa de diálogo de aceitação menciona o Adobe Marketing Cloud em vez do Adobe Experience Cloud. NPR-23210: Hotfix do CQ-4237799
* A opção de filtro deixa AEM lento após a atualização da versão 6.3 para a 6.4. NPR-23260: Hotfix do CQ-4239847 (para verificar)
* Backport pró-ativo para correções granite.omnisearch.core. NPR-23536
* Backport pró-ativo para correções de platform.clientlibs. NPR-23569
* Herança da configuração Cloud Service interrompida ao editar outras propriedades da página. NPR-23216: Hotfix do CQ-4239782
* Ativação do suporte STARTTLS no Day CQ Mail Service. NPR-23941: Hotfix do CQ-4240397

**Projetos**

* (Fragmento de conteúdo) A cópia de idioma para o ativo incorporado não é criada enquanto o ativo em inglês é adicionado à tradução. Hotfix do CQ-4243477
* A lista suspensa de configuração do msft está mostrando a configuração de /libs(6.4 configs) em vez de /etc(6.3 configs) no modo herdado. Hotfix do CQ-4243475
* Promover e excluir automaticamente inicializações de tradução em projetos de tradução. Hotfix do CQ-4243474
* Fragmento de conteúdo dentro de sites que não está sendo traduzido. Hotfix do CQ-4243482, CQ-4243483, CQ-4245687
* Erro do servidor ao abrir o filtro de pesquisa do trabalho de tradução. Hotfix do CQ-4236813
* A lista suspensa de configuração de credencial fica em branco mesmo depois que tif está presente em /conf/we-retail. Hotfix do CQ-4236315
* Abrir KPI do Projeto: degradação de desempenho conforme mais projetos são criados. NPR-23840: Hotfix do CQ-4238392
* Iniciador do fluxo de trabalho não pode aceitar o valor TypeHint de String. NPR-23863: Hotfix do CQ-4238356

**Comunidades**

* Vulnerabilidades de segurança na versão 1.0 do Handlebars. NPR-23636: Hotfix do CQ-4243055
* A permissão em massa de mensagens sinalizadas não está funcionando. NPR-23867: Hotfix do CQ-4243962
* O valor padrão não é exibido no botão de classificação no componente do fórum. NPR-23882: Hotfix do CQ-4243375
* Problemas com o delivery de mensagens de sites da Comunidade para grupos. NPR-23935

**Fluxo de trabalho**

* O Serviço de notificação por email do fluxo de trabalho do Day CQ aciona um email por nó Mongo para notificações WorkflowCompleted e WorkflowAborted. NPR-22515: Hotfix do CQ-4238172
* A execução do fluxo de trabalho do ativo de atualização do DAM gera um NullPointerException. NPR-23010: Hotfix do Granite-21096
* A etapa Processo de fluxo de trabalho não exibe scripts de /etc/workflow/scripts. NPR-23263: Hotfix do Granite-20775
* A Etapa dinâmica do participante do fluxo de trabalho não exibe scripts de /apps/workflow/scripts. NPR-23464: Hotfix do Granite-21276
* Não é possível editar qualquer fluxo de trabalho depois de editá-lo uma vez. NPR-23742: Hotfix do CQ-4238526
* (Interface clássica) Ao editar os inicializadores do fluxo de trabalho, as condições desaparecem, fazendo com que os fluxos de trabalho sejam iniciados sem condições. NPR-23835: Hotfix do CQ-4239153
* Caixa de entrada do projeto: a alternância para a exibição de calendário mostra o conteúdo principal da caixa de entrada. NPR-23947: Hotfix do CQ-4241236
* É necessário expor os detalhes da carga no pacote para que o componente HTL possa exibir o valor na exibição de lista. NPR-23948: Hotfix do CQ-4240953
* Não é possível armazenar dados de diálogo na etapa Participante da caixa de diálogo. NPR-23965: Hotfix do CQ-4234123
* (Interface do usuário de toque) Ao salvar um modelo de fluxo de trabalho, o botão &quot;Sincronizar&quot; é alterado para &quot;Sincronizado&quot;, resultando em erro ortográfico. Hotfix do CQ-4244843
* Caixa de entrada do projeto: a alternância para a exibição de calendário mostra o conteúdo principal da caixa de entrada. Hotfix do CQ-4244436
* Não é possível selecionar Diálogos na etapa Participante da Caixa de Diálogo. Hotfix do CQ-4244532
* Backport pró-ativo para correções granite.omnisearch.core. NPR-23536
* Problema no aplicativo Mobile Workspace 6.4 com a tarefa compartilhada. NPR-26383

**WCM - Tradução**

* (Painel de referência) Os trabalhos de tradução não estão sendo executados durante a criação do projeto. Hotfix do CQ-4245327

**WCM - MSM**

* (MSM) Melhoria no desempenho da implantação. Hotfix do CQ-4231488
* (MSM) Intervalo de tempo no Acompanhamento de evento entre o evento realmente acontecendo e o manuseio de evento. Hotfix do CQ-4227766

**Screens**

* A página de tela falha com erro devido à falta de dependências para screens-core-pkg:1.4.42. Hotfix do CQ-4245918

**Projetos - Tradução**

* (Fragmento de conteúdo) A cópia de idioma para o ativo incorporado não é criada enquanto o ativo em inglês é adicionado à tradução. Hotfix do CQ-4243477
* A lista suspensa de configuração do msft está mostrando a configuração de /libs(6.4 configs)em vez de /etc(6.3 configs) no modo herdado. Hotfix do CQ-4243475
* Promover e excluir automaticamente inicializações de tradução em projetos de tradução. Hotfix do CQ-4243474
* Fragmento de conteúdo dentro de sites que não está sendo traduzido. Hotfix do CQ-4243482, CQ-4243483, CQ-4245687
* Erro do servidor ao abrir o filtro de pesquisa do trabalho de tradução. Hotfix do CQ-4236813
* A lista suspensa de configuração de credencial fica em branco mesmo depois que tif está presente em /conf/we-retail. Hotfix do CQ-4236315

**Gerenciamento de fragmentos de conteúdo**

* A exclusão de componentes preenche logs com rastreamentos de pilha. Hotfix do CQ-4242315

**DAM - Geral**

* Fechar a visualização detalhada de um ativo retorna à página de resultados de pesquisa incorreta. Hotfix do CQ-4240960
* (Camera Raw) A opção de ajuste de imagem está ausente. Hotfix do CQ-4246121
* IndexOutOfBoundsException: Relatório de modificação de ativos OOTB. Hotfix do CQ-4239744
* Remova a pontuação de confiança do csv do relatório. Hotfix do CQ-4241491
* Entrega de email de compartilhamento de link interrompida para remetente que não é de &quot;administrador&quot;. Hotfix do CQ-4240357
* Correção de falhas de TI. Hotfix do CQ-4249891

**DAM - Brand Portal**

* As propriedades do ativo listam apenas 3 propriedades na primeira guia, e todas as guias ficam vazias. Hotfix do CQ-4242503
* Os predicados de tipo de arquivo e tamanho de arquivo não estão disponíveis no formulário de pesquisa publicado. Hotfix do CQ-4242026
* A pesquisa no predicado de diretório deve ser filtrada/não mostrada nos filtros de pesquisa. Hotfix do CQ-4241386
* A pesquisa padrão de deve existir após a despublicação. Hotfix do CQ-4241383, CQ-4241113
* Publicar no gesto do brand portal não funciona para predefinições de imagens. Hotfix do CQ-4241074
* Publicar no Brand Portal não funciona para coleções. Hotfix do CQ-4241122, CQ-4246558

**DAM - Cliente DM**

* Atualizar para 6.4 remove os perfis de codificação de vídeo criados anteriormente. Hotfix do CQ-4244067
* O atributo Texto alternativo é quebrado no componente Dynamic Media. Hotfix do CQ-4244081
* (DMS7) A edição de conjuntos remotos no AEM não é substituída no Scene7. Hotfix do CQ-4243430
* Verificação da build 6.4 SP1 no DM Hybrid. Hotfix do CQ-4244623
* (DMS7-UA) Ao clicar no botão Incorporar de um ativo de vídeo publicado, nada parece acontecer. Espera-se que a caixa de diálogo Incorporar seja exibida com o código HTML. Hotfix do CQ-4245237
* (DM híbrido) A URL de cópia para ativos de vídeo publicados ou conjuntos de mídia mista fica &quot;`[object Object]`&quot; na caixa de diálogo URL. Hotfix do CQ-4245236, CQ-4245451
* (DMHybrid) A página Exibição de detalhes do vídeo não contém a visualização da exibição do ativo de vídeo e gera uma mensagem de erro no console. Hotfix do CQ-4244320
* Codificação automática do S7 do conteúdo we.retail. Hotfix do CQ-4242253
* As predefinições de processamento de vídeo de pré-atualização não podem ter uma nova predefinição de codificação de vídeo adicionada nem editar as predefinições de codificação existentes. Hotfix do CQ-4240407
* As Predefinições de imagem de pré-atualização são mostradas como Não publicadas na página Representações e não produzem URL. Hotfix do CQ-4240406
* (CSS) Os ativos são mostrados, mas os visualizadores usados são padrão e não os visualizadores OOTB. Hotfix do CQ-4239839
* Desativação da limpeza etapa de interrupção da execução manual e uso de classes de coral privadas. Hotfix do CQ-4239729
* O visualizador de imagens está gerando um erro e não exibe o recorte inteligente correto. Hotfix do CQ-4237564
* A predefinição herdada em /etc parece estar quebrada e não foi migrada para o local em /conf ao salvar. Hotfix do CQ-4237416
* Regressão no OOB VideoViewer 5.8.x - o visualizador expande o iframe para a direita, quebrando assim o layout da página. Hotfix do CQ-4235465
* (DMS7) O URL de renderização do Recorte inteligente e os botões Incorporar estão ativos para imagens que não foram publicadas. Hotfix do CQ-4233696
* (DMHybrid) Restaure o recurso de cortar/girar anterior. Hotfix do CQ-4239489
* Ao visualizar um vídeo na exibição de cartão, o botão Reproduzir não alterna para pausar. Hotfix do CQ-4238592
* Ao executar uma atualização de Opt-in, a configuração do YouTube não é movida/copiada de seu local antigo para o novo local. Hotfix do CQ-4238590
* O DropDois Perfis de processamento de vídeo AVS OOTB são listados em Propriedades da pasta e apenas um contém codificações definidas. Hotfix do CQ-4238096
* (DMS7) Recorte inteligente: Exibição de detalhes: O botão URL é rotulado como Botão Copiar para renderizações. Hotfix do CQ-4237804
* A página de listagem Predefinição do visualizador permanece em branco mesmo após a execução dos comandos curl. Hotfix do CQ-4243246
* Desativado o passo de limpeza suspender a execução manual e o uso de classes de coral privadas. Hotfix do CQ-4239729
* A página Detalhes do relatório de vídeo não mostra o ativo de vídeo. Hotfix do CQ-4246208

**DAM - DMServices**

* (DMS7) Configuração da nuvem: Não é possível sincronizar o novo conteúdo com o Scene7 após a atualização para o SP1. Hotfix do CQ-4244437
* (DMHybrid) Perfis de cores e configurações de catálogo não estão sendo registrados em uma chamada debug_info=catalog. Hotfix do CQ-4242346
* Adicione perfis de cores às configurações do cliente nos servidores de entrega. Hotfix do CQ-4241818, CQ-4241819
* (DMHybrid) Depois de 6,3 &amp;gt; Atualização 6.4, as configurações do catálogo são movidas para o nó incorreto. Hotfix do CQ-4239974, CQ-4239975
* O script pushviewerpresets (DMHybrid) não cria os nós necessários para modificar as configurações do catálogo. Hotfix do CQ-4240076
* Ao usar a seleção suspensa &quot;Formatar&quot; e selecionar os formatos PNG ou JPG, o arquivo baixado é mostrado como saturado e mais escuro que o ativo original. Hotfix do CQ-4240073
* (DMS7) Remova o mapeamento de Tipo MIME: image_x-eps. Hotfix do CQ-4240394
* (DMS7) Os parâmetros de upload para o plano de fundo de nocaute não passam pelo ipsApiService.log e, portanto, não funcionam. Hotfix do CQ-4240686
* A atualização de perfis de processamento de imagem criados em uma instância 6.3 para 6.4 quebra a propriedade &quot;Tipo de corte&quot;. Hotfix do CQ-4237739
* (Dynamic Media) O upload de ativos comuns fora da pasta smartcortar falha. Hotfix do CQ-4237670
* Ajuste o código de fallback do perfil para o nome do perfil &quot;Codificação de vídeo adaptável&quot; para &quot;Adaptive_Video_Encoding&quot;. Hotfix do CQ-4237666
* Os dados EmbedXMP são sempre definidos como &quot;ativos&quot; para o processo de geração de Ptiff. Hotfix do CQ-4234498
* A representação de imagem CMYK tem saturação incorreta. Hotfix do CQ-4235470
* As configurações do Servidor de imagem não são replicadas para entrega enquanto os logs de replicação as marcam com êxito. Hotfix do CQ-4239480, CQ-4239046
* (DMS7) Não é possível criar conjuntos usando referências antigas/novas para a Configuração da nuvem. Hotfix do CQ-4238078
* A etapa do fluxo de trabalho do Scene7 lê apenas o Scene7 no nome e na descrição, mas não esclarece a etapa do fluxo de trabalho no fluxo de trabalho de atualização do DAM. Hotfix do CQ-4237865

**DAM - Tags inteligentes**

* Introduzido [Tags inteligentes aprimoradas](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Forms**

As correções do AEM Forms são entregues por meio de pacotes complementares e outros instaladores de patches fornecidos com a versão. Para obter mais detalhes, consulte Versões do AEM Forms.

Os principais destaques do AEM Forms são:

* AEM Forms apresenta [recurso de relatórios de transação](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) para rastrear e manter a contagem de transações, como formulários enviados, documentos processados e documentos renderizados na implantação do AEM Forms. Ele fornece insights sobre o uso do produto e ajuda os usuários de negócios a entender os volumes de processamento digital.
* Ativação do suporte PDF/UA para formulários XML.
* Adição de allowProxy = true para Clientlib **aemfd.ccm.channel.contentpage**
* Atualização do código para fazer pesquisa de título avançada como contém em vez de igual.
* Atualize para a nova versão do Gerenciador de pacotes de nós (NPM) no Computador de integração contínua.

**Pacote complementar do Forms**

**Integração de backend**

* Um erro é gerado ao fornecer um valor nulo como um valor para um campo opcional. NPR-24397
* A chamada de WSDL está falhando quando o elemento tem namespace diferente do global. NPR-24281
* (FDM WSDL) Obtendo DermisException: Dados de lista com exceção no caso de matriz de tipo de propriedade. NPR-24265
* (FDM WSDL) Obtendo DermisException: java.lang.Exception: createSOAPParam: Params Inválidos. NPR-24264
* (SDK do cliente do FDM) Não é possível fazer testes do pré/pós-processador e da ação de envio personalizada. Hotfix do CQ-4238469
* Correções de problemas de Javadoc em Dermis. Hotfix do CQ-4244250
* Entrada aprimorada em WSDL (Web Services Description Language). Hotfix do CQ-4244133
* O teste de autenticação básica para WSDL resulta em um erro diferente para a mesma configuração no AEM 6.3 e AEM 6.4. Hotfix do CQ-4244132
* Solicitação para incluir ValueUtil no sdk do cliente e javadocs. Hotfix do CQ-4242803
* (Configuração da nuvem FDM) Não é possível configurar a Autenticação baseada em SOAP a partir da configuração da nuvem. Hotfix do CQ-4238462
* Dermis - Adicione pacotes ausentes no Javadocs. Hotfix do CQ-4242815
* WSDLInvokerParams a ser incluído no sdk do cliente do complemento Forms. NPR-23381: Hotfix do CQ-4240233

**Formulários adaptáveis**

* A representação do documento (IC) deve ser registrada como uma transação usando o Serviço de Registro de Transações. Hotfix do CQ-4245333
* Durante a execução do UAT5, uma entrada está ausente no pdf gerado no estágio de verificação. Hotfix do CQ-4243184
* Caso de teste para obter uma cópia detalhada do guideContext. Hotfix do CQ-4242924
* O campo de tipo de prova está ausente na execução do UAT3 no servidor atualizado mais recente. Hotfix do CQ-4243120
* No servidor atualizado, o formulário enviado não possui os valores Estado/Província/Região e País presentes no servidor de pré-atualização. Hotfix do CQ-4241444
* Erro (ExpressionEditor) ao navegar até o estágio Verificar durante o envio do formulário. Hotfix do CQ-4241384
* Os valores estão ausentes no estágio de verificação no servidor pré-atualizado e atualizado para o formulário enviado. Hotfix do CQ-4241896
* O botão Sair e salvar na parte inferior da página não está funcionando. Hotfix do CQ-4240112
* Número de contato ausente na configuração atualizada. Hotfix do CQ-4239870
* Em `ACTION TAKEN` seção na guia Tipo de litígio , &quot;Documentos adicionais para suportar minha solicitação&quot; tem um campo adicional Tipo de prova salvo &quot;nela. Hotfix do CQ-4239873
* Erro &quot;getDataAPI&quot; encontrado no estágio verifyPdf. Hotfix do CQ-4239865
* Erros nos logs de migração para a instância de criação e publicação. Hotfix do CQ-4239365
* Erros nos logs de migração para a instância de criação e publicação. Hotfix do CQ-4239635
* Erro de desserialização, como &quot;Deserialização não permitida para a classe sun.util.calendar.ZoneInfo&quot; em registros de erro após o envio de um formulário adaptável. Hotfix do CQ-4240419
* O campo de estado não está sendo preenchido na representação do formulário móvel. Hotfix do CQ-4240597
* Remova o uso de referência de componentes em modelos da lista anti-padrão. Hotfix do CQ-4239217
* HTML5 Caixa numérica definida como Flutuante ou Decimal fornece resultados de validação diferentes em navegadores diferentes. NPR-23528: Hotfix do CQ-4244097
* (Carregamento de imagem) A imagem não é exibida na visualização DOR. Hotfix do CQ-4243178
* O servidor JEE gera um erro ao tentar enviar o formulário adaptável com &quot;PDF de email&quot; e &quot;Incluir anexos&quot;. Hotfix do CQ-4239894
* O gráfico não é plotado no tempo de execução usando tabela/painel. Hotfix do CQ-4240010
* O envio do formulário adaptável não está funcionando e nenhuma alteração na contagem de transações devido a falha no envio. Hotfix do CQ-4246125
* (Escolha de Imagem) O documento de opções de registro não está visível. Hotfix do CQ-4236976
* A interface do usuário do editor de modelos não é estável. Hotfix do CQ-4241497
* As AFs não são exibidas usando a guia ativos do painel lateral, enquanto são exibidas usando a opção Procurar para AEM caixa de diálogo de propriedade de componente de formulário. Hotfix do CQ-4236751
* A ID de fluxo de trabalho gerada para conversão de formulário deve estar disponível no Formulário adaptável gerado. Hotfix do CQ-4240014
* Não é possível selecionar o modelo para criar uma página em sites na Atualização direta: Livecycle para servidor 6.4. Hotfix do CQ-4241300

**Serviço de Assembler**

* Registro de transações nos Serviços do Assembler. Hotfix do CQ-4245018, CQ-4245017, CQ-4245016.
* A transação não é reportada quando a conversão de PDF/A é feita usando DDX. Hotfix do CQ-4246039

**Gerenciador do Forms**

* Lista de botões FM CREATE para ser classificada alfabeticamente. Hotfix do CQ-4242307

**Portal do Forms**

* Os rascunhos salvos no servidor de pré-atualização não são abertos corretamente no servidor atualizado. Hotfix do CQ-4243303
* Atualização da versão para 7.1 para adobe-formsmanager-core-module. Hotfix do CQ-4245753
* Os rascunhos salvos no servidor de pré-atualização não são abertos corretamente no servidor atualizado. Hotfix do CQ-4243303
* Os cenários de anexo estão quebrando ao substituir/adicionar/remover anexos em nova instância/mesma instância de rascunho. Hotfix do CQ-4243165
* A contagem de rascunhos recuperados do query do banco de dados é superior à contagem de rascunhos presentes no portal. Hotfix do CQ-4241489
* O Forms enviado no servidor de pré-atualização não está presente no servidor atualizado. Hotfix do CQ-4241490
* O formulário exibido na interface do usuário na guia envios está em estado Não enviado, apesar da mensagem de envio bem-sucedida. Hotfix do CQ-4241487
* O guideContext deve ser formado pela cópia detalhada dos campos, pois guideContext contém customPropertyMap que é um objeto. Hotfix do CQ-4240126
* Erro ao tentar salvar um formulário. Hotfix do CQ-4240763
* A entrada para formulários salvos e enviados está sendo preenchida em crx/de, apesar de termos a configuração do banco de dados fornecida no Rascunho e na Configuração de Envio do Forms Portal. Hotfix do CQ-4240726
* (Pesquisar &amp; Lister) O valor fixo do título de pesquisa avançada deve funcionar como contém em vez de igual. Hotfix do CQ-4245499

**Formulários para publicação de conteúdo para dispositivos móveis**

* O campo de data está sobreposto no Mobile Forms. Hotfix do CQ-4242256
* O envio de formulário para Forms móvel deve ser registrado como uma transação usando o Serviço de registro de transações. Hotfix do CQ-4246166
* O envio de formulário no Conjunto de formulários deve ser registrado como uma transação usando o Serviço de registro de transações. Hotfix do CQ-4246165

**Aplicativo AEM Forms**

* (Aplicativo do Windows) Não é possível renderizar o formulário. Hotfix do CQ-4238005

**OSGI do fluxo de trabalho**

* Logon de transação na tarefa Atribuir fluxo de trabalho. Hotfix do CQ-4244440
* (Etapa do FDM) Não é possível usar valores dos metadados do fluxo de trabalho quando uma etapa Atribuir tarefa é inserida entre a etapa do processo e a etapa do fdm. Hotfix do CQ-4241472
* A delegação de tarefa de atribuição não funciona na Integração do Forms em Workflows OSGI. NPR-23709: Hotfix do CQ-4243700
* (Editor de modelo de fluxo de trabalho) Alguns modelos de fluxo de trabalho não são editáveis por meio do editor de modelo WF da interface clássica. Hotfix do CQ-4241151

**Documento de vários canais**

* O campo Data no Modelo está sobrepondo o subformulário na criação de IC. Hotfix do CQ-4240110
* O cabeçalho não deve ser excluído ou movido para cima e para baixo na criação de canais Web IC. Hotfix do CQ-4243358
* (Editor de IC) Linhas padrão a serem definidas como 1 para componentes de Tabela. Hotfix do CQ-4244848
* Área de destino para permanecer visível mesmo depois que o conteúdo for arrastado e solto nela. Hotfix do CQ-4244534
* O canal da Web não reconhece o espaço de guias nos Fragmentos do Documento de Texto. Hotfix do CQ-4244481
* (Canal de impressão) A representação do documento (IC) deve ser registrada como uma transação usando o Serviço de Registro de Transações. Hotfix do CQ-4245335
* (Canal da Web) A representação de documento (IC) deve ser registrada como uma transação usando o Serviço de Registro de Transações. Hotfix do CQ-4245334
* A Pesquisa do contêiner de documento ou a Pesquisa da árvore do modelo de dados deve ser unificada para a pesquisa do filtro Ativo. Hotfix do CQ-4242305
* (Fragmento do documento) A propriedade de recuo recua o texto em quantas unidades não podem ser compreendidas. Hotfix do CQ-4241082, CQ-4240643
* (Editor de IC) O ícone Editar fragmento no bloco do fragmento do documento listado na guia Ativos não é muito fácil de ser descoberto e compreensível. Hotfix do CQ-4241047
* Permitir acesso anônimo à biblioteca de clientes inacessível do IC Anonymous. Hotfix do CQ-4245588
* (Canal da Web) Os dados não são resolvidos em nenhuma das tabelas na visualização da Web e são mostrados como em branco. Hotfix do CQ-4244476
* Os cabeçalhos de tabela são mostrados como variáveis no canal da Web na geração automática. Hotfix do CQ-4244242
* (Editor de IC) O conteúdo de um Fragmento de documento usado em um IC deve ser automaticamente redimensionado para se ajustar à largura da Área de destino. Hotfix do CQ-4244094
* O nome do canal mostrado no topo central deve ser consistente com o título de IC para WEB / IMPRESSÃO. Hotfix do CQ-4242498
* Editor de texto Painel de objeto de dados deve listar somente as entidades de nível superior, Hotfix do CQ-4244121
* O nome padrão não é atribuído ao adicionar um novo componente no editor. Hotfix do CQ-4244691
* Adicionar a configuração Colspan em todos os componentes do canal da Web. Hotfix do CQ-4244946
* A propriedade Largura da tabela do fragmento de layout não está sendo redefinida e respeitada no Canal de impressão Carta ou Comunicação do cliente. Hotfix do CQ-4241574

**Gerenciamento de correspondência**

* Legendas removidas do modelo de carta após a edição de um ativo de texto que contém espaços reservados. NPR-24196
* O arquivo XDP, quando carregado e usado como layout para modelos de carta, não consegue visualizar ou editar os modelos. NPR-24143: Hotfix do CQ-4244407
* A seleção de atribuição é selecionada por padrão no fragmento de lista. Hotfix do CQ-4240097
* Editor de condições - A avaliação de vários resultados deve ser habilitada por padrão. Hotfix do CQ-4240096
* A imagem quando excluída da Lista ainda mostra a imagem na visualização. Hotfix do CQ-4239909
* O conjunto de regras no módulo de condição é definido como &quot;Padrão&quot; para todos os módulos. Hotfix do CQ-4239878
* A criação do Dicionário de dados falha com o erro &quot;Exceção JCR desconhecida&quot;. Hotfix do CQ-4244122
* Lacunas no JavaDocs de conteúdo 6.3. Hotfix do CQ-4213586

**Instalador do Forms JEE**

**Núcleo**

* (Espaço de trabalho do HTML) Os detalhes de rastreamento estão ausentes em aplicativos com o símbolo de parênteses no nome. NPR-23402

**Serviço PDFG**

* Logon de transação em serviços PDFG. Hotfix do CQ-4244951, CQ-4244586
* Redução de PDF ao desincorporar seletivamente fontes por meio de uma única chamada de API. NPR-23287
* As configurações de PDFG atualizam o problema AEM atualização. Hotfix do CQ-4241176
* Registro de transações no Serviço PDFUtility. Hotfix do CQ-4245014

**Gerenciamento de processos**

* (Espaço de trabalho HTML) Os pontos de partida do processo não são classificados em ordem alfanumérica. Hotfix do CQ-4239629
* (HTML workspace) Prepare a chamada de dados que aparece duas vezes quando o rascunho é aberto pela primeira vez. Hotfix do CQ-4243280
* (HTML Workspace) O processo de preparação de dados é acionado ao fechar um formulário. Hotfix do CQ-4239456
* O espaço de trabalho trava quando atravessado entre duas tarefas. Hotfix do CQ-4237125

**Workbench**

* Gerenciar perfil de ação O processo de preparação de dados falha quando a configuração padrão do processo de renderização é definida como HTML. Hotfix do CQ-4244292

**Forms Designer**

* Adicione suporte PDF/UA a formulários XML gerados pelo Designer e pelo Serviço de saída. NPR-23022
* Os hiperlinks em linha definidos no Designer não são marcados nem têm texto alternativo quando salvos como PDF a partir do Designer. NPR-23023

**Feature Packs incluídos**

**Ativos**

* Adição da capacidade de Tags inteligentes aprimoradas. Para obter mais informações, consulte [Tags inteligentes aprimoradas](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951: Hotfix do CQ-4234883
* Introdução às referências da AEM Assets no InDesign. Para obter mais informações, consulte [Referências do AEM Assets no InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Criação de página) Melhorias no Editor de imagens. Para obter mais informações, consulte [Editor de imagens](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24267: Hotfix do CQ-4245502

**Pacotes OSGi e pacotes de conteúdo incluídos**

O texto seguinte documenta a lista de pacotes OSGi e os pacotes de conteúdo incluídos no CFP.

Lista de pacotes OSGi incluídos no AEM 6.4.1.0

[Obter arquivo](assets/6_4_1_0_bundle-list.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.1.0

[Obter arquivo](assets/6_4_1_0_content-package-list.txt)

### Instalar 6.4.8.0 {#install}

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
>Para clientes com Feature Packs instalados no AEM 6.4. Os Feature Packs opcionais fornecidos pelo Adobe têm dependências da versão de lançamento e do service pack. Se você tiver algum Feature Pack instalado, entre em contato com a equipe de Atendimento ao cliente da AEM para validar a compatibilidade desses pacotes de recursos com este service pack para o AEM 6.4.

* AEM 6.4.8.0 exige o AEM 6.4. Para obter mais detalhes, consulte [documentação de atualização](../sites-deploying/upgrade.md).
* O download do Service Pack está disponível em [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) para download.
* Em uma implantação com MongoDB e várias instâncias, instale o AEM 6.4.8.0 em uma das instâncias do autor usando o Gerenciador de pacotes.
* Antes de instalar o Service pack, verifique se você tem um instantâneo ou um backup atualizado da sua instância do AEM.
* Reinicie a instância antes da instalação. Embora isso seja necessário apenas quando a instância ainda está no modo de atualização (e esse é o caso quando a instância acabou de ser atualizada de uma versão anterior), geralmente é recomendável se a instância estava em execução por um período de tempo mais longo.

>[!NOTE]
>
>A Adobe não recomenda remover ou desinstalar o pacote AEM 6.4.8.0.

### Instalar o Service Pack por meio do Gerenciador de Pacotes {#install-the-service-pack-via-package-share}

Execute as seguintes etapas para instalar o Service Pack em uma instância do AEM 6.4 existente:

1. Baixe o pacote da Distribuição de software.

1. No AEM, faça logon no Gerenciador de pacotes e adicione o pacote AEM 6.4.8.0 baixado. Selecione o pacote carregado e clique em **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**A caixa de diálogo na interface do usuário do Gerenciador de pacotes às vezes sai imediatamente durante a instalação da versão 6.4.8.0**
>
>Portanto, é recomendável aguardar a estabilização dos registros de erros antes de acessar a instância. O usuário deve aguardar os registros específicos relacionados à desinstalação do pacote do atualizador antes de ter certeza de que as instalações foram bem-sucedidas. Geralmente isso acontece no Safari, mas pode acontecer intermitentemente em qualquer navegador.

### Instalação automática {#auto-installation}

Há duas maneiras de instalar automaticamente o AEM 6.4.8.0 em uma instância em execução:

A. Coloque o pacote em ..*/crx-quickstart/install* enquanto o servidor estiver em execução. O pacote é instalado automaticamente.

B. Use o [API HTTP do Gerenciador de pacotes](/help/sites-administering/package-manager.md) - certifique-se de usar `cmd=install&recursive=true` - para que o pacote aninhado seja instalado.

>[!NOTE]
>
>O AEM 6.4.8.0 não oferece suporte à instalação do Bootstrap.

### Validar instalação {#validate-install}

1. A página Informações do produto (*/system/console/ productinfo *) agora deve mostrar a cadeia de caracteres de versão atualizada do &quot;Adobe Experience Manager, Versão 6.4.8.0&quot; em Produtos instalados.
1. Todos os pacotes OSGI são ATIVOS ou FRAGMENTOS no Console OSGi (Use o console da Web: /system/console/bundles).
1. O pacote OSGI org.apache.jackrabbit.oak-core é na versão 1.8.17 ou superior (Use o Console da Web: /system/console/bundles).

Para determinar a plataforma certificada para execução com esta versão do AEM Sites e do Assets, consulte [Requisitos técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Após a instalação bem-sucedida do pacote, será exibida uma mensagem >informativa indicando que o conteúdo do pacote foi instalado com êxito, como **&quot;Pacote de Conteúdo AEM-6.4-Service-Pack-7 instalado com êxito.&quot;**

### Atualizar visualizadores do Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">O AEM 6.4.8.0 contém a nova versão dos visualizadores do Dynamic Media (5.10.1) que permite a verificação de nomes duplicados na página Predefinição de imagem. Os clientes do Dynamic Media são aconselhados a executar o seguinte comando para trazer as predefinições do visualizador prontas para o estado atualizado.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará novas predefinições do visualizador para o local /conf.

### Instalar o pacote complementar do AEM Forms {#install-aem-forms-add-on-package}

#### Instalar complemento do AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms. As correções do AEM Forms são entregues por meio de um pacote complementar separado.

>[!NOTE]
>
>O AEM 6.4.8.0 inclui uma nova versão do [Pacote de compatibilidade do AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). Se você estiver usando uma versão mais antiga do Pacote de Compatibilidade do AEM Forms e estiver atualizando para AEM 6.4.8.0, instale a versão mais recente do pacote de compatibilidade do AEM Forms após a instalação do Pacote de Suplementos do Forms.

1. Verifique se você instalou o AEM Service Pack.
1. Baixe o pacote complementar de formulários correspondente listado em [Versões do AEM Forms](https://helpx.adobe.com/br/aem-forms/kb/aem-forms-releases.html) para seu sistema operacional.
1. Instale o pacote complementar de formulários conforme descrito em [Instalação de pacotes complementares AEM formulários](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Instalar o instalador do AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Pule se você não estiver usando o AEM Forms no JEE. As correções no JEE do AEM Forms são entregues por meio de um instalador separado.

Para obter informações sobre como instalar o instalador cumulativo para AEM Forms JEE e configuração pós-implantação, consulte [Instalador de patches do AEM Forms JEE 0015](https://helpx.adobe.com/br/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Configurações necessárias para o NPR-21268 {#configuration-settings-required-for-npr}

Se você estiver usando a interface clássica (antiga) e tiver criado modelos de metadados usando-a, siga as etapas para executar o script JMX para preservá-las -

1. Vá para /system/console/jmx.
1. Clique em &quot;Migrar modelos de metadados&quot;.
1. Clique em &quot;migrateMetadataTemplatesAtPath&quot; e forneça o caminho da pasta no qual deseja que os modelos de metadados sejam preservados.

#### Configurações necessárias para o NPR-24536 {#configuration-settings-required-for-npr-1}

A contagem de filas compartilhadas não é atualizada, por padrão, para outros usuários quando um usuário reivindica uma tarefa. Para isso, introduzimos uma nova propriedade. Siga as etapas abaixo para configurar essa propriedade na sua instância do AEM:

1. Vá para a interface do Administrador -> Serviços -> Espaço de trabalho -> Administração global.
1. Exportar configurações globais.
1. No arquivo XML baixado, adicione a tag &lt;client_taskspollinginterval>10º&lt;/client_taskspollinginterval> Aqui, 10 é o exemplo de valor em segundos. É possível modificá-la de acordo.
1. Salve o arquivo.
1. Volte para interface do Administrador -> Serviços -> Espaço de trabalho -> Administração global.
1. Importe o arquivo xml na seção Importar configurações globais.
1. Agora você pode fazer logout do sistema e logon novamente.
1. A contagem da fila compartilhada inicia a atualização para outros usuários na área de trabalho.
1. Para desativar a pesquisa, altere o valor para 0 e importe o arquivo XML novamente.

### Uber Jar {#uber-jar}

O Uber Jar para AEM 6.4.8.0 está disponível na seção [Repositório Adobe Public Maven](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Para usar o Uber Jar em um projeto Maven, consulte o artigo [Como usar o Uber jar](../sites-developing/ht-projects-maven.md) e inclua a seguinte dependência no POM do projeto:

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
| Integração do Assets e da Adobe Creative Cloud | [O compartilhamento de pastas do AEM para a Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) foi introduzido no AEM 6.2 como uma forma de fornecer aos usuários criativos acesso aos ativos do AEM. Uma nova funcionalidade lançada no aplicativo da Creative Cloud, o Adobe Asset Link, fornece uma experiência de usuário melhor e acesso avançado a ativos do AEM diretamente do Photoshop, InDesign e Illustrator. A Adobe não fará mais aprimoramentos no recurso de compartilhamento de pastas. Embora o recurso esteja incluído no AEM, os clientes são recomendados a usar a substituição. | Adobe Asset Link ou aplicativo de desktop. Para obter mais informações, consulte o artigo [Integração da AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problemas conhecidos {#known-issues}

* Os seguintes erros e avisos podem ser exibidos durante a instalação:

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Tempo limite aguardando a conclusão da alteração de reg não registrada.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Nenhuma janela de manutenção encontrada em granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: O método unbindEmenda gerou uma exceção (java.lang.IllegalStateException: Serviço já não registrado).
Esses erros não exigem nenhuma ação, pois não afetam a instância do AEM.

### Problemas resolvidos {#resolved-issues}

**AEM 6.4.4.0**

* Nenhum erro de recurso encontrado é observado ao importar/exportar metadados. CQ-4253263
* Não é possível editar nenhum componente de imagem e propriedades de página depois de aplicar a 6.4.3.0 sobre a 6.4.2.0. CQ-4260316 e CQ-4260441 Para contornar esse problema:
   * Vá para o Gerenciador de pacotes
   * Reinstale o pacote &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * Recompilar todos os JSPs `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` OU Reinicie a instância.

### Pacotes OSGi e pacotes de conteúdo incluídos {#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de conteúdo incluídos no AEM 6.4.8.0.

Lista de pacotes OSGi incluídos no AEM 6.4.8.0

[Obter arquivo](assets/6.4.8.0_osgi_bundles.txt)

Lista de pacotes de conteúdo incluídos no AEM 6.4.8.0

[Obter arquivo](assets/6.4.8.0_content_packages.txt)

### Recursos úteis {#helpful-resources}

* [Notas de versão do AEM 6.4](../release-notes/release-notes.md)
* [Página do produto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentação do AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=pt-BR)
* Inscreva-se em [Atualizações de produtos de prioridade da Adobe](https://www.adobe.com/subscription/priority-product-update.html)

### Sites restritos {#restricted-sites-new}

Estes sites estão disponíveis somente para clientes. Se você for um cliente e precisar de acesso, entre em contato com o gerente de contas da Adobe.

* [Baixe o produto em licensing.adobe.com](https://licensing.adobe.com/).
* Atualizações, patches e pacotes de produtos para obter funcionalidade adicional em [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Suporte ao cliente via Admin Console](https://adminconsole.adobe.com/). Para obter mais informações, consulte [Nova experiência de suporte ao cliente do Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).
