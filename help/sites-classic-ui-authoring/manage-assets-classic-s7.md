---
title: Adicionar recursos do Dynamic Media Classic à sua página
seo-title: Adding Dynamic Media Classic features to your page
description: O Adobe Dynamic Media Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email, impressão e monitores conectados à Internet.
seo-description: Adobe Dynamic Media Classic is a hosted solution for managing, enhancing, publishing, and delivering rich media assets to Web, mobile, email, and Internet-connected displays and print.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
exl-id: 93921d23-a2bf-43b6-b002-58a7482b22b0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3383'
ht-degree: 0%

---

# Adicionar recursos do Dynamic Media Classic à sua página{#adding-scene-features-to-your-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Dynamic Media Classic é uma solução hospedada para gerenciar, aprimorar, publicar e fornecer ativos de mídia avançada para Web, dispositivos móveis, email, impressão e monitores conectados à Internet.

Você pode visualizar AEM ativos publicados no Dynamic Media Classic em vários visualizadores:

* Zoom
* Flyout
* Vídeo
* Modelo da imagem
* Imagem

Você pode publicar ativos digitais diretamente do AEM para o Dynamic Media Classic e pode publicar ativos digitais do Dynamic Media Classic para o AEM.

Esta seção descreve como publicar ativos digitais do AEM para o Dynamic Media Classic e vice-versa. Os visualizadores também são descritos detalhadamente. Para obter informações sobre como configurar o AEM para o Dynamic Media Classic, consulte [Integração do Dynamic Media Classic com o AEM](/help/sites-administering/scene7.md).

Consulte também [Adição de mapas de imagem](/help/assets/image-maps.md).

Para obter mais informações sobre o uso de componentes de vídeo com AEM, consulte o seguinte:

