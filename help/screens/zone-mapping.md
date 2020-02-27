---
title: Editor de layout de exibição
seo-title: Editor de layout de exibição
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 6c3b35bc-ea4f-46d4-bfed-2505ae21f764
contentOwner: jsyal
discoiquuid: 679da35f-2b6b-4910-92bd-5dbd4ae3742a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Editor de layout de exibição{#display-layout-editor}

O ***Mapeamento de zonas*** permite que você crie diferentes zonas e use diversos recursos, como vídeos, imagens e texto, que podem ser combinados em uma única tela de formas contextuais. É possível extrair imagens, vídeos e textos e permitir que tudo se misture para criar uma experiência digital intuitiva e interativa. De acordo com os requisitos do projeto, às vezes você precisa de várias zonas em uma exibição.

Por exemplo, uma sequência de produtos com um feed de redes sociais relacionado executado em duas zonas separadas em uma única exibição.

## Visão geral {#overview}

Ao criar uma exibição para o seu canal, você pode escolher diferentes opções de modelos para visualizar/gerenciar o conteúdo no seu canal.

Os seguintes modelos estão disponíveis ao criar zonas para exibição:

* 2x1
* 2x2
* 3x1
* 4x1
* 5x1

O uso de qualquer um desses modelos permite que você crie uma experiência de sinalização digital intuitiva e interativa, em que é possível aproveitar uma variedade de conteúdo em uma única tela.

>[!NOTE]
>
>To learn in-depth about creating channels and displays, see [Managing Channels](managing-channels.md) and [Managing Displays](managing-displays.md) respectively in Authoring Screens.

## Descrição do caso de uso {#use-case-description}

Esse caso de uso permite que você crie um projeto do AEM Screens com um canal que usa o conteúdo e o exibe na tela em várias zonas.

>[!NOTE]
>
>Zonas não dimensionam o conteúdo, e isso deve ser feito antes da inserção do conteúdo nos seus canais.

### Etapas para criar um projeto {#steps-for-creating-a-project}

Siga as etapas abaixo para criar um projeto do AEM Screens que mostra como realizar o mapeamento de zonas para o projeto do AEM Screens:

1. ***Criação de um novo projeto do Screens***

   1. Selecione o link do Adobe Experience Manager (canto superior esquerdo) e, em seguida, o Screens. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).
   1. Click **Create** to create a new Screens project.
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.
   1. Enter the title as **Demo Mapping Project** and click **Create**.
   ![zm1](assets/zm1.gif)

1. ***Criação de uma nova pasta de canais***

   1. Navegue até** Zone Mapping Project**.
   1. Clique em **Criar** na barra de ações. Um assistente será aberto.
   1. Choose the **Channels Folder **and click **Next**.
   1. Enter the Title as **Dual Zone **and click **Create**.
   ![zm2](assets/zm2.gif)

1. ***Criação de um novo canal***

   1. Navigate to the **Zone Mapping Project** you created and select the Channels folder (**Dual Zone**).
   1. Clique em **Criar** na barra de ações. Um assistente será aberto.
   1. Choose the **Sequence Channel **and click **Next**.
   1. Enter the **Title** as **Left** and click **Create**.
   Da mesma forma, crie outro canal de sequência como **Direito** no **Projeto de mapeamento de zonas**.

   ![zm3](assets/zm3.gif)

1. ***Adição de conteúdo aos canais***

   1. Navigate to the **Zone Mapping Project** you created and select the **Channel** you created.
   1. Click **Edit** from the action bar.
   1. The editor for the **Left** opens. Clique no ícone que alterna o painel lateral no lado esquerdo da barra de ações para abrir os ativos e componentes.
   1. Arraste e solte os componentes que você deseja adicionar ao seu canal.
   Da mesma forma, adicione conteúdo também ao canal **Direito**.

   ![zm4](assets/zm4.gif)

   >[!NOTE]
   >
   >Você pode preencher o conteúdo nos seus canais com diferentes ativos (imagens, vídeos) de acordo com os requisitos do seu projeto.

1. ***Criação de uma nova localização***

   1. Navigate to the** Zone Mapping Project** and select the **Locations** folder.
   1. Click **Create** next to the plus icon in the action bar. Um assistente será aberto.
   1. Select **Location** from the wizard and click **Next**.
   1. Enter the **Title** for your location (enter the title as **San Jose**) and click **Create**.
   ![zm5](assets/zm5.gif)

