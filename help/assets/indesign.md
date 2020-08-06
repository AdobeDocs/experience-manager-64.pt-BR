---
title: Integrar o AEM Assets ao Adobe InDesign Server
description: Saiba como integrar a AEM Assets ao InDesign Server.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 5%

---


# Integrar o AEM Assets ao Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Os ativos Adobe Experience Manager (AEM) usam:

* Um proxy para distribuir a carga de determinadas tarefas de processamento. Um proxy é uma instância AEM que se comunica com um representante para atender a uma tarefa específica e outras instâncias AEM para fornecer os resultados.
* Um funcionário proxy para definir e gerenciar uma tarefa específica.

Podem abranger uma grande variedade de tarefas; por exemplo, usar um Adobe InDesign Server para processar arquivos.

Para fazer o upload completo de arquivos para a AEM Assets criados com a Adobe InDesign, um proxy é usado. Isso usa um funcionário proxy para se comunicar com o Adobe InDesign Server, onde [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) são executados para extrair metadados e gerar várias execuções para o AEM Assets. O trabalho proxy permite a comunicação bidirecional entre o InDesign Server e as instâncias AEM em uma configuração em nuvem.

>[!NOTE]
>
>A Adobe InDesign é composta por dois produtos:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Isso permite que você crie layouts de página para distribuição impressa e/ou digital.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Esse mecanismo permite que você crie documentos automatizados de forma programática com base no que você criou com o InDesign. Ele opera como um serviço que oferece uma interface para seu mecanismo [ExtendScript](https://www.adobe.com/devnet/scripting.html) .\
   >  Os scripts são escritos no ExtendScript, que é semelhante ao javascript. Para obter informações sobre scripts do Indesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>



## Como a Extração funciona {#how-the-extraction-works}

O InDesign Server pode ser integrado ao AEM Assets para que os arquivos criados com o InDesign ( `.indd`) possam ser carregados, as representações geradas, *todas* as mídias extraídas (por exemplo, vídeo) e armazenadas como ativos:

>[!NOTE]
>
>As versões anteriores do AEM conseguiram extrair XMP e a miniatura, agora todas as mídias podem ser extraídas.

1. Carregue seu `.indd` arquivo no AEM Assets.
1. Uma estrutura envia scripts de comando para o InDesign Server via SOAP (Simple Object Access Protocol).

   Esse script de comando:

   * Recupere o `.indd` arquivo.
   * Executar comandos do InDesign Server:

      * A estrutura, o texto e quaisquer arquivos de mídia são extraídos.
      * Execuções de PDF e JPG são geradas.
      * Execuções HTML e IDML são geradas.
   * Poste os arquivos resultantes de volta ao AEM Assets.

   >[!NOTE]
   >
   >O IDML é um formato baseado em XML que renderiza *tudo* no arquivo de InDesign. Ele é armazenado como um pacote compactado usando a compactação [Zip](https://www.techterms.com/definition/zip) .
   >
   >Consulte [Adobe InDesign Interchange Formats INX e IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) para obter mais informações.

   >[!CAUTION]
   >
   >Se o InDesign Server não estiver instalado ou configurado, você ainda poderá fazer upload de um `.indd` arquivo para o AEM. No entanto, as representações geradas serão limitadas a `png` e `jpeg`, você não poderá gerar `html`ou as representações da página `idml` .

1. Após a geração de extração e execução:

   * A estrutura é replicada para um `cq:Page` (tipo de representação).
   * O texto e os arquivos extraídos são armazenados no AEM Assets.
   * Todas as representações são armazenadas no AEM Assets, no próprio ativo.

## Integração do InDesign Server com o AEM {#integrating-the-indesign-server-with-aem}

Para integrar o InDesign Server para uso com a AEM Assets e depois de configurar seu proxy, é necessário:

1. [Instale o InDesign Server](#installing-the-indesign-server).
1. Se necessário, [configure o AEM Assets Workflow](#configuring-the-aem-assets-workflow).

   Isso só é necessário se os valores padrão não forem apropriados para sua instância.

1. Configure um [proxy para o InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Instalação do InDesign Server {#installing-the-indesign-server}

Para instalar e start o InDesign Server para uso com AEM:

1. Baixe e instale o Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 e superior).

1. Se necessário, você pode personalizar a configuração da instância do InDesign Server.

1. Na linha de comando, start o servidor:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Isso start o servidor com o plug-in SOAP que escuta na porta 8080. Todas as mensagens de registro e saída são gravadas diretamente na janela de comando.

   >[!NOTE]
   >
   >Se desejar salvar as mensagens de saída em um arquivo, use redirecionamento; por exemplo, em Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configuração do fluxo de trabalho do AEM Assets {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **DAM Update Asset**, that has several process steps specifically for InDesign:

* [Extração de mídia](#media-extraction)
* [Extração de página](#page-extraction)

Este fluxo de trabalho é configurado com valores padrão que podem ser adaptados para sua configuração nas várias instâncias do autor (este é um fluxo de trabalho padrão, portanto, mais informações estão disponíveis em [Editar um fluxo de trabalho](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se você estiver usando os valores padrão (incluindo a porta SOAP), nenhuma configuração será necessária.

Após a configuração, o upload de arquivos de InDesign no AEM Assets (por qualquer um dos métodos habituais) acionará o fluxo de trabalho necessário para processar o ativo e preparar as várias execuções. Teste sua configuração carregando um `.indd` arquivo no AEM Assets para confirmar que você vê as diferentes execuções criadas pelo IDS em `<*your_asset*>.indd/Renditions`

#### Extração de mídia {#media-extraction}

Esta etapa controla a extração da mídia a partir do `.indd` arquivo.

Para personalizar, edite a guia **[!UICONTROL Argumentos]** da etapa **[!UICONTROL Extração de mídia]**.

![Argumentos de extração de mídia e caminhos de script](assets/media_extraction_arguments_scripts.png)

Argumentos de extração de mídia e caminhos de script

* **Biblioteca** ExtendScript: Esta é uma biblioteca de métodos http get/post simples, exigida pelos outros scripts.

* **Estender scripts**: É possível especificar diferentes combinações de scripts aqui. Se você quiser que seus próprios scripts sejam executados no InDesign Server, salve os scripts em `/apps/settings/dam/indesign/scripts`.

   Para obter informações sobre scripts do Indesign, consulte [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Não altere a biblioteca ExtendScript. A biblioteca fornece a funcionalidade HTTP necessária para se comunicar com o Sling. Esta configuração especifica a biblioteca a ser enviada para a Adobe InDesign Server para uso lá.

O `ThumbnailExport.jsx` script executado pela etapa de fluxo de trabalho da Extração de mídia gera uma execução em miniatura no formato .jpg. Essa execução é usada pela etapa de fluxo de trabalho Processar miniaturas para gerar as representações estáticas exigidas pela AEM.

Você pode configurar a etapa de fluxo de trabalho Processar miniaturas para gerar representações estáticas em tamanhos diferentes. Certifique-se de não remover os padrões, pois eles são exigidos pela interface do usuário do AEM Assets. Por fim, a etapa do fluxo de trabalho Excluir representação de Pré-visualização de imagem remove a execução de miniatura .jpg, pois ela não é mais necessária.

#### Extração de página {#page-extraction}

Isso cria uma página AEM dos elementos extraídos. Um manipulador de extração é usado para extrair dados de uma execução (atualmente HTML ou IDML). Esses dados são usados para criar uma página usando o PageBuilder.

Para personalizar, edite a guia **[!UICONTROL Argumentos]** da etapa **Extração de página**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Manipulador** de Extração da página: Na lista suspensa, selecione o manipulador que deseja usar. Um manipulador de extração opera em uma representação específica, escolhida por um `RenditionPicker` relacionado (consulte a `ExtractionHandler` API). Por padrão, o IDML Export Extração Handler está disponível. Ele opera na `IDML` representação gerada na etapa MediaExtract.

* **Nome** da página: Especifique o nome que deseja atribuir à página resultante. Se deixado em branco, o nome será &quot;page&quot; (ou um derivado se &quot;page&quot; já existir).

* **Título** da página: Especifique o título que deseja atribuir à página resultante.

* **Caminho** raiz da página: O caminho para o local raiz da página resultante. Se deixado em branco, o nó que retém as representações do ativo será usado.

* **Modelo** de página: O modelo a ser usado ao gerar a página resultante.

* **Design** da página: O design da página a ser usado ao gerar a página resultante.

### Configuração do trabalho proxy para o InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>O trabalhador reside na instância do proxy.

1. No console Ferramentas, expanda Configurações **[!UICONTROL de]** Cloud Services no painel esquerdo. Em seguida, expanda Configuração **[!UICONTROL de proxy da]** Cloud.

1. Clique duas vezes no **[!UICONTROL trabalhador IDS]** para abrir a configuração.

1. Clique em **[!UICONTROL Editar]** para abrir a caixa de diálogo de configuração e definir as configurações necessárias:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool** IDS: Os pontos de extremidade SOAP a serem usados para comunicação com o InDesign Server. Você pode adicionar, remover e ordenar itens necessários.

1. Clique em **[!UICONTROL OK]** para salvar.

### Configuração do Externalizador de links CQ de dia  {#configuring-day-cq-link-externalizer}

Se o servidor do InDesign e o AEM forem executados em hosts diferentes ou se ambos os aplicativos não forem executados em portas padrão, configure o **Day CQ Link Externalizer** para definir o nome do host, a porta e o caminho do conteúdo para o servidor do InDesign.

1. Acesse o Configuration Manager no URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Localize o **[!UICONTROL Day CQ Link Externalizer]** e clique no ícone **[!UICONTROL Editar]** para abri-lo.
1. Especifique o nome do host e o caminho de contexto para o servidor do Indesign e clique em **[!UICONTROL Salvar]**.

   ![chlimage_1-290](assets/chlimage_1-290.png)

### Ativação do processamento de trabalho paralelo para InDesigns Server {#enabling-parallel-job-processing-for-indesign-server-s}

Agora você pode ativar o processamento paralelo de tarefas para IDS.

Primeiro, é necessário determinar o número máximo de trabalhos paralelos ( `x`) que um InDesign Server pode processar:

* Em uma única máquina de multiprocessador, o número máximo de trabalhos paralelos (x) que um InDesign Server pode processar é um menor que o número de processadores executando IDS.
* Ao executar IDS em várias máquinas, é necessário contar o número total de processadores disponíveis (ou seja, em todas as máquinas) e, em seguida, subtrair o número total de máquinas.

Para configurar o número de trabalhos de IDS paralelos:

1. Abra a guia **[!UICONTROL Configurações]** do Console do Felix; por exemplo:

   `http://localhost:4502/system/console/configMgr`

1. Selecione a fila de processamento IDS em:

   `Apache Sling Job Queue Configuration`

1. Ajustar:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Máximo de Trabalhos]** Paralelos - `<*x*>` (conforme calculado acima)

1. Salve essas alterações.
1. Para habilitar o suporte a várias sessões para o Adobe CS6 e posterior, marque a `enable.multisession.name` caixa de seleção em `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Crie um [pool de &lt; `*x*>` trabalhadores IDS adicionando pontos de extremidade SOAP à configuração](#configuring-the-proxy-worker-for-indesign-server)do IDS Worker.

   Se houver várias máquinas executando InDesigns Server, adicione pontos de extremidade SOAP (número de processadores por máquina -1) para cada máquina.

   >[!NOTE]
   >
   >Ao trabalhar com um pool de trabalhadores, você pode habilitar a lista de bloqueios de trabalhadores IDS.
   >
   >Para fazer isso, ative a caixa de seleção &quot;enable.retry.name&quot;, na `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuração, que ativa as tentativas de trabalho do IDS.
   >
   >Além disso, na `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuração, defina um valor positivo para o `max.errors.to.blacklist` parâmetro que determina o número de tentativas da tarefa antes de excluir uma IDS da lista de manipuladores de tarefas
   >
   >Por padrão, após o tempo configurável (`retry.interval.to.whitelist.name`) em minutos, o IDS worker é revalidado. Se o trabalhador for encontrado on-line, ele será removido da lista de bloqueios.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Habilitar suporte para o Adobe InDesign Server 10.0 ou posterior {#enabling-support-for-indesign-server-or-higher}

Para o servidor de InDesign 10.0 ou superior, execute as seguintes etapas para habilitar o suporte a várias sessões.

1. Abra o Configuration Manager da sua [!DNL Assets] instância `https://[aem_server]:[port]/system/console/configMgr`.
1. Edite a configuração `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecione **[!UICONTROL ids.cc.enable]** e clique em **[!UICONTROL Salvar]**.

>[!NOTE]
>
>Para [!DNL InDesign Server] integração com [!DNL Assets], use um processador multi-core porque o recurso de suporte de sessão necessário para a integração não é suportado em sistemas de núcleo único.

## Configurar credenciais de Experience Manager {#configure-aem-credentials}

Você pode alterar as credenciais de administrador padrão (nome de usuário e senha) para acessar o servidor de InDesigns da instância de AEM sem interromper a integração com o servidor Adobe InDesign.

1. Ir para `/etc/cloudservices/proxy.html`.
1. Na caixa de diálogo, especifique o novo nome de usuário e senha.
1. Salve as credenciais.
