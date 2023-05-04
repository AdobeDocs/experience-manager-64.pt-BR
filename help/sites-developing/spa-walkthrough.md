---
title: Introdução e passo a passo do SPA
seo-title: SPA Introduction and Walkthrough
description: Este artigo apresenta os conceitos de um SPA e aborda o uso de um SPA básico para criação, mostrando como ele está relacionado ao editor de SPA integrado do AEM.
seo-description: This article introduces the concepts of a SPA and walks through using a basic SPA application for authoring, showing how it relates to the underlying AEM SPA Editor.
uuid: 97a199af-b684-433d-b7b1-a8378513cb3d
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 77b42490-15db-41d5-9757-17009f1c1efd
exl-id: 85179139-a841-42b0-8590-d1fb88c1ebbf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 59%

---

# Introdução e passo a passo do SPA{#spa-introduction-and-walkthrough}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Aplicativos de página única (SPAs) podem oferecer experiências interessantes para usuários de sites. Os desenvolvedores desejam criar sites usando estruturas de SPA, e os autores desejam editar o conteúdo de um site criado usando essas estruturas diretamente no AEM.

O editor de SPA oferece uma solução abrangente para permitir o uso de SPAs no AEM. Este artigo aborda o uso de um SPA básico para criação e mostra como ele se relaciona ao editor de SPA integrado do AEM.

>[!NOTE]
>
>O recurso Editor de aplicativo de página única (SPA) requer AEM 6.4 service pack 2 ou mais recente.
>
>O Editor de SPA é a solução recomendada para projetos que exigem renderização do lado do cliente baseada em SPA estrutura (por exemplo, Reagir ou Angular).

## Introdução {#introduction}

### Objetivo do artigo {#article-objective}

Este artigo apresenta os conceitos básicos sobre SPAs antes de conduzir o leitor por um passo a passo do editor de SPA, usando um SPA simples para demonstrar a edição básica de conteúdo. Em seguida, ele se aprofunda na construção da página e em como o SPA se relaciona e interage com o editor de SPA do AEM.

A meta desta introdução e passo a passo é demonstrar a um desenvolvedor do AEM por que SPAs são relevantes, como eles geralmente funcionam, como um SPA é manipulado pelo editor de SPA do AEM e como ele é diferente de um aplicativo padrão do AEM.

A apresentação é baseada na funcionalidade de AEM padrão e no aplicativo We.Retail Journal de amostra. Os seguintes requisitos devem ser atendidos:

