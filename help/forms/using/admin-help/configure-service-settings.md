---
title: Definir configurações de serviço
seo-title: Configure service settings
description: Saiba como definir configurações de serviço.
seo-description: Learn how to configure service settings.
uuid: e95425a4-62f6-473e-b21b-d081c432e02d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2fab4b0c-e5db-47cd-b85a-4ff5ad6eb178
exl-id: be1f8c59-b5d8-4d87-af7b-1034d73e7e83
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '10683'
ht-degree: 0%

---

# Definir configurações de serviço {#configure-service-settings}

Você pode usar a página Gerenciamento de serviços para definir as configurações de cada um dos serviços que fazem parte AEM formulários. As configurações disponíveis variam, dependendo do serviço que está sendo configurado.

1. No console de administração, clique em Serviços > Aplicativos e Serviços > Gerenciamento de Serviços.
1. Pare o serviço antes de alterá-lo. (Consulte [Iniciar e parar serviços](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
1. Clique no nome do serviço que deseja configurar.
1. Se o serviço tiver uma guia Configuração, use-a para alterar as configurações do serviço. Consulte a lista de links abaixo para obter detalhes.

   >[!NOTE]
   >
   >Nem todos os serviços listados na página Gerenciamento de Serviços têm uma guia Configuração. Para processos criados, a guia Configuração é exibida somente se você tiver adicionado um parâmetro de configuração ao processo no Workbench. (Consulte &quot;Parâmetros de configuração&quot; na * [Ajuda do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) .) *

1. Clique na guia Security e defina as configurações de segurança para o serviço. Consulte [Modificando configurações de segurança de um serviço](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Se o serviço tiver uma guia Endpoints , use-a para alterar as configurações do endpoint . Consulte [Gerenciando Endpoints](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Clique na guia Pooling e defina as configurações de pooling. Consulte [Configuração de pool para um serviço](configure-service-settings.md#configuring-pooling-for-a-service).
1. Clique em Salvar para salvar suas alterações ou em Cancelar para descartá-las.
1. Marque a caixa de seleção ao lado do nome do serviço e clique em Start para reiniciar o serviço.

## Configurações do serviço de workflow de auditoria {#audit-workflow-service-settings}

O Workbench oferece a capacidade de registrar instâncias de processo conforme elas são executadas em tempo de execução e, em seguida, reproduzi-las para observar o comportamento do processo. (Consulte [Ajuda do Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).) Para conservar espaço no sistema de arquivos do servidor de formulários, é possível limitar a quantidade de dados de gravação do processo armazenados. Você pode configurar as seguintes propriedades do serviço Serviço de Workflow de Auditoria ( `AuditWorkflowService`):

**maxNumberOfRecordingInstances:** o número máximo de gravações armazenadas. Quando o número máximo é armazenado, a gravação mais antiga é removida do sistema de arquivos quando uma nova gravação é criada. Essa propriedade é útil se você tende a criar muitas gravações e deseja remover gravações antigas automaticamente. O valor padrão é 50.

**MaxNumberOfRecordingEntries:** o número máximo de entradas de dados que podem ser armazenadas para cada gravação. As entradas de dados são informações sobre operações em andamento. Várias entradas são armazenadas para cada execução de uma operação, como se a operação foi iniciada, se a operação foi concluída e se a rota que leva à operação foi concluída. Essa propriedade é útil quando processos podem incluir muitas execuções de operação, por exemplo, quando um loop infinito é encontrado. O valor padrão é 50.

## configurações do serviço de formulários com código de barras {#barcoded-forms-service-settings}

O serviço de formulários com códigos de barras `(BarcodedFormsService)` extrai dados de códigos de barras de imagens digitalizadas. O serviço aceita um formulário com códigos de barras (TIFF ou PDF) como entrada e extrai a representação da máquina dos dados codificados pelo código de barras.

As configurações a seguir estão disponíveis para o serviço de formulários com códigos de barras.

**Ler à esquerda:** quando selecionadas, as imagens de códigos de barras são digitalizadas horizontalmente da direita para a esquerda.

**Lido à direita:** quando selecionadas, as imagens de códigos de barras são digitalizadas horizontalmente da esquerda para a direita.

**Leitura para cima:** quando selecionadas, as imagens de códigos de barras são digitalizadas verticalmente de baixo para cima.

**Ler para baixo:** quando selecionadas, as imagens de códigos de barras são digitalizadas verticalmente de cima para baixo.

>[!NOTE]
>
>Por padrão, todas as opções são selecionadas. Desmarque uma opção somente se tiver certeza de que nenhum código de barras aparecerá assim em seus formulários.

**Caminho do Arquivo Base:** O caminho do arquivo relativo ao qual os parâmetros de entrada e saída do lote para as operações Executar Trabalho de Arquivo XML e Executar Trabalho de Arquivo Simples são resolvidos. Nas configurações em cluster, o caminho do arquivo base deve ser um local do sistema de arquivos compartilhado no qual todos os nós do cluster tenham acesso de leitura/gravação.

**Nome da Fonte de Dados:** O nome da fonte de dados usada para manter informações de estado e histórico sobre trabalhos de processamento em lote. A fonte de dados especificada deve suportar transações globais (XA).

## Configurações do serviço Central Migration Bridge (obsoleto) {#central-migration-bridge-service-settings}

O serviço Central Migration Bridge ( `CentralMigrationBridge`) chama um subconjunto da funcionalidade Adobe Central Pro Output Server (Central), que inclui os comandos JFMERGE, JFTRANS e XMLIMPORT. As operações do serviço Central Migration Bridge permitem reutilizar os seguintes ativos centrais em AEM formulários:

* design de modelo (&amp;ast;.ifd)
* modelos de saída (&amp;ast;.mdf)
* arquivos de dados (&amp;ast;.dat files)
* arquivos preâmbulo (&amp;ast;.pre)
* arquivos de definição de dados (&amp;ast;.tdf)

A configuração a seguir está disponível para o serviço Central Migration Bridge.

**Diretório de instalação central:** o diretório onde o Adobe Central 5.7 está instalado.

## Conector de repositório de conteúdo para configurações de serviço EMC Documentum {#content-repository-connector-for-emc-documentum-service-settings}

O Content Repository Connector for EMC Documentum Service ( `EMCDocumentumContentRepositoryConnector`) permite criar processos que interagem com conteúdo armazenado em um repositório Documentum.

A configuração a seguir está disponível para o Content Repository Connector for EMC Documentum Service.

**Caminho padrão do objeto Asset Link:** a parte padrão do caminho no repositório Documentum para armazenar o objeto Asset Link. O caminho real consiste no caminho padrão e no local do modelo de formulário no repositório de formulários AEM.

Por exemplo, se o caminho padrão estiver definido como `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` e o modelo de formulário estiver armazenado em uma pasta `/Docbase/forms/`, o objeto Asset Link será armazenado no seguinte local:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

O valor padrão desta configuração é `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`.

## Conector de Repositório de Conteúdo para configurações de serviço IBM FileNet {#content-repository-connector-for-ibm-filenet-service-settings}

O Conector de Repositório de Conteúdo para IBM FileNet permite criar processos que interagem com o conteúdo armazenado em um repositório IBM FileNet.

A seguinte configuração está disponível para o Content Repository Connector for IBM FileNet service.

**Caminho padrão do objeto Asset Link:** a parte padrão do caminho no repositório IBM FileNet para armazenar o objeto Asset Link. O caminho real consiste no caminho padrão e no local do modelo de formulário no repositório de formulários AEM.

Por exemplo, se o caminho padrão estiver definido como `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` e o modelo de formulário estiver armazenado em uma pasta `/Docbase/forms/`, o objeto Asset Link será armazenado no seguinte local:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

O valor padrão desta configuração é `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`.

## Converter configurações do serviço PDF {#convert-pdf-service-settings}

O serviço Converter PDF ( `ConvertPdfService`) converte documentos PDF em PostScript e em vários formatos de imagem (JPEG, JPEG 2000, PNG e TIFF). A conversão de um documento PDF em PostScript é útil para a impressão automática baseada em servidor em qualquer impressora PostScript. A conversão de um documento PDF em um arquivo TIFF de várias páginas é prática ao arquivar documentos em sistemas de gerenciamento de conteúdo que não oferecem suporte a documentos PDF.

As configurações a seguir estão disponíveis para o serviço Converter PDF.

**Tipo de Transação:** Especifica como um contexto de transação deve ser propagado para uma operação.

**Obrigatório:** Suporta um contexto de transação, se existir; caso contrário, um novo contexto de transação será criado. Este é o valor padrão.

**Requer novo:** sempre cria um novo contexto de transação. Se existir um contexto de transação ativo, ele será suspenso.

**Tempo Limite da Transação (em segundos):** O número de segundos que o provedor de transação subjacente deve aguardar antes de reverter uma transação que está envolvendo essa operação. Esse valor será ignorado se um contexto de transação existente for propagado. O valor padrão é 180.

**Resolução de limite para suavização (em dpi):** A resolução da imagem abaixo da qual a suavização (ou suavização de borda) é aplicada ao texto, arte da linha e imagens, se você tiver selecionado as opções &quot;Aplicar suavização a&quot; para esses elementos.

**Aplicar suavização ao texto:** Controla a suavização de texto. Para desativar a suavização do texto e tornar o texto mais nítido e mais fácil de ler com um ampliador de tela, desmarque essa caixa de seleção.

**Aplicar suavização a LineArt:** aplica suavização para remover ângulos abruptos em linhas.

**Aplique suavização a imagens:** Aplica suavização para minimizar alterações abruptas em imagens.

## Configurações do serviço Distiller {#distiller-service-settings}

O serviço Distiller ( `DistillerService`) converte arquivos PostScript, Encapsulated PostScript (EPS) e PRN em arquivos PDF em uma rede.

As configurações a seguir estão disponíveis para o serviço Distiller.

**Configurações do Adobe PDF:** as seguintes configurações predefinidas são aplicadas ao PDF gerado:

* Impressão de alta qualidade
* Páginas com tamanho maior
* CMYK do PDFA1b 2005
* RGB do PDFA1b 2005
* PDFX1a 2001
* PDFX3 2002
* Qualidade da imprensa
* Menor tamanho de arquivo
* Padrão

Novas configurações podem ser criadas por meio da interface do usuário do Gerador de PDF.

**Configurações de segurança:** configurações de segurança pré-definidas aplicadas a documentos PDF gerados. O valor padrão é Sem segurança. Você deve criar configurações de segurança usando o Gerador de PDF e inserir a configuração aqui.

**Tamanho do Pool:** O tamanho inicial do pool. Quando o serviço Distiller é implantado, esse número é usado para determinar o número de instâncias de implementação do serviço criadas e alocadas ao pool livre aguardando solicitações de invocação. O contêiner de serviço pode responder imediatamente a solicitações de invocação sem ter que primeiro inicializar uma instância de serviço.

## Configurações do serviço Gerenciamento de documentos {#document-management-service-settings}

>[!NOTE]
>
>O Adobe® LiveCycle® Content Services ES (obsoleto) é um sistema de gerenciamento de conteúdo instalado com o LiveCycle. Ele permite que os usuários criem, gerenciem, monitorem e otimizem processos centrados em seres humanos. O suporte aos Serviços de conteúdo (obsoleto) termina em 31/12/2014. Consulte [Adobe product lifecycle document](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).

O serviço de Gerenciamento de documentos ( `DocumentManagementService`) permite que os processos usem a funcionalidade de gerenciamento de conteúdo fornecida pelos Serviços de conteúdo (obsoleto). As operações de Gerenciamento de documentos fornecem tarefas básicas necessárias para manter espaços e conteúdo no sistema de gerenciamento de conteúdo. Exemplos dessas tarefas são copiar, excluir, mover, recuperar e armazenar conteúdo, criar espaços e associações e obter e definir atributos de conteúdo.

As configurações a seguir estão disponíveis para o serviço Gerenciamento de documentos.

**Esquema de armazenamento:** o esquema da loja na qual o conteúdo está localizado. O valor padrão é espaço de trabalho.

**Porta HTTP:** a porta usada para acessar os Serviços de conteúdo (obsoleto). O valor padrão é 8080.

## Configurações do serviço de email {#email-service-settings}

O email é usado para distribuir conteúdo ou fornecer informações de status como parte de um processo automatizado. O serviço de email ( `EmailService`) permite que os processos recebam mensagens de email de um servidor POP3 ou IMAP e enviem mensagens de email para um servidor SMTP.

Por exemplo, um processo usa o serviço Email para enviar uma mensagem de email com um anexo de formulário PDF. O serviço de Email se conecta a um servidor SMTP para enviar a mensagem de email com o anexo. O formulário PDF foi projetado para permitir que o destinatário clique em Enviar após preencher o formulário. A ação faz com que o formulário seja retornado como anexo ao servidor de email designado. O serviço de Email recupera a mensagem de email retornada e armazena o formulário preenchido em uma variável de formulário de dados de processo.

As configurações a seguir estão disponíveis para o serviço de email.

**Host SMTP:** o endereço IP ou URL do servidor SMTP a ser usado para enviar email.

**Número da porta SMTP:** a porta usada para se conectar ao servidor SMTP.

**Autenticação SMTP:** selecione se a autenticação do usuário é necessária para se conectar ao servidor SMTP.

**Usuário SMTP:** o nome de usuário da conta de usuário a ser usada para fazer logon no servidor SMTP.

**Senha SMTP:** a senha associada à conta de usuário SMTP.

**Segurança de transporte SMTP:** o protocolo de segurança a ser usado para conexão com o servidor SMTP:

* Selecione Nenhum se nenhum protocolo for usado (os dados são enviados em texto claro)
* Selecione SSL se o protocolo Secure Sockets Layer for usado.
* Selecione TLS se a Segurança da camada de transporte for usada.

**Host POP3/IMAP:** o endereço IP ou URL do servidor POP3 ou IMAP a ser usado para enviar emails.

**Nome de usuário POP3/IMAP:** o nome de usuário da conta de usuário a ser usada para fazer logon no servidor POP3 ou IMAP.

**Senha POP3/IMAP:** a senha associada à conta de usuário POP3 ou IMAP.

**Número da porta POP3/IMAP:** a porta usada para se conectar ao servidor POP3 ou IMAP.

**POP3/IMAP:** o protocolo a ser usado para enviar e receber email.

**Segurança de transporte de recepção:** o protocolo de segurança a ser usado para conexão com o servidor SMTP:

* Selecione None se nenhum protocolo for usado (os dados são enviados em texto claro).
* Selecione SSL se o protocolo Secure Sockets Layer for usado.
* Selecione TLS se a Segurança da camada de transporte for usada.

## Configurações do serviço de criptografia {#encryption-service-settings}

O Serviço de criptografia ( `EncryptionService`) permite criptografar e descriptografar documentos. Quando um documento é criptografado, seu conteúdo se torna ilegível. Um usuário autorizado pode descriptografar o documento para obter acesso ao conteúdo. Se um documento PDF for criptografado com uma senha, o usuário deverá especificar a senha de abertura antes que o documento possa ser visualizado no Adobe Reader ou Adobe Acrobat. Da mesma forma, se um documento PDF for criptografado com um certificado, o usuário deverá descriptografar o documento PDF com a chave pública que corresponde ao certificado (chave privada) que foi usado para criptografar o documento PDF.

As configurações a seguir estão disponíveis para o serviço de Criptografia.

**Servidor LDAP padrão ao qual se conectar:** Nome do host do servidor LDAP usado para recuperar certificados para criptografia de documento.

**Porta LDAP padrão à qual se conectar:** Número da porta do servidor LDAP.

**Nome de usuário LDAP padrão:** se o servidor LDAP exigir autenticação, especifique o nome de usuário a ser usado para conexão com o servidor LDAP.

**Senha LDAP padrão:** se o servidor LDAP exigir autenticação, especifique a senha que corresponde ao nome de usuário a ser usado para conexão com o servidor LDAP.

>[!NOTE]
>
>Use autenticação simples (nome de usuário e senha) somente quando a conexão for protegida via SSL (usando LDAPS).

**Modo de Compatibilidade:**

## Configurações do serviço FTP {#ftp-service-settings}

O serviço FTP ( `FTP`) permite que os processos interajam com um servidor FTP. As operações do serviço FTP podem recuperar arquivos do servidor FTP, colocar arquivos no servidor FTP e excluir arquivos do servidor FTP. Por exemplo, documentos como relatórios gerados a partir de um processo podem ser armazenados em um servidor FTP para distribuição. Ou um sistema externo pode gerar alguns arquivos com base em etapas anteriores em um processo. Em uma etapa subsequente do processo, os arquivos podem ser transferidos para um local remoto.

As configurações a seguir estão disponíveis para o serviço FTP.

**Host padrão:** O endereço IP ou URL do servidor FTP.

**Porta padrão:** A porta usada para se conectar ao servidor FTP. O valor padrão é 21.

**Nome de usuário padrão:** o nome da conta de usuário que você pode usar para acessar o servidor FTP. A conta de usuário deve ter privilégios suficientes para executar as operações FTP necessárias para esse serviço.

**Senha padrão:** A senha a ser usada com o nome de usuário especificado para autenticação com o servidor FTP.

## Gerar configurações do serviço PDF {#generate-pdf-service-settings}

O serviço Gerar PDF ( `GeneratePDFService`) converte arquivos em vários formatos nativos em documentos PDF e converte documentos PDF em vários formatos de arquivo.

As configurações a seguir estão disponíveis para o serviço Gerar PDF.

**Configurações do Adobe PDF:** o nome das configurações pré-definidas do Adobe PDF a serem aplicadas a um trabalho de conversão, se essas configurações não forem especificadas como parte dos parâmetros de invocação da API. As configurações do Adobe PDF são definidas no console de administração clicando em Serviços > Gerador de PDF > Configurações do Adobe PDF. Essas configurações são aplicáveis somente às conversões baseadas no PDFMaker.

**Configurações de segurança:** o nome das configurações de segurança pré-definidas a serem aplicadas a um trabalho de conversão, se essas configurações não forem especificadas como parte dos parâmetros de invocação da API. As configurações de segurança são definidas no console de administração, clicando em Serviços > Gerador de PDF> Configurações de segurança.

**Configurações do tipo de arquivo:** o nome da configuração pré-configurada do tipo de arquivo a ser aplicada a um trabalho de conversão, se essas configurações não forem especificadas como parte dos parâmetros de invocação da API. As configurações de tipo de arquivo são definidas no console de administração, clicando em Serviços > Gerador de PDF> Configurações de tipo de arquivo.

**Use o Acrobat WebCapture (somente Windows):** quando essa configuração é verdadeira, o serviço Gerar PDF usa o Acrobat X Pro para todas as conversões de HTML para PDF. Isso pode melhorar a qualidade dos arquivos PDF produzidos a partir de HTML, embora o desempenho possa ser um pouco menor. O valor padrão é false.

**Usar conversão de imagem do Acrobat (somente Windows):** quando essa configuração for verdadeira, o serviço Gerar PDF usará o Acrobat X Pro para todas as conversões de imagem em PDF. Essa configuração é útil somente se o mecanismo de conversão Java puro padrão não conseguir converter uma proporção significativa das imagens de entrada com êxito. O valor padrão é false.

**Ativar conversões do AutoCAD baseadas em Acrobat (somente Windows):**  Quando essa configuração é verdadeira, o serviço Gerar PDF usa o Acrobat X Pro para todas as conversões de DWG em PDF. Essa configuração é útil somente se o AutoCAD não estiver instalado no servidor ou se o mecanismo de conversão do AutoCAD não conseguir converter arquivos com êxito.

**Expressões regulares para descobrir caracteres especiais proibidos no nome do usuário (somente Windows):** especifica caracteres que interferem nas operações de Export PDF e Optimize PDF quando os caracteres aparecem no nome de um usuário.

**Tamanho do Pool de ImageToPDF:** O tamanho do pool do conversor padrão (Java puro) de Imagem para PDF no serviço Gerar PDF. Essa configuração controla o máximo de conversões simultâneas de Imagem em PDF que o serviço Gerar PDF pode realizar. O valor padrão dessa configuração (recomendado para sistemas de processador único) é 3, o que pode aumentar em sistemas de multiprocessador.

**Tamanho do pool de HTML para PDF:** O tamanho do pool do conversor de HTML para PDF no serviço Gerar PDF. Essa configuração controla o máximo de conversões HTML para PDF simultâneas que o serviço Gerar PDF pode realizar. O valor padrão dessa configuração (recomendado para sistemas de processador único) é 3, o que pode aumentar em sistemas de multiprocessador.

**Tamanho do Pool de OCR:** O tamanho do pool do PaperCaptureService que o Gerador de PDF usa para OCR. O valor padrão dessa configuração (recomendado para sistemas de processador único) é 3, o que pode aumentar em sistemas de multiprocessador. Esta configuração é válida somente em sistemas Windows.

**Família de fontes de fallback para conversões de HTML em PDF:**  o nome da família de fontes a ser usada em documentos PDF quando a fonte usada no HTML original não estiver disponível para o servidor de formulários de AEM. Especifique uma família de fontes se desejar converter páginas HTML que usam fontes indisponíveis. Por exemplo, as páginas criadas em idiomas regionais podem usar fontes indisponíveis.

**Lógica de repetição para** conversões nativasRege a geração de PDF novas tentativas se a primeira tentativa de conversão falhar:

**Nenhuma tentativa**

Não tente novamente a conversão do PDF se a primeira tentativa de conversão falhar

**Tentar novamente**

Repita a conversão do PDF, independentemente de o tempo limite ter sido atingido. A duração padrão do tempo limite para a primeira tentativa é de 270s.

**Tentar novamente se o tempo permitir**

Tente novamente a conversão do PDF se o tempo consumido para a primeira tentativa de conversão for menor que a duração do tempo limite especificado. Por exemplo, se a duração do tempo limite for de 270s e a primeira tentativa consumida de 200s, o Gerador de PDF tentará novamente a conversão. Se a primeira tentativa consumiu 270, a conversão não será repetida.

## Guias das configurações do serviço Utilitários ES4 {#guides-es4-utilities-service-settings}

Quando você cria um Guia, alguns recursos, como a definição do Guia, são incorporados a ele. Os recursos também podem existir como referências aos ativos do aplicativo armazenados localmente ou no servidor de formulários AEM. O Guia não contém dados e os valores para o local de envio e entradas não são adequados para todos os ambientes externos.

Na maioria dos casos, os serviços de renderização padrão dos Guias são suficientes para preparar um Guia para uso no Workspace ou em outros ambientes externos. (Na exibição Serviços, no Workbench, o serviço padrão é Guias (sistema)/Processos/Guia de Renderização - 1.0.) O serviço Utilitários Guia ( `GuidesUtility`) permite criar um processo personalizado para renderizar um Guia, se necessário.

As operações do Guia Utilitários permitem adicionar as seguintes tarefas de renderização do Guia a um processo:

* Determine se os dados estão disponíveis para preencher o Guia com
* Incorpore os dados do Guia ou converta-os em um link
* Converter conteúdo referenciado em URLs acessíveis externamente
* Substitua valores em um documento HTML ou outro wrapper, ou converta-os em URLs que são acessíveis externamente
* Definir o local de envio
* Especificar valores de entrada
* Crie um parâmetro para representar o conteúdo referenciado
* Se houver variações disponíveis, defina uma variação

Os valores padrão para o serviço Utilitários Guia suportam a maioria dos casos de uso. No entanto, se necessário, é possível alterar os seguintes valores.

**publicPaths:** essa opção foi substituída. Não use essa opção com formulários AEM.

**pathInfoExpiryInSeconds:** o intervalo após o qual expira uma solicitação de informações de caminho de um cliente. O padrão é 1.

**collateralExpiryInSeconds:** o intervalo após o qual expira um pedido de garantia de um cliente. O padrão é 315576000.

**mismatchExpiryInSeconds:** o intervalo após o qual expira uma solicitação de garantia de um cliente, quando a eTag (tag de entidade) não corresponde. (Uma eTag é um cabeçalho de resposta HTTP.) O padrão é 1.

**guideContext:** A raiz de contexto do aplicativo web Guides. Corresponde ao valor definido usando a aplicação Web Guias. O padrão é /Guides/.

**secureRandomAlgorithm:** O algoritmo a ser usado ao gerar chaves e identificadores. Esse valor é passado para o método getInstance da classe SecureRandom Java. O padrão é SHA1PRNG.

**idBytes:** o número de bytes aleatórios a serem usados em um identificador de chave. O padrão é 6.

**macAlgorithm:** O algoritmo MAC (message authentication code) a ser usado para verificação de URL de garantia. Esse método é passado para o método getInstance da classe Mac. O padrão é HmacSHA1.

**macRefreshIntervalInMinutes:** A quantidade de tempo em que uma chave está ativa. Quando uma chave está ativa para esse intervalo, uma nova chave é gerada. A nova chave se torna a chave ativa. A chave ativa anteriormente é mantida por 10% do intervalo de atualização. Esse comportamento permite que os URLs gerados usando a chave antiga continuem a funcionar no switch principal. O padrão é 144000.

**macOverlapIntervalInMinutes:** Duração de tempo em que a chave anterior permanecerá válida após uma nova ser gerada. O padrão é 1440 minutos (1 dia).

**macKeySeed:** um valor seed para gerar o URL seguro. Quando essa é a opção , a chave nunca é atualizada. Definir a mesma seed em diferentes servidores resultará na geração de URLs seguros que são compatíveis. Isso pode ser útil se vários servidores de formulários estiverem em uso atrás de um balanceador de carga. Insira uma sequência aleatória de caracteres e números como a propagação.

### Uso de guias em um cluster de servidores {#using-guides-in-a-server-cluster}

A renderização de um Guia em um cluster de servidores que não usa sessões aderentes falha com um NullPointerException. Uma solicitação de Guias usa URLs seguros que, por padrão, são exclusivos ao servidor em que são gerados. Em um cluster que usa sessões aderentes, depois que uma solicitação atinge um nó no cluster, todas as solicitações subsequentes dessa sessão ou usuário são roteadas exclusivamente para esse servidor e tudo está bem. Em um cluster que não usa sessões aderentes, as solicitações subsequentes podem atingir qualquer servidor no cluster. Se o servidor que as solicitações acessaram não for o original, ele não resolverá o URL seguro.

Se você estiver usando Guias em um cluster de servidores que não usa sessões aderentes, defina o valor macKeySeed para o serviço GuidesUtility e pare e inicie o cluster.

O valor macKeySeed é o seed para o gerador de números aleatórios que é usado para gerar os URLs seguros. Configurar esse valor faz com que cada nó do cluster inicialize o gerador de números aleatórios da mesma maneira e tenha acesso aos mesmos URLs seguros. Você pode usar qualquer string aleatória para esse valor de seed.

Altere o valor macKeySeed quando precisar atualizar os URLs seguros. A atualização dos URLs seguros depende da sua política de segurança e é semelhante à política de atualização para alterar a senha raiz principal do servidor. O macSeedValue é análogo à senha principal para os URLs seguros, porque é usado para gerar um novo número aleatório exclusivo para uso na geração e recuperação seguras de URLs.

Você deve reiniciar o cluster porque macSeedValue é somente leitura na inicialização do sistema. Todos os nós precisam ser reiniciados para ler o valor, pois eles o usam independentemente para inicializar seus números aleatórios internos com o valor de propagação.

## Configurações do serviço JDBC {#jdbc-service-settings}

O serviço JDBC ( `JdbcService`) permite que os processos interajam com bancos de dados.

A configuração a seguir está disponível para o serviço JDBC.

**datasourceName:** Um valor de string que representa o nome JNDI da fonte de dados a ser usada para se conectar ao servidor de banco de dados. A fonte de dados deve ser definida no servidor de aplicativos que hospeda o servidor de formulários. O valor padrão é o nome JNDI da fonte de dados para o banco de dados de formulários AEM.

## Configurações do serviço JMS {#jms-service-settings}

O serviço JMS ( `JMS`) permite a interação com provedores do Sistema de Mensagens Java (JMS) que implementam mensagens ponto a ponto e publicam/assinam mensagens.

Configure o serviço JMS com propriedades padrão para que as operações de serviço possam se conectar e interagir com um provedor JMS e um serviço JNDI associado. Os valores das propriedades do serviço são definidos como valores padrão com base no JBoss Application Server. Altere esses valores se estiver usando um servidor de aplicativos diferente para hospedar formulários AEM.

As configurações a seguir estão disponíveis para o serviço JMS.

**URL do provedor:** o URL do provedor de serviços JNDI. O valor padrão é baseado no Servidor de Aplicativos JBoss. O URL a seguir são valores padrão para os servidores de aplicativos compatíveis com AEM formulários:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**Nome de usuário JNDI:** o nome de usuário da conta a ser usada para autenticação com o provedor de serviço JNDI, que é usado para procurar nomes de fila e tópico. O valor padrão é convidado.

**Senha JNDI:** A senha associada ao nome de usuário especificado para o Nome de usuário JNDI. O valor padrão é convidado.

**Fábrica de contexto inicial:** A classe Java a ser usada como a fábrica de contexto inicial. O serviço JMS usa essa classe para criar um contexto inicial, que é o ponto de partida para resolver nomes de tópicos e filas. O valor padrão é a fábrica de contexto inicial do serviço JMS no JBoss. As seguintes classes são as fábricas de contexto iniciais dos servidores de aplicativos que AEM formulários oferecem suporte:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**WebLogic:** weblogic.jndi.WLInitialContextFactory

**WebSphere:** com.ibm.websphere.naming.WsnInitialContextFactory

**Nome de Usuário da Conexão:** A senha associada ao nome de usuário especificado para Nome de Usuário da Conexão. O valor padrão é convidado.

**Senha da Conexão:** A senha associada ao nome de usuário especificado para Nome de Usuário da Conexão. O valor padrão é convidado.

**Outras propriedades:** nome da propriedade e pares de valores que você pode passar para o provedor de serviços JNDI. Essas propriedades dependem da implementação e da configuração do provedor que você está usando.

Os pares de nome e valor da propriedade são separados por ponto e vírgula **;**. Por exemplo, o texto a seguir mostra o valor que seria especificado para duas propriedades chamadas name1 e name2, com valores value1 e value2, respectivamente:

`name1=value1;name2=value2`

## Configurações do serviço LDAP {#ldap-service-settings}

O serviço LDAP ( `LDAPService`) fornece operações para consulta de diretórios LDAP. Geralmente, os diretórios LDAP são usados para armazenar informações sobre pessoas, grupos e serviços em uma organização.

As configurações a seguir estão disponíveis para o serviço LDAP.

**Fábrica de contexto inicial:** a classe Java a ser usada como a fábrica de contexto. Essa classe é usada para criar uma conexão com o servidor LDAP. O valor padrão é com.sun.jndi.ldap.LdapCtxFactory, que é apropriado para a maioria dos servidores LDAP.

**URL do provedor:** o URL a ser usado para se conectar ao serviço LDAP. O formato do valor é `ldap://server name:port`

*nome do servidor* é o nome do computador que hospeda o servidor LDAP

** portas de comunicações que o serviço LDAP usa. O valor padrão é 389, que é a porta padrão usada para conexões LDAP.

**Nome do Usuário:** O nome de usuário da conta de usuário a ser usada para fazer logon no servidor LDAP. A conta de usuário precisa ter permissão para se conectar ao servidor e ler as informações no diretório LDAP.

Dependendo do servidor LDAP, o nome de usuário pode ser um nome de usuário simples, como `myname` ou um DN, como `cn=myname,cn=users,dc=myorg`.

**Senha:** a senha que corresponde ao nome de usuário fornecido para a configuração Nome de usuário.

**Outras propriedades:** um valor de string que representa outras propriedades e seus valores correspondentes que você pode fornecer ao servidor LDAP. O valor está no seguinte formato:

`property=value;property=value;...`

## Definições do serviço de configuração do Microsoft SharePoint {#microsoft-sharepoint-configuration-service-settings}

O serviço de configuração do Microsoft SharePoint `(MSSharePointConfigService)`permite especificar credenciais para o usuário de formulários AEM que tem permissões de representação. Para obter informações sobre permissões de representação, consulte [Configuração do Conector para Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html).

As seguintes configurações estão disponíveis para o serviço de configuração do Microsoft SharePoint:

* Nome de usuário para um usuário com permissões de representação
* Senha do usuário acima

**Ativar SSL (HTTPS):**

**Time to Live:** duração, em segundos, de validade e armazenamento em cache do perfil de provisionamento no cliente. O padrão é 86400 (24 horas). Quando um aplicativo cliente sincroniza com o servidor e o tempo especificado passou, o aplicativo cliente solicita um novo perfil de provisionamento do servidor.

**Criptografia:** especifica se os dados armazenados no dispositivo móvel devem ser criptografados.

**Aplicativo Forms:** ativa o recurso Forms nos aplicativos clientes móveis. Quando essa opção é selecionada, os usuários podem abrir formulários e iniciar processos a partir de seus dispositivos móveis.

**Aplicativo de Tarefas:** Habilita o recurso Tarefas nos aplicativos clientes móveis. Quando essa opção é selecionada, os usuários podem acessar suas listas de tarefas e concluir tarefas de seus dispositivos móveis.

**Aplicativo de serviços de conteúdo:** ativa o recurso Serviços de conteúdo no aplicativo cliente móvel. Esse recurso está disponível somente para iOS. Quando essa opção é selecionada, os usuários do iPhone e do iPad podem acessar arquivos armazenados no servidor WebDAV de suas organizações.

**Suporte offline:** permite que os usuários continuem usando os aplicativos clientes móveis mesmo quando não têm uma conexão com o servidor (por exemplo, quando estão fora do intervalo de células ou no modo avião). Os usuários também devem ativar a configuração Suporte offline em seus dispositivos móveis. Esse recurso está disponível para dispositivos Android e iOS. Por padrão, esse recurso está desativado.

>[!NOTE]
>
>Se o suporte offline tiver sido ativado e você o desativar, os perfis de provisionamento dos usuários serão atualizados imediatamente ou assim que estiverem online. Se um usuário tiver trabalhado offline, todas as tarefas pendentes serão retornadas à lista de Tarefas e todos os itens em sua Fila, incluindo formulários pendentes, tarefas e formulários contendo erros de validação, serão excluídos da Fila.

**Android:** permite que dispositivos Android se conectem ao servidor.

**Apple iOS:** permite que iPhones e iPads se conectem ao servidor.

**AIR:** permite que dispositivos que executam aplicativos com base no Adobe AIR® se conectem ao servidor.

**BlackBerry:** permite que dispositivos BlackBerry se conectem ao servidor.

**Android Microsoft Exchange AtiveSync Obrigatório:** Especifica se o Microsoft Exchange AtiveSync policy manager (EA) deve estar instalado e ativo em dispositivos Android. Quando essa opção é selecionada, EA deve ser aplicada no dispositivo Android. Quando essa opção não está selecionada, nenhuma verificação é executada, embora outros requisitos ainda sejam aplicados.

**Comprimento mínimo do PIN do Android:** os dispositivos Android devem ter uma configuração global que imponha que o PIN ou a senha tenham pelo menos esse comprimento. Basta ter um PIN com o comprimento especificado não é suficiente. O comprimento do PIN deve ser aplicado pelo sistema para que os usuários não possam remover ou reduzir o PIN posteriormente. O valor padrão é 4.

**Máximo de tentativas de senha do Android antes da limpeza:** os dispositivos Android têm uma configuração global que limpa o sistema após um número especificado de tentativas de senha inválidas. Essa configuração global foi ativada e é igual ou inferior ao valor especificado aqui. O valor padrão é 5.

**Remoção da limpeza do Android:** especifica o que acontece quando uma violação de política ocorre em um dispositivo Android. Quando esta opção é selecionada, a conta é excluída. Quando essa opção não está selecionada, a senha da conta armazenada e os dados em cache são excluídos. Não são feitas mais tentativas de sincronização até que o usuário corrija a violação da política.

## Configurações do serviço de saída {#output-service-settings}

O serviço de saída `(OutputService)`permite mesclar dados de formulário XML com um design de formulário criado AEM Designer de formulários para criar um fluxo de saída de documento em um dos seguintes formatos:

* Um fluxo de saída de documento PDF ou PDF/A.
* Um fluxo de saída do Adobe PostScript.
* Um fluxo de saída PCL (Printer Control Language).
* Um fluxo de saída ZPL (Zebra Programming Language).

O fluxo de saída pode ser enviado para uma impressora de rede, uma impressora local ou um arquivo de disco. Ao usar o Serviço de saída como parte de um processo, também é possível enviar o fluxo de saída para um recipient de email como um anexo de arquivo.

As configurações a seguir estão disponíveis para o serviço Saída.

**Tipo de Transação:** Especifica como um contexto de transação deve ser propagado para uma operação:

**Obrigatório:** suporta um contexto de transação se já existir; caso contrário, um novo contexto de transação será criado. Este é o valor padrão.

**Requer novo:** sempre cria um novo contexto de transação. Se existir um contexto de transação ativo, ele será suspenso.

**Tempo Limite da Transação (em segundos):** O número de segundos que o provedor de transação subjacente aguarda antes de reverter uma transação que está envolvendo essa operação. Esse valor será ignorado se um contexto de transação existente for propagado.

Ao processar arquivos de dados grandes ou operar em um servidor ocupado, pode ser necessário aumentar o tempo limite do serviço de saída. Para alterar o valor de tempo limite, verifique se os servidores de hardware têm memória adequada e se a memória está disponível para o heap do Java Application Server. O valor padrão é `180`.

## Configurações do serviço de configuração PDFG {#pdfg-config-service-settings}

As configurações a seguir estão disponíveis para o serviço de configuração PDFG ( `PDFGConfigService`).

**Diretório de opções de trabalho do usuário:** o caminho da pasta do sistema de arquivos onde o serviço c grava os arquivos de opções de trabalho acessíveis ao Acrobat Pro Extended. O valor padrão é [user.home]/Application Data/Adobe/Adobe PDF/Settings.

**Diretório de inicialização do PS:** o caminho da pasta do sistema de arquivos onde os arquivos de inicialização exigidos pelo Adobe Acrobat Distiller são salvos. O valor padrão é [user.home]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**Arquivo de inicialização PS:** o nome do arquivo de inicialização exigido pelo Adobe Acrobat Distiller. O valor padrão é example.ps.

**Tempo limite de conversão do servidor:** o tempo limite máximo de conversão de trabalhos (em segundos) para o serviço Gerar PDF e o serviço Distiller. Essa configuração limita o tempo limite máximo de conversão que pode ser especificado no arquivo config.xml e nas páginas do console de administração para o Gerador de PDF. O valor padrão é 270.

**Tempo limite global do servidor:** ao executar conversões de PDF, um servidor de formulários considera o limite de tempo. Configure o valor do tempo limite para resolver o problema.

**Prefixo de opções de trabalho:**  um prefixo usado pelo serviço Gerar PDF para incluir uma sequência curta nos arquivos de opções de trabalho que ele cria temporariamente para uso pelo Acrobat Distiller. O valor padrão é pdfg.

**Aplicativos não Unicode:** uma lista separada por vírgulas de nomes de aplicativos que são conhecidos por serem incapazes de Unicode. Essa lista é pré-preenchida com os nomes de vários aplicativos, cujo suporte é pré-configurado no Gerador de PDF. Se você optar por adicionar suporte para conversões de PDF por meio de outros aplicativos de terceiros que não são compatíveis com Unicode, será necessário adicioná-los a essa lista. O valor padrão é Autocad, Excel, PowerPoint, Project, Publisher, Visio, Word, WordPerfect.

**Contagem de Threadpool do Servidor:** Controla o tamanho do pool de threads que o serviço Gerar PDF usa internamente para atender às solicitações de conversão de HTML em PDF que envolvem spidering (conversão de páginas vinculadas acessíveis a partir da página principal). O valor padrão é 20.

**Segundos da verificação de limpeza PDFG:** consulte a seção Segundos da expiração do trabalho para obter detalhes.

**Segundos de expiração do trabalho:** o serviço Gerar PDF exclui os arquivos de entrada assim que são convertidos. Ele armazena arquivos de saída temporariamente, por um período determinado pelas configurações de Segundos de Verificação de Limpeza de PDFG e Segundos de Expiração de Trabalho.

A configuração Segundos da expiração do trabalho especifica a idade de um arquivo ou pasta vazia antes de ser elegível para exclusão. A configuração Segundos da varredura de limpeza de PDFG especifica a frequência com que um thread de limpeza verifica as pastas temporárias em busca de arquivos que podem ser excluídos.

Por exemplo, se Job Expiration Seconds estiver definido como 100 e PDFG Cleanup Scan Seconds estiver definido como 200, o thread de limpeza será executado a cada 200 segundos e excluirá arquivos com 100 segundos ou mais.

O valor padrão de Segundos da Verificação de Limpeza de PDFG é `43200` (12 horas). O valor padrão de Segundos da Expiração do Trabalho é `86400` (24 horas).

**Local padrão:** usado para substituir a localidade padrão (país + idioma) do servidor em que o serviço Gerar PDF é implantado. Se esse parâmetro não for especificado, a localidade padrão será determinada a partir do sistema operacional no qual o serviço será implantado. Esse parâmetro controla o idioma em que as mensagens de erro são retornadas às APIs.

## configurações do serviço de Data Services do fluxo de trabalho de formulários {#forms-workflow-data-services-service-settings}

Os seguintes serviços estendem os Serviços de Dados e expõem montadores que o Workspace usa para conversar com o servidor. Não altere as opções de configuração desses serviços a menos que seja instruído a fazê-lo pelo Suporte Adobe. Esses serviços não se destinam ao acesso direto:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Remoção das configurações de serviço {#remoting-service-settings}

A maioria dos serviços é configurada para que você possa acessá-los por meio de (obsoleto para formulários AEM) AEM Remoção de formulários. Para obter informações sobre (Obsoleto para formulários AEM) AEM Remoção de formulários, consulte [Programação com formulários AEM](https://adobe.com/go/learn_aemforms_programming_63).

As configurações a seguir estão disponíveis para o serviço Remoting.

**Método de Autenticação do Cliente Flex:** Determina o tipo de resposta que o servidor envia ao cliente quando o serviço chamado está habilitado para segurança, a operação invocada não oferece suporte a invocações anônimas e o cliente transmite nenhuma ou credenciais inválidas. Escolha de Personalizado ou Básico. O valor padrão é Básico.

**Permitir serialização de classes não serializáveis:** A maioria dos pontos de extremidade de formulários AEM permite que somente classes serializáveis sejam usadas para invocação. Em versões mais antigas, o terminal Remoting permitia que classes não serializáveis fossem usadas para invocação de clientes baseados em Flex. Para evitar uma vulnerabilidade de segurança descrita no APS11-15, isso foi alterado. Se desejar continuar usando classes não serializáveis com o ponto de extremidade Remota do Flex, marque essa caixa de seleção.

## Configurações do serviço de repositório {#repository-service-settings}

O serviço Repositório ( `RepositoryService`) fornece serviços de armazenamento e gerenciamento de recursos para AEM formulários. Quando os desenvolvedores criam um aplicativo, eles podem implantar os ativos no repositório em vez de em um sistema de arquivos. Os ativos podem incluir qualquer tipo de material adicional, incluindo formulários XML, PDF forms (incluindo formulários Acrobat), fragmentos de formulário, imagens, perfis, políticas, arquivos SWF, arquivos DX, esquemas XML, arquivos WSDL e dados de teste.

Você pode usar o repositório padrão incluído nos formulários AEM ou usar um repositório de terceiros (EMC Documentum Content Server, IBM FileNet Content Manager ou IBM Content Manager).

O serviço Provedor de Repositório é um delegado de serviço que atua como a interface de um serviço de provedor. Isso permite que você se conecte a uma API comum e não precisa saber qual serviço de provedor está implementando os recursos de armazenamento. O serviço Provedor de Repositório fornece armazenamento de banco de dados para os recursos do serviço de Repositório.

A configuração a seguir está disponível para o serviço Repositório.

**Serviço de Provedor:** O nome do serviço usado como o provedor de armazenamento. O valor padrão é RepositoryProviderService.

## Configurações do serviço de assinatura {#signature-service-settings}

O serviço de assinatura ( `SignatureService`) permite que sua organização proteja a segurança e a privacidade de documentos do Adobe PDF que distribui e recebe. Esse serviço usa assinaturas digitais e certificação para garantir que os documentos não sejam alterados. A alteração de um documento quebra sua assinatura. Como os recursos de segurança são aplicados ao próprio documento, ele permanece protegido e controlado por todo o seu ciclo de vida; além do firewall, quando ele é baixado offline e é enviado de volta à sua organização.

As configurações a seguir estão disponíveis para o serviço de assinatura.

**Nome do serviço SPI remoto do HSM:** essa opção é para uso quando o HSM é instalado em um computador remoto. Especifique essa opção quando AEM formulários estiverem instalados em um Windows de 64 bits e você estiver usando dispositivos HSM para assinatura.

**URL do serviço Web remoto do HSM:** especifique essa opção quando os formulários AEM estiverem instalados no Windows de 64 bits e estiver usando dispositivos HSM para assinatura.

**Certificação para incluir alterações no carregamento do formulário:** quando essa opção é selecionada, o Estado do formulário XFA é certificado além do modelo XFA. Observe que ativar essa opção pode ter um impacto negativo no desempenho. O valor padrão é true.

**Executar scripts JavaScript de documento:** especifica se os scripts JavaScript de documento devem ser executados durante as operações de assinatura. O valor padrão é false.

**Processar documentos com compatibilidade com o Acrobat 9:**  Especifica se deve ser habilitada a compatibilidade com o Acrobat 9. Por exemplo, quando essa opção é selecionada, a Certificação visível em PDFs dinâmicos é ativada. O valor padrão é false.

**Incorporar informações de revogação ao assinar:** especifica se as informações de revogação estão incorporadas ao assinar o documento PDF. O valor padrão é false.

**Incorporar informações de revogação ao certificar:** especifica se as informações de revogação estão incorporadas durante a certificação do documento PDF. O valor padrão é false.

**Impor incorporação de informações de revogação para todos os certificados durante a assinatura/certificação:** especifica se uma operação de assinatura ou certificação falha se informações de revogação válidas para todos os certificados não estão incorporadas. Observe que, se um certificado não contiver nenhuma informação CRL ou OCSP, ele será considerado válido, mesmo que nenhuma informação de revogação seja recuperada. O valor padrão é false.

**Ordem de Verificação de Revogação:** Especifica a ordem da verificação de revogação quando a verificação é possível por meio dos mecanismos CRL (Certificate Revocation List) e OCSP (Online Certificate Status Protocol). O valor padrão é OCSPFfirst.

**Tamanho máximo das informações de arquivamento de revogação:** o tamanho máximo das informações de arquivo de revogação em kilobytes. AEM formulários tenta armazenar o máximo possível de informações de revogação sem exceder o limite. O valor padrão é 10 KB.

**Assinaturas de suporte criadas a partir de compilações de pré-lançamento de produtos de Adobe:**  quando essa opção é selecionada, a assinatura criada usando a versão de pré-lançamento dos produtos de Adobe validará corretamente. O valor padrão é false.

**Opção de Tempo de Verificação:** Especifica a hora da verificação do certificado de um assinante. O valor padrão é Tempo Seguro Mais Tempo Atual.

**Usar Informações de Revogação Arquivadas na Assinatura durante a Validação:** Especifica se as informações de revogação que são arquivadas com a assinatura são usadas para verificação de revogação. O valor padrão é true.

**Usar informações de validação armazenadas no documento para validação de assinaturas:** quando essa opção é selecionada, as informações de validação (incluindo informações de revogação e carimbo de data e hora) incorporadas no documento são usadas para validar assinaturas. O valor padrão é true.

**Máximo de sessões de verificação aninhadas permitidas:** o número máximo de sessões de verificação aninhadas permitidas. AEM formulários usam esse valor para impedir um loop infinito ao verificar os certificados do assinante OCSP ou CRL quando o certificado OCSP ou CRL não está configurado corretamente. O valor padrão é 10.

**Inclinação máxima do relógio para verificação:** o tempo máximo, em minutos, em que a hora de assinatura pode ser após o tempo de validação. Se o desvio do relógio for maior que este valor, a assinatura não será válida. O valor padrão é de 65 minutos.

**Cache do tempo de vida do certificado:** a duração de um certificado, recuperado online ou por outros meios, no cache. O valor padrão é 1 dia.

### Opções de transporte {#transport-options}

**Host proxy:** o URL do host proxy. Usado somente se algum valor válido for fornecido. Nenhum valor padrão.

**Porta de proxy:** a porta de proxy. Digite qualquer número de porta válido de 0 a 65535. O valor padrão é 80.

**Nome de usuário do logon de proxy:** o nome de usuário do logon de proxy. Usado somente se algum valor válido for fornecido para host proxy e porta proxy. Nenhum valor padrão.

**Senha de logon do proxy:** a senha de logon do proxy. Usado somente se algum valor válido for fornecido para host proxy, porta proxy e nome de usuário de logon proxy. Nenhum valor padrão.

**Limite máximo de download:** a quantidade máxima de dados, em MBs, que podem ser recebidos por conexão. O valor mínimo é 1 MB e o valor máximo é 1024 MB. O valor padrão é 16 MB.

**Tempo limite da conexão:** o tempo máximo de espera, em segundos, para estabelecer uma nova conexão. O valor mínimo é 1 e o valor máximo é 300. O valor padrão é 5.

**Tempo limite do soquete:** o tempo máximo para aguardar, em segundos, antes que ocorra um tempo limite do soquete (enquanto aguarda a transferência de dados). O valor mínimo é 1 e o valor máximo é 3600. O valor padrão é 30.

### Opções de validação de caminho {#path-validation-options}

**Exigir política explícita:** especifica se o caminho deve ser válido para pelo menos uma das políticas de certificado associadas à âncora de confiança do certificado do assinante. O valor padrão é false.

**Inibir QUALQUER política:** Especifica se o identificador de objeto de política (OID) deve ser processado se estiver incluído em um certificado. O valor padrão é false.

**Inibir mapeamento de política:** especifica se o mapeamento de política é permitido no caminho de certificação. O valor padrão é false.

**Verificar todos os caminhos:** especifica se todos os caminhos devem ser validados ou se a validação deve parar após localizar o primeiro caminho válido. Selecione verdadeiro ou falso. O valor padrão é false.

**Servidor LDAP:** O servidor LDAP usado para procurar certificados para validação de caminho. Nenhum valor padrão.

**Seguir os URIs no Certificado AIA:** Especifica se os URIs (Uniform Resource Identifiers) no Certificado AIA são processados durante a descoberta do caminho. O valor padrão é false.

**Extensão de Restrições Básicas exigida em Certificados CA:**  Especifica se a extensão de certificado de Restrições Básicas da autoridade de certificação (CA) deve estar presente para certificados CA. Alguns certificados de raiz certificados alemães anteriores (7 e anteriores) não são compatíveis com o RFC 3280 e não contêm a extensão de restrição básica. Se for sabido que o certificado EE de um usuário acorda até uma raiz alemã, desmarque essa caixa de seleção. O valor padrão é true.

**Exigir assinatura de certificado válida durante a criação da cadeia:** especifica se o construtor de cadeia requer assinaturas válidas em certificados usados para criar cadeias. Quando esta caixa de seleção é selecionada, o construtor de cadeia não cria cadeias com assinaturas RSA inválidas em certificados. Considere a cadeia CA > ICA > EE, onde a assinatura da CA em uma ICA não é válida. Se essa configuração for verdadeira, o prédio da cadeia parará na ICA, e a CA não será incluída na cadeia. Se essa configuração for falsa, a cadeia completa de 3 certificados será produzida. Essa configuração não afeta assinaturas DSA. O valor padrão é false.

### Opções do provedor de carimbo de data e hora {#timestamp-provider-options}

**URL do servidor TSP:** o URL do provedor de carimbo de data e hora padrão. Usado somente se algum valor válido for fornecido. Nenhum valor padrão.

**Nome de usuário do servidor TSP:** o nome do usuário, se exigido pelo provedor de carimbo de data e hora. Usado somente se algum valor válido for fornecido para o URL. Nenhum valor padrão.

**Senha do servidor TSP:** a senha do nome de usuário acima, se exigido pelo provedor de carimbo de data e hora. Usado somente se algum valor válido for fornecido para o URL e o nome de usuário. Nenhum valor padrão.

**Solicitar algoritmo de hash:** especifica o algoritmo de hash a ser usado ao criar a solicitação para o provedor de carimbo de data e hora. O valor padrão é SHA1.

**Estilo de Verificação de Revogação:** Especifica o estilo de verificação de revogação usado para determinar o status de confiança do certificado do provedor de carimbo de data e hora a partir de seu status de revogação observado. O valor padrão é BestEffort.

**Enviar Nonce:** especifica se um nonce é enviado com a solicitação do provedor de carimbo de data e hora. Um nonce pode ser um carimbo de data e hora, um contador de visitas em uma página da Web ou um marcador especial destinado a limitar ou impedir a repetição ou reprodução não autorizada de um arquivo. O valor padrão é true.

**Usar carimbos de data e hora expirados durante a validação:**  quando essa opção é selecionada, os carimbos de data e hora expirados podem ser usados para recuperar os tempos de validação das assinaturas. O valor padrão é true.

**Tamanho da resposta TSP:** tamanho estimado, em bytes, da resposta TSP. Esse valor deve representar o tamanho máximo da resposta do carimbo de data e hora que o provedor de carimbo de data e hora configurado poderia retornar. Não altere isso a menos que tenha certeza absoluta. O valor mínimo é 60B e o valor máximo é 10240B. O valor padrão é 4096B.

**Ignorar Extensão** do Servidor TimeStamp: Selecione a opção  **Ignorar** extensão do servidor TimeStamp para impedir que o servidor AEM Forms entre em contato com o servidor de carimbo de data/hora especificado. A seleção da opção ajuda a evitar falhas de processo que acontecem devido ao tempo limite da conexão entre o AEM Forms e os servidores de carimbo de data e hora.

### Opções da lista de revogação de certificado {#certificate-revocation-list-options}

**Consultar URI local primeiro:** especifica se o local da CRL fornecido na Pesquisa de URI ou CRL local deve ter preferência sobre qualquer local especificado em um certificado para fins de verificação de revogação. O valor padrão é false.

**URI local para pesquisa de CRL:** URL do provedor de CRL local. Esse valor é consultado somente se a configuração Consultar URI local First estiver definida como true. Nenhum valor padrão.

**Estilo de Verificação de Revogação:** Especifica o estilo de verificação de revogação usado para determinar o status de confiança do certificado do provedor de CRL a partir de seu status de revogação observado. O valor padrão é BestEffort.

**Servidor LDAP para pesquisa CRL:** O servidor LDAP usado para obter as CRLs (como www.ldap.com). Todas as consultas baseadas em DN para CRLs serão direcionadas a este servidor. Nenhum valor padrão.

**Ir Online:** Especifica se deve ficar online para buscar uma CRL. Se for falso, somente as CRLs em cache (no disco local ou aquelas incorporadas com assinatura) serão consultadas. O valor padrão é true.

**Ignorar datas de validade:** Especifica se deve ignorar os tempos de thisUpdate e nextUpdate da resposta, o que impede que esses horários tenham um efeito negativo na validade da resposta. O valor padrão é false.

**Exigir extensão AKI no CRL:** Especifica se a extensão Identificador de Chave da Autoridade deve ser incluída em um CRL. O valor padrão é false.

### Opções de Protocolo de Status de Certificado Online {#online-certificate-status-protocol-options}

**URL do servidor OCSP:** URL do servidor OCSP padrão. Se o servidor OCSP especificado por meio desse URL é usado depende da configuração da opção URL para consulta. Nenhum valor padrão.

**Opção de consulta de URL:** controla a lista e a ordem dos servidores OCSP usados para executar a verificação de status. O valor padrão é UseAIAInCert.

**Estilo de verificação de revogação:** especifica o estilo de verificação de revogação usado ao verificar o certificado do servidor OCSP. O valor padrão é CheckIfAvailable.

**Enviar Nonce:** especifica se um nonce é enviado com a solicitação OCSP. Um nonce pode ser um carimbo de data e hora, um contador de visitas em uma página da Web ou um marcador especial destinado a limitar ou impedir a repetição ou reprodução não autorizada de um arquivo. O valor padrão é true.

**Tempo máximo de desvio do relógio:** desvio máximo permitido, em minutos, entre o tempo de resposta e o tempo local. O valor mínimo é 0 e o valor máximo é 2147483647m. O valor padrão é 5m.

**Tempo de atualização da resposta:** Tempo máximo, em minutos, para o qual uma resposta OCSP pré-construída é considerada válida. O valor mínimo é 1m e o valor máximo permitido é 2147483647. O valor padrão é 525600 (um ano).

**Assinar solicitação OCSP:** Especifica se a solicitação OCSP deve ser assinada. O valor padrão é false.

**Alias de Credencial do Assinante da Solicitação:** Especifica o alias da credencial a ser usado para assinar a solicitação OCSP se a assinatura estiver ativada. Usado somente se a assinatura da solicitação OCSP estiver ativada. Nenhum valor padrão.

**Ir Online:** Especifica se deve ficar online para efetuar a verificação de revogação. O valor padrão é true.

**Ignorar os tempos de thisUpdate e nextUpdate da resposta:** Especifica se deve ignorar os tempos de thisUpdate e nextUpdate da resposta, o que impede que esses horários tenham um efeito negativo na validade da resposta. O valor padrão é false.

**Permitir extensão OCSPNoCheck:**  Especifica se a extensão OCSPNoCheck é permitida no certificado de assinatura de resposta. O valor padrão é true.

**Exigir extensão de certHash OCSP ISIS-MTT:** Especifica se uma extensão de hash de chave pública de certificado deve ser incluída nas respostas OCSP. O valor padrão é false.

### Opções de tratamento de erros para depuração {#error-handling-options-for-debugging}

**Limpar Cache de Certificado na próxima chamada de API:** Especifica se a limpeza do Cache de Certificado deve ser feita quando a próxima Operação do Serviço de Assinatura for chamada. Depois que a operação é chamada, essa opção é definida como false. O valor padrão é false.

**Limpar o cache da CRL na próxima chamada de API:** Especifica se a limpeza do cache da CRL deve ser feita quando a próxima operação do serviço de assinatura for chamada. Depois que a operação é chamada, essa opção é definida como false. O valor padrão é false.

**Limpar Cache OCSP na próxima chamada de API:** Especifica se a limpeza do Cache OCSP deve ser feita quando a próxima Operação do Serviço de Assinatura for chamada. Depois que a operação é chamada, essa opção é definida como false. O valor padrão é false.

## Configurações do serviço de pastas assistidas {#watched-folder-service-settings}

O serviço Pasta assistida ( `WatchedFolder`) configura atributos comuns a todos os pontos de extremidade de pasta monitorados. Também fornece valores padrão para endpoints de pastas observados. (Consulte [Configuração de pontos de extremidade de pasta observados](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).) Ela não é invocada por aplicativos clientes externos ou usada em processos criados no Workbench.

As configurações a seguir estão disponíveis para o serviço Pasta assistida.

**Expressão Cron:** A expressão cron usada pelo quartzo para agendar a pesquisa do diretório de entrada.

**Contagem de repetição:** o número de vezes em que o diretório de entrada é pesquisado. A contagem de repetição padrão a ser usada se esse valor não for especificado na configuração de ponto de extremidade. Um valor de -1 indica a verificação indefinida do diretório. O valor padrão é -1.

**Intervalo de repetição:** o número padrão se houver segundos entre cada pesquisa. Esse valor é usado como o intervalo de repetição, a menos que um valor diferente seja especificado na configuração do ponto de extremidade da pasta monitorada. O valor padrão é 5. Consulte a descrição da configuração Tamanho do lote para obter mais informações.

**Assíncrono:** identifica o tipo de invocação como assíncrona ou síncrona. Processos transitórios e síncronos só podem ser invocados de forma síncrona. O valor padrão é assíncrono.

**Tempo de espera:** o valor padrão por tempo, em segundos, depois que os arquivos são recuperados das pastas de entrada. Se o arquivo ou pasta for anterior ao tempo especificado no tempo de espera, ele será selecionado para processamento. O valor padrão é 0.

**Tamanho do lote:** o valor padrão do número de arquivos ou pastas processados por varredura. O valor padrão é 2.

As configurações Repetir intervalo e Tamanho do lote determinam quantos arquivos a Pasta assistida recebe em cada verificação. A Pasta assistida usa um conjunto de encadeamentos do Quartz para digitalizar a pasta de entrada. O conjunto de threads é compartilhado com outros serviços. Se o intervalo de varredura for pequeno, os threads verificarão a pasta de entrada com frequência. Se os arquivos forem soltos com frequência na pasta monitorada, mantenha o intervalo de verificação pequeno. Se os arquivos forem descartados com pouca frequência, use um intervalo de varredura maior para que os outros serviços possam usar os threads.

Se houver um grande volume de arquivos sendo descartados, torne o tamanho do lote grande. Por exemplo, se o serviço chamado pelo endpoint da pasta assistida puder processar 700 arquivos por minuto e os usuários soltarem arquivos na pasta de entrada na mesma taxa, em seguida, definir o Tamanho do lote como 350 e o Intervalo de repetição como 30 segundos ajudará no desempenho da Pasta assistida sem incorrer no custo de varredura da pasta assistida com muita frequência.

Quando os arquivos são soltos na pasta assistida, ela lista os arquivos na entrada, o que pode reduzir o desempenho se a varredura estiver acontecendo a cada segundo. Aumentar o intervalo de varredura pode melhorar o desempenho. Se o volume de arquivos que está sendo descartado for pequeno, ajuste o Tamanho do lote e o Intervalo de repetição apropriadamente. Por exemplo, se 10 arquivos forem descartados a cada segundo, tente definir o Intervalo de repetição como 1 segundo e o Tamanho do lote como 10.

Em uma configuração de cluster, o tamanho do lote de um endpoint de pasta monitorada não é dimensionado para vários nós do cluster. Por exemplo, se o tamanho do lote estiver definido como `2` para um cluster de dois nós e a opção Throttle estiver selecionada, os nós processarão arquivos coletivamente em lotes de dois, em vez de cada nó processar dois arquivos de cada vez.

**Substituir nomes de arquivo duplicados:**  uma string booleana que especifica se a pasta assistida substitui nomes de arquivo de resultado duplicado e se documentos preservados com o mesmo nome devem ser substituídos.

**Pasta de preservação:** o valor padrão da pasta de preservação. Essa pasta é usada para copiar os arquivos de origem no em caso de processamento bem-sucedido da entrada. Esse valor pode ser um caminho vazio, relativo ou absoluto com um padrão de arquivo, conforme descrito para a configuração Pasta de resultados .

**Pasta de falha:** o nome da pasta onde os arquivos de falha são copiados. Esse valor pode ser um caminho vazio, relativo ou absoluto com um padrão de arquivo, conforme descrito para a configuração Pasta de resultados .

**Pasta de resultados:** o nome padrão da pasta de resultados. Essa pasta é usada para copiar os arquivos de resultados. Esse valor pode ser um caminho vazio, relativo ou absoluto com o seguinte padrão de arquivo.

* %F = prefixo do nome do arquivo
* %E = extensão de nome de arquivo
* %Y = ano (completo)
* %y = ano (últimos dois dígitos)
* %M = mês
* %D = dia do mês
* %d = dia do ano
* %H = hora (relógio de 24 horas)
* %h = hora (relógio de 12 horas)
* %m = minuto
* %s = segundo
* %l = milissegundos
* %R = número aleatório (de 0 a 9)
* %P = id de processo ou tarefa

Por exemplo, se forem 20 horas em 17 de julho de 2009 e você especificar `C:/Test/WF0/failure/%Y/%M/%D/%H/`, a pasta de resultados será `C:/Test/WF0/failure/2009/07/17/20`.

Se o caminho não for absoluto, mas relativo, a pasta será criada dentro da pasta assistida. Para obter mais informações sobre padrões de arquivo, consulte [Sobre padrões de arquivo](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Quanto menor for o tamanho das pastas de resultados, melhor será o desempenho da Pasta assistida. Por exemplo, se a carga estimada da pasta assistida for de 1.000 arquivos a cada hora, tente um padrão como `result/%Y%M%D%H` para que uma nova subpasta seja criada a cada hora. Se a carga for menor (por exemplo, 1000 arquivos por dia), você poderá usar um padrão como `result/%Y%M%D`.

**Pasta de palco:** o nome padrão da pasta de palco dentro da pasta assistida.

**Pasta de entrada:** o nome padrão da pasta de entrada dentro da pasta assistida.

**Preservar em falha:** se for verdadeiro, os arquivos originais serão preservados na pasta de falha durante a falha.

**Controle:** quando essa opção é selecionada, ela limita o número de trabalhos de pasta monitorados que AEM formulários processados em um determinado momento. O valor Tamanho do Lote determina o número máximo de tarefas (Consulte Sobre o controle).

## Configurações do serviço Web {#web-service-service-settings}

O serviço Serviço Web ( `WebService`) permite que os processos invoquem operações de serviço Web.

O serviço Serviço Web permite que processos invoquem operações de serviço Web. Por exemplo, uma organização pode querer integrar um processo para armazenar e recuperar informações, como contato e detalhes da conta, chamando os serviços Web expostos de um provedor de serviços. O serviço Web chama um serviço Web especificado e transmite valores para cada um de seus parâmetros. Em seguida, salva os valores de retorno da operação em uma variável designada em um processo.

O serviço Web interage com serviços da Web enviando e recebendo mensagens SOAP. O serviço também oferece suporte ao envio de anexos MIME, MTOM e SwaRef com mensagens SOAP usando o protocolo WS-Attachment. As interações do serviço Web são compatíveis com sistemas SAP e serviços Web .NET.

As configurações a seguir estão disponíveis para o serviço de serviço da Web.

**Armazenamento de chaves:** o caminho completo do arquivo do repositório de chaves que contém a chave privada a ser usada para autenticação. O servidor de formulários deve ser capaz de acessar o arquivo.

**Senha do armazenamento de chaves:** a senha do arquivo do armazenamento de chaves.

**Tipo de armazenamento de chave:** o tipo do armazenamento de chaves. Não forneça valor para usar o tipo de armazenamento de chaves padrão configurado para a JVM que executa o servidor de formulários. Caso contrário, forneça um dos seguintes valores:

* jks
* pkcs12
* cms
* jceks

**Armazenamento de confiança:** o caminho completo do arquivo de armazenamento de confiança que contém a chave pública do servidor de serviço da Web.

**Senha do armazenamento de confiança:** a senha do arquivo do armazenamento de confiança.

**Tipo de Armazenamento de Confiança:** O tipo do armazenamento de confiança. Não forneça valor para usar o tipo de armazenamento de chaves padrão configurado para a JVM que executa o servidor de formulários. Caso contrário, forneça um dos seguintes valores:

* jks
* pkcs12
* cms
* jceks

## Configurações do serviço de transformação XSLT {#xslt-transformation-service-settings}

O serviço de transformação XSLT ( `XSLTService`) permite que os processos apliquem Transformações de linguagem de folha de estilos extensível (XSLT) em documentos XML.

A seguinte configuração está disponível para o serviço de Transformação XSLT.

**Nome da fábrica:** o nome totalmente qualificado da classe Java a ser usada para executar transformações XSLT. Se nenhum valor for especificado, a fábrica padrão configurada na máquina virtual Java que executa o servidor de formulários será usada.

## Modificação das configurações de segurança de um serviço {#modifying-security-settings-for-a-service}

o servidor forms permite definir as configurações de segurança para cada serviço, o que permite configurar o controle de acesso refinado em um nível de serviço por serviço.

Os perfis de segurança padrão são instalados, que podem ser configurados para atender às necessidades do seu sistema. Cada perfil de segurança tem um domínio associado e é criado no nível do usuário ou no nível do grupo.

### Modificar definições de segurança para um serviço {#modify-security-settings-for-a-service}

1. No console de administração, clique em Serviços > Aplicativos e Serviços > Gerenciamento de Serviços.
1. Na página Gerenciamento de serviços , clique no serviço a ser configurado.
1. Clique na guia Segurança.
1. Na lista Exigir chamadas para autenticação , selecione Sim ou Não para especificar se o serviço pode ser chamado com ou sem credenciais.

   Se você selecionar Sim, o chamador do serviço deve ser autenticado e o principal do usuário desse chamador deve ser autorizado a invocar o serviço; caso contrário, a tentativa de invocação será recusada.

   Se você selecionar Não, o chamador do serviço pode ou não ser autenticado. A invocação do serviço sempre terá êxito porque não existe uma verificação de autorização.

1. Para serviços que contêm uma ou mais operações sinalizadas para acesso anônimo, selecione ou desmarque Acesso Anônimo Permitido. Quando o acesso anônimo é ativado, qualquer usuário no sistema pode chamar operações no serviço. Se o acesso anônimo estiver desativado, os usuários devem receber permissão para chamar o serviço e chamar as operações. Os usuários recebem essas permissões diretamente ou como parte de um grupo que tem essas permissões.
1. Para alguns serviços, a conta de usuário que executa a operação afeta os resultados. Por exemplo, nos Serviços de conteúdo (obsoleto), o usuário que armazena conteúdo é proprietário do conteúdo, o que afeta quem pode acessá-lo posteriormente. Se você estiver usando um processo para armazenar conteúdo, pense em qual usuário é usado para executar o serviço de Gerenciamento de documentos, pois esse usuário será o proprietário do conteúdo armazenado.

   Para especificar a identidade de tempo de execução usada por um serviço para executar operações, selecione Especificar Executar como, selecione uma opção na lista associada e clique em Salvar. Escolha entre as seguintes opções:

   **Invocador:** usa a mesma identidade do usuário que chamou o serviço.

   **Sistema:** usa o usuário do Sistema para executar o serviço com privilégios totais.

   **Usuário nomeado:** permite que você execute o serviço como um usuário específico. Ao selecionar esta opção, clique em Selecionar Usuário para exibir a página Selecionar Principal, onde você pode procurar e selecionar o usuário.

   Se você não selecionar Especificar Executar como, o comportamento padrão será usado.

   >[!NOTE]
   >
   >Os serviços de renderização e envio usados com as variáveis xfaForm, Document Form e Form são sempre executados usando a conta de usuário do Sistema.

1. Clique em Adicionar Principal para especificar as permissões que os usuários e grupos têm para este serviço.
1. A tela Selecionar Principal exibe os usuários e grupos configurados no Gerenciamento de Usuários. Se o usuário ou grupo desejado não for exibido, use a função de pesquisa para encontrá-lo. Clique em um nome de usuário ou grupo.
1. Na tela Adicionar permissões , selecione as permissões a serem atribuídas ao usuário ou grupo para este serviço:

   * **INVOKE_PERM:** para invocar todas as operações no serviço
   * **MODIFY_CONFIG_PERM:** Para modificar a configuração de um serviço
   * **SUPERVISOR_PERM:** para exibir os dados da instância do processo de um serviço criado de um processo
   * **START_STOP_PERM:** para iniciar e parar um serviço
   * **ADD_REMOVE_ENDPOINTS_PERM:** Para adicionar, remover e modificar endpoints de um serviço
   * **CREATE_VERSION_PERM:** Para criar uma nova versão do serviço
   * **DELETE_VERSION_PERM:** Para excluir uma versão do serviço
   * **MODIFY_VERSION_PERM:** para modificar uma versão do serviço
   * **READ_PERM:** para exibir o serviço
   * **PROCESS_OWNER_PERM:** para uso em uma versão futura de formulários AEM. Não use essa permissão.
   * **SERVICE_MANAGER_PERM:** para uso em uma versão futura de formulários AEM. Não use essa permissão.
   * **SERVICE_AGENT_PERM:** para uso em uma versão futura de formulários AEM. Não use essa permissão.

1. Clique em Adicionar.

### Remover o principal de um perfil de segurança {#remove-the-principal-from-a-security-profile}

1. Na página Gerenciamento de serviços , selecione o serviço a ser configurado.
1. Clique na guia **Security**, selecione o perfil de segurança a ser removido e clique em **Remove**.

## Configuração de pool para um serviço {#configuring-pooling-for-a-service}

Cada serviço pode aproveitar os recursos de pool para manipular solicitações de invocação recebidas. Usar um pool de serviços garante que as instâncias de serviço sejam chamadas por um único thread de cada vez e sejam reutilizadas em solicitações de invocação, o que pode resultar em um desempenho aprimorado. Você também pode usar o pool para especificar a opção Máximo de instâncias de serviço assíncronas , que permite que os serviços limitem o número de solicitações tratadas em paralelo.

### Ativar pooling {#enable-pooling}

1. No console de administração, clique em Serviços > Aplicativos e Serviços > Gerenciamento de Serviços.
1. Na página Gerenciamento de serviços , clique no serviço a ser configurado.
1. Clique na guia Pooling .
1. Na lista Estratégia de processamento de solicitações , selecione Instâncias agrupadas para todas as solicitações.
1. Na caixa Tamanho do Pool de Instâncias do Serviço Inicial , digite o tamanho inicial do pool. Quando o serviço é implantado, esse número é usado para determinar o número de instâncias de implementação do serviço criadas e alocadas no pool livre, aguardando solicitações de invocação. Isso permite que o contêiner de serviço responda imediatamente às solicitações de invocação sem precisar primeiro inicializar uma instância de serviço.
1. Na caixa Tamanho máximo do pool de instâncias do serviço , digite o número máximo de instâncias no pool para um determinado serviço. Essa configuração controla o número de threads que podem executar um determinado serviço em um determinado momento. O valor padrão é 0, o que resulta em um tamanho de pool ilimitado.
1. Na caixa Máximo de instâncias de serviço assíncrono , insira o número máximo de instâncias do pool que podem ser usadas para atender a solicitações assíncronas em um determinado momento. Essa configuração permite que o serviço limite o número de solicitações que pode lidar simultaneamente.
1. Na caixa Tempo Limite de Espera de Invocação , digite o número de milissegundos para aguardar que um serviço fique disponível para uma solicitação de invocação. Se você não especificar um valor para essa configuração, o padrão será 0, o que resultará em nenhum tempo de espera.
1. Clique em Salvar.

### Remover pooling {#remove-pooling}

1. No console de administração, clique em Serviços > Aplicativos e Serviços > Gerenciamento de Serviços.
1. Na página Gerenciamento de serviços , clique no serviço a ser configurado.
1. Clique na guia Pooling .
1. Na lista Estratégia de processamento de solicitações , selecione Nova instância para cada solicitação ou Instância única para todas as solicitações.

   **Instância única para todas as solicitações:** uma instância de serviço é criada e armazenada em cache quando a primeira solicitação chega ao contêiner. Cada solicitação depois dessa solicitação usa a mesma instância de serviço para lidar com a solicitação.

   **Nova instância para cada solicitação:** uma nova instância de serviço é criada para cada invocação recebida.

1. Clique em Salvar.
