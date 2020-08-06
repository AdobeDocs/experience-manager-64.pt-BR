---
title: Serviço de saída
seo-title: Serviço de saída
description: Descreve o Serviço de Saída, que faz parte AEM Serviços de Documento
seo-description: Descreve o Serviço de Saída, que faz parte AEM Serviços de Documento
uuid: acd64bbb-91df-49bc-9216-2e860812bbe9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 8b96ba2d-007e-472a-875f-2caedd35ecf4
translation-type: tm+mt
source-git-commit: de440f57091d814a0a7ff48e9a0383c5415a0a5b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Serviço de saída {#output-service}

## Visão geral {#overview}

O serviço de saída é um serviço OSGi que faz parte AEM Documento Services. O serviço de saída suporta vários formatos de saída e recursos de design de saída do AEM Forms Designer. O serviço de saída pode converter modelos XFA e dados XML para gerar documentos de impressão em vários formatos.

O serviço de saída permite criar aplicativos que permitem:

* Gere documentos de formulário finais preenchendo arquivos de modelo com dados XML.
* Gere formulários de saída em vários formatos, incluindo fluxos de impressão PDF, PostScript, PCL e ZPL não interativos.
* Gere PDFs de impressão a partir de PDFs de formulário XFA.
* Gere documentos PDF, PostScript, PCL e ZPL em massa ao mesclar vários conjuntos de dados com modelos fornecidos.

>[!NOTE]
>
>O serviço de saída é um aplicativo de 32 bits. No Microsoft Windows, um aplicativo de 32 bits pode usar no máximo 2 GB de memória. O limite também se aplica ao serviço de saída.

## Criação de documentos de formulário não interativos {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

Normalmente, você cria modelos usando o AEM Forms Designer. As `generatePDFOutput` e `generatePrintedOutput` as APIs do serviço de Saída permitem converter esses modelos diretamente em vários formatos, incluindo PDF, PostScript, ZPL e PCL.

A `generatePDFOutput` operação gera PDFs, enquanto a `generatePrintedOutput` operação gera formatos PostScript, ZPL e PCL. O primeiro parâmetro de ambas as operações aceita o nome do arquivo de modelo (por exemplo `ExpenseClaim.xdp`) ou um objeto de Documento que contém o modelo. Ao especificar o nome do arquivo de modelo, especifique também a raiz do conteúdo como o caminho para a pasta que contém o modelo. Você pode especificar a raiz do conteúdo usando o parâmetro `PDFOutputOptions` ou o `PrintedOutputOptions` . Consulte Javadoc para obter detalhes sobre outras opções que você pode especificar usando esses parâmetros.

O segundo parâmetro aceita um documento XML que é unido ao modelo ao gerar o documento de saída.

A `generatePDFOutput` operação também pode aceitar um formulário PDF baseado em XFA como entrada e retornar uma versão não interativa do formulário PDF como saída.

## Geração de documentos de formulário não interativos {#generating-non-interactive-form-documents}

Considere um cenário em que você tenha um ou mais modelos e vários registros de dados XML para cada modelo.

Use as operações `generatePDFOutputBatch` e `generatePrintedOutputBatch` do serviço de Saída para gerar um documento de impressão para cada registro.

Você também pode combinar os registros em um único documento. Ambas as operações utilizam quatro parâmetros.

O primeiro parâmetro é um Mapa que contém uma string arbitrária como a chave e o nome do arquivo de modelo como valor.

O segundo parâmetro é um Mapa diferente cujo valor é um objeto de Documento que contém dados XML. A chave é a mesma especificada para o primeiro parâmetro.

O terceiro parâmetro para `generatePDFOutputBatch` ou `generatePrintedOutputBatch` é do tipo `PDFOutputOptions` ou `PrintedOutputOptions` , respectivamente.

Os tipos de parâmetro são os mesmos que os tipos de parâmetros para as operações `generatePDFOutput` e `generatePrintedOutput` e têm o mesmo efeito.

O quarto parâmetro é do tipo `BatchOptions`, que você usa para especificar se um arquivo separado pode ser gerado para cada registro. O valor padrão desse parâmetro é falso.

Tanto `generatePrintedOutputBatch` quanto `generatePDFOutputBatch` retornam um valor do tipo `BatchResult`. O valor contém uma lista de documentos gerados. Ele também contém um documento de metadados no formato XML que contém informações relacionadas a cada documento gerado.
