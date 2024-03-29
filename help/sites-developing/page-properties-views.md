---
title: Personalização de exibições das propriedades da página
seo-title: Customizing Views of Page Properties
description: Cada página tem um conjunto de propriedades que você pode editar conforme necessário
seo-description: Every page has a set of properties that you can edit as required
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
exl-id: 25dad368-8227-424d-960b-1664d8e20a21
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 3%

---

# Personalização de exibições das propriedades da página{#customizing-views-of-page-properties}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Cada página tem um conjunto de [propriedades](/help/sites-authoring/editing-page-properties.md) que podem ser visualizadas e editadas pelos usuários; alguns são necessários ao criar a página (criar exibição), outros podem ser visualizados e editados (editar exibição) em um estágio posterior. Essas propriedades da página são definidas e disponibilizadas pela caixa de diálogo ( `cq:dialog`) do componente de página apropriado.

>[!CAUTION]
>
>A personalização da exibição das propriedades da página não está disponível na interface clássica.

O estado padrão de cada propriedade de página é:

* oculto na exibição de criação (por exemplo, **Criar página** assistente)

* disponível na exibição de edição (por exemplo, **Propriedades da exibição**)

Os campos devem ser configurados especificamente se alguma alteração for necessária. Isso é feito usando as propriedades apropriadas do nó:

* Propriedade da página a ser disponibilizada na exibição de criação (por exemplo, **Criar página** assistente):

   * Nome: `cq:showOnCreate`
   * Tipo: `Boolean`

* Propriedade da página a ser disponibilizada na exibição de edição (por exemplo, **Exibir**/**Editar**) **Propriedades** ):

   * Nome: `cq:hideOnEdit`
   * Tipo: `Boolean`

Por exemplo, consulte as configurações de campos agrupados na variável **Mais títulos e descrição** no **Básico** guia para o componente Página de base. Elas estão visíveis na variável **Criar página** assistente como `cq:showOnCreate` foi definida como `true`:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Consulte a [Tutorial de extensões de propriedades da página](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) para obter um guia sobre como personalizar as propriedades da página.

## Configurar as propriedades da página {#configuring-your-page-properties}

Você também pode configurar os campos disponíveis configurando a caixa de diálogo do componente de página e aplicando as propriedades de nó apropriadas.

Por exemplo, por padrão, a variável [**Criar página** assistente](/help/sites-authoring/managing-pages.md#creating-a-new-page) mostra os campos agrupados em **Mais títulos e descrição**. Para ocultá-los, configure:

1. Crie o componente da página em `/apps`.
1. Criar uma substituição (usando *diff da caixa de diálogo* do [Fusão de Recursos Sling](/help/sites-developing/sling-resource-merger.md)) para o `basic` seção do componente página; por exemplo:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Como referência, consulte:
   >
   >
   ```
   >/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog
   >```
   >
   >No entanto, você ***must*** não altere nada no `/libs` caminho.
   >
   >Isso ocorre porque o conteúdo da variável `/libs` O é substituído na próxima vez que você atualizar sua instância (e pode ser substituído quando você aplicar um hotfix ou pacote de recursos).
   >
   >O método recomendado para configuração e outras alterações é:
   >
   >1. Recrie o item necessário (ou seja, como ele existe em `/libs`) `/apps`
   >1. Faça quaisquer alterações no `/apps`


1. Defina as `path` propriedade em `basic` para apontar para a substituição da guia básica (consulte a próxima etapa também). Por exemplo:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Criar uma substituição do `basic` - `moretitles` seção no caminho correspondente; por exemplo:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Aplique a propriedade de nó apropriada:

   * **Nome**: `cq:showOnCreate`
   * **Tipo**: `Boolean`
   * **Valor**: `false`

   O **Mais títulos e descrição** não será mais exibida na variável **Criar página** assistente.

>[!NOTE]
>
>Ao configurar as propriedades de página para uso com cópias dinâmicas, consulte [Configuração de bloqueios MSM nas propriedades da página](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) para obter mais detalhes.

## Exemplo de configuração das propriedades da página {#sample-configuration-of-page-properties}

Essa amostra demonstra a técnica de comparação da caixa de diálogo do [Fusão de Recursos Sling](/help/sites-developing/sling-resource-merger.md); , incluindo a utilização de [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Também ilustra o uso de ambos `cq:showOnCreate` e `cq:hideOnEdit`.

CÓDIGO NO GITHUB

Você pode encontrar o código desta página no GitHub

* [Abra o projeto de diálogo da extensão de criação do aem-page no GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
