---
title: Noções básicas sobre a estrutura de pastas
seo-title: Understanding the folder structure
description: Como entender a estrutura de pastas do código-fonte do espaço de trabalho do AEM Forms para personalizar.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# Noções básicas sobre a estrutura de pastas {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os componentes do espaço de trabalho do AEM Forms são projetados na arquitetura MVC usando Backbone. Cada componente tem um arquivo para:

* Modelo, que contém lógica de negócios.
* Modelo, que é um arquivo HTML contendo controles de interface.
* Exibir, que atua como uma classe Controladora para Modelo.

Os ativos de todos os componentes são colocados na estrutura de pastas descrita abaixo. Para acessar os ativos, faça logon no CRXDE Lite e navegue até `/libs/ws/js/runtime/`.

**modelos** Contém modelos de backbone.

**exibições** Contém visualizações de backbone.

**modelos** Contém apenas os modelos HTML para os componentes.

**rotas** Contém rotas universais. A pasta Modelos nas rotas contém o código HTML e as referências aos componentes.

**serviços** Contém a interface de serviço para chamar APIs do servidor do Adobe Experience Manager no terminal REST.

**util** Contém utilitários genéricos utilizáveis por vários componentes.
