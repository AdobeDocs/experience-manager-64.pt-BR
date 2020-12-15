---
title: Gerencie ativos compostos e gere subativos.
description: Saiba como criar referências a ativos AEM a partir de arquivos InDesign, Adobe Illustrator e Photoshop. Saiba mais sobre como usar o recurso Visualizador de página para visualização de páginas individuais de arquivos de várias páginas, incluindo arquivos PDF, INDD, PPT, PPTX e AI.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---


# Gerenciar ativos compostos com subativos {#managing-compound-assets}

Os ativos Adobe Experience Manager (AEM) podem identificar se um arquivo carregado contém referências a ativos que já existem no repositório. Este recurso está disponível somente para formatos de arquivo suportados. Se o ativo carregado contiver referências a ativos AEM, um link bidirecional será criado entre os ativos carregados e referenciados.

Além de eliminar a redundância, a referência a ativos AEM em aplicativos Adobe Creative Cloud aumenta a colaboração e a eficiência dos usuários.

A AEM Assets suporta **referenciação bidirecional**. Você pode encontrar ativos referenciados na página de detalhes do ativo do arquivo carregado. Além disso, você pode visualização os arquivos de referência para AEM ativos na página de detalhes do ativo referenciado.

As referências são resolvidas com base no caminho, na ID do documento e na ID da instância dos ativos referenciados.

## Adicionar AEM Assets como referências no Adobe Illustrator {#refai}

Você pode fazer referência a ativos AEM existentes em um arquivo Adobe Illustrator.

