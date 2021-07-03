---
title: Pesquisa de texto completo GQL
description: Explore o recurso de pesquisa de texto completo do GQL no AEM Assets. Use-o para pesquisar ativos com base em metadados específicos, como título, descrição e nome do autor.
contentOwner: AG
feature: Pesquisar,Metadados
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 2%

---

# Pesquisa de texto completo GQL {#gql-full-text-search}

Explore o recurso de pesquisa de texto completo do GQL no AEM Assets. Use-o para pesquisar ativos com base em metadados específicos, como título, descrição e nome do autor.

O recurso de pesquisa de texto completo do GQL permite pesquisar ativos com base em metadados específicos, como título, descrição, autor e assim por diante.

Para pesquisar um ativo com base em seus metadados, por exemplo, título, especifique a palavra-chave de metadados seguida de seu valor no painel de pesquisa. O recurso de pesquisa de texto completo do GQL buscará apenas os ativos cujos metadados correspondam exatamente ao valor correspondente inserido.

Por exemplo, para procurar ativos com o título &quot;Target&quot;, execute estas etapas:

## Pesquisar ativos {#searching-assets}

1. Na barra de ferramentas da interface do usuário do Assets, clique ou toque no ícone **[!UICONTROL Pesquisar]** para exibir a caixa Omnisearch.

   ![](assets/do-not-localize/chlimage_1.png)

1. Com o cursor na caixa Omnisearch, pressione Enter.
1. Clique ou toque no ícone de Navegação global para exibir o painel **[!UICONTROL Filtros]**.
1. Na caixa Pesquisa Omni , especifique o valor &quot;Target&quot;. Para limitar sua pesquisa a uma pasta específica, clique ou toque no ícone Procurar no painel Filtros e selecione a pasta. Nesse caso, a correspondência é pesquisada somente na pasta e nas subpastas abaixo dela.

   >[!NOTE]
   >
   >Também é possível realizar a pesquisa de texto completo na pasta. Nesse caso, você deve especificar um termo de pesquisa de texto completo que não esteja vazio.

   ![gql_search](assets/gql_search.png)

1. Pressione **[!UICONTROL Enter]**. A interface do usuário do AEM Assets exibe apenas os ativos cujo título corresponde exatamente ao &quot;Target&quot;.

O recurso de pesquisa de texto completo do GQL permite pesquisar ativos com base no seguinte:

* Consulta complexa criada ao combinar por meio de uma operação E, os valores especificados para vários campos de metadados (propriedades)
* Vários valores para um único campo de metadados
* Correspondências de subsequência de caracteres

O recurso de pesquisa de texto completo do GQL permite pesquisar ativos com base nas seguintes propriedades de metadados. Os nomes das propriedades (por exemplo, autor, título e assim por diante) e dos valores distinguem maiúsculas de minúsculas.

>[!NOTE]
>
>A pesquisa de texto completo do GQL funciona somente para predicados de texto completo.

| Propriedade | Formato de pesquisa (valor de aspecto) |
|---|---|
| [!UICONTROL Título] | title:John |
| [!UICONTROL Criador] | criador:John |
| [!UICONTROL Contribuinte] | colaborador:John |
| [!UICONTROL Local] | local:Índia |
| [!UICONTROL Descrição] | description: &quot;Imagem de exemplo&quot; |
| [!UICONTROL Ferramenta Criador] | criatortool: &quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL Proprietário de direitos autorais] | copyrights towner: &quot;Adobe Systems&quot; |
| [!UICONTROL Contribuinte] | colaborador:John |
| [!UICONTROL Termos de Uso ] | usageterms:&quot;CopyRights Reserved&quot; |
| [!UICONTROL Criado] | criado:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Expira Data] | expira:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL No horário] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Hora de desligar] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Intervalo de tempo]  (expira o dateontime, offtime) | campo de faceta: limite inferior..upperbound |
| [!UICONTROL Caminho] | /content/dam/&lt;nome da pasta> |
| [!UICONTROL Título do PDF] | pdftitle:&quot;Documento do Adobe&quot; |
| [!UICONTROL Assunto] | assunto: &quot;Formação&quot; |
| [!UICONTROL Tags] | Tags: &quot;Localização E Viagem&quot; |
| [!UICONTROL Tipo] | type: &quot;image\png&quot; |
| [!UICONTROL Largura da imagem] | largura:limite inferior..upperbound |
| [!UICONTROL Altura da imagem] | altura:limite inferior..upperbound |
| [!UICONTROL Person] | pessoa:John |

