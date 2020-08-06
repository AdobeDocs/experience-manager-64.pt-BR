---
title: Integração AEM 3D com Autodesk 3ds Max
seo-title: Integração AEM 3D com AutoDesk 3ds Max
description: Como opção, você pode integrar AEM 3D com o software Autodesk 3ds Max para permitir o suporte para arquivos 3ds Max nativos (.MAX). A renderização por meio de 3ds Max não é suportada no momento.
seo-description: Como opção, você pode integrar AEM 3D com o software Autodesk 3ds Max para permitir o suporte para arquivos 3ds Max nativos (.MAX). A renderização por meio de 3ds Max não é suportada no momento.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Integração AEM 3D com Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Esta tarefa é opcional e diz respeito apenas ao Windows.

Como opção, você pode integrar AEM 3D com o software Autodesk 3ds Max para permitir o suporte para arquivos 3ds Max nativos (.MAX). A renderização por meio de 3ds Max não é suportada no momento.

Consulte Configurações [](advanced-config-3d.md)avançadas.

Consulte também [Integração AEM 3D com o AutoDesk Maya](integrate-maya-with-3d.md).

**Para integrar AEM 3D com o Autodesk 3ds Max**:

1. Instale o software Autodesk 3ds Max nos mesmos servidores onde os nós de autor de AEM estão instalados.

   Após a instalação, verifique se você pode abrir e usar o Maya e se não há problemas de licenciamento.

   >[!NOTE]
   >
   >Para evitar problemas de acesso negado, instale o Max de 3ds usando a mesma conta de usuário administrador como AEM.

1. Em 3ds Max, clique em **[!UICONTROL Personalizar > Gerenciador]** de plug-ins.

   Localize `FBXMAX.DLU` e verifique se seu **[!UICONTROL Status]** está **[!UICONTROL carregado**.

   Feche a caixa de diálogo Gerenciador **** de plug-ins e 3ds máx.

1. Atualize o script de conversão.

   AEM usa um script de linha de comando para chamar o utilitário de linha de comando 3ds Max `3dsmaxcmd.exe`. Você deve editar esse script se tiver instalado uma versão diferente de 3ds Max 2016, ou se tiver instalado 3ds Max em um local não padrão, ou se tiver instalado AEM em uma partição ou unidade diferente.

   1. Abra CRXDE Lite e navegue até `/libs/settings/dam/v3D/scripts/max`.
   1. Clique com o Duplo do mouse `export-fbx.bat` para abri-lo.
   1. Edite a primeira linha do script conforme necessário para refletir a localização do `3dsmaxcmd.exe` utilitário. Por exemplo, se 3ds Max 2017 for usado e AEM estiver instalado em uma unidade de disco diferente:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Perto do canto superior esquerdo da página CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

   Perto do canto superior esquerdo da página CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

1. Remova a pasta de trabalho (somente necessário se tiver sido feita uma tentativa anterior de assimilar um arquivo .MAX).

   1. No CRXDE Lite, navegue até `/libs/settings/dam/v3D/Paths/maxWorkPath`. Por padrão, o valor dessa configuração é `./MaxWork`, que é relativo à pasta raiz de instalação AEM.
   1. Faça logon no próprio servidor e use o Explorador de Arquivos para navegar até a pasta raiz de instalação do AEM.
   1. Exclua a pasta **[!UICONTROL MaxWork]** , incluindo todo o seu conteúdo, se ela existir.

      A pasta será recriada automaticamente na próxima vez que um arquivo .MAX for assimilado.

1. Ative 3ds Max para ingestão, fazendo o seguinte:

   1. No CRXDE Lite, navegue até `/libs/settings/dam/v3D/assetTypes/max` e defina a propriedade **[!UICONTROL Enabled]** como true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Perto do canto superior esquerdo da página CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

## Testando a integração de AEM 3D com o Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Abra o AEM Assets e faça upload do arquivo localizado em `.max` na pasta `sample-3D-content/models` test3d **** .

   Observe que sample-3D-content.zip foi baixado anteriormente para validar a funcionalidade básica 3D.

1. Retorne à visualização de **[!UICONTROL cartão]** e observe os banners de mensagem exibidos nos ativos carregados.

   O banner Formato de conversão é exibido enquanto o Máx. de 3ds está convertendo o formato máx. de 3ds nativo em .FBX.

1. Após a conclusão do processamento, abra `logo-sphere.max` a visualização **[!UICONTROL Detalhe]** .

   A experiência de Pré-visualização é a mesma que com `logo_sphere.fbx`.

