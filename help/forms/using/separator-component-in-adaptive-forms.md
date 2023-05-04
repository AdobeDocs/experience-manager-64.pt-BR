---
title: Componente separador em formulários adaptáveis
seo-title: Separator component in adaptive forms
description: Você pode usar o componente separador para separar visualmente seções de um formulário.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 2%

---

# Componente separador em formulários adaptáveis {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode usar o componente separador para segregar visualmente os painéis de um formulário. Você pode definir a aparência e o estilo gerais de um componente separador especificando as seguintes propriedades do componente separador:

* **Nome do elemento:** Especifica o nome do componente. As expressões SOM endereçam o componente com o valor especificado no campo Nome do elemento .
* **Espessura:** Especifica a espessura do componente separador em pixels.
* **Colspan:** Especifica o número de colunas nas quais um componente separador é expandido.
* **Classe CSS:** Especifica a classe CSS personalizada para o componente separador
* **Estilos em linha:** Com o AEM Forms, agora é possível aplicar estilos de CSS em linha a componentes de formulário adaptáveis individuais e visualizar as alterações em tempo real.

Para especificar as propriedades de um componente separador:

1. Selecione um componente separador e toque em ![cmppr](assets/cmppr.png). As propriedades são abertas na barra lateral.
1. Clique em uma guia na seção Propriedades de CSS em linha para especificar as propriedades de CSS. Por exemplo: a. Na guia Campo, clique em **Adicionar item**. Uma linha com dois campos é adicionada.
1. No primeiro campo à esquerda, especifique uma propriedade CSS3 que deseja aplicar. Por exemplo, **border**. Você também pode selecionar uma propriedade clicando no botão de seta para baixo. A lista suspensa não é exaustiva e você pode especificar qualquer nome de propriedade CSS3 compatível nesse campo.
1. No campo adjacente, especifique um valor válido para a propriedade CSS3 especificada. Por exemplo, **preto sólido 3 px**.
1. Clique em **Adicionar item** para especificar outra propriedade e seu valor.
1. Clique em **Visualizar** para visualizar as alterações no formulário.
1. Clique em **OK** para confirmar as alterações ou em **Cancelar **para sair da caixa de diálogo sem alterações.
