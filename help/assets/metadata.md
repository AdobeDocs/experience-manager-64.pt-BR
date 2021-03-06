---
title: Gerencie metadados de seus ativos digitais em [!DNL Adobe Experience Manager].
description: Saiba mais sobre os tipos de metadados e como [!DNL Adobe Experience Manager Assets] helps manage metadata for assets to allow easier categorization and organization of assets. [!DNL Experience Manager] possibilita organizar e processar ativos automaticamente com base em seus metadados.
contentOwner: AG
feature: Marcação, metadados
role: Architect, Leader
exl-id: 05bbf89a-4cf5-49bb-aea8-a585c641eda2
source-git-commit: fc725206728e238ab9da1fb30cee8fb407257b62
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 0%

---

# Gerenciar metadados dos ativos digitais {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] mantém metadados para cada ativo. Ela facilita a categorização e a organização de ativos e ajuda as pessoas que estão procurando por um ativo específico. Com a capacidade de extrair metadados de arquivos carregados para [!DNL Experience Manager Assets], o gerenciamento de metadados integra-se ao fluxo de trabalho criativo. Com a capacidade de manter e gerenciar metadados com seus ativos, você pode organizar e processar ativos automaticamente com base em seus metadados.

* [Metadados XMP](xmp.md).
* [Como editar ou adicionar metadados](meta-edit.md).
* [Referência de schemas de metadados](meta-ref.md).

## Por que precisamos de metadados {#why-we-need-metadata}

Metadados significa dados sobre dados. Nesse sentido, os dados se referem ao seu ativo digital, digamos uma imagem. Os metadados são essenciais para um gerenciamento eficiente de ativos.

Metadados é a coleção de todos os dados disponíveis para um ativo, mas que não estão necessariamente contidos nessa imagem. Alguns exemplos de metadados são:

* Nome do ativo.
* Hora e data da última modificação.
* Tamanho do ativo como ele foi armazenado no repositório.
* Nome da pasta na qual ele está contido.
* Ativos relacionados ou tags aplicadas.

As informações acima são as propriedades básicas de metadados que [!DNL Experience Manager] pode gerenciar para ativos, o que permite que os usuários vejam todos os ativos. Por exemplo, solicitar ativos pela última data de modificação é útil ao tentar descobrir ativos adicionados recentemente.

Você pode adicionar mais dados de alto nível aos ativos digitais, por exemplo:

* Tipo de ativo (é uma imagem, um vídeo, um clipe de áudio ou um documento?).
* Proprietário do ativo.
* Título do ativo.
* Descrição do ativo.
* Tags atribuídas a um ativo.

Mais metadados ajudam a categorizar ativos e são úteis à medida que a quantidade de informações digitais aumenta. É possível gerenciar algumas centenas de arquivos com base apenas nos nomes de arquivo. No entanto, essa abordagem não é escalável. Fica aquém do aumento do número de pessoas envolvidas e do número de ativos gerenciados.

Com a adição de metadados, o valor de um ativo digital cresce, porque o ativo se torna,

* Mais acessível - os sistemas e usuários podem encontrá-lo facilmente.
* Mais fácil de gerenciar: é possível encontrar ativos com o mesmo conjunto de propriedades mais facilmente e aplicar alterações a eles.
* Concluído - o ativo carrega mais informações e contexto com mais metadados.

Por esses motivos, [!DNL Assets] fornece o meio certo para criar, gerenciar e trocar metadados para seus ativos digitais.

## Tipos de metadados {#types-of-metadata}

Os dois tipos básicos de metadados são metadados técnicos e descritivos.

Os metadados técnicos são úteis para aplicativos de software que lidam com ativos digitais e não devem ser mantidos manualmente. [!DNL Experience Manager Assets] e outros softwares determinam automaticamente os metadados técnicos e podem mudar quando o ativo é modificado. Os metadados técnicos disponíveis de um ativo dependem principalmente do tipo de arquivo do ativo. Alguns exemplos de metadados técnicos são:

