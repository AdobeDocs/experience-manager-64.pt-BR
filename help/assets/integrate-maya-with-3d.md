---
title: Integração AEM 3D com o Autodesk Maya
seo-title: Integração AEM 3D com o Autodesk Maya
description: Opcionalmente, é possível integrar AEM 3D com o software Autodesk® Maya® para ativar o suporte a arquivos Maya nativos (.MA e .MB) e para permitir renderizar ativos 3D no AEM com qualquer renderizador Maya disponível.
seo-description: Opcionalmente, é possível integrar AEM 3D com o software Autodesk® Maya® para ativar o suporte a arquivos Maya nativos (.MA e .MB) e para permitir renderizar ativos 3D no AEM com qualquer renderizador Maya disponível.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
exl-id: 52ecbf81-0953-4c44-bc2c-d40e507b8d98
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# Integração AEM 3D com o Autodesk Maya {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>Esta tarefa é opcional e pertence apenas ao Windows.

Opcionalmente, é possível integrar AEM 3D com o software Autodesk® Maya® para ativar o suporte a arquivos Maya nativos (`.MA` e `.MB`) e permitir renderizar ativos 3D no AEM com qualquer renderizador Maya disponível.

*Essa integração é somente* para Windows.

Ao integrar com o Autodesk Maya, você deve instalar e configurar o Autodesk Maya, adicionar o caminho à pasta executável do Maya, ativar o Maya para assimilação e renderização e testar a integração.

Consulte [Configurações avançadas](advanced-config-3d.md).

Consulte também [Integrando AEM 3D com o AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md).

**Para integrar AEM 3D com o Autodesk Maya**:

1. Instale o software Autodesk Maya 2016 nos mesmos servidores em que AEM está hospedado.

   Após a instalação, verifique se você pode abrir e usar o Maya e se não há problemas de licenciamento.

   >[!NOTE]
   >
   >AEM usa somente a ferramenta de renderização de linha de comando Maya (`render.exe`). Uma única licença de rede Maya permite que até cinco servidores processem ou renderizem o conteúdo Maya simultaneamente.

1. No Maya, ative o plug-in Autodesk FBX®.
1. Instale o plug-in de renderização do MentalRay ou outro renderizador desejado.

   Após a instalação, verifique se o MentalRay está disponível no Maya.

1. Adicione o caminho para a pasta executável do Maya à variável de ambiente PATH do Windows.

   Por exemplo, no Windows Server 2012, toque em **[!UICONTROL Iniciar] > [!UICONTROL Painel de Controle] > [!UICONTROL Sistema e Segurança] > [!UICONTROL Sistema] > [!UICONTROL Configurações Avançadas do Sistema] > [!UICONTROL Variáveis de Ambiente&lt;a111/ .]** Anexe o caminho completo para a pasta `Maya2016\bin` para a variável `Path`do sistema.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Para ativar o Maya para assimilação e renderização, abra **[!UICONTROL CRXDE Lite]** e navegue até `/libs/settings/dam/v3D/assetTypes/maya` e defina a propriedade **[!UICONTROL Enabled]** para `true`.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. Para ativar o formato de arquivo JT (Siemens PLM Open CAD), navegue até `/libs/settings/dam/v3D/assetTypes/jt` e defina a propriedade **[!UICONTROL Enabled]** como `true`.
1. No AEM, ative o Maya como renderizador. Comece navegando até **[!UICONTROL Tools > General > CRXDE Lite]**.
1. Na página **[!UICONTROL CRXDE Lite]**, no painel esquerdo, navegue até o seguinte:

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Defina a propriedade **[!UICONTROL Enabled]** para `true`.

1. Próximo ao canto superior esquerdo da página **[!UICONTROL CRXDE Lite]**, toque em **[!UICONTROL Salvar tudo]**.

   O Maya agora está habilitado como renderizador.

## Testando a integração do AEM 3D com o Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. Abra o AEM Assets e faça upload dos arquivos `.MA` localizados em `sample-3D-content/models` para a pasta `test3d` .

   Observe que `sample-3D-content.zip` foi baixado anteriormente para validar a funcionalidade básica de 3D.

