---
title: Vídeo no Dynamic Media
description: Saiba como trabalhar com vídeo no Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
exl-id: acb95a2b-0171-449e-97fa-f9a533f990de
feature: Video
role: User
source-git-commit: 7f4e44eb75ccae4a9ab1d95171b95a5e9fe48f64
workflow-type: tm+mt
source-wordcount: '10383'
ht-degree: 4%

---

# Vídeo {#video}

Esta seção descreve como trabalhar com vídeo no Dynamic Media.

## Início rápido: Vídeos {#quick-start-videos}

A seguinte descrição passo a passo do fluxo de trabalho foi criada para ajudá-lo a ativar e executar rapidamente com conjuntos de vídeos adaptáveis no Dynamic Media. Após cada etapa, são referências cruzadas a títulos de tópico, onde você pode encontrar mais informações.

>[!NOTE]
>
>Antes de trabalhar com vídeo no Dynamic Media, verifique se o administrador do AEM já ativou e configurou o Dynamic Media Cloud Services.
>
>* Consulte [Configuração do Dynamic Media Cloud Services em Configuração do Dynamic Media - Modo híbrido.](/help/assets/config-dynamic.md)
>* Consulte [Configuração do Dynamic Media - Modo Scene7](config-dms7.md) e [Solução de problemas do Dynamic Media - Modo Scene7](troubleshoot-dms7.md)

>


