---
title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
seo-title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
description: Como configurar um estágio IBL com Autodesk Maya e Mental Ray
seo-description: Como configurar um estágio IBL com Autodesk Maya e Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 69%

---


# Configuração de um palco IBL com o Autodesk Maya e o Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. No Maya, crie uma nova cena vazia.

1. Crie uma referência (temporária) a um modelo representativo. Isso ajuda facilita a avaliação da iluminação, a configuração de câmeras e a configuração do renderizador.
1. Configure a iluminação baseada em imagem.

   1. In **[!UICONTROL Render Settings]**, select **[!UICONTROL Render Render Using: mental ray]**, and open the Scene tab.
   1. Open the **[!UICONTROL Render Environment]** accordion and click **[!UICONTROL Render Create Image Based Lighting**.
   1. Click the box icon that has a right arrow on the left side of the box to select the IBL node `mentalRayIblShape1`, then exit **[!UICONTROL Render Settings]**.
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.
   1. Defina a Escala do nó para tornar a esfera do ambiente significativamente maior que o maior objeto 3D a ser mostrado com esse palco (por exemplo, `10000,10000,10000`).
   1. Selecione o nó `AdobeIblShape` e configure-o da seguinte maneira:

      * **[!UICONTROL Mapeamento]** - Esférico
      * **[!UICONTROL Tipo]** - Arquivo de imagem
      * **[!UICONTROL Emitir luz]** - verdadeiro
   1. Attach the desired 32-bit TIFF image to the `AdobeIbl` node.


1. Configure o plano base.

   * Crie um plano adequado para usar como plano base e dimensione-o para caber razoavelmente dentro da esfera IBL, passando pela origem das coordenadas.
   * Attach a **[!UICONTROL Use Background]** material to the ground plane and name it `AdobeUseBackground` and attach it to the ground plane object.

1. (Opcional) Crie e configure câmeras.

   Faça com que as câmeras se voltem para o centro da cena onde o ativo será inserido. Defina as câmeras como renderizáveis.

1. Configure a renderização com o Mental Ray.

   Configure the **[!UICONTROL Render Settings]** with the following suggestions.

   * **[!UICONTROL Guia Comum]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all **[!UICONTROL Renderable Cameras]**.

   * **[!UICONTROL Guia Qualidade]**

      * **Qualidade geral** `0.5`-   ou menos
      * **Modo** de Difusão Indireta (GI) - `Final Gather`
      * ``**Filter Size** - `2.0`, `2.0`
   * Renderize a cena nos tamanhos de imagem típicos que você espera usar. Se necessário, refine as luzes, ou as Configurações de renderização, ou faça as duas coisas para obter os resultados desejados.

      Esteja ciente de que a renderização com o Mental Ray, usando a iluminação baseada em imagem, é muito lenta e exige muita CPU. A Adobe recomenda que você defina as configurações de qualidade mais baixas que ainda sejam capazes de produzir a qualidade de renderização desejada.


1. Remova a referência criada na etapa 2.

1. Salve a cena e saia do Autodesk Maya.

1. Carregue a cena e o PTIFF do IBL no AEM e aguarde a conclusão do processamento de upload.

   Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

1. Resolva quaisquer dependências de arquivos.

   Consulte [Resolução de dependências de arquivos](resolve-file-dependencies.md).

   O AEM 3D pode não conseguir detectar a imagem IBL configurada no palco. Nessas situações, você deve resolver as dependências ausentes manualmente. Você pode atribuir a mesma imagem PTIFF IBL carregada anteriormente para cada uma das dependências ausentes. Ou, você pode atribuir imagens diferentes para controlar ainda mais os efeitos da IBL. Depois de resolver as dependências, certifique-se de tocar em **[!UICONTROL Salvar]** para iniciar o reprocessamento.

1. Abra as Propriedades do ativo no AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Verifique se a **[!UICONTROL Classe]** está definida como **[!UICONTROL Estágio 3D]**. Salve e saia.

1. Abra um ativo 3D, selecione o novo estágio e verifique se ele é visualizado e renderizado como esperado.

