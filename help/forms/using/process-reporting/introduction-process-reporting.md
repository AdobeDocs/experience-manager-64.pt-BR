---
title: Introdução ao Relatório de Processos
seo-title: Introduction to Process Reporting
description: Introdução e principais recursos do AEM Forms no JEE Process Reporting
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
exl-id: 279b2f89-5b91-4b8f-ab0f-8ade9b9f3932
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 3%

---

# Introdução ao Relatório de Processos {#introduction-to-process-reporting}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

![relatório de processos](assets/process-reporting.png)

O Process Reporting é uma ferramenta baseada em navegador usada para criar e exibir relatórios sobre processos e tarefas do AEM Forms.

O Relatório de processos fornece um conjunto de relatórios prontos para uso que permitem filtrar, exibir informações sobre processos de execução longa, duração do processo e volume de fluxo de trabalho.

Além disso, o Process Reporting fornece uma interface para executar consultas adhoc e integrar exibições de relatório personalizadas à interface do usuário do Process Reporting .

Para obter a lista de navegadores compatíveis, consulte [Plataformas compatíveis com a AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

O Process Reporting é criado em módulos que:

* Ler dados do processo do banco de dados AEM Forms
* Publicar dados do processo em um repositório incorporado do Process Reporting
* Fornece uma interface de usuário baseada em navegador para exibir relatórios

## Principais recursos {#key-capabilities}

### Relatório sempre ativo {#always-on-reporting}

![gerenciamento de site](assets/site-management.png)

Exiba a lista de processos de longa execução, gráficos de duração do processo e execute consultas personalizadas usando filtros.

O Process Reporting também fornece a opção para exportar o relatório e os dados da consulta no formato CSV.

### Relatórios ad hoc {#adhoc-reports}

![imprimir&amp;-cor](assets/print-&-colour.png)

Use filtros para obter uma exibição específica dos seus dados.

Você pode pesquisar processos ou tarefas por ID, duração, datas de início e término, iniciador do processo etc.

É possível combinar vários filtros para criar relatórios específicos.

Você pode salvar os filtros de relatório a serem executados em uma data ou hora posterior.

### Histórico de Processo/Tarefa {#process-task-history}

![gerenciamento de arquivos](assets/file-management.png)

Os servidores da AEM Forms executam vários processos em paralelo. Esses processos continuam fazendo a transição de um estado para outro. Ao publicar dados do Forms no repositório do Process Reporting em intervalos regulares, o Process Reporting retém as informações de transição sobre os processos em execução no AEM Forms.

### Controle de acesso {#access-control-br}

![sem título](assets/untitled.png)

Relatório de processos fornece acesso com base em permissão à interface do usuário.

Isso significa que somente os usuários com permissões de relatório têm acesso à interface do usuário do Process Reporting.
