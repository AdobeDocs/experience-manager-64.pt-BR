---
title: Conjuntos de rotação
description: Saiba como trabalhar com Conjuntos de rotação no Dynamic Media. Um Conjunto de rotação simula o ato real de girar um objeto para examiná-lo a partir de qualquer ângulo.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 47cb6d40-a5c4-4f6a-9794-bd2eddfaa7d0
feature: Spin Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1959'
ht-degree: 6%

---

# Conjuntos de rotação {#spin-sets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Um Conjunto de rotação simula o ato real de girar um objeto para examiná-lo. Os Conjuntos de rotação permitem visualizar itens de qualquer ângulo, obtendo os detalhes visuais principais de qualquer ângulo.

Um Conjunto de rotação simula uma experiência de visualização de 360 graus. O Dynamic Media oferece Conjuntos de rotação de eixo único em que os visualizadores podem girar um item. Além disso, os usuários podem &quot;formar livremente&quot; o zoom e deslocar qualquer uma das exibições com apenas alguns cliques do mouse. Dessa forma, os usuários podem examinar um item mais detalhadamente de um ponto de vista específico.

Os conjuntos de rotação são designados por um banner com a palavra **[!UICONTROL SPINSET]**. Além disso, se o Conjunto de rotação for publicado, então a data de publicação, indicada pela variável **[!UICONTROL World]** estiver no banner junto com a última data de modificação, indicada pela variável **[!UICONTROL Lápis]** será exibido.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Para obter informações sobre a interface do usuário do Assets, consulte [Gerenciamento de ativos com a interface de toque](managing-assets-touch-ui.md).

Quando você cria um Conjunto de rotação, o Adobe recomenda a seguinte prática recomendada e aplica o seguinte limite:

| Tipo de limite | Prática recomendada | Limite imposto |
| --- | --- | --- |
| Número máximo de linhas/colunas por conjunto 2D | 12 a 18 imagens por conjunto | 1000 |

Consulte também [Limitações do Dynamic Media](/help/assets/limitations.md).

## Início rápido: Conjuntos de rotação {#quick-start-spin-sets}

Para ativar e executar rapidamente com Conjuntos de rotação, siga este fluxo de trabalho:

