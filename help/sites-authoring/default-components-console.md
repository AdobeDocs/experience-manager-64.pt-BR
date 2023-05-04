---
title: Console de componentes
seo-title: Components Console
description: Console de componentes
seo-description: null
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
exl-id: fa583a06-e75c-41de-a977-7e459ab8bca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 47%

---

# Console de componentes{#components-console}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O console Componentes permite navegar por todos os componentes definidos para a sua instância e exibir as principais informações de cada componente.

Ele pode ser acessado de **Ferramentas** -> **Geral** -> **Componentes**. No console, as visualizações em Cartão e Lista estão disponíveis. Como não há estrutura em árvore para componentes, a exibição em coluna não está disponível.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>O console Componentes mostra todos os componentes do sistema. O [Navegador de componentes](/help/sites-authoring/author-environment-tools.md#components-browser) mostra componentes que estão disponíveis para autores e oculta todos os grupos de componentes que começam com um ponto final ( `.`).

## Pesquisar {#search-features}

Com o ícone **Apenas conteúdo** (na parte superior esquerda), você pode abrir o painel **Pesquisar** para pesquisar e/ou filtrar os componentes: 

![chlimage_1-302](assets/chlimage_1-302.png)

## Detalhes do componente {#component-details}

Para exibir detalhes sobre um componente específico, toque/clique no recurso desejado. Três guias fornecem:

* **Propriedades**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Na guia Propriedades, é possível:

   * Veja as propriedades gerais do componente.
   * Veja como a função [ícone ou abreviação foi definido](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) para o componente.

      * Clicar na fonte do ícone o direcionará para esse componente.
   * Visualize o **Tipo de recurso** e **Supertipo de Recurso** (se definido) para o componente.

      * Clicar no Supertipo do recurso levará você até esse componente.
   >[!NOTE]
   >
   >Como `/apps` não pode ser editado no tempo de execução, o console Componentes fica somente leitura.

* **Políticas**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **Uso em tempo real**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >Devido à natureza das informações coletadas para esta exibição, ela pode levar algum tempo para ser agrupada/exibida. 

* **Documentação**

   Se o desenvolvedor tiver fornecido [documentação do componente](/help/sites-developing/developing-components.md#documenting-your-component), ele aparecerá no **Documentação** guia . Se não houver documentação disponível, a guia **Documentação** não será exibida.

   ![chlimage_1-305](assets/chlimage_1-305.png)
