---
title: Perfis para processar metadados, imagens e vídeos
description: Um perfil com um conjunto de regras sobre as opções a serem aplicadas a ativos carregados em uma pasta. Especifique o perfil de metadados e o perfil de codificação de vídeo que serão aplicados aos ativos de vídeo carregados. Para ativos de imagem, você também pode especificar qual perfil de imagem aplicar aos ativos de imagem para que eles sejam cortados corretamente.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
feature: Workflow,Asset Management,Renditions
role: User,Admin
exl-id: 78d76b4f-a46c-4ffc-b772-ed925eb8e34c
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 2%

---

# Sobre perfis para processamento de metadados, imagens e vídeos {#profiles-for-processing-metadata-images-and-videos}

Um perfil é uma receita para quais opções se aplicam a ativos que são carregados em uma pasta. Por exemplo, você pode especificar qual perfil de metadados e perfil de codificação de vídeo aplicar aos ativos de vídeo você faz upload. Ou qual perfil de imagem aplicar aos ativos de imagem para cortá-los corretamente.

Essas regras podem incluir adição de metadados, recorte inteligente de imagens ou estabelecimento de perfis de codificação de vídeo. No AEM, você pode criar três tipos de perfis, que são abordados detalhadamente nos seguintes links:

* [Perfis de metadados](metadata-profiles.md)
* [Perfis de imagem](image-profiles.md)
* [Perfis de vídeo](video-profiles.md)

Você deve ter direitos de Administrador para criar, editar e excluir metadados, imagens ou perfis de vídeo.

Após criar seus metadados, imagem ou perfil de vídeo, atribua-os a uma ou mais pastas que usa como destino para os ativos recém-carregados.

