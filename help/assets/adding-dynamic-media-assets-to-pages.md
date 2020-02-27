---
title: Adição de ativos de Mídia dinâmica a páginas
seo-title: Adição de ativos de Mídia dinâmica a páginas
description: Como adicionar componentes do Dynamic Media a uma página no AEM
seo-description: Como adicionar componentes do Dynamic Media a uma página no AEM
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6

---


# Adição de ativos de Mídia dinâmica a páginas {#adding-dynamic-media-assets-to-pages}

To add the dynamic media functionality to assets you use on your websites, you can add the **Dynamic Media** or **Interactive Media** component directly on the page. Para fazer isso, entre no modo Layout e ative os componentes de mídia dinâmica. Em seguida, adicione esses componentes à página e adicionar ativos ao componente. A mídia dinâmica e os componentes de mídia interativa são inteligentes: eles sabem se você está adicionando uma imagem ou um vídeo, e as opções disponíveis mudam de acordo.

Você adiciona ativos de mídia dinâmica diretamente à página se estiver usando o AEM como seu WCM. Se estiver usando um dispositivo de terceiros no WCM, [vincule](linking-urls-to-yourwebapplication.md) ou [incorpore](embed-code.md) os ativos. Para obter um site responsivo de terceiros, consulte [Fornecer imagens otimizadas para um site responsivo](responsive-site.md).

>[!NOTE]
>
>Você deve publicar ativos antes de adicioná-los às páginas no AEM. See [Publishing Dynamic Media Assets](publishing-dynamicmedia-assets.md).

## Adding a Dynamic Media component to a page {#adding-a-dynamic-media-component-to-a-page}

Adicionar o componente Mídia dinâmica ou Mídia interativa a uma página é o mesmo que adicionar um componente a qualquer página. Os componentes Mídia dinâmica e Mídia interativa estão descritos em detalhes nas seções a seguir.

>[!NOTE]
>
>Se houver um componente de Mídia dinâmica, um componente de Mídia interativa ou ambos em uma página da Web acessada por um usuário com permissões somente leitura, a página será quebrada e os componentes não serão renderizados corretamente. O motivo é que a página é reconstruída para garantir que as propriedades dos componentes sejam boas e que quaisquer ativos e configurações referenciadas sejam acessíveis. A página é renderizada novamente, fazendo com que os componentes se quebrem; o respectivo código de componente na página não pode ser renderizado novamente devido ao acesso somente leitura do usuário.
>  
>Para evitar esse problema, verifique se os usuários do AEM Sites têm as permissões necessárias para acessar os ativos.

