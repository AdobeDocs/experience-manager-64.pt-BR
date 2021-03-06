---
title: Adicionar componentes do Dynamic Media Classic às páginas
description: Como adicionar recursos e componentes do Dynamic Media Classic às páginas no Adobe Experience Manager.
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: managing-assets
exl-id: b11b19c1-712d-4698-aefc-930ff8cacbc1
feature: Dynamic Media Classic
role: User
source-git-commit: 50b657456d2a0eaaaf681d3902eba38b15d00e12
workflow-type: tm+mt
source-wordcount: '2824'
ht-degree: 27%

---

# Adicionar componentes do Dynamic Media Classic às páginas {#adding-scene-features-to-your-page}

O Adobe Dynamic Media Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email, impressão e monitores conectados à Internet.

Você pode visualizar AEM ativos publicados no Dynamic Media Classic em vários visualizadores:

* Zoom
* Flyout
* Vídeo
* Modelo de imagem
* Imagem

Você pode publicar ativos digitais diretamente do AEM para o Dynamic Media Classic e pode publicar ativos digitais do Dynamic Media Classic para o AEM.

Este documento descreve como publicar ativos digitais do AEM para o Dynamic Media Classic e vice-versa. Os visualizadores também são descritos detalhadamente. Para obter informações sobre como configurar o AEM para o Dynamic Media Classic, consulte [Integração do Dynamic Media Classic com o AEM](/help/sites-administering/scene7.md).

Consulte também [Adição de mapas de imagem](image-maps.md).

Para obter mais informações sobre como usar componentes de vídeo com AEM, consulte [Vídeo](video.md).