1. Retorne à visualização **[!UICONTROL Cartão]** e observe os banners de mensagem mostrados nos ativos carregados.

   O banner Formato de conversão é exibido enquanto o Maya está convertendo o formato nativo `.MA` em `.FBX`.

1. Após a conclusão de todo o processamento, abra o ativo `logo-sphere.ma` e selecione o estágio `stage-helipad.ma`.

   A experiência de Visualização é a mesma que com `logo_sphere.fbx` e `stage-helipad.fbx`.

1. Próximo ao canto superior esquerdo da página, toque ou clique na lista suspensa e selecione **[!UICONTROL CRender]**.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. Na lista suspensa **[!UICONTROL Renderizador]**, selecione **[!UICONTROL Autodesk Maya]** e toque em **[!UICONTROL Iniciar Renderização]**.
1. Próximo ao canto superior direito da página, toque ou clique em **[!UICONTROL Fechar]** para retornar ao modo de exibição **[!UICONTROL Cartão]**.

   Observe o banner de mensagem no ativo de imagem que está sendo renderizado (`logo-sphere`, a menos que um nome de imagem diferente tenha sido especificado). Uma barra de progresso no banner mostra o progresso da renderização.

   >[!NOTE]
   >
   >A renderização exige muito da CPU e pode levar vários minutos para ser concluída

1. Depois que a renderização for concluída, abra o ativo de imagem renderizado.

   Verifique se a imagem renderizada corresponde razoavelmente à imagem que você estava visualizando no momento em que clicou em **[!UICONTROL Renderizar agora]**.

## Ativar Formatos Adicionais Suportados Pelo Maya {#enabling-additional-formats-supported-by-maya}

(Opcional) O Maya suporta diversos formatos de entrada 3D, qualquer um dos quais pode ser ativado para que o AEM reconheça o tipo de arquivo. Quando ativado, o AEM envia o arquivo para o Maya para convertê-lo em um formato intermediário que pode ser assimilado diretamente pelo AEM.

Dependendo do formato, o suporte a recursos pode ser limitado (por exemplo, materiais podem não ser passados) e a qualidade/fidelidade pode ser limitada (por exemplo, faces revertidas). O Adobe suporta apenas o mecanismo geral, mas não qualquer conversão de formato específica.

Consulte [Formatos de importação de dados suportados | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) para obter informações sobre os formatos suportados pelo Maya.

**Para ativar formatos adicionais compatíveis com AEM**:

1. Usando **[!UICONTROL CRXDE Lite]**, navegue até `/libs/settings/dam/v3D/assetTypes`.
1. Faça uma cópia do nó **[!UICONTROL jt]**. Clique com o botão direito do mouse no nó **[!UICONTROL jt]** e selecione **[!UICONTROL Copiar]**, clique com o botão direito do mouse na pasta **[!UICONTROL assetTypes]** e selecione **[!UICONTROL Colar]**. Isso deve produzir um novo nó `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. Renomeie o novo nó para atribuí-lo um nome exclusivo que represente o tipo de arquivo a ser adicionado. O sufixo do arquivo pode ser usado para qualquer outro identificador exclusivo.

1. Defina a propriedade **[!UICONTROL Enabled]** do novo nó para `true`.

1. Defina a propriedade **[!UICONTROL Extension]** da nova nota para o sufixo/extensão de arquivo do formato que está sendo adicionado.
1. Defina a propriedade **[!UICONTROL MimeType]** com um valor apropriado. `application/x-` seguido pelo valor da  **** Extensionproperty deve funcionar para a maioria dos tipos de arquivo.
1. Certifique-se de que a propriedade **[!UICONTROL Conversion]** esteja definida como `fbx` e **[!UICONTROL AssimilarRegime]** como `Maya`.
1. Clique em **[!UICONTROL Salvar tudo]** próximo à parte superior esquerda da página.

A captura de tela a seguir ilustra um formato de arquivo adicionado, usando o COLLADA DAE como exemplo:

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)
