---
title: Conjuntos de rotação
seo-title: Conjuntos de rotação
description: Saiba como trabalhar com conjuntos de rotação em mídia dinâmica
seo-description: Saiba como trabalhar com conjuntos de rotação em mídia dinâmica
uuid: a80a0491-6500-463a-83c4-ff4b90a88182
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: afacb3ad-e4ad-4d06-a898-f3f2da8bbb64
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1839'
ht-degree: 6%

---


# Conjuntos de rotação {#spin-sets}

Um Conjunto de rotação simula o ato real de girar um objeto para examiná-lo. Os Conjuntos de rotação possibilitam a visualização de itens de qualquer ângulo, obtendo os detalhes visuais principais de qualquer ângulo.

Um conjunto de rotação simula uma experiência de visualização de 360 graus. O Dynamic Media oferta Conjuntos de rotação de eixo único nos quais os visualizadores podem girar um item. Além disso, os usuários podem aplicar zoom e deslocar qualquer uma das visualizações com apenas alguns cliques do mouse. Dessa forma, os usuários podem examinar um item mais detalhadamente de um ponto de vista específico.

Spin Sets are designated by a banner with the word **[!UICONTROL SPINSET]**. In addition, if the Spin Set is published, then the publish date, indicated by the **[!UICONTROL World]** icon is on the banner along with the last modification date, indicated by the **[!UICONTROL Pencil]** icon displays.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Para obter informações sobre a interface do usuário Ativos, consulte [Gerenciamento de ativos com a interface do usuário](managing-assets-touch-ui.md)de toque.

## Start rápido: Conjuntos de rotação {#quick-start-spin-sets}

Para colocar você em funcionamento rapidamente com Conjuntos de rotação, siga este fluxo de trabalho:

