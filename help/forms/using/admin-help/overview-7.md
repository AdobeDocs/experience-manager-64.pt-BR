---
title: Noções básicas para a configuração de formulários
seo-title: Basics of configuring forms
description: Saiba mais sobre os vários serviços de formulários que ajudam a criar aplicativos interativos de captura de dados.
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Noções básicas para a configuração de formulários {#basics-of-configuring-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O serviço Forms permite criar aplicativos clientes interativos de captura de dados que validam, processam, transformam e entregam formulários normalmente criados no Designer. Os autores de formulários desenvolvem um design de formulário único que o serviço Forms renderiza em vários formatos:

* como PDF no Adobe Reader ou em um navegador
* como HTML em vários ambientes de navegador, incluindo uma renderização XHTML 1.0 compatível
* como Guias de formulário em vários ambientes de navegador compatíveis com o Adobe Flash Player.

Para obter mais informações sobre o serviço Forms, consulte [Referência de serviços](https://www.adobe.com/go/learn_aemforms_services_63).

Usando a página Forms no console de administração, você pode configurar o comportamento do serviço Forms. Essas configurações se aplicam a todas as invocações do serviço. Todos os parâmetros enviados pelo SDK dos formulários AEM substituem as configurações definidas no console de administração; contudo, afetam apenas essa invocação específica.

Depois de alterar as configurações do Forms no console de administração, clique em Salvar. Não é necessário reiniciar o servidor para que as alterações entrem em vigor. No entanto, pode ser necessário parar e reiniciar o serviço Forms ao definir as configurações do modo de cache. (Consulte [Iniciar e parar serviços](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
