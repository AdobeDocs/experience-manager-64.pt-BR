---
title: Ativos relacionados
description: Saiba como relacionar ativos que compartilham determinados atributos comuns. Também é possível usar o recurso para criar relacionamentos de origem/derivados entre ativos.
contentOwner: AG
feature: Asset Management,Collaboration
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 1%

---


# Ativos relacionados {#related-assets}

Os ativos Adobe Experience Manager (AEM) permitem relacionar manualmente os ativos com base nas necessidades de sua organização usando o recurso Ativos relacionados . Por exemplo, você pode relacionar um arquivo de licença com um ativo ou uma imagem/vídeo em um tópico semelhante. Você pode relacionar ativos que compartilham determinados atributos comuns. Também é possível usar o recurso para criar relacionamentos de origem/derivados entre ativos. Por exemplo, se você tiver um arquivo PDF gerado a partir de um arquivo INDD, poderá relacionar o arquivo PDF ao seu arquivo INDD de origem.

Dessa forma, você tem a flexibilidade de compartilhar um arquivo de baixa resolução (por exemplo, PDF/JPG) para fornecedores/agências e disponibilizar o arquivo de alta resolução (por exemplo, INDD) somente mediante solicitação.

## Ativos relacionados {#relating-assets}

1. Na interface do Assets, abra a página de propriedades de um ativo que deseja relacionar.

   ![chlimage_1-272](assets/chlimage_1-272.png)

   Como alternativa, selecione o ativo na exibição em lista.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Você também pode selecionar o ativo de uma coleção.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Para relacionar outro ativo com o ativo selecionado, clique/toque no ícone **[!UICONTROL Relate]** na barra de ferramentas.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Faça uma das seguintes opções:

   * Para relacionar o arquivo de origem do ativo, selecione **[!UICONTROL Source]** na lista.
   * Para relacionar um arquivo derivado, selecione **[!UICONTROL Derivado]** na lista.
   * Para criar uma relação bidirecional entre os ativos, selecione **[!UICONTROL Others]** na lista.

   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Na tela **[!UICONTROL Selecionar ativo]**, navegue até o local do ativo que deseja relacionar e selecione-o.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Clique/toque no ícone **[!UICONTROL Confirmar]**.
1. Clique/toque em **[!UICONTROL OK]** para fechar a caixa de diálogo. Dependendo da escolha do relacionamento na etapa 3, o ativo relacionado é listado em uma categoria apropriada na seção **[!UICONTROL Relacionado]**. Por exemplo, se o ativo relacionado for o arquivo de origem do ativo atual, ele será listado em **[!UICONTROL Source]**.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Para desrelacionar um ativo, clique/toque no ícone **[!UICONTROL Não Relacionado]** na barra de ferramentas.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Selecione o(s) ativo(s) que deseja desrelacionar da caixa de diálogo **[!UICONTROL Remover relações]** e clique/toque em **[!UICONTROL Não relacionar]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Clique/toque em **[!UICONTROL OK]** para fechar a caixa de diálogo. Os ativos para os quais você removeu relações são excluídos da lista de ativos relacionados na seção **[!UICONTROL Relacionado]**.

## Tradução de ativos relacionados {#translating-related-assets}

Criar relacionamentos de origem/derivados entre ativos usando o recurso Ativos relacionados também é útil em fluxos de trabalho de tradução. Quando você executa um fluxo de trabalho de tradução em um ativo derivado, o AEM Assets busca automaticamente qualquer ativo que o arquivo de origem faça referência e o inclui para tradução. Dessa forma, o ativo referenciado pelo ativo de origem é convertido junto com a fonte e os ativos derivados. Por exemplo, considere um cenário em que a cópia em inglês inclua um ativo derivado e o arquivo de origem, como mostrado.

![chlimage_1-281](assets/chlimage_1-281.png)

Se o arquivo de origem estiver relacionado a outro ativo, o AEM Assets buscará o ativo referenciado e o incluirá na tradução.

![chlimage_1-282](assets/chlimage_1-282.png)

1. Traduza os ativos na pasta de origem para um idioma de destino seguindo as etapas em [Criar um novo projeto de tradução](translation-projects.md#create-a-new-translation-project). Por exemplo, nesse caso, traduza os ativos para francês.
1. Na página Projetos , abra a pasta de tradução.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Clique/toque no bloco do projeto para abrir a página de detalhes.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Clique/toque nas reticências abaixo do cartão Tarefa de tradução para exibir o status da tradução.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Selecione o ativo e clique/toque em **[!UICONTROL Revelar no Assets]** na barra de ferramentas para exibir o status de tradução do ativo.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Para verificar se os ativos relacionados à origem foram traduzidos, clique/toque no ativo de origem.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Selecione o ativo que está relacionado à origem e clique/toque em **[!UICONTROL Revelar no Assets]**. O ativo relacionado convertido é exibido.

   ![chlimage_1-288](assets/chlimage_1-288.png)
