---
title: Criar formulários HTML5 acessíveis
seo-title: Criar formulários HTML5 acessíveis
description: Os formulários HTML5 usam o padrão de acessibilidade ARIA HTML5. Esses formulários oferecem suporte à navegação por guias e são certificados para serem compatíveis com leitores de tela comuns.
seo-description: Os formulários HTML5 usam o padrão de acessibilidade ARIA HTML5. Esses formulários oferecem suporte à navegação por guias e são certificados para serem compatíveis com leitores de tela comuns.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Criar formulários HTML5 acessíveis {#designing-accessible-html-forms}

Os formulários HTML5 usam o padrão de acessibilidade ARIA HTML5 para gerar formulários HTML acessíveis. Esses formulários oferecem suporte à navegação por guias (exceto o Mozilla FireFox) e são certificados para serem compatíveis com leitores de tela comuns. Para gerar um formulário HTML5 com bons recursos de acessibilidade, projete o modelo de formulário XFA com base em algumas diretrizes [de design](/help/forms/using/best-practices-for-html5-forms.md)básicas. As diretrizes de design incluem configurar a ordem de tabulação correta e fornecer o conteúdo de Texto falado para cada controle de formulário. O AEM Forms Designer oferece suporte à configuração desses atributos de controle de formulário para gerar um formulário PDF e HTML5 acessíveis.

*Observação: a navegação com guias não cobre campos protegidos, como campos de cálculo que exibem a soma dos valores. Para que o leitor de tela leia o valor de um campo protegido, coloque um campo vazio somente leitura na parte superior ou ao lado do campo protegido. Atribua o valor do campo protegido ao novo campo Somente leitura. O leitor de tela ou a navegação com guias pode selecionar esse campo somente leitura e falar como o valor do campo protegido.*

O AEM Forms Designer inclui várias opções de Texto falado que podem ser passadas para leitores de tela. Para cada objeto em um formulário, o usuário pode especificar uma das várias configurações para o texto do leitor de tela:

* Texto personalizado do leitor de tela, que pode ser definido usando a paleta Acessibilidade. Os autores podem anotar os nomes de botões e campos, bem como sua finalidade.
* Dicas de ferramentas, que podem ser definidas na paleta Acessibilidade.
* Legendas para campos no formulário.
* Nomes de objetos, conforme especificado na opção Nome da guia Vínculo.

![acessibilidade](assets/accessibility.png)

Quando várias opções, como dica de ferramenta, Texto de Reader de tela e Legenda, estiverem disponíveis em um controle de formulário, o Reader de tela usará apenas uma dessas propriedades. A ordem padrão é Texto Reader de tela personalizada, dica de ferramenta, Legenda e Nome. You can override the default order using the Screen Reader **Precedence** option in the Accessibility palette.
