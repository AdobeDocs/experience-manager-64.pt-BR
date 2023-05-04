---
title: Integração do Target com fragmentos de experiência
seo-title: Target Integration with Experience Fragments
description: Integração do Target com fragmentos de experiência
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 76%

---

# Integração do Target com fragmentos de experiência{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Essa funcionalidade requer a aplicação de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) ou posterior.

Você pode exportar [Fragmentos de experiência](/help/sites-authoring/experience-fragments.md), criado no Adobe Experience Manager (AEM), no Adobe Target. Eles podem ser usados como ofertas em atividades do Target, para testar e personalizar experiências em escala. Isso permite combinar a facilidade de uso e o poder do AEM, com os poderosos recursos de Inteligência automatizada (AI) e Aprendizagem de máquina (ML) no Target.

## Pré-requisitos {#prerequisites}

Várias ações são necessárias:

1. Você precisa integrar o AEM ao Target. Consulte [Integração com o Adobe Target](/help/sites-administering/target.md) para obter mais informações.
1. Fragmentos de experiência são exportados da instância do autor, portanto, é necessário [Configurar o Link Externalizer](/help/sites-developing/externalizer.md) na instância do autor para garantir que todos os links sejam externalizados para a instância de publicação.

## Adicionar a configuração da nuvem {#add-the-cloud-configuration}

Antes de exportar um fragmento, é necessário adicionar a **Configuração da nuvem** do **Adobe Target** ao fragmento ou pasta:

1. Navegue até o console **Fragmentos de experiência**.
1. Abra as **Propriedades de página** da pasta ou fragmento apropriado.

   >[!NOTE]
   >
   >Se você adicionar a configuração da nuvem à pasta principal do fragmento de experiência, a configuração será herdada pelas pastas secundárias.
   >
   >Se você adicionar a configuração da nuvem ao próprio fragmento de experiência, a configuração será herdada por todas as variações.

1. Selecione a guia **Cloud Services**.

1. Em **Configuração Cloud Service**, selecione **Adobe Target** na lista suspensa.
1. Em **Adobe Target**, selecione a configuração apropriada.

1. **Salvar e fechar**.

## Exportar um fragmento de experiência para o Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Para ativos de mídia, como imagens, somente uma referência é exportada para o Target. O ativo em si permanece armazenado no AEM Assets e é entregue a partir da instância de publicação do AEM.
>
>Devido a isso, o fragmento de experiência, com todos os ativos relacionados, precisa ser publicado antes da exportação para o Target.

Para exportar um fragmento de experiência do AEM para o Target (depois de especificar a configuração da nuvem):

1. Navegue até o console Fragmento de experiência.
1. Selecione o fragmento de experiência que deseja exportar para o Target.

   >[!NOTE]
   >
   >Ele deve ser uma variação web do fragmento de experiência.

1. Toque/clique em **Exportar para o Adobe Target**.

   >[!NOTE]
   >
   >Se o fragmento de experiência já tiver sido exportado, selecione **Atualizar no Adobe Target**.

1. Toque/clique em **Exportar sem publicar** ou em **Publicar**, conforme necessário.

   >[!NOTE]
   >
   >Selecionar** Publicar** publicará o fragmento de experiência imediatamente e o enviará para o Target.

1. Toque ou clique em **OK** na caixa de diálogo de confirmação.

   Seu fragmento de experiência agora deve estar no Target.

>[!NOTE]
>
>Como alternativa, você pode executar a exportação a partir do editor de páginas, usando comandos comparáveis no menu [Informações da página](/help/sites-authoring/author-environment-tools.md#page-information).

## Usar os fragmentos de experiência no Target {#using-your-experience-fragments-in-target}

Depois de executar as tarefas anteriores, o fragmento de experiência é exibido na página Ofertas do Target. Consulte a [documentação específica do Target](https://experiencecloud.adobe.com/resources/help/pt_BR/target/target/aem-experience-fragments.html) para saber mais sobre o que você pode realizar lá.

## Excluir um fragmento de experiência já exportado para o Target {#deleting-an-experience-fragment-already-exported-to-target}

Excluir um fragmento de experiência que já foi exportado para o Target pode causar problemas se o fragmento já estiver sendo usado em uma oferta no Target. A exclusão do fragmento tornaria a oferta inutilizável, pois o conteúdo do fragmento estaria sendo entregue pelo AEM.

Para evitar essas situações:

* Se o fragmento de experiência não estiver sendo usado atualmente em uma atividade, o AEM permite que o usuário exclua o fragmento sem mostrar uma mensagem de aviso.
* Se o Fragmento de experiência estiver sendo usado atualmente por uma atividade no Target, uma mensagem de erro avisará o usuário do AEM sobre as possíveis consequências que a exclusão do fragmento terá na atividade.

   A mensagem de erro no AEM não proíbe que o usuário exclua (à força) o fragmento de experiência. Se o fragmento de experiência for excluído:

   * A oferta do Target com o fragmento de experiência do AEM pode exibir um comportamento indesejado

      * A oferta provavelmente ainda será renderizada, pois o HTML do fragmento de experiência foi enviado para o Target
      * Qualquer referência no fragmento de experiência pode não funcionar corretamente se os ativos referenciados também tiverem sido excluídos no AEM.
   * É impossível realizar qualquer alteração adicional no fragmento de experiência, pois ele não existe mais no AEM.
