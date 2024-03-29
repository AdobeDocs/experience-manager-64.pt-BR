---
title: Sua caixa de entrada
seo-title: Your Inbox
description: Gerenciamento de tarefas com a caixa de entrada
seo-description: Managing your tasks with the inbox
uuid: ddd48019-ce69-4a47-be2b-5b66ae2fe3c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8b607b55-2412-469f-856b-0a3dea4b0efb
exl-id: 9037f21c-5392-4322-af0d-7e220c810954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 34%

---

# Sua caixa de entrada{#your-inbox}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode receber notificações de várias áreas de AEM, incluindo fluxos de trabalho e projetos; por exemplo, sobre:

* Tarefas:

   * eles também podem ser criados em vários pontos da interface do usuário do AEM, por exemplo, em **Projetos**,
   * podem ser o produto de um fluxo de trabalho **Criar tarefa** ou **Criar tarefa do projeto** etapa.

* Fluxos de trabalhos:

   * itens de trabalho que representam as ações que você precisa executar no conteúdo da página;

      * estes são o produto do fluxo de trabalho **Participante** etapas
   * itens de falha, para permitir que os administradores tentem novamente a etapa que falhou.


Você recebe essas notificações em sua própria Caixa de entrada, onde pode visualizá-las e tomar medidas.

