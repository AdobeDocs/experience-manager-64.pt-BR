---
title: Gerenciar tags inteligentes
description: Atualizar ou remover as tags inteligentes imprecisas para melhorar a relevância das tags
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 4%

---

# Gerenciamento de tags inteligentes {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode preparar tags inteligentes para remover qualquer tag imprecisa que tenha sido atribuída às imagens da sua marca, para que somente as tags mais relevantes sejam exibidas.

A moderação de tags inteligentes também ajuda a refinar as pesquisas de imagens baseadas em tags, garantindo que sua imagem apareça nos resultados da pesquisa para as tags mais relevantes. Essencialmente, ajuda a eliminar as chances de imagens não relacionadas serem exibidas nos resultados da pesquisa.

Também é possível atribuir uma classificação mais alta a uma tag para aumentar sua relevância em relação a uma imagem. Promover uma tag para uma imagem aumenta a probabilidade da imagem aparecer nos resultados da pesquisa quando uma pesquisa é executada com base na tag específica.

1. Na caixa OmniSearch , procure por ativos com base em uma tag.
1. Inspect os resultados da pesquisa para identificar uma imagem que você não acha relevante para sua pesquisa.
1. Selecione a imagem e clique/toque no **[!UICONTROL Gerenciar tags]** ícone na barra de ferramentas.
1. No **[!UICONTROL Gerenciar tags]** inspecione as tags. Se você não quiser que a imagem seja pesquisada com base em uma tag específica, selecione a tag e clique/toque no **[!UICONTROL Excluir]** ícone na barra de ferramentas. Como alternativa, clique/toque no (**[!UICONTROL X]**) que aparece ao lado do rótulo.
1. Para atribuir uma classificação mais alta a uma tag, selecione a tag e clique/toque na tag **[!UICONTROL Promover]** ícone na barra de ferramentas. A tag promovida é movida para a variável **[!UICONTROL Tags]** seção.
1. Clique/toque em **[!UICONTROL Salvar]** e em **[!UICONTROL OK]** para fechar a caixa de diálogo Êxito.
1. Navegue até a página de propriedades da imagem. Observe que a tag promovida tem uma relevância alta e, portanto, aparece mais alta nos resultados da pesquisa.

## Entender [!DNL Experience Manager] resultados de pesquisa com tags inteligentes {#understand-search-results-with-smart-tags}

Por padrão, [!DNL Experience Manager] a pesquisa combina os termos de pesquisa com um `AND` cláusula. O uso de tags inteligentes não altera esse comportamento padrão. O uso de tags inteligentes adiciona uma `OR` para localizar qualquer um dos termos de pesquisa no aplica tags inteligentes. Por exemplo, considere pesquisar por `woman running`. Ativos com apenas `woman` ou apenas `running` palavras-chave nos metadados não aparecem nos resultados da pesquisa por padrão. No entanto, um ativo marcado com `woman` ou `running` o uso de tags inteligentes é exibido em tal query de pesquisa. Então os resultados da pesquisa são uma combinação de...

* ativos com ambas as palavras-chave, `woman` e `running` nos metadados.
* ativos marcados com tags inteligentes com uma das palavras-chave.

Os resultados da pesquisa que correspondem a todos os termos de pesquisa nos campos de metadados são exibidos primeiro, seguidos pelos resultados da pesquisa que correspondem a qualquer um dos termos de pesquisa nas tags inteligentes. No exemplo acima, a ordem aproximada de exibição dos resultados da pesquisa é:

1. correspondências de `woman running` nos vários campos de metadados.
1. correspondências de `woman running` em tags inteligentes.
1. correspondências de `woman` ou `running` em tags inteligentes.
