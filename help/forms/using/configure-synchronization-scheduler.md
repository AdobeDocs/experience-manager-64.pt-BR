---
title: Configurar o agendador de sincronização
seo-title: Configuring the synchronization scheduler
description: Saiba como migrar e sincronizar ativos, configurar o agendador de sincronização e usar pastas para organizar ativos.
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Configurar o agendador de sincronização {#configuring-the-synchronization-scheduler}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Por padrão, o agendador de sincronização é executado após cada 3 minutos para sincronizar todos os ativos modificados e atualizados no repositório por meio do LiveCycle Workbench 11. Os aplicativos que contêm formulários e recursos ficam visíveis na interface do usuário do AEM Forms após a conclusão do processo de sincronização.

## Alterar intervalo do agendador de sincronização {#change-interval-of-the-synchronization-scheduler}

Execute as seguintes etapas para alterar o intervalo do agendador de sincronização:

1. Faça logon no AEM Configuration Manager. O URL do Configuration Manager é `https://[Server]:[Port]/lc/system/console/configMgr`

1. Localize e abra o **FormsManagerConfiguration** pacote.

1. Especifique um novo valor para a variável **Frequência do Scheduler de Sincronização** opção.

   A unidade da frequência é minutos. Por exemplo, para configurar o scheduler para ser executado após cada 60 minutos, especifique 60.

## Sincronização de ativos {#synchronizing-assets}

Você pode usar o **Sincronizar ativos do repositório** para sincronizar manualmente os ativos. Execute as seguintes etapas para sincronizar manualmente os ativos:

1. Faça logon no AEM Forms. O URL padrão é `https://[Server]:[Port]/lc/aem/forms/`.

   ![Interface do usuário do AEM Forms](assets/aem_forms_ui.png)

   **Figura:** *Interface do usuário do AEM Forms*

1. Clique no botão ![aem6forms_sync](assets/aem6forms_sync.png) na barra de ferramentas. Se você não tiver ativos no caminho configurado pela última vez, a caixa de diálogo será exibida abaixo. Clique em **Iniciar** para iniciar a sincronização.

   ![Caixa de diálogo Sincronização](assets/migrate-and-syncronize.png)

   **Figura:** *Caixa de diálogo Sincronização*

## Resolução de problemas de erro de sincronização {#troubleshooting-synchronization-error}

Você pode criar novos aplicativos no designer de workflow (LiveCycle Workbench).

Se o aplicativo recém-criado e uma pasta em /content/dam/formsanddocuments tiver um nome idêntico, um erro &quot;*Um ativo com o mesmo nome deste aplicativo já existe no nível raiz.*&quot; está registrado.

Para resolver o conflito, renomeie o aplicativo e sincronize manualmente os ativos.

![Conflitos na caixa de diálogo sincronização de ativos](assets/sync-conflict.png)

**Figura:** *Conflitos na caixa de diálogo sincronização de ativos*
