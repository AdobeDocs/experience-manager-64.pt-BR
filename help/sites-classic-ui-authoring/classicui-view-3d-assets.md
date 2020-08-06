---
title: Exibir ativos 3D
seo-title: Exibir ativos 3D
description: ' O visualizador 3D interativo está disponível na página de detalhes do ativo no AEM. O visualizador inclui, entre outras coisas, uma coleção de controles de câmera interativos que permitem girar, aplicar zoom e deslocar o ativo 3D.'
seo-description: ' O visualizador 3D interativo está disponível na página de detalhes do ativo no AEM. O visualizador inclui, entre outras coisas, uma coleção de controles de câmera interativos que permitem girar, aplicar zoom e deslocar o ativo 3D.'
uuid: 06dea4d6-c33a-45da-a9a7-7caae9d1717a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 5e1e0039-670e-4051-9f2a-e88162482467
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 70%

---


# Exibir ativos 3D{#viewing-d-assets}

 O visualizador 3D interativo está disponível na página de detalhes do ativo no AEM. O visualizador inclui, entre outras coisas, uma coleção de controles de câmera interativos que permitem girar, aplicar zoom e deslocar o ativo 3D.

![chlimage_1-16](assets/chlimage_1-16.png)

Além de utilizar os palcos padrão no AEM 3D, também é possível usar os palcos criados em um aplicativo de terceiros e enviados por upload para o AEM.

Consulte [Sobre o uso de palcos no AEM 3D](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md).

>[!NOTE]
>
>Para ver um ativo 3D, seu dispositivo ou navegador de desktop devem ser habilitados para WebGL. Além disso, o hardware gráfico subjacente deve ter recursos e memória suficientes para renderizar os modelos do tamanho desejado.

## Considerações de desempenho ao visualizar os ativos 3D {#performance-considerations-when-you-view-d-assets}

O tempo que leva para abrir um ativo 3D na exibição de página dos detalhes do ativo depende de vários fatores. Esses fatores incluem informações como as seguintes:

* Largura de banda e latências ao servidor.
* Tamanho modelo (número de faces).
* Número e tamanho dos mapas.
* Complexidade do palco. Por exemplo, o tamanho da imagem IBL.

Além disso, os recursos do computador cliente, como uma estação de trabalho, um notebook ou um dispositivo de toque móvel, também são importantes de se considerar ao manipular a câmera interativamente. Um sistema bastante eficiente com bons recursos gráficos pode tornar a experiência de visualização interativa em 3D mais fácil e favorável.

**Para exibir os ativos 3D**:

1. Verifique se você fez upload dos ativos 3D no AEM.

   Consulte [Sobre o upload e o processamento de ativos 3D no AEM](/help/sites-classic-ui-authoring/classicui-upload-proc-3d.md).
1. No **[!UICONTROL Adobe Experience Manager]**, na página **[!UICONTROL Navegação]**, toque em **[!UICONTROL Assets]**.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.

1. Navegue até o ativo 3D que deseja visualizar.
1. Toque no cartão de ativo 3D para abri-lo na página de detalhes do ativo.

