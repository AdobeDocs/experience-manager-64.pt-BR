---
title: Vincular URLs ao seu aplicativo web
seo-title: Linking URLs to your Web Application
description: Como vincular URLs ao aplicativo da Web no dynamic media
seo-description: How to link URLs to your web application in dynamic media
uuid: cf599e66-b1f9-40c0-b572-cea19f2e6793
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d12e6ea3-aaf4-4672-9679-3c16c76d7d5b
exl-id: e076349d-8b1a-487f-b982-9440d7de13b9
feature: Configuration
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 10%

---

# Vincular URLs ao seu aplicativo web {#linking-urls-to-your-web-application}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Seus sites e aplicativos acessam os serviços da Dynamic Media por meio de chamadas de URL. Após publicar um ativo, o Dynamic Media ativa uma string de URL que faz referência a ele. Você pode colar esses URLs em um navegador da Web para testes.

Você vincula a URLs somente se *not* usando AEM como WCM. A vinculação/incorporação é usada quando você deseja fornecer um reprodutor de vídeo como uma janela pop-up ou modal. Se estiver usando o AEM como o WCM, [você adiciona os ativos diretamente na página.](adding-dynamic-media-assets-to-pages.md)

Para colocar essas cadeias de caracteres de URL em suas páginas da Web e aplicativos, copie-as do Dynamic Media.

>[!NOTE]
>
>As cadeias de caracteres de URL só estão disponíveis para representações dinâmicas de ativos. No momento, eles não estão disponíveis para ativos estáticos que residem no DAM e não no servidor de mídia dinâmica. O botão URL não é exibido para representações estáticas.

Consulte também [Incorporação do visualizador de vídeo ou imagem a uma página da Web.](embed-code.md)

Consulte também [Vincular URLs do YouTube ao seu aplicativo da Web.](video.md)

Consulte também [Fornecer imagens otimizadas para um site responsivo.](responsive-site.md)

