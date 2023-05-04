---
title: Admin Console
seo-title: Admin Consoles
description: Saiba como usar os Admin Console disponíveis no AEM.
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# Admin Console{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Por padrão, a capacidade de alternar para a interface clássica por meio dos consoles de administrador foi desativada. Portanto, os ícones pop-up que foram vistos ao passar o mouse sobre determinados ícones do console, permitindo o acesso à interface clássica, não são mais exibidos.

![screen_shot_2018-03-23at11956](assets/screen_shot_2018-03-23at111956.png)

Cada console que tem uma versão da interface clássica em `/libs/cq/core/content/nav` pode ser reativado individualmente para que a função **Interface clássica** nova opção aparece sobre o ícone do console ao passar o mouse.

Neste exemplo, estamos reativando a interface clássica para o console Sites .

1. Usando o CRXDE Lite, encontre o nó correspondente ao Admin Console para o qual você deseja reativar a interface do usuário clássica. Encontram-se em:

   `/libs/cq/core/content/nav`

   Por exemplo

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Selecione o nó correspondente ao console para o qual você deseja reativar a interface do usuário clássica. No nosso exemplo, reativaremos a interface clássica para o console Sites .

   `/libs/cq/core/content/nav/sites`

1. Crie uma sobreposição usando o **Nó de sobreposição** opção; por exemplo:

   * **Caminho**: `/apps/cq/core/content/nav/sites`
   * **Local de sobreposição**: `/apps/`
   * **Corresponder tipos de nó**: ativo (marque a caixa de seleção)

1. Adicione a seguinte propriedade booleana ao nó sobreposto:

   `enableDesktopOnly = {Boolean}true`

1. O **Interface clássica** está novamente disponível como uma opção de oferta no admin console.

   ![screen_shot_2018-03-23at11924](assets/screen_shot_2018-03-23at111924.png)

Repita essas etapas para cada console para o qual deseja reativar o acesso à versão da interface clássica.
