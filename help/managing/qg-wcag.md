---
title: Guia rápido para WCAG 2.0
seo-title: Guia rápido para WCAG 2.0
description: Leia uma rápida visão geral das diretrizes de acessibilidade do WCAG 2.0.
seo-description: Leia uma rápida visão geral das diretrizes de acessibilidade do WCAG 2.0.
uuid: a5cf463e-89e9-4cc0-9c91-69a1fd3d8ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility
content-type: reference
discoiquuid: 3cac0e34-7514-48ce-a93b-592bbdbcd252
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 82%

---


# Quick Guide to WCAG 2.0{#quick-guide-to-wcag}

AEM foi desenvolvido para maximizar a conformidade com as Diretrizes de acessibilidade do conteúdo da Web:

The [Web Content Accessibility Guidelines version 2.0 (WCAG2)](https://www.w3.org/TR/WCAG/) are a set of internationally recognized guidelines developed by the [World Wide Web Consortium (W3C)](https://www.w3.org/) under their [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/).

A WCAG 2.0 consiste em um conjunto de diretrizes de tecnologia independentes e critérios de sucesso para ajudar a tornar o conteúdo da Web acessível e utilizável para pessoas com necessidades especiais. Essas diretrizes fazem aconselhamento aos criadores de conteúdo, designers e desenvolvedores da Web, a fim de garantir que os recursos que produzem sejam o mais acessíveis possível ao maior número de pessoas possível, independentemente de qualquer deficiência que tenham. Por exemplo, deficiência visual, perda auditiva, dificuldades de aprendizado, limitações relacionadas à idade, entre outras.

Por exemplo, descrever uma imagem (ou qualquer outro conteúdo não textual) usando o `alt` atributo em HTML beneficia muito as pessoas que são cegas ou amblíopes. A descrição textual no `alt` atributo pode ser convertida em saída de fala ou transmitida para exibições eletrônicas atualizáveis em braille.

Além disso, a WCAG 2.0 pode resultar em vantagens para outros beneficiários, incluindo pessoas que podem ser consideradas *com deficiência situacional*. Pessoas que, devido a circunstâncias como a tecnologia de navegação, a velocidade de conexão da rede ou o ambiente de navegação, podem enfrentar barreiras semelhantes às de pessoas com deficiências.

Usando o Adobe Experience Manager, os criadores de conteúdo e/ou proprietários de sites podem criar conteúdo na Web que atenda aos critérios de sucesso relevantes de Nível A e de Nível AA da WCAG 2.0:

Portanto, entender os objetivos da WCAG 2.0 e como as diretrizes são estruturadas é uma parte importante da compreensão da acessibilidade da Web e como as diretrizes podem ajudar na criação de conteúdo acessível na Web.

A intenção da WCAG 2.0 é fornecer diretrizes que:

* São **agnósticos tecnológicos:**

   Em outras palavras, orientações que podem ser aplicadas a diversos formatos de conteúdo da Web, não apenas HTML. Assim, a WCAG 2.0 pode abranger o conteúdo gerado ou fornecido em PDF, Flash, JavaScript e outras tecnologias atuais e futuras na Web. O objetivo é resolver uma deficiência reconhecida do WCAG 1.0, na medida em que o foco era no HTML, em detrimento de outros formatos de conteúdo da Web.

* São **testáveis:**

   Cada orientação é redigida de forma a poder ser objetivamente testada, a fim de garantir que um grupo de peritos em matéria de acessibilidade concordasse, de um modo geral, que a orientação foi cumprida. Um dos desafios das diretrizes de acessibilidade é que, embora algumas possam ser testadas tecnicamente, outras exigem uma avaliação humana para determinar se a diretriz foi ou não cumprida com êxito. O WCAG 2.0 foi escrito com o objetivo de reduzir a subjetividade que estava presente em algumas das diretrizes e pontos de verificação do WCAG 1.0.

* Oferecem suporte à **implementação priorizada e contextual:**

   Tal como acontece com o WCAG 1.0, as orientações do WCAG 2.0 são prioritárias, relacionadas com o impacto provável de não seguir uma orientação para um grupo específico de utilizadores com deficiência. Isso permite que os autores tomem uma decisão bem informada sobre as orientações mais importantes para suas situações específicas. Além disso, é introduzido o conceito &quot;*com suporte para acessibilidade*&quot;. Isso permite que os autores tomem decisões sobre como usar tecnologias da Web que possam não ter suporte total para acessibilidade ou exigir que os usuários tenham tecnologias de assistência e/ou navegadores específicos para se beneficiarem dos recursos de acessibilidade.

Esses objetivos influenciaram significativamente a estrutura da WCAG 2.0.

>[!NOTE]
>
>Não é possível criar um site que atenda a todas as deficiências ou tipos de pessoas possíveis. O objetivo da WCAG 2.0 é ajudar os autores da Web a criar sites que sejam, na medida do possível, acessíveis em determinadas condições e dentro dos limites da razão.

>[!NOTE]
>
>Se estiver familiarizado com o WCAG 1.0, você observará algumas alterações no WCAG 2.0. Estes dizem respeito ao âmbito, à organização e ao objetivo.

## Estrutura {#structure}

A WCAG 2.0 está estruturada de forma a introduzir conceitos de criação de conteúdo acessível na Web de forma progressivamente detalhada. Isso pode dar a impressão de que a WCAG 2.0 é um conjunto muito complexo de documentos interligados, mas o objetivo é (progressivamente) fornecer informações mais detalhadas conforme e quando os autores precisarem - em vez de fornecer tudo isso em um documento muito volumoso.

O WCAG 2.0 consiste em quatro princípios chave para um design acessível. São eles:

1. **Perceptível**: um usuário pode perceber o conteúdo da Web em questão?
1. **Operável**: um usuário pode navegar, inserir dados ou interagir com o conteúdo da Web?
1. **Compreensível**: um usuário pode processar e compreender o conteúdo da Web apresentado a ele?
1. **Robusto**: o conteúdo da Web está disponível da maneira desejada em uma ampla variedade de ambientes de navegação, incluindo ambientes de navegação herdados e emergentes?

Estes princípios são por vezes referidos pela sigla POUR.

* Cada **princípio** consiste em uma ou mais **diretrizes**.

   * As diretrizes são redigidas como instruções, que são positivas (faça isso...) ou negativas (não faça isso...).
   * As diretrizes são numeradas de 1.1 a 4.1 e o primeiro número corresponde ao princípio principal.

* Cada diretriz consiste em um ou mais **critérios de sucesso**.

   * Os critérios de sucesso são redigidos como declarações, que são `True` ou `False` para qualquer página da Web.
   * Os critérios de sucesso podem incluir opções ou exceções; situações em que os critérios de sucesso não precisam ser cumpridos.
   * Os critérios de sucesso são numerados de acordo com a diretriz e o princípio principais, de 1.1.1 a 4.1.1. Eles também têm um nome curto que resume a intenção do critério, para uma referência mais fácil. Por exemplo, o critério de sucesso 1.1.1 é alternativo não textual.
   * Os critérios de sucesso incluem uma lista de **técnicas** relacionadas (descritas mais detalhadamente abaixo).

## Recursos de suporte {#supporting-resources}

Além dos componentes principais de Princípios, Diretrizes e Critérios de sucesso da WCAG 2.0, existe uma série de documentos de suporte. Alguns deles fornecem conselhos específicos sobre como cumprir os aspectos das diretrizes, outros são referências mais gerais que ajudam os autores, designers e desenvolvedores da Web de todas as habilidades a entender e usar a WCAG 2.0 da forma mais eficaz possível.

Embora a WCAG 2.0 seja um documento estável e não mude, a maioria desses recursos de suporte corresponde a documentos dinâmicos. Eles serão alterados e desenvolvidos com o tempo, à medida que surjam novas tecnologias e sejam encontrados novos exemplos de como a acessibilidade da Web pode ser alcançada.

### Recursos da WCAG 2.0 {#wcag-resources}

* [Um resumo de todos os documentos](https://www.w3.org/WAI/intro/wcag.php)relacionados ao WCAG 2.0;
* [Explicação da relação entre os diferentes componentes](https://www.w3.org/WAI/intro/wcag20);
* [Perguntas frequentes sobre a WCAG 2.0](https://www.w3.org/WAI/WCAG20/wcag2faq.html);

### Técnicas da WCAG 2.0 {#techniques-for-wcag}

As técnicas da WCAG 2.0 estão disponíveis na página [Técnicas da WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/) .

As **técnicas** formam o nível abaixo dos critérios de sucesso na hierarquia da WCAG 2.0. Elas são classificadas pela WAI como informativas, não normativas. Em outras palavras, não é necessário seguir uma técnica específica para que um recurso esteja em conformidade com a WCAG 2.0.

Como as técnicas são muito mais específicas do que os critérios de sucesso, elas geralmente se referem a determinada tecnologia, tipo de conteúdo (por exemplo, HTML ou vídeo) ou situação (por exemplo, comércio eletrônico ou aplicativo de e-learning). Você pode considerar técnicas como exemplos comprovados de como diretrizes e critérios de sucesso específicos podem ser cumpridos, portanto, elas são úteis para autores e desenvolvedores que trabalham em determinados contextos.

As técnicas podem ser acessadas:

* Por coleção (as técnicas podem ser gerais ou estar relacionadas a uma tecnologia ou formato específico - como HTML, CSS ou Scripts do cliente) ou
* Em critérios de sucesso relacionados. As técnicas podem ser aplicadas a mais de um critério de sucesso.

Cada técnica tem um número exclusivo, que está relacionado à coleção. Por exemplo, uma das técnicas ARIA é a *Técnica ARIA2: identificação de campos obrigatórios com a propriedade &quot;obrigatório&quot;*.

As técnicas podem ser suficientes, consultivas ou uma falha:

* Uma *Técnica suficiente* é aquela que, se for seguida, será suficiente para cumprir um critério de sucesso específico.
* Uma *Técnica consultiva* é aquela que, se for seguida, terá um impacto positivo na acessibilidade, mas pode não ser suficiente por si só para garantir que um critério específico de sucesso seja cumprido.
* Uma *Falha* é uma técnica que descreve um exemplo específico de onde um critério de sucesso não seria atendido.

Os detalhes das técnicas incluem uma descrição, aplicabilidade, exemplos, recursos para obter mais informações e detalhes sobre como os autores podem testar a aplicação bem-sucedida da técnica.

A lista de técnicas não está completa e a WAI atualiza constantemente a lista com novos exemplos, refletindo os desenvolvimentos na tecnologia da Web, abordagens de design e resultados de pesquisa. Portanto, vale a pena verificar regularmente a lista de técnicas quanto a novas adições.

### Noções básicas sobre a WCAG 2.0 {#understanding-wcag}

Trata-se de uma série de documentos que fornecem conselhos para ajudar os leitores a compreender o objetivo de diretrizes e critérios de sucesso específicos. Você pode [baixar uma introdução, além de links para informações mais detalhadas](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/Overview.html).

Cada diretriz e critério de sucesso tem também sua própria página de &quot;Noções básicas&quot;, que fornece informações sobre:

* A intenção da diretriz;
* Critérios de sucesso específicos;
* Técnicas de aconselhamento, que ajudam a cumprir os requisitos da diretriz, mas que não se enquadram em nenhum critério de sucesso específico.

A página de &quot;noções básicas&quot; de cada critério de sucesso fornece informações sobre:

* A intenção do critério de sucesso;
* Exemplos gerais de como o critério de sucesso pode ser cumprido;
* Recursos relacionados (não W3C) sobre como cumprir o critério de sucesso;
* Técnicas e falhas: exemplos específicos e detalhados de como o critério de sucesso pode ser atendido (descritos mais detalhadamente abaixo)
* Termos principais - um glossário de termos importantes para entender o critério de sucesso.

Um exemplo pode ser encontrado em: [Noções sobre o critério de sucesso 1.1.1 (&quot;Conteúdo não textual&quot;)](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/text-equiv-all.html).

### Como cumprir a WCAG 2.0 {#how-to-meet-wcag}

A seção &quot;Como cumprir&quot; está disponível na página [Como cumprir a WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/) . Esta seção fornece uma apresentação alternativa da WCAG, que permite refinar o conteúdo das diretrizes para os mais relevantes para os próprios interesses ou circunstâncias do leitor. Os leitores podem filtrar as técnicas de critérios de sucesso que desejam visualização, especificando tecnologias específicas de conteúdo na Web, como folhas de estilos em cascata ou scripts, ou especificando um ou mais níveis de prioridade específicos.

Sem filtragem, esse recurso fornece todos os critérios de sucesso agrupados por diretriz. Para cada critério de sucesso, é fornecido o seguinte:

* O texto do critério de sucesso;
* Um link para o documento de &quot;noções básicas&quot; correspondente;
* Uma lista de técnicas suficientes relacionadas, que está associada aos detalhes de cada técnica;
* Uma lista de técnicas consultivas relacionadas, que está associada aos detalhes de cada técnica (se houver);
* Uma lista de falhas relacionadas, que está associada aos detalhes de cada falha.