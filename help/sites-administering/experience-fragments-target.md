---
title: Integração de Públicos alvos com fragmentos de experiência
seo-title: Integração de Públicos alvos com fragmentos de experiência
description: Integração de Públicos alvos com fragmentos de experiência
seo-description: Integração de Públicos alvos com fragmentos de experiência
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# Integração de Públicos alvos com fragmentos de experiência{#target-integration-with-experience-fragments}

>[!NOTE]
>
>Essa funcionalidade exige a aplicação do [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) ou posterior.

Você pode exportar Fragmentos [de](/help/sites-authoring/experience-fragments.md)experiência criados no Adobe Experience Manager (AEM) para o Adobe Target. Eles podem ser usados como ofertas em atividades Públicos alvos, para testar e personalizar experiências em escala. Isso permite combinar a facilidade de uso e o poder do AEM, com os poderosos recursos de Inteligência automatizada (AI) e Aprendizagem de máquina (ML) no Público alvo.

## Pré-requisitos {#prerequisites}

Várias ações são obrigatórias:

1. Você tem que integrar AEM com o Público alvo. See [Integrating with Adobe Target](/help/sites-administering/target.md) for more information.
1. Os Fragmentos de experiência são exportados da instância do autor, portanto, é necessário [Configurar o Externalizador](/help/sites-developing/externalizer.md) de links na instância do autor para garantir que todos os links sejam externalizados para a instância de publicação.

## Adicionar a configuração da nuvem {#add-the-cloud-configuration}

Antes de exportar um fragmento, é necessário adicionar a Configuração **da** nuvem para **Adobe Target** ao fragmento ou pasta:

1. Navigate to the **Experience Fragments** console.
1. Abra Propriedades **da** página para a pasta ou fragmento apropriado.

   >[!NOTE]
   >
   >Se você adicionar a configuração de nuvem à pasta pai do Fragmento de experiência, a configuração será herdada por todos os filhos.
   >
   >Se você adicionar a configuração de nuvem ao próprio Fragmento de experiência, a configuração será herdada por todas as variações.

1. Selecione a guia **Cloud Services** .

1. Em Configuração **do** Cloud Service, selecione **Adobe Target** na lista suspensa.
1. Em **Adobe Target**, selecione a configuração apropriada.

1. **Salvar e fechar**.

## Exportação de um fragmento de experiência para o Público alvo {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Para ativos de mídia, como imagens, apenas uma referência é exportada para o Público alvo. O ativo em si permanece armazenado no AEM Assets e é entregue da instância de publicação AEM.
>
>Devido a isso, o Fragmento de experiência, com todos os ativos relacionados, precisa ser publicado antes de exportar para o Público alvo.

Para exportar um fragmento de experiência de AEM para Público alvo (depois de especificar a Configuração da nuvem):

1. Navegue até o console Fragmento de experiência.
1. Selecione o Fragmento de experiência que deseja exportar para o público alvo.

   >[!NOTE]
   >
   >Deve ser uma variação da Web do Fragmento de experiência.

1. Toque/clique em **Exportar para Adobe Target**.

   >[!NOTE]
   >
   >Se o Fragmento de experiência já tiver sido exportado, selecione **Atualizar no Adobe Target**.

1. Toque/clique em **Exportar sem publicar** ou **Publicar** , conforme necessário.

   >[!NOTE]
   >
   >Selecionar** Publicar** publicará o fragmento da experiência imediatamente e o enviará para o Público alvo.

1. Toque/clique em **OK** na caixa de diálogo de confirmação.

   Seu fragmento de experiência agora deve estar no Público alvo.

>[!NOTE]
>
>Como alternativa, você pode executar a exportação do editor de páginas, usando comandos comparáveis no menu Informações [da](/help/sites-authoring/author-environment-tools.md#page-information) página.

## Uso dos fragmentos de experiência no Público alvo {#using-your-experience-fragments-in-target}

Depois de executar as tarefas anteriores, o fragmento de experiência é exibido na página Ofertas no Público alvo. Consulte a documentação [](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) específica do Público alvo para saber mais sobre o que você pode alcançar.

## Excluindo um fragmento de experiência já exportado para o Público alvo {#deleting-an-experience-fragment-already-exported-to-target}

A exclusão de um fragmento de experiência que já foi exportado para o Público alvo pode causar problemas se o fragmento já estiver sendo usado em uma oferta no Público alvo. A exclusão do fragmento tornaria a oferta inutilizável, pois o conteúdo do fragmento está sendo entregue pela AEM.

Para evitar tais situações:

* Se o Fragmento de experiência não estiver sendo usado em uma atividade no momento, AEM permite que o usuário exclua o fragmento sem uma mensagem de aviso.
* Se o Fragmento de experiência estiver sendo usado por uma atividade no Público alvo, uma mensagem de erro avisará o usuário AEM sobre possíveis consequências que a exclusão do fragmento terá na atividade.

   A mensagem de erro no AEM não proíbe que o usuário (force-)exclua o Fragmento de experiência. Se o Fragmento de experiência for excluído:

   * A oferta do Público alvo com AEM Fragmento de experiência pode mostrar um comportamento indesejado

      * A oferta provavelmente ainda será renderizada, pois o HTML do fragmento de experiência foi enviado para o Público alvo
      * Qualquer referência no Fragmento de experiência pode não funcionar corretamente se os ativos referenciados também tiverem sido excluídos no AEM.
   * É claro, quaisquer modificações adicionais no Fragmento de experiência são impossíveis, pois o Fragmento de experiência não existe mais no AEM.


