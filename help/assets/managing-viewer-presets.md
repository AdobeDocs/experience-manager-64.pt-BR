---
title: Gerenciar predefinições do visualizador do Dynamic Media
seo-title: Gerenciar predefinições do visualizador do Dynamic Media
description: Como criar e gerenciar predefinições do visualizador do Dynamic Media
seo-description: Como criar e gerenciar predefinições do visualizador do Dynamic Media
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Predefinições do visualizador
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '4236'
ht-degree: 12%

---

# Gerenciar predefinições do visualizador do Dynamic Media {#managing-viewer-presets}

Uma predefinição do visualizador do Dynamic Media é uma coleção de configurações que determinam como os usuários visualizam ativos de mídia avançada em suas telas de computadores e dispositivos móveis. Se você for um administrador, poderá criar Predefinições do visualizador. As configurações estão disponíveis para uma matriz de opções de configuração do visualizador. Por exemplo, você pode alterar o tamanho de exibição do visualizador ou o comportamento de zoom.

Para obter instruções sobre como criar e personalizar suas próprias predefinições do visualizador de HTML5, consulte a Documentação da API do SDK do visualizador de HTML5 do Adobe Dynamic Media *HTML5.* O SDK está disponível no servidor de publicação do IS incorporado no próprio SDK. Cada versão da biblioteca tem sua própria documentação do SDK incluída.

Caminho: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
Por exemplo, 3.10 SDK: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

