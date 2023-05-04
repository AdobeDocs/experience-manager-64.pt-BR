---
title: Especificação de fontes a serem incorporadas
seo-title: Specifying fonts to embed
description: Saiba como especificar fontes a serem incorporadas.
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 3%

---

# Especificação de fontes a serem incorporadas {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode especificar quais fontes são sempre incorporadas ou nunca incorporadas aos formulários gerados pelo serviço Forms. A incorporação de fontes aumenta o tamanho do arquivo dos formulários. Incorpore fontes incomuns que os usuários raramente possuem em seus sistemas. Não incorpore fontes comuns que elas normalmente instalaram.

>[!NOTE]
>
>Se você tiver especificado um arquivo XCI personalizado para Forms, a opção de fonte incorporada no arquivo XCI substituirá essas configurações. (Consulte [Configuração de localizações para Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. No console de administração, clique em **[!UICONTROL Serviços > Forms]**.
1. Em **[!UICONTROL Configurações de incorporação de fonte]** no **[!UICONTROL Sempre incorporar fontes]** digite os nomes das fontes a serem incorporadas aos formulários, separados por vírgulas. As fontes especificadas só serão incorporadas no formulário gerado se forem usadas no formulário. Essa configuração será ignorada se a opção de fonte incorporada tiver sido ativada no arquivo XCI enviado ao serviço porque, nesse caso, todas as fontes usadas no PDF sempre serão incorporadas.
1. No **[!UICONTROL Nunca incorporar fontes]** digite os nomes das fontes que não serão incorporadas aos formulários, separados por vírgulas. As fontes especificadas não são incorporadas no PDF, mesmo se forem usadas no PDF gerado. Essa configuração será ignorada se a opção de fonte incorporada tiver sido desativada no arquivo XCI enviado ao serviço porque, nesse caso, nenhuma das fontes usadas no PDF é incorporada.
1. Clique em **[!UICONTROL Salvar]**.