* Tamanho de um arquivo.
* Dimension (altura e largura) de uma imagem.
* Taxa de bits de um arquivo de áudio ou vídeo.
* Resolução (nível de detalhes) de uma imagem.

Os metadados descritivos são metadados relacionados ao domínio do aplicativo, por exemplo, o negócio de onde um ativo vem. Metadados descritivos não podem ser determinados automaticamente. Ele é criado manual ou semiautomaticamente. Por exemplo, uma câmera ativada por GPS pode rastrear automaticamente a latitude e a longitude e adicionar geotag à imagem.

O custo de criar manualmente informações de metadados descritivos é alto. Assim, os padrões são estabelecidos para facilitar a troca de metadados entre sistemas e organizações de software. [!DNL Experience Manager Assets] O suporta todas as normas relevantes para a gestão de metadados.

## Padrões de codificação {#encoding-standards}

Há várias maneiras de incorporar metadados em arquivos. Há suporte para uma seleção de padrões de codificação:

* XMP: usado por [!DNL Assets] para armazenar os metadados extraídos no repositório.
* ID3: para arquivos de áudio e vídeo.
* Exif: para arquivos de imagem.
* Outro/Legado: de [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] e assim por diante.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) é um padrão aberto usado pelo  [!DNL Experience Manager Assets] para todo o gerenciamento de metadados. O padrão oferece codificação de metadados universais que podem ser incorporados em todos os formatos de arquivo. O Adobe e outras empresas oferecem suporte XMP padrão, pois fornece um modelo de conteúdo avançado. Os usuários XMP padrão e [!DNL Experience Manager Assets] têm uma plataforma poderosa para desenvolver. Para obter mais informações, consulte [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Os dados armazenados nessas tags ID3 são exibidos quando você reproduz um arquivo de áudio digital em seu computador ou em um player MP3 portátil.

As tags ID3 foram projetadas para o formato de arquivo MP3. Informações adicionais sobre formatos:

* As tags ID3 funcionam em arquivos MP3 e mp3PRO.
* O WAV não tem tags.
* O WMA tem tags proprietárias que não permitem implementação de código aberto.
* O Ogg Vorbis usa Comentários Xiph incorporados no contêiner Ogg.
* O AAC usa um formato de marcação proprietário.

### Exif {#exif}

O formato de arquivo de imagem permutável (Exif) é o formato de metadados mais popular usado em fotografia digital. Ele fornece uma maneira de incorporar um vocabulário fixo de propriedades de metadados em muitos formatos de arquivo, como JPEG, TIFF, RIFF e WAV. O Exif armazena metadados como pares de um nome de metadados e um valor de metadados. Esses pares nome-valor-metadados também são chamados de tags , não devem ser confundidos com a marcação em [!DNL Experience Manager]. Câmeras digitais modernas criam metadados Exif e softwares gráficos modernos suportam isso. O formato Exif é o menor denominador comum para o gerenciamento de metadados, especialmente para imagens.

Uma grande limitação do Exif é que alguns formatos de arquivo de imagem populares, como BMP, GIF ou PNG, não são compatíveis.

Os campos de metadados definidos pela Exif normalmente têm natureza técnica e são de uso limitado para o gerenciamento de metadados descritivos. Por esse motivo, [!DNL Experience Manager Assets] oferece mapeamento de propriedades Exif em [esquemas de metadados comuns](metadata-schemas.md) e em [XMP](xmp-writeback.md).

### Outros metadados {#other-metadata}

Outros metadados que podem ser incorporados de arquivos incluem [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], e assim por diante.

## Esquemas de metadados {#metadata-schemata}

Os esquemas de metadados são conjuntos predefinidos de definições de propriedades de metadados que podem ser usadas em vários aplicativos. As propriedades são sempre associadas a um ativo, o que significa que as propriedades são &quot;sobre&quot; o recurso.

Você também pode criar seus próprios esquemas de metadados se não existir nenhum que atenda às suas necessidades. Não duplique as informações existentes. Em uma organização, separar esquemas facilita o compartilhamento de metadados. [!DNL Experience Manager] O fornece uma lista padrão dos esquemas de metadados mais populares. A lista ajuda você a iniciar rapidamente sua estratégia de metadados e escolher rapidamente as propriedades de metadados necessárias.

Os esquemas de metadados compatíveis estão listados abaixo.

### Metadados padrão {#standard-metadata}

* DC - [!DNL Dublin Core] é um conjunto de metadados importante e amplamente usado.
* DICOM - Digital Imaging and Communications in Medicine (Imagem digital e comunicações em medicina).
* `Iptc4xmpCore` e  `iptc4xmpExt` - O International Press Communications Standard contém muitos metadados específicos de assunto.
* RDF - Estrutura de Descrição do Recurso - para metadados semanticos da Web genéricos.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - Bilhete básico de trabalho.

### Metadados específicos do aplicativo {#application-specific-metadata}

Os metadados específicos do aplicativo incluem metadados técnicos e descritivos. Se você usar esses metadados, outros aplicativos talvez não consigam usá-los. Por exemplo, um aplicativo de renderização de imagem diferente pode não conseguir acessar metadados [!DNL Adobe Photoshop]. Você pode criar uma etapa de fluxo de trabalho que altera uma propriedade específica do aplicativo para uma propriedade padrão.

* ACDSee - Metadados gerenciados pelo programa [!DNL ACDSee]. Consulte [www.acdsee.com/](https://www.acdsee.com/).
* Álbum - [!DNL Adobe Photoshop Album].
* CQ - Usado por [!DNL Experience Manager Assets].
* DAM - Usado por [!DNL Experience Manager Assets].
* DEX - [Optima SC Description Explorer](http://www.optimasc.com/products/dex/index.html) é uma coleção de ferramentas para metadados e gerenciamento de arquivos para sistemas operacionais Windows.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto e MP - Microsoft Photo.
* PDF e PDF/X.
* Photoshop e psAux - [!DNL Adobe Photoshop].

### Metadados de Digital Rights Management {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS - [Sistema Universal de Licenciamento de Imagem](https://www.useplus.com).
* PRISM - [Requisitos de publicação para metadados padrão do setor](https://www.idealliance.org/prism-metadata).
* PRL - Linguagem de direitos PRISM.
* PUR - Direitos de uso do PRISM.
* `xmpPlus` - Integração da PLUS com a XMP.

### Metadados específicos da fotografia {#photography-specific-metadata}

* Exif - Informações técnicas da câmera, incluindo a posição GPS.
* CRS - [!DNL Camera Raw] esquema.
* `iptc4xmpCore` e `iptc4xmpExt`.
* TIFF - metadados de imagem (não apenas para imagens TIFF).

### Metadados específicos para impressão {#print-specific-metadata}

* PDF e PDF/X - Adobe PDF e aplicativos de terceiros.
* PRISM - [Requisitos de publicação para metadados padrão do setor](http://www.prismstandard.org/specifications/).
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - XMP metadados para texto paginado.

### Metadados específicos de multimídia {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - Gerenciamento de mídia.

## Fluxos de trabalho orientados por metadados {#metadata-driven-workflows}

A criação de fluxos de trabalho orientados por metadados ajuda a automatizar alguns processos, o que melhora a eficiência. Em um fluxo de trabalho orientado por metadados, o sistema de gerenciamento de fluxo de trabalho lê o fluxo de trabalho e, como resultado, executa alguma ação predefinida. Por exemplo, algumas das maneiras de usar workflows orientados por metadados:

* O fluxo de trabalho pode verificar se uma imagem tem um título ou não. Caso contrário, o sistema notifica para adicionar um título.
* O workflow pode verificar se um aviso de copyright em um ativo permite distribuição ou não. Assim, o sistema envia o ativo para um servidor ou outro.
* Um workflow pode verificar ativos sem metadados obrigatórios predefinidos ou ativos com metadados *inválidos*.
