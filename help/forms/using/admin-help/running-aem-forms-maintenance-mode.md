---
title: Execução de formulários AEM no modo de manutenção
seo-title: Running AEM forms in maintenance mode
description: O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar AEM formulários ou aplicar um service pack. Saiba mais sobre como executar AEM formulários no modo de manutenção.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 7%

---

# Execução de formulários AEM no modo de manutenção {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar AEM formulários ou aplicar um service pack.

Evite invocar qualquer processo enquanto o servidor estiver em modo de manutenção. Isso é o que acontece se um processo é chamado enquanto o servidor está no modo de manutenção:

* Se o processo tiver uma duração longa, ele será adicionado ao banco de dados do trabalho, mas não será iniciado. Ao sair do modo de manutenção, o AEM forms processa os trabalhos de longa duração em sua fila, mesmo se o servidor tiver sido reiniciado durante o modo de manutenção.
* Se o processo tiver vida curta, ele será processado imediatamente.

**Coloque formulários AEM no modo de manutenção**

1. Em um navegador da web, digite:

   `https://`*[hostname ]*`:`*[porta]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[nome de usuário do administrador ]*`&password=`*[senha]*

   Uma mensagem &quot;agora pausada&quot; é exibida na janela do navegador.

   >[!NOTE]
   >
   >Se você encerrar o servidor enquanto ele estiver no modo de manutenção, ele ainda estará no modo de manutenção quando for reiniciado. Você deve desativar o modo de manutenção quando terminar suas tarefas de manutenção.

**Verifique se AEM formulários estão sendo executados no modo de manutenção**

1. Em um navegador da web, digite:

   `https://`*[hostname]:[porta ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[nome de usuário do administrador]* `&password=`*[senha ]*

   O status é exibido na janela do navegador. Um status &quot;true&quot; indica que o servidor está sendo executado no modo de manutenção e &quot;false&quot; indica que o servidor não está no modo de manutenção.

**Desligar o modo de manutenção**

1. Em um navegador da web, digite:

   `https://`*[hostname]:[porta ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[nome de usuário do administrador]* `&password=`*[senha ]*

   Uma mensagem &quot;agora em execução&quot; é exibida na janela do navegador.