>[!NOTE]
>
>Se os ativos do Dynamic Media Classic não forem exibidos corretamente, verifique se a Mídia dinâmica é [desativado](config-dynamic.md#disabling-dynamic-media) e, em seguida, atualize a página.

## Publicar manualmente no Dynamic Media Classic a partir de ativos {#manually-publishing-to-scene-from-assets}

Você pode publicar ativos digitais no Dynamic Media Classic da seguinte maneira:

* [Na interface do usuário clássica no console Assets](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [Na interface do usuário clássica de um ativo](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [Na interface do usuário clássica de fora da pasta de destino CQ](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>AEM publica no Dynamic Media Classic de forma assíncrona. Depois de clicar em **[!UICONTROL Publicar]**, pode levar vários segundos para que o ativo seja publicado no Dynamic Media Classic.

## Componentes do Dynamic Media Classic {#scene-components}

Os seguintes componentes do Dynamic Media Classic estão disponíveis no AEM:

* Zoom
* Flyout (Zoom)
* Modelo de imagem
* Imagem
* Vídeo

>[!NOTE]
>
>Esses componentes não estão disponíveis por padrão e precisam ser selecionados em **[!UICONTROL Design]** antes de usar.

Após a sua disponibilização no **[!UICONTROL Design]** , é possível adicionar os componentes à página como qualquer outro componente AEM. Os ativos que ainda não foram publicados na Dynamic Media Classic são publicados na Dynamic Media Classic se estiverem em uma pasta sincronizada, em uma página ou com uma configuração da nuvem do Dynamic Media Classic.

>[!NOTE]
>
>Se você estiver criando e desenvolvendo visualizadores personalizados e usando o Localizador de conteúdo, será necessário adicionar explicitamente a variável **[!UICONTROL allowfullscreen]** parâmetro.

### Aviso de fim de vida útil de visualizadores Flash {#flash-viewers-end-of-life-notice}

A partir de 31 de janeiro de 2017, a Adobe Dynamic Media Classic encerrou o suporte para a plataforma do visualizador de Flashes.

### Adicionar um componente do Dynamic Media Classic (Scene7) a uma página {#adding-a-scene-component-to-a-page}

Adicionar um componente do Dynamic Media Classic (Scene7) a uma página é o mesmo que adicionar um componente a qualquer página. Os componentes do Dynamic Media Classic são descritos detalhadamente nas seções a seguir.

**Para adicionar um componente Dynamic Media Classic (Scene7) a uma página**:

1. Em AEM, abra a página à qual deseja adicionar o componente Dynamic Media Classic (Scene7).

1. Se nenhum componente do Dynamic Media Classic estiver disponível, clique em **[!UICONTROL Design]** toque em qualquer componente com uma borda azul, toque no modo **[!UICONTROL Pai]** e depois o **[!UICONTROL Configuração]** ícone . Em **[!UICONTROL Parsys (Design)]**, selecione todos os componentes do Dynamic Media Classic para torná-los disponíveis e clique em **[!UICONTROL OK]**.

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Clique em **[!UICONTROL Editar]** para retornar a **[!UICONTROL Editar]** modo.

1. Arraste um componente do grupo Dynamic Media Classic no sidekick até a página no local desejado.

1. Clique no botão **[!UICONTROL Configuração]** ícone para abrir o componente.

1. Edite o componente conforme necessário e clique em **[!UICONTROL OK]** para salvar as alterações.
1. Arraste a imagem ou o vídeo do navegador de conteúdo para o componente Dynamic Media Classic adicionado à página.

   >[!NOTE]
   >
   >Somente na interface de toque, você deve arrastar e soltar a imagem ou o vídeo no componente do Dynamic Media Classic que você colocou na página. Não há suporte para selecionar e editar o componente do Dynamic Media Classic e, em seguida, escolher o ativo.

### Adicionar experiências de visualização interativas a um site responsivo {#adding-interactive-viewing-experiences-to-a-responsive-website}

Design responsivo para seus ativos significa que eles se adaptam dependendo de onde são exibidos. Com o design responsivo, os mesmos ativos podem ser exibidos de maneira eficaz em diversos dispositivos.

Consulte também [Design responsivo para páginas da Web](/help/sites-developing/responsive.md).

**Para adicionar uma experiência de visualização interativa a um site responsivo**:

1. Faça logon no AEM e certifique-se de ter [Adobe Dynamic Media Classic Cloud Services configurado](/help/sites-administering/scene7.md#configuring-scene-integration) e que os componentes do Dynamic Media Classic estão disponíveis.

   >[!NOTE]
   >
   >Se os componentes do Dynamic Media Classic não estiverem disponíveis, verifique se [permitir-lhes por meio do modo Design](/help/sites-authoring/default-components-designmode.md).

1. Em um site com a variável **[!UICONTROL Dynamic Media Classic]** componentes ativados, arrastar e **[!UICONTROL Imagem]** para a página.
1. Selecione o componente e toque no ícone de configuração.
1. No **[!UICONTROL Configurações do Dynamic Media Classic]** ajuste os pontos de interrupção.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Verifique se os visualizadores estão sendo redimensionados de maneira adequada e de que todas as interações sejam otimizadas para desktop, tablet e dispositivo móvel.

### Configurações comuns a todos os componentes do Dynamic Media Classic {#settings-common-to-all-scene-components}

Embora as opções de configuração variem, as opções a seguir são comuns a todos [!UICONTROL Dynamic Media Classic] componentes:

* **[!UICONTROL Referência de arquivo]**
Navegue até o arquivo que deseja referenciar. A referência de arquivo mostra o URL do ativo e não necessariamente o URL completo do Dynamic Media Classic, incluindo os comandos e parâmetros de URL. Não é possível adicionar comandos e parâmetros de URL do Dynamic Media Classic neste campo. Eles devem ser adicionados por meio da funcionalidade correspondente no componente.
* **[!UICONTROL Largura]**
Permite definir a largura.
* **[!UICONTROL Altura]**
Permite definir a altura.

Você define essas opções de configuração abrindo (clicando duas vezes em) um componente do Dynamic Media Classic, por exemplo, ao abrir um **[!UICONTROL Zoom]** componente:

![chlimage_1-226](assets/chlimage_1-226.png)

### Zoom {#zoom}

O componente de Zoom do HTML5 exibe uma imagem maior quando você pressiona o botão **[!UICONTROL +]** botão.

O ativo tem ferramentas de zoom na parte inferior. Toque **[!UICONTROL +]** para aumentar. Toque **[!UICONTROL -]** para reduzir. Tocar no **[!UICONTROL x]** ou a seta de redefinição de zoom traz a imagem de volta ao tamanho original de importação. Toque nas setas diagonais para torná-las em tela cheia. Toque **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode configurar [configurações comuns a todos [!UICONTROL Dynamic Media Classic] componentes](#settings-common-to-all-scene-components).

![chlimage_1-227](assets/chlimage_1-227.png)

### Flyout {#flyout}

Na HTML5 **[!UICONTROL Flyout]** componente, o ativo é mostrado como tela dividida; deixou o ativo no tamanho especificado; à direita, a parte de zoom é exibida. Toque **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode configurar [configurações comuns a todos os componentes do Dynamic Media Classic](#settings-common-to-all-scene-components).

>[!NOTE]
>
>Se o seu **[!UICONTROL Flyout]** O componente usa um tamanho personalizado, em seguida, esse tamanho personalizado é usado e a configuração responsiva do componente é desativada.
>
>Se o seu **[!UICONTROL Flyout]** O componente usa o tamanho padrão, como definido na variável **[!UICONTROL Visualização de projeto]**, o tamanho padrão é usado e o componente é estendido para acomodar o tamanho do layout da página com a configuração responsiva do componente ativada. Esteja ciente, no entanto, de que há uma limitação na configuração responsiva do componente. Quando você usar a variável **[!UICONTROL Flyout]** com a configuração responsiva, você não deve usá-lo com o trecho de página completo. Caso contrário, a variável **[!UICONTROL Flyout]** pode se estender além da borda direita da página.

![chlimage_1-228](assets/chlimage_1-228.png)

### Imagem {#image}

A Dynamic Media Classic **[!UICONTROL Imagem]** permite adicionar a funcionalidade do Dynamic Media Classic às imagens, como modificadores do Dynamic Media Classic, predefinições de imagem ou visualizador e nitidez. A Dynamic Media Classic **[!UICONTROL Imagem]** é semelhante a outros componentes de imagem no AEM com funcionalidade especial do Dynamic Media Classic. Neste exemplo, a imagem tem o modificador Dynamic Media Classic URL, **&amp;op_invert=1** aplicada.

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Título, Texto alternativo]**
No **[!UICONTROL Avançado]** , adicione um título à imagem e um texto alternativo para os usuários que tenham os gráficos desativados.

* **[!UICONTROL URL, Abrir em]**
É possível definir um ativo de para abrir um link. Defina o **[!UICONTROL URL]** e, em **[!UICONTROL Abrir em]**, indique se você deseja que ele abra na mesma janela ou em uma nova.

![chlimage_1-230](assets/chlimage_1-230.png)

* **[!UICONTROL Predefinição do visualizador]**
Selecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições do visualizador](/help/assets/managing-viewer-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

* **[!UICONTROL Configuração do Dynamic Media Classic]**
Selecione a configuração do Dynamic Media Classic que deseja usar para buscar predefinições de imagens ativas do SPS.

* **[!UICONTROL Predefinição de imagem]**
Selecione uma predefinição de imagem existente no menu suspenso. Se a predefinição de imagem que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

* **[!UICONTROL Formato de saída]**
Selecione o formato de saída da imagem, por exemplo jpeg. Dependendo do formato de saída selecionado, você pode ter opções de configuração adicionais. Consulte [Práticas recomendadas de predefinição de imagem](/help/assets/managing-image-presets.md#image-preset-options).

* **[!UICONTROL Nitidez]**
Selecione como deseja ajustar a nitidez da imagem. A nitidez é explicada detalhadamente em [Práticas recomendadas da predefinição de imagem](/help/assets/managing-image-presets.md#image-preset-options) e [Práticas recomendadas de nitidez](/help/assets/assets/sharpening_images.pdf).

* **[!UICONTROL Modificadores de URL]**
Você pode alterar os efeitos da imagem fornecendo comandos adicionais de imagem do Dynamic Media Classic. Eles estão descritos em [Predefinições de imagem](/help/assets/managing-image-presets.md) e na [Referência de comandos](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

* **[!UICONTROL Pontos de interrupção]**
Se seu site for responsivo, você deseja ajustar os pontos de interrupção. Os pontos de interrupção devem ser separados por vírgulas ( , ).

### Modelo de imagem {#image-template}

[Modelos de imagem do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/creating-template.html#creating-the-initial-template) são conteúdo em camadas do Photoshop que foi importado para o Dynamic Media Classic, onde o conteúdo e as propriedades foram parametrizadas para oferecer variabilidade. O componente do **[!UICONTROL Modelo de imagem]** permite importar imagens e alterar dinamicamente o texto no AEM. Além disso, é possível configurar o componente do **[!UICONTROL Modelo de imagem]** para usar valores do contexto de cliente, de modo que cada usuário experiencie a imagem de uma maneira personalizada.

Toque **[!UICONTROL Editar]** para configurar o componente. Você pode configurar [configurações comuns a todos os componentes do Dynamic Media Classic](#settings-common-to-all-scene-components) assim como outras configurações descritas nesta seção.

![chlimage_1-231](assets/chlimage_1-231.png)

* **[!UICONTROL Referência de arquivo, Largura, Altura]**
Consulte as configurações comuns a todos os componentes do Dynamic Media Classic.

   >[!NOTE]
   >
   >Comandos e parâmetros de URL do Dynamic Media Classic não podem ser adicionados diretamente ao URL de referência de arquivo. Eles podem ser definidos somente na interface do componente no painel **[!UICONTROL Parâmetro]**.

* **[!UICONTROL Título, Texto alternativo]**
Na guia Modelo de imagem do Dynamic Media Classic , adicione um título à imagem e um texto alternativo para os usuários que tenham os gráficos desativados.

* **[!UICONTROL URL, Abrir em]**
É possível definir um ativo de para abrir um link. Defina o URL e, em Abrir em, indique se você deseja que ele abra na mesma janela ou em uma nova.

![chlimage_1-232](assets/chlimage_1-232.png)

* **[!UICONTROL Painel de parâmetros]**
Ao importar uma imagem, os parâmetros são preenchidos previamente com informações da imagem. Caso nenhum conteúdo possa ser alterado dinamicamente, essa janela fica vazia.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Alterar o texto dinamicamente {#changing-text-dynamically}

Para alterar o texto dinamicamente, insira o novo texto nos campos e clique em **[!UICONTROL OK]**. Neste exemplo, o **[!UICONTROL Preço]** agora é $50 e o frete é de 99 centavos de dólar.

![chlimage_1-234](assets/chlimage_1-234.png)

O texto na imagem é alterado. Você pode redefinir o texto de volta para o valor original tocando em **[!UICONTROL Redefinir]** ao lado do campo .

![chlimage_1-235](assets/chlimage_1-235.png)

#### Alterar o texto para refletir o valor de contexto do cliente {#changing-text-to-reflect-the-value-of-a-client-context-value}

Para vincular um campo a um valor de contexto de cliente, toque em **[!UICONTROL Selecionar]** para abrir o menu de contexto do cliente, selecione o contexto do cliente e toque em **[!UICONTROL OK]**. Neste exemplo, o nome é alterado com base na vinculação do Nome com o nome formatado no perfil.

![chlimage_1-236](assets/chlimage_1-236.png)

O texto reflete o nome do cliente conectado no momento. É possível redefinir o texto de volta para o valor original ao clicar em **[!UICONTROL Redefinir]** próximo ao campo.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Como tornar o modelo de imagem do Dynamic Media Classic um link {#making-the-scene-image-template-a-link}

1. Na página com a Dynamic Media Classic **[!UICONTROL Modelo de imagem]** componente, toque **[!UICONTROL Editar]**.
1. No **[!UICONTROL URL]** , insira o URL para o qual os usuários são direcionados quando a imagem é tocada. No campo **[!UICONTROL Abrir em]**, selecione se deseja onde o destino seja aberto (uma nova janela ou na mesma).

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Toque **[!UICONTROL OK]**.

### Componente de vídeo {#video-component}

A Dynamic Media Classic **[!UICONTROL Vídeo]** O componente (disponível na seção Dynamic Media Classic do sidekick) usa a detecção de dispositivo e de largura de banda para veicular o vídeo correto em cada tela. Este componente é um reprodutor de vídeo HTML5; é um visualizador único que pode ser usado em todos os canais.

Ele pode ser usado pra conjuntos de vídeos adaptáveis, um único vídeo MP4 ou um único vídeo F4V.

Consulte [Vídeo](s7-video.md) para obter mais informações sobre como os vídeos funcionam com a integração do Dynamic Media Classic. Além disso, consulte [o componente Vídeo do Dynamic Media Classic versus o componente Vídeo de base](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Restrições conhecidas do componente de vídeo {#known-limitations-for-the-video-component}

O Adobe DAM e o WCM mostram se um vídeo principal é carregado por upload. Eles não mostram os ativos de proxy a seguir:

* Representações codificadas do Dynamic Media Classic
* Conjuntos de vídeo adaptáveis Dynamic Media Classic

Ao usar um conjunto de vídeos adaptáveis com o componente de vídeo do Dynamic Media Classic, é necessário redimensionar o componente para ajustar as dimensões do vídeo.

## Navegador de conteúdo do Dynamic Media Classic {#scene-content-browser}

O navegador de conteúdo do Dynamic Media Classic permite exibir o conteúdo do Dynamic Media Classic diretamente no AEM. Para acessar o navegador de conteúdo, no **[!UICONTROL Localizador de conteúdo]**, selecione **[!UICONTROL Dynamic Media Classic]** na interface otimizada para toque ou na **[!UICONTROL S7]** na interface do usuário clássica. A funcionalidade é idêntica em ambas as interfaces do usuário.

Caso tenha diversas configurações, o AEM exibe, por padrão, a [configuração padrão](/help/sites-administering/scene7.md#configuring-a-default-configuration). Você pode selecionar configurações diferentes diretamente no navegador de conteúdo do Dynamic Media Classic no menu suspenso.

>[!NOTE]
>
>* Os ativos localizados na pasta ad-hoc não aparecerão no navegador de conteúdo do Dynamic Media Classic.
>* When [A Visualização segura está ativada](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), os ativos publicados e não publicados no Dynamic Media Classic aparecem no navegador de conteúdo do Dynamic Media Classic.
>* Se você não vir **[!UICONTROL Dynamic Media Classic]** ou **[!UICONTROL S7]** como uma opção no navegador de conteúdo, é necessário [configurar o Dynamic Media Classic para funcionar com o AEM](/help/sites-administering/scene7.md).
>* Para vídeo, o navegador de conteúdo do Dynamic Media Classic é compatível com:
   >   * Conjuntos de vídeos adaptáveis: contêiner de todas as representações de vídeo necessárias para uma reprodução perfeita em diversas telas
   >   * Vídeo MP4 único
   >   * Vídeo F4V único


### Navegação de conteúdo na interface otimizada para toque {#browsing-content-in-the-touch-optimized-ui}

Você pode acessar o navegador de conteúdo na interface otimizada para toque ou clássica. Atualmente, a interface otimizada para toque tem a seguinte limitação:

* FXG e ativos Flash da Dynamic Media Classic não são compatíveis.

Navegue pelos ativos do Dynamic Media Classic selecionando **[!UICONTROL Dynamic Media Classic]** no terceiro menu suspenso. O Dynamic Media Classic não será exibido na lista se você não tiver configurado a integração Dynamic Media Classic/AEM.

>[!NOTE]
>
>* O navegador de conteúdo do Dynamic Media Classic carrega cerca de 100 ativos e os classifica por nome.
>* Se você tiver um servidor de visualização seguro definido, o navegador usará esse servidor de visualização para renderizar miniaturas e ativos.

>


![chlimage_1-240](assets/chlimage_1-240.png)

Além disso, você pode navegar pelas informações de resolução, tamanho, dias desde a modificação e nome do arquivo ao passar o mouse sobre o ativo no navegador.

![chlimage_1-241](assets/chlimage_1-241.png)

* Para Conjuntos de vídeos adaptáveis e Modelos, nenhuma informação de tamanho é gerada para miniaturas.
* Para Conjuntos de vídeos adaptáveis, nenhuma resolução é gerada para miniaturas.

### Pesquisar ativos do Dynamic Media Classic com o navegador de conteúdo {#searching-for-scene-assets-with-the-content-browser}

Pesquisar ativos do Dynamic Media Classic é semelhante a pesquisar ativos AEM exceto que, ao pesquisar, você está realmente vendo uma visualização remota dos ativos no sistema Dynamic Media Classic, em vez de importá-los diretamente para o AEM.

É possível usar a interface do usuário clássica ou a otimizada para toque para visualizar e pesquisar ativos. Dependendo da interface, a maneira como você pesquisa é levemente diferente.

Ao pesquisar em qualquer uma das interfaces de usuário, você pode filtrar pelos seguintes critérios (mostrados aqui na interface otimizada para toque):

* **[!UICONTROL Inserir palavras-chave]**
Você pode pesquisar ativos por nome. Ao pesquisar, as palavras-chave inseridas corresponderão às palavras com as quais o nome de arquivo come. Por exemplo, digitar a palavra “nadar” pesquisaria todos os nomes de arquivo de ativo que comecem com as letras nessa ordem. Toque em Inserir depois de digitar o termo para localizar o ativo.

![chlimage_1-242](assets/chlimage_1-242.png)

* **[!UICONTROL Pasta/caminho]**
O nome da pasta que aparece é baseado na configuração selecionada. Você pode detalhar para níveis inferiores tocando no ícone de pasta, selecionando uma subpasta e tocando na marca de seleção para selecioná-la.

Se você inserir uma palavra-chave e selecionar uma pasta, o AEM procura nessa pasta e em todas as subpastas. No entanto, se você não digitar nenhuma palavra-chave ao pesquisar, selecionar a pasta exibirá somente os ativos nessa pasta e não incluirá nenhuma subpasta.

Por padrão, o AEM procura na pasta selecionada e em todas as subpastas.

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Tipo de ativo]**
Selecionar **[!UICONTROL Dynamic Media Classic]** para navegar pelo conteúdo do Dynamic Media Classic. Essa opção só estará disponível se o Dynamic Media Classic tiver sido configurado.

![chlimage_1-244](assets/chlimage_1-244.png)

* **[!UICONTROL Configuração]**
Se você tiver mais de uma configuração Dynamic Media Classic definida em [!UICONTROL Cloud Services], você pode selecioná-lo aqui. Como resultado, a pasta será alterada com base na configuração escolhida.

![chlimage_1-245](assets/chlimage_1-245.png)

* **[!UICONTROL Tipo de ativo]**
No navegador Dynamic Media Classic, você pode filtrar resultados para incluir qualquer um dos seguintes itens: imagens, modelos, vídeos e conjuntos de vídeos adaptáveis. Se você não selecionar nenhum tipo de ativo, o AEM procura todos os tipos de ativo por padrão.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* Na interface do usuário clássica, também é possível procurar pelo **Flash** e pelo **FXG**. A filtragem para eles na interface otimizada para toque não é compatível atualmente.
>
>* Ao pesquisar por vídeo, você estará procurando uma única representação. Os resultados retornam a representação original (somente o &amp;ast;.mp4) e a representação codificada.
>* Ao pesquisar um conjunto de vídeos adaptáveis, você está pesquisando a pasta e todas as subpastas, mas somente se tiver adicionado uma palavra-chave à pesquisa. Caso não tenha adicionado uma palavra-chave, o AEM não pesquisará nas subpastas.

>


* **[!UICONTROL Publicar status]**
Você pode filtrar por ativos com base no status da publicação: **[!UICONTROL Não publicado]** ou **[!UICONTROL Publicado]**. Se você não selecionar nenhuma **[!UICONTROL Publicar status]**, AEM por padrão pesquisa todos os status de publicação.

![chlimage_1-247](assets/chlimage_1-247.png)
