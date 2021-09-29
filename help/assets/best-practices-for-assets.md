---
title: Práticas recomendadas para gerenciar ativos usando AEM
description: Identifique e siga as práticas recomendadas que aprimoram a estabilidade e o desempenho do sistema sob carga, dependendo da implantação do  [!DNL Experience Manager] Assets e dos recursos usados para assimilar e processar ativos.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Práticas recomendadas para ativos [!DNL Experience Manager] {#best-practices-for-assets}

Os ativos Adobe Experience Manager são uma parte essencial do fornecimento de experiências de marketing digital de alta qualidade que contribuem para a consecução de objetivos comerciais através do aumento da velocidade do seu conteúdo. Se você trabalhar com um grande número de ativos no [!DNL Assets] ou fizer upload regular/periodicamente de vários ativos, incluindo vídeos e mídia dinâmica, otimizar sua experiência de gerenciamento de ativos digitais é essencial para a eficiência do sistema.

Dependendo de como você posicionou [!DNL Assets] para sua organização e dos recursos que você usa em relação à assimilação de ativos, geração de representação e extração de metadados, identificar e seguir as práticas recomendadas em diferentes áreas melhora muito a estabilidade e o desempenho do sistema sob carga.

Depois de revisar os guias a seguir, você terá o conhecimento e as ferramentas para criar e gerenciar um sistema de gerenciamento de ativos da empresa que atenda às suas necessidades.

* [](performance-tuning-guidelines.md)
Guia de ajuste de desempenho de ativosInclui um conjunto de práticas recomendadas que podem ser seguidas em qualquer ponto da implementação, mesmo após entrar em vigor, para garantir que você obtenha o máximo do seu sistema.
* [](assets-sizing-guide.md)
Guia de dimensionamento de ativosAo elaborar estimativas para uma implementação de Ativos, é importante garantir que haja recursos suficientes disponíveis em termos de armazenamento de ativos, CPU, memória, E/S e throughput da rede. Dimensionar muitos desses itens requer compreender quantos ativos estão sendo carregados no sistema. Este guia inclui práticas recomendadas que ajudam a determinar métricas eficientes para estimar a infraestrutura e os recursos necessários para implantar [!DNL Experience Manager] ativos, bem como uma ferramenta de dimensionamento.
* [](assets-migration-guide.md)
Guia de migração de ativosSe você quiser migrar ativos do seu sistema herdado para os  [!DNL Experience Manager] Ativos, há várias etapas a serem consideradas para simplificar o processo de migração. O guia Migração inclui práticas recomendadas em torno das tarefas que você executa para trazer os ativos para [!DNL Experience Manager] de maneira gradual. Isso inclui aplicar metadados, gerar representações e ativar os ativos para publicar a implantação.
* [](assets-network-considerations.md)
Considerações de rede de ativosAo manipular a  [!DNL Experience Manager] implantação, entender a topologia de rede é importante para entender o desempenho da rede, identificar pontos de bloqueio e descrever a experiência esperada do usuário. O documento Considerações de rede do Assets discute as considerações de rede ao projetar sua implantação do [!DNL Experience Manager] Ativo.
* [](assets-monitoring-best-practices.md)
Guia de monitoramento de ativosApós a implantação da  [!DNL Experience Manager] implantação, você deve monitorar determinadas tarefas e o sistema em geral para garantir a integridade do sistema e a eficiência das operações. O guia de monitoramento inclui práticas recomendadas para monitorar vários aspectos de seu sistema.
* (Obsoleto) [Guia de descarregamento de ativos](assets-offloading-best-practices.md)
O manuseio de arquivos grandes e a execução de fluxos de trabalho em [!DNL Experience Manager] Assets podem consumir recursos consideráveis de CPU, memória e E/S. Descarregar essas tarefas pode reduzir os custos indiretos de CPU, memória e E/S. O guia de descarregamento de Ativos inclui casos de uso recomendados e práticas recomendadas para a descarregamento de Ativos.
* [[!DNL Experience Manager] práticas recomendadas do aplicativo de desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] o aplicativo de desktop vincula sua solução de gerenciamento de ativos digitais (DAM) ao seu desktop para que você possa abrir os arquivos que estão disponíveis na interface do usuário da  [!DNL Experience Manager] Web diretamente no desktop. [!DNL Experience Manager] o fluxo de trabalho fácil de usar do aplicativo de desktop é ativado com a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop. Este guia explica os principais recursos e o uso recomendado do [!DNL Experience Manager] aplicativo de desktop.
* [[!DNL Experience Manager] e ](aem-cc-integration-best-practices.md)
práticas recomendadas de integração do Creative CloudÉ possível integrar sua  [!DNL Experience Manager] implantação com o Creative Cloud de várias maneiras. Seguir algumas práticas recomendadas para simplificar sua integração e os fluxos de trabalho de transferência de ativos ajuda a obter o máximo de eficiência. Este guia inclui práticas recomendadas para a integração de [!DNL Experience Manager] ativos com o Adobe Creative Cloud.
* (Obsoleto) [[!DNL Experience Manager] para a pasta Creative Cloud que compartilha práticas recomendadas](aem-cc-folder-sharing-best-practices.md)
Você pode configurar [!DNL Experience Manager] para permitir que os usuários no DAM compartilhem pastas com usuários do Creative Cloud (CC), de modo que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes criativas e usuários do DAM. Este guia explica as práticas recomendadas para o uso do [!DNL Experience Manager] no recurso de compartilhamento de pastas do Creative Cloud.
