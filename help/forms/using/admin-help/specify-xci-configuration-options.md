---
title: Especificar opções de configuração XCI
seo-title: Specify XCI configuration options
description: Saiba como especificar opções de configuração de XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 6%

---

# Especificar opções de configuração XCI {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Output permite especificar um arquivo XCI personalizado que ele usa para renderização. (Consulte [Especificar locais de arquivo para saída](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) Por padrão, o Output substitui algumas das opções especificadas no arquivo XCI, incluindo as seguintes:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Você pode selecionar opções que cancelam a substituição das opções listadas acima, nesse caso, a Saída usa os valores especificados no arquivo XCI personalizado.

1. No console de administração, clique em Serviços > saída.
1. Marque ou desmarque a caixa de seleção Usar opções de XCI padrão do sistema . Quando essa opção é selecionada, o Output usa os valores padrão para as configurações de pacotes, criador, produtor e compressObjectStream. Quando essa opção está desmarcada, o Output usa os valores especificados no arquivo XCI personalizado.
1. Clique em Salvar.
