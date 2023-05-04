---
title: Modelos no Repositório
seo-title: Models in Repository
description: null
seo-description: null
uuid: 54f81180-4178-4e33-a6f0-e9e6ea50798e
contentOwner: User
content-type: reference
discoiquuid: ae1a72f4-d8c1-4c75-ba2c-7322f3743b17
noindex: true
redirecttarget: /content/help/en/experience-manager/6-4/mobile/using/administer-mobile-apps
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 1%

---


# Modelos no Repositório{#models-in-repository}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>A Adobe recomenda usar o Editor de SPA para projetos que exigem renderização do lado do cliente com base em estrutura de aplicativo de página única (por exemplo, React). [Saiba mais](/help/sites-developing/spa-overview.md).

Um modelo contém um conjunto de tipos de dados que definem as propriedades que serão renderizadas pelos serviços de conteúdo. Um modelo também define as relações entre outros modelos para impor a integridade dos dados.

Como desenvolvedor, você deve estar familiarizado com a estrutura Modelo no repositório. Você pode criar seus próprios modelos e entidades de acordo com as necessidades do seu aplicativo.

## Criação de tipos de modelo {#creating-model-types}

Há dois tipos de modelo fornecidos pelo sistema em */libs/settings/mobileapps/model-types*. Se quiser substituir o modelo do sistema, digite um *mobileapps/model-types* O nó precisará ser criado no nó de configuração no qual você deseja que a substituição ocorra.

Por exemplo, se você criou configurações em */conf/myconf1* e */conf/myconf2* e deseja substituir os tipos de modelo de sistema no *conf1* somente, você criaria um *mobileapps/model-types* nas configurações de *conf1*.

Se você quiser permitir que os tipos de dados sejam adicionados a um modelo, o tipo de modelo deverá ter um nó filho chamado &#39;scaffolding&#39; do tipo &#39;cq:Page&#39; e um tipo de recurso de *wcm/scaffolding/components/scaffolding*.

A página de scaffolding também deve incluir um *dataTypesConfig* no nó PageContent , que indica que os tipos de dados criados a partir desse tipo poderão ser usados.

>[!NOTE]
>
>A **Andaime** é uma página que define os tipos de dados que podem ser editados por uma entidade com base no modelo. Cada tipo de dados também pode ser configurado para definir como o campo será apresentado na interface do usuário, bem como como como o valor de dados será mantido.

### Configuração dos tipos de dados {#data-types-config}

O nó de configuração dos tipos de dados contém uma lista de itens do tipo de dados. Cada item de tipo de dados especifica como um tipo de dados será exibido no editor de modelo, bem como como deve ser mantido para eventual renderização por uma entidade.

| **Nome da Propriedade** | **Descrição** |
|---|---|
| fieldIcon | classe de ícone CoralUI para representar o tipo de dados |
| fieldPropResourceType | componente que renderizará todas as propriedades para configurar o tipo de dados |
| fieldProperties | lista de vários valores dos componentes de propriedade que são usados quando fieldPropResourceType é *mobileapps/caas/gui/components/models/editor/datatypes/field* |
| fieldResourceType | resourceType do nó persistente para o tipo de dados (ou seja, o componente que renderizará a propriedade no editor de entidades) |
| fieldViewResourceType | componente a ser usado para renderizar o tipo de dados na exibição do editor de modelo (fieldResourceType será usado se essa propriedade for omitida) |
| fieldTitle | nome do tipo de dados que será exibido no editor de modelo |
| multiFieldResourceType | tipo de recurso a ser usado no nó persistente quando vários valores forem selecionados |
| renderType | pista de renderização para renderização no cliente |

### Sobreposição de configuração dos tipos de dados {#data-types-config-overlay}

A propriedade &#39;dataTypesConfig&#39; suporta a mesclagem de recursos Sling. Isso significa que os tipos de dados usados pelos tipos de modelo do sistema (ou até mesmo os tipos de modelo personalizados) podem ser personalizados usando nós de sobreposição.

Uma sobreposição de */libs/settings/mobileapps/models/formbuilderconfig/datatypes* precisará ser criada e personalizada conforme desejado.

Por exemplo, uma sobreposição para o tipo de dados String pode ser adicionada para alterar fieldResourceType para um componente personalizado.

Para obter mais informações sobre a Mesclagem de recursos do Sling, consulte [Usando a Fusão de Recursos do Sling no AEM](/help/sites-developing/sling-resource-merger.md).

![chlimage_1-7](assets/chlimage_1-7.png)

### Tipos de dados {#data-types}

Um tipo de dados de modelo é um componente de formulário que pode incluir dados a serem incluídos ao publicar um formulário. O componente de tipo de dados pode ser tão complicado quanto desejado. Um exemplo de um tipo de dados personalizado pode ser um bloco de endereços para um determinado país, para evitar a necessidade de recriá-lo o tempo todo usando os tipos de dados primitivos.

Consulte &#39;/libs/mobileapps/caas/components/form/contentreference&#39; como um exemplo de um tipo de dados personalizado.

