---
title: Exibir ativos 3D
description: Saiba mais sobre o visualizador 3D interativo disponível na página Detalhes do ativo no AEM e como usá-lo para exibir ativos 3D.
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
exl-id: 71f89564-a413-49f6-8d6e-c5305bf92c75
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 35%

---

# Exibir ativos 3D {#viewing-d-assets}

>[!IMPORTANT]
>
>AEM 3D no AEM 6.4 não é mais compatível. O Adobe recomenda usar o recurso de ativos 3D em [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) ou [AEM 6.5.3 ou superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) para exibir ativos 3D.

Este documento descreve como visualizar ativos 3D nos detalhes do ativo e como visualizar ativos que estão no componente 3D nos sites.

## Visualização de ativos 3D na página Detalhes do ativo {#viewing-d-assets-in-the-asset-details-page}

O visualizador 3D interativo está disponível na página de detalhes do ativo no AEM. O visualizador inclui, entre outras coisas, uma coleção de controles de câmera interativos que permitem girar, aplicar zoom e deslocar o ativo 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

Além de utilizar os palcos padrão no AEM 3D, também é possível usar os palcos criados em um aplicativo de terceiros e enviados por upload para o AEM.

Consulte [Sobre o uso de palcos no AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Para ver um ativo 3D, seu dispositivo ou navegador de desktop devem ser habilitados para WebGL. Além disso, o hardware gráfico subjacente deve ter recursos e memória suficientes para renderizar modelos do tamanho e complexidade desejados. Determinados recursos de visualização, como sombra, não estão disponíveis em todos os navegadores.

### Considerações de desempenho ao visualizar os ativos 3D {#performance-considerations-when-you-view-d-assets}

O tempo que leva para abrir um ativo 3D na exibição de página dos detalhes do ativo depende de vários fatores. Esses fatores incluem informações como as seguintes:

* Largura de banda e latências ao servidor.
* Tamanho modelo (número de faces).
* Número e tamanho dos mapas.
* Complexidade do palco. Por exemplo, o tamanho da imagem IBL.

Além disso, os recursos do computador cliente, como uma estação de trabalho, um notebook ou um dispositivo de toque móvel, também são importantes a serem considerados ao manipular a câmera interativamente. Um sistema bastante eficiente com bons recursos gráficos pode tornar a experiência de visualização interativa em 3D mais fácil e favorável.

**Para exibir os ativos 3D**:

1. Verifique se você fez upload dos ativos 3D no AEM.

   Consulte [Sobre o upload e o processamento de ativos 3D no AEM](upload-processing-3d-assets.md).

1. Em AEM, na página **[!UICONTROL Navegação]**, toque em **[!UICONTROL Ativos]**.
1. Próximo ao canto superior direito da página, na lista suspensa **[!UICONTROL Exibir]**, toque em **[!UICONTROL Exibição de cartão]**.
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
      <td><p>Toque ou clique para alternar entre os modos Zoom e Perspectiva.</p> <p>Ou pressione e mantenha pressionada a tecla <code>ALT/OPTION</code> durante a ação para alternar temporariamente para o modo Perspectiva<br />. Solte a tecla para reverter para o modo Zoom.</p> 
      <ul> 
      <li><strong>Zoom</strong> - Diminua o comportamento de entrada e saída que move a câmera para mais perto ou mais longe do <br /> ativo que você está visualizando. O zoom é o comportamento padrão para o botão de rolagem do mouse (se disponível), para os gestos de pinça com dois dedos em dispositivos móveis ou com se mantém a tecla Shift pressionada ao arrastar para cima ou para baixo usando o botão esquerdo do mouse.</li> 
      <li><strong>Perspectiva</strong> - Altera o comprimento focal (também conhecido como campo de visão) da câmera, mantendo o tamanho relativo do ativo na exibição. A perspectiva é o comportamento alternativo para o botão de rolagem (se disponível), para os gestos de pinça com dois dedos em dispositivos móveis ou com se mantém a tecla Shift pressionada ao arrastar para cima ou para baixo usando o botão esquerdo do mouse.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Órbita</p> <p>ou</p> <p>Panorâmica</p> </td> 
      <td><p>Toque ou clique para alternar entre os modos Órbita e Deslocar.</p> <p>Ou pressione e mantenha pressionada a tecla <code>ALT/OPTION</code> durante a ação para alternar temporariamente para o modo Deslocar. Solte a tecla para reverter para o modo Órbita.</p> 
      <ul> 
      <li><strong>Órbita</strong> - Move a câmera de exibição em uma esfera centralizada em um ponto de destino que está localizado próximo do centro do ativo 3D por padrão. Órbita é o comportamento padrão ao arrastar com o botão esquerdo ou com um único toque em dispositivos móveis.</li> 
      <li><strong>Deslocar</strong>-Move a câmera no plano de exibição. O ponto de destino é movido de modo correspondente; assim, as ações de órbita subsequentes moverão a câmera ao redor de um novo ponto de destino. Deslocamento é o comportamento alternativo para arrastar com o botão esquerdo e arrastar com um único toque.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Examinar</p> <p>ou</p> <p>Target</p> </td> 
      <td><p>Toque ou clique para alternar entre os modos Examinar e Destino.</p> 
      <ul> 
      <li><strong>Examinar</strong> - Toque ou clique para entrar no modo de Direcionamento.</li> 
      <li><strong>Target</strong> - Toque ou clique em um ponto em qualquer lugar do ativo 3D para centrar a exibição nessa parte do ativo.<br /> As ações de órbita usam o novo ponto de destino.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Redefinir</td> 
      <td>Toque ou clique em para restaurar o ponto de destino da exibição para o centro do modelo. A redefinição também aproxima ou afasta a câmera para mostrar o ativo inteiro e em um tamanho de visualização razoável.<br /></td> 
      </tr> 
    </tbody> 
    </table>

   * Próximo ao canto superior direito da página de detalhes do ativo, toque no ícone **[!UICONTROL Seletor de palco]**. Selecione um nome de palco com o plano de fundo e a iluminação que deseja aplicar ao ativo 3D.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Os palcos fornecem o ambiente, o plano base e a iluminação em que o modelo 3D é visualizado.

   Consulte [Sobre o uso de palcos no AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Próximo ao canto superior direito da página de detalhes do ativo, toque no ícone **[!UICONTROL Seletor de câmera]** e selecione uma exibição de câmera que deseja aplicar ao ativo 3D.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Os palcos geralmente fornecem câmeras predefinidas. É possível selecionar novamente a câmera atual para restaurar as configurações predefinidas.

   Consulte [Sobre o uso de palcos no AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. No canto superior direito da página, toque **[!UICONTROL Salvar]**.
1. Faça uma das seguintes opções:

   * Renderizar o ativo 3D.

      Consulte [Renderizar ativos 3D](rendering-3d-assets.md).

   * No canto superior direito da página, toque em **[!UICONTROL Fechar]** para voltar à página Assets.

## Visualização de ativos 3D no componente Sites 3D {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Esta seção se aplica somente ao visualizador webGL clássico usado para tipos de ativos 3D diferentes do Adobe Dimension.

Dependendo do tipo de dispositivo, você acessa os recursos do componente 3D de várias maneiras.

Para obter mais informações, consulte:

* [Dispositivos de ecrã táctil](#touchscreen-devices)
* [Dispositivos de touchpad](#touchpad-devices)
* [Dispositivos de mouse e de trackball](#mouse-and-trackball-devices)

Consulte também [Visualização de uma página da Web que tenha um componente 3D](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Dispositivos de tela sensível ao toque {#touchscreen-devices}

Para trabalhar com componentes 3D com dispositivos de tela sensível ao toque:

1. Use um arrastar com um dedo ou deslizar o dedo para mover (&quot;órbita&quot;) o ponto de vista (&quot;câmera&quot;) ao redor do objeto. É possível exibir o objeto de qualquer direção.

1. Use uma pinça de dois dedos para mover a câmera para perto ou mais longe do objeto. Essa ação é semelhante a aumentar ou diminuir o zoom e permite inspecionar os detalhes do objeto. Como alternativa, pressione e mantenha pressionados os botões + ou - para aproximar ou afastar a câmera do objeto.

1. Use um arrastar com dois dedos para deslocar a câmera. Essa ação move a câmera lateralmente para permitir que você veja diferentes partes do objeto enquanto amplia o zoom. Como alternativa, toque no botão **[!UICONTROL Órbita/Deslocar alternar]** para alternar para o modo Deslocar, em seguida, use um arrastar com um dedo para deslocar a câmera. Toque no botão **[!UICONTROL Alternar órbita/deslocamento]** para reverter para o modo **[!UICONTROL Órbita]**.

1. Toque em **[!UICONTROL Reiniciar visualizador]** para redefinir a câmera. Essa ação traz o objeto de volta à visualização completa e, se estiver ativada, retoma a rotação automática.

1. Toque em **[!UICONTROL Tela cheia]** para entrar no modo de tela cheia (se suportado pelo dispositivo). Toque em **[!UICONTROL Tela cheia]** novamente para restaurar o visualizador 3D para o modo incorporado na página.

### Dispositivos de touchpad {#touchpad-devices}

Para trabalhar com componentes 3D com dispositivos de touchpad:

1. Use um arrastar com um dedo enquanto mantém o botão do touchpad (esquerda) baixo para mover (&quot;órbita&quot;) o ponto de vista (&quot;câmera&quot;) ao redor do objeto. É possível exibir o objeto de qualquer direção.

1. Use um arrastar com dois dedos para baixo ou para cima com botões do touchpad para cima para mover a câmera para perto ou mais longe do objeto. Essa ação é semelhante a aumentar ou diminuir o zoom e permite inspecionar detalhes do objeto. Como alternativa, clique e segure os botões **[!UICONTROL Ampliar]** ou **[!UICONTROL Menos zoom]** para mover a câmera para perto ou mais longe do objeto.

1. Use um arrastar com um dedo enquanto segura a tecla **ALT/option** e o botão do touchpad (esquerda) para deslocar a câmera. Essa ação move a câmera lateralmente para permitir que você veja diferentes partes do objeto enquanto amplia o zoom. Como alternativa, clique no botão **[!UICONTROL Órbita/Deslocar alternar]** para alternar para o modo **[!UICONTROL Deslocar]** e, em seguida, use um arrastar com um dedo enquanto segura o botão (à esquerda) para deslocar a câmera. Clique no botão **[!UICONTROL Alternar Órbita/Deslocar]** novamente para reverter para o modo **[!UICONTROL Órbita]**.

1. Clique em **[!UICONTROL Reset Viewer]** para reiniciar a câmera. Essa ação traz o objeto de volta à visualização completa e, se estiver ativada, retoma a rotação automática.

1. Clique em **[!UICONTROL Tela cheia]** para entrar no modo de tela cheia. Use a tecla **Escape** no teclado ou clique **[!UICONTROL Tela cheia]** novamente para restaurar o visualizador 3D para o modo incorporado da página.

### Dispositivos de mouse e de trackball {#mouse-and-trackball-devices}

Para trabalhar com componentes 3D com dispositivos de mouse e trackball:

1. Arraste enquanto segura o botão esquerdo do mouse para baixo para mover (&quot;órbita&quot;) o ponto de vista (&quot;câmera&quot;) ao redor do objeto. É possível exibir o objeto de qualquer direção.

1. Use a roda de rolagem para mover a câmera para perto ou mais longe do objeto. É semelhante a aumentar ou diminuir o zoom e permite inspecionar os detalhes do objeto. Como alternativa, clique e segure os botões **[!UICONTROL Ampliar]** ou **[!UICONTROL Menos zoom]** para mover a câmera para perto ou mais longe do objeto.

1. Arraste enquanto segura a tecla **ALT/option** e o botão esquerdo do mouse para deslocar a câmera. Isso move a câmera lateralmente para permitir a observação de diferentes partes do objeto enquanto amplia o zoom. Como alternativa, clique no botão **[!UICONTROL Órbita/Deslocar Alternar]** para alternar para o modo **[!UICONTROL Deslocar]** e arraste enquanto segura o botão esquerdo do mouse para deslocar a câmera. Clique novamente em **[!UICONTROL Órbita/Deslocar alternância]** para reverter para o modo **[!UICONTROL Órbita]**.
1. Clique em **[!UICONTROL Reset Viewer]** para reiniciar a câmera. Essa ação traz o objeto de volta à visualização completa e, se estiver ativada, retoma a rotação automática.
1. Clique em **[!UICONTROL Tela cheia]** para entrar no modo de tela cheia. Use a tecla **[!UICONTROL Escape]** no teclado ou clique **[!UICONTROL Tela cheia]** novamente para restaurar o visualizador 3D para o modo incorporado da página.
