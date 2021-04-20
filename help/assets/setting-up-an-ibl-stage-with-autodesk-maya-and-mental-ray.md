---
title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
seo-title: Configuração de um palco IBL com o Autodesk Maya e o Mental Ray
description: Como configurar um palco IBL com o Autodesk Maya e o Mental Ray
seo-description: Como configurar um palco IBL com o Autodesk Maya e o Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
exl-id: ecb489e2-fd6f-4163-9739-5d7ff497d305
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 69%

---

# Configuração de um palco IBL com o Autodesk Maya e o Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. No Maya, crie uma nova cena vazia.

1. Crie uma referência (temporária) a um modelo representativo. Isso ajuda facilita a avaliação da iluminação, a configuração de câmeras e a configuração do renderizador.
1. Configure a iluminação baseada em imagem.

   1. Em **[!UICONTROL Configurações de renderização]**, selecione **[!UICONTROL Renderizar renderização usando: mental ray]** e abra a guia Cena.
   1. Abra a opção **[!UICONTROL Ambiente de renderização]** e clique em **[!UICONTROL Renderizar iluminação baseada em imagem]**.
   1. Clique no ícone da caixa que tem uma seta para a direita no lado esquerdo da caixa para selecionar o nó IBL `mentalRayIblShape1` e saia **[!UICONTROL Configurações de renderização]**.
   1. No **[!UICONTROL Editor de atributos]**, selecione o nó de transformação `mentalRayIbl1` e renomeie o nó de transformação para `AdobeIbl`.
   1. Defina a Escala do nó para tornar a esfera do ambiente significativamente maior que o maior objeto 3D a ser mostrado com esse palco (por exemplo, `10000,10000,10000`).
   1. Selecione o nó `AdobeIblShape` e configure-o da seguinte maneira:

      * **[!UICONTROL Mapeamento]** - Esférico
      * **[!UICONTROL Tipo]** - Arquivo de imagem
      * **[!UICONTROL Emitir luz]** - verdadeiro
   1. Anexe a imagem TIFF de 32 bits desejada ao nó `AdobeIbl` .


1. Configure o plano base.

   * Crie um plano adequado para usar como plano base e dimensione-o para caber razoavelmente dentro da esfera IBL, passando pela origem das coordenadas.
   * Conecte um material **[!UICONTROL Use Background]** ao plano base e o nomeie `AdobeUseBackground` e o anexe ao objeto do plano base.

1. (Opcional) Crie e configure câmeras.

   Faça com que as câmeras se voltem para o centro da cena onde o ativo será inserido. Defina as câmeras como renderizáveis.

1. Configure a renderização com o Mental Ray.

   Configure as **[!UICONTROL Configurações de renderização]** com as seguintes sugestões.

   * **** Guia Commontab

      Desmarque a caixa de seleção **[!UICONTROL Alpha channel (mask)]** para todas as **[!UICONTROL Renderable Cameras]**.

   * **[!UICONTROL Guia Qualidade]**

      * **Qualidade geral** `0.5`-   ou menos
      * **Modo difuso indireto (GI)**  -  `Final Gather`
      * **Tamanho**  do filtro -  `2.0`,  `2.0`
   * Renderize a cena nos tamanhos de imagem típicos que você espera usar. Se necessário, refine as luzes, ou as Configurações de renderização, ou faça as duas coisas para obter os resultados desejados.

      Esteja ciente de que a renderização com o Mental Ray, usando a iluminação baseada em imagem, é muito lenta e exige muita CPU. A Adobe recomenda que você defina as configurações de qualidade mais baixas que ainda sejam capazes de produzir a qualidade de renderização desejada.


1. Remova a referência criada na etapa 2.

1. Salve a cena e saia do Autodesk Maya.

1. Carregue a cena e o PTIFF do IBL no AEM e aguarde a conclusão do processamento de upload.

   Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

1. Resolva quaisquer dependências de arquivos.

   Consulte [Resolução de dependências de arquivos](resolve-file-dependencies.md).

   O AEM 3D pode não conseguir detectar a imagem IBL configurada no palco. Nessas situações, você deve resolver as dependências ausentes manualmente. Você pode atribuir a mesma imagem PTIFF IBL carregada anteriormente para cada uma das dependências ausentes. Ou, você pode atribuir imagens diferentes para controlar ainda mais os efeitos da IBL. Depois de resolver as dependências, certifique-se de tocar em **[!UICONTROL Salvar]** para iniciar o reprocessamento.

1. Abra as Propriedades do ativo no AEM. Defina **[!UICONTROL Title]** para uma string adequada que aparecerá na lista suspensa **[!UICONTROL Seletor de preparo]**. Verifique se a **[!UICONTROL Classe]** está definida como **[!UICONTROL Estágio 3D]**. Salve e saia.

1. Abra um ativo 3D, selecione o novo estágio e verifique se ele é visualizado e renderizado como esperado.
