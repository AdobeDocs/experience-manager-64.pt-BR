---
title: Práticas recomendadas de formato de arquivo de ativos
description: Práticas recomendadas para suporte a arquivos nos ativos AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Assets file format best practices {#assets-file-format-best-practices}

O AEM Assets oferece suporte a várias bibliotecas proprietárias e de arquivos de terceiros para atender aos diversos requisitos de suporte de arquivos dos usuários. As bibliotecas da Adobe suportadas incluem Adobe Camera Raw, Gibson, Adobe PDF Rasterizer e Adobe InDesign Server. Além disso, os ativos AEM oferecem suporte a bibliotecas de terceiros, incluindo ImageMagick, 12Monkeys e assim por diante.

For the supported file formats, see [Assets supported formats](assets-formats.md).

## Biblioteca do Adobe Camera Raw {#adobe-camera-raw-library}

Para obter o melhor desempenho, a Adobe recomenda usar a biblioteca do Adobe Camera Raw para:

* RAW
* DNG

A biblioteca do Adobe Camera Raw oferece suporte ao perfil de cores CMYK como entrada. No entanto, ele gera a saída no espaço de cores RGB e suporta a saída somente no formato JPEG. Ele não retém o espaço de cores do arquivo de origem (por exemplo, CMYK) nas miniaturas.

Para obter mais informações, consulte Suporte ao [Camera Raw](camera-raw.md) nos ativos AEM.

## Biblioteca do Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Para obter melhores resultados, a Adobe recomenda usar a biblioteca do Adobe PDF Rasterizer para os seguintes arquivos:

* Arquivos PDF pesados e com conteúdo intenso
* Arquivos AI com miniaturas não gerados na caixa
* Para arquivos AI com cores SPOT (PMS)

As miniaturas e visualizações geradas usando o PDF Rasterizer têm melhor qualidade em comparação à saída rasterizada predefinida. A biblioteca do Adobe PDF Rasterizer não suporta nenhuma conversão de espaço de cor. Independentemente do espaço de cor do arquivo PDF de origem, o Adobe PDF Rasterizer gera apenas saída RGB.

## Adobe InDesign Server {#adobe-indesign-cc-server}

A Adobe recomenda usar o servidor do Adobe InDesign para extrair execuções específicas do Adobe InDesign, como IDML e HTML. Para obter mais informações, consulte [Adicionar ativos AEM como referências no Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

O Dynamic Media gera e oferece várias variações de conteúdo rico em tempo real por meio de sua rede global, escalável e otimizada para desempenho. Ele proporciona experiências de visualização interativas e simplifica o processo de gerenciamento de campanha digital. Para obter detalhes sobre como ativar o Dynamic Media, consulte [Configuração do Dynamic Media](config-dynamic.md).

Atualmente, o Dynamic Media pode oferecer suporte a vídeos com até 20 GB de conteúdo por arquivo.

## Biblioteca ImageMagick {#imagemagick-library}

A Adobe recomenda usar a biblioteca ImageMagick nos seguintes cenários:

* Para gerar execuções de miniatura para arquivos EPS
* Para preservar as informações do perfil da imagem
* Para preservar a transparência
* Para processar arquivos PSD e PSB

Para saber como configurar a biblioteca ImageMagic no AEM, consulte [Uso do ImageMagick](media-handlers.md#an-example-using-imagemagick). Para obter o uso ideal, consulte Práticas [recomendadas para configurar o ImageMagick](best-practices-for-imagemagick.md).

## Biblioteca de transcodificação de imagens {#image-transcoding-library}

A Biblioteca de transcodificação de imagens da Adobe é uma solução de processamento de imagens que executa funções essenciais de manipulação de imagens, incluindo codificação de imagens, transcodificação, redefinição de resolução, redimensionamento e assim por diante.

A biblioteca de transcodificação de imagens suporta os seguintes tipos MIME:

* JPG/JPEG
* PNG (8 bits e 16 bits)
* GIF
* BMP
* TIFF/TIFF compactado (exceto Tiffs de 32 bits e PTiffs).
* ICO
* ICN

Para obter detalhes, consulte Biblioteca [de transcodificação de](imaging-transcoding-library.md)imagens.
