---
title: Editor
seo-title: Editor
description: Saiba como alternar de volta para o Editor de interface clássica.
seo-description: Saiba como alternar de volta para o Editor de interface clássica.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
translation-type: tm+mt
source-git-commit: 9fa15a44cf83a50538cea3fb37bcccf405f66738
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 7%

---


# Editor{#editor}

Por padrão, a capacidade de alternar para a interface clássica a partir do editor foi desativada.

![chlimage_1-9](assets/chlimage_1-9.png)

Para reativar a opção **Abrir na interface** clássica no menu Informações **da** página, siga estas etapas.

1. Usando o CRXDE Lite, localize o seguinte nó:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Por exemplo

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. Criar uma sobreposição usando a opção **Sobrepor nó** ; por exemplo:

   * **Caminho**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Local de sobreposição**: `/apps/`
   * **Corresponder tipos** de nós: ativo (marque a caixa de seleção)

1. Adicione a seguinte propriedade de texto de vários valores ao nó sobreposto:

   `sling:hideProperties = ["granite:hidden"]`

1. A opção **Abrir na interface clássica** está novamente disponível no menu Informações **da** página ao editar páginas.

   ![chlimage_1-10](assets/chlimage_1-10.png)

