---
title: Seletor de ativos
description: Saiba como usar o seletor de ativos para pesquisar, filtrar, navegar e buscar metadados para ativos nos ativos Adobe Experience Manager (AEM). Saiba também como personalizar a interface do seletor de ativos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1de8efce9cd5cf47163cba8f0c962a9e2fc5116c
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 1%

---


# Asset selector {#asset-selector}

>[!NOTE]
>
>O seletor de ativos era chamado de Seletor [de](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) ativos em versões anteriores do AEM.

O seletor de ativos permite que você navegue, pesquise e filtre ativos em [!DNL Adobe Experience Manager] Ativos. Você também pode buscar os metadados dos ativos selecionados usando o seletor de ativos. Para personalizar a interface do seletor de ativos, você pode iniciá-la com parâmetros de solicitação suportados. Esses parâmetros definem o contexto do seletor de ativos para um cenário específico.

Atualmente, você pode passar os parâmetros de solicitação `assettype` (*Imagem/Vídeo/Texto*) e a seleção `mode` (*Único/Múltiplo*) como informações contextuais para o seletor de ativos, que permanece intacto durante toda a seleção.

O seletor de ativos usa a mensagem HTML5 **Window.postMessage** para enviar dados do ativo selecionado para o recipient.

O seletor de ativos é baseado no vocabulário do seletor de fundações de Granite. Por padrão, o seletor de ativos opera no modo de navegação. No entanto, você pode aplicar filtros usando a experiência do Omnisearch para refinar sua pesquisa por ativos específicos.

É possível integrar qualquer página da Web (independentemente de fazer parte do container do CQ) ao seletor de ativos (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Parâmetros contextuais {#contextual-parameters}

Você pode passar os seguintes parâmetros de solicitação em um URL para iniciar o seletor de ativos em um contexto específico:

| Nome | Valores | Exemplo | Propósito |
|---|---|---|---|
| sufixo do recurso (B) | Caminho da pasta como o sufixo do recurso no URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Para iniciar o seletor de ativos com uma pasta específica selecionada, por exemplo, com a pasta `/content/dam/we-retail/en/activities` selecionada, o URL deve ser do formato: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Se você precisar que uma pasta específica seja selecionada quando o seletor de ativos for iniciado, passe-o como um sufixo de recurso. |
| modo | único, múltiplo | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | No modo múltiplo, você pode selecionar vários ativos simultaneamente usando o seletor de ativos. |
| caixa de diálogo | verdadeiro, falso | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Use esses parâmetros para abrir o seletor de ativos como Caixa de diálogo Granite. Essa opção só é aplicável quando você inicia o seletor de ativos por meio do campo Caminho de Granite e o configura como URL pickerSrc. |
| root | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Use essa opção para especificar a pasta raiz do seletor de ativos. Nesse caso, o seletor de ativos permite que você selecione apenas ativos secundários (diretos/indiretos) na pasta raiz. |
| modo de exibição | pesquisa |  | Para iniciar o seletor de ativos no modo de pesquisa, com parâmetros tipo de ativo e tipo de métrica. |
| tipo de ativo (S) | imagens, documentos, multimídia, arquivos | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Use essa opção para filtrar os tipos de ativos com base no valor passado. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) de um ativo (curinga também compatível) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Use-o para filtrar ativos com base em tipos MIME |

## Usar o seletor de ativos {#using-the-asset-selector}

1. Para acessar a interface do seletor de ativos, acesse `https://[AEM_server]:[port]/aem/assetpicker`.
1. Navegue até a pasta desejada e selecione um ou mais ativos.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   Como alternativa, você pode pesquisar pelo ativo desejado na caixa OmniSearch e, em seguida, selecioná-lo.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Se você pesquisar ativos usando a caixa OmniSearch, poderá selecionar vários filtros no painel **[!UICONTROL Filtros]** para refinar sua pesquisa.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Toque/clique em **[!UICONTROL Selecionar]** na barra de ferramentas.
