---
title: Gerenciar ativos de vídeo
description: Saiba como carregar, pré-visualização, anotar e publicar ativos de vídeo.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
translation-type: tm+mt
source-git-commit: 2a24d7b9232f39d47d79d995251a14beb0c0f666
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 8%

---


# Gerenciar ativos de vídeo {#managing-video-assets}

Saiba como gerenciar e editar os ativos de vídeo nos ativos Adobe Experience Manager (AEM). Além disso, se você estiver licenciado para usar o Dynamic Media, consulte a documentação [do](video.md)Dynamic Media Video.

## Fazer upload e pré-visualização de ativos de vídeo {#uploading-and-previewing-video-assets}

A AEM Assets gera pré-visualizações para ativos de vídeo com a extensão MP4. Se o formato do ativo não for MP4, instale o FFmpeg pack para gerar uma pré-visualização. FFmpeg cria representações de vídeo do tipo OGG e MP4. Você pode pré-visualização essas execuções na interface do usuário do AEM Assets.

1. Na pasta ou subpastas Ativos digitais, navegue até o local onde deseja adicionar ativos digitais.
1. Para carregar o ativo, clique ou toque em **[!UICONTROL Criar]** na barra de ferramentas e escolha **[!UICONTROL Arquivos]**. Como alternativa, solte-o diretamente na área de ativos. Consulte [Fazer upload de ativos](managing-assets-touch-ui.md#uploading-assets) para obter detalhes sobre a operação de upload.
1. Para pré-visualização de um vídeo na visualização da placa, toque no botão **[!UICONTROL Reproduzir]** no ativo de vídeo.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Você pode pausar ou reproduzir vídeo apenas na visualização **[!UICONTROL do cartão]** . O botão Reproduzir/Pausar não está disponível na visualização da **[!UICONTROL Lista]** .

1. Toque no ícone **[!UICONTROL Editar]** no cartão para pré-visualização do vídeo na visualização **[!UICONTROL Detalhes]** .

   O vídeo é reproduzido no player de vídeo nativo do navegador. Você pode reproduzir, pausar, controlar o volume e aplicar zoom no vídeo em tela cheia.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configuração para carregar ativos com mais de 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Por padrão, a AEM Assets não permite fazer upload de ativos com mais de 2 GB devido a um limite de tamanho de arquivo. No entanto, você pode substituir esse limite indo para o CRXDE Lite e criando um nó no `/apps` diretório. O nó deve ter o mesmo nome de nó, estrutura de diretório e propriedades de ordem de nó comparáveis.

Além da configuração do AEM Assets, altere as seguintes configurações para fazer upload de ativos grandes:

* Aumente o tempo de expiração do token. Consulte Servlet [!UICONTROL CSRF] Adobe Granite no Console da Web em `https://[aem_server]:[port]/system/console/configMgr`. Para obter mais informações, consulte Proteção [](/help/sites-developing/csrf-protection.md)CSRF.
* Aumente a configuração `receiveTimeout` no Dispatcher. Para obter mais informações, consulte Configuração [do](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)Dispatcher.

>[!NOTE]
>
>A interface do usuário AEM Classic não tem uma restrição de limite de tamanho de arquivo de dois gigabytes. Além disso, o fluxo de trabalho completo para vídeos grandes não é totalmente compatível.

Para configurar um limite de tamanho de arquivo maior, execute as seguintes etapas no `/apps` diretório.

1. No AEM, toque em **[!UICONTROL Ferramentas > Geral > CRXDE Lite]**.
1. Na página **[!UICONTROL CRXDE Lite]** , na janela do diretório à esquerda, navegue até `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Para ver a janela do diretório, toque no `>>` ícone.
1. From the toolbar, tap **[!UICONTROL Overlay Node]**. Como alternativa, selecione **[!UICONTROL Sobrepor nó]** no menu de contexto.
1. Na caixa de diálogo **[!UICONTROL Sobrepor nó]**, toque em **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Atualize o navegador. O nó de sobreposição `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` é selecionado.
1. Na guia **[!UICONTROL Propriedades]** , digite o valor apropriado em bytes para aumentar o limite de tamanho para o tamanho desejado. Por exemplo, insira `32212254720` valor para aumentar o limite de tamanho para 30 GB.

1. Na barra de ferramentas, toque em **[!UICONTROL Salvar tudo]**.
1. No AEM, toque em **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. Na página Pacotes **[!UICONTROL do Console da Web do]** Adobe Experience Manager, na coluna **[!UICONTROL Nome]** da tabela, localize e toque em **[!UICONTROL Adobe Granite Workflow Job Handler]**.
1. In the **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours).
1. Toque em **[!UICONTROL Salvar]**.
1. Em AEM, toque em **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. Na página Modelos **[!UICONTROL de]** fluxo de trabalho, selecione **[!UICONTROL Dynamic Media Encode Video]**(Codificação de vídeo em mídia dinâmica) e toque em **[!UICONTROL Editar]**.
1. Na página **[!UICONTROL Fluxo de trabalho]** , toque em duplo no componente Processo **[!UICONTROL de serviço de vídeo]** do Dynamic Media.
1. Na caixa de diálogo **[!UICONTROL Propriedades da etapa]**, na guia **[!UICONTROL Comum]**, expanda **[!UICONTROL Configurações avançadas]**.
1. No campo **[!UICONTROL Tempo limite]**, especifique um valor `18000` e toque em **[!UICONTROL OK]** para retornar à página de fluxo de trabalho **[!UICONTROL Codificação de vídeo do Dynamic Media]**.
1. Próximo à parte superior da página, abaixo do título da página Codificação de vídeo **[!UICONTROL do]** Dynamic Media, toque em **[!UICONTROL Salvar]**.

## Publicar ativos de vídeo {#publishing-video-assets}

Após a publicação dos ativos de vídeo, eles estarão disponíveis para inclusão em uma página da Web por meio de um URL ou incorporação em uma página da Web. Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).

## Anotar ativos de vídeo {#annotating-video-assets}

1. No console Ativos, toque no ícone **[!UICONTROL Editar]** no cartão do ativo para exibir a página de detalhes do ativo.
1. Toque no ícone de **[!UICONTROL Pré-visualização]** para reproduzir o vídeo.
1. Para anotar o vídeo, toque no botão **[!UICONTROL Anotar]** . Uma anotação é adicionada no ponto de tempo específico (quadro) do vídeo.

   Ao anotar, você pode desenhar na tela e incluir um comentário com o desenho. Os comentários são salvos automaticamente no Adobe Experience Manager Assets.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Para sair do assistente de anotações, toque em **[!UICONTROL Fechar]**.

1. To jump to a specific point in the video, specify the time in seconds in the text field and click **[!UICONTROL Jump]**. For example, to skip the first 20 seconds of video, enter `20` in the text field.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Clique em uma anotação para visualização-la na linha do tempo. Toque em **[!UICONTROL Excluir]** para remover a anotação da linha do tempo.

   ![chlimage_1-206](assets/chlimage_1-206.png)
