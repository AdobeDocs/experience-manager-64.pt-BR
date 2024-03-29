---
title: Criação de conteúdo direcionado usando o modo Direcionar
seo-title: Authoring Targeted Content Using Targeting Mode
description: O modo de Direcionamento e o componente de Direcionamento fornecem ferramentas para criar conteúdo para experiências
seo-description: Targeting mode and the Target component provide tools for creating content for experiences
uuid: 174f9e9b-02c7-48dd-92fc-e407d2a734c3
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 0e2e95fa-9e27-4edc-b57b-82cefe8d4088
exl-id: 9b973d03-fd0a-4c22-8045-7dddc024e553
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 33%

---

# Criação de conteúdo direcionado usando o modo Direcionar{#authoring-targeted-content-using-targeting-mode}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Crie conteúdo direcionado usando o modo de Direcionamento do AEM. O modo de Direcionamento e o componente de Direcionamento fornecem ferramentas para criar conteúdo para experiências:

* Reconheça facilmente o conteúdo direcionado que está na página. Uma linha pontilhada forma uma borda em torno de todo o conteúdo direcionado.
* Selecione uma marca e uma atividade para ver as experiências.
* Adicione experiências a uma atividade ou remova experiências.
* Realize testes A/B e converta vencedores (somente Adobe Target).
* Adicione ofertas a uma experiência criando ofertas ou usando ofertas de uma biblioteca.
* Configure metas e monitore o desempenho.
* Simule a experiência do usuário.
* Para obter mais personalizações, configure o componente de Direcionamento .

Você pode usar o AEM ou o Adobe Target como mecanismo de direcionamento (é necessário ter uma conta válida do Adobe Target para usar o Adobe Target). Se você estiver usando o Adobe Target, é necessário configurar a integração primeiro. Consulte [instruções para integração com o Adobe Target](/help/sites-administering/target.md).

![chlimage_1-59](assets/chlimage_1-59.png)

As atividades e experiências que você vê no modo de Direcionamento refletem o [Console de atividades](/help/sites-authoring/activitylib.md):

* As alterações feitas nas atividades e experiências usando o modo de Direcionamento são refletidas no console Atividades.
* As alterações feitas no console Atividades são refletidas no modo Direcionar .

>[!NOTE]
>
>Quando você cria uma campanha no Adobe Target, ele atribui uma propriedade chamada `thirdPartyId` a cada campanha. Quando você exclui a campanha no Adobe Target, o thirdPartyId não é excluído. Não é possível reutilizar o `thirdPartyId` para campanhas de tipos diferentes (AB, XT) e ele não pode ser removido manualmente. Para evitar esse problema, dê a cada campanha um nome exclusivo. Por isso, nomes de campanhas não podem ser reutilizados em diferentes tipos de campanha.
>
>Se você usar o mesmo nome no mesmo tipo de campanha, a campanha existente será substituída.
>
>Se, durante a sincronização, você encontrar o erro “A solicitação falhou. `thirdPartyId` já existe”, altere o nome da campanha e sincronize novamente.

>[!NOTE]
>
>Ao direcionar, a combinação de identidade visual e atividade é mantida no nível do usuário, não no nível do canal.

## Alternar para o modo de direcionamento {#switching-to-targeting-mode}

Alterne para o modo de Direcionamento para acessar as ferramentas de criação de conteúdo direcionado.

Para alternar para o modo de Direcionamento:

1. Abra a página para a qual deseja criar conteúdo direcionado.
1. Na barra de ferramentas, na parte superior da página, clique ou toque no menu suspenso de modo para revelar os tipos disponíveis.

   ![chlimage_1-60](assets/chlimage_1-60.png)

1. Clique ou toque em **Direcionamento**. As opções de direcionamento são exibidas na parte superior da página.

   ![chlimage_1-61](assets/chlimage_1-61.png)

## Adicionar uma atividade usando o modo de direcionamento {#adding-an-activity-using-targeting-mode}

Use o modo de Direcionamento para adicionar uma atividade a uma marca. Ao adicionar uma atividade, ela contém a experiência Padrão. Após adicionar a atividade, você inicia o processo de direcionamento de conteúdo para a atividade.

Você também pode criar e gerenciar atividades do Adobe Target a partir do AEM com a opção de selecionar o mecanismo de direcionamento - AEM ou Adobe Target - e selecionar o tipo de atividade - Direcionamento de experiência ou Teste A/B.

Além disso, é possível gerenciar metas e métricas para todas as atividades do Adobe Target e gerenciar os públicos da Adobe Target. O relatório de atividades do Adobe Target, incluindo a conversão de vencedores para testes A/B, também é incluído.

Quando você adiciona uma atividade, ela também é exibida na variável [Console de atividades](/help/sites-authoring/activitylib.md).

Para adicionar uma atividade:

