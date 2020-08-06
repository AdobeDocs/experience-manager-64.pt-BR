---
title: Sincronizar o aplicativo
seo-title: Sincronizar o aplicativo
description: Sincronize o aplicativo AEM Forms em seu dispositivo móvel com o servidor AEM Forms.
seo-description: Sincronize o aplicativo AEM Forms em seu dispositivo móvel com o servidor AEM Forms.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Sincronizar o aplicativo {#synchronizing-the-app}

## Sincronizar o aplicativo {#synchronizing-the-app-1}

Os formulários no aplicativo são baixados do servidor AEM Forms. Os formulários são baixados nas guias Tarefa e Forms. Os rascunhos criados a partir de formulários são baixados na guia rascunhos e os rascunhos criados a partir do tarefa são baixados na guia tarefa. Para um formulário independente no servidor OSGi, os formulários e rascunhos são baixados nas guias Forms e Draft, respectivamente.

Quando você preenche e envia um formulário, o formulário é carregado de volta ao servidor da AEM Forms instantaneamente se o aplicativo estiver online. Os formulários são obtidos do servidor quando o aplicativo é sincronizado. No entanto, os rascunhos são sincronizados com o servidor instantaneamente se o aplicativo estiver online.

Quando você está online com o servidor AEM Forms, por padrão, seu aplicativo é sincronizado a cada 15 minutos. No entanto, você tem a opção de alterar a frequência de sincronização. Como alternativa, você pode sincronizar manualmente o aplicativo a qualquer momento.

**Para sincronizar o aplicativo manualmente**

Toque no botão Sincronizar aplicativo ![de](assets/sync-app.png) sincronização no canto inferior direito da tela inicial.

**Alteração da frequência de sincronização**

1. Para acessar a tela Setting (Configuração), toque no botão de menu no canto superior esquerdo da tela Home (Início) e, em seguida, toque em **Settings (Configurações)**.
1. Na tela Configurações, toque na guia Geral.

   ![Configuração de frequência de sincronização na janela Configurações gerais](assets/gen-settings-1.png)

1. Na opção Frequência de sincronização, toque no valor à direita de Frequência de sincronização.
1. Na lista suspensa, selecione a nova frequência de sincronização.

### Especificações técnicas {#technical-specifications}

* A lógica principal de enviar os dados do aplicativo offline para o servidor AEM Forms está incluída em runtime/offline/util/offline.js.
* Na função .js, a chamada para a função processOfflineSubmitedSavedTasks(...) envia as tarefas salvas / enviadas ao servidor. Também lida com erros ou conflitos no processo de sincronização. Se o envio de uma tarefa falhar, a tarefa no aplicativo será marcada como com falha. Além disso, a tarefa permanece em sua Caixa de saída.
* As funções syncSubmitedTask() e syncSavedTask() executam operações em tarefas individuais.
* A chamada para a função processOfflineSubmitedSavedTasks() é iniciada pelo componente de lista depois que um usuário seleciona para sincronizar o estado offline com o servidor ou uma sincronização automática pelo thread em segundo plano.

