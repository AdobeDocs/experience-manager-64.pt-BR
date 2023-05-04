---
title: Ferramentas de desenvolvimento
seo-title: Development Tools
description: Para desenvolver aplicativos JCR, Apache Sling ou AEM, vários conjuntos de ferramentas estão disponíveis
seo-description: To develop your JCR, Apache Sling or AEM applications, a number of tool sets are available
uuid: 1bee3a52-5d76-4b0c-a222-a02e12ff3a43
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 76c570e5-46ed-46be-9864-4fe4a83f0caf
exl-id: 3c18feab-97a6-49f2-96be-7e7458199f5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 4%

---

# Ferramentas de desenvolvimento{#development-tools}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para desenvolver aplicativos JCR, Apache Sling ou AEM, os seguintes conjuntos de ferramentas estão disponíveis:

* um conjunto constituído por [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) e WebDAV. O CRXDE Lite está incorporado ao CRX/AEM e permite que você execute tarefas de desenvolvimento padrão no navegador. Com o CRXDE Lite, você pode criar e editar arquivos (como .jsp e .java), pastas, modelos, componentes, caixas de diálogo, nós, propriedades e pacotes enquanto faz logon e integra com o SVN.

   O CRXDE Lite é recomendado quando você não tem acesso direto ao servidor CRX/AEM, quando você desenvolve um aplicativo estendendo ou modificando os componentes prontos para uso e pacotes Java ou quando não precisa de um depurador dedicado, conclusão de código e realce de sintaxe.

* Um conjunto que consiste em um ambiente de desenvolvimento integrado (por exemplo: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) ou [IntelliJ](/help/sites-developing/ht-intellij.md)), uma ferramenta de build (por exemplo: [Apache Maven](/help/sites-developing/ht-projects-maven.md)), FileVault que foi desenvolvido pelo Adobe para mapear um repositório a um sistema de arquivos, um sistema de controle de versão (por exemplo: Subversão), um sistema de rastreador de erros (por exemplo: Jira), um sistema central de gerenciamento de dependência (por exemplo: Apache Archiva) e um sistema de automação de compilação (por exemplo: Apache Continuum).

   Essa configuração permite integrar totalmente seu aplicativo (conteúdo, código, configuração) em qualquer ambiente e processo de desenvolvimento. O link entre os diferentes elementos é a representação do sistema de arquivos do repositório por meio do FileVault, pois todas as ferramentas de desenvolvimento mencionadas anteriormente podem funcionar com arquivos.

## Extensões para ambientes de desenvolvimento integrados {#extensions-for-integrated-development-environments}

O Adobe lançou as seguintes extensões:

* [AEM Extensão Eclipse](/help/sites-developing/aem-eclipse.md)
* [Extensão de colchetes AEM](/help/sites-developing/aem-brackets.md)
* [AEM extensão IntelliJ](https://github.com/headwirecom/aem-ide-tooling-4-intellij/blob/master/documenation/AEM%20Tooling%20Plugin%20for%20IntelliJ%20IDEA.pdf) (de fio de cabeça)

### Outras ferramentas {#other-tools}

AEM navios com outras ferramentas que facilitem o desenvolvimento:

* [Editor de caixa de diálogo](/help/sites-developing/dialog-editor.md)
* [Usar o tradutor para gerenciar dicionários](/help/sites-developing/i18n-translator.md)
* [Gerenciamento de pacotes usando o Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Como desenvolver projetos AEM usando o Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Como criar projetos AEM usando o Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Como desenvolver projetos AEM usando o IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Como usar a ferramenta VLT](/help/sites-developing/ht-vlttool.md)
* [Como usar a ferramenta Servidor proxy](/help/sites-developing/ht-proxy-server.md)
* [Ferramentas de Modernização do AEM](/help/sites-developing/modernization-tools.md)
* [Ferramenta AEM Repo](/help/sites-developing/aem-repo-tool.md)

Ferramentas que facilitam a criação de novos projetos:

* [Arquétipo de projeto do AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* [Modelos AEM Lazybones](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>O tutorial a seguir pode ser de interesse para iniciar um novo projeto de AEM:\
>[Introdução ao AEM Sites Parte 1 - Configuração do projeto](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
