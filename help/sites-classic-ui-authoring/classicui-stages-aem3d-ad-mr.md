---
title: Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray
seo-title: Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray
description: Saiba mais sobre como configurar um estágio padrão com o Autodesk Maya e o Mental Ray.
seo-description: Saiba mais sobre como configurar um estágio padrão com o Autodesk Maya e o Mental Ray.
uuid: 05c4858b-6261-4de3-a87a-03dd6bc519a4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f30c4039-3bbf-4d02-a9b5-bda6ccce16b9
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 81%

---


# Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray{#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. No Maya, crie uma nova cena vazia.
1. Crie uma referência (temporária) a um modelo representativo. Isso ajuda facilita a avaliação da iluminação, a configuração de câmeras e a configuração do renderizador.

1. Adicione luzes como de costume. Atualmente, o AEM 3D oferece suporte aos seguintes tipos de luz:

   * Luzes direcionais
   * Luzes de refletor
   * Luzes de ponto

   Outros tipos de luzes são ignorados ou convertidos em um dos tipos acima com suporte quando o estágio é carregado no AEM 3D. Os tipos convertidos são usados quando você visualiza o ativo e renderiza usando o renderizador Rapid Refine integrado. Os tipos de luz originais são usados ao renderizar com Maya.

1. Crie um plano base, se necessário, e aplique um material adequado.

   A Adobe recomenda que você configure um plano base como unilateral. Isso garante que você possa visualização o ativo de baixo em AEM 3D sem que o plano de fundo oculte o ativo.

1. (Opcional) Crie e configure câmeras.

   Faça com que as câmeras se voltem para o centro da cena onde o ativo será inserido. Defina as câmeras como renderizáveis.

1. Configure a renderização com o Mental Ray.

   Configure the **[!UICONTROL Render Settings]** with the following suggestions:

   * **[!UICONTROL Guia Comum]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all [!UICONTROL Renderable Cameras].

   * **[!UICONTROL Guia Qualidade]**

      * **[!UICONTROL Qualidade]** geral `- 0.5` ou menor
      * **[!UICONTROL Modo]** de Difusão Indireta (GI) - `Final Gather`
      * **[!UICONTROL Tamanho]** do filtro - `2.0`, `2.0`
   * Renderize a cena nos tamanhos de imagem típicos que você espera usar. If necessary, refine the lights, or [!UICONTROL Render settings], or do both to achieve the results you want.

      Esteja ciente de que a renderização com o Mental Ray, usando a iluminação baseada em imagem, é muito lenta e exige muita CPU. A Adobe recomenda que você defina as configurações de qualidade mais baixas que ainda sejam capazes de produzir a qualidade de renderização desejada.


1. Remova a referência criada na etapa 2.
1. Salve a cena e saia do Autodesk Maya.
1. Carregue a cena no AEM e aguarde a conclusão do processamento de upload.

   Consulte [Upload de ativos](/help/assets/managing-assets-touch-ui.md#uploading-assets).

   Se o Autodesk® Maya® não estiver configurado no servidor do AEM, exporte um FBX do Maya e faça o upload para o AEM.

1. Abra as Propriedades do ativo no AEM. Defina Título como uma sequência de caracteres adequada que será exibida na lista suspensa Seletor de estágio. Verifique se a **[!UICONTROL Classe]** está definida como **[!UICONTROL Estágio 3D]**. Salve e saia.
1. Abra um ativo 3D, selecione o novo estágio e verifique se ele é visualizado e renderizado como esperado.

