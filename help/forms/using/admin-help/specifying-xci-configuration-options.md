---
title: Especificação das opções de configuração XCI
seo-title: Specifying XCI configuration options
description: Saiba como especificar opções de configuração de XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 6%

---

# Especificação das opções de configuração XCI {#specifying-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Forms permite especificar um arquivo XCI personalizado que será usado para renderização. (Consulte [Configuração de localizações para Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Por padrão, o Forms substitui algumas das opções especificadas no arquivo XCI, incluindo as seguintes:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Você pode selecionar opções que cancelam a substituição das opções listadas acima, nesse caso, o Forms usará os valores especificados no arquivo XCI personalizado.

1. No console de administração, clique em Serviços > Forms.
1. Marque ou desmarque a caixa de seleção Usar opções de XCI padrão do sistema . Quando essa opção é selecionada, o Forms usa os valores padrão para as configurações de pacotes, criador, produtor e compressObjectStream. Quando essa opção é desmarcada, o Forms usa os valores especificados no arquivo XCI personalizado.
1. Clique em Salvar.
