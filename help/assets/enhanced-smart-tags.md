---
title: Tags inteligentes aprimoradas
description: Tags inteligentes aprimoradas
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Smart Tags,Search
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 14%

---

# Tags inteligentes aprimoradas {#enhanced-smart-tags}

## Visão geral das tags inteligentes aprimoradas {#overview-of-enhanced-smart-tags}

As organizações que lidam com ativos digitais cada vez mais usam um vocabulário controlado por taxonomia em metadados de ativos. Basicamente, inclui uma lista de palavras-chave que funcionários, parceiros e clientes costumam usar para consultar e pesquisar ativos digitais de uma classe específica. Marcar ativos com um vocabulário controlado por taxonomia garante que eles possam ser facilmente identificados e recuperados por pesquisas baseadas em tags.

Comparado aos vocabulários de linguagem natural, a marcação de ativos digitais com base na taxonomia comercial ajuda a alinhá-los aos negócios de uma empresa e garante que os ativos mais relevantes apareçam em pesquisas.

Por exemplo, um fabricante de carros pode marcar imagens de carros com nomes de modelos para que somente imagens relevantes sejam exibidas quando imagens de vários modelos forem pesquisadas para projetar uma campanha promocional.

Para que o Serviço de conteúdo inteligente aplique as tags certas, você deve treiná-lo para reconhecer sua taxonomia. Para treinar o serviço, primeiro prepare um conjunto de ativos e tags que descrevam melhor esses ativos. Aplique essas tags nos ativos e execute um fluxo de trabalho de treinamento para ajudar o serviço a aprender.

Depois que uma tag é treinada e pronta, o serviço agora pode aplicar essas tags em ativos por meio de um fluxo de trabalho de marcação.

Em segundo plano, o Serviço de conteúdo inteligente usa a estrutura de IA do Adobe Sensei para treinar o algoritmo de reconhecimento de imagem de acordo com sua estrutura de tags e sua taxonomia comercial. Essa inteligência de conteúdo é então usada para aplicar tags relevantes em um conjunto diferente de ativos.

O Serviço de conteúdo inteligente é um serviço em nuvem hospedado em [!DNL Adobe I/O]. Para usá-lo no Adobe Experience Manager, o administrador do sistema deve integrar a instância [!DNL Experience Manager] com [!DNL Adobe I/O].

Em resumo, estas são as principais etapas para usar o Serviço de conteúdo inteligente:

* Integração
* Revisão de ativos e tags (definição de taxonomia)
* Treinamento do Serviço de conteúdo inteligente
* Marcação automática

![fluxograma](assets/flowchart.gif)

## Pré-requisitos {#prerequisites}

Antes de usar o Serviço de conteúdo inteligente, verifique o seguinte para criar uma integração em [!DNL Adobe I/O]:

* Existência de uma Adobe ID com privilégios de administrador para a organização.
* O serviço de Conteúdo Inteligente está habilitado para sua organização.

## Integração {#onboarding}

O Serviço de conteúdo inteligente está disponível para compra como um complemento para [!DNL Experience Manager] . Após a compra, um email é enviado ao administrador da organização com um link para [!DNL Adobe I/O].

O administrador pode seguir o link para integrar o Serviço de conteúdo inteligente com [!DNL Experience Manager] . Para integrar o serviço aos ativos [!DNL Experience Manager], consulte [Configurar tags inteligentes](config-smart-tagging.md).

O processo de integração é concluído quando o administrador configura o serviço e adiciona usuários em [!DNL Experience Manager] .

## Revisão de ativos e tags {#reviewing-assets-and-tags}

Depois que estiver integrado, a primeira coisa que você deseja fazer é identificar um conjunto de tags que descreva melhor essas imagens no contexto de sua empresa.

Em seguida, revise as imagens para identificar um conjunto de imagens que melhor representam seu produto para um requisito específico de negócios. Certifique-se de que os ativos em seu conjunto preparado estejam em conformidade com [Diretrizes de treinamento do Serviço de conteúdo inteligente](smart-tags-training-guidelines.md).

Adicione os ativos a uma pasta e aplique as tags a cada ativo da página de propriedades. Em seguida, execute o workflow de treinamento nesta pasta. O conjunto preparado de ativos permite que o Serviço de conteúdo inteligente treine efetivamente mais ativos usando suas definições de taxonomia.

