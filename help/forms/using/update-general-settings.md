---
title: Atualização de configurações gerais
seo-title: Atualização de configurações gerais
description: Atualize as configurações do aplicativo AEM Forms, como a tela inicial, e busque as opções de pontos de partida e anexos
seo-description: Atualize as configurações do aplicativo AEM Forms, como a tela inicial, e busque as opções de pontos de partida e anexos
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---


# Atualização de configurações gerais {#updating-general-settings}

As configurações gerais do aplicativo AEM Forms permitem que você especifique configurações como buscar anexos, modo offline, tela de aterrissagem, categoria padrão e frequência de salvamento automático.

## Atualização das configurações gerais no aplicativo {#working-with-the-form}

Quando você sincroniza seu aplicativo com o servidor AEM Forms, todos os formulários e tarefas definidas são baixados para seu dispositivo móvel.

A solução de aplicativo AEM Forms predefinida não baixa os anexos associados a cada formulário quando o aplicativo é sincronizado.

Na guia Geral, altere os anexos de download, o modo offline, a tela de aterrissagem, as configurações de gravação automática e sincronização. Você pode alterar a tela [](/help/forms/using/home-screen.md) inicial do seu aplicativo.

**Navegue até a guia Geral na tela Configurações**

1. Para acessar a tela Configuração, toque no botão Menu no canto superior esquerdo da tela Início e, em seguida, em **Configurações**.
1. Na tela Configurações, toque na guia Geral.

   ![Configurações gerais no aplicativo AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >As opções podem ser exibidas de forma diferente em diferentes dispositivos móveis.

### Configurações gerais {#general-settings}

Você pode fazer as seguintes alterações nas configurações do aplicativo.

* **Buscar anexos** de tarefa: Para especificar se os anexos associados devem ou não ser baixados quando cada tarefa for baixada no aplicativo.

* **Modo** offline: Para ativar ou desativar o serviço offline para aplicativos AEM Forms. Consulte [Trabalhar no modo](/help/forms/using/work-offline-mode.md) offline para obter detalhes.

* **Tela** de aterrissagem: Para definir o local do start (tela[](/help/forms/using/home-screen.md)inicial) do aplicativo.

   Opções disponíveis:

   * Forms
   * Tarefas
   * Favoritos

* **categoria** padrão: Permite que você selecione a categoria de formulários a serem exibidos na tela inicial. Quando você seleciona Todos, pode ver todos os formulários na tela inicial. As Categorias são preenchidas com base nos formulários carregados no aplicativo. O Forms está disponível no aplicativo com base nas configurações de formulário especificadas no servidor AEM Forms.

* **Frequência** de salvamento automático: Para definir a frequência na qual seu aplicativo [móvel salva os dados](/help/forms/using/autosave-data-app.md) do formulário localmente.

* **Frequência** de sincronização: Para definir a frequência na qual seu aplicativo [móvel é sincronizado](/help/forms/using/sync-app.md) com o servidor AEM Forms no modo online.

**Limpar dados** locais: Limpe o banco de dados, incluindo configurações e dados locais para todos os usuários e armazenamentos de arquivos do dispositivo.

>[!NOTE]
>
>Limpar o cache desconectará você imediatamente do aplicativo.
>
>No entanto, você será solicitado a confirmar a operação de limpeza do cache.
