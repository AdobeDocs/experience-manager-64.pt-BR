---
title: Criação de formulários adaptáveis acessíveis
seo-title: Creating accessible adaptive forms
description: O AEM Forms fornece ferramentas e para criar formulários adaptáveis acessíveis, além de ajudar a estar em conformidade com os padrões de acessibilidade.
seo-description: AEM Forms provides you tools and to create accessible adaptive forms and helps comply with accessibility standards.
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
feature: Adaptive Forms
exl-id: adad26fa-b27a-4bd7-806c-4ddfbaae7a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Criação de formulários adaptáveis acessíveis {#creating-accessible-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

Um formulário acessível é um formulário que todos podem usar, incluindo usuários com necessidades especiais. O Adobe Experience Manager (AEM) inclui vários recursos e funcionalidades que melhoram a utilização de formulários adaptáveis para usuários com diferentes capacidades. A solução também auxilia os autores de formulários na criação de formulários adaptáveis acessíveis.

Criar a acessibilidade em formulários adaptáveis não só permite o maior público-alvo possível para o conteúdo, como também é um requisito ao fornecer documentos em regiões onde a conformidade com os padrões de acessibilidade é obrigatória. Os desenvolvedores de formulários de ajuda da AEM Forms estão em conformidade com os padrões de acessibilidade.

Ao criar um formulário adaptável, o autor deve considerar os seguintes pontos para criar um formulário adaptável acessível:

* Fornecer rótulos adequados para controles de formulário
* Fornecer equivalentes de texto para imagens
* Fornecer contraste de cor suficiente
* Verifique se os controles de formulário são acessíveis ao teclado

## Fornecer rótulos adequados para controles de formulário {#provide-proper-labels-for-form-controls}

O rótulo ou o título de um componente identifica o que o componente de formulário representa. Por exemplo, o texto &quot;Nome&quot; informa aos usuários que eles devem inserir seu nome em um campo de texto. Para ser acessível por leitores de tela, o rótulo é associado de forma programática a um componente de formulário. Como alternativa, o controle de formulário é configurado com informações adicionais de acessibilidade.

O rótulo percebido pelos leitores de tela não precisa ser necessariamente o mesmo da legenda visual. Em alguns casos, talvez você queira ser mais específico sobre a finalidade do controle. Para cada objeto de campo em um formulário, as opções de acessibilidade podem ser usadas para especificar o que o leitor de tela anuncia para identificar o campo de formulário específico.

Para usar a opção Acessibilidade , siga estas etapas:

1. Selecione um componente e toque em ![cmppr](assets/cmppr.png).
1. Clique em **Acessibilidade** na barra lateral para escolher a opção de acessibilidade desejada.

### Opções de acessibilidade em componentes de formulário {#accessibility-options-in-form-components}

![Opções de acessibilidade em componentes de formulário](assets/accessibility-options.png)

**Texto personalizado** Os autores de formulários fornecem o conteúdo na opção acessibilidade Campo de texto personalizado. A tecnologia de assistência, como leitores de tela, usa esse texto personalizado. Usar a configuração de Título é a melhor opção na maioria dos cenários. Considere criar Reader de tela personalizada somente texto ao usar o Título ou uma breve descrição não é possível.

**Descrição curta** Para a maioria dos componentes, a breve descrição é exibida no tempo de execução, quando o usuário passa o ponteiro sobre o componente. É possível definir essa opção no campo de descrição curta, na opção de conteúdo da ajuda.

**Título** Use essa opção para permitir que o AEM Forms use o rótulo visual associado ao campo de formulário como o texto do leitor de tela.

**Nome** Você pode especificar um valor no campo Nome da guia Vínculo. O nome não pode conter espaços.

**Nenhum** Selecionar Nenhum faz com que o objeto de formulário não tenha um nome no formulário publicado. Nenhum não é uma configuração recomendada para controles de formulário.

>[!NOTE]
>
>Botão de opção e caixa de seleção podem ter apenas duas opções de acessibilidade, a saber, Texto personalizado e Título.

>[!NOTE]
>
>Para formulários adaptáveis baseados em XFA, a opção de acessibilidade é herdada das opções de acessibilidade definidas no XDP. Dicas de ferramentas do XDP são mapeadas para a Descrição curta e a Legenda são mapeadas para o Título. As outras opções funcionam como estão.

## Fornecer equivalentes de texto para imagens {#provide-text-equivalents-for-images}

As imagens podem ajudar a melhorar a compreensão para alguns usuários. No entanto, para usuários que usam leitores de tela, as imagens diminuem a acessibilidade de seu formulário. Se você optar por usar imagens, forneça descrições de texto para todas as imagens.

O texto deve descrever o objeto e sua finalidade no formulário. Um leitor de tela lê esse texto alternativo quando encontra uma imagem. Uma imagem deve sempre ter um texto alternativo especificado.

Selecione um componente de imagem e toque em ![cmppr](assets/cmppr.png). Na barra lateral, em Propriedades, especifique o texto alternativo para uma imagem.

![Texto alternativo para uma imagem](assets/image-properties.png)

## Fornecer contraste de cor suficiente {#provide-sufficient-color-contrast}

O design de acessibilidade envolve considerar diretrizes adicionais para o uso de cores. Os autores de formulários podem usar cores para melhorar a aparência dos formulários, destacando vários componentes de formulário. No entanto, um uso impróprio da cor pode tornar um formulário difícil ou impossível de ser lido por pessoas com habilidades diferentes.

Os usuários portadores de deficiência visual dependem de um alto contraste entre o texto e o plano de fundo para ler o conteúdo digital. Sem contraste suficiente, um formulário pode se tornar difícil, se não impossível, de ler para alguns usuários.

É recomendável usar as cores padrão de fonte e plano de fundo — conteúdo em preto em um plano de fundo branco. Se você alterar as cores padrão, escolha uma cor de primeiro plano escura em uma cor de plano de fundo clara ou vice-versa.

Consulte [Criar temas personalizados para formulários adaptáveis](/help/forms/using/creating-custom-adaptive-form-themes.md), para obter mais informações sobre como alterar o contraste de cores e o tema dos formulários adaptáveis.

## Verifique se os controles de formulário são acessíveis ao teclado {#ensure-that-form-controls-are-keyboard-accessible}

Um formulário acessível pode ser preenchido completamente usando apenas o teclado ou um dispositivo de entrada equivalente. Usuários com mobilidade reduzida ou visão deficiente podem não ter escolha senão usar o teclado e muitos usuários que podem usar um mouse, preferir a entrada do teclado. Ao permitir os vários métodos de entrada, você não apenas cria formulários acessíveis, como também cria formulários mais adequados para as preferências de todos os usuários.

Os seguintes atalhos de teclado estão disponíveis no AEM Forms.

| Ação | Atalho de teclado |
|---|---|
| Mover o cursor para frente em um formulário | Guia |
| Mover o cursor para trás em um formulário | Shift+Tab |
| Mover para o próximo painel | Alt+Seta para a direita |
| Mover para o painel anterior | Alt+Seta para a esquerda |
| Redefinir os dados preenchidos em um formulário | Alt+R |
| Enviar um formulário | Alt+S | configuring-watched-folder-endpoints.md |
