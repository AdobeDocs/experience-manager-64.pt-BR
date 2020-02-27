---
title: Configurar o Editor de Rich Text
seo-title: Configurar o Editor de Rich Text
description: Saiba como configurar o Editor de Rich Text do AEM.
seo-description: Saiba como configurar o Editor de Rich Text do AEM.
uuid: 82d2fe41-676a-4a49-939f-13374b9d869f
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 9248d09c-b749-4aca-9167-1707c1dd8a53
translation-type: tm+mt
source-git-commit: 01a748a6f6f92c752fc6a14005f236fee304c2eb

---


# Configure the Rich Text Editor {#configure-the-rich-text-editor}

O Editor de Rich Text (RTE) fornece aos autores uma ampla variedade de funcionalidades para editar seu conteúdo de texto. Ícones, caixas de seleção, barra de ferramentas e menus são fornecidos para uma experiência de edição de texto WYSIWYG.

O RTE pode ser configurado para ativar, desativar e estender os recursos disponíveis nos componentes de criação. Para saber como usar os recursos do RTE para criação, consulte [Usar o Editor de Rich Text para criação](/help/sites-authoring/rich-text-editor.md).

O fluxo de trabalho a seguir ilustra uma ordem recomendada para a conclusão das tarefas de configuração do RTE.

![Fluxo de trabalho típico para configurar o Editor de Rich Text](assets/rte_workflow_v1.png)

**** Figura: Fluxo de trabalho *típico para configurar o Editor de Rich Text*

## Entenda a interface habilitada para toque e a interface clássica {#understand-touch-enabled-ui-and-classic-ui}

A interface do usuário habilitada para toque é a interface padrão do AEM. A Adobe introduziu a interface do usuário para toque com design [](/help/sites-authoring/responsive-layout.md) responsivo para o ambiente de criação, na versão 5.6.A interface do usuário de toque foi projetada para dispositivos de toque e desktop. A interface do usuário é consideravelmente diferente da interface clássica original.

![Barra de ferramentas do Editor de Rich Text na interface habilitada para toque](assets/chlimage_1-404.png)

**** Figura: Barra de ferramentas do Editor de Rich Text na interface habilitada para toque **

![Barra de ferramentas do Editor de Rich Text na interface clássica](assets/rtedefault.png)

**** Figura: Barra de ferramentas do Editor de Rich Text na interface clássica **

**Consulte também**:

