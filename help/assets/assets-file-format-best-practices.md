---
title: Práticas recomendadas de formato de arquivo de ativos
description: Práticas recomendadas para o suporte a arquivos no [!DNL Experience Manager] Ativos.
contentOwner: AG
feature: Asset Management,Developer Tools
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 2%

---

# Práticas recomendadas de formato de arquivo de ativos {#assets-file-format-best-practices}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager Assets] O suporta muitas bibliotecas de formatos de arquivo proprietárias e de terceiros para atender a diversos requisitos de suporte de arquivos dos usuários. As bibliotecas Adobe compatíveis incluem Adobe Camera Raw, Gibson, Adobe PDF Rasterizer e Adobe InDesign Server. Além disso, [!DNL Assets] O suporta bibliotecas de terceiros, incluindo ImageMagick, TwelveMonkeys e assim por diante.

Para obter os formatos de arquivo suportados, consulte [Formatos compatíveis com os ativos](assets-formats.md).

## Biblioteca da Adobe Camera Raw {#adobe-camera-raw-library}

Para obter o melhor desempenho, o Adobe recomenda o uso da biblioteca Adobe Camera Raw para:

* BRUTO
* DNG

A biblioteca Adobe Camera Raw oferece suporte ao perfil de cores CMYK como entrada. No entanto, ele gera a saída no RGB colorspace e suporta a saída somente no formato JPEG. Ele não retém o espaço de cores do arquivo de origem (por exemplo, CMYK) nas miniaturas.

Para obter mais informações, consulte [Suporte Camera Raw](camera-raw.md) em [!DNL Assets].

## Biblioteca Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obter melhores resultados, o Adobe recomenda usar a biblioteca Adobe PDF Rasterizer para os seguintes arquivos:

* Arquivos PDF pesados e com uso intenso de conteúdo
* Arquivos AI com miniaturas não gerados imediatamente
* Para arquivos AI com cores SPOT (PMS)

As miniaturas e visualizações geradas usando o PDF Rasterizer têm melhor qualidade em comparação à saída raster predefinida. A biblioteca Adobe PDF Rasterizer não oferece suporte a nenhuma conversão de espaço de cores. Independentemente do espaço de cores do arquivo PDF de origem, o Adobe PDF Rasterizer gera apenas saída RGB.

## Servidor Adobe InDesign {#adobe-indesign-cc-server}

O Adobe recomenda usar o servidor Adobe InDesign para extrair representações específicas do Adobe InDesign, como IDML e HTML. Para obter mais informações, consulte [Adição de [!DNL Experience Manager] ativos como referências no Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

A Dynamic Media gera e oferece várias variações de conteúdo rico em tempo real por meio de sua rede global, escalável e otimizada para desempenho. Ele fornece experiências de visualização interativas e simplifica o processo de gerenciamento de campanhas digitais. Para obter detalhes sobre como habilitar o Dynamic Media, consulte [Configuração do Dynamic Media](config-dynamic.md).

Atualmente, o Dynamic Media pode oferecer suporte a vídeos de até 15 GB de conteúdo por arquivo.

## Biblioteca ImageMagick {#imagemagick-library}

O Adobe recomenda usar a biblioteca ImageMagick nos seguintes cenários:

* Para gerar representações em miniatura de arquivos EPS
* Para preservar as informações do perfil da imagem
* Preservação da transparência
* Para processar arquivos PSD e PSB

Para saber como configurar a biblioteca do ImageMagic em [!DNL Experience Manager], consulte [Usando o ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obter o uso ideal, consulte [Práticas recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md).

## Biblioteca de transcodificação de imagem {#image-transcoding-library}

A Biblioteca de transcodificação de imagens do Adobe é uma solução de processamento de imagens que executa funções essenciais de manipulação de imagens, incluindo codificação de imagens, transcodificação, reamostragem, redimensionamento e assim por diante.

A biblioteca de transcodificação de imagens oferece suporte aos seguintes tipos MIME:

* JPG/JPEG
* PNG (8 bits e 16 bits)
* GIF
* BMP
* TIFF/TIFF compactado (exceto os Tiffs de 32 bits e os PTiffs).
* ICO
* ICN

Para obter detalhes, consulte [Biblioteca de transcodificação de imagens](imaging-transcoding-library.md).
