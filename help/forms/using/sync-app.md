---
title: Sincronização do aplicativo
seo-title: Synchronizing the app
description: Sincronize o aplicativo AEM Forms em seu dispositivo móvel com o servidor AEM Forms.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Sincronização do aplicativo {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sincronização do aplicativo {#synchronizing-the-app-1}

Os formulários no seu aplicativo são baixados do servidor do AEM Forms. Os formulários são baixados nas guias Tarefas e Forms . Os rascunhos criados a partir de formulários são baixados na guia rascunhos e os rascunhos criados a partir de tarefas são baixados na guia tarefas . Para um formulário independente no servidor OSGi, os formulários e rascunhos são baixados nas guias Forms e Rascunho , respectivamente.

Quando você preenche e envia um formulário, o formulário é carregado de volta ao servidor da AEM Forms instantaneamente se o aplicativo estiver online. Os formulários são buscados no servidor quando o aplicativo é sincronizado. Os rascunhos, no entanto, são sincronizados instantaneamente com o servidor se o aplicativo estiver online.

Por padrão, quando você está online com o servidor do AEM Forms, seu aplicativo é sincronizado a cada 15 minutos. No entanto, você tem a opção de alterar a frequência de sincronização. Como alternativa, você pode sincronizar manualmente o aplicativo a qualquer momento.

**Para sincronizar o aplicativo manualmente**

Toque no botão Sincronizar ![sync-app](assets/sync-app.png) no canto inferior direito da tela inicial.

**Para alterar a frequência de sincronização**

1. Para ir para a tela Definição, toque no botão de menu no canto superior esquerdo do ecrã inicial e toque em **Configurações**.
1. Na tela Configurações , toque na guia Geral .

   ![Configuração de frequência de sincronização na janela Configurações gerais](assets/gen-settings-1.png)

1. Na opção Sync frequency , toque no valor à direita de Sync frequency .
1. Na lista suspensa, selecione a nova frequência de sincronização.

### Especificações técnicas {#technical-specifications}

* A lógica principal de enviar os dados do aplicativo offline para o servidor do AEM Forms está incluída em runtime/offline/util/offline.js.
* No .js, a chamada para a função processOfflineSubmitedSavedTasks(..) envia as tarefas salvas / enviadas ao servidor. Ele também lida com erros ou conflitos no processo de sincronização. Se o envio de uma tarefa falhar, a tarefa no aplicativo será marcada como falha. Além disso, a tarefa permanece em sua Caixa de saída.
* As funções syncSubmitedTask() e syncSavedTask() executam operações em tarefas individuais.
* A chamada para a função processOfflineSubmitedSavedTasks() é iniciada pelo componente de lista de tarefas depois que um usuário seleciona para sincronizar o estado offline com o servidor ou uma sincronização automática pelo thread em segundo plano.
