---
title: Sobre o uso de palcos no AEM 3D
seo-title: Sobre o uso de palcos no AEM 3D
description: Os estágios são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico.
seo-description: Os estágios são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
exl-id: 6d82fec0-608e-4eaa-aebd-b3ce2f7d8088
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 55%

---

# Sobre o uso de palcos no AEM 3D {#about-the-use-of-stages-in-aem-d}

Palcos são arquivos de cenas 3D leves que fornecem o ambiente de visualização básico (luzes, planos de fundo, planos base ou outras geometrias fixas), câmeras predefinidas opcionais e configurações de renderização para renderizadores de terceiros.

>[!NOTE]
>
>O formato **[!UICONTROL OBJ 3D]** não suporta luzes. Portanto, ele não pode ser usado para fornecer palcos ao AEM 3D.

O formato de arquivo do palco determina qual renderizador você pode usar com ele. Por exemplo, se o Autodesk® Maya® for usado para renderização de alta qualidade, o palco deverá estar no formato `.ma` ou `.mb`. Se você pretende usar apenas o renderizador Rapid Refine™ padrão, qualquer formato de arquivo de estágio compatível é aceitável.

Todas as configurações de renderização no AEM 3D, exceto o tipo e o tamanho da imagem de saída, devem ser pré-configuradas e salvas no arquivo de palco antes de serem carregadas no AEM.