>[!NOTE]
>
>O AEM pronto para uso vem pré-carregado com tarefas administrativas atribuídas ao grupo de usuários administradores. Consulte [Tarefas administrativas prontas para uso](#out-of-the-box-administrative-tasks) para obter detalhes.

>[!NOTE]
>
>Para obter mais informações sobre os tipos de item, consulte também:
>
>* [Projetos](/help/sites-authoring/touch-ui-managing-projects.md)
>* [Projetos - trabalhar com tarefas](/help/sites-authoring/task-content.md)
>* [Fluxos de trabalhos](/help/sites-authoring/workflows.md)
>* [Forms](/help/forms/home.md)
>


## Caixa de entrada no cabeçalho {#inbox-in-the-header}

De qualquer um dos consoles, o número atual de itens na sua caixa de entrada é mostrado no cabeçalho. O indicador também pode ser aberto para fornecer acesso rápido às páginas que exigem ações ou acesso à caixa de entrada:

![wf-80](assets/wf-80.png)

>[!NOTE]
>
>Algumas ações também serão mostradas na [exibição de cartão do recurso apropriado](/help/sites-authoring/basic-handling.md#card-view).

## Tarefas administrativas prontas para uso  {#out-of-the-box-administrative-tasks}

O AEM pronto para uso vem pré-carregado com quatro tarefas atribuídas ao grupo de usuários administradores.

* [Configurar Analytics e Targeting](/help/sites-administering/opt-in.md)
* [Aplicar a lista de verificação de segurança do AEM](/help/sites-administering/security-checklist.md)
* Permitir coleta de dados estatísticos de uso agregados
* [Configurar HTTPS](/help/sites-administering/ssl-by-default.md)

## Abrir a Caixa de entrada   {#opening-the-inbox}

Para abrir a caixa de entrada de notificação do AEM:

1. Clique/toque no indicador na barra de ferramentas.

1. Selecione **Exibir todos**. A **Caixa de entrada do AEM** será aberta. A caixa de entrada mostra itens de fluxos de trabalho, projetos e tarefas.
1. A exibição padrão é [Exibição em lista](#inbox-list-view), mas você também pode alternar para [Exibição de calendário](#inbox-calendar-view). Isso é feito com o seletor de visualização (barra de ferramentas, parte superior direita).

   Para ambas as exibições você também pode definir [Exibir configurações](#inbox-view-settings); as opções disponíveis dependem da exibição atual.

   ![wf-79](assets/wf-79.png)

>[!NOTE]
>
>A caixa de entrada funciona como um console, portanto, use [Navegação global](/help/sites-authoring/basic-handling.md#global-navigation) ou [Pesquisar](/help/sites-authoring/search.md) para navegar para outro local quando terminar.

### Caixa de entrada - exibição de lista {#inbox-list-view}

Esta exibição lista todos os itens, juntamente com as principais informações relevantes:

![wf-82](assets/wf-82.png)

### Caixa de entrada - Exibição de calendário {#inbox-calendar-view}

Essa exibição apresenta itens de acordo com sua posição no calendário e a exibição precisa selecionada:

![wf-93](assets/wf-93.png)

É possível:

* selecionar uma exibição específica; **Linha do tempo**, **Coluna**, **Lista**

* especifique as tarefas a serem exibidas de acordo com **Agendar**; **Todos**, **Planejado**, **Em Andamento**, **Em breve**, **Vencimento Anterior**

* detalhar para obter informações mais detalhadas sobre um item
* selecione um intervalo de datas para focalizar na exibição:

![wf-91](assets/wf-91.png)

### Caixa de entrada - configurações de exibição {#inbox-view-settings}

Para ambas as exibições (Lista e Calendário), você pode definir configurações:

* **Exibição de calendário**

   Para **Exibição de calendário** você pode configurar:

   * **Agrupar por**
   * **Agendamento** ou **Nenhum**
   * **Tamanho do cartão**

   ![wf-92](assets/wf-92.png)

* **Exibição de lista**

   Para **Exibição de lista** você pode configurar o mecanismo de classificação:

   * **Classificar em**
   * **Ordem de classificação**

   ![wf-83](assets/wf-83.png)

## Realizar ação em um item {#taking-action-on-an-item}

1. Para executar uma ação em um item, selecione a miniatura do item apropriado. Os ícones das ações aplicáveis a esse item serão mostrados na barra de ferramentas:

   ![wf-84](assets/wf-84.png)

   As ações são apropriadas ao item e incluem:

   * **Concluir** ação; por exemplo, uma tarefa ou item de fluxo de trabalho.
   * **Atribuir novamente**/**Delegar** um item.
   * **Abrir** Um artigo; dependendo do tipo de item, essa ação pode:

      * mostrar as propriedades do item
      * abrir um painel ou assistente apropriado para uma nova ação
      * abrir documentação relacionada
   * **Recuar** para uma etapa anterior.
   * Visualizar a carga de um fluxo de trabalho.
   * Criar um projeto a partir do item.

   >[!NOTE]
   >
   >Para obter mais informações, consulte:
   >
   >* Itens de fluxo de trabalho - [participar de fluxos de trabalho](/help/sites-authoring/workflows-participating.md)


1. Dependendo do item selecionado, uma ação será iniciada; por exemplo:

   * uma caixa de diálogo apropriada para a ação será aberta.
   * um assistente de ação será iniciado.
   * uma página de documentação será aberta.

   Por exemplo, **Atribuir novamente** abrirá uma caixa de diálogo:

   ![wf-85](assets/wf-85.png)

   Se uma caixa de diálogo, um assistente ou uma página de documentação tiver sido aberta, é possível:

   * Confirmar a ação adequada; Por exemplo, Atribuir novamente.
   * Cancelar a ação.
   * Seta para trás; por exemplo, se um assistente de ação ou uma página de documentação tiver sido aberta, você poderá retornar à Caixa de entrada.


## Criação de uma tarefa {#creating-a-task}

Na caixa de entrada, é possível criar tarefas:

1. Selecionar **Criar**, em seguida **Tarefa**.
1. Preencha os campos necessários no **Básico** e **Avançado** guias; somente a variável **Título** é obrigatório, todas as outras são opcionais:

   * **Básico**:

      * **Título**
      * **Projeto**
      * **Destinatário**
      * **Conteúdo**; semelhante a Carga, essa é uma referência da tarefa a um local no repositório
      * **Descrição**
      * **Prioridade da tarefa**
      * **Data inicial**
      * **Data de vencimento**

   ![wf-86](assets/wf-86.png)

   * **Avançado**

      * **Nome**: isso será usado para formar o URL; se estiver em branco, será baseado na variável **Título**.

   ![wf-87](assets/wf-87.png)

1. Selecione **Enviar**.

## Criação de um projeto   {#creating-a-project}

Para determinadas tarefas, você pode criar um [Projeto](/help/sites-authoring/projects.md) com base nessa tarefa:

1. Selecione a tarefa apropriada tocando/clicando na miniatura.

   >[!NOTE]
   >
   >Somente tarefas criadas usando a opção **Criar** da **Caixa de entrada** podem ser usadas para criar um projeto.
   >
   >Itens de trabalho (de um fluxo de trabalho) não podem ser usados para criar um projeto.

1. Selecione **Criar projeto** na barra de ferramentas para abrir o assistente.
1. Selecione o modelo apropriado e **Próximo**.
1. Especifique as propriedades necessárias:

   * **Básico**

      * **Título**
      * **Descrição**
      * **Data inicial**
      * **Data de vencimento**
      * **Usuário** e papel
   * **Avançado**

      * **Nome**
   >[!NOTE]
   >
   >Consulte [Criação de um projeto](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) para obter informações completas.

1. Selecionar **Criar** para confirmar a ação.

## Filtrar itens na Caixa de entrada do AEM {#filtering-items-in-the-aem-inbox}

Você pode filtrar os itens listados:

1. Abra a **Caixa de entrada do AEM**.

1. Abra o seletor de filtro:

   ![wf-88](assets/wf-88.png)

1. Você pode filtrar os itens listados de acordo com uma variedade de critérios, muitos dos quais podem ser refinados; por exemplo:

   ![wf-89](assets/wf-89.png)

   >[!NOTE]
   >
   >Com [Configurações de exibição](#inbox-view-settings) você também pode configurar a ordem de classificação ao usar a [Exibição de lista](#inbox-list-view).
