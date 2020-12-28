---
title: Configurar o componente Vídeo
seo-title: Configurar o componente Vídeo
description: Saiba como configurar o Componente de vídeo.
seo-description: Saiba como configurar o Componente de vídeo.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
translation-type: tm+mt
source-git-commit: d2b4e6599a7b1c01dc220a03b2be9aa55e5d7458
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 8%

---


# Configurar o componente de Vídeo {#configure-the-video-component}

O [Componente de vídeo](/help/sites-authoring/default-components-foundation.md#video) permite que você coloque um elemento de vídeo OOTB (out-of-the-box) predefinido na sua página.

Para que ocorra a transcodificação correta, o administrador deve [Instalar FFmpeg e configurar AEM](#install-ffmpeg) separadamente. Eles também podem [Configurar os perfis de vídeo](#configure-video-profiles) para uso com elementos de HTML5.

## Configurar perfis de vídeo {#configure-video-profiles}

Talvez você queira definir perfis de vídeo para usar em elementos HTML5. Os escolhidos aqui são usados em ordem. Para acessar, use o [Modo de design](/help/sites-authoring/default-components-designmode.md) (Somente interface clássica) e selecione a guia **[!UICONTROL Perfis]**:

![chlimage_1-317](assets/chlimage_1-317.png)

Você também pode configurar o design dos componentes e parâmetros do vídeo para [!UICONTROL Reprodução], [!UICONTROL Flash] e [!UICONTROL Avançado].

## Instalar FFmpeg e configurar AEM {#install-ffmpeg}

O Componente de vídeo depende do produto FFmpeg de código aberto de terceiros para a transcodificação adequada de vídeos que podem ser baixados de [https://ffmpeg.org/](https://ffmpeg.org/). Depois de instalar o FFmpeg, é necessário configurar o AEM para usar um codec de áudio específico e opções específicas de tempo de execução.

**Para instalar o FFmpeg para a sua plataforma**:

* **No Windows:**

   1. Baixe o binário compilado como `ffmpeg.zip`
   1. Descompacte para uma pasta.
   1. Defina a variável de ambiente do sistema `PATH` como `<*your-ffmpeg-locatio*n>\bin`
   1. Reinicie o AEM.

* **No Mac OS X:**

   1. Instalar Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Instale o XQuartz/X11.
   1. Instale o MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. No console, execute o seguinte comando e siga as instruções:

      `sudo port install ffmpeg`

      `FFmpeg` deve estar dentro  `PATH` para que AEM possa pegá-lo pela linha de comando.

* **Usar a versão pré-compilada para o OS X 10.6:**

   1. Baixe a versão pré-compilada.
   1. Extraia-o para o diretório `/usr/local`.
   1. No terminal, execute:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Para configurar AEM**:

1. Abra [!UICONTROL CRXDE Lite] no navegador da Web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Selecione o nó `/libs/settings/dam/video/format_aac/jcr:content` e verifique se as propriedades do nó são as seguintes:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Para personalizar a configuração, crie uma sobreposição no nó `/apps/settings/` e mova a mesma estrutura no nó `/conf/global/settings/`. Não pode ser editado no nó `/libs`. Por exemplo, para sobrepor o caminho `/libs/settings/dam/video/fullhd-bp`, crie-o em `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Sobreponha e edite todo o nó do perfil e não apenas a propriedade que precisa de modificação. Tais recursos não são resolvidos através da SlingResourceFusão.

1. Se você alterou qualquer uma das propriedades, clique em **[!UICONTROL Salvar tudo]**.

>[!NOTE]
>
>Os modelos de fluxo de trabalho OTB não são preservados quando você atualiza sua instância AEM. O Adobe recomenda que você copie modelos de fluxo de trabalho OTB antes de editá-los. Por exemplo, copie o modelo de Ativo de atualização de DAM OOTB antes de editar a etapa de Transcodificação FFmpeg no modelo de Ativo de atualização de DAM para selecionar nomes de perfis de vídeo existentes antes da atualização. Em seguida, você pode sobrepor o nó `/apps` para permitir que AEM recupere as alterações personalizadas no modelo OTB.

