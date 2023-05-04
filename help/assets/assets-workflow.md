---
title: Processar ativos para realizar processos de negócios, realizar auditorias, alcançar conformidade e manter a conformidade básica
description: Processamento de ativos para converter formatos, criar representações, gerenciar ativos, validar ativos e executar fluxos de trabalho.
contentOwner: AG
feature: Workflow,Renditions
role: User,Admin
exl-id: 4fb3d12c-feac-45b9-8d09-3b6995591b3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 3%

---

# Processar ativos digitais {#process-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] O permite trabalhar com os ativos digitais de várias maneiras para permitir um processamento de ativos robusto. Você pode usar os métodos de processamento disponíveis ou estender os métodos para garantir a conclusão completa do processo de negócios usando, auditorias e conformidade, detecção e distribuição de e a integridade básica de seus ativos digitais. Você pode fazer tudo isso, além de atingir a escala e a personalização necessárias.

## Entender workflows {#understand-workflows}

Para processamento de ativos, [!DNL Experience Manager] O usa workflows. Os fluxos de trabalho ajudam a automatizar a lógica ou as atividades de negócios. Etapas granulares para realizar tarefas específicas são fornecidas por padrão e os desenvolvedores podem criar suas próprias etapas personalizadas. Essas etapas podem ser combinadas em uma ordem lógica para criar workflows. Por exemplo, um fluxo de trabalho pode aplicar automaticamente uma marca d&#39;água em imagens carregadas com base em critérios específicos, como metadados incorporados na imagem, pasta na qual é carregado, resolução da imagem e assim por diante. Outro exemplo é um fluxo de trabalho configurado para marcar imagens de maneira semelhante e, ao mesmo tempo, endereçar várias necessidades de gerenciamento de ativos, como adicionar metadados, criar representações, adicionar tags inteligentes para descoberta de ativos, publicar em um armazenamento de dados, definir permissões para acesso do usuário e assim por diante.

## Fluxos de trabalho padrão disponíveis no Experience Manager {#default-workflows}

Por padrão, todos os ativos carregados são processados usando [!UICONTROL Ativo de atualização DAM] fluxo de trabalho. O fluxo de trabalho é executado para cada ativo carregado e realiza tarefas básicas de gerenciamento de ativos, como geração de representação, gravação de metadados, extração de página, extração de mídia e transcodificação.

Para ver os vários modelos de fluxo de trabalho disponíveis por padrão, consulte [!UICONTROL Ferramentas > Fluxo de trabalho > Modelos] em [!DNL Experience Manager].

![Alguns dos workflows padrão](assets/aem-default-workflows.png)

*Figura: Alguns dos workflows padrão estão disponíveis em [!DNL Experience Manager].*

## Aplicar fluxos de trabalho a ativos {#applying-workflows-to-assets}

Aplicar fluxos de trabalho a ativos digitais é o mesmo que aplicar a páginas do site. Para obter um guia completo sobre como criar e usar workflows, consulte [iniciar workflows](/help/sites-authoring/workflows-participating.md).

Use fluxos de trabalho em ativos digitais para ativar o ativo ou criar marcas d&#39;água. Muitos dos workflows de ativos são ativados automaticamente. Por exemplo, o fluxo de trabalho que cria uma representação automaticamente depois que uma imagem é editada é ativado automaticamente.

