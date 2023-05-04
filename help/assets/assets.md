---
title: Introdução ao  [!DNL Adobe Experience Manager Assets]
description: Saiba o que é gerenciamento de ativos digitais, seus casos de uso e [!DNL Adobe Experience Manager Asset] oferta.
contentOwner: AG
feature: Asset Management
role: Leader,Architect,User
exl-id: 9292871d-3b10-49f8-ac1a-4770b4e44048
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 1%

---

# Sobre [!DNL Adobe Experience Manager Assets] como uma solução DAM {#about-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Assets] O é uma ferramenta de Gerenciamento de ativos digitais (DAM) que faz parte integrante do [!DNL Experience Manager] e permite que sua empresa gerencie e distribua ativos digitais. Os usuários em uma organização podem gerenciar, armazenar e acessar muitos tipos de ativos digitais, como imagens, vídeos, documentos, clipes de áudio, arquivos 3D e mídia avançada para uso na Web, em impressão e para distribuição digital.

## O que é o Gerenciamento de ativos digitais? {#what-is-digital-asset-management}

[!DNL Assets] O oferece compartilhamento e distribuição dos principais ativos digitais de uma organização em toda a empresa. Os usuários em uma organização podem armazenar, gerenciar e acessar ativos digitais como imagens, gráficos, áudio, vídeo e documentos por meio de uma interface da Web (ou uma pasta CIFS ou WebDAV).

[!DNL Assets] capacidade de [!DNL Experience Manager] permite fazer o seguinte:

* Adicione e compartilhe imagens, documentos, arquivos de áudio e vídeo em vários formatos de arquivo.
* Gerencie ativos agrupando-os por tags, lightbox ou estrelas (seus favoritos). Adicionar anotações a ativos.
* Encontre ativos pesquisando nomes de arquivos, o texto completo de documentos e pesquisando datas, tipo de documento e tags.
* Adicionar ou editar informações de metadados para ativos. Os metadados são automaticamente versionados juntamente com o ativo correspondente. Você pode importar ou exportar metadados de ativos.
* Execute funções de edição de imagens, como dimensionamento e adição de filtros de imagem. Importe e exporte vários ativos digitais simultaneamente usando uma pasta WebDAV ou CIFS.
* Use fluxos de trabalho e notificações para permitir o processamento conjunto e o download de qualquer conjunto de ativos e gerenciar direitos de acesso a ativos.

### [!DNL Experience Manager Assets] é integrado ao [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] integra-se totalmente com [!DNL Sites] e funciona perfeitamente em todos os casos de uso. Por exemplo, ao criar páginas da Web, a variável [!DNL Sites] os autores podem encontrar e usar os ativos digitais no Localizador de conteúdo. A interface do usuário de [!DNL Assets] é igual à [!DNL Sites]. Consulte [visão geral dos sites](/help/sites-authoring/qg-page-authoring.md) para obter detalhes completos.

<!-- TBD: Update image for branding 

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

Assets managed within [!DNL Experience Manager] DAM can then be accessed via the content finder of WCM:

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png) -->

### Gerenciamento de ativos digitais versus o componente de imagem {#digital-asset-management-versus-image-component}

Ao determinar se uma imagem deve ser colocada no repositório DAM ou usar um componente de imagem, considere o ciclo de vida da imagem:

* Se a imagem tiver o mesmo ciclo de vida que a página, use o componente Imagem .
* Se a imagem tiver um ciclo de vida separado, por exemplo, se você usar a imagem duas vezes ou fora do WCM, use [!DNL Assets].

## O que são ativos digitais? {#what-are-digital-assets}

Um ativo é um documento digital, imagem, vídeo ou áudio (ou parte dele) que pode ter várias representações e subativos (por exemplo, camadas em um arquivo do Photoshop, slides em um arquivo do PowerPoint, páginas em um pdf, arquivos em um ZIP).

Um ativo é essencialmente um binário com metadados, além de representações e subativos. Consulte a [Guia de desempenho do DAM](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html) para obter informações detalhadas.

