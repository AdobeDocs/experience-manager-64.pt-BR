---
title: Configuração de Insights de Ativos
description: Saiba como configurar o Asset Insights no AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 10%

---


# Configuração de Insights de Ativos {#configuring-asset-insights}

O Adobe Experience Manager (AEM) Assets obtém dados de uso AEM ativos usados por sites de terceiros da Adobe Analytics. Para permitir que o Asset Insights recupere esses dados e gere insights, configure primeiro o recurso para integrar-se à Adobe Analytics.

>[!NOTE]
>
>Os insights só são suportados e fornecidos para imagens.

1. No AEM, clique em **[!UICONTROL Ferramentas > Ativos]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Clique no cartão **[!UICONTROL Configuração do Insights]**.
1. No assistente, selecione um centro de dados e forneça suas credenciais, incluindo o nome de sua organização, nome de usuário e senha.

   ![chlimage_1-211](assets/insights_config2.png)

1. Clique/toque em **[!UICONTROL Autenticar]**.
1. Depois que AEM autenticar suas credenciais, na lista **[!UICONTROL Report Suite]** , escolha um conjunto de relatórios da Adobe Analytics de onde deseja que o Asset Insights busque dados. Clique em **[!UICONTROL Adicionar]**.
1. Depois de AEM configurar seu conjunto de relatórios, clique/toque em **[!UICONTROL Concluído]**.

## Rastreador de página {#page-tracker}

Depois de configurar sua conta do Analytics, o código do rastreador de páginas é gerado para você. Para permitir que o Assets Insights rastreie ativos AEM usados em sites de terceiros, inclua o código do rastreador de página no código do site. Use o utilitário do rastreador de páginas no AEM Assets para gerar o código do rastreador de páginas. Para obter mais informações sobre como incluir o código do Rastreador de páginas em páginas da Web de terceiros, consulte [Uso do Rastreador de páginas e Incorporar código em páginas](touch-ui-using-page-tracker.md)da Web.

1. In AEM, click the **[!UICONTROL Tools > Assets]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Na página **[!UICONTROL Navegação]**, clique no cartão do **[!UICONTROL Rastreador de páginas do Insights]**.
1. Clique no ícone **[!UICONTROL Download]** para baixar o código do rastreador de página.