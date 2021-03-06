---
title: Adição de ativos do Dynamic Media a páginas
seo-title: Adição de ativos do Dynamic Media a páginas
description: Para adicionar a funcionalidade de mídia dinâmica aos recursos que você usa nos seus sites, é possível adicionar o componente Mídia dinâmica ou Mídia interativa diretamente na página.
seo-description: Para adicionar a funcionalidade de mídia dinâmica aos recursos que você usa nos seus sites, é possível adicionar o componente Mídia dinâmica ou Mídia interativa diretamente na página.
uuid: 650d0867-a079-4936-a466-55b7a30803a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 331f4980-5193-4546-a22e-f27e38bb8250
translation-type: tm+mt
source-git-commit: 44fb6e0ae344111385be844dfad1c6618c9209f0
workflow-type: tm+mt
source-wordcount: '1718'
ht-degree: 56%

---


# Adição de ativos do Dynamic Media a páginas{#adding-dynamic-media-assets-to-pages}

Para adicionar a funcionalidade do Dynamic Media aos ativos usados em seus sites, você pode adicionar o componente **[!UICONTROL Dynamic Media]** ou **[!UICONTROL Interative Media]** diretamente na página. Para fazer isso, entre no modo [!UICONTROL Design] e ative os componentes de mídia dinâmica. Em seguida, adicione esses componentes à página e adicionar ativos ao componente. A mídia dinâmica e os componentes de mídia interativa são inteligentes: eles sabem se você está adicionando uma imagem ou um vídeo, e as opções disponíveis mudam de acordo.

Você adiciona ativos de mídia dinâmica diretamente à página se estiver usando AEM como seu WCM.

>[!NOTE]
>
>Os mapas de imagem estão disponíveis imediatamente para banners de carrossel.

## Adicionar um componente Dynamic Media a uma página {#adding-a-dynamic-media-component-to-a-page}

Adicionar o componente [!UICONTROL Dynamic Media] ou [!UICONTROL Interative Media] a uma página é o mesmo que adicionar um componente a qualquer página. Os componentes [!UICONTROL Dynamic Media] e [!UICONTROL Interative Media] são descritos detalhadamente nas seções a seguir.

Para adicionar um componente/visualizador de mídia dinâmica a uma página:

1. No AEM, abra a página à qual você deseja adicionar o componente Mídia dinâmica.
1. Se nenhum componente Dynamic Media estiver disponível, clique na régua no [!UICONTROL Sidekick] para entrar no modo **[!UICONTROL Design]**, clique em **[!UICONTROL Editar]** parsys e selecione **[!UICONTROL Dynamic Media]** para disponibilizar os componentes Dynamic Media.

   >[!NOTE]
   >
   >Para obter mais informações, Consulte [Configuração dos componentes no modo de Design](/help/sites-authoring/default-components-designmode.md).

