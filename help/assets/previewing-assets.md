---
title: Visualização de ativos do Dynamic Media
seo-title: Previewing Dynamic Media assets
description: Saiba como visualizar ativos no Dynamic Media
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 5%

---

# Visualização de ativos do Dynamic Media {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode usar **[!UICONTROL Visualizar]** para ver a aparência de um ativo digital do Dynamic Media quando visualizado por um cliente em seu próprio navegador da Web. O visualizador incorporado padrão entre dispositivos atribuído ao ativo é usado para a **[!UICONTROL Visualizar]**.

Um visualizador é uma coleção de várias configurações ou &quot;predefinições&quot;, como o tamanho de exibição do visualizador, comportamento de zoom, esquemas de cores, bordas, fontes e assim por diante, que determinam como os usuários visualizam ativos de mídia avançada em suas telas de computadores e dispositivos móveis.

Além de usar o recurso de visualização dedicado para vídeos, conjuntos de rotação e conjuntos de imagens, também é possível visualizar um ativo usando predefinições do visualizador que você criou. Ou use predefinições de imagens para visualizar representações de imagens.

* [Aplicação de predefinições da imagem](image-presets.md)
* [Aplicação de predefinições do visualizador](viewer-presets.md)

>[!NOTE]
>
>Quando você está em uma página da Web (Sites) no AEM, não pode visualizar ativos no modo **[!UICONTROL Editar]**. Você precisa acessar o modo **[!UICONTROL Visualização]** clicando em **Visualização** no canto superior direito.

**Para visualizar ativos**:

1. De **Adobe Experience Manager**, no **[!UICONTROL Navegação]** página, toque em **[!UICONTROL Ativo]s**, em seguida **[!UICONTROL Arquivos]** para acessar ativos.
1. Próximo ao canto superior direito da página, da **[!UICONTROL Exibir]** lista suspensa, toque em **[!UICONTROL Exibição de lista]**.
1. (Opcional) Use o **[!UICONTROL Tipo]** para classificar os ativos pelo tipo que deseja visualizar.
1. Em **[!UICONTROL Título]** , clique no nome do título (não na imagem em miniatura) do ativo que deseja visualizar.
1. Dependendo do tipo de ativo que você clicou, siga um destes procedimentos:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo de ativo que você tocou</strong><br /> </td> 
   <td><strong>Pode visualizar o ativo em uma representação específica?</strong></td> 
   <td><strong>É possível visualizar o ativo em um visualizador específico?</strong></td> 
  </tr>
  <tr>
   <td><p>Imagem</p> </td> 
   <td>Sim</td> 
   <td>Sim</td> 
   <td><p><strong>Visualização de ativos em uma representação específica</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Representações </strong>na lista, em seguida, selecione uma representação específica que deseja visualizar.</li> 
    </ul> <p><strong>Para visualizar o ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista, em seguida, selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use o <strong>+</strong> e <strong>- </strong>para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque duas vezes na imagem para ampliar pelas etapas. Quando atingir o zoom máximo, toque duas vezes na imagem novamente para redefinir o estado do zoom. Arraste a imagem para o panorama.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>Multimídia</td> 
   <td>Sim</td> 
   <td>Sim</td> 
   <td><p><strong>Visualização de ativos em uma representação específica</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Representações </strong>na lista, em seguida, selecione uma representação específica que deseja visualizar.</li> 
    </ul> <p>Selecionar uma representação de vídeo de resolução mais alta para visualização pode fazer com que o vídeo apareça truncado. Isso ocorre porque a visualização da representação mostra a resolução exata que seus clientes a verão, tudo no contexto do visualizador incorporado usado para a visualização.</p> <p>Ao visualizar um conjunto de vídeos adaptáveis no nível do Ativo, as representações são agrupadas em uma experiência de reprodução. Ou seja, o vídeo adaptável é dimensionado corretamente para exibição e reprodução usando a melhor resolução no contexto do dispositivo de exibição e da velocidade de conexão.<br /> </p> <p><strong>Para visualizar um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista, em seguida, selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de imagens</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para visualizar um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista, em seguida, selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use o <strong>+</strong> e <strong>- </strong>para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque duas vezes na imagem para ampliar pelas etapas. Quando atingir o zoom máximo, toque duas vezes na imagem novamente para redefinir o estado do zoom. Arraste a imagem para o panorama.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de rotação</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para visualizar um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista, em seguida, selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use o <strong>+</strong> e <strong>- </strong>para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque duas vezes na imagem para ampliar pelas etapas. Quando atingir o zoom máximo, toque duas vezes na imagem novamente para redefinir o estado do zoom. Arraste a imagem para o panorama.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de mídias mistas</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para visualizar um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Clique em <strong>Visualizadores</strong> na lista, em seguida, selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Use o <strong>+</strong> e <strong>- </strong>para aumentar ou diminuir o zoom da imagem selecionada, respectivamente. Clique em <strong>Redefinir</strong> para retornar a imagem ao zoom original.<br /> Se você estiver em um dispositivo móvel, toque duas vezes na imagem para ampliar pelas etapas. Quando atingir o zoom máximo, toque duas vezes na imagem novamente para redefinir o estado do zoom. Arraste a imagem para o panorama.</p> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.</p> </td> 
  </tr>
  <tr>
   <td>Conjunto de carrossel</td> 
   <td>Não</td> 
   <td>Sim</td> 
   <td><p><strong>Para visualizar um ativo em um visualizador específico</strong></p> 
    <ul> 
     <li>Ao lado do canto superior esquerdo da página, clique no ícone para que a lista suspensa seja exibida. Selecione um visualizador que deseja aplicar ao ativo.</li> 
    </ul> <p>Para ativar ou desativar as predefinições do visualizador na interface do usuário, consulte <a href="/help/assets/managing-viewer-presets.md">Gerenciar predefinições do visualizador</a>.</p> </td> 
  </tr>
 </tbody>
</table>
