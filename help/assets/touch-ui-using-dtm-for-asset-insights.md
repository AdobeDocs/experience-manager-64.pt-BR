---
title: Ativar insights de ativos por meio do DTM
description: Saiba como usar o Adobe Dynamic Tag Management (DTM) para ativar o Assets Insights.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 1%

---

# Ativar insights de ativos por meio do DTM {#enabling-asset-insights-through-dtm}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Adobe Dynamic Tag Management é uma ferramenta que ativa suas ferramentas de marketing digital. É fornecido gratuitamente para os clientes da Adobe Analytics. Você pode personalizar o código de rastreamento para permitir que soluções de CMS de terceiros usem o Assets Insights ou usar o DTM para inserir tags do Assets Insights. Os insights são suportados e fornecidos apenas para imagens.

>[!CAUTION]
>
>Adobe DTM está obsoleto em favor de [!DNL Adobe Experience Platform] e em breve [fim da vida útil](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). O Adobe recomenda que você [use [!DNL Adobe Experience Platform] para insights de ativos](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

Execute as etapas a seguir para ativar o Assets Insights por meio do DTM:

1. Toque/clique no botão [!DNL Experience Manager] logotipo e acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Ativos]** > **[!UICONTROL Configuração do Insights]**.
1. [Configurar [!DNL Experience Manager] instância com Cloud Service do DTM](../sites-administering/dtm.md)

   O token da API deve estar disponível assim que você fizer logon no [https://dtm.adobe.com](https://dtm.adobe.com/) e visita **[!UICONTROL Configurações da conta]** no ícone Perfil . Essa etapa não é necessária do ponto de vista do Assets Insights, pois a integração de [!DNL Experience Manager Sites] O com o Assets Insights ainda está em andamento.

1. Faça logon em [https://dtm.adobe.com](https://dtm.adobe.com/)e selecione uma Empresa, conforme apropriado.
1. Criar/abrir uma propriedade da Web existente

   * Selecione o **[!UICONTROL Propriedades da Web]** e toque/clique **[!UICONTROL Adicionar propriedade]**.
   * Atualize os campos conforme apropriado e toque/clique **[!UICONTROL Criar propriedade]** (consulte [documentação](https://helpx.adobe.com/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. No **[!UICONTROL Regras]** guia , selecione **[!UICONTROL Regras de carregamento da página]** no painel de navegação e toque/clique **[!UICONTROL Criar nova regra]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Expandir **[!UICONTROL Javascript /Tags De Terceiros]**. Em seguida, toque/clique **[!UICONTROL Adicionar novo script]** no **[!UICONTROL HTML sequencial]** para abrir a caixa de diálogo Script.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Toque/clique no botão [!DNL Experience Manager] logotipo e acesse **[!UICONTROL Ferramentas > Ativos]**.
1. Toque/clique **[!UICONTROL Rastreador de página do Insights]**, copie o código do rastreador e o cole na caixa de diálogo Script aberta na etapa 6. Salve as alterações.

   >[!NOTE]
   >
   >* `AppMeasurement.js` foi removida. Ela deve estar disponível por meio da ferramenta Adobe Analytics do DTM.
   >* A chamada para `assetAnalytics.dispatcher.init()` for removido. Espera-se que a função seja chamada assim que a ferramenta Adobe Analytics do DTM terminar o carregamento.
   >* Dependendo de onde o Rastreador de página do Assets Insights está hospedado (por exemplo, AEM, CDN e assim por diante), a origem da origem do script pode exigir alterações.
   >* Para o Rastreador de página hospedado AEM, a origem deve apontar para uma instância de publicação usando o nome do host da instância do dispatcher.


1. Abrir [https://dtm.adobe.com](https://dtm.adobe.com). Clique em Visão geral na propriedade da Web e clique em Adicionar ferramenta ou abra uma Ferramenta Adobe Analytics existente. Ao criar a ferramenta, é possível definir o Método de configuração como Automático.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Selecione Conjuntos de relatórios de preparo/produção, conforme apropriado.

1. Expandir **[!UICONTROL Gerenciamento de biblioteca]** e assegurar que **[!UICONTROL Carregar biblioteca em]** está definida como **[!UICONTROL Início da página]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Expandir **[!UICONTROL Personalizar código de página]** e clique ou toque em **[!UICONTROL Abrir editor]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. Cole o seguinte código na janela:

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * A regra de carregamento de página no DTM inclui apenas o código pagetracker.js . Qualquer `assetAnalytics` são considerados substituições de valores padrão. Elas não são exigidas por padrão.
   * As chamadas de código `assetAnalytics.dispatcher.init()` depois de `_satellite.getToolsByType('sc')[0].getS()` é inicializado e `assetAnalytics,dispatcher.init` está disponível. Portanto, você pode ignorar a adição na etapa 11.
   * Conforme indicado nos comentários dentro do código do Rastreador de página do Insights (**[!UICONTROL Ferramentas > Ativos > Rastreador de página do Insights]**), quando o Rastreador de página não cria um `AppMeasurement` , os três primeiros argumentos (RSID, Servidor de rastreamento e Namespace do visitante) são irrelevantes. Strings vazias são passadas para realçar isso.

      Os argumentos restantes correspondem ao que está configurado na página Configuração do Insights (**[!UICONTROL Ferramentas > Ativos > Configuração do Insights]**).

   * O objeto AppMeasurement é recuperado por meio de uma consulta `satelliteLib` para todos os mecanismos de SiteCatalyst disponíveis. Se várias tags estiverem configuradas, altere o índice do seletor de matriz apropriadamente. As entradas no array são solicitadas de acordo com as ferramentas do SiteCatalyst disponíveis na interface do DTM.

1. Salve e feche a janela Editor de código e salve as alterações na configuração da Ferramenta.
1. No **[!UICONTROL Aprovações]** , aprove as aprovações pendentes. A tag do DTM está pronta para inserção na página da Web. Para obter detalhes sobre como inserir tags DTM em páginas da Web, consulte a página arquivada sobre [integração do DTM em modelos de página personalizados](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
