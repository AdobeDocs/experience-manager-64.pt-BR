---
title: Configuração do RTE para produção de sites acessíveis
seo-title: Configuring RTE for Producing Accessible Sites
description: Saiba como configurar o Editor de Rich Text AEM para produzir sites acessíveis.
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 1%

---

# Configuração do RTE para produção de sites acessíveis {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM suporta ambos:

* recursos padrão de acessibilidade, incluindo texto alternativo para imagens
* bem como recursos adicionais que podem ser acessados ao criar conteúdo com componentes que usam o editor de rich text (RTE)

>[!NOTE]
>
>* [Guia rápido para a WCAG 2.0](/help/managing/qg-wcag.md)
>* [Criação de conteúdo acessível (Conformidade com a WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)


Os autores de conteúdo podem usar os recursos do RTE para fornecer informações de acessibilidade, ao adicionar conteúdo a uma página. Isso pode incluir a adição de informações estruturais por meio de cabeçalhos e elementos de parágrafo.

Você pode [configurar e personalizar esses recursos configurando plug-ins do RTE](#configuring-the-plugin-features) para o componente. Por exemplo, a variável `paraformat` o plug-in permite adicionar outros elementos semânticos em nível de bloco, incluindo a extensão do número de níveis de cabeçalho suportados além do básico `H1`, `H2` e `H3` fornecido por padrão.

O RTE está disponível em diversos componentes, tanto da interface habilitada para toque quanto da clássica. No entanto, o principal componente para usar o RTE é o **Texto** componente.

O **Texto** no AEM está disponível para as interfaces de usuário habilitadas para toque e clássica. As imagens a seguir mostram o editor de rich text com um intervalo de plug-ins ativados, incluindo `paraformat`:

* O **Texto** componente na interface habilitada para toque:

   ![Componente de texto (RTE) no modo de tela cheia na interface do usuário habilitada para toque.](assets/chlimage_1-206.png)

* O **Texto** na interface clássica:

   ![Caixa de diálogo de edição (RTE) do componente de texto na interface clássica.](assets/chlimage_1-207.png)

>[!NOTE]
>
>Há diferenças entre os recursos do RTE disponíveis na interface clássica e na interface habilitada para toque. Para obter mais detalhes, consulte
>
>* [Plug-ins e seus recursos](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Plug-ins e seus recursos - Interface habilitada para toque](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## Configuração dos recursos do plug-in {#configuring-the-plugin-features}

Instruções completas sobre como configurar o RTE estão disponíveis no [Configuração do editor de rich text](/help/sites-administering/rich-text-editor.md) página. Isso abrange todos os problemas, incluindo as principais etapas:

* [Plug-ins e seus recursos](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Locais de configuração](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Ativar um plug-in e configurar a propriedade de recursos](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Configuração de outra funcionalidade do RTE](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Ao configurar um plug-in no `rtePlugins` sub-ramificação no CRXDE Lite (consulte a imagem a seguir), é possível ativar todos os recursos ou recursos específicos desse plug-in.

![CRXDE Lite mostrando um exemplo de rtePlugin.](assets/chlimage_1-208.png)

### Exemplo - Especificação de formatos de parágrafo disponíveis no campo de seleção RTE {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Os novos formatos de bloco semântico podem ser disponibilizados para seleção através de:

1. Dependendo do RTE, determine e navegue até o [local de configuração](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Ativar o campo de seleção Parágrafos](/help/sites-administering/rich-text-editor.md); por [ativação do plug-in](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Especifique os formatos que deseja disponibilizar no campo de seleção Parágrafos](/help/sites-administering/rich-text-editor.md).
1. Os formatos de parágrafo são então disponibilizados ao autor de conteúdo a partir dos campos de seleção no RTE. Elas podem ser acessadas:

   * Uso do parágrafo ([travesseiro](https://en.wikipedia.org/wiki/Pilcrow)) na interface habilitada para toque:

   ![Ícone Parágrafo (pilcrow).](do-not-localize/chlimage_1-7.png)

   * Usar o **Formato** no campo (seletor suspenso) da interface clássica.


Com elementos estruturais disponíveis no RTE por meio das opções de formato de parágrafo, o AEM oferece uma boa base para o desenvolvimento de conteúdo acessível. Os autores de conteúdo não podem usar o RTE para formatar o tamanho da fonte, as cores ou outros atributos relacionados, impedindo a criação de formatação em linha. Em vez disso, eles devem selecionar os elementos estruturais apropriados, como cabeçalhos e usar estilos globais escolhidos na opção Estilos . Isso garante uma marcação limpa, opções maiores para usuários que navegam com suas próprias folhas de estilos e conteúdo estruturado corretamente.

## Uso do recurso Editar fonte {#use-of-the-source-edit-feature}

Em alguns casos, os autores de conteúdo considerarão necessário examinar e ajustar o código-fonte do HTML criado usando o RTE. Por exemplo, um conteúdo criado no RTE pode exigir marcação adicional para garantir a conformidade com a WCAG 2.0. Isso pode ser feito com o [edição de origem](/help/sites-administering/rich-text-editor.md#aboutplugins) da RTE. É possível especificar a variável [ `sourceedit` no `misctools` plugin](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Use o `sourceedit` recurso com cuidado. A digitação de erros e/ou recursos não suportados pode causar mais problemas.

## Adicionar suporte para elementos e atributos de HTML adicionais {#adding-support-for-additional-html-elements-and-attributes}

Para estender ainda mais os recursos de acessibilidade de AEM, é possível estender os componentes existentes com base no RTE (como **Texto** e **Tabela** componentes) com elementos e atributos adicionais.

O procedimento a seguir ilustra como estender o **Tabela** com um **Legenda** elemento que fornece informações sobre uma tabela de dados para usuários de tecnologia assistiva:

### Exemplo - Adicionar a legenda à caixa de diálogo Propriedades da tabela {#example-adding-the-caption-to-the-table-properties-dialog}

No construtor do `TablePropertiesDialog`, adicione um campo de entrada de texto adicional usado para editar a legenda. Observe que `itemId` deve ser definido como `caption` (ou seja, o nome do atributo DOM) para manipular automaticamente seu conteúdo.

Em **Tabela** você deve definir ou remover explicitamente o atributo para/do elemento DOM. O valor é transmitido pela caixa de diálogo no `config` objeto. Observe que os atributos DOM devem ser definidos/removidos usando o `CQ.form.rte.Common` métodos ( `com` é um atalho para `CQ.form.rte.Common`) para evitar armadilhas comuns com implementações de navegador.

>[!NOTE]
>
>Este procedimento é adequado somente para a interface clássica.

### Instruções passo a passo {#step-by-step-instructions}

1. Inicie o CRXDE Lite. Por exemplo: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   para:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Talvez seja necessário criar pastas intermediárias se elas ainda não existirem.

1. Copiar:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   para:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Abra o seguinte arquivo para edição (abra com um clique duplo):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. No `constructor` , antes da leitura da linha:

   ```
   var dialogRef = this;
   ```

   Adicione o seguinte código:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Abra o seguinte arquivo:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Adicione o seguinte código ao final do `transferConfigToTable` método :

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Salve as alterações usando **Salvar tudo**

>[!NOTE]
>
>Um campo de texto simples não é o único tipo de entrada permitido para o valor do elemento de legenda. Qualquer widget ExtJS, que fornece o valor da legenda por meio de seu `getValue()` , poderia ser usado.
>
>Para adicionar recursos de edição a outros elementos e atributos adicionais, verifique se:
>
>* O `itemId` para cada campo correspondente é definida com o nome do atributo DOM apropriado (`TablePropertiesDialog`).
>* O atributo é definido e/ou removido explicitamente no elemento DOM (`Table`).

