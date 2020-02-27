---
title: Loop de aquisição de várias zonas para uma única zona
seo-title: Loop de aquisição de várias zonas para uma única zona
description: 'Siga esta página para saber mais sobre Multi Zone to Single Zone Takeover Loop em um projeto do AEM Screens.  '
seo-description: 'Loop de aquisição de várias zonas para uma única região em um projeto do AEM Screens.  '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Loop de aquisição de várias zonas para uma única zona{#single-zoneto-multizone}

## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout de várias zonas que alterna com um canal de layout de zona única. Cada canal tem ativos de imagem/vídeo em sequência.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de saber como:

* **[Criar e gerenciar canais](/help/screens/managing-channels.md)**
* **[Criar e gerenciar locais](/help/screens/managing-locations.md)**
* **[Criar e gerenciar programações](/help/screens/managing-schedules.md)**
* **[Registro do dispositivo](/help/screens/device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um projeto do AEM Screens chamado de **TakeoverLoop**, conforme mostrado abaixo.

   >[!NOTE]
   >
   >Para saber mais sobre como criar e gerenciar projetos no AEM Screens, consulte [Criar um projeto](/help/screens/creating-a-screens-project.md).

   ![](assets/takeover-loop1.png)

1. **Criação de um canal de tela dividida**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.
   1. Selecione Canal **de tela dividida da barra** esquerda L no assistente e crie o canal chamado **MultiZoneLayout**.

      ![](assets/takeover-loop2.png)

   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra um vídeo, uma imagem e um banner de texto no canal, como mostrado abaixo.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **Criação de um canal 2X2 com quatro imagens**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo Canal **de tela dividida** 2X2 no assistente e crie o canal chamado **TwobyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor e arraste e solte quatro imagens (quatro zonas diferentes) nesse canal, como mostrado abaixo.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **Criação de um canal de tela dividida 1X2 com duas imagens**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo **1X2 de Canal** de Tela Dividida do assistente e crie o canal chamado **OneTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor e arraste e solte duas imagens (duas zonas diferentes) nesse canal, como mostrado abaixo.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **Criação de um canal com um vídeo em tela cheia**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo de Canal **de** sequência no assistente e crie o canal chamado **FullScreensVideo**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor, arrastar e soltar o componente de vídeo nesse canal e adicionar o vídeo desejado, como mostrado abaixo.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)