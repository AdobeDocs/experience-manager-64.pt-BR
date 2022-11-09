---
title: NÃO PUBLICAR, MAS NÃO DELETE Personalizar modelos de fragmentos de conteúdo
seo-title: Customizing Content Fragment Models
description: Os Modelos de fragmentos de conteúdo podem ser personalizados e estendidos.
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---


# NÃO PUBLICAR, MAS NÃO DELETE Personalizar modelos de fragmentos de conteúdo{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

O editor do Modelo de fragmento de conteúdo é um assistente baseado em `Formbuilder`, herdada de:

`granite/ui/components/foundation/form/formbuilder`

Esse componente tem as ferramentas necessárias para renderizar a interface de arrastar e soltar do editor de modelo, completo com tipos de dados e propriedades para cada um.

## Localizações {#locations}

Os modelos são salvos e criados em `/conf`em uma pasta que tenha o [Propriedade Modelos de fragmento do conteúdo](/help/assets/content-fragments-models.md#enable-content-fragment-models) habilitado. Essa configuração também pode ser vista na variável **Propriedades da configuração**, acessível a partir do **[Navegador de configuração](/help/sites-administering/configurations.md)**.

1. Navegue até o navegador por **Ferramentas**, **Geral**, **Navegador de configuração**
Por exemplo, 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. No navegador, selecione a configuração apropriada e **Propriedades** na barra de ferramentas.

   Por exemplo, as propriedades de `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

No console modelos, todas as pastas com o **Modelos de fragmentos do conteúdo** será exibida. Navegar via **Ferramentas**, **Ativos**, **Modelos de fragmentos do conteúdo**; por exemplo, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Um usuário pode [criar um modelo de fragmento de conteúdo](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) usando o **Criar modelo** assistente (usando **Criar** do console).

>[!CAUTION]
>
>Você ***must*** não altere nada no `/libs` caminho.
>
>Isso ocorre porque o conteúdo da variável `/libs` O é substituído na próxima vez que você atualizar sua instância (e pode ser substituído quando você aplicar um hotfix ou pacote de recursos).

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

   O `model` nó contém uma propriedade `dataTypesConfig`, usado para determinar os tipos de dados usados no editor de modelo.

* `items`

   Em `items` , todos os tipos de dados adicionados ao modelo são salvos (como arrastados e soltos no editor de modelo). Cada item recebe um nome de nó aleatório, mas para que o editor de fragmento de conteúdo funcione com esse modelo, cada item deve ter um `name` propriedade. Além disso, nesse nó, todas as propriedades de configuração de um tipo de dados específico são salvas, incluindo as propriedades padrão necessárias para renderizar os componentes.

>[!CAUTION]
>
>Todos os tipos de dados arrastados e soltos em um editor de modelo e, como tal, instanciados, **must** ter `name` entrada de propriedade pelo usuário.
>
>Isso é visto como **Nome da propriedade &amp;ast;** no **Propriedades** guia do editor de modelo.

## Estrutura do Editor de Modelos {#structure-of-the-model-editor}

O **Editor do modelo de fragmento de conteúdo** tem duas partes:

* O painel de visualização, ou exibição, à esquerda, onde é possível soltar itens. Isso:

   * Mostra uma pré-visualização do **Tipo de dados** isso é instanciado.
   * Permite a ordenação dentro do Editor de modelo.

* O **Tipos de dados**/**Propriedades** no painel no lado direito. Isso:

   * Mostra uma lista de tipos de dados que podem ser arrastados e instanciados.
   * Para o editor de modelo pronto para uso, a lista está presente em:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Todos os tipos de dados renderizados têm duas tags de script que, quando instanciadas, formarão a exibição (o componente renderizado no lado esquerdo) e a **Propriedades** , que define as propriedades que um usuário pode definir para um determinado componente.

>[!CAUTION]
>
>Você ***must*** não altere nada no `/libs` caminho.
>
>Isso ocorre porque o conteúdo da variável `/libs` O é substituído na próxima vez que você atualizar sua instância (e pode ser substituído quando você aplicar um hotfix ou pacote de recursos).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Quando um tipo de dados é instanciado, as entradas de HTML são criadas para cada propriedade em que o componente precisa ser renderizado em um fragmento de conteúdo. Por exemplo, elas incluem:

* **Nome da propriedade &amp;ast;** ( `name`) - atua como um identificador para componentes

* **Renderizar como** ( `metaType`) - digite o componente a ser renderizado como

* **Descrição** ( `fieldDescription`) - descrição do componente no Fragmento de conteúdo

* e outros.

