---
title: Práticas recomendadas para gerenciar ativos usando AEM
description: Identifique e siga as práticas recomendadas que aprimoram a estabilidade e o desempenho do sistema em carga, dependendo da implantação e dos recursos da AEM Assets usados para assimilar e processar ativos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Best practices for AEM Assets {#best-practices-for-assets}

O Adobe Experience Manager (AEM) Assets é uma parte crucial do fornecimento de experiências de marketing digital de alta qualidade que contribuem para a consecução das metas comerciais através do aumento da velocidade do conteúdo. Se você trabalha com um grande número de ativos no AEM Assets ou faz upload regular/periódico de diversos ativos, incluindo vídeos e mídias dinâmicas, a otimização da experiência de gerenciamento de ativos digitais é essencial para a eficiência do sistema.

Dependendo de como você posicionou a AEM Assets para sua organização e dos recursos usados em torno da assimilação de ativos, geração de execuções e extração de metadados, identificar e seguir as práticas recomendadas em diferentes áreas aumenta consideravelmente a estabilidade e o desempenho do sistema com carga.

Depois de revisar os seguintes guias, você terá o conhecimento e as ferramentas para criar e gerenciar um sistema de gerenciamento de ativos corporativos que atenda às suas necessidades.

* [Guia](performance-tuning-guidelines.md)de ajuste de desempenho de ativosInclui um conjunto de práticas recomendadas que podem ser seguidas a qualquer momento na sua implementação, mesmo depois de entrar em funcionamento, para garantir que você obtenha o máximo do seu sistema.
* [Guia](assets-sizing-guide.md)de dimensionamento de ativos Ao elaborar estimativas para uma implementação de Ativos, é importante garantir que haja recursos suficientes disponíveis em termos de armazenamento de ativos, CPU, memória, E/S e throughput da rede. Dimensionar muitos desses itens requer compreender quantos ativos estão sendo carregados no sistema. Este guia inclui práticas recomendadas que ajudam a determinar métricas eficientes para estimar a infraestrutura e os recursos necessários para implantar o AEM Assets, bem como uma ferramenta de dimensionamento.
* [Guia](assets-migration-guide.md)de migração de ativos Se você quiser migrar ativos do seu sistema herdado para a AEM Assets, há várias etapas a serem consideradas para simplificar o processo de migração. O guia Migração inclui as práticas recomendadas em torno das tarefas que você executa para trazer os ativos para AEM de forma gradual. Isso inclui aplicar metadados, gerar representações e ativar os ativos para publicar a implantação.
* [Considerações](assets-network-considerations.md)de rede de ativos Ao manipular AEM implantação, entender a topologia de rede é importante para entender o desempenho da rede, identificar pontos de interrupção e descrever a experiência esperada do usuário. O documento de considerações de rede do Assets discute as considerações de rede ao projetar sua implantação do AEM Asset.
* [Guia](assets-monitoring-best-practices.md)de monitoramento de ativos Depois que sua implantação AEM é implantada, você deve monitorar determinadas tarefas e o sistema em geral para garantir a integridade e eficiência do sistema. O guia de monitoramento inclui práticas recomendadas para monitorar vários aspectos do seu sistema.
* (Desaprovado) Guia [de descarregamento de ativos](assets-offloading-best-practices.md)Manuseio de arquivos grandes e execução de workflows no AEM Assets podem consumir recursos consideráveis de CPU, memória e E/S. Descarregar essas tarefas pode reduzir os custos indiretos de CPU, memória e E/S. O guia de descarregamento de Ativos inclui casos de uso recomendados e práticas recomendadas para descarregamento de Ativos.
* [AEM práticas](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)recomendadas AEM aplicativo de desktop vincula sua solução de gerenciamento de ativos digitais (DAM) ao seu desktop para que você possa abrir os arquivos disponíveis na interface do usuário da Web AEM diretamente no desktop. AEM fluxo de trabalho fácil de usar do aplicativo desktop é ativado usando a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop. Este guia explica os principais recursos e o uso recomendado AEM aplicativo para desktop.
* [Práticas recomendadas de integração de AEM e Creative Cloud](aem-cc-integration-best-practices.md)Você pode integrar sua implantação de AEM com Creative Cloud de várias maneiras. Seguir algumas práticas recomendadas para simplificar a integração e os workflows de transferência de ativos ajuda a obter o máximo de eficiência. Este guia inclui as práticas recomendadas para a integração do AEM Assets com a Adobe Creative Cloud.
* (Obsoleto) [AEM as práticas](aem-cc-folder-sharing-best-practices.md)recomendadas de compartilhamento de pastas do Creative CloudVocê pode configurar AEM para permitir que os usuários do DAM compartilhem pastas com usuários do Creative Cloud (CC), para que eles fiquem disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes de criação e usuários do DAM. Este guia explica as práticas recomendadas para aproveitar o recurso de compartilhamento de pastas de AEM para Creative Cloud.
