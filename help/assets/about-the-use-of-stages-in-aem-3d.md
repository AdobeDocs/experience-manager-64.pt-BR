---
title: Sobre o uso de palcos no AEM 3D
seo-title: Sobre o uso de palcos no AEM 3D
description: As etapas são arquivos de cena 3D de peso leve que fornecem o ambiente básico de visualização.
seo-description: As etapas são arquivos de cena 3D de peso leve que fornecem o ambiente básico de visualização.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 56%

---


# Sobre o uso de palcos no AEM 3D {#about-the-use-of-stages-in-aem-d}

Palcos são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico (luzes, planos de fundo, planos base ou outras geometrias fixas), câmeras predefinidas opcionais e configurações de renderização para renderizadores de terceiros.

>[!NOTE]
>
>The **[!UICONTROL OBJ 3D]** format does not support lights. Portanto, ele não pode ser usado para fornecer palcos ao AEM 3D.

O formato de arquivo do palco determina qual renderizador você pode usar com ele. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Se você pretende usar apenas o renderizador Rapid Refine™ padrão, qualquer formato de arquivo de estágio compatível é aceitável.

Todas as configurações de renderização em AEM 3D, exceto o tipo e o tamanho da imagem de saída, devem ser pré-configuradas e salvas no arquivo de palco antes do upload para AEM.