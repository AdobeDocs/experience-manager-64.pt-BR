---
title: Práticas recomendadas de formato de arquivo de ativos
description: Práticas recomendadas para o suporte a arquivos no AEM Assets.
contentOwner: AG
feature: Asset Management,Developer Tools
role: Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Práticas recomendadas de formato de arquivo de ativos {#assets-file-format-best-practices}

A AEM Assets oferece suporte a várias bibliotecas de formatos de arquivo proprietárias e de terceiros para atender a diversos requisitos de suporte de arquivos dos usuários. As bibliotecas Adobe compatíveis incluem Adobe Camera Raw, Gibson, Adobe PDF Rasterizer e Adobe InDesign Server. Além disso, o AEM Assets oferece suporte a bibliotecas de terceiros, incluindo o ImageMagick, o TDozeMonkeys e assim por diante.

Para os formatos de arquivo compatíveis, consulte [Formatos compatíveis com ativos](assets-formats.md).

## Biblioteca da Adobe Camera Raw {#adobe-camera-raw-library}

Para obter o melhor desempenho, o Adobe recomenda o uso da biblioteca Adobe Camera Raw para:

* BRUTO
* DNG

A biblioteca Adobe Camera Raw oferece suporte ao perfil de cores CMYK como entrada. No entanto, ele gera a saída no espaço de cores RGB e suporta a saída somente no formato JPEG. Ele não retém o espaço de cores do arquivo de origem (por exemplo, CMYK) nas miniaturas.

Para obter mais informações, consulte [Suporte Camera Raw](camera-raw.md) no AEM Assets.

## Biblioteca do Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obter melhores resultados, o Adobe recomenda usar a biblioteca Adobe PDF Rasterizer para os seguintes arquivos:

* Arquivos PDF pesados e com uso intenso de conteúdo
* Arquivos AI com miniaturas não gerados imediatamente
* Para arquivos AI com cores SPOT (PMS)

Miniaturas e visualizações geradas usando o PDF Rasterizer têm melhor qualidade em comparação à saída rasterizada predefinida. A biblioteca Adobe PDF Rasterizer não oferece suporte a nenhuma conversão de espaço de cores. Independentemente do espaço de cores do arquivo PDF de origem, o Adobe PDF Rasterizer gera apenas saída RGB.

## Servidor Adobe InDesign {#adobe-indesign-cc-server}

O Adobe recomenda usar o servidor Adobe InDesign para extrair representações específicas do Adobe InDesign, como IDML e HTML. Para obter mais informações, consulte [Adicionar ativos AEM como referências no Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

A Dynamic Media gera e oferece várias variações de conteúdo rico em tempo real por meio de sua rede global, escalável e otimizada para desempenho. Ele fornece experiências de visualização interativas e simplifica o processo de gerenciamento de campanhas digitais. Para obter detalhes sobre como habilitar o Dynamic Media, consulte [Configuração do Dynamic Media](config-dynamic.md).

Atualmente, o Dynamic Media pode oferecer suporte a vídeos de até 15 GB de conteúdo por arquivo.

## Biblioteca ImageMagick {#imagemagick-library}

O Adobe recomenda usar a biblioteca ImageMagick nos seguintes cenários:

* Para gerar representações em miniatura de arquivos EPS
* Para preservar as informações do perfil da imagem
* Preservação da transparência
* Para processar arquivos PSD e PSB

Para saber como configurar a biblioteca ImageMagic no AEM, consulte [Usando o ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obter um uso ideal, consulte [Práticas recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md).

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

Para obter detalhes, consulte [Biblioteca de transcodificação de imagem](imaging-transcoding-library.md).
