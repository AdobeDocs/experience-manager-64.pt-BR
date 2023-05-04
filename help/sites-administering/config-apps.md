---
title: Configuração para aplicativos AEM
seo-title: Configuring for AEM Apps
description: Saiba como configurar AEM aplicativos.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 4%

---

# Configuração para aplicativos AEM{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os aplicativos Adobe Experience Manager oferecem a capacidade de atualizar o conteúdo do aplicativo ao ar (OTA). O conteúdo atualizado é armazenado na instância de publicação. Para permitir que o aplicativo em seu dispositivo se conecte à instância de publicação e verifique se há atualizações, a instância de publicação precisa ser configurada para permitir um cabeçalho de referenciador vazio.

## Configuração do Cabeçalho do Referenciador Vazio {#configuring-empty-referrer-header}

Para configurar o serviço de filtro do referenciador:

* Abra o console do Apache Felix (**Configurações**) em:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Faça logon como administrador.
* No **Configurações** selecione: *Filtro de referenciador do Apache Sling*
* Marque o campo Permitir vazio para permitir cabeçalhos de referenciador vazios/ausentes.
* Clique em **Salvar** para salvar as alterações.

![chlimage_1-58](assets/chlimage_1-58.png)

Consulte a [Configurações de OSGI](/help/sites-deploying/osgi-configuration-settings.md) e [Lista de verificação de segurança - Problemas com a falsificação de solicitação entre sites](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) para obter mais detalhes.