1. No AEM, abra a página onde deseja adicionar o componente Mídia dinâmica ou Mídia interativa.
1. No painel esquerdo, clique no ícone **[!UICONTROL Componentes]** e filtre para **[!UICONTROL Dynamic Media]**. Se nenhum componente do Dynamic Media estiver disponível, será necessário ativar os componentes do Dynamic Media. Consulte [Edição de modelos](/help/sites-authoring/templates.md#editing-templates-template-authors) de página para obter mais informações.

   ![chlimage_1-538](assets/chlimage_1-537.png)

1. Arraste o componente **[!UICONTROL Mídia]** dinâmica ou Mídia **** interativa até a página no local desejado.
1. Clique na caixa azul ao redor do componente e toque no ícone **[!UICONTROL Configuração]** (chave).
1. [Edite os componentes](#dynamic-media-components) conforme necessário e clique na marca de seleção para salvar as alterações.

## Localização de componentes do Dynamic Media {#localizing-dynamic-media-components}

Você pode localizar componentes do Dynamic Media de uma das duas maneiras:

* Em uma página da Web no Sites, abra **[!UICONTROL Propriedades]** e selecione a guia **[!UICONTROL Avançado]**. Selecione o idioma desejado para localização.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* No seletor do site, selecione a página ou o grupo de páginas desejado. Toque em **[!UICONTROL Propriedades]** e selecione a guia **[!UICONTROL Avançado]** . Selecione o idioma desejado para localização.

   >[!NOTE]
   >
   >Observe que nem todos os idiomas disponíveis no menu **[!UICONTROL Idioma]** têm tokens atribuídos no momento.

## Dynamic Media components {#dynamic-media-components}

O Dynamic Media e o Interative Media estão disponíveis na guia [!UICONTROL Dynamic Media] em [!UICONTROL Components]. Use o componente Interative Media] para qualquer ativo interativo, como vídeo interativo, imagens interativas ou conjuntos de carrossel. Para todos os outros componentes de mídia dinâmica, use o componente Mídia dinâmica.

>[!NOTE]
>
>Esses componentes não estão disponíveis por padrão e precisam ser disponibilizados pelo editor de modelos antes de usar. [Depois que eles forem disponibilizados](/help/sites-authoring/templates.md#editing-templates-template-authors)no editor de modelos, você poderá adicionar os componentes à sua página como faria com qualquer outro componente AEM.

![chlimage_1-539](assets/chlimage_1-539.png)

### Componente Mídia dinâmica {#dynamic-media-component}

O componente Dynamic Media é inteligente — dependendo se você adicionar uma imagem ou um vídeo, você terá várias opções. O componente oferece suporte a predefinições de imagem, visualizadores baseados em imagem, como conjuntos de imagens, conjuntos de rotação, conjuntos de mídia mista e vídeo. Além disso, o visualizador responde. Ou seja, o tamanho da tela muda automaticamente com base no tamanho da tela. Todos são visualizadores HTML5.

>[!NOTE]
>
>Se houver um componente de Mídia dinâmica, um componente de Mídia interativa ou ambos em uma página da Web acessada por um usuário com permissões somente leitura, a página será quebrada e os componentes não serão renderizados corretamente. O motivo é que a página é reconstruída para garantir que as propriedades dos componentes sejam boas e que quaisquer ativos e configurações referenciadas sejam acessíveis. A página é renderizada novamente, fazendo com que os componentes se quebrem; o respectivo código de componente na página não pode ser renderizado novamente devido ao acesso somente leitura do usuário.
>  
>Para evitar esse problema, verifique se os usuários do AEM Sites têm as permissões necessárias para acessar os ativos.

>[!NOTE]
>
>Quando você adiciona o componente Mídia dinâmica e as **[!UICONTROL Configurações de mídia dinâmica]** estão em branco ou não é possível adicionar um ativo corretamente, verifique o seguinte:
>
>* Você [ativou a Mídia dinâmica](config-dynamic.md). As mídias dinâmicas são desativadas por padrão.
>* A imagem tem um arquivo tiff de pirâmide. As imagens importadas antes de a mídia dinâmica ser ativada não possuem um arquivo tiff de pirâmide.
>



#### Ao trabalhar com imagens {#when-working-with-images}

O componente Mídia dinâmica permite adicionar imagens dinâmicas, incluindo conjuntos de imagens, conjuntos de rotação e conjuntos de mídia mista. Você pode ampliar, reduzir e, se aplicável, transformar uma imagem em um conjunto de giro ou selecionar uma imagem de outro tipo de conjunto.

Você também pode configurar a predefinição do visualizador, a predefinição da imagem ou o formato da imagem diretamente no componente. Para tornar uma imagem responsiva, você pode definir os pontos de interrupção ou aplicar uma predefinição de imagem responsiva.

You can edit the following Dynamic Media Settings by clicking the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Por padrão, o componente de imagem do Dynamic Media é adaptável. If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** settings.

* **[!UICONTROL Predefinição]**do visualizadorSelecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte Gerenciar predefinições do visualizador. Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.
Essa será a única opção disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia. As predefinições do visualizador exibidas também são inteligentes: apenas as predefinições relevantes do visualizador são exibidas.

* **[!UICONTROL Os modificadores do visualizador]** visualizadores assumem a forma de par name=value com um &amp; delimitador e permitem alterar os visualizadores conforme descrito no Guia de referência do visualizador. Um exemplo de um modificador do visualizador é post-erimage=img.jpg&amp;caption=text.vtt,1 que define uma imagem diferente para a miniatura do vídeo e associa um arquivo de legenda/legenda ao vídeo.

* **[!UICONTROL Predefinição]**de imagem Selecione uma predefinição de imagem existente no menu suspenso. Se a predefinição de imagem que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte Gerenciar predefinições de imagens. Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL Modificadores de imagem]**Você pode aplicar efeitos de imagem fornecendo comandos de imagem adicionais. Elas são descritas nas predefinições de imagem e na referência do Comando de disponibilização de imagem.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL Pontos de interrupção]**Se você estiver usando esse ativo em um site responsivo, precisará adicionar os pontos de interrupção da imagem. Os pontos de interrupção da imagem precisam ser separados por vírgulas (,). Essa opção funciona quando não há altura ou largura definida em uma predefinição de imagem.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.
You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Título]** Altere o título da imagem.

