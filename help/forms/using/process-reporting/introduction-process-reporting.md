---
title: Introdução ao Relatórios do processo
seo-title: Introdução ao Relatórios do processo
description: Introdução e principais recursos do AEM Forms no Relatórios JEE Process
seo-description: Introdução e principais recursos do AEM Forms no Relatórios JEE Process
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Introdução ao Relatórios do processo {#introduction-to-process-reporting}

![relatórios de processos](assets/process-reporting.png)

O Process Relatórios é uma ferramenta baseada em navegador que você usa para criar e visualização relatórios de processos e tarefas do AEM Forms.

O Process Relatórios fornece um conjunto de relatórios prontos para uso que permitem filtrar, visualização de informações sobre processos de longa execução, duração do processo e volume do fluxo de trabalho.

Além disso, o Relatórios Process fornece uma interface para executar query adhoc e integrar visualizações de relatório personalizadas à interface do usuário do Process Relatórios.

Para obter a lista de navegadores suportados, consulte Plataformas [suportadas pela](/help/forms/using/aem-forms-jee-supported-platforms.md)AEM Forms.

O Relatórios de processo é construído em módulos que:

* Ler dados de processo do AEM Forms Database
* Publicar dados do processo em um repositório de Relatórios do Processo incorporado
* Fornece uma interface de usuário baseada em navegador para relatórios de visualização

## Principais recursos {#key-capabilities}

### Relatórios sempre ativo {#always-on-reporting}

![gerenciamento de sites](assets/site-management.png)

Visualização a lista de processos de longa execução, gráficos de duração do processo e execução de query personalizados usando filtros.

O Process Relatórios também oferece a opção de exportar os dados do relatório e do query no formato CSV.

### Relatórios ad hoc {#adhoc-reports}

![impressão&amp;-colorido](assets/print-&-colour.png)

Use filtros para obter uma visualização específica dos seus dados.

Você pode pesquisar processos ou tarefas por ID, duração, datas de start e término, iniciador do processo etc.

É possível combinar vários filtros para criar relatórios específicos.

Você pode salvar os filtros do relatório para serem executados em uma data ou hora posterior.

### Histórico de processos/Tarefas {#process-task-history}

![gerenciamento de arquivos](assets/file-management.png)

Os servidores AEM Forms executam vários processos em paralelo. Esses processos continuam em transição de um estado para outro. Ao publicar dados da Forms no repositório do Process Relatórios em intervalos regulares, o Process Relatórios retém as informações de transição sobre os processos em execução no AEM Forms.

### Controle de acesso {#access-control-br}

![sem título](assets/untitled.png)

O Process Reporting fornece acesso baseado em permissões à interface do usuário.

Isso significa que somente os usuários com permissões de relatórios têm acesso à interface do usuário do Process Relatórios.


