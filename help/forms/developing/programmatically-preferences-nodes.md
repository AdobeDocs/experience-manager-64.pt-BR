---
title: Gerenciamento programático de PreferênciasNodes
seo-title: Programmatically managing the PreferencesNodes
description: Use a API de serviço do Gerenciador de preferências (Java) para gerenciar programaticamente os nós de preferências.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Gerenciar programaticamente os nós de preferências {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Este tópico descreve como você pode usar a API de serviço do Gerenciador de preferências (Java) para gerenciar programaticamente os nós de preferências.

Você pode alterar manualmente as configurações da interface do usuário do administrador. Para alterar as opções, navegue até `Home>Settings>User Management> Configuration>Manual Configuration`. Importar `config.xml` depois de fazer as alterações, você notará que todas as alterações, exceto as feitas no nó `/Adobe/Adobe Experience Manager Forms/Config/UM persist` estão perdidos. A visualização da Importação e exportação do Gerenciamento de Usuário não suporta a alteração das configurações de outros componentes. Agora, essas alterações podem ser feitas usando `PreferencesManagerServiceClient` APIs.

**Resumo das etapas** Para gerenciar programaticamente os nós de preferências, execute as seguintes etapas:

1. Inclua arquivos de projeto.
1. Criar um cliente PreferencesManagerService
1. Chamar a função ou as operações de permissão apropriadas

**Incluir arquivos de projeto**

Inclua os arquivos necessários no seu projeto de desenvolvimento. Se você estiver criando um aplicativo cliente usando Java, inclua os arquivos JAR necessários. Se você estiver usando serviços da Web, certifique-se de incluir os arquivos proxy.

**Criar um cliente PreferencesManagerService**

Antes de poder executar programaticamente uma operação PreferencesManagerService de Gerenciamento de Usuário, você deve criar um cliente PreferencesManagerService . Com a API Java, isso é feito criando um objeto PreferencesManagerServiceClient .

**Chamar a função ou as operações de permissão apropriadas**

Depois de criar o cliente de serviço, você pode chamar as operações do Gerenciador de preferências. O cliente de serviço permite ler e definir permissões.