>[!NOTE]
>
>1. A formação é um processo irrevogável. O Adobe recomenda que você analise as tags no conjunto de ativos preparado bem antes de treinar o Serviço de conteúdo inteligente nas tags.
>1. Leia [Diretrizes de treinamento do Serviço de conteúdo inteligente](smart-tags-training-guidelines.md) antes de iniciar o treinamento para qualquer tag.
>1. Ao treinar o Serviço de conteúdo inteligente pela primeira vez, o Adobe recomenda treiná-lo em pelo menos duas tags distintas.

>


## Treinamento do Serviço de conteúdo inteligente {#training-the-smart-content-service}

Para que o Serviço de conteúdo inteligente reconheça sua taxonomia comercial, execute-a em um conjunto de ativos que já incluem tags relevantes para sua empresa. Após o treinamento, o serviço pode aplicar a mesma taxonomia em um conjunto semelhante de ativos.

Você pode treinar o serviço várias vezes para melhorar sua capacidade de aplicar tags relevantes. Após cada ciclo de treinamento, execute um fluxo de trabalho de marcação e verifique se os ativos estão marcados adequadamente.

Você pode treinar o Serviço de conteúdo inteligente periodicamente ou de acordo com requisitos.

>[!NOTE]
>
>O fluxo de trabalho de treinamento é executado somente em pastas.

### Formação contínua {#periodic-training}

Você pode habilitar o Serviço de conteúdo inteligente para treinar periodicamente nos ativos e tags associadas em uma pasta. Abra a página de propriedades da pasta de ativos, selecione **[!UICONTROL Ativar tags inteligentes]** na guia **[!UICONTROL Detalhes]** e salve as alterações.

![enable_smart_tags](assets/enable_smart_tags.png)

Depois que essa opção é selecionada para uma pasta, [!DNL Experience Manager] executa um fluxo de trabalho de treinamento automaticamente para treinar o Serviço de conteúdo inteligente nos ativos da pasta e suas tags. Por padrão, o fluxo de trabalho de treinamento é executado semanalmente às 12h30 dos sábados.

### Treinamento sob demanda {#on-demand-training}

Você pode treinar o Serviço de conteúdo inteligente sempre que necessário no console Fluxo de trabalho.

1. Toque/clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. Na página **[!UICONTROL Modelos de fluxo de trabalho]**, selecione o fluxo de trabalho **[!UICONTROL Treinamento de tags inteligentes]** e toque/clique em **[!UICONTROL Iniciar fluxo de trabalho]** na barra de ferramentas.
1. Na caixa de diálogo **[!UICONTROL Executar fluxo de trabalho]**, navegue até a pasta de carga que inclui os ativos marcados para treinar o serviço.
1. Especifique um título para o fluxo de trabalho e adicione um comentário. Em seguida, toque/clique em **[!UICONTROL Executar]**. Os ativos e tags são enviados para treinamento.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Depois que os ativos em uma pasta forem processados para treinamento, somente os ativos modificados serão processados em ciclos de treinamento subsequentes.

### Exibição de relatórios de treinamento {#viewing-training-reports}

Para verificar se o Serviço de conteúdo inteligente é treinado em suas tags no conjunto de ativos de treinamento, analise o relatório do fluxo de trabalho de treinamento no console Relatórios .

1. Toque/clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas > Ativos > Relatórios]**.
1. Na página **[!UICONTROL Relatórios de ativos]**, toque/clique em **[!UICONTROL Criar]**.
1. Selecione o relatório **[!UICONTROL Treinamento de tags inteligentes]** e toque/clique em **[!UICONTROL Avançar]** na barra de ferramentas.
1. Especifique um título e uma descrição para o relatório. Em **[!UICONTROL Agendar relatório]**, deixe a opção **[!UICONTROL Agora]** selecionada. Se desejar agendar o relatório para posteriormente, selecione **[!UICONTROL Posteriormente]** e especifique uma data e hora. Em seguida, toque/clique em **[!UICONTROL Criar]** na barra de ferramentas.
1. Na página **[!UICONTROL Relatórios de ativos]**, selecione o relatório gerado. Para exibir o relatório, toque/clique no ícone **[!UICONTROL Exibir]** na barra de ferramentas.
1. Revise os detalhes do relatório.

   O relatório exibe o status do treinamento das tags que você treinou. A cor verde na coluna **[!UICONTROL Status de treinamento]** indica que o Serviço de conteúdo inteligente foi treinado para a tag. A cor amarela indica que o serviço não é completamente treinado para uma tag específica. Nesse caso, adicione mais imagens com a tag específica e execute o fluxo de trabalho de treinamento para treinar o serviço completamente na tag.

   Se você não vir suas tags neste relatório, execute o fluxo de trabalho de treinamento novamente para essas tags.