1. [Carregue suas imagens para várias visualizações.](#uploading-assets-for-spin-sets)

   No mínimo, você precisa de 8 a 12 fotos de um item para um Conjunto de rotação unidimensional e 16 a 24 para um Conjunto de rotação bidimensional. As fotos devem ser tiradas a intervalos regulares para dar a impressão de que o item está girando e sendo virado. Por exemplo, se um Conjunto de rotação unidimensional incluir 12 fotos, gire o item 30 graus (360/12) para cada tomada.

1. [Criar Conjuntos de rotação.](#creating-spin-sets)

   Para criar um Conjunto de rotação, selecione **[!UICONTROL Criar > Conjunto]** de rotação e nomeie o conjunto, escolha os ativos e classifique as imagens na ordem em que serão exibidas.

   See [Working with Selectors](working-with-selectors.md).

   >[!NOTE]
   >
   >You can also create Spin Sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   *Os conjuntos de lotes são criados pelo IPS (Image Production System) como parte da ingestão de ativos e estão disponíveis somente no modo* Dynamic Media - Scene7.

1. Configure as predefinições [do visualizador do](managing-viewer-presets.md)Spin Set, conforme necessário.

   Os administradores podem criar ou modificar as predefinições do visualizador do Spin Set. To see your Spin Set with a Viewer preset, select the Spin Set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   Consulte **[!UICONTROL Ferramentas > Ativos > Predefinições]** do visualizador para criar ou editar predefinições do visualizador.

   Consulte [Adicionar e editar predefinições do visualizador.](managing-viewer-presets.md)

1. [Exibindo Conjuntos](#viewing-spin-sets)de rotação.

   Você pode visualização e acessar conjuntos criados por meio de predefinições de conjuntos de lotes de três maneiras diferentes. (Os conjuntos criados usando predefinições de conjuntos de lotes *não* aparecem na interface do usuário.)

1. [Conjuntos de rotação de Pré-visualização.](previewing-assets.md)

   Selecione o Conjunto de rotação e você pode pré-visualização-lo. Gire o conjunto de rotação. Você pode escolher visualizadores diferentes no menu **[!UICONTROL Visualizadores]** , disponível no menu suspenso do painel esquerdo.

1. [Publicar Conjuntos de rotação.](publishing-dynamicmedia-assets.md)

   A publicação de um conjunto de rotação ativa a ordem na qual as imagens aparecem em um conjunto de rotação. Certifique-se de ordená-los de modo que a rotação seja uma visualização suave de 360 graus.**[!UICONTROL URL]** e string **[!UICONTROL Incorporada]** . Além disso, você deve [publicar a predefinição](managing-viewer-presets.md)do visualizador.

1. [Vincule URLs à sua Aplicação web](linking-urls-to-yourwebapplication.md) ou [Incorpore o visualizador](embed-code.md)de vídeo ou imagem.

   A AEM Assets cria chamadas de URL para Conjuntos de rotação e as ativa após a publicação dos Conjuntos de rotação. Você pode copiar esses URLs ao pré-visualização de ativos. Como alternativa, você pode incorporá-los ao seu site.

   Selecione o Conjunto de rotação e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte [Vincular um conjunto de rotação a uma página da Web](linking-urls-to-yourwebapplication.md) e [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

Se necessário, é possível [editar Conjuntos](#editing-spin-sets)de rotação. Além disso, você pode visualização e editar as propriedades [do Conjunto de](managing-assets-touch-ui.md#editing-properties)rotação.

## Fazer upload de ativos para conjuntos de rotação {#uploading-assets-for-spin-sets}

No mínimo, você precisa de 8 a 12 fotos de um item para um Conjunto de rotação unidimensional e 16 a 24 para um Conjunto de rotação bidimensional. As fotos devem ser tiradas a intervalos regulares para dar a impressão de que o item está girando e sendo virado. Por exemplo, se um Conjunto de rotação unidimensional incluir 12 fotos, gire o item 30 graus (360/12) para cada tomada.

Você pode carregar imagens para os Conjuntos de rotação da mesma forma que faria [upload de qualquer outro ativo no AEM Assets](managing-assets-touch-ui.md).

### Diretrizes para fotografar imagens do Spin Set {#guidelines-for-shooting-spin-set-images}

Veja a seguir algumas práticas recomendadas para imagens de conjunto de rotação. Em geral, quanto mais imagens você tiver em um Conjunto de rotação, melhor será o efeito de rotação da imagem. No entanto, a inclusão de muitas imagens no conjunto também aumenta a quantidade de tempo necessário para carregar as imagens. AEM recomenda estas diretrizes para fotografar imagens para uso em Conjuntos de rotação:

* No mínimo, use 8 a 12 imagens em um conjunto de rotação unidimensional e 16 a 24 imagens em um conjunto de rotação bidimensional. É necessário um mínimo de 8 imagens para rodar 360 graus. Conjuntos de rotação unidimensionais são mais comuns, pois a criação de Conjuntos de rotação bidimensionais exige muita mão de obra.
* Usar um formato sem perdas; TIFF e PNG são recomendados.
* Mascarar todas as imagens para que o item apareça em um fundo branco puro ou em outro plano de alto contraste. Como opção, adicione sombras.
* Verifique se os detalhes do produto estão bem iluminados e em foco.
* Leve imagens de rotação para roupas de moda com um manequim ou modelo. Muitas vezes o manequim é completamente mascarado (utilizando um manequim de vidro) ou na imagem é apresentado um manequim/forma estilizada. É possível criar um conjunto de rotação no modelo definindo o número de ângulos. Marque cada ângulo com uma fita no chão para guiar o modelo a pisar e olhe na direção de cada tomada.

## Criação de Conjuntos de rotação {#creating-spin-sets}

A ordem em que as imagens aparecem em um conjunto de rotação é importante. Certifique-se de ordená-los de modo que a rotação seja uma visualização suave de 360 graus.

>[!NOTE]
>
>Também é possível criar conjuntos de rotação automaticamente por meio de [predefinições de conjuntos em lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
Os conjuntos de lotes são criados pelo IPS (Image Production System) como parte da ingestão de ativos e estão disponíveis somente no modo Dynamic Media - Scene7.
>
>Consulte &quot;Criação de predefinições de conjuntos de lotes para gerar automaticamente Conjuntos de imagens e Conjuntos de rotação&quot; em [Configuração de Mídia dinâmica - modo](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)Scene7.

**Para criar Conjuntos de rotação:**

1. In Assets, navigate to where you want to create a spin set, tap **[!UICONTROL Create]**, and select **[!UICONTROL Spin Set**. Além disso, crie o conjunto de dentro de uma pasta que contenha seus ativos.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. Na página Editor **[!UICONTROL do conjunto de]** rotação, no campo **[!UICONTROL Título]** , digite um nome para o conjunto de rotação. O nome aparece no banner no Conjunto de rotação. Opcionalmente, informe uma descrição.

   ![chlimage_1-302](assets/chlimage_1-382.png)

   Ao criar o conjunto de rotação, você pode alterar a miniatura do conjunto de rotação ou permitir que AEM selecione a miniatura automaticamente com base nos ativos no conjunto de rotação. Para selecionar uma miniatura, toque em **[!UICONTROL Alterar miniatura]**. Selecione qualquer imagem (você também pode navegar para outras pastas para localizar imagens). If you have selected a thumbnail and then decide that you want AEM to generate one from the spin set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Execute um dos procedimentos a seguir:

   * Perto do canto superior esquerdo da página do Editor **[!UICONTROL de conjunto de]** rotação, toque em **[!UICONTROL Adicionar ativo]**.
   * Próximo ao meio da página do Editor **[!UICONTROL de conjunto de]** rotação, toque em **[!UICONTROL Tocar para abrir o Seletor]** de ativos.

   Toque em para selecionar ativos que deseja incluir no Conjunto de rotação. Os ativos selecionados têm um ícone de marca de seleção sobre eles. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select]**.

   Com o Seletor de ativos, procure por ativos ao digitar uma palavra-chave e tocar em **[!UICONTROL Retornar]**. Aplique filtros para refinar os resultados da pesquisa. Filtre por caminho, coleção, tipo de arquivo e tag. Selecione o filtro e toque no ícone **[!UICONTROL Filtro]**, na barra de ferramentas. Para alterar a visualização, próximo ao canto superior direito da página, toque no ícone de **[!UICONTROL Visualização]** e, em seguida, toque em Visualização **[!UICONTROL da]** coluna, Visualização **[!UICONTROL da]** placa ou Visualização **[!UICONTROL da]** Lista.

   See [Working with Selectors](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Quando você adiciona ativos ao seu conjunto, eles são adicionados automaticamente em ordem alfanumérica. Você pode reordenar ou classificar manualmente os ativos depois de adicioná-los. Se necessário, arraste o ícone **[!UICONTROL Reordenar]** de um ativo à direita do nome do arquivo do ativo para reordenar as imagens para cima ou para baixo na lista definida.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Opcional) Execute um dos procedimentos a seguir:

   * Para excluir uma imagem, selecione-a e toque em **[!UICONTROL Excluir ativo]**.
   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a preset to apply to all the assets at once.

1. Toque em **[!UICONTROL Salvar]**. Seu Spin Set recém-criado é exibido na pasta em que você o criou.

## Visualizando Conjuntos de rotação {#viewing-spin-sets}

Você pode criar conjuntos de rotação na interface do usuário ou automaticamente usando predefinições [de conjuntos de](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)lotes. No entanto, os conjuntos criados usando predefinições de conjuntos de lotes *não* são exibidos na interface do usuário. Você pode acessar conjuntos criados por meio de predefinições de conjuntos de lotes de três maneiras diferentes. (Esses métodos estão disponíveis mesmo se você tiver criado os Conjuntos de rotação na interface do usuário).

Você também pode visualização conjuntos por meio da interface do usuário, conforme descrito em [Edição de conjuntos de rotação](#editing-spin-sets).

**Para visualização de Conjuntos de rotação:**

1. Ao abrir as propriedades de um ativo individual. As propriedades indicam quais conjuntos o ativo selecionado é membro (em **[!UICONTROL Membro dos conjuntos]**). Toque no nome do conjunto para ver o conjunto inteiro.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. A partir de uma imagem de membro de qualquer conjunto. Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. From search, you can select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   A pesquisa retorna conjuntos correspondentes criados manualmente na interface do usuário ou criados automaticamente por meio de predefinições de conjuntos de lotes. Para conjuntos automatizados, o query de pesquisa é realizado usando **[!UICONTROL Start com]** critérios de pesquisa diferentes AEM pesquisa que se baseia no uso de critérios de pesquisa **[!UICONTROL Contém]** . Definir o filtro como **[!UICONTROL Conjuntos]** é a única maneira de pesquisar conjuntos automatizados.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Edição de conjuntos de rotação {#editing-spin-sets}

É possível executar várias tarefas de edição em Conjuntos de rotação, como:

* Adicione imagens ao conjunto de rotação.
* Reordene as imagens no Conjunto de rotação.
* Exclua ativos no Conjunto de rotação.
* Aplicar predefinições do visualizador.
* Exclua o conjunto de rotação.

**Para editar um conjunto de rotação:**

1. Execute um dos procedimentos a seguir:

   * Passe o mouse sobre um ativo do Conjunto de rotação e, em seguida, toque em **[!UICONTROL Editar]** (ícone de lápis).
   * Passe o mouse sobre um ativo do Conjunto de rotação, toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção) e, em seguida, toque em **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque em um ativo do Conjunto de rotação e, em seguida, toque em **[!UICONTROL Editar]** (ícone de lápis) na barra de ferramentas.

1. Para editar o Conjunto de rotação, execute um dos procedimentos a seguir:

   * Para reordenar imagens, arraste uma imagem para um novo local (selecione o ícone de reordenação para mover itens).
   * Para classificar itens em ordem crescente ou decrescente, toque no cabeçalho da coluna.
   * Para adicionar um ativo ou atualizar um ativo existente, toque em **[!UICONTROL Adicionar ativo]**. Navegue até um ativo, selecione-o e, em seguida, toque em **[!UICONTROL Selecionar]** próximo ao canto superior direito.
Se você excluir a imagem que AEM usa para a miniatura substituindo-a por outra imagem, o ativo original ainda será exibido.
   * Para excluir um ativo, selecione-o e toque em **[!UICONTROL Excluir ativo]**.
   * Para aplicar uma predefinição, toque no ícone **[!UICONTROL Predefinir]** e selecione uma predefinição.
   * Para excluir um conjunto de rotação inteiro, navegue até o conjunto de rotação, selecione-o e selecione **[!UICONTROL Excluir]**

      >[!NOTE]
      >* You can edit the images in a Spin Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the **[!UICONTROL Edit]** (pencil icon) on an individual asset to open the editing window.


1. Clique em **[!UICONTROL Salvar]** ao concluir a edição.

## Visualizar conjuntos de giro {#previewing-spin-sets}

Consulte [Visualizar ativos](previewing-assets.md).

## Publicar conjuntos de rotação {#publishing-spin-sets}

Consulte [Publicação de ativos](publishing-dynamicmedia-assets.md).