Todos os tipos de dados primitivos usam os componentes de formulário Granite existentes. Consulte: [https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html)

Qualquer tipo de dados personalizado pode ser adicionado a uma configuração de tipo de dados para uso pelo editor de modelo.

## Criação de modelos {#creating-models}

Você pode começar a criar modelos depois que todos os tipos de modelo e tipos de dados desejados tiverem sido desenvolvidos. Os autores acabarão usando modelos para criar entidades das quais os serviços de conteúdo usam para renderizar seus dados.

A criação de um modelo consiste em escolher um tipo de modelo permitido com base na configuração atual e, em seguida, fornecer um título e uma descrição.

Para saber mais sobre como criar e gerenciar um modelo no painel, consulte [Criação de um modelo](/help/mobile/administer-mobile-apps.md) em criação para aplicativos móveis.

### Propriedades de um Modelo {#properties-of-a-model}

A tabela a seguir mostra as propriedades definidas para um modelo:

| **Nome da Propriedade** | **Descrição** |
|---|---|
| Título do modelo | nome do modelo |
| Descrição | descrição do modelo |
| Miniatura  | imagem em miniatura do modelo |
| Tipo de modelo | tipo do modelo (pode ser uma string simples ou um caminho para um componente real) |
| Filhos permitidos | caminho de um modelo que pode ser filho deste modelo |
| Primários permitidos | caminho de um modelo que pode ser um pai deste modelo |

>[!NOTE]
>
>O *crianças permitidas* e *pais permitidos* As propriedades do seguem as mesmas regras dos Modelos de página. Para obter mais informações, consulte [Modelos de página](/help/sites-developing/page-templates-static.md).
>
>Em referência a *Tipo de modelo* , todos os modelos devem ter um supertipo de *mobileapps/caas/components/data/entity* mas pode ter um subtipo que permite que a entrega de conteúdo seja personalizada. Garantir que todos os tipos de modelo sejam exclusivos também pode ajudar os clientes dos serviços de conteúdo a distinguir entre objetos nos dados.

### Editar um modelo {#editing-a-model}

A edição de um modelo envolve a abertura do formulário de diálogo de scaffolding associado a um modelo para edição. Geralmente, o scaffolding é um nó filho do modelo, mas pode ser localizado fora dele, se desejado, especificando seu caminho usando a propriedade &#39;cq:scaffolding&#39;. Isso é útil se você quiser compartilhar o mesmo scaffolding entre vários modelos que precisam ter propriedades diferentes.

Quando o scaffolding do modelo estiver localizado, o editor de modelo renderizará o que for encontrado em &#39;jcr:content/cq:dialog/content&#39;. Atualmente, apenas um layout fixo de até 3 colunas é compatível com o mecanismo do construtor de formulários do lado do cliente. À direita da caixa de diálogo de formulário renderizado estará uma lista de todos os tipos de dados especificados na configuração de tipos de dados. Os tipos de dados podem ser editados ao clicar neles. O painel direito mudará para a guia properties do tipo de dados selecionado. Novos tipos de dados podem ser adicionados arrastando-os para a tela de visualização. Clicar em Salvar propaga as alterações no servidor. Clicar em Cancelar fecha o editor de modelo.

>[!NOTE]
>
>Todos os modelos são Modelos, então eles seguem todas as regras de Modelos AEM. Isso permite o uso de propriedades como *allowedParents* e *allowedChildren* propriedades. Eles são eficazes ao criar novas Entidades com base em um modelo. As regras do modelo garantirão que as entidades só possam se basear em determinados modelos dependendo de sua hierarquia.
>
>Para saber mais sobre como editar um modelo no painel, consulte [Criação de um modelo](/help/mobile/administer-mobile-apps.md) em criação para aplicativos móveis.

### Modelos do sistema {#system-models}

Dois tipos de modelos de sistema predefinidos são fornecidos para uma reutilização simples de conteúdo. Esses modelos não podem ser editados.

**Modelo de páginas** O modelo Páginas fornece um método rápido para reutilizar o conteúdo existente do Sites para entrega por serviços de conteúdo.

O resourceType das entidades com base no modelo de Páginas é: mobileapps/caas/components/data/pages

Caminho: Caminho para uma página de Sites. O conteúdo desse caminho (e seus filhos) será renderizado pelos manipuladores do serviço de conteúdo.

**Modelo de ativos** O modelo de Ativos fornece um método rápido para reutilizar o conteúdo existente do Assets para entrega pelos serviços de conteúdo.

O resourceType das entidades com base no modelo de Páginas é: *mobileapps/caas/components/data/assets.*

Lista de ativos: Lista de caminhos do Assets. Cada ativo será adicionado como um nó de entidade filho com um resourceType de *wcm/foundation/components/image*.

>[!NOTE]
>
>Para saber mais sobre como usar esses modelos para criar modelos a partir do painel, consulte [Criação de um modelo](/help/mobile/administer-mobile-apps.md) em criação para aplicativos móveis.
