---
title: Alteração de ativo acionada por dados
seo-title: Alteração de ativo acionada por dados
description: Siga este exemplo de caso de uso para saber como obter conteúdo personalizado com base em alguma condição prévia (por exemplo, tempo de sua localização).
seo-description: Siga este exemplo de caso de uso para saber como obter conteúdo personalizado com base em alguma condição prévia (por exemplo, tempo de sua localização).
uuid: 8e557e4c-a6e2-4e4a-87bd-e01e2ff0043d
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: example
topic-tags: use-case-examples
discoiquuid: 878a2354-0990-4b21-b1ab-b9b33b50e353
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Alteração de ativo acionada por dados{#data-triggered-asset-change}

## Descrição do caso de uso {#use-case-description}

Este exemplo de caso de uso descreve como obter conteúdo personalizado com base no tempo de sua localização.

O projeto a seguir do AEM Screens aproveita a personalização do AEM, que inclui o ContextHub, o mecanismo de Segmentação e a interface de direcionamento de conteúdo.

Este caso de uso fornece conteúdo personalizado com base no tempo atual em cada local, se o tempo for:

* *ensolarado, exibe roupas de verão*
* *frio, exibe roupas de inverno*

>[!NOTE]
>
>Para fins de demonstração, este caso de uso captura a localização geográfica para mostrar a atualização do conteúdo. Você pode atualizar manualmente a exibição de Localização geográfica da saída em diferentes cenários.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de que entende:

* [Personalização](/help/sites-administering/personalization.md)
* [Configuração do ContextHub](/help/sites-administering/contexthub-config.md)
* [Configuração da segmentação com o ContextHub](/help/sites-administering/segmentation.md)
* [Criar conteúdo direcionado usando o modo de direcionamento](/help/sites-authoring/content-targeting-touch.md)

### Principais intervenientes {#primary-actors}

Autores de conteúdo

## Fluxo básico:Configuração do projeto {#basic-flow-setting-up-the-project}

Siga as etapas abaixo para configurar um projeto que mostre dados de alteração de ativos acionados:

1. Crie um projeto do AEM Screens chamado de **DataTriggerAsset**, conforme mostrado abaixo.

   ![screen_shot_2019-02-28at120427pm](assets/screen_shot_2019-02-28at120427pm.png)

1. **Criação de um canal de sequência**

   1. Selecione a pasta **Canais** e clique em **Criar** para abrir o assistente para criar um canal.
   1. Selecione Canal **de** sequência no assistente e crie o canal chamado **DataTrigger**.
   ![screen_shot_2019-02-28at120710pm](assets/screen_shot_2019-02-28at120710pm.png)

1. **Adicionar conteúdo ao canal de sequência**

   1. Selecione o canal **DataTrigger**.
   1. Clique em **Editar** na barra de ações para abrir o editor. Arraste e solte alguns ativos em seu canal.
   ![screen_shot_2019-02-28at21511pm](assets/screen_shot_2019-02-28at21511pm.png)

   >[!NOTE]
   >
   >É necessário adicionar somente as imagens padrão ao editor. As imagens que você deseja substituir devem ser adicionadas ao editor quando você alternar para o modo de definição de metas na etapa 6.

1. **Configuração do ContextHub e Configurações de definição de metas**

   1. Navegue até **DataTriggerAsset** —> **Channels** —> **DataTrigger** e clique em **Propriedades** na barra de ações.
   1. Clique na guia **Personalização** .
   ![screen_shot_2019-02-28at10644pm](assets/screen_shot_2019-02-28at10644pm.png)

1. **Adicionar configurações do ContextHub e de definição de metas**

   1. Para fins de demonstração, baixe o pacote de conteúdo abaixo.
   1. Depois de baixar o pacote para sua instância do AEM, é necessário definir o ContextHub e o Caminho dos segmentos:
   * Para o **ContextHub**, defina o caminho como: ***/libs/settings/cloudsettings/legado/contexthub***
   * Para Caminho **de** segmentos, defina o caminho como: ***/conf/acionadores de dados/configurações/wcm/segmentos***
   Acionadores de dados

   [Obter arquivo](assets/data-triggers-1_00.zip)

   >[!NOTE]
   >
   >Para saber mais sobre como configurar o ContextHub e a Segmentação, consulte:
   >
   >* [Configuração do ContextHub](/help/sites-administering/contexthub-config.md)
   >* [Configuração da segmentação com o ContextHub](/help/sites-administering/segmentation.md)


   ![screen_shot_2019-02-28at31502pm](assets/screen_shot_2019-02-28at31502pm.png)

   Clique em **Salvar e fechar**.

1. **Alternar para o modo de Direcionamento**

   1. Navegue até **DataTriggerAsset** > **Canais** > **DataTrigger** e clique em **Editar** na barra de ações.
   1. Selecione **Definição de metas** na barra de menus em **Editar**.
   ![screen_shot_2019-02-28at21849pm](assets/screen_shot_2019-02-28at21849pm.png)

1. **Adicionar o conteúdo direcionado**

   1. Selecione Acionadores **de** dados em **BRAND** e **Acionador de dados sazonais **em **ATIVIDADE**.
   1. Click the **Start Targeting**
   ![screen_shot_2019-02-28at31953pm](assets/screen_shot_2019-02-28at31953pm.png)

1. **Definição do componente direcionado**

   1. Selecione o componente para o qual deseja ter conteúdo direcionado.
   1. Clique no botão **Target** para ativar a definição de metas para esse componente.
   1. Defina o conteúdo para cada variação selecionando a variação nos **Públicos** no painel lateral e ajustando o conteúdo conforme necessário.
   >[!NOTE]
   >
   >Para ocultar o painel **Ativos** no editor, clique na seta para a esquerda no painel lateral direito, como mostra a figura abaixo.

   ![target](assets/target.gif)

## Exibição dos resultados {#viewing-the-results}

Depois de concluir as etapas anteriores, siga para visualizar e exibir os resultados:

1. Clique em **Visualizar** no editor.

   ![target2](assets/target2.gif)

1. Para mostrar como a imagem mudará, dependendo do local e da temperatura da área, clique manualmente no ícone do ContextHub, como mostrado abaixo.

   Assim que você atualizar o local, a temperatura dessa área será capturada e a imagem será atualizada com a seleção de inverno e substituirá a imagem de seleção de verão.

   ![target3](assets/target3.gif)

