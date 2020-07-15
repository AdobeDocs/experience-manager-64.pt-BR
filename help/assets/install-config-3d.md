---
title: Instalação e configuração do AEM 3D
seo-title: Instalação e configuração do AEM 3D
description: Saiba como instalar e configurar o AEM 3D
seo-description: Saiba como instalar e configurar o AEM 3D
uuid: a60732ff-fd66-4f29-b901-42a3cfd58b65
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5898d084-4b45-41bc-ad2e-2fcc65b0392c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '1634'
ht-degree: 0%

---


# Instalação e configuração do AEM 3D {#installing-and-configuring-aem-d}

A instalação e configuração do AEM 3D (versão 3.0) envolve o seguinte:

1. Instalação da biblioteca SDK do Autodesk® FBX®.
1. Download e instalação do pacote de código 3D nativo.
1. Configurar o fluxo de trabalho de ingestão de ativos 3D e reiniciar o AEM.
1. Validação da configuração do AEM 3D.

Consulte também [Trabalhar com ativos](assets-3d.md)3D.

Consulte também as notas [de versão dos ativos](/help/release-notes/aem3d-release-notes.md) AEM 3D para obter pré-requisitos, navegadores compatíveis e outras importantes informações de versão.

Consulte também [Trabalhar com o componente](using-the-3d-sites-component.md)Sites 3D.

>[!NOTE]
>
>Antes de baixar e instalar o pacote 3D, verifique se você instalou todos os pacotes AEM de pré-requisito com êxito. See the [AEM 3D Release Notes.](install-config-3d.md)

## Instalação da biblioteca de SDK do Autodesk FBX {#installing-the-autodesk-fbx-sdk-library}

O código AEM 3D nativo requer a biblioteca FBX do Autodesk para suportar o formato de arquivo FBX. (No momento, a Adobe não pode redistribuir essa biblioteca.)

Consulte também Configurações [](advanced-config-3d.md)avançadas.

1. Faça logon no host onde o AEM está instalado.

   * Se esta for uma implantação do Windows Server, faça logon no servidor como Administrador.
   * Se for uma área de trabalho MAC ou Windows, verifique se você tem privilégios de administrador.

1. Use o link apropriado para o seu sistema operacional para baixar o SDK **FBX versão 2016.1.2**

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. Instale o SDK do FBX:

   * Windows. Instale na mesma unidade em que o AEM está localizado.
   * Mac. Instale na mesma partição em que o AEM está localizado.
   * Linux. Extraia o pacote baixado e siga as instruções em `<yourFBXSDKpath>/Install_FbxFileSdk.txt`. Instale o SDK para `/usr`.

## Download e instalação do pacote de código 3D nativo {#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>Antes de continuar com a instalação e configuração do AEM 3D, a Adobe recomenda que você implante todos os service packs e outros recursos relacionados aplicáveis. See [AEM 3D Release Notes](/help/release-notes/aem3d-release-notes.md).

Consulte também Configurações [](advanced-config-3d.md)avançadas.

**Para instalar o pacote** de código 3D nativo:

1. Faça uma das seguintes opções:

   * Se esta for uma implantação do Windows Server, faça logon no servidor como Administrador.
   * Se for uma área de trabalho Mac ou Windows, verifique se você tem privilégios de Administrador.

