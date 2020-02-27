---
title: Trabalhar com o AEM Screens Player
seo-title: Trabalhar com o Player do Screens
description: Siga esta página para saber mais sobre o Player do Screens. Ela também explica a Interface do usuário do administrador e o Seletor de canal.
seo-description: Siga esta página para saber mais sobre o Player do Screens. Ela também explica a Interface do usuário do administrador e o Seletor de canal.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Working with AEM Screens Player{#working-with-aem-screens-player}

Você pode gerenciar o conteúdo do canal e outras configurações no AEM Screens Player.

>[!NOTE]
>
>Pressione ***Ctrl+Cmd+F*** para sair do modo de tela cheia do Player do AEM Screens para OS X.

Depois que você atribui um canal a uma exibição, o Player do AEM Screens exibe o conteúdo. Você pode definir as configurações do seu player usando as preferências da interface do usuário do administrador (no painel) ou no próprio player.

## Uso do painel Dispositivos {#using-the-device-dashboard}

Você pode configurar as preferências do seu dispositivo no painel Dispositivos, acessível na sua instância de criação do AEM.

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --> ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Clique no dispositivo para abrir o painel Dispositivos.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### A Interface do usuário do administrador {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. Além disso, se você desativar essa opção no painel Dispositivos, o usuário não poderá abrir a interface do usuário do administrador.

Para exibir a interface do usuário do administrador no player do Screens, pressione e segure no canto superior esquerdo para abrir o menu Admin, no player do AEM Screens ativado para toque ou com o uso de um mouse. Ele mostra informações após a conclusão do registro e o carregamento dos canais.

>[!NOTE]
>
>Além disso, você pode visualizar o tempo de atividade do aplicativo Player do AEM Screens para verificar seu status de integridade.

![chlimage_1-3](assets/chlimage_1-3.gif)

Se você selecionar a opção **Configuração** no menu lateral, também poderá redefinir **Firmware**, **Preferências** ou **Para fábrica** nessa caixa de diálogo.

Além disso, você pode especificar o número máximo de arquivos de log a serem mantidos para um player do AEM Screens no **Máximo Não. dos arquivos de log a serem mantidos**. Consulte a captura de tela abaixo para obter mais detalhes.

>[!NOTE]
>
>A opção **Atualizar firmware** só funciona no cordova, como players Android.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Você pode limpar o cache de canais e aplicativos da Interface do usuário do administrador no player do AEM Screens.

Selecione **Cache de conteúdo** no painel lateral para atualizar o cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### O Seletor de canal {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

Além disso, se você desativar essa opção no painel Dispositivos, o usuário não poderá controlar as preferências de canal no Player do Screens.

Você pode alternar e controlar as configurações do seu canal no Player do Screens.

Para exibir o seletor de canais do player, pressione e segure no canto inferior esquerdo para abrir o seletor de canais, que permite trocar canais e usar outros recursos.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Você também pode ativar ou desativar o menu do administrador e o seletor de canais para o player no player do Screens.
>
>(Consulte *Alterar as preferências do player do Screens*, conforme mencionado na seção abaixo).

### Gerenciamento de preferências do Player do AEM Screens {#managing-preferences-from-the-aem-screens-player}

Você também pode alterar as configurações da interface do usuário do administrador e do seletor de canal do próprio player.

Siga estas etapas para alterar as preferências do seu Player:

1. Pressione e segure no canto superior esquerdo do canal inativo para abrir o painel do administrador.
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solução de problemas do Player do AEM Screens {#troubleshooting-aem-screens-player}

É possível solucionar vários problemas associados ao Player do AEM Screens (hardware e software):

| **Problemas** | **Recomendações** |
|---|---|
| O armazenamento do player está cheio | Eliminar arquivos desnecessários |
| Player perdeu a rede | Use o cabo Cat-5/Cat-6. Para wifi, reduza a distância do roteador ao dispositivo do player |
| O AEM Screens Player falhou | É recomendável ter um aplicativo de monitoramento que verifique se o AEM Screens Player sempre é executado |
| Configurações perdidas do AEM Screens Player | Verificar conexão com o servidor AEM |
| O AEM Screens Player não inicia automaticamente após reiniciar/reiniciar o Player | Verificar a pasta de início do SO ou o procedimento de inicialização |
| O AEM Screens Player mostra conteúdo incorreto/antigo | Verificar conexão de rede |

### Atualizações para o Player do AEM Screens {#updates-for-aem-screens-player}

Existem dois tipos de atualizações para o Player do AEM Screens:

| **Método** | **Detalhes** | **via remoto** | **Automatizado** | **0 Tempo de inatividade** |
|---|---|---|---|---|
| Atualização do firmware | Aplicado em Players instalados existentes via comando remoto. Após a atualização, o Player será recarregado automaticamente com o conteúdo existente. | Sim | Personalizado | Quase - 1 a 3 segundos |
| Atualizações do shell do player | Este é um novo executável a ser implantado no Player. É necessário fazer uma cópia remota do novo binário no player, interromper a execução atual e iniciar a nova versão. Pode ser necessário fazer um novo download do pré-carregamento dos pacotes. | Sim (via shell remoto) | Personalizado | Não |

