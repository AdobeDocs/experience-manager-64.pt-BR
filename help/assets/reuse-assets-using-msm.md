---
title: Reutilizar ativos usando o MSM para ativos
description: Use ativos em várias páginas/pastas que são derivadas e vinculadas a ativos pai. Os ativos permanecem sincronizados com uma cópia principal e, com alguns cliques, recebem as atualizações dos ativos principais.
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '3158'
ht-degree: 9%

---


# Reutilizar ativos usando o MSM para ativos {#reuse-assets-using-msm-for-assets}

A funcionalidade Multi Site Manager (MSM) no Adobe Experience Manager (AEM) permite que os usuários reutilizem o conteúdo criado uma vez e reutilizado em vários locais da Web. O mesmo está disponível para ativos digitais que a funcionalidade MSM para ativos. Usando o MSM para ativos, é possível:

* Crie ativos uma vez e faça cópias desses ativos para reutilizá-los em outras áreas do site.
* Mantenha várias cópias sincronizadas e atualize a cópia primária original uma vez para enviar as alterações para as cópias secundárias.
* Faça alterações locais suspendendo temporária ou permanentemente a vinculação entre ativos pai e filho.

## Pré-requisitos {#msm-prerequisites}

Para usar o MSM para os Ativos, instale pelo menos o Service Pack 5. Para obter mais informações, consulte as notas de versão.
[notas](/help/release-notes/assets.md)de versão.

## Entenda os benefícios e os conceitos {#understand-benefits-concepts}

### Como funciona e benefícios {#how-it-works-the-benefits}

