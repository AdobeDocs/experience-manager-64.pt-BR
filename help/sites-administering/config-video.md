---
title: Configurar o componente de Vídeo
seo-title: Configure the Video component
description: Saiba como configurar o Componente de vídeo.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 2%

---

# Configurar o componente de Vídeo {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O [Componente de vídeo](/help/sites-authoring/default-components-foundation.md#video) permite colocar um elemento de vídeo OOTB (pronto para uso) predefinido na sua página.

Para que ocorra a transcodificação adequada, o administrador deve [Instale o FFmpeg e configure o AEM](#install-ffmpeg) separadamente. Eles também podem [Configurar os perfis de vídeo](#configure-video-profiles) para uso com elementos HTML5.

>[!CAUTION]
>
>Não é mais esperado que esse componente funcione imediatamente sem uma personalização abrangente no nível do projeto.

## Configurar perfis de vídeo {#configure-video-profiles}

Talvez você queira definir perfis de vídeo para usar em elementos do HTML5. Os escolhidos aqui são usados em ordem. Para acessar, use [Modo Design](/help/sites-authoring/default-components-designmode.md) (Somente interface clássica) e selecione o **[!UICONTROL Perfis]** guia :

![chlimage_1-317](assets/chlimage_1-317.png)

Você também pode configurar o design dos componentes e parâmetros de vídeo para [!UICONTROL Reprodução], [!UICONTROL Flash]e [!UICONTROL Avançado].

## Instale o FFmpeg e configure o AEM {#install-ffmpeg}

O Componente de vídeo depende do produto FFmpeg de código aberto de terceiros para obter a transcodificação adequada dos vídeos que podem ser baixados de [https://ffmpeg.org/](https://ffmpeg.org/). Após instalar o FFmpeg, é necessário configurar o AEM para usar um codec de áudio específico e opções específicas de tempo de execução.

**Para instalar o FFmpeg para a sua plataforma**:

* **No Windows:**

   1. Baixe o binário compilado como `ffmpeg.zip`
   1. Descompacte para uma pasta.
   1. Definir a variável de ambiente do sistema `PATH` para `<*your-ffmpeg-locatio*n>\bin`
   1. Reinicie o AEM.

* **No Mac OS X:**

   1. Instalar Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Instale o XQuartz/X11.
   1. Instale o MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. No console, execute o seguinte comando e siga as instruções:

      `sudo port install ffmpeg`

      `FFmpeg` deve estar em `PATH` para que AEM possa selecioná-lo por meio da linha de comando.

* **Uso da versão pré-compilada para o OS X 10.6:**

   1. Baixe a versão pré-compilada.
   1. Extraia-o para o `/usr/local` diretório.
   1. No terminal, execute:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Para configurar AEM**:

1. Abrir [!UICONTROL CRXDE Lite] no navegador da Web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Selecione o `/libs/settings/dam/video/format_aac/jcr:content` e garanta que as propriedades do nó sejam as seguintes:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Para personalizar a configuração, crie uma sobreposição em `/apps/settings/` nó e mova a mesma estrutura em `/conf/global/settings/` nó . Não pode ser editado em `/libs` nó . Por exemplo, para sobrepor o caminho `/libs/settings/dam/video/fullhd-bp`, crie-o em `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Sobreponha e edite todo o nó do perfil e não apenas a propriedade que precisa de modificação. Esses recursos não são resolvidos através do SlingResourceMerger.

1. Se tiver alterado qualquer uma das propriedades, clique em **[!UICONTROL Salvar tudo]**.

>[!NOTE]
>
>Os modelos de fluxo de trabalho OOTB não são preservados quando você atualiza sua instância do AEM. O Adobe recomenda que você copie modelos de fluxo de trabalho OTB antes de editá-los. Por exemplo, copie o modelo de Ativo de atualização do DAM OOTB antes de editar a etapa Transcodificação do FFmpeg no modelo de Ativo de atualização do DAM para escolher nomes de perfil de vídeo existentes antes da atualização. Em seguida, é possível sobrepor o `/apps` nó para permitir AEM recuperar as alterações personalizadas no modelo OOTB.
