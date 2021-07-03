---
title: Metadados de XMP
description: Saiba mais sobre o padrão de metadados de XMP (Plataforma de metadados extensível) usado pelo AEM Assets para gerenciamento de metadados. O XMP fornece um formato padrão para a criação, o processamento e o intercâmbio de metadados para uma grande variedade de aplicativos.
contentOwner: AG
feature: Metadados
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 19%

---

# Metadados XMP {#xmp-metadata}

XMP (Plataforma de metadados extensível) é o padrão de metadados usado pelo AEM Assets para todo o gerenciamento de metadados. O XMP fornece um formato padrão para a criação, o processamento e o intercâmbio de metadados para uma grande variedade de aplicativos.

Além de oferecer a codificação de metadados universais que pode ser incorporada a todos os formatos de arquivo, o XMP fornece um [modelo de conteúdo avançado](xmp.md#xmp-core-concepts) e é [suportado pelo Adobe](xmp.md#advantages-of-xmp) e por outras empresas, para que os usuários de XMP em combinação com o AEM Assets tenham uma plataforma poderosa para desenvolver.

A [XMP especificação](https://www.adobe.com/devnet/xmp.html) está disponível no Adobe.

## O que é XMP? {#what-is-xmp}

A AEM Assets oferece suporte nativo ao XMP - a Plataforma de metadados extensível liderada pelo Adobe. XMP é um padrão para processar e armazenar metadados padronizados e proprietários em ativos digitais. O XMP foi projetado para ser o padrão comum que permite que vários aplicativos funcionem com metadados de maneira eficaz.

Os profissionais de produção, por exemplo, usam o suporte XMP integrado nos aplicativos Adobe para transmitir informações em vários formatos de arquivo. O repositório AEM Assets extrai os metadados XMP e os usa para gerenciar o ciclo de vida do conteúdo e oferece a capacidade de criar fluxos de trabalho de automação.

XMP padroniza como os metadados são definidos, criados e processados fornecendo um modelo de dados, um modelo de armazenamento e esquemas. Todos esses conceitos são abordados nesta seção.

Todos os metadados herdados de EXIF, ID3 ou Microsoft Office são traduzidos automaticamente para XMP, o que pode ser estendido para oferecer suporte ao esquema de metadados específico do cliente, como catálogos de produtos.

Os metadados no XMP consistem em um conjunto de propriedades. Essas propriedades são sempre associadas a um\
entidade específica designada por recurso; ou seja, as propriedades são &quot;sobre&quot; o recurso. No caso de XMP, o recurso é sempre o ativo.

### Adobe {#adobe}

O Adobe introduziu o padrão de XMP como parte do produto de software Adobe Acrobat. Desde então, a norma XMP foi amplamente adotada.

### XMP ecossistema {#xmp-ecosystem}

O XMP define um modelo de [metadados](https://pt.wikipedia.org/wiki/Metadados) que pode ser usado com qualquer conjunto definido de itens de metadados. O XMP também define [esquemas](https://en.wikipedia.org/wiki/XML_schema) específicos de propriedades básicas úteis para gravar o histórico de um recurso à medida que ele passa por várias etapas de processamento, de ser fotografado, [digitalizado](https://pt.wikipedia.org/wiki/Digitalizador) ou criado como texto, até etapas de edição de fotos (como [recorte](https://en.wikipedia.org/wiki/Cropping_%28image%29) ou ajuste de cor), para montagem em uma imagem final. O XMP permite que cada programa de software ou dispositivo ao longo do caminho adicione suas próprias informações a um recurso digital, que pode ser retido no arquivo digital final.

O XMP geralmente é serializado e armazenado usando um subconjunto do [W3C](https://pt.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://pt.wikipedia.org/wiki/Resource_Description_Framework) (RDF), que por sua vez é expresso em [XML](https://pt.wikipedia.org/wiki/XML).

## Vantagens do XMP {#advantages-of-xmp}

XMP tem as seguintes vantagens em relação a outros padrões e esquemas de codificação:

* Metadados baseados em XMP são muito avançados e otimizados.
* XMP permite ter vários valores para uma propriedade.
* XMP tem codificação padronizada, que permite a troca fácil de metadados.
* XMP é extensível. É possível adicionar mais informações aos ativos.

### Extensíveis {#extensible}

O padrão de XMP foi projetado para ser extensível, permitindo adicionar tipos personalizados de metadados aos dados de XMP. Por outro lado, EXIF não - tem uma lista fixa de propriedades que não pode ser estendida.

>[!NOTE]
>
>XMP geralmente não permite que tipos de dados binários sejam incorporados. Para carregar dados binários no XMP, por exemplo, imagens em miniatura, eles devem ser codificados em um formato compatível com XML, como Base64.

## XMP Conceitos principais {#xmp-core-concepts}

As seções a seguir descrevem os conceitos principais de XMP, incluindo namespaces e schemas, propriedades e valores e alternativas de idioma.

### Namespaces e Schemata {#namespaces-and-schemata}

Um esquema XMP é um conjunto de nomes de propriedade em um namespace XML comum que inclui\
Tipo de dados e informações descritivas. Um esquema de XMP é identificado por seu URI de namespace XML. O uso de namespaces impede conflitos entre propriedades em esquemas diferentes que tenham o mesmo nome, mas um significado diferente.

Por exemplo, a propriedade **Creator** em dois esquemas projetados independentemente pode significar a pessoa que criou o ativo ou pode significar o aplicativo que criou o ativo (por exemplo, Adobe Photoshop).

### Propriedades e valores {#properties-and-values}

XMP pode incluir propriedades de um ou mais schemas.

Por exemplo, um subconjunto típico usado por muitos aplicativos Adobe pode incluir o seguinte:

* Esquema principal de Dublin: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP esquema básico: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP schema de gerenciamento de direitos: xmpRights:WebStatement, xmpRights:Marked
* XMP schema de gerenciamento de mídia: xmpMM:DocumentID

### Alternativas de idioma {#language-alternatives}

XMP oferece a capacidade de adicionar uma propriedade **xml:lang** às propriedades do texto para especificar o idioma do texto.
