---
title: Instalação e configuração do AEM 3D
seo-title: Instalação e configuração do AEM 3D
description: Saiba como instalar e configurar AEM 3D
seo-description: Saiba como instalar e configurar AEM 3D
uuid: a60732ff-fd66-4f29-b901-42a3cfd58b65
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5898d084-4b45-41bc-ad2e-2fcc65b0392c
exl-id: 5baaef61-5c70-4796-8ae2-44053e855ad9
feature: Ativos 3D
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 1%

---

# Instalação e configuração do AEM 3D {#installing-and-configuring-aem-d}

>[!IMPORTANT]
>
>AEM 3D no AEM 6.4 não é mais compatível. O Adobe recomenda usar o recurso de ativos 3D em [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) ou [AEM 6.5.3 ou superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

A instalação e configuração do AEM 3D (versão 3.0) envolve o seguinte:

1. Instalação da biblioteca de SDK FBX® do Autodesk®.
1. Download e instalação do pacote de código 3D nativo.
1. Configurar o fluxo de trabalho de assimilação de ativos 3D e reiniciar o AEM.
1. Validando a configuração do AEM 3D.

Consulte também [Trabalhar com ativos 3D](assets-3d.md).

Consulte também [AEM notas de versão do 3D Assets](/help/release-notes/aem3d-release-notes.md) para obter pré-requisitos, navegadores compatíveis e outras informações importantes da versão.

Consulte também [Trabalhar com o componente Sites 3D](using-the-3d-sites-component.md).

>[!NOTE]
>
>Antes de baixar e instalar o pacote 3D, verifique se você instalou todos os pré-requisitos AEM pacotes com êxito. Consulte as [Notas de versão AEM 3D.](install-config-3d.md)

## Instalação da biblioteca de SDK FBX do Autodesk {#installing-the-autodesk-fbx-sdk-library}

O código AEM 3D nativo requer a biblioteca FBX do Autodesk para suportar o formato de arquivo FBX. (No momento, o Adobe não pode redistribuir essa biblioteca.)

Consulte também [Configurações avançadas](advanced-config-3d.md).

1. Faça logon no host onde o AEM está instalado.

   * Se esta for uma implantação do Windows Server, faça logon no servidor como Administrador.
   * Se esta for uma área de trabalho MAC ou Windows, certifique-se de ter privilégios de administrador.

1. Use o link apropriado para seu sistema operacional para baixar o **FBX SDK versão 2016.1.2**

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. Instale o SDK do FBX:

   * Windows. Instale na mesma unidade em que AEM está localizado.
   * Mac. Instale na mesma partição em que AEM está localizado.
   * Linux. Extraia o pacote baixado e siga as instruções em `<yourFBXSDKpath>/Install_FbxFileSdk.txt`. Instale o SDK em `/usr`.

## Download e instalação do pacote de código 3D nativo {#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>Antes de continuar com a instalação e a configuração do AEM 3D, o Adobe recomenda que você implante service packs e outros pacotes de recursos relacionados aplicáveis. Consulte [AEM Notas de versão 3D](/help/release-notes/aem3d-release-notes.md).

Consulte também [Configurações avançadas](advanced-config-3d.md).

**Para instalar o pacote** de código 3D nativo:

1. Faça uma das seguintes opções:

   * Se esta for uma implantação do Windows Server, faça logon no servidor como Administrador.
   * Se esta for uma área de trabalho Mac ou Windows, verifique se você tem privilégios de Administrador.

1. Verifique se você tem um navegador compatível disponível para acessar AEM.

   Consulte [Requisitos do sistema](/help/release-notes/aem3d-release-notes.md#system-requirements).

1. Acesse [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Localize a versão 3.0.1 do pacote de recursos `AEM-6.4-DynamicMedia-3D` e baixe-a.

1. Em AEM, clique em **[!UICONTROL Ferramentas > Administração > Implantação > Gerenciador de Pacotes]**.

1. Faça upload do pacote de recursos baixado para o AEM. Localize-o e clique em **[!UICONTROL Instalar]**.

1. Na caixa de diálogo **[!UICONTROL Instalar Pacote]**, expanda **Configurações Avançadas** e defina **[!UICONTROL Manuseio de Controle de Acesso]** para **Mesclar**.
1. Clique em **[!UICONTROL Install]** para iniciar a instalação do pacote.

   O arquivo `sample-3D-content.zip` é colocado na pasta raiz **[!UICONTROL Assets]**. Consulte [Validando a configuração do AEM 3D](#validating-the-setup-of-aem-d) para obter mais informações.

## Configurar o fluxo de trabalho de assimilação de ativos 3D e reiniciar AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**Para configurar o fluxo de trabalho de assimilação de ativos 3D**:

1. Em AEM, clique no logotipo do AEM para acessar o console de navegação global, clique no ícone **[!UICONTROL Ferramentas]** e navegue até **[!UICONTROL Fluxo de trabalho > Modelos]**.
1. Na página **[!UICONTROL Modelos de fluxo de trabalho]**, passe o mouse sobre o fluxo de trabalho **[!UICONTROL Ativo de atualização DAM]** e, quando a marca de seleção for exibida, selecione-a.

1. Na barra de ferramentas, clique em **[!UICONTROL Editar]**.
1. Na tela **[!UICONTROL Ativo de atualização do DAM]**, no painel flutuante AEM, clique no ícone **[!UICONTROL Mais]** à direita de Fluxo de trabalho para expandir a lista. Selecione **[!UICONTROL Etapa do Processo]** na lista.
1. Arraste **[!UICONTROL Etapa do processo]** e solte-a no workflow logo antes do componente **[!UICONTROL Fluxo de trabalho do ativo de atualização do DAM concluído]** próximo ao final do fluxo de trabalho.

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. Clique duas vezes na etapa recém-adicionada do processo.
1. Na caixa de diálogo **[!UICONTROL Propriedades da etapa]**, na guia **[!UICONTROL Comum]**, no campo **[!UICONTROL Título]**, digite uma descrição adequada para o processo, como `Process 3D content`.
1. Clique na guia **[!UICONTROL Process]**.

1. No menu suspenso **[!UICONTROL Process]**, selecione **[!UICONTROL Serviço de objeto 3D geométrico]** e marque a caixa de seleção **[!UICONTROL Avanço do manipulador]**.

   ![3d_install-process-step-propertiesdlg](assets/3d_install-process-steppropertiesdlg.png)

1. Próximo ao canto superior direito da caixa de diálogo, clique no ícone de marca de seleção para retornar à página Ativo de atualização DAM.
1. Próximo ao canto superior direito da página **[!UICONTROL Ativo de atualização do DAM]**, clique em **[!UICONTROL Sincronizar]** para salvar o modelo de fluxo de trabalho editado.
1. Reinicie o AEM.

   Após a reinicialização, você está pronto para carregar conteúdo 3D e AEM processá-lo.

   Continue com [Validando a configuração do AEM 3D](#validating-the-setup-of-aem-d).

## Validando a configuração do AEM 3D {#validating-the-setup-of-aem-d}

1. Em AEM, clique em **[!UICONTROL Ferramentas > Ativos]**, baixe `sample-3D-content.zip` e expanda o arquivo baixado. (Agora você pode excluir `sample-3D-content.zip` no AEM.)

   Verifique se você está em **[!UICONTROL Exibição de cartão]** para visualizar o feedback de upload e processamento nas etapas restantes.

1. Crie uma pasta chamada `test3d` para receber conteúdo de teste.
1. Faça upload de todos os arquivos de `sample-3D-content/images` para a pasta `test3d`.
1. Aguarde até que o upload e o processamento sejam concluídos. Talvez seja necessário atualizar o navegador.

   Faça upload dos três arquivos `.fbx` de `sample-3D-content/` para a pasta `test3d`.

   Ainda não carregue os arquivos do modelo .ma.

1. Na Exibição de cartão, observe os banners de mensagem mostrados nos cartões de ativos 3d.

   Cada ativo continua por várias etapas de processamento. Quando o **[!UICONTROL Criando Pré-visualização...]** etapa de processamento concluída, o cartão é atualizado com uma imagem em miniatura. Quando o processamento final é concluído, o banner é substituído pelo indicador **[!UICONTROL NEW]**.

   >[!NOTE]
   >
   >Espera-se um alto uso da CPU enquanto o processamento 3D está em andamento. Dependendo da capacidade disponível da CPU, pode levar um tempo substancial para concluir todo o processamento.

   ![screenshot_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. Agora você aprenderá a resolver dependências de arquivos.

   No banner **[!UICONTROL Dependências Não Resolvidas]** para o cartão `stage-helipad.fbx`, clique no ícone **[!UICONTROL Ponto de Exclamação]** para navegar até as propriedades do ativo e abrir a guia **Dependências**.

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. Clique no ícone **[!UICONTROL Folder/Magnifying Glass]** à direita do nome do arquivo para abrir o navegador de ativos e resolver as dependências da seguinte maneira:

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. Clique em **[!UICONTROL Salvar]** e **[!UICONTROL Fechar]** para concluir o processamento do ativo e retornar para a **[!UICONTROL Exibição de cartão]**, respectivamente.
1. Quando o processamento estiver concluído, você verá o seguinte em **[!UICONTROL Exibição de cartão]**:

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. Na página test3d , clique no cartão `logo-sphere.fbx` para abrir o modelo em **[!UICONTROL Exibição de detalhes]**.

   Próximo ao canto superior direito da página logo-sphere.fbx, clique no ícone Destaque do palco para expandir o menu suspenso e selecione `stage-spotlights.fbx`.

   ![chlimage_1-375](assets/chlimage_1-375.png)

1. Na lista suspensa **[!UICONTROL Destaque de palco]**, selecione `stage-helipad.fbx`.

   Usando o botão esquerdo do mouse para ajustar a exibição. A iluminação do plano de fundo e do modelo muda para refletir a seleção do novo estágio.

   ![chlimage_1-376](assets/chlimage_1-376.png)

## Configuração do suporte para ativos Adobe Dimension {#configuring-support-for-adobe-dimension-assets}

>[!NOTE]
>
>Essa tarefa de configuração é opcional.

Opcionalmente, é possível configurar o suporte no AEM 3D para ativos do Adobe Dimension.

Você deve configurar um serviço de conversão externo para permitir a assimilação, pré-visualização e publicação de ativos Adobe Dimension 3D no AEM. O serviço converte do formato Adobe Dimension proprietário (`.dn`) em uma variante de glTF (formatada como um arquivo `.glb`) que é salva com o ativo Dn como representação. A representação `.glb` é usada para a visualização baseada na Web do ativo 3D no AEM Assets, Sites e Screens, e também está disponível para download para uso com aplicativos de terceiros.

>[!NOTE]
>
>O serviço de conversão é hospedado pelo Adobe no Amazon AWS. Após configurar corretamente o serviço, os arquivos `.dn` carregados no AEM são copiados com segurança para o serviço de conversão por meio de armazenamento temporário no Amazon S3. O resultado da conversão é transferido de volta para AEM por meio de armazenamento temporário S3. Todas as transferências e armazenamento são seguras. Além disso, o conteúdo persiste no S3 e o serviço de conversão apenas brevemente (normalmente não mais do que alguns minutos).

**Para configurar o suporte para ativos** do Adobe Dimension:

1. Entre em contato com o gerente de contas do Adobe AEM, especialista em provisionamento ou representante de suporte para solicitar credenciais para **AEM3D Services**.

   >[!NOTE]
   >
   >Somente um conjunto de credenciais é necessário para cada organização, independentemente do número de instâncias AEM em que as credenciais são instaladas.

1. Verifique se você recebeu as seguintes informações:

   * accountId
   * customerId
   * password
   * identityPoolId
   * userPoolId
   * clientId

1. Como Administrador, faça logon na instância do autor do AEM onde deseja instalar as credenciais e abra **[!UICONTROL CRXDE Lite]**.
1. Configure as novas informações de credenciais fazendo o seguinte no CRXDE Lite:

   1. Navegue até `/libs/settings/dam/v3D/services/dncr` e defina a propriedade `clientId` para o novo valor.
   1. Navegue até `/libs/settings/dam/v3D/services/aws` e defina as propriedades `accountId`, `customerId`, `identityPoolId` e `userPoolId` para os novos valores.
   1. Carregue o novo valor de senha na propriedade `encryptedPassword`. Esse valor é automaticamente criptografado quando você toca em **[!UICONTROL Salvar tudo]**.
   1. Toque em **[!UICONTROL Salvar tudo]**, recarregue a página e verifique se a propriedade `encryptedPassword` mostra uma string diferente entre chaves. Essa aparência indica que a senha está criptografada e segura corretamente.

1. Especifique o formato da renderização de conversão `.glb` fazendo o seguinte em **[!UICONTROL CRXDE Lite]**:

   1. Navegue até `/libs/settings/dam/v3D/services/dncr` em **[!UICONTROL CRXDE Lite]**.
   1. Defina a propriedade `outputFormat` como `Dn` ou `generic`.

      Quando definida como `Dn`, a conversão `.glb` incluirá extensões específicas do Adobe, como iluminação IBL, para melhor qualidade ao visualizar ativos Dn no AEM. No entanto, a renderização .glb convertida pode não ser renderizada corretamente em aplicativos de terceiros.

      Quando definido como `generic`, a renderização `.glb` é genérica sem extensões específicas do Adobe. Essa configuração permite que ele seja usado em aplicativos de terceiros, enquanto a visualização com o visualizador 3D AEM será visualmente menos ideal.

1. Ative o formato de arquivo Dn fazendo o seguinte em **[!UICONTROL CRXDE Lite]**:

   1. Vá até `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. Defina a propriedade `Enabled` como true.

1. Valide a configuração fazendo o seguinte:

   1. Abra o AEM Assets.
   1. Carregue `logo_sphere.dn` para a pasta `test3d`. O arquivo está localizado em `sample-3D-content/models`.

      Observe que `sample-3D-content.zip` foi baixado anteriormente para validar a funcionalidade básica de 3D.
   1. Retorne para a **[!UICONTROL Exibição de cartão]** e observe o banner de mensagem mostrado no ativo carregado. O **[!UICONTROL Formato de Conversão...O banner]** é exibido enquanto o processo de conversão está em andamento.
   1. Após a conclusão de todo o processamento, abra o ativo em **[!UICONTROL Detail View]** para verificar se o ativo convertido é exibido corretamente e se os controles de navegação do visualizador são utilizáveis.

   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   Se um &quot;Erro de processamento&quot; for exibido no ativo Dn no **[!UICONTROL Exibição de cartão]** após 10-15 minutos, a conversão falhou.

   Nesse caso, você pode solucionar problemas de conversão fazendo o seguinte:

   * Exclua o ativo e faça upload dele novamente.
   * Certifique-se de ter definido corretamente todos os parâmetros de configuração em **[!UICONTROL CRXDE Lite]**.
   * Verifique se nenhum firewall está bloqueando o acesso ao serviço de conversão e aos pontos de extremidade AWS.
