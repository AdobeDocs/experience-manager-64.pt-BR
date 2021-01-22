---
title: Imagens panorâmicas
Description: Learn how to work with panoramic images in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 4%

---


# Imagens panorâmicas {#panoramic-images}

Esta seção descreve como trabalhar com o visualizador Imagem panorâmica para renderizar imagens panorâmicas esféricas para uma experiência de visualização de 360° imersiva de uma sala, propriedade, local ou paisagem.

Consulte também [Gerenciar predefinições do visualizador](managing-viewer-presets.md).

![panorâmica-image2](assets/panoramic-image2.png)

## Fazer upload de ativos para uso com o Visualizador de imagem panorâmica {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Para um ativo carregado se qualificar como uma imagem de panorama esférica que você pretende usar com o visualizador de Imagem panorâmica, o ativo deve ter um ou ambos os seguintes itens:

* Uma proporção largura/altura de 2.

   Você pode substituir a configuração de proporção padrão de 2 em **[!UICONTROL CRXDE Lite]** no seguinte:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Marcado com as palavras-chave `equirectangular`, ou `spherical` e `panorama`, ou `spherical` e `panoramic`. Consulte [Usando tags](/help/sites-authoring/tags.md).

Tanto a proporção quanto os critérios de palavra-chave se aplicam aos ativos panorâmicos da página de detalhes do ativo e o componente **[!UICONTROL Panorâmica Media]** 

Para fazer upload de ativos para uso com o visualizador de Imagem panorâmica, consulte [Fazer upload de ativos](managing-assets-touch-ui.md#uploading-assets).

## Configuração do Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Para que o visualizador de Imagem panorâmica funcione corretamente no AEM, é necessário sincronizar as predefinições do visualizador de Imagem panorâmica com os metadados específicos do Dynamic Media Classic e do Dynamic Media Classic para que as predefinições do visualizador sejam atualizadas no JCR. Para fazer isso, configure o Dynamic Media Classic da seguinte maneira:

1. [Faça logon em seu ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) aplicativo de desktop Dynamic Media Classic para cada conta de empresa.

1. Perto do canto superior direito da página, clique em **[!UICONTROL Configuração > Configuração de aplicativo > Configuração de publicação > Servidor de imagem]**.
1. Na página **[!UICONTROL Publicar no servidor de imagens]**, no menu suspenso **[!UICONTROL Publicar contexto]** próximo à parte superior, selecione **[!UICONTROL Servidor de imagens]**.

1. Na mesma página **[!UICONTROL Publicar no servidor de imagens]**, localize o cabeçalho **[!UICONTROL Atributos de solicitação]**.
1. No cabeçalho **[!UICONTROL Atributos de solicitação]**, localize **[!UICONTROL Limite de tamanho de imagem de resposta]**. Em seguida, nos campos associados **[!UICONTROL Largura]** e **[!UICONTROL Altura]**, aumente o tamanho máximo de imagem permitido para imagens panorâmicas.

   O Dynamic Media Classic tem um limite de 25.000.000 pixels. O tamanho máximo permitido para imagens com uma proporção de 2:1 é 7000 x 3500. No entanto, para telas típicas de desktop, 4096 x 2048 pixels são suficientes.

   >[!NOTE]
   >
   >Somente as imagens que se encaixam no tamanho máximo permitido de imagem são suportadas. As solicitações de imagens acima do limite de tamanho resultarão em uma resposta 403.

1. No cabeçalho **[Atributos de solicitação]**, faça o seguinte:

   * Defina **[!UICONTROL Modo de ofuscação de solicitação]** como **[!UICONTROL Desativado]**.
   * Defina **[!UICONTROL Modo de bloqueio de solicitação]** como **[!UICONTROL Desativado]**.

   Essas configurações são necessárias para o uso do componente **[!UICONTROL Mídia panorâmica]** no AEM.

1. Na parte inferior da página **[!UICONTROL Publicar no Servidor de Imagens]**, no lado esquerdo, toque em **[!UICONTROL Salvar]**.

1. No canto inferior direito, toque em **[!UICONTROL Close]**.

### Solução de problemas do componente de mídia panorâmica {#troubleshooting-the-panoramic-media-wcm-component}

Se você soltou uma imagem no componente **[!UICONTROL Panorâmica Media]** no WCM e o placeholder do componente entrou em colapso, talvez você queira solucionar o seguinte:

* Se você encontrar um erro 403 Proibido, ele pode ter sido causado pelo tamanho da imagem solicitada ser muito grande. Revise as configurações *Limite de tamanho de imagem de resposta* em [Configuração do Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Para um *Bloqueio inválido* no ativo ou *Erro de análise* exibido na página, marque **[!UICONTROL Modo de ofuscação de solicitação]** e **[!UICONTROL Modo de bloqueio de solicitação]** para garantir que eles estejam desativados.
* Para um erro de tela contaminada, configure um **[!UICONTROL Caminho do arquivo de definição de conjunto de regras e Invalide CTN]** para as solicitações anteriores do ativo de imagem.
* Se a qualidade da imagem ficar muito baixa depois de uma solicitação de imagem com dimensionamento acima do limite suportado, verifique se a configuração **[!UICONTROL Atributos de codificação JPEG > Quality]** não está vazia. Uma configuração típica para o campo **[!UICONTROL Quality]** é `95`. Você pode encontrar a configuração na página **[!UICONTROL Publicar]** do servidor de imagens. Para acessar a página, consulte [Configuração do Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Visualização de imagens panorâmicas {#previewing-panoramic-images}

Consulte [Visualizar ativos](previewing-assets.md).

## Publicar imagens panorâmicas {#publishing-panoramic-images}

Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