1. Para baixar o relatório, selecione-o na lista e toque/clique no ícone **[!UICONTROL Download]** na barra de ferramentas. O relatório é baixado como um arquivo Excel.

## Marcar ativos automaticamente {#tagging-assets-automatically}

Depois de ter treinado o Serviço de conteúdo inteligente, você pode acionar o fluxo de trabalho de marcação para aplicar automaticamente as tags apropriadas em um conjunto diferente de ativos semelhantes.

Você pode executar o fluxo de trabalho de marcação periodicamente ou sempre que necessário.

>[!NOTE]
>
>O fluxo de trabalho de marcação é executado em ativos e pastas.

### Marcação periódica {#periodic-tagging}

Você pode permitir que o Serviço de conteúdo inteligente marque periodicamente ativos em uma pasta. Abra a página de propriedades da pasta de ativos, selecione **[!UICONTROL Ativar tags inteligentes]** na guia **[!UICONTROL Detalhes]** e salve as alterações.

Quando essa opção é selecionada para uma pasta, o Serviço de conteúdo inteligente insere tags automaticamente nos ativos da pasta. Por padrão, o fluxo de trabalho de marcação é executado todos os dias às 12:00 AM.

### Marcação sob demanda {#on-demand-tagging}

Você pode acionar o fluxo de trabalho de marcação a partir dos itens a seguir para marcar seus ativos instantaneamente:

* Console de fluxo de trabalho
* Linha do tempo

>[!NOTE]
>
>Se você executar o fluxo de trabalho de marcação na linha do tempo, poderá aplicar tags em no máximo 15 ativos de cada vez.

#### Marcar ativos no console Fluxo de trabalho {#tagging-assets-from-the-workflow-console}

1. Toque/clique no logotipo [!DNL Experience Manager] e acesse **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. Na página **[!UICONTROL Modelos de fluxo]** de trabalho, selecione o fluxo de trabalho **[!UICONTROL Ativos de tags inteligentes do DAM]** e toque/clique em **[!UICONTROL Iniciar fluxo de trabalho]** na barra de ferramentas.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Na caixa de diálogo **[!UICONTROL Executar fluxo de trabalho]**, navegue até a pasta de carga que contém ativos nos quais você deseja aplicar suas tags automaticamente.
1. Especifique um título para o fluxo de trabalho e um comentário opcional. Em seguida, toque/clique em **[!UICONTROL Executar]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navegue até a pasta de ativos e revise as tags para verificar se o Serviço de conteúdo inteligente marcou seus ativos corretamente. Para obter detalhes, consulte [Gerenciamento de tags inteligentes](managing-smart-tags.md).

#### Marcar ativos na linha do tempo {#tagging-assets-from-the-timeline}

1. Na interface do usuário do Assets, selecione a pasta que contém ativos ou ativos específicos aos quais deseja aplicar tags inteligentes.
1. Toque/clique no ícone de Navegação global e abra a linha do tempo.
1. Toque/clique na seta na parte inferior e toque/clique em **[!UICONTROL Iniciar fluxo de trabalho]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecione o fluxo de trabalho **[!UICONTROL Ativos de tags inteligentes do DAM]** e especifique um título para o fluxo de trabalho.
1. Toque/clique em **[!UICONTROL Iniciar]**. O fluxo de trabalho aplica suas tags em ativos. Navegue até a pasta de ativos e revise as tags para verificar se o Serviço de conteúdo inteligente marcou seus ativos corretamente. Para obter detalhes, consulte [Gerenciamento de tags inteligentes](managing-smart-tags.md).

>[!NOTE]
>
>Nos ciclos de marcação subsequentes, somente os ativos modificados são marcados novamente com tags recém-treinadas.
>
>No entanto, mesmo ativos inalterados são marcados se a diferença entre os últimos e os atuais ciclos de marcação do fluxo de trabalho de marcação exceder 24 horas.
>
>Para workflows de marcação periódica, os ativos inalterados são marcados quando a lacuna excede 6 meses.
