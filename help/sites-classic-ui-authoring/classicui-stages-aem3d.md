---
title: Sobre o uso de palcos no AEM 3D
seo-title: Sobre o uso de palcos no AEM 3D
description: Palcos são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico (luzes, planos de fundo, planos base ou outras geometrias fixas), câmeras predefinidas opcionais e configurações de renderização para renderizadores de terceiros.
seo-description: Palcos são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico (luzes, planos de fundo, planos base ou outras geometrias fixas), câmeras predefinidas opcionais e configurações de renderização para renderizadores de terceiros.
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 78%

---


# Sobre o uso de palcos no AEM 3D{#about-the-use-of-stages-in-aem-d}

Palcos são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico (luzes, planos de fundo, planos base ou outras geometrias fixas), câmeras predefinidas opcionais e configurações de renderização para renderizadores de terceiros.

>[!NOTE]
>
>O formato OBJ 3D não oferece suporte para luzes. Portanto, ele não pode ser usado para fornecer palcos ao AEM 3D.

O formato de arquivo do palco determina qual renderizador você pode usar com ele. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Se você pretende usar apenas o renderizador Rapid Refine™ padrão, qualquer formato de arquivo de estágio compatível é aceitável.

Todas as configurações de renderização em AEM 3D, exceto o tipo e o tamanho da imagem de saída, devem ser pré-configurados e salvos no arquivo de estágio antes de serem carregados para AEM.

