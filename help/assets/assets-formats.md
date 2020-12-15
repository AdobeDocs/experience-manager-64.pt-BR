---
title: Formatos de arquivo suportados no AEM Assets
description: Lista de formatos de arquivos e tipos MIME suportados pela AEM Assets e os recursos compatíveis com cada formato.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2baa172088f646752e85168d432d46942ac8244e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 9%

---


# Formatos de arquivos suportados no AEM Assets {#assets-supported-formats}

A AEM Assets oferece suporte a uma grande variedade de formatos de arquivo e cada funcionalidade tem suporte variado para diferentes tipos de MIME.

Para integrar a AEM Assets com outras soluções de gerenciamento de ativos digitais (DAM) compatíveis com padrões e software para desktop, use a Plataforma extensível de metadados (XMP) da Adobe.

Use a legenda para entender o nível de suporte.

| Nível de suporte | Descrição |
|:---:|---|
| Satélite | Compatível |
| * | Suportado com recursos complementares |
| - | Não aplicável |

## Formatos de imagem rasterizados {#supported-raster-image-formats}

Os formatos de imagem rasterizados compatíveis com os recursos de gerenciamento de ativos são os seguintes:

| Formato | Armazenamento | Gerenciamento de metadados | Extração de metadados | Geração de miniaturas | Edição interativa | Writeback de metadados | Insights |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| GIF | Satélite | Satélite | Satélite | Satélite | Satélite |  | Satélite |
| TIFF | Satélite | Satélite | Satélite | Satélite |  | Satélite | Satélite |
| JPEG | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| BMP | Satélite | Satélite | Satélite | Satélite | Satélite |  | Satélite |
| PNM | Satélite | Satélite |  |  |  |  | Satélite |
| PGM | Satélite | Satélite |  |  |  |  | Satélite |
| PBM | Satélite | Satélite |  |  |  |  | Satélite |
| PPM | Satélite | Satélite |  |  |  |  | Satélite |
| PSD **‡** | Satélite | Satélite | Satélite | Satélite |  |  | Satélite |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite | Satélite | Satélite | Satélite |  | Satélite |  |
| PICT |  |  |  |  |  |  | Satélite |
| PSB | Satélite | Satélite | Satélite | Satélite |  |  |  |

**‡** A imagem mesclada é extraída do arquivo PSD. É uma imagem gerada pela Adobe Photoshop e incluída no arquivo PSD. Dependendo das configurações, a imagem mesclada pode ou não ser a imagem real.

Os formatos de imagem rasterizados compatíveis com os recursos do Dynamic Media são os seguintes:

| Formato | Carregar<br> (Formato de entrada) | Create<br> image<br> preset<br> (formato de saída) | Pré-visualização<br> representação dinâmica<br> | Entrega<br> representação dinâmica<br> | Baixar<br> representação dinâmica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | Satélite | Satélite | Satélite | Satélite | Satélite |
| GIF | Satélite | Satélite | Satélite | Satélite | Satélite |
| TIFF | Satélite | Satélite | Satélite | Satélite | Satélite |
| JPEG | Satélite | Satélite | Satélite | Satélite | Satélite |
| BMP | Satélite |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **‡** | Satélite |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite | Satélite | Satélite | Satélite | Satélite |
| PICT | Satélite |  |  |  |  |
| PSB |  |  |  |  |  |

**‡** A imagem mesclada é extraída do arquivo PSD. É uma imagem gerada pela Adobe Photoshop e incluída no arquivo PSD. Dependendo das configurações, a imagem mesclada pode ou não ser a imagem real.

Além das informações acima, considere o seguinte:

