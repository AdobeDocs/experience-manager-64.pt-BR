---
title: Conjuntos de mídia mista
description: Saiba como trabalhar com conjuntos de mídia mista (imagens, conjuntos de imagens, conjuntos de rotação e vídeos) no Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 252c1a50-17ac-4412-88d6-49bb6850658d
feature: Mixed Media Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 18%

---

# Conjuntos de mídia mista {#mixed-media-sets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os Conjuntos de mídias mistas permitem que você forneça uma combinação de imagens, Conjuntos de imagens, Conjuntos de rotação e vídeos em uma apresentação.

Os Conjuntos de mídias mistas são designados por um banner com a palavra **[!UICONTROL MixedMediaSet]**. Além disso, se o Conjunto de mídias mistas for publicado, a data de publicação, indicada pelo ícone **[!UICONTROL Mundo]**, estará no banner junto com a última data de modificação, indicada pelo ícone **[!UICONTROL Lápis]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Para obter informações sobre a interface do usuário do Assets, consulte [Gerenciamento de ativos com a interface de toque](managing-assets-touch-ui.md).

## Início rápido: Conjuntos de mídia mista {#quick-start-mixed-media-sets}

Para ativar e executar rapidamente com Conjuntos de mídias mistas, siga estas etapas:

1. [Fazer upload de seus ativos](#uploading-assets).

   Comece carregando as imagens e os vídeos dos Conjuntos de mídias mistas. Se necessário, crie seus [Conjuntos de imagens](image-sets.md) e [Conjuntos de rotação](spin-sets.md). Como os usuários podem ampliar imagens no Visualizador de conjunto de mídias mistas, considere o zoom ao escolher imagens. Verifique se as imagens têm pelo menos 2000 pixels na maior dimensão.

1. [Criar conjuntos de mídia mista.](#creating-mixed-media-sets)

   Para criar um Conjunto de mídias mistas, no **[!UICONTROL Ativos]** página, toque em **[!UICONTROL Criar > Conjunto de mídias mistas]**, em seguida, nomeie o conjunto. Escolha os ativos e escolha a ordem em que as imagens serão exibidas.

   Consulte [Trabalhar com seletores.](working-with-selectors.md)

1. Configurar [Predefinições do visualizador de mídia mista](managing-viewer-presets.md), conforme necessário.

   Os administradores podem criar ou modificar as Predefinições do visualizador de conjunto de mídia mista. Para ver sua mídia mista com uma predefinição do visualizador, selecione o conjunto de mídias mistas e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte **[!UICONTROL Ferramentas > Ativos > Predefinições do visualizador]** para criar ou editar predefinições do visualizador.

   Consulte [Adicionar e editar predefinições do visualizador.](managing-viewer-presets.md)

1. [Visualizar conjuntos de mídia mista.](#previewing-mixed-media-sets)

   Selecione o Conjunto de mídias mistas e você pode visualizá-lo. Clique nos ícones de miniatura para examinar seu Conjunto de mídias mistas no Visualizador selecionado. Você pode escolher visualizadores diferentes do **[!UICONTROL Visualizadores]** , disponível no menu suspenso do painel à esquerda.

1. [Publicar Conjuntos de Mídias Mistas.](#publishing-mixed-media-sets)

   A publicação de um Conjunto de mídias mistas ativa o URL e a cadeia de caracteres de inserção. Além disso, você deve [publicar a predefinição do visualizador](managing-viewer-presets.md#publishing-viewer-presets).

1. [Vincular URLs ao seu aplicativo web](linking-urls-to-yourwebapplication.md) ou [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

   O AEM Assets cria chamadas de URL para Conjuntos de mídia mista e as ativa após publicar os conjuntos de mídia mista. Você pode copiar esses URLs ao visualizar ativos. Como alternativa, você pode incorporá-los ao seu site.

   Selecione o Conjunto de mídias mistas e, no menu suspenso do painel à esquerda, selecione **[!UICONTROL Visualizadores]**.

   Consulte [Vincular um conjunto de mídias mistas a uma página da Web](linking-urls-to-yourwebapplication.md) e [Incorporar o visualizador de vídeo ou imagem](embed-code.md).

Se precisar, edite [Conjuntos de mídia mista](#editing-mixed-media-sets). Além disso, você pode visualizar e modificar [Propriedades do Conjunto de mídias mistas](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>Se tiver problemas ao criar conjuntos, consulte [Solução de problemas do Dynamic Media - Modo Scene7](troubleshoot-dms7.md).

## Upload de ativos {#uploading-assets}

Comece carregando as imagens e os vídeos dos Conjuntos de mídias mistas. Como os usuários podem ampliar imagens no Visualizador de conjunto de mídias mistas, considere o zoom ao escolher imagens. Verifique se as imagens têm pelo menos 2000 pixels na maior dimensão.

Além disso, se você quiser adicionar conjuntos de rotação ou conjuntos de imagens ao conjunto de mídia mista, crie-os também.

## Criação de conjuntos de mídia mista {#creating-mixed-media-sets}

Você pode adicionar imagens, conjuntos de imagens, conjuntos de rotação e vídeos ao seu conjunto de mídias mistas. Verifique se os arquivos, os conjuntos de imagens e os conjuntos de rotação estão prontos para publicação antes de adicioná-los ao Conjunto de mídias mistas.

Ao adicionar ativos ao seu conjunto, eles são automaticamente adicionados em ordem alfanumérica. Você pode reordenar ou classificar ativos manualmente após a adição.

**Para criar um Conjunto de mídias mistas**:

1. No Assets, navegue até o local em que deseja criar um conjunto de mídia mista, clique em **Criar** e selecione **[!UICONTROL Conjunto de mídia mista]**. Além disso, crie o conjunto de dentro de uma pasta que contenha seus ativos.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. No **[!UICONTROL Editor de conjunto de mídia mista]** página, em **[!UICONTROL Título]**, digite um nome para o Conjunto de mídias mistas. O nome aparece no banner através do Conjunto de mídias mistas. Opcionalmente, informe uma descrição.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Ao criar o conjunto de mídias mistas, você pode alterar a miniatura do conjunto de mídias mistas ou permitir que AEM selecione a miniatura automaticamente com base nos ativos no conjunto de mídias mistas. Para selecionar uma miniatura, clique em **[!UICONTROL Alterar miniatura]** e selecione qualquer imagem (você também pode navegar para outras pastas para localizar imagens). Se tiver selecionado uma miniatura e decidir que deseja AEM uma a partir do conjunto de mídias mistas, selecione **[!UICONTROL Alterar para Miniatura Automática]**.

1. Toque no **[!UICONTROL Seletor de ativos]** para selecionar ativos que deseja incluir no Conjunto de mídias mistas. Selecione-os e toque em **[!UICONTROL Selecionar]**.

   Com o **[!UICONTROL Seletor de ativos]**, procure por ativos ao digitar uma palavra-chave e tocar em **[!UICONTROL Retorno]**. Aplique filtros para refinar os resultados da pesquisa. Filtre por caminho, coleção, tipo de arquivo e tag. Selecione o filtro e toque no ícone **[!UICONTROL Filtro]**, na barra de ferramentas. Altere a exibição ao selecionar o ícone Exibir e selecionar **[!UICONTROL Lista]**, **[!UICONTROL Coluna]** ou **[!UICONTROL Cartão]** exibir.

   Consulte [Trabalhar com seletores](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Reorganize os ativos arrastando-os para cima ou para baixo na lista (deve selecionar o ícone reordenar), conforme necessário.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   Se quiser adicionar miniaturas, clique no botão **[!UICONTROL +]** ícone ao lado da imagem e navegue até a miniatura desejada. Quando terminar de selecionar todas as imagens em miniatura, toque em **[!UICONTROL Salvar]**.

   >[!NOTE]
   >
   >Se desejar adicionar ativos, toque em **[!UICONTROL Adicionar ativo]**.

1. Para excluir um ativo, marque a caixa de seleção correspondente e toque em **[!UICONTROL Excluir ativo]**.
1. Para aplicar uma predefinição, toque em **[!UICONTROL Predefinição]** no canto superior direito e selecione uma predefinição para aplicar aos ativos.
1. Clique em **[!UICONTROL Salvar]**. O Conjunto de mídias mistas recém-criado é exibido na pasta em que você o criou.

## Editar conjuntos de mídia mista {#editing-mixed-media-sets}

Você pode executar uma variedade de tarefas de edição em ativos em Conjuntos de mídias mistas diretamente na interface do usuário [como você faria com qualquer ativo em Ativos](managing-assets-touch-ui.md). Você também pode executar as seguintes ações em Conjuntos de mídias mistas:

* Adicione ativos ao Conjunto de mídias mistas.
* Reorganize os ativos no Conjunto de mídias mistas.
* Exclua ativos no Conjunto de mídias mistas.
* Aplicar predefinições do visualizador.
* Altere a miniatura padrão.

**Para editar conjuntos de mídia mista**:

1. Siga um destes procedimentos:

   * Passe o mouse sobre um ativo de Conjunto de mídias mistas, em seguida, toque em **[!UICONTROL Editar]** (ícone de lápis).
   * Passe o mouse sobre um ativo de Conjunto de mídias mistas, toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção) e toque em **[!UICONTROL Editar]** na barra de ferramentas.
   * Toque em um ativo Conjunto de mídias mistas e toque em **[!UICONTROL Editar]** (ícone de lápis) na barra de ferramentas.

1. No Editor do conjunto de mídias mistas, siga um destes procedimentos:

   * Para reorganizar ativos - No painel esquerdo, toque em **[!UICONTROL Ativos]** (ícone de imagem), arraste um ativo para um novo local.
   * Para adicionar ativos - Na barra de ferramentas, toque em **[!UICONTROL Adicionar ativo]**. Navegue até os ativos. Para cada ativo que deseja adicionar, passe o mouse sobre a imagem do ativo (não o nome do ativo) e toque no ícone de marca de seleção. No canto superior direito, toque em **[!UICONTROL Selecionar]**.
   * Para excluir um ativo - No painel esquerdo, toque em **[!UICONTROL Ativos]** (ícone de imagem), em seguida, selecione o ativo. Na barra de ferramentas, toque em **[!UICONTROL Excluir ativo]**.
   * Para classificar ativos pelo nome em ordem crescente ou decrescente, no painel esquerdo, toque em **[!UICONTROL Ativos]** (ícone de imagem). À direita do **[!UICONTROL Ativos]** toque nos ícones de cursor para cima ou para baixo.

   >[!NOTE]
   >
   >* Para excluir um Conjunto de mídias mistas inteiro, de qualquer modo de exibição (como **[!UICONTROL Cartão]** exibir ou **[!UICONTROL Coluna]** ) navegue até o Conjunto de mídias mistas. Passe o cursor sobre o ativo e toque no ícone de marca de seleção para selecioná-lo. Press **[!UICONTROL Backspace]** no teclado ou toque em **[!UICONTROL Mais]** (três pontos) na barra de ferramentas, em seguida, toque em **[!UICONTROL Excluir]**.
   >* Edite os ativos em um Conjunto de mídias mistas ao navegar até o conjunto, tocar em **[!UICONTROL Definir membros]** no painel à esquerda e, em seguida, toque no **[!UICONTROL Lápis]** ícone em um ativo individual para abrir a janela de edição.


1. Toque **[!UICONTROL Salvar]** quando terminar a edição.

   >[!NOTE]
   >
   >* Para editar os ativos em um Conjunto de mídias mistas - Navegue até o Conjunto de mídias mistas. Toque (não selecione) no conjunto para abri-lo no AEM **[!UICONTROL Definir visualização]** página. No painel à esquerda, toque no sinal de seta para baixo para abrir a lista suspensa e toque em **[!UICONTROL Definir membros]**. No **[!UICONTROL Definir membros]** página, passe o mouse sobre um ativo e toque em **[!UICONTROL Editar]** (ícone de lápis) para abrir a página de edição.
   >* Para excluir um conjunto de mídia mista inteiro - A partir de qualquer modo de exibição (como **[!UICONTROL Cartão]** exibir ou **[!UICONTROL Coluna]** ), navegue até o Conjunto de mídias mistas. Passe o mouse sobre o conjunto e toque em **[!UICONTROL Selecionar]** (ícone de marca de seleção). Press **[!UICONTROL Backspace]** no teclado ou toque em **[!UICONTROL Mais]** (linha de três pontos), em seguida, toque em **[!UICONTROL Excluir]**.


## Visualização de conjuntos de mídia mista {#previewing-mixed-media-sets}

Consulte [Visualização de ativos](previewing-assets.md) para obter detalhes sobre como visualizar Conjuntos de mídias mistas.

## Publicar conjuntos de mídia mista {#publishing-mixed-media-sets}

Consulte [Publicar ativos](publishing-dynamicmedia-assets.md) para obter detalhes sobre como publicar Conjuntos de mídias mistas.

>[!NOTE]
>
>Se o Mixed Media Det não terminar totalmente no serviço de delivery na primeira vez que você o publicar, talvez seja necessário publicar o conjunto de mídias mistas uma segunda vez.
