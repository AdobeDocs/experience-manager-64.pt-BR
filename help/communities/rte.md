---
title: Princípios básicos do editor de rich text
seo-title: Rich Text Editor Essentials
description: Visão geral de recursos do Editor de Rich Text
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 6%

---

# Princípios básicos do editor de rich text {#rich-text-editor-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Um Editor de Rich Text (RTE) fornece a capacidade de inserir texto com marcação.

Para componentes das Comunidades, enquanto são semelhantes ao [editor de rich text no ambiente do autor](../../help/sites-authoring/rich-text-editor.md), afeta o texto inserido no ambiente de publicação.

![chlimage_1-410](assets/chlimage_1-410.png)

## Ativação do editor de rich text {#enabling-rich-text-editor}

Os componentes de Comunidades que permitem conteúdo gerado pelo usuário (UGC) podem ser habilitados para permitir o RTE. Dependendo de o componente ter sido adicionado a uma página ou incluído em uma [função](functions.md), o RTE pode ou não ser ativado por padrão.

Se não estiver ativado, basta inserir [modo de edição do autor](sites-console.md#authoring-site-content), selecione o componente para edição e selecione o `Rich Text Editor` caixa de seleção.

O RTE está disponível para os seguintes componentes do Communities:

* [Blog](blog-feature.md)
* [Calendário](calendar.md)
* [Comentários](comments.md)
* [Filelibrary](file-library.md)
* [Fórum](forum.md)
* [Mensagens](configure-messaging.md)
* [QnA](working-with-qna.md)
* [Revisões](reviews.md)

## Personalização {#customization}

A personalização do editor de rich text é possível, pois a implementação é baseada em [Editor CKE](https://www.ckeditor.com/).

A configuração atual dos componentes das Comunidades está no `cq.social.  scf   clientlib`, localizado no repositório em

`/libs/clientlibs/social/commons/scf/ckrte.js`

A modificação da clientlib cq.social.scf não é recomendada, pois as atualizações futuras podem substituir qualquer edição.

### Exemplo de personalização: Links em linha {#example-customization-inline-links}

Devido a questões de segurança, as opções de hiperlink não são incluídas no conjunto de ícones de rich text apresentados aos membros por padrão. A habilidade para o mal é extensa quando os hrefs são permitidos no UGC.

Para adicionar as opções de hiperlink à barra de ferramentas:

* Adicionar uma barra de ferramentas chamada &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Selecionar **[!UICONTROL Salvar tudo]**

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
