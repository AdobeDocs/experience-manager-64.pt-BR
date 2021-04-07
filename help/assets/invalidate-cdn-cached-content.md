---
title: Invalidação do conteúdo em cache do CDN
seo-title: Invalidação do conteúdo em cache do CDN
description: A invalidação do conteúdo em cache CDN (Content Delivery Network) permite atualizar rapidamente os ativos entregues pela Dynamic Media, em vez de esperar que o cache expire.
seo-description: A invalidação do conteúdo em cache CDN (Content Delivery Network) permite atualizar rapidamente os ativos entregues pela Dynamic Media, em vez de esperar que o cache expire.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Gerenciamento de ativos,Cache CDN
role: Administrator,Business Practitioner,Developer
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 28%

---

# Invalidação do conteúdo em cache do CDN {#invalidating-your-cdn-cached-content}

Os ativos do Dynamic Media são armazenados em cache pela CDN para entrega rápida. No entanto, quando você faz atualizações em um ativo, pode desejar que essas alterações entrem em vigor imediatamente. A invalidação do conteúdo em cache CDN (Content Delivery Network) permite atualizar rapidamente os ativos entregues pela Dynamic Media, em vez de esperar que o cache expire.

Consulte também [Visão geral do cache no Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Para invalidar o conteúdo em cache do CDN:**

1. Faça logon no aplicativo de desktop do Dynamic Media Classic.

   [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app)

   Suas credenciais e logon foram fornecidas pelo Adobe no momento do provisionamento. Caso não tenha essas informações, entre em contato com o Suporte Técnico.

1. Clique em **[!UICONTROL Configuração > Configuração do aplicativo > Configurações gerais]**.
1. Na página Configurações gerais do aplicativo , no cabeçalho do grupo Servidores , localize a caixa de texto **[!UICONTROL Modelo de invalidação CDN]** .

1. Especifique o modelo que é usado para invalidar o cache CDN (Content Delivery Network).

   Por exemplo, suponha que você insira um URL de imagem (incluindo predefinições ou modificadores de imagem) que faça referência a `<ID>`, em vez de uma ID de imagem específica, como no exemplo a seguir:

   `https://server.com/is/image/Company/<ID>?$product$`

   Se o Modelo contiver apenas `<ID>`, o Dynamic Media preencherá `https://<server>/is/image`, onde `<server>` é o Nome do Servidor de Publicação definido em Configurações Gerais e &lt;ID> é o(s) ativo(s) selecionado(s) para invalidação.

1. No canto inferior direito da página, clique em **[!UICONTROL Fechar]**.
1. Na interface do usuário do aplicativo de desktop do Dynamic Media Classic, selecione um ou mais ativos e clique em **[!UICONTROL File > Invalidate CDN]**. Você verá uma lista de um ou mais URLs gerados a partir do modelo criado e dos ativos selecionados. Ele usa o URL do servidor listado em &quot;Nome do servidor publicado&quot; nas Configurações gerais do aplicativo.

   Por exemplo, com o Modelo de Invalidação CDN definido na etapa anterior, suponha que você tenha selecionado uma única imagem de ativo de imagem chamada `Backpack_B`. Ao clicar em **[!UICONTROL File > Invalidate CDN]**, o resultado será o seguinte URL gerado na interface do usuário de Invalidação CDN:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Na caixa de listagem URL, clique em **[!UICONTROL Continue]** para limpar o cache de cada URL específico. Observe que é possível editar um URL ou adicionar um URL digitando-o ou colando-o na caixa de listagem do URL; não é necessário definir o Modelo de Invalidação CDN antecipadamente.

   Depois de clicar em **[!UICONTROL Continuar]**, é exibido um indicador que fornece uma estimativa de quanto tempo levará para limpar o cache.

   Se você selecionou vários ativos e clicou em **[!UICONTROL Arquivo > Invalidar CDN]**, cada ativo é referenciado no **[!UICONTROL URL de modelo]** salvo. Portanto, você pode definir um **[!UICONTROL Modelo de invalidação CDN]** referenciando cada predefinição de imagem do URL referenciada em seu site (como detalhes do produto, resultados de pesquisa e assim por diante). Em seguida, ao selecionar uma ou mais imagens para invalidação do cache, os URLs preenchem automaticamente a interface.

   >[!NOTE]
   >
   >Ao selecionar ativos e, em seguida, clicar em **[!UICONTROL Arquivo > Invalidar CDN]**, o Dynamic Media usa um modelo CDN de invalidação para criar URLs automaticamente com o objetivo de invalidar a partir da Rede de fornecimento de conteúdo (CDN). Se não houver nada na caixa de texto **[!UICONTROL Invalidar modelo CDN]**, você receberá uma lista de URLs em branco. O armazenamento em cache na CDN não se baseia em ativos, ele é baseado em URL. Portanto, é necessário estar ciente de todos os URLs que estão em seu site. Depois de determinar esses URLs, você pode adicioná-los à caixa de texto **[!UICONTROL Invalidar modelo CDN]** anteriormente nas etapas. Em seguida, selecione esses ativos e invalide os URLs em uma etapa.
   >
   >Outra opção é adicionar URLs completos à lista **[!UICONTROL Invalidar CDN]**. Se você seguir essa abordagem, não será necessário selecionar ativos no Dynamic Media Classic antes de ir para a opção **[!UICONTROL File > Invalidate CDN]** .