1. ***Criação de uma nova exibição para San Jose***

   1. Navigate to the location where you want to create your display (**Demo Mapping Project** --> **Locations** --> **San Jose**) and select **San Jose**.
   1. Clique em **Criar** na barra de ações. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your display location (enter the title as **Dual Zone**).
   1. Under the **Display** tab, choose the details of the Layout. Choose the Resolution as **Full HD**.
   1. Choose the **Number of Devices Horizontally** as **2**. Choose the **Number of Devices Vertically** as **1**.
   1. Clique em **Criar**.
   ![zm6](assets/zm6.gif)

1. ***Atribuição de um canal***

   1. Navigate to the display from **Zone Mapping Project** --> **Locations** --> **San Jose** --> **Dual Zone Display**.
   1. Select **Dual Zone Display **and tap/click **Assign Channel** from the action bar, Or,
   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **A caixa de diálogo Atribuição do canal **é aberta.
   1. Enter the **Channel Role** as **Zone**.
   1. Selecione Canal de referência por caminho. Select the channel folder path (**Zone Mapping Project **--> **Channels** --> **Dual Zone** ) in the Channel.
   1. Select the **Priority** for this channel as **1**. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Clique em **Salvar**.
   ![zm7](assets/zm7.gif)

1. ***Registro e atribuição do dispositivo***

   1. Inicialize uma janela de navegador separada. Vá para o player do Screens usando o navegador da Web ou inicie o aplicativo do AEM Screens. Ao abrir o dispositivo, você perceberá o estado do dispositivo como não registrado.
   1. From the AEM dashboard, navigate to **Zone Mapping Project** --> **Devices**.
   1. Clique em** Gerenciador de dispositivos** na barra de ações.
   1. Click **Device Registration** and you will see the pending devices.
   1. Select the device you want to register and click **Register Device**.
   1. Você precisará validar o código verificando-o no navegador da web ou no player do AEM Screens. Click **Validate** to navigate to **Device Registration** screen.
   1. Enter **Title** as **Zone Device** and click **Register** and the device will be registered.
   1. Click **Assign Display** to move on to the next step where you assign the device to a display.
   1. Click **Assign Device** fand select the display path for your channel () as */content/screens/Test_Project/Locations/TestLocation/TestDisplay*. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.
   ![zm8](assets/zm8.gif)

1. ***Criação de uma exibição de várias zonas***

   1. Navigate and select the display from **Zone Mapping Project** --> **Locations** --> **San Jose **--> **Dual Zone **display and click **Dashboard** from the action bar.
   1. Selecione o ícone à esquerda de **Configuração do dispositivo** do seu player, no painel **DISPOSITIVOS**, e clique em **Propriedades**.
   1. Navegue até a guia **Configuração do dispositivo** e preencha os campos **Mapeamento** e **Modelo**. Enter *{&quot;a1&quot;:&quot;${display.channel}/left&quot;, &quot;a2&quot;: &quot;${display.channel}/right&quot;}* in the **Mapping** field and template as *grid-2x1*.
   1. Click **Save &amp; Close** and reload the player.
   >[!NOTE]
   >
   >***Noções básicas sobre mapeamento e modelos na configuração do dispositivo:***
   >
   >* Os identificadores “a1” e “a2” correspondem às zonas definidas no modelo, isto é, “screens-zone-a1” e “screens-zone-a2”.
   >* ${display.channel}/left&quot; aponta para o canal que será incorporado na zona, sendo que &quot;display.channel&quot; aponta para o caminho do canal atual na exibição. Dessa forma, os filhos “left” e “right” do canal são incorporados.


   ![screen_shot_2018-01-22at114708am](assets/screen_shot_2018-01-22at114708am.png)

#### Visualização de conteúdo no player do AEM Screens {#viewing-content-in-aem-screens-player}

Carregue o Player do AEM Screens ou use o navegador da web.

Você notará o conteúdo de ambos os canais (esquerdo e direito) exibidos no player do Screens. O conteúdo aparece como uma zona de exibição 2x1.

![](do-not-localize/screen_shot_2018-01-22at120206pm.png)

### Inferência {#inference}

Mapeamento de zonas que usa um dos modelos disponíveis ao criar um canal no AEM Screens e que permite que você aplique o nivelamento no lado do cliente. É possível criar zonas diferentes na sua tela e preenchê-las com vídeos, imagens e outros recursos disponíveis.