1. Usando [AEM aplicativo desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html), instale o repositório AEM Assets como uma unidade em sua máquina local. Na unidade montada, navegue até o local do ativo que deseja referenciar.
1. Arraste o ativo da unidade montada para o arquivo Illustrator.
1. Salve o arquivo Illustrator na unidade montada ou [carregue](managing-assets-touch-ui.md#uploading-assets) no repositório AEM.
1. Após a conclusão do fluxo de trabalho, vá para a página de detalhes do ativo do ativo. As referências aos ativos AEM existentes estão listadas em **[!UICONTROL Dependências]** na coluna **[!UICONTROL Referências]**.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Os ativos referenciados que aparecem em **[!UICONTROL Dependências]** também podem ser referenciados por arquivos diferentes do atual. Para visualização de uma lista de arquivos de referência para um ativo, clique no ativo em **[!UICONTROL Dependências]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Clique no ícone **[!UICONTROL Propriedades da Visualização]** na barra de ferramentas. Na página de propriedades, a lista de arquivos que fazem referência ao ativo atual é exibida na coluna **[!UICONTROL Referências]** na guia **[!UICONTROL Básico]**.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adicionar ativos AEM como referências no Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Para fazer referência AEM ativos de dentro de um arquivo de InDesign, arraste AEM ativos para o arquivo de InDesign ou exporte o arquivo de InDesign como um arquivo ZIP.

Os ativos referenciados já existem no AEM Assets. Você pode extrair subativos por [configurar o servidor de InDesigns](indesign.md). Os ativos incorporados em um arquivo de InDesign são extraídos como subativos.

>[!NOTE]
>
>Se o servidor do InDesign for proxy, os arquivos do InDesign terão sua pré-visualização incorporada aos metadados do XMP. Nesse caso, a extração em miniatura não é explicitamente exigida. No entanto, se o servidor do InDesign não for proxy, as miniaturas deverão ser explicitamente extraídas para arquivos do InDesign.

### Criar referências Arrastar ativos AEM {#create-references-by-dragging-aem-assets}

Este procedimento é semelhante a [Adicionar ativos AEM como referências no Adobe Illustrator](#refai).

### Crie referências a ativos AEM exportando um arquivo ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Execute as etapas em [Criação de modelos de fluxo de trabalho](/help/sites-developing/workflows-models.md) para criar um novo fluxo de trabalho.
1. Use o recurso Pacote da Adobe InDesign para exportar o documento.
A Adobe InDesign pode exportar um documento e os ativos vinculados como um pacote. Nesse caso, a pasta exportada contém uma pasta Links que contém subativos no arquivo de InDesign.
1. Crie um arquivo ZIP e carregue-o no repositório AEM.
1. Start do fluxo de trabalho do Unarchiver.
1. Quando o fluxo de trabalho é concluído, as referências na pasta Links são automaticamente mencionadas como subativos. Para visualização de uma lista de ativos referenciados, navegue até a página de detalhes do ativo do InDesign e feche o [Painel](/help/sites-authoring/basic-handling.md#rail-selector).

## Adicionar ativos AEM como referências no Adobe Photoshop {#refps}

1. Usando um cliente WebDav, monte o AEM Assets como uma unidade.
1. Para criar referências a ativos AEM em um arquivo Photoshop, navegue até os ativos correspondentes na unidade montada usando a funcionalidade Colocar vinculado no Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Salve o arquivo Photoshop na unidade montada ou [upload](managing-assets-touch-ui.md#uploading-assets) no repositório AEM.
1. Após a conclusão do fluxo de trabalho, as referências aos ativos AEM existentes são listadas na página de detalhes do ativo.

   Para visualização dos ativos referenciados, feche o [Painel](/help/sites-authoring/basic-handling.md#rail-selector) na página de detalhes do ativo.

1. Os ativos referenciados também contêm a lista de ativos dos quais são referenciados. Para visualização de uma lista de ativos referenciados, navegue até a página de detalhes do ativo e feche o [trilho](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Os ativos em ativos compostos também podem ser referenciados com base na ID do Documento e na ID da instância. Essa funcionalidade está disponível somente nas versões Adobe Illustrator e Adobe Photoshop. Para outros, a referência é feita com base na trajetória relativa dos ativos vinculados no ativo composto principal, conforme feito em versões anteriores do AEM.

## Criar subativos {#generate-subassets}

Para os ativos suportados com formatos de várias páginas — Arquivos PDF, arquivos AI, arquivos Microsoft PowerPoint e Apple Keynote e arquivos Adobe InDesign — AEM pode gerar subativos que correspondem a cada página individual do ativo original. Esses subativos estão vinculados ao ativo *parent* e facilitam a visualização de várias páginas. Para todos os outros fins, os subativos são tratados como ativos normais em AEM.

Por padrão, a geração de conjunto de subconjuntos é desativada. Para ativar a geração de subativos, siga estas etapas:

1. Efetue login no Experience Manager como um administrador. Acesse **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. Selecione **[!UICONTROL DAM Update Asset]** e clique em **[!UICONTROL Editar]**.
1. Clique em **[!UICONTROL Alternar painel lateral]** e localize a etapa **[!UICONTROL Criar subativo]**. Adicione a etapa ao fluxo de trabalho. Clique em **[!UICONTROL Sincronizar]**.

Para gerar os subativos, execute um dos procedimentos a seguir:

* Novos ativos: O fluxo de trabalho [!UICONTROL DAM Update Assets] é executado em qualquer novo ativo carregado para AEM. Os subativos são gerados automaticamente para novos ativos de várias páginas.
* Ativos de várias páginas existentes: Execute manualmente o fluxo de trabalho [!UICONTROL DAM Update Assets] seguindo qualquer uma das etapas:

   * Selecione um ativo e clique em [!UICONTROL Linha do tempo] para abrir o painel esquerdo. Como alternativa, use o atalho de teclado `alt + 3`. Clique em [!UICONTROL Fluxo de trabalho do Start], selecione [!UICONTROL Ativo de atualização do DAM], clique em [!UICONTROL Start] e clique em [!UICONTROL Prosseguir].
   * Selecione um ativo e clique em [!UICONTROL Criar > Fluxo de trabalho] na barra de ferramentas. Na caixa de diálogo pop-up, selecione [!UICONTROL DAM Update Asset] fluxo de trabalho, clique em [!UICONTROL Start] e em [!UICONTROL Prosseguir].

Especificamente para documentos do Microsoft Word, execute o fluxo de trabalho **[!UICONTROL Documentos do DAM Parse Word]**. Ele gera um componente `cq:Page` do conteúdo do documento do Microsoft Word. As imagens extraídas do documento são referenciadas do componente `cq:Page`. Essas imagens são extraídas mesmo se a geração de subativos estiver desativada.

## Visualização de subativos {#viewing-subassets}

Os subativos são exibidos somente se os subativos forem gerados e estiverem disponíveis para o ativo multipáginas selecionado. Para visualização dos subativos gerados, abra o ativo de várias páginas. Na área superior esquerda da página, clique em ![ícone do painel esquerdo](assets/do-not-localize/aem_leftrail_contentonly.png) e clique em **[!UICONTROL Subassets]** na lista. Quando você seleciona **[!UICONTROL Subassets]** na lista. Como alternativa, use o atalho de teclado `alt + 5`.

![Visualização de subativos para um ativo de várias páginas](assets/view_subassets_simulation.gif)

## Páginas de visualização de um arquivo de várias páginas {#view-pages-of-a-multi-page-file}

É possível visualização de um arquivo de várias páginas, como PDF, INDD, PPT, PPTX e AI, usando o recurso Visualizador de páginas do AEM Assets. Abra um ativo de várias páginas e clique em **[!UICONTROL Páginas de Visualização]** no canto superior esquerdo da página. O Visualizador de página que é aberto exibe as páginas do ativo e os controles para navegar e aplicar zoom em cada página.

![Visualização e visualização de páginas de um ativo de várias páginas](assets/view_multipage_asset_fmr.gif)

Para o InDesign, você pode extrair páginas usando o servidor do InDesign. Se as pré-visualizações das páginas forem salvas durante a criação do arquivo de InDesign, o InDesign Server não será necessário para a extração da página.

As seguintes opções estão disponíveis na barra de ferramentas, no painel esquerdo e nos controles do Visualizador de páginas:

* **[!UICONTROL As]** ações da área de trabalho para abrir ou revelar um subativo específico usando AEM aplicativo da área de trabalho. Veja como [configurar as Ações da área de trabalho](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2) se você estiver usando AEM aplicativo da área de trabalho.

* **[!UICONTROL A]** opção Propriedades abre a   página Propriedades do subativo específico.

* **[!UICONTROL A opção]** Anotar permite que você anote o subativo específico. As anotações usadas em subativos separados são coletadas e exibidas juntas quando o ativo pai é aberto para exibição.

* **[!UICONTROL A opção]** Visão geral da página exibe todos os subativos simultaneamente.

* **[!UICONTROL A opção]** Linha do tempo no painel esquerdo depois de clicar em  ![Ícone do painel esquerdo ](assets/do-not-localize/aem_leftrail_contentonly.png) exibe o fluxo de atividade do arquivo.

## Práticas recomendadas e limitação {#best-practice-limitation-tips}

* A geração de subconjuntos pode consumir muitos recursos em qualquer implantação de Experience Manager. Se você estiver gerando subativos quando os ativos complexos forem carregados, adicione a etapa no fluxo de trabalho Atualizar ativo do DAM. Se você estiver gerando subativos sob demanda, crie um fluxo de trabalho separado para gerar subativos. Um fluxo de trabalho dedicado permite que você pule as outras etapas no fluxo de trabalho do DAM Update Asset e salve os recursos tecnológicos.

>[!MORELIKETHIS]
>
>* [Usar o aplicativo Adobe Experience Manager para desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

