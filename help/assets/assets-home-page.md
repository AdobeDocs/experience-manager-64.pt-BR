---
title: Experiência com o Home page AEM Assets
description: Personalize o Home page AEM Assets para obter uma excelente experiência de tela de boas-vindas, incluindo um instantâneo de atividades recentes sobre ativos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---


# Experiência com o Home page AEM Assets {#aem-assets-home-page-experience}

Personalize o Home page AEM Assets para obter uma excelente experiência de tela de boas-vindas, incluindo um instantâneo de atividades recentes sobre ativos.

O Home page Adobe Experience Manager (AEM) Assets fornece uma experiência de tela de boas-vindas rica e personalizada, que inclui um instantâneo de atividades recentes, como ativos que foram exibidos ou carregados recentemente.

O Home page Ativos está desativado por padrão. Para ativá-lo, execute as seguintes etapas:

1. Para acessar AEM Configuration Manager, clique em **[!UICONTROL Ferramentas > Operação > Console Web]**.
1. Abra o serviço **Day CQ DAM Evento Recorder**.
1. Selecione **[!UICONTROL Ativar este serviço]** para ativar a gravação de atividade.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Na lista **Tipos de evento**, selecione os eventos a serem gravados e salve as alterações.

   >[!CAUTION]
   >
   >Ativar as opções visualizadas Ativo visualizado, Projetos visualizados e Coleções aumenta significativamente o número de eventos registrados.

1. Abra o serviço **[!UICONTROL Sinalizador do recurso Home page do ativo DAM]** do Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Selecione a opção **[!UICONTROL isEnabled.name]** para ativar o recurso de Home page Ativos. Salve as alterações.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra a caixa de diálogo **[!UICONTROL Preferências de usuário]** e selecione **[!UICONTROL Ativar Home page de ativos]**. Salve as alterações.

   ![user_preferences](assets/user_preferences.png)

Depois de ativar o Home page Ativos, navegue até a interface do usuário Ativos na página Navegação.

![home_page](assets/home_page.png)

Toque/clique em **[!UICONTROL Clique aqui para configurar seu link de experiência]** para adicionar seu nome de usuário, imagem de plano de fundo e imagem de perfil.

O Home page Ativos inclui as seguintes seções:

* Seção de boas-vindas
* Seção do Widget

**Seção de boas-vindas**

Se o seu perfil existir, a seção Boas-vindas exibirá uma mensagem de boas-vindas endereçada a você. Além disso, exibe a imagem do perfil e uma imagem de boas-vindas (se já estiver configurada).

Se o perfil estiver incompleto, a seção Bem-vindo exibirá uma mensagem genérica de boas-vindas e um espaço reservado para a imagem do perfil.

**Seção do Widget**

Esta seção é exibida abaixo da seção Boas-vindas e exibe os widgets predefinidos nas seguintes seções:

* Atividade
* Recentes
* Descobrir

**Atividade**: Nesta seção, o  **My** Ativitywidget exibe atividades recentes executadas pelo usuário conectado com ativos (incluindo ativos sem representações), como uploads de ativos, downloads, criação de ativos, edições, comentários, anotações e compartilhamentos.

**Recente**: O widget  **Visualizado** recentemente nesta seção exibe entidades acessadas recentemente pelo usuário conectado, incluindo pastas, coleções e projetos.

**Discover**: O  **** Banca desta seção exibe os ativos e as execuções carregados recentemente para a instância do AEM Assets.

Para habilitar a remoção de dados de atividade do usuário, ative o **serviço de remoção de Evento DAM** do Configuration Manager. Após habilitar esse serviço, as atividades do usuário conectado que excederem um número especificado serão excluídas pelo sistema.

A tela de boas-vindas fornece ferramentas de navegação fáceis, por exemplo ícones na barra de ferramentas para acessar pastas, coleções e catálogos.

>[!NOTE]
>
>Habilitar os serviços de Gravação e Expurgação de Eventos do Day CQ DAM aumenta as operações de gravação no JCR e a indexação de pesquisa, o que aumenta significativamente a carga no servidor AEM. A carga adicional no servidor AEM pode afetar seu desempenho.

>[!CAUTION]
>
>Capturar, filtrar e expurgar atividades de usuário necessárias para o Home page do ativo impõem uma sobrecarga no desempenho. Portanto, os administradores devem configurar o Home page de forma eficiente para os usuários do público alvo.
>
>O Adobe recomenda que os administradores e usuários que executam operações em massa evitem usar o recurso Home page de ativos para evitar o aumento das atividades do usuário. Além disso, os administradores podem excluir atividades de gravação para usuários específicos ao configurar **Gravador de Eventos Day CQ DAM** do Configuration Manager.
>
>Se você usar o recurso, o Adobe recomenda agendar a frequência de expurgação com base na carga do servidor.
