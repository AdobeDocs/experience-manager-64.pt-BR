---
title: Integração AEM 3D com o Autodesk 3ds Max
seo-title: Integração AEM 3D com o AutoDesk 3ds Max
description: Opcionalmente, é possível integrar AEM 3D com o software Autodesk 3ds Max para ativar o suporte para arquivos 3ds Max (.MAX) nativos. A renderização por meio de 3ds Max não é compatível no momento.
seo-description: Opcionalmente, é possível integrar AEM 3D com o software Autodesk 3ds Max para ativar o suporte para arquivos 3ds Max (.MAX) nativos. A renderização por meio de 3ds Max não é compatível no momento.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
exl-id: 2edecd53-0a2d-44bb-968a-d988c780e142
feature: Ativos 3D
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Integração AEM 3D com o Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Esta tarefa é opcional e pertence apenas ao Windows.

Opcionalmente, é possível integrar AEM 3D com o software Autodesk 3ds Max para ativar o suporte para arquivos 3ds Max (.MAX) nativos. A renderização por meio de 3ds Max não é compatível no momento.

Consulte [Configurações avançadas](advanced-config-3d.md).

Consulte também [Integração do AEM 3D com o AutoDesk Maya](integrate-maya-with-3d.md).

**Para integrar AEM 3D com o Autodesk 3ds Max**:

1. Instale o software Autodesk 3ds Max nos mesmos servidores onde os nós do AEM Author estão instalados.

   Após a instalação, verifique se você pode abrir e usar o Maya e se não há problemas de licenciamento.

   >[!NOTE]
   >
   >Para evitar problemas de acesso negado, instale o Max 3ds usando a mesma conta de usuário administrador do AEM.

1. Em 3ds Max, clique em **[!UICONTROL Personalizar > Gerenciador de plug-ins]**.

   Localize `FBXMAX.DLU` e verifique se seu **[!UICONTROL Status]** é **[!UICONTROL carregado]**.

   Feche a caixa de diálogo **[!UICONTROL Gerenciador de plug-ins]** e o Máx. de 3ds.

1. Atualize o script de conversão.

   AEM usa um script de linha de comando para chamar o utilitário de linha de comando 3ds Max `3dsmaxcmd.exe`. Você deve editar esse script se tiver instalado uma versão diferente de 3ds Max 2016, ou se tiver instalado o 3ds Max em um local não padrão, ou se tiver instalado o AEM em uma partição ou unidade diferente.

   1. Abra o CRXDE Lite e navegue até `/libs/settings/dam/v3D/scripts/max`.
   1. Clique duas vezes em `export-fbx.bat` para abri-lo.
   1. Edite a primeira linha do script conforme necessário para refletir o local do utilitário `3dsmaxcmd.exe`. Por exemplo, se 3ds Max 2017 for usado e AEM estiver instalado em uma unidade de disco diferente:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Próximo ao canto superior esquerdo da página do CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

   Próximo ao canto superior esquerdo da página do CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

1. Remova a pasta de trabalho (necessário somente se tiver sido feita uma tentativa anterior de assimilar um arquivo .MAX).

   1. No CRXDE Lite, navegue até `/libs/settings/dam/v3D/Paths/maxWorkPath`. Por padrão, o valor dessa configuração é `./MaxWork`, que é relativo à pasta raiz de instalação AEM.
   1. Faça logon no próprio servidor e use o Explorador de Arquivos para navegar até a pasta raiz de instalação do AEM.
   1. Exclua a pasta **[!UICONTROL MaxWork]** - incluindo todo o conteúdo - se ela existir.

      A pasta é recriada automaticamente na próxima vez que um arquivo .MAX for assimilado.

1. Ative o Máx. de 3ds para assimilação fazendo o seguinte:

   1. No CRXDE Lite, navegue até `/libs/settings/dam/v3D/assetTypes/max` e defina a propriedade **[!UICONTROL Enabled]** como true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Próximo ao canto superior esquerdo da página do CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

## Testando a integração do AEM 3D com o Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Abra o AEM Assets e faça upload do arquivo `.max` localizado em `sample-3D-content/models` para a pasta **[!UICONTROL test3d]**.

   Observe que sample-3D-content.zip foi baixado anteriormente para validar a funcionalidade básica de 3D.

1. Retorne à visualização **[!UICONTROL Cartão]** e observe os banners de mensagem mostrados nos ativos carregados.

   O banner de Formato de conversão é exibido, enquanto o Máx. de 3ds está convertendo o formato máximo de 3ds nativo em .FBX.

1. Após a conclusão do processamento, abra `logo-sphere.max` na visualização **[!UICONTROL Detail]**.

   A experiência de Visualização é a mesma que com `logo_sphere.fbx`.
