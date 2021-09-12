---
title: Gerencie ativos compostos e gere subativos.
description: Saiba como criar referências a ativos AEM a partir de arquivos do InDesign, Adobe Illustrator e Photoshop. Saiba também como usar o recurso Visualizador de página para exibir páginas individuais de arquivos de várias páginas, incluindo arquivos PDF, INDD, PPT, PPTX e AI.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '1408'
ht-degree: 0%

---

# Gerenciar ativos compostos com subativos {#managing-compound-assets}

Os ativos Adobe Experience Manager (AEM) podem identificar se um arquivo carregado contém referências a ativos que já existem no repositório. Esse recurso está disponível somente para formatos de arquivo compatíveis. Se o ativo carregado contiver referências a ativos AEM, um link bidirecional será criado entre os ativos carregados e referenciados.

Além de eliminar a redundância, a referência a ativos AEM em aplicativos Adobe Creative Cloud aumenta a colaboração e a eficiência e produtividade dos usuários.

O AEM Assets suporta **referência bidirecional**. Você pode encontrar ativos referenciados na página de detalhes do ativo do arquivo carregado. Além disso, é possível exibir os arquivos de referência para AEM ativos na página de detalhes do ativo do ativo referenciado.

As referências são resolvidas com base no caminho, na ID do documento e na ID da instância dos ativos referenciados.

## Adobe Illustrator: Adicionar ativos como referências {#refai}

Você pode fazer referência a ativos AEM existentes em um arquivo Adobe Illustrator.