>[!NOTE]
>
>Se um fluxo de trabalho disponível na interface clássica não estiver disponível na interface habilitada para toque, como [!UICONTROL Solicitação para ativar] e [!UICONTROL Solicitação para desativar], consulte [criar modelos de fluxo de trabalho](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Aplicar um fluxo de trabalho a um [!DNL Experience Manager] ativo {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Para aplicar um fluxo de trabalho a um ativo, siga estas etapas:

1. Navegue até o local do ativo para o qual deseja iniciar um fluxo de trabalho e clique no ativo para abrir a página de ativo.

1. Navegue até o local do ativo para o qual deseja iniciar um fluxo de trabalho e clique no ativo para abrir a página de ativo. Selecionar **[!UICONTROL Linha do tempo]** no menu para exibir a linha do tempo.

   ![linha do tempo 2](assets/timeline-2.png)

1. Clique em **[!UICONTROL Ações]** na parte inferior para abrir a lista de ações disponíveis para o ativo.

1. Clique em **[!UICONTROL Iniciar fluxo de trabalho]** na lista.

1. No **[!UICONTROL Iniciar fluxo de trabalho]** selecione um modelo de fluxo de trabalho na lista.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Opcional) Especifique um título para o fluxo de trabalho, que pode ser usado para fazer referência à instância do fluxo de trabalho.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Clique em **[!UICONTROL Iniciar]**, depois clique em **[!UICONTROL Continue]** na caixa de diálogo para confirmar. Cada etapa do fluxo de trabalho é exibida na linha do tempo como um evento.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Aplicar um fluxo de trabalho a vários ativos {#applying-a-workflow-to-multiple-assets}

1. No console Assets, navegue até o local dos ativos para os quais deseja iniciar um fluxo de trabalho e selecione os ativos. Selecionar **[!UICONTROL Linha do tempo]** no menu para exibir a linha do tempo.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Clique no botão **[!UICONTROL Ações]** na parte inferior.

1. Clique em **[!UICONTROL Iniciar fluxo de trabalho]**. No **[!UICONTROL Iniciar fluxo de trabalho]** selecione um modelo de fluxo de trabalho na lista.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Opcional) Especifique um título para o fluxo de trabalho, que pode ser usado para fazer referência à instância do fluxo de trabalho.

1. Clique em **[!UICONTROL Iniciar]** e em **[!UICONTROL Confirmar]** na caixa de diálogo. O fluxo de trabalho é executado em todos os ativos selecionados.

## Aplicar um fluxo de trabalho a várias pastas {#applying-a-workflow-to-multiple-folders}

O procedimento para aplicar um fluxo de trabalho a várias pastas é semelhante ao procedimento para aplicar um fluxo de trabalho a vários ativos. Selecione as pastas no console Assets e execute as etapas 2 a 7 do procedimento [aplicar um fluxo de trabalho a vários ativos](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Aplicar um fluxo de trabalho a uma coleção {#applying-a-workflow-to-a-collection}

Para obter detalhes sobre como aplicar um fluxo de trabalho a uma coleção, consulte [aplicar um fluxo de trabalho a uma coleção](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Iniciar automaticamente um workflow para processar ativos condicionalmente {#auto-execute-workflow-on-some-assets}

Os administradores podem configurar o fluxo de trabalho para executar e processar ativos automaticamente com base em condições predefinidas. A funcionalidade é útil para usuários de linha de negócios e profissionais de marketing, por exemplo, para criar fluxo de trabalho personalizado em pastas específicas. Digamos que todos os ativos da sessão fotográfica de uma agência possam ter marca d&#39;água ou que todos os ativos carregados por um freelancer possam ser processados para criar representações específicas.

Para um modelo de fluxo de trabalho, os usuários podem criar um iniciador de fluxo de trabalho que o executa. Um iniciador de workflow monitora as alterações no repositório de conteúdo e executa o workflow quando as condições predefinidas são cumpridas. Os administradores podem fornecer acesso aos profissionais de marketing para criar os fluxos de trabalho e configurar o iniciador. Os usuários podem modificar o padrão [!UICONTROL Ativo de atualização DAM] para adicionar as etapas adicionais necessárias para processar ativos específicos. O workflow é executado em todos os ativos recém-carregados. Use uma das seguintes abordagens para limitar a execução das etapas adicionais em ativos específicos:

* Faça uma cópia do [!UICONTROL Ativo de atualização DAM] e modifique-o para ser executado em uma hierarquia de pasta específica. Essa abordagem é útil para algumas pastas.
* As etapas de processamento adicionais podem ser adicionadas usando um [OU divisão](/help/sites-developing/workflows-step-ref.md#or-split) como condicionalmente aplicável a quantas pastas forem necessárias.

## Práticas recomendadas e limitações {#best-practices-limitations-tips}

* Considere suas necessidades para todos os tipos de representações ao projetar fluxos de trabalho. Se você não prever a necessidade de uma representação no futuro, remova sua etapa de criação do fluxo de trabalho. As representações não podem ser excluídas em massa posteriormente. As representações indesejadas podem ocupar muito espaço de armazenamento após uso prolongado de [!DNL Experience Manager]. Para ativos individuais, você pode remover as renderizações manualmente da interface do usuário. Para vários ativos, você pode personalizar [!DNL Experience Manager] para excluir representações específicas ou excluir os ativos e carregá-los novamente.
* Por padrão, [!UICONTROL Ativo de atualização DAM] O fluxo de trabalho inclui algumas etapas para criar miniaturas e representações da Web. Se qualquer renderização padrão for removida do fluxo de trabalho, a interface do usuário de [!DNL Assets] não é renderizada corretamente.

>[!MORELIKETHIS]
>
>* [Aplicar e participar de fluxos de trabalho](/help/sites-authoring/workflows.md)
>* [Criar modelos de fluxo de trabalho e estender a funcionalidade do fluxo de trabalho](/help/sites-developing/workflows.md)
>* [Métodos para executar workflows](/help/sites-administering/workflows-starting.md)
>* [Práticas recomendadas para workflows](/help/sites-developing/workflows-best-practices.md)

