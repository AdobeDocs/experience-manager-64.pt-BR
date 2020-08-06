---
title: Gerenciar tags inteligentes
description: Atualizar ou remover as tags inteligentes imprecisas para melhorar a relevância das tags
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# Gerenciamento de tags inteligentes {#managing-smart-tags}

É possível preparar tags inteligentes para remover tags imprecisas que possam ter sido atribuídas às imagens da sua marca, de modo que somente as tags mais relevantes sejam exibidas.

A moderação de tags inteligentes também ajuda a refinar pesquisas baseadas em tags para imagens, garantindo que sua imagem apareça nos resultados da pesquisa para obter as tags mais relevantes. Essencialmente, ajuda a eliminar as chances de imagens não relacionadas aparecerem nos resultados da pesquisa.

Também é possível atribuir uma classificação mais alta a uma tag para aumentar sua relevância em relação a uma imagem. A promoção de uma tag para uma imagem aumenta as chances de a imagem aparecer nos resultados da pesquisa quando uma pesquisa é realizada com base na tag específica.

1. Na caixa OmniSearch, procure ativos com base em uma tag.
1. Inspect os resultados da pesquisa para identificar uma imagem que você não acha relevante para sua pesquisa.
1. Selecione a imagem e clique/toque no ícone **[!UICONTROL Gerenciar tags]** na barra de ferramentas.
1. Na página **[!UICONTROL Gerenciar tags]** , inspecione as tags. Se você não quiser que a imagem seja pesquisada com base em uma tag específica, selecione a tag e clique/toque no ícone **[!UICONTROL Excluir]** na barra de ferramentas. Como alternativa, clique/toque no símbolo (**[!UICONTROL X]**) que aparece ao lado do rótulo.
1. Para atribuir uma classificação superior a uma tag, selecione-a e clique/toque no ícone **[!UICONTROL Promover]** na barra de ferramentas. A tag promovida é movida para a seção **[!UICONTROL Tags]** .
1. Clique/toque em **[!UICONTROL Salvar]** e em **[!UICONTROL OK]** para fechar a caixa de diálogo Êxito.
1. Navegue até a página de propriedades da imagem. Observe que a tag promovida tem uma relevância alta e, portanto, aparece mais alta nos resultados da pesquisa.

## Compreender AEM resultados de pesquisa com tags inteligentes {#understand-search-results-with-smart-tags}

Por padrão, AEM pesquisa combina os termos de pesquisa com uma `AND` cláusula. O uso de tags inteligentes não altera esse comportamento padrão. O uso de tags inteligentes adiciona uma `OR` cláusula adicional para localizar qualquer um dos termos de pesquisa nas tags inteligentes aplicadas. For example, consider searching for `woman running`. Por padrão, os ativos com apenas `woman` ou apenas `running` palavras-chave nos metadados não aparecem nos resultados da pesquisa. No entanto, um ativo marcado com tags ou `woman` `running` usando tags inteligentes é exibido em um query de pesquisa desse tipo. Então os resultados da pesquisa são uma combinação de...

* ativos com ambas as palavras-chave `woman` e `running` nos metadados.
* ativos marcados com inteligência com qualquer uma das palavras-chave.

Os resultados da pesquisa que correspondem a todos os termos de pesquisa nos campos de metadados são exibidos primeiro, seguidos dos resultados da pesquisa que correspondem a qualquer um dos termos de pesquisa nas tags inteligentes. No exemplo acima, a ordem aproximada de exibição dos resultados da pesquisa é:

1. corresponde `woman running` aos vários campos de metadados.
1. corresponde a `woman running` em tags inteligentes.
1. correspondências de `woman` ou de `running` em tags inteligentes.