Para entender os cenários de uso para reutilizar o mesmo conteúdo (texto e ativos) em vários locais da Web, consulte [possíveis cenários](/help/sites-administering/msm.md#possible-scenarios)MSM. AEM mantém um link entre o ativo original e suas cópias vinculadas, chamadas de cópias ativas (LCs). A vinculação mantida permite que alterações centralizadas sejam enviadas para muitas cópias online. Isso permite atualizações mais rápidas, além de eliminar as limitações do gerenciamento de cópias de duplicados. A propagação das alterações é livre de erros e centralizada. A funcionalidade permite espaço para atualizações limitadas a cópias online selecionadas. Os usuários podem desanexar a vinculação, ou seja, interromper a herança, e fazer edições locais que não são substituídas quando a próxima vez que a cópia principal for atualizada e as alterações forem distribuídas. A desanexação pode ser feita para alguns campos de metadados selecionados ou para um ativo inteiro. Ele permite flexibilidade para atualizar localmente ativos que são originalmente herdados de uma cópia primária.

O MSM mantém uma relação ao vivo entre o ativo de origem e suas cópias ao vivo para que:

* As alterações nos ativos de origem também são aplicadas (distribuídas) às cópias online, ou seja, as cópias online são sincronizadas com a fonte.

* É possível atualizar as cópias online suspendendo a relação ao vivo ou removendo a herança de alguns campos limitados. As modificações na fonte não são mais aplicadas à cópia online.

### Glossário de termos de MSM para ativos {#glossary-msm-for-assets}

* **Fonte:** Os ativos ou pastas originais. Cópia principal da qual as cópias online são derivadas.

* **Live copy:** A cópia dos ativos/pastas de origem que está em sincronização com a origem. As cópias online podem ser uma fonte de outras cópias online. Consulte [como criar LCs](#create-live-copy-asset).

* **Herança:** Um link/referência entre um ativo/pasta de live copy e sua origem que o sistema usa para lembrar onde enviar as atualizações. A herança existe em um nível granular para campos de metadados. A herança pode ser removida para campos de metadados seletivos e, ao mesmo tempo, preservar a relação ao vivo entre a fonte e sua cópia ao vivo.

* **Implantação**: Uma ação que empurra as modificações feitas na fonte para downstream para suas cópias ativas. É possível atualizar uma ou mais cópias ao vivo de uma só vez usando a ação de implantação. Consulte [distribuição](#rollout-action).

* **Configuração de implantação:** Regras que determinam quais propriedades são sincronizadas, como e quando. Essas configurações são aplicadas ao criar cópias ao vivo; podem ser editados posteriormente; e um filho pode herdar a configuração de implantação de seu ativo pai. Para o MSM for Assets, use apenas a configuração de implantação Padrão. As outras configurações de implantação não estão disponíveis para o MSM for Assets.

* **Sincronizar:** Outra ação, além da implementação, que traz paridade entre a origem e sua live copy enviando as atualizações da origem para as live copies. Uma sincronização é iniciada para uma cópia ativa específica e a ação extrai as alterações da origem. Usar essa ação é possível para atualizar apenas uma das cópias ativas. Consulte [sincronizar ação](#about-synchronize-action).

* **Suspender:** Remova temporariamente a relação ao vivo entre uma live copy e sua pasta/ativo de origem. Você pode retomar a relação. Consulte [suspender ação](#suspend-and-resume-relationship).

* **Retomar:** Retome a relação ao vivo para que uma live copy seja novamente start recebendo as atualizações da fonte. Consulte [retomar ação](#suspend-and-resume-relationship).

* **Redefinir:** A ação de redefinição torna a live copy novamente uma réplica da origem, substituindo quaisquer alterações locais. Também remove cancelamentos de herança e redefine a herança em todos os campos de metadados. Para fazer modificações locais no futuro, você deve cancelar novamente a herança de campos específicos. Consulte modificações [locais no LC](#make-local-modifications-to-live-copy).

* **Desanexar:** Remova irrevogavelmente a relação ao vivo de um ativo/pasta de live copy. Depois de desanexar a ação, as cópias online nunca poderão receber atualizações da origem e ela deixará de ser uma cópia ativa. Consulte [remover relacionamento](#remove-live-relationship).

## Criar cópia online de um ativo {#create-live-copy-asset}

Para criar uma live copy de um ou mais ativos ou pastas de origem, siga um destes procedimentos:

* **Método 1**: Selecione os ativos de origem e clique em **[!UICONTROL Criar > Live Copy]** na barra de ferramentas na parte superior.
* **Método 2**: Em AEM interface do usuário, clique em **[!UICONTROL Criar > Live Copy]** no canto superior direito da interface.

Você pode criar cópias ao vivo de um ativo ou de uma pasta, uma de cada vez. Você pode criar cópias ao vivo que são derivadas de um ativo ou de uma pasta que seja uma cópia ao vivo.

Fragmentos de conteúdo (CFs) não são suportados no caso de uso. Ao tentar criar suas cópias online, os CFs são copiados como estão sem nenhum relacionamento. Os CFs copiados são um instantâneo no tempo e não são atualizados quando os CFs originais são atualizados.

Para criar cópias ao vivo usando o primeiro método, siga estas etapas:

1. Selecione os ativos ou pastas de origem. Na barra de ferramentas, clique em **[!UICONTROL Criar > Live Copy]**.
   ![Criar live copy a partir AEM interface](assets/lc_create1.png)
1. Selecione o ativo ou pasta de origem. Clique em **[!UICONTROL Avançar]**.
1. Forneça o título e o nome. Os ativos não têm filhos. Ao criar uma cópia ao vivo das pastas, você pode optar por incluir ou excluir filhos.
1. Selecione uma configuração de implantação. Clique em **[!UICONTROL Criar]**.

Para criar cópias ao vivo usando o segundo método, siga estas etapas:

1. Em AEM interface, no canto superior direito, clique em **[!UICONTROL Criar > Live Copy]**.
   ![Criar live copy a partir AEM interface](assets/lc_create2.png)
1. Selecione o ativo ou pasta de origem. Clique em **[!UICONTROL Avançar]**.
1. Selecione a pasta de destino. Clique em **[!UICONTROL Avançar]**.
1. Forneça o título e o nome. Os ativos não têm filhos. Ao criar uma cópia ao vivo das pastas, você pode optar por incluir ou excluir filhos.
1. Selecione uma configuração de implantação. Clique em **[!UICONTROL Criar]**.

>[!NOTE]
>
>Quando uma origem ou uma cópia ao vivo é movida, os relacionamentos são mantidos. Quando uma live copy é excluída, os relacionamentos são removidos.

## Visualização de várias propriedades e status de cópia de origem e live {#view-properties-statuses-source-and-lc}

Você pode visualização as informações e os status relacionados ao MSM de live copy, como relacionamento, sincronização, implantações e muito mais, das várias áreas da interface do usuário AEM. Os dois métodos a seguir funcionam para ativos e pastas:

* Selecione o ativo live copy e localize as informações em sua página **[!UICONTROL Propriedades]** .
* Selecione a pasta de origem e localize as informações detalhadas de cada live copy no **[!UICONTROL Live Copy Console]**.

>[!TIP]
>
>To check the status of a few separate live copies, use the first method that is see the **[!UICONTROL Properties]** page. To check statuses of many live copies, use the second method, that is, see **[!UICONTROL Relationship Status]** page.

### Informações e status de uma live copy {#information-status-of-one-lc}

Para verificar as informações e os status de um ativo de live copy ou de uma pasta, siga estas etapas.

1. Selecione um ativo de live copy ou uma pasta. Click **[!UICONTROL Properties]** from the toolbar. Como alternativa, use o atalho de teclado `p`.
1. Click **[!UICONTROL Live Copy]**. Você pode verificar o caminho da origem, o status da suspensão, o status da sincronização, a data da última implantação e o usuário que realizou a última implantação.
   ![Informações e status do Live Copy](assets/lc_folder_properties.png)
1. Você pode ativar ou desativar se os ativos filho pegarem a configuração da live copy emprestada.
1. Você pode escolher a opção para a live copy para herdar a configuração de implantação do pai ou alterar a configuração.

### Informações e status de todas as cópias online de uma pasta {#information-status-of-all-lcs-of-folder}

AEM fornece um console para verificar as estátuas de todas as cópias online de uma pasta de origem. Esse console exibe o status de todos os ativos filho.

1. Selecione uma pasta de origem. Click **[!UICONTROL Properties]** from the toolbar. Como alternativa, use o atalho de teclado `p`.
1. Clique em **[!UICONTROL Origem da Live Copy]**. Para abrir o console, clique em **[!UICONTROL Visão geral da Live Copy]**. Esse painel fornece um status de nível superior de todos os ativos secundários.
   ![Status de Visualização de cópias online no Console de Live Copy da origem](assets/lc_statuses.png)
1. Para exibir as informações detalhadas sobre cada ativo na pasta live copy, selecione um ativo e clique em **[!UICONTROL Status do relacionamento]** na barra de ferramentas.
   ![Informações e status detalhados de um ativo filho de uma live copy em uma pasta](assets/lc_relationship_status.png)

>[!TIP]
>
>Você pode ver rapidamente os status de cópias ao vivo de outras pastas sem precisar navegar muito. Basta alterar a pasta na lista pop-up na parte central superior da interface Visão geral **** da Live Copy.

### Ações rápidas do painel Referências para origem {#quick-actions-from-references-rail-for-source}

Para um ativo ou pasta de origem, você pode ver as seguintes informações e realizar as seguintes ações diretamente do painel Referências:

* Veja os caminhos das cópias online.
* Abra ou revele uma cópia ativa específica AEM interface do usuário.
* Sincronize as atualizações com uma cópia ativa específica.
* Suspenda a relação ou altere a configuração de implantação de uma cópia ativa específica.
* Acesse o console de visão geral do live copy.

Select the source asset or folder, open the left rail, and click **[!UICONTROL References]**. Como alternativa, selecione um ativo ou pasta e use o atalho de teclado `Alt + 4`.

![Ações e informações disponíveis no painel Referências para a fonte selecionada](assets/lc_referencerail_source.png)

Para obter uma cópia online específica, clique em **[!UICONTROL Editar Live Copy]** para suspender a relação ou alterar a configuração de implantação.

![Suspender relação ou alterar a configuração de implantação de uma cópia ativa específica](assets/lc_edit_referencerail.png)

### Ações rápidas do painel Referências para live copy {#quick-actions-from-references-rail-for-live-copy}

Para um ativo ou pasta live copy, você pode ver as seguintes informações e realizar as seguintes ações diretamente do painel Referências:

* Consulte o caminho de sua origem.
* Abra ou revele uma cópia ativa específica AEM interface do usuário.
* Implantar as atualizações.

Selecione um ativo ou uma pasta de live copy, abra o painel à esquerda e clique em **[!UICONTROL Referências]**. Como alternativa, selecione um ativo ou pasta e use o atalho de teclado `Alt + 4`.

![Ações disponíveis no painel Referências para a live copy selecionada](assets/lc_referencerail.png)

## Propagar modificações de cópias de origem para live {#propagate-modifications-from-source-to-live-copies}

Depois que uma fonte é modificada, as alterações podem ser propagadas para as cópias online usando uma ação de sincronização ou uma ação de implantação. Para entender a diferença entre as duas ações, consulte o [glossário](#glossary-msm-for-assets).

### Ação de implantação {#rollout-action}

Você pode iniciar uma ação de implantação a partir do ativo de origem e atualizar todas ou algumas cópias ao vivo selecionadas.

1. Selecione um ativo de live copy ou uma pasta. Click **[!UICONTROL Properties]** from the toolbar. Como alternativa, use o atalho de teclado `p`.
1. Clique em **[!UICONTROL Origem da Live Copy]**. Click **[!UICONTROL Rollout]** from the toolbar.
1. Selecione as cópias online que deseja atualizar. Clique em **[!UICONTROL Rollout]**.
1. Para implementar as atualizações feitas nos ativos filho, selecione Origem do **[!UICONTROL roll-out e Todos os filhos]**.
   ![Implantar as modificações da origem em algumas ou em todas as cópias online](assets/lc_rollout_page.png)

>[!NOTE]
>
>As modificações feitas em um ativo de origem são distribuídas somente para as cópias online diretamente relacionadas. Se uma live copy for derivada de outra live copy, as modificações não serão distribuídas para a live copy derivada.

Como alternativa, você pode iniciar uma ação de implantação no painel [!UICONTROL Referências] depois de selecionar uma cópia ativa específica. Para obter mais informações, consulte Ações [rápidas no painel Referências para cópia](#quick-actions-from-references-rail-for-live-copy)ativa. Neste método de implantação, somente a cópia ao vivo selecionada e, opcionalmente, seus filhos são atualizados.

![Implantar as modificações da origem na live copy selecionada](assets/lc_rollout_dialog.png)

### Sobre a ação de sincronização {#about-synchronize-action}

Uma ação de sincronização puxa as modificações de uma fonte somente para a live copy selecionada. A ação de sincronização respeita e mantém as modificações locais feitas após cancelar a herança. As modificações locais não são substituídas e a herança cancelada não é restabelecida. É possível iniciar uma ação de sincronização de três maneiras.

| Onde na interface AEM | Quando e por que usar | Como usar |
|---|---|---|
| [!UICONTROL Painel Referências] | Sincronize rapidamente quando você já tiver a fonte selecionada. | Consulte Ações [rápidas do painel Referências para origem](#quick-actions-from-references-rail-for-source) |
| Barra de ferramentas na página [!UICONTROL Propriedades] | Inicie uma sincronização quando você já tiver as propriedades de live copy abertas. | Consulte [Sincronizar uma live copy](#synchronize-live-copy) |
| [!UICONTROL Console Visão geral] do Live Copy | Sincronize rapidamente vários ativos (não necessariamente todos) quando a pasta de origem estiver selecionada ou o console Visão geral  da Live Copy já estiver aberto. A ação de sincronização é iniciada para um ativo de cada vez, mas é uma forma mais rápida de sincronizar vários ativos de uma só vez. | Consulte [Ações em muitos ativos em uma pasta live copy](#take-actions-on-many-assets-in-lcfolder) |

### Sincronizar uma live copy {#synchronize-live-copy}

Para iniciar uma ação de sincronização, abra a página **[!UICONTROL Propriedades]** de uma live copy, clique em **[!UICONTROL Live Copy]** e na ação desejada da barra de ferramentas.

Para saber os status e as informações relacionadas a uma ação de sincronização, consulte [Informações e status de todas as cópias online de uma pasta](#information-status-of-all-lcs-of-folder).

![A ação de sincronização puxa as alterações feitas na origem](assets/lc_sync.png)

>[!NOTE]
>
>Se a relação for suspensa, a ação de sincronização não estará disponível na barra de ferramentas. Embora a ação de sincronização esteja disponível no painel [!UICONTROL Referências] , as modificações não são propagadas mesmo depois de uma implementação com êxito.

## Suspender e retomar a relação {#suspend-and-resume-relationship}

Você pode suspender temporariamente a relação para impedir que uma cópia ativa receba modificações feitas no ativo ou pasta de origem. A relação também pode ser retomada para cópia ao vivo para start que recebe as modificações da fonte.

Para suspender ou retomar, abra a página **[!UICONTROL Propriedades]** de uma live copy, clique em **[!UICONTROL Live Copy]** e clique na ação desejada na barra de ferramentas.

Como alternativa, você pode suspender ou retomar rapidamente os relacionamentos de vários ativos em uma pasta de live copy a partir do console **[!UICONTROL Visão geral da Live Copy]**. Consulte [Realizar ações em muitos ativos nas pastas de live copy](#take-actions-on-many-assets-in-lcfolder).

## Fazer modificações locais em uma live copy {#make-local-modifications-to-live-copy}

Uma live copy é uma réplica da fonte original quando é criada. Os valores de metadados de uma live copy são herdados da fonte. Os campos de metadados mantêm a herança individualmente com os respectivos campos do ativo de origem.

Entretanto, você tem a flexibilidade de fazer modificações locais em uma live copy para alterar algumas propriedades selecionadas. Para fazer modificações locais, cancele a herança da propriedade desejada. Quando a herança de um ou mais campos de metadados é cancelada, o relacionamento em tampo real do ativo e a herança dos outros campos de metadados são mantidas. Qualquer sincronização ou implementação não substitui as modificações locais. Para isso, abra a página **[!UICONTROL Propriedades]** de um ativo de live copy, clique no ícone **[!UICONTROL Cancelar herança]** ao lado de um campo de metadados.

Você pode desfazer todas as modificações locais e reverter o ativo para o estado de sua origem. A ação de redefinição substitui irrevogavelmente e instantaneamente todas as modificações locais e restabelece a herança em todos os campos de metadados. Para reverter, na página **[!UICONTROL Propriedades]** de um ativo de live copy, clique em **[!UICONTROL Redefinir]** na barra de ferramentas.

![A ação Redefinir substitui as edições locais e traz a cópia online parcialmente com sua fonte](assets/lc_reset.png)

## Remover relação ao vivo {#remove-live-relationship}

Você pode remover completamente a relação entre uma fonte e uma cópia ao vivo usando a ação Desanexar. A live copy torna-se um ativo ou pasta independente depois de ser desanexada. É exibido como um novo ativo na interface AEM, imediatamente após a desanexação. Para desanexar uma live copy de sua origem, siga estas etapas.

1. Selecione um ativo ou pasta de cópia ativa. Click **[!UICONTROL Properties]** from the toolbar. Como alternativa, use o atalho de teclado p.
1. Click **[!UICONTROL Live Copy]**. Clique em **[!UICONTROL Desanexar]** na barra de ferramentas. Clique em **[!UICONTROL Desanexar]** na caixa de diálogo apresentada.
   ![A ação de desanexação remove completamente a relação entre a origem e a cópia ativa](assets/lc_detach.png)

>[!CAUTION]
>
>A relação é removida assim que você clica em [!UICONTROL Desanexar] da caixa de diálogo. Não é possível desfazer isso clicando em [!UICONTROL Cancelar] na página Propriedades.

Alternatively, you can quickly detach multiple assets in a live copy folder from the **[!UICONTROL Live Copy Overview]** console. Consulte [Realizar ações em muitos ativos nas pastas de live copy](#take-actions-on-many-assets-in-lcfolder).

## Execute ações em muitos ativos em uma pasta live copy {#take-actions-on-many-assets-in-lcfolder}

Se você tiver vários ativos em uma pasta live copy, iniciar ações em cada ativo pode ser tedioso. Você pode iniciar rapidamente as ações básicas em muitos ativos a partir do Console de Live Copy. Os métodos acima continuam a funcionar para ativos individuais.

1. Selecione uma pasta de origem. Click **[!UICONTROL Properties]** from the toolbar. Como alternativa, use o atalho de teclado p.
1. Clique em Origem da Live Copy. Para abrir o console, clique em **[!UICONTROL Visão geral da Live Copy]**.
1. Nesse painel, selecione um ativo de live copy de uma pasta live copy. Clique nas ações desejadas na barra de ferramentas. The actions available are **[!UICONTROL Edit]**, **[!UICONTROL Synchronize]**, **[!UICONTROL Reset]**, **[!UICONTROL Suspend]**, and **[!UICONTROL Detach]**. É possível iniciar rapidamente essas ações em qualquer ativo em qualquer número de pastas de live copy que estejam em um relacionamento ativo com a pasta de origem selecionada.
   ![Atualize facilmente muitos ativos em pastas de Live Copy do console Visão geral da Live Copy](assets/lc_console_update_assets.png)

## Estender MSM para ativos {#extend-msm-for-assets}

AEM permite estender a funcionalidade usando as APIs Java MSM. Para os Ativos, a extensão funciona exatamente como funciona com o MSM para o Site. Para obter detalhes, consulte [Extensão do MSM](../sites-developing/extending-msm.md) e as seguintes seções para obter informações sobre tarefas específicas:

* [Visão geral das APIs](../sites-developing/extending-msm.md#overview-of-the-java-api)
* [Criar uma nova ação de sincronização](../sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Criar uma nova configuração de implantação](../sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [Criar e usar uma classe simples do LiveActionFactory](../sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* O Blueprint no MSM for Site é chamado de Live Copy source in MSM for Assets.
>* A remoção da etapa de capítulos no assistente para criação de site não é compatível com o MSM for Assets.
>* A configuração de bloqueios MSM nas propriedades da página (interface habilitada para toque) não é suportada no MSM para Ativos.


## Impacto das tarefas de gerenciamento de ativos em cópias online {#impact-of-asset-management-tasks-on-live-copies}

As cópias online e as fontes são ativos ou pastas que podem ser gerenciados, até certo ponto, como ativos digitais. Algumas tarefas de gerenciamento de ativos em AEM têm um impacto específico nas cópias online.

* A cópia de uma live copy cria um ativo live copy com a mesma fonte da primeira live copy.
* Quando você move uma fonte ou sua cópia ao vivo, a relação ao vivo é mantida.
* A ação Editar não funciona para ativos de cópia ativa.
* A ação de check-out não está disponível para ativos de live copy.
* Para a pasta de origem, a opção para criar tarefas de revisão está disponível.
* Ao exibir a listagem de ativos na visualização de listas e na visualização de colunas, um ativo ou pasta de live copy exibirá &#39;live copy&#39; em relação a ele. Isso ajuda você a identificar facilmente cópias online em uma pasta.

## Comparar MSM para ativos e sites {#compare-msm-for-assets-and-sites}

Em mais cenários, o MSM for Assets corresponde ao comportamento da funcionalidade MSM for Sites. Algumas diferenças principais são:

* Em Sites, você pode comparar um blueprint e sua cópia online, mas não é possível no Assets comparar uma fonte à sua cópia online.
* Os sites geralmente têm filhos, mas os Ativos não. A opção para incluir ou excluir filhos não está presente ao criar cópias ao vivo de ativos individuais.
* A remoção da etapa de capítulos no assistente para criação de site não é compatível com o MSM for Assets.
* A configuração de bloqueios MSM nas propriedades da página (interface habilitada para toque) não é suportada no MSM para Ativos.
* Para o MSM for Assets, use apenas a configuração de implantação Padrão. As outras configurações de implantação não estão disponíveis para o MSM for Assets.

## Limitações do MSM para ativos {#limitations-of-msm-for-assets}

Veja a seguir a limitação com MSM para Ativos.

* Fragmentos de conteúdo (CFs) não são suportados no caso de uso. Ao tentar criar suas cópias online, os CFs são copiados como estão sem nenhum relacionamento. Os CFs copiados são um instantâneo no tempo e não são atualizados quando os CFs originais são atualizados.
