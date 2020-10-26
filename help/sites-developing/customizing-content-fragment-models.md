---
title: NÃO PUBLICAR, MAS NÃO DELETE Personalizar modelos de fragmento de conteúdo
seo-title: Personalização de modelos de fragmento de conteúdo
description: Os Modelos de fragmento de conteúdo podem ser personalizados e estendidos.
seo-description: Os Modelos de fragmento de conteúdo podem ser personalizados e estendidos.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# NÃO PUBLICAR, MAS NÃO DELETE Personalizar modelos de fragmento de conteúdo{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

O editor do Modelo de fragmento de conteúdo é um assistente baseado em `Formbuilder`, herdado de:

`granite/ui/components/foundation/form/formbuilder`

Esse componente tem as ferramentas necessárias para renderizar a interface de arrastar e soltar do editor de modelo, completo com tipos de dados e propriedades para cada um.

## Localizações {#locations}

Os modelos são salvos e criados em `/conf`, em uma pasta que tem a propriedade [Modelos de fragmento de](/help/assets/content-fragments-models.md#enable-content-fragment-models) conteúdo ativada. Essa configuração também pode ser vista nas Propriedades **** de configuração, acessíveis no Navegador **[de](/help/sites-administering/configurations.md)** configuração.

1. Navegue até o navegador por meio de **Ferramentas**, **Geral**, Navegador **de** configuração. Por exemplo, 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. No navegador, selecione a configuração apropriada e, em seguida, **Propriedades** na barra de ferramentas.

   Por exemplo, as propriedades de `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

No console modelos, todas as pastas com a propriedade Modelos **de fragmento de** conteúdo serão exibidas. Navegue por **Ferramentas**, **Ativos**, Modelos **de fragmento de** conteúdo; por exemplo, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Um usuário pode [criar um modelo](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) de fragmento de conteúdo usando o assistente **Criar modelo** (usando **Criar** do console).

>[!CAUTION]
>
>Você não ***deve*** alterar nada no `/libs` caminho.
>
>Isso ocorre porque o conteúdo do é substituído na próxima vez que você atualizar sua instância (e pode ser substituído quando você aplicar uma correção ou um pacote de recursos). `/libs`

## Estrutura de um Modelo {#structure-of-a-model}

O assistente criará uma entrada com esta estrutura:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Todos os modelos são salvos em subpastas desta pasta.

* `jcr:content`

   Cada modelo contém um `jcr:content` nó que:

   * contém propriedades de informações sobre o modelo, como `jcr:title`, `lastModified`, `lastModifiedBy`
   * geralmente tem o `sling:ResourceType` de `dam/cfm/models/console/components/data/entity/default`,

      com o `sling:ResourceSuperType` de `dam/cfm/models/console/components/data/entity`

* `model`

   O `model` nó contém uma propriedade `dataTypesConfig`, usada para determinar os tipos de dados usados no editor de modelo.

* `items`

   No `items` nó, todos os tipos de dados adicionados ao modelo são salvos (como arrastados e soltos no editor de modelo). Cada item recebe um nome de nó aleatório, mas para que o editor de fragmentos de conteúdo funcione com esse modelo, cada item deve ter uma `name` propriedade. Além disso, neste nó, todas as propriedades de configuração de um tipo de dados específico são salvas, incluindo as propriedades padrão necessárias para renderizar os componentes.

>[!CAUTION]
>
>Todos os tipos de dados arrastados e soltos em um editor de modelo e, como tal, instanciados **devem** ter a `name` propriedade inserida pelo usuário.
>
>Isto é visto como Nome da **propriedade &amp;ast;** na guia **Propriedades** do editor de modelo.

## Estrutura do Editor de Modelos {#structure-of-the-model-editor}

O Editor **do Modelo de Fragmento de** Conteúdo tem duas partes:

* O painel pré-visualização, ou visualização, no lado esquerdo, onde é possível soltar itens. Isso:

   * Mostra uma pré-visualização do Tipo **de** dados que é instanciada.
   * Permite a ordem dentro do Editor de modelos.

* As guias Tipos **de** dados/**Propriedades** no painel à direita. Isso:

   * Mostra uma lista de tipos de dados que podem ser arrastados e instanciados.
   * Para o editor de modelo predefinido, a lista está presente em:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Todos os tipos de dados renderizados têm duas tags de script que, quando instanciadas, formarão a visualização (o componente renderizado no lado esquerdo) e a guia **Propriedades** , que define as propriedades que um usuário pode definir para um determinado componente.

>[!CAUTION]
>
>Você não ***deve*** alterar nada no `/libs` caminho.
>
>Isso ocorre porque o conteúdo do é substituído na próxima vez que você atualizar sua instância (e pode ser substituído quando você aplicar uma correção ou um pacote de recursos). `/libs`

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Quando um tipo de dados é instanciado, as entradas HTML são criadas para cada propriedade que o componente precisa ser renderizado em um fragmento de conteúdo. Por exemplo, eles incluem:

* **Nome da propriedade &amp;ast;** ( `name`) - atua como um identificador para componentes

* **Renderizar como** ( `metaType`) - digite o componente a ser renderizado como

* **Descrição** ( `fieldDescription`) - descrição do componente no Fragmento do conteúdo

* e outros.

