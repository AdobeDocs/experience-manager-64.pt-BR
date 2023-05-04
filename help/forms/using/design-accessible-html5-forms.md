---
title: Criação de formulários HTML5 acessíveis
seo-title: Designing accessible HTML5 forms
description: Os formulários HTML5 usam o padrão de acessibilidade ARIA HTML5. Esses formulários são compatíveis com a navegação por guias e têm certificação de serem compatíveis com leitores de tela comuns.
seo-description: HTML5 forms use the ARIA HTML5 accessibility standard. These forms support tabbed navigation and are certified to be compatible with common screen readers.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: Mobile Forms
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 2%

---

# Criação de formulários HTML5 acessíveis {#designing-accessible-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os formulários HTML5 usam o padrão de acessibilidade ARIA HTML5 para gerar formulários HTML acessíveis. Esses formulários são compatíveis com a navegação por guias (exceto o Mozilla FireFox) e são certificados como compatíveis com leitores de tela comuns. Para gerar um formulário HTML5 com bons recursos de acessibilidade, crie o modelo de formulário XFA com base em alguns [diretrizes básicas de design](/help/forms/using/best-practices-for-html5-forms.md). As diretrizes de design incluem configurar a ordem de tabulação correta e fornecer o conteúdo de Texto falado para cada controle de formulário. O AEM Forms Designer oferece suporte à configuração desses atributos de controle de formulário para gerar um formulário Accessible PDF e HTML5.

*Observação:A navegação com guias não cobre campos protegidos, como campos de cálculo que exibem a soma dos valores. Para que o leitor de tela leia o valor de um campo protegido, coloque um campo Somente leitura vazio na parte superior ou ao lado do campo protegido. Atribua o valor do campo protegido ao novo campo Somente leitura. O leitor de tela ou a navegação por guias pode escolher esse campo somente leitura e retorná-lo como o valor do campo protegido.*

O AEM Forms Designer inclui várias opções de Texto falado que podem ser passadas para leitores de tela. Para cada objeto em um formulário, o usuário pode especificar uma das várias configurações para o texto do leitor de tela:

* Texto personalizado do leitor de tela, que pode ser definido usando a paleta Acessibilidade. Os autores podem anotar os nomes dos botões e campos, bem como sua finalidade.
* Dicas de ferramentas, que podem ser definidas na paleta Acessibilidade.
* Legendas para campos no formulário.
* Nomes de objetos, conforme especificado na opção Nome da guia Vínculo.

![acessibilidade](assets/accessibility.png)

Quando várias opções, como dica de ferramenta, Reader de tela e Legenda estão disponíveis em um controle de Formulário, o Reader de tela usa apenas uma dessas propriedades. A ordem padrão é Texto personalizado de Reader de tela, dica de ferramenta, Legenda e Nome. Você pode substituir a ordem padrão usando o Reader da tela **Precedência** na paleta Acessibilidade.