* [AEM versão 6.4 com service pack 2 ou mais recente](/help/release-notes/sp-release-notes.md)
* [Instale o aplicativo We.Retail Journal de amostra disponível no GitHub aqui.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>[!CAUTION]
>
>Este documento usa o [Aplicativo de diário We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) apenas para fins de demonstração. Ele não deve ser utilizado ao trabalhar em projetos.
>
>Qualquer projeto do AEM deve utilizar o [Arquétipo de projeto do AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=pt-BR), que aceita projetos SPA que usam o React ou Angular e utiliza o SDK do SPA.

### O que é um SPA? {#what-is-a-spa}

Um aplicativo de página única (SPA) é diferente de uma página convencional, no sentido de que ele é renderizado no lado do cliente e orientado principalmente por Javascript, dependendo das chamadas do Ajax para carregar dados e atualizar dinamicamente a página. A maior parte ou todo o conteúdo é recuperado uma vez em um único carregamento de página, com os recursos adicionais sendo carregados de forma assíncrona conforme necessário, com base na interação do usuário com a página.

Isso reduz a necessidade de atualizações de página e apresenta uma experiência ao usuário que é contínua, rápida e se parece mais com uma experiência de aplicativo nativo.

O editor de SPA do AEM permite que desenvolvedores de front-end criem SPAs que possam ser integrados a um site do AEM, possibilitando que os autores de conteúdo editem o conteúdo do SPA tão facilmente quanto qualquer outro conteúdo do AEM.

### Por que um SPA? {#why-a-spa}

Devido a ser mais rápido, fluido e semelhante a um aplicativo nativo, um SPA apresenta uma experiência muito atrativa não apenas para o visitante da página da web, mas também para profissionais de marketing e desenvolvedores, devido à natureza do funcionamento dos SPAs.

![screen_shot_2018-08-20at135550](assets/screen_shot_2018-08-20at135550.png)

**Visitantes**

* Os visitantes desejam experiências nativas quando interagem com o conteúdo.
* Dados claros informam que quanto mais rapidamente uma página é exibida, maior é a possibilidade de uma conversão.

**Profissionais de marketing**

* Os profissionais de marketing desejam oferecer experiências nativas e relevantes para atrair visitantes a se envolverem totalmente com o conteúdo.
* A personalização pode tornar essas experiências ainda mais atrativas.

**Desenvolvedores**

* Os desenvolvedores desejam uma separação clara entre o conteúdo e a apresentação.
* Uma boa separação torna o sistema mais extensível, além de permitir o desenvolvimento independente do front-end.

### Como funciona um SPA? {#how-does-a-spa-work}

A ideia principal por trás de um SPA é que as chamadas e a dependência em um servidor sejam reduzidas para minimizar os atrasos causados pelas chamadas do servidor, de modo que o SPA se aproxime da capacidade de resposta de um aplicativo nativo.

Em uma página da web tradicional e sequencial, somente os dados necessários para a página imediata são carregados. Isso significa que quando o visitante se move para outra página, o servidor é chamado para os recursos adicionais. As chamadas adicionais podem ser necessárias, pois o visitante interage com elementos na página. Essas várias chamadas podem criar uma sensação de defasagem ou atraso na página, pois ela precisa acompanhar as solicitações do visitante.

![screen_shot_2018-08-20at140449](assets/screen_shot_2018-08-20at140449.png)

Para uma experiência mais fluida, que se aproxima do que um visitante espera de aplicativos móveis e nativos, um SPA carrega todos os dados necessários para o visitante na primeira carga. Embora possa ser um pouco mais demorado no início, isso elimina a necessidade de chamadas de servidor adicionais.

Ao renderizar no lado do cliente, o elemento da página reage mais rapidamente e as interações com a página pelo visitante são imediatas. Qualquer dado adicional que possa ser necessário é chamado de forma assíncrona para maximizar a velocidade da página.

>[!NOTE]
>
>Para obter detalhes técnicos sobre como SPA trabalhar no AEM, consulte o artigo [Introdução ao SPA no AEM](/help/sites-developing/spa-getting-started-react.md).
>
>Para uma análise mais detalhada do design, arquitetura e fluxo de trabalho técnico do Editor de SPA, consulte o artigo [Visão geral do editor de SPA](/help/sites-developing/spa-overview.md).

## Experiência de edição de conteúdo com SPA {#content-editing-experience-with-spa}

Quando uma SPA é criada para aproveitar o Editor de SPA de AEM, o autor de conteúdo não percebe diferença ao editar e criar conteúdo. A funcionalidade comum do AEM pode ser utilizada e nenhuma alteração no fluxo de trabalho do autor é necessária.

>[!NOTE]
>
>A apresentação é baseada na funcionalidade de AEM padrão e no aplicativo We.Retail Journal de amostra. Os seguintes requisitos devem ser atendidos:
>
>* [AEM versão 6.4 com service pack 2](/help/release-notes/sp-release-notes.md)
>* [Instale o aplicativo We.Retail Journal de amostra disponível no GitHub aqui.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)
>


1. Edite o aplicativo We.Retail Journal em AEM.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at142533](assets/screen_shot_2018-06-07at142533.png)

1. Selecione um componente de cabeçalho e observe que uma barra de ferramentas aparece como para qualquer outro componente. Selecione **[!UICONTROL Editar]**.

   ![screen_shot_2018-06-07at142937](assets/screen_shot_2018-06-07at142937.png)