* **[!UICONTROL Texto]**alternativoAdicione um título à imagem para os usuários que tiverem gráficos desativados.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL URL, Abrir no]**Você pode definir um ativo para abrir um link. Defina o URL e, em Abrir em, indique se você deseja que ele abra na mesma janela ou em uma nova.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL Largura]** e **[!UICONTROL altura]** Insira o valor em pixels se desejar que a imagem tenha um tamanho fixo. Deixar esses valores em branco torna o recurso adaptável.

#### Ao trabalhar com vídeo {#when-working-with-video}

Use o componente Mídia dinâmica para adicionar vídeo dinâmico às páginas da Web. Ao editar o componente, você pode optar por usar uma predefinição de visualizador de vídeo predefinida para reproduzir o vídeo na página.

![chlimage_1-540](assets/chlimage_1-540.png)

You can edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Por padrão, o componente de vídeo Mídia dinâmica é adaptável. If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the [!UICONTROL Advanced] tab.

* **[!UICONTROL Predefinição]** do visualizadorSelecione uma predefinição do visualizador de vídeo existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte Gerenciar predefinições do visualizador.

* **[!UICONTROL Os modificadores do visualizador]** visualizadores assumem a forma de par nome=valor com um &amp; delimitador e permitem alterar os visualizadores conforme descrito no Guia de referência do Adobe Viewers. Um exemplo de um modificador do visualizador é post-erimage=img.jpg&amp;caption=text.vtt,1

   Com modificadores do visualizador, por exemplo, você pode fazer o seguinte:

   * Associar um arquivo de legenda a um vídeo [https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html)
   * Associar um arquivo de navegação a um vídeo [https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html)

You can edit the following [!UICONTROL Advanced Settings] by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Título]** Altere o título do vídeo.

* **[!UICONTROL Largura]** e **[!UICONTROL altura]** Insira o valor em pixels se desejar que o vídeo tenha um tamanho fixo. Deixar esses valores em branco faz com ele que seja adaptável.

#### Ao trabalhar com o Smart Crop {#when-working-with-smart-crop}

Use o componente Mídia dinâmica para adicionar ativos de imagem de Recorte inteligente às suas páginas da Web. Ao editar o componente, você pode optar por usar uma predefinição de visualizador de vídeo predefinida para reproduzir o vídeo na página.

Consulte também Perfis [de](image-profiles.md)imagem.

![dm-settings-smart-cut](assets/dm-settings-smart-crop.png)

You can edit the following [!UICONTROL Dynamic Media Settings] by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Por padrão, o componente de imagem do Dynamic Media é adaptável. Se desejar torná-lo de um tamanho fixo, defina-o no componente na guia [!UICONTROL Avançado] com a **[!UICONTROL Largura]** e a **[!UICONTROL Altura]**.

* **[!UICONTROL Modificadores de imagem]**Você pode aplicar efeitos de imagem fornecendo comandos de imagem adicionais. Elas são descritas nas predefinições de imagem e na referência do Comando de disponibilização de imagem.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

You can edit the following **[!UICONTROL Advanced]** settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Título]** Altere o título da imagem de Recorte inteligente.

* **[!UICONTROL Texto]**alternativoAdicione um título à imagem de recorte inteligente para os usuários que têm gráficos desativados.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL URL, Abrir no]**Você pode definir um ativo para abrir um link. Defina o URL e, em Abrir em, indique se você deseja que ele abra na mesma janela ou em uma nova.
Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

