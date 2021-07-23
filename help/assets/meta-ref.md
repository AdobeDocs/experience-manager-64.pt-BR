---
title: Referência de esquemas de metadados
description: 'Saiba mais sobre as convenções padrão para descrever metadados de ativos, incluindo Dublin Core, IPTC e outros esquemas de metadados. '
contentOwner: AG
feature: Metadados
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: fc725206728e238ab9da1fb30cee8fb407257b62
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# Referência de esquemas de metadados {#metadata-schemata-reference}

A referência a seguir inclui informações sobre um esquema de metadados específico (em ordem alfabética), bem como uma lista de propriedades e suas definições.

## Dublin Core {#dublin-core}

Os metadados Dublin Core fornecem um conjunto padronizado de convenções para descrever ativos para facilitar a localização. No AEM Assets, o Dublin Core descreve ativos digitais, incluindo vídeo, som, imagens e documentos.

O Conjunto de elementos de metadados principal simples de Dublin (DCMES) contém 15 elementos de metadados, conforme listados na tabela a seguir. Cada elemento Dublin Core é opcional e pode ser repetido. Você pode adicionar ou excluir informações de metadados Dublin Core da mesma maneira que faria para metadados específicos de tipo de mídia.

Além do DCMES, existem outros elementos de metadados criados pela iniciativa Dublin Core. Consulte a [Iniciativa de Dublin Core](https://dublincore.org/) para obter mais informações.

| Propriedade | Descrição |
|---|---|
| colaborador | A pessoa ou empresa responsável pela contribuição para o conteúdo. |
| cobertura | A localização geográfica ou período que o ativo cobre. |
| criador | A pessoa ou empresa responsável pela criação do conteúdo. |
| date | Data ou período associado ao ativo. |
| descrição | Mais informações sobre o ativo. |
| format | O formato de arquivo, a mídia física ou as dimensões do ativo. AEM usa dc:format para indicar o tipo MIME do ativo. |
| identifier | Uma referência exclusiva ao ativo. |
| language | O idioma do ativo (por exemplo, en para inglês). |
| editor | A pessoa ou empresa responsável pela disponibilização do ativo. |
| relation | Um ativo relacionado. |
| direitos | Informações sobre quem tem os direitos a esse ativo. |
| source | Um ativo relacionado do qual o ativo é derivado. |
| assunto | O tópico do ativo. |
| título | Um nome para o ativo. |
| tipo | A natureza ou o gênero do ativo. |

## IPTC {#iptc}

O International Press Telecommunications Council (IPTC) é um consórcio de agências de notícias em todo o mundo - um de seus objetivos é desenvolver e manter padrões técnicos. O IPTC definiu um conjunto de padrões de metadados de fotos para imagens que são aceitas quase universalmente entre fotógrafos. Esses padrões de metadados faziam parte do padrão mais amplo conhecido como IPTC Information Interchange Model (IIM), criado nos anos 90.

Embora as informações do cabeçalho IPTC tenham sido substituídas principalmente por XMP, um esquema principal IPTC e um esquema de extensão estão disponíveis para XMP. Em programas de imagem, as propriedades XMP e IPTC são sincronizadas.
