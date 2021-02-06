---
title: Gerencie seus ativos digitais usando o AEM Assets
description: Saiba mais sobre várias tarefas de gerenciamento e edição de ativos que você pode executar usando a interface de usuário otimizada ao toque da AEM Assets
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 59fed31d276510c3346a46ac38f2a79c6f91d848
workflow-type: tm+mt
source-wordcount: '10039'
ht-degree: 2%

---


# Gerenciar seus ativos digitais {#managing-assets-with-the-touch-optimized-ui}

Saiba mais sobre várias tarefas de gerenciamento e edição de ativos que você pode executar usando a interface de usuário otimizada ao toque do AEM Assets.

Este artigo descreve como gerenciar e editar ativos usando a interface de usuário otimizada ao toque do Adobe Experience Manager (AEM) Assets. Para obter um conhecimento elementar sobre a interface do usuário, consulte [Manuseio básico da interface de usuário de toque](/help/sites-authoring/basic-handling.md). Para gerenciar fragmentos de conteúdo, consulte [Gerenciamento de fragmentos de conteúdo](content-fragments-managing.md) ativos.

## Criar pastas {#create-folders}

Ao organizar uma coleção de ativos, por exemplo, todas as imagens `Nature`, você pode criar pastas para mantê-las juntas. Você pode usar pastas para categorizar e organizar seus ativos. A AEM Assets não exige que você organize ativos em pastas para trabalhar melhor.

>[!NOTE]
>
>* O compartilhamento de uma pasta Assets do tipo `sling:OrderedFolder` não é suportado ao compartilhar com o Marketing Cloud. Se quiser compartilhar uma pasta, não selecione Solicitado ao criar uma pasta.
>* O Experience Manager não permite o uso da palavra `subassets` como o nome de uma pasta. É uma palavra-chave reservada para nós que contêm subativos para ativos compostos.


1. Navegue até o local na pasta de ativos digitais onde deseja criar uma nova pasta.
1. No menu, clique em **[!UICONTROL Criar]**. Selecione **[!UICONTROL Nova pasta]**.
1. No campo **[!UICONTROL Title]**, forneça um nome de pasta. Por padrão, o DAM usa o título fornecido como o nome da pasta. Depois que a pasta for criada, você poderá substituir o padrão e especificar outro nome de pasta.
1. Clique em **[!UICONTROL Criar]**. Sua pasta é exibida na pasta de ativos digitais.

Os seguintes caracteres (lista separada por espaços de) não são suportados:

