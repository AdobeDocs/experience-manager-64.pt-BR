---
title: Visualização de ativos do Dynamic Media
seo-title: Visualização de ativos do Dynamic Media
description: Saiba como pré-visualização ativos no Dynamic Media
seo-description: Saiba como pré-visualização ativos no Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 5%

---


# Visualização de ativos do Dynamic Media {#previewing-assets}

Você pode usar a **[!UICONTROL Pré-visualização]** para ver a aparência de um ativo digital do Dynamic Media quando ele é exibido por um cliente em seu próprio navegador. O visualizador incorporado e entre dispositivos padrão atribuído ao ativo é usado para a **[!UICONTROL Pré-visualização]**.

Um visualizador é uma coleção de várias configurações ou &quot;predefinições&quot;, como tamanho de exibição do visualizador, comportamento de zoom, esquemas de cores, bordas, fontes e assim por diante, que determinam como os usuários visualizações ativos de mídia avançada em suas telas de computadores e dispositivos móveis.

Além de usar o recurso de pré-visualização dedicada para vídeos, conjuntos de rotação e conjuntos de imagens, você também pode pré-visualização um ativo usando as predefinições do visualizador que você criou. Ou, use predefinições de imagens para representações de pré-visualização de imagens.

* [Aplicar predefinições de imagens](image-presets.md)
* [Aplicar predefinições do visualizador](viewer-presets.md)

>[!NOTE]
>
>Quando você está em uma página da Web (Sites) no AEM, não pode visualizar ativos no modo **[!UICONTROL Editar]**. Você precisa acessar o modo **[!UICONTROL Visualização]** clicando em **Visualização** no canto superior direito.

**Para pré-visualização de ativos**:

1. From **Adobe Experience Manager**, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Asset]s **, then**[!UICONTROL Files ]**to access assets.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL List View]**.
1. (Opcional) Use a coluna **[!UICONTROL Tipo]** para classificar os ativos pelo tipo que deseja pré-visualização.
1. Na coluna **[!UICONTROL Título]** , clique no nome do título (não na imagem em miniatura) do ativo que deseja pré-visualização.
1. Dependendo do tipo de ativo clicado, execute um dos procedimentos a seguir:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo de ativo que você tocou</strong><br /> </td> 
   <td><strong>É capaz de pré-visualização de ativos em uma representação específica?</strong></td> 
   <td><strong>É capaz de pré-visualização de ativos em um visualizador específico?</strong></td> 
  </tr>
  <tr>
   <td><p>Imagem</p> </td> 
   <td>Sim</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de ativos em uma representação específica</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Representações </strong>na lista e selecione uma representação específica que deseja pré-visualização.</li> 
    </ul> <p><strong>Para pré-visualização de ativos em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista e selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use os <strong>ícones</strong> + <strong>e </strong>- para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque com o duplo na imagem para ampliar pelas etapas. Quando você atingir o zoom máximo, toque com o duplo na imagem novamente para redefinir o estado de zoom. Arraste pela imagem para deslocar.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimídia</td> 
   <td>Sim</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de ativos em uma representação específica</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Representações </strong>na lista e selecione uma representação específica que deseja pré-visualização.</li> 
    </ul> <p>Selecionar uma execução de vídeo de resolução mais alta para a pré-visualização pode fazer com que o vídeo apareça truncado. Isso ocorre porque a pré-visualização de execução mostra a resolução exata que seus clientes verão, tudo isso no contexto do visualizador incorporado usado para a pré-visualização.</p> <p>Quando você pré-visualização um conjunto de vídeo adaptável no nível do ativo, as renderizações são agrupadas em uma única experiência de reprodução. Ou seja, o vídeo adaptável é dimensionado corretamente para exibição e reprodução usando a melhor resolução no contexto do dispositivo de exibição e da velocidade da conexão.<br /> </p> <p><strong>Para pré-visualização de um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista e selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de imagens</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista e selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use os <strong>ícones</strong> + <strong>e </strong>- para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque com o duplo na imagem para ampliar pelas etapas. Quando você atingir o zoom máximo, toque com o duplo na imagem novamente para redefinir o estado de zoom. Arraste pela imagem para deslocar.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de rotação</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista e selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use os <strong>ícones</strong> + <strong>e </strong>- para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque com o duplo na imagem para ampliar pelas etapas. Quando você atingir o zoom máximo, toque com o duplo na imagem novamente para redefinir o estado de zoom. Arraste pela imagem para deslocar.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de mídia mista</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista e selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use os <strong>ícones</strong> + <strong>e </strong>- para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque com o duplo na imagem para ampliar pelas etapas. Quando você atingir o zoom máximo, toque com o duplo na imagem novamente para redefinir o estado de zoom. Arraste pela imagem para deslocar.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de carrossel</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para pré-visualização de um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Próximo ao canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Selecione um visualizador que você deseja aplicar ao ativo.</li> 
    </ul> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciamento de predefinições</a>do visualizador.</p> </td> 
  </tr>
 </tbody>
</table>

