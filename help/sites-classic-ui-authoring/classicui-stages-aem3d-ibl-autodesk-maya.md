---
title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
seo-title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
description: Saiba mais sobre como configurar um palco IBL com o Autodesk Maya e o Mental Ray.
seo-description: Saiba mais sobre como configurar um palco IBL com o Autodesk Maya e o Mental Ray.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 80%

---


# Configuração de um palco IBL com o Autodesk Maya e o Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. No Maya, crie uma nova cena vazia.

1. Crie uma referência (temporária) a um modelo representativo. Isso ajuda facilita a avaliação da iluminação, a configuração de câmeras e a configuração do renderizador.
1. Configure a iluminação baseada em imagem.

   1. Em Configurações de renderização, selecione **[!UICONTROL Renderizar usando: mental ray]** e abra a guia Cena.****
   1. Open the **[!UICONTROL Environment]** accordion, then click **[!UICONTROL Create Image Based Lighting]**.
   1. Clique no ícone de caixa que tem uma seta para a direita no lado esquerdo da caixa para selecionar o nó IBL `mentalRayIblShape1`[!UICONTROL . Em seguida, saia das Configurações de renderização].
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.

   1. Set the [!UICONTROL Scale] of the node to make the environment sphere significantly larger than the largest 3D object to be shown with this stage (for example, `10000,10000,10000`).
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

   Configure the [!UICONTROL Render Settings] with the following suggestions.

   * **[!UICONTROL Guia Comum]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Guia Qualidade]**

      * **[!UICONTROL Qualidade geral]** `0.5`-   ou menos
      * **[!UICONTROL Modo]** de Difusão Indireta (GI) - `Final Gather`
      * **[!UICONTROL Tamanho]** do filtro - `2.0`, `2.0`
   * Renderize a cena nos tamanhos de imagem típicos que você espera usar. Se necessário, refine as luzes, ou as Configurações de renderização, ou faça as duas coisas para obter os resultados desejados.

      Esteja ciente de que a renderização com o Mental Ray, usando a iluminação baseada em imagem, é muito lenta e exige muita CPU. A Adobe recomenda que você defina as configurações de qualidade mais baixas que ainda sejam capazes de produzir a qualidade de renderização desejada.


1. Remova a referência criada na etapa 2.

1. Salve a cena e saia do Autodesk Maya.

1. Carregue a cena e o PTIFF do IBL no AEM e aguarde a conclusão do processamento de upload.

   Consulte [Upload de ativos](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Resolva quaisquer dependências de arquivos.

   Consulte [Resolução de dependências de arquivos](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   O AEM 3D pode não conseguir detectar a imagem IBL configurada no palco. Nessas situações, você deve resolver as dependências ausentes manualmente. Você pode atribuir a mesma imagem PTIFF IBL carregada anteriormente para cada uma das dependências ausentes. Ou, você pode atribuir imagens diferentes para controlar ainda mais os efeitos da IBL. Depois de resolver as dependências, certifique-se de tocar em **Salvar** para iniciar o reprocessamento.

1. Abra as Propriedades do ativo no AEM. Defina Título como uma sequência de caracteres adequada que será exibida na lista suspensa Seletor de estágio. Verifique se a **[!UICONTROL Classe]** está definida como **[!UICONTROL Estágio 3D]**. Salve e saia.

1. Abra um ativo 3D, selecione o novo estágio e verifique se ele é visualizado e renderizado como esperado.

