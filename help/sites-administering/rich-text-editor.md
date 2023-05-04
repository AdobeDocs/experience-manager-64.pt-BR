---
title: Configurar o editor de rich text
description: Saiba como configurar o Editor de Rich Text do AEM.
contentOwner: AG
exl-id: 2d5e9ada-1567-43dc-ab19-6891e20e1d0b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2695'
ht-degree: 1%

---

# Configurar o editor de rich text {#configure-the-rich-text-editor}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O Editor de Rich Text (RTE) fornece aos autores uma ampla variedade de funcionalidades para editar seu conteúdo de texto. Os ícones, caixas de seleção, barra de ferramentas e menus são fornecidos para uma experiência de edição de texto WYSIWYG.

Para saber como usar os recursos do RTE para criação, consulte [Usar o editor de rich text para criação](/help/sites-authoring/rich-text-editor.md). O RTE pode ser configurado para ativar, desativar e estender os recursos disponíveis nos componentes de criação. O workflow a seguir ilustra uma ordem recomendada de conclusão das tarefas de configuração do RTE no Experience Manager.

![Fluxo de trabalho típico para configurar o Editor de Rich Text](assets/rte_workflow_v1.png)

*Figura: Fluxo de trabalho típico para configurar o Editor de Rich Text*

## Entender a interface habilitada para toque e a interface clássica {#understand-touch-enabled-ui-and-classic-ui}

A interface de usuário habilitada para toque é a interface de usuário padrão para AEM. O Adobe apresentou a interface do usuário de toque com [design responsivo](/help/sites-authoring/responsive-layout.md) para o ambiente de criação, na versão 5.6. A interface do usuário de toque foi projetada para dispositivos de toque e desktop. A interface do usuário é consideravelmente diferente da interface clássica original.

![Barra de ferramentas do Editor de Rich Text na interface habilitada para toque](assets/chlimage_1-404.png)

*Figura: Barra de ferramentas do Editor de Rich Text na interface habilitada para toque*

![Barra de ferramentas do Editor de Rich Text na interface clássica](assets/rtedefault.png)

*Figura: Barra de ferramentas do Editor de Rich Text na interface clássica*