* [Recomendações da interface do usuário](/help/sites-deploying/ui-recommendations.md)
* Sobre a substituição da interface clássica, consulte Notas de versão do [AEM 6.4](/help/release-notes/deprecated-removed-features.md)
* Para obter a diferença entre as interfaces de usuário, consulte Interface de usuário [sensível ao toque e Interface clássica](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
* Para entender a interface habilitada para toque em detalhes, consulte [Conceitos da interface do usuário de toque do AEM](/help/sites-developing/touch-ui-concepts.md)

## Vários modos de edição {#editingmodes}

Os autores podem criar e editar conteúdo textual no AEM usando os diferentes modos de componentes. As opções da barra de ferramentas para criação e formatação de conteúdo e a experiência do usuário dos componentes habilitados para RTE em diferentes modos de edição variam com base nas configurações do RTE.

<table> 
 <tbody> 
  <tr> 
   <th>Modo de edição</th> 
   <th>Área de edição</th> 
   <th>Recursos recomendados a serem ativados<br /> </th> 
   <th>Interface do usuário de toque</th> 
   <th>Interface do usuário clássica</th> 
  </tr> 
  <tr> 
   <td>Inline</td> 
   <td>Edição no local para edições rápidas e secundárias; Formatar sem abrir uma caixa de diálogo</td> 
   <td>Recursos mínimos do RTE</td> 
   <td>S</td> 
   <td>S</td> 
  </tr> 
  <tr> 
   <td>RTE tela cheia</td> 
   <td>Cobre a página inteira<br /> </td> 
   <td>Todos os recursos RTE necessários<br /> </td> 
   <td>S</td> 
   <td>N<br /> </td> 
  </tr> 
  <tr> 
   <td>Caixa de diálogo</td> 
   <td>Caixa de diálogo sobre o conteúdo da página, mas não cobre a página inteira</td> 
   <td>Todos os recursos do RTE necessários na interface clássica; habilite criteriosamente os recursos na interface do usuário de toque<br /> </td> 
   <td>S</td> 
   <td>S</td> 
  </tr> 
  <tr> 
   <td>Tela cheia do diálogo<br /> </td> 
   <td>Igual ao modo de tela cheia; contém campos da caixa de diálogo ao lado do RTE<br /> </td> 
   <td>Todos os recursos RTE necessários</td> 
   <td>S</td> 
   <td>N</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O recurso de edição de origem não está disponível no modo de edição em linha na interface habilitada para toque. Não é possível arrastar imagens no modo de tela cheia. Todos os outros recursos funcionam em todos os modos.

### Edição em linha {#inline-editing}

Quando aberto (com um toque/clique duplo lento), o conteúdo pode ser editado na página. Uma barra de ferramentas compacta com opções básicas é apresentada.

![Edição em linha com barra de ferramentas básica na interface habilitada para toque](assets/chlimage_1-405.png)

**** Figura: Edição *em linha com barra de ferramentas básica na interface habilitada para toque*

Na interface clássica, um clique duplo lento no componente permite a edição em linha e um contorno laranja destaca o conteúdo. Se o Localizador de conteúdo estiver aberto, uma barra de ferramentas com as opções de formatação RTE disponíveis será exibida na parte superior da janela. Se o Localizador de conteúdo não estiver aberto, as opções de formatação não serão exibidas e você só poderá fazer edições de texto básicas.

### Full screen editing {#full-screen-editing}

Os componentes do AEM podem ser abertos na exibição em tela cheia que oculta o conteúdo da página e ocupa a tela disponível. Considere a edição em tela cheia de uma versão detalhada da edição em linha, já que ela oferece as opções de edição mais avançadas. Pode ser aberto clicando em ![rte_fullscreen](assets/rte_fullscreen.png), na barra de ferramentas compacta ao usar o modo de edição em linha.

O modo de tela cheia da caixa de diálogo fornece uma barra de ferramentas RTE detalhada e as opções e os componentes que estão disponíveis no modo de diálogo. É aplicável somente para uma caixa de diálogo que contenha RTE junto com outros componentes.

![A barra de ferramentas RTE detalhada ao editar no modo de tela cheia na interface habilitada para toque](assets/chlimage_1-406.png)

**** Figura: *A barra de ferramentas RTE detalhada ao editar no modo de tela cheia na interface habilitada para toque*

### Edição de diálogo {#dialog-editing}

Quando um componente é clicado duas vezes na interface clássica, uma caixa de diálogo é aberta para edição do conteúdo. A caixa de diálogo é aberta na parte superior da página existente. Em alguns cenários específicos, a caixa de diálogo é aberta como uma janela pop-up. Por exemplo, quando um componente de Texto faz parte de uma coluna em um layout de página com várias colunas e a área disponível para a caixa de diálogo é menor.

![Modo de edição de diálogo na interface habilitada para toque](assets/dialog_editing_modetouchui.png)

**** Figura: Modo de edição da *caixa de diálogo na interface habilitada para toque*

![Caixa de diálogo na interface clássica que contém a barra de ferramentas detalhada para edição](assets/chlimage_1-407.png)

**** Figura: Caixa de *diálogo na interface clássica que contém a barra de ferramentas detalhada para edição*

## Sobre plug-ins RTE e os recursos associados {#aboutplugins}

A funcionalidade é disponibilizada por meio de uma série de plug-ins, cada um com:

* Uma `features` propriedade:

   * Isso é usado para ativar ou desativar a funcionalidade básica desse plug-in.
   * Isso pode ser configurado usando um procedimento padronizado.

* Quando apropriado, mais propriedades e opções que exigem configuração especializada.

Os recursos básicos do RTE são ativados ou desativados pelo valor da `features` propriedade em um nó específico ao plug-in adequado.

A tabela a seguir lista os plug-ins atuais, mostrando:

* IDs de plug-in com um link para a documentação da API. A ID é usada como o nome do nó ao [ativar um plug-in](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Valores permitidos para a `features` propriedade.
* Uma descrição da funcionalidade fornecida pelo plug-in.

<table> 
 <tbody> 
  <tr> 
   <td><p>ID<br /> do plug-in <br /> </p> </td> 
   <td><p>features<br /> <br /> </p> </td> 
   <td><p>Descrição<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>editar</p> </td> 
   <td><p>copiar<br /> colar<br /> colar padrão<br /> colar-plaintext<br /> paste-wordhtml</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="_blank">Corte, copie e, os três modos</a>de colagem.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin">findreplace</a></p> </td> 
   <td><p>find<br /> replace</p> </td> 
   <td><p>Localize e substitua.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin">format</a></p> </td> 
   <td><p>negrito<br /> itálico<br /> sublinhado</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="_blank">Formatação</a>de texto básica.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin">imagem</a></p> </td> 
   <td><p>imagem</p> </td> 
   <td><p>Defina algumas propriedades de imagem, como alinhamento e texto alternativo. O suporte básico para arrastar e soltar imagens do Content Finder funciona sem esse plug-in.</p> <p><em>Observação</em>: O comportamento de criação pode variar com o navegador. Por exemplo, o Mozilla Firefox fornece recursos de redimensionamento, mas o Google Chrome não.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin">teclas</a></p> </td> 
   <td><p> </p> </td> 
   <td><p>Para definir esse valor, consulte o tamanho <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#tabsize" target="_blank">da</a>guia.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin">justify</a></p> </td> 
   <td><p>justificativa<br /> justificativa<br /> da justiça</p> </td> 
   <td><p>Alinhamento de parágrafo.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin">links</a></p> </td> 
   <td><p>modiylink<br /> desvincular<br /> âncora</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#linkstyles" target="_blank">Hiperlinks e âncoras</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin">lists</a></p> </td> 
   <td><p>recuo<br /> desordenado<br /> e recuo<br /> pedido</p> </td> 
   <td><p>Esse plug-in controla tanto o <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#indentmargin" target="_blank">recuo quanto as listas</a>; incluindo listas aninhadas.</p> </td> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin">miscelânea</a></p> </td> 
   <td><p>specialchars<br /> sourceedit</p> </td> 
   <td>Ferramentas diversas permitem que os autores digitem caracteres <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#spchar" target="_blank"></a> especiais ou editem a fonte HTML. Além disso, você pode adicionar um <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#definerangechar" target="_blank">intervalo completo de caracteres</a> especiais se desejar definir sua própria lista.</td> 
  </tr> 
  <tr> 
   <td><p>Paraformat</p> </td> 
   <td><p>paraformat</p> </td> 
   <td>Os formatos de parágrafo padrão são Parágrafo, Cabeçalho 1, Cabeçalho 2 e Cabeçalho 3 (&lt;p&gt;, &lt;h1&gt;, &lt;h2&gt; e &lt;h3&gt;). É possível <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#paraformats" target="_blank">adicionar mais formatos</a> de parágrafo ou estender a lista.</td> 
  </tr> 
  <tr> 
   <td><p>verificação ortográfica</p> </td> 
   <td><p>checktext</p> </td> 
   <td><p><a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#adddict" target="_blank">Verificador ortográfico</a>com reconhecimento de idioma.</p> </td> 
  </tr> 
  <tr> 
   <td><p>estilos</p> </td> 
   <td><p>estilos</p> </td> 
   <td>Suporte para estilização usando uma classe CSS. <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles" target="-blank">Adicione novos estilos</a> de texto se desejar adicionar (ou estender) seu próprio intervalo de estilos para uso com texto.</td> 
  </tr> 
  <tr> 
   <td><p>subsobrescrito</p> </td> 
   <td><p>sobrescrito<br /> subscrito</p> </td> 
   <td><p>Extensões para os formatos básicos, adicionando sub e super scripts.</p> </td> 
  </tr> 
  <tr> 
   <td><p>tabela</p> </td> 
   <td><p>tabela<br /> removível<br /> insertrow<br /> removerow<br /> insertcolumn<br /> removecolumn<br /> cellprops<br /> mergecells<br /> splitcell<br /> seltrow<br /> seleted colunas</p> </td> 
   <td>Consulte <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles" target="_blank">configurar estilos</a>de tabela, se desejar adicionar seus próprios estilos para tabelas inteiras ou células individuais.</td> 
  </tr> 
  <tr> 
   <td><p>desfazer</p> </td> 
   <td><p>undo<br /> redo</p> </td> 
   <td>Tamanho do histórico das operações <a href="/help/sites-administering/configure-rich-text-editor-plug-ins.md#undohistory" target="_blank">desfazer e refazer</a> .</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O plug-in de tela cheia não é suportado no modo de diálogo. Use a configuração `dialogFullScreen` para configurar a barra de ferramentas para o modo de tela cheia.

## Entenda os caminhos e locais de configuração {#understand-the-configuration-paths-and-locations}

O [modo de edição do RTE (e a interface do usuário)](#editingmodes) que você fornece aos autores decide o local dos detalhes de configuração quando você está [ativando os plug-ins](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)do RTE:

| Modo de edição | Localização para a interface de toque | Localização para a interface clássica |
|---|---|---|
| Inline | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Tela cheia | `cq:editConfig/cq:inplaceEditing` | Não aplicável |
| Caixa de diálogo | `cq:dialog` | `dialog` |
| Caixa de diálogo Tela cheia | `cq:dialog` | Não aplicável |

>[!NOTE]
>
>Não nomeie o nó `cq:inplaceEditing` como `config`. No `cq:inplaceEditing` nó, defina as seguintes propriedades:
>
>* **Nome**: `configPath`
   >
   >
* **Tipo**: `String`
   >
   >
* **Valor**: caminho do nó que contém a configuração real
>
>
Não nomeie o nó de configuração RTE como `config`. Caso contrário, as configurações do RTE terão efeito apenas para os administradores e não para os usuários do grupo `content-author`.

Configure as seguintes propriedades que se aplicam no modo de edição de Diálogo somente na interface de usuário de toque:

* `useFixedInlineToolbar`: Defina essa propriedade Booliana definida no nó RTE (um com sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) como `True`, para que a barra de ferramentas RTE seja corrigida em vez de flutuante.

   Quando essa propriedade é verdadeira, a edição de Richtext é, por padrão, iniciada no evento &quot;base-contentloaded&quot;.

   Para evitar isso, defina a propriedade `customStart` como `True`e dispare o evento &#39;início-da-taxa&#39; para iniciar a edição do RTE. Quando essa propriedade é &#39;true&#39;, o comportamento padrão, iniciar na hora do clique, não funciona.

* `customStart`: Defina essa propriedade Booliana definida no nó RTE como `True`, para controlar quando iniciar o RTE acionando o evento `rte-start`.

* `rte-start`: Acionar esse evento no RTE, quando iniciar a edição `contenteditable-div` do RTE. Isso funciona somente se `customStart` tiver sido definido como verdadeiro.

Quando o RTE é usado na caixa de diálogo habilitada para toque, a definição da propriedade `useFixedInlineToolbar` como true é obrigatória para evitar problemas.

## Ativar funcionalidades do RTE ativando plug-ins {#enable-rte-functionalities-by-activating-plug-ins}

As funcionalidades do RTE são disponibilizadas por meio de uma série de plug-ins, cada um com a propriedade features. Você pode configurar a propriedade features para ativar ou desativar os vários recursos de cada plug-in.

Para obter configurações detalhadas dos plug-ins RTE, consulte [como ativar e configurar os plug-ins](/help/sites-administering/configure-rich-text-editor-plug-ins.md)RTE.


Baixe esta configuração de amostra para entender como configurar o RTE. Neste pacote, todos os recursos estão ativados.

[Obter arquivo](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
>
>O componente [de texto Componentes](https://helpx.adobe.com/experience-manager/core-components/using/text.html) principais permite que os editores de modelo configurem muitos plug-ins RTE na interface do usuário como políticas de conteúdo, eliminando a necessidade de configuração técnica. As políticas de conteúdo podem funcionar com configurações da interface do usuário do RTE, conforme descrito. Para obter mais informações, consulte as configurações da interface do usuário do [RTE e as políticas](/help/sites-administering/rich-text-editor.md#rtecontentpolicies)de conteúdo, [Criar modelos](/help/sites-authoring/templates.md)de página e a documentação [do desenvolvedor dos Componentes](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)principais.

>[!NOTE]
>
>Para fins de referência, os componentes de Texto padrão (fornecidos como parte de uma instalação padrão) podem ser encontrados em:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>
Para criar seu próprio componente de texto, copie o componente acima em vez de editar esses componentes.

## Configurar a barra de ferramentas RTE {#dialogfullscreen}

O AEM permite que você configure a interface para o Editor de RichText de forma diferente para os diferentes modos de edição. As configurações padrão são fornecidas abaixo. É possível substituir esses padrões com base em seus requisitos.

Para obter a melhor experiência de criação:

* Em uma caixa de diálogo flutuante, ative apenas os plug-ins que não têm um pop-up, pois a caixa de diálogo flutuante é menor em tamanho.
* Na caixa de diálogo de tela cheia, ative todos os plug-ins necessários, mesmo os plug-ins com pop-up maior, como o `Paste` plug-in. Use a `dialogFullScreen` configuração descrita abaixo.

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

Diferentes configurações de interface são usadas para o modo em linha e para o modo de tela cheia. A propriedade da barra de ferramentas é usada para especificar os botões da barra de ferramentas. Por exemplo, se o botão for um recurso (por exemplo, `Bold`), ele será especificado como `PluginName#FeatureName` (por exemplo, `links#modifylink`). Se o botão for um pop-up (contendo alguns recursos de um plug-in), ele será especificado como `#PluginName` (por exemplo, `#format`). Separadores (| ) entre um grupo de botões pode ser especificado com &#39;-&#39;.

O nó pop-up no modo em linha ou em tela cheia contém uma lista das opções que estão sendo usadas. Cada nó filho sob o `popovers` nó é nomeado após o plug-in (por exemplo, `format`). Ela tem uma propriedade `items` que contém uma lista de recursos do plug-in (por exemplo, `format#bold`).

## Configurações e políticas de conteúdo da interface do usuário do RTE {#rtecontentpolicies}

Os administradores podem controlar as opções de RTE usando políticas de conteúdo, digamos, em vez de fazer a configuração conforme descrito acima. As políticas de conteúdo definem as propriedades de design de um componente quando usadas como parte de um modelo [](../sites-authoring/templates.md)editável. Por exemplo, se um componente de texto que usa o RTE for usado com um modelo editável, a política de conteúdo poderá definir que a opção em negrito esteja disponível e algumas opções de formatação de parágrafo estarão disponíveis. As políticas de conteúdo são reutilizáveis e podem ser aplicadas em vários modelos.

A partir do AEM 6.4 Service Pack 3, as opções disponíveis no RTE fluem a jusante das configurações da interface do usuário para as políticas de conteúdo.

* As configurações da interface do usuário definem quais opções estão disponíveis para as políticas de conteúdo.
* Se a configuração da interface do usuário do RTE tiver sido removida ou não ativar um item, a política de conteúdo não poderá configurá-lo.
* Um autor tem acesso apenas à funcionalidade que é disponibilizada pelas configurações da interface do usuário e pelas políticas de conteúdo.

Como exemplo, você pode ver a documentação [do Componente principal de](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)texto.

## Personalizar o mapeamento entre ícones e comandos da barra de ferramentas {#iconstoolbar}

Você pode personalizar o mapeamento entre os ícones Corais exibidos na barra de ferramentas RTE e os comandos disponíveis. Não é possível usar outros ícones além dos ícones Corais.

1. Crie um nó com o nome `icons` em `uiSettings/cui`.

1. Crie nós para ícones individuais abaixo dele.
1. Em cada um dos nós de ícone individuais, especifique um ícone Coral e um comando para mapear para o ícone.

Abaixo está um trecho de amostra para mapear o comando Negrito para o ícone Coral chamado `textItalic`.

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

## Alternar para o Editor de Rich Text CoralUI 2 {#switch-to-coralui-rich-text-editor}

Em uma página, você pode incluir a clientlib do RTE CoralUI 2 ou a clientlib do RTE CoralUI 3. Por padrão, o Editor de Rich Text inclui a clientlib RTE CoralUI 3. Para alternar para o RTE CoralUI 2, execute as seguintes etapas.

>[!NOTE]
>
>A Adobe não recomenda a alternância como prática recomendada. Alternar para RTE CoralUI 2 como último recurso. Os plug-ins personalizados para o RTE CoralUI 2 funcionam com o RTE CoralUI 3 se os plug-ins não dependerem dos internos do RTE, como classes. Se você estiver usando plug-ins personalizados para o RTE CoralUI 3, use a `rte.coralui3` biblioteca.

1. Sobreponha o nó `/libs/cq/gui/components/authoring/editors/clientlibs/core` em `/apps`e faça o seguinte:

   * Replace `rte.coralui3` with `rte.coralui2` for the dependencies property.
   * Replace `cq.authoring.editor.core.inlineediting.rte.coralui3` with `cq.authoring.editor.core.inlineediting.rte.coralui2` for the embed property.
   * Replace `cq.authoring.rte.coralui3` with `cq.authoring.rte.coralui2` for the embed property.

1. Sobreponha os nós `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` e `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` em `/apps`.

   Remova a categoria `cq.authoring.dialog` de `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` e adicione-a a `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Altere qualquer outra dependência que esteja sendo incluída na página de `rte.coralui3` para `rte.coralui2`. Por exemplo, depois de sobrepor o nó `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` em `/apps`, altere qualquer dependência dele de `rte.coralui3` para `rte.coralui2`.

1. Sobreponha o nó `cq/ui/widgets` em `/apps`. Substitua a dependência `cq.rte` no nó `/apps/cq/ui/widgets` por `cq.coralui2.rte`.

>[!NOTE]
>
>O RTE CoralUI 2 usa modelos handlebars para caixas de diálogo de plug-in. Portanto, a clientlib do RTE CoralUI 2 tinha uma dependência na clientlib handlebars. O RTE CoralUI 3 não usa modelos handlebars e não tem nenhuma dependência associada. Se os plug-ins personalizados usam modelos handlebars, inclua a clientlib handlebars na sua página da Web.

## Informações adicionais {#further-information}

Para obter mais informações sobre como configurar o RTE, consulte a referência à API [do widget](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html) AEM.

Em particular, para ver os plug-ins e as opções relacionadas disponíveis:

* O componente [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText) fornece um campo de formulário para editar informações de texto estilizado (rich text). Para saber todos os parâmetros disponíveis para o formulário Rich Text, consulte as Opções de configuração.
* O componente RichText fornece uma ampla variedade de funcionalidades usando plug-ins listados em [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Para cada plug-in:

   * consulte os Recursos para obter detalhes sobre a funcionalidade que pode ser ativada (ou desativada)
   * Consulte as Opções de configuração para ver todos os parâmetros disponíveis para obter a configuração detalhada do plug-in adequado

* Mais informações sobre Regras HTML para links também estão disponíveis.

As opções acima podem ser usadas para estender e personalizar seu próprio RTE. Por exemplo, para listar as âncoras disponíveis na página ao criar um link, você pode fornecer sua própria implementação do `LinkPlugin`.

## Limitações conhecidas {#known-limitations}

O recurso RTE AEM tem as seguintes limitações:

* Os recursos do RTE são suportados apenas nas caixas de diálogo de componentes do AEM. O RTE não é compatível com assistentes ou formulários básicos, como Propriedades [da](../sites-developing/page-properties-views.md) página e [Andaime](../sites-authoring/scaffolding.md) na interface habilitada para toque.

* O AEM não funciona em dispositivos [](../release-notes/known-issues.md)híbridos.

* Não nomeie o nó de configuração RTE `config`. Caso contrário, a configuração do RTE entrará em vigor somente para os administradores e não para os usuários do grupo `content-author`.

* O RTE não oferece suporte a quadros incorporados ou iframe para incorporar conteúdo.

>[!MORELIKETHIS]
>
>* [Configurar plug-ins RTE](configure-rich-text-editor-plug-ins.md)
>* [Usar o Editor de Rich Text para criação](../sites-authoring/rich-text-editor.md)
>* [Configurar o RTE para sites acessíveis](rte-accessible-content.md)
>* [Paridade de recursos da interface de usuário de toque e da interface de usuário clássica](../release-notes/touch-ui-features-status.md)
>* [Amostra do tutorial para criar um componente composto de vários campos](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

