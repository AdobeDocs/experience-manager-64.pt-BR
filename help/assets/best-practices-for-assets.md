---
title: Práticas recomendadas para gerenciar ativos usando AEM
description: Identifique e siga as práticas recomendadas que aprimoram a estabilidade e o desempenho do sistema sob carga, dependendo da implantação do AEM Assets e dos recursos usados para assimilar e processar ativos.
contentOwner: AG
feature: Gerenciamento de ativos
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# Práticas recomendadas para o AEM Assets {#best-practices-for-assets}

O Adobe Experience Manager (AEM) Assets é uma parte essencial do fornecimento de experiências de marketing digital de alta qualidade que contribuem para a realização de objetivos comerciais por meio do aumento da velocidade do conteúdo. Se você trabalhar com um grande número de ativos no AEM Assets ou fizer upload regular/periódico de vários ativos, incluindo vídeos e mídia dinâmica, otimizar sua experiência de gerenciamento de ativos digitais é essencial para a eficiência do sistema.

Dependendo de como você posicionou o AEM Assets para sua organização e dos recursos que você usa em relação à assimilação de ativos, geração de representação e extração de metadados, identificar e seguir as práticas recomendadas em diferentes áreas melhora muito a estabilidade e o desempenho do sistema sob carga.

Depois de revisar os guias a seguir, você terá o conhecimento e as ferramentas para criar e gerenciar um sistema de gerenciamento de ativos da empresa que atenda às suas necessidades.

* [](performance-tuning-guidelines.md)
Guia de ajuste de desempenho de ativosInclui um conjunto de práticas recomendadas que podem ser seguidas em qualquer ponto da implementação, mesmo após entrar em vigor, para garantir que você obtenha o máximo do seu sistema.
* [](assets-sizing-guide.md)
Guia de dimensionamento de ativosAo elaborar estimativas para uma implementação de Ativos, é importante garantir que haja recursos suficientes disponíveis em termos de armazenamento de ativos, CPU, memória, E/S e throughput da rede. Dimensionar muitos desses itens requer compreender quantos ativos estão sendo carregados no sistema. Este guia inclui práticas recomendadas que ajudam a determinar métricas eficientes para estimar a infraestrutura e os recursos necessários para implantar o AEM Assets, bem como uma ferramenta de dimensionamento.
* [](assets-migration-guide.md)
Guia de migração de ativosSe você deseja migrar ativos do seu sistema herdado para o AEM Assets, há várias etapas a serem consideradas para simplificar o processo de migração. O guia Migração inclui práticas recomendadas para as tarefas que você executa para trazer os ativos para o AEM de forma gradual. Isso inclui aplicar metadados, gerar representações e ativar os ativos para publicar a implantação.
* [](assets-network-considerations.md)
Considerações de rede de ativosAo manipular AEM implantação, entender a topologia de rede é importante para entender o desempenho da rede, identificar pontos de estrangulamento e descrever a experiência esperada do usuário. O documento Considerações de rede do Assets discute as considerações de rede ao projetar a implantação do AEM Asset.
* [](assets-monitoring-best-practices.md)
Guia de monitoramento de ativosApós a implantação da sua implantação de AEM, você deve monitorar determinadas tarefas e o sistema em geral para garantir a integridade do sistema e a eficiência das operações. O guia de monitoramento inclui práticas recomendadas para monitorar vários aspectos de seu sistema.
* (Obsoleto) [Guia de descarregamento de ativos](assets-offloading-best-practices.md)
Lidar com arquivos grandes e executar workflows no AEM Assets pode consumir recursos consideráveis de CPU, memória e E/S. Descarregar essas tarefas pode reduzir os custos indiretos de CPU, memória e E/S. O guia de descarregamento de Ativos inclui casos de uso recomendados e práticas recomendadas para a descarregamento de Ativos.
* [AEM ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
práticas recomendadas do aplicativo de desktopO aplicativo de desktop do AEM vincula sua solução de gerenciamento de ativos digitais (DAM) ao desktop, para que você possa abrir os arquivos que estão disponíveis na interface AEM da Web diretamente no desktop. AEM fluxo de trabalho fácil de usar do aplicativo de desktop é ativado com a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop. Este guia explica os principais recursos e o uso recomendado de AEM aplicativo de desktop.
* [AEM e ](aem-cc-integration-best-practices.md)
práticas recomendadas de integração do Creative CloudÉ possível integrar a implantação do AEM com o Creative Cloud de várias maneiras. Seguir algumas práticas recomendadas para simplificar sua integração e os fluxos de trabalho de transferência de ativos ajuda a obter o máximo de eficiência. Este guia inclui práticas recomendadas para a integração do AEM Assets com o Adobe Creative Cloud.
* (Obsoleto) [AEM às práticas recomendadas de compartilhamento de pastas do Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Você pode configurar o AEM para permitir que os usuários no DAM compartilhem pastas com usuários do Creative Cloud (CC), para que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes criativas e usuários do DAM. Este guia explica as práticas recomendadas para o uso do recurso de compartilhamento de AEM para pasta do Creative Cloud.
