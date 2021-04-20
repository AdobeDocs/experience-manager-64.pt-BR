---
title: Configuração do Asset Insights
description: Saiba como configurar o Asset Insights no AEM Assets.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 10%

---


# Configuração do Asset Insights {#configuring-asset-insights}

O Adobe Experience Manager (AEM) Assets busca dados de uso AEM ativos usados por sites de terceiros do Adobe Analytics. Para permitir que o Asset Insights recupere esses dados e gere insights, primeiro configure o recurso para se integrar ao Adobe Analytics.

>[!NOTE]
>
>Os insights são suportados e fornecidos apenas para imagens.

1. No AEM, clique em **[!UICONTROL Ferramentas > Ativos]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Clique no cartão **[!UICONTROL Configuração do Insights]**.
1. No assistente, selecione um data center e forneça suas credenciais, incluindo o nome da organização, o nome de usuário e a senha.

   ![chlimage_1-211](assets/insights_config2.png)

1. Clique/toque em **[!UICONTROL Autenticar]**.
1. Depois de AEM autenticar suas credenciais, na lista **[!UICONTROL Report Suite]**, escolha um conjunto de relatórios do Adobe Analytics no qual deseja que o Asset Insights busque dados. Clique em **[!UICONTROL Adicionar]**.
1. Depois de AEM configurar seu conjunto de relatórios, clique/toque em **[!UICONTROL Concluído]**.

## Rastreador de página {#page-tracker}

Após configurar sua conta do Analytics, o código do Rastreador de página é gerado para você. Para permitir que o Assets Insights rastreie AEM ativos usados em sites de terceiros, inclua o código do rastreador de página no código do site. Use o utilitário do Rastreador de página no AEM Assets para gerar o código do rastreador de página. Para obter mais informações sobre como incluir o código do Rastreador de página em páginas da Web de terceiros, consulte [Usar o Rastreador de página e Incorporar código em páginas da Web](touch-ui-using-page-tracker.md).

1. Em AEM, clique em **[!UICONTROL Ferramentas > Ativos]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Na página **[!UICONTROL Navegação]**, clique no cartão do **[!UICONTROL Rastreador de páginas do Insights]**.
1. Clique no ícone **[!UICONTROL Download]** para baixar o código do rastreador de página.