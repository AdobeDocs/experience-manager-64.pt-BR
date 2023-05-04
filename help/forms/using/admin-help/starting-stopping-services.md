---
title: Iniciar e parar serviços
seo-title: Starting and stopping services
description: Saiba como iniciar e interromper serviços associados aos módulos AEM Forms e ao servidor de aplicativos e banco de dados.
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 2%

---

# Iniciar e parar serviços {#starting-and-stopping-services}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Há dois tipos de serviços que fazem parte de AEM formulários:

* Serviços que controlam o servidor de aplicativos e o banco de dados dos formulários AEM.
* Serviços que controlam AEM módulos de formulários

## Iniciar ou parar os serviços associados aos módulos de formulários AEM {#start-or-stop-the-services-associated-with-aem-forms-modules}

Os módulos de formulários AEM (por exemplo, Forms, Rights Management, Output) operam como serviços. Às vezes, pode ser necessário interromper ou iniciar os serviços para esses módulos de formulários AEM. Por exemplo, você deve parar e reiniciar um serviço de formulários AEM depois de alterar uma configuração do serviço.

1. No console de administração, clique em **Serviços** > **Aplicativos e serviços** > **Gerenciamento de serviços**.
1. Na página Gerenciamento de serviços , marque a caixa de seleção ao lado do serviço para interromper ou iniciar e clique em Parar ou Iniciar.

## Iniciar ou parar serviços para o servidor de aplicativos e o banco de dados {#start-or-stop-services-for-the-application-server-and-database}

Uma implementação completa de formulários AEM inclui um servidor de aplicativos e serviços de banco de dados:

* *`[application server]`* para formulários AEM
* *`[database]`* para formulários AEM

No Windows, esses serviços são acessíveis por meio do **Ferramentas administrativas** > **Painel Serviços**. Por exemplo, se você instalou formulários AEM no JBoss usando o método turnkey, os seguintes serviços estarão disponíveis no sistema:

* JBoss para formulários Adobe Experience Manager
* MySQL for Adobe Experience Manager forms

Inicie ou pare esses serviços selecionando-os na lista do painel Serviços e clicando no botão de ação apropriado no painel.

No UNIX® ou Linux, insira o seguinte texto de uma linha de comando, onde *`[service name]`* é o nome do serviço que você está verificando:

```as3
     ps -A | grep [service name]
```