Consulte também o [Adobe Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Esta seção descreve como criar, editar e gerenciar predefinições do visualizador. Você pode aplicar uma predefinição do visualizador a um ativo a qualquer momento que o visualizar. Consulte [Aplicação de predefinições do visualizador](viewer-presets.md).

>[!NOTE]
>
>Observe que a edição de qualquer *predefinições predefinidas e predefinidas do visualizador* não é um cenário suportado. Se você tentar editar uma predefinição do visualizador pronta para uso, será solicitado que você salve a predefinição do visualizador usando um novo nome.

## Acessibilidade de teclado para visualizadores {#keyboard-accessibility-for-viewers}

Todos os visualizadores prontos para uso suportam acessibilidade do teclado.

Consulte também [Acessibilidade do teclado e navegação](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Gerenciar predefinições do visualizador do Dynamic Media {#managing-presets}

Adicione, edite, exclua, publique, cancele a publicação e visualize predefinições do visualizador no AEM ao tocar em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.

![ativos-ferramentas](assets/tools-assets.png)

>[!NOTE]
>
>Por padrão, o sistema mostra 15 predefinições do visualizador ao selecionar Visualizadores na exibição detalhada de um ativo. Você pode aumentar esse limite. Consulte [Aumentar o número de predefinições do visualizador exibidas](#increasing-the-number-of-viewer-presets-that-display).

## Suporte ao visualizador para páginas da Web responsivas projetadas {#viewer-support-for-responsive-designed-web-pages}

Páginas da Web diferentes têm necessidades diferentes. Por exemplo, às vezes, você deseja uma página da Web que forneça um link que abra o Visualizador de HTML5 em uma janela separada do navegador. Em outros casos, pode ser necessário incorporar o Visualizador de HTML5 diretamente na página de hospedagem. No último caso, a página da Web pode ter um layout estático. Ou pode ser *responsivo* e exibido de forma diferente em diferentes dispositivos ou para tamanhos de janela de navegador diferentes. Para acomodar essas necessidades, todos os visualizadores HTML5 predefinidos e prontos que vêm com o Dynamic Media suportam páginas da Web estáticas e páginas da Web responsivas projetadas.

Consulte [Biblioteca de imagens responsivas](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) na *Ajuda da API de disponibilização de imagens* para obter mais informações sobre como incorporar visualizadores responsivos às suas páginas da Web.

>[!NOTE]
>
>Observe que você deve publicar todos os visualizadores prontos para uso antes de usá-los pela primeira vez.\
>Consulte [Predefinições do Visualizador de Publicação.](#publishing-viewer-presets)

## Compatibilidade do sistema predefinido do visualizador {#viewer-preset-system-compatibility}

Todas as predefinições do visualizador prontas para uso que acompanham o Dynamic Media são totalmente compatíveis com os seguintes sistemas:

* Desktops
* Apple iPhone
* Apple iPad
* Android Smartphone
* Tablet Android
* Para vídeo, é fornecido suporte adicional para reprodução MP4 para [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) e [Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### Tipos de mídia avançada para predefinições do visualizador {#rich-media-types-for-viewer-presets}

Os administradores podem adicionar e personalizar os seguintes tipos de mídia avançada ao criar novas predefinições do visualizador.

| Tipos de mídia avançada | Descrição |
|:---|:---|
| **Conjunto do Carousel** | Pontos de acesso, mapas de imagem ou ambos são adicionados a uma série de duas ou mais imagens. Um cliente pode deslocar as imagens para a esquerda ou para a direita e clicar em um ponto de acesso em uma imagem para obter detalhes adicionais ou para comprar diretamente da categoria, da página inicial ou da página de aterrissagem de um site. |
| **Flyout Zoom** | Exibe uma segunda imagem da área com zoom ao lado da imagem original. Não há controles a serem usados; os usuários movem a seleção para a área que desejam visualizar. |
|  | Ao determinar o uso total da largura de banda para esse visualizador, considere que a imagem principal e a imagem flyout são servidas no visualizador. O tamanho da imagem principal (Largura e Altura do Palco) e o Fator de Zoom determinam o tamanho da imagem do flyout. Para impedir que o tamanho do arquivo flyout se torne muito grande, equilibre esses dois valores: se você tiver um tamanho de imagem principal grande, abaixe o valor de Fator de Zoom. (A Largura do Flyout e a Altura do Flyout determinam o tamanho da janela do flyout, mas não o tamanho da imagem do flyout que é servida no visualizador.) |
|  | Por exemplo, se o tamanho da imagem principal for 350 por 350 pixels, com um Fator de Zoom de 3, a imagem de flyout resultante será de 1050 por 1050 pixels. Se o tamanho da imagem principal for 300 por 300 pixels, com um Fator de Zoom de 4, a imagem de flyout será de 1200 por 1200 pixels. Dependendo da configuração de qualidade JPEG (as configurações recomendadas estão entre 80 e 90), você pode diminuir o tamanho do arquivo significativamente. Os fatores de zoom recomendados são de 2,5 a 4, dependendo do tamanho da imagem principal. |
| **Zoom em linha** | Exibe uma imagem da área com zoom no visualizador original. Não há controles para usar. Ou seja, os usuários movem a seleção para a área que desejam visualizar. |
| **Definição de imagem** | No visualizador de Conjunto de imagens, os usuários podem ver diferentes exibições ou variações de cor de um item clicando em uma imagem em miniatura. Esse visualizador também oferece ferramentas de zoom para examinar imagens de perto. |
| **Imagem interativa** | Os pontos de acesso são adicionados a partes de uma imagem em que um cliente pode clicar para obter detalhes adicionais ou para comprar diretamente de uma categoria de site, página inicial ou página inicial. |
| **Vídeo interativo** | As miniaturas são adicionadas aos segmentos da linha do tempo em um vídeo, em que um cliente pode clicar para obter detalhes adicionais ou para comprar diretamente da categoria, da página inicial ou da página de aterrissagem de um site. |
| **Mix de mídia** | Exibe diferentes tipos de mídia em um visualizador. Você pode incluir conjuntos de rotação, conjunto de imagens, imagens e vídeos. |
| **Imagem panorâmica** | Os visualizadores Panorâmica Image e PanorâmicaVR renderizam imagens panorâmicas esféricas para mergulhar os usuários em uma experiência de visualização de 360° de uma sala, propriedade, localização ou paisagem. |
|  | Para que uma imagem carregada seja qualificada como um panorama esférico, ela deve ter um ou ambos os itens a seguir: <ul><li>Uma proporção de aspecto de 2:1.</li><li>Marcada com as palavras-chave &quot;equirectangular&quot;, &quot;esférico&quot; e &quot;panorama&quot;, &quot;esférico&quot; e &quot;panorâmico&quot;. Consulte [Uso de tags](../sites-authoring/tags.md).</li></ul> |
|  | Tanto a proporção quanto os critérios de palavra-chave se aplicam aos ativos panorâmicos da página de detalhes do ativo e ao componente WCM &quot;Mídia panorâmica&quot;. |
|  | Importante: Este visualizador só está disponível no modo Dynamic Media - Scene7. |
| **Grupo de rotação** | Fornece várias visualizações de uma imagem para que os usuários possam girar o objeto para examinar os diferentes lados e ângulos. |
| **Vídeo** | Reproduz vídeo usando streaming progressivo ou adaptável de taxa de bits. O streaming adaptável da taxa de bits executa automaticamente a detecção de dispositivo e de largura de banda para veicular o vídeo de qualidade certa no formato correto. |
| **Zoom vertical** | O visualizador de Zoom vertical permite maximizar uma experiência de visualização de imagem de produto para fornecer aos usuários a melhor representação de um produto. A localização vertical das amostras faz o seguinte: <ul><li>Garante que as amostras estejam acima da dobra. Com amostras horizontais, dependendo do tamanho da tela da área de trabalho do  do usuário, as amostras não ficavam visíveis até que o usuário rolasse pela página. Ao colocar as amostras verticalmente no visualizador, ele garante que elas fiquem visíveis, independentemente do tamanho da tela do usuário.</li><li>Maximiza o tamanho da imagem principal. Com amostras horizontais, é necessário reservar espaço na página para garantir que elas estejam visíveis. Esse posicionamento diminuiu o tamanho da imagem principal. No entanto, com um layout de amostra vertical, não é necessário alocar esse espaço. Dessa forma, você pode maximizar o tamanho da imagem principal.</li></ul> |
| **Zoom** | Permite que os usuários ampliem a área clicando nela. Os usuários podem clicar em controles para ampliar, reduzir e redefinir a imagem para seu tamanho padrão. |

## Lista de predefinições do visualizador pronto para uso {#list-of-out-of-the-box-viewer-presets}

A tabela a seguir identifica todas as predefinições do visualizador predefinidas e prontas para uso que acompanham o Dynamic Media.

Consulte também [Demonstrações em tempo real](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Para obter informações sobre versões compatíveis de navegadores da Web e sistemas operacionais para visualizadores, consulte as Notas de versão dos visualizadores.

Consulte *Notas de versão dos visualizadores* no índice do [Guia de referência dos visualizadores](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

>[!NOTE]
>
>Todas as predefinições do visualizador prontas para uso no Dynamic Media já estão ativadas (ativadas), mas você deve publicá-las.\
>Consulte [Predefinições do visualizador de publicação](#publishing-viewer-presets).
>
>Todas as novas predefinições do visualizador criadas e adicionadas devem ser ativadas *e* publicadas.\
>Consulte [Ativando ou desativando predefinições do visualizador](#activating-or-deactivating-viewer-presets) e [Predefinições do visualizador de publicação](#publishing-viewer-presets).

| Título da predefinição do visualizador | Tipo | Nome do arquivo CSS |
|:---|:---|:---|
| Carrossel_Dotted_dark | Carrossel_Set | html5_carouselviewer_doted_dark.css |
| Carrossel_Dotted_light | Carrossel_Set | html5_carouselviewer_doted_light.css |
| Carrossel_Numérico_escuro | Carrossel_Set | html5_carouselviewer_numeric_dark.css |
| Carrossel_Numeric_light | Carrossel_Set | html5_carouselviewer_numeric_light.css |
| Flyout | Flyout_Zoom | html5_flyoutviewer.css |
| ImageSet_dark | Definição de imagem | html5_zoomviewer_dark.css |
| ImageSet_light | Definição de imagem | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | Mixed_Media | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | Mixed_Media | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | Flyout_Zoom | html5_inlinezoomviewer.css |
| MixedMedia_dark | Mixed_Media | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | Mixed_Media | html5_mixedmediaviewer_light.css |
| PanorâmicaImage | Panorâmica_Imagem | html5_panoramicimage.css |
| PanorâmicaImageVR | Panorâmica_Imagem | html5_panoramicimage.css |
| Shoppable_Banner | Imagem_Interativa | html5_interactiveimage.css |
| Shoppable_Video_dark | Interative_Video | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Interative_Video | html5_interactivevideovewer_light.css |
| SpinSet_dark | Spin_Set | html5_spinviewer_dark.css |
| SpinSet_light | Spin_Set | html5_spinviewer_light.css |
| Vídeo (inclui suporte para legendas ocultas) | Vídeo | html5_videoviewer.css |
| Video_social (Inclui suporte para legendas ocultas e mídia social) | Vídeo | html5_videoviewersocial.css |
| Zoom_escuro | Zoom | html5_basiczoomviewer_dark.css |
| Zoom_light | Zoom | html5_basiczoomviewer_light.css |
| ZoomVertical_escuro | Zoom Vertical | html5_zoomverticalviewer_dark.css |
| ZoomVertical_Light | Zoom Vertical | html5_zoomverticalviewer_light.css |

### Matriz de gestos de visualizadores móveis compatível {#supported-mobile-viewers-gestures-matrix}

A tabela a seguir identifica os gestos do visualizador móvel que são compatíveis com dispositivos iOS, Android 2.x e Android 3.x.

| Gesto | Zoom do Flyout | Zoom | Rotação |
|---|---|---|---|
| **Arrastar** | Canetas | Canetas | Canetas |
| **Tocar** | Mostra a janela do flyout | Mostra ou oculta a interface do usuário | Mostra ou oculta a interface do usuário |
| **Toque duplo** | Não se aplica | Amplia ou redefine | Amplia ou redefine |
| **Pinça aberta** | Não se aplica | Ampliação (somente iOS e Android 3x) | Ampliação (somente iOS e Android 3x) |
| **Feche a pinça** | Não se aplica | Diminui o zoom (somente iOS e Android 3x) | Diminui o zoom (somente iOS e Android 3x) |
| **Deslizar** | Rola a barra de amostra | Rolar imagens | Rotação |
| **Cintilação** | Rola a barra de amostra | Rolar imagens | Rotação |

## Aumentar o número de predefinições do visualizador do Dynamic Media que exibem {#increasing-the-number-of-viewer-presets-that-display}

AEM mostra uma grande variedade de predefinições do visualizador ao visualizar ativos de **[!UICONTROL Exibição de detalhes > Visualizadores]**. Você pode aumentar ou diminuir o número de visualizadores exibidos.

**Para aumentar o número de predefinições do visualizador do Dynamic Media exibidas**:

1. Navegue até **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Navegue até o nó da listagem de predefinições do visualizador em `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Na propriedade **[!UICONTROL limit]**, altere o **[!UICONTROL Value]**, que é definido como 15 por padrão, para o número desejado.
1. Navegue até a fonte de dados predefinida do visualizador em `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. Na propriedade **[!UICONTROL limit]**, altere o número para o número desejado, por exemplo `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Toque em **[!UICONTROL Salvar tudo]**.

## Criar uma nova predefinição do visualizador do Dynamic Media {#creating-a-new-viewer-preset}

A criação de predefinições do visualizador permite aplicar várias configurações para visualizar e interagir com ativos. No entanto, não é necessário criar novas predefinições do visualizador. Se preferir, você pode usar as predefinições padrão do visualizador pronto para uso que já vêm com o AEM Assets.

Se você optar por criar uma nova predefinição do visualizador, depois de salvá-la, o estado do visualizador será ativado automaticamente (definido como **On**) na página **[!UICONTROL Predefinições do visualizador]**. Esse estado significa que está visível no componente **[!UICONTROL Dynamic Media]** e no componente **[!UICONTROL Mídia interativa]** e sempre que você visualiza uma imagem ou vídeo.

Algumas predefinições do visualizador têm configurações exclusivas que podem afetar o uso e o comportamento geral do visualizador. Dependendo da predefinição do visualizador que você estiver criando, talvez você queira estar ciente dessas considerações especiais.

Consulte [Considerações especiais para criar uma predefinição do Visualizador interativo](#special-considerations-for-creating-an-interactive-viewer-preset).

Consulte [Considerações especiais para criar uma predefinição do Visualizador do banner do carrossel](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**Para criar uma nova predefinição** do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.

   ![predefinições do visualizador](assets/viewerpresets.png)

1. Na página **[!UICONTROL Predefinições do visualizador]** , na barra de ferramentas, toque em **[!UICONTROL Criar]**.
1. Na caixa de diálogo **[!UICONTROL New Viewer Preset]**, no campo **[!UICONTROL Preset Name]**, digite o nome da nova predefinição. Escolha um nome com cuidado, eles não são editáveis depois de tocar em **[!UICONTROL Create]**.

   Quando você salvar a predefinição posteriormente nessas etapas, o nome aparecerá na página Predefinições do visualizador no cabeçalho da coluna **[!UICONTROL Título da predefinição]**.

1. No menu suspenso **[!UICONTROL Rich Media Type]**, selecione o tipo de predefinição do visualizador que deseja criar e, no canto superior direito da página, toque em **[!UICONTROL Criar]**.

   Consulte [Tipos de mídia avançada para predefinições do visualizador](#rich-media-types-for-viewer-presets).

1. Na página **Editar predefinição do visualizador**, toque na guia **[!UICONTROL Aparência]**.
1. Faça uma das seguintes opções:

   * No menu suspenso **[!UICONTROL Tipo selecionado]**, selecione um componente cujo design visual você deseja personalizar. Como alternativa, toque em qualquer elemento visual no visualizador para selecioná-lo para configuração.

      O editor visual permite ver qual efeito uma determinada propriedade tem em um estilo. Basta definir ou ajustar qualquer propriedade para ver instantaneamente qual efeito ela tem no visualizador usando a amostra à esquerda do editor.

      As propriedades de estilo CSS para cada tipo de predefinição do visualizador são descritas no tópico de Ajuda &quot;Personalizando *&lt;nome_do_visualizador>* visualizador&quot; no [Guia de referência do visualizador](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

      Por exemplo, se você estiver criando uma predefinição do visualizador do tipo `Mixed_Media`, consulte [Personalizando visualizador de mídia mista](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) para obter uma lista e uma descrição de cada propriedade.

   * Se você tiver definido as configurações de estilo em um arquivo CSS separado, é possível fazer upload do arquivo CSS para o AEM Assets. Toque em **[!UICONTROL Importar CSS]** abaixo do menu suspenso **[!UICONTROL Tipo selecionado]** (talvez seja necessário rolar o editor visual para cima para vê-lo) para encontrar o arquivo CSS carregado e associá-lo à predefinição do visualizador.

      Ao importar um arquivo CSS, o editor visual verifica se o CSS usa os marcadores do visualizador corretos. Por exemplo, se você estiver criando um visualizador de Zoom, todas as regras de CSS importadas devem ser definidas usando o nome da classe do visualizador `.s7mixedmediaviewer` definido em um elemento do visualizador pai.

      Você pode importar CSS arbitrário e artesanal, desde que ele defina corretamente os marcadores de CSS para um determinado visualizador. (Os marcadores CSS são descritos em qualquer tópico da Ajuda &quot;Personalizando *&lt;nome do visualizador>* visualizador&quot; no [Guia de referência de visualizadores](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html). Por exemplo, se você deseja ler sobre marcadores CSS para o Visualizador de Zoom, consulte [Personalizando Visualizador de Zoom](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) No entanto, é possível que o editor visual não entenda alguns valores de CSS. Nesses casos, o editor visual tenta substituir os erros para que o CSS ainda possa funcionar.
   >[!NOTE]
   >
   >Se preferir editar o CSS diretamente em sua forma bruta, toque em **[!UICONTROL Mostrar/Ocultar CSS]** abaixo do menu suspenso Tipo selecionado (talvez seja necessário rolar o editor visual para cima para vê-lo).****
   >
   >Como o editor visual, quando você faz uma alteração em uma propriedade diretamente no CSS, você pode ver instantaneamente qual efeito ela tem na amostra do visualizador. E essa mesma propriedade é atualizada automaticamente ao mesmo tempo no editor visual. Dessa forma, você pode usar o editor de CSS bruto, o editor visual ou ambos alternadamente.

   >[!NOTE]
   >
   >Para arte-final de botão, escolha a imagem 2x e faça upload de arte de alta resolução. Ao trabalhar com imagens interativas e banners que podem ser comprados, também é possível selecionar a partir de vários botões de ponto de acesso prontos para uso.

1. (Opcional) Próximo à parte superior da página **[!UICONTROL Editar predefinição do visualizador]**, toque em **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** ou **[!UICONTROL Telefone]** para definir estilos visuais de forma exclusiva para diferentes tipos de dispositivo e tela.
1. Na página **[!UICONTROL Editar predefinição do visualizador]**, toque na guia **Comportamento**. Como alternativa, toque ou clique em qualquer elemento visual no visualizador para selecioná-lo para configuração.
1. No menu suspenso **[!UICONTROL Tipo selecionado]**, selecione um componente cujos comportamentos você deseja alterar.

   Muitos componentes no editor visual têm uma descrição detalhada associada a ela. Essas descrições são exibidas em caixas azuis quando você expande um componente para revelar seus parâmetros associados.

   Alguns tipos de Visualizador têm componentes que permitem especificar comandos do Servidor de imagens em um campo de texto **Comando IS**. Para obter uma lista de comandos que podem ser usados, consulte a [Referência da API de disponibilização de imagens](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html).

   >[!NOTE]
   >
   >**Se estiver usando um dispositivo de toque, como um telefone ou tablet...**
   >
   >Depois de digitar um valor no campo de texto, toque em outro lugar na interface do usuário para enviar a alteração e fechar o teclado virtual. Se você tocar em **[!UICONTROL Enter]**, nenhuma ação ocorre.

1. Próximo ao canto superior direito da página, toque em **[!UICONTROL Salvar]**.
1. Publique sua nova predefinição do visualizador. Você deve publicar a predefinição antes de usá-la em seu site.

   Consulte [Predefinições do visualizador de publicação](#publishing-viewer-presets).

## Considerações especiais para criar uma predefinição do Visualizador interativo {#special-considerations-for-creating-an-interactive-viewer-preset}

**Sobre modos de exibição para miniaturas de imagem no painel**

Ao criar ou editar uma predefinição do visualizador de Vídeo interativo, você tem a opção de qual configuração **[!UICONTROL Modo de exibição]** usar ao selecionar `InteractiveSwatches` no menu suspenso **[!UICONTROL Componente selecionado]** sob a guia **[!UICONTROL Comportamento]**. O modo de exibição escolhido afeta a forma como e quando as miniaturas são exibidas durante a reprodução do vídeo. Você pode escolher um `segment`modo de exibição (padrão) ou um `continuous`modo de exibição.

| Modo de exibição | Descrição |
|---|---|
| [!UICONTROL Segmento] |  Segmenta o modo de exibição padrão das predefinições do Visualizador de vídeo interativo prontas para uso do Visualizador de vídeo interativo Shoppable_Video_light e Shoppable_Video_dark, além de qualquer predefinição do Visualizador de vídeo interativo que você mesmo cria. |
|  | Nesse modo, quando há menos miniaturas atribuídas a um segmento de vídeo do que o número de pontos visíveis no painel de exibição, as miniaturas do subsegmento seguinte ou anterior não são recebidas para preencher nenhum ponto vazio no painel. Ou seja, preserva a exibição de amostras atribuídas ao segmento específico do vídeo. |
| [!UICONTROL Contínuo] | No modo de exibição [!UICONTROL Continuous], se o número de miniaturas em um segmento for menor que o número visível no painel, o visualizador incluirá automaticamente a exibição de miniaturas do próximo segmento ou do segmento anterior, nos casos em que a última miniatura for exibida. |

**Sobre o comportamento de rolagem automática no visualizador de vídeo interativo**

O comportamento de rolagem automática das miniaturas no visualizador de Vídeo interativo funciona independentemente do modo de exibição escolhido.

Ao criar ou editar uma predefinição interativa do visualizador de vídeo, você acessa **[!UICONTROL Rolagem automática]** na guia **[!UICONTROL Comportamento]**. Na guia Comportamento, no menu suspenso **[!UICONTROL Componentes selecionados]**, toque em **[!UICONTROL InteractiveSwatches]**. A caixa de seleção **[!UICONTROL Rolagem automática]** está listada abaixo do campo de texto Comando IS.

Se desativar a opção **[!UICONTROL Rolagem automática]** (desmarcar a caixa de seleção) na predefinição do visualizador, durante a reprodução do vídeo pelo usuário, o painel exibirá apenas a primeira imagem em miniatura em toda a duração do vídeo. Entretanto, um usuário pode rolar manualmente pelas miniaturas usando os ícones de seta para cima e para baixo, se desejar.

Ao ativar (selecionar) a **[!UICONTROL Rolagem automática]** na predefinição do visualizador as imagens em miniatura atribuídas a um segmento de vídeo são roladas para exibição no início de um segmento durante a reprodução do vídeo. Entretanto, há instâncias em que determinadas miniaturas em um segmento são exibidas com duas vezes mais comprimento no início ou no final delas. Esse comportamento ocorre porque a quantidade de miniaturas em um segmento é maior que o número visível no painel e não é divisível uniformemente.

Para ilustrar, suponha que você tenha um segmento de vídeo de 30 segundos. E há um total de nove miniaturas para serem exibidas nos 30 segundos. Seu navegador é dimensionado de forma que haja quatro posições de miniatura visíveis no painel de exibição. O segmento de tempo do vídeo de 30 segundos é dividido em três subsegmentos. A tabela a seguir mostra o detalhamento de quais miniaturas são exibidas para um determinado subsegmento de tempo:

| **Subsegmento de vídeo** | **Tempo do subsegmento em segundos** | **Miniaturas visíveis no painel** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

O subsegmento de vídeo 3 não se estende além das miniaturas atribuídas a ele. Observe também que as miniaturas 4, 6 e 7 são visíveis no painel duas vezes mais longas do que as outras miniaturas.

A lógica que o visualizador usa para quantas miniaturas são exibidas no painel com base no número de posições disponíveis é a seguinte:

* Número de subsegmentos = arredondar para o próximo subsegmento (número de miniaturas/número de slots visíveis no painel de miniatura, com base no tamanho da janela do navegador).

   Usando o exemplo na tabela acima, 9 miniaturas / 4 slots = 2,25; a lógica do visualizador arredonda até três subsegmentos.

* Número de miniaturas = arredondar para a próxima miniatura (número de miniaturas / número de subsegmentos de vídeo).

   Usando o exemplo na tabela acima, 9 miniaturas / 3 subsegmentos de vídeo = 3 miniaturas.

* Duração do subsegmento = duração total do vídeo / número de subsegmentos do vídeo.

   Usando o exemplo na tabela acima, 30 segundos / 3 subsegmentos de vídeo = 10 segundos de exibição de cada subsegmento de vídeo.

### Considerações especiais para criar uma predefinição do visualizador do banner do carrossel {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Ao criar predefinições do visualizador de banner do carrossel, a alteração do estilo dos pontos de acesso pode ser acessada da seguinte maneira:

|  | **Descrição** | **Ações** |
|---|---|---|
| **Ícone do ponto de acesso** | Alterar o ícone usado para ponto de acesso | Para alterar a imagem do ícone do ponto de acesso, na guia **[!UICONTROL Aparência]**, em **[!UICONTROL Componente selecionado]**, toque em **[!UICONTROL ImageMapEffect]**. Em **[!UICONTROL Ícone]**, selecione **[!UICONTROL Plano de fundo]** e, no campo **[!UICONTROL Imagem]**, navegue até a imagem de plano de fundo desejada. |

## Ativar ou desativar as predefinições do visualizador do Dynamic Media {#activating-or-deactivating-viewer-presets}

As Predefinições do visualizador disponíveis na interface do usuário dependem de quais estão ativas no modo Autor. Por padrão, uma predefinição do visualizador é *On* depois de criá-la. Se você desativar a predefinição, ela não será exibida no modo Autor. Se a predefinição for publicada. ele sempre será publicado independentemente de estar ligado ou desligado. Talvez você queira desativar as predefinições do visualizador se a lista se tornar muito difícil ou se não quiser que uma predefinição do visualizador seja disponibilizada para uso.

**Para ativar ou desativar as predefinições** do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.
1. Na página **[!UICONTROL Predefinição do visualizador]**, no cabeçalho da coluna **[!UICONTROL Estado]**, toque no botão para ativar ou desativar uma predefinição do visualizador.

   As predefinições do visualizador ativadas têm o botão de alternância exibido à direita, dentro de uma caixa azul; as predefinições do visualizador desativadas têm o botão de alternância exibido à esquerda, dentro de uma caixa cinza-claro.

## Publicar predefinições do visualizador do Dynamic Media {#publishing-viewer-presets}

Ativar (ou ativar *Ativado*) o estado de uma predefinição do visualizador significa que ela está visível no componente Dynamic Media, no componente Mídia interativa e sempre que você exibe um ativo.

No entanto, para fornecer um ativo com uma predefinição do visualizador, a predefinição do visualizador também deve ser publicada. Todas as predefinições do visualizador devem ser ativadas *e* publicadas para obter o URL ou código incorporado de um ativo. Ative e publique todas as predefinições do visualizador prontas para uso que acompanham o Dynamic Media. As predefinições do visualizador personalizado criadas e adicionadas são ativadas automaticamente, mas também devem ser publicadas.

Consulte [Ativando ou desativando predefinições do visualizador](#activating-or-deactivating-viewer-presets).

Consulte também [Visualização de ativos](previewing-assets.md).

**Para publicar predefinições** do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.
1. Selecione uma ou mais predefinições do visualizador que você deseja publicar.
1. Na barra de ferramentas, toque no ícone **[!UICONTROL Publish]**.

## Classificação das predefinições do visualizador do Dynamic Media {#sorting-viewer-presets}

**Para classificar as predefinições** do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, no painel à esquerda, toque em **Ferramentas** (ícone de martelo) **[!UICONTROL > Ativos > Predefinições do visualizador]**.
1. Clique em **[!UICONTROL Título da predefinição]**, **[!UICONTROL Tipo]**, **[!UICONTROL Publicado]** ou **[!UICONTROL Estado]** para classificar pelo cabeçalho da coluna. Por exemplo, clique em **[!UICONTROL Tipo]** para classificar os tipos de predefinição do visualizador em ordem alfabética ou não.

## Editar predefinições do visualizador do Dynamic Media {#editing-viewer-presets}

Observe que a edição de qualquer *predefinições predefinidas e predefinidas do visualizador* não é um cenário suportado. Se você editar uma predefinição do visualizador pronta para uso, será solicitado que ela seja salva com um novo nome.

**Para editar as predefinições** do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.
1. Selecione uma predefinição marcando a caixa à esquerda do título da predefinição do visualizador.
1. Na barra de ferramentas, toque em **[!UICONTROL Editar]**.
1. Na página **[!UICONTROL Editar predefinição do visualizador]** faça as alterações desejadas na predefinição do visualizador.
1. Faça uma das seguintes opções:

   * Toque em **[!UICONTROL Salvar]** para salvar suas alterações e retornar à página **[!UICONTROL Predefinição do visualizador]**.
   * Toque em **[!UICONTROL Cancelar]** para evitar alterações feitas e retornar à página **[!UICONTROL Predefinição do visualizador]**.

## Excluindo predefinições personalizadas do visualizador do Dynamic Media {#deleting-custom-viewer-presets}

É possível excluir as Predefinições do visualizador que você criou e adicionou ao Dynamic Media.

**Para excluir predefinições** personalizadas do visualizador do Dynamic Media:

1. No canto superior esquerdo do AEM, toque no logotipo do AEM e, em seguida, no painel à esquerda, toque em **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]**.
1. Na página **[!UICONTROL Predefinições do visualizador]**, marque um **[!UICONTROL Título da predefinição]** e toque no ícone **[!UICONTROL Lixeira]**.
1. Toque em **[!UICONTROL Excluir]**.

## Aplicar uma predefinição do visualizador do Dynamic Media a um ativo {#applying-a-viewer-preset-to-an-asset}

Se já tiver publicado o ativo e o visualizador selecionado, os botões **[!UICONTROL URL]** e **[!UICONTROL Incorporar]** aparecerão depois de selecionar uma predefinição do visualizador.

**Para aplicar uma predefinição do visualizador do Dynamic Media a um ativo**:

1. Abra o ativo e, próximo ao canto superior esquerdo da página, toque no menu suspenso e selecione **[!UICONTROL Visualizadores]**.

   >[!NOTE]
   >
   >Se já tiver publicado o ativo e o visualizador selecionado, os botões **[!UICONTROL URL]** e **[!UICONTROL Incorporar]** aparecerão depois de selecionar uma predefinição do visualizador.

1. Selecione uma predefinição do visualizador no painel esquerdo para aplicá-la ao ativo.

   Você pode [copiar o URL para compartilhar](linking-urls-to-yourwebapplication.md) com outros usuários.

## Fornecer ativos com predefinições do visualizador do Dynamic Media {#delivering-assets-with-viewer-presets}

Para obter os URLs das Predefinições do visualizador, consulte [Vincular URLs à sua aplicação web](linking-urls-to-yourwebapplication.md). Consulte também [Incorporação do visualizador de vídeo em uma página da Web](embed-code.md).

Se você estiver usando o AEM como o WCM, é possível adicionar ativos usando as predefinições do visualizador diretamente na página. Consulte [Adicionar ativos Dynamic Media às páginas](adding-dynamic-media-assets-to-pages.md).
