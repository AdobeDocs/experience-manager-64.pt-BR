---
title: Baixe ativos digitais de [!DNL Adobe Experience Manager].
description: Saiba como baixar ativos do  [!DNL Adobe Experience Manager] e ativar ou desativar a funcionalidade de download.
contentOwner: AG
feature: Asset Management,Asset Distribution
role: User
exl-id: bfe4d597-1080-4de5-a100-73a5175863d7
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 3%

---

# Baixar ativos de [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Você pode baixar ativos, incluindo representações estáticas e dinâmicas. Como alternativa, você pode enviar emails com links para ativos diretamente de [!DNL Adobe Experience Manager Assets]. Os ativos baixados são agrupados em um arquivo ZIP. O arquivo ZIP compactado tem um tamanho máximo de arquivo de 1 GB para o trabalho de exportação. É permitido um máximo de 500 ativos totais por trabalho de exportação.

>[!NOTE]
>
>Os recipients de emails devem ser membros do grupo `dam-users` para acessar o link de download do ZIP na mensagem de email. Para baixar os ativos, os membros devem ter permissões para iniciar fluxos de trabalho que acionam o download de ativos.

Os tipos de ativos Conjuntos de imagens, Conjuntos de rotação, Conjuntos de mídia mista e Conjuntos de carrossel não podem ser baixados.

Para baixar ativos, siga estas etapas:

1. No canto superior esquerdo do AEM, toque no logotipo [!DNL Experience Manager] e, em seguida, no painel à esquerda, toque em **[!UICONTROL Navegação]**.
1. Na página Navegação, toque em **[!UICONTROL Ativos]** > **[!UICONTROL Arquivos.]**
1. Navegue até uma pasta que contenha ativos que você deseja baixar.
1. Selecione a pasta ou selecione um ou mais ativos na pasta.
1. Na barra de ferramentas, toque em **[!UICONTROL Download.]**

   ![Opções disponíveis ao baixar ativos do Experience Manager Assets](/help/assets/assets/asset_download_dialog.png)

   *Figura: Opções da caixa de diálogo Download.*

1. Na caixa de diálogo Download, selecione as opções de download desejadas.

   | Opção de exportação ou download | Descrição |
   |---|---|
   | **[!UICONTROL Criar uma pasta separada para cada ativo]** | Selecione essa opção para incluir cada ativo que você baixar, incluindo ativos em pastas filhas aninhadas na pasta principal do ativo, em uma pasta no computador local. Quando essa opção não é selecionada, por padrão, a hierarquia de pastas é ignorada e todos os ativos são baixados em uma pasta no computador local. |
   | **[!UICONTROL Email]** | Uma notificação por email é enviada ao usuário. Os modelos padrão de emails estão disponíveis nos seguintes locais:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Os modelos personalizados durante a implantação estão disponíveis nos seguintes locais: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Você pode armazenar modelos personalizados específicos do locatário nos seguintes locais:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Ativos]** | Selecione essa opção para baixar o ativo em seu formulário original sem nenhuma representação.<br>A opção de subativos estará disponível se o ativo original tiver subativos. |
   | **[!UICONTROL Representações]** | Uma representação é uma representação binária de um ativo. Os ativos têm uma representação principal: a do arquivo carregado. Eles podem ter qualquer número de representações. <br> Com essa opção, você pode selecionar as representações que deseja baixar. As representações disponíveis dependem do ativo selecionado. A opção estará disponível se o ativo tiver renderizações. |
   | **[!UICONTROL Representações dinâmicas]** | Selecione essa opção para gerar uma série de representações alternativas em tempo real. Ao selecionar essa opção, você também seleciona as representações que deseja criar dinamicamente selecionando na lista [Predefinição de imagem](image-presets.md). <br>Além disso, é possível selecionar o tamanho e a unidade de medida, o formato, o espaço de cores, a resolução e qualquer modificador de imagem opcional, como inverter a imagem. A opção só estará disponível se você tiver [!DNL Dynamic Media] ativado. |

1. Na caixa de diálogo, toque em **[!UICONTROL Download.]**.

Ao selecionar uma pasta para baixar, a hierarquia completa do ativo na pasta é baixada. Para incluir cada ativo que você baixar (incluindo ativos em pastas filhas aninhadas na pasta principal) em uma pasta individual, selecione **[!UICONTROL Criar pasta separada para cada ativo]**.

## Habilitar servlet de download de ativos {#enable-asset-download-servlet}

O servlet padrão em [!DNL Experience Manager] permite que usuários autenticados emitam solicitações de download arbitrariamente grandes e simultâneas para criar arquivos ZIP de ativos visíveis para eles que podem sobrecarregar o servidor e a rede. Para atenuar possíveis riscos de DoS causados por esse recurso, o componente `AssetDownloadServlet` OSGi é desabilitado por padrão para instâncias de publicação.

Para permitir o download de ativos do DAM, digamos ao usar algo como o Asset Share Commons ou outra implementação semelhante a portal, ative manualmente o servlet por meio de uma configuração OSGi. A Adobe recomenda definir o tamanho de download permitido o mais baixo possível sem afetar os requisitos diários de download. Um alto valor pode afetar o desempenho.

1. Crie uma pasta com uma convenção de nomenclatura que seja direcionada ao modo de execução de publicação (`config.publish`): `/apps/<your-app-name>/config.publish`. Para definir as propriedades de configuração para um modo de execução, consulte [Executar Modos](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Na pasta de configuração, crie um arquivo do tipo `nt:file` chamado `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Preencha `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` com o seguinte. Define um tamanho máximo (em bytes) para o download como valor de `asset.download.prezip.maxcontentsize`. A amostra abaixo configura o tamanho máximo do download ZIP para não exceder 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Desativar o servlet de download de ativos {#disable-asset-download-servlet}

O `Asset Download Servlet` pode ser desativado em [!DNL Experience Manager] Instâncias de publicação atualizando a configuração do dispatcher para bloquear qualquer solicitação de download de ativos. O servlet também pode ser desabilitado manualmente por meio do console OSGi diretamente.

1. Para bloquear solicitações de download de ativos por meio de uma configuração de dispatcher, edite a configuração `dispatcher.any` e adicione uma regra à seção de filtro [a2/>. `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter)

1. Para desativar o componente OSGi em uma instância de publicação, acesse o console OSGi em `http://[aem_server]:[port]/system/console/components`. Localize `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` e clique em **[!UICONTROL Desativar]**.

>[!MORELIKETHIS]
>
>* [Baixar ativos](drm.md) protegidos por DRM.
>* [Baixe ativos usando o aplicativo de desktop do Experience Manager no desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=pt-BR) Win ou Mac.
>* [Baixe ativos usando o Adobe Assets Link nos aplicativos](https://helpx.adobe.com/br/enterprise/using/manage-assets-using-adobe-asset-link.html) compatíveis com a Adobe Creative Cloud.

