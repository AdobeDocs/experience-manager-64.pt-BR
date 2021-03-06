---
title: Execução de formulários AEM no modo de manutenção
seo-title: Execução de formulários AEM no modo de manutenção
description: O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar formulários AEM ou aplicar um service pack. Saiba mais sobre como executar formulários AEM no modo de manutenção.
seo-description: O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar formulários AEM ou aplicar um service pack. Saiba mais sobre como executar formulários AEM no modo de manutenção.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Execução de formulários AEM no modo de manutenção {#running-aem-forms-in-maintenance-mode}

O modo de manutenção é útil ao executar tarefas como corrigir um DSC, atualizar formulários AEM ou aplicar um service pack.

Evite invocar qualquer processo enquanto o servidor estiver no modo de manutenção. Isso é o que acontece se um processo for chamado enquanto o servidor estiver no modo de manutenção:

* Se o processo tiver duração longa, ele será adicionado ao banco de dados do trabalho, mas não será iniciado. Quando você sai do modo de manutenção, AEM formulários processa as tarefas de longa duração em sua fila, mesmo se o servidor foi reiniciado enquanto estava no modo de manutenção.
* Se o processo tem vida curta, ele é processado imediatamente.

**Colocar formulários AEM no modo de manutenção**

1. Em um navegador da Web, digite:

   `https://`*[]*`:`*[]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[hostnameportadministrative ]*`&password=`*[usernamepassword]*

   Uma mensagem &quot;agora pausada&quot; é exibida na janela do navegador.

   >[!NOTE]
   >
   >Se você encerrar o servidor enquanto ele estiver no modo de manutenção, ele ainda estará no modo de manutenção quando for reiniciado. Você deve desativar o modo de manutenção quando terminar suas tarefas de manutenção.

**Verifique se AEM formulários está sendo executado no modo de manutenção**

1. Em um navegador da Web, digite:

   `https://`*[nome] do host:[]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[portadministrative]* `&password=`*[usernamepassword ]*

   O status é exibido na janela do navegador. Um status &quot;true&quot; indica que o servidor está sendo executado no modo de manutenção e &quot;false&quot; indica que o servidor não está no modo de manutenção.

**Desativar modo de manutenção**

1. Em um navegador da Web, digite:

   `https://`*[nome] do host:[]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[portadministrative]* `&password=`*[usernamepassword ]*

   Uma mensagem &quot;agora em execução&quot; é exibida na janela do navegador.