>[!CAUTION]
>
>Fazer upload e/ou editar um grande volume de ativos (especialmente imagens) pode afetar o desempenho de seus [!DNL Experience Manager] implantação.

### [!DNL Experience Manager Assets] terminologia {#aem-assets-terminology}

Ao trabalhar com ativos digitais no [!DNL Experience Manager], é necessário entender a seguinte terminologia:

* **Coleção**: Uma coleção de ativos, com base na localização física (pasta), nas propriedades comuns (pasta de pesquisa salva) ou na seleção de usuários (pastas lightbox).

* **Metadados** [!DNL Assets] Ter metadados; por exemplo, autor, data de expiração, informações de DRM (Digital Rights Management) e assim por diante. Os metadados estão sob controle de acesso. [!DNL Assets] O suporta os seguintes esquemas comuns de metadados prontos para uso:

   * Dublin Core: incluindo autor, descrição, data, assunto e assim por diante.
   * IPTC: incluindo evento, modelo, local e assim por diante.
   * WCM: incluindo propriedades de página, [!UICONTROL Hora de ligar] e [!UICONTROL Hora de desligar]e assim por diante.

* **Marcação**: [!DNL Assets] pode ser marcada e classificada. Consulte [organizar ativos](/help/assets/organize-assets.md).

* **Representações**: Uma representação é a representação binária de um ativo. [!DNL Assets] sempre tenha uma representação primária - a do arquivo carregado. Eles podem ter qualquer número de representações adicionais que são criadas, por exemplo, por etapas de fluxo de trabalho personalizadas ou quando um ativo é carregado. As representações podem ter um tamanho diferente, com uma resolução diferente, com uma marca d&#39;água adicionada ou alguma outra característica alterada.

* **Versões**: O controle de versão cria um instantâneo de ativos digitais em um ponto específico do tempo. Você pode restaurar ativos para versões anteriores. Consulte [versão em [!DNL Assets]](managing-assets-touch-ui.md#asset-versioning).

* **Subativos**: Subativos são ativos que compõem um ativo, por exemplo, camadas em uma [!DNL Adobe Photoshop] arquivo ou páginas em um arquivo PDF. Em [!DNL Assets], você pode gerenciar subativos como faria com os ativos.

### Como trabalhar com ativos digitais {#how-to-work-with-assets}

Você executa uma ação em um ativo ou coleção. As ações podem criar ou modificar ativos, coleções e representações. Muitas das ações básicas executadas em ativos - carregar, excluir, atualizar, salvar sub-ativos - acionam fluxos de trabalho pré-configurados. Eles são ativados automaticamente em [!DNL Assets] e são descritas em pormenor em [!DNL Assets] manipuladores de mídia.

As tarefas que você pode executar com esses workflows pré-configurados:

* Salve o ativo no repositório ou exclua o ativo dele.
* Extrair e salvar metadados para o ativo; os itens de metadados individuais são salvos como XMP.
* Gerar representações e miniaturas para o ativo; incluindo redimensionamento automático e recorte, quando necessário.
* Transcodifique o ativo, quando necessário. Por exemplo, o vídeo para uso em dispositivos móveis e na Web é transcodificado com 24 quadros por segundo, e o vídeo para download com 30 quadros por segundo. O áudio para uso na Web e em dispositivos móveis é transcodificado com 128 Kbps, o áudio para download com 192 Kbps.

É claro que também é possível aplicar fluxos de trabalho manualmente. Consulte [Manipuladores de mídia de ativos](media-handlers.md)para obter uma lista de workflows padrão.

## [!DNL Experience Manager Assets] e [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Consulte [Ativos e Media Library](medialibrary.md) para obter informações sobre as diferenças.

>[!MORELIKETHIS]
>
>* [Introdução ao vídeo - Experience Manager Assets as a moderno DAM](https://www.youtube.com/watch?v=PBwQqZgC-yo)

