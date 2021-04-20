---
title: Gerenciar tags inteligentes
description: Atualizar ou remover as tags inteligentes imprecisas para melhorar a relevância das tags
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 3%

---


# Gerenciamento de tags inteligentes {#managing-smart-tags}

Você pode preparar tags inteligentes para remover qualquer tag imprecisa que tenha sido atribuída às imagens da sua marca, para que somente as tags mais relevantes sejam exibidas.

A moderação de tags inteligentes também ajuda a refinar as pesquisas de imagens baseadas em tags, garantindo que sua imagem apareça nos resultados da pesquisa para as tags mais relevantes. Essencialmente, ajuda a eliminar as chances de imagens não relacionadas serem exibidas nos resultados da pesquisa.

Também é possível atribuir uma classificação mais alta a uma tag para aumentar sua relevância em relação a uma imagem. Promover uma tag para uma imagem aumenta a probabilidade da imagem aparecer nos resultados da pesquisa quando uma pesquisa é executada com base na tag específica.

1. Na caixa OmniSearch , procure por ativos com base em uma tag.
1. Inspect os resultados da pesquisa para identificar uma imagem que você não acha relevante para sua pesquisa.
1. Selecione a imagem e clique/toque no ícone **[!UICONTROL Gerenciar tags]** na barra de ferramentas.
1. Na página **[!UICONTROL Gerenciar tags]**, inspecione as tags. Se não quiser que a imagem seja pesquisada com base em uma tag específica, selecione a tag e clique/toque no ícone **[!UICONTROL Delete]** na barra de ferramentas. Como alternativa, clique/toque no símbolo (**[!UICONTROL X]**) que aparece ao lado do rótulo.
1. Para atribuir uma classificação mais alta a uma tag, selecione a tag e clique/toque no ícone **[!UICONTROL Promover]** na barra de ferramentas. A tag promovida é movida para a seção **[!UICONTROL Tags]**.
1. Clique/toque em **[!UICONTROL Salvar]** e em **[!UICONTROL OK]** para fechar a caixa de diálogo Êxito.
1. Navegue até a página de propriedades da imagem. Observe que a tag promovida tem uma relevância alta e, portanto, aparece mais alta nos resultados da pesquisa.

## Entender AEM resultados de pesquisa com tags inteligentes {#understand-search-results-with-smart-tags}

Por padrão, AEM pesquisa combina os termos de pesquisa com uma cláusula `AND`. O uso de tags inteligentes não altera esse comportamento padrão. O uso de tags inteligentes adiciona uma cláusula `OR` adicional para localizar qualquer um dos termos de pesquisa nas tags inteligentes de aplicação. Por exemplo, considere pesquisar por `woman running`. Os ativos com apenas `woman` ou apenas `running` palavra-chave nos metadados não aparecem nos resultados da pesquisa por padrão. No entanto, um ativo marcado com `woman` ou `running` usando tags inteligentes aparece em tal query de pesquisa. Então os resultados da pesquisa são uma combinação de...

* ativos com ambas as palavras-chave, `woman` e `running` nos metadados.
* ativos marcados com tags inteligentes com uma das palavras-chave.

Os resultados da pesquisa que correspondem a todos os termos de pesquisa nos campos de metadados são exibidos primeiro, seguidos pelos resultados da pesquisa que correspondem a qualquer um dos termos de pesquisa nas tags inteligentes. No exemplo acima, a ordem aproximada de exibição dos resultados da pesquisa é:

1. corresponde a `woman running` nos vários campos de metadados.
1. corresponde de `woman running` em tags inteligentes.
1. correspondências de `woman` ou de `running` em tags inteligentes.