* **[!UICONTROL Altura** e **[!UICONTROL Largura]** Insira o valor em pixels se desejar que a imagem de corte inteligente tenha um tamanho fixo. Deixar esses valores em branco faz com ele que seja adaptável.

### Interactive Media component {#interactive-media-component}

O componente Mídia interativa é para ativos que possuem interatividade em pontos de acesso ou mapas de imagem. Se você tiver uma imagem interativa, um vídeo interativo ou um banner de carrossel, use o componente Mídia interativa.

O componente de Mídia interativa é inteligente — dependendo se você adicionar uma imagem ou um vídeo, você terá várias opções. Além disso, o visualizador é responsivo: o tamanho da tela muda automaticamente com base no tamanho da tela. Todos são visualizadores HTML5.

>[!NOTE]
>
>Se houver um componente de Mídia dinâmica, um componente de Mídia interativa ou ambos em uma página da Web acessada por um usuário com permissões somente leitura, a página será quebrada e os componentes não serão renderizados corretamente. O motivo é que a página é reconstruída para garantir que as propriedades dos componentes sejam boas e que quaisquer ativos e configurações referenciadas sejam acessíveis. A página é renderizada novamente, fazendo com que os componentes se quebrem; o respectivo código de componente na página não pode ser renderizado novamente devido ao acesso somente leitura do usuário.
> 
>Para evitar esse problema, verifique se os usuários do AEM Sites têm as permissões necessárias para acessar os ativos.

![chlimage_1-541](assets/chlimage_1-541.png)

É possível editar as seguintes configurações **[!UICONTROL Gerais]** clicando em **[!UICONTROL Editar]** no componente.

* **[!UICONTROL Predefinição]** do visualizadorSelecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. As Predefinições do visualizador devem ser publicadas para poderem ser usadas. Consulte Gerenciar predefinições do visualizador.

* **[!UICONTROL Título]** Altere o título do vídeo.

* **[!UICONTROL Largura]** e **[!UICONTROL altura]** Insira o valor em pixels se desejar que o vídeo tenha um tamanho fixo. Deixar esses valores em branco faz com ele que seja adaptável.

É possível editar as seguintes configurações de **[!UICONTROL Adicionar ao carrinho]** clicando em **[!UICONTROL Editar]** no componente.

* **[!UICONTROL Mostrar ativo]** do produto Por padrão, esse valor é selecionado. O ativo do produto mostra uma imagem do produto, conforme definido no módulo Comércio. Limpe a marca de seleção para não mostrar o ativo do produto.

* **[!UICONTROL Mostrar preço]** do produto Por padrão, esse valor é selecionado. O preço do produto mostra o preço do item, conforme definido no módulo Comércio. Limpe a marca de seleção para não mostrar o preço do produto.

* **[!UICONTROL Mostrar formulário]** do produto Por padrão, esse valor não está selecionado. O Formulário de produto inclui quaisquer variantes de produto, como tamanho e cor. Limpe a marca de seleção para não mostrar as variantes do produto.

### Componente de mídia panorâmica {#panoramic-media-component}

O componente de Mídia panorâmica é destinado aos ativos que são imagens panorâmicas esféricas. Essas imagens fornecem uma experiência de visualização de 360° de uma sala, propriedade, local ou paisagem. Para que uma imagem seja qualificada como um panorama esférico, ela deve ter um OU ambos os seguintes:

* Uma proporção largura/altura de 2:1.
* Marcado com as palavras-chave &quot;equirectangular&quot; ou (&quot;esférico&quot; + &quot;panorama&quot;) ou (&quot;esférico&quot; + &quot;panorâmico&quot;). Consulte [Uso de tags](/help/sites-authoring/tags.md).

Tanto a proporção quanto os critérios de palavra-chave se aplicam aos ativos panorâmicos para a página de detalhes do ativo e o componente WCM &quot;Mídia panorâmica&quot;.

![panorâmico-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Você pode editar a seguinte configuração tocando em **[!UICONTROL Configurar]** no componente.

* **[!UICONTROL Predefinição]** do visualizadorSelecione um visualizador existente no menu suspenso Predefinição do visualizador.

Se a predefinição do visualizador que você está procurando não estiver visível, verifique se ela foi publicada. É necessário publicar as predefinições do visualizador antes de usá-las. Consulte [Gerenciar predefinições do visualizador](managing-viewer-presets.md).

### Usar HTTP/2 para fornecer ativos de Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 é o novo protocolo da Web atualizado que melhora a maneira como os navegadores e servidores se comunicam. Fornece transferência de informações mais rápida e reduz a quantidade de poder de processamento necessário. A entrega de ativos de Dynamic Media pode estar acima de HTTP/2, o que oferece melhor resposta e tempo de carregamento.

Consulte Entrega [HTTP2 de conteúdo](http2.md) para obter detalhes completos sobre como começar a usar HTTP/2 com sua conta de Dynamic Media.

>[!MORELIKETHIS]
>
>* [Como entender o gerenciamento de cores com o AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Usar miniatura de vídeo personalizada com o AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Noções básicas sobre o Visualizador de ativos com o AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Usar vídeo interativo com o AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Usar o player de vídeo no AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Usar o ajuste de nitidez de imagem com o AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

