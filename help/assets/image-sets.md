---
title: Conjuntos de imagem
seo-title: Conjuntos de imagem
description: Saiba como trabalhar com conjuntos de imagens em mídia dinâmica
seo-description: Saiba como trabalhar com conjuntos de imagens em mídia dinâmica
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Conjuntos de imagem {#image-sets}

Os Conjuntos de imagens fornecem aos usuários uma experiência de visualização integrada, na qual eles podem ver diferentes visualizações de um item clicando em uma imagem em miniatura. Os Conjuntos de imagens permitem que você apresente exibições alternativas de um item e o visualizador oferece ferramentas de zoom para examinar as imagens de perto.

Image Sets are designated by a banner with the word **[!UICONTROL IMAGESET]**. Além disso, se o Conjunto de imagens for publicado, a data de publicação, indicada pelo ícone **[!UICONTROL Mundo]**, estará no banner junto com a última data de modificação, indicada pelo ícone **[!UICONTROL Lápis]**.

![chlimage_1-339](assets/chlimage_1-339.png)

No conjunto de imagens, também é possível criar amostras criando um Conjunto de imagens e adicionando miniaturas.

Esse aplicativo é especialmente útil para quando você deseja mostrar um item em uma cor, padrão ou finalização diferente. Para criar um Conjunto de imagens com amostras de cores, você precisa de uma imagem para cada cor, padrão ou acabamento diferente que deseja apresentar aos usuários. Você também precisa de uma cor, padrão ou amostra de fim para cada cor, padrão ou final.

Por exemplo, suponha que você queira apresentar imagens de maiúsculas com diferentes notas coloridas; as contas são vermelho, verde e azul. Neste caso, você precisa de três tiros do mesmo chapéu. Você precisa de um tiro com um vermelho, um com um verde, e outro com uma conta azul. Você também precisa de uma amostra de cor vermelha, verde e azul. As amostras de cores servem como miniaturas que os usuários clicam no Visualizador do conjunto de amostras para ver a tampa vermelha, com borda verde ou com borda azul.

>[!NOTE]
>
>Para obter informações sobre a interface do usuário Ativos, consulte [Gerenciamento de ativos com a interface do usuário](managing-assets-touch-ui.md)de toque.

## Início rápido: Conjuntos de imagens {#quick-start-image-sets}

Para começar a trabalhar rapidamente:

1. [Carregue suas imagens mestre para várias exibições.](#uploading-assets-in-image-sets)

   Comece carregando as imagens para seus Conjuntos de imagens. Como os usuários podem aplicar zoom em imagens no Visualizador do conjunto de imagens, considere o zoom ao escolher imagens. Verifique se as imagens têm pelo menos 2000 pixels na maior dimensão. O AEM Assets suporta vários formatos de arquivo de imagem, mas as imagens TIFF, PNG e EPS sem perdas são recomendadas.

1. [Criar conjuntos de imagens.](#creating-image-sets)

   Em Conjuntos de imagens, os usuários clicam em imagens em miniatura no Visualizador do conjunto de imagens.

   Para criar um Conjunto de imagens em Ativos, toque em **[!UICONTROL Criar > Conjuntos]** de imagens. Em seguida, adicione imagens e toque em **[!UICONTROL Salvar]**.

   You can also create image sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

   **Importante** — Os conjuntos de lotes são criados pelo IPS (Image Production System) como parte da ingestão de ativos e estão disponíveis somente no modo Dynamic Media - Scene7.

   Consulte [Preparando ativos do Conjunto de imagens para fazer upload e upload dos arquivos](#uploading-assets-in-image-sets).

   See [Working with Selectors.](working-with-selectors.md)

1. Adicione predefinições [do Visualizador do conjunto de](managing-viewer-presets.md)imagens, conforme necessário.

   Administrators can create or modify Image **[!UICONTROL Set Viewer Presets]**. To see your image set with a viewer preset, select the image set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   Consulte **[!UICONTROL Ferramentas > Ativos > Predefinições]** do visualizador para criar ou editar predefinições do visualizador.

1. (Opcional) [Visualizando Conjuntos](image-sets.md#viewing-image-sets) de Imagens que foram criados usando predefinições de conjuntos de lotes.
1. [Visualizar conjuntos de imagens.](previewing-assets.md)

   Selecione o Conjunto de imagens e você pode visualizá-lo. Toque nos ícones de miniatura para examinar seu Conjunto de imagens no Visualizador selecionado. Você pode escolher visualizadores diferentes no menu **[!UICONTROL Visualizadores]** , disponível no menu suspenso do painel esquerdo.

1. [Publicar conjuntos de imagens.](publishing-dynamicmedia-assets.md)

   A publicação de um conjunto de imagens ativa o URL e a string Incorporada. Além disso, você deve [publicar qualquer predefinição](managing-viewer-presets.md) do visualizador personalizado que tenha criado. As predefinições do visualizador predefinidas já estão publicadas.

1. [Vincule URLs ao aplicativo](linking-urls-to-yourwebapplication.md) da Web ou [Incorpore o visualizador](embed-code.md)de vídeo ou imagem.

   Os ativos AEM criam chamadas de URL para Conjuntos de imagens e as ativam depois que você publica os conjuntos de imagens. Você pode copiar esses URLs ao visualizar ativos. Como alternativa, você pode incorporá-los ao seu site.

   Selecione o Conjunto de imagens e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte [Vincular um conjunto de imagens a uma página da Web](linking-urls-to-yourwebapplication.md) e [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

Para editar Conjuntos de imagens, consulte [edição de Conjuntos de imagens.](#editing-image-sets) Além disso, é possível exibir e editar as propriedades [do Conjunto de](managing-assets-touch-ui.md#editing-properties)imagens.

Se tiver problemas ao criar conjuntos, consulte Imagens e conjuntos no modo [Solução de](troubleshoot-dms7.md#images-and-sets)problemas de Dynamic Media - Scene7.

## Fazer upload de ativos em conjuntos de imagens {#uploading-assets-in-image-sets}

Comece carregando as imagens para seus Conjuntos de imagens. Como os usuários podem aplicar zoom em imagens no Visualizador do conjunto de imagens, considere o zoom ao escolher imagens. Verifique se as imagens têm pelo menos 2000 pixels na maior dimensão. Os Conjuntos de imagens são compatíveis com vários formatos de arquivo de imagem, mas as imagens TIFF, PNG e EPS são recomendadas sem perdas.

Você pode carregar imagens para Conjuntos de imagens da mesma forma que faria [upload de qualquer outro ativo em Ativos](managing-assets-touch-ui.md#uploading-assets).

### Preparando ativos de Conjunto de imagens para upload {#preparing-image-set-assets-for-upload}

Antes de criar Conjuntos de imagens, verifique se as imagens têm o tamanho e o formato corretos.

Para criar um Conjunto de imagens de várias exibições, você precisa de imagens que mostrem um item de diferentes pontos de vista ou mostrem diferentes aspectos do mesmo item. O objetivo é destacar os recursos importantes de um item para que os visualizadores tenham uma imagem completa de como ele se parece ou faz.

Como os usuários podem aplicar zoom em Conjuntos de imagens, verifique se as imagens têm pelo menos 2000 pixels na maior dimensão. Os ativos oferecem suporte para vários formatos de arquivo de imagem, mas são recomendadas imagens TIFF, PNG e EPS sem perdas.

>[!NOTE]
>
>Além disso, se estiver usando miniaturas para indicar amostras de produtos, é necessário fazer o seguinte:
>
>Você precisa de vinhetas ou fotos diferentes da mesma imagem mostrando-as em cores, padrões ou finalizações diferentes. Você também precisa de arquivos em miniatura que correspondam às diferentes cores, padrões ou finalizações. Por exemplo, para apresentar miniaturas com um conjunto de imagens mostrando a mesma jaqueta em preto, marrom e verde, é necessário:
>
>* Um tiro preto, marrom e verde do mesmo casaco.
>* Uma miniatura de cor preta, marrom e verde.
>



## Criação de conjuntos de imagens {#creating-image-sets}

Você pode criar Conjuntos de imagens pela interface do usuário ou por meio da API. Esta seção descreve como criar Conjuntos de imagens na interface do usuário.

>[!NOTE]
>
>You can also create image sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**** Importante: Os conjuntos de lotes são criados pelo IPS (Image Production System) como parte da ingestão de ativos e estão disponíveis somente no modo Dynamic Media - Scene7.

Quando você adiciona ativos ao seu conjunto, eles são adicionados automaticamente em ordem alfanumérica. Você pode reordenar ou classificar manualmente os ativos depois de adicionados.

>[!NOTE]
>
>Os conjuntos de imagens não são suportados em ativos com `,` (vírgula) no nome do arquivo.

**Para criar um conjunto** de imagens:

1. In **Assets**, navigate to where you want to create an image set, tap **[!UICONTROL Create]**, and select **[!UICONTROL Image Set]**. Além disso, crie o conjunto de dentro de uma pasta que contenha seus ativos.

   ![chlimage_1-344](assets/chlimage_1-340.png)

1. Na página Editor do conjunto de imagens, no campo **[!UICONTROL Título]** , digite um nome para o Conjunto de imagens. O nome é exibido no banner ao longo do Conjunto de imagens. Opcionalmente, informe uma descrição.

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >Ao criar o conjunto de imagens, você pode alterar a miniatura do conjunto de imagens ou permitir que o AEM selecione a miniatura automaticamente com base nos ativos no conjunto de imagens. Para selecionar uma miniatura, toque em **[!UICONTROL Alterar miniatura]** e selecione qualquer imagem (você também pode navegar para outras pastas para localizar imagens). Se tiver selecionado uma miniatura e decidir que deseja que o AEM gere uma a partir do conjunto de imagens, selecione **[!UICONTROL Alternar para Miniatura automática]**.

1. Execute um dos procedimentos a seguir:

   * Perto do canto superior esquerdo da página do Editor **[!UICONTROL do conjunto de]** imagens, toque em **[!UICONTROL Adicionar ativo]**.
   * Próximo ao meio da página do Editor **[!UICONTROL do conjunto de]** imagens, toque em **[!UICONTROL Tocar para abrir o Seletor]** de ativos.
   Toque em para selecionar ativos que deseja incluir no conjunto de imagens. Os ativos selecionados têm um ícone de marca de seleção sobre eles. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select]**.

   Com o Seletor de ativos, procure por ativos ao digitar uma palavra-chave e tocar em **[!UICONTROL Retornar]**. Aplique filtros para refinar os resultados da pesquisa. Filtre por caminho, coleção, tipo de arquivo e tag. Selecione o filtro e toque no ícone **[!UICONTROL Filtro]**, na barra de ferramentas. Change the view by tapping the **[!UICONTROL View]** icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View]**.

   See [Working with Selectors.](working-with-selectors.md)

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. Quando você adiciona ativos ao seu conjunto, eles são adicionados automaticamente em ordem alfanumérica. Você pode reordenar ou classificar manualmente os ativos depois de adicioná-los.

   Se necessário, arraste o ícone **[!UICONTROL Reordenar]** de um ativo à direita do nome do arquivo do ativo para reordenar as imagens para cima ou para baixo na lista definida.

   ![spin_set_assets](assets/spin_set_assets.png)

   If you want to change a thumbnail or swatch, tap the **[!UICONTROL Thumbnail]** icon next to the image and navigate to the thumbnail or swatch you want. When done selecting all the images tap **[!UICONTROL Save]**.

1. (Opcional) Execute um dos procedimentos a seguir:

   * Para excluir uma imagem, selecione-a e toque em **[!UICONTROL Excluir ativo]**.
   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a preset to apply to all the assets at once.

1. Toque em **[!UICONTROL Salvar]**. Seu conjunto de imagens recém-criado é exibido na pasta em que você o criou.

## Visualizando conjuntos de imagens {#viewing-image-sets}

Você pode criar conjuntos de imagens na interface do usuário ou automaticamente usando predefinições [de conjuntos de](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)lotes.

**Importante** —Os conjuntos de lotes são criados pelo IPS [Image Production System] como parte da ingestão de ativos e estão disponíveis somente no modo Dynamic Media - Scene7.)

No entanto, os conjuntos criados usando predefinições de conjuntos de lotes *não* são exibidos na interface do usuário. Você pode ver esses conjuntos de três maneiras diferentes. (Esses métodos estão disponíveis mesmo se você tiver criado os conjuntos de imagens na interface do usuário).

* Ao abrir as propriedades de um ativo individual. As propriedades indicam quais conjuntos o ativo selecionado é membro (em **[!UICONTROL Membro dos conjuntos]**). Toque no nome do conjunto para ver o conjunto inteiro.

   ![chlimage_1-343](assets/chlimage_1-343.png)

* A partir de uma imagem de membro de qualquer conjunto. Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-344](assets/chlimage_1-344.png)

* From search, you can select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   A pesquisa retorna conjuntos correspondentes criados manualmente na interface do usuário ou criados automaticamente por meio de predefinições de conjuntos de lotes. Para conjuntos automatizados, a consulta de pesquisa é realizada usando critérios de pesquisa &quot;Começa com&quot; diferentes da pesquisa do AEM, que se baseia no uso de critérios de pesquisa &quot;Contém&quot;. Definir o filtro como **[!UICONTROL Conjuntos]** é a única maneira de pesquisar conjuntos automatizados.

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>É possível exibir os conjuntos por meio da interface do usuário, conforme descrito em [Edição de conjuntos](#editing-image-sets)de imagens.

## Edição de conjuntos de imagens {#editing-image-sets}

Você pode executar várias tarefas de edição em Conjuntos de imagens, como:

* Adicione imagens ao conjunto de imagens.
* Reordene as imagens no Conjunto de imagens.
* Excluir ativos no Conjunto de imagens.
* Aplicar predefinições do visualizador.
* Exclua o conjunto de imagens.

**Para editar conjuntos** de imagens:

1. Execute um dos procedimentos a seguir:

   * Passe o mouse sobre um ativo do Conjunto de imagens e toque em **[!UICONTROL Editar]** (ícone de lápis).
   * Passe o mouse sobre um ativo do Conjunto de imagens, toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção) e, em seguida, toque em **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque em um ativo do Conjunto de imagens e, em seguida, toque em **[!UICONTROL Editar]** (ícone de lápis) na barra de ferramentas.

1. Para editar as imagens no Conjunto de imagens, execute um dos procedimentos a seguir:

   * Para reorganizar ativos, arraste uma imagem para um novo local (selecione o ícone de reordenação para mover itens).
   * Para classificar itens em ordem crescente ou decrescente, toque no cabeçalho da coluna.
   * Para adicionar um ativo ou atualizar um ativo existente, toque em **[!UICONTROL Adicionar ativo]**. Navegue até um ativo, selecione-o e toque em **[!UICONTROL Selecionar]** próximo ao canto superior direito da página.
   >[!NOTE]
   >Se você excluir a imagem que o AEM usa para a miniatura substituindo-a por outra imagem, o ativo original ainda será exibido.

   * Para excluir um ativo, selecione-o e toque em **[!UICONTROL Excluir ativo]**.
   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a viewer preset.
   * Para adicionar ou alterar uma miniatura, selecione o ícone de miniatura ao lado direito do ativo. Navegue até a nova miniatura ou ativo de amostra, selecione-o e toque em **[!UICONTROL Selecionar]**.
   * Para excluir um conjunto de imagens inteiro, navegue até o conjunto de imagens, selecione-o e toque em **[!UICONTROL Excluir]**.
   >[!NOTE]
   >
   >Edite as imagens em um Conjunto de imagens ao navegar até o conjunto, tocar em **[!UICONTROL Definir membros]** no painel à esquerda e tocar no ícone Lápis em um ativo individual para abrir a janela de edição.****

1. Toque em **[!UICONTROL Salvar]** quando terminar a edição.

## Visualizar conjuntos de imagens {#previewing-image-sets}

Consulte [Visualizar ativos](previewing-assets.md).

## Publicar conjuntos de imagens {#publishing-image-sets}

Consulte [Publicação de ativos](publishing-dynamicmedia-assets.md).
