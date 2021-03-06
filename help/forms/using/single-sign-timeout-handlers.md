---
title: Manipuladores de logon único e tempo limite
seo-title: Manipuladores de logon único e tempo limite
description: Como definir o valor de limite de tempo de sessão para o espaço de trabalho AEM Forms.
seo-description: Como definir o valor de limite de tempo de sessão para o espaço de trabalho AEM Forms.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Manipuladores de logon único e tempo limite {#single-sign-on-and-timeout-handlers}

A área de trabalho do AEM Forms está habilitada para SSO. Se um usuário tiver feito logon em um aplicativo AEM Forms, como a interface do usuário do Forms Manager ou do Gerador de PDF, e acessar a área de trabalho do AEM Forms na mesma sessão do navegador, o usuário terá feito logon na área de trabalho do AEM Forms e vice-versa.

## Tratamento do tempo limite do servidor na área de trabalho AEM Forms {#handling-server-timeout-in-nbsp-aem-forms-workspace}

O tempo limite da sessão para um usuário pode ser configurado no Console de administração.

Para definir o tempo limite, faça logon em `https://[server]:[port]/adminui`, navegue até **Configurações > Gerenciamento do usuário > Configuração > Configurar atributos avançados do sistema** e faça as configurações desejadas.

No espaço de trabalho AEM Forms, o tempo limite é tratado como:

* A duração da sessão de um usuário está disponível em resposta à chamada `initialize` que inicializa a sessão do usuário.
* Uma caixa de diálogo pop-up notifica o usuário de que a sessão está prestes a expirar, 15 segundos antes da expiração da sessão.

Nesta caixa de diálogo pop-up:

* Clique em OK para encerrar a sessão do usuário.
* Clique em Cancelar para reinicializar a sessão do usuário.

>[!NOTE]
>
>Se nenhuma ação for executada, o usuário será automaticamente desconectado da área de trabalho do AEM Forms três segundos antes da expiração da sessão.
