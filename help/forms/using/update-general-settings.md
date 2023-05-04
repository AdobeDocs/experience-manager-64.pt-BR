---
title: Atualização das configurações gerais
seo-title: Updating general settings
description: Atualize as configurações do aplicativo AEM Forms, como a tela inicial e as opções de busca de pontos de partida e anexos
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 3%

---

# Atualização das configurações gerais {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

As configurações gerais do aplicativo AEM Forms permitem especificar configurações, como buscar anexos, modo offline, tela de aterrissagem, categoria padrão e frequência de salvamento automático.

## Atualização das configurações gerais no seu aplicativo {#working-with-the-form}

Ao sincronizar seu aplicativo com o servidor do AEM Forms, todos os formulários e tarefas definidas serão baixados no dispositivo móvel.

A solução de aplicativo AEM Forms pronta para uso não baixa os anexos associados a cada formulário quando o aplicativo é sincronizado.

Na guia General , altere os anexos de download, o modo offline, a tela de aterrissagem, o salvamento automático e as configurações de sincronização. Você pode alterar a variável [Tela inicial](/help/forms/using/home-screen.md) do seu aplicativo.

**Navegue até a guia Geral na tela Configurações**

1. Para ir para a tela Configuração, toque no botão Menu no canto superior esquerdo da tela inicial e toque em **Configurações**.
1. Na tela Configurações , toque na guia Geral .

   ![Configurações gerais no aplicativo AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >As opções podem ser exibidas de forma diferente em diferentes dispositivos móveis.

### Configurações gerais {#general-settings}

Você pode fazer as seguintes alterações nas configurações do seu aplicativo.

* **Buscar anexos da tarefa**: Especificar se os anexos associados devem ou não ser baixados quando cada tarefa for baixada no aplicativo.

* **Modo offline**: Para ativar ou desativar o serviço offline para o aplicativo AEM Forms. Consulte [Trabalhar no modo offline](/help/forms/using/work-offline-mode.md) para obter detalhes.

* **Tela de aterrissagem**: Para definir o local de início ([Tela inicial](/help/forms/using/home-screen.md)) para o aplicativo.

   Opções disponíveis:

   * Forms
   * Tarefas
   * Favoritos

* **Categoria padrão**: Permite que você selecione a categoria de formulários a serem mostrados na tela inicial. Ao selecionar Todos, você pode ver todos os formulários na tela inicial. As categorias são preenchidas com base nos formulários carregados no aplicativo. O Forms está disponível no aplicativo com base nas configurações de formulário especificadas no servidor do AEM Forms.

* **Frequência de Salvamento Automático**: Para definir a frequência na qual o [aplicativo móvel salva dados de formulário](/help/forms/using/autosave-data-app.md) localmente.

* **Frequência de Sincronização**: Para definir a frequência na qual o [aplicativo móvel é sincronizado](/help/forms/using/sync-app.md) com o servidor AEM Forms no modo online.

**Limpar dados locais**: Limpe o banco de dados, incluindo configurações e dados locais para todos os usuários e armazenamento de arquivos do dispositivo.

>[!NOTE]
>
>Limpar o cache fará logoff imediatamente do aplicativo.
>
>No entanto, você será solicitado a confirmar a operação de limpeza do cache.
