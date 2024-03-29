---
title: Componentes AEM - Noções básicas
seo-title: AEM Components - The Basics
description: Ao começar a desenvolver novos componentes, você precisa entender os conceitos básicos de sua estrutura e configuração
seo-description: When you start to develop new components you need to understand the basics of their structure and configuration
uuid: 0225b34d-5ac4-40c3-b226-0c9b24bdf782
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 1f9867f1-5089-46d0-8e21-30d62dbf4f45
legacypath: /content/docs/en/aem/6-0/develop/components/components-develop
exl-id: 2c8956bf-e20a-441d-aecc-f2600e1fa11e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4995'
ht-degree: 1%

---

# Componentes AEM - Noções básicas{#aem-components-the-basics}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Quando você começa a desenvolver novos componentes, é necessário compreender as noções básicas de sua estrutura e configuração.

Esse processo envolve a leitura da teoria e a análise da grande variedade de implementações de componentes em uma instância de AEM padrão. Essa última abordagem é um pouco complicada pelo fato de que, embora a AEM tenha mudado para uma nova interface padrão, moderna e habilitada para toque, ela continua a oferecer suporte à interface clássica.

## Visão geral {#overview}

Esta seção aborda os principais conceitos e problemas como uma introdução aos detalhes necessários ao desenvolver seus próprios componentes.

### Planejamento {#planning}

Antes de começar a realmente configurar ou codificar seu componente, você deve perguntar:

* O que exatamente você precisa que o novo componente faça?

   * Uma especificação clara ajuda em todas as etapas de desenvolvimento, teste e transferência.

      Os detalhes podem mudar com o tempo, mas a especificação pode ser atualizada (embora as alterações também devam ser documentadas).

* Você precisa criar seu componente do zero ou pode herdar as noções básicas de um componente existente?

   * Não há necessidade de reinventar a roda.
   * Há vários mecanismos fornecidos pelo AEM para permitir herdar e estender detalhes de outra definição de componente, incluindo substituição, sobreposição e o [Fusão de Recursos Sling](/help/sites-developing/sling-resource-merger.md).

* Seu componente precisará de lógica para selecionar/manipular o conteúdo?

   * A lógica deve ser mantida separada da camada da interface do usuário. O HTL foi projetado para ajudar a garantir que isso aconteça.

* Seu componente precisará de formatação CSS?

   * A formatação de CSS deve ser mantida separada das definições do componente. Defina as convenções para nomear seus elementos HTML para que você possa modificá-los por meio de arquivos CSS externos.

