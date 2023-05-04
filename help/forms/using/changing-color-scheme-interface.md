---
title: Alteração do esquema de cores da interface
seo-title: Changing the color scheme of the interface
description: Como modificar o esquema de cores das partes da interface do usuário do AEM Forms workspace de forma seletiva.
seo-description: How to modify the color scheme of AEM Forms workspace user interface portions selectively.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: efbb9a9e-0ddf-49f2-bcb8-14cd0c6de5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Alteração do esquema de cores da interface {#changing-the-color-scheme-of-the-interface}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode modificar o esquema de cores das partes da interface do usuário do espaço de trabalho do AEM Forms para atender aos seus requisitos. Veja a seguir alguns exemplos de personalizações representativas do esquema de cores. Além das etapas discutidas neste artigo, consulte [Etapas genéricas para personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).

## Barra de navegação superior {#top-navigation-bar}

### Usar imagem de fundo {#using-background-image}

Para atualizar a barra de navegação na parte superior do espaço de trabalho do AEM Forms.

1. Crie uma imagem de plano de fundo para atualizar a cor. Nomeie o arquivo como newBackground.jpg.
1. Faça upload do arquivo de imagem de fundo na pasta /apps/ws/images usando um cliente WebDAV.

   >[!NOTE]
   >
   >Para obter mais informações sobre o acesso WebDAV, consulte [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Faça referência à nova imagem de plano de fundo em /apps/ws/css/newStyle.css adicionando o seguinte estilo.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Uso da propriedade de cor no CSS {#using-color-property-in-css}

1. Adicione o seguinte estilo em newStyle.css em /apps/ws/css

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Componente Categoria {#category-component}

O componente Categoria exibe as várias categorias de suas tarefas no painel esquerdo. Para alterar sua cor, defina a cor do plano de fundo em `.category` elemento do arquivo CSS.

## Componente de tarefa {#task-component}

As tarefas são exibidas no painel do meio chamado Componente TaskList. Para alterar sua cor, modifique o estilo associado ao seletor .task na folha de estilos.
