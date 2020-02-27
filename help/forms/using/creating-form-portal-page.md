---
title: Criar uma página de portal de formulários
seo-title: Criar uma página de portal de formulários
description: O Portal de formulários equipe os desenvolvedores da Web com componentes para criar e personalizar um portal de formulários em sites criados usando o Adobe Experience Manager (AEM).
seo-description: O Portal de formulários equipe os desenvolvedores da Web com componentes para criar e personalizar um portal de formulários em sites criados usando o Adobe Experience Manager (AEM).
uuid: 328f3342-d6ca-4413-9f1d-1a550df74bde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7387dfe8-0029-4ad0-b319-fc519928318b
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Criar uma página de portal de formulários {#creating-a-forms-portal-page}

Os componentes do portal de formulários equipam os desenvolvedores da Web com componentes para criar e personalizar um portal de formulários em sites criados usando o Adobe Experience Manager (AEM). Para obter uma visão geral rápida do portal de formulários, consulte [Introdução à publicação de formulários em um portal](/help/forms/using/introduction-publishing-forms.md).

## Pré-requisitos {#prerequisites}

Os componentes do portal de formulários não estão disponíveis para uso por padrão. Certifique-se de que as seguintes categorias de componentes do portal de formulários estejam ativadas conforme descrito em [Ativação de componentes](/help/forms/using/enabling-forms-portal-components.md)do portal de formulários.

**O Document Services** inclui os componentes Pesquisa e Lister, Link e Rascunhos e Submissões.

**Os Predicados** do Document Services incluem os componentes Predicado por data, Predicado de texto completo, Predicado de propriedades e Predicado por tags. Esses componentes são usados para configurar a pesquisa no componente Pesquisar e Lister.

Depois de habilitados em uma página de sites do AEM, essas categorias de componentes estão disponíveis para uso no navegador de componentes.

![](assets/component-categories.png) Componentes do portal do AEM Forms no navegador **de componentes** Figura: Categorias de componentes do portal do *Forms*

## Componente de pesquisa e lister {#search-amp-lister-component}

O componente de Pesquisa e Lister, disponível na categoria de componente do Document Services, é usado para listar formulários em uma página e implementar a pesquisa nos formulários listados. O componente inclui dois painéis:

* Painel de lista onde os formulários estão listados.
* Painel de pesquisa onde você adiciona a funcionalidade de pesquisa.

Você pode arrastar e soltar o componente Pesquisar e Lister da categoria de componente do Document Services no navegador de componentes para a página. O componente, quando adicionado, é semelhante ao seguinte.

![](assets/fp-grid-viw.png) Componente de pesquisa e lister em uma página **** Figura: Componente *de pesquisa e lister em uma página com layout Grade*

### Painel Lista {#list-pane}

O painel Lista é uma área em que seus formulários são listados. O componente Pesquisar e lister fornece várias opções de configuração que podem ser usadas para controlar a exibição de formulários no painel Lista.

Para configurar o painel Lista, toque no componente Pesquisar e Lister e toque em ![settings_icon](assets/settings_icon.png). A caixa de diálogo **[!UICONTROL Editar componente]** é aberta.

![](assets/edit-list.png) Painel de lista no modo **de edição** Figura: Painel *Lista no modo de edição*

A caixa de diálogo **[!UICONTROL Editar]** inclui várias guias que fornecem opções de configuração descritas na tabela abaixo. Pressione **[!UICONTROL OK]** para salvar a configuração, quando concluído.

<table> 
 <tbody> 
  <tr> 
   <th>Guia</th> 
   <th>Configuração</th> 
   <th>Descrição</th> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Pastas de ativos</strong></span></td> 
   <td>Adicionar Item</td> 
   <td>Configura as pastas onde os ativos são carregados usando a interface do usuário do AEM Forms. Por padrão, lista todos os ativos carregados. Para obter mais informações sobre a interface do usuário do AEM Forms, consulte <a href="/help/forms/using/introduction-managing-forms.md" target="_blank">Introdução ao gerenciamento de formulários</a>.</td> 
  </tr> 
  <tr> 
   <td><p><span class="uicontrol"><strong>Exibir</strong></span></p> </td> 
   <td>Texto do título</td> 
   <td>Título do componente de Pesquisa e Lister. O título padrão é Portal <strong>do Forms.</strong></td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Modelo de layout</td> 
   <td>Layout dos ativos. </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Desativar pesquisa avançada</td> 
   <td>Quando ativado, oculta o ícone de pesquisa avançada.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Desativar pesquisa de texto</td> 
   <td>Quando ativada, oculta a barra de pesquisa de texto completo.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Resultado</strong></span></td> 
   <td>Número de resultados por página</td> 
   <td>Configura o número máximo de formulários que você deseja exibir em uma página.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Texto de resultados</td> 
   <td><p>Configura o texto de resultados (por exemplo, 1-12 de 601 <strong>Resultados</strong>). The default value is <strong>Results</strong>.</p> <p>Por exemplo, se você especificar <strong>Formulários </strong>nesse campo e houver um total de 601 formulários, o texto resultante será alterado para 1-12 de 601 <strong>Formulários.</strong></p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Texto da página</td> 
   <td><p>Configura o texto da página (por exemplo, <strong>Página </strong>1 de 51). The default value is <strong>Page</strong>.</p> <p>Por exemplo, se você especificar o Formulário <strong>de aplicativo </strong>neste campo e houver 51 páginas, o texto da página será alterado para Formulário <strong>de aplicativo </strong>1 de 51.</p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Do Texto</td> 
   <td><p>Substitui a palavra <strong>de</strong> pelo texto especificado (Página 1 <strong>de </strong>51). The default value is <strong>of</strong>.</p> <p>Por exemplo, se você especificar <strong>fora </strong>desse campo, o texto mudará para Página 1 <strong>de </strong>51.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Link do formulário</strong></span></td> 
   <td>Tipo de renderização</td> 
   <td>Controla a listagem de formulários com base no tipo de renderização especificado. As opções disponíveis são PDF e HTML. Por exemplo, se você selecionar somente HTML como tipo de renderização, os formulários PDF serão filtrados.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Perfil HTML</td> 
   <td>Configura o perfil HTML a ser usado para renderização. Todos os perfis disponíveis estão listados na lista suspensa.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Enviar URL</td> 
   <td><p>Configura um servlet no qual os dados do formulário são enviados.</p> <p><strong></strong> Observação: O URL de <em>envio de um formulário pode ser especificado em vários locais e sua ordem de precedência é a seguinte:</em></p> 
    <ol> 
     <li><em>O URL de envio incorporado no formulário (no botão Enviar) tem a prioridade mais alta.</em></li> 
     <li><em>O URL de envio mencionado na interface do usuário do AEM Forms tem a segunda prioridade mais alta.</em></li> 
     <li><em>O URL de envio mencionado no portal de formulários tem a prioridade mais baixa.</em></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Dica da ferramenta Ação de renderização HTML</td> 
   <td>Configura o texto da dica de ferramenta, que é exibida ao passar o ponteiro do mouse sobre <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> (o ícone HTML5).</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Dica da ferramenta Ação de renderização de PDF</td> 
   <td>Configura o texto da dica de ferramenta, que é exibida ao passar o ponteiro do mouse sobre <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> (o ícone PDF).</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Estilo</strong></span></td> 
   <td>Tipo de estilo</td> 
   <td>Permite que você especifique <strong>Sem estilo, Estilo</strong>padrão ou Estilo <strong>personalizado </strong>para listar os formulários.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Caminho de estilo personalizado</td> 
   <td>Se você selecionou Personalizado como o Tipo de estilo, navegue para especificar o caminho para o CSS personalizado, caso contrário selecione Padrão.</td> 
  </tr> 
 </tbody> 
</table>

### Painel de pesquisa {#search-pane}

O painel Pesquisar permite que você adicione os componentes Predicado de data, Predicado de texto completo, Predicado de propriedades e Predicado de tags da categoria Predicados do Document Services no Sidekick de AEM. Esses componentes implementam a funcionalidade de pesquisa para que os usuários realizem a pesquisa nos formulários listados.

**** Dica: *É possível controlar a lista de formulários exibida no portal de formulários com base em critérios predefinidos e ocultar a funcionalidade de pesquisa para usuários finais. Para controlar a lista de formulários, use os componentes Predicar para aplicar filtros de pesquisa. Você também pode especificar os valores de filtro padrão e desativar a pesquisa na guia Exibir da caixa de diálogo Editar componente.*

![](assets/search-with-predicates.png) Painel de pesquisa com data, texto completo, propriedades e tags - Predicado **** Figura: Painel de *pesquisa com data, texto completo, propriedades e previsão de tags*

#### Predicado de data {#date-predicate}

O componente Predicado de data, quando adicionado, permite a pesquisa nos formulários listados que foram modificados durante uma duração especificada.

Para configurar o componente Predicado de data:

1. Toque no componente e toque em ![settings_icon](assets/settings_icon.png). A caixa de diálogo Editar é aberta.
1. Especifique o seguinte:

   * **** Tipo: A única opção disponível é Data **[!UICONTROL da]**&#x200B;última modificação.
   * **** Texto: Rótulo ou legenda para o Componente de previsão de data. O valor padrão é Data **[!UICONTROL da]**&#x200B;última modificação.
   * **** Rótulo da data de início: Rótulo ou legenda do campo de data inicial.
   * **** Rótulo da data final: Rótulo ou legenda para o campo de data final.
   * **** Ocultar: Para aplicar o filtro de datas padrão à lista de formulários.

1. Toque em **[!UICONTROL OK]**.

#### Predicado de texto completo {#full-text-predicate}

O componente Predicado de texto completo implementa a pesquisa de texto completo nos dados do formulário, como nome e descrição. Os usuários podem pesquisar qualquer string de texto para retornar formulários que contenham o texto em seu nome ou descrição.

Para configurar o componente Predicado de texto completo:

1. Toque no componente e toque em ![settings_icon](assets/settings_icon.png). A caixa de diálogo Editar é aberta.
1. Especifique o título no campo Título **** principal.
1. Toque Em **[!UICONTROL Ok]**.

#### Predicado de propriedades {#properties-predicate}

O componente Predicado de propriedades implementa a pesquisa de formulários com base nas propriedades do formulário, como título, autor e descrição.

Para configurar o componente Predicado de propriedades:

1. Toque no componente e toque em ![settings_icon](assets/settings_icon.png). A caixa de diálogo **[!UICONTROL Editar]** é aberta.
1. Na guia **[!UICONTROL Geral]** , especifique o rótulo de pesquisa. The default value is **[!UICONTROL Properties]**.

1. Na guia **[!UICONTROL Opções]** , toque em **[!UICONTROL Adicionar item]**.
1. Selecione uma propriedade na lista suspensa e especifique um rótulo de pesquisa para ela no campo abaixo da lista suspensa.
1. Repita a etapa 4 para adicionar mais propriedades. Você também pode especificar um valor de filtro padrão para listar formulários com base nos critérios especificados e ocultar a propriedade para pesquisa por usuários finais. Marque a caixa de seleção Ocultar para uma propriedade e especifique o valor do filtro padrão.

   Por exemplo, se você deseja exibir formulários que contêm &quot;Viagem&quot; em seus títulos, selecione Ocultar ao lado da propriedade Título. Além disso, especifique Viagem na caixa de texto de valor de filtro padrão.

1. Toque em **[!UICONTROL OK]**.

#### Predicado de tags {#tags-predicate}

O componente Predicado de tags implementa a pesquisa de formulários com base em tags definidas no Gerenciador de formulários.

Para configurar o componente Predicado de tags:

1. Toque no componente e toque em ![settings_icon](assets/settings_icon.png). A caixa de diálogo **[!UICONTROL Editar]** é aberta.
1. Toque no botão de seta para baixo ao lado do campo Tags.
1. Selecione as tags apropriadas.
1. Toque em **[!UICONTROL OK]**.

As tags selecionadas são exibidas no painel Pesquisar junto com as caixas de seleção. Os usuários agora podem restringir sua pesquisa com base nas tags.

## Listar formulários em uma página {#list-forms-on-a-page-br}

Para listar formulários em uma página, adicione o Componente **[!UICONTROL Pesquisar e Lister]** à página e configure o Painel **[!UICONTROL de lista]**. Para permitir que os usuários finais pesquisem formulários com data, texto e tags, adicione um componente do Painel **[!UICONTROL de]** pesquisa.

Para vincular um formulário de qualquer lugar na página, use o componente Link. Para obter mais informações sobre o componente de link, consulte [Incorporação do componente de link em uma página](/help/forms/using/embedding-link-component-page.md).

Para listar os formulários que estão em um estado de rascunho e os formulários que já foram enviados, use o componente **[!UICONTROL Rascunhos e Envios]** . Para obter mais informações, consulte [Personalizando o componente](/help/forms/using/draft-submission-component.md)Rascunhos e Envios.

## Compatibilidade com dispositivos móveis {#mobile-device-friendliness}

O componente de Pesquisa e Lister do Portal do Forms é compatível com dispositivos móveis e se adapta adequadamente. Todas as três exibições padrão: Os relatos de grade, placa e painel de acordo com o dispositivo no qual o site é aberto, são fornecidos com o fato de que a página da Web também se adapta. O fato simples é que o Search &amp; Lister é apenas um componente e não governa o estilo de nível de página.

A imagem a seguir mostra o componente de Pesquisa e Lister quando aberto em um dispositivo móvel:

![](assets/search_lister.png) Captura de tela do componente **Pesquisa e Lister** Figura: componente *Pesquisar e Lister*

## Personalizar uma página do portal de formulários {#customizing-a-forms-portal-page-br}

Você pode personalizar uma página do portal de formulários para fornecer uma aparência distinta à página. Você também pode adicionar metadados para melhorar a experiência de pesquisa, alterar o layout da página e adicionar estilos CSS personalizados. Para obter mais informações, consulte [Personalizar modelos para componentes](/help/forms/using/customizing-templates-forms-portal-components.md)do Portal de Formulários.

A interface do usuário do AEM Forms permite adicionar metadados personalizados a formulários. Os metadados personalizados são úteis para fornecer uma experiência de listagem e pesquisa de formulários aos usuários finais. Para obter mais informações sobre metadados personalizados, consulte [Personalizar modelos para componentes](/help/forms/using/customizing-templates-forms-portal-components.md)do Portal de formulários.

O portal de formulários fornece ações de renderização. Você pode personalizar o portal de formulários para adicionar mais ações. Para obter informações detalhadas, consulte [Adicionar ação personalizada em itens do lister de formulários.](/help/forms/using/add-custom-action-form-lister.md)