* [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Se os ativos do Dynamic Media Classic não forem exibidos corretamente, verifique se a Mídia dinâmica é [desativado](/help/assets/config-dynamic.md#disabling-dynamic-media) e, em seguida, atualize a página.

## Publicar manualmente no Dynamic Media Classic a partir de ativos {#manually-publishing-to-scene-from-assets}

Você pode publicar ativos digitais no Dynamic Media Classic pelo console Assets na interface clássica ou diretamente do ativo.

>[!NOTE]
>
>AEM publica no Dynamic Media Classic de forma assíncrona. Depois de clicar em **[!UICONTROL Publicar]**, pode levar vários segundos para que o ativo seja publicado no Dynamic Media Classic.

### Publicação por meio do console Assets {#publishing-from-the-assets-console}

Para publicar no Dynamic Media Classic por meio do console Assets se os ativos estiverem em uma pasta de destino do Dynamic Media Classic:

1. Na interface AEM clássica, clique em **[!UICONTROL Ativos digitais]** para acessar o gerenciador de ativos digitais.

1. Selecione o ativo (ou ativos) ou a pasta na pasta de destino que deseja publicar no Dynamic Media Classic, clique com o botão direito do mouse e selecione **[!UICONTROL Publicar no Dynamic Media Classic]**. Como alternativa, você pode selecionar **[!UICONTROL Publicar no Dynamic Media Classic]** do **[!UICONTROL Ferramentas]** menu.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Acesse a Dynamic Media Classic e confirme se os ativos estão disponíveis.

   >[!NOTE]
   >
   >Se os ativos não estiverem em uma pasta sincronizada do Dynamic Media Classic, **[!UICONTROL Publicar no Dynamic Media Classic]** em ambos os menus é visível, mas desativado.

### Publicação a partir de um ativo {#publishing-from-an-asset}

Você pode publicar manualmente um ativo, desde que ele esteja localizado na pasta sincronizada do Dynamic Media Classic.

>[!NOTE]
>
>Se o ativo não estiver localizado na pasta sincronizada do Dynamic Media Classic, o link para **[!UICONTROL Publicar no Dynamic Media Classic]** não está disponível.

**Publicar no Dynamic Media Classic diretamente de um ativo digital**:

1. Em AEM, clique em **[!UICONTROL Ativos digitais]** para acessar o gerenciador de ativos digitais.

1. Clique duas vezes para abrir um ativo.

1. No painel de detalhes do ativo, selecione **[!UICONTROL Publicar no Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. O link muda para **[!UICONTROL Publicando ...]** e depois **[!UICONTROL Publicado]**. Vá para a Dynamic Media Classic e confirme se o ativo está disponível.

   >[!NOTE]
   >
   >Se o ativo não for publicado corretamente no Dynamic Media Classic, o link será alterado para **[!UICONTROL Falha na publicação]**. Se o ativo já tiver sido publicado no Dynamic Media Classic, o link exibirá **[!UICONTROL Publicar novamente no Dynamic Media Classic]**. A republicação permite fazer alterações em um ativo no AEM e publicá-lo novamente.

### Publicar ativos de fora da pasta de destino do CQ {#publishing-assets-from-outside-the-cq-target-folder}

O Adobe recomenda publicar ativos no Dynamic Media Classic somente a partir de ativos na pasta de destino do Dynamic Media Classic. No entanto, se você precisar fazer upload de ativos de uma pasta fora da pasta de destino, ainda poderá fazer isso fazendo upload deles para um *ad-hoc* no Dynamic Media Classic.

Faça isso configurando a configuração da Nuvem para a página em que o ativo será exibido. Em seguida, adicione um componente Dynamic Media Classic à página e arraste e solte um ativo no componente. Depois que as propriedades da página forem definidas para essa página, uma **[!UICONTROL Publicar no Dynamic Media Classic]** é exibido e, quando selecionado, aciona o upload para o Dynamic Media Classic.

>[!NOTE]
>
>Os ativos que estão na pasta ad-hoc não aparecem no navegador de conteúdo do Dynamic Media Classic.

**Publicar ativos que residem fora da pasta de destino CQ**:

1. Em AEM na interface clássica, clique em **[!UICONTROL Sites]** e navegue até a página da Web à qual deseja adicionar um ativo digital que ainda não foi publicado no Dynamic Media Classic. (As regras de herança de página normal se aplicam.)

1. No sidekick, clique no botão **[!UICONTROL Página]** ícone e, em seguida, clique em **[!UICONTROL Propriedades da página]**.

1. Clique em **[!UICONTROL Cloud Services] > [!UICONTROL Adicionar serviços] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Na lista suspensa Adobe Dynamic Media Classic , selecione a configuração desejada e clique em **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Na página da Web, adicione um componente Dynamic Media Classic (Scene7) ao local desejado na página.
1. No localizador de conteúdo, arraste um ativo digital para o componente. Você verá um link para **[!UICONTROL Verificar status de publicação do Dynamic Media Classic]**.

   >[!NOTE]
   >
   >Se o ativo digital estiver na pasta de destino CQ, nenhum link para **[!UICONTROL Verificar status de publicação do Dynamic Media Classic]** é exibido. Os ativos são colocados no componente.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Clique em **[!UICONTROL Verificar status de publicação do Dynamic Media Classic]**. Se o ativo não estiver publicado, AEM o publica no Dynamic Media Classic. Após o upload, o ativo é localizado na pasta ad-hoc. Por padrão, a pasta ad-hoc está localizada no `name_of_the_company/CQ5_adhoc`. Você pode [configure isso, se necessário](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Se o ativo não estiver em uma pasta sincronizada do Dynamic Media Classic e não houver nenhuma configuração de nuvem do Dynamic Media Classic associada à página atual, o upload falhará.

## Componentes do Dynamic Media Classic (Scene7) {#scene-components}

Os seguintes componentes do Dynamic Media Classic estão disponíveis no AEM:

* Zoom
* Flyout (Zoom)
* Modelo da imagem
* Imagem
* Vídeo

>[!NOTE]
>
>Esses componentes não estão disponíveis por padrão e precisam ser selecionados em **[!UICONTROL Design]** antes de usar.

Após a sua disponibilização no **[!UICONTROL Design]** , é possível adicionar os componentes à página como qualquer outro componente AEM. Os ativos que ainda não foram publicados na Dynamic Media Classic são publicados na Dynamic Media Classic se estiverem em uma pasta sincronizada, em uma página ou com uma configuração da nuvem do Dynamic Media Classic.

### Aviso de fim de vida útil dos visualizadores do Flash {#flash-viewers-end-of-life-notice}

A partir de 31 de janeiro de 2017, a Adobe Dynamic Media Classic encerrou oficialmente o suporte para a plataforma do visualizador de Flashes.

### Adicionar um componente Dynamic Media Classic a uma página {#adding-a-scene-component-to-a-page}

Adicionar um componente do Dynamic Media Classic a uma página é o mesmo que adicionar um componente a qualquer página. Os componentes do Dynamic Media Classic são descritos detalhadamente nas seções a seguir.

**Para adicionar um componente/visualizador do Dynamic Media Classic a uma página na interface clássica**:

1. Em AEM, abra a página à qual deseja adicionar o componente Dynamic Media Classic.

1. Se nenhum componente do Dynamic Media Classic estiver disponível, clique na régua do sidekick para entrar **[!UICONTROL Design]** , clique em **[!UICONTROL Editar]** parsys e selecione todas as **[!UICONTROL Dynamic Media Classic]** componentes para disponibilizá-los.

1. Retornar para **[!UICONTROL Editar]** clicando no lápis no sidekick.

1. Arraste um componente do **[!UICONTROL Dynamic Media Classic]** no sidekick até a página no local desejado.

1. Clique em **[!UICONTROL Editar]** para abrir o componente.

1. Edite o componente conforme necessário e clique em **[!UICONTROL OK]** para salvar as alterações.

### Adicionar experiências de visualização interativas a um site responsivo {#adding-interactive-viewing-experiences-to-a-responsive-website}

Design responsivo para seus ativos significa que eles se adaptam dependendo de onde são exibidos. Com um design responsivo, os mesmos ativos são exibidos efetivamente em vários dispositivos.

**Para adicionar uma experiência de visualização interativa a um site responsivo na interface clássica**:

1. Faça logon no AEM e certifique-se de ter [Adobe Dynamic Media Classic Cloud Services configurado](/help/sites-administering/scene7.md#configuring-scene-integration) e que os componentes do Dynamic Media Classic estão disponíveis.

   >[!NOTE]
   >
   >Se os componentes do WCM Dynamic Media Classic não estiverem disponíveis, certifique-se de ativá-los por meio do **[!UICONTROL Design] modo.

1. Em um site com os componentes do Dynamic Media Classic ativados, arraste um **[!UICONTROL Imagem]** para a página.
1. Edite o componente e ajuste os pontos de interrupção no **[!UICONTROL Configurações do Dynamic Media Classic]** guia .

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Confirme se os visualizadores estão sendo redimensionados de forma responsiva e se todas as interações estão otimizadas para desktop, tablet e dispositivo móvel.

### Configurações comuns a todos os componentes do Dynamic Media Classic {#settings-common-to-all-scene-components}

Embora as opções de configuração variem, as seguintes são comuns a todos os componentes do Dynamic Media Classic:

* **[!UICONTROL Referência de arquivo]** - Navegue até o arquivo que deseja referenciar. A referência de arquivo mostra o URL do ativo e não necessariamente o URL completo do Dynamic Media Classic, incluindo os comandos e parâmetros de URL. Não é possível adicionar comandos e parâmetros de URL do Dynamic Media Classic neste campo. Eles devem ser adicionados por meio da funcionalidade correspondente no componente.
* **[!UICONTROL Largura]** - Permite definir a largura.
* **[!UICONTROL Altura]** - Permite definir a altura.

Você define essas opções de configuração clicando duas vezes em um componente do Dynamic Media Classic, por exemplo, ao abrir um **[!UICONTROL Zoom]** componente:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

O componente de Zoom do HTML5 exibe uma imagem maior quando você pressiona o botão +.

O ativo tem ferramentas de zoom na parte inferior. Clique em **[!UICONTROL +]** para aumentar. Clique em **[!UICONTROL -]** para reduzir. Clicar **[!UICONTROL x]** ou a seta de redefinição de zoom traz a imagem de volta ao tamanho original de importação. Clique nas setas diagonais para abri-la em tela cheia. Clique em **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode configurar [configurações comuns a todos os componentes do Dynamic Media Classic](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### Flyout {#flyout}

No componente do Flyout HTML5, o ativo é mostrado como tela dividida; deixou o ativo no tamanho especificado; à direita, a parte de zoom é exibida. Clique em **[!UICONTROL Editar]** para configurar o componente. Com esse componente, você pode configurar [configurações comuns a todos os componentes do Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Se o seu componente do Flyout usa um tamanho personalizado, esse tamanho é usado e a configuração responsiva do componente é desativada.
>
>Se o componente do Flyout usar o tamanho padrão, como definido na variável [!UICONTROL Design] exibição, o tamanho padrão é usado e o componente é estendido para acomodar o tamanho do layout da página com a configuração responsiva do componente ativada. Esteja ciente, no entanto, de que há uma limitação na configuração responsiva do componente. Ao usar o componente do Flyout com configuração responsiva, você não deve usá-lo com o trecho de página completo. Caso contrário, o Flyout poderá se estender além da borda direita da página.

![chlimage_1-81](assets/chlimage_1-81.png)

### Imagem {#image}

O componente Imagem do Dynamic Media Classic permite que você adicione funcionalidade do Dynamic Media Classic a suas imagens, como modificadores do Dynamic Media Classic, predefinições de imagem ou visualizador e nitidez. O componente de imagem da Dynamic Media Classic é semelhante a outros componentes de imagem em AEM com funcionalidade especial do Dynamic Media Classic. Neste exemplo, a imagem tem o modificador Dynamic Media Classic URL, `&op_invert=1` aplicada.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Título, Texto alternativo]** - No [!UICONTROL Avançado] , adicione um título à imagem e um texto alternativo para os usuários que tenham os gráficos desativados.

**[!UICONTROL URL, Abrir em]** - É possível definir um ativo de para abrir um link. Defina as **[!UICONTROL URL]** e **[!UICONTROL Abrir em]** para indicar se deseja abri-la na mesma janela ou em uma nova janela.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Predefinição do visualizador]** - Selecione uma predefinição de visualizador existente no menu suspenso. Se a predefinição do visualizador que você está procurando não estiver visível, talvez seja necessário torná-la visível. Consulte [Gerenciar predefinições do visualizador](/help/assets/managing-viewer-presets.md). Não é possível selecionar uma predefinição do visualizador se você estiver usando uma predefinição de imagem e vice-versa.

**[!UICONTROL Configuração do Dynamic Media Classic]** - Selecione a configuração do Dynamic Media Classic que deseja usar para buscar predefinições de imagens ativas do Sistema de Publicação Scene7.

**[!UICONTROL Predefinição de imagem]** - Selecione uma predefinição de imagem existente no menu suspenso. Se a predefinição de imagem que você está procurando não estiver visível, talvez seja necessário torná-la visível. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md). Não é possível selecionar uma predefinição do visualizador se você estiver usando uma predefinição de imagem e vice-versa.

**[!UICONTROL Formato de saída]** - Selecione o formato de saída da imagem, por exemplo jpeg. Dependendo do formato de saída selecionado, você pode ter opções de configuração adicionais. Consulte [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md).

**[!UICONTROL Nitidez]** - Selecione como deseja ajustar a nitidez da imagem. A nitidez é explicada detalhadamente em [*Práticas recomendadas de qualidade e nitidez da imagem do Adobe Dynamic Media Classic*](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL Modificadores de URL]** - Você pode alterar os efeitos da imagem fornecendo comandos adicionais de imagem do Dynamic Media Classic. Estes são descritos em [Gerenciar predefinições de imagens](/help/assets/managing-image-presets.md) e [Referência de comando](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Pontos de interrupção]** - Se o seu site for responsivo, você deseja ajustar os pontos de interrupção. Os pontos de interrupção devem ser separados por vírgulas `,`.

### Modelo da imagem {#image-template}

[Modelos de imagem do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) são conteúdo em camadas do Photoshop que foi importado para o Dynamic Media Classic, onde o conteúdo e as propriedades foram parametrizadas para oferecer variabilidade. O **[!UICONTROL Modelo de imagem]** permite que você importe imagens e altere o texto dinamicamente no AEM. Além disso, você pode configurar a variável **[!UICONTROL Modelo de imagem]** componente para usar valores do contexto do cliente, de modo que cada usuário experimente a imagem de uma maneira personalizada.

Clique em **[!UICONTROL Editar]** para configurar o componente. Você pode configurar [configurações comuns a todos os componentes do Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) assim como outras configurações descritas nesta seção.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Referência de arquivo, Largura, Altura]** - Consulte as configurações comuns a todos os componentes do Dynamic Media Classic.

>[!NOTE]
>
>Comandos e parâmetros de URL do Dynamic Media Classic não podem ser adicionados diretamente ao URL de referência de arquivo. Eles só podem ser definidos na interface do componente no **[!UICONTROL Parâmetro]** painel.

**[!UICONTROL Título, Texto alternativo]** No [!UICONTROL Modelo de imagem do Dynamic Media Classic] , adicione um título à imagem e um texto alternativo para os usuários que tenham os gráficos desativados.

**[!UICONTROL URL, Abrir em]** É possível definir um ativo de para abrir um link. Defina as **[!UICONTROL URL]** e **[!UICONTROL Abrir em]** indique se deseja que ele seja aberto na mesma janela ou em uma nova janela.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Painel de parâmetros]** Ao importar uma imagem, os parâmetros são preenchidos previamente com informações da imagem. Se não houver conteúdo que possa ser alterado dinamicamente, essa janela ficará vazia.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Alteração dinâmica do texto {#changing-text-dynamically}

Para alterar o texto dinamicamente, insira o novo texto nos campos e clique em **[!UICONTROL OK]**. Neste exemplo, a variável **[!UICONTROL Preço]** agora é de US$ 50 e o frete é de 99 centavos.

![chlimage_1-86](assets/chlimage_1-86.png)

O texto na imagem muda. Você pode redefinir o texto de volta ao valor original clicando em **[!UICONTROL Redefinir]** ao lado do campo .

![chlimage_1-87](assets/chlimage_1-87.png)

#### Alteração do texto para refletir o valor de contexto do cliente {#changing-text-to-reflect-the-value-of-a-client-context-value}

Para vincular um campo a um valor de contexto de cliente, clique em **[!UICONTROL Selecionar]** para abrir o menu de contexto do cliente, selecione o contexto do cliente e clique em **[!UICONTROL OK]**. Neste exemplo, o nome é alterado com base na vinculação do Nome ao nome formatado no perfil.

![chlimage_1-88](assets/chlimage_1-88.png)

O texto reflete o nome do usuário conectado no momento. Você pode redefinir o texto de volta ao valor original clicando em **[!UICONTROL Redefinir]** ao lado do campo .

![chlimage_1-89](assets/chlimage_1-89.png)

#### Como tornar o modelo de imagem do Dynamic Media Classic um link {#making-the-scene-image-template-a-link}

**Para transformar o modelo de imagem do Dynamic Media Classic em um link**:

1. Na página com o componente de modelo de imagem do Dynamic Media Classic, clique em **[!UICONTROL Editar]**.
1. No **[!UICONTROL URL]** , insira o URL para o qual os usuários são direcionados ao clicarem na imagem. No **[!UICONTROL Abrir em]** , selecione se deseja que o target seja aberto (uma nova janela ou a mesma).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Clique em **[!UICONTROL OK]**.

### Componente de vídeo {#video-component}

A Dynamic Media Classic **[!UICONTROL Vídeo]** O componente (disponível na seção Dynamic Media Classic do sidekick) usa a detecção de dispositivo e de largura de banda para veicular o vídeo correto em cada tela. Este componente é um reprodutor de vídeo HTML5; é um visualizador único que pode ser usado entre canais.

Ele pode ser usado para conjuntos de vídeos adaptáveis, um único vídeo MP4 ou um único vídeo F4V.

Consulte [Vídeo](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) para obter mais informações sobre como os vídeos funcionam com a integração do Dynamic Media Classic. Além disso, veja como [o **Vídeo Dynamic Media Classic** componente compara com a base **vídeo** componente](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-91](assets/chlimage_1-91.png)

### Limitações conhecidas do componente de vídeo {#known-limitations-for-the-video-component}

O Adobe DAM e o WCM mostram se um vídeo principal foi carregado. Eles não mostram esses ativos de proxy:

* Representações codificadas do Dynamic Media Classic
* Conjuntos de vídeo adaptáveis Dynamic Media Classic

Ao usar um conjunto de vídeos adaptáveis com o componente de vídeo do Dynamic Media Classic, você deve redimensionar o componente para ajustar as dimensões do vídeo.

## Navegador de conteúdo do Dynamic Media Classic {#scene-content-browser}

O navegador de conteúdo do Dynamic Media Classic permite exibir o conteúdo do Dynamic Media Classic diretamente no AEM. Para acessar o navegador de conteúdo, no Localizador de conteúdo, selecione **[!UICONTROL Dynamic Media Classic]** na interface otimizada para toque ou na **[!UICONTROL S7]** na interface do usuário clássica. A funcionalidade é idêntica em ambas as interfaces do usuário.

Se você tiver várias configurações, AEM por padrão, a variável [configuração padrão](/help/sites-administering/scene7.md#configuring-a-default-configuration). Você pode selecionar configurações diferentes diretamente no navegador de conteúdo do Dynamic Media Classic no menu suspenso.

>[!NOTE]
>
>* Os ativos localizados na pasta ad-hoc não aparecem no navegador de conteúdo do Dynamic Media Classic.
>* When [A Visualização segura está ativada](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), os ativos publicados e não publicados no Dynamic Media Classic aparecem no navegador de conteúdo do Dynamic Media Classic.
>* Se você não vir **[!UICONTROL Dynamic Media Classic]** ou **[!UICONTROL S7]** como uma opção no navegador de conteúdo, é necessário [configurar o Dynamic Media Classic para funcionar com o AEM](/help/sites-administering/scene7.md).
>
>* Para vídeo, o navegador de conteúdo do Dynamic Media Classic é compatível com:
>
>* Conjuntos de vídeos adaptáveis: contêiner de todas as representações de vídeo necessárias para uma reprodução contínua em várias telas
>* Vídeo MP4 único
>* Vídeo F4V único


### Navegação pelo conteúdo na interface clássica {#browsing-content-in-the-classic-ui}

Navegue pelo conteúdo no Dynamic Media Classic clicando no link **[!UICONTROL S7]** guia .

Você pode alterar a configuração que está acessando selecionando a configuração . As pastas mudam, dependendo da configuração selecionada.

![chlimage_1-92](assets/chlimage_1-92.png)

Assim como no localizador de conteúdo para Ativos, você pode pesquisar por ativos e filtrar resultados. No entanto, ao contrário do Localizador de Ativos, ao inserir uma palavra-chave no **[!UICONTROL S7]** guia , o nome do arquivo *começa com* a string inserida, em vez de *contendo* a palavra-chave no nome do arquivo.

Por padrão, os ativos são exibidos por nome de arquivo. Também é possível filtrar os resultados por tipo de ativo.

>[!NOTE]
>
>Para vídeo, o navegador de conteúdo Dynamic Media Classic do WCM é compatível com:
>
>* Conjuntos de vídeos adaptáveis: contêiner de todas as representações de vídeo necessárias para uma reprodução contínua em várias telas
>* Vídeo MP4 único
>* Vídeo F4V único
>


### Pesquisar ativos do Dynamic Media Classic com o navegador de conteúdo {#searching-for-scene-assets-with-the-content-browser}

Pesquisar ativos do Dynamic Media Classic é semelhante a pesquisar ativos AEM exceto que, ao pesquisar, você está realmente vendo uma visualização remota dos ativos no sistema Dynamic Media Classic, em vez de importá-los diretamente para o AEM.

Você pode usar a interface clássica ou a interface otimizada para toque para exibir e procurar ativos. Dependendo da interface, a forma como você pesquisa é um pouco diferente.

Ao pesquisar em qualquer uma das interfaces do usuário, você pode filtrar pelos seguintes critérios (mostrados aqui na interface otimizada para toque):

**[!UICONTROL Inserir palavras-chave]** - Você pode pesquisar ativos por nome. Ao pesquisar as palavras-chave inseridas, o nome do arquivo começa com isso. Por exemplo, digitar a palavra &quot;nadar&quot; procuraria quaisquer nomes de arquivo de ativo que comecem com essas letras nessa ordem. Certifique-se de clicar em Inserir depois de digitar o termo para localizar o ativo.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Pasta/caminho]** - O nome da pasta que aparece é baseado na configuração selecionada. Você pode detalhar até níveis inferiores clicando no ícone de pasta, selecionando uma subpasta e, em seguida, clicando na marca de seleção para selecioná-la.

Se você inserir uma palavra-chave e selecionar uma pasta, o AEM pesquisará essa pasta e quaisquer subpastas. No entanto, se você não inserir nenhuma palavra-chave ao pesquisar, selecionar a pasta mostrará apenas os ativos nessa pasta e não incluirá nenhuma subpasta.

Por padrão, o AEM pesquisa a pasta selecionada e todas as subpastas.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Tipo de ativo]** Selecione Dynamic Media Classic para navegar pelo conteúdo do Dynamic Media Classic. Essa opção só estará disponível se você já tiver configurado o Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**[!UICONTROL Configuração]** Se você tiver mais de uma configuração Dynamic Media Classic definida em [!UICONTROL Cloud Services], você pode selecioná-lo aqui. Como resultado, a pasta será alterada com base na configuração escolhida.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Tipo de ativo]** No navegador Dynamic Media Classic, você pode filtrar resultados para incluir qualquer um dos seguintes itens: imagens, modelos, vídeos e conjuntos de vídeos adaptáveis. Se você não selecionar nenhum tipo de ativo, AEM por padrão pesquisa todos os tipos de ativo.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Ao pesquisar vídeo, você está pesquisando uma única representação. Os resultados retornam a representação original (somente o &amp;ast;.mp4) e a representação codificada.
>* Ao pesquisar um conjunto de vídeos adaptáveis, você está pesquisando a pasta e todas as subpastas, mas somente se tiver adicionado uma palavra-chave à pesquisa. Se você não tiver adicionado uma palavra-chave, o AEM não pesquisará nas subpastas.
>


**[!UICONTROL Publicar status]** Você pode filtrar por ativos com base no status da publicação: [!UICONTROL Publicado] ou [!UICONTROL Não publicado]. Se você não selecionar nenhuma [!UICONTROL Status da publicação], AEM por padrão pesquisa todos os status de publicação.

![chlimage_1-98](assets/chlimage_1-98.png)
