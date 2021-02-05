---
title: Vídeo
description: Saiba mais sobre o gerenciamento centralizado de ativos de vídeo no qual você pode fazer upload de vídeos para ativos de Experience Manager para autocodificação no Dynamic Media Classic. Você também pode acessar vídeos do Dynamic Media Classic diretamente dos Ativos do Experience Manager. A integração de vídeo do Dynamic Media Classic estende o alcance de vídeos otimizados a todas as telas com detecção automática de dispositivos e largura de banda.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
translation-type: tm+mt
source-git-commit: 53fab119fc178e5ac88257cab1e930d4472eaa14
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Vídeo {#video}

Os ativos fornecem gerenciamento centralizado de ativos de vídeo, onde você pode fazer upload de vídeos diretamente para os Ativos para autocodificação para o Dynamic Media Classic. Você também pode acessar vídeos do Dynamic Media Classic diretamente de Ativos para criação de página.

A integração de vídeo do Dynamic Media Classic estende o alcance do vídeo otimizado para todas as telas (detecção automática de dispositivo e largura de banda).

O componente **[!UICONTROL Scene7 Video]** executa automaticamente a detecção de dispositivos e largura de banda para reproduzir o formato correto e o vídeo de qualidade correta em desktops, tablets e dispositivos móveis.

Você pode incluir conjuntos de vídeo adaptáveis em vez de apenas ativos de vídeo único. Um conjunto de vídeo adaptável é um container para todas as execuções de vídeo necessárias para reproduzir o vídeo sem problemas em várias telas. Um Conjunto de vídeos adaptáveis agrupa versões do mesmo vídeo que são codificadas em diferentes taxas de bits e formatos. Por exemplo, 400 kbps, 800 kbps e 1000 kbps. Use um Conjunto de vídeos adaptáveis, juntamente com o componente de vídeo S7, para streaming de vídeo adaptável em vários tipos de tela. Por exemplo, dispositivos móveis desktop, iOS, Android, BlackBerry e Windows.

Consulte [a documentação do Dynamic Media Classic sobre conjuntos de vídeo adaptáveis para obter mais informações](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## Sobre o FFMPEG e o Dynamic Media Classic {#about-ffmpeg-and-scene}

O processo de codificação de vídeo padrão se baseia no uso da integração em FFMPEG com perfis de vídeo. Portanto, o fluxo de trabalho de ingestão DAM predefinido contém as duas etapas de fluxo de trabalho baseadas em ffmpeg a seguir:

* Miniaturas de FFMPEG
* Codificação FFMPEG

Ativar e configurar a integração do Dynamic Media Classic não remove nem desativa automaticamente essas duas etapas do fluxo de trabalho do fluxo de trabalho de ingestão DAM predefinido. Se você já usar a codificação de vídeo baseada em FFMPEG no Experience Manager, é provável que tenha o FFMPEG instalado nos ambientes de criação. Nesse caso, um novo vídeo assimilado usando DAM seria codificado duas vezes: uma vez do codificador FFMPEG e uma vez da integração com o Dynamic Media Classic.

Se você tiver a codificação de vídeo baseada em FFMPEG configurada em AEM e FFMPEG instalada, poderá remover os dois workflows FFMPEG dos workflows de ingestão de DAM.

## Formatos suportados {#supported-formats}

Os seguintes formatos são compatíveis com o componente de vídeo do Scene7:

* F4V H.264
* MP4 H.264

## Como decidir onde fazer upload de seu vídeo {#deciding-where-to-upload-your-video}

Para decidir onde fazer upload de seus ativos de vídeo, considere o seguinte:

* O ativo de vídeo requer um fluxo de trabalho?
* O ativo de vídeo requer controle de versão?

Se a resposta for “sim” para ambas as perguntas, faça upload do vídeo diretamente no Adobe DAM. Se a resposta for &quot;não&quot; para ambas as perguntas, faça upload do vídeo diretamente para o Dynamic Media Classic. O fluxo de trabalho para cada cenário está descrito nas próximas seções.

### Se você estiver carregando seu vídeo diretamente para Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Se você precisar de um fluxo de trabalho ou controle de versão para seus ativos, carregue primeiro no Adobe DAM. Este é o fluxo de trabalho recomendado:

1. Faça upload do ativo de vídeo para Adobe DAM e codifique e publique automaticamente no Dynamic Media Classic.
1. No Experience Manager, acesse ativos de vídeo no WCM na guia **[!UICONTROL Filmes]** do Localizador de conteúdo.
1. Autor com o componente **[!UICONTROL Scene7 Video]** ou **[!UICONTROL Foundation Video]**.

### Se estiver fazendo upload do vídeo no Scene7 {#if-you-are-uploading-your-video-to-scene}

Se você não precisar de um fluxo de trabalho ou controle de versão para seus ativos, faça upload dos ativos para a Scene7. Este é o fluxo de trabalho recomendado:

1. No Dynamic Media Classic, [configure um carregamento e codificação FTP programados para o Scene7 (automatizado pelo sistema)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. No Experience Manager, acesse ativos de vídeo no WCM na guia **[!UICONTROL Scene7]** do Localizador de conteúdo.
1. Autor com o componente **[!UICONTROL Scene7 Video]**.

## Configurar a integração de vídeo do Scene7 {#configuring-integration-with-scene-video}

Para configurar predefinições universais:

1. Em **[!UICONTROL Serviços em nuvem]**, navegue até a configuração do **[!UICONTROL Scene7]** e clique em **[!UICONTROL Editar]**.
1. Selecione a guia **[!UICONTROL Vídeo]**.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >A guia **[!UICONTROL Vídeo]** não será exibida se a página não possuir uma configuração de nuvem.

1. Selecione o perfil de codificação de vídeo adaptável, um perfil de codificação de vídeo pronto para uso ou um perfil de codificação de vídeo personalizado.

   >[!NOTE]
   >
   >Para obter mais informações sobre o que as predefinições de vídeo significam, consulte a [documentação do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >A Adobe recomenda selecionar ambos os conjuntos de vídeos adaptáveis ao configurar as predefinições universais ou selecionar a opção **[!UICONTROL Codificação de vídeo adaptável]**.

1. Os perfis de codificação selecionados são aplicados automaticamente a todos os vídeos enviados por upload para a pasta de destino DAM CQ configurada para essa configuração de nuvem do Scene7. É possível configurar várias configurações de nuvem do Scene7 com diferentes pastas de destino para aplicar diversos perfis de codificação, conforme necessário.

## Atualizar as predefinições de codificação e do visualizador  {#updating-viewer-and-encoding-presets}

Se as predefinições foram atualizadas no Scene7, é necessário atualizar o visualizador e as predefinições de codificação para vídeo no Experience Manager. Nesses casos, navegue até a configuração do Scene7 na configuração da nuvem e clique em **[!UICONTROL Atualizar o visualizador e as predefinições de codificação]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Carregar seu vídeo principal para o Scene7 a partir do Adobe DAM {#uploading-your-master-video}

1. Navegue até a pasta de destino DAM CQ onde você definiu as configurações de nuvem com os perfis de codificação do Scene7.
1. Clique em **[!UICONTROL Fazer upload]** para fazer upload do vídeo mestre. O upload e a codificação do vídeo são concluídos depois que o fluxo de trabalho do Ativo de atualização do DAM é concluído e **[!UICONTROL Publicar no Scene7]** tem uma marca de seleção.

   >[!NOTE]
   >
   >Leva algum tempo para que as miniaturas de vídeo sejam geradas.

   Arrastar o vídeo principal do DAM para o componente de vídeo acessa *all* as renderizações de proxy codificadas do Scene7 para o delivery.

## Comparação do componente de vídeo de base com o componente de vídeo do Scene7 {#foundation-video-component-versus-scene-video-component}

Ao usar o Experience Manager, você tem acesso ao componente Vídeo disponível no Sites e ao componente de vídeo do Scene7. Esses componentes não são intercambiáveis.

O componente de vídeo do Scene7 funciona somente para vídeos do Scene7. O componente básico funciona com vídeos armazenados do Experience Manager (usando o ffmpeg) e vídeos do Scene7.

A matriz a seguir explica quando usar qual componente:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>O componente de vídeo S7 usa o perfil de vídeo universal. No entanto, você pode obter o player de vídeo baseado em HTML5 no Experience Manager. Basta copiar o código incorporado do player de vídeo HTML5 e colocá-lo na sua página de Experience Manager.

## Componente de vídeo Experience Manager {#aem-video-component}

Mesmo se o uso do componente de vídeo do Scene7 for recomendado para a visualização de vídeos do Scene7, use vídeos do Scene7 com o Componente de vídeo básico, para obter mais detalhes.

### Comparação de vídeo Experience Manager e vídeo Scene7 {#aem-video-and-scene-video-comparison}

A tabela a seguir fornece uma comparação de alto nível dos recursos suportados entre o componente Experience Manager Foundation Video e o componente Scene7 Video:

|  | Vídeo sobre Experience Manager Foundation | Vídeo do Scene7 |
|---|---|---|
| Abordagem | Abordagem de HTML5 primeiro. O Flash é usado somente para o fallback não-HTML5. | Flash na maioria dos computadores. O HTML5 é usado para dispositivos móveis e tablets. |
| Entrega | Progressiva | Transmissão adaptável |
| Acompanhamento | Sim | Sim |
| Extensibilidade | Sim | Sim (com [Documentação da API do SDK do Visualizador HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Vídeo móvel | Sim | Sim |

### Configuração  {#setting-up}

#### Criação de perfis de vídeo {#creating-video-profiles}

As várias codificações de vídeo são criadas de acordo com as predefinições de codificação do Scene7 selecionadas na configuração da nuvem do Scene7. Para que o componente Foundation Video os use, é necessário criar um perfil de vídeo para cada predefinição de codificação do Scene7 selecionada. Esse método permite que o componente de vídeo selecione as execuções de DAM de acordo.

>[!NOTE]
>
>Os novos perfis de vídeo e as alterações a eles devem ser ativados para publicação.

1. No Experience Manager, toque em **[!UICONTROL Ferramentas] > [!UICONTROL Console de Configuração]**.
1. Na **[!UICONTROL Console de configuração]** navegue até **[!UICONTROL Ferramentas > DAM > Perfis de vídeo]** na árvore de navegação.
1. Crie um Perfil Scene7 Video. No **[!UICONTROL Novo...]** lista suspensa, selecione **[!UICONTROL Criar página]** e selecione o modelo de Perfil Scene7 Video. Forneça um nome para a nova página de perfil de vídeo e clique em **[!UICONTROL Criar]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Edite o novo perfil de vídeo. Selecione primeiro a configuração de nuvem. Em seguida, selecione a mesma predefinição de codificação selecionada na configuração de nuvem.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Propriedade | Descrição |
   |---|---|
   | Configurações de nuvem do Scene7 | A configuração da nuvem a ser usada para as predefinições de codificação. |
   | Predefinição de codificação do Scene7 | A predefinição de codificação para mapear este perfil de vídeo. |
   | Tipo de vídeo HTML5 | Essa propriedade permite definir o valor da propriedade type do elemento de fonte de vídeo HTML5. Essa informação não é fornecida pelas predefinições de codificação do S7, mas é necessária para renderizar corretamente os vídeos usando o elemento de vídeo HTML5. Uma lista de formatos comuns é fornecida, mas eles podem ser substituídos por outros formatos. |

   Repita essa etapa para todas as predefinições de codificação selecionadas na configuração de nuvem que você deseja usar no componente de vídeo.

#### Configurando o design {#configuring-design}

O componente **[!UICONTROL Foundation Video]** deve saber quais perfis de vídeo serão usados para criar a lista de fontes de vídeo. Abra a caixa de diálogo de design de componentes de vídeo e configure o design de componentes para usar os novos perfis de vídeo.

>[!NOTE]
>
>Se você usar o componente **[!UICONTROL Foundation Video]** em uma página móvel, repita essas etapas no design da página móvel.

>[!NOTE]
>
>As alterações feitas no design exigem a ativação do design para que possam entrar em vigor na publicação.

1. Abra a caixa de diálogo de design do componente **[!UICONTROL Foundation Video]** e mude para a guia **[!UICONTROL Perfis]**. Em seguida, exclua os perfis predefinidos e adicione os novos perfis de vídeo S7. A ordem da lista do perfil na caixa de diálogo de design define a ordem do elemento de fontes de vídeo ao renderizar.
1. Para navegadores que não suportam HTML5, o componente de vídeo permite configurar um fallback de Flash. Abra a caixa de diálogo de design de componentes de vídeo e mude para a guia **[!UICONTROL Flash]**. Configure as configurações do Flash Player e atribua um perfil de fallback para o Flash Player.

#### Lista de verificação {#checklist}

1. Criar uma configuração da nuvem S7. Verifique se as predefinições de codificação de vídeo estão definidas e se o importador está em execução.
1. Crie um perfil de vídeo do S7 para cada predefinição de codificação de vídeo selecionada na configuração da nuvem.
1. Os perfis de vídeo devem ser ativados.
1. Configure o design do componente **[!UICONTROL Foundation Video]** na sua página.
1. Ative o design após finalizar as alterações no design.

