---
title: Imagens panorâmicas
description: Saiba como trabalhar com imagens panorâmicas no Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# Imagens panorâmicas {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta seção descreve como trabalhar com o visualizador de Imagem panorâmica para renderizar imagens panorâmicas esféricas para uma experiência de visualização imersiva de 360° de uma sala, propriedade, localização ou paisagem.

Consulte também [Gerenciar predefinições do visualizador](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Fazer upload de ativos para uso com o visualizador de Imagem panorâmica {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Para que um ativo carregado seja qualificado como uma imagem panorâmica esférica que você pretende usar com o visualizador de Imagem panorâmica, o ativo deve ter um ou ambos os itens a seguir:

* Uma proporção largura/altura de 2.

   Você pode substituir a configuração padrão de proporção de aspecto de 2 pol. **[!UICONTROL CRXDE Lite]** no seguinte:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Marcado com as palavras-chave `equirectangular`ou `spherical`e `panorama`ou `spherical` e `panoramic`. Consulte [Uso de tags](/help/sites-authoring/tags.md).

Tanto a proporção quanto os critérios de palavra-chave se aplicam aos ativos panorâmicos da página de detalhes do ativo e o componente **[!UICONTROL Panorâmica Media]** 

Para fazer upload de ativos para uso com o visualizador de Imagem panorâmica, consulte [Fazer upload de ativos](managing-assets-touch-ui.md#uploading-assets).

## Configuração do Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Para que o visualizador de Imagem panorâmica funcione corretamente no AEM, é necessário sincronizar as predefinições do visualizador de Imagem panorâmica com os metadados específicos do Dynamic Media Classic e do Dynamic Media Classic para que as predefinições do visualizador sejam atualizadas no JCR. Para fazer isso, configure o Dynamic Media Classic da seguinte maneira:

1. [Faça logon no aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) para cada conta da empresa.

1. Ao lado do canto superior direito da página, clique em **[!UICONTROL Configuração > Configuração do aplicativo > Configuração de publicação > Servidor de imagem]**.
1. No **[!UICONTROL Publicação do servidor de imagens]** da página **[!UICONTROL Publicar contexto]** no menu suspenso próximo à parte superior, selecione **[!UICONTROL Serviço de imagem]**.

1. No mesmo **[!UICONTROL Publicação do servidor de imagens]** localize o cabeçalho **[!UICONTROL Atributos da solicitação]**.
1. Em **[!UICONTROL Atributos da solicitação]** cabeçalho, localizar **[!UICONTROL Limite de tamanho da imagem de resposta]**. Em seguida, no **[!UICONTROL Largura]** e **[!UICONTROL Altura]** aumentar o tamanho máximo de imagem permitido para imagens panorâmicas.

   O Dynamic Media Classic tem um limite de 25.000.000 pixels. O tamanho máximo permitido para imagens com uma proporção de aspecto de 2:1 é 7000 x 3500. No entanto, para telas típicas de desktop, 4096 x 2048 pixels é suficiente.

   >[!NOTE]
   >
   >Somente imagens que se encaixam no tamanho máximo permitido da imagem são suportadas. As solicitações de imagens acima do limite de tamanho resultarão em uma resposta 403.

1. Em **[Atributos da solicitação]** , faça o seguinte:

   * Definir **[!UICONTROL Modo de ofuscação de solicitação]** para **[!UICONTROL Desabilitado]**.
   * Definir **[!UICONTROL Modo de bloqueio de solicitação]** para **[!UICONTROL Desabilitado]**.

   Essas configurações são necessárias para usar a variável **[!UICONTROL Mídia panorâmica]** no AEM.

1. Na parte inferior do **[!UICONTROL Publicação do servidor de imagens]** no lado esquerdo, toque em **[!UICONTROL Salvar]**.

1. No canto inferior direito, toque em **[!UICONTROL Fechar]**.

### Solução de problemas do componente Mídia panorâmica {#troubleshooting-the-panoramic-media-wcm-component}

Se você soltou uma imagem na **[!UICONTROL Mídia panorâmica]** no WCM e o placeholder do componente recolhidos, talvez você queira solucionar os seguintes problemas:

* Se você tiver um erro 403 Forbidden , ele pode ter sido causado pelo tamanho da imagem solicitada ser muito grande. Revise o *Limite de tamanho da imagem de resposta* configurações em [Configuração do Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Para um *Bloqueio inválido* no ativo ou *Erro de análise* exibido na página, marque **[!UICONTROL Modo de ofuscação de solicitação]** e **[!UICONTROL Modo de bloqueio de solicitação]** para garantir que estejam desativadas.
* Para um erro de tela contaminada, configure um **[!UICONTROL Caminho do arquivo de definição do conjunto de regras e Invalidar o CTN]** para as solicitações anteriores do ativo de imagem.
* Se a qualidade da imagem ficar muito baixa depois de uma solicitação de imagem com dimensionamento acima do limite suportado, verifique se a variável **[!UICONTROL Atributos de codificação JPEG > Qualidade]** não está vazia. Uma configuração típica para a variável **[!UICONTROL Qualidade]** é `95`. Você pode encontrar a configuração no **[!UICONTROL Publicação do servidor de imagens]** página. Para acessar a página, consulte [Configuração do Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Visualização de imagens panorâmicas {#previewing-panoramic-images}

Consulte [Visualização de ativos](previewing-assets.md).

## Publicação de imagens panorâmicas {#publishing-panoramic-images}

Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
