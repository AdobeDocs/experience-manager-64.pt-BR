---
title: Banners em carrossel
seo-title: Banners em carrossel
description: Saiba como trabalhar com banners de carrossel em mídia dinâmica
seo-description: Saiba como trabalhar com banners de carrossel em mídia dinâmica
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
exl-id: d2fdad3f-513b-4147-a7c6-a3c1b64dd6e3
feature: Banners em carrossel
role: User
source-git-commit: 76592d2714106f96184196b9e8db012801bf7c28
workflow-type: tm+mt
source-wordcount: '4749'
ht-degree: 4%

---

# Banners em carrossel {#carousel-banners}

Os banners em carrossel permitem que os profissionais de marketing determinem a conversão, criando facilmente conteúdo promocional giratório interativo e o entregando a qualquer tela.

Criar e modificar o conteúdo em destaque em banners promocionais pode ser demorado, limitando sua capacidade de publicar rapidamente novo conteúdo ou torná-lo mais direcionado. Os banners em carrossel permitem que você crie ou modifique rapidamente banners giratórios, adicione interatividade como hotspots vinculando a detalhes do produto ou recursos relacionados e os entregue a qualquer tela - permitindo que você traga novo conteúdo promocional para o mercado mais rápido.

Os banners de carrossel são designados por um banner com a palavra **CAROUSELSET**:

![chlimage_1-438](assets/chlimage_1-438.png)

Em seu site, um banner de carrossel pode ter a seguinte aparência:

![chlimage_1-439](assets/chlimage_1-439.png)

Aqui você pode navegar pelas imagens (clicando nos números). Além disso, os slides giram automaticamente com base em um intervalo de tempo que você pode personalizar. As imagens adicionadas no banner do carrossel são compatíveis com hotspots e mapas de imagem, onde os usuários podem tocar ou acessar um hiperlink ou acessar uma janela do Quickview.

Neste exemplo, um usuário tocou ou clicou em um mapa de imagem e acessou a janela Quickview para obter luvas:

![chlimage_1-440](assets/chlimage_1-440.png)

## Veja como os banners em carrossel são criados {#watch-how-carousel-banners-are-created}

