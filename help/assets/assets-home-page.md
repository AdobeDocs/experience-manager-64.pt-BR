---
title: '"[!DNL Experience Manager Assets] Experiência da página inicial"'
description: Personalize a Página inicial do Assets para obter uma experiência rica em tela de boas-vindas, incluindo um instantâneo das atividades recentes em torno dos ativos.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: d9cfb5376210234b3b05877509c273c52d9cecf3
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager Assets] Experiência da página inicial {#aem-assets-home-page-experience}

Personalize o [!DNL Experience Manager Assets] Página inicial para obter uma experiência avançada em tela de boas-vindas, incluindo um instantâneo das atividades recentes em torno dos ativos.

O [!DNL Adobe Experience Manager Assets] A página inicial fornece uma experiência de tela de boas-vindas rica e personalizada, que inclui um instantâneo de atividades recentes, como ativos que foram visualizados ou carregados recentemente.

A Página inicial dos Ativos está desativada por padrão. Para habilitá-lo, execute as seguintes etapas:

1. Para acessar [!DNL Experience Manager] Gerenciador de configuração, clique em **[!UICONTROL Ferramentas > Operação > Console da Web]**.
1. Abra o **Gravador de eventos CQ DAM** serviço.
1. Selecione o **[!UICONTROL Ativar este serviço]** para ativar o registro de atividades.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. No **Tipos de evento** selecione os eventos a serem registrados e salve as alterações.

   >[!CAUTION]
   >
   >Ativar as opções de ativo visualizado, Projetos visualizados e Coleções visualizadas aumenta significativamente o número de eventos gravados.

1. Abra o **[!UICONTROL Sinalizador de recurso da página inicial de ativos DAM]** serviço do Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Selecione o **[!UICONTROL isEnabled.name]** para ativar o recurso Página inicial do Assets. Salve as alterações.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra o **[!UICONTROL Preferências do usuário]** e selecione **[!UICONTROL Ativar a Página inicial dos ativos]**. Salve as alterações.

   ![user_preferences](assets/user_preferences.png)

Depois de ativar a Página inicial dos Ativos, navegue até a interface do usuário dos Ativos na página Navegação .

![home_page](assets/home_page.png)

Toque/clique no botão **[!UICONTROL Clique aqui para configurar seu link de experiência]** para adicionar seu nome de usuário, imagem de plano de fundo e imagem de perfil.

A Página inicial dos Ativos inclui as seguintes seções:

* Seção de boas-vindas
* Seção de widget

**Seção de boas-vindas**

Se o seu perfil existir, a seção Welcome exibirá uma mensagem de boas-vindas endereçada a você. Além disso, ele exibe a imagem do perfil e uma imagem de boas-vindas (se configurada já).

Se o seu perfil estiver incompleto, a seção Welcome exibirá uma mensagem de boas-vindas genérica e um espaço reservado para a imagem do seu perfil.

**Seção de widget**

Esta seção aparece abaixo da seção de Boas-vindas e exibe os widgets prontos para uso nas seguintes seções:

* Atividade
* Recentes
* Descobrir

**Atividade**: Nesta seção, a variável **Minha atividade** O widget exibe atividades recentes executadas pelo usuário conectado com ativos (incluindo ativos sem representações), por exemplo, uploads de ativos, downloads, criação de ativos, edições, comentários, anotações e compartilhamentos.

**Recente**: O **Visualizados recentemente** O widget nesta seção exibe entidades acessadas recentemente pelo usuário conectado, incluindo pastas, coleções e projetos.

**Discover**: O **Novo** o widget nesta seção exibe os ativos e as execuções carregados recentemente na [!DNL Assets] instância.

Para habilitar a limpeza dos dados de atividade do usuário, habilite a variável **Serviço de limpeza de eventos DAM** do Configuration Manager. Após habilitar esse serviço, as atividades do usuário conectado que excedem um número especificado são excluídas pelo sistema.

A tela de Boas-vindas fornece recursos de navegação fáceis, por exemplo, ícones na barra de ferramentas para acessar pastas, coleções e catálogos.

>[!NOTE]
>
>Habilitar o Day CQ DAM Event Recorder e os serviços de limpeza de eventos DAM aumenta as operações de gravação no JCR e a indexação de pesquisa, o que aumenta significativamente a carga no [!DNL Experience Manager] servidor. A carga adicional no [!DNL Experience Manager] pode afetar seu desempenho.

>[!CAUTION]
>
>Capturar, filtrar e expurgar atividades do usuário necessárias para a Página inicial do ativo impõem uma sobrecarga no desempenho. Portanto, os administradores devem configurar a Página inicial de maneira eficaz para os usuários do público-alvo.
>
>O Adobe recomenda que os administradores e usuários que realizam operações em massa evitem usar o recurso Página inicial do ativo para evitar o aumento das atividades do usuário. Além disso, os administradores podem excluir as atividades de gravação de usuários específicos ao configurar **Gravador de eventos CQ DAM** do Configuration Manager.
>
>Se você usar o recurso , o Adobe recomenda agendar a frequência de limpeza com base na carga do servidor.