1. [Carregue suas imagens para várias exibições.](#uploading-assets-for-spin-sets)

   No mínimo, você precisa de 8 a 12 capturas de um item para um Conjunto de rotação unidimensional e 16 a 24 para um Conjunto de rotação bidimensional. As fotos devem ser tiradas regularmente para dar a impressão de que o item está girando e sendo virado. Por exemplo, se um Conjunto de rotação unidimensional incluir 12 capturas, gire o item 30 graus (360/12) para cada disparo.

1. [Criar Conjuntos De Rotação.](#creating-spin-sets)

   Para criar um Conjunto de rotação, selecione **[!UICONTROL Criar > Conjunto de rotação]** e nomeie o conjunto, escolha os ativos e classifique as imagens na ordem em que serão exibidas.

   Consulte [Trabalhar com seletores](working-with-selectors.md).

   >[!NOTE]
   >
   >Você também pode criar Conjuntos de rotação automaticamente por meio de [predefinições do conjunto de lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*Os conjuntos em lotes são criados pelo IPS (Sistema de produção de imagem) como parte da ingestão de ativos e estão disponíveis apenas no modo Dynamic Media - Scene7*.

1. Configurar [Predefinições do visualizador de conjunto de rotação](managing-viewer-presets.md), conforme necessário.

   Os administradores podem criar ou modificar as predefinições do Visualizador do conjunto de rotação. Para ver seu Conjunto de rotação com uma predefinição do visualizador, selecione o Conjunto de rotação e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]** para criar ou editar predefinições do visualizador.

   Consulte [Adicionar e editar predefinições do visualizador.](managing-viewer-presets.md)

1. [Visualização de conjuntos de rotação](#viewing-spin-sets).

   Você pode exibir e acessar conjuntos criados por meio de predefinições de conjuntos em lotes de três maneiras diferentes. (Conjuntos criados usando predefinições de conjunto de lotes, *not* aparecem na interface do usuário.)

1. [Visualizar conjuntos de rotação.](previewing-assets.md)

   Selecione o Conjunto de rotação e você pode visualizá-lo. Gire o conjunto de rotação. Você pode escolher visualizadores diferentes do **[!UICONTROL Visualizadores]** , disponível no menu suspenso do painel à esquerda.

1. [Publicar Conjuntos De Rotação.](publishing-dynamicmedia-assets.md)

   A publicação de um Conjunto de rotação ativa a ordem em que as imagens aparecem em um conjunto de rotação. Certifique-se de ordená-los para que o giro seja uma exibição suave de 360 graus.**[!UICONTROL URL]** e **[!UICONTROL Incorporar]** string. Além disso, você deve [publicar a predefinição do visualizador](managing-viewer-presets.md).

1. [Vincular URLs ao seu aplicativo web](linking-urls-to-yourwebapplication.md) ou [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

   O AEM Assets cria chamadas de URL para Conjuntos de rotação e as ativa depois que você publica os Conjuntos de rotação. Você pode copiar esses URLs ao visualizar ativos. Como alternativa, você pode incorporá-los ao seu site.

   Selecione o Conjunto de rotação e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte [Vincular um conjunto de rotação a uma página da Web](linking-urls-to-yourwebapplication.md) e [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

Se precisar, você pode [editar Conjuntos de rotação](#editing-spin-sets). Além disso, é possível visualizar e editar [Propriedades do conjunto de rotação](managing-assets-touch-ui.md#editing-properties).

## Fazer upload de ativos para conjuntos de rotação {#uploading-assets-for-spin-sets}

No mínimo, você precisa de 8 a 12 capturas de um item para um Conjunto de rotação unidimensional e 16 a 24 para um Conjunto de rotação bidimensional. As fotos devem ser tiradas regularmente para dar a impressão de que o item está girando e sendo virado. Por exemplo, se um Conjunto de rotação unidimensional incluir 12 capturas, gire o item 30 graus (360/12) para cada disparo.

Você pode fazer upload de imagens para os Conjuntos de rotação como faria [fazer upload de qualquer outro ativo no AEM Assets](managing-assets-touch-ui.md).

### Diretrizes para fotografar imagens do Conjunto de rotação {#guidelines-for-shooting-spin-set-images}

Veja a seguir algumas práticas recomendadas sobre imagens de conjunto de rotação. Em geral, quanto mais imagens você tiver em um Conjunto de rotação, melhor será o efeito giratório da imagem. No entanto, incluir muitas imagens no conjunto também aumenta a quantidade de tempo que as imagens levam para serem carregadas. AEM recomenda estas diretrizes para fotografar imagens para uso em Conjuntos de rotação:

* No mínimo, use 8 a 12 imagens em um conjunto de rotação unidimensional e 16 a 24 imagens em um conjunto de rotação bidimensional. É necessário um mínimo de 8 imagens para rodar 360 graus. Os Conjuntos de rotação unidimensionais são mais comuns, pois a criação de Conjuntos de rotação bidimensionais exige muito trabalho.
* Usar um formato sem perdas; TIFF e PNG são recomendadas.
* Mascarar todas as imagens para que o item apareça em um plano de fundo branco ou de alto contraste. Como opção, adicione sombras.
* Verifique se os detalhes do produto estão bem iluminados e em foco.
* Use imagens de rotação para roupas de moda com um manequim ou modelo. Frequentemente, o manequim é completamente mascarado (utilizando um manequim de vidro) ou na imagem aparece um manequim/moldura estilizada. Você pode criar um conjunto de rotação no modelo definindo o número de ângulos. Marque cada ângulo com uma fita no chão para guiar o modelo para pisar e olhe na direção de cada tomada.

## Criação de conjuntos de rotação {#creating-spin-sets}

A ordem em que as imagens aparecem em um conjunto de rotação é importante. Certifique-se de ordená-los para que o giro seja uma exibição suave de 360 graus.

>[!NOTE]
>
>Também é possível criar conjuntos de rotação automaticamente por meio de [predefinições de conjuntos em lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>
>Os conjuntos em lotes são criados pelo IPS (Sistema de produção de imagem) como parte da ingestão de ativos e estão disponíveis apenas no modo Dynamic Media - Scene7.
>
>Consulte &quot;Criando predefinições de conjuntos de lotes para gerar automaticamente conjuntos de imagens e conjuntos de rotação&quot; em [Configuração do Dynamic Media - Modo Scene7](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

Quando você cria um Conjunto de rotação, o Adobe recomenda a seguinte prática recomendada e aplica o seguinte limite:

| Tipo de limite | Prática recomendada | Limite imposto |
| --- | --- | --- |
| Número máximo de linhas/colunas por conjunto 2D | 12 a 18 imagens por conjunto | 1000 |

Consulte também [Limitações do Dynamic Media](/help/assets/limitations.md).

**Para criar Conjuntos de rotação:**

1. No Assets, navegue até o local em que deseja criar um conjunto de rotação, toque em **[!UICONTROL Criar]** e selecione **[!UICONTROL Conjunto de rotação]**. Além disso, crie o conjunto de dentro de uma pasta que contenha seus ativos.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. No **[!UICONTROL Editor de conjunto de rotação]** na página **[!UICONTROL Título]** digite um nome para o Conjunto de rotação. O nome aparece no banner através do Conjunto de rotação. Opcionalmente, informe uma descrição.

   ![chlimage_1-382](assets/chlimage_1-382.png)

   Ao criar o conjunto de rotação, você pode alterar a miniatura do conjunto de rotação ou permitir que AEM selecione a miniatura automaticamente com base nos ativos no conjunto de rotação. Para selecionar uma miniatura, toque em **[!UICONTROL Alterar miniatura]**. Selecione qualquer imagem (você também pode navegar para outras pastas para localizar imagens). Se tiver selecionado uma miniatura e decidir que deseja AEM gerar uma a partir do conjunto de rotação, selecione **[!UICONTROL Alterar para Miniatura Automática]**.

1. Siga um destes procedimentos:

   * Próximo ao canto superior esquerdo do **[!UICONTROL Editor de conjunto de rotação]** página, toque em **[!UICONTROL Adicionar ativo]**.
   * Próximo do meio da **[!UICONTROL Editor de conjunto de rotação]** página, toque em **[!UICONTROL Toque para abrir o Seletor de ativos]**.

   Toque para selecionar ativos que deseja incluir no seu Conjunto de rotação. Os ativos selecionados têm um ícone de marca de seleção sobre eles. Quando terminar, próximo ao canto superior direito da página, toque em **[!UICONTROL Selecionar]**.

   Com o Seletor de ativos, procure por ativos ao digitar uma palavra-chave e tocar em **[!UICONTROL Retornar]**. Aplique filtros para refinar os resultados da pesquisa. Filtre por caminho, coleção, tipo de arquivo e tag. Selecione o filtro e toque no ícone **[!UICONTROL Filtro]**, na barra de ferramentas. Para alterar a exibição, próximo ao canto superior direito da página, toque no **[!UICONTROL Exibir]** ícone e toque em **[!UICONTROL Exibição de coluna]**, **[!UICONTROL Exibição de cartão]** ou **[!UICONTROL Exibição de lista]**.

   Consulte [Trabalhar com seletores](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Ao adicionar ativos ao seu conjunto, eles são automaticamente adicionados em ordem alfanumérica. Você pode reordenar ou classificar ativos manualmente depois de adicioná-los. Se necessário, arraste o **[!UICONTROL Reordenar]** ícone à direita do nome do arquivo do ativo para reordenar as imagens para cima ou para baixo na lista definida.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Opcional) Siga um destes procedimentos:

   * Para excluir uma imagem, selecione-a e toque em **[!UICONTROL Excluir ativo]**.
   * Para aplicar uma predefinição, próximo ao canto superior direito da página, toque em **[!UICONTROL Predefinição]** e, em seguida, selecione uma predefinição para aplicar a todos os ativos ao mesmo tempo.

1. Toque **[!UICONTROL Salvar]**. Seu Conjunto de rotação recém-criado aparece na pasta em que você o criou.

## Visualização de conjuntos de rotação {#viewing-spin-sets}

Você pode criar conjuntos de rotação na interface do usuário ou automaticamente usando [predefinições do conjunto de lotes](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). No entanto, os conjuntos criados usando predefinições de conjunto de lotes, *not* forem exibidos na interface do usuário do . Você pode acessar conjuntos criados por meio de predefinições de conjuntos em lotes de três maneiras diferentes. (Esses métodos estão disponíveis mesmo se você criou os Conjuntos de rotação na interface do usuário).

Você também pode visualizar conjuntos por meio da interface do usuário, conforme descrito em [Editar conjuntos de rotação](#editing-spin-sets).

**Para exibir Conjuntos de rotação:**

1. Ao abrir as propriedades de um ativo individual. As propriedades indicam quais conjuntos o ativo selecionado é um membro de (em **[!UICONTROL Membro dos Conjuntos]**). Toque no nome do conjunto para ver todo o conjunto.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. A partir de uma imagem de membro de qualquer conjunto. Selecione o **[!UICONTROL Conjuntos]** para exibir os conjuntos dos quais o ativo é membro.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. Na pesquisa, você pode selecionar **[!UICONTROL Filtros]**, em seguida expanda **[!UICONTROL Dynamic Media]** e selecione **[!UICONTROL Conjuntos]**.

   A pesquisa retorna conjuntos correspondentes que foram criados manualmente na interface do usuário ou criados automaticamente por meio de predefinições de conjuntos em lotes. Para conjuntos automatizados, a consulta de pesquisa é realizada usando **[!UICONTROL Começa com]** critérios de pesquisa diferentes da pesquisa de AEM baseada no uso de **[!UICONTROL Contém]** critérios de pesquisa. Definição do filtro como **[!UICONTROL Conjuntos]** é a única maneira de pesquisar conjuntos automatizados.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Editar conjuntos de rotação {#editing-spin-sets}

Você pode executar várias tarefas de edição em Conjuntos de rotação, como o seguinte:

* Adicione imagens ao Conjunto de rotação.
* Reordene as imagens no Conjunto de rotação.
* Exclua ativos no Conjunto de rotação.
* Aplicar predefinições do visualizador.
* Exclua o Conjunto de rotação.

**Para editar um Conjunto de rotação:**

1. Siga um destes procedimentos:

   * Passe o mouse sobre um ativo Conjunto de rotação, em seguida toque em **[!UICONTROL Editar]** (ícone de lápis).
   * Passe o mouse sobre um ativo Conjunto de rotação, toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção) e toque em **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque em um ativo Conjunto de rotação e toque em **[!UICONTROL Editar]** (ícone de lápis) na barra de ferramentas.

1. Para editar o Conjunto de rotação, siga um destes procedimentos:

   * Para reorganizar imagens, arraste uma imagem para um novo local (selecione o ícone de reordenação para mover itens).
   * Para classificar itens em ordem crescente ou decrescente, toque no cabeçalho da coluna.
   * Para adicionar um ativo ou atualizar um ativo existente, toque em **[!UICONTROL Adicionar ativo]**. Navegue até um ativo, selecione-o e toque em **[!UICONTROL Selecionar]** próximo ao canto superior direito.
Se você excluir a imagem que AEM usa para a miniatura ao substituí-la por outra imagem, o ativo original ainda será exibido.
   * Para excluir um ativo, selecione-o e toque em **[!UICONTROL Excluir ativo]**.
   * Para aplicar uma predefinição, toque no **[!UICONTROL Predefinição]** e selecione uma predefinição.
   * Para excluir um Conjunto de rotação inteiro, navegue até o Conjunto de rotação, selecione-o e selecione **[!UICONTROL Excluir]**

      >[!NOTE]
      >* Você pode editar as imagens em um Conjunto de rotação navegando até o conjunto e tocando em **[!UICONTROL Definir membros]** no painel à esquerda e toque no **[!UICONTROL Editar]** (ícone de lápis) em um ativo individual para abrir a janela de edição.


1. Clique em **[!UICONTROL Salvar]** ao concluir a edição.

## Visualização de conjuntos de rotação {#previewing-spin-sets}

Consulte [Visualização de ativos](previewing-assets.md).

## Publicação de conjuntos de rotação {#publishing-spin-sets}

Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).