1. Edite o conteúdo normalmente no AEM e observe que as alterações são mantidas.

   ![screen_shot_2018-06-07at143419](assets/screen_shot_2018-06-07at143419.png)

   >[!NOTE]
   >Consulte a [Visão geral do editor de SPA](spa-overview.md#requirements-limitations) para obter mais informações sobre o editor de texto em vigor e o SPA.

1. Use o Navegador de ativos para arrastar e soltar uma nova imagem em um componente de imagem.

   ![screen_shot_2018-06-07at143530](assets/screen_shot_2018-06-07at143530.png)

1. A alteração é mantida.

   ![screen_shot_2018-06-07at143732](assets/screen_shot_2018-06-07at143732.png)

Outras operações de criação são permitidas, como arrastar e soltar componentes adicionais na página, reorganizar componentes e modificar o layout, assim como acontece em qualquer outro aplicativo do que não seja um SPA.

>[!NOTE]
>
>O editor de SPA não modifica o DOM do aplicativo. O próprio SPA é responsável pelo DOM.
>
>Para ver como isso funciona, prossiga para a próxima seção deste artigo: [SPAs e o editor de SPA do AEM](/help/sites-developing/spa-walkthrough.md#spa-apps-and-the-aem-spa-editor).

## SPAs e o editor de SPA do AEM {#spa-apps-and-the-aem-spa-editor}

Usar o comportamento de um SPA para o usuário final e, em seguida, inspecionar a página de SPA ajuda a entender melhor como um aplicativo SAP funciona com o Editor de SPA em AEM.

### Usando um SPA {#using-an-spa-application}

1. Carregue o aplicativo We.Retail Journal no servidor de publicação ou usando a opção **[!UICONTROL Exibir como publicado]** do **Informações da página** no editor de páginas.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-08at102650](assets/screen_shot_2018-06-08at102650.png)

   Observe a estrutura das páginas, incluindo a navegação para páginas filhas, widget de clima e artigos.

1. Navegue até uma página secundária usando o menu e veja que a página é carregada imediatamente sem a necessidade de uma atualização.

   ![screen_shot_2018-06-08at102815](assets/screen_shot_2018-06-08at102815.png)

1. Abra as ferramentas do desenvolvedor incorporadas ao seu navegador e monitore a atividade da rede à medida que navega pelas páginas secundárias.

   ![screen_shot_2018-06-08at103922](assets/screen_shot_2018-06-08at103922.png)

   Há muito pouco tráfego ao mudar de uma página para outra no aplicativo. A página não é recarregada e somente as novas imagens são solicitadas.

   O SPA gerencia o conteúdo e o roteamento totalmente no lado do cliente.

Mas se a página não é recarregada ao navegar pelas páginas secundárias, como ela é carregada?

A próxima seção, [Carregando um aplicativo SPA](/help/sites-developing/spa-walkthrough.md#loading-an-spa-application), aprofunda-se nos mecanismos de carregamento de SPA e como o conteúdo pode ser carregado de forma síncrona e assíncrona.

### Carregar um SPA {#loading-an-spa-application}

1. Se ainda não tiver sido carregado, carregue o aplicativo We.Retail Journal no servidor de publicação ou usando a opção **[!UICONTROL Exibir como publicado]** do **Informações da página** no editor de páginas.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at144736](assets/screen_shot_2018-06-07at144736.png)

1. Use a ferramenta incorporada do seu navegador para visualizar a fonte da página.
1. Observe que o conteúdo da fonte é extremamente limitado.

   ```
   <!DOCTYPE HTML>
   <html lang="en-CH">
       <head>
       <meta charset="UTF-8">
       <title>We.Retail Journal</title>
   
       <meta name="template" content="we-retail-react-template"/>
   
   <link rel="stylesheet" href="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.css" type="text/css">
   
   <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
   
   </head>
       <body class="page basicpage">
   
   <div id="page"></div>
   
   <script type="text/javascript" src="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.js"></script>
   
       </body>
   </html>
   ```

   A página não possui conteúdo em seu corpo. Ele é formado principalmente por folhas de estilos e uma chamada para um script React, `we-retail-journal-react.js`.

   Esse script React é o driver principal desse aplicativo e é responsável pela renderização de todo o conteúdo.

1. Use as ferramentas internas do seu navegador para inspecionar a página. Veja o conteúdo do DOM totalmente carregado.

   ![screen_shot_2018-06-07at151848](assets/screen_shot_2018-06-07at151848.png)

1. Alterne para a guia Rede no Inspetor e recarregue a página.

   Ignorando solicitações de imagem, observe que os recursos primários carregados para a página são a própria página, o CSS, o React Javascript, suas dependências, bem como os dados JSON da página.

   ![screen_shot_2018-06-07at152155](assets/screen_shot_2018-06-07at152155.png)

1. Carregue o `react.model.json` em uma nova guia.

   `/content/we-retail-journal/react.model.json`

   ![screen_shot_2018-06-07at152636](assets/screen_shot_2018-06-07at152636.png)

   O editor de SPA do AEM aproveita os [serviços de conteúdo do AEM](/help/assets/content-fragments.md) para fornecer todo o conteúdo da página como um modelo JSON.

   Ao implementar interfaces específicas, os modelos do Sling fornecem as informações necessárias para o SPA. A entrega dos dados JSON é delegada de cima para baixo a cada componente (da página, ao parágrafo, ao componente etc.).

   Cada componente escolhe o que expõe e como é renderizado (no lado do servidor com HTL ou no lado do cliente com o React). É claro que este artigo se concentra na renderização do lado do cliente com o React.

1. O modelo também pode agrupar as páginas para que elas sejam carregadas de forma síncrona, reduzindo o número de recarregamentos de página necessários.

   No exemplo do We.Retail Journal, a variável `home`, `blog`e `aboutus` as páginas são carregadas de forma síncrona, já que os visitantes normalmente visitam todas essas páginas. No entanto, a variável `weather` é carregada de forma assíncrona, já que os visitantes têm menos probabilidade de visitá-la.

   Esse comportamento não é obrigatório e é totalmente configurável.

   ![screen_shot_2018-06-07at153945](assets/screen_shot_2018-06-07at153945.png)

1. Para ver essa diferença de comportamento, recarregue a página  e limpe as atividades de rede do inspetor. Navegue até o blog e as páginas sobre nós no menu da página e veja se não há nenhum relatório de atividade de rede.

   Navegue até a página do tempo e veja se a variável `weather.model.json` é chamado de forma assíncrona.

   ![screen_shot_2018-06-07at155738](assets/screen_shot_2018-06-07at155738.png)

### Interação com o editor de SPA {#interaction-with-the-spa-editor}

Usando o exemplo de aplicativo We.Retail Journal, está claro como o aplicativo se comporta e é carregado quando publicado, aproveitando os serviços de conteúdo para a entrega de conteúdo JSON, bem como o carregamento assíncrono de recursos.

Além disso, para o autor de conteúdo, a criação de conteúdo no editor de SPA é realizada sem interrupções no AEM.

Na seção a seguir, exploraremos o contrato que permite que o editor de SPA relacione componentes dentro do SPA aos componentes do AEM, o que garante essa experiência de edição contínua.

1. Carregue o aplicativo We.Retail Journal no editor e alterne para **Visualizar** modo.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

1. Usando as ferramentas de desenvolvedor incorporadas do seu navegador, inspecione o conteúdo da página. Usando a ferramenta de seleção, selecione um componente editável na página e visualize os detalhes do elemento.

   Observe que o componente tem um novo atributo de dados `data-cq-data-path`.

   ![screen_shot_2018-06-08at095124](assets/screen_shot_2018-06-08at095124.png)

   Por exemplo

   `data-cq-data-path="root/responsivegrid/paragraph_1`

   Esses caminhos permitem a recuperação e a associação do objeto de configuração de contexto de edição de cada componente.

   Esse é o único atributo de marcação necessário para que o editor reconheça esse componente como editável no SPA. Com base nesse atributo, o editor de SPA determinará qual configuração editável está associada ao componente, para que os elementos (quadro, barra de ferramentas etc.) corretos sejam carregados.

   Alguns nomes de classe específicos também são adicionados para marcar espaços reservados e para a funcionalidade de arrastar e soltar ativos.

   >[!NOTE]
   >
   >Essa é uma alteração no comportamento de páginas renderizadas do lado do servidor no AEM, onde há uma `cq` elemento inserido para cada componente editável.
   >
   >Essa abordagem no SPA remove a necessidade de inserir elementos personalizados, confiando apenas em um atributo de dados adicional, tornando a marcação mais simples para o desenvolvedor principal.

## Próximas etapas {#next-steps}

Agora que você entende a experiência de edição de SPA no AEM e como um SPA se relaciona ao editor de SPA, aprofunde-se ainda mais para entender como um SPA é criado.

* [Introdução ao SPA no AEM](/help/sites-developing/spa-getting-started-react.md) mostra como um SPA básico é criado para funcionar com o Editor de SPA no AEM
* A [Visão geral do editor de SPA](/help/sites-developing/spa-overview.md) aborda em detalhes o modelo de comunicação do AEM e do SPA.
* O artigo [Desenvolvimento de SPAs para o AEM](/help/sites-developing/spa-architecture.md) descreve como envolver desenvolvedores de front-end no desenvolvimento de um SPA para o AEM e como os SPAs interagem com a arquitetura do AEM.
