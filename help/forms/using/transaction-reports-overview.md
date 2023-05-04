---
title: Visão geral dos relatórios de transação
seo-title: Transaction Reports Overview
description: Manter uma contagem de todos os formulários enviados, comunicação interativa renderizada, Documentos convertidos em um formato para outro e muito mais
seo-description: Keep a count of all the forms submitted, interactive communication rendered, Documents converted to one format to another, and more
uuid: b40220e6-88c8-4507-b228-6c57d9b54422
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 1fb11e02-d8f1-41a0-8e23-cb890b4e2244
exl-id: a545aa0a-9d71-48ba-ba3e-ed30a7e34f3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 1%

---

# Visão geral dos relatórios de transação {#transaction-reports-overview}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Manter uma contagem de todos os formulários enviados, comunicação interativa renderizada, Documentos convertidos em um formato para outro e muito mais

## Introdução {#introduction}

Relatórios de transação no AEM Forms permitem que você mantenha uma contagem de todas as transações realizadas desde uma data especificada na implantação do AEM Forms. O objetivo é fornecer informações sobre o uso do produto e ajudar as partes interessadas a entender seus volumes de processamento digital. Exemplos de uma transação incluem:

* Envio de um formulário adaptável, um formulário HTML5 ou um conjunto de formulários
* Representação de uma versão impressa ou da Web de uma comunicação interativa
* Conversão de um documento de um formato de arquivo para outro

Para obter mais informações sobre o que é considerado uma transação, consulte [APIs faturáveis](/help/forms/using/transaction-reports-billable-apis.md).

A gravação de transação é desativada por padrão. Você pode [habilitar gravação de transações](/help/forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) do Console AEM Web. Você pode exibir relatórios de transação nas instâncias de autor, processamento ou publicação. Exiba relatórios de transação nas instâncias de criação ou processamento para obter uma soma agregada de todas as transações. Visualize relatórios de transação nas instâncias de publicação para obter uma contagem de todas as transações que ocorrem apenas nessa instância de publicação, de onde o relatório é executado.

Não crie conteúdo (Crie formulários adaptáveis, comunicação interativa, temas e outras atividades de criação) e processe documentos (Use workflows, serviços de documento e outras atividades de processamento) na mesma instância de AEM. Manter a gravação de transações desativada para os servidores da AEM Forms usados para criar conteúdo. Mantenha a gravação de transações ativada para os servidores da AEM Forms usados para processar documentos.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Uma transação permanece no buffer por um período especificado (Tempo do buffer de liberação + Tempo de replicação inversa). Por padrão, leva aproximadamente 90 segundos para a contagem de transações ser refletida no relatório de transações.

Ações como enviar um Formulário PDF, usar a interface do usuário do agente para visualizar uma comunicação interativa ou usar métodos de envio de formulário não padrão não são contabilizadas como transações. A AEM Forms fornece uma API para registrar essas transações. Chame a API das implementações personalizadas para registrar uma transação.

## Topologia suportada {#supported-topology}

Os relatórios de transação estão disponíveis somente no AEM Forms no ambiente OSGi. Ele oferece suporte para author-publish, author-processing-publish e somente a topologias de processamento. Por exemplo, topologias, consulte [Topologias de arquitetura e implantação do AEM Forms](/help/forms/using/transaction-reports-overview.md).

A contagem de transações é replicada reversa das instâncias de publicação para as instâncias de autor ou de processamento. Uma topologia indicativa de autor-publicação é exibida abaixo:

![simple-author-publish-topology](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>Os relatórios de transação do AEM Forms não são compatíveis com topologias que contêm apenas instâncias de publicação.

### Orientações para a utilização dos relatórios de transações {#guidelines-for-using-transaction-reports}

* Desative os relatórios de transação em todas as instâncias do autor, pois os relatórios em instâncias do autor incluem transações registradas durante as atividades de criação.
* Ative o **Mostrar transações apenas da publicação** na instância de autor para exibir transações cumulativas de todas as instâncias de publicação. Você também pode exibir relatórios de transação em cada instância de publicação para transações reais apenas nessa instância de publicação específica.
* Não use instâncias de autor para executar fluxos de trabalho e processar documentos.
* Antes de usar o relatório de transações, se você tiver uma topologia com servidores de publicação, verifique se a replicação inversa está ativada para todas as instâncias de publicação.
* Os dados de transação são replicados reversivamente de uma instância de publicação para apenas a instância de autor ou processamento correspondente. A instância de processamento ou autor não pode replicar mais os dados para outra instância. Por exemplo, se você tiver a topologia author-processing-publish, os dados de transação agregados serão replicados somente para a instância de processamento.

## Artigos relacionados {#related-articles}

* [Exibindo e Noções Gerais de Relatórios de Transações](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [APIs faturáveis dos relatórios de transação](/help/forms/using/transaction-reports-billable-apis.md)
* [Registrar uma transação para implementações personalizadas](/help/forms/using/record-transaction-custom-implementation.md)
