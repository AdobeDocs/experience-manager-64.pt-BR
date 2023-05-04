---
title: Integrar [!DNL Experience Manager] Ativos com a Adobe InDesign Server
description: Saiba como integrar [!DNL Experience Manager] Ativos com o InDesign Server.
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 4%

---

# Integrar ativos ao Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager Assets usa:

* Um proxy para distribuir a carga de determinadas tarefas de processamento. Um proxy é um [!DNL Experience Manager] instância que se comunica com um trabalhador proxy para realizar uma tarefa específica, e outras [!DNL Experience Manager] para entregar os resultados.
* Um trabalhador proxy para definir e gerenciar uma tarefa específica.

Estas podem abranger uma grande variedade de tarefas; por exemplo, usar um Adobe InDesign Server para processar arquivos.

Para fazer o upload completo dos arquivos para o [!DNL Experience Manager] Ativos que você criou com o Adobe InDesign que um proxy é usado. Isso usa um trabalhador proxy para se comunicar com a Adobe InDesign Server, onde [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) são executados para extrair metadados e gerar várias renderizações para [!DNL Experience Manager] Ativos. O trabalhador proxy permite a comunicação bidirecional entre o InDesign Server e o [!DNL Experience Manager] instância(s) em uma configuração de nuvem.

>[!NOTE]
>
>O Adobe InDesign vem como dois produtos:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Isso permite que você crie layouts de página para distribuição impressa e/ou digital.
>
>* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Esse mecanismo permite que você crie documentos automatizados de forma programática com base no que você criou com o InDesign. Funciona como um serviço que oferece uma interface para o seu [ExtendScript](https://www.adobe.com/devnet/scripting.html) motor.\
   >  Os scripts são gravados em ExtendScript, que é semelhante ao JavaScript. Para obter informações sobre scripts Adobe InDesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## Como a extração funciona {#how-the-extraction-works}

O InDesign Server pode ser integrado ao [!DNL Experience Manager] Ativos para que os arquivos sejam criados com o InDesign ( `.indd`) podem ser carregadas, representações geradas, *all* mídia extraída (por exemplo, vídeo) e armazenada como ativos:

>[!NOTE]
>
>Versões anteriores de [!DNL Experience Manager] Conseguimos extrair XMP e a miniatura, agora todas as mídias podem ser extraídas.

1. Carregue seu `.indd` para [!DNL Experience Manager] Ativos.
1. Uma estrutura envia scripts de comando para o InDesign Server via SOAP (Simple Object Access Protocol).

   Este script de comando irá:

   * Recupere o `.indd` arquivo.
   * Executar comandos do InDesign Server:

      * A estrutura, o texto e os arquivos de mídia são extraídos.
      * As representações de PDF e JPG são geradas.
      * As representações de HTML e IDML são geradas.
   * Poste os arquivos resultantes de volta para [!DNL Experience Manager] Ativos.

   >[!NOTE]
   >
   >IDML é um formato baseado em XML que renderiza *all* no arquivo InDesign. Ele é armazenado como um pacote compactado usando [CEP](https://www.techterms.com/definition/zip) compactação.
   >
   >Consulte [Adobe InDesign Interchange Formatos INX e IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) para obter mais informações.

   >[!CAUTION]
   >
   >Se o InDesign Server não estiver instalado ou configurado, você ainda poderá fazer upload de um `.indd` arquivo em [!DNL Experience Manager]. No entanto, as representações geradas serão limitadas a `png` e `jpeg`, você não poderá gerar `html`, `idml` ou as representações de página.

1. Após a geração da extração e da representação:

   * A estrutura é replicada para um `cq:Page` (tipo de representação).
   * O texto e os arquivos extraídos são armazenados em [!DNL Experience Manager] Ativos.
   * Todas as representações são armazenadas em [!DNL Experience Manager] Ativos, no próprio ativo.

## Integração do InDesign Server com [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

Para integrar o InDesign Server para uso com o [!DNL Experience Manager] Ativos e, após configurar seu proxy, é necessário:

1. [Instalar o InDesign Server](#installing-the-indesign-server).
1. Se necessário, [configure o [!DNL Experience Manager] Fluxo de trabalho dos ativos](#configuring-the-aem-assets-workflow).

   Isso só será necessário se os valores padrão não forem apropriados para sua instância.

1. Configure um [trabalhador proxy para o InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Instalação do InDesign Server {#installing-the-indesign-server}

Para instalar e iniciar o InDesign Server para uso com [!DNL Experience Manager]:

1. Baixe e instale o Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 e superior).

1. Se necessário, é possível personalizar a configuração da instância do InDesign Server.

1. Na linha de comando, inicie o servidor:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Isso iniciará o servidor com o plug-in SOAP escutando na porta 8080. Todas as mensagens de log e a saída são gravadas diretamente na janela de comando.

   >[!NOTE]
   >
   >Se desejar salvar as mensagens de saída em um arquivo, use redirecionamento; por exemplo, em Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configurar a [!DNL Experience Manager] Fluxo de trabalho dos ativos {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] Os ativos têm um fluxo de trabalho pré-configurado **Ativo de atualização DAM**, que tem várias etapas do processo especificamente para o InDesign:

* [Extração de mídia ](#media-extraction)
* [Extração de página](#page-extraction)

Esse workflow é configurado com valores padrão que podem ser adaptados para sua configuração nas várias instâncias do autor (esse é um workflow padrão, portanto, mais informações estão disponíveis em [Editar um fluxo de trabalho](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se você estiver usando os valores padrão (incluindo a porta SOAP), nenhuma configuração será necessária.

Após a configuração, faça upload dos arquivos InDesign para [!DNL Experience Manager] Os ativos (de acordo com qualquer um dos métodos habituais) acionarão o fluxo de trabalho necessário para processar o ativo e preparar as várias representações. Teste sua configuração carregando uma `.indd` arquivo em [!DNL Experience Manager] Ativos para confirmar que você vê as diferentes representações criadas por IDS em `<*your_asset*>.indd/Renditions`

#### Extração de mídia  {#media-extraction}

Essa etapa controla a extração de mídia do `.indd` arquivo.

Para personalizar, edite a guia **[!UICONTROL Argumentos]** da etapa **[!UICONTROL Extração de mídia]**.

![Argumentos de extração de mídia e caminhos de script](assets/media_extraction_arguments_scripts.png)

Argumentos de extração de mídia e caminhos de script

* **Biblioteca da ExtendScript**: Esta é uma biblioteca de método http get/post simples, exigida pelos outros scripts.

* **Estender scripts**: Você pode especificar combinações de script diferentes aqui. Se quiser que seus próprios scripts sejam executados no InDesign Server, salve os scripts em `/apps/settings/dam/indesign/scripts`.

   Para obter informações sobre scripts de InDesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Não altere a biblioteca ExtendScript. A biblioteca fornece a funcionalidade HTTP necessária para se comunicar com o Sling. Essa configuração especifica a biblioteca a ser enviada para uso no Adobe InDesign Server.

O `ThumbnailExport.jsx` O script executado pela etapa do fluxo de trabalho Extração de mídia gera uma renderização de miniatura no formato JPG. Essa representação é usada pela etapa do fluxo de trabalho Processar miniaturas para gerar as representações estáticas necessárias para [!DNL Experience Manager].

Você pode configurar a etapa do fluxo de trabalho Processar miniaturas para gerar representações estáticas em tamanhos diferentes. Certifique-se de não remover os padrões, pois eles são exigidos pela variável [!DNL Experience Manager] Interface do usuário do Assets. Finalmente, a etapa do fluxo de trabalho Excluir representação da visualização de imagem remove a renderização de miniatura .jpg, pois não é mais necessária.

#### Extração de página {#page-extraction}

Isso cria um [!DNL Experience Manager] dos elementos extraídos. Um manipulador de extração é usado para extrair dados de uma representação (atualmente HTML ou IDML). Esses dados são usados para criar uma página usando o PageBuilder.

Para personalizar, edite a guia **[!UICONTROL Argumentos]** da etapa **Extração de página**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Manipulador de extração de página**: Na lista suspensa, selecione o manipulador que deseja usar. Um manipulador de extração opera em uma representação específica, escolhida por um `RenditionPicker` relacionado (consulte a `ExtractionHandler` API). Por padrão, o IDML Export Extraction Handler está disponível. Ela opera no `IDML` representação gerada na etapa MediaExtract .

* **Nome da página**: Especifique o nome que deseja atribuir à página resultante. Se deixado em branco, o nome será &quot;página&quot; (ou um derivado se &quot;página&quot; já existir).

* **Título da página**: Especifique o título que deseja atribuir à página resultante.

* **Caminho raiz da página**: O caminho para o local raiz da página resultante. Se deixado em branco, o nó que mantém as representações do ativo é usado.

* **Modelo de página**: O modelo a ser usado ao gerar a página resultante.

* **Design da página**: O design da página a ser usado ao gerar a página resultante.

### Configurar o trabalhador proxy para o InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>O trabalhador reside na instância do proxy.

1. No console Ferramentas , expanda **[!UICONTROL Configurações do Cloud Services]** no painel esquerdo. Em seguida, expanda **[!UICONTROL Configuração do Cloud Proxy]**.

1. Clique duas vezes no **[!UICONTROL trabalhador IDS]** para abrir a configuração.

1. Clique em **[!UICONTROL Editar]** para abrir a caixa de diálogo de configuração e definir as configurações necessárias:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool IDS**: Os endpoints SOAP a serem usados para comunicação com o InDesign Server. Você pode adicionar, remover e ordenar itens necessários.

1. Clique em **[!UICONTROL OK]** para salvar.

### Configurar o Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Se o InDesign Server e [!DNL Experience Manager] estão em hosts diferentes ou um ou ambos os aplicativos não estão funcionando em portas padrão, configure **Externalizador de links CQ do dia** para definir o nome do host, a porta e o caminho do conteúdo para o InDesign Server.

1. Acesse o Configuration Manager no URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Localize a configuração **[!UICONTROL Externalizador de links CQ do dia]**. Clique em **[!UICONTROL Editar]** para abrir.
1. As configurações do Link Externalizer ajudam a criar URLs absolutos para o [!DNL Experience Manager] e para a [!DNL InDesign Server]. Use **[!UICONTROL Domínios]** para especificar o nome do host e o caminho do contexto para a variável [!DNL Adobe InDesign Server]. Siga as instruções na tela. Clique em **[!UICONTROL Salvar]**.

   ![Configurações do externalizador de links](assets/link-externalizer-config.png)

### Ativação do processamento de trabalho paralelo para InDesigns Server {#enabling-parallel-job-processing-for-indesign-server}

Agora é possível habilitar o processamento paralelo de tarefas para IDS.

Primeiro, você precisa determinar o número máximo de trabalhos paralelos ( `x`) um InDesign Server pode processar:

* Em uma única máquina de multiprocessador, o número máximo de tarefas paralelas (x) que um InDesign Server pode processar é um a menos do que o número de processadores executando IDS.
* Ao executar IDS em várias máquinas, é necessário contar o número total de processadores disponíveis (ou seja, em todas as máquinas) e subtrair o número total de máquinas.

Para configurar o número de trabalhos paralelos do IDS:

1. Abra o **[!UICONTROL Configurações]** guia do Felix Console; por exemplo:

   `http://localhost:4502/system/console/configMgr`

1. Selecione a fila de processamento do IDS em:

   `Apache Sling Job Queue Configuration`

1. Definir:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Máximo de trabalhos paralelos]** - `<*x*>` (conforme calculado acima)

1. Salve essas alterações.
1. Para ativar o suporte a várias sessões para o Adobe CS6 e posterior, verifique o `enable.multisession.name` caixa de seleção em `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Crie um [conjunto de &lt; `*x*>` Trabalhadores IDS adicionando pontos de extremidade SOAP à configuração do trabalhador IDS](#configuring-the-proxy-worker-for-indesign-server).

   Se houver várias máquinas executando InDesigns Server, adicione pontos de extremidade SOAP (número de processadores por máquina -1) para cada máquina.

   >[!NOTE]
   >
   >Ao trabalhar com um pool de trabalhadores, você pode habilitar a lista de bloqueios de trabalhadores IDS.
   >
   >Para fazer isso, ative a caixa de seleção &quot;enable.retry.name&quot;, na guia `com.day.cq.dam.ids.impl.IDSJobProcessor.name` , que permite novas tentativas de trabalho do IDS.
   >
   >Além disso, em `com.day.cq.dam.ids.impl.IDSPoolImpl.name` , defina um valor positivo para `max.errors.to.blacklist` parâmetro que determina o número de novas tentativas de trabalho antes de barrar uma IDS da lista de manipuladores de trabalho
   >
   >Por padrão, depois do valor configurável (`retry.interval.to.whitelist.name`) em minutos, o trabalhador IDS é revalidado. Se o trabalhador for encontrado online, ele será removido da lista de bloqueios.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Ativar o suporte para o Adobe InDesign Server 10.0 ou posterior {#enabling-support-for-indesign-server-or-higher}

Para o servidor InDesign 10.0 ou superior, execute as seguintes etapas para ativar o suporte a várias sessões.

1. Abra o Gerenciador de configuração no [!DNL Assets] instância `https://[aem_server]:[port]/system/console/configMgr`.
1. Editar a configuração `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecionar **[!UICONTROL ids.cc.enable]** e clique em **[!UICONTROL Salvar]**.

>[!NOTE]
>
>Para [!DNL InDesign Server] integração com [!DNL Assets], use um processador multi-núcleo porque o recurso de suporte de sessão necessário para a integração não é suportado em sistemas de núcleo único.

## Configurar credenciais do Experience Manager {#configure-aem-credentials}

Você pode alterar as credenciais de administrador padrão (nome de usuário e senha) para acessar o servidor do InDesign de seu [!DNL Experience Manager] sem interromper a integração com o servidor do Adobe InDesign.

1. Ir para `/etc/cloudservices/proxy.html`.
1. Na caixa de diálogo, especifique o novo nome de usuário e senha.
1. Salve as credenciais.
