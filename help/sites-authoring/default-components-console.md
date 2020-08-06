---
title: Console de componentes
seo-title: Console de componentes
description: 'null'
seo-description: 'null'
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 93%

---


# Console de componentes{#components-console}

O console Componentes permite navegar em todos os componentes definidos para a sua instância e exibir as principais informações de cada componente. 

It can be accessed from **Tools** -> **General** -> **Components**. No console, as visualizações em Cartão e Lista estão disponíveis. Como não há estrutura em árvore para componentes, a exibição em coluna não está disponível.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>O console Componentes mostra todos os componentes do sistema. O [Navegador de componentes](/help/sites-authoring/author-environment-tools.md#components-browser) mostra componentes que estão disponíveis para autores e oculta todos os grupos de componentes que começam com um ponto final ( `.`).

## Pesquisar {#search-features}

Com o ícone **Apenas conteúdo** (na parte superior esquerda), você pode abrir o painel **Pesquisar** para pesquisar e/ou filtrar os componentes: 

![chlimage_1-302](assets/chlimage_1-302.png)

## Detalhes do componente {#component-details}

Para exibir detalhes sobre um componente específico, toque/clique no recurso desejado. As três guias fornecem:

* **Propriedades**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Na guia Propriedades, é possível:

   * Veja as propriedades gerais do componente.
   * Visualizar como o [ícone ou a abreviação foi definida](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) para o componente.

      * Clicar na origem do ícone levará você até esse componente.
   * Visualizar o **Tipo de recurso** e o **Supertipo do recurso** (se definido) para o componente.

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

   Se o desenvolvedor tiver fornecido a [documentação referente ao componente](/help/sites-developing/developing-components.md#documenting-your-component), ela aparecerá na guia **Documentação**. Se não houver documentação disponível, a guia **Documentação** não será exibida.

   ![chlimage_1-305](assets/chlimage_1-305.png)

