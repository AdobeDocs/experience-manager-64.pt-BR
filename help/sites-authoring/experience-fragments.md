---
title: Fragmentos de experiência
seo-title: Experience Fragments
description: Fragmentos de experiência
seo-description: null
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
exl-id: 8906b3ab-cb08-4b3e-8796-334e36b1e491
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 48%

---

# Fragmentos de experiência{#experience-fragments}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Um Fragmento de experiência é um grupo de um ou mais componentes, incluindo conteúdo e layout que podem ser referenciados nas páginas. Eles podem conter qualquer componente.

Um fragmento de experiência:

* Faz parte de uma experiência (página).
* Pode ser usado em várias páginas.
* É baseado em um modelo (somente editável) para definir a estrutura e os componentes.
* É composto de um ou mais componentes, com layout, em um sistema de parágrafos.
* Pode conter outros fragmentos de experiência.
* Pode ser combinado com outros componentes (incluindo outros Fragmentos de experiência) para formar uma página completa (experiência).
* Pode ter variações diferentes, que podem compartilhar conteúdo e/ou componentes.
* Pode ser dividida em blocos de construção que poderão ser usados em várias variações do fragmento.

Use os Fragmentos de experiência:

* Se um autor quiser reutilizar partes (um fragmento de uma experiência) de uma página, precisará copiar e colar esse fragmento. Criar e manter essa experiências de copiar/colar é um processo demorado e pode causar erros feitos pelo usuário. Os fragmentos de experiência eliminam a necessidade de copiar/colar.
* Para dar suporte ao caso de uso de CMS sem periféricos. Os autores desejam usar o AEM somente para criação, não para entrega ao cliente. Um ponto de contato ou sistema de terceiros consumiria essa experiência e a entregaria para o usuário final.

>[!NOTE]
>
>O acesso de gravação para fragmentos de experiência requer que a conta de usuário seja registrada no grupo:
>
>`experience-fragments-editors`
>
>Entre em contato com o administrador do sistema em caso de problemas.

## Quando você deve usar fragmentos de experiência?   {#when-should-you-use-experience-fragments}

Fragmentos de experiência devem ser usados:

* Sempre que quiser reutilizar experiências.

   * Experiências que serão reutilizadas com o mesmo conteúdo ou com conteúdo semelhante

* Ao usar o AEM como uma plataforma de entrega de conteúdo para terceiros.

   * Qualquer solução que deseje usar o AEM como a plataforma de entrega de conteúdo
   * Ao incorporar conteúdo em pontos de contato de terceiros

* Se você tiver uma Experiência com variações ou representações diferentes.

   * Canal ou variações específicas do contexto
   * Experiências que fazem sentido agrupar (por exemplo, uma campanha com experiências diferentes em canais)

* Quando você usar o Comércio omnichannel.

   * Ao compartilhar conteúdo comercial em canais de redes sociais em escala
   * Tornar pontos de toque transacionais

## Organizar os Fragmentos de experiência {#organizing-your-experience-fragments}

Recomenda-se:
* usar pastas para organizar os Fragmentos de experiência,