Consulte também [Fazer upload de ativos.](managing-assets-touch-ui.md#uploading-assets)

## Obter um URL para um ativo {#obtaining-a-url-for-an-asset}

Você pode obter uma string de URL gerada por uma Predefinição de imagem ou por uma Predefinição do visualizador. Depois de copiar o URL, ele chega à Área de transferência para que você possa colá-lo conforme necessário nas páginas do seu site ou aplicativo.

>[!NOTE]
>
>O URL não está disponível para cópia até que você tenha publicado o ativo selecionado. Além disso, você também deve publicar a predefinição do visualizador ou a predefinição de imagem.
>
>Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
>
>Consulte [Predefinições do visualizador de publicação](managing-viewer-presets.md#publishing-viewer-presets).
>
>Consulte [Publicar predefinições da imagem](managing-image-presets.md#publishing-image-presets).

Há várias maneiras diferentes de obter uma string de URL. No entanto, as etapas abaixo mostram apenas um método que você pode usar.

**Para obter um URL para um ativo**:

1. Navegue até o *publicado* ativo cujo URL predefinido de imagem ou URL predefinido do visualizador você deseja copiar e toque no ativo para abri-lo.

   Lembre-se de que os URLs só estão disponíveis para cópia *depois* que você *publicou* os ativos pela primeira vez. Além disso, a predefinição do visualizador ou da imagem também deve ser publicada.

   Consulte [Publicar ativos.](publishing-dynamicmedia-assets.md)

   Consulte [Predefinições do visualizador de publicação](managing-viewer-presets.md#publishing-viewer-presets).

   Consulte [Publicar predefinições da imagem](managing-image-presets.md#publishing-image-presets).

1. Com base no ativo selecionado, execute um dos seguintes procedimentos:

   * Se você selecionou uma imagem, no menu suspenso, toque em **[!UICONTROL Representações]**.

      Em **[!UICONTROL Dinâmico]** toque em um nome predefinido para exibir sua representação no quadro direito. Talvez seja necessário rolar a lista Representações para ver o cabeçalho Dinâmico .

      Na parte inferior do painel à esquerda, toque em **[!UICONTROL URL]**.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * Se você selecionou um conjunto de rotação, um conjunto de imagens, um conjunto de carrossel ou um vídeo, no menu suspenso, toque em **[!UICONTROL Visualizadores]**.

      No painel à esquerda, toque em um nome de predefinição do visualizador. Uma visualização do conjunto ou do vídeo é aberta em uma página separada.

      No painel à esquerda, na parte inferior, toque em **[!UICONTROL URL]**.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Selecione e copie o texto no navegador para visualizar o ativo ou para adicioná-lo à página de conteúdo da Web.

   Para sair da janela do URL, toque no **[!UICONTROL X]** ou toque **[!UICONTROL Fechar]**.

## Obter um URL para um ativo estático {#obtaining-a-url-for-a-static-asset}

O Dynamic Media oferece suporte à entrega de ativos estáticos, que são ativos adicionais além de apenas imagens e vídeo. Os formatos de ativos estáticos suportados para entrega incluem:

* GIF animado
* Arquivos de áudio
* CSS
* JavaScript (quando sua empresa é configurada com seu próprio domínio)
* PDF
* SVG
* XML
* ZIP

**Para obter um URL para um ativo estático**:

1. Navegue até o ativo *estático *publicado cujo URL você deseja copiar e toque no ativo para abri-lo.

   Lembre-se de que os URLs só estão disponíveis para cópia *after* você tem primeiro *publicado* o ativo estático.

   Consulte [Publicar ativos.](publishing-dynamicmedia-assets.md)

1. Use qualquer um dos métodos a seguir para obter o URL do ativo estático publicado:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Por exemplo, `https://aem.com/is/content/adobe/image.gif`.
   * click **[!UICONTROL Ativo > Representações dinâmicas]**, em seguida, toque em uma representação dinâmica do ativo estático e copie o URL.

      Altere o URL copiado para usar `is/content` no caminho em vez de `is/image/`.


## Obter um URL de vídeo para uma representação de vídeo publicada {#obtaining-a-video-url-for-a-published-video-rendition}

1. Em AEM, navegue até **[!UICONTROL Ferramentas > Implantação > Nuvem > Cloud Services]**.
1. Na página **[!UICONTROL Serviços da nuvem]**, role até o cabeçalho **[!UICONTROL Serviços de nuvem do Dynamic Media]** e toque em **[!UICONTROL Mostrar configurações]**.
1. Em **[!UICONTROL Configurações disponíveis]**, toque no nome da configuração desejada.

1. No **[!UICONTROL Configurações da Dynamic Media Cloud]** página, em **[!UICONTROL URL do serviço de vídeo]**, copie todo o caminho do URL. Posteriormente, você precisará do caminho do URL copiado nas etapas.

   Por exemplo, o caminho do URL pode ser semelhante ao seguinte:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (O caminho acima serve apenas para fins ilustrativos; não é o caminho real que você copia.)

1. Em **[!UICONTROL ID de registro]**, copie o nome do cliente encontrado na última parte da ID.

   Por exemplo, se a ID de registro foi `87654321|MyCompany`, o nome do cliente seria `MyCompany`.

1. Próximo ao canto superior esquerdo da página, toque em **[!UICONTROL Cloud Service]s**, em seguida, toque no ícone de AEM e navegue até **[!UICONTROL Geral > CRXDE Lite]**.
1. Copie todo o caminho de representação de vídeo do JCR (Java Content Repository).

   Por exemplo, o caminho de representação do vídeo pode ser exibido de forma semelhante ao seguinte:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (O caminho acima serve apenas para fins ilustrativos; não é o caminho real que você copia.)

1. Organize as informações copiadas na seguinte ordem para formar um caminho de URL completo:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Por exemplo, usando os caminhos de exemplo e o nome de cliente de exemplo das etapas acima, o caminho completo é exibido da seguinte maneira:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Este é o URL completo do vídeo para uma representação de vídeo publicada.

## Obter um URL de vídeo para transmissão adaptável (HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Em AEM, navegue até **[!UICONTROL Ferramentas > Implantação > Nuvem > Cloud Services]**.
1. Na página **[!UICONTROL Serviços da nuvem]**, role até o cabeçalho **[!UICONTROL Serviços de nuvem do Dynamic Media]** e toque em **[!UICONTROL Mostrar configurações]**.
1. Em **[!UICONTROL Configurações disponíveis]**, toque no nome da configuração desejada.
1. No **[!UICONTROL Configurações do Dynamic Media Cloud Services]** faça o seguinte:

   * Em **[!UICONTROL URL do serviço de vídeo]**, copie o caminho do URL inteiro. Posteriormente, você precisará do caminho do URL copiado nessas etapas. Por exemplo, o caminho do URL pode ser semelhante ao seguinte:

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (O caminho acima serve apenas para fins ilustrativos; não é o caminho real que você copia.)

   * Em **[!UICONTROL ID de registro]**, copie o nome do cliente encontrado na última parte da ID. Posteriormente, você precisará do nome do cliente copiado nessas etapas.

      Por exemplo, se a ID de registro foi `87654321|demoCo`, o nome do cliente que você copiar seria `demoCo`.


1. Com base no protocolo de entrega de vídeo que você está usando, copie o respectivo seletor de protocolo. Posteriormente, você precisará do seletor de protocolo copiado nessas etapas.

   | Protocolo de entrega de vídeo usado | Seletor de protocolo a ser usado |
   |---|---|
   | HTTP <br> Se estiver usando HTTP (entrega de vídeo não segura), altere https para http no valor do URL do Serviço de vídeo copiado anteriormente. | `public/` |
   | HTTPS | `public-ssl/` |

1. Copie o caminho completo do ativo de vídeo no AEM, conforme processado pelo Dynamic Media. Posteriormente, você precisará desse caminho de ativo de vídeo copiado nessas etapas.

   Por exemplo:

   `/content/dam/marketing/MyVideo.mp4`

1. Combine todas as partes copiadas anteriormente para criar uma cadeia de caracteres na seguinte ordem:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Por exemplo, usando as informações copiadas dos exemplos nessas etapas, a sequência de caracteres seria exibida da seguinte maneira:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Preencha o URL ao anexar `.m3u8` ao final da string. Por exemplo, anexar `.m3u8` para a string da etapa anterior, o caminho completo do URL seria exibido da seguinte maneira:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Usar HTTP/2 para fornecer ativos da Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 é o novo protocolo da Web atualizado que melhora a maneira como os navegadores e servidores se comunicam. Ele oferece transferência mais rápida de informações e reduz a quantidade de poder de processamento necessário. A entrega de ativos do Dynamic Media agora pode ser feita via HTTP/2, o que oferece melhor resposta e tempo de carregamento.

Consulte [Entrega de conteúdo HTTP2](http2.md) para obter detalhes completos sobre a introdução ao HTTP/2 com sua conta do Dynamic Media.