Assista a uma apresentação de 10 minutos e 33 segundos sobre [como os banners de carrossel são criados](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Você também aprenderá a visualizar, editar e fornecer banners em carrossel.

>[!NOTE]
>
>Usuários não administrativos devem ser adicionados ao grupo **dam-users** para poderem criar ou editar banners de carrossel. Se tiver problemas ao criar ou editar, consulte o administrador do sistema que pode adicioná-lo ao grupo **dam-users**.

## Início rápido: Banners em carrossel {#quick-start-carousel-banners}

Para ativar e executar rapidamente:

1. [Identificar hotspots e variáveis de mapa de imagem](#identifying-hotspot-and-image-map-variables)  (somente para clientes que usam AEM Assets + Dynamic Media)

   Comece identificando as variáveis dinâmicas usadas pela implementação existente do Quickview, para que você possa inserir os pontos de acesso e os dados do mapa de imagem corretamente durante o processo de criação do banner de carrossel no AEM Assets.

   >[!NOTE]
   >
   >Se você for um cliente do AEM Sites ou do Ecommerce, poderá usar o recurso integrado para navegar até páginas de produtos e pesquisar os SKUs existentes no catálogo de produtos. Não é necessário inserir manualmente as variáveis de ponto de acesso ou mapa de imagem. Consulte as informações sobre [como configurar o eCommerce](/help/sites-administering/generic.md).
   >
   >Se você for um cliente do AEM Assets e Dynamic Media, insira manualmente os dados dos pontos de acesso e mapas de imagem e integre o URL publicado ou o código Incorporado ao seu sistema de gerenciamento de conteúdo de terceiros.

1. Opcional: [crie uma predefinição do visualizador Conjunto de carrossel](managing-viewer-presets.md), conforme necessário.

   Se você for um administrador, poderá personalizar o comportamento e a aparência do carrossel criando sua própria predefinição do visualizador do carrossel. O principal benefício é que você pode reutilizar essa predefinição do visualizador personalizado para vários carrosséis. No entanto, os usuários também têm a opção de personalizar o comportamento e a aparência do carrossel diretamente durante a criação do carrossel. Essa é a abordagem preferida quando você deseja um design muito específico para um determinado carrossel.

1. [Faça upload de um banner de imagem](#uploading-image-banners).

   Carregue banners de imagem que você deseja tornar interativos.

1. [Criar um conjunto de carrossel](#creating-carousel-sets).

   Em Conjuntos de carrosséis, os usuários navegam por imagens de banner e tocam em pontos de acesso ou mapas de imagem para acessar conteúdo relevante.

   Para criar um Conjunto de carrossel no Assets, toque em **[!UICONTROL Criar]** e selecione **[!UICONTROL Conjuntos de carrossel]**. Adicione ativos a slides e toque em **[!UICONTROL Salvar]**. Além disso, edite a aparência e o comportamento do carrossel diretamente no editor.

1. [Adicione pontos de acesso ou mapas de imagem a um banner de imagem.](#adding-hotspots-or-image-maps-to-an-image-banner)

   Adicione um ou mais pontos de acesso ou mapas de imagem a um banner de imagem e associe cada um a uma ação, como um link, uma visualização rápida ou um fragmento de experiência. Após adicionar pontos de acesso ou mapas de imagem, conclua esta tarefa publicando o conjunto de carrossel. A publicação cria o código incorporado que pode ser usado para copiar e aplicar à página de aterrissagem do site.

   Consulte [(Opcional) Visualização dos banners do carrossel](#optional-previewing-carousel-banners) - Opcional. Se desejar, é possível visualizar uma representação do conjunto de carrossel e testar sua interatividade.

1. [Publique banners em carrossel.](#publishing-carousel-banners)

   Você publica um Conjunto de carrossel como faria com qualquer ativo. No Assets, navegue até o Conjunto de carrossel e selecione-o e toque ou toque em **[!UICONTROL Publicar]**. A publicação de um Conjunto de carrossel ativa o URL e a cadeia de caracteres de inserção.

1. Faça uma das seguintes opções:

   * [Adicionar um banner de carrossel à ](#adding-a-carousel-banner-to-your-website-page) página do site. Você pode adicionar a URL do banner de carrossel ou incorporar o código que você copiou na página do site.

      * [Integre o banner do carrossel a um Quickview](#integrating-the-carousel-banner-with-an-existing-quickview) existente. Se você estiver usando um sistema de gerenciamento de conteúdo da Web de terceiros, será necessário integrar o novo banner de carrossel com a implementação existente do Quickview em seu site.
   * [Adicione um banner de carrossel ao seu site no ](adding-dynamic-media-assets-to-pages.md) AEM. Se você for um cliente do AEM Sites, poderá adicionar o conjunto de carrossel diretamente à página no AEM, usando o componente Mídia interativa .


Se precisar editar Conjuntos de carrossel, consulte [editar Conjuntos de carrossel](#editing-carousel-sets). Além disso, você pode visualizar e editar [Propriedades do Conjunto de carrossel](/help/assets/managing-assets-touch-ui.md#editing-properties).

## Identificação das variáveis de mapa de imagem e ponto de acesso {#identifying-hotspot-and-image-map-variables}

Comece identificando variáveis dinâmicas usadas pela implementação existente do Quickview, para que você possa inserir pontos de acesso ou dados de mapa de imagem corretamente durante o processo de criação do conjunto de carrossel no AEM Assets.

Quando você adiciona pontos de acesso ou mapas de imagem a uma imagem de banner no AEM Assets, é necessário atribuir um SKU e variáveis adicionais opcionais a cada ponto de acesso ou mapa de imagem. Essas variáveis são usadas posteriormente para corresponder pontos de acesso ou mapas de imagem com conteúdo do Quickview.

>[!NOTE]
>
>Se você for um cliente do AEM Sites e/ou AEM Ecommerce, pule esta etapa. Não é necessário identificar manualmente os pontos de acesso ou as variáveis do mapa de imagem; você pode usar a integração com o Ecommerce para integração de produto. Consulte as informações sobre [como configurar o eCommerce](/help/sites-administering/generic.md). Além disso, você pode usar o componente Interativo e adicioná-lo à sua página da Web.
>
>Se você for um cliente de AEM Assets ou Mídia, publique o URL ou código Incorporado e faça a integração com seu sistema de gerenciamento de conteúdo de terceiros e identifique pontos de acesso e mapas de imagem manualmente.

É importante identificar corretamente o número e o tipo de variáveis a serem associadas ao ponto de acesso ou aos dados do mapa de imagem. Cada ponto de acesso ou mapa de imagem adicionado a uma imagem de banner deve ter informações suficientes para identificar inequivocamente o produto no sistema de back-end existente. Ao mesmo tempo, cada ponto de acesso ou mapa de imagem não deve incluir mais dados do que o necessário. O motivo é que isso tornaria o processo de entrada de dados excessivamente complexo e o gerenciamento contínuo de hotspots ou mapas de imagem mais propenso a erros.

Há diferentes maneiras de identificar um conjunto de variáveis a serem usadas para pontos de acesso ou dados de mapa de imagem.

Às vezes, pode ser suficiente consultar especialistas de TI responsáveis pela implementação atual do Quickview, pois eles provavelmente saberão qual é o conjunto mínimo de dados necessário para identificar o Quickview no sistema. No entanto, na maioria dos casos, também é possível simplesmente analisar o comportamento existente do código front-end.

A maioria das implementações do Quickview usa o seguinte paradigma:

* O usuário ativa um elemento da interface do usuário no site. Por exemplo, clicar em um botão **[!UICONTROL Exibição rápida]**.
* O site envia uma solicitação do Ajax para o backend para carregar os dados ou o conteúdo do Quickview, se necessário.
* Os dados do Quickview são traduzidos para o conteúdo em preparação para renderização na página da Web.
* Por fim, o código front-end renderiza visualmente esse conteúdo na tela.

A abordagem é visitar diferentes áreas do site existente onde o recurso Quickview é implementado, acionar o Quickview e capturar o URL Ajax enviado pela página da Web para carregar os dados ou o conteúdo do Quickview.

Normalmente, não há necessidade de usar ferramentas de depuração especializadas. Os navegadores modernos da Web apresentam inspetores da Web que fazem um trabalho adequado. A seguir estão alguns exemplos de navegadores da Web que incluem inspetores da Web:

* Para ver todas as solicitações HTTP de saída no Google Chrome, pressione F12 (Windows) ou Command-Option-I (Mac) para abrir o painel Ferramentas do Desenvolvedor e toque na guia **[!UICONTROL Rede]**.
* No Firefox, é possível ativar o plug-in do Firebug pressionando F12 (Windows) ou Command-Option-I (Mac) e usar a guia Net ou usar a ferramenta Inspetor integrada e a guia Rede.

Quando o monitoramento de rede estiver ativado no navegador, acione o Quickview na página.

Agora, encontre o URL do Ajax do Quickview no log de rede e copie o URL registrado para análise futura. Na maioria dos casos, quando você aciona o Quickview, há várias solicitações que são enviadas ao servidor. Normalmente, o URL de Ajax do Quickview é um dos primeiros na lista. Ela tem uma parte ou um caminho complexo da sequência de consulta e seu tipo MIME de resposta é `text/html`, `text/xml` ou `text/javascript`.

Durante esse processo, é importante visitar áreas diferentes de seu site, com categorias e tipos de produtos diferentes. O motivo é que os URLs do Quickview podem ter partes comuns para uma determinada categoria de site, mas são alteradas somente se você visitar uma área diferente do site.

No caso mais simples, a única parte variável no URL do Quickview é o SKU do produto. Nesse caso, o valor SKU é o único dado necessário para adicionar pontos de acesso ou mapas de imagem à imagem do banner.

No entanto, em casos complexos, o URL do Quickview tem elementos variáveis diferentes além do SKU, como ID da categoria, código de cor, código de tamanho e assim por diante. Nesses casos, cada elemento é uma variável separada no ponto de acesso ou na definição de dados do mapa de imagem no recurso de banner do carrossel.

Considere os exemplos a seguir de URLs do Quickview e seus pontos de acesso ou variáveis de mapa de imagem resultantes:

<table> 
 <tbody> 
  <tr> 
   <td>SKU único, encontrado na string de consulta.</td> 
   <td><p>Os URLs do Quickview registrados incluem o seguinte:</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>A única parte variável no URL é o valor do parâmetro da string de consulta <code>productId=</code> e é claramente um valor SKU. Portanto, nossos pontos de acesso ou mapas de imagem precisam apenas de campos SKU preenchidos com valores como <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU único, encontrado no caminho do URL.</td> 
   <td><p>Os URLs do Quickview registrados incluem o seguinte:</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>A parte variável está na última parte do caminho e se torna o valor SKU dos pontos de acesso/mapas de imagem:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU e ID de categoria na sequência de consulta.</td> 
   <td><p>Os URLs do Quickview registrados incluem o seguinte:</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>Nesse caso, há duas partes variáveis no URL. O SKU é armazenado no parâmetro <code>prodId</code> e a ID da categoria é armazenada no parâmetro <code>category=</code>.</p> <p>Dessa forma, as definições de ponto de acesso/mapa de imagem são pares. Ou seja, um valor SKU e uma variável adicional chamada <code>categoryId</code>. Os pares resultantes são os seguintes:</p> 
    <ul> 
     <li><p>O SKU é <strong><code>305466</code></strong> e <code>categoryId</code> é <code>1100004</code>.</p> </li> 
     <li><p>O SKU é <strong><code>310181</code></strong> e <code>categoryId</code> é <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>O SKU é <strong><code>308706</code></strong> e <code>categoryId</code> é <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Fazer upload de banners de imagem {#uploading-image-banners}

Se você já tiver carregado as imagens que deseja usar, avance para a próxima etapa, [Criação de conjuntos de carrossel](#creating-carousel-sets). Observe que as imagens usadas no carrossel devem ser carregadas após a ativação do Dynamic Media.

Para fazer upload de banners de imagem, consulte [Fazer upload de ativos](managing-assets-touch-ui.md).

## Criação de conjuntos de carrossel {#creating-carousel-sets}

>[!NOTE]
>
>Usuários não administrativos devem ser adicionados ao grupo **[!UICONTROL dam-users]** para poderem criar ou editar banners de carrossel. Se tiver problemas ao criar ou editar, consulte o administrador do sistema que pode adicioná-lo ao grupo **dam-users**.

**Para criar um Conjunto** de carrossel:

1. No Assets, navegue até a pasta onde deseja criar o Conjunto de carrossel e toque em **[!UICONTROL Criar > Conjunto de carrossel]**.
1. Na página **[!UICONTROL Editor de banner do carrossel]**, toque em **[!UICONTROL Toque para abrir o Seletor de ativos]** para selecionar a imagem do primeiro slide.

   Na página **[!UICONTROL Editor de banner de carrossel]** , siga um destes procedimentos:

   * Próximo ao canto superior esquerdo da página, toque no ícone **[!UICONTROL Adicionar slide]**.
   * Próximo ao meio da página, toque em **[!UICONTROL Toque para abrir o Seletor de ativos]**.

   Toque para selecionar os ativos que deseja incluir ao Conjunto de carrossel. Os ativos selecionados têm um ícone de marca de seleção sobre eles. Quando terminar, próximo ao canto superior direito da página, toque em **[!UICONTROL Selecionar]**.

   Com o Seletor de ativos, procure por ativos ao digitar uma palavra-chave e tocar em **[!UICONTROL Retornar]**. Aplique filtros para refinar os resultados da pesquisa. Filtre por caminho, coleção, tipo de arquivo e tag. Selecione o filtro e toque no ícone **[!UICONTROL Filtro]**, na barra de ferramentas. Altere a exibição ao tocar no ícone **[!UICONTROL Exibir]** e selecionar **[!UICONTROL Exibição de coluna]**, **[!UICONTROL Exibição de cartão]** ou **[!UICONTROL Exibição de lista]**.

   Consulte [Trabalhar com seletores](working-with-selectors.md) para obter mais informações.

1. Continue a adicionar slides até ter adicionado todas as imagens que deseja girar no Conjunto de carrossel.
1. (Opcional) Siga um destes procedimentos:

   * Se necessário, arraste os slides para reordenar as imagens na lista de definição.
   * Para excluir uma imagem, selecione-a e toque em **[!UICONTROL Excluir slide]** na barra de ferramentas.
   * Para aplicar uma predefinição, próximo ao canto superior direito da página, toque na lista suspensa predefinição e selecione uma predefinição para aplicar ao conjunto ao mesmo tempo.

   Para excluir um slide, toque no slide e em **[!UICONTROL Excluir slide]** na barra de ferramentas. Para mover um slide, toque no ícone do remetente e segure e mova-se para o local desejado.

1. Depois de ter adicionado as imagens nos slides, você pode adicionar um ponto de acesso, mapa de imagem ou ambos à sua imagem. Consulte [adicionar pontos de acesso ou mapas de imagem](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Você pode alterar o design visual e o comportamento dos conjuntos de carrossel tocando ou clicando nas guias Comportamento e Aparência e fazendo ajustes na aparência do seu banner de carrossel ou no comportamento dos componentes específicos. Consulte [gerenciar predefinições do visualizador](viewer-presets.md) para obter mais informações sobre como usar o editor do visualizador.

   >[!NOTE]
   >
   >Para banners de carrossel, as seguintes opções podem ser ajustadas:
   >* Duração que uma imagem exibe. Por padrão, cada imagem é exibida por 9 segundos.
   >* Animação. Por padrão, cada transição de slide está esmaecida. Você pode alterá-lo para uma transição de slide.
   >* Estilo dos botões. Os usuários podem girar pelos banners tocando em cada ponto ou número. Você pode alterar o local em que os botões de indicador definidos são exibidos (e se são numéricos ou de estilo pontilhado) e o tamanho deles.
   >* Altere o estilo de realce de um mapa de imagem ou o ícone usado para pontos de acesso.
   >* Antes de editar uma predefinição do visualizador, escolha o estilo do qual deseja basear a predefinição. Se não fizer isso, ao começar a editar a predefinição do visualizador, você perderá todas as alterações se decidir alterar para uma predefinição diferente.


   Você também pode visualizar como será o banner do carrossel. Consulte [(Opcional) Visualização de banners do carrossel](#optional-previewing-carousel-banners).

1. Toque em **[!UICONTROL Salvar]** quando terminar.

## Adicionar pontos de acesso ou mapas de imagem a um banner de imagem {#adding-hotspots-or-image-maps-to-an-image-banner}

Você pode adicionar pontos de acesso ou mapas de imagem a um banner usando o editor Conjunto de carrossel.

Ao adicionar pontos de acesso ou mapas de imagem, você pode defini-los como uma exibição pop-up do Quickview, como um hiperlink ou um Fragmento de experiência.

Consulte [Fragmentos de experiência](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Esteja ciente de que as ferramentas de compartilhamento de mídia social no Banner do carrossel não são compatíveis quando você incorpora o visualizador a um Fragmento de experiência. Para contornar isso, você pode usar ou criar predefinições do visualizador que não tenham ferramentas de compartilhamento de redes sociais. Essas predefinições do visualizador permitem que você as incorpore com êxito aos Fragmentos de experiência.

À medida que você adiciona pontos de acesso ou mapas de imagem a uma imagem, lembre-se de salvar seu trabalho. **** As  **** opções Undoand Redooptions, próximo ao canto superior direito da página, são compatíveis durante a sessão de criação/edição atual.

Quando terminar de criar o banner do carrossel, você pode usar opcionalmente **[!UICONTROL Preview]** para ver uma representação de como o banner do carrossel aparecerá para os clientes.

Consulte [(Opcional) Visualização de banners do carrossel](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Quando você adiciona pontos de acesso a uma imagem em um [Imagem interativa](interactive-images.md) ou um Banner de carrossel, as informações do ponto de acesso são armazenadas no mesmo local de metadados - em relação ao local da imagem - independentemente de ser uma Imagem interativa ou um Banner de carrossel. Essa funcionalidade significa que você pode reutilizar facilmente a mesma imagem, juntamente com os dados de ponto de acesso definidos, em qualquer um dos visualizadores.
>
>Esteja ciente, no entanto, de que os carrossel Banners suportam mapas de imagens em imagens que também podem conter pontos de acesso; uma Imagem interativa não. Lembre-se disso se você pretende criar uma Imagem interativa ou Banner de carrossel que usa a mesma imagem. Você pode criar Imagens interativas e Banners de carrossel usando cópias separadas da mesma imagem.

>[!NOTE]
>
>Se você estiver editando imagens interativas com pontos de acesso e recortar a imagem, seus pontos de acesso serão removidos.

**Para adicionar pontos de acesso a um banner** de imagem:

1. Em Ativos, navegue até o conjunto de carrossel que deseja tornar interativo.
1. Selecione o conjunto de carrossel e toque em **[!UICONTROL Editar]**.
1. No Editor do visualizador de carrossel, selecione o slide que deseja tornar interativo.
1. Próximo ao canto superior esquerdo da página, toque em **[!UICONTROL Ponto de acesso]** ou **[!UICONTROL Mapa de imagem]**.
1. Siga um destes procedimentos:

   * Para pontos de conexão: Na imagem, toque em um local onde deseja que o ponto de acesso apareça.
   * Para mapas de imagem: Na imagem, toque em e arraste de cima para a esquerda e de baixo para a direita para criar a área do mapa de imagem. É possível ajustar o tamanho do mapa de imagem arrastando os cantos.

   Se necessário, arraste o ponto de acesso ou o mapa de imagem para um novo local. Adicione pontos de acesso adicionais ou mapas de imagem, conforme necessário.

   Para excluir um ponto de acesso ou mapa de imagem, toque na guia **[!UICONTROL Ações]**. No cabeçalho **[!UICONTROL Mapas e pontos de acesso]**, no menu suspenso **[!UICONTROL Tipo selecionado]**, selecione o nome do ponto de acesso ou mapa de imagem que deseja remover. Toque no ícone **[!UICONTROL Lixeira]**, ao lado do menu, e toque em **[!UICONTROL Excluir]**.

1. No campo de texto Nome , digite o nome do ponto de acesso ou do mapa de imagem. Esse nome também aparece na lista suspensa **[!UICONTROL Mapas e hotspot]**. Fornecer um nome facilita a identificação do ponto de acesso ou mapa de imagem se você decidir fazer alterações nele no futuro.
1. Siga um destes procedimentos na guia **[!UICONTROL Actions]**:

   * Toque em **[!UICONTROL Quickview]**.

      * Se você for um cliente do AEM Sites e do Ecommerce, toque no ícone **[!UICONTROL Seletor de produto]** (lupa) para abrir a página **[!UICONTROL Selecionar produto]**. Toque no produto que deseja usar e toque na marca de seleção no canto superior direito da página para retornar ao **[!UICONTROL Editor de banner do carrossel]**.
      * Se você não for um cliente do AEM Sites ou do Ecommerce

         * Consulte [Identificação de variáveis de ponto de acesso](#identifying-hotspot-and-image-map-variables) como você pode desejar definir essas variáveis.
         * Em seguida, insira manualmente o valor de SKU. No campo de texto **[!UICONTROL Valor SKU]**, digite o SKU do produto (unidade de manutenção de estoque), que é um identificador exclusivo para cada produto ou serviço distinto que você oferece. O valor de SKU inserido preenche automaticamente a parte variável do modelo do Quickview, de modo que o sistema saiba associar o ponto de acesso com um Quickview específico do SKU.
         * (Opcional) Se houver outras variáveis no Quickview que você precisa usar para identificar ainda mais um produto, toque em **[!UICONTROL Adicionar variável genérica]**. No campo de texto, especifique uma variável adicional. Por exemplo, `category=Mens` é uma variável adicionada.
         * Consulte [Trabalhar com seletores](working-with-selectors.md) para obter mais informações.
   * Toque em **[!UICONTROL Hiperlink]**.

      * Se você for um cliente do AEM Sites, toque no ícone **[!UICONTROL Seletor de site]** (pasta) para navegar até um URL.

         >[!NOTE]
         >O método de vinculação baseado em URL não é possível se o conteúdo interativo tiver links com URLs relativos, especialmente links para páginas do AEM Sites.

      * Se você for um cliente independente, no campo de texto **[!UICONTROL HREF]**, especifique o caminho do URL completo para uma página da Web vinculada.

         Certifique-se de especificar se deseja abrir o link em uma nova guia do navegador (padrão recomendado) ou na mesma guia.

         Consulte [Trabalhar com seletores](working-with-selectors.md) para obter mais informações.
   * Toque em **[!UICONTROL Fragmento de experiência]**.

      * Se você for um cliente do AEM Sites, toque no ícone **[!UICONTROL Pesquisar]** (lupa) para abrir a página Fragmento de experiência . Toque no Fragmento de experiência que deseja usar e toque em **[!UICONTROL Selecionar]** no canto superior direito da página para retornar à página Gerenciamento de ponto de acesso.

         Consulte [Fragmentos de experiência](/help/sites-authoring/experience-fragments.md).

         **Observação**: Esteja ciente de que as ferramentas de compartilhamento de mídia social no Banner do carrossel não são compatíveis quando você incorpora o visualizador a um Fragmento de experiência. Para contornar isso, você pode usar ou criar predefinições do visualizador que não tenham ferramentas de compartilhamento de redes sociais. Essas predefinições do visualizador permitem que você as incorpore com êxito aos Fragmentos de experiência.

      * Especifique a largura e a altura do Fragmento de experiência como ele aparecerá no banner.

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   Você também pode visualizar como será o banner do carrossel. Consulte [(Opcional) Visualização de banners do carrossel](#optional-previewing-carousel-banners).

1. Toque em **[!UICONTROL Salvar]**.
1. Publique o conjunto de carrossel. A publicação cria o código incorporado ou URL que você pode usar na página do site. Se você for um cliente do AEM Sites, poderá adicionar o conjunto de carrossel diretamente à sua página da Web.

   Consulte [Publicação de ativos](publishing-dynamicmedia-assets.md).

   Consulte [Adicionar um conjunto de carrossel à página de aterrissagem do site](#adding-a-carousel-banner-to-your-website-page)

## Edição de conjuntos de carrossel {#editing-carousel-sets}

>[!NOTE]
>
>Usuários não administrativos devem ser adicionados ao grupo **[!UICONTROL dam-users]** para poderem criar ou editar banners de carrossel. Se tiver problemas ao criar ou editar, consulte o administrador do sistema que pode adicioná-lo ao grupo **[!UICONTROL dam-users]**.

Você pode executar várias tarefas de edição em Conjuntos de carrossel, como as seguintes:

* Adicione slides a um conjunto de carrossel. Consulte também [Trabalhar com seletores](working-with-selectors.md).
* Reordene os slides no Conjunto de carrossel.
* Exclua ativos no Conjunto de carrossel.
* Aplique uma predefinição do visualizador.
* Exclua o Conjunto de carrossel.
* Adicione ou edite pontos de acesso e mapas de imagem. Consulte também [Trabalhar com seletores](working-with-selectors.md).

Esteja ciente de que, se você estiver editando imagens interativas com pontos de acesso e recortar a imagem, seus pontos de acesso serão removidos.

**Para editar um conjunto** de carrossel:

1. Siga um destes procedimentos:

   * Passe o mouse sobre um ativo Conjunto de carrossel e toque em **[!UICONTROL Editar]** (ícone de lápis).
   * Passe o mouse sobre um ativo Conjunto de carrossel, toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção) e toque em **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque em um ativo Conjunto de carrossel e, no canto superior esquerdo da página, toque em **[!UICONTROL Editar]** (ícone de lápis).

1. Para editar o Conjunto de carrossel, siga um destes procedimentos:

   * Para adicionar um slide, toque no ícone **[!UICONTROL Adicionar slide]** e navegue até o ativo que deseja adicionar ao slide e toque na marca de seleção.
   * Para reorganizar os slides, arraste um slide para um novo local (selecione o ícone de reordenação para mover itens).
   * Para adicionar um ponto de acesso ou mapa de imagem, toque no ponto de acesso ou nos ícones do mapa de imagem e consulte [adicionar pontos de acesso e mapas de imagem](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Para editar a aparência ou o comportamento do conjunto de carrossel, toque na guia **[!UICONTROL Aparência]** ou na guia **[!UICONTROL Comportamento]** e defina as opções desejadas.
   * Para editar pontos de acesso ou mapas de imagem, no slide apropriado, selecione um ponto de acesso ou mapa de imagem e faça as alterações necessárias na guia **[!UICONTROL Actions]**.
   * Para excluir um slide, selecione-o e toque em **[!UICONTROL Excluir slide]** na barra de ferramentas.
   * Para aplicar uma predefinição, próximo ao canto superior direito da página, toque na lista suspensa predefinição e selecione uma predefinição do visualizador.
   * Para excluir um Conjunto de carrossel inteiro, navegue até o Conjunto de carrossel, selecione-o e toque em **[!UICONTROL Excluir]**.

## (Opcional) Visualização dos banners do carrossel {#optional-previewing-carousel-banners}

Você pode usar **[!UICONTROL Visualizar]** para ver a aparência do seu banner de carrossel para os clientes e testar os pontos de acesso e mapas de imagem dos banners de carrossel para garantir que eles estejam se comportando conforme esperado.

Quando estiver satisfeito com o banner do carrossel, você pode publicá-lo.

* Consulte [Incorporando o visualizador de vídeo ou imagem em uma página da Web](embed-code.md).
* Consulte [Vincular URLs ao aplicativo Web](linking-urls-to-yourwebapplication.md). Observe que o método de vinculação baseado em URL não é possível se o conteúdo interativo tiver links com URLs relativos, especialmente links para páginas do AEM Sites.
* Consulte [Adicionar ativos Dynamic Media às páginas.](adding-dynamic-media-assets-to-pages.md)

Você pode visualizar banners de carrossel no Editor de carrossel (método preferencial) ou na lista **[!UICONTROL Visualizadores]**.

**Para visualizar banners** de carrossel:

1. Em **[!UICONTROL Assets]**, navegue até um banner de carrossel existente que você criou e toque para abri-lo.
1. Toque em **[!UICONTROL Editar]**.
1. Na lista de predefinições do visualizador, no canto direito da barra de ferramentas, selecione um visualizador para visualizar o banner do carrossel.

   ![lista suspensa experience_fragment-carouselbanner-viewerdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Toque em **[!UICONTROL Visualizar]**.
1. Toque nos pontos de acesso ou mapas de imagem na imagem para testar suas ações associadas.

**Para visualizar banners de carrossel na lista** Visualizadores:

1. Em **[!UICONTROL Assets]**, navegue até um banner de carrossel existente que você criou e toque para abri-lo.
1. Próximo ao canto superior esquerdo da página **[!UICONTROL Visualizar]**, toque no ícone **[!UICONTROL Conteúdo]**.
1. Na lista **[!UICONTROL Visualizadores]** no painel no lado esquerdo da página, toque no nome da predefinição do visualizador do banner de carrossel que deseja usar.
1. Toque nos pontos de acesso ou mapas de imagem na imagem para testar suas ações associadas.

## Publicação de banners em carrossel {#publishing-carousel-banners}

Você precisa publicar o carrossel para usá-lo. A publicação de um Conjunto de carrossel ativa o URL e o Código incorporado. Ele também publica o carrossel para a nuvem do Dynamic Media, que é integrada a uma CDN para entrega escalável e com desempenho.

Se você usar uma imagem interativa existente com pontos de acesso para o seu banner de carrossel, deverá publicar a imagem interativa separadamente depois de publicar o banner de carrossel.

Além disso, se você modificar uma imagem interativa publicada pré-existente que esteja usando em um banner de carrossel, deverá publicar a imagem interativa antes que essas alterações sejam refletidas no banner de carrossel.

Consulte [Publicação de ativos Dynamic Media](publishing-dynamicmedia-assets.md) para obter informações sobre como publicar banners de carrossel.

## Adicionar um banner de carrossel à página do seu site {#adding-a-carousel-banner-to-your-website-page}

Depois de fazer upload das imagens do banner para criar um carrossel, adicionar pontos de acesso e/ou mapas de imagem ao banner e publicar o conjunto de carrossel, você estará pronto para adicioná-lo à página do site existente.

Se você for um cliente do AEM Sites, poderá adicionar o banner do carrossel diretamente à sua página, arrastando o componente Mídia interativa para a página. Consulte [Adicionar ativos Dynamic Media às páginas.](adding-dynamic-media-assets-to-pages.md)

No entanto, se você for um cliente independente de ativos de AEM, poderá adicionar manualmente o banner do carrossel à página inicial do site, conforme descrito nesta seção.

1. Copie o código incorporado do conjunto de carrossel publicado.

   Consulte [Incorporando o visualizador de vídeo ou imagem em uma página da Web](embed-code.md).

1. Adicione o código incorporado que você copiou do AEM Assets para sua página da Web.

   O código incorporado copiado é responsivo, portanto, deve se ajustar automaticamente à área de incorporação da página.

## Integração do banner do carrossel com um Quickview existente {#integrating-the-carousel-banner-with-an-existing-quickview}

Essa tarefa se aplica somente se você for um cliente independente do AEM Assets.

A última etapa desse processo é integrar o banner do carrossel a uma implementação existente do Quickview em seu site. Cada implementação do Quickview é única e é necessária uma abordagem específica que provavelmente envolva a assistência de uma pessoa de TI front-end.

A implementação existente do Quickview normalmente representa uma cadeia de ações inter-relacionadas que ocorrem na página da Web na seguinte ordem:

1. Um usuário aciona um elemento na interface do usuário do site.
1. O código front-end obtém um URL do Quickview com base no elemento da interface do usuário acionado na etapa 1.
1. O código de front-end envia uma solicitação Ajax usando o URL obtido na etapa 2.
1. A lógica de back-end retorna os dados ou o conteúdo correspondentes do Quickview de volta ao código de front-end.
1. O código front-end carrega os dados ou o conteúdo do Quickview.
1. Opcionalmente, o código front-end converte os dados do Quickview carregados em uma representação HTML.
1. O código front-end exibe uma caixa de diálogo ou painel modal e renderiza o conteúdo HTML na tela do usuário final.

Essas chamadas podem não representar chamadas de API públicas independentes que podem ser chamadas pela lógica da página da Web de uma etapa arbitrária. Em vez disso, é uma chamada encadeada em que cada próxima etapa está oculta na última fase (retorno de chamada) da etapa anterior.

Ao mesmo tempo em que o banner do carrossel substitui a etapa 1 e parcialmente a etapa 2, quando um usuário clica em um ponto de acesso ou mapa de imagem dentro do banner do carrossel, essa interação do usuário é tratada pelo visualizador. O visualizador retorna um evento para a página da Web que contém todos os pontos de acesso ou dados de mapa de imagem adicionados anteriormente.

Nesse manipulador de evento, o código front-end faz o seguinte:

* Escuta um evento emitido pelo banner do carrossel.
* Constrói um URL do Quickview com base no ponto de acesso ou nos dados do mapa de imagem.
* Aciona o processo de carregamento do Quickview a partir do back-end e renderização na tela para exibição.

O código incorporado retornado pelo AEM Assets já tem um manipulador de eventos pronto para uso no local, que é comentado.

Portanto, é necessário remover o comentário do código e substituir o corpo do manipulador de teste pelo código específico da página da Web em particular.

O processo de construção do URL do Quickview é basicamente oposto do processo usado para identificar o ponto de acesso e as variáveis de mapa de imagem abordadas anteriormente.

Consulte [Identificação de variáveis de ponto de acesso e mapa de imagem](#identifying-hotspot-and-image-map-variables).

A última etapa para acionar o URL do Quickview e ativar o painel do Quickview provavelmente requer a assistência de uma pessoa de TI front-end do seu departamento de TI. Eles têm o conhecimento de saber mais sobre como acionar com precisão a implementação do Quickview a partir da etapa adequada, tendo um URL Quickview pronto para uso.

## Uso do Quickviews para criar pop-ups personalizados {#using-quickviews-to-create-custom-pop-ups}

Consulte [Usar o Quickviews para criar pop-ups personalizados](custom-pop-ups.md).