1. Usando [AEM aplicativo de desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=pt-BR), monte o repositório AEM Assets como uma unidade em sua máquina local. Na unidade montada, navegue até o local do ativo que deseja referenciar.
1. Arraste o ativo da unidade montada para o arquivo Illustrator.
1. Salve o arquivo Illustrator na unidade montada ou [upload](managing-assets-touch-ui.md#uploading-assets) no repositório AEM.
1. Depois que o fluxo de trabalho for concluído, acesse a página de detalhes do ativo. As referências a ativos AEM existentes são listadas em **[!UICONTROL Dependências]** na coluna **[!UICONTROL Referências]**.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Os ativos referenciados que aparecem em **[!UICONTROL Dependências]** também podem ser referenciados por arquivos diferentes do atual. Para exibir uma lista de arquivos de referência para um ativo, clique no ativo em **[!UICONTROL Dependências]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Clique no ícone **[!UICONTROL Exibir propriedades]** na barra de ferramentas. Na página de propriedades, a lista de arquivos que fazem referência ao ativo atual é exibida na coluna **[!UICONTROL Referências]** na guia **[!UICONTROL Básico]**.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: Adicionar ativos como referências {#add-aem-assets-as-references-in-adobe-indesign}

Para fazer referência AEM ativos de um arquivo de InDesign, arraste AEM ativos para o arquivo de InDesign ou exporte o arquivo de InDesign como um arquivo ZIP.

Os ativos referenciados já existem no AEM Assets. Você pode extrair subativos usando [configurar o servidor do InDesign](indesign.md). Os ativos incorporados em um arquivo do InDesign são extraídos como subativos.

>[!NOTE]
>
>Se o servidor do InDesign for proxy, os arquivos do InDesign terão a visualização incorporada aos metadados XMP. Nesse caso, a extração em miniatura não é explicitamente necessária. No entanto, se o servidor do InDesign não tiver proxy, as miniaturas deverão ser extraídas explicitamente para os arquivos do InDesign.

Quando um arquivo INDD é carregado, as referências são buscadas consultando ativos com as propriedades `xmpMM:InstanceID` e `xmpMM:DocumentID` no repositório.

### Criar referências arrastando ativos {#create-references-by-dragging-aem-assets}

Este procedimento é semelhante a [Adicionar ativos como referências no Adobe Illustrator](#refai).

### Criar referências a ativos exportando um arquivo ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Execute as etapas em [Criação de modelos de fluxo de trabalho](/help/sites-developing/workflows-models.md) para criar um novo fluxo de trabalho.
1. Use o recurso [Pacote do Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) para exportar o documento. A Adobe InDesign pode exportar um documento e os ativos vinculados como um pacote. Nesse caso, a pasta exportada contém uma pasta `Links` que contém subativos no arquivo de InDesign. A pasta `Links` está presente na mesma pasta que o arquivo INDD.
1. Crie um arquivo ZIP e faça upload dele para o repositório AEM.
1. Inicie o fluxo de trabalho do Unarchiver .
1. Quando o fluxo de trabalho é concluído, as referências na pasta Links são automaticamente referenciadas como subativos. Para exibir uma lista dos ativos referenciados, navegue até a página de detalhes do ativo do InDesign e feche o [Trilho](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: Adicionar ativos como referências {#refps}

1. Usando um cliente WebDav, monte o AEM Assets como uma unidade.
1. Para criar referências a ativos AEM em um arquivo Photoshop, navegue até os ativos correspondentes na unidade montada usando a funcionalidade Colocar vinculado no Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Salve o arquivo Photoshop na unidade montada ou [upload](managing-assets-touch-ui.md#uploading-assets) no repositório AEM.
1. Após a conclusão do fluxo de trabalho, as referências aos ativos AEM existentes são listadas na página de detalhes do ativo.

   Para exibir os ativos referenciados, feche o [Trilho](/help/sites-authoring/basic-handling.md#rail-selector) na página de detalhes do ativo.

1. Os ativos referenciados também contêm a lista de ativos dos quais são referenciados. Para exibir uma lista de ativos referenciados, navegue até a página de detalhes do ativo e feche o [trilho](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Os ativos em ativos compostos também podem ser referenciados com base na ID do documento e na ID da instância. Essa funcionalidade está disponível somente nas versões Adobe Illustrator e Adobe Photoshop. Para outros, a referência é feita com base no caminho relativo de ativos vinculados no ativo composto principal, conforme feito em versões anteriores do AEM.

## Criar subativos {#generate-subassets}

Para os ativos suportados com formatos de várias páginas — arquivos PDF, arquivos AI, arquivos Microsoft PowerPoint e Apple Keynote e arquivos Adobe InDesign — AEM podem gerar subativos que correspondem a cada página individual do ativo original. Esses subativos estão vinculados ao ativo *principal* e facilitam a visualização de várias páginas. Para todos os outros fins, os ativos secundários são tratados como ativos normais em AEM.

A geração de subconjunto é desabilitada por padrão. Para ativar a geração de subativos, siga estas etapas:

1. Faça o login no Experience Manager como administrador. Acesse **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. Selecione **[!UICONTROL Ativo de atualização do DAM]** e clique em **[!UICONTROL Editar]**.
1. Clique em **[!UICONTROL Alternar painel lateral]** e localize a etapa **[!UICONTROL Criar subativo]**. Adicione a etapa ao workflow. Clique em **[!UICONTROL Sincronizar]**.

Para gerar os subativos, siga um destes procedimentos:

* Novos ativos: O workflow [!UICONTROL Ativos de atualização do DAM] é executado em qualquer novo ativo que seja carregado no AEM. Os subativos são gerados automaticamente para novos ativos de várias páginas.
* Ativos de várias páginas existentes: Execute manualmente o fluxo de trabalho [!UICONTROL Atualizar ativos do DAM] seguindo uma das etapas:

   * Selecione um ativo e clique em [!UICONTROL Linha do tempo] para abrir o painel esquerdo. Como alternativa, use o atalho de teclado `alt + 3`. Clique em [!UICONTROL Iniciar Fluxo de Trabalho], selecione [!UICONTROL Ativo de Atualização DAM], clique em [!UICONTROL Iniciar] e clique em [!UICONTROL Continuar].
   * Selecione um ativo e clique em [!UICONTROL Create > Workflow] na barra de ferramentas. Na caixa de diálogo pop-up, selecione [!UICONTROL DAM Update Asset] fluxo de trabalho, clique em [!UICONTROL Iniciar] e clique em [!UICONTROL Continuar].

Especificamente para documentos do Microsoft Word, execute o workflow **[!UICONTROL Documentos do DAM Parse Word]**. Ele gera um componente `cq:Page` do conteúdo do documento do Microsoft Word. As imagens extraídas do documento são referenciadas do componente `cq:Page`. Essas imagens são extraídas mesmo se a geração de subativos estiver desativada.

## Exibir subativos {#viewing-subassets}

Os subativos são exibidos somente se os subativos forem gerados e estiverem disponíveis para o ativo de várias páginas selecionado. Para exibir os subativos gerados, abra o ativo de várias páginas. Na área superior esquerda da página, clique em ![Ícone do painel à esquerda](assets/do-not-localize/aem_leftrail_contentonly.png) e clique em **[!UICONTROL Subassets]** na lista. Ao selecionar **[!UICONTROL Subassets]** na lista. Como alternativa, use o atalho de teclado `alt + 5`.

![Exibir subativos para um ativo de várias páginas](assets/view_subassets_simulation.gif)

## Exibir páginas de um arquivo de várias páginas {#view-pages-of-a-multi-page-file}

É possível visualizar um arquivo de várias páginas, como PDF, INDD, PPT, PPTX e arquivo AI, usando o recurso Visualizador de página do AEM Assets. Abra um ativo de várias páginas e clique em **[!UICONTROL Exibir páginas]** no canto superior esquerdo da página. O Visualizador de página que é aberto exibe as páginas do ativo e os controles para navegar e aplicar zoom a cada página.

![Exibir e ver páginas de um ativo de várias páginas](assets/view_multipage_asset_fmr.gif)

Para o InDesign, você pode extrair páginas usando o servidor do InDesign. Se as visualizações de páginas forem salvas durante a criação do arquivo de InDesign, o InDesign Server não será necessário para a extração de página.

As seguintes opções estão disponíveis na barra de ferramentas, no painel à esquerda e nos controles do Visualizador de páginas:

* **[!UICONTROL As]** ações da área de trabalho para abrir ou revelar um subativo específico usando AEM aplicativo da área de trabalho. Consulte como [configurar as Ações da Área de Trabalho](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) se estiver usando AEM aplicativo de área de trabalho.

* **** A opção Propriedades abre a   página Propriedades do subativo específico.

* **** A opção Anotar permite anotar o subativo específico. As anotações usadas em subativos separados são coletadas e exibidas juntas quando o ativo principal é aberto para exibição.

* **[!UICONTROL A opção]** Visão geral da página exibe todos os subativos simultaneamente.

* **** A opção Linha do tempo no painel esquerdo depois de clicar no ícone  ![do painel esquerdo ](assets/do-not-localize/aem_leftrail_contentonly.png) exibe o fluxo de atividade do arquivo.

## Práticas recomendadas e limitação {#best-practice-limitation-tips}

* A geração de subconjunto pode consumir muitos recursos em qualquer implantação de Experience Manager. Se você estiver gerando subativos quando ativos complexos forem carregados, adicione a etapa no fluxo de trabalho Ativo de atualização DAM . Se você estiver gerando subativos sob demanda, crie um workflow separado para gerar subativos. Um fluxo de trabalho dedicado permite ignorar as outras etapas no fluxo de trabalho Ativo de atualização DAM e salvar recursos computacionais.

>[!MORELIKETHIS]
>
>* [Usar o aplicativo de desktop do Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

