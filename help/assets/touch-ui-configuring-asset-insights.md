---
title: Configuração do Assets Insights
description: Saiba como configurar o Assets Insights no [!DNL Experience Manager] Ativos.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 11%

---

# Configuração do Assets Insights {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Experience Manager Assets busca dados de uso ao redor do [!DNL Experience Manager] ativos usados por sites de terceiros do Adobe Analytics. Para permitir que o Assets Insights recupere esses dados e gere insights, primeiro configure o recurso para se integrar ao Adobe Analytics.

>[!NOTE]
>
>Os insights são suportados e fornecidos apenas para imagens.

1. No AEM, clique em **[!UICONTROL Ferramentas > Ativos]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Clique no cartão **[!UICONTROL Configuração do Insights]**.
1. No assistente, selecione um data center e forneça suas credenciais, incluindo o nome da organização, o nome de usuário e a senha.

   ![chlimage_1-211](assets/insights_config2.png)

1. Clique/toque em **[!UICONTROL Autenticar]**.
1. Depois [!DNL Experience Manager] autentica suas credenciais no **[!UICONTROL Conjunto de relatórios]** escolha um conjunto de relatórios do Adobe Analytics de onde deseja que o Assets Insights busque dados. Clique em **[!UICONTROL Adicionar]**.
1. Depois [!DNL Experience Manager] configure seu conjunto de relatórios, clique/toque **[!UICONTROL Concluído]**.

## Rastreador de página {#page-tracker}

Após configurar sua conta do Analytics, o código do Rastreador de página é gerado para você. Para permitir que o Assets Insights rastreie [!DNL Experience Manager] ativos usados em sites de terceiros, inclua o código do rastreador de página no código do site. Use o utilitário do Rastreador de páginas em [!DNL Experience Manager] Ativos para gerar o código do rastreador de página. Para obter mais informações sobre como incluir o código do Rastreador de página em páginas da Web de terceiros, consulte [Usar o rastreador de página e incorporar código em páginas da Web](touch-ui-using-page-tracker.md).

1. Em AEM, clique no botão **[!UICONTROL Ferramentas > Ativos]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Na página **[!UICONTROL Navegação]**, clique no cartão do **[!UICONTROL Rastreador de páginas do Insights]**.
1. Clique no botão **[!UICONTROL Baixar]** ícone para baixar o código do rastreador de página.
