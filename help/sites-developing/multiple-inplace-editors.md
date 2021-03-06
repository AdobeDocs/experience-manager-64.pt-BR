---
title: Configure o RTE para vários editores no local.
description: Crie vários editores no local no Adobe Experience Manager configurando o Editor de Rich Text.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 44e7afdd5a5738dde73ab1d05a1c83a4bb24df92
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---


# Configurar vários editores no local {#configure-multiple-in-place-editors}

Você pode configurar o Editor de Rich Text no Adobe Experience Manager para que ele tenha vários editores no local. Quando configurado, você pode selecionar o conteúdo apropriado e abrir o editor apropriado.

![Um editor local específico](assets/rte-inplace-editor.png)

## Configurar vários editores {#configure-multiple-editors}

Para habilitar vários editores no local, a estrutura de um tipo de nó `cq:InplaceEditingConfig` foi aprimorada com a definição do tipo de nó `cq:ChildEditorConfig`.

Por exemplo:

```js
   /**
       * Configures in-place editing of a component.
       *
       * @prop active true to activate in-place editing for the component.
       * @prop editorType ID of in-place editor to use.
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional).
       * @node config editor's config (used if no configPath is specified; optional).
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a sub-component. The name of the this node is
      * used as DD ID.
      *
      * @prop type type of the inline editor. For example, ["image"].
      * @prop title Title of the inline editor.
      * @prop icon Icon to represent the inline editor.
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

Para configurar vários editores, siga estas etapas:

1. No nó `cq:inplaceEditing` (do tipo `cq:InplaceEditingConfig`), defina as seguintes propriedades:

   * Nome:`editorType`
   * Tipo: `String`
   * Valor: `hybrid`

1. Neste nó, crie um nó:

   * Nome: `cq:ChildEditors`
   * Tipo: `nt:unstructured`

1. No nó `cq:childEditors`, crie um nó para cada editor local:

   * Nome: O nome de cada nó é o nome da propriedade que ele representa, como é o caso dos públicos alvos descartados. Por exemplo, `image` e `text`.
   * Tipo: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Há uma correlação entre os públicos alvos de soltar definidos e os editores filhos. O nome do nó `cq:ChildEditorConfig` é considerado como a ID do público alvo de soltar, para uso como parâmetro para o editor filho selecionado. Se a subárea editável não tiver um público alvo de soltar, por exemplo, em um componente de texto, o nome do editor filho ainda será considerado como uma ID para identificar a área editável correspondente.

1. Em cada um desses nós (`cq:ChildEditorConfig`), defina as propriedades:

   * Nome: `type`.
   * Valor: O nome do editor no local registrado; por exemplo, `image` e `text`.

   * Nome: `title`.
   * Valor: O título exibido na lista de seleção de componentes dos editores disponíveis. Por exemplo, `Image` e `Text`.

### Configuração adicional para editores de Rich Text {#additional-configuration-for-rich-text-editors}

A configuração para vários editores de Rich Text é um pouco diferente, pois você pode configurar cada instância individual do RTE separadamente. Para obter detalhes, consulte [configurar o Editor de Rich Text](/help/sites-administering/rich-text-editor.md). Para que vários RTEs criem uma configuração para cada RTE no local. O Adobe recomenda criar o novo nó de configuração em `cq:InplaceEditingConfig`, já que cada RTE individual pode ter uma configuração diferente. No novo nó, crie cada configuração individual do RTE.

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    someconfig
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>No entanto, para o RTE, a propriedade `configPath` é suportada quando há apenas uma instância do editor de texto (subárea editável) no componente. Esse uso de `configPath` é fornecido para oferecer suporte à compatibilidade com versões anteriores das caixas de diálogo da interface do usuário mais antigas do componente.

>[!CAUTION]
>
>Não nomeie o nó de configuração RTE como `config`. Caso contrário, as configurações do RTE estarão disponíveis somente para os administradores e não para os usuários no grupo `content-author`.

## Amostras de código {#code-samples}

Você pode encontrar o código desta página no projeto [aem-authoring-hybrideditors no GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). Você pode baixar o projeto completo como [um arquivo ZIP](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip).

## Adicionar um editor no local {#add-an-in-place-editor}

Para obter informações gerais sobre como adicionar um editor no local, consulte o documento [personalizar criação de página](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Configure o Editor de Rich Text no Experience Manager](/help/sites-administering/rich-text-editor.md).