1. Verifique se você tem um navegador compatível disponível para acessar o AEM.

   Consulte Requisitos [do sistema](/help/release-notes/aem3d-release-notes.md#system-requirements).

1. Acesse o portal [de distribuição de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)software. Localize a versão 3.0.1 do pacote de `AEM-6.4-DynamicMedia-3D` recursos e baixe-a.

1. No AEM, clique em **[!UICONTROL Ferramentas > Administração > Implantação > Gerenciador]** de pacotes.

1. Carregue o pacote de recursos baixado no AEM. Localize-o e clique em **[!UICONTROL Instalar]**.

1. Na caixa de diálogo **[!UICONTROL Instalar pacote]** , expanda Configurações **** avançadas e defina Manuseio **[!UICONTROL de]** Controle de acesso como **Mesclar**.
1. Clique em **[!UICONTROL Instalar]** para iniciar a instalação do pacote.

   O arquivo `sample-3D-content.zip` é colocado na pasta raiz **[!UICONTROL Assets]** . Consulte [Validação da configuração do AEM 3D](#validating-the-setup-of-aem-d) para obter mais informações.

## Configurar o fluxo de trabalho de ingestão de ativos 3D e reiniciar o AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**Para configurar o fluxo de trabalho** de ingestão de ativos 3D:

1. No AEM, clique no logotipo do AEM para acessar o console de navegação global, clique no ícone **[!UICONTROL Ferramentas]** e navegue até **[!UICONTROL Fluxo de trabalho > Modelos]**.
1. Na página Modelos **[!UICONTROL de]** fluxo de trabalho, passe o mouse sobre o fluxo de trabalho Atualizar ativo **[!UICONTROL do]** DAM e, quando a marca de seleção for exibida, selecione-a.

1. Na barra de ferramentas, clique em **[!UICONTROL Editar]**.
1. Na tela Atualizar ativo **[!UICONTROL do]** DAM, no painel flutuante do AEM, clique no ícone **[!UICONTROL Plus]** à direita de Fluxo de trabalho para expandir a lista. Selecione Etapa **[!UICONTROL do]** processo na lista.
1. Arraste a Etapa **[!UICONTROL do]** processo e solte-a no fluxo de trabalho imediatamente antes do componente Fluxo de trabalho de atualização do ativo **[!UICONTROL DAM concluído]** próximo ao final do fluxo de trabalho.

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. Clique com o Duplo do mouse na etapa de processo recém-adicionada.
1. Na caixa de diálogo Propriedades **[!UICONTROL da]** etapa, na guia **[!UICONTROL Comum]** , no campo **[!UICONTROL Título]** , digite uma descrição adequada para o processo, como `Process 3D content`.
1. Click the **[!UICONTROL Process]** tab.

1. No menu suspenso **[!UICONTROL Processo]** , selecione Serviço **[!UICONTROL de objeto 3D]** geométrico e marque a caixa de seleção Avanço **[!UICONTROL do]** manipulador.

   ![3d_install-process-steppropertiesdlg](assets/3d_install-process-steppropertiesdlg.png)

1. Perto do canto superior direito da caixa de diálogo, clique no ícone de marca de seleção para retornar à página Atualizar ativo DAM.
1. Perto do canto superior direito da página Atualizar ativo **[!UICONTROL do]** DAM, clique em **[!UICONTROL Sincronizar]** para salvar o modelo de fluxo de trabalho editado.
1. Reinicie o AEM.

   Após a reinicialização, você está pronto para carregar conteúdo 3D e fazer com que o AEM o processe.

   Continue com [Validação da configuração do AEM 3D](#validating-the-setup-of-aem-d).

## Validação da configuração do AEM 3D {#validating-the-setup-of-aem-d}

1. No AEM, clique em **[!UICONTROL Ferramentas > Ativos]**, baixe `sample-3D-content.zip`e expanda o arquivo baixado. (Agora você pode excluir `sample-3D-content.zip` no AEM.)

   Verifique se você está na Visualização **[!UICONTROL de]** cartão para fazer upload e processar feedback de visualização nas etapas restantes.

1. Crie uma pasta chamada `test3d` para receber conteúdo de teste.
1. Faça upload de todos os arquivos `sample-3D-content/images` para a `test3d` pasta.
1. Aguarde a conclusão do upload e do processamento. Talvez seja necessário atualizar o navegador.

   Faça upload dos três `.fbx` arquivos `sample-3D-content/` para a `test3d` pasta.

   Ainda não carregue os arquivos do modelo .ma.

1. Na Visualização de cartão, observe os banners de mensagem exibidos nos cartões de ativos 3d.

   Cada ativo continua por várias etapas de processamento. Quando a Pré-visualização **[!UICONTROL de criação...]** etapa de processamento concluída, o cartão é atualizado com uma imagem em miniatura. Quando o processamento final estiver concluído, o banner será substituído pelo indicador **[!UICONTROL NEW]** .

   >[!NOTE]
   >
   >Espere uma utilização muito alta da CPU enquanto o processamento 3D estiver em andamento. Dependendo da capacidade disponível da CPU, pode levar bastante tempo para concluir todo o processamento.

   ![captura de tela_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. Agora você aprenderá a resolver dependências de arquivos.

   No banner Dependências **** Não Resolvidas do `stage-helipad.fbx` cartão, clique no ícone **[!UICONTROL Ponto]** de Exclamação para navegar até as propriedades do ativo e abrir a guia **Dependências** .

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. Clique no ícone **[!UICONTROL Pasta/Lupa]** à direita do nome do arquivo para abrir o navegador de ativos e resolver as dependências da seguinte maneira:

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. Clique em **[!UICONTROL Salvar]** e **[!UICONTROL Fechar]** para concluir o processamento do ativo e retornar à Visualização **[!UICONTROL de]** cartão, respectivamente.
1. Quando o processamento estiver concluído, você verá o seguinte na Visualização **[!UICONTROL da]** placa:

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. Na página test3d, clique no `logo-sphere.fbx` cartão para abrir o modelo em **[!UICONTROL Detail Visualização]**.

   Próximo ao canto superior direito da página logo-spero.fbx, clique no ícone Destaque do Palco para expandir o menu suspenso e selecione `stage-spotlights.fbx`.

   ![chlimage_1-375](assets/chlimage_1-375.png)

1. Na lista suspensa **[!UICONTROL Destaque]** do palco, selecione `stage-helipad.fbx`.

   Usando o botão esquerdo do mouse para ajustar a visualização. A iluminação do plano de fundo e do modelo muda para refletir a nova seleção de estágio.

   ![chlimage_1-376](assets/chlimage_1-376.png)

## Configurar suporte para ativos do Adobe Dimension {#configuring-support-for-adobe-dimension-assets}

>[!NOTE]
>
>Esta tarefa de configuração é opcional.

Como opção, você pode configurar o suporte no AEM 3D para ativos do Adobe Dimension.

Você deve configurar um serviço de conversão externo para permitir a ingestão, pré-visualização e publicação de ativos 3D do Adobe Dimension no AEM. O serviço converte do formato exclusivo Adobe Dimension (`.dn`) em uma variante de glTF (formatado como um `.glb` arquivo) que é salva com o ativo Dn como uma execução. A `.glb` execução é usada para a visualização baseada na Web do ativo 3D em AEM Assets, sites e telas, e também está disponível para download para uso com aplicativos de terceiros.

>[!NOTE]
>
>O serviço de conversão é hospedado pela Adobe no Amazon AWS. Depois de configurar corretamente o serviço, `.dn` os arquivos carregados no AEM são copiados com segurança para o serviço de conversão por meio de armazenamento temporário no Amazon S3. O resultado da conversão é transferido de volta para o AEM por meio de um armazenamento S3 temporário. Todas as transferências e armazenamentos são garantidas. Além disso, o conteúdo persiste no S3 e o serviço de conversão apenas brevemente (normalmente não mais do que alguns minutos).

**Para configurar o suporte para ativos** do Adobe Dimension:

1. Entre em contato com seu gerente de contas, especialista em provisionamento ou representante de suporte do Adobe AEM para solicitar credenciais para os Serviços **** AEM3D.

   >[!NOTE]
   >
   >Somente um conjunto de credenciais é necessário para cada organização, independentemente do número de instâncias do AEM nas quais as credenciais estão instaladas.

1. Verifique se você recebeu as seguintes informações:

   * accountId
   * customerId
   * password
   * identityPoolId
   * userPoolId
   * clientId

1. Como Administrador, faça logon na instância do autor de AEM onde deseja instalar as credenciais e abra o **[!UICONTROL CRXDE Lite]**.
1. Configure as novas informações de credenciais fazendo o seguinte no CRXDE Lite:

   1. Navegue até `/libs/settings/dam/v3D/services/dncr` `clientId` a propriedade e defina-a para o novo valor.
   1. Navegue até `/libs/settings/dam/v3D/services/aws` e defina as propriedades `accountId`, `customerId`, `identityPoolId`e `userPoolId` para os novos valores.
   1. Carregue o valor da nova senha na `encryptedPassword` propriedade. Esse valor é automaticamente criptografado quando você toca em **[!UICONTROL Salvar tudo]**.
   1. Toque em **[!UICONTROL Salvar tudo]**, recarregue a página e verifique se a `encryptedPassword` propriedade mostra uma string diferente entre chaves. Essa aparência indica que a senha está criptografada e segura corretamente.

1. Especifique o formato da representação de `.glb` conversão, fazendo o seguinte no **[!UICONTROL CRXDE Lite]**:

   1. Navegue até `/libs/settings/dam/v3D/services/dncr` no **[!UICONTROL CRXDE Lite]**.
   1. Defina a `outputFormat` propriedade como `Dn` ou `generic`.

      Quando definida como `Dn`, a conversão `.glb` inclui extensões específicas da Adobe, como iluminação IBL, para melhor qualidade ao exibir ativos Dn no AEM. No entanto, a execução .glb convertida pode não ser renderizada corretamente em aplicativos de terceiros.

      Quando definida como `generic`, a execução `.glb` é genérica sem extensões específicas da Adobe. Essa configuração permite que ele seja usado em aplicativos de terceiros, enquanto a visualização com o visualizador AEM 3D estará visualmente aquém do ideal.

1. Ative o formato de arquivo Dn fazendo o seguinte no **[!UICONTROL CRXDE Lite]**:

   1. Vá até `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. Defina a `Enabled` propriedade como true.

1. Valide a configuração fazendo o seguinte:

   1. Abra AEM Assets.
   1. Carregue `logo_sphere.dn` para a `test3d` pasta. O arquivo está localizado em `sample-3D-content/models`.

      Observe que `sample-3D-content.zip` foi baixado anteriormente para validar a funcionalidade básica 3D.
   1. Retorne à Visualização **[!UICONTROL do]** cartão e observe o banner de mensagem mostrado no ativo carregado. O Formato de **[!UICONTROL Conversão...]** o banner é exibido enquanto o processo de conversão está em andamento.
   1. Depois que todo o processamento for concluído, abra o ativo em Visualização **** Detalhada para verificar se o ativo convertido é exibido corretamente e se os controles de navegação do visualizador são utilizáveis.

   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   Se um &quot;Erro de processamento&quot; for exibido no ativo Dn na Visualização **[!UICONTROL do]** cartão após 10 a 15 minutos, a conversão falhou.

   Nesse caso, você pode solucionar o problema da conversão fazendo o seguinte:

   * Exclua o ativo e faça upload dele novamente.
   * Verifique se você definiu corretamente todos os parâmetros de configuração no **[!UICONTROL CRXDE Lite]**.
   * Verifique se nenhum firewall está bloqueando o acesso ao serviço de conversão e aos pontos de extremidade AWS.