* [configurar os modelos permitidos nessas pastas](#configure-allowed-templates-folder).

A criação de pastas permite:

* criar uma estrutura significativa para os Fragmentos de experiência; por exemplo, de acordo com a classificação

   >[!NOTE]
   >
   >Não é necessário alinhar a estrutura dos Fragmentos de experiência com a estrutura de página do site.

* [alocar os modelos permitidos no nível da pasta](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Você pode usar o [editor de modelos](/help/sites-authoring/templates.md) para criar seu próprio modelo.

O exemplo a seguir mostra Fragmentos de experiência estruturados de acordo com `Contributors`. A estrutura usada também ilustra a maneira como outros recursos, como o Gerenciamento de vários sites (incluindo cópias de idiomas), podem ser usados.

>[!CAUTION]
>
>A seguinte captura de tela foi tirada do site WKND usando o Adobe Experience Manager as a Cloud Service.

![Pastas para Fragmentos de experiência](assets/xf-folders.png)

## Criação e configuração de uma pasta para os Fragmentos de experiência {#creating-and-configuring-a-folder-for-your-experience-fragments}

Para criar e configurar uma pasta para os Fragmentos de experiência, recomenda-se:

1. [Criar uma pasta](/help/sites-authoring/managing-pages.md#creating-a-new-folder).

1. [Configurar os modelos de Fragmento de experiência permitidos para essa pasta](#configure-allowed-templates-folder).

>[!NOTE]
>
>Também é possível configurar a variável [Modelos permitidos para sua instância](#configure-allowed-templates-instance), mas este método é **not** recomendado, pois os valores podem ser substituídos na atualização.

### Configurar os Modelos permitidos para sua Pasta {#configure-allowed-templates-folder}

>[!NOTE]
>
>Esse é o método recomendado para especificar os **[!UICONTROL Modelos permitidos]**, pois os valores não serão substituídos na atualização.

1. Acesse a pasta **[!UICONTROL Fragmentos de experiência]** necessária.

1. Selecione a pasta e depois as **[!UICONTROL Propriedades]**.

1. Especifique a expressão regular para recuperar os modelos necessários no campo **[!UICONTROL Modelos permitidos]**.

   Por exemplo:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![Propriedades dos fragmentos de experiência - Modelos permitidos](assets/xf-folders-templates.png)

1. Selecione **[!UICONTROL Salvar e fechar]**.

### Configurar os Modelos permitidos para sua Instância {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Não é recomendável alterar a variável **[!UICONTROL Modelos permitidos]** por esse método, pois os modelos especificados podem ser substituídos na atualização.
>
>Use esta caixa de diálogo apenas para fins informativos.

1. Acesse o console **[!UICONTROL Fragmentos de experiência]** necessário.

1. Selecione **[!UICONTROL Opções de configuração]**:

   ![Botão Configuração](assets/xf-folders-18.png)

1. Especifique os modelos necessários na caixa de diálogo **[!UICONTROL Configurar fragmentos de experiência]**:

   ![Configurar fragmentos de experiência](assets/xf-folders-19.png)

1. Selecione **[!UICONTROL Salvar]**.

## Criação de um fragmento de experiência {#creating-an-experience-fragment}

Para criar um fragmento de experiência:

1. Selecione **[!UICONTROL Fragmentos de experiência]** na Navegação global.

   ![screen_shot_2018-04-05at9221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. Navegue até a pasta desejada e selecione **[!UICONTROL Criar]**.

1. Selecione **[!UICONTROL Fragmento de experiência]** para abrir o assistente **[!UICONTROL Criar fragmento de experiência]**.

   Selecione o **[!UICONTROL modelo]** obrigatório e, em seguida, clique em **[!UICONTROL Avançar]**:

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. Insira as **[!UICONTROL Propriedades]** do Fragmento de experiência.

   É obrigatório ter um **[!UICONTROL título]**. Se a variável **[!UICONTROL Nome]** for deixado em branco, ele será derivado do **[!UICONTROL Título]**.

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. Clique em **[!UICONTROL Criar]**.

   Uma mensagem será exibida. Selecionar:

   * **[!UICONTROL Concluído]** para retornar ao console
   * **[!UICONTROL Abrir]** para abrir o editor de fragmento

## Edição de seu fragmento de experiência {#editing-your-experience-fragment}

O Editor de fragmento de experiência oferece recursos semelhantes ao Editor de páginas normal. Consulte [Editar conteúdo da página](/help/sites-authoring/editing-content.md) para obter mais informações sobre como usá-lo.

O seguinte procedimento de exemplo ilustra como criar um teaser para um produto:

1. Arraste e solte uma **[!UICONTROL Teaser da categoria]** do [Navegador de componentes](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. Selecionar **[[!UICONTROL Configurar]](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)** na barra de ferramentas do componente.
1. Adicione o **[!UICONTROL Ativo]** e defina as **[!UICONTROL Propriedades]** conforme necessário.
1. Confirme as definições com **[!UICONTROL Concluído]** (ícone de marca de verificação).
1. Adicione mais componentes conforme necessário.

## Criação de uma variação de Fragmento de experiência {#creating-an-experience-fragment-variation}

Você pode criar variações do Fragmento de experiência, dependendo das suas necessidades:

1. Abra o fragmento para [edição](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Abra a guia **[!UICONTROL Variações]**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **Criar** O permite criar:

   * **[!UICONTROL Variação]**
   * **[!UICONTROL Variação como Live Copy]**.

1. Defina as propriedades necessárias:

   * **[!UICONTROL Modelo]**
   * **[!UICONTROL Título]**
   * **[!UICONTROL Nome]**; se deixado em branco, ele será derivado do Título
   * **[!UICONTROL Descrição]**
   * **[!UICONTROL Tags de variação]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. Confirme com **[!UICONTROL Concluído]** (ícone de marca de verificação), a nova variação será mostrada no painel:

   ![xf-authoring-08](assets/xf-authoring-08.png)

## Usar seu fragmento de experiência {#using-your-experience-fragment}

Agora é possível usar o Fragmento de experiência ao criar suas páginas:

1. Abra qualquer página para edição.

   Por exemplo: [http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. Crie uma instância do componente Fragmento de experiência arrastando o componente do navegador Componentes para o sistema de parágrafos da página:

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. Adicione o Fragmento de experiência real à ocorrência de componente:

   * Arraste o fragmento necessário do Navegador de Ativos e solte no componente
   * Selecionar **[!UICONTROL Configurar]** na barra de ferramentas do componente e especifique o fragmento a ser usado, confirme com **Concluído** (marca de verificação)

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >Editar, na barra de ferramentas do componente, opera como um atalho para abrir o fragmento no editor de fragmentos.

## Blocos de construção {#building-blocks}

Selecione um ou mais componentes para criar um bloco de construção para reciclagem no seu fragmento:

### Criar um bloco de construção {#creating-a-building-block}

Para criar um novo Bloco de construção:

1. No editor Fragmento de experiência, selecione os componentes que deseja reutilizar:

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. Na barra de ferramentas dos componentes, selecione **[!UICONTROL Converter em bloco de construção]**:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   Por exemplo:

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. Insira o nome do **[!UICONTROL Bloco de construção]** e confirme com **[!UICONTROL Converter]**:

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. O **Bloco de construção** será mostrado na guia e poderá ser selecionado no sistema de parágrafos:

   ![xf-authoring-15](assets/xf-authoring-15.png)

### Gerenciar um bloco de construção {#managing-a-building-block}

O bloco de construção está visível na guia **[!UICONTROL Blocos de construção]**. Para cada bloco, as seguintes ações estão disponíveis:

* Acesse o mestre: abra a variação mestre em uma nova guia
* Renomear
* Excluir

![xf-authoring-16](assets/xf-authoring-16.png)

### Usar um bloco de construção {#using-a-building-block}

Arraste o bloco de construção para o sistema de parágrafo de qualquer fragmento, como com qualquer componente.

## A representação HTML simples {#the-plain-html-rendition}

Usar o `.plain.` no URL, você pode acessar a representação de HTML simples.

Isso está disponível no navegador, mas o objetivo principal é permitir outros aplicativos (por exemplo, aplicativos da Web de terceiros, implementações móveis personalizadas) para acessar o conteúdo do Fragmento de experiência diretamente, usando apenas o URL.

A representação de HTML simples adiciona o protocolo, host e caminho de contexto aos caminhos que são:

* do tipo: `src`, `href`ou `action`

* ou terminar com: `-src`ou `-href`

Por exemplo:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Os links sempre fazem referência à instância de publicação. Eles devem ser consumidos por terceiros, de modo que o link sempre será chamado da instância de publicação, não do autor.

![xf-authoring-17](assets/xf-authoring-17.png)

## Exportar fragmentos de experiência {#exporting-experience-fragments}

Por padrão, os Fragmentos de experiência são entregues no formato HTML. Isso pode ser usado por canais de AEM e de terceiros.

Para exportação para o Adobe Target, é usado o HTML. Consulte [Integração do Target com fragmentos de experiência](/help/sites-administering/experience-fragments-target.md) para obter informações completas.