* Que aspectos de segurança devo ter em consideração?

   * Consulte [Lista de verificação de segurança - Práticas recomendadas de desenvolvimento](/help/sites-administering/security-checklist.md#development-best-practices) para obter mais detalhes.

### Interface habilitada para toque vs clássica {#touch-enabled-vs-classic-ui}

Antes de qualquer discussão séria começar sobre o desenvolvimento de componentes, você precisa saber qual interface de usuário seus autores usarão:

* **Interface habilitada para toque**
   [A interface de usuário padrão](/help/sites-developing/touch-ui-concepts.md) que foi introduzido no AEM 5.6.0 como visualização e estendido no 6.x. É baseado na experiência unificada do usuário para a Adobe Marketing Cloud, usando as tecnologias subjacentes de [Interface do usuário do Coral](/help/sites-developing/touch-ui-concepts.md#coral-ui) e [Interface do usuário do Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui).

* **Interface clássica**
Interface do usuário baseada na tecnologia ExtJS que foi introduzida com o CQ 5.1.

Consulte [Interface da interface do usuário do Recommendations para clientes](/help/sites-deploying/ui-recommendations.md) para obter mais detalhes.

Os componentes podem ser implementados para suportar a interface habilitada para toque, a interface clássica ou ambos. Ao observar uma instância padrão, você também verá componentes prontos para uso que foram originalmente projetados para a interface clássica, para a interface habilitada para toque ou ambos.

Por isso, abordaremos as noções básicas de ambas as páginas e como reconhecê-las, nesta página.

>[!NOTE]
>
>O Adobe recomenda o aproveitamento da interface habilitada para toque para se beneficiar da tecnologia mais recente. [Ferramentas de Modernização AEM](modernization-tools.md) pode facilitar a migração.

### Lógica de conteúdo e marcação de renderização  {#content-logic-and-rendering-markup}

É recomendável manter o código responsável pela marcação e renderização separadas do código que controla a lógica usada para selecionar o conteúdo do componente.

Essa filosofia é apoiada por [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html), uma linguagem de modelo que é propositalmente limitada para garantir uma linguagem de programação real é usada para definir a lógica comercial subjacente. Essa lógica (opcional) é invocada do HTL com um comando específico. Esse mecanismo destaca o código chamado para uma determinada visualização e, se necessário, permite uma lógica específica para diferentes visualizações do mesmo componente.

### HTL vs JSP {#htl-vs-jsp}

HTL é uma linguagem de modelo do HTML introduzida com o AEM 6.0.

A discussão sobre se usar [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) ou JSP (Java Server Pages) ao desenvolver seus próprios componentes deve ser simples, pois o HTL agora é a linguagem de script recomendada para o AEM.

O HTL e o JSP podem ser usados para desenvolver componentes para a interface clássica e a interface habilitada para toque. Embora possa haver uma tendência de supor que HTL seja somente para a interface habilitada para toque e JSP para a interface clássica, isso é um equívoco e mais devido ao tempo. A interface do usuário habilitada para toque e o HTL foram incorporados ao AEM aproximadamente no mesmo período. Como o HTL agora é o idioma recomendado, ele está sendo usado para novos componentes, que tendem a ser para a interface habilitada para toque.

>[!NOTE]
>
>As exceções são Campos de formulário da interface do usuário do Granite (conforme usado em caixas de diálogo). Elas ainda exigem o uso do JSP.

### Desenvolvimento de seus próprios componentes {#developing-your-own-components}

Para criar seus próprios componentes para a interface do usuário apropriada, consulte (após ler esta página):

* [Componentes de AEM para a interface de usuário habilitada para toque](/help/sites-developing/developing-components.md)
* [Componentes do AEM para a interface clássica](/help/sites-developing/developing-components-classic.md)

Uma maneira rápida de começar é copiar um componente existente e fazer as alterações desejadas. Para saber como criar seus próprios componentes e adicioná-los ao sistema de parágrafos, consulte:

* [Componentes de desenvolvimento](/help/sites-developing/developing-components-samples.md) (focado na interface habilitada para toque)

### Mover componentes para a instância de publicação {#moving-components-to-the-publish-instance}

Os componentes que renderizam o conteúdo devem ser implantados na mesma instância AEM do conteúdo. Portanto, todos os componentes usados para criar e renderizar páginas na instância do autor devem ser implantados na instância de publicação. Quando implantados, os componentes ficam disponíveis para renderizar páginas ativadas.

Use as seguintes ferramentas para mover seus componentes para a instância de publicação:

* [Usar o Gerenciador de Pacotes](/help/sites-administering/package-manager.md) para adicionar seus componentes a um pacote e movê-los para outra instância do AEM.
* [Use a ferramenta Ativar replicação da árvore](/help/sites-authoring/publishing-pages.md#manage-publication) para replicar os componentes.

>[!NOTE]
>
>Esses mecanismos também podem ser usados para transferir o componente entre outras instâncias, por exemplo, do desenvolvimento para a instância de teste.

### Componentes a serem conhecidos desde o início {#components-to-be-aware-of-from-the-start}

* Página:

   * AEM tem a variável *página* componente ( `cq:Page`).
   * Esse é um tipo específico de recurso, importante para o gerenciamento de conteúdo.
      * Uma página corresponde a uma página da Web que contém conteúdo para seu site.

* Sistemas de parágrafo:

   * O sistema de parágrafo é uma parte essencial de um site, pois gerencia uma lista de parágrafos. É usado para manter e estruturar os componentes individuais que contêm o conteúdo real.
   * Você pode criar, mover, copiar e excluir parágrafos no sistema de parágrafos.
   * Você também pode selecionar os componentes que estarão disponíveis para uso em um sistema de parágrafos específico.
   * Há vários sistemas de parágrafo disponíveis em uma instância padrão (por exemplo, `parsys`, ` [responsivegrid](/help/sites-authoring/responsive-layout.md)`).

## Estrutura {#structure}

A estrutura de um componente de AEM é poderosa e flexível, as principais considerações são:

* Tipo de recurso
* Definição do componente
* Propriedades e nós secundários de um componente
* Caixas de diálogo
* Caixas de diálogo de design
* Disponibilidade de componentes
* Componentes e o conteúdo que eles criam

### Tipo de recurso {#resource-type}

Um elemento-chave da estrutura é o tipo de recurso.

* A estrutura de conteúdo declara intenções.
* O tipo de recurso implementa-os.

Essa é uma abstração que ajuda a garantir que, mesmo quando a aparência muda com o tempo, a intenção permanece o tempo.

### Definição do componente {#component-definition}

#### Noções básicas sobre componentes {#component-basics}

A definição de um componente pode ser dividida da seguinte maneira:

* AEM componentes se baseiam em [Sling](https://sling.apache.org/documentation.html).
* AEM componentes estão (normalmente) localizados em:

   * HTL: `/libs/wcm/foundation/components`
   * JSP: `/libs/foundation/components`

* Os componentes específicos do projeto/site estão (normalmente) localizados em:

   * `/apps/<myApp>/components`

* AEM componentes padrão são definidos como `cq:Component` e ter os elementos principais:

   * propriedades do jcr:

      Uma lista de propriedades do jcr; são variáveis e algumas podem ser opcionais por meio da estrutura básica de um nó de componente, suas propriedades e subnós são definidos pela variável `cq:Component` definição

   * Recursos:

      Eles definem elementos estáticos usados pelo componente.

   * Scripts:

   São usados para implementar o comportamento da instância resultante do componente.

* **Nó raiz**:

   * `<mycomponent> (cq:Component)` - Nó de hierarquia do componente.

* **Propriedades vitais**:

   * `jcr:title` - Título do componente; por exemplo, usado como um rótulo quando o componente está listado no navegador de componentes ou no sidekick.
   * `jcr:description` - Descrição do componente; pode ser usado como dica de mouse sobre o navegador de componentes ou sidekick.
   * IU Clássica:

      * `icon.png` - Ícone para este componente.
      * `thumbnail.png` - Imagem exibida se esse componente estiver listado no sistema de parágrafo.
   * Interface de toque

      * Consulte a seção [Ícone de componente na interface do usuário de toque](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) para obter detalhes.


* **Nós Secundários Vitais**:

   * `cq:editConfig (cq:EditConfig)` - Define as propriedades de edição do componente e permite que o componente apareça no navegador Componentes ou no Sidekick.

      Observação: se o componente tiver uma caixa de diálogo, ela aparecerá automaticamente no navegador Componentes ou no Sidekick, mesmo se cq:editConfig não existir.

   * `cq:childEditConfig (cq:EditConfig)` - Controla os aspectos da interface do usuário do autor para componentes filhos que não definem seus próprios `cq:editConfig`.
   * Interface habilitada para toque:

      * `cq:dialog` ( `nt:unstructured`) - Caixa de diálogo desse componente. Define a interface que permite ao usuário configurar o componente e/ou editar conteúdo.
      * `cq:design_dialog` ( `nt:unstructured`) - Edição de design para este componente
   * IU Clássica:

      * `dialog` ( `cq:Dialog`) - Caixa de diálogo desse componente. Define a interface que permite ao usuário configurar o componente e/ou editar conteúdo.
      * `design_dialog` ( `cq:Dialog`) - Edição de design para este componente.


#### Ícone de componente na interface do usuário de toque {#component-icon-in-touch-ui}

O ícone ou a abreviação do componente é definido por meio das propriedades do JCR do componente quando ele é criado pelo desenvolvedor. Essas propriedades são avaliadas na ordem a seguir e a primeira propriedade válida encontrada é usada.

1. `cq:icon` - Propriedade da string que aponta para um ícone padrão na [Biblioteca da interface do usuário do Coral](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) para exibir no navegador de componentes

   * Use o valor do atributo HTML do ícone Coral.

1. `abbreviation` - Propriedade String para personalizar a abreviação do nome do componente no navegador do componente

   * A abreviação deve ser limitada a dois caracteres.
   * Fornecer uma string vazia criará a abreviação dos dois primeiros caracteres do `jcr:title` propriedade.

      * Por exemplo, &quot;Im&quot; para &quot;Image&quot;
      * O título localizado será usado para criar a abreviação.
   * A abreviação só é traduzida se o componente tiver uma `abbreviation_commentI18n` , que é usada como dica de tradução.


1. `cq:icon.png` ou `cq:icon.svg` - Ícone para esse componente, que é mostrado no navegador de componentes

   * 20 x 20 pixels é o tamanho dos ícones dos componentes padrão.

      * Os ícones maiores serão baixados (no lado do cliente).
   * A cor recomendada é rgb(112, 112, 112) > #707070
   * O plano de fundo dos ícones de componentes padrão é transparente.
   * Somente `.png` e `.svg` os arquivos são suportados.
   * Ao importar do sistema de arquivos por meio do plug-in Eclipse, os nomes de arquivo precisam ser evitados como `_cq_icon.png` ou `_cq_icon.svg` por exemplo.
   * `.png` tem precedência sobre `.svg` se ambos estiverem presentes


Se nenhuma das propriedades acima ( `cq:icon`, `abbreviation`, `cq:icon.png` ou `cq:icon.svg`) são encontradas no componente :

* O sistema pesquisará as mesmas propriedades nos supercomponentes seguindo o `sling:resourceSuperType` propriedade.
* Se nada ou uma abreviação vazia for encontrada no nível do supercomponente, o sistema criará a abreviação das primeiras letras do `jcr:title` propriedade do componente atual.

Para cancelar a herança de ícones de supercomponentes, defina um valor vazio `abbreviation` no componente será revertido para o comportamento padrão.

O [Console do componente](/help/sites-authoring/default-components-console.md#component-details) exibe como o ícone de um componente específico é definido.

#### Exemplo de ícone SVG {#svg-icon-example}

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" id="Layer_1" xmlns="https://www.w3.org/2000/svg" xmlns:xlink="https://www.w3.org/1999/xlink" x="0px" y="0px"
     width="20px" height="20px" viewBox="0 0 20 20" enable-background="new 0 0 20 20" xml:space="preserve">
    <ellipse cx="5" cy="5" rx="3" ry="3" fill="#707070"/>
    <ellipse cx="15" cy="5" rx="4" ry="4" fill="#707070"/>
    <ellipse cx="5" cy="15" rx="5" ry="5" fill="#707070"/>
    <ellipse cx="15" cy="15" rx="4" ry="4" fill="#707070"/>
</svg>
```

### Propriedades e nós secundários de um componente {#properties-and-child-nodes-of-a-component}

Muitos dos nós/propriedades necessários para definir um componente são comuns a ambas as interfaces do usuário, com diferenças que permanecem independentes para que seu componente possa funcionar em ambos os ambientes.

Um componente é um nó do tipo `cq:Component` e tem as seguintes propriedades e nós secundários:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome <br /> </strong></td> 
   <td><strong>Tipo <br /> </strong></td> 
   <td><strong>Descrição <br /> </strong></td> 
  </tr> 
  <tr> 
   <td>.<br /> </td> 
   <td><code>cq:Component</code></td> 
   <td>Componente atual. Um componente é do tipo de nó <code>cq:Component</code>.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>componentGroup</code></td> 
   <td><code>String</code></td> 
   <td>Grupo no qual o componente pode ser selecionado no navegador Componentes (interface habilitada para toque) ou no Sidekick (interface clássica).<br /> Um valor de <code>.hidden</code> é usada para componentes que não estão disponíveis para seleção na interface do usuário, como os sistemas de parágrafo reais.</td> 
  </tr> 
  <tr> 
   <td><code>cq:isContainer</code></td> 
   <td><code>Boolean</code></td> 
   <td>Indica se o componente é um componente de contêiner e, portanto, pode conter outros componentes, como um sistema de parágrafo.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>cq:dialog</code></td> 
   <td><code>nt:unstructured</code> </td> 
   <td>Definição da caixa de diálogo de edição para a interface habilitada para toque.</td> 
  </tr> 
  <tr> 
   <td><code>dialog</code></td> 
   <td><code>cq:Dialog</code></td> 
   <td>Definição da caixa de diálogo de edição para a interface clássica.</td> 
  </tr> 
  <tr> 
   <td><code>cq:design_dialog</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Definição da caixa de diálogo de design para a interface habilitada para toque.</td> 
  </tr> 
  <tr> 
   <td><code>design_dialog</code></td> 
   <td><code>cq:Dialog </code></td> 
   <td>Definição da caixa de diálogo de design para a interface clássica.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>dialogPath</code></td> 
   <td><code>String</code></td> 
   <td>Caminho para uma caixa de diálogo para abranger o caso em que o componente não tem um nó de diálogo.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>cq:cellName</code></td> 
   <td><code>String</code></td> 
   <td>Se definida, essa propriedade será considerada como ID da célula. Para obter mais informações, consulte o artigo da Base de conhecimento <a href="https://helpx.adobe.com/experience-manager/kb/DesigneCellId.html">Como as IDs de células de design são criadas</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>cq:childEditConfig</code></td> 
   <td><code>cq:EditConfig</code></td> 
   <td>Quando o componente é um contêiner, como por exemplo um sistema de parágrafo, isso direciona a configuração de edição dos nós filhos.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>cq:editConfig</code></td> 
   <td><code>cq:EditConfig</code></td> 
   <td><a href="#edit-behavior">Editar configuração do componente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>cq:htmlTag</code></td> 
   <td><code>nt:unstructured </code></td> 
   <td>Retorna atributos de tag adicionais que são adicionados à tag html circundante. Permite a adição de atributos aos divs gerados automaticamente.</td> 
  </tr> 
  <tr> 
   <td><code>cq:noDecoration</code></td> 
   <td><code>Boolean</code></td> 
   <td>Se verdadeiro, o componente não é renderizado com classes div e css geradas automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>cq:template</code></td> 
   <td><code>nt:unstructured</code></td> 
   <td>Se encontrado, esse nó será usado como um modelo de conteúdo quando o componente for adicionado do Navegador de componentes ou do Sidekick.</td> 
  </tr> 
  <tr> 
   <td><code>cq:templatePath</code></td> 
   <td><code>String</code></td> 
   <td>Caminho para um nó a ser usado como um modelo de conteúdo quando o componente for adicionado do navegador Componentes ou do Sidekick. Deve ser um caminho absoluto, não relativo ao nó do componente.<br /> A menos que você queira reutilizar o conteúdo já disponível em outro lugar, isso não é obrigatório e <code>cq:template</code> é suficiente (ver abaixo).</td> 
  </tr> 
  <tr> 
   <td><code>jcr:created</code></td> 
   <td><code>Date</code></td> 
   <td>Data de criação do componente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>jcr:description</code></td> 
   <td><code>String</code></td> 
   <td>Descrição do componente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>jcr:title</code></td> 
   <td><code>String</code></td> 
   <td>Título do componente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>sling:resourceSuperType</code></td> 
   <td><code>String</code></td> 
   <td>Quando definido, o componente herda desse componente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>virtual</code></td> 
   <td><code>sling:Folder</code></td> 
   <td>Permite a criação de componentes virtuais. Para ver um exemplo, verifique o componente de contato em:<br /> <code>/libs/foundation/components/profile/form/contact</code></td> 
  </tr>
  <tr> 
   <td><code>&lt;breadcrumb.jsp&gt;</code></td> 
   <td><code>nt:file</code> </td> 
   <td>Arquivo de script.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>icon.png</code></td> 
   <td><code>nt:file</code></td> 
   <td>O ícone do componente aparece ao lado do Título no Sidekick.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>thumbnail.png</code></td> 
   <td><code>nt:file</code></td> 
   <td>Miniatura opcional mostrada enquanto o componente é arrastado do Sidekick para o lugar.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Se olharmos para a **Texto** componente (qualquer versão), podemos ver estes elementos:

* HTL ( `/libs/wcm/foundation/components/text`)

   ![chlimage_1-241](assets/chlimage_1-241.png)

* JSP ( `/libs/foundation/components/text`)

   ![screen_shot_2012-02-13at60457pm](assets/screen_shot_2012-02-13at60457pm.png)

As propriedades de interesses específicos incluem:

* `jcr:title` - o título do componente; isso pode ser usado para identificar o componente, por exemplo, ele aparece na lista de componentes no navegador de componentes ou no sidekick
* `jcr:description` - descrição do componente; pode ser usado como dica de mouse sobre a lista de componentes dentro do sidekick

* `sling:resourceSuperType`: isso indica o caminho da herança ao estender um componente (substituindo uma definição)

Os nós filhos de interesse especial incluem:

* `cq:editConfig` ( `cq:EditConfig`) - controlo dos aspectos visuais; por exemplo, ele pode definir a aparência de uma barra ou de um widget ou pode adicionar controles personalizados

* `cq:childEditConfig` ( `cq:EditConfig`) - controla os aspectos visuais dos componentes filhos que não têm as suas próprias definições

* Interface habilitada para toque:

   * `cq:dialog` ( `nt:unstructured`) - define a caixa de diálogo para editar o conteúdo desse componente
   * `cq:design_dialog` ( `nt:unstructured`) - especifica as opções de edição de design para este componente

* IU Clássica:

   * `dialog` ( `cq:Dialog`) - define a caixa de diálogo para editar o conteúdo desse componente (específico da interface clássica)
   * `design_dialog` ( `cq:Dialog`) - especifica as opções de edição de design para este componente
   * `icon.png` - arquivo gráfico a ser usado como ícone para o componente no Sidekick
   * `thumbnail.png` - arquivo gráfico a ser usado como miniatura do componente ao arrastá-lo do Sidekick

### Caixas de diálogo {#dialogs}

As caixas de diálogo são um elemento essencial do seu componente, pois fornecem uma interface para os autores configurar e fornecer entrada para esse componente.

Dependendo da complexidade do componente, a caixa de diálogo pode precisar de uma ou mais guias, para manter a caixa de diálogo curta e classificar os campos de entrada.

As definições de caixa de diálogo são específicas da interface do usuário:

>[!NOTE]
>
>* Para fins de compatibilidade, a interface do usuário habilitada para toque pode usar a definição de uma caixa de diálogo da interface do usuário clássica, quando nenhuma caixa de diálogo tiver sido definida para a interface do usuário habilitada para toque.
>* O [Ferramentas de Modernização AEM](/help/sites-developing/modernization-tools.md) O também é fornecido para ajudá-lo a estender/converter componentes que tenham apenas caixas de diálogo definidas para a interface clássica.
>


* Interface habilitada para toque

   * `cq:dialog` ( `nt:unstructured`) nós:

      * definir a caixa de diálogo para editar o conteúdo deste componente
      * específico da interface habilitada para toque
      * são definidas usando componentes da interface do usuário do Granite
      * ter uma propriedade `sling:resourceType`, como estrutura de conteúdo padrão do Sling
      * pode ter uma propriedade `helpPath` para definir o recurso de ajuda sensível ao contexto (caminho absoluto ou relativo) que é acessado quando o ícone de Ajuda (o ? ) está selecionada.

         * Para componentes prontos para uso, isso geralmente faz referência a uma página na documentação.
         * Se não `helpPath` for especificada, o URL padrão (página de visão geral da documentação) será exibido.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   Na caixa de diálogo , campos individuais são definidos:

   ![screen_shot_2012-02-13at60937pm](assets/screen_shot_2012-02-13at60937pm.png)

* IU Clássica

   * `dialog` ( `cq:Dialog`) nós

      * definir a caixa de diálogo para editar o conteúdo deste componente
      * específico da interface clássica
      * são definidas usando widgets ExtJS
      * ter uma propriedade `xtype`, que se refere a ExtJS
      * pode ter uma propriedade `helpPath` para definir o recurso de ajuda sensível ao contexto (caminho absoluto ou relativo) que é acessado quando a variável **Ajuda** é selecionado.

         * Para componentes prontos para uso, isso geralmente faz referência a uma página na documentação.
         * Se não `helpPath` for especificada, o URL padrão (página de visão geral da documentação) será exibido.

   ![chlimage_1-243](assets/chlimage_1-243.png)

   Na caixa de diálogo , campos individuais são definidos:

   ![chlimage_1-244](assets/chlimage_1-244.png)

   Em uma caixa de diálogo clássica:

   * você pode criar a caixa de diálogo como `cq:Dialog`, que fornecerá uma única guia - como no componente de texto, ou se você precisar de várias guias, como no componente de tempo de texto, a caixa de diálogo poderá ser definida como `cq:TabPanel`.
   * a `cq:WidgetCollection` ( `items`) é usada para fornecer uma base para qualquer campo de entrada ( `cq:Widget`) ou outras guias ( `cq:Widget`). Essa hierarquia pode ser estendida.


### Caixas de diálogo de design {#design-dialogs}

As caixas de diálogo Design são muito semelhantes às caixas de diálogo usadas para editar e configurar o conteúdo, mas fornecem a interface para os autores configurar e fornecer detalhes de design para esse componente.

[As caixas de diálogo Design estão disponíveis no Modo Design](/help/sites-authoring/default-components-designmode.md), embora não sejam necessários para todos os componentes, por exemplo **Título** e **Imagem** ambos têm diálogos de design, enquanto **Texto** não.

A caixa de diálogo de design do sistema de parágrafo (por exemplo, parsys) é um caso especial, pois permite que o usuário defina outros componentes específicos para serem selecionados (do navegador de componentes ou do sidekick) na página.

### Adicionar seu componente ao sistema de parágrafos {#adding-your-component-to-the-paragraph-system}

Depois que um componente é definido, ele deve ser disponibilizado para uso. Para disponibilizar um componente para uso em um sistema de parágrafo, é possível:

1. Abrir [Modo Design](/help/sites-authoring/default-components-designmode.md) para uma página e habilite o componente desejado.
1. Adicione os componentes necessários ao `components` propriedade da definição do modelo em:

   `/etc/designs/<*yourProject*>/jcr:content/<*yourTemplate*>/par`

   Por exemplo, consulte:

   `/etc/designs/geometrixx/jcr:content/contentpage/par`

   ![chlimage_1-245](assets/chlimage_1-245.png)

### Componentes e o conteúdo que eles criam {#components-and-the-content-they-create}

Se criarmos e configurarmos uma instância do **Título** componente na página: `<content-path>/Prototype.html`

* Interface habilitada para toque

   ![chlimage_1-246](assets/chlimage_1-246.png)

* IU Clássica

   ![screen_shot_2012-02-01at34257pm](assets/screen_shot_2012-02-01at34257pm.png)

Então podemos ver a estrutura do conteúdo criado no repositório:

![screen_shot_2012-02-13at61405pm](assets/screen_shot_2012-02-13at61405pm.png)

Em particular, se você observar o texto real para uma **Título**:

* a definição (para ambas as interfaces de usuário) tem a propriedade `name`= `./jcr:title`

   * `/libs/foundation/components/title/cq:dialog/content/items/column/items/title`
   * `/libs/foundation/components/title/dialog/items/title`

* no conteúdo, isso gera a propriedade `jcr:title` mantendo o conteúdo do autor.

As propriedades definidas dependem das definições individuais. Embora possam ser mais complexas do que acima, seguem ainda os mesmos princípios básicos.

## Hierarquia e herança de componentes {#component-hierarchy-and-inheritance}

Os componentes no AEM estão sujeitos a 3 hierarquias diferentes:

* **Hierarquia do Tipo de Recurso**

   Isso é usado para estender componentes usando a propriedade `sling:resourceSuperType`. Isso permite que o componente herde. Por exemplo, um componente de texto herdará vários atributos do componente padrão.

   * scripts (resolvido pelo Sling)
   * caixas de diálogo
   * descrições (incluindo imagens em miniatura, ícones, etc.)

* **Hierarquia do contêiner**

   Isso é usado para preencher as configurações para o componente filho e é mais usado em um cenário parsys.

   Por exemplo, as configurações dos botões da barra de edição, o layout do conjunto de controle (barras de edição, rolagem), o layout da caixa de diálogo (em linha, flutuante) podem ser definidos no componente pai e propagados para os componentes filho.

   Configurações (relacionadas à funcionalidade de edição) em `cq:editConfig` e `cq:childEditConfig` são propagadas.

* **Incluir hierarquia**

   Isso é imposto no tempo de execução pela sequência de inclusões.

   Essa hierarquia é usada pelo Designer, que, por sua vez, atua como base para vários aspectos de design da renderização; incluindo informações de layout, informações de css, os componentes disponíveis em um parsys, entre outros.

## Editar comportamento {#edit-behavior}

Esta seção explica como configurar o comportamento de edição de um componente. Isso inclui atributos como ações disponíveis para o componente, características do editor local e ouvintes relacionados a eventos no componente.

A configuração é comum à interface habilitada para toque e clássica, embora com determinadas diferenças específicas.

O comportamento de edição de um componente é configurado ao adicionar um `cq:editConfig` nó do tipo `cq:EditConfig` abaixo do nó do componente (do tipo `cq:Component`) e adicionando propriedades específicas e nós secundários. As seguintes propriedades e nós secundários estão disponíveis:

* [ `cq:editConfig` propriedades do nó](#configuring-with-cq-editconfig-properties):

   * `cq:actions` ( `String array`): define as ações que podem ser executadas no componente.
   * `cq:layout` ( `String`): : define como o componente é editado na interface clássica.
   * `cq:dialogMode` ( `String`): define como a caixa de diálogo do componente é aberta na interface clássica

      * Na interface habilitada para toque, as caixas de diálogo estão sempre flutuando no modo de desktop e abertas automaticamente como tela cheia em dispositivos móveis.
   * `cq:emptyText` ( `String`): define o texto que é exibido quando nenhum conteúdo visual está presente.
   * `cq:inherit` ( `Boolean`): define se os valores ausentes são herdados do componente do qual ele herda.
   * `dialogLayout` (String): define como a caixa de diálogo deve ser aberta.


* [ `cq:editConfig` nós filhos](#configuring-with-cq-editconfig-child-nodes):

   * `cq:dropTargets` (tipo de nó) `nt:unstructured`): define uma lista de destinos de soltar que podem aceitar uma queda de um ativo do localizador de conteúdo

      * Vários destinos de soltar estão disponíveis somente na interface clássica.
      * Na interface habilitada para toque, é permitido um único destino de soltar.
   * `cq:actionConfigs` (tipo de nó) `nt:unstructured`): define uma lista de novas ações que são anexadas à lista cq:actions.
   * `cq:formParameters` (tipo de nó) `nt:unstructured`): O define parâmetros adicionais que são adicionados ao formulário de diálogo.
   * `cq:inplaceEditing` (tipo de nó) `cq:InplaceEditingConfig`): define uma configuração de edição local para o componente.
   * `cq:listeners` (tipo de nó) `cq:EditListenersConfig`): define o que acontece antes ou depois que uma ação ocorre no componente.


>[!NOTE]
>
>Nesta página, um nó (propriedades e nós filhos) é representado como XML, como mostrado no exemplo a seguir.

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:dialogMode="floating"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afteredit="REFRESH_PAGE"/>
</jcr:root>
```

Há muitas configurações existentes no repositório. Você pode pesquisar facilmente propriedades específicas ou nós secundários:

* Para procurar uma propriedade do `cq:editConfig` nó, por exemplo `cq:actions`, você pode usar a ferramenta Query no **CRXDE Lite** e pesquise com a seguinte sequência de consulta XPath:

   `//element(cq:editConfig, cq:EditConfig)[@cq:actions]`

* Para procurar um nó filho de `cq:editConfig`, por exemplo, você pode pesquisar por `cq:dropTargets`, que é do tipo `cq:DropTargetConfig`; você pode usar a ferramenta Consulta em ** CRXDE Lite* e pesquisar com a seguinte string de consulta XPath:

   `//element(cq:dropTargets, cq:DropTargetConfig)`

### Marcadores de posição de componente {#component-placeholders}

Os componentes devem sempre renderizar algum HTML visível para o autor, mesmo quando o componente não tiver conteúdo. Caso contrário, pode desaparecer visualmente da interface do editor, tornando-a tecnicamente presente, mas invisível, na página e no editor. Nesse caso, os autores não poderão selecionar e interagir com o componente vazio.

Por isso, os componentes devem renderizar um espaço reservado, desde que não renderizem nenhuma saída visível quando a página for renderizada no editor de páginas (quando o modo WCM estiver `edit` ou `preview`).
A marcação de HTML típica para um espaço reservado é a seguinte:

```HTML
<div class="cq-placeholder" data-emptytext="Component Name"></div>
```

O script HTL típico que renderiza o HTML de espaço reservado acima é o seguinte:

```HTML
<div class="cq-placeholder" data-emptytext="${component.properties.jcr:title}"
     data-sly-test="${(wcmmode.edit || wcmmode.preview) && isEmpty}"></div>
```

No exemplo anterior, `isEmpty` é uma variável que é verdadeira somente quando o componente não tem conteúdo e é invisível para o autor.

Para evitar a repetição, o Adobe recomenda que os implementadores de componentes usem um template HTL para esses espaços reservados, [como o fornecido pelos Componentes principais.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/commons/v1/templates.html)

O uso do template no link anterior é feito com a seguinte linha de HTL:

```HTML
<sly data-sly-use.template="core/wcm/components/commons/v1/templates.html"
     data-sly-call="${template.placeholder @ isEmpty=!model.text}"></sly>
```

No exemplo anterior, `model.text` é a variável que é verdadeira somente quando o conteúdo tem conteúdo e é visível.

Um exemplo de uso desse modelo pode ser visto nos Componentes principais, [como no Componente de título.](https://github.com/adobe/aem-core-wcm-components/blob/master/content/src/content/jcr_root/apps/core/wcm/components/title/v2/title/title.html#L27)

### Configurar com cq:EditConfig Properties {#configuring-with-cq-editconfig-properties}

### cq:actions {#cq-actions}

O `cq:actions` propriedade ( `String array`) define uma ou várias ações que podem ser executadas no componente. Os seguintes valores estão disponíveis para configuração:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Valor da propriedade</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><code>text:&lt;some text&gt;</code></td> 
   <td>Exibe o valor do texto estático &lt;some text=""&gt;<br /> Visível somente na interface clássica. A interface habilitada para toque não exibe ações em um menu contextual, portanto, isso não é aplicável.</td> 
  </tr> 
  <tr> 
   <td>-</td> 
   <td>Adiciona um espaçador.<br /> Visível somente na interface clássica. A interface habilitada para toque não exibe ações em um menu contextual, portanto, isso não é aplicável.</td> 
  </tr> 
  <tr> 
   <td><code>edit</code></td> 
   <td>Adiciona um botão para editar o componente.</td> 
  </tr> 
    <tr>
    <td><code>editannotate</code></td>
    <td>Adiciona um botão para editar o componente, bem como permitir <a href="/help/sites-authoring/annotations.md">anotações</a>.</td>
   </tr>
  <tr> 
   <td><code>delete</code></td> 
   <td>Adiciona um botão para excluir o componente</td> 
  </tr> 
  <tr> 
   <td><code>insert</code></td> 
   <td>Adiciona um botão para inserir um novo componente antes do atual</td> 
  </tr> 
  <tr> 
   <td><code>copymove</code></td> 
   <td>Adiciona um botão para copiar e recortar o componente.</td> 
  </tr> 
 </tbody> 
</table>

A configuração a seguir adiciona um botão de edição, um espaçador, um botão de exclusão e um botão de inserção à barra de edição do componente:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit,-,delete,insert]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig"/>
```

A configuração a seguir adiciona o texto &quot;Configurações herdadas da estrutura base&quot; à barra de edição do componente:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[text:Inherited Configurations from Base Framework]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig"/>
```

### cq:layout (somente interface clássica) {#cq-layout-classic-ui-only}

O `cq:layout` propriedade ( `String`) define como o componente pode ser editado na interface clássica. Os seguintes valores estão disponíveis:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Valor da propriedade</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><code>rollover</code></td> 
   <td>Valor padrão. A edição do componente pode ser acessada "ao passar o mouse" por meio de cliques e/ou do menu de contexto.<br /> Para uso avançado, observe que o objeto correspondente do lado do cliente é: <code>CQ.wcm.EditRollover</code>.</td> 
  </tr> 
  <tr> 
   <td><code>editbar</code></td> 
   <td>A edição do componente é acessível por meio de uma barra de ferramentas.<br /> Para uso avançado, observe que o objeto correspondente do lado do cliente é: <code>CQ.wcm.EditBar</code>.</td> 
  </tr> 
  <tr> 
   <td><code>auto</code></td> 
   <td>A escolha é deixada ao código do lado do cliente.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Os conceitos de sobreposição e barra de edição não são aplicáveis na interface habilitada para toque.

A configuração a seguir adiciona um botão de edição à barra de edição de componentes:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
</jcr:root>
```

### cq:dialogMode (somente interface clássica) {#cq-dialogmode-classic-ui-only}

O componente pode ser vinculado a uma caixa de diálogo de edição. O `cq:dialogMode` propriedade ( `String`) define como a caixa de diálogo do componente será aberta na interface clássica. Os seguintes valores estão disponíveis:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Valor da propriedade</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><code>floating</code></td> 
   <td>A caixa de diálogo está flutuando.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>inline</code></td> 
   <td>(Valor padrão). A caixa de diálogo é ancorada sobre o componente.<br /> </td> 
  </tr> 
  <tr> 
   <td><code>auto</code></td> 
   <td>Se a largura do componente for menor que o lado do cliente <code>CQ.themes.wcm.EditBase.INLINE_MINIMUM_WIDTH</code> , a caixa de diálogo está flutuando, caso contrário, está em linha.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Na interface habilitada para toque, as caixas de diálogo estão sempre flutuando no modo de desktop e abertas automaticamente como tela cheia em dispositivos móveis.

A configuração a seguir define uma barra de edição com um botão de edição e uma caixa de diálogo flutuante:

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
    cq:actions="[edit]"
    cq:dialogMode="floating"
    cq:layout="editbar"
    jcr:primaryType="cq:EditConfig">
</jcr:root>
```

### cq:emptyText {#cq-emptytext}

O `cq:emptyText` propriedade ( `String`) define o texto que é exibido quando nenhum conteúdo visual está presente. O padrão é: `Drag components or assets here`.

### cq:herit {#cq-inherit}

O `cq:inherit` propriedade ( `boolean`) define se os valores ausentes são herdados do componente do qual ele herda. O padrão é `false`.

### dialogLayout {#dialoglayout}

O `dialogLayout` define como uma caixa de diálogo deve ser aberta por padrão.

* Um valor de `fullscreen` abre a caixa de diálogo em tela cheia.
* Um valor vazio ou a ausência da propriedade assumem o padrão de abrir a caixa de diálogo normalmente.
* Observe que o usuário sempre pode alternar o modo de tela cheia na caixa de diálogo.
* Não se aplica à interface clássica.

### Configurar com nós filho cq:EditConfig {#configuring-with-cq-editconfig-child-nodes}

### cq:dropTargets {#cq-droptargets}

O `cq:dropTargets` nó (tipo de nó) `nt:unstructured`) define uma lista de destinos de soltar que podem aceitar uma queda de um ativo arrastado do localizador de conteúdo. Ele serve como uma coleção de nós do tipo `cq:DropTargetConfig`.

>[!NOTE]
>
>Vários destinos de soltar estão disponíveis somente na interface clássica.
>
>Na interface habilitada para toque, somente o primeiro destino será usado.

Cada nó filho do tipo `cq:DropTargetConfig` define um destino de soltar no componente. O nome do nó é importante porque ele deve ser usado no JSP, da seguinte maneira, para gerar o nome da classe CSS atribuído ao elemento DOM que é o destino final efetivo:

```
<drop target css class> = <drag and drop prefix> + 
 <node name of the drop target in the edit configuration>
```

O `<*drag and drop prefix*>` é definido pela propriedade Java:

`com.day.cq.wcm.api.components.DropTarget.CSS_CLASS_PREFIX`.

Por exemplo, o nome da classe é definido da seguinte maneira no JSP do componente de Download\
( `/libs/foundation/components/download/download.jsp`), onde `file` é o nome do nó do destino de soltar na configuração de edição do componente de Download:

`String ddClassName = DropTarget.CSS_CLASS_PREFIX + "file";`

O nó do tipo `cq:DropTargetConfig` precisa ter as seguintes propriedades:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome da Propriedade</strong></td> 
   <td><strong>Valor da propriedade<br /> </strong></td> 
  </tr> 
  <tr> 
   <td><code>accept</code></td> 
   <td>Regex aplicado ao tipo MIME do ativo para validar se a queda é permitida.</td> 
  </tr> 
  <tr> 
   <td><code>groups</code></td> 
   <td>Matriz de grupos de destino de soltar. Cada grupo deve corresponder ao tipo de grupo definido na extensão do localizador de conteúdo e que está anexado aos ativos.</td> 
  </tr> 
  <tr> 
   <td><code>propertyName</code></td> 
   <td>Nome da propriedade que será atualizada após uma queda válida.</td> 
  </tr> 
 </tbody> 
</table>

A configuração a seguir é obtida do componente Download . Ela ativa qualquer ativo (o tipo MIME pode ser qualquer string) da variável `media` grupo a ser descartado do localizador de conteúdo no componente. Após a queda, a propriedade do componente `fileReference` está sendo atualizado:

```
    <cq:dropTargets jcr:primaryType="nt:unstructured">
        <file
            jcr:primaryType="cq:DropTargetConfig"
            accept="[.*]"
            groups="[media]"
            propertyName="./fileReference"/>
    </cq:dropTargets>
```

### cq:actionConfigs (somente interface clássica) {#cq-actionconfigs-classic-ui-only}

O `cq:actionConfigs` nó (tipo de nó) `nt:unstructured`) define uma lista de novas ações que são anexadas à lista definida pelo `cq:actions` propriedade. Cada nó filho de `cq:actionConfigs` define uma nova ação definindo um widget.

O exemplo de configuração a seguir define um novo botão (com um separador para a interface clássica):

* um separador, definido pelo xtype `tbseparator`;

   * Isso é usado somente pela interface clássica.
   * Essa definição é ignorada pela interface habilitada para toque, pois xtypes são ignorados (e separadores são desnecessários, pois a barra de ferramentas de ação é construída de forma diferente na interface habilitada para toque).

* um botão chamado **Gerenciar comentários** que executa a função do manipulador `CQ_collab_forum_openCollabAdmin()`.

```
<jcr:root xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    cq:actions="[EDIT,COPYMOVE,DELETE,INSERT]"
    jcr:primaryType="cq:EditConfig">
    <cq:actionConfigs jcr:primaryType="nt:unstructured">
        <separator0
            jcr:primaryType="nt:unstructured"
            xtype="tbseparator"/>
        <manage
            jcr:primaryType="nt:unstructured"
            handler="function(){CQ_collab_forum_openCollabAdmin();}"
            text="Manage comments"/>
    </cq:actionConfigs>
</jcr:root>
```

>[!NOTE]
>
>Consulte [Adicionar nova ação a uma barra de ferramentas de componentes](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) como exemplo para a interface habilitada para toque.

### cq:formParameters {#cq-formparameters}

O `cq:formParameters` nó (tipo de nó) `nt:unstructured`) define parâmetros adicionais que são adicionados ao formulário de diálogo. Cada propriedade é mapeada para um parâmetro de formulário.

A configuração a seguir adiciona um parâmetro chamado `name`, defina com o valor `photos/primary` ao formulário de diálogo:

```
    <cq:formParameters
        jcr:primaryType="nt:unstructured"
        name="photos/primary"/>
```

### cq:inplaceEditing {#cq-inplaceediting}

O `cq:inplaceEditing` nó (tipo de nó) `cq:InplaceEditingConfig`) define uma configuração de edição local para o componente. Pode ter as seguintes propriedades:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome da Propriedade</strong></td> 
   <td><strong>Valor da propriedade<br /> </strong></td> 
  </tr> 
  <tr> 
   <td><code>active</code></td> 
   <td>(<code>boolean</code>) Verdadeiro para ativar a edição local do componente.</td> 
  </tr> 
  <tr> 
   <td><code>configPath</code></td> 
   <td>(<code>String</code>) Caminho da configuração do editor. A configuração pode ser especificada por um nó de configuração.</td> 
  </tr> 
  <tr> 
   <td><code>editorType</code></td> 
   <td><p>(<code>String</code>) Tipo de editor. Os tipos disponíveis são:</p> 
    <ul> 
     <li>texto simples: a ser usado para conteúdo não HTML.<br /> </li> 
     <li>Título: é um editor de texto simples aprimorado que converte títulos gráficos em um texto simples antes do início da edição. Usado pelo componente de título do Geometrixx.<br /> </li> 
     <li>texto: a ser usado para o conteúdo do HTML (usa o Editor de Rich Text).<br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

A configuração a seguir permite a edição local do componente e define `plaintext` como tipo de editor:

```
    <cq:inplaceEditing
        jcr:primaryType="cq:InplaceEditingConfig"
        active="{Boolean}true"
        editorType="plaintext"/>
```

### cq:listeners {#cq-listeners}

O `cq:listeners` nó (tipo de nó) `cq:EditListenersConfig`) define o que acontece antes ou depois de uma ação no componente. A tabela a seguir define suas possíveis propriedades.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome da Propriedade</strong></td> 
   <td><strong>Valor da propriedade<br /> </strong></td> 
   <td><p><strong>Valor padrão</strong></p> <p>(Somente interface clássica)</p> </td> 
  </tr> 
  <tr> 
   <td><code>beforedelete</code></td> 
   <td>O manipulador é acionado antes da remoção do componente.<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>beforeedit</code></td> 
   <td>O manipulador é acionado antes que o componente seja editado.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>beforecopy</code></td> 
   <td>O manipulador é acionado antes que o componente seja copiado.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>beforemove</code></td> 
   <td>O manipulador é acionado antes que o componente seja movido.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>beforeinsert</code></td> 
   <td>O manipulador é acionado antes da inserção do componente.<br /> Somente operacional para a interface habilitada para toque.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>beforechildinsert</code></td> 
   <td>O manipulador é acionado antes que o componente seja inserido em outro componente (somente contêineres).</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>afterdelete</code></td> 
   <td>O manipulador é acionado após a remoção do componente.</td> 
   <td><code>REFRESH_SELF</code></td> 
  </tr> 
  <tr> 
   <td><code>afteredit</code></td> 
   <td>O manipulador é acionado após a edição do componente.</td> 
   <td><code>REFRESH_SELF</code></td> 
  </tr> 
  <tr> 
   <td><code>aftercopy</code></td> 
   <td>O manipulador é acionado após o componente ser copiado.</td> 
   <td><code>REFRESH_SELF</code></td> 
  </tr> 
  <tr> 
   <td><code>afterinsert</code></td> 
   <td>O manipulador é acionado após a inserção do componente.</td> 
   <td><code>REFRESH_INSERTED</code></td> 
  </tr> 
  <tr> 
   <td><code>aftermove</code></td> 
   <td>O manipulador é acionado após o componente ser movido.</td> 
   <td><code>REFRESH_SELFMOVED</code></td> 
  </tr> 
  <tr> 
   <td><code>afterchildinsert</code></td> 
   <td>O manipulador é acionado após o componente ser inserido em outro componente (somente contêineres).</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>O `REFRESH_INSERTED` e `REFRESH_SELFMOVED` os manipuladores só estão disponíveis na interface clássica.