1. Volte para o modo **[!UICONTROL Editar]** clicando no ícone de lápis no [!UICONTROL Sidekick].
1. Arraste o componente **[!UICONTROL Dynamic Media]** ou **[!UICONTROL Interative Media]** do grupo **[!UICONTROL Outros]** no sidekick para a página no local desejado.
1. Clique em **[!UICONTROL Editar]** para abrir o componente.
1. [](#dynamic-media-component)Edite o componente conforme necessário e clique em **[!UICONTROL OK]** para salvar as alterações.

## Componentes de mídia dinâmica {#dynamic-media-components}

[!UICONTROL A Dynamic ] Media e a  [!UICONTROL Interative ] Media estão disponíveis no   Sidekickunder  **[!UICONTROL Dynamic Media]**. Você usa o componente **[!UICONTROL Mídia interativa]** para quaisquer ativos interativos, como vídeo interativo, imagens interativas ou conjuntos de carrossel. Para todos os outros componentes de mídia dinâmica, use o componente **[!UICONTROL Mídia dinâmica]**.

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>Esses componentes não estão disponíveis por padrão e precisam ser selecionados no modo de Design antes de serem usados. [Depois que eles forem disponibilizados no modo de Design](/help/sites-authoring/default-components-designmode.md), você poderá adicionar os componentes à sua página como faria com qualquer outro componente do AEM.

### Componente Mídia dinâmica {#dynamic-media-component}

O componente Dynamic Media é inteligente — dependendo se você adicionar uma imagem ou um vídeo, você terá várias opções. O componente oferece suporte a predefinições de imagem, visualizadores baseados em imagem, como conjuntos de imagens, conjuntos de rotação, conjuntos de mídia mista e vídeo. Além disso, o visualizador responde. Ou seja, o tamanho da tela muda automaticamente com base no tamanho da tela. Todos os visualizadores são baseados em HTML5.

>[!NOTE]
>
>Quando você adicionar o componente [!UICONTROL Dynamic Media] e **[!UICONTROL Configurações do Dynamic Media]** estiver em branco ou não puder adicionar um ativo corretamente, verifique o seguinte:
>
>* Você [ativou a Mídia dinâmica](/help/assets/config-dynamic.md). As mídias dinâmicas são desativadas por padrão.
>* A imagem tem um arquivo tiff de pirâmide. As imagens importadas antes de a mídia dinâmica ser ativada não possuem um arquivo tiff de pirâmide.

>



#### Ao trabalhar com imagens {#when-working-with-images}

O componente [!UICONTROL Dynamic Media] permite que você adicione imagens dinâmicas, incluindo conjuntos de imagens, conjuntos de rotação e conjuntos de mídia mista. Você pode ampliar, reduzir e, se aplicável, transformar uma imagem em um conjunto de giro ou selecionar uma imagem de outro tipo de conjunto.

Você também pode configurar a predefinição do visualizador, a predefinição da imagem ou o formato da imagem diretamente no componente. Para tornar uma imagem responsiva, você pode definir os pontos de interrupção ou aplicar uma predefinição de imagem responsiva.

![chlimage_1-72](assets/chlimage_1-72.png)

Você pode editar as seguintes configurações do Dynamic Media clicando em **[!UICONTROL Editar]** no componente e clicando na guia **[!UICONTROL Configurações do Dynamic Media]**.

![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>Por padrão, o componente de imagem do Dynamic Media é adaptável. Se desejar torná-lo um tamanho fixo, defina-o no componente na guia **[!UICONTROL Avançado]** com as propriedades **[!UICONTROL Largura]** e **[!UICONTROL Altura]**.

**[!UICONTROL Predefinição]**  do visualizador - selecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições do visualizador](/help/assets/managing-viewer-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

Essa será a única opção disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia. As predefinições do visualizador exibidas também são inteligentes - somente as predefinições do visualizador relevantes são exibidas.

**[!UICONTROL Predefinição]**  de imagem - selecione uma predefinição de imagem existente no menu suspenso. Se a predefinição de imagem que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

**[!UICONTROL Modificadores]**  de imagem - É possível alterar os efeitos de imagem fornecendo comandos de imagem adicionais. Estes estão descritos em [Gerenciar predefinições de imagens](/help/assets/managing-viewer-presets.md) e [Referência de comando](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

**[!UICONTROL Pontos de interrupção]**  - se você estiver usando esse ativo em um site responsivo, é necessário adicionar os pontos de interrupção da página. Os pontos de interrupção da imagem precisam ser separados por vírgulas (,). Essa opção funciona quando não há altura ou largura definida em uma predefinição de imagem.

Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

Você pode editar as seguintes [!UICONTROL Configurações avançadas] clicando em **[!UICONTROL Editar]** no componente.

**[!UICONTROL Título]**  - Altere o título da imagem.

**[!UICONTROL Texto]**  alternativo - Adicione um título à imagem para os usuários que tiverem gráficos desativados.

Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

**[!UICONTROL URL, Abrir]**  - você pode definir um ativo de para abrir um link. Defina **[!UICONTROL URL]** e **[!UICONTROL Abrir em]** para indicar se deseja que ele seja aberto na mesma janela ou em uma nova janela.

Essa opção não estará disponível se você estiver visualizando conjuntos de imagens, conjuntos de rotação ou conjuntos de mix de mídia.

**[!UICONTROL Largura e altura]**  - insira o valor em pixels se desejar que a imagem tenha um tamanho fixo. Deixar esses valores em branco torna o recurso adaptável.

#### Ao trabalhar com vídeo {#when-working-with-video}

Use o componente [!UICONTROL Dynamic Media] para adicionar vídeo dinâmico às suas páginas da Web. Ao editar o componente, você pode optar por usar uma predefinição de visualizador de vídeo predefinida para reproduzir o vídeo na página.

![chlimage_1-74](assets/chlimage_1-74.png)

Você pode editar as seguintes [!UICONTROL Configurações do Dynamic Media] clicando em **[!UICONTROL Editar]** no componente.

>[!NOTE]
>
>Por padrão, o componente de vídeo Mídia dinâmica é adaptável. Se desejar torná-lo um tamanho fixo, defina-o no componente com **[!UICONTROL Largura]** e **[!UICONTROL Altura]** na guia **[!UICONTROL Avançado]**.

**[!UICONTROL Predefinição]**  do visualizador - selecione uma predefinição do visualizador de vídeo existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições do visualizador](/help/assets/managing-viewer-presets.md).

Você pode editar as seguintes configurações de [!UICONTROL Avançado] clicando em **[!UICONTROL Editar]** no componente.

**[!UICONTROL Título]**  - Altere o título do vídeo.

**[!UICONTROL Largura e altura]**  - insira o valor em pixels se desejar que o vídeo tenha um tamanho fixo. Deixar esses valores em branco faz com ele que seja adaptável.

#### Como fornecer vídeos seguros {#how-to-delivery-secure-video}

No AEM 6.2, ao instalar [FP-13480](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq620/featurepack/cq-6.2.0-featurepack-13480), você pode controlar se um vídeo é entregue por meio de uma conexão SSL segura (HTTPS) ou por uma conexão não segura (HTTP). Por padrão, o protocolo de entrega de vídeo é herdado automaticamente do protocolo da página da web de incorporação. Se a página da web for carregada via HTTPS, o vídeo também será entregue via HTTPS. E vice-versa, se a página da web estiver em HTTP, o vídeo será entregue via HTTP. Na maioria dos casos, esse comportamento padrão é satisfatório, e não há necessidade de fazer alterações na configuração. No entanto, você pode substituir esse comportamento padrão anexando `VideoPlayer.ssl=on` ao final de um caminho de URL ou à lista de outros parâmetros de configuração do visualizador em um trecho de código de incorporação, para forçar a entrega segura de vídeos.

Para obter mais informações sobre a entrega segura de vídeos e o uso do atributo de configuração `VideoPlayer.ssl` no caminho do URL, consulte [Entrega de vídeo seguro](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-viewer-20-securevideodelivery.html) no Guia de referência de visualizadores. Além do visualizador de vídeo, o delivery de vídeo seguro está disponível para o visualizador de mídia mista e o visualizador de vídeo interativo.

### Componente Mídia interativa {#interactive-media-component}

O componente Mídia interativa é para ativos que possuem interatividade em pontos de acesso ou mapas de imagem. Se você tiver uma imagem interativa, um vídeo interativo ou um banner de carrossel, use o componente **[!UICONTROL Mídia interativa]**.

O componente [!UICONTROL Interative Media] é inteligente - dependendo se você adicionar uma imagem ou um vídeo, você terá várias opções. Além disso, o visualizador responde. Ou seja, o tamanho da tela muda automaticamente com base no tamanho da tela. Todos os visualizadores são visualizadores baseados em HTML5.

![chlimage_1-75](assets/chlimage_1-75.png)

É possível editar as seguintes configurações **[!UICONTROL Gerais]** clicando em **[!UICONTROL Editar]** no componente.

**[!UICONTROL Predefinição]**  do visualizador - selecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. As Predefinições do visualizador devem ser publicadas para poderem ser usadas. Consulte Gerenciar predefinições do visualizador.

**[!UICONTROL Título]**  - Altere o título do vídeo.

**[!UICONTROL Largura e altura]**  - insira o valor em pixels se desejar que o vídeo tenha um tamanho fixo. Deixar esses valores em branco faz com ele que seja adaptável.

É possível editar as seguintes configurações de **[!UICONTROL Adicionar ao carrinho]** clicando em **[!UICONTROL Editar]** no componente.

**[!UICONTROL Mostrar ativo]**  do produto - por padrão, esse valor é selecionado. O ativo do produto mostra uma imagem do produto, conforme definido no módulo Comércio. Limpe a marca de seleção para não mostrar o ativo do produto.

**[!UICONTROL Mostrar preço]**  do produto - Por padrão, esse valor é selecionado. O preço do produto mostra o preço do item, conforme definido no módulo Comércio. Limpe a marca de seleção para não mostrar o preço do produto.

**[!UICONTROL Mostrar formulário]**  do produto - Por padrão, esse valor não está selecionado. O Formulário de produto inclui quaisquer variantes de produto, como tamanho e cor. Limpe a marca de seleção para não mostrar as variantes do produto.
