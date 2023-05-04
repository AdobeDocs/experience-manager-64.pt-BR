---
title: Interação entre backbone
seo-title: Backbone interaction
description: Informações conceituais sobre o uso de modelos JavaScript Backbone no espaço de trabalho do AEM Forms.
seo-description: Conceptual information about use of Backbone JavaScript models in AEM Forms workspace.
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
exl-id: f726cb73-732c-4893-bdb5-10ddcf4a340a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 1%

---

# Interação entre backbone {#backbone-interaction}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Backbone é uma biblioteca que ajuda a criar e seguir a arquitetura MVC em aplicativos da Web. A ideia básica do Backbone é organizar sua interface em exibições lógicas, apoiadas por modelos, que podem ser atualizadas independentemente quando o modelo for alterado, sem precisar redesenhar a página. Para obter mais informações sobre Backbone, consulte [https://backbonejs.org](https://backbonejs.org/).

Alguns conceitos-chave são os seguintes:

**Modelo de backbone** Contém dados e a maior parte da lógica relacionada a esses dados.

**Exibição de backbone** Usado para representar o estado do modelo correspondente. Na verdade, uma visualização de backbone se comporta como um controlador, ouvindo eventos da interface do usuário, como cliques do usuário, ou para modelar eventos (como dados alterados) e modifica a interface do usuário, conforme apropriado.

**modelo HTML** Um modelo de wrapper que tem espaços reservados preenchidos pelo modelo.

**Área de trabalho do AEM Forms** Contém vários componentes individuais. Cada componente:

* Representa um único elemento lógico da interface do usuário.
* Pode ser uma coleção de componentes semelhantes.
* Composto por modelo Backbone, visualização Backbone e modelo HTML.
* Contém referência a um serviço.
* Contém referência a utilitários necessários.

Quando um componente é inicializado, os seguintes objetos são criados:

* Uma nova instância do modelo Backbone do componente é criada. O serviço é inserido no modelo.
* Uma nova instância da visualização Backbone é criada.
* A instância do modelo correspondente, modelo HTML e Utilitários é inserida na exibição.

Na exibição Backbone, há um mapa de eventos que mapeia os vários eventos que podem surgir devido a interações da interface do usuário com um manipulador correspondente. Esse mapeamento é iniciado assim que um componente é inicializado.

Quando uma exibição é inicializada, a exibição chama seu modelo correspondente para buscar dados do servidor. Quando todos os dados exigidos por uma exibição estiverem disponíveis, ela renderizará os dados no formato especificado pelo modelo HTML. Várias exibições podem compartilhar o mesmo modelo para comunicação.

![](do-not-localize/aem_forms_workflow.png)

Um exemplo:

1. O usuário clica em um template de tarefa na lista de tarefas.
1. A exibição Tarefa escuta o clique e chama a função de renderização no modelo de tarefa.
1. Posteriormente, o modelo de tarefa chama o serviço, que é um ponto comum para toda a comunicação com o servidor AEM Forms.
1. A classe de serviço chama o endpoint REST do AEM Forms para método de renderização via ajax.
1. O retorno de chamada bem-sucedido para esta invocação Ajax é definido no modelo de tarefa.
1. O modelo de tarefa gera um evento de backbone como uma notificação de conclusão da chamada de renderização.
1. Outra exibição, exibição de detalhes da tarefa, escuta esse evento do modelo de tarefa.
1. A exibição Detalhes da tarefa altera o modelo de detalhes da tarefa para exibir a tarefa renderizada (formulário, detalhes, anexos, observações e assim por diante) para o usuário.
