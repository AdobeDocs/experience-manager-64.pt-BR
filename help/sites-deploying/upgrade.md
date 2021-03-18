---
title: Atualização para o AEM 6.4
seo-title: Atualização para o AEM 6.4
description: Saiba mais sobre as noções básicas para atualizar uma instalação de AEM mais antiga para a AEM 6.4.
seo-description: Saiba mais sobre as noções básicas para atualizar uma instalação de AEM mais antiga para a AEM 6.4.
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: Atualização
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---


# Atualização para AEM 6.4{#upgrading-to-aem}

Nesta seção, cobrimos a atualização de uma instalação AEM para AEM 6.4:

* [Planejamento da atualização](/help/sites-deploying/upgrade-planning.md)
* [Avaliação da complexidade da atualização com o Detector de padrões](/help/sites-deploying/pattern-detector.md)
* [Compatibilidade com versões anteriores no AEM 6.4](/help/sites-deploying/backward-compatibility.md)
* [Procedimento de atualização](/help/sites-deploying/upgrade-procedure.md)
* [Atualização de código e personalizações](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Tarefas de manutenção de pré-atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Execução de uma atualização no local](/help/sites-deploying/in-place-upgrade.md)
* [Verificação e solução de problemas da pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Atualizações sustentáveis](/help/sites-deploying/sustainable-upgrades.md)
* [Migração de conteúdo ocioso](/help/sites-deploying/lazy-content-migration.md)
* [Reestruturação do repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md)

Para facilitar a referência aos casos de AEM envolvidos nesses procedimentos, os termos a seguir são usados em todos esses artigos:

* A instância *source* é a instância AEM da qual você está atualizando.
* A instância *target* é aquela para a qual você está atualizando.

>[!NOTE]
>
>Como parte dos esforços para melhorar a confiabilidade das atualizações, o AEM 6.4 foi submetido a uma reestruturação abrangente do repositório. Para obter mais informações sobre como se alinhar com a nova estrutura, consulte [Reestruturação do Repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md)

## O que mudou? {#what-has-changed}

Veja a seguir as principais mudanças observadas nas últimas versões do AEM:

AEM 6.0 apresentou o novo repositório Jackrabbit Oak. Os Managers de persistência foram substituídos por [Micro Kernels](/help/sites-deploying/recommended-deploys.md). A partir da versão 6.1, o CRX2 não é mais suportado. Uma ferramenta de migração chamada crx2oak precisa ser executada para migrar repositórios CRX2 de instâncias 5.6.1. Para obter mais informações, consulte [Uso da ferramenta de migração CRX2OAK](/help/sites-deploying/using-crx2oak.md).

Se o Asset Insights for usado e você estiver atualizando de uma versão anterior à AEM 6.2, os ativos deverão ser migrados e ter IDs geradas por um Bean JMX. Em nossos testes internos, 125 mil ativos em um ambiente TarMK foram migrados em uma hora, mas seus resultados podem variar.

O AEM 6.3 introduziu um novo formato para o `SegmentNodeStore`, que é a base da implementação do TarMK. Se estiver atualizando de uma versão anterior à AEM 6.3, isso exigirá uma migração de repositório como parte da atualização, envolvendo tempo de inatividade do sistema.

A Engenharia de Adobe estima que seja em torno de 20 minutos. Observe que a reindexação não será necessária. Além disso, uma nova versão da ferramenta crx2oak foi lançada para funcionar com o novo formato de repositório.

**Essa migração não é necessária se estiver atualizando do AEM 6.3 para o AEM 6.4.**

As tarefas de manutenção de pré-atualização foram otimizadas para oferecer suporte à automação.

As opções de uso da linha de comando da ferramenta crx2oak foram alteradas para serem amigáveis à automação e suportar mais caminhos de atualização.

As verificações pós-atualização também foram amigáveis para automação.

A coleta periódica de lixo de revisões e coleta de lixo do armazenamento de dados agora são tarefas de manutenção de rotina que precisam ser executadas periodicamente. Com a introdução do AEM 6.3, o Adobe suporta e recomenda a Limpeza de Revisão Online. Consulte [Revisão de limpeza](/help/sites-deploying/revision-cleanup.md) para obter informações sobre como configurar essas tarefas.

**AEM 6.4** apresenta o  [Detector de ](/help/sites-deploying/pattern-detector.md) padrões para avaliar a complexidade da atualização à medida que você começa a planejar a atualização. O 6.4 também tem um foco forte em [compatibilidade com versões anteriores](/help/sites-deploying/backward-compatibility.md) dos recursos. Por fim, práticas recomendadas para [atualizações sustentáveis](/help/sites-deploying/sustainable-upgrades.md) também são adicionadas.

Para obter mais detalhes sobre o que foi alterado em versões recentes do AEM, consulte as notas de versão completas:

* [https://helpx.adobe.com/br/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/br/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/br/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/br/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/br/experience-manager/6-4/release-notes.html)

## Visão geral da atualização {#upgrade-overview}

Atualizar AEM é um processo de várias etapas, às vezes de vários meses. A seguinte estrutura foi fornecida como uma visão geral do que está incluído em um projeto de atualização e do conteúdo que foi incluído nesta documentação:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Fluxo de atualização com melhorias de atualização do 6.4 {#upgrade-overview-1}

O diagrama abaixo captura o fluxo geral recomendado realce a abordagem de atualização. Observe a referência aos novos recursos que introduzimos. A atualização deve começar com o Detector de padrões (consulte [Avaliação da complexidade da atualização com o Detector de padrões](/help/sites-deploying/pattern-detector.md)), que deve permitir que você decida o caminho que deseja seguir para compatibilidade com o AEM 6.4 com base nos padrões do relatório gerado.

Havia um grande foco no 6.4 para manter todos os novos recursos compatíveis com versões anteriores, mas nos casos em que ainda há alguns problemas de compatibilidade com versões anteriores, o modo de compatibilidade permite adiar temporariamente o desenvolvimento para manter seu código personalizado em conformidade com o 6.4. Essa abordagem ajuda você a evitar o esforço de desenvolvimento imediatamente após a atualização (consulte [Compatibilidade com versões anteriores no AEM 6.4](/help/sites-deploying/backward-compatibility.md)).

Finalmente, em seu ciclo de desenvolvimento 6.4, os recursos introduzidos em Atualizações sustentáveis (consulte [Atualizações sustentáveis](/help/sites-deploying/sustainable-upgrades.md)) ajudam a seguir as práticas recomendadas para tornar as atualizações futuras ainda mais eficientes e ininterruptas.

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)