* O suporte para arquivos EPS se aplica somente a imagens rasterizadas. Por exemplo, a geração de miniaturas para imagens vetoriais EPS não é suportada por padrão. Para adicionar suporte, [configure ImageMagick](best-practices-for-imagemagick.md). Para integrar ferramentas de terceiros para ativar recursos adicionais, consulte [Manipulador de Mídia baseado na linha de comando](media-handlers.md#command-line-based-media-handler).

* A gravação de metadados funciona no formato de arquivo PSB quando é adicionada ao manipulador `NComm`.

* Para usar o Dynamic Media para pré-visualização e gerar renderizações dinâmicas para arquivos EPS, consulte [formatos de arquivo Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para arquivos EPS, o write-back de metadados é compatível com a versão 3.0 ou posterior da Convenção de estruturação de Documentos PostScript (PS-Adobe).

## Formatos de imagem rasterizada não suportados no Dynamic Media {#unsupported-image-formats-dynamic-media}

A lista a seguir descreve os subtipos de formatos de arquivo de imagem rasterizada que são *não* suportados no Dynamic Media.

Consulte também [Detectar formatos de arquivo não suportados para Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* Arquivos PNG com um tamanho de bloco IDAT maior que 100 MB.
* Arquivos PSB.
* Arquivos PSD com um espaço de cor diferente de CMYK, RGB, Escala de cinza ou Bitmap não são suportados. Espaços de cores Indexadas, Lab e DuoTone não são suportados.
* Arquivos PSD com uma profundidade de bits superior a 16.
* Arquivos TIFF com dados de ponto flutuante.
* Arquivos TIFF com espaço de cor Lab.

## Biblioteca do PDF Rasterizer {#supported-pdf-rasterizer-library}

A biblioteca do Adobe PDF Rasterizer gera miniaturas e pré-visualizações de alta qualidade para arquivos PDF e Adobe Illustrator grandes e com grande quantidade de conteúdo. O Adobe recomenda usar a biblioteca do Rasterizer de PDF para o seguinte:

* Arquivos AI/PDF com uso intenso de conteúdo que consomem muitos recursos para serem processados.
* Arquivos AI/PDF, para os quais as miniaturas não são geradas por padrão.
* Arquivos AI com cores Pantone Matching System (PMS).

Consulte [Usando o Rasterizer de PDF](aem-pdf-rasterizer.md).

## Biblioteca de transcodificação de imagens {#supported-image-transcoding-library}

A Biblioteca de transcodificação de imagens do Adobe é uma solução de processamento de imagens que executa funções essenciais de manipulação de imagens, como codificação, transcodificação, redefinição de resolução e redimensionamento.

A Biblioteca de transcodificação de imagens suporta JPG/JPEG, PNG (8 bits e 16 bits), GIF, BMP, TIFF/Compressed TIFF (exceto arquivos TIFF de 32 bits e arquivos PTIFF), ICO e ICN MIME.

Consulte [Biblioteca de transcodificação de imagens](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

A biblioteca do Adobe Camera Raw permite que o AEM Assets assimile imagens brutas. Consulte [Suporte Camera Raw](camera-raw.md).

## Formatos de documento {#supported-document-formats}

Os formatos de documento suportados para recursos de gerenciamento de ativos são os seguintes:

| Formato | Armazenamento | Gerenciamento de metadados<br> | Extração de texto completo<br> | Extração Metadados<br> | Geração de miniatura<br> | Extração Subasset<br> | Writeback de metadados<br> |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite | Satélite |  | Satélite | Satélite | Satélite | Satélite |
| DOC | Satélite | Satélite | Satélite | Satélite |  |  |  |
| DOCX | Satélite | Satélite | Satélite | Satélite |  |  |  |
| ODT | Satélite | Satélite | Satélite |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| HTML | Satélite | Satélite | Satélite |  |  |  |  |
| RTF | Satélite | Satélite | Satélite |  |  |  |  |
| TXT | Satélite | Satélite | Satélite |  |  |  |  |
| XLS | Satélite | Satélite | Satélite |  |  |  |  |
| XLSX | Satélite | Satélite | Satélite | Satélite |  |  |  |
| ODS | Satélite | Satélite | Satélite |  |  |  |  |
| PPT | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| PPTX | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| ODP | Satélite | Satélite | Satélite |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | Satélite | Satélite |  | Satélite | Satélite | Satélite | Satélite |
| PS | Satélite | Satélite |  |  |  |  |  |
| QXP | Satélite | Satélite |  |  |  |  |  |
| EPUB | Satélite | Satélite |  | Satélite | Satélite |  |  |

Os formatos de documento suportados para os recursos do Dynamic Media são os seguintes:

| Formato | Carregar<br> (Formato de entrada) | Create<br> image<br> preset<br> (formato de saída) | Pré-visualização<br> representação dinâmica<br> | Entrega<br> representação dinâmica<br> | Baixar<br> representação dinâmica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | Satélite | Satélite | Satélite | Satélite | Satélite |
| HTML |  |  |  |  |  |
| TTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | Satélite |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Além da funcionalidade acima, considere o seguinte:

* Para usar o Dynamic Media para gerar renderizações dinâmicas para arquivos PDF, consulte [formatos de arquivo Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para usar o Dynamic Media para pré-visualização e gerar renderizações dinâmicas para arquivos AI, consulte [formatos de arquivo Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Para usar o Dynamic Media para gerar execuções dinâmicas para arquivos INDD, consulte [formato de arquivo InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formatos de multimídia {#supported-multimedia-formats}

| Formato | Armazenamento | Gerenciamento de metadados | Extração de metadados | Geração de miniaturas | Transcodificação FMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | Satélite | Satélite |  | - | * |
| MIDI | Satélite | Satélite |  | - | * |
| 3GP | Satélite | Satélite |  | - | * |
| MP3 | Satélite | Satélite | Satélite | - | * |
| MPG | Satélite | Satélite |  | - | * |
| OGA | Satélite | Satélite |  | - | * |
| OGG | Satélite | Satélite |  | - | * |
| RA | Satélite | Satélite |  | - | * |
| WAV | Satélite | Satélite |  | - | * |
| WMA | Satélite | Satélite |  | - | * |
| DVI | Satélite | Satélite |  | * | * |
| FLV | Satélite | Satélite |  | * | * |
| M4V | Satélite | Satélite |  | * | * |
| MPEG | Satélite | Satélite |  | * | * |
| OGV | Satélite | Satélite |  | * | * |
| MOV | Satélite | Satélite |  | * | * |
| WMV | Satélite | Satélite |  | * | * |
| SWF | Satélite | Satélite |  |  |  |

## Formatos de vídeo de entrada para Dynamic Media Transcoding {#supported-input-video-formats-for-dynamic-media-transcoding}

| Extensão do arquivo de vídeo | Container | Codecs de vídeo recomendados | Codecs de vídeo não suportados |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (todos os perfis) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Animação da Apple |
| FLV, F4V | Flash Adobe | H264/AVC, Flix VP6, H263, Sorenson | SWF (arquivos de animação vetorial) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | Intercalação A/V | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | VP8 do Google |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Vídeo vermelho bruto | MJPEG 2000 |  |
| RAM, RM | RealVideo | Não suportado | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Flash nativo | Codec de áudio sem perda gratuito |  |
| MJ2 | Motion JPEG 2000 | Codec Motion JPEG 2000 |  |

## Formatos de arquivo {#supported-archive-formats}

Os formatos de arquivamento suportados e a aplicabilidade dos workflows DAM comuns são abordados na tabela a seguir.

| Formato | Armazenamento | Versões | Fluxo de trabalho | Publicação | Controle de acesso | delivery Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| JAR | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| RAR | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| TAR | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| ZIP **†** | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |

**†** A imagem mesclada é extraída do arquivo PSD. É uma imagem gerada pela Adobe Photoshop e incluída no arquivo PSD. Dependendo das configurações, a imagem mesclada pode ou não ser a imagem real. Os arquivos ZIP criados com o algoritmo `Deflate64` têm suporte limitado no AEM. Não há suporte para operações de arquivamento e desarquivamento. No entanto, operações como upload, navegação e download são suportadas.

## Outros formatos suportados {#other-supported-formats}

A aplicabilidade de workflows DAM comuns para alguns outros formatos de arquivo está descrita na tabela abaixo.

| Formato | Armazenamento | Versões | Fluxo de trabalho | Publicação | Controle de acesso | delivery Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| SVG | Satélite | Satélite | Satélite | Satélite | Satélite |  |
| CSS | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| VTT | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| XML | Satélite | Satélite | Satélite | Satélite | Satélite | Satélite |
| JavaScript (quando configurado com o próprio domínio do delivery) |  |  |  |  |  | Satélite |

**#** Os outros formatos são suportados no DAM para gerenciamento de armazenamentos, versões, ACL, fluxo de trabalho, publicação e metadados.

## Tipos MIME suportados {#supported-mime-types}

Por padrão, AEM detecta o tipo de arquivo usando a extensão de arquivo. AEM pode detectá-lo do conteúdo dos arquivos. Para a última opção, selecione [!UICONTROL Detectar MIME da opção content] em [!UICONTROL Day CQ DAM Mime Type Service] no Console da Web AEM.

Uma lista de tipos MIME suportados está disponível no CRXDE Lite em `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Extensão de arquivo | Tipo MIME/tipo de mídia da Internet | Valor de jobParam padrão | Valor jobParam permitido |
|---|---|---|---|
| Imagem | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | O jobParam padrão se aplica a todos os ativos do tipo mime de imagem.<ul><li>[knockoutBackgroundOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharMaskOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcluirVídeoMestreDeAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcluirVídeoMestreDeAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Habilite o suporte](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) ao parâmetro de trabalho de upload de ativos/Scene7 baseados em tipos MIME.
>* [Configure o tipo de MIME baseado no suporte](config-dynamic.md) de parâmetros de trabalho de upload.

