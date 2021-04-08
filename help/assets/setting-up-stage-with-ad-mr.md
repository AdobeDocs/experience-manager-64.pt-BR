---
title: Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray
seo-title: Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray
description: Como configurar um estágio padrão com o Autodesk Maya e o Mental Ray
seo-description: Como configurar um estágio padrão com o Autodesk Maya e o Mental Ray
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
exl-id: facd0411-8a3c-4b1a-af9d-0d59e0399b2c
feature: Ativos 3D
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 77%

---

# Configuração de um estágio padrão com o Autodesk Maya e o Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. No Maya, crie uma nova cena vazia.
1. Crie uma referência (temporária) a um modelo representativo. Isso ajuda facilita a avaliação da iluminação, a configuração de câmeras e a configuração do renderizador.

1. Adicione luzes como de costume. Atualmente, o AEM 3D oferece suporte aos seguintes tipos de luz:

   * Luzes direcionais
   * Luzes de refletor
   * Luzes de ponto

   Outros tipos de luzes são ignorados ou convertidos em um dos tipos acima com suporte quando o estágio é carregado no AEM 3D. Os tipos convertidos são usados quando você visualiza o ativo e renderiza usando o renderizador Rapid Refine integrado. Os tipos de luz originais são usados ao renderizar com o Maya.

1. Crie um plano base, se necessário, e aplique um material adequado.

   A Adobe recomenda que você configure um plano base como unilateral. Isso garante que você possa visualizar o ativo de baixo em AEM 3D sem que o plano base o oculte.

1. (Opcional) Crie e configure câmeras.

   Faça com que as câmeras se voltem para o centro da cena onde o ativo será inserido. Defina as câmeras como renderizáveis.

1. Configure a renderização com o Mental Ray.

   Defina as configurações de renderização com as seguintes sugestões:

   * **** Guia Commontab

      Desmarque a caixa de seleção **[!UICONTROL Alpha channel (mask)]** para todas as câmeras renderizáveis.

   * **[!UICONTROL Guia Qualidade]**

      * **[!UICONTROL Qualidade geral]** `- 0.5` ou menos
      * **[!UICONTROL Modo difuso indireto (GI)]**  -  `Final Gather`
      * **[!UICONTROL Tamanho]**  do filtro -  `2.0`,  `2.0`
   * Renderize a cena nos tamanhos de imagem típicos que você espera usar. Se necessário, refine as luzes ou as Configurações de renderização, ou faça as duas coisas para obter os resultados desejados.

      Esteja ciente de que a renderização com o Mental Ray, usando a iluminação baseada em imagem, é muito lenta e exige muita CPU. A Adobe recomenda que você defina as configurações de qualidade mais baixas que ainda sejam capazes de produzir a qualidade de renderização desejada.


1. Remova a referência criada na etapa 2.

1. Salve a cena e saia do Autodesk Maya.
1. Carregue a cena no AEM e aguarde a conclusão do processamento de upload.

   Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

   Se o Autodesk® Maya® não estiver configurado no servidor do AEM, exporte um FBX do Maya e faça o upload para o AEM.

1. Abra as Propriedades do ativo no AEM. Defina **[!UICONTROL Title]** para uma string adequada que aparecerá na lista suspensa **[!UICONTROL Seletor de preparo]**. Verifique se a **[!UICONTROL Classe]** está definida como **[!UICONTROL Estágio 3D]**. Salve e saia.
1. Abra um ativo 3D, selecione o novo estágio e verifique se ele é visualizado e renderizado como esperado.