Estes são alguns exemplos de formatos de pesquisa para consultas complexas:

* Para exibir todos os ativos com vários campos de facetas (por exemplo: title=John Doe e ferramenta criadora = Adobe Photoshop):

til: ferramenta criadora do &quot;John Doe&quot; : Adobe&amp;ast;

* Para exibir todos os ativos quando o valor das facetas não for uma única palavra, mas uma frase (por exemplo: title=Scott Reynolds)

title: &quot;Scott Reynolds&quot;

* Para exibir ativos com vários valores de uma única propriedade (por exemplo: title=Scott Reynolds ou John Doe)

title: &quot;Scott Reynolds&quot; OU &quot;John Doe&quot;

* Para exibir ativos com valores de propriedade começando com uma string específica (por exemplo: título é Scott Reynolds)

title: &quot;Scott&quot;

* Para exibir ativos com valores de propriedade terminando com uma string específica (por exemplo: título é Scott Reynolds)

title: &quot;Reynolds&quot;

* Para exibir ativos com um valor de propriedade que contenha uma string específica (por exemplo: título = Sala de Reunião de Basileia)

Título: &quot;Reunião&quot;;

* Para exibir ativos que contêm uma string específica e têm um valor de propriedade específico (por exemplo: procure por Adobe de sequência em ativos com title=John Doe)

&amp;ast;Adobe&amp;ast; title: &quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>O caminho, limite, tamanho e ordem das propriedades não podem ser OUed com qualquer outra propriedade.
>
>A palavra-chave de uma propriedade gerada pelo usuário é seu rótulo de campo no editor de propriedades em minúsculas, com espaços removidos.


>[!NOTE]
>
>Se você gravar uma consulta JCR para pesquisar apenas subativos, os ativos referenciados correspondentes também serão exibidos junto com os subativos correspondentes.

A pesquisa de texto completo também é compatível com operadores como -, ^ e assim por diante. Para pesquisar essas letras como literais de string, coloque a expressão de pesquisa entre aspas duplas. Por exemplo, use &quot;Notebook - Beauty&quot; em vez de Notebook - Beauty.

## Aumentar a pesquisa {#boosting-search}

Você pode melhorar a relevância das palavras-chave para ativos específicos para ajudar a aumentar as pesquisas com base nas palavras-chave. Em outras palavras, as imagens para as quais você promove palavras-chave específicas são exibidas na parte superior dos resultados da pesquisa quando você pesquisa com base nessas palavras-chave.

1. Na interface do usuário do Assets, abra a página de propriedades do ativo para o qual deseja promover uma palavra-chave.
1. Alterne para a guia **[!UICONTROL Avançado]** e clique/toque em **[!UICONTROL Adicionar]** em **[!UICONTROL Elevar para palavras-chave de pesquisa]**.

   ![elevate_for_search](assets/elevate_for_search.png)

1. Na caixa **[!UICONTROL Promover de pesquisa]**, especifique uma palavra-chave para a qual deseja impulsionar a pesquisa da imagem e clique/toque em **[!UICONTROL Adicionar]**. Se necessário, especifique várias palavras-chave da mesma maneira.

   ![add_search_word](assets/add_search_word.png)

1. Clique/toque em **[!UICONTROL Salvar e fechar]**.
1. Procure a palavra-chave usando a caixa Omnisearch . O ativo para o qual você promoveu essa palavra-chave aparece entre os principais resultados de pesquisa.