Um conceito importante sobre o uso de perfis em [!DNL Experience Manager] Assets é que eles são atribuídos a pastas. Em um perfil estão as configurações no formato de perfis de metadados, juntamente com perfis de vídeo ou perfis de imagem. Essas configurações processam o conteúdo de uma pasta junto com qualquer uma de suas subpastas. Portanto, a forma como você nomeia arquivos e pastas, como organiza subpastas e como manipula os arquivos nessas pastas tem um impacto significativo na forma como esses ativos são processados por um perfil. Ao usar estratégias consistentes e apropriadas de nomeação de arquivos e pastas, juntamente com uma boa prática de metadados, você pode aproveitar ao máximo sua coleção de ativos digitais e garantir que os arquivos corretos sejam processados pelo perfil correto. Para obter um exemplo, consulte [organizar ativos usando pastas](organize-assets.md#organize-using-folders).

>[!NOTE]
>
>Os ativos que você move de uma pasta para outra não são reprocessados. Por exemplo, suponha que você tenha a Pasta 1 que tem o perfil A atribuído a ela e a Pasta 2 que tem o perfil B atribuído a ela. Se você mover ativos da Pasta 1 para a Pasta 2, os ativos movidos manterão o processamento original da Pasta 1.
>
>O mesmo é verdadeiro mesmo quando você move ativos entre duas pastas que têm o mesmo perfil atribuído a ele.

## Reprocessando ativos em uma pasta {#reprocessing-assets}

>[!NOTE]
>
>Aplica-se a *Dynamic Media - Modo Scene7* somente em [!DNL Experience Manager] 6.4.7.0 ou posterior.

Você pode reprocessar ativos em uma pasta que já tenha um perfil de processamento existente que você alterou posteriormente.

Por exemplo, suponha que você criou um perfil de Imagem e o atribuiu a uma pasta. Qualquer ativo de imagem carregado na pasta tinha automaticamente o perfil de imagem aplicado aos ativos. No entanto, posteriormente você decide adicionar uma nova proporção de recorte inteligente ao perfil. Agora, em vez de selecionar e fazer upload novamente dos ativos para a pasta, basta executar o *Scene7: Fluxo de trabalho Reprocessar ativos* .

Você pode executar o fluxo de trabalho de reprocessamento em um ativo para o qual o processamento falhou na primeira vez. Dessa forma, mesmo que você não tenha editado um perfil de processamento ou aplicado um perfil de processamento, ainda poderá executar o fluxo de trabalho de reprocessamento em uma pasta de ativos a qualquer momento.

Opcionalmente, é possível ajustar o tamanho do lote do workflow de reprocessamento a partir de um padrão de 50 ativos até 1000 ativos. Ao executar o _Scene7: Fluxo de trabalho Reprocessar ativos_ em uma pasta, os ativos são agrupados em lotes e, em seguida, enviados ao servidor da Dynamic Media para processamento. Após o processamento, os metadados de cada ativo em todo o conjunto de lotes são atualizados no AEM. Se o tamanho do lote for muito grande, pode ocorrer um atraso no processamento. Ou, se o tamanho do lote for muito pequeno, pode causar muitas viagens de ida e volta para o servidor do Dynamic Media.

Consulte [Ajustar o tamanho do lote do workflow de reprocessamento](#adjusting-load).

>[!NOTE]
>
>Se estiver executando uma migração em massa de ativos do Dynamic Media Classic para o AEM, você deverá habilitar o agente de replicação de Migração no servidor do Dynamic Media. Quando a migração estiver concluída, desative o agente. O agente de publicação de Migração deve estar desabilitado no servidor do Dynamic Media para que o fluxo de trabalho de Reprocessamento funcione como esperado.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**Para reprocessar ativos em uma pasta**:

1. No AEM, na página Ativos , navegue até uma pasta de ativos que tem um perfil de processamento atribuído a ela e para a qual deseja aplicar o **Scene7: Reprocessar o fluxo de trabalho do Asset**,

   As pastas que têm um perfil de processamento já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta na Exibição de cartão.

1. Selecione uma pasta.

   * O workflow considera todos os arquivos na pasta selecionada, de forma recursiva.
   * Se houver uma ou mais subpastas com ativos na pasta selecionada principal, o fluxo de trabalho reprocessará cada ativo na hierarquia de pastas.
   * Como prática recomendada, evite executar esse workflow em uma hierarquia de pastas que tenha mais de 1000 ativos.

1. Próximo ao canto superior esquerdo da página, na lista suspensa, clique em **[!UICONTROL Linha do tempo]**.
1. Próximo ao canto inferior esquerdo da página, à direita do campo Comentário , clique no ícone do carrinho ( **^** ) .

   ![Reprocessar fluxo de trabalho de ativos 1](/help/assets/assets/reprocess-assets1.png)

1. Clique em **[!UICONTROL Iniciar fluxo de trabalho]**.
1. Na lista suspensa **[!UICONTROL Iniciar fluxo de trabalho]** , escolha **[!UICONTROL Scene7: Reprocessar Ativos]**.
1. (Opcional) No campo de texto **Enter title of workflow** , digite um nome para o workflow. Você pode usar o nome para fazer referência à instância do workflow, se necessário.

   ![Reprocessar ativos 2](/help/assets/assets/reprocess-assets2.png)

1. Clique em **[!UICONTROL Iniciar]** e em **[!UICONTROL Confirmar]**.

   Para monitorar o workflow ou verificar seu progresso, na página principal do console [!DNL Experience Manager], clique em **[!UICONTROL Tools > Workflow]**. Na página Instâncias de fluxo de trabalho , selecione um fluxo de trabalho. Na barra de menus, clique em **[!UICONTROL Abrir Histórico]**. Você também pode encerrar, suspender ou renomear um fluxo de trabalho selecionado na mesma página Instâncias de fluxo de trabalho .

### Ajustar o tamanho do lote do workflow de reprocessamento {#adjusting-load}

(Opcional) O tamanho padrão do lote no fluxo de trabalho de reprocessamento é de 50 ativos por trabalho. Esse tamanho ideal do lote é regulado pelo tamanho médio do ativo e pelos tipos MIME de ativos em que o reprocessamento é executado. Um valor mais alto significa que você terá muitos arquivos em um único trabalho de reprocessamento. Assim, o banner de processamento permanece em [!DNL Experience Manager] ativos por um tempo maior. No entanto, se o tamanho médio do arquivo for de 1 MB ou menos Adobe, a recomenda que você aumente o valor para várias centenas, mas nunca mais que 1000. Se o tamanho médio do arquivo for grande, centenas de megabytes-Adobe, recomenda-se reduzir o tamanho do lote para até 10.

**Como opção, ajuste o tamanho do lote do workflow de reprocessamento**

1. No Experience Manager, toque em **[!UICONTROL Adobe Experience Manager]** para acessar o console de navegação global e, em seguida, toque no ícone **[!UICONTROL Ferramentas]** (martelo) > **[!UICONTROL Fluxo de trabalho > Modelos]**.
1. Na página Modelos de fluxo de trabalho , na Exibição de cartão ou Exibição de lista, selecione **[!UICONTROL Scene7: Reprocessar Ativos]**.

   ![Página Modelos de fluxo de trabalho com o Scene7: Fluxo de trabalho Reprocessar ativos selecionado na Exibição de cartão](/help/assets/assets-dm/reprocess-assets7.png)

1. Na barra de ferramentas, clique em **[!UICONTROL Editar]**. Uma nova guia do navegador abre o Scene7: Página de modelo de fluxo de trabalho Reprocessar ativos .
1. Na Scene7: Reprocessar página do fluxo de trabalho Ativos , próximo ao canto superior direito, toque em **[!UICONTROL Editar]** para &quot;desbloquear&quot; o fluxo de trabalho.
1. No fluxo de trabalho, selecione o componente Upload em lote do Scene7 para abrir a barra de ferramentas e toque em **[!UICONTROL Configurar]** na barra de ferramentas.

   ![Componente de upload em lote do Scene7](/help/assets/assets-dm/reprocess-assets8.png)

1. Na caixa de diálogo **[!UICONTROL Upload em lote para propriedades da etapa do Scene7]**, defina o seguinte:
   * Nos campos de texto **[!UICONTROL Title]** e **[!UICONTROL Description]**, insira um novo título e descrição para a tarefa, se desejado.
   * Selecione **[!UICONTROL Handler Advance]** se o manipulador avançar para a próxima etapa.
   * No campo **[!UICONTROL Timeout]**, digite o tempo limite do processo externo (segundos).
   * No campo **[!UICONTROL Period]**, insira um intervalo de sondagem (segundos) para testar a conclusão do processo externo.
   * No **[!UICONTROL Campo de lote]**, insira o número máximo de ativos (50-1000) a serem processados em um trabalho de upload de processamento em lote do servidor Dynamic Media.
   * Selecione **[!UICONTROL Avançar no tempo limite]** se desejar avançar quando o tempo limite for atingido. Desmarque se deseja continuar com a caixa de entrada quando o tempo limite for atingido.

   ![Caixa de diálogo Propriedades](/help/assets/assets-dm/reprocess-assets3.png)

1. No canto superior direito da caixa de diálogo **[!UICONTROL Carregar em lote para propriedades da etapa do Scene7]**, toque em **[!UICONTROL Concluído]**.

1. No canto superior direito da Scene7: Reprocessar página de modelo de fluxo de trabalho do Assets, toque em **[!UICONTROL Sincronizar]**. Quando você vê **[!UICONTROL Sincronizado]**, o modelo de tempo de execução do workflow é sincronizado e pronto para reprocessar o ativo em uma pasta.

   ![Sincronização do modelo de fluxo de trabalho](/help/assets/assets-dm/reprocess-assets1.png)

1. Feche a guia do navegador que mostra a Scene7: Reprocessar modelo de fluxo de trabalho do Assets.

<!-- 1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main [!DNL Experience Manager] console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model. -->