1. Siga um destes procedimentos:

   * No canto inferior direito da página de detalhes do ativo, use a paleta de controle de câmera para alterar as diferentes exibições do ativo.

      Se você usar um dispositivo sem entrada de toque e sem botão de rolagem, como o mouse clássico de um único botão da Apple, ainda poderá alterar o zoom ou a perspectiva de um ativo 3D nos respectivos modos. Você executa a ação pressionando e mantendo a tecla `SHIFT` pressionada ao soltar o botão do mouse e arrastar para cima ou para baixo.

      Ao usar um teclado de toque em um notebook típico, geralmente é difícil controlar os comportamentos de zoom ou perspectiva com o gesto de dois dedos. Nesses casos, é possível pressionar e manter a tecla `SHIFT` pressionada durante a ação. Esse tipo de esforço reduz a velocidade do gesto de pinça e facilita atingir o nível exato de zoom ou perspectiva que você deseja. Como alternativa, é possível usar uma ação de arrastar um dedo para cima ou para baixo com a tecla `SHIFT` pressionada para afetar os comportamentos de zoom ou perspectiva.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nome do controle da câmera</strong><br /> </td> 
      <td><strong>Descrição</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>ou</p> <p>Persp</p> </td> 
      <td><p>Toque ou clique para alternar entre os modos Zoom e Perspectiva.</p> <p>Or, press and hold down the <code>ALT/OPTION</code> key during the action to temporarily toggle to Perspective<br /> mode. Solte a tecla para reverter para o modo Zoom.</p> 
        <ul> 
        <li><strong>Comportamento de mais e menos zoom</strong>- Dolly que move a câmera mais perto ou mais longe do ativo<br /> que você está visualizando. O zoom é o comportamento padrão para o botão de rolagem do mouse (se disponível), para os gestos de pinça com dois dedos em dispositivos móveis ou com se mantém a tecla Shift pressionada ao arrastar para cima ou para baixo usando o botão esquerdo do mouse.</li> 
        <li><strong>Perspectiva</strong>- Altera a duração focal (também conhecida como campo de visualização) da câmera, mantendo o tamanho relativo do ativo na visualização. A perspectiva é o comportamento alternativo para o botão de rolagem (se disponível), para os gestos de pinça com dois dedos em dispositivos móveis ou com se mantém a tecla Shift pressionada ao arrastar para cima ou para baixo usando o botão esquerdo do mouse.</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Órbita</p> <p>ou</p> <p>Panorâmica</p> </td> 
      <td><p>Toque ou clique para alternar entre os modos de órbita e Deslocamento.</p> <p>Or, press and hold the <code>ALT/OPTION</code> key during the action to temporarily toggle to Pan mode. Solte a tecla para reverter para o modo Órbita.</p> 
        <ul> 
        <li><strong>Órbita</strong>- Move a câmera de visualização em uma esfera centralizada em um ponto de público alvo que está localizado perto do centro do ativo 3D para ser o padrão. Órbita é o comportamento padrão ao arrastar com o botão esquerdo ou com um único toque em dispositivos móveis.</li> 
        <li><strong>Deslocamento</strong>-Move a câmera no plano de visualização. O ponto de destino é movido de modo correspondente; assim, as ações de órbita subsequentes moverão a câmera ao redor de um novo ponto de destino. Deslocamento é o comportamento alternativo para arrastar com o botão esquerdo e arrastar com um único toque.</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Examinar</p> <p>ou</p> <p>Target</p> </td> 
      <td><p>Toque ou clique para alternar entre os modos Examine e Público alvo.</p> 
        <ul> 
        <li><strong>Pressione a tecla Examine</strong>ou clique para entrar no modo de Público alvo.</li> 
        <li><strong>Público alvo</strong>- Toque ou clique em um ponto em qualquer lugar do ativo 3D para centralizar a visualização nessa parte do ativo.<br /> As ações de órbita usam o novo ponto de destino.</li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td>Redefinir</td> 
      <td>Toque ou clique para restaurar o ponto de público alvo da visualização para o centro do modelo. Reset also moves the camera<br /> closer or further away to show the asset in its entirety and at a reasonable viewing size.</td> 
      </tr> 
    </tbody> 
    </table>

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon. Selecione um nome de palco com o plano de fundo e a iluminação que deseja aplicar ao ativo 3D.

   ![](do-not-localize/chlimage_1-2.png)

   As etapas fornecem o plano de fundo do ambiente, plano de solo e iluminação em que o modelo 3D é visualizado.

   Consulte [Sobre o uso de palcos no AEM 3D](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md).

1. Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon, then select a camera view that you want to apply to the 3D asset.

   ![](do-not-localize/chlimage_1-3.png)

   Os palcos geralmente fornecem câmeras predefinidas. É possível selecionar novamente a câmera atual para restaurar as configurações predefinidas.

   Consulte [Sobre o uso de palcos no AEM 3D](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md).

1. No canto superior direito da página, toque **[!UICONTROL Salvar]**.
1. Faça uma das seguintes opções:

   * Renderizar o ativo 3D.

      Consulte [Renderizar ativos 3D](/help/sites-classic-ui-authoring/classicui-rendering-3d.md).

   * No canto superior direito da página, toque em **[!UICONTROL Fechar]** para voltar à página Assets.