>[!NOTE]
>
>Os valores padrão para os ouvintes são definidos somente na interface clássica.

>[!NOTE]
>
>No caso de componentes aninhados, há certas restrições nas ações definidas como propriedades na variável `cq:listeners` nó:
>
>* Para componentes aninhados, os valores das seguintes propriedades *must* be `REFRESH_PAGE`:
>
>  * `aftermove`
>  * `aftercopy`


O manipulador de eventos pode ser implementado com uma implementação personalizada. Por exemplo (onde `project.customerAction` é um método estático):

`afteredit = "project.customerAction"`

O exemplo a seguir é equivalente ao `REFRESH_INSERTED` configuração:

`afterinsert="function(path, definition) { this.refreshCreated(path, definition); }"`

>[!NOTE]
>
>Para a interface clássica, para ver quais parâmetros podem ser usados nos manipuladores, consulte o `before<action>` e `after<action>` seção de eventos da [ `CQ.wcm.EditBar`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar) e [ `CQ.wcm.EditRollover`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover) documentação do widget.

Com a seguinte configuração, a página é atualizada após o componente ter sido excluído, editado, inserido ou movido:

```
    <cq:listeners
        jcr:primaryType="cq:EditListenersConfig"
        afterdelete="REFRESH_PAGE"
        afteredit="REFRESH_PAGE"
        afterinsert="REFRESH_PAGE"
        afterMove="REFRESH_PAGE"/>
```
