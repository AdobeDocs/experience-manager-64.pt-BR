---
title: Configuração do conector para Microsoft SharePoint
seo-title: Configuring Connector for Microsoft SharePoint
description: Configure o Conector para Microsoft SharePoint para permitir a comunicação entre AEM formulários e o Microsoft SharePoint.
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Configuração do conector para Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O conector para Microsoft SharePoint habilita a comunicação entre AEM formulários e o Microsoft SharePoint. Para obter mais informações de fundo, consulte &quot;Conectores para ECM&quot; em [Referência de serviços](https://www.adobe.com/go/learn_aemforms_services_63).

1. No console de administração, clique em Serviços > Conector para Microsoft SharePoint.
1. Especifique as seguintes configurações para o servidor do SharePoint:

   **Nome do host do servidor SharePoint:** O número da porta do nome do host do aplicativo Web no servidor SharePoint, no formato `[hostname]:[port]`.

   **Nome de usuário:** A conta de usuário usada para se conectar ao servidor do SharePoint.

   **Senha:** Senha da conta de usuário usada para se conectar ao servidor do SharePoint

   **Nome do domínio:** Domínio onde o servidor do SharePoint está localizado.

1. Clique em Salvar.

## Serviço de configuração do Microsoft SharePoint {#microsoft-sharepoint-configuration-service}

O serviço de configuração do Microsoft SharePoint `(MSSharePointConfigService)` permite especificar credenciais para o usuário dos formulários AEM que tem permissões de representação. Para obter informações sobre permissões de representação, consulte [Configuração do conector para Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Siga estas etapas para especificar as configurações para `MSSharePointConfigService`:

1. No console de administração, clique em Serviços > Aplicativos e Serviços > Gerenciamento de Serviços.
1. Navegue pela lista de serviços e clique em `MSSharePointConfigService`.
1. Especifique as seguintes configurações na página Configuração:

   * Nome De Usuário Para Um Usuário Com Permissões De Representação
   * Senha Do Usuário Acima

1. Clique em Salvar.
