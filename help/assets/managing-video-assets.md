---
title: Gerenciar ativos de vídeo
description: Saiba como fazer upload, visualizar, anotar e publicar ativos de vídeo.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 9%

---

# Gerenciar ativos de vídeo {#managing-video-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como gerenciar e editar os ativos de vídeo nos Ativos da Adobe Experience Manager. Além disso, se você tiver licença para usar o Dynamic Media, consulte o [Documentação de vídeo do Dynamic Media](video.md).

## Fazer upload e visualizar ativos de vídeo {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] Os ativos geram visualizações para ativos de vídeo com a extensão MP4. Se o formato do ativo não for MP4, instale o FFmpeg pack para gerar uma pré-visualização. FFmpeg cria representações de vídeo do tipo OGG e MP4. Você pode visualizar essas representações no [!DNL Experience Manager] Interface do usuário do Assets.

1. Na pasta ou nas subpastas Ativos digitais, navegue até o local onde deseja adicionar ativos digitais.
1. Para fazer upload do ativo, clique ou toque em **[!UICONTROL Criar]** na barra de ferramentas e escolha **[!UICONTROL Arquivos]**. Como alternativa, solte-o diretamente na área de ativos. Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets) para obter detalhes sobre a operação de upload.
1. Para visualizar um vídeo na exibição de Cartão, toque no **[!UICONTROL Reproduzir]** no ativo de vídeo.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Você pode pausar ou reproduzir o vídeo na **[!UICONTROL Cartão]** exibir somente. O botão Reproduzir/Pausar não está disponível no **[!UICONTROL Lista]** exibir.

1. Toque no **[!UICONTROL Editar]** ícone no cartão para visualizar o vídeo no **[!UICONTROL Detalhes]** exibir.

   O vídeo é reproduzido no player de vídeo nativo do navegador. Você pode reproduzir, pausar, controlar o volume e aplicar zoom ao vídeo em tela cheia.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configuração para fazer upload de ativos com mais de 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Por padrão, a variável [!DNL Experience Manager] Os ativos não permitem fazer upload de ativos com mais de 2 GB por causa de um limite de tamanho de arquivo. No entanto, é possível substituir esse limite indo até o CRXDE Lite e criando um nó sob o `/apps` diretório. O nó deve ter o mesmo nome de nó, estrutura de diretório e propriedades de nó comparáveis da ordem.

Além de [!DNL Experience Manager] Configuração de ativos, altere as seguintes configurações para fazer upload de ativos grandes:

* Aumente o tempo de expiração do token. Consulte [!UICONTROL Servlet CSRF do Adobe Granite] no Console da Web em `https://[aem_server]:[port]/system/console/configMgr`. Para obter mais informações, consulte [Proteção CSRF](/help/sites-developing/csrf-protection.md).
* Aumente o `receiveTimeout` na configuração do Dispatcher. Para obter mais informações, consulte [Configuração do Dispatcher do Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>O [!DNL Experience Manager] A interface de usuário clássica não tem uma restrição de limite de tamanho de arquivo de dois gigabytes. Além disso, o fluxo de trabalho completo para vídeo grande não é totalmente compatível.

Para configurar um limite de tamanho de arquivo mais alto, execute as seguintes etapas no `/apps` diretório.

1. No AEM, toque em **[!UICONTROL Ferramentas > Geral > CRXDE Lite]**.
1. No **[!UICONTROL CRXDE Lite]** na janela do diretório à esquerda, navegue até `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Para ver a janela do diretório, toque em `>>` ícone .
1. Na barra de ferramentas, toque em **[!UICONTROL Nó de sobreposição]**. Como alternativa, selecione **[!UICONTROL Sobrepor nó]** no menu de contexto.
1. Na caixa de diálogo **[!UICONTROL Sobrepor nó]**, toque em **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Atualize o navegador. O nó de sobreposição `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` está selecionada.
1. No **[!UICONTROL Propriedades]** , insira o valor apropriado em bytes para aumentar o limite de tamanho para o tamanho desejado. Por exemplo, insira `32212254720` para aumentar o limite de tamanho para 30 GB.

1. Na barra de ferramentas, toque em **[!UICONTROL Salvar tudo]**.
1. No AEM, toque em **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. No **[!UICONTROL Pacotes do console da Web do Adobe Experience Manager]** na página **[!UICONTROL Nome]** coluna da tabela, localize e toque **[!UICONTROL Manipulador de Trabalho do Processo Externo do Fluxo de Trabalho do Adobe Granite]**.
1. No **[!UICONTROL Manipulador de Trabalho do Processo Externo do Fluxo de Trabalho do Adobe Granite]** , defina os segundos para ambos **[!UICONTROL Tempo limite padrão]** e **[!UICONTROL Tempo limite máximo]** campos para `18000` (cinco horas).
1. Toque **[!UICONTROL Salvar]**.
1. Em AEM, toque em **[!UICONTROL Ferramentas > Fluxo de trabalho > Modelos]**.
1. No **[!UICONTROL Modelos de fluxo de trabalho]** página, selecione **[!UICONTROL Codificar vídeo no Dynamic Media]** e toque em **[!UICONTROL Editar]**.
1. No **[!UICONTROL Fluxo de trabalho]** toque duas vezes na página **[!UICONTROL Processo de serviço de vídeo do Dynamic Media]** componente.
1. Na caixa de diálogo **[!UICONTROL Propriedades da etapa]**, na guia **[!UICONTROL Comum]**, expanda **[!UICONTROL Configurações avançadas]**.
1. No campo **[!UICONTROL Tempo limite]**, especifique um valor `18000` e toque em **[!UICONTROL OK]** para retornar à página de fluxo de trabalho **[!UICONTROL Codificação de vídeo do Dynamic Media]**.
1. Próximo à parte superior da página, abaixo do **[!UICONTROL Codificar vídeo no Dynamic Media]** título da página, toque **[!UICONTROL Salvar]**.

## Publicar ativos de vídeo {#publishing-video-assets}

Após a publicação dos ativos de vídeo, eles ficam disponíveis para inclusão em uma página da Web por meio de um URL ou incorporação em uma página da Web. Consulte [Publicar ativos](publishing-dynamicmedia-assets.md).

## Anotar ativos de vídeo {#annotating-video-assets}

1. No console Assets, toque no **[!UICONTROL Editar]** ícone no cartão do ativo para exibir a página de detalhes do ativo.
1. Toque no **[!UICONTROL Visualizar]** ícone para reproduzir o vídeo.
1. Para anotar o vídeo, toque no botão **[!UICONTROL Anotar]** botão. Uma anotação é adicionada no ponto de tempo (quadro) específico do vídeo.

   Ao anotar, é possível desenhar na tela e incluir um comentário com o desenho. Os comentários são salvos automaticamente no Adobe Experience Manager Assets.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Para sair do assistente de anotação, toque em **[!UICONTROL Fechar]**.

1. Para pular para um ponto específico no vídeo, especifique o tempo em segundos no campo de texto e clique em **[!UICONTROL Salto]**. Por exemplo, para ignorar os primeiros 20 segundos de vídeo, insira `20` no campo de texto.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Clique em uma anotação para exibi-la na linha do tempo. Toque **[!UICONTROL Excluir]** para remover a anotação da linha do tempo.

   ![chlimage_1-206](assets/chlimage_1-206.png)
