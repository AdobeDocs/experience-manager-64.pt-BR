---
title: Essenciais do Editor de Rich Text
seo-title: Essenciais do Editor de Rich Text
description: Visão geral do recurso Editor de Rich Text
seo-description: Visão geral do recurso Editor de Rich Text
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 3%

---


# Rich Text Editor Essentials {#rich-text-editor-essentials}

## Visão geral {#overview}

Um Editor de Rich Text (RTE) fornece a capacidade de inserir texto com marcação.

Para componentes Comunidades, embora semelhante ao [editor de Rich Text no ambiente do autor](../../help/sites-authoring/rich-text-editor.md), afeta o texto inserido no ambiente de publicação.

![chlimage_1-410](assets/chlimage_1-410.png)

## Ativando o Editor de Rich Text {#enabling-rich-text-editor}

Os componentes das comunidades que permitem o conteúdo gerado pelo usuário (UGC) podem ser ativados para permitir o RTE. Dependendo de o componente ter sido adicionado a uma página ou incluído em uma [função](functions.md), o RTE pode ou não ser ativado por padrão.

Se não estiver ativado, basta inserir [modo de edição do autor](sites-console.md#authoring-site-content), selecionar o componente para edição e marcar a caixa de seleção `Rich Text Editor`.

O RTE está disponível para os seguintes componentes das Comunidades:

* [Blog](blog-feature.md)
* [Calendário](calendar.md)
* [Comentários](comments.md)
* [Filelibração](file-library.md)
* [Fórum](forum.md)
* [Mensagens](configure-messaging.md)
* [Perguntas e respostas](working-with-qna.md)
* [Revisões](reviews.md)

## Personalização {#customization}

A personalização do editor de Rich Text é possível, pois a implementação se baseia em [CKEditor](https://www.ckeditor.com/).

A configuração atual dos componentes Comunidades está no `cq.social.  scf   clientlib`, localizado no repositório em

`/libs/clientlibs/social/commons/scf/ckrte.js`

Não é recomendável modificar a clientlib cq.social.scf, pois as atualizações futuras podem substituir qualquer edição.

### Exemplo de personalização: Links em linha {#example-customization-inline-links}

Devido a questões de segurança, as opções de hiperlink não são incluídas no conjunto de ícones Rich Text apresentados aos membros por padrão. A habilidade de pecado é extensa quando são permitidos hrefs na UGC.

Para adicionar as opções de hiperlink à barra de ferramentas:

* Adicionar uma barra de ferramentas chamada &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Selecione **[!UICONTROL Salvar tudo]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```

