---
title: Adicionar recursos do Dynamic Media Classic à sua página
seo-title: Adicionar recursos do Dynamic Media Classic à sua página
description: O Adobe Dynamic Media Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email e telas e impressão conectadas à Internet.
seo-description: O Adobe Dynamic Media Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email e telas e impressão conectadas à Internet.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
translation-type: tm+mt
source-git-commit: 0016825ced6706cda7447546af876d5a897c8ff5
workflow-type: tm+mt
source-wordcount: '3428'
ht-degree: 32%

---


# Adicionar recursos do Dynamic Media Classic à sua página{#adding-scene-features-to-your-page}

[O Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email e telas e impressão conectadas à Internet.

Você pode visualização AEM ativos publicados no Dynamic Media Classic em vários visualizadores:

* Zoom
* Flyout
* Vídeo
* Modelo de imagem
* Imagem

Você pode publicar ativos digitais diretamente do AEM para o Dynamic Media Classic e pode publicar ativos digitais do Dynamic Media Classic para AEM.

Esta seção descreve como publicar ativos digitais do AEM para o Dynamic Media Classic e vice-versa. Os visualizadores também são descritos detalhadamente. Para obter informações sobre como configurar AEM para o Dynamic Media Classic, consulte [Integração do Dynamic Media Classic com AEM](/help/sites-administering/scene7.md).

Consulte também [Adição de mapas de imagem](/help/assets/image-maps.md).

Para obter mais informações sobre como usar componentes de vídeo no AEM, consulte o seguinte:

* [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Se os ativos do Dynamic Media Classic não forem exibidos corretamente, verifique se a Mídia dinâmica está [desativada](/help/assets/config-dynamic.md#disabling-dynamic-media) e atualize a página.

## Publicar manualmente no Dynamic Media Classic a partir de Ativos {#manually-publishing-to-scene-from-assets}

Você pode publicar ativos digitais no Dynamic Media Classic no console Ativos na interface clássica ou diretamente do ativo.

>[!NOTE]
>
>AEM publica no Dynamic Media Classic de forma assíncrona. Depois de clicar em **[!UICONTROL Publicar]**, pode levar vários segundos para que o ativo publique no Dynamic Media Classic.


### Publicação por meio do console Assets {#publishing-from-the-assets-console}

Para publicar no Dynamic Media Classic no console Ativos, se os ativos estiverem em uma pasta de público alvo do Dynamic Media Classic:

1. Na interface clássica AEM, clique em **[!UICONTROL Ativos digitais]** para acessar o gerenciador de ativos digitais.

1. Selecione o ativo (ou ativos) ou a pasta na pasta do público alvo que deseja publicar no Dynamic Media Classic e clique com o botão direito do mouse e selecione **[!UICONTROL Publicar no Dynamic Media Classic]**. Como alternativa, você pode selecionar **[!UICONTROL Publicar no Dynamic Media Classic]** no menu **[!UICONTROL Ferramentas]**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Vá para o Dynamic Media Classic e confirme se os ativos estão disponíveis.

   >[!NOTE]
   >
   >Se os ativos não estiverem em uma pasta sincronizada do Dynamic Media Classic, **[!UICONTROL Publicar no Dynamic Media Classic]** em ambos os menus estará visível, mas desativado.

### Publicar a partir de um ativo {#publishing-from-an-asset}

Você pode publicar manualmente um ativo, contanto que ele esteja localizado dentro da pasta sincronizada do Dynamic Media Classic.

>[!NOTE]
>
>Se o ativo não estiver localizado na pasta sincronizada do Dynamic Media Classic, o link para **[!UICONTROL Publicar no Dynamic Media Classic]** não estará disponível.

**Para publicar no Dynamic Media Classic diretamente de um ativo** digital:

1. No AEM, clique em **[!UICONTROL Ativos digitais]** para acessar o gerenciador de ativos digitais.

1. Clique duas vezes para abrir um ativo.

1. No painel de detalhes do ativo, selecione **[!UICONTROL Publicar no Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. O link é alterado para **[!UICONTROL Publicando...]** e, em seguida, para **[!UICONTROL Publicado]**. Vá para o Dynamic Media Classic e confirme se o ativo está disponível.

   >[!NOTE]
   >
   >Se o ativo não publicar corretamente no Dynamic Media Classic, o link mudará para **[!UICONTROL Falha na publicação]**. Se o ativo já tiver sido publicado no Dynamic Media Classic, o link exibirá **[!UICONTROL Publicar novamente no Dynamic Media Classic]**. A republicação permite fazer alterações em um ativo no AEM e republicá-los.

### Publicar ativos fora da pasta de públicos alvos do CQ {#publishing-assets-from-outside-the-cq-target-folder}

O Adobe recomenda que você publique ativos no Dynamic Media Classic somente de ativos na pasta de públicos alvos do Dynamic Media Classic. No entanto, se você precisar carregar ativos de uma pasta fora da pasta do público alvo, ainda será possível fazer isso fazendo upload deles para uma pasta *ad-hoc* no Dynamic Media Classic.

Para fazer isso, configure a configuração da nuvem para a página onde o ativo será exibido. Em seguida, adicione um componente do Dynamic Media Classic à página e arraste e solte um ativo no componente. Depois que as propriedades da página são definidas para essa página, um link **[!UICONTROL Publicar no Dynamic Media Classic]** é exibido quando o usuário selecionado dispara o upload para o Dynamic Media Classic.

>[!NOTE]
>
>Os ativos que estão na pasta ad-hoc não aparecem no navegador de conteúdo do Dynamic Media Classic.

**Para publicar ativos que residem fora da pasta de destino CQ**:

1. Em AEM na interface clássica, clique em **[!UICONTROL Sites]** e navegue até a página da Web à qual você deseja adicionar um ativo digital que ainda não foi publicado no Dynamic Media Classic. (As regras usuais de herança de página se aplicam.)

1. No sidekick, clique no ícone **[!UICONTROL Página]** e, em seguida, clique em **[!UICONTROL Propriedades da página]**.

1. Clique em **[!UICONTROL Cloud Services] > [!UICONTROL Adicionar serviços] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Na lista suspensa Adobe Dynamic Media Classic, selecione a configuração desejada e clique em **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Na página da Web, adicione um componente do Dynamic Media Classic (Scene7) ao local desejado na página.
1. No localizador de conteúdo, arraste um ativo digital para o componente. Você verá um link para **[!UICONTROL Verificar o status de publicação do Dynamic Media Classic]**.

   >[!NOTE]
   >
   >Se o ativo digital estiver na pasta do público alvo CQ, nenhum link para **[!UICONTROL Verificar o status de publicação do Dynamic Media Classic]** será exibido. Os ativos são colocados no componente.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Clique em **[!UICONTROL Verificar o status de publicação do Dynamic Media Classic]**. Se o ativo não for publicado, AEM o publicará no Dynamic Media Classic. Depois de enviado por upload, o ativo estará localizado na pasta ad-hoc. Por padrão, a pasta ad-hoc está localizada em `name_of_the_company/CQ5_adhoc`. É possível [alterar essa configuração, se necessário](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Se o ativo não estiver em uma pasta sincronizada do Dynamic Media Classic e não houver nenhuma configuração de nuvem do Dynamic Media Classic associada à página atual, o upload falhará.

## Componentes do Dynamic Media Classic (Scene7) {#scene-components}

Os seguintes componentes do Dynamic Media Classic estão disponíveis no AEM:

* Zoom
* Flyout (Zoom)
* Modelo de imagem
* Imagem
* Vídeo

>[!NOTE]
>
>Esses componentes não estão disponíveis por padrão e precisam ser selecionados no modo **[!UICONTROL Design]** antes de usar.

Depois que eles forem disponibilizados no modo **[!UICONTROL Design]**, você poderá adicionar os componentes à sua página como qualquer outro componente AEM. Os ativos que ainda não foram publicados no Dynamic Media Classic são publicados no Dynamic Media Classic se estiverem em uma pasta sincronizada ou em uma página ou com uma configuração de nuvem do Dynamic Media Classic.

### Aviso ao fim da vida útil dos visualizadores de Flashes {#flash-viewers-end-of-life-notice}

A partir de 31 de janeiro de 2017, o Adobe Dynamic Media Classic encerrou oficialmente o suporte para a plataforma do visualizador de Flashes.

Para obter mais informações sobre essa alteração importante, consulte [Perguntas frequentes sobre o fim da vida útil do visualizador de Flashes](https://docs.adobe.com/content/docs/pt/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Adicionar um componente do Dynamic Media Classic a uma página {#adding-a-scene-component-to-a-page}

Adicionar um componente do Dynamic Media Classic a uma página é o mesmo que adicionar um componente a qualquer página. Os componentes do Dynamic Media Classic são descritos detalhadamente nas seções a seguir.

**Para adicionar um componente/visualizador do Dynamic Media Classic a uma página na interface clássica**:

1. Em AEM, abra a página onde deseja adicionar o componente Dynamic Media Classic.

1. Se nenhum componente do Dynamic Media Classic estiver disponível, clique na régua no sidekick para entrar no modo **[!UICONTROL Design]**, clique em **[!UICONTROL Editar]** parsys e selecione todos os componentes **[!UICONTROL Dynamic Media Classic]** para disponibilizá-los.

1. Retorne ao modo **[!UICONTROL Editar]** clicando no lápis no sidekick.

1. Arraste um componente do grupo **[!UICONTROL Dynamic Media Classic]** no sidekick para a página no local desejado.

1. Clique em **[!UICONTROL Editar]** para abrir o componente.

1. Edite o componente conforme necessário e clique em **[!UICONTROL OK]** para salvar as alterações.

### Adicionar experiência de exibição interativa a um site responsivo {#adding-interactive-viewing-experiences-to-a-responsive-website}

Design responsivo para seus ativos significa que eles se adaptam dependendo de onde são exibidos. Com um design responsivo, os mesmos ativos são exibidos eficientemente em vários dispositivos.

**Para adicionar uma experiência de exibição interativa a um site responsivo na interface do usuário clássica**:

1. Faça logon no AEM e certifique-se de que você tenha [configurado o Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) e que os componentes do Dynamic Media Classic estejam disponíveis.

   >[!NOTE]
   >
   >Se os componentes WCM do Dynamic Media Classic não estiverem disponíveis, certifique-se de ativá-los por meio do modo **[!UICONTROL Design].

1. Em um site com os componentes do Dynamic Media Classic ativados, arraste um visualizador **[!UICONTROL Image]** até a página.
1. Edite o componente e ajuste os pontos de interrupção na guia **[!UICONTROL Configurações do Dynamic Media Classic]**.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Verifique se os visualizadores estão sendo redimensionados de maneira adequada e de que todas as interações sejam otimizadas para desktop, tablet e dispositivo móvel.

### Configurações comuns a todos os componentes do Dynamic Media Classic {#settings-common-to-all-scene-components}

Embora as opções de configuração variem, as seguintes opções são comuns a todos os componentes do Dynamic Media Classic:

* **[!UICONTROL Referência de arquivo]**: navegue até um arquivo que deseje referenciar. A referência de arquivo mostra o URL do ativo e não necessariamente o URL completo do Dynamic Media Classic, incluindo os comandos e parâmetros do URL. Não é possível adicionar comandos e parâmetros de URL do Dynamic Media Classic neste campo. Eles devem ser adicionados por meio da funcionalidade correspondente no componente.
* **[!UICONTROL Largura]**: permite definir a largura.
* **[!UICONTROL Altura]**: permite definir a altura.

Você define essas opções de configuração clicando com o duplo em um componente do Dynamic Media Classic, por exemplo, ao abrir um componente **[!UICONTROL Zoom]**:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

O componente de Zoom HTML5 exibe uma imagem maior quando você pressiona o botão +.

O ativo tem ferramentas de zoom na parte inferior. Clique em **[!UICONTROL +]** para ampliar. Clique em **[!UICONTROL -]** para reduzir. Clicar em **[!UICONTROL x]** ou na seta de redefinição de zoom traz a imagem de volta ao tamanho original que foi importado como. Clique nas setas diagonais para abri-la em tela cheia. Clique em **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode definir [configurações comuns a todos os componentes do Dynamic Media Classic](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flyout {#flyout}

No componente do Flyout HTML5, o ativo é exibido como tela dividida; na parte à esquerda, o ativo no tamanho especificado; na parte à direita, a proporção de zoom é exibida. Clique em **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode definir [configurações comuns a todos os componentes do Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Se o seu componente do Flyout usa um tamanho personalizado, tal tamanho é usado e a configuração de componente é desabilitada.
>
>Se o componente Flyout usar o tamanho padrão, conforme definido na visualização [!UICONTROL Design], o tamanho padrão será usado e o componente será expandido para acomodar o tamanho do layout da página com a configuração responsiva do componente ativada. Esteja ciente, no entanto, de que há uma limitação na configuração responsiva do componente. Ao usar o componente do Flyout com a configuração responsiva, você não deve usá-lo com a ampliação de página inteira. Caso contrário, o Flyout poderá se estender além da borda direita da página.

![chlimage_1-81](assets/chlimage_1-81.png)

### Imagem {#image}

O componente Imagem clássica do Dynamic Media permite que você adicione a funcionalidade do Dynamic Media Classic às suas imagens, como modificadores do Dynamic Media Classic, predefinições de imagens ou visualizador e nitidez. O componente de imagem do Dynamic Media Classic é semelhante a outros componentes de imagem em AEM com funcionalidade especial do Dynamic Media Classic. Neste exemplo, a imagem tem o modificador de URL do Dynamic Media Classic, `&op_invert=1` aplicado.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Título, Texto]**  alternativo - Na guia   Avançado, adicione um título à imagem e ao texto alternativo para os usuários que tiverem gráficos desativados.

**[!UICONTROL URL, Abrir]**  - você pode definir um ativo de para abrir um link. Defina **[!UICONTROL URL]** e **[!UICONTROL Abrir em]** para indicar se deseja que ele seja aberto na mesma janela ou em uma nova janela.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Predefinição]**  do visualizador - selecione uma predefinição do visualizador existente no menu suspenso. Se a predefinição de visualizador que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições do visualizador](/help/assets/managing-viewer-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

**[!UICONTROL Configuração]**  do Dynamic Media Classic - Selecione a configuração do Dynamic Media Classic que deseja usar para buscar predefinições de imagens ativas do Scene7 Publishing System.

**[!UICONTROL Predefinição]**  de imagem - selecione uma predefinição de imagem existente no menu suspenso. Se a predefinição de imagem que você está procurando não estiver visível, pode ser necessário torná-la visível. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md). Não é possível selecionar uma predefinição de visualizador se você estiver usando uma predefinição de imagem e vice-versa.

**[!UICONTROL Formato]**  de saída - Selecione o formato de saída da imagem, por exemplo jpeg. Dependendo do formato de saída selecionado, você pode ter opções de configuração adicionais. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md).

**[!UICONTROL Nitidez]**  - Selecione como deseja tornar a imagem nítida. A nitidez é explicada em detalhes em [*Qualidade de imagem clássica do Adobe Dynamic Media e Práticas recomendadas de nitidez*](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL Modificadores]**  de URL - é possível alterar os efeitos de imagem fornecendo comandos adicionais de imagem do Dynamic Media Classic. Estes estão descritos em [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md) e [Referência de comando](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Pontos de interrupção]**  - se o site estiver respondendo, você deseja ajustar os pontos de interrupção. Os pontos de interrupção devem ser separados por vírgulas `,`.

### Modelo de imagem {#image-template}

[Os ](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) modelos de imagem do Dynamic Media Classic são conteúdo em camadas do Photoshop importado para o Dynamic Media Classic, onde o conteúdo e as propriedades foram parametrizados para variabilidade. O componente do **[!UICONTROL Modelo de imagem]** permite importar imagens e alterar dinamicamente o texto no AEM. Além disso, é possível configurar o componente do **[!UICONTROL Modelo de imagem]** para usar valores do contexto de cliente, de modo que cada usuário experiencie a imagem de uma maneira personalizada.

Clique em **[!UICONTROL Editar]** para configurar o componente. Você pode definir [configurações comuns a todos os componentes do Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents), bem como outras configurações descritas nesta seção.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Referência de arquivo, Largura, Altura]**  - Consulte as configurações comuns a todos os componentes do Dynamic Media Classic.

>[!NOTE]
>
>Os parâmetros e comandos do URL do Dynamic Media Classic não podem ser adicionados diretamente ao URL de referência de arquivo. Eles podem ser definidos somente na interface do componente no painel **[!UICONTROL Parâmetro]**.

**[!UICONTROL Título,]** Texto alternativoNa guia  [!UICONTROL Dynamic Media Classic Image ] Templatetab, adicione um título à imagem e ao texto alternativo para os usuários que tiverem gráficos desativados.

**[!UICONTROL URL, Abrir]** noVocê pode definir um ativo de para abrir um link. Defina o **[!UICONTROL URL]** e, em **[!UICONTROL Abrir em]**, indique se você deseja que ele abra na mesma janela ou em uma nova.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Painel]** de parâmetrosAo importar uma imagem, os parâmetros são pré-preenchidos com informações da imagem. Caso nenhum conteúdo possa ser alterado dinamicamente, essa janela fica vazia.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Alterar o texto dinamicamente {#changing-text-dynamically}

Para alterar o texto dinamicamente, insira o novo texto nos campos e clique em **[!UICONTROL OK]**. Neste exemplo, o **[!UICONTROL Preço]** agora é $50 e o frete é de 99 centavos de dólar.

![chlimage_1-86](assets/chlimage_1-86.png)

O texto na imagem é alterado. É possível redefinir o texto de volta para o valor original ao clicar em **[!UICONTROL Redefinir]** próximo ao campo.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Alterar o texto para refletir o valor de contexto do cliente {#changing-text-to-reflect-the-value-of-a-client-context-value}

Para vincular um campo a um valor de contexto do cliente, clique em **[!UICONTROL Selecionar]** para abrir o menu de contexto do cliente, selecione o contexto do cliente e clique em **[!UICONTROL OK]**. Neste exemplo, o nome é alterado com base na vinculação do Nome com o nome formatado no perfil.

![chlimage_1-88](assets/chlimage_1-88.png)

O texto reflete o nome do cliente conectado no momento. É possível redefinir o texto de volta para o valor original ao clicar em **[!UICONTROL Redefinir]** próximo ao campo.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Como tornar o modelo de imagem do Dynamic Media Classic um link {#making-the-scene-image-template-a-link}

**Para tornar o modelo de imagem do Dynamic Media Classic um link**:

1. Na página com o componente de modelo de imagem do Dynamic Media Classic, clique em **[!UICONTROL Editar]**.
1. No campo de **[!UICONTROL URL]**, insira o URL para qual os usuários são direcionados ao clicarem na imagem. No campo **[!UICONTROL Abrir em]**, selecione se deseja onde o destino seja aberto (uma nova janela ou na mesma).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Clique em **[!UICONTROL OK]**.

### Componente de vídeo  {#video-component}

O componente Dynamic Media Classic **[!UICONTROL Video]** (disponível na seção Dynamic Media Classic do sidekick) usa a detecção de dispositivos e largura de banda para fornecer o vídeo correto a cada tela. Este componente é um reprodutor de vídeo HTML5; é um visualizador único que pode ser usado em todos os canais.

Ele pode ser usado pra conjuntos de vídeos adaptáveis, um único vídeo MP4 ou um único vídeo F4V.

Consulte [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) para obter mais informações sobre como os vídeos funcionam com a integração do Dynamic Media Classic. Além disso, veja como o [componente **vídeo do Dynamic Media Classic** se compara ao componente **video** da fundação](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-91](assets/chlimage_1-91.png)

### Restrições conhecidas do componente de vídeo {#known-limitations-for-the-video-component}

O Adobe DAM e o WCM mostram se um vídeo principal é carregado por upload. Eles não mostram os ativos de proxy a seguir:

* Execuções codificadas do Dynamic Media Classic
* Conjuntos de vídeo adaptativos Dynamic Media Classic

Ao usar um conjunto de vídeo adaptável com o componente de vídeo Dynamic Media Classic, você deve redimensionar o componente para ajustar às dimensões do vídeo.

## Navegador de conteúdo do Dynamic Media Classic {#scene-content-browser}

O navegador de conteúdo do Dynamic Media Classic permite que você visualização conteúdo do Dynamic Media Classic diretamente no AEM. Para acessar o navegador de conteúdo, no Localizador de conteúdo, selecione **[!UICONTROL Dynamic Media Classic]** na interface de usuário otimizada ao toque ou o ícone **[!UICONTROL S7]** na interface de usuário clássica. A funcionalidade é idêntica em ambas as interfaces do usuário.

Caso tenha diversas configurações, o AEM exibe, por padrão, a [configuração padrão](/help/sites-administering/scene7.md#configuring-a-default-configuration). Você pode selecionar configurações diferentes diretamente no navegador de conteúdo do Dynamic Media Classic no menu suspenso.

>[!NOTE]
>
>* Os ativos localizados na pasta ad-hoc não aparecem no navegador de conteúdo do Dynamic Media Classic.
>* Quando [A Pré-visualização segura está ativada](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), os ativos publicados e não publicados no Dynamic Media Classic aparecem no navegador de conteúdo do Dynamic Media Classic.
>* Se você não vir **[!UICONTROL o Dynamic Media Classic]** ou o ícone **[!UICONTROL S7]** como uma opção no navegador de conteúdo, é necessário [configurar o Dynamic Media Classic para trabalhar com AEM](/help/sites-administering/scene7.md).

   >
   >
* Para vídeo, o navegador de conteúdo do Dynamic Media Classic é compatível:
   >
   >
* Conjuntos de vídeos adaptáveis: contêiner de todas as representações de vídeo necessárias para uma reprodução perfeita em diversas telas
>* Vídeo MP4 único
>* Vídeo F4V único


### Pesquisar conteúdo na interface do usuário clássica {#browsing-content-in-the-classic-ui}

Navegue pelo conteúdo no Dynamic Media Classic clicando na guia **[!UICONTROL S7]**.

Você pode alterar a configuração que está acessando selecionando a configuração. As pastas mudam dependendo da configuração selecionada.

![chlimage_1-92](assets/chlimage_1-92.png)

Da mesma maneira que você faz com o localizador de conteúdo do Assets, é possível pesquisar por ativos e filtrar resultados. Contudo, diferente do localizador do Assets, ao inserir uma palavra-chave na guia **[!UICONTROL S7]**, o nome de arquivo *começa com* a sequência de caracteres inserida, em vez de *conter* a palavra-chave no nome.

Por padrão, os ativos são exibidos por nome de arquivo. Além disso, é possível filtrar resultados por tipo de ativo.

>[!NOTE]
>
>Para vídeo, o navegador de conteúdo do Dynamic Media Classic do WCM é compatível:
>
>* Conjuntos de vídeos adaptáveis: contêiner de todas as representações de vídeo necessárias para uma reprodução perfeita em diversas telas
>* Vídeo MP4 único
>* Vídeo F4V único

>



### Procurando ativos do Dynamic Media Classic com o navegador de conteúdo {#searching-for-scene-assets-with-the-content-browser}

Pesquisar ativos do Dynamic Media Classic é semelhante a pesquisar AEM ativos, exceto que ao pesquisar, você está vendo uma visualização remota dos ativos no sistema Dynamic Media Classic, em vez de importá-los diretamente para o AEM.

É possível usar a interface do usuário clássica ou a otimizada para toque para visualizar e pesquisar ativos. Dependendo da interface, a maneira como você pesquisa é levemente diferente.

Ao pesquisar em qualquer uma das interfaces de usuário, você pode filtrar pelos seguintes critérios (mostrados aqui na interface otimizada para toque):

**[!UICONTROL Digite palavras-chave]**  - você pode pesquisar ativos por nome. Ao pesquisar, as palavras-chave inseridas corresponderão às palavras com as quais o nome de arquivo come. Por exemplo, digitar a palavra “nadar” pesquisaria todos os nomes de arquivo de ativo que comecem com as letras nessa ordem. Não se esqueça de clicar em Enter depois de digitar o termo para encontrar o ativo.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Pasta/caminho]**  - O nome da pasta que aparece é baseado na configuração selecionada. Para fazer uma busca detalhada, clique no ícone de pasta e selecione uma subpasta, em seguida clique na marca de seleção para selecioná-la.

Se você inserir uma palavra-chave e selecionar uma pasta, o AEM procura nessa pasta e em todas as subpastas. No entanto, se você não digitar nenhuma palavra-chave ao pesquisar, selecionar a pasta exibirá somente os ativos nessa pasta e não incluirá nenhuma subpasta.

Por padrão, o AEM procura na pasta selecionada e em todas as subpastas.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Tipo de]** ativoSelecione Dynamic Media Classic para navegar pelo conteúdo do Dynamic Media Classic. Essa opção só estará disponível se você já tiver configurado o Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**** ConfiguraçãoSe você tiver mais de uma configuração do Dynamic Media Classic definida no  [!UICONTROL Cloud Services], você pode selecioná-la aqui. Como resultado, a pasta será alterada com base na configuração escolhida.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Tipo de]** ativoNo navegador Dynamic Media Classic, você pode filtrar os resultados para incluir qualquer um dos seguintes: imagens, modelos, vídeos e conjuntos de vídeo adaptáveis. Se você não selecionar nenhum tipo de ativo, o AEM procura todos os tipos de ativo por padrão.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Ao pesquisar por vídeo, você estará procurando uma única representação. Os resultados retornam a execução original (somente &amp;ast;.mp4) e a execução codificada.
>* Ao pesquisar um conjunto de vídeos adaptáveis, você está pesquisando a pasta e todas as subpastas, mas somente se tiver adicionado uma palavra-chave à pesquisa. Caso não tenha adicionado uma palavra-chave, o AEM não pesquisará nas subpastas.

>



**[!UICONTROL Publicar]** statusVocê pode filtrar por ativos com base no status da publicação:   Publicado ou  [!UICONTROL Não publicado]. Se você não selecionar [!UICONTROL Publicar status], o AEM por padrão pesquisará todos os status de publicação.

![chlimage_1-98](assets/chlimage_1-98.png)