>[!MORELIKETHIS]
>
>* [Recomendações da interface do usuário](/help/sites-deploying/ui-recommendations.md)
>* Sobre como descontinuar a interface do usuário clássica, consulte [Notas de versão do AEM 6.4](/help/release-notes/deprecated-removed-features.md)
>* Para obter a diferença entre as interfaces de usuário, consulte [Interface do usuário de toque e clássica](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* Para entender a interface habilitada para toque em detalhes, consulte [Conceitos da interface de AEM toque](/help/sites-developing/touch-ui-concepts.md)


## Vários modos de edição {#editingmodes}

Os autores podem criar e editar conteúdo textual no AEM usando os diferentes modos de componentes. As opções da barra de ferramentas para criação e formatação de conteúdo e a experiência do usuário de componentes habilitados para RTE em diferentes modos de edição variam com base nas configurações de RTE.

| Modo de edição | Área de edição | Recursos recomendados a serem ativados | Interface de toque | IU Clássica |
|--- |--- |--- |--- |--- |
| Inline | Edição no local para edições rápidas e secundárias; Formatar sem abrir uma caixa de diálogo | Recursos mínimos do RTE | Y | Y |
| Tela cheia do RTE | Capa a página inteira | Todos os recursos RTE necessários | Y | N |
| Caixa de diálogo | Caixa de diálogo na parte superior do conteúdo da página, mas não cobre a página inteira | Todos os recursos de RTE necessários na interface clássica; Habilite criteriosamente os recursos na interface do usuário de toque | Y | Y |
| Tela cheia da caixa de diálogo | Igual ao modo de tela cheia; contém campos da caixa de diálogo ao lado do RTE | Todos os recursos RTE necessários | Y | N |

>[!NOTE]
>
>O recurso de edição de origem não está disponível no modo de edição em linha na interface do usuário habilitada para toque. Não é possível arrastar as imagens no modo de tela cheia. Todos os outros recursos funcionam em todos os modos.

### Edição em linha {#inline-editing}

Quando aberto (com um toque/clique duplo lento), o conteúdo pode ser editado na página. Uma barra de ferramentas compacta com opções básicas é apresentada.

![Edição em linha com a barra de ferramentas básica na interface do usuário habilitada para toque](assets/chlimage_1-405.png)

*Figura: Edição em linha com a barra de ferramentas básica na interface do usuário habilitada para toque*

Na interface clássica, um clique duplo lento no componente permite a edição em linha e um contorno laranja destaca o conteúdo. Se o Localizador de conteúdo estiver aberto, uma barra de ferramentas com as opções disponíveis de formatação do RTE será exibida na parte superior da janela. Se o Localizador de conteúdo não estiver aberto, as opções de formatação não serão exibidas e você poderá fazer apenas edições básicas de texto.

### Edição em de tela cheia {#full-screen-editing}

AEM componentes podem ser abertos na visualização em tela cheia, que oculta o conteúdo da página e ocupa a tela disponível. Considere a edição em tela cheia de uma versão detalhada da edição em linha, pois oferece as opções de edição mais abrangentes. Ele pode ser aberto clicando em ![rte_fullscreen](assets/rte_fullscreen.png), na barra de ferramentas compacta, ao usar o modo de edição em linha.

O modo de tela cheia da caixa de diálogo fornece uma barra de ferramentas de RTE detalhada e as opções e os componentes disponíveis no modo de diálogo. É aplicável somente para uma caixa de diálogo que contém o RTE juntamente com outros componentes.

![A barra de ferramentas do RTE detalhada ao editar no modo de tela cheia na interface do usuário habilitada para toque](assets/chlimage_1-406.png)

*Figura: A barra de ferramentas do RTE detalhada ao editar no modo de tela cheia na interface do usuário habilitada para toque*

### Edição de caixa de diálogo {#dialog-editing}

Quando um componente é clicado duas vezes na interface clássica, uma caixa de diálogo é aberta para edição do conteúdo. A caixa de diálogo é aberta na parte superior da página existente. Em alguns cenários específicos, a caixa de diálogo é aberta como uma janela pop-up. Por exemplo, quando um componente de Texto faz parte de uma coluna em um layout de página de várias colunas e a área disponível para a caixa de diálogo é menor.

![Modo de edição de caixa de diálogo na interface habilitada para toque](assets/dialog_editing_modetouchui.png)

*Figura: Modo de edição de caixa de diálogo na interface habilitada para toque*

![Caixa de diálogo na interface clássica que contém a barra de ferramentas detalhada para edição](assets/chlimage_1-407.png)

*Figura: Caixa de diálogo na interface clássica que contém a barra de ferramentas detalhada para edição*

## Sobre plug-ins do RTE e os recursos associados {#aboutplugins}

A funcionalidade é disponibilizada por meio de uma série de plug-ins, cada um com:

* A `features` propriedade:

   * Isso é usado para ativar ou desativar a funcionalidade básica desse plug-in.
   * Isso pode ser configurado através de um procedimento normalizado.

* Quando apropriado, mais propriedades e opções que exigem configuração especializada.

Os recursos básicos do RTE são ativados ou desativados pelo valor do `features` em um nó específico do plug-in adequado.

A tabela a seguir lista os plug-ins atuais, mostrando:

* IDs de plug-in com um link para a documentação da API. A ID é usada como o nome do nó quando [ativação de um plug-in](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Valores permitidos para o `features` propriedade.
* Uma descrição da funcionalidade fornecida pelo plug-in.

| ID do plug-in | recursos | Descrição |
|--- |--- |--- |
| editar | recortar copiar colar padrão colar-pintar-texto colar-pasta-pasta-wordhtml | [Recortar, copiar e, os três modos de colar](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [findreplace](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | localizar substituir | Localizar e substituir. |
| [format](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | negrito itálico sublinhado | [Formatação básica de texto](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles). |
| [imagem](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | imagem | Suporte básico a imagens (arraste do conteúdo ou do Localizador de conteúdo). Dependendo do navegador, o suporte tem comportamentos diferentes para autores |
| [teclas](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | Para definir esse valor, consulte [tamanho da guia](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tab-size). |
| [justify](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justificativa da justiça | Alinhamento de parágrafo. |
| [links](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | modificar a âncora de desvinculação de link | [Hiperlinks e âncoras](/help/sites-administering/configure-rich-text-editor-plug-ins.md#link-styles). |
| [listas](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | recuo não ordenado | Esse plug-in controla ambos [recuo e listas](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indent-margin); incluindo listas aninhadas. |
| [miscelânea](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | opções especiais | Ferramentas diversas permitem que os autores insiram [caracteres especiais](/help/sites-administering/configure-rich-text-editor-plug-ins.md#special-char) ou edite a fonte do HTML. Além disso, você pode adicionar um todo [gama de caracteres especiais](/help/sites-administering/configure-rich-text-editor-plug-ins.md#define-range-char) se quiser definir sua própria lista. |
| Paraformat | paraformat | Os formatos de parágrafo padrão são Parágrafo, Cabeçalho 1, Cabeçalho 2 e Cabeçalho 3 (`<p>`, `<h1>`, `<h2>`e `<h3>`). Você pode [adicionar mais formatos de parágrafo](/help/sites-administering/configure-rich-text-editor-plug-ins.md#para-formats) ou estender a lista. |
| verificação ortográfica | texto de verificação | [Verificador ortográfico com reconhecimento de idioma](/help/sites-administering/configure-rich-text-editor-plug-ins.md#add-dict). |
| estilos | estilos | Suporte para estilo usando uma classe CSS. [Adicionar novos estilos de texto](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles) se quiser adicionar (ou estender) seu próprio intervalo de estilos para uso com texto. |
| subsobrescrito | sobrescrito subscrito | Extensões para os formatos básicos, adicionando sub e super scripts. |
| tabela | tabela removível inserir removerow inserir coluna removecolumn cellprops mergecells dividir seleção de célula | Consulte [configurar estilos de tabela](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles), se quiser adicionar seus próprios estilos para tabelas inteiras ou células individuais. |
| desfazer | desfazer refazer | Tamanho histórico de [desfazer e refazer](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undo-history) operações. |

>[!NOTE]
>
>O plug-in de tela cheia não é compatível com o modo de diálogo. Utilização do `dialogFullScreen` configuração para configurar a barra de ferramentas para o modo de tela cheia.

## Entender os caminhos e os locais de configuração {#understand-the-configuration-paths-and-locations}

O [modo de edição do RTE (e a interface do usuário)](#editingmodes) que você fornece para seus autores e decide o local para os detalhes de configuração quando [ativação dos plug-ins do RTE](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin):

| Modo de edição | Localização da interface do usuário de toque | Localização da interface clássica |
|---|---|---|
| Inline | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Tela cheia | `cq:editConfig/cq:inplaceEditing` | Não aplicável |
| Caixa de diálogo | `cq:dialog` | `dialog` |
| Caixa de diálogo de tela cheia | `cq:dialog` | Não aplicável |

>[!NOTE]
>
>Não nomeie o nó sob `cq:inplaceEditing` as `config`. Ligado `cq:inplaceEditing` , defina as seguintes propriedades:
>
>* **Nome**: `configPath`
>* **Tipo**: `String`
>* **Valor**: caminho do nó que contém a configuração real
>
>Não nomeie o nó de configuração do RTE como `config`. Caso contrário, as configurações do RTE entrarão em vigor apenas para os administradores e não para os usuários do grupo `content-author`.

Configure as seguintes propriedades que se aplicam somente ao modo de edição da caixa de diálogo na interface de toque:

* `useFixedInlineToolbar`: Defina essa propriedade booleana definida no nó RTE (um com sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) a `True`, para corrigir a barra de ferramentas do RTE em vez de flutuar.

   Quando essa propriedade é verdadeira, a edição de Richtext é, por padrão, iniciada no evento &quot;foundation-contentloaded&quot;.

   Para evitar isso, defina a propriedade `customStart` para `True`e acione o evento &quot;rte-start&quot; para iniciar a edição do RTE. Quando essa propriedade é &#39;true&#39;, o comportamento padrão, início de rte no clique, não funciona.

* `customStart`: Defina essa propriedade booleana definida no nó RTE como `True`, para controlar quando iniciar o RTE, acionando o evento `rte-start`.

* `rte-start`: Acione esse evento na `contenteditable-div` do RTE, quando começar a editar o RTE. Isso funciona somente se `customStart` foi definida como true.

Quando o RTE é usado na caixa de diálogo habilitada para toque, defina a propriedade `useFixedInlineToolbar` como true é obrigatório para evitar problemas.

## Personalização na edição do local {#customizing-in-place-editing}

Você pode definir em qual seletor de HTML o editor de texto é iniciado configurando as seguintes propriedades:

* **`editElementQuery`** - Definido em `cq:InplaceEditingConfig`, essa propriedade é usada para especificar um seletor do elemento HTML no qual a edição em linha do Componente de texto será iniciada. Se não especificado, a edição em linha é iniciada diretamente no HTML de Componente de texto.
* **`textPropertyName`** - Definido em `cq:InplaceEditingConfig`, essa propriedade é usada para especificar o nome da propriedade que será salva no nó de conteúdo, onde o valor de HTML do componente de texto será mantido após a edição em linha.

A propriedade correspondente para o modo de diálogo é `name`.

## Ative as funcionalidades do RTE ativando plug-ins {#enable-rte-functionalities-by-activating-plug-ins}

As funcionalidades do RTE são disponibilizadas por meio de uma série de plug-ins, cada um com a propriedade features . Você pode configurar a propriedade features para ativar ou desativar os vários recursos de cada plug-in.

Para obter configurações detalhadas dos plug-ins do RTE, consulte [como ativar e configurar os plug-ins do RTE](/help/sites-administering/configure-rich-text-editor-plug-ins.md).

Baixe essa configuração de amostra para entender como configurar o RTE. Neste pacote, todos os recursos estão ativados.

[Obter arquivo](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>O [Componente de texto Componentes principais](https://helpx.adobe.com/experience-manager/core-components/using/text.html) O permite que os editores de modelo configurem muitos plug-ins do RTE na interface do usuário como políticas de conteúdo, eliminando a necessidade de configuração técnica. As políticas de conteúdo podem funcionar com as configurações da interface do usuário do RTE, conforme descrito. Para obter mais informações, consulte o [Configurações e políticas de conteúdo da interface do usuário do RTE](/help/sites-administering/rich-text-editor.md#rtecontentpolicies), [Criar modelos de página](/help/sites-authoring/templates.md)e o [Documentação do desenvolvedor dos Componentes principais](https://helpx.adobe.com/experience-manager/core-components/using/developing.html).

>[!NOTE]
>
>Para fins de referência, os componentes de Texto padrão (fornecidos como parte de uma instalação padrão) podem ser encontrados em:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>Para criar seu próprio componente de texto, copie o componente acima em vez de editar esses componentes.

## Configurar a barra de ferramentas do RTE {#dialogfullscreen}

AEM permite configurar a interface do usuário para o Editor de RichText de forma diferente para os diferentes modos de edição. As configurações padrão são fornecidas abaixo. Você pode substituir esses padrões com base em seus requisitos.

Para obter a melhor experiência de criação:

* Em uma caixa de diálogo flutuante, ative apenas os plug-ins que não têm um pop-up, pois a caixa de diálogo flutuante é menor em tamanho.
* Na caixa de diálogo de tela cheia, ative todos os plug-ins necessários, até mesmo os plug-ins com um pop-up maior, como `Paste` plug-in. Use o `dialogFullScreen` configuração descrita abaixo.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Diferentes configurações da interface do usuário são usadas para o modo em linha e o modo de tela cheia. A propriedade da barra de ferramentas é usada para especificar os botões da barra de ferramentas. Por exemplo, se o botão for um recurso (por exemplo, `Bold`), é especificado como `PluginName#FeatureName` (por exemplo, `links#modifylink`). Se o botão for um portátil (contendo alguns recursos de um plug-in), ele será especificado como `#PluginName` (por exemplo, `#format`). Separadores ( | ) entre um grupo de botões pode ser especificado com &#39;-&#39;.

O nó pop-up no modo em linha ou em tela cheia contém uma lista dos recursos que estão sendo usados. Cada nó filho sob o `popovers` o nó é nomeado após o plug-in (por exemplo, `format`). Tem uma propriedade `items` contendo uma lista de recursos do plug-in (por exemplo, `format#bold`).

## Configurações da interface do usuário do RTE e políticas de conteúdo {#rtecontentpolicies}

Os administradores podem controlar as opções de RTE usando políticas de conteúdo, em vez de fazer a configuração conforme descrito acima. As políticas de conteúdo definem as propriedades de design de um componente, quando usadas como parte de um [modelo editável](../sites-authoring/templates.md). Por exemplo, se um componente de texto que usa o RTE for usado com um modelo editável, a política de conteúdo poderá definir que a opção em negrito esteja disponível e algumas opções de formatação de parágrafo estarão disponíveis. As políticas de conteúdo são reutilizáveis e podem ser aplicadas em vários modelos.

AEM 6.4 do Service Pack 3 em diante, as opções disponíveis no RTE fluem downstream das configurações da interface do usuário para as políticas de conteúdo.

* As configurações da interface do usuário definem quais opções estão disponíveis para as políticas de conteúdo.
* Se a configuração da interface do usuário do RTE tiver sido removida ou não ativar um item, a política de conteúdo não poderá configurá-la.
* Um autor tem acesso somente à funcionalidade disponibilizada pelas configurações da interface do usuário e pelas políticas de conteúdo.

Como exemplo, você pode ver a variável [Documentação do componente principal de texto](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor).

## Personalizar mapeamento entre ícones e comandos da barra de ferramentas {#iconstoolbar}

Você pode personalizar o mapeamento entre os ícones Corais exibidos na barra de ferramentas do RTE e os comandos disponíveis. Não é possível usar outros ícones além dos ícones Coral.

1. Criar um nó chamado `icons` under `uiSettings/cui`.

1. Crie nós para ícones individuais abaixo dele.
1. Em cada um dos nós de ícone individuais, especifique um ícone Coral e um comando para mapear para o ícone.

Abaixo está um trecho de amostra para mapear o comando em negrito para o ícone Coral chamado `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## Alternar para Editor de Rich Text da CoralUI 2 {#switch-to-coralui-rich-text-editor}

Em uma página, você pode incluir a clientlib do RTE CoralUI 2 ou a clientlib do RTE CoralUI 3. Por padrão, o Editor de Rich Text inclui a clientlib do RTE CoralUI 3. Para alternar para o RTE CoralUI 2, execute as seguintes etapas.

>[!NOTE]
>
>O Adobe não recomenda a alternância como prática recomendada. Alterne para CoralUI 2 RTE como último recurso. Os plug-ins personalizados para o RTE CoralUI 2 funcionam com o RTE CoralUI 3 se os plug-ins não dependerem dos internos do RTE, como classes. Se você estiver usando plug-ins personalizados para o RTE CoralUI 3, use `rte.coralui3` biblioteca.

1. Sobrepor o nó `/libs/cq/gui/components/authoring/editors/clientlibs/core` under `/apps`e faça o seguinte:

   * Substituir `rte.coralui3` com `rte.coralui2` para a propriedade dependencies .
   * Substituir `cq.authoring.editor.core.inlineediting.rte.coralui3` com `cq.authoring.editor.core.inlineediting.rte.coralui2` para a propriedade embed .
   * Substituir `cq.authoring.rte.coralui3` com `cq.authoring.rte.coralui2` para a propriedade embed .

1. Sobrepor os nós `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` e `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` under `/apps`.

   Remover categoria `cq.authoring.dialog` from `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` e adicione-o a `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Altere qualquer outra dependência que esteja sendo incluída na página de `rte.coralui3` para `rte.coralui2`. Por exemplo, depois de sobrepor o nó `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` under `/apps`, alterar qualquer dependência de `rte.coralui3` para `rte.coralui2`.

1. Sobrepor o nó `cq/ui/widgets` under `/apps`. Substituir a dependência `cq.rte` no nó `/apps/cq/ui/widgets` com `cq.coralui2.rte`.

>[!NOTE]
>
>O RTE CoralUI 2 usa modelos handlebars para caixas de diálogo de plug-in. Portanto, a clientlib do RTE CoralUI 2 tinha uma dependência na clientlib handlebars. O RTE CoralUI 3 não usa modelos handlebars e não tem nenhuma dependência associada. Se os plug-ins personalizados usam modelos handlebars, inclua a clientlib handlebars em sua página da Web.

## Informações adicionais {#further-information}

Para obter mais informações sobre como configurar o RTE, consulte o [API do widget AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) referência.

Especificamente, para ver os plug-ins e as opções relacionadas disponíveis:

* O [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) fornece um campo de formulário para editar informações de texto estilizado (rich text). Para saber todos os parâmetros disponíveis para o formulário Rich Text, consulte as Opções de configuração.
* O componente RichText fornece uma ampla variedade de funcionalidades usando plug-ins listados em [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Para cada plug-in:

   * Consulte os Recursos para obter detalhes sobre a funcionalidade que pode ser ativada (ou desativada).
   * Consulte as Opções de configuração para todos os parâmetros disponíveis para obter a configuração detalhada do plug-in adequado.

* Mais informações sobre Regras de HTML para links também estão disponíveis.

As opções acima podem ser usadas para estender e personalizar seu próprio RTE. Por exemplo, para listar as âncoras disponíveis na página ao criar um link, você pode fornecer sua própria implementação da variável `LinkPlugin`.

## Limitações conhecidas {#known-limitations}

AEM recurso RTE tem as seguintes limitações:

* Os recursos do RTE são compatíveis apenas em caixas de diálogo de componentes AEM. O RTE não é compatível com assistentes ou formulários básicos como [Propriedades da página](/help/sites-developing/page-properties-views.md) e [Andaime](/help/sites-authoring/scaffolding.md) na interface habilitada para toque.

* AEM não funciona em [Dispositivos híbridos](/help/release-notes/known-issues.md).

* Não nomeie o nó de configuração do RTE `config`. Caso contrário, a configuração do RTE entrará em vigor apenas para os administradores e não para os usuários do grupo `content-author`.

* O RTE não é compatível com quadros ou iframe em linha para incorporar o conteúdo.

>[!MORELIKETHIS]
>
>* [Configurar plug-ins do RTE](configure-rich-text-editor-plug-ins.md)
>* [Usar o editor de rich text para criação](../sites-authoring/rich-text-editor.md)
>* [Configurar o RTE para sites acessíveis](rte-accessible-content.md)
>* [Paridade de recursos da interface do usuário de toque e da interface clássica](../release-notes/touch-ui-features-status.md)
>* [Amostra de tutorial para criar componente composto de vários campos](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

