---
title: Arquivos de log
seo-title: Log files
description: Eventos como erros de tempo de execução ou de inicialização são registrados nos arquivos de log do servidor de aplicativos, que podem ser abertos usando qualquer editor de texto.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 4%

---

# Arquivos de log {#log-files}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Eventos como erros de tempo de execução ou de inicialização são registrados nos arquivos de log do servidor de aplicativos. Se tiver problemas ao implantar no servidor de aplicativos, você poderá usar os arquivos de log para ajudá-lo a encontrar o problema. Você pode abrir os arquivos de log usando qualquer editor de texto.

(JBoss) Os seguintes arquivos de log estão localizados na variável `*[appserver root]*/server/*[server]*/log` diretório:

* boot.log
* server.log.*[aaaa-mm-dd]*
* server.log

(WebLogic) Os arquivos de log de domínio estão localizados na *[appserverdomain]* os arquivos de log do servidor e do diretório estão localizados na seção *[appserverdomain]/servidores/[nome do appserver]/logs *diretório:

* access.log
* *[nome do appserver]*.log
* *[nome do appserver]*.out.*[número incremental]*

(WebSphere) Os seguintes arquivos de log estão localizados na *[raiz do appserver]*/profiles/default/logs/*[nome do appserver]* diretório:

* SystemErr.log
* SystemOut.log
* StartServer.log
