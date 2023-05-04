---
title: Práticas recomendadas para gerenciar ativos usando AEM
description: Identifique e siga as práticas recomendadas que melhoram a estabilidade e o desempenho do sistema sob carga, dependendo do [!DNL Experience Manager] Implantação de ativos e recursos usados para assimilar e processar ativos.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Práticas recomendadas para [!DNL Experience Manager] Ativos {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os ativos Adobe Experience Manager são uma parte essencial do fornecimento de experiências de marketing digital de alta qualidade que contribuem para a consecução de objetivos comerciais através do aumento da velocidade do seu conteúdo. Se você trabalhar com um grande número de ativos no [!DNL Assets] ou faça upload regular/periodicamente de vários ativos, incluindo vídeos e mídias dinâmicas, a otimização de sua experiência de gerenciamento de ativos digitais é essencial para a eficiência do sistema.

Dependendo de como você tiver posicionado [!DNL Assets] para sua organização e os recursos que você usa em relação à assimilação de ativos, geração de representação e extração de metadados, identificar e seguir as práticas recomendadas em diferentes áreas melhora muito a estabilidade e o desempenho do sistema sob carga.

Depois de revisar os guias a seguir, você terá o conhecimento e as ferramentas para criar e gerenciar um sistema de gerenciamento de ativos da empresa que atenda às suas necessidades.

* [Guia de ajuste de desempenho de ativos](performance-tuning-guidelines.md)
Inclui um conjunto de práticas recomendadas que podem ser seguidas em qualquer ponto da implementação, mesmo após entrar em vigor, para garantir que você obtenha o máximo do seu sistema.
* [Guia de dimensionamento de ativos](assets-sizing-guide.md)
Ao elaborar estimativas para uma implementação do Assets, é importante garantir que haja recursos suficientes disponíveis em termos de armazenamento de ativos, CPU, memória, E/S e throughput da rede. Dimensionar muitos desses itens requer compreender quantos ativos estão sendo carregados no sistema. Este guia inclui práticas recomendadas que ajudam a determinar métricas eficientes para estimar a infraestrutura e os recursos necessários para implantar [!DNL Experience Manager] Ativos e uma ferramenta de dimensionamento.
* [Guia de migração de ativos](assets-migration-guide.md)
Caso deseje migrar ativos do sistema herdado para o [!DNL Experience Manager] Ativos, há várias etapas a serem consideradas para simplificar o processo de migração. O guia Migração inclui práticas recomendadas para as tarefas que você executa para trazer os ativos para o [!DNL Experience Manager] em função das fases. Isso inclui aplicar metadados, gerar representações e ativar os ativos para publicar a implantação.
* [Considerações sobre a rede de ativos](assets-network-considerations.md)
Ao manusear [!DNL Experience Manager] a implantação, a compreensão da topologia de rede é importante para entender o desempenho da rede, identificar pontos de estrangulamento e descrever a experiência esperada do usuário. O documento Considerações de rede do Assets discute as considerações de rede ao projetar seu [!DNL Experience Manager] Implantação de ativos.
* [Guia de monitoramento de ativos](assets-monitoring-best-practices.md)
Depois de [!DNL Experience Manager] for implantada, você deverá monitorar determinadas tarefas e o sistema em geral para garantir a integridade do sistema e a eficiência das operações. O guia de monitoramento inclui práticas recomendadas para monitorar vários aspectos de seu sistema.
* (Obsoleto) [Guia de descarregamento de ativos](assets-offloading-best-practices.md)
Manuseio de arquivos grandes e execução de workflows no [!DNL Experience Manager] Os recursos podem consumir recursos consideráveis de CPU, memória e E/S. Descarregar essas tarefas pode reduzir os custos indiretos de CPU, memória e E/S. O guia de descarregamento de Ativos inclui casos de uso recomendados e práticas recomendadas para a descarregamento de Ativos.
* [[!DNL Experience Manager] práticas recomendadas do aplicativo de desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] o aplicativo de desktop vincula sua solução de gerenciamento de ativos digitais (DAM) ao seu desktop para que você possa abrir os arquivos disponíveis no [!DNL Experience Manager] interface da Web diretamente no desktop. [!DNL Experience Manager] o fluxo de trabalho fácil de usar do aplicativo de desktop é ativado com a tecnologia de compartilhamento de rede fornecida pelos sistemas operacionais de desktop. Este guia explica os principais recursos e o uso recomendado de [!DNL Experience Manager] aplicativo de desktop.
* [[!DNL Experience Manager] e práticas recomendadas de integração do Creative Cloud](aem-cc-integration-best-practices.md)
É possível integrar a [!DNL Experience Manager] implantação com o Creative Cloud de várias maneiras. Seguir algumas práticas recomendadas para simplificar sua integração e os fluxos de trabalho de transferência de ativos ajuda a obter o máximo de eficiência. Este guia inclui práticas recomendadas para integração [!DNL Experience Manager] Ativos com a Adobe Creative Cloud.
* (Obsoleto) [[!DNL Experience Manager] para compartilhar práticas recomendadas de compartilhamento de pastas do Creative Cloud](aem-cc-folder-sharing-best-practices.md)
Você pode configurar [!DNL Experience Manager] para permitir que usuários no DAM compartilhem pastas com usuários do Creative Cloud, para que eles estejam disponíveis como pastas compartilhadas no serviço Creative Cloud Assets. O recurso pode ser usado para trocar arquivos entre equipes criativas e usuários do DAM. Este guia explica as práticas recomendadas para o aproveitamento do [!DNL Experience Manager] para o recurso de compartilhamento de pastas do Creative Cloud.