1. Use o **Marca** menu suspenso para selecionar a marca para a qual deseja criar a atividade.

   >[!NOTE]
   >
   >Recomenda-se [criar marcas pelo console atividades](/help/sites-authoring/activitylib.md#creating-a-brand-using-the-activities-console).
   >
   >Se você criar uma marca de qualquer outra maneira, faça com que o nó `/campaigns/<brand>/master` exista ou ocorrerá um erro ao tentar criar uma atividade.

1. Clique ou toque em + ao lado do **Atividade** menu suspenso.
1. Digite um nome para a atividade.

   >[!NOTE]
   >
   >Quando você cria uma nova atividade e tem uma configuração da nuvem do Adobe Target anexada à página ou a uma página principal, o AEM assume automaticamente o Adobe Target como mecanismo.

1. No menu suspenso do mecanismo de **Direcionamento**, selecione o mecanismo direcionamento.

   * Se você selecionar **ContextHub AEM**, os campos restantes estarão esmaecidos e indisponíveis. Clique ou toque em **Criar**.
   * Se você selecionar **Adobe Target**, é possível selecionar uma configuração (por padrão, é a configuração fornecida ao [configuração da conta](/help/sites-administering/opt-in.md)) e Tipo de atividade.
   * Se estiver usando a integração AEM/Adobe Campaign e estiver enviando o conteúdo direcionado (boletins informativos), selecione **Adobe Campaign**. Consulte [Integração com o Adobe Campaign](/help/sites-administering/campaign.md) para obter mais informações.

1. No menu Atividade, selecione **Direcionamento de experiência** ou **Teste A/B**.

   * Direcionamento de experiência - gerencie as atividades do Adobe Target a partir do AEM.
   * Teste A/B - crie/gerencie atividades de teste A/B no Adobe Target a partir de AEM.

## O processo de direcionamento: Criar, direcionar e metas e configurações {#the-targeting-process-create-target-and-goals-settings}

O modo de Direcionamento permite configurar vários aspectos de uma atividade. Use o seguinte processo de três etapas para criar conteúdo direcionado para uma atividade de marca:

1. [Criar](#create-authoring-the-experiences): Adicione ou remova experiências e adicione ofertas para cada experiência.
1. [Target](#target-configuring-the-audiences): Especifique o público alvo de cada experiência. Você pode direcionar um público-alvo específico e, se estiver usando o teste A/B, decidir qual porcentagem do tráfego vai para qual experiência.
1. [Metas e configurações](#goals-settings-configuring-the-activity-and-setting-goals): Agende a atividade e defina a prioridade. Também é possível definir metas de métricas de sucesso.

Use o procedimento a seguir para iniciar o processo de direcionamento de conteúdo para uma atividade.

>[!NOTE]
>
>Para usar o processo de direcionamento, você deve ser membro do grupo de usuários Autores da atividade de direcionamento.

Para adicionar uma atividade:

1. No **Marca** no menu suspenso , selecione a marca que contém a atividade em que você está trabalhando.
1. No **Atividade** no menu suspenso , selecione a atividade para a qual você está criando o conteúdo direcionado.
1. Para revelar os controles que o orientam pelo processo de direcionamento, clique ou toque em **Iniciar o direcionamento**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

   >[!NOTE]
   >
   >Para alterar a atividade com a qual você está trabalhando, clique ou toque em **Voltar**.

## Criar: Criação das experiências {#create-authoring-the-experiences}

A etapa Criar do direcionamento de conteúdo envolve a criação de experiências. Durante essa etapa, você pode criar ou excluir as experiências da atividade e adicionar ofertas a cada experiência.

### Visualização das ofertas de experiência no modo de direcionamento {#seeing-experience-offers-in-targeting-mode}

Depois de [iniciar o processo de direcionamento](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings), selecione uma experiência para ver as ofertas fornecidas para ela. Quando você seleciona uma experiência, os componentes direcionados na página mudam para mostrar a oferta dessa experiência.

>[!CAUTION]
>
>Tenha cuidado ao desativar o direcionamento para um componente que já esteja direcionado na instância do autor. A respectiva atividade será automaticamente excluída da instância de publicação também.

>[!NOTE]
>
>Uma oferta é o conteúdo de um componente direcionado.

As experiências são exibidas no painel Públicos-alvo. No exemplo a seguir, as experiências incluem **Padrão**, **Feminino**, **Feminino acima de 30** e **Feminino abaixo de 30**. Este exemplo mostra a oferta Padrão de um componente de **Imagem** direcionado.

![chlimage_1-63](assets/chlimage_1-63.png)

Quando uma experiência diferente é selecionada, o componente de imagem mostra a oferta para essa experiência.

![chlimage_1-64](assets/chlimage_1-64.png)

Quando uma experiência é selecionada e o componente de destino não inclui uma oferta para essa experiência, o componente exibe **Adicionar oferta** sobreposta à oferta padrão semitransparente. Quando nenhuma oferta é criada para uma experiência, a oferta **Padrão** é exibida no segmento que está mapeado para a experiência.

![chlimage_1-65](assets/chlimage_1-65.png)

A experiência padrão também é exibida quando as propriedades do visitante não correspondem aos segmentos mapeados às experiências. Consulte [Adicionar experiências usando o modo de direcionamento](#adding-and-removing-experiences-using-targeting-mode).

### Ofertas personalizadas e ofertas de biblioteca {#custom-offers-and-library-offers}

Ofertas que são [criado na página](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) e usados para uma única experiência são chamados de ofertas personalizadas. A imagem a seguir é sobreposta ao conteúdo de uma oferta personalizada:

![chlimage_1-66](assets/chlimage_1-66.png)

As ofertas [adicionadas de uma biblioteca de ofertas](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) são sobrepostas com a seguinte imagem:

![chlimage_1-67](assets/chlimage_1-67.png)

Você pode salvar ofertas personalizadas em uma biblioteca de ofertas se decidir reutilizá-la. Também é possível converter uma oferta da biblioteca em uma oferta personalizada se quiser modificar o conteúdo de uma experiência. Após a edição, é possível salvar a oferta novamente na biblioteca.

### Adicionar e remover experiências usando o modo de direcionamento {#adding-and-removing-experiences-using-targeting-mode}

Uso da etapa Criar de [processo de direcionamento](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings), você pode adicionar e remover experiências. Além disso, você pode duplicar uma experiência e também renomeá-la.

#### Adicionar experiências usando o modo de direcionamento {#adding-experiences-using-targeting-mode}

Para adicionar uma experiência:

1. Para adicionar uma experiência, clique ou toque em **+ Adicionar direcionamento de experiência**, que aparece abaixo das experiências existentes no painel **Públicos**.
1. Selecione um público-alvo. Por padrão, esse nome é o nome da experiência. Você pode digitar outro nome, se desejar. Clique ou toque em **OK**.

#### Remover experiências usando o modo de direcionamento {#removing-experiences-using-targeting-mode}

Para excluir uma experiência:

1. Clique ou toque na seta ao lado do nome da experiência.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Clique em **Excluir**.

#### Renomear experiências usando o modo de direcionamento {#renaming-experiences-using-targeting-mode}

Para renomear experiências usando o Modo de direcionamento:

1. Clique ou toque na seta ao lado do nome da experiência.
1. Clique em **Renomear experiência** e digite o novo nome.
1. Clique ou toque em outro local na tela para salvar as alterações.

#### Edição de públicos-alvo usando o modo de direcionamento {#editing-audiences-using-targeting-mode}

Para editar os públicos-alvo usando o modo de direcionamento:

1. Clique ou toque na seta ao lado do nome da experiência.
1. Clique em **Editar público** e selecione um novo público.
1. Clique em **OK**.

#### Duplicação de experiências usando o modo de direcionamento {#duplicating-experiences-using-targeting-mode}

Para copiar experiências usando o modo de direcionamento:

1. Clique ou toque na seta ao lado do nome da experiência.
1. Clique em **Duplicar** e escolha o público.
1. Renomeie a experiência, se desejado, e clique em **OK**.

### Criação de ofertas usando o modo de direcionamento {#creating-offers-using-targeting-mode}

Direcione um componente para criar ofertas para experiências. Os componentes direcionados fornecem o conteúdo que é usado como ofertas para experiências.

* [Direcionar um componente existente](/help/sites-authoring/content-targeting-touch.md#creating-a-default-offer-by-targeting-an-existing-component). O conteúdo se torna a oferta da Experiência padrão.
* [Adicione um componente de Direcionamento](/help/sites-authoring/content-targeting-touch.md#creating-an-offer-by-adding-a-target-component) e, em seguida, adicione o conteúdo ao componente.

Depois que um componente é direcionado, você pode adicionar ofertas para cada experiência:

* [Adicionar ofertas personalizadas](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer).
* [Adicionar ofertas de uma biblioteca](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library).

As seguintes ferramentas estão disponíveis para trabalhar com ofertas:

* [Adicionar uma oferta personalizada a uma biblioteca de ofertas](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library).
* [Converter uma oferta de biblioteca a uma oferta personalizada](/help/sites-authoring/content-targeting-touch.md#converting-a-library-offer-to-a-custom-library).
* [Abra uma oferta da biblioteca e edite o conteúdo](/help/sites-authoring/content-targeting-touch.md#editing-a-library-offer).

#### Criação de uma oferta padrão direcionando um componente existente {#creating-a-default-offer-by-targeting-an-existing-component}

Direcione um componente na página para usá-lo como a oferta para a experiência Padrão da atividade. Quando você direciona um componente, ele é envolvido em um componente de Direcionamento e seu conteúdo se torna a oferta para a experiência Padrão.

Ao direcionar um componente, somente esse componente pode ser usado na oferta. Não é possível remover o componente da oferta ou adicionar outros componentes à oferta.

Execute o procedimento a seguir após [iniciar o processo de direcionamento](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings).

1. Clique ou toque no componente para direcionar. A barra de ferramentas do componente é exibida, semelhante ao exemplo a seguir.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. Clique ou toque no ícone de Direcionamento.

   ![](do-not-localize/chlimage_1.png)

   O conteúdo do componente é a oferta para a experiência padrão. Quando um componente é direcionado, seu nó padrão é replicado para cada experiência. Isso é necessário para editar o nó de conteúdo correto durante a criação da experiência. Para essas experiências diferentes do padrão,[ adicione uma oferta personalizada](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) ou[ adicione uma oferta da biblioteca](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library).

#### Criação de uma oferta adicionando um componente de Direcionamento {#creating-an-offer-by-adding-a-target-component}

Adicione um componente de Direcionamento para criar a oferta para experiência Padrão. O componente de Direcionamento é um contêiner de outros componentes e os componentes incluídos nele tornam-se direcionados. No componente de Direcionamento, é possível adicionar vários componentes para criar uma oferta. Além disso, é possível usar componentes diferentes em cada experiência para criar ofertas diferentes.

Consulte [Configuração das opções do componente de Direcionamento](/help/sites-authoring/content-targeting-touch.md#configuring-target-component-options) para obter informações sobre como personalizar esse componente.

>[!NOTE]
>
>As ofertas criadas usando o [console Ofertas](/help/sites-authoring/offerlib.md) também podem conter vários componentes. Essas ofertas pertencem a uma biblioteca de ofertas e podem ser usadas para várias experiências.

Como o componente de Direcionamento é um contêiner, ele aparece como uma área para soltar outros componentes.

No modo de Direcionamento, o componente de Direcionamento tem uma borda azul e a mensagem de destino indica a natureza direcionada.

![chlimage_1-70](assets/chlimage_1-70.png)

No modo de Edição, o componente de Direcionamento tem um ícone de alvo.

![](do-not-localize/chlimage_1-1.png)

Quando você arrasta os componentes ao componente de Direcionamento, eles se tornam componentes direcionados.

![chlimage_1-71](assets/chlimage_1-71.png)

Quando você adiciona um componente ao componente de Direcionamento, ele fornece conteúdo para uma experiência específica. Para especificar a experiência, selecione a experiência antes de adicionar os componentes.

Você pode adicionar um componente de Direcionamento à página no modo de Edição ou no modo de Direcionamento. Você pode adicionar componentes ao componente de Direcionamento somente no modo de Direcionamento. O componente de Direcionamento pertence ao grupo de componentes Personalização .

Se estiver editando o conteúdo direcionado, clique ou toque em **Iniciar o direcionamento **antes de fazer isso.

1. Arraste o componente de Direcionamento para a página onde deseja que a oferta apareça.
1. Por padrão, nenhuma ID de localização é definida. Clique ou toque no ícone de engrenagem de configuração para definir o local.

   >[!NOTE]
   >
   >Se definido pelo administrador, talvez seja necessário definir explicitamente a localização.
   >
   >Os administradores podem decidir se essa configuração é obrigatória em **https://&lt;host>:&lt;port>/system/console/configMgr/com.day.cq.personalization.impl.servlets.TargetingConfigurationServlet**
   Para exigir que os usuários insiram um local, marque a caixa de seleção **Forçar local**.

1. Selecione a experiência para a qual deseja criar a oferta.
1. Crie a oferta:

   * Para a experiência padrão, arraste os componentes para área de destino e edite suas propriedades como de costume para criar o conteúdo da oferta.
   * Para experiências não padrão, [adicionar uma oferta personalizada](#adding-a-custom-offer) ou [adicionar uma oferta de biblioteca](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library).

#### Adicionar uma oferta personalizada {#adding-a-custom-offer}

Crie uma oferta criando o conteúdo de um componente direcionado no modo de Direcionamento. Ao criar uma oferta personalizada, ela é usada como a oferta para uma única experiência.

Se decidir que a oferta pode ser usada para outras experiências, poderá criar uma oferta personalizada e [adicioná-la à biblioteca](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library). Para obter informações sobre como usar o console Ofertas para criar uma oferta reutilizável, consulte [Adicionar uma oferta a uma biblioteca de ofertas](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library).

1. Selecione a experiência à qual você está adicionando a oferta.
1. Para exibir o menu de componentes, clique ou toque no componente direcionado ao qual você está adicionando a oferta.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Clique ou toque no ícone + .

   O conteúdo da oferta Padrão é usado como a oferta para a experiência atual.

1. Clique ou toque na oferta para exibir o menu da oferta e, em seguida, clique ou toque no ícone de edição.

   ![](do-not-localize/chlimage_1-2.png)

1. Edite o conteúdo do componente.

#### Adicionar uma oferta de uma biblioteca de ofertas {#adding-an-offer-from-an-offer-library}

Adicione uma oferta da [biblioteca de ofertas](/help/sites-authoring/offerlib.md) a uma experiência. É possível adicionar qualquer oferta da biblioteca da marca que você está direcionando.

Não é possível adicionar ofertas de biblioteca à experiência padrão.

1. Selecione a experiência à qual você está adicionando a oferta.
1. Para exibir o menu de componentes, clique ou toque no componente direcionado ao qual você está adicionando a oferta.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Clique ou toque no ícone de pasta.

   ![](do-not-localize/chlimage_1-3.png)

1. Selecione a oferta da biblioteca e clique ou toque no ícone de marca de seleção.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   O seletor de ofertas permite procurar ou filtrar ofertas. Ao navegar ou filtrar, você também pode desejar classificar as ofertas e alterar como visualizá-las. O número no canto superior direito indica quantas ofertas estão disponíveis na biblioteca atual.

   * Clique ou toque em **Procurar** para navegar para outra pasta. O painel de navegação é aberto e você clica na seta para mostrar o detalhamento das pastas. Clique ou toque novamente em **Procurar** para fechar o painel de navegação.

   ![chlimage_1-75](assets/chlimage_1-75.png)

   * Clique ou toque em **Filtro** para filtrar as ofertas com palavras-chave ou tags. Você digita palavras-chave e seleciona tags no menu suspenso. Clique ou toque em **Filtro** novamente para fechar o painel de filtragem.

   ![chlimage_1-76](assets/chlimage_1-76.png)

   * Altere a forma como você classifica as ofertas clicando ou tocando na seta ao lado de **Do mais novo ao mais antigo**. As ofertas podem ser ordenadas da mais recente para a mais antiga ou da mais antiga para a mais recente.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   Clique ou toque no ícone ao lado de **Exibir como** para exibir as ofertas como mosaicos ou como uma lista.

   ![chlimage_1-78](assets/chlimage_1-78.png)

#### Adicionar uma oferta personalizada a uma biblioteca {#adding-a-custom-offer-to-a-library}

Adicione uma oferta personalizada à [biblioteca de ofertas](/help/sites-authoring/offerlib.md) quando quiser reutilizá-la como oferta para várias experiências. É possível adicionar ofertas à biblioteca da marca atual que você está direcionando.

Para obter informações sobre como usar o console Ofertas para criar uma oferta reutilizável, consulte [Adicionar uma oferta a uma biblioteca de ofertas](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library).

1. Selecione a experiência para revelar a oferta personalizada.
1. Clique ou toque na oferta personalizada para exibir o menu da oferta e, em seguida, clique ou toque no **Salvar oferta na biblioteca de ofertas** ícone .

   ![](do-not-localize/chlimage_1-4.png)

1. Digite um nome para a oferta e selecione a biblioteca à qual você está adicionando a oferta, em seguida, clique ou toque no ícone de marca de seleção.

#### Conversão de uma oferta de biblioteca para uma biblioteca personalizada {#converting-a-library-offer-to-a-custom-library}

Converta uma oferta de biblioteca em uma oferta personalizada para alterar a oferta para a experiência atual e sem alterar a oferta em outras experiências.

1. Selecione a experiência para revelar a oferta da biblioteca.
1. Clique ou toque na oferta da biblioteca para exibir o menu da oferta e, em seguida, clique ou toque no ícone Converter para oferta em linha .

   ![](do-not-localize/chlimage_1-5.png)

#### Editar uma oferta da biblioteca {#editing-a-library-offer}

Abra uma oferta de biblioteca de uma experiência no modo Direcionado para editar a oferta. As alterações feitas aparecem em todas as experiências que usam a oferta.

1. Selecione a experiência para revelar a oferta da biblioteca.
1. Converta a oferta da biblioteca em uma oferta local/personalizada. Consulte [Converter uma oferta de biblioteca a uma biblioteca personalizada](#converting-a-library-offer-to-a-custom-library).
1. Edite o conteúdo da oferta.

1. Salve na biblioteca. Consulte [Adicionar uma oferta personalizada a uma biblioteca](#adding-a-custom-offer-to-a-library).

## Target: Configuração dos públicos-alvo {#target-configuring-the-audiences}

A etapa do Target de [processo de direcionamento](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) envolve o mapeamento de públicos-alvo com as experiências com as quais você trabalhou na etapa Criar . A página do Target mostra os públicos-alvo que cada experiência está direcionando. Você pode especificar ou alterar o público-alvo de cada experiência. Se você estiver usando o Adobe Target, também poderá criar testes A/B que permitem direcionar a porcentagem do tráfego de um público-alvo para uma experiência específica.

### Se estiver usando o direcionamento do AEM ou o Adobe Target (direcionamento de experiência) ... {#if-you-are-using-aem-targeting-or-adobe-target-experience-targeting}

Os públicos são exibidos no lado esquerdo do diagrama de mapeamento e as experiências, no lado direito.

![chlimage_1-79](assets/chlimage_1-79.png)

Defina um público usando um segmento. A configuração da nuvem para a página determina os segmentos que estão disponíveis para você. Quando a página não está associada a uma configuração de nuvem do Adobe Target, AEM segmentos ficam disponíveis para definir públicos. Quando a página é associada a uma configuração de nuvem do Adobe Target, você usa os segmentos do Target .

Para obter informações sobre mecanismos de direcionamento, consulte [Mecanismo de direcionamento](/help/sites-authoring/personalization.md#targeting-engine).

Um público-alvo não deve ser usado por mais de uma experiência. Um símbolo de aviso é exibido ao lado de uma experiência quando ela é mapeada para um público-alvo mapeado para outra experiência.

![](do-not-localize/chlimage_1-6.png)

### Associar experiências com públicos-alvo (AEM ou Adobe Target) {#associating-experiences-with-audiences-aem-or-adobe-target}

Use o procedimento a seguir para associar uma experiência a um público-alvo ao usar o direcionamento AEM (ou o direcionamento de experiência do Adobe Target):

1. Clique ou toque na seta suspensa ao lado da caixa do público-alvo que está mapeada para a experiência.
1. (Opcional) Clique ou toque em **Editar** e digite uma palavra-chave para pesquisar pelo segmento desejado.
1. Na lista de públicos, selecione o público e clique ou toque em **OK**.

### Se estiver usando o Teste A/B (Adobe Target) ... {#if-you-are-using-a-b-testing-adobe-target}

Se você tiver uma atividade de teste A/B, os públicos-alvo estarão à esquerda, a porcentagem de exibição de cada experiência estará no meio e as experiências estarão à direita.

É possível alterar as porcentagens, desde que somem até 100%. Um público-alvo pode ser usado por várias experiências em testes A/B.

![chlimage_1-80](assets/chlimage_1-80.png)

### Associar públicos-alvo e porcentagens de tráfego ao teste A/B {#associating-audiences-and-traffic-percentages-with-a-b-testing}

1. Clique ou toque na caixa suspensa ao lado do público-alvo mapeado para a experiência.
1. (Opcional) Clique em **Editar** em seguida, digite uma palavra-chave para procurar pelo segmento desejado.
1. Clique ou toque em **OK.**
1. Insira as porcentagens para configurar como o tráfego de público-alvo é roteado para cada experiência. O número total deve ser igual a 100.
1. (Opcional) Edite o nome da experiência clicando no menu suspenso ao lado do nome da experiência.

## Metas e configurações: Configuração da atividade e da definição de metas {#goals-settings-configuring-the-activity-and-setting-goals}

A etapa Metas e configurações do [processo de direcionamento](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) envolve a configuração do comportamento da atividade da marca. Especifique quando a atividade começa e termina, bem como a prioridade da atividade. Além disso, você também rastreia metas. Especificamente, é possível decidir o que deseja medir com suas atividades.

Métricas de meta só estarão disponíveis se você usar o Adobe Target para seu mecanismo de direcionamento. Você deve definir pelo menos uma métrica de meta. Se você tiver o Adobe Analytics configurado e uma configuração de nuvem A4T do Analytics, poderá selecionar se deseja que a fonte de relatórios seja Adobe Target ou Adobe Analytics.

As métricas de meta são medidas apenas para a campanha publicada.

Se estiver usando AEM como mecanismo de direcionamento:

![chlimage_1-81](assets/chlimage_1-81.png)

Se estiver usando o Adobe Target como mecanismo de direcionamento:

![chlimage_1-82](assets/chlimage_1-82.png)

Se estiver usando o Adobe Target como mecanismo de direcionamento e tiver o A4T Analytics configurado para a conta, terá um menu suspenso **Fonte de relatórios** adicional:

![chlimage_1-83](assets/chlimage_1-83.png)

As seguintes métricas de sucesso estão disponíveis (usadas somente para publicação):

<table> 
 <tbody> 
  <tr> 
   <td><strong>Conversão</strong></td> 
   <td><p>A porcentagem de visitantes que clicaram em qualquer parte da experiência que está sendo testada. Uma conversão pode ser contada uma vez por visitante ou cada vez que um visitante conclui uma conversão. A métrica de conversão é definida como uma das seguintes opções:</p> 
    <ul> 
     <li><strong>Visualizada uma página</strong> - Você pode definir a página visualizada pelo público-alvo selecionando <strong>O URL é</strong> e definindo o URL ou vários URLs, ou selecionando <strong>URL contém</strong> e, em seguida, adicionar um caminho ou palavra-chave.</li> 
     <li><strong>Visualizada uma mbox</strong> - Você pode definir a mbox visualizada pelo seu público inserindo o nome da mbox. Você pode inserir várias mboxes clicando em <strong>Adicionar uma mbox</strong>.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Receita</strong></td> 
   <td><p>Receita gerada pela visita. Você pode escolher entre as seguintes métricas de receita:</p> 
    <ul> 
     <li>Receita por visitante (RPV)</li> 
     <li>Valor médio de pedido (AOV)</li> 
     <li>Total de vendas </li> 
     <li>Pedidos</li> 
    </ul> <p>Para qualquer uma dessas opções, a visualização de uma mbox indica que a meta foi atingida. É possível definir a mbox ou várias mboxes.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Envolvimento</strong></td> 
   <td><p>Você pode medir três tipos de envolvimento:</p> 
    <ul> 
     <li>Exibições da página</li> 
     <li>Marcação personalizada</li> 
     <li>Horário no site</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Além disso, há configurações avançadas que permitem determinar como contar métricas de sucesso. As opções incluem a contagem da métrica por impressão ou uma vez por visitante e a escolha entre manter o usuário na atividade ou removê-lo.

Use as configurações avançadas para determinar o que acontece **after** um usuário encontra a métrica de meta. A tabela a seguir mostra as opções disponíveis.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Após um usuário encontrar essa métrica de meta...</strong></td> 
   <td><strong>Você seleciona o seguinte para acontecer...</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Incrementar contagem e manter usuário em atividade</strong></td> 
   <td>Especifique como a contagem é incrementada: 
    <ul> 
     <li>Uma vez por participante</li> 
     <li>Em todas as impressões, excluindo atualizações de página</li> 
     <li>Em todas as impressões</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Incrementar contagem, liberar usuário e permitir reentrada</strong></td> 
   <td>Selecione a experiência que o visitante vê ao entrar na atividade novamente: 
    <ul> 
     <li>Mesma experiência</li> 
     <li>Experiência aleatória</li> 
     <li>Experiência não vista</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Aumentar Contagem, Liberar Usuário e Reentrada de Barra</strong></td> 
   <td>Determine o que o usuário vê em vez do conteúdo da atividade: 
    <ul> 
     <li>Mesma experiência, sem rastreamento</li> 
     <li>Conteúdo padrão ou outro conteúdo de atividade</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Consulte [Documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html?lang=pt-BR) para obter mais informações sobre métricas de sucesso.

### Definição das configurações (direcionamento AEM) {#configuring-settings-aem-targeting}

Para definir as configurações usando o direcionamento AEM:

1. Para especificar quando a atividade começa, use o **Iniciar** menu suspenso para selecionar um dos seguintes valores:

   * **Quando ativado**: A atividade começa quando a página que contém o conteúdo direcionado é ativada.
   * **Data e hora especificadas**: Um horário específico. Ao selecionar essa opção, clique ou toque no ícone de calendário, selecione uma data e especifique a hora para iniciar a atividade.

1. Para especificar quando a atividade termina, use o **End** menu suspenso para selecionar um dos seguintes valores:

   * **Quando desativado**: A atividade termina quando a página que contém o conteúdo direcionado é desativada.
   * **Data e hora especificadas**: Um horário específico. Ao selecionar essa opção, clique ou toque no ícone de calendário, selecione uma data e especifique a hora para terminar a atividade.

1. Para especificar uma prioridade para a atividade, use o controle deslizante para selecionar **Baixo**, **Normal** ou **Alto**.

### Definição de metas e configurações (Adobe Target) {#configuring-goals-settings-adobe-target}

Para definir metas e configurações se estiver usando o Adobe Target:

1. Para especificar quando a atividade começa, use o **Iniciar** menu suspenso para selecionar um dos seguintes valores:

   * **Quando ativado**: A atividade começa quando a página que contém o conteúdo direcionado é ativada.
   * **Data e hora especificadas**: Um horário específico. Ao selecionar essa opção, clique ou toque no ícone de calendário, selecione uma data e especifique a hora para iniciar a atividade.

1. Para especificar quando a atividade termina, use o **End** menu suspenso para selecionar um dos seguintes valores:

   * **Quando desativado**: A atividade termina quando a página que contém o conteúdo direcionado é desativada.
   * **Data e hora especificadas**: Um horário específico. Ao selecionar essa opção, clique ou toque no ícone de calendário, selecione uma data e especifique a hora para terminar a atividade.

1. Para especificar uma prioridade para a atividade, use o controle deslizante para selecionar **Baixo**, **Normal** ou **Alto**.
1. Se tiver configurado o Adobe Analytics com sua conta Adobe Target, você verá a variável **Fonte de geração de relatórios** menu suspenso. Selecione **Adobe Target** ou **Adobe Analytics** como a fonte.

   Se você selecionar **Adobe Analytics**, selecione a empresa e o conjunto de relatórios. Se você selecionar **Adobe Target**, nenhuma ação é necessária.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Na área **Métrica de meta**, em **Meu objetivo principal**, selecione a métrica de sucesso que deseja rastrear - Conversão, Receita, Participação - e insira como essa métrica é medida (ou que ação o público-alvo executa para indicar que um objetivo foi atingido). Consulte a definição das métricas de objetivo na tabela anterior e consulte a [documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html?lang=pt-BR) sobre métricas de sucesso.

   Você pode renomear a meta ao clicar nos três pontos no canto superior direito e selecionar **Renomear**.

   Se precisar limpar todos os campos, clique nos três pontos no canto superior direito e selecione **Limpar todos os campos**.

   Todas as métricas também têm configurações avançadas que você pode definir. Selecionar **Configurações avançadas** para acessá-los. Consulte a definição de como as métricas de sucesso são contadas na tabela anterior, bem como a [documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html?lang=pt-BR).

   >[!NOTE]
   Você deve ter, pelo menos, uma meta definida.

   ![chlimage_1-85](assets/chlimage_1-85.png)

   >[!NOTE]
   Se houver informações ausentes em sua métrica, uma linha vermelha circulará a métrica.

1. Clique em **Adicionar uma nova métrica** para configurar métricas de sucesso adicionais.

   ![chlimage_1-86](assets/chlimage_1-86.png)

   >[!NOTE]
   Você pode remover metas adicionais clicando ou tocando nos três pontos e clicando ou tocando em **Excluir**. AEM exige que você tenha pelo menos uma meta definida.

1. Se quiser ter mais controle sobre como as métricas de sucesso são contadas, clique ou toque em **Configurações avançadas** para acessá-las.
1. Clique em **Salvar**.

Após configurar, você pode [visualizar o desempenho de suas atividades](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test) que usam o Adobe Target (direcionamento de experiência ou teste A/B). Além disso, com o direcionamento do teste A/B, é possível [converter os vencedores.](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test)

## Simulação de uma experiência {#simulating-an-experience}

Simule a experiência de um visitante para verificar se o conteúdo da página aparece como esperado de acordo com o design do conteúdo direcionado. Ao simular, carregue diferentes perfis de usuário e veja o conteúdo direcionado para esse usuário.

Os critérios a seguir determinam o conteúdo que aparece ao simular a experiência de um visitante:

* Os dados no armazenamento de sessão do usuário (via Context Hub).
* O [Atividades ativadas](/help/sites-authoring/activitylib.md).
* O [regras que definem os segmentos](/help/sites-administering/campaign-segmentation.md).
* O conteúdo das experiências nos componentes do Target.
* O [configuração do mecanismo de direcionamento](/help/sites-authoring/activitylib.md).

Se um conteúdo inesperado for exibido na página ao carregar um perfil, verifique a configuração de cada item nesta lista.

>[!NOTE]
Se você estiver usando testes A/B, ao simular experiências será exibido com base na porcentagem de tráfego. Isso é controlado pelo Adobe Target, o que pode levar a resultados inesperados para os autores. (A atividade _author é sincronizada com configurações específicas que permitem reavaliação durante a simulação.) Os autores podem precisar atualizar para ver as outras experiências com base em suas configurações de tráfego.

Para simular a experiência do visitante, use as seguintes ferramentas:

* A atividade de simulação no modo de Direcionamento: A página exibe as ofertas para o usuário que está atualmente selecionado no Context Hub. É possível editar as ofertas que direcionam o usuário.
* Modo de visualização: Use o Context Hub para selecionar os usuários e locais que atendem aos critérios dos segmentos em que suas experiências se baseiam. Quando suas seleções do Context Hub mudam, o conteúdo direcionado muda de acordo.

1. Para alternar para o modo de Visualização, clique ou toque em **Visualização** na barra de ferramentas.
1. Na barra de ferramentas, clique ou toque no ícone do Context Hub.

   ![](do-not-localize/chlimage_1-7.png)

1. Use o Context Hub para alterar as propriedades do contexto. Por exemplo, clique ou toque na propriedade Persona para selecionar um usuário diferente.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   A página muda para mostrar o conteúdo direcionado para o contexto atual.

1. Para fazer alterações nas ofertas exibidas, alterne para o modo de Direcionamento. Com a atividade de simulação selecionada, edite as ofertas para o contexto que você configurou no modo de Visualização.

## Configuração das opções do componente de destino {#configuring-target-component-options}

Você pode personalizar o componente de Direcionamento acessando as opções do componente de uma das duas formas a seguir:

1. Depois de direcionar o componente, no componente de Direcionamento, clique ou toque no componente e no ícone de configurações (engrenagem).

   ![](do-not-localize/chlimage_1-8.png)

   O AEM exibe a janela de opções do componente de Direcionamento.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Como alternativa, para acessar essas configurações no modo de tela cheia, na janela de opções do componente de Direcionamento, clique ou toque no ícone de tela cheia.

   ![](do-not-localize/chlimage_1-9.png)

   O AEM exibe a janela de opções do componente de Direcionamento em tela cheia.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Defina as configurações do componente de Direcionamento conforme descrito nas tabelas a seguir.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Local</strong></td> 
   <td><p>O local é uma sequência de caracteres que dá um nome ao local do conteúdo direcionado e conecta ofertas a lugares (ou locais ou componentes) na página onde essas ofertas devem ser colocadas.</p> <p>Este campo é um valor genérico.</p> <p>Se você adicionar uma oferta a um componente, ela se lembrará da ID de localização. Quando a página é executada, o mecanismo avalia os segmentos do usuário e, com base nisso, resolve as experiências das campanhas ativas que devem ser exibidas. Em seguida, ele verifica as IDs de localização na página e tenta corresponder as ofertas com essas IDs de localização a elas.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Mecanismo</strong></td> 
   <td>Selecionar entre <strong>Regras do lado do cliente (sem rastreamento), Adobe Target, ContextHub, </strong>e<strong> Adobe Campaign </strong>dependendo do mecanismo que deseja usar.</td> 
  </tr> 
 </tbody> 
</table>

Se você selecionar Adobe Target como mecanismo:

![chlimage_1-90](assets/chlimage_1-90.png)

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Destinação exata</strong></td> 
   <td><p>Habilitar o direcionamento preciso informa ao componente para esperar que os dados do contexto do cliente ou do hub de contexto estejam disponíveis antes de enviar a solicitação para o Adobe Target. Pode aumentar o tempo de carregamento. Ao criar, o direcionamento preciso está sempre ativado.</p> <p>Se você selecionar a variável <strong>Direcionamento preciso</strong> , a mbox executa uma <code>mboxDefine</code> primeiro e um <code>mboxUpdate</code> posteriormente, resultando em uma solicitação do Ajax quando os dados estiverem disponíveis.</p> <p>Se você não selecionar a opção <strong>Direcionamento preciso</strong> , a mbox executa uma <code>mboxCreate</code> resultando em uma solicitação síncrona imediatamente (nesse caso, nem todos os dados de contexto podem estar disponíveis ainda).</p> <p><strong>Observação:</strong> Ativar ou desativar o direcionamento preciso em um componente específico não afeta as configurações definidas globalmente. Sempre é possível substituir as configurações globais selecionando Direcionamento preciso no componente.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Incluir segmentos resolvidos</strong></td> 
   <td><p>Selecionar essa caixa de seleção inclui todos os segmentos resolvidos na chamada da mbox e quaisquer parâmetros configurados na página e na estrutura.</p> <p>Somente funciona em situações com a API XML na qual você está sincronizando os segmentos do AEM. Se tiver segmentos no AEM que não são manipulados pelo Adobe Target (como segmentos de script), essa opção permite resolver o segmento no AEM e enviar informações para o Adobe Target de que o segmento está ativo.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Parâmetros herdados de contexto</strong></td> 
   <td>Lista os parâmetros de contexto herdados da estrutura do Adobe Target, se houver, associados à página selecionada.</td> 
  </tr> 
  <tr> 
   <td><strong>Parâmetros de contexto</strong></td> 
   <td>Clique ou toque em <strong>Adicionar campo</strong> para configurar parâmetros de contexto adicionais (o mesmo que está disponível na estrutura do Target). Parâmetros de contexto adicionados ao componente são aplicados <i>only</i> ao componente e não a outro componente, como ocorre ao adicionar parâmetros de contexto diretamente à estrutura.</td> 
  </tr> 
  <tr> 
   <td><strong>Parâmetros estáticos</strong></td> 
   <td>Clique ou toque em <strong>Adicionar campo</strong> para configurar parâmetros estáticos adicionais (o mesmo que está disponível na estrutura do Target). Os parâmetros estáticos adicionados ao componente se aplicam <i>only</i> ao componente e não a outro componente, como ocorre ao adicionar parâmetros estáticos diretamente à estrutura. Os parâmetros estáticos não provêm do contexto (contexto do cliente do content hub).</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
Quando você seleciona um componente e o torna passível de direcionamento, o AEM também substitui o componente e injeta um componente do Adobe Target. (O componente Adobe Target não é usado apenas quando você o adiciona manualmente à página, mas também quando você direciona um componente existente.)

Se você selecionar Contexto do Cliente (lado do cliente) como mecanismo:

![chlimage_1-91](assets/chlimage_1-91.png)

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opção</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Opções para o lado do cliente - Estratégia</strong></td> 
   <td><p>Selecione uma das opções a seguir:</p> 
    <ul> 
     <li><strong>First</strong>: A experiência mais alta na lista, conforme solicitado na campanha.</li> 
     <li><strong>Random</strong>: Qualquer experiência é usada.</li> 
     <li><strong>Pontuação da sequência de cliques</strong>: As tags e as ocorrências de tag relacionadas que são rastreadas no contexto do cliente são usadas. As taxas de ocorrência de tags definidas na página de teaser são comparadas.</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Selecione **Adobe Campaign** como mecanismo se estiver integrando o AEM com o Adobe Campaign. Consulte [Integração do AEM com o Adobe Campaign](/help/sites-administering/campaign.md) para obter mais informações.

Selecione **ContextHub** como mecanismo se estiver usando o ContextHub para o direcionamento. Consulte [Configuração do ContextHub.](/help/sites-administering/contexthub-config.md)