* o nome do arquivo de ativo não deve conter `* / : [ \ \ ] | # % { } ? &`
* o nome da pasta de ativos não deve conter `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

## Carregar ativos {#uploading-assets}

Você pode fazer upload de vários tipos de ativos (incluindo imagens, arquivos PDF, arquivos RAW e assim por diante) da pasta local ou de uma unidade de rede para o AEM Assets.

>[!NOTE]
>
>No modo Dynamic Media - Scene7, você só pode fazer upload de ativos com tamanhos de arquivo de 2 GB ou menos.

Você pode optar por carregar ativos para pastas com ou sem um perfil de processamento atribuído a eles.

Para pastas com um perfil de processamento atribuído, o nome do perfil aparece na miniatura na visualização do cartão. Na visualização da lista, o nome do perfil aparece na coluna **[!UICONTROL Processando Perfil]**. Consulte [Processando Perfis](processing-profiles.md).

Antes de fazer upload de um ativo, verifique se ele está em um formato [suportado](assets-formats.md).

**Para fazer upload de ativos**:

1. Na interface da Web Ativos, navegue até o local onde deseja adicionar ativos digitais.
1. Para fazer upload dos ativos, execute um dos procedimentos a seguir:

   * Na barra de ferramentas, toque no ícone **[!UICONTROL Criar]**. Em seguida, no menu, toque em **[!UICONTROL Arquivos]**. Você pode renomear o arquivo na caixa de diálogo apresentada, se necessário.
   * Em um navegador compatível com HTML5, arraste os ativos diretamente na interface. A caixa de diálogo para renomear o arquivo não é exibida.

   ![create_menu](assets/create_menu.png)

   Para selecionar vários arquivos, pressione a tecla Ctrl/Command e selecione os ativos na caixa de diálogo do seletor de arquivos. Em um iPad, é possível selecionar apenas um arquivo por vez.

   Você pode pausar o upload de ativos grandes (maior que 500 MB) e retomá-lo mais tarde a partir da mesma página. Toque no ícone **[!UICONTROL Pausar]** ao lado da barra de progresso que aparece quando os start de upload são carregados.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   O tamanho acima do qual um ativo é considerado um grande ativo é configurável. Por exemplo, você pode configurar o sistema para considerar ativos acima de 1000 MB (em vez de 500 MB) como ativos grandes. Nesse caso, o botão **[!UICONTROL Pausar]** na barra de progresso é exibido quando ativos de tamanho superior a 1000 MB são carregados.

   O botão **[!UICONTROL Pausar]** não aparece se um ficheiro com mais de 1000 MB é carregado com um ficheiro com menos de 1000 MB. No entanto, se você cancelar o carregamento de arquivo com menos de 1000 MB, o botão **[!UICONTROL Pausar]** será exibido.

   Para modificar o limite de tamanho, configure a propriedade `chunkUploadMinFileSize` do nó `fileupload`no repositório CRX.

   Quando você clica no ícone **[!UICONTROL Pausar]**, ele alterna para um ícone **[!UICONTROL Reproduzir]**. Para retomar o carregamento, clique no ícone **[!UICONTROL Reproduzir]**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

   Para cancelar um upload em andamento, clique no botão `X` ao lado da barra de progresso. Ao cancelar a operação de upload, a AEM Assets exclui a parte parcialmente carregada do ativo.

   A capacidade de retomar o carregamento é especialmente útil em cenários de largura de banda baixa e falhas de rede, onde demora muito para carregar um grande ativo. Você pode pausar a operação de upload e continuar mais tarde quando a situação melhorar. Ao retomar, carregando start a partir do ponto em que você o pausou.

   Durante a operação de upload, o AEM salva as partes do ativo que estão sendo carregadas como partes de dados no repositório CRX. Quando o upload é concluído, AEM consolida esses blocos em um único bloco de dados no repositório.

   Para configurar a tarefa de limpeza para os trabalhos de carregamento de segmentos não concluídos, vá para `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.

   Se você fizer upload de um ativo com o mesmo nome de um ativo já disponível no local em que você está fazendo upload do ativo, uma caixa de diálogo de aviso será exibida.

   Você pode optar por substituir um ativo existente, criar outra versão ou manter ambos renomeando o novo ativo que é carregado. Se você substituir um ativo existente, os metadados do ativo e quaisquer modificações e histórico anteriores (por exemplo, anotações, colheitas etc.) serão excluídos. Se você optar por manter ambos os ativos, o novo ativo será renomeado.

   ![chlimage_1-7](assets/chlimage_1-7.png)

   >[!NOTE]
   >
   >Quando você seleciona **[!UICONTROL Substituir]** na caixa de diálogo **[!UICONTROL Conflito de nomes]**, a ID do ativo é regenerada para o novo ativo. Essa ID é diferente da ID do ativo anterior.
   >
   >Se **[!UICONTROL Asset Insights]** estiver habilitado para rastrear impressões/cliques com a Adobe Analytics, essa ID de ativo regenerada invalida os dados capturados para o ativo no Adobe Analytics.

   Se o ativo carregado existir no AEM Assets, a caixa de diálogo **[!UICONTROL Duplicados detectados]** avisa que você está tentando carregar um ativo de duplicado. A caixa de diálogo é exibida somente se o valor de soma de verificação SHA 1 do binário do ativo existente corresponder ao valor de soma de verificação do ativo que você carrega. Neste caso, os nomes dos ativos são irrelevantes. Em outras palavras, a caixa de diálogo pode aparecer até mesmo para ativos que têm nomes diferentes se os valores SHA 1 para seus binários forem os mesmos.

   >[!NOTE]
   >
   >A caixa de diálogo **[!UICONTROL Duplicados Detectados]** só aparece quando o recurso **[!UICONTROL Detecção de Duplicados]** está ativado. Para ativar o recurso **[!UICONTROL Detecção de Duplicados]**, consulte [Ativando a Detecção de Duplicados](duplicate-detection.md).

   ![chlimage_1-8](assets/chlimage_1-8.png)

   Toque em **[!UICONTROL Manter]** para manter o ativo do duplicado no AEM Assets. Toque em **[!UICONTROL Excluir]** para excluir o ativo de duplicado que você carregou.

   A AEM Assets impede que você carregue ativos com caracteres proibidos em seus nomes de arquivo. Se você tentar carregar um ativo que inclua os caracteres não permitidos, o AEM Assets exibirá uma mensagem de aviso sobre a presença de caracteres proibidos no nome do arquivo e interromperá o upload até que você remova esses caracteres ou faça upload com um nome permitido.

   Para adequar-se a convenções de nomenclatura de arquivos específicas para sua organização, a caixa de diálogo **[!UICONTROL Carregar ativos]** permite que você especifique nomes longos para os arquivos carregados.

   ![chlimage_1-9](assets/chlimage_1-9.png)

   No entanto, os seguintes caracteres (lista separada por espaços de) não são suportados:
   * o nome do arquivo de ativo não deve conter `* / : [ \ \ ] | # % { } ? &`
   * o nome da pasta de ativos não deve conter `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

   Além disso, a interface Assets exibe o ativo mais recente que você carrega ou a pasta que cria primeiro em todas as visualizações (**[!UICONTROL visualização de cartão]**, **[!UICONTROL visualização de Lista]** e **[!UICONTROL visualização de colunas]**).

   Muitas vezes, ao fazer upload de ativos grandes ou de vários ativos simultaneamente, os indicadores visuais permitem avaliar o progresso. A caixa de diálogo **[!UICONTROL Carregar progresso]** exibe a contagem de arquivos carregados com êxito e os arquivos que não foram carregados.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   Se você cancelar a operação de upload antes que os arquivos sejam carregados, a AEM Assets interrompe o upload do arquivo atual e atualiza o conteúdo. No entanto, os arquivos que já foram carregados não são excluídos.

### Carregamentos em série {#serial-uploads}

O upload de vários ativos em massa consome recursos significativos do sistema, o que pode afetar negativamente o desempenho da sua implantação AEM. Os gargalos potenciais podem ser a sua conexão com a Internet, operações de leitura/gravação em disco, limitações do navegador da Web no número de solicitações de POST no carregamento de ativos simultâneos. A operação de carregamento em massa pode falhar ou terminar prematuramente. Em outras palavras, os ativos AEM podem perder alguns arquivos enquanto ingerem vários arquivos ou, ao mesmo tempo, não assimilam nenhum arquivo.

Para superar essa situação, a AEM Assets ingere um ativo por vez (upload em série) durante uma operação de upload em massa, em vez de ingerir todos os ativos simultaneamente.

Por padrão, o carregamento em série de ativos é ativado. Para desativar o recurso e permitir o carregamento simultâneo, sobreponha o nó `fileupload` no CRXDe defina o valor da propriedade `parallelUploads` como `true`.

### Carregar ativos usando FTP {#uploading-assets-using-ftp}

A Dynamic Media permite o carregamento em lote de ativos por meio do servidor FTP. Se você pretende carregar ativos grandes (>1 GB) ou pastas e subpastas inteiras, deve usar o FTP. Você pode até mesmo configurar o upload do FTP para que ocorra de forma recorrente e programada.

>[!NOTE]
>
>No modo Dynamic Media - Scene7, você só pode fazer upload de ativos com tamanhos de arquivo de 2 GB ou menos.

>[!NOTE]
>
>Para fazer upload de ativos por meio do FTP no Dynamic Media - Pacote de recursos de instalação no modo Scene7 (FP) 18912 AEM autor. Entre em contato com o Atendimento ao cliente do Adobe para obter acesso ao FP-18912 e concluir a configuração da sua conta FTP. Consulte [Instalação do pacote de recursos 18912 para migração de ativos em massa](/help/assets/bulk-ingest-migrate.md).
>
>Se você usar o FTP para fazer upload de ativos, as configurações de upload especificadas em AEM serão ignoradas. Em vez disso, as regras de processamento de arquivos, conforme definidas no Dynamic Media Classic, são usadas.

**Para fazer upload de ativos usando FTP**

1. Usando sua escolha de cliente FTP, faça logon no servidor FTP usando o nome de usuário e a senha FTP recebidos do email de provisionamento. No cliente FTP, carregue arquivos ou pastas no servidor FTP.
1. Abra o [aplicativo Dynamic Media Classic para desktop](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) e faça logon na sua conta usando as credenciais recebidas do email de provisionamento.
1. Na barra de navegação global, toque em **[!UICONTROL Carregar]**.
1. Na página **[!UICONTROL Carregar]**, perto do canto superior esquerdo, toque na guia **[!UICONTROL Via FTP]**.
1. No lado esquerdo da página, escolha uma pasta FTP da qual fazer upload de arquivos; no lado direito da página, escolha uma pasta de destino.
1. Perto do canto inferior direito da página, toque em **[!UICONTROL Opções de trabalho]** e defina as opções desejadas com base nos ativos na pasta selecionada.

   Consulte [Carregar opções de tarefa](#upload-job-options).

   >[!NOTE]
   >
   >Quando você carrega ativos por meio do FTP, as opções de trabalho de upload definidas no Dynamic Media Classic têm prioridade aos parâmetros de processamento de ativos definidos no AEM.

1. No canto inferior direito da caixa de diálogo **[!UICONTROL Carregar opções de trabalho]**, toque em **[!UICONTROL Salvar]**.
1. No canto inferior direito da página **[!UICONTROL Carregar]**, toque em **[!UICONTROL Enviar carregamento]**.

   Para visualização do progresso do upload, na barra de navegação global, toque em **[!UICONTROL Jobs]**. A página **[!UICONTROL Tarefas]** exibe o progresso do upload. Você pode continuar trabalhando no AEM e voltar para a página de Tarefas no Dynamic Media Classic a qualquer momento para revisar um trabalho em andamento.

   Para cancelar um trabalho de upload em andamento, toque em **[!UICONTROL Cancelar]** ao lado da hora **[!UICONTROL Duração]**.

#### Carregar Opções de Trabalho {#upload-job-options}

| Opção Carregar | Subopção | Descrição |
|---|---|---|
| Nome da tarefa |  | O nome padrão pré-preenchido no campo de texto inclui a parte digitada pelo usuário do nome e o carimbo de data e hora. Você pode usar o nome padrão ou digitar o nome de sua própria criação para este trabalho de upload. <br>O trabalho e outros trabalhos de upload e publicação são registrados na página Tarefas, onde você pode verificar o status dos trabalhos. |
| Publicar após carregar |  | Publica automaticamente os ativos que você carrega. |
| Substituir em qualquer pasta, o mesmo nome do ativo base, independentemente da extensão |  | Selecione essa opção se desejar que os arquivos carregados substituam os arquivos existentes pelos mesmos nomes. O nome desta opção pode ser diferente, dependendo das configurações em **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Configurações gerais]** > **[!UICONTROL Carregar para o aplicativo]** > **[!UICONTROL Substituir imagens]**. |
| Descompactar arquivos ZIP ou TAR no upload |  |  |
| Opções de trabalho |  | Toque/ clique em **[!UICONTROL Opções de trabalho]** para abrir a caixa de diálogo [!UICONTROL Carregar opções de trabalho] e escolha opções que afetem todo o trabalho de upload. Essas opções são as mesmas para todos os tipos de arquivos.<br>Você pode escolher as opções padrão para fazer upload de arquivos a partir da página Configurações gerais do aplicativo. Para abrir esta página, escolha **[!UICONTROL Configuração]** > **[!UICONTROL Configuração de Aplicativo]**. Toque no botão **[!UICONTROL Opções de carregamento padrão]** para abrir a caixa de diálogo [!UICONTROL Carregar opções de tarefa]. |
|  | Quando | Selecione Uma vez ou Recorrente. Para definir um trabalho recorrente, escolha uma opção Repetir (Diário, Semanal, Mensal ou Personalizado) para especificar quando você deseja que o trabalho de upload do FTP seja repetido. Em seguida, especifique as opções de agendamento conforme necessário. |
|  | Incluir subpastas | Carregue todas as subpastas dentro da pasta que você deseja carregar. Os nomes da pasta e suas subpastas carregadas são inseridos automaticamente no AEM Assets. |
|  | Opções de corte | Para recortar manualmente das laterais de uma imagem, selecione o menu Recortar e escolha Manual. Em seguida, insira o número de pixels a serem cortados de qualquer lado ou de cada lado da imagem. A quantidade de imagens cortadas depende da configuração ppi (pixels por polegada) no arquivo de imagem. Por exemplo, se a imagem exibir 150 ppi e você digitar 75 nas caixas de texto Superior, Direita, Inferior e Esquerda, meia polegada será cortada de cada lado.<br> Para recortar automaticamente pixels de espaço em branco de uma imagem, abra o menu Recortar, escolha Manual e insira medidas de pixel nos campos Superior, Direita, Inferior e Esquerda para recortar das laterais. Você também pode escolher Aparar no menu Cortar e escolher estas opções:<br> **Aparar com base em** <ul><li>**Cor**  - Escolha a opção Cor. Em seguida, selecione o menu Canto e escolha o canto da imagem com a cor que melhor representa a cor do espaço em branco que você deseja cortar.</li><li>**Transparência**  - Escolha a opção Transparência.<br> **Tolerância**  - Arraste o controle deslizante para especificar uma tolerância de 0 a 1.Para aparar com base na cor, especifique 0 para recortar os pixels somente se eles corresponderem exatamente à cor selecionada no canto da imagem. Números próximos a 1 permitem mais diferenças de cor.<br>Para aparar com base na transparência, especifique 0 para cortar pixels somente se eles forem transparentes. Números mais próximos a 1 permitem mais transparência.</li></ul><br>Observe que essas opções de corte não são destrutivas. |
|  | Opções de Perfil de cores | Escolha uma conversão de cores ao criar arquivos otimizados usados para o delivery:<ul><li>Preservação de cor padrão: Mantém as cores da imagem de origem sempre que as imagens contêm informações de espaço de cor; não há conversão de cores. Quase todas as imagens hoje têm o perfil de cor apropriado já incorporado. No entanto, se uma imagem de origem CMYK não contiver um perfil de cor incorporado, as cores serão convertidas em espaço de cor sRGB (azul verde padrão). O sRGB é o espaço de cores recomendado para exibir imagens em páginas da Web.</li><li>Manter espaço de cor original: Mantém as cores originais sem qualquer conversão de cores no momento. Para imagens sem um perfil de cor incorporado, qualquer conversão de cor é feita usando os perfis de cor padrão definidos nas configurações de Publicação. Os perfis coloridos podem não estar alinhados com a cor nos arquivos criados com essa opção. Portanto, é recomendável usar a opção Preservação de cor padrão.</li><li>Personalizado de > Para<br> Abre menus para que você possa escolher um espaço de cores Converter de e Converter em. Essa opção avançada substitui todas as informações de cores incorporadas no arquivo de origem. Selecione essa opção quando todas as imagens que você está enviando contiverem dados de perfil de cor incorretos ou ausentes.</li></ul> |
|  | Opções de edição de imagens | É possível preservar as máscaras de recorte em imagens e escolher um perfil colorido.<br> Consulte  [Configuração de opções de edição de imagens no upload](#setting-image-editing-options-at-upload). |
|  | Opções de Postscript | Você pode rasterizar arquivos de PostScript®, recortar arquivos, manter planos de fundo transparentes, escolher uma resolução e escolher um espaço de cor.<br> Consulte  [Configuração de opções](#setting-postscript-and-illustrator-upload-options) de upload de PostScript e Illustrator. |
|  | Opções do Photoshop | Você pode criar modelos a partir de arquivos Adobe® Photoshop®, manter camadas, especificar como as camadas são nomeadas, extrair texto e especificar como as imagens são ancoradas em modelos.<br> Observe que os modelos não são suportados no AEM.<br> Consulte  [Configuração das opções](#setting-photoshop-upload-options) de upload do Photoshop. |
|  | Opções de PDF | Você pode rasterizar os arquivos, extrair palavras de pesquisa e links, gerar automaticamente um eCatalog, definir a resolução e escolher um espaço de cor.<br> Observe que os eCatalogs não são suportados no AEM. <br> Consulte  [Configuração de opções](#setting-pdf-upload-options) de upload de PDF. |
|  | Opções do Illustrator | Você pode rasterizar arquivos Adobe Illustrator®, manter planos de fundo transparentes, escolher uma resolução e escolher um espaço de cor.<br> Consulte  [Configuração de opções](#setting-postscript-and-illustrator-upload-options) de upload de PostScript e Illustrator. |
|  | Opções de vídeo | Você pode transcodificar um arquivo de vídeo escolhendo uma predefinição de vídeo.<br> Consulte  [Configuração de opções](#setting-evideo-upload-options) de upload de eVideo. |
|  | Predefinições do conjunto de lotes | Para criar um Conjunto de imagens ou um Conjunto de rotação a partir dos arquivos carregados, clique na coluna Ativo da predefinição que deseja usar. É possível selecionar mais de uma predefinição. As predefinições são criadas na página Configuração de aplicativo/Predefinições de conjunto de lotes do Dynamic Media Classic.<br> Consulte  [Configuração de predefinições de conjuntos de lotes para gerar automaticamente conjuntos de imagens e ](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) configurações de rotação para saber mais sobre como criar predefinições de conjuntos de lotes.<br> Consulte  [Configuração de predefinições de conjuntos de lotes no upload](#setting-batch-set-presets-at-upload). |

#### Definir opções de edição de imagem no upload {#setting-image-editing-options-at-upload}

Ao carregar arquivos de imagem, incluindo arquivos AI, EPS e PSD, você pode realizar as seguintes ações de edição na caixa de diálogo **[!UICONTROL Carregar opções de trabalho]**:

* Recorte o espaço em branco da borda das imagens (consulte a descrição na tabela acima).
* Recorte manualmente das laterais das imagens (consulte a descrição na tabela acima).
* Escolha um perfil colorido (consulte a descrição da opção na tabela acima).
* Crie uma máscara a partir de um caminho de recorte.
* Nitidez de imagens com opções de máscara nítida
* Plano de fundo de separação

| Opção | Subopção | Descrição |
|---|---|---|
| Criar máscara a partir do caminho de recorte |  | Crie uma máscara para a imagem com base em suas informações de caminho de recorte. Essa opção se aplica a imagens criadas com aplicativos de edição de imagens nas quais um caminho de recorte foi criado. |
| Mascaramento sem nitidez |  | Permite ajustar um efeito de filtro de nitidez na imagem final com resolução reduzida, controlando a intensidade do efeito, o raio do efeito (conforme medido em pixels) e um limite de contraste que é ignorado.<br> Esse efeito usa as mesmas opções do filtro Máscara de nitidez da Photoshop. Ao contrário do que o nome sugere, a Máscara de nitidez é um filtro de nitidez. Em Mascaramento de nitidez, defina as opções desejadas. As opções de configuração são descritas a seguir: |
|  | Quantidade | Controla a quantidade de contraste que é aplicada aos pixels da borda.<br> Pense nisso como a intensidade do efeito. A principal diferença entre os valores da quantidade de máscara de nitidez no Dynamic Media e os valores da quantidade no Adobe Photoshop é que a Photoshop tem um intervalo de valores de 1% a 500%. Enquanto que, no Dynamic Media, o intervalo de valores é de 0,0 a 5,0. Um valor de 5,0 é o equivalente bruto de 500% no Photoshop; um valor de 0,9 é o equivalente a 90%, e assim por diante. |
|  | Raio | Controla o raio do efeito. O intervalo de valores é de 0 a 250.<br> O efeito é executado em todos os pixels em uma imagem e irradia de todos os pixels em todas as direções. O raio é medido em pixels. Por exemplo, para obter um efeito de nitidez semelhante para uma imagem de 2000 x 2000 pixels e 500 x 500 pixels, você definiria um raio de dois pixels na imagem de 2000 x 2000 pixels e um valor de raio de um pixel na imagem de 500 x 500 pixels. Um valor maior é usado para uma imagem que tem mais pixels. |
|  | Limite | O limite é um intervalo de contraste que é ignorado quando o filtro Máscara de nitidez é aplicado. É importante para que nenhum &quot;ruído&quot; seja introduzido em uma imagem quando esse filtro for usado. O intervalo de valores é de 0 a 255, que é o número de etapas de brilho em uma imagem em tons de cinza. 0=preto, 128=50% cinza e 255=branco.<br> Por exemplo, um valor limite de 12 ignora pequenas variações é o brilho do tom de pele para evitar a adição de ruído, mas ainda adiciona o contraste da borda a áreas contrastantes, como onde as pestanas encontram a pele.<br> Por exemplo, se você tiver uma foto do rosto de uma pessoa, a Máscara de nitidez afeta as partes contrastantes da imagem, como o local em que as pestanas e a pele se encontram para criar uma área de contraste óbvia, e a própria pele lisa. Mesmo a pele mais suave exibe alterações sutis nos valores de brilho. Se você não usar um valor limite, o filtro acentuará essas alterações sutis em pixels de pele. Por sua vez, cria-se um efeito ruidoso e indesejável enquanto o contraste nas pestanas aumenta, aumentando a nitidez.<br> Para evitar esse problema, é introduzido um valor limite que informa ao filtro que ignore os pixels que não alteram o contraste drasticamente, como pele lisa.<br> No gráfico de zipper mostrado anteriormente, observe a textura ao lado dos zippers. O ruído da imagem é exibido porque os valores de limite eram muito baixos para suprimir o ruído. |
|  | Monocromático | Selecione para desmarcar o brilho da imagem da máscara de nitidez (intensidade).<br> Desmarque para desmarcar a máscara de nitidez de cada componente de cor separadamente. |
| Plano de fundo de separação |  | Remove automaticamente o plano de fundo de uma imagem quando você a carrega. Essa técnica é útil para chamar a atenção para um objeto específico e destacá-lo de um fundo ocupado. Selecione para ativar ou &quot;ativar&quot; o recurso de Plano de fundo de separação e as seguintes subopções: |
|  | Canto | Obrigatório.<br> O canto da imagem que é usado para definir a cor do plano de fundo para separação.<br> Você pode escolher entre  **Superior esquerdo**,  **Inferior esquerdo**,  **Superior direito** ou  **Inferior direito**. |
|  | Método de preenchimento | Obrigatório.<br> Controla a transparência de pixels a partir do local Canto que você definiu.<br> Você pode escolher entre os seguintes métodos de preenchimento: <ul><li>**Preenchimento**  do Flood - torna todos os pixels transparentes que correspondem ao Canto especificado e conectado a ele.</li><li>**Corresponder pixel**  - torna todos os pixels correspondentes transparentes, independentemente de sua localização na imagem.</li></ul> |
|  | Tolerância | Opcional.<br> Controla a quantidade permitida de variação na correspondência de cores de pixels com base no local Canto que você definiu.<br> Use um valor de 0,0 para corresponder exatamente às cores dos pixels ou use um valor de 1,0 para permitir a maior variação. |

#### Definir opções de upload do PostScript e do Illustrator {#setting-postscript-and-illustrator-upload-options}

Ao carregar arquivos de imagem PostScript (EPS) ou Illustrator (AI), você pode formatá-los de várias maneiras. Você pode rasterizar os arquivos, manter o plano de fundo transparente, escolher uma resolução e escolher um espaço de cor. As opções para a formatação de arquivos PostScript e Illustrator estão disponíveis na caixa de diálogo Carregar opções de trabalho em Opções de PostScript e Opções do Illustrator.

| Opção | Subopção | Descrição |
|---|---|---|
| Processando |  | Escolha **[!UICONTROL Rasterizar]** para converter gráficos vetoriais no arquivo para o formato de bitmap. |
| Manter plano de fundo transparente na imagem renderizada |  | Manter a transparência em segundo plano do arquivo. |
| Resolução |  | Determina a configuração de resolução. Essa configuração determina quantos pixels são exibidos por polegada no arquivo. |
| Espaço de cor |  | Selecione o menu Espaço de cor e escolha entre as seguintes opções de espaço de cor: |
|  | Detectar automaticamente | Mantém o espaço de cores do arquivo. |
|  | Forçar como RGB | Converte para o espaço de cores RGB. |
|  | Forçar como CMYK | Converte para o espaço de cores CMYK. |
|  | Forçar como escala de cinza | Converte para o espaço de cores em tons de cinza. |

#### Definir opções de upload do Photoshop {#setting-photoshop-upload-options}

Os arquivos PSD (Documento Photoshop) são usados com mais frequência para criar modelos de imagem. Ao carregar um arquivo PSD, você pode criar um modelo de imagem automaticamente a partir do arquivo (selecione a opção Criar modelo na tela Carregar).

O Dynamic Media cria várias imagens de um arquivo PSD com camadas se você usar o arquivo para criar um modelo; cria uma imagem para cada camada.

Use as **[!UICONTROL Opções de corte]** e **[!UICONTROL Opções de Perfil de cor]**, descritas acima, com as opções de upload do Photoshop.

>[!NOTE]
>
>Os modelos não são suportados em AEM.

| Opção | Subopção | Descrição |
|---|---|---|
| Manter camadas |  | Limpa as camadas no PSD, se houver, em ativos individuais. As camadas de ativo permanecem associadas ao PSD. É possível visualização-los abrindo o arquivo PSD na visualização Detalhe e selecionando o painel de camadas. |
| Criar modelo |  | Cria um modelo a partir das camadas no arquivo PSD. |
| Extrair texto |  | Extrai o texto para que os usuários possam pesquisar por texto em um Visualizador. |
| Estender camadas ao tamanho do plano de fundo |  | Estende o tamanho das camadas de imagem recortadas até o tamanho da camada de plano de fundo. |
| Nomenclatura de camada |  | As camadas no arquivo PSD são carregadas como imagens separadas. |
|  | Nome da camada | Nomeia as imagens após seus nomes de camada no arquivo PSD. Por exemplo, uma camada chamada Tag de preço no arquivo PSD original se torna uma imagem chamada Tag de preço. No entanto, se os nomes de camada no arquivo PSD forem nomes de camada padrão do Photoshop (Plano de fundo, Camada 1, Camada 2 e assim por diante), as imagens serão nomeadas após seus números de camada no arquivo PSD, não seus nomes de camada padrão. |
|  | Photoshop e número de camada | Nomeia as imagens após seus números de camada no arquivo PSD, ignorando os nomes das camadas originais. As imagens são nomeadas com o nome de arquivo Photoshop e um número de camada anexado. Por exemplo, a segunda camada de um arquivo chamado Spring Ad.psd é chamada Spring Ad_2 mesmo se ela tiver um nome não padrão no Photoshop. |
|  | Nome da Photoshop e da camada | Nomeia as imagens após o arquivo PSD seguido do nome da camada ou do número da camada. O número da camada será usado se os nomes da camada no arquivo PSD forem nomes padrão da camada Photoshop. Por exemplo, uma camada chamada Marca de preço em um arquivo PSD chamado SpringAd é chamada Marca Ad_Price Primavera. Uma camada com o nome padrão Camada 2 é chamada Primavera Ad_2. |
| Âncora |  | Especifique como as imagens são ancoradas em modelos gerados a partir da composição em camadas produzida a partir do arquivo PSD. Por padrão, a âncora é o centro. Uma âncora central permite que as imagens de substituição preencham melhor o mesmo espaço, independentemente da proporção da imagem de substituição. Imagens com um aspecto diferente que substituem essa imagem, ao referenciar o modelo e usar substituição de parâmetro, ocupam efetivamente o mesmo espaço. Altere para uma configuração diferente se o aplicativo exigir as imagens de substituição para preencher o espaço alocado no modelo. |

#### Definir opções de upload de PDF {#setting-pdf-upload-options}

Ao carregar um arquivo PDF, você pode formatá-lo de várias maneiras. Você corta suas páginas, extrai palavras de pesquisa, digita uma resolução de pixels por polegada e escolhe um espaço de cor. Os arquivos PDF geralmente contêm uma margem de aparagem, marcas de corte, marcas de registro e marcas de outra impressora. É possível recortar essas marcas dos lados das páginas ao carregar um arquivo PDF.

>[!NOTE]
>
>Os eCatalogs não são suportados em AEM.

Escolha uma das seguintes opções:

| Opção | Subopção | Descrição |
|---|---|---|
| Processando | Rasterizar | (Padrão) Limpa as páginas no arquivo PDF e converte gráficos vetoriais em imagens de bitmap. Escolha essa opção para criar um eCatalog. |
| Extrair | Pesquisar palavras | Extrai palavras do arquivo PDF para que o arquivo possa ser pesquisado por palavra-chave em um eCatalog Viewer. |
|  | Links | Extrai links dos arquivos PDF e os converte em mapas de imagem usados em um eCatalog Viewer. |
| Gerar automaticamente o eCatalog de várias páginas em PDF |  | Cria automaticamente um eCatalog a partir do arquivo PDF. O eCatalog recebe o nome do arquivo PDF que você carregou. Essa opção só estará disponível se você rasterizar o arquivo PDF ao carregá-lo. |
| Resolução |  | Determina a configuração de resolução. Essa configuração determina quantos pixels são exibidos por polegada no arquivo PDF. O padrão é 150. |
| Espaço de cor |  | Selecione o menu Espaço de cor e escolha um espaço de cor para o arquivo PDF. A maioria dos arquivos PDF tem imagens coloridas RGB e CMYK. O espaço de cores RGB é preferível para visualização online. |
|  | Detectar automaticamente | Mantém o espaço de cores do arquivo PDF. |
|  | Forçar como RGB | Converte para o espaço de cores RGB. |
|  | Forçar como CMYK | Converte para o espaço de cores CMYK. |
|  | Forçar como escala de cinza | Converte para o espaço de cores em tons de cinza. |

#### Definir opções de upload de eVideo {#setting-evideo-upload-options}

Você pode transcodificar um arquivo de vídeo escolhendo entre várias predefinições de vídeo.

| Opção | Subopção | Descrição |
|---|---|---|
| Vídeo adaptável |  | Uma única predefinição de codificação que funciona com qualquer proporção para criar vídeos para delivery, tablet e desktop. Os vídeos de origem carregados que são codificados com essa predefinição são definidos com uma altura fixa. Entretanto, a largura é dimensionada automaticamente para preservar a proporção do vídeo. <br>A prática recomendada é usar a codificação de vídeo adaptável. |
| Predefinições de codificação única | Classificar predefinições de codificação | Selecione Nome ou Tamanho para classificar as predefinições de codificação listadas em Desktop, Móvel e Tablet por nome ou por tamanho de resolução. |
|  | Área de trabalho | Crie um arquivo MP4 para fornecer uma experiência de streaming ou vídeo progressivo para computadores desktop.Selecione uma ou mais proporções com o tamanho da resolução e a taxa de dados do público alvo desejados. |
|  | Móvel | Crie um arquivo MP4 para delivery em dispositivos móveis iPhone ou Android.Selecione uma ou mais proporções com o tamanho da resolução e a taxa de dados do público alvo desejados. |
|  | Tablet | Crie um arquivo MP4 para delivery em dispositivos tablet iPad ou Android.Selecione uma ou mais proporções com o tamanho de resolução e a taxa de dados do público alvo desejados. |

#### Definir predefinições de conjunto de lotes ao carregar {#setting-batch-set-presets-at-upload}

Se quiser criar automaticamente um Conjunto de imagens ou um Conjunto de rotação a partir de imagens carregadas, clique na coluna **[!UICONTROL Ativo]** para a predefinição que deseja usar. É possível selecionar mais de uma predefinição.

Consulte [Configurando predefinições de conjuntos de lotes para Gerar automaticamente conjuntos de imagens e conjuntos de rotação](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) para saber mais sobre como criar predefinições de conjuntos de lotes.

### Carregamentos em sequência {#streamed-uploads}

Se você carregar vários ativos, as chamadas de E/S para o servidor AEM aumentam drasticamente, o que reduz a eficiência de upload e pode até mesmo fazer com que o tempo limite seja excedido. A AEM Assets oferece suporte ao upload simplificado de ativos. O carregamento em sequência reduz a E/S do disco durante a operação de upload, evitando o armazenamento de ativos em uma pasta temporária no servidor antes de copiá-lo para o repositório. Em vez disso, os dados são transferidos diretamente para o repositório. Dessa forma, o tempo de upload de ativos grandes e a possibilidade de tempos limite são reduzidos. Por padrão, o upload continuado é ativado no AEM Assets.

O carregamento de fluxo é desabilitado para AEM em execução no servidor JEE com a versão servlet-api inferior a 3.1.

### Extrair arquivo ZIP contendo ativos {#extract-zip-archive-containing-assets}

Você pode carregar arquivos ZIP como qualquer outro ativo suportado. As mesmas regras de nome de arquivo se aplicam aos arquivos ZIP. AEM permite que você extraia um arquivo ZIP para um local DAM.

Selecione um arquivo ZIP de cada vez, clique em **[!UICONTROL Extrair arquivo]** e selecione uma pasta de destino. Selecione uma opção para lidar com conflitos, se houver. Se os ativos no arquivo ZIP já existirem na pasta de destino, você poderá selecionar uma destas opções: pule a extração, substitua os arquivos existentes, mantenha ambos os ativos renomeando ou crie uma nova versão.

Após a extração ser concluída, AEM notifica você na área de notificação. Enquanto AEM extrai o ZIP, você pode voltar ao seu trabalho sem interromper a extração.

![Notificação de extração ZIP](assets/zip_extract_notification.png)

Algumas limitações do recurso são:

* Se uma pasta com o mesmo nome existir no destino, os ativos do arquivo ZIP serão extraídos na pasta existente.

* Se você cancelar a extração, os ativos já extraídos não serão excluídos.

* Não é possível selecionar dois arquivos ZIP ao mesmo tempo e extraí-los. Você só pode extrair um arquivo ZIP por vez.

## ativos de pré-visualização {#previewing-assets}

**Para pré-visualização de ativos**:

1. Na interface do usuário Ativos, navegue até o local do ativo que deseja pré-visualização.
1. Toque no ativo desejado para abri-lo.

1. No modo de pré-visualização, as opções de zoom estão disponíveis para [tipos de imagem suportados](assets-formats.md#supported-raster-image-formats) (com edição interativa).

   Para aplicar zoom em um ativo, toque em **[!UICONTROL +]** (ou toque na lupa do ativo). Para diminuir o zoom, toque em **[!UICONTROL -]**. Ao ampliar, você pode observar cuidadosamente qualquer área da imagem ao deslocar o panorama. A seta **[!UICONTROL Redefinir zoom]** traz de volta à visualização original.

   ![uploadicon](assets/uploadicon.png)

   Toque no botão **[!UICONTROL Redefinir]** para redefinir a visualização para o tamanho original.

   ![chlimage_1-11](assets/chlimage_1-11.png)

>[!MORELIKETHIS]
>
>* [Pré-visualização do Dynamic Media Assets](/help/assets/previewing-assets.md).
>* [subativos](managing-linked-subassets.md#viewing-subassets) de visualização.


## Editar propriedades {#editing-properties}

1. Navegue até o local do ativo cujos metadados você deseja editar.

1. Selecione o ativo e toque em **[!UICONTROL Propriedades]** na barra de ferramentas para visualização das propriedades do ativo. Como alternativa, escolha a ação rápida **[!UICONTROL Propriedades]** no cartão de ativos.

   ![properties_quickaction](assets/properties_quickaction.png)

1. Na página **[!UICONTROL Propriedades]**, edite as propriedades de metadados em várias guias. Por exemplo, na guia **[!UICONTROL Basic]**, edite o título, a descrição e assim por diante.

   O layout da página **[!UICONTROL Propriedades]** e as propriedades de metadados disponíveis dependem do schema de metadados subjacente. Para saber como modificar o layout da página **[!UICONTROL Propriedades]**, consulte [Schemas de metadados](metadata-schemas.md).

1. Para programar uma data/hora específica para a ativação do ativo, use o seletor de datas ao lado do campo **[!UICONTROL No horário]**.

   ![Definir tempo de ativação para que os ativos disponibilizem por um período fixo entre o tempo de ativação e de desativação](assets/chlimage_1-12.png)

1. Para desativar o ativo após uma duração específica, escolha a data e a hora de desativação no seletor de datas ao lado do campo **[!UICONTROL Tempo de desligamento]**.

   A data de desativação deve ser posterior à data de ativação de um ativo. Depois do [!UICONTROL Tempo desligado], um ativo e suas representações não estão disponíveis por meio da interface da Web Ativos ou por meio da API HTTP.

   ![Desativar tempo para que os ativos parem de sua disponibilidade após um determinado período de tempo](assets/chlimage_1-13.png)

1. No campo **[!UICONTROL Tags]**, selecione uma ou mais tags. Para adicionar uma tag personalizada, digite o nome da tag na caixa e pressione **[!UICONTROL Enter]**. A nova tag é salva no AEM.

   O YouTube requer tags para publicar e ter um link para o YouTube (se um link adequado puder ser encontrado).
Para criar tags, você precisa de permissão de gravação para `/content/cq:tags/default` no repositório CRX.

1. Para fornecer uma classificação ao ativo, toque na guia **[!UICONTROL Avançado]** e, em seguida, toque na estrela na posição apropriada para atribuir a classificação desejada.

   ![classificações](assets/ratings.png)

   A pontuação de classificação atribuída ao ativo é exibida em **[!UICONTROL Suas classificações]**. A pontuação de classificação média recebida dos usuários que classificaram o ativo é exibida em **[!UICONTROL Classificação]**. Além disso, a análise das pontuações de classificação que contribuem para a pontuação de classificação média é exibida em **[!UICONTROL Divisão de classificação]**. Você pode pesquisar ativos com base nas pontuações de classificação médias.

1. Para obter estatísticas de uso de visualização para o ativo, toque na guia **[!UICONTROL Insights]**.

   As estatísticas de uso incluem o seguinte:

   * Número de vezes que o ativo foi exibido ou baixado.
   * Canais/dispositivos através dos quais o ativo foi usado.
   * Soluções criativas onde o ativo foi usado recentemente.

   Para obter mais detalhes, consulte [Asset Insights](touch-ui-asset-insights.md).

1. Toque em **[!UICONTROL Salvar e fechar]**.
1. Navegue até a interface do usuário Ativos. As propriedades de metadados editadas, incluindo título, descrição, classificações e assim por diante, são exibidas no cartão de ativos na visualização do cartão e em colunas relevantes na visualização da lista.

## Copiar ativos {#copying-assets}

Quando você copia um ativo ou uma pasta, o ativo inteiro ou a pasta é copiado, juntamente com sua estrutura de conteúdo. Um ativo copiado ou uma pasta é duplicado no local do público alvo. O ativo no local de origem não é alterado.

Alguns atributos exclusivos a uma cópia específica de um ativo não são transmitidos. Alguns exemplos são:

* ID do ativo, data e hora de criação e versões e histórico de versões. Algumas dessas propriedades são indicadas pelas propriedades `jcr:uuid`, `jcr:created` e `cq:name`.

* O tempo de criação e os caminhos referenciados são exclusivos para cada ativo e cada uma de suas execuções.

As outras propriedades e informações de metadados são mantidas. Uma cópia parcial não é criada ao copiar um ativo.

1. Na interface do usuário do Assets, selecione um ou mais ativos e toque no ícone **[!UICONTROL Copiar]** na barra de ferramentas. Como alternativa, escolha a ação rápida **[!UICONTROL Copiar]** no cartão de ativos.

   ![copy_icon](assets/copy_icon.png)

   >[!NOTE]
   >
   >Se você usar a ação rápida **[!UICONTROL Copiar]**, poderá copiar apenas um ativo por vez.

1. Navegue até o local onde deseja copiar os ativos.

   >[!NOTE]
   >
   >Se você copiar um ativo no mesmo local, AEM gera automaticamente uma variação do nome. Por exemplo, se você copiar um ativo chamado Quadrado, AEM gera automaticamente o título para sua cópia como Quadrado1.

1. Toque no ícone do ativo **[!UICONTROL Colar]** na barra de ferramentas:

   ![chlimage_1-14](assets/chlimage_1-14.png)

   Os ativos são copiados para este local.

   >[!NOTE]
   >
   >O ícone **[!UICONTROL Colar]** está disponível na barra de ferramentas até que a operação de colagem seja concluída.

## Mover e renomear ativos {#moving-or-renaming-assets}

Quando você move ativos (ou pastas) para outro local, os ativos (ou pastas) não são duplicados, ao contrário de copiar o ativo. Os ativos (ou as pastas) são colocados no local do público alvo e removidos do local de origem. Também é possível renomear o ativo ao movê-lo para o novo local. Se você estiver movendo um ativo publicado para um local diferente, você terá a opção de publicar novamente o ativo. Por padrão, a operação de movimentação em um ativo publicado automaticamente a despublica. O ativo movido será republicado se o autor selecionar a opção [!UICONTROL Publicar novamente] ao mover o ativo.

![Você pode republicar um ativo já publicado ao movê-lo](assets/republish-on-move.png)

Para mover ativos ou pastas:

1. Navegue até o local do ativo que deseja mover.

![Você pode republicar um ativo já publicado ao movê-lo](assets/republish-on-move.png)

Para mover ativos ou pastas:

1. Navegue até o local do ativo que deseja mover.

1. Selecione o ativo e clique na opção **[!UICONTROL Mover]** na barra de ferramentas.
   ![Opção Mover na barra de ferramentas Ativos](assets/do-not-localize/move_icon.png)

1. No assistente [!UICONTROL Mover ativos], execute um dos procedimentos a seguir:

   * Especifique o nome do ativo depois de movê-lo. Em seguida, clique em **[!UICONTROL Próximo]** para prosseguir.

   * Clique em **[!UICONTROL Cancelar]** para parar o processo.
   >[!NOTE]
   >
   >* Você pode especificar o mesmo nome para o ativo se não houver um ativo com esse nome no novo local. No entanto, você deve usar um nome diferente se mover o ativo para um local onde um ativo com o mesmo nome exista. Se você usar o mesmo nome, o sistema gera automaticamente uma variação do nome. Por exemplo, se seu ativo tiver o nome Quadrado, o sistema gera o nome Quadrado1 para sua cópia.
   >* Ao renomear, o espaço em branco não é permitido no nome do arquivo.


1. Na caixa de diálogo **[!UICONTROL Selecionar destino]**, siga um destes procedimentos:

   * Navegue até o novo local dos ativos e clique em **[!UICONTROL Próximo]** para prosseguir.

   * Clique em **[!UICONTROL Voltar]** para voltar à tela **[!UICONTROL Renomear]**.

1. Se os ativos que estão sendo movidos tiverem páginas, ativos ou coleções de referência, a guia **[!UICONTROL Ajustar referências]** aparecerá ao lado da guia **[!UICONTROL Selecionar destino]**.

   Execute um dos procedimentos a seguir na tela **[!UICONTROL Ajustar referências]**:

   * Especifique as referências a serem ajustadas com base nos novos detalhes e clique em **[!UICONTROL Mover]** para continuar.

   * Na coluna **[!UICONTROL Ajustar]**, selecione/cancele a seleção das referências aos ativos.
   * Clique em **[!UICONTROL Voltar]** para voltar à tela **[!UICONTROL Selecionar destino]**.

   * Clique em **[!UICONTROL Cancelar]** para parar a operação de movimentação.

   Se você não atualizar referências, elas continuarão apontando para o caminho anterior do ativo. Se você ajustar as referências, elas serão atualizadas para o novo caminho do ativo.

### Mover ativos usando a operação de arrastar {#move-using-drag}

Você pode mover ativos (ou pastas) para uma pasta irmão arrastando-os para o local do público alvo, em vez de usar a opção [!UICONTROL Mover] na interface do usuário. No entanto, essa operação só é possível na visualização da lista.

Mover ativos arrastando-os não abre o assistente [!UICONTROL Mover ativos], portanto, você não tem a opção de renomear os ativos ao mover-se. Além disso, os ativos já publicados são republicados ao movê-los arrastando-os, sem solicitar a aprovação do usuário para republicar.

![Mover ativos para pastas semelhantes arrastando ativos](assets/move-by-drag.gif)

## Gerenciar execuções {#managing-renditions}

1. Você pode adicionar ou remover representações de um ativo, exceto o original. Navegue até o local do ativo para o qual você deseja adicionar ou remover representações.

1. Toque no ativo para abrir sua página de ativos.

   ![chlimage_1-15](assets/chlimage_1-15.png)

1. Toque no ícone **[!UICONTROL Navegação Global]** e selecione **[!UICONTROL Representações]** na lista.

   ![renditions_menu](assets/renditions_menu.png)

1. No painel **[!UICONTROL Representações]**, visualização a lista de representações geradas para o ativo.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Por padrão, a AEM Assets não exibe a representação original do ativo no modo de pré-visualização. Se você for um administrador, poderá usar sobreposições para configurar o AEM Assets para exibir as representações originais no modo de pré-visualização.

1. Selecione uma representação para visualização ou exclua a representação.

   **Excluir uma representação**

   Selecione uma representação no painel **[!UICONTROL Representações]** e toque no ícone **[!UICONTROL Excluir representação]** da [barra de ferramentas](/help/sites-authoring/basic-handling.md). As execuções não podem ser excluídas em massa após a conclusão do processamento do ativo. Para ativos individuais, você pode remover execuções manualmente da interface do usuário. Para vários ativos, você pode personalizar o Experience Manager para excluir execuções específicas ou excluir os ativos e fazer upload novamente dos ativos excluídos.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Carregar uma nova execução**

   Navegue até a página de detalhes do ativo e toque no ícone **[!UICONTROL Adicionar representação]** na barra de ferramentas para fazer upload de uma nova representação do ativo.

   ![chlimage_1-16](assets/chlimage_1-16.png)

   >[!NOTE]
   >
   >Se você selecionar uma representação no painel **[!UICONTROL Representações]**, a barra de ferramentas alterará o contexto e exibirá somente as ações relevantes para a representação. Opções, como o ícone **[!UICONTROL Carregar representação]** não é exibido. Para exibir essas opções na barra de ferramentas, navegue até a página de detalhes do ativo.

   Você pode configurar as dimensões para a representação que deseja exibir na página de detalhes de um ativo de imagem ou vídeo. Com base nas dimensões especificadas, o AEM Assets exibe a representação com as dimensões exatas ou mais próximas.

   Para configurar dimensões de representação de uma imagem no nível de detalhes do ativo, sobreponha o nó **[!UICONTROL renditionpicker]** `libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker` e configure o valor da propriedade width. Configure o **[!UICONTROL tamanho (Longo) em KB]** da propriedade no lugar da largura para personalizar a representação na página Detalhes do ativo com base no tamanho da imagem. Para personalização baseada em tamanho, a propriedade **[!UICONTROL favoriteOriginal]** atribui preferência ao original se o tamanho da representação correspondente for maior que o original.

   Da mesma forma, você pode personalizar a imagem da página **[!UICONTROL Anotações]** sobrepondo `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   ![chlimage_1-17](assets/chlimage_1-17.png)

   Para configurar dimensões de representação para um ativo de vídeo, navegue até o nó **[!UICONTROL videopicker]** no repositório CRX no local `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, sobreponha o nó e edite a propriedade apropriada.

   >[!NOTE]
   >
   >As anotações em vídeo são compatíveis apenas em navegadores com formatos de vídeo compatíveis com HTML5. Além disso, dependendo do navegador, diferentes formatos de vídeo são suportados.

Para obter informações sobre subativos, consulte [gerenciar subativos](managing-linked-subassets.md).

## Excluir ativos {#deleting-assets}

Para resolver ou remover as referências recebidas de outras páginas, atualize as referências relevantes antes de excluir um ativo.

Além disso, desative o botão forçar exclusão usando uma sobreposição para impedir que os usuários excluam ativos referenciados e deixem links quebrados.

Você precisa de permissões de exclusão no dam/asset para poder excluir um ativo. Se você tiver apenas permissões de modificação, poderá apenas editar os metadados do ativo e adicionar anotações ao ativo. No entanto, não é possível excluir o ativo ou seus metadados.

**Para excluir ativos**:

1. Navegue até o local dos ativos que deseja excluir.

1. Selecione o ativo e toque no ícone **[!UICONTROL Excluir]** na barra de ferramentas.

   ![delete_icon](assets/delete_icon.png)

1. Na caixa de diálogo de confirmação, toque em:

   * **** Cancelar para interromper a ação
   * **[!UICONTROL Para confirmar]** a ação, use o seguinte:

      * Se o ativo não tiver referências, ele será excluído.
      * Se o ativo tiver referências, uma mensagem de erro informará que **[!UICONTROL Um ou mais ativos são referenciados]**. Você pode selecionar **[!UICONTROL Forçar exclusão]** ou **[!UICONTROL Cancelar]**.

   >[!NOTE]
   >
   >Para resolver ou remover as referências recebidas de outras páginas, atualize as referências relevantes antes de excluir um ativo.
   >
   >Além disso, desative o botão **[!UICONTROL Forçar exclusão]** usando uma sobreposição para impedir que os usuários excluam ativos referenciados e deixem links quebrados.

## Baixar ativos {#downloading-assets}

Consulte [Baixar ativos de AEM](download-assets-from-aem.md)

## Publicar ativos {#publishing-assets}

Se você publicar um ativo que está sendo processado, somente o conteúdo original será publicado. As execuções estão faltando. Aguarde a conclusão do processamento e publique ou republique o ativo após a conclusão do processamento.

Se a pasta que você deseja publicar incluir uma pasta vazia, a pasta vazia não será publicada.

Para obter mais informações específicas ao Dynamic Media, consulte [Publicar Dynamic Media Assets](publishing-dynamicmedia-assets.md).

**Para publicar ativos**:

1. Navegue até o local dos ativos/pastas que deseja publicar

1. Selecione a ação rápida **[!UICONTROL Publicar]** no cartão de ativos ou selecione o ativo e toque no ícone **[!UICONTROL Publicação rápida]** na barra de ferramentas.
1. Se o ativo fizer referência a outros ativos, suas referências serão listadas no assistente. Somente as referências que não foram publicadas ou modificadas desde a última vez que foram publicadas ou não foram publicadas são exibidas. Escolha as referências que deseja publicar.

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Toque em **[!UICONTROL Publicar]** para confirmar a ativação dos ativos.

## Cancelar a publicação de ativos {#unpublishing-assets}

Ao cancelar a publicação de um ativo complexo, cancele a publicação somente do ativo. Evite cancelar a publicação das referências, pois elas podem ser referenciadas por outros ativos publicados.

**Para cancelar a publicação de ativos**:

1. Navegue até o local do ativo ou da pasta do ativo que deseja remover do ambiente de publicação (cancelar publicação).

1. Selecione o ativo ou a pasta para cancelar a publicação e toque no ícone **[!UICONTROL Gerenciar publicação]** na barra de ferramentas.

   ![manage_publication](assets/manage_publication.png)

1. Selecione a ação **[!UICONTROL Cancelar a publicação]** da lista.

   ![unpublish_action](assets/unpublish_action.png)

1. Para cancelar a publicação do ativo mais tarde, selecione **[!UICONTROL Cancelar a publicação mais tarde]** e selecione uma data para cancelar a publicação do ativo.
1. Agende uma data para o ativo ficar indisponível a partir do ambiente de publicação.
1. Se o ativo fizer referência a outros ativos, escolha as referências que deseja cancelar a publicação. Toque em **[!UICONTROL Cancelar a publicação]**.
1. Na caixa de diálogo de confirmação, execute um dos procedimentos a seguir:

   * Toque em **[!UICONTROL Cancelar]** para parar a ação
   * Toque em **[!UICONTROL Cancelar a publicação]** para confirmar que os ativos não foram publicados (não estão mais disponíveis no ambiente de publicação) na data especificada.

## Criar um grupo de usuários fechado {#closed-user-group}

Um CUG (Closed User Group) é usado para limitar o acesso a pastas de ativos específicas publicadas da AEM. Se você criar um CUG para uma pasta, o acesso à pasta (incluindo os ativos e as subpastas da pasta) será restrito somente aos membros ou grupos atribuídos. Para acessar a pasta, eles devem fazer logon usando suas credenciais de segurança.

CUG são uma maneira extra de restringir o acesso aos seus ativos. Você também pode configurar uma página de logon para a pasta.

**Para criar um grupo** de usuários fechado:

1. Selecione uma pasta na interface do usuário do Assets e toque no ícone **[!UICONTROL Propriedades]** na barra de ferramentas para exibir a página de propriedades.
1. Na guia **[!UICONTROL Permissões]**, adicione membros ou grupos em **[!UICONTROL Grupo de usuários fechado]**.

   ![add_user](assets/add_user.png)

1. Para exibir uma tela de logon quando os usuários acessarem a pasta, selecione a opção **[!UICONTROL Ativar]**. Em seguida, selecione o caminho para uma página de logon no AEM e salve as alterações.

   ![login_page](assets/login_page.png)

   Se você não especificar o caminho para uma página de logon, AEM exibirá a página de logon padrão na instância de publicação.

1. Publique a pasta e tente acessá-la da instância de publicação. Uma tela de login é exibida.
1. Se você for um membro do CUG, insira suas credenciais de segurança. A pasta é exibida depois que AEM o autentica.

## Pesquisar ativos {#searching-assets}

A pesquisa básica está detalhada na seção [Pesquisar e filtrar](/help/sites-authoring/search.md#search-and-filter). Use o painel **[!UICONTROL Pesquisar]** para pesquisar ativos, tags e metadados. Você pode pesquisar partes de uma string usando o asterisco curinga. Além disso, você pode personalizar o painel **[!UICONTROL Pesquisar]** usando [Aspectos de pesquisa](search-facets.md).

![Painel_filtros](assets/filters_panel.png)

Para ativos carregados recentemente, seus metadados (incluindo títulos, tags e assim por diante) não estão disponíveis imediatamente na lista de sugestões que aparecem quando você digita na caixa Omnisearch.

Isso ocorre porque a AEM Assets aguarda até a expiração de um período de tempo limite (1 hora por padrão) antes de executar um trabalho em segundo plano para indexar os metadados de todos os ativos recentemente carregados/atualizados e adicioná-los à lista de sugestões.

## Usar ações rápidas {#quick-actions}

Os ícones de ação rápida estão disponíveis para um único ativo por vez. Dependendo do seu dispositivo, execute as seguintes ações para exibir os ícones de ação rápida:

* Dispositivos de toque: Toque e segure. Por exemplo, em um iPad, é possível tocar e segurar um ativo para que as ações rápidas sejam exibidas.
* Dispositivos não sensíveis ao toque: Passe o ponteiro do mouse. Por exemplo, em um dispositivo de desktop, a barra de ação rápida é exibida se você passar o ponteiro do mouse sobre a miniatura do ativo.

### Navegue até e selecione ativos {#navigating-and-selecting-assets}

Você pode visualização, navegar e selecionar ativos com qualquer uma das visualizações disponíveis (cartão, coluna, lista) usando o ícone **[!UICONTROL Selecionar]**. **[!UICONTROL Seleted (Selecionar)]** é exibido como uma ação rápida na visualização do cartão.

![select_quick_action](assets/select_quick_action.png)

Na visualização da lista, **[!UICONTROL Select]** é exibido quando você passa o ícone do mouse sobre a miniatura antes dos nomes dos ativos/pastas na lista.

![select_quick_in_listview](assets/select_quick_in_listview.png)

Semelhante à visualização da lista, **[!UICONTROL Select]** aparece quando você passa o mouse sobre a miniatura antes dos nomes dos ativos ou da pasta na visualização da coluna.

![select_quick_in_columnview](assets/select_quick_in_columnview.png)

Para obter mais informações, consulte [Visualizar e selecionar seus recursos](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Editar imagens {#editing-images}

As ferramentas de edição na interface do AEM Assets permitem executar pequenos trabalhos de edição em ativos de imagem. É possível recortar, girar, virar e executar outras tarefas de edição em imagens. Também é possível adicionar mapas de imagem a ativos.

A edição de imagens é compatível com arquivos que têm os seguintes formatos:

* BMP
* GIF
* PNG
* JPEG

Para alguns componentes, o modo **[!UICONTROL Tela cheia]** tem opções adicionais disponíveis.

Para editar um arquivo TXT, defina **[!UICONTROL Externalizador de links Day CQ]** de dentro do Configuration Manager.

Também é possível adicionar mapas de imagem usando o editor de imagens. Para obter detalhes, consulte [Adicionar mapas de imagem](image-maps.md).

**Para editar imagens**:

1. Execute um dos procedimentos a seguir para abrir um ativo no modo de edição:

   * Selecione o ativo e clique no ícone **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque na opção **[!UICONTROL Editar]** que é exibida em um ativo na visualização do cartão.
   * Na página de ativos, toque no ícone **[!UICONTROL Editar]** na barra de ferramentas.

   ![edit_icon](assets/edit_icon.png)

1. Para recortar a imagem, toque em **[!UICONTROL Recortar]**.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Selecione a opção desejada na lista. A área de corte aparece na imagem com base na opção escolhida. A opção **[!UICONTROL Mão livre]** permite cortar a imagem sem restrições de proporção.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Selecione a área a ser recortada e redimensione ou reposicione-a na imagem.
1. Use a opção **[!UICONTROL Concluir]** no canto superior direito para cortar a imagem. Tocar em **[!UICONTROL Concluir]** também aciona a regeneração de execuções.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Use os ícones **[!UICONTROL Desfazer]** e **[!UICONTROL Refazer]** no canto superior direito para reverter para a imagem não cortada ou manter a imagem recortada, respectivamente.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Toque no ícone **[!UICONTROL Girar]** apropriado para girar a imagem no sentido horário ou anti-horário.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Toque no ícone **[!UICONTROL Virar]** apropriado para virar a imagem na horizontal ou na vertical.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Toque no ícone **[!UICONTROL Concluir]** para salvar as alterações.

   ![chlimage_1-28](assets/chlimage_1-28.png)

## Usar a linha do tempo {#timeline}

A **[!UICONTROL Linha do tempo]** permite que você visualização vários eventos para um item selecionado, como workflows ativos para um ativo, comentários, anotações, registros de atividades e versões.

No console [Coleções](managing-collections-touch-ui.md#navigating-the-collections-console), a lista **[!UICONTROL Mostrar tudo]** fornece opções para visualização somente de comentários e workflows. Além disso, a linha do tempo é exibida somente para coleções de nível superior listadas no console. Ela não será exibida se você navegar dentro de qualquer uma das coleções.

**[!UICONTROL O]** Timelinecontiver várias  [opções específicas para Fragmentos](content-fragments-managing.md#timeline-for-content-fragments) de conteúdo; essa funcionalidade exige  [AEM 6.4 Service Pack 2 (6.4.2.0) ](/help/release-notes/sp-release-notes.md) ou posterior.

**Para usar a Linha do tempo**:

1. Abra a página do ativo de um ativo ou selecione-o na interface do usuário Ativos.
1. Toque no ícone **[!UICONTROL Navegação global]** e escolha **[Linha do tempo]** na lista.

   ![linha do tempo](assets/timeline.png)

1. Na lista exibida, use a lista **[!UICONTROL Mostrar tudo]** para filtrar os resultados com base em comentários, versões, workflows e atividades.

   ![linha do tempo_opções](assets/timeline_options.png)

## Adicionar anotações {#annotating}

Anotações são comentários ou notas explicativas adicionadas a imagens ou vídeos. As anotações fornecem aos comerciantes a capacidade de colaborar e deixar feedback sobre os ativos.

As anotações de vídeo são compatíveis apenas em navegadores com formatos de vídeo compatíveis com HTML5. Os formatos de vídeo suportados pela AEM Assets dependem do navegador.

Para Fragmentos de conteúdo, as anotações [são criadas no editor](content-fragments-variations.md#annotating-a-content-fragment); essa funcionalidade exige o [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) ou posterior.

É possível adicionar várias anotações antes de salvá-las.

É possível adicionar anotações a ativos de vídeo. Ao anotar vídeos, o player pausa para permitir que você anote em um quadro. Para obter detalhes, consulte [gerenciar ativos de vídeo](managing-video-assets.md).

Também é possível adicionar anotações a uma coleção. No entanto, se uma coleção contiver coleções secundárias, você poderá adicionar anotações ou comentários somente à coleção pai. A opção **[!UICONTROL Anotar]** não está disponível para coleções secundárias.

**Para adicionar anotações**:

1. Navegue até o local do ativo ao qual você deseja adicionar anotações.
1. Toque no ícone **[!UICONTROL Anotar]** de um dos seguintes:

   * [Ações rápidas](managing-assets-touch-ui.md#quick-actions)
   * Na barra de ferramentas depois de selecionar o ativo ou navegar até a página do ativo

   ![chlimage_1-21](assets/chlimage_1-29.png)

1. Adicione um comentário na caixa **[!UICONTROL Comentário]** na parte inferior da linha do tempo. Como alternativa, marque uma área na imagem e adicione uma anotação na caixa de diálogo **[!UICONTROL Adicionar anotação]**.

   ![chlimage_1-30](assets/chlimage_1-30.png)

1. Para notificar um usuário sobre uma anotação, especifique o endereço de email do usuário e adicione o comentário. Por exemplo, para notificar Aaron McDonald sobre uma anotação, digite @aa. As dicas para todos os usuários correspondentes são exibidas em uma lista. Selecione o endereço de email do Aaron na lista para marcá-lo com o comentário. Da mesma forma, você pode marcar mais usuários em qualquer lugar dentro da anotação ou antes ou depois dela.

   >[!NOTE]
   >
   >Para um usuário que não seja administrador, as sugestões serão exibidas somente se o usuário tiver permissões de Leitura em `/home` no CRXDE.

   ![chlimage_1-31](assets/chlimage_1-31.png)

1. Depois de adicionar a anotação, toque em **[!UICONTROL Adicionar]** para salvá-la. Uma notificação para a anotação é enviada para Aaron.

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Toque em **[!UICONTROL Fechar]** para sair do modo **[!UICONTROL Anotação]**.
1. Para visualização da notificação, faça logon no AEM Assets com as credenciais do Aaron MacDonald e toque no ícone **[!UICONTROL Notificações]** para visualização da notificação.

1. Para escolher uma cor diferente para diferenciar os usuários, toque no ícone **[!UICONTROL Perfil]** e toque em **[!UICONTROL Minhas preferências]**.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Especifique a cor desejada na caixa **[!UICONTROL Cor da anotação]** e toque em **[!UICONTROL Aceitar]**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

### Visualização de anotações salvas {#viewing-saved-annotations}

1. Para visualização de anotações salvas para um ativo, navegue até o local do ativo e abra a página do ativo para o ativo.

1. Toque no ícone **[!UICONTROL Navegação global]** e toque em **[!UICONTROL Linha do tempo]** a partir da lista.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Na lista **[!UICONTROL Exibir todos]** na linha do tempo, selecione **[!UICONTROL Comentários]** para filtrar os resultados com base em anotações.

   ![chlimage_1-36](assets/chlimage_1-36.png)

1. Toque em um comentário no painel **[!UICONTROL Linha do tempo]** para visualização a anotação correspondente na imagem.

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. Toque em **[!UICONTROL Excluir]** para remover um comentário específico.

### Imprimir anotações {#printing-annotations}

Se um ativo tiver anotações ou tiver sido submetido a um fluxo de trabalho de revisão, você poderá imprimir o ativo junto com anotações e revisar o status como um arquivo PDF para revisão offline.

Você também pode imprimir somente as anotações ou o status da revisão.

Anotações extensas podem não ser renderizadas corretamente no arquivo PDF. Para uma renderização ideal, o Adobe recomenda que você limite as anotações a 50 palavras.

Para imprimir as anotações e revisar o status, toque no ícone **[!UICONTROL Imprimir]** e siga as instruções do assistente. O ícone **[!UICONTROL Imprimir]** aparece na barra de ferramentas somente quando o ativo tem pelo menos um status de anotação ou revisão atribuído a ele.

1. Na interface do usuário Ativos, abra a página pré-visualização de um ativo.
1. Faça uma das seguintes opções:

   * Para imprimir todas as anotações e o status da revisão, vá para a etapa 4.
   * Para imprimir anotações específicas e verificar o status, abra a [Linha do tempo](managing-assets-touch-ui.md#timeline) e prossiga para a etapa 3.

1. Para imprimir anotações específicas, selecione as anotações na **[!UICONTROL Linha do tempo]**.

   ![chlimage_1-38](assets/chlimage_1-38.png)

   Para imprimir somente o status da revisão, selecione-o na **[!UICONTROL Linha do tempo]**.

   ![chlimage_1-39](assets/chlimage_1-39.png)

1. Na barra de ferramentas, toque no ícone **[!UICONTROL Imprimir]**.

   ![chlimage_1-40](assets/chlimage_1-40.png)

1. Na caixa de diálogo **[!UICONTROL Imprimir]**, escolha a posição que deseja que as anotações ou o status de revisão sejam exibidos no PDF. Por exemplo, se desejar que as anotações ou o status sejam impressos no canto superior direito da página que contém a imagem impressa, use a configuração **[!UICONTROL Superior esquerdo]** (padrão).

   ![chlimage_1-41](assets/chlimage_1-41.png)

   É possível escolher outras configurações, dependendo da posição em que deseja que as anotações ou o status apareçam no PDF impresso. Se desejar que as anotações ou o status apareçam em uma página separada do ativo impresso, escolha **[!UICONTROL Próxima página]**.

1. Toque em **[!UICONTROL Imprimir]**. Dependendo da opção escolhida na etapa 2, o PDF gerado exibirá as anotações ou o status na posição especificada. Por exemplo, se optar por imprimir as anotações e o status da revisão usando a configuração **[!UICONTROL Superior esquerdo]**, o resultado será semelhante ao arquivo PDF mostrado aqui.

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. Baixe ou imprima o PDF usando as opções na parte superior direita.

   ![chlimage_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Se o ativo tiver subativos, você poderá imprimir todos os subativos junto com suas anotações específicas em nível de página.

   Para modificar a aparência do arquivo PDF renderizado, por exemplo, a cor, o tamanho e o estilo da fonte, a cor de plano de fundo dos comentários e status, abra a **[!UICONTROL Configuração do PDF de anotação]** de **[!UICONTROL Configuration Manager]** e modifique as opções desejadas. Por exemplo, para alterar a cor de exibição do status aprovado, modifique o código de cor no campo correspondente. Para obter informações sobre como alterar a cor da fonte das anotações, consulte [Anotar](managing-assets-touch-ui.md#annotating).

   ![chlimage_1-44](assets/chlimage_1-44.png)

   Retorne ao arquivo PDF renderizado e atualize-o. O PDF atualizado reflete as alterações feitas.

**Para imprimir anotações em idiomas** estrangeiros: Se um ativo incluir anotações em idiomas estrangeiros (especialmente idiomas não latinos), você deve primeiro configurar o CQ-DAM-Handler-Gibson Font Manager Service no servidor AEM para poder imprimir essas anotações. Ao configurar o serviço CQ-DAM-Handler-Gibson Font Manager, forneça o caminho onde as fontes dos idiomas desejados estão localizadas.

1. Abra a página de configuração **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager Service]** a partir da URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl).
1. Para configurar **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager Service]**, execute um dos seguintes procedimentos:

   * Na opção de diretório **[!UICONTROL Fontes do sistema]**, especifique o caminho completo para o diretório de fontes no seu sistema. Por exemplo, se você for um usuário do Mac, poderá especificar o caminho como `/Library/Fonts` na opção de diretório **[!UICONTROL Fontes do sistema]**. AEM as fontes deste diretório.
   * Crie um diretório chamado **fonts** dentro da pasta **[!UICONTROL crx-quickstart]**. **[!UICONTROL O serviço CQ-DAM-Handler-Gibson Font Manager]** busca automaticamente as fontes no local  `crx-quickstart/fonts`. Você pode substituir esse caminho padrão na opção de diretório **[!UICONTROL Fontes do servidor Adobe]**.
   * Crie uma nova pasta para fontes em seu sistema e armazene as fontes desejadas na pasta. Em seguida, especifique o caminho completo para essa pasta na opção de diretório **[!UICONTROL Fontes do cliente]**.

1. Acesse a configuração de **[!UICONTROL Anotação PDF]** a partir do URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig](http://localhost:4502/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig).
1. Configure o **[!UICONTROL PDF de anotação]** com o conjunto correto de tipos de letra como segue:

   * Inclua a string `<font_family_name_of_custom_font, sans-serif>` na opção font-family. Por exemplo, se você quiser imprimir anotações em CJK (chinês, japonês e coreano), inclua a string `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` na opção font-family. Se quiser imprimir anotações em Hindi, baixe a fonte apropriada e configure a família de fontes como Arial Unicode MS, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, sans-serif.

1. Reinicie a instância AEM.

Este é um exemplo de como você configura AEM para imprimir anotações em CJK (chinês, japonês e coreano):

1. Baixe as fontes do Google Noto CJK dos links a seguir e armazene-as no diretório de fontes configurado no Serviço do Gerenciador de fontes.

   * Todas em uma fonte Super CJK: [https://www.google.com/get/noto/help/cjk/](https://www.google.com/get/noto/help/cjk/)
   * Noto Sans (para as línguas europeias): [https://www.google.com/get/noto/](https://www.google.com/get/noto/)
   * Não use fontes para um idioma de sua escolha: [https://www.google.com/get/noto/](https://www.google.com/get/noto/)

1. Configure o arquivo PDF de anotação definindo o parâmetro font-family como `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif`. Esta configuração está disponível por padrão e funciona para todos os idiomas europeus e CJK.
1. Se o idioma de sua escolha for diferente dos idiomas mencionados na etapa 2, anexe uma entrada apropriada (separada por vírgulas) à família de fontes padrão.

## Criar controle de versão de ativos {#asset-versioning}

O controle de versão cria um instantâneo de ativos digitais em um ponto específico do tempo. O controle de versão ajuda a restaurar ativos para um estado anterior posteriormente. Por exemplo, se você deseja desfazer uma alteração feita em um ativo, restaure a versão não editada do ativo.

A seguir estão os cenários nos quais você cria versões:

* Você modifica uma imagem em um aplicativo diferente e faz upload para a AEM Assets. Uma versão da imagem é criada para que sua imagem original não seja substituída.
* Edite os metadados de um ativo.
* Use AEM aplicativo de desktop para fazer check-out de um ativo existente e salvar suas alterações. Uma nova versão é criada sempre que o ativo é salvo.

Você também pode ativar o controle automático de versão por meio de um fluxo de trabalho. Quando você cria uma versão para um ativo, os metadados e as execuções são salvos junto com a versão. As execuções são alternativas renderizadas das mesmas imagens, por exemplo, uma execução PNG de um arquivo JPEG carregado.

A funcionalidade de controle de versão permite fazer o seguinte:

* Criar uma versão de um ativo.
* Visualização da revisão atual de um ativo.
* Restaure o ativo para uma versão anterior.

**Para criar o controle de versão** do ativo:

1. Navegue até o local do ativo para o qual deseja criar uma versão e clique nele para abrir sua página de ativo.

1. Clique no ícone **[!UICONTROL Navegação Global]** e escolha **[!UICONTROL Linha do tempo]** no menu.

   ![linha do tempo 1](assets/timeline-1.png)

1. Clique em **[!UICONTROL Ações]** na parte inferior para visualização das ações disponíveis que você pode executar no ativo.

1. Clique em **[!UICONTROL Salvar como versão]** para criar uma versão para o ativo.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Adicione um rótulo e um comentário e clique em **[!UICONTROL Criar]** para criar uma versão. Como alternativa, toque em **[!UICONTROL Cancelar]** para sair da operação.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Para visualização da nova versão, abra a lista **[!UICONTROL Mostrar tudo]** na linha do tempo na página de detalhes do ativo ou na interface [!DNL Assets] e escolha **[!UICONTROL Versões]**.

   ![version_option](assets/versions_option.png)

1. Selecione uma versão específica para o ativo a ser pré-visualização ou permita que ele apareça na interface do usuário do Assets.

   ![select_version](assets/select_version.png)

   >[!NOTE]
   >
   >Você também pode selecionar o ativo da visualização [Lista](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) ou da visualização [Coluna](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

1. Adicione um rótulo e um comentário para a versão para reverter para a versão específica na interface do usuário do Assets.

   ![save_version](assets/save_version.png)

1. Para gerar uma pré-visualização para a versão, clique em **[!UICONTROL Versão da Pré-visualização]**.
1. Para exibir essa versão na interface do usuário do Assets, selecione **[!UICONTROL Reverter para esta versão]**.
1. Para comparar duas versões, vá para a página de ativos do ativo e clique na versão que deseja comparar com a versão atual.

   ![Selecione uma versão anterior do ativo para comparar com a versão atual](assets/select_version_tocompare.png)

1. Na linha do tempo, selecione a versão que deseja comparar e arraste o controle deslizante para a esquerda para sobrepor essa versão à versão atual e compare.

   ![compare_Versões](assets/compare_versions.png)

### Start de um fluxo de trabalho em um ativo {#starting-a-workflow-on-an-asset}

Consulte [aplicar um fluxo de trabalho a um ativo AEM](/help/assets/assets-workflow.md#apply-a-workflow-to-an-aem-asset).

## Sobre coleções {#collections}

Uma coleção é um conjunto ordenado de ativos. Use coleções para compartilhar ativos entre usuários.

* Uma coleção pode incluir ativos de diferentes locais, pois eles só contêm referências a esses ativos. Cada coleção mantém a integridade referencial dos ativos.
* Você pode compartilhar coleções com vários usuários com diferentes níveis de privilégio, incluindo edição, visualização e assim por diante.

Um usuário pode ter acesso a várias coleções. As coleções são dos seguintes tipos, com base na maneira como elas coletam ativos:

* Uma coleção com uma **lista de referência estática** de ativos, pastas e outras coleções.

* Uma coleção que usa **critérios de pesquisa** e preenche dinamicamente ativos com base nos critérios. Isso é chamado de **Coleção inteligente**.

Consulte [Gerenciar coleções](managing-collections-touch-ui.md) para obter detalhes sobre o gerenciamento de coleções.

>[!NOTE]
>
>Você exige direitos de acesso apropriados para sua conta criar ou editar ativos.