1. **Fazer upload de seus vídeos do Dynamic Media** fazendo o seguinte:

   * Crie seu próprio perfil de codificação de vídeo. Ou você pode simplesmente usar o perfil predefinido de &quot;Codificação de vídeo adaptável&quot; que vem com o Dynamic Media.

      * [Criação de um perfil de codificação de vídeo](video-profiles.md).
      * Saiba mais sobre [Práticas recomendadas para codificação de vídeo](#best-practices-for-encoding-videos).
   * Associe o perfil de processamento de vídeo a uma ou mais pastas, onde você fará upload dos vídeos principais.

      * [Aplicar um perfil de vídeo a pastas](video-profiles.md#applying-a-video-profile-to-folders).
      * Saiba mais sobre [Práticas recomendadas para organizar ativos digitais para usar perfis de processamento](organize-assets.md#organize-using-folders).
      * Saiba mais sobre [Organizar ativos digitais](organize-assets.md).
   * Faça upload dos vídeos de origem primária para as pastas. Ao adicionar vídeos à pasta, eles são codificados de acordo com o perfil de processamento de vídeo atribuído à pasta.

      * O Dynamic Media oferece suporte principalmente a vídeos de forma curta com uma duração máxima de 30 minutos.
      * Você pode fazer upload de arquivos de vídeo com até 15 GB cada.
      * [Fazer upload de seus vídeos](managing-video-assets.md#uploading-and-previewing-video-assets).
      * Saiba mais sobre [Formatos de arquivo de entrada suportados](assets-formats.md#supported-multimedia-formats).
   * Monitorar como [a codificação de vídeo está progredindo](#monitoring-video-encoding-and-youtube-publishing-progress) na visualização de ativo ou fluxo de trabalho.




1. **Gerenciar os vídeos do Dynamic Media** executando um dos seguintes procedimentos:

   * Organizar, navegar e pesquisar ativos de vídeo

      * [Organizar ativos digitais](organize-assets.md)

         Saiba mais sobre [Práticas recomendadas para organizar ativos digitais para usar perfis de processamento](organize-assets.md#organize-using-folders)

      * [Pesquisar ativos de vídeo](search-video-assets.md) ou [Pesquisar ativos](managing-assets-touch-ui.md#searching-assets)
   * Visualizar e publicar ativos de vídeo

      * Visualize o vídeo de origem e as representações codificadas do vídeo, juntamente com as miniaturas associadas:

         [Visualização de vídeos](managing-video-assets.md#uploading-and-previewing-video-assets) ou [Visualização de ativos](previewing-assets.md)

         [Exibição de representações de vídeo](video-renditions.md)

[Gerenciamento de representações de vídeo](managing-assets-touch-ui.md#managing-renditions)

      * [Gerenciar predefinições do visualizador](managing-viewer-presets.md)
      * [Publicação de ativos](publishing-dynamicmedia-assets.md)
   * Trabalhar com metadados de vídeo

      * Visualize as propriedades de uma representação de vídeo codificado, como taxa de quadros, taxa de bits de áudio e vídeo e codec:

         [Exibir propriedades de representação de vídeo](video-renditions.md)

      * Edite as propriedades do vídeo, como título, descrição e tags, e os campos de metadados personalizados:

[Edição de propriedades do vídeo](managing-assets-touch-ui.md#editing-properties)

      * [Gerenciamento de metadados para ativos digitais](metadata.md)
      * [Esquemas de metadados](metadata-schemas.md)
   * Revisar, aprovar e anotar vídeos

      * [Anotação de vídeos](managing-video-assets.md#annotating-video-assets) ou [Anotar ativos](managing-assets-touch-ui.md#annotating)
      * [Aplicar fluxos de trabalho a ativos](assets-workflow.md) ou [Iniciar um fluxo de trabalho em um ativo](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [Revisar ativos da pasta](bulk-approval.md)
      * [Projetos](/help/sites-authoring/projects.md)




1. **Publicar seus vídeos do Dynamic Media** executando um dos seguintes procedimentos:

   * Se você estiver usando o Adobe Experience Manager como seu sistema de gerenciamento de conteúdo da Web, poderá adicionar vídeos diretamente às suas páginas da Web.

      * [Adicionar vídeos às suas páginas da Web](adding-dynamic-media-assets-to-pages.md).
   * Se você estiver usando um sistema de gerenciamento de conteúdo da Web de terceiros, poderá vincular ou incorporar vídeos às suas páginas da Web.

      * Integrar vídeo usando URL:

         [Vincular URLs do ao aplicativo da Web](linking-urls-to-yourwebapplication.md).
      * Integre o vídeo usando o código incorporado na página da Web:

         [Incorporação do visualizador de vídeo em uma página da Web](embed-code.md).
   * [Publicar vídeos no YouTube](#publishing-videos-to-youtube).
   * [Geração de relatórios de vídeo](#viewing-video-reports).
   * [Adição de legendas ao vídeo](#adding-captions-to-video).



## Trabalhar com vídeo no Dynamic Media {#working-with-video-in-dynamic-media}

O vídeo no Dynamic Media é uma solução completa que facilita a publicação de vídeo adaptável de alta qualidade para transmissão em várias telas, incluindo dispositivos móveis para desktop, iOS, Android, Blackberry e Windows. Um Conjunto de vídeos adaptáveis agrupa versões do mesmo vídeo codificadas em diferentes formatos e taxas de bits, como 400 kbps, 800 kbps e 1000 kbps. O computador desktop ou dispositivo móvel detecta a largura de banda disponível.

Por exemplo, em um dispositivo móvel iOS, ele detecta uma largura de banda como 3G, 4G ou Wi-Fi. Em seguida, ele seleciona automaticamente o vídeo codificado direito dentre as várias taxas de bits de vídeo no Conjunto de vídeos adaptáveis. O vídeo é transmitido em desktops, dispositivos móveis ou tablets.

Além disso, a qualidade do vídeo é alternada dinamicamente automaticamente se as condições da rede mudarem no desktop ou no dispositivo móvel. Além disso, se um cliente entrar no modo de tela cheia em um desktop, o Adaptive Video Set responde usando uma resolução melhor, melhorando assim a experiência de visualização do cliente. O uso de conjuntos de vídeos adaptáveis fornece a melhor reprodução possível para os clientes que reproduzem o vídeo do Dynamic Media em várias telas e dispositivos.

A lógica usada por um reprodutor de vídeo para determinar qual vídeo codificado reproduzir ou selecionar durante a reprodução é baseada no seguinte algoritmo:

1. O reprodutor de vídeo carrega o fragmento de vídeo inicial com base na taxa de bits mais próxima do valor definido para &quot;taxa de bits inicial&quot; no próprio reprodutor.
1. O reprodutor de vídeo é alternado com base em alterações na velocidade da largura de banda usando os seguintes critérios:

   1. O reprodutor escolhe o fluxo de largura de banda mais alto abaixo ou igual à largura de banda estimada.
   1. O Player considera apenas 80% da largura de banda disponível. No entanto, se estiver mudando, é mais conservador em apenas 70% para evitar sobrestimações e imediatamente voltar.

Para obter informações técnicas detalhadas sobre o algoritmo, consulte [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Para gerenciar vídeos únicos e conjuntos de vídeos adaptáveis, o seguinte é suportado:

* Upload de vídeo de vários formatos de vídeo e formatos de áudio suportados e codificação de vídeo para o formato MP4 H.264 para reprodução em várias telas. Você pode usar predefinições de vídeo adaptável predefinidas, predefinições de codificação de vídeo único ou personalizar sua própria codificação para controlar a qualidade e o tamanho do vídeo.

   * Quando um conjunto de vídeo adaptável é gerado, ele inclui vídeos MP4.
   * **Observação**: Vídeos principais/de origem não são adicionados a um Conjunto de vídeos adaptáveis.

* Legenda de vídeo em todos os visualizadores de vídeo do HTML5.
* Organize, navegue e pesquise vídeos com suporte completo a metadados para o gerenciamento eficiente dos ativos de vídeo.
* Forneça Conjuntos de Vídeos Adaptativos para a Web, bem como para desktops e dispositivos móveis, incluindo iPhone, iPad, Android, Blackberry e Windows phone.

O streaming de vídeo adaptável é compatível com diversas plataformas iOS. Consulte a [Guia de referência de visualizadores de Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

O Dynamic Media oferece suporte para reprodução de vídeo móvel para vídeo MP4 H.264. Você pode encontrar dispositivos Blackberry que suportam esse formato de vídeo no seguinte endereço: [Formatos de vídeo compatíveis com o Blackberry](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

Você pode encontrar dispositivos Windows compatíveis com este formato de vídeo no seguinte endereço: [Formatos de vídeo compatíveis com o Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* Reproduzir o vídeo usando as Predefinições do visualizador de vídeo do Dynamic Media, incluindo o seguinte:

   * Visualizadores de vídeo individuais.
   * Visualizadores de mídia mista que combinam conteúdo de vídeo e imagem.

* Configure players de vídeo para atender às suas necessidades de marca.
* Integre vídeo ao seu site, site móvel ou aplicativo móvel com um URL simples ou código incorporado.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480). -->

Consulte também [Sobre visualizadores do HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) no Adobe Dynamic Media Viewers Reference Guide.

## Prática recomendada: Uso do visualizador de vídeo do HTML5 {#best-practice-using-the-html-video-viewer}

As predefinições do visualizador de vídeo do Dynamic Media HTML5 são players de vídeo robustos. Você pode usá-los para evitar muitos problemas comuns associados à reprodução de vídeo do HTML5 e problemas associados a dispositivos móveis, como a falta de entrega de transmissão adaptável e o alcance limitado do navegador do desktop.

No lado do design do reprodutor, é possível projetar toda a funcionalidade do reprodutor de vídeo usando ferramentas de desenvolvimento da Web padrão. Por exemplo, você pode projetar botões, controles e imagens de fundo de pôster personalizadas usando HTML5 e CSS para ajudá-lo a alcançar seus clientes com uma aparência personalizada.

No lado da reprodução do visualizador, ele detecta automaticamente o recurso de vídeo do navegador. Ele então serve o vídeo usando o streaming de HLS (streaming de vídeo adaptável). Ou, se esses métodos de entrega não estiverem presentes, então HTML5 progressivo será usado.

Ao combinar em um único reprodutor a capacidade de projetar os componentes de reprodução usando HTML5 e CSS, ter reprodução incorporada e usar transmissão adaptável e progressiva, dependendo da capacidade do navegador, você estende o alcance do conteúdo de mídia avançada para usuários de desktop e móveis e garante uma experiência de vídeo simplificada.

Consulte também [Sobre visualizadores do HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html) no Guia de referência de visualizadores do Adobe.

### Reprodução de vídeo em computadores desktop e dispositivos móveis usando o visualizador de vídeo HTML5 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Para streaming de vídeo adaptável para desktop e dispositivos móveis, os vídeos usados para alternância de taxa de bits são baseados em todos os vídeos MP4 no Adaptive Video Set.

A reprodução de vídeo ocorre usando streaming de vídeo HLS (HTTP Live Streaming) ou download de vídeo progressivo. Em versões anteriores do AEM, como 6.0, 6.1 e 6.2, os vídeos eram transmitidos via HTTP.

No entanto, no AEM 6.3 e mais, os vídeos agora são transmitidos por HTTPS (ou seja, streaming de vídeo HLS), pois o URL do serviço de gateway do DM sempre usa HTTPS também. Observe que não há impacto do cliente nesse comportamento padrão. Ou seja, o streaming de vídeo sempre ocorrerá por HTTPS, a menos que não seja suportado pelo navegador. (ver quadro seguinte). Portanto,

* Se você tiver um site HTTPS com streaming de vídeo HTTPS, o streaming estará bom.
* Se você tiver um site HTTP com streaming de vídeo HTTPS, o streaming estará correto e não haverá problemas de conteúdo misto no navegador da Web.

O HLS (HTTP Live Streaming) é um padrão Apple para streaming de vídeo adaptável que ajusta automaticamente a reprodução com base na capacidade da largura de banda da rede. Ele também permite que o cliente &quot;procure&quot; em qualquer ponto do vídeo, sem precisar aguardar o download do restante do vídeo (consulte também HTTP Live Streaming).

O vídeo progressivo é fornecido pelo download e armazenamento local do vídeo na tela de desktop de um usuário ou no dispositivo móvel.

A tabela a seguir descreve o dispositivo, o navegador e o método de reprodução de vídeos em computadores desktop e dispositivos móveis usando o Dynamic Media Video Viewer.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Device</strong></td>
   <td><strong>Navegador</strong></td>
   <td><strong>Modo de reprodução de vídeo</strong></td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Internet Explorer 9 e 10</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Internet Explorer 11+</td>
   <td>No Windows 8 e no Windows 10 - Forçar o uso de HTTPS sempre que HLS for solicitado. Limitação conhecida: HTTP no HLS não funciona nesta combinação de navegador/sistema operacional<br /> <br /> No Windows 7 - Download progressivo. Usa a lógica padrão para selecionar o protocolo HTTP versus HTTPS.</td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Firefox 23-44</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Firefox 45 ou superior</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Cromo</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Área de trabalho</td>
   <td>Safari (Mac)</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Chrome (Android 6 ou anterior)</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Chrome (Android 7 ou posterior)</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Android (navegador padrão)</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Safari (iOS)</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Chrome (iOS)</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
  <tr> 
   <td>Móvel</td>
   <td>Blackberry</td>
   <td>Transmissão de vídeo HLS.</td>
  </tr>
 </tbody>
</table>

## Arquitetura da solução de vídeo Dynamic Media {#architecture-of-dynamic-media-video-solution}

O gráfico a seguir mostra o fluxo de trabalho de criação geral de vídeos que são carregados e codificados por meio do DMGgateway e disponibilizados para consumo público.

![chlimage_1-427](assets/chlimage_1-427.png)

## Arquitetura de publicação híbrida para vídeos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Práticas recomendadas para codificação de vídeos {#best-practices-for-encoding-videos}

O fluxo de trabalho **[!UICONTROL Codificação de vídeo do Dynamic Media]** codifica o vídeo se você tiver ativado a mídia dinâmica e configurado os serviços da nuvem de vídeo. Esse fluxo de trabalho captura o histórico do processo de fluxo de trabalho e as informações de falha. Consulte [Monitorar o progresso da codificação de vídeo e da publicação no YouTube](#monitoring-video-encoding-and-youtube-publishing-progress). Se você ativou o Dynamic Media e configurou os serviços da Video Cloud, a variável **[!UICONTROL Codificar vídeo no Dynamic Media]** O fluxo de trabalho entra em vigor automaticamente ao carregar um vídeo. (Se você não estiver usando o Dynamic Media, a variável **[!UICONTROL Ativo de atualização DAM]** O fluxo de trabalho entra em vigor.)

<!-- DEAD ARTICLE AND VIDEO LINK The following are best-practice tips for encoding source video files.

For advice about video encoding, see the following:

* Article: *Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution:* [www.adobe.com/go/learn_s7_streaming101_en](https://www.adobe.com/go/learn_s7_streaming101_en).
* Video: *Video Encoding Basics:* [www.adobe.com/go/learn_s7_encoding_en](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Arquivos de vídeo de origem primária {#source-video-files}

Ao codificar um arquivo de vídeo, use um arquivo de vídeo de origem com a maior qualidade possível. Evite usar arquivos de vídeo previamente codificados, pois esses arquivos já estão compactados, e uma codificação adicional criará um vídeo de qualidade inferior.

* O Dynamic Media oferece suporte principalmente a vídeos de forma curta com uma duração máxima de 30 minutos.
* Você pode fazer upload de arquivos de vídeo de origem primária com até 15 GB cada.

A tabela a seguir descreve o tamanho recomendado, a proporção e a taxa mínima de bits que seus arquivos de vídeo de origem devem ter antes de codificá-los:

| Tamanho | Taxa de proporção | Taxa mínima de bits |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 4500 kbps para a maioria dos vídeos. |
| 1280 X 720 | 16:9 | 3000 - 6000 kbps, dependendo da quantidade de movimento no vídeo. |
| 1920 X 1080 | 16:99 | 6000 - 8000 kbps, dependendo da quantidade de movimento no vídeo. |

### Obter os metadados de um arquivo {#obtaining-a-file-s-metadata}

Você pode obter os metadados de um arquivo ao exibir os metadados usando uma ferramenta de edição de vídeo ou um aplicativo projetado para obter metadados. A seguir estão as instruções para usar MediaInfo, um aplicativo de terceiros, para obter os metadados de um arquivo de vídeo:

1. Vá para esta página da Web: [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo).
1. Selecione e baixe o instalador da versão da GUI que você está usando e siga as instruções de instalação.
1. Após a instalação, clique com o botão direito do mouse no arquivo de vídeo (somente Windows) e selecione **[!UICONTROL MediaInfo]** ou abrir **[!UICONTROL MediaInfo]** e arraste o arquivo de vídeo para o aplicativo. Você verá todos os metadados associados ao arquivo de vídeo, incluindo largura, altura e fps.

### Taxa de proporção {#aspect-ratio}

Ao escolher ou criar uma predefinição de codificação de vídeo para o arquivo de vídeo principal, verifique se a predefinição tem a mesma proporção do vídeo principal. A proporção é a relação entre a largura e a altura do vídeo.

Para determinar a proporção de um arquivo de vídeo, obtenha os metadados do arquivo e anote a largura e a altura do arquivo (consulte Obter os metadados de um arquivo acima). Em seguida, use essa fórmula para determinar a proporção:

*largura/altura = proporção*

A tabela a seguir descreve como os resultados da fórmula são traduzidos para opções comuns de proporção:

| Resultado da fórmula | Taxa de proporção |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:99 |
| 0,56 | 9:16 |

Por exemplo, um vídeo com 1440 largura x 1080 altura tem uma proporção largura/altura de 1440/1080 ou 1,33. Nesse caso, você escolhe uma predefinição de codificação de vídeo com uma proporção de aspecto 4:3 para codificar o arquivo de vídeo.

### Taxa de bits {#bitrate}

A taxa de bits é a quantidade de dados codificada para formar um único segundo de reprodução de vídeo. A taxa de bits é medida em kilobits por segundo (Kbps).

Como todos os codecs usam compactação com perdas, a taxa de bits é o fator mais importante na qualidade do vídeo. Com a compactação com perdas, quanto mais você compacta um arquivo de vídeo, mais a qualidade é degradada. Por isso, todas as outras características são iguais (resolução, taxa de quadros e codec), quanto menor a taxa de bits, menor a qualidade do arquivo compactado.

Ao selecionar uma codificação de taxa de bits, você pode escolher dois tipos:

* **Codificação constante da taxa de bits** (CBR) - Durante a codificação de CBR, a taxa de bits ou o número de bits por segundo é mantido o mesmo durante todo o processo de codificação. A codificação CBR mantém a taxa de dados definida para sua configuração durante todo o vídeo. Além disso, a codificação CBR não otimiza arquivos de mídia para qualidade, mas salva no espaço de armazenamento.

   Use o CBR se o vídeo contiver um nível de movimento semelhante em todo o vídeo. O CBR é mais usado para transmissão de conteúdo de vídeo. Consulte também [Usar parâmetros de codificação de vídeo personalizados](video-profiles.md#using-custom-added-video-encoding-parameters).

* **Codificação da taxa de bits variável** (VBR) - A codificação VBR ajusta a taxa de dados para baixo e para o limite superior definido, com base nos dados exigidos pelo compressor. Isso significa que, durante um processo de codificação VBR, a taxa de bits do arquivo de mídia aumenta ou diminui dinamicamente, dependendo das necessidades de taxa de bits dos arquivos de mídia.

   O VBR demora mais para codificar, mas produz os resultados mais favoráveis; a qualidade do arquivo de mídia é superior. O VBR é usado mais frequentemente para entrega progressiva de conteúdo de vídeo em http.

**Quando você deve usar o VBR versus o CRB?**
Quando se trata de selecionar VBR versus CBR, é quase sempre recomendável usar VBR para seus arquivos de mídia. O VBR fornece arquivos de maior qualidade a taxas de bits competitivas. Ao usar o VBR, certifique-se de usar com a codificação de duas etapas e definir a taxa de bits máxima para ser 1,5x a taxa de bits do vídeo de destino.

Ao escolher uma predefinição de codificação de vídeo, considere a velocidade de conexão do usuário final de destino. Escolha uma predefinição com uma taxa de dados de 80% dessa velocidade. Por exemplo, se a velocidade de conexão do usuário final de destino for 1000 Kbps, a melhor predefinição é aquela com uma taxa de dados de vídeo de 800 Kbps.

Esta tabela descreve a taxa de dados de velocidades de conexão típicas.

| Velocidade (Kbps) | Tipo de conexão |
|--- |--- |
| 256 | Conexão discada. |
| 800 | Conexão móvel típica. Para essa conexão, direcione uma taxa de dados no intervalo de 400 a um máximo de 800 para experiências 3G. |
| 2000 | Conexão típica de desktop de banda larga. Para esta conexão, direcione uma taxa de dados no intervalo de 800-2000 Kbps, com a maioria dos destinos com média de 1200-1500 Kbps. |
| 5000 | Conexão típica de alta banda larga. A codificação nesse intervalo superior não é recomendada porque a entrega de vídeo nessa velocidade não está disponível para a maioria dos consumidores. |

### Resolução {#resolution}

**Resolução** descreve a altura e a largura de um arquivo de vídeo em pixels. A maioria dos vídeos de origem é armazenada em alta resolução (por exemplo, 1920 x 1080). Para fins de transmissão, o vídeo de origem é compactado em uma resolução menor (640 x 480 ou menor).

A resolução e a taxa de dados são dois fatores totalmente vinculados que determinam a qualidade do vídeo. Para manter a mesma qualidade de vídeo, quanto maior o número de pixels em um arquivo de vídeo (quanto maior a resolução), maior deverá ser a taxa de dados. Por exemplo, considere o número de pixels por quadro em uma resolução de 320 x 240 e um arquivo de vídeo de resolução de 640 x 480:

| Resolução | Pixels por quadro |
|--- |--- |
| 320 x 240 | 76 800 |
| 640 x 480 | 307 200 |

O arquivo de 640 x 480 tem quatro vezes mais pixels por quadro. Para atingir a mesma taxa de dados para essas duas resoluções de exemplo, aplique quatro vezes a compactação no arquivo 640 x 480, o que pode reduzir a qualidade do vídeo. Portanto, uma taxa de dados de vídeo de 250 Kbps produz uma exibição de alta qualidade com uma resolução de 320 x 240, mas não com resolução de 640 x 480.

Em geral, quanto maior for a taxa de dados, melhor será a aparência do vídeo e maior será a resolução usada, maior será a taxa de dados necessária para manter a qualidade de exibição (em comparação com resoluções mais baixas).

Como a resolução e a taxa de dados estão vinculadas, você tem duas opções ao codificar o vídeo:

* Escolha uma taxa de dados e, em seguida, codifique na resolução mais alta que fique boa na taxa de dados escolhida.
* Escolha uma resolução e, em seguida, codifique na taxa de dados necessária para obter vídeo de alta qualidade na resolução escolhida.

Ao escolher (ou criar) uma predefinição de codificação de vídeo para o arquivo de vídeo principal, use esta tabela para direcionar a resolução correta:

| Resolução | Altura (pixels) | Tamanho da tela |
|--- |--- |--- |
| 240p | 240 | Tela pequena |
| 300p | 300 | Tela pequena normalmente para dispositivos móveis |
| 360p | 360 | Tela pequena |
| 480p | 480 | Tela média |
| 720p | 720 | Tela grande |
| 1080p | 1080 | Tela grande de alta definição |

### Fps (Quadros por segundo) {#fps-frames-per-second}

Nos Estados Unidos e Japão, a maioria dos vídeos é capturada a 29,97 quadros por segundo (fps); na Europa, a maioria dos vídeos é filmada a 25 fps. O filme é filmado a 24 fps.

Escolha uma predefinição de codificação de vídeo que corresponda à taxa fps do arquivo de vídeo principal. Por exemplo, se o vídeo principal tiver 25 fps, escolha uma predefinição de codificação com 25 fps. Por padrão, toda codificação personalizada usa o fps do arquivo de vídeo principal. Por isso, não é necessário especificar explicitamente a configuração fps ao criar uma predefinição de codificação de vídeo.

### Dimensões de codificação de vídeo {#video-encoding-dimensions}

Para obter resultados ideais, selecione dimensões de codificação de modo que o vídeo de origem seja um múltiplo completo de todos os vídeos codificados.

Para calcular essa proporção, você divide a largura da origem por largura codificada para obter a relação de largura. Em seguida, divida a altura da origem por altura codificada para obter a proporção de altura.

Se a proporção resultante for um inteiro, significa que o vídeo é dimensionado de maneira ideal. Se a proporção resultante não for um inteiro, ela afetará a qualidade do vídeo, deixando artefatos de pixel à esquerda na exibição. Esse efeito é mais notável quando o vídeo tem texto.

Por exemplo, suponha que o vídeo de origem seja 1920 x 1080. Na tabela a seguir, os três vídeos codificados fornecem as configurações de codificação ideais para usar.

<table> 
 <tbody> 
  <tr> 
   <th><p>Tipo de vídeo</p> </th> 
   <th><p>Largura x altura</p> </th> 
   <th><p>Proporção de largura</p> </th> 
   <th><p>Taxa de altura</p> </th> 
  </tr>
  <tr> 
   <td><p>Origem</p> </td> 
   <td><p>1920x1080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>3</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificado</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### Formato de arquivo de vídeo codificado {#encoded-video-file-format}

A Dynamic Media recomenda usar predefinições de codificação de vídeo MP4 H.264. Como os arquivos MP4 usam o codec de vídeo H.264, ele fornece vídeo de alta qualidade, mas em um tamanho de arquivo compactado.

## Publicar vídeos no YouTube {#publishing-videos-to-youtube}

Você pode publicar ativos de vídeo no local AEM diretamente em um canal do YouTube criado anteriormente.

Para publicar ativos de vídeo no YouTube, configure o AEM Assets com tags. Você associa essas tags a um canal YouTube. Se a tag de um ativo de vídeo corresponder à tag de um canal de YouTube, o vídeo será publicado no YouTube. Se o ativo de vídeo não tiver uma tag , ele não será publicado no YouTube.

A publicação no YouTube ignora o sistema de perfil de processamento no AEM e, portanto, também o perfil de codificação de vídeo. Esse desvio ocorre porque o YouTube tem sua própria codificação, portanto, um perfil de processamento de vídeo não é necessário. Na maioria dos casos, no entanto, espera-se que você já tenha feito seus ativos de vídeo passarem por um perfil de processamento de vídeo. Ao ignorar o perfil de processamento de vídeo e publicar diretamente no YouTube, isso significa apenas que o ativo de vídeo no AEM Asset não obtém uma miniatura visualizável. Isso também significa que, se você executar no modo de execução do dynamicmedia, os vídeos que não estiverem codificados não funcionarão com nenhum dos tipos de ativos do Dynamic Media.

A publicação de ativos de vídeo em servidores da YouTube envolve a conclusão das seguintes tarefas para garantir a autenticação segura de servidor para servidor com o YouTube:

1. [Definir as configurações da Google Cloud](#configuring-google-cloud-settings)
1. [Criar um canal YouTube](#creating-a-youtube-channel)
1. [Adicionar tags para publicação](#adding-tags-for-publishing)
1. [Ativar o agente YouTube Publish Replication](#enabling-the-youtube-publish-replication-agent)
1. [Configurar o YouTube no AEM](#setting-up-youtube-in-aem)
1. [(Opcional) Automatize a configuração das propriedades padrão do YouTube para seus vídeos carregados](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publicar vídeos no seu canal do YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Opcional) Verificar o vídeo publicado no YouTube](video.md#optional-verifying-the-published-video-on-youtube)
1. [Vincular URLs do YouTube à sua aplicação web](#linking-youtube-urls-to-your-web-application)

Você também pode [cancelar a publicação de vídeos para removê-los do YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Definir as configurações da Google Cloud {#configuring-google-cloud-settings}

Para publicar no YouTube, você precisa de uma conta do Google. Se você tiver uma conta GMAIL, já terá uma conta Google. Caso não tenha uma conta Google, crie uma facilmente. Você precisa da conta, pois precisa de credenciais para publicar ativos de vídeo no YouTube. Se você já tiver uma conta criada, ignore esta tarefa e prossiga para [Criação de um canal YouTube](#creating-a-youtube-channel).

>[!NOTE]
>
>As etapas a seguir foram precisas no momento da escrita. No entanto, o Google atualiza periodicamente seus sites sem aviso prévio. Como tal, essas etapas podem ser um pouco diferentes.

**Para definir as configurações da Google Cloud:**

1. Crie uma nova conta do Google.

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Se você já tiver uma conta do Google, pule para a próxima etapa.

1. Ir para [https://cloud.google.com/](https://cloud.google.com/).
1. Na página da Google Cloud Platform, próximo à parte superior, toque em **[!UICONTROL Console]**. Pode precisar de **Fazer logon** usando suas credenciais de conta do Google.
1. No **[!UICONTROL Painel]** página, toque em **[!UICONTROL Criar projeto]**.
1. No **[!UICONTROL Novo projeto]** , digite um nome de projeto.

   Observe que a ID do projeto se baseia no nome do projeto. Como tal, escolha cuidadosamente o nome do projeto; ele não pode ser alterado após ser criado. Além disso, será necessário inserir a mesma ID de projeto novamente ao configurar o YouTube no Adobe Experience Manager posteriormente. Talvez você queira anotar a ID do projeto.
1. Toque **[!UICONTROL Criar]**.

1. No **[!UICONTROL Painel]** no **[!UICONTROL Introdução]** cartão, toque em **[!UICONTROL Ativar APIs e obter credenciais como chaves]**.
1. Próximo ao topo da **[!UICONTROL Painel]** página, toque em **[!UICONTROL Habilitar API]**.
1. No **[!UICONTROL Biblioteca]** em APIs do YouTube, toque em **[!UICONTROL API de dados do YouTube]**.
1. Próximo ao topo da **[!UICONTROL API de dados do YouTube v3]** página, toque em **[!UICONTROL Habilitar]** para ligar.
1. Para usar a API, talvez você precise de credenciais. Se necessário, toque em **[!UICONTROL Criar credenciais]**.
1. No **[!UICONTROL De onde você chamará a API?]** , selecione **[!UICONTROL Servidor da Web (por exemplo, node.js, Tomcat)]**.
1. Em **[!UICONTROL Que dados você acessará?]** select **[!UICONTROL Dados do usuário]**.
1. Toque **[!UICONTROL Quais credenciais são necessárias?]**.
1. Em **[!UICONTROL Criar uma ID de cliente OAuth 2.0]** digite um nome exclusivo.
1. No campo de texto sob a variável **[!UICONTROL Origens Javascript autorizadas]** , insira o seguinte caminho, substituindo seu próprio domínio e número da porta no caminho e pressione **[!UICONTROL Enter]** para adicionar o caminho à lista:

   `https://<servername.domain>:<port_number>`

   Por exemplo, `https://1a2b3c.mycompany.com:4321`

   **Observação**: O exemplo de caminho acima destina-se apenas a fins ilustrativos.

1. No campo de texto sob a variável **[!UICONTROL URIs de redirecionamento autorizados]** , digite o seguinte, substituindo seu próprio domínio e número da porta no caminho, e pressione Enter para adicionar o caminho à lista:

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Por exemplo, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Observação**: O exemplo de caminho acima destina-se apenas a fins ilustrativos.

1. Toque **[!UICONTROL Criar ID de cliente]**.
1. Na página Credenciais , no **[!UICONTROL Configurar a tela de consentimento do OAuth 2.0]** selecione o endereço do Gmail que você está usando no momento.
1. No campo de texto sob a variável **[!UICONTROL Nome do produto exibido aos usuários]** , insira o que deseja mostrar na tela de consentimento.

   A tela de consentimento é exibida para o administrador do AEM quando eles são autenticados para o YouTube; AEM entrará em contato com a YouTube para obter permissão.

1. Toque **[!UICONTROL Continuar]**.
1. Em **[!UICONTROL Baixar credenciais]** cabeçalho, toque **[!UICONTROL Baixar]**.
1. Salve as `client_id.json` arquivo.

   Você precisará desse arquivo json baixado ao configurar o YouTube no Adobe Experience Manager posteriormente.

1. Toque **[!UICONTROL Concluído]**.

   Agora você criará um canal YouTube.

### Criação de um canal YouTube {#creating-a-youtube-channel}

A publicação de vídeos no YouTube requer um ou mais canais. Caso já tenha criado um canal YouTube, ignore esta tarefa e vá para **Adição de tags para publicação**.

>[!CAUTION]
>
>Certifique-se de que você já configurou um ou mais canais no YouTube &amp;ast;before&amp;ast; você adiciona canais em Configurações do YouTube em AEM (consulte [Configuração do YouTube no AEM](#setting-up-youtube-in-aem) abaixo). Se você não conseguir fazer isso, não receberá nenhum aviso de nenhum canal existente. No entanto, a autenticação da Google ainda ocorre ao adicionar um canal, mas não há uma opção para escolher qual canal o vídeo será enviado.

**Para criar um canal YouTube:**

1. Ir para [https://www.youtube.com](https://www.youtube.com/) e faça logon usando suas credenciais de conta do Google.
1. No canto superior direito da página do YouTube, toque na imagem do perfil (também pode aparecer como uma letra dentro de um círculo colorido sólido) e toque em **[!UICONTROL Configurações do YouTube]** (ícone de engrenagem arredondada).
1. No **[!UICONTROL Visão geral]** na página **[!UICONTROL Recursos adicionais]** cabeçalho, toque **[!UICONTROL Ver todos os meus canais ou criar um novo canal]**.
1. No **[!UICONTROL Canais]** página, toque em **[!UICONTROL Criar um novo canal]**.
1. No **[!UICONTROL Conta de marca]** na página **[!UICONTROL Nome da conta da marca]** , insira um nome de negócios ou qualquer outro nome de canal que você escolher onde deseja publicar seus ativos de vídeo e toque em **[!UICONTROL Criar]**.

   Lembre-se do nome inserido aqui, pois será necessário inseri-lo novamente ao configurar o YouTube no AEM.

1. (Opcional) Se necessário, adicione mais canais.

   Agora, você adicionará tags para publicação.

### Adicionar tags para publicação {#adding-tags-for-publishing}

Para publicar seus vídeos no YouTube, AEM associa as tags a um ou mais canais do YouTube. Para adicionar tags para publicação, consulte [Administração de tags](/help/sites-administering/tags.md).

Ou, se você pretende usar as tags padrão no AEM, ignore esta tarefa e vá para [Ativação do agente de replicação YouTube Publish](#enabling-the-youtube-publish-replication-agent).

### Ativar o agente de replicação do YouTube Publish {#enabling-the-youtube-publish-replication-agent}

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Implantação > Replicação > Agentes no Autor]**.
1. No **[!UICONTROL Agentes de Autor]** página, toque em **[!UICONTROL Publicação do YouTube (YouTube)]**.
1. Na barra de ferramentas, à direita de Configurações, toque em **[!UICONTROL Editar]**.
1. Selecione o **[!UICONTROL Ativado]** caixa de seleção para ativar o agente de replicação.
1. toque **[!UICONTROL OK]**.

   Agora, você configurará o YouTube no AEM.

### Configurar o YouTube no AEM {#setting-up-youtube-in-aem}

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Implantação > Cloud Services]**.
1. Em **[!UICONTROL Serviços de terceiros]** cabeçalho, em YouTube, toque em **[!UICONTROL Configurar agora]**.
1. No **[!UICONTROL Criar configuração]** , digite um título (obrigatório) e um nome (opcional) nos respectivos campos.
1. Toque **[!UICONTROL Criar]**.
1. No **[!UICONTROL Configurações da conta do YouTube]** na caixa de diálogo , na **[!UICONTROL Nome do aplicativo]** digite a ID do projeto do Google.

   Você especificou a ID do projeto quando definiu as configurações da Google Cloud anteriormente.

   Deixe o **[!UICONTROL Configuração da conta YouTube]** caixa de diálogo aberta; você retornará a ele em um momento.

1. Usando um editor de texto simples, abra o arquivo JSON que você baixou e salvou anteriormente na tarefa Configuração das configurações da Google Cloud.
1. Selecione e copie o texto JSON inteiro.
1. Retorne ao **[!UICONTROL Configurações da conta do YouTube]** caixa de diálogo. No campo **[!UICONTROL Configuração JSON]**, cole o texto JSON.
1. Toque **[!UICONTROL OK]**.

   Agora, você configurará os canais YouTube no AEM.

1. À direita de **[!UICONTROL Canais disponíveis]**, toque em **[!UICONTROL +]** (ícone de adição).
1. No **[!UICONTROL Configurações do canal YouTube]** na caixa de diálogo , na **[!UICONTROL Título]** , digite o nome do canal criado na tarefa **C[!UICONTROL Criação de um canal YouTube]** anteriormente.

   Opcionalmente, é possível adicionar uma descrição, se desejar.

1. Toque **[!UICONTROL OK]**.
1. Autenticação YouTube/Google é exibida. Se você ainda não estiver conectado à conta da Google Cloud, ignore esta etapa.

   * Insira o nome de usuário e a senha do Google associados à ID do projeto do Google e o texto JSON acima.
   * Dependendo de quantos canais sua conta tem para ver dois ou mais itens. Selecione um canal. Não selecione o endereço de email.
   * Na próxima página, toque em **[!UICONTROL Aceitar]** para permitir o acesso a este canal.

1. Toque **[!UICONTROL Permitir]**.

   Agora você irá configurar tags para publicação.

1. **Configuração de tags para publicação** - No **[!UICONTROL Cloud Services > YouTube]** toque na página **[!UICONTROL Lápis]** para editar a lista de tags que deseja usar.
1. Toque no ícone da lista suspensa (sinal de interpolação) para exibir a lista de tags disponíveis no AEM.
1. Toque em uma ou mais tags para adicioná-las.

   Para excluir uma tag adicionada, selecione a tag e toque em **[!UICONTROL X]**.

1. Quando terminar de adicionar as tags desejadas, toque em **[!UICONTROL OK]**.

   Agora você publica vídeos no seu canal do YouTube.

### (Opcional) Automatize a configuração das propriedades padrão do YouTube para seus vídeos carregados {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Você pode automatizar a configuração das propriedades do YouTube ao fazer upload dos vídeos. Para isso, crie um perfil de processamento de metadados no AEM.

Para criar o perfil de processamento de metadados, você primeiro copiará valores dos campos **[!UICONTROL Rótulo do campo]**, **[!UICONTROL Mapear para a propriedade]** e **[!UICONTROL Opções]**, todos encontrados nos Esquemas de metadados do vídeo. Em seguida, você criará seu perfil de processamento de metadados de vídeo do YouTube, adicionando esses valores a ele.

**Como opção, para automatizar a configuração das propriedades padrão do YouTube para os vídeos carregados:**

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Esquemas de metadados]**.
1. Toque **[!UICONTROL default]**. (Não adicione uma marca de seleção à caixa de seleção à esquerda de &quot;padrão&quot;.)
1. No **[!UICONTROL default]** marque a caixa à esquerda de **[!UICONTROL vídeo]** e toque em **[!UICONTROL Editar]**.
1. No **[!UICONTROL Editor de esquema de metadados]** toque na página **[!UICONTROL Avançado]** guia .
1. No cabeçalho Publicação no YouTube, toque em **[!UICONTROL Categoria do YouTube]**. (Não toque na lista suspensa Categoria do YouTube .)
1. No lado direito da página, em **[!UICONTROL Configurações]** , faça o seguinte:

   * No **[!UICONTROL Rótulo do campo]** , selecione e copie o valor.

      Cole o valor copiado em um editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

   * No **[!UICONTROL Mapear para propriedade]** , selecione e copie o valor.

      Cole o valor copiado no editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

   * Em **[!UICONTROL Opções]**, selecione e copie o valor padrão que deseja usar (como People &amp; Blogs ou Science &amp; Technology).

      Cole o valor copiado no editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

1. No cabeçalho Publicação no YouTube, toque em **[!UICONTROL Privacidade da YouTube]**. (Não toque na lista suspensa Privacidade da YouTube .)
1. No lado direito da página, em **[!UICONTROL Configurações]** , faça o seguinte:

   * No **[!UICONTROL Rótulo do campo]** , selecione e copie o valor.

      Cole o valor copiado em um editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

   * No **[!UICONTROL Mapear para propriedade]** , selecione e copie o valor.

      Cole o valor copiado no editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

   * Em **[!UICONTROL Opções]**, selecione e copie o valor padrão que deseja usar. Observe que as Opções são agrupadas em pares de dois. O campo inferior do par é o valor padrão que você deseja copiar, como público, não listado ou privado.

      Cole o valor copiado no editor de texto aberto. Você precisará desse valor posteriormente ao criar seu perfil de processamento de metadados. Deixe o editor de texto aberto.

1. Próximo ao canto superior direito do **[!UICONTROL Editor de esquema de metadados]** página, toque em **[!UICONTROL Cancelar]**.
1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Perfis de metadados]**.

1. No **[!UICONTROL Perfis de metadados]** , próximo ao canto superior direito da página, toque em **[!UICONTROL Criar]**. No **[!UICONTROL Adicionar perfil de metadados]** na caixa de diálogo , na **[!UICONTROL Título do perfil]** campo de texto, insira o nome `YouTube Video`.
1. No **[!UICONTROL Editor de perfil de metadados]** toque na página **[!UICONTROL Avanço]** guia .
1. Adicione os valores copiados de Publicação no YouTube ao perfil, fazendo o seguinte:

   * No lado direito da página, toque no **[!UICONTROL Criar formulário]** guia .
   * Arraste o componente rotulado **[!UICONTROL Cabeçalho da seção]** à esquerda e solte-a na área do formulário.
   * Toque **[!UICONTROL Rótulo do campo]** para selecionar o componente.
   * No lado direito da página, em **[!UICONTROL Configurações]** na guia , no **[!UICONTROL Rótulo do campo]** campo de texto, digite `YouTube Publishing`.
   * Toque no **[!UICONTROL Criar formulário]** e arraste o componente rotulado **[!UICONTROL Texto de linha única]** e solte-o abaixo do **[!UICONTROL Publicação no YouTube]** cabeçalho que você acabou de criar.
   * Toque **[!UICONTROL Rótulo do campo]** para selecionar o componente.
   * No lado direito da página, em **[!UICONTROL Configurações]** cole a guia **[!UICONTROL Publicação no YouTube]** valores (**[!UICONTROL Rótulo do campo]** e **[!UICONTROL Mapear para propriedade]** que você copiou anteriormente, em seus respectivos campos no formulário. Cole o **[!UICONTROL Opções]** na variável **[!UICONTROL Valor padrão]** campo.

1. Adicione os valores copiados da Privacidade do YouTube ao perfil, fazendo o seguinte:

   * No lado direito da página, toque no **[!UICONTROL Criar formulário]** guia .
   * Arraste o componente rotulado **[!UICONTROL Cabeçalho da seção]** à esquerda e solte-a na área do formulário.
   * Toque **[!UICONTROL Rótulo do campo]** para selecionar o componente.
   * No lado direito da página, na guia Configurações , no campo de texto Rótulo do campo , digite `YouTube Privacy`.
   * Toque no **[!UICONTROL Criar formulário]** e arraste o componente rotulado **[!UICONTROL Texto de linha única]** e solte-o abaixo do **[!UICONTROL Privacidade da YouTube]** Você acabou de criar.
   * Toque **[!UICONTROL Rótulo do campo]** para selecionar o componente.
   * No lado direito da página, em **[!UICONTROL Configurações]** cole a guia **[!UICONTROL Publicação no YouTube]** valores (**[!UICONTROL Rótulo do campo]** e **[!UICONTROL Mapear para propriedade]** que você copiou anteriormente, em seus respectivos campos no formulário. Cole o **[!UICONTROL Opções]** na variável **[!UICONTROL Valor padrão]** campo.

1. Próximo ao canto superior direito da página, toque em **[!UICONTROL Salvar]**.
1. Aplique o perfil de metadados de Publicação do YouTube às pastas onde você fará upload de vídeos. Você precisará ter o Perfil de metadados e o Perfil de vídeo definidos.

   Consulte [Perfis de metadados](metadata-profiles.md) e [Perfis de vídeo](video-profiles.md).

### Publicar vídeos no seu canal do YouTube {#publishing-videos-to-your-youtube-channel}

Agora, associe as tags adicionadas anteriormente aos ativos de vídeo. Esse processo permite AEM saber quais ativos serão publicados no canal do YouTube.

Para publicar conteúdo do YouTube, o AEM usa o **[!UICONTROL Publicar no YouTube]** , que permite monitorar o progresso e exibir as informações de falha.
Consulte [Monitorar o progresso da codificação de vídeo e da publicação no YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Para publicar vídeos no seu canal do YouTube:**

1. Em AEM, navegue até um ativo de vídeo que deseja publicar no canal do YouTube.
1. Selecione o ativo de vídeo.

   Independentemente do ativo de vídeo selecionado (como o vídeo de origem original ou uma representação codificada), o vídeo de origem original sempre é carregado.

1. Na barra de ferramentas, toque em **[!UICONTROL Propriedades]**.
1. No **[!UICONTROL Básico]** guia , no cabeçalho Metadados , toque em **[!UICONTROL Procurar]** à direita do **[!UICONTROL Tags]** campo.
1. No **[!UICONTROL Selecionar Tags]** , navegue até as tags que deseja usar e selecione uma ou mais tags.
1. No canto superior direito da página, toque no **[!UICONTROL Confirmar]** ícone .
1. No canto superior direito da página de propriedades do vídeo, toque em **[!UICONTROL Salvar]**.
1. Na barra de ferramentas, toque em **[!UICONTROL Publicar > Publicar]**.

   Opcionalmente, é possível verificar o vídeo publicado no canal do YouTube.

### (Opcional) Verificar o vídeo publicado no YouTube {#optional-verifying-the-published-video-on-youtube}

Você pode monitorar o progresso da publicação do YouTube (ou desfazer a publicação).

Consulte [Monitorar o progresso da codificação de vídeo e da publicação no YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Os tempos de publicação podem variar bastante, dependendo de vários fatores que incluem o formato do vídeo principal, o tamanho do arquivo e o tráfego de upload. O processo de publicação pode levar de alguns minutos a várias horas. Além disso, esteja ciente de que os formatos de resolução mais alta são renderizados muito mais lentamente. Por exemplo, 720p e 1080p levam significativamente mais tempo para aparecer do que 480p.

Após oito horas, se você ainda vir uma mensagem de status que diz **[!UICONTROL Carregado (processando, aguarde)]**, tente remover o vídeo do site e carregá-lo novamente.

### Vincular URLs do YouTube à sua aplicação web {#linking-youtube-urls-to-your-web-application}

Você pode obter uma string de URL do YouTube gerada pelo Dynamic Media após publicar o vídeo. Ao copiar o URL do YouTube, ele chega à Área de transferência para que você possa colá-lo conforme necessário nas páginas do seu site ou aplicativo.

O URL do YouTube não está disponível para cópia até que você tenha publicado o ativo de vídeo no YouTube.

**Para vincular URLs do YouTube ao seu aplicativo da Web:**

1. Navegue até a YouTube *publicado* ativo de vídeo cujo URL você deseja copiar e, em seguida, selecione-o.

   Lembre-se de que os URLs do YouTube só estão disponíveis para cópia *after* você tem primeiro *publicado* os ativos de vídeo para a YouTube.

1. Na barra de ferramentas, toque em **[!UICONTROL Propriedades]**.
1. Toque no **[!UICONTROL Avançado]** guia .
1. Em **[!UICONTROL Publicação no YouTube]** no cabeçalho **[!UICONTROL URL do YouTube]** Liste, selecione e copie o texto do URL para seu navegador da Web para visualizar o ativo ou adicionar a sua página de conteúdo da Web.

### Cancelar a publicação de vídeos para removê-los do YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Ao cancelar a publicação de um ativo de vídeo no AEM, o vídeo é removido do YouTube.

>[!CAUTION]
>
>Se você remover um vídeo diretamente do YouTube, o AEM não estará ciente e continuará a se comportar como se o vídeo ainda estivesse publicado no YouTube. Sempre cancele a publicação de um ativo de vídeo do YouTube por meio de AEM.

Para remover o conteúdo do YouTube, o AEM usa a variável **[!UICONTROL Cancelar publicação do YouTube]** , que permite monitorar o progresso e exibir as informações de falha.
Consulte [Monitorar o progresso da codificação de vídeo e da publicação no YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Para cancelar a publicação de vídeos para removê-los do YouTube:**

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]**.
1. Navegue até os ativos de vídeo que você deseja cancelar a publicação por meio do canal do YouTube.
1. Em um modo de seleção de ativo, selecione um ou mais ativos de vídeo publicados.
1. Na barra de ferramentas, toque em **[!UICONTROL Cancelar publicação]** > **[!UICONTROL Cancelar publicação]**.

## Monitorar o progresso da codificação de vídeo e da publicação no YouTube {#monitoring-video-encoding-and-youtube-publishing-progress}

Ao fazer o upload de um novo vídeo para uma pasta com codificação de vídeo aplicada ou ao publicar seu vídeo no youtube, você pode monitorar de várias maneiras como sua codificação de vídeo/publicação do youtube está progredindo (ou falhando). O progresso real da publicação do YouTube só está disponível por meio dos logs, mas se ele falhar ou ser bem-sucedido é listado de formas adicionais descritas no procedimento a seguir. Além disso, você pode receber notificações por email quando um fluxo de trabalho de publicação do YouTube ou uma codificação de vídeo for concluída ou abortada.

### Monitorar progresso {#monitoring-progress}

Para monitorar o progresso (incluindo codificação com falha/publicação do YouTube):

1. Exibir o progresso da codificação de vídeo na pasta de ativos:

   * Em **[!UICONTROL Exibição de cartão]**, o progresso da codificação de vídeo é exibido no ativo por porcentagem. Se houver um erro, essas informações também serão exibidas no ativo.

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * Em **[!UICONTROL Exibição de lista]**, o progresso da codificação do vídeo é exibido na **[!UICONTROL Status do processamento]** coluna. Se houver um erro, essa mensagem será exibida nessa mesma coluna.

      ![chlimage_1-430](assets/chlimage_1-430.png)

      Essa coluna não é exibida por padrão. Para ativar a coluna, selecione **[!UICONTROL Exibir configurações]** do **[!UICONTROL Exibições]** e adicione o **[!UICONTROL Status do processamento]** coluna e toque **[!UICONTROL Atualizar]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. Exibir o progresso nos detalhes do ativo. Ao tocar em um ativo, abra o menu suspenso e selecione **[!UICONTROL Linha do tempo]**. Para restringi-lo a atividades de fluxo de trabalho, como codificação ou publicação no YouTube, selecione **[!UICONTROL Fluxos de trabalho]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Qualquer informação do fluxo de trabalho, como codificação, é exibida na linha do tempo. Para publicação no YouTube, a variável **[!UICONTROL Fluxo de trabalho]** linha do tempo também inclui o nome do canal do YouTube e o URL do vídeo do YouTube. Além disso, você vê notificações de falha no **[!UICONTROL Fluxo de trabalho]** linha do tempo.

   >[!NOTE]
   >
   >Pode levar muito tempo para que as mensagens de erro/falha sejam gravadas devido a várias configurações de fluxo de trabalho em **[!UICONTROL tentativas]**, **[!UICONTROL atraso de nova tentativa]** e **[!UICONTROL timeout]** from [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), por exemplo:
   >
   >* Configuração da fila de trabalhos do Apache Sling
   >* Manipulador de Trabalho do Processo Externo do Fluxo de Trabalho do Adobe Granite
   >* Fila de tempo limite do fluxo de trabalho do Granite

   > 
   >Você pode ajustar as **[!UICONTROL tentativas]**, o **[!UICONTROL atraso de repetição]** e as propriedades de **[!UICONTROL tempo limite]** nessas configurações.

1. Para fluxos de trabalho em andamento, consulte **Instâncias de fluxo de trabalho** disponível em **[!UICONTROL Ferramentas > Fluxo de trabalho > Instâncias]**.

   >[!NOTE]
   >
   >Você pode precisar de direitos administrativos para acessar o **[!UICONTROL Ferramentas]** menu.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Selecione a instância e toque em **[!UICONTROL Abrir Histórico]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   No **[!UICONTROL Instâncias de fluxo de trabalho]** , você também pode suspender, encerrar ou renomear workflows. Consulte [Administração de fluxos de trabalho](/help/sites-administering/workflows-administering.md) para obter mais informações.

1. Para tarefas com falha, consulte **Falhas de fluxo de trabalho** disponível em **[!UICONTROL Ferramentas > Fluxo de trabalho > Falhas]**. A **[!UICONTROL Falha do fluxo de trabalho]** lista todas as atividades do fluxo de trabalho com falha.

   >[!NOTE]
   >
   >Você pode precisar de direitos administrativos para acessar o **[!UICONTROL Ferramentas]** menu.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Pode levar muito tempo para que a mensagem de erro seja gravada devido a várias configurações de workflow em **[!UICONTROL tentativas]**, **[!UICONTROL atraso de nova tentativa]** e **[!UICONTROL timeout]** from [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr), por exemplo:
   >
   >* Configuração da fila de trabalhos do Apache Sling
   >* Manipulador de Trabalho do Processo Externo do Fluxo de Trabalho do Adobe Granite
   >* Fila de tempo limite do fluxo de trabalho do Granite

   >
   >Você pode ajustar as **[!UICONTROL tentativas]**, o **[!UICONTROL atraso de repetição]** e as propriedades de **[!UICONTROL tempo limite]** nessas configurações.

1. Para fluxos de trabalho concluídos, consulte **[!UICONTROL Arquivo de fluxo de trabalho]** disponível em **[!UICONTROL Ferramentas > Fluxo de trabalho > Arquivar]**. O **[!UICONTROL Arquivo de fluxo de trabalho]** lista todas as atividades de fluxo de trabalho concluídas.

   Você pode precisar de direitos administrativos para acessar o **[!UICONTROL Ferramentas]** menu.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. Você pode receber notificações por email sobre trabalhos de fluxo de trabalho abortados ou com falha. Essas notificações por email podem ser configuradas por um administrador.
Consulte [Configuração de notificações por email](#configuring-e-mail-notifications).

#### Configurar notificações por email {#configuring-e-mail-notifications}

Você pode precisar de direitos administrativos para acessar o **[!UICONTROL Ferramentas]** menu.

A forma como você configura a notificação depende se você deseja notificações para codificar trabalhos ou trabalhos de publicação do YouTube:

* Para tarefas de codificação, você pode acessar a página de configuração de todas as notificações por email AEM fluxo de trabalho em **[!UICONTROL Ferramentas > Operações > Console da Web]** e procurando por **[!UICONTROL Serviço de Notificação por Email do Workflow CQ Dia]**. Consulte [Configuração da notificação por email no AEM](/help/sites-administering/notification.md). Você pode marcar ou desmarcar as caixas de seleção para **[!UICONTROL Notificar sobre Abortar]** ou **[!UICONTROL Notificar quando Concluído]** em conformidade.

* Para trabalhos de publicação do YouTube, faça o seguinte:

1. Em AEM, selecione **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.
1. Selecione o **[!UICONTROL Publicar no YouTube]** , em seguida, toque em **[!UICONTROL Editar]**.
1. Clique com o botão direito do mouse no **[!UICONTROL Upload do YouTube]** etapa do fluxo de trabalho e toque em **[!UICONTROL Editar]**.
1. Toque no **[!UICONTROL Argumento]s** guia .
1. Você pode marcar ou desmarcar as seguintes caixas de seleção:

   * **[!UICONTROL Início da publicação]**
   * **[!UICONTROL Falha na publicação]**
   * **[!UICONTROL Publicar conclusão]**, que inclui informações sobre canais e URLs

   Limpar uma caixa de seleção significa que você não receberá a notificação por email especificada do fluxo de trabalho de Publicação do YouTube .

   >[!NOTE]
   >
   >Esses emails são específicos do YouTube e, além das notificações por email de workflow genéricas. Como resultado, você pode receber dois conjuntos de notificações por email - a notificação genérica disponível no **Serviço de Notificação por Email do Workflow CQ Dia** e uma específica para o YouTube, dependendo das configurações.

## Exibir relatórios de vídeo {#viewing-video-reports}

Os relatórios de vídeo estão disponíveis ao executar o Dynamic Media - Modo híbrido; os relatórios não estão disponíveis quando você executa o modo Dynamic Media - Scene7.

Os Relatórios de vídeo exibem várias métricas agregadas em um período especificado para ajudar você a monitorar o desempenho *publicado *individual e de vídeos agregados conforme o esperado. Os seguintes dados de métricas principais são agregados para todos os vídeos publicados em todo o seu site:

* Vídeos iniciados
* Taxa de Conclusão
* Tempo médio no vídeo
* Tempo total no vídeo
* Vídeos por visita

Uma tabela de todos *publicado* os vídeos também são listados para que você possa acompanhar os vídeos mais vistos em seu site com base no total de inícios de vídeo.

Ao tocar no nome de um vídeo na lista, ele mostra o relatório de retenção de público-alvo (lista suspensa) do vídeo, na forma de um gráfico de linha. O gráfico exibe o número de visualizações em qualquer momento durante a reprodução do vídeo. Quando você reproduz o vídeo, a barra vertical é rastreada em sincronização com o indicador de hora no reprodutor. Quedas nos dados do gráfico de linha indicam onde o público-alvo sai do desinteresse.

Se o vídeo foi codificado fora do Adobe Experience Manager Dynamic Media, o gráfico de retenção de público-alvo (lista suspensa) e os dados de Porcentagem de reprodução na tabela não estarão disponíveis.

Consulte também [Configuração do Dynamic Media Cloud Services](/help/assets/config-dynamic.md).

>[!NOTE]
>
>Os dados de rastreamento e relatórios se baseiam exclusivamente no uso do próprio reprodutor de vídeo do Dynamic Media e da predefinição associada do reprodutor de vídeo. Dessa forma, não é possível rastrear e gerar relatórios sobre os vídeos reproduzidos por meio de outros players de vídeo.

Por padrão, na primeira vez que você insere Relatórios de vídeo, o relatório exibe dados de vídeo que começam no primeiro dia do mês atual e terminam com a data do mês atual. No entanto, você pode substituir o intervalo de datas padrão especificando seu próprio intervalo de datas. Na próxima vez que você inserir os Relatórios de vídeo, será usado o intervalo de datas especificado.

Para que os relatórios de vídeo funcionem corretamente, uma ID de conjunto de relatórios é criada automaticamente quando o Dynamic Media Cloud Services é configurado. Ao mesmo tempo, a ID do conjunto de relatórios é enviada para o servidor de publicação, para que fique disponível para o recurso Copiar URL ao visualizar ativos. No entanto, isso requer que o servidor de publicação já esteja configurado. Se o servidor de Publicação não estiver configurado, você ainda poderá publicar para ver o relatório de vídeo. No entanto, será necessário retornar à Configuração da Dynamic Media Cloud e tocar em **OK**.

**Para exibir relatórios de vídeo:**

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]** > **[!UICONTROL Relatórios de vídeo]**.
1. Na página Relatórios de vídeo , execute um dos seguintes procedimentos:

   * Próximo ao canto superior direito, toque no **[!UICONTROL Atualizar relatório de vídeo]** ícone .

      Você só precisará usar Atualizar se a data final do relatório for o dia atual. Isso garante que você visualize o rastreamento de vídeo que ocorreu desde a última vez em que você executou o relatório.

   * Próximo ao canto superior direito, toque no **[!UICONTROL Seletor de data]** ícone .

      Especifique o intervalo de datas de início e término para o qual deseja obter os dados de vídeo e toque em **[!UICONTROL Executar relatório]**.
   O **[!UICONTROL Principais métricas]** caixa de grupo identifica várias medidas agregadas para todas *publicado* vídeos em seu site.

1. Na tabela que lista os vídeos publicados principais, toque no nome de um vídeo para reproduzir o vídeo e também veja o relatório de retenção de público-alvo (drop-off) do vídeo.

### Exibir relatórios de vídeo com base em um visualizador de vídeo criado por meio do SDK do visualizador do Dynamic Media HTML5 {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Se você estiver usando um visualizador de vídeo pronto para uso fornecido pelo Dynamic Media ou se tiver criado uma predefinição de visualizador personalizada com base em um visualizador de vídeo pronto para uso, nenhuma etapa adicional será necessária para exibir relatórios de vídeo. No entanto, se você criou seu próprio visualizador de vídeo com base na API do SDK do visualizador do HTML5, use as seguintes etapas para garantir que o visualizador de vídeo esteja enviando eventos de rastreamento para os Relatórios de vídeo do Dynamic Media.

Use o [Guia de referência de visualizadores do Adobe Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html) e [API do SDK do visualizador do HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) para criar seus próprios visualizadores de vídeo.

Para exibir os Relatórios de vídeo com base em um visualizador de vídeo criado usando a API do SDK do visualizador do HTML5:

1. Navegue até qualquer ativo de vídeo publicado.
1. Próximo ao canto superior esquerdo da página do ativo, na lista suspensa, selecione **[!UICONTROL Visualizadores]**.
1. Selecione qualquer predefinição do visualizador de vídeo e copie o código incorporado.
1. No código incorporado, encontre a linha com o seguinte:

   `videoViewer.setParam("config2", "<value>");`

   O `config2` ativa o rastreamento em visualizadores do HTML5. Também é uma predefinição específica da empresa que contém as informações de configuração dos Relatórios de vídeo e das configurações específicas do Adobe Analytics para o cliente.

   O valor correto do parâmetro config2 é encontrado tanto no **[!UICONTROL Código incorporado]** quanto na função de cópia **[!UICONTROL URL]**. No URL do comando de cópia **[!UICONTROL URL]**, procure pelo parâmetro `&config2=<value>`. O valor é quase sempre `companypreset`, mas em algumas instâncias também pode ser `companypreset-1`, `companypreset-2` e assim por diante.

1. No código personalizado do visualizador de vídeo, adicione AppMeasurementBridge.jsp à página do visualizador fazendo o seguinte:

   * Primeiro, determine se você precisa da variável `&preset` parâmetro.

      Se a variável `config2` parâmetro é `companypreset`, você *not* need `&preset=parameter`.

      If `config2` for qualquer outra coisa, defina o parâmetro predefinido como `config2` parâmetro. Por exemplo, se `config2=companypreset-2`, adicionar `&param2=companypreset-2` para o URL AppMeasurementBridge.jsp.

   * Em seguida, adicione o script AppMeasurementBridge.jsp:

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Crie o componente TrackingManager fazendo o seguinte:

   * Depois de chamar `s7sdk.Util.init();` crie uma instância TrackingManager para rastrear eventos, adicionando o seguinte:

      `var trackingManager = new s7sdk.TrackingManager();`

   * Conecte componentes ao TrackingManager fazendo o seguinte:

      No `s7sdk.Event.SDK_READY` manipulador de eventos, anexe o componente que deseja rastrear ao TrackingManager.

      Por exemplo, se o componente for `videoPlayer`, adicionar

      `trackingManager.attach(videoPlayer);`

      para anexar o componente ao trackingManager. Para rastrear vários visualizadores em uma página, use vários componentes do gerenciador de rastreamento.

   * Crie o objeto AppMeasurementBridge adicionando o seguinte:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * Adicione a função de rastreamento ao adicionar o seguinte:

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   O objeto appMeasurementBridge tem uma função de rastreamento integrada. No entanto, você pode fornecer o seu próprio para suportar vários sistemas de rastreamento ou outras funcionalidades.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

## Adicionar legendas ocultas ao vídeo {#adding-captions-to-video}

Você pode estender o alcance de seus vídeos para os mercados globais adicionando legendas ocultas a vídeos individuais ou aos Conjuntos de vídeos adaptáveis. Ao adicionar legendas, você evita a necessidade de dublar o áudio ou a necessidade de usar alto-falantes nativos para regravar o áudio para cada idioma diferente. O vídeo é reproduzido no idioma em que foi gravado. As legendas em idioma estrangeiro são exibidas para que pessoas de idiomas diferentes ainda possam entender a parte de áudio.

As legendas ocultas também permitem maior acessibilidade para pessoas surdas ou com deficiência auditiva.

>[!NOTE]
>
>O reprodutor de vídeo usado deve ser compatível com a exibição de legendas.

O Dynamic Media tem a capacidade de converter arquivos de legenda para o formato JSON (JavaScript Object Notation). Essa conversão significa que você pode incorporar o texto JSON em uma página da Web como uma transcrição oculta, mas completa, do vídeo. Os mecanismos de pesquisa podem, então, rastrear e indexar o conteúdo para tornar os vídeos mais fáceis de serem descobertos e fornecer aos clientes detalhes adicionais sobre o conteúdo do vídeo.

Consulte [Fornecer conteúdo estático (não imagem)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) no *Ajuda da API de disponibilização e renderização de imagens do Dynamic Media* para obter mais informações sobre como usar a função JSON em um URL.

**Para adicionar legendas ou legendas ao vídeo:**

1. Use um aplicativo ou serviço de terceiros para criar sua legenda/arquivo de subtítulo de vídeo.

   Certifique-se de que o arquivo criado siga o padrão WebVTT (Web Video Text Tracks). A extensão de nome de arquivo de legendagem é .vtt. Você pode obter mais informações sobre o padrão de legendagem WebVTT.

   Consulte [WebVTT: O formato de Rastreamento de texto da Web](https://dev.w3.org/html5/webvtt/).

   Há ferramentas e serviços gratuitos e premium que podem ser usados para criar arquivos de legenda/subtítulo fora do Dynamic Media. Por exemplo, para criar um arquivo de legenda de vídeo simples sem estilização, você pode usar a seguinte ferramenta de edição e criação de legendas online gratuitas:

   [Criador de legendas WebVTT](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Para obter melhores resultados, use a ferramenta no Internet Explorer 9 ou superior, Google Chrome ou Safari.

   Na ferramenta, no **[!UICONTROL Inserir o URL do arquivo de vídeo]** cole o URL copiado do arquivo de vídeo e toque em **[!UICONTROL Carregar]**. Consulte [Obter um URL de um ativo](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) para obter o URL para o próprio arquivo de vídeo, o qual você pode colar no campo **[!UICONTROL Inserir URL]** do arquivo de vídeo. O Internet Explorer, o Chrome ou o Safari podem reproduzir nativamente o vídeo.

   Agora siga as instruções na tela do site para criar e salvar seu arquivo WebVTT. Quando terminar, copie o conteúdo do arquivo de legenda e o cole em um editor de texto simples e salve com uma extensão de nome de arquivo .vtt.

   >[!NOTE]
   >
   >Para obter suporte global a legendas de vídeo em vários idiomas, esteja ciente de que o padrão WebVTT requer a criação de arquivos .vtt e chamadas separadas para cada idioma que você deseja suportar.

   Geralmente, você deseja nomear o arquivo VTT da legenda com o mesmo nome do arquivo de vídeo e anexá-lo à localidade do idioma, como -EN, ou -FR, ou -DE e assim por diante. Ao fazer isso, ele pode ajudá-lo a automatizar a geração dos URLs de vídeo usando seu sistema de gerenciamento de conteúdo da Web existente.

1. No AEM, carregue o arquivo de legenda da WebVTT no DAM.
1. Navegue até o *publicado* ativo de vídeo que você deseja associar ao arquivo de legenda carregado.

   Lembre-se de que os URLs só estão disponíveis para cópia *depois* que você *publicou* os ativos pela primeira vez.

   Consulte [Publicar ativos.](publishing-dynamicmedia-assets.md)

1. Faça uma das seguintes opções:

   * Para obter uma experiência do visualizador de vídeo pop-up, toque em **[!UICONTROL URL]**. Na caixa de diálogo URL, selecione e copie o URL para a Área de transferência e, em seguida, passe o URL para um editor de texto simples. Anexe o URL copiado do vídeo com a seguinte sintaxe:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Observe que `,1` no final do caminho da legenda. Imediatamente após a extensão do nome de arquivo .vtt no caminho, você tem a opção de ativar (ativar) ou desativar (desativar) o botão de legenda fechada na barra do reprodutor de vídeo, definindo como `,1` ou `,0`, respectivamente.

   * Para obter uma experiência de visualizador de vídeo incorporado, toque em **[!UICONTROL Código incorporado]**. Na caixa de diálogo Incorporar código, selecione e copie o código incorporado na Área de transferência e cole o código em um editor de texto simples. Anexe o código incorporado copiado com a seguinte sintaxe:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Observe que `,1` no final do caminho da legenda. Imediatamente após a extensão do nome de arquivo .vtt no caminho, você tem a opção de ativar (ativar) ou desativar (desativar) o botão de legenda fechada na barra do reprodutor de vídeo, definindo como `,1` ou `,0`, respectivamente.

## Adicionar marcadores de capítulo ao vídeo {#adding-chapter-markers-to-video}

Você pode tornar seus vídeos de formulário longos mais fáceis de assistir e navegar adicionando marcadores de capítulo a vídeos individuais ou aos Conjuntos de vídeos adaptáveis. Quando um usuário reproduz o vídeo, pode tocar nos marcadores de capítulo na linha do tempo do vídeo (também conhecido como depurador de vídeo) para navegar facilmente até o ponto de interesse, ou imediatamente para novos conteúdos, demonstrações, tutoriais e assim por diante.

>[!NOTE]
>
>O reprodutor de vídeo usado deve suportar o uso de marcadores de capítulo. Os players de vídeo do Dynamic Media são compatíveis com marcadores de capítulo, mas o uso de players de vídeo de terceiros não é compatível.

Se desejar, você pode criar e marcar seu próprio visualizador de vídeo personalizado com capítulos em vez de usar uma predefinição do visualizador de vídeo. Para obter instruções sobre como criar seu próprio visualizador do HTML5 com navegação de capítulo, na API do SDK do visualizador do Adobe HTML5, consulte o cabeçalho &quot;Personalização do comportamento usando modificadores&quot; nas classes `s7sdk.video.VideoPlayer` e `s7sdk.video.VideoScrubber`. Consulte a [API do SDK do visualizador do HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) documentação.

Você cria uma lista de capítulo para o vídeo da mesma forma que cria legendas. Ou seja, você cria um arquivo WebVTT. Observe, no entanto, que esse arquivo deve ser separado de qualquer arquivo de legenda WebVTT que você também possa estar usando; não é possível combinar legendas e capítulos em um arquivo WebVTT.

Você pode usar a seguinte amostra como exemplo do formato usado para criar um arquivo WebVTT com navegação de capítulo:

### Arquivo WebVTT com navegação de capítulo de vídeo {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

No exemplo acima, `Chapter 1` é o identificador de sinalização e é opcional. A hora de sinalização de `00:00:000 --> 01:04:364` especifica a hora de início e a hora de término do capítulo, em `00:00:000` formato. Os últimos três dígitos são milissegundos e podem ser deixados como `000`, se preferir. O título do capítulo de `The bicycle store behind it all` é a descrição real do conteúdo do capítulo. O identificador de sinalização, a hora de início e o título do capítulo são exibidos em uma pop-up no reprodutor de vídeo quando um usuário passa o ponteiro do mouse sobre um ponto de sinalização visual na linha do tempo do vídeo.

Como você está usando um visualizador de vídeo HTML5, certifique-se de que o arquivo de capítulo criado siga o padrão WebVTT (Web Video Text Tracks). A extensão do nome de arquivo do capítulo é .vtt. Você pode obter mais informações sobre o padrão de legendagem WebVTT.

Consulte [WebVTT: O formato de Rastreamento de texto da Web](https://dev.w3.org/html5/webvtt/)

**Para adicionar marcadores de capítulo ao vídeo:**

1. Usando um editor de texto simples fora do AEM, crie seu arquivo de capítulo de vídeo.

   Para obter suporte global a capítulos de vídeo em idiomas diferentes do inglês, esteja ciente de que o padrão WebVTT requer a criação de arquivos .vtt separados e chamadas para cada idioma que você deseja suportar.

1. Salve as `.vtt` na codificação UTF8 para evitar problemas com a representação de caracteres no texto do título do capítulo.

   Geralmente, você deseja nomear o arquivo VTT do capítulo com o mesmo nome do arquivo de vídeo e anexá-lo a capítulos. Ao fazer isso, ele pode ajudá-lo a automatizar a geração dos URLs de vídeo usando seu sistema de gerenciamento de conteúdo da Web existente.
1. No AEM, faça upload do arquivo de capítulo WebVTT.

   Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

1. Faça uma das seguintes opções:

   <table> 
     <tbody> 
      <tr> 
       <td>Para obter uma experiência de visualizador de vídeo pop-up</td> 
       <td> 
       <ol> 
       <li>Navegue até o <i>publicado </i>ativo de vídeo que você deseja associar ao arquivo de capítulo carregado. Lembre-se de que os URLs só estão disponíveis para cópia <i>depois</i> que você <i>publicou</i> os ativos pela primeira vez. Consulte <a href="/help/assets/publishing-dynamicmedia-assets.md">Publicar ativos.</a></li> 
       <li>No menu suspenso , toque em <strong>Visualizadores</strong>.</li> 
       <li>No painel à esquerda, toque no nome predefinido do visualizador de vídeo. Uma visualização do vídeo é aberta em uma página separada.</li> 
       <li>No painel à esquerda, na parte inferior, toque em <strong>URL</strong>.</li> 
       <li>Na caixa de diálogo URL, selecione e copie o URL para a Área de transferência e, em seguida, passe o URL para um editor de texto simples.</li> 
       <li>Anexe o URL copiado do vídeo com a seguinte sintaxe para associá-lo ao URL copiado para o arquivo de capítulo:<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>Para uma experiência de visualizador de vídeo incorporado<br /> </td> 
       <td> 
       <ol> 
       <li>Navegue até o <i>publicado </i>ativo de vídeo que você deseja associar ao arquivo de capítulo carregado. Lembre-se de que os URLs só estão disponíveis para cópia <i>depois</i> que você <i>publicou</i> os ativos pela primeira vez. Consulte <a href="/help/assets/publishing-dynamicmedia-assets.md">Publicar ativos.</a></li> 
       <li>No menu suspenso , toque em <strong>Visualizadores</strong>.</li> 
       <li>No painel à esquerda, toque no nome predefinido do visualizador de vídeo. Uma visualização do vídeo é aberta em uma página separada.</li> 
       <li>No painel à esquerda, na parte inferior, toque em <strong>Incorporar</strong>.</li> 
       <li>Na caixa de diálogo Incorporar código, selecione e copie o código inteiro para a Área de transferência e, em seguida, cole-o em um editor de texto simples.</li> 
       <li>Anexe o código incorporado do vídeo à seguinte sintaxe para associá-lo ao URL copiado ao arquivo de capítulo:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## Sobre miniaturas de vídeo {#about-video-thumbnails}

Você pode escolher entre uma das dez imagens em miniatura geradas automaticamente pelo Dynamic Media para adicionar ao vídeo. O reprodutor de vídeo exibe a miniatura selecionada quando um ativo de vídeo é usado com o componente Dynamic Media no ambiente de criação do AEM Sites, AEM Mobile ou AEM Screens. A miniatura serve como uma imagem estática que melhor representa o conteúdo de todo o vídeo e estimula ainda mais os usuários a tocar no botão Reproduzir .

Com base no tempo total do vídeo, o Dynamic Media captura dez imagens em miniatura (padrão) em 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81% e 91% no vídeo. As dez miniaturas persistem, o que significa que, se você decidir escolher uma miniatura diferente posteriormente, não precisará gerar novamente a série. Você visualiza as dez imagens em miniatura e, em seguida, seleciona aquela que deseja usar com o vídeo. Se quiser mudar para o padrão, use o CRXDE Lite para configurar o intervalo de tempo em que as imagens em miniatura são geradas. Por exemplo, se você quiser gerar apenas uma série de quatro imagens em miniatura espaçadas uniformemente a partir do seu vídeo, é possível configurar o tempo do intervalo em 24%, 49%, 74% e 99%.

Idealmente, você pode adicionar uma miniatura de vídeo a qualquer momento depois de fazer upload do vídeo, mas antes de publicar o vídeo no seu site.

Se preferir, você pode optar por fazer upload de uma miniatura personalizada para representar seu vídeo em vez de usar uma miniatura gerada pelo Dynamic Media. Por exemplo, você pode criar uma imagem em miniatura personalizada que tenha o título do seu vídeo, uma imagem de abertura atraente ou uma imagem muito específica capturada do seu vídeo. A imagem de miniatura de vídeo personalizada carregada deve ter uma resolução máxima de 1280 x 720 pixels (largura mínima de 640 pixels) e não deve ser maior que 2 MB.

>[!NOTE]
>
>As miniaturas de vídeo personalizadas só estão disponíveis ao executar o Dynamic Media - Modo híbrido.

### Adicionar uma miniatura de vídeo {#adding-a-video-thumbnail}

1. Navegue até um ativo de vídeo carregado que você deseja adicionar uma miniatura de vídeo.
1. No modo de seleção de ativos, a partir do **[!UICONTROL Exibição de lista]** ou **[!UICONTROL Exibição de cartão]**, toque no ativo de vídeo.
1. Na barra de ferramentas, toque no botão **[!UICONTROL Propriedades da exibição]** ícone (um círculo com um &quot;i&quot; nele).
1. No vídeo **[!UICONTROL Propriedades]** página, toque em **[!UICONTROL Alterar miniatura]**.
1. No **[!UICONTROL Alterar miniatura]** na barra de ferramentas, toque em **[!UICONTROL Selecionar quadro]**.

   O Dynamic Media gera uma série de imagens em miniatura do vídeo, com base no intervalo padrão ou no intervalo de tempo personalizado.

1. Visualize as imagens em miniatura geradas e selecione aquela que deseja adicionar ao vídeo.
1. Toque **[!UICONTROL Salvar alteração]**.

   A imagem em miniatura do vídeo é atualizada para usar a miniatura selecionada. Se decidir alterar a imagem em miniatura posteriormente, você poderá retornar ao **[!UICONTROL Alterar miniatura]** e selecione uma nova.

   Se você configurou novos intervalos de tempo padrão, ou carregou um novo vídeo para substituir o vídeo existente, será necessário ter o Dynamic Media regenerando as miniaturas.

   Consulte [Configuração do intervalo de tempo padrão em que as miniaturas de vídeo são geradas](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configure o intervalo de tempo padrão em que as miniaturas de vídeo são geradas {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Ao configurar e salvar o novo intervalo padrão, a alteração se aplica automaticamente somente aos vídeos que você fizer upload no futuro. Ele não aplica automaticamente o novo padrão aos vídeos que você carregou anteriormente. Para vídeos existentes, você deve gerar novamente as miniaturas.

Consulte [Adicionar uma miniatura de vídeo](#adding-a-video-thumbnail).

Para configurar o intervalo de tempo padrão em que as miniaturas de vídeo são geradas,

1. No AEM, toque em **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL CRXDE Lite]**.

1. Na página CRXDE Lite, no painel de diretórios à esquerda, navegue até `o etc/dam/imageserver/configuration/jcr:content/settings.`

   se o painel do diretório não estiver visível, talvez seja necessário tocar no ícone >> à esquerda da guia Home .

1. No painel inferior direito, no **[!UICONTROL Propriedades]** guia , toque duas vezes `thumbnailtime`.
1. Na caixa de diálogo Editar hora da miniatura, use os campos de texto para inserir valores de intervalo como porcentagens.

   * Toque no ícone de sinal de adição (+) para adicionar um ou mais campos de valor de intervalo. Talvez seja necessário rolar até a parte inferior da caixa de diálogo para ver o ícone .
   * Toque no ícone do sinal de menos (-) à direita de um campo de valor de intervalo para excluí-lo da lista.
   * Toque no ícone de seta para cima e no ícone de seta para baixo para reordenar os valores do intervalo.

1. Toque **[!UICONTROL OK]** para retornar ao **[!UICONTROL Propriedades]** guia .
1. Próximo ao canto superior esquerdo da página do CRXDE Lite, toque em **[!UICONTROL Salvar tudo]** em seguida, toque no **[!UICONTROL Página inicial]** no canto superior esquerdo para retornar ao AEM.

   Consulte [Adicionar uma miniatura de vídeo.](#adding-a-video-thumbnail)

### Adicionar uma miniatura de vídeo personalizada {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>Esse recurso só está disponível quando você executa o Dynamic Media - Modo híbrido.

1. Navegue até um ativo de vídeo carregado que você deseja adicionar uma miniatura de vídeo.
1. No modo de seleção de ativos, a partir do **[!UICONTROL Exibição de lista]** ou **[!UICONTROL Exibição de cartão]**, toque no ativo de vídeo.
1. Na barra de ferramentas, toque no botão **[!UICONTROL Propriedades da exibição]** ícone (um círculo com um &quot;i&quot; nele).
1. No vídeo **[!UICONTROL Propriedades]** página, toque em **[!UICONTROL Alterar miniatura]**.
1. No **[!UICONTROL Alterar miniatura]** na barra de ferramentas, toque em **[!UICONTROL Fazer upload da nova miniatura]**.
1. Navegue até uma imagem em miniatura que deseja usar, selecione-a e toque em **[!UICONTROL Abrir]** para começar a carregar a imagem no AEM
1. Depois que a imagem é carregada com sucesso, no **[!UICONTROL Alterar miniatura]** página, toque em **[!UICONTROL Salvar alterações]**.

   A miniatura personalizada é adicionada ao vídeo.
