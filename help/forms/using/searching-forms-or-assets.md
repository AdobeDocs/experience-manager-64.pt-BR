---
title: Pesquisar formulários e ativos
seo-title: Pesquisar formulários e ativos
description: Você pode pesquisar formulários e ativos em sua instância AEM usando a pesquisa AEM. A pesquisa básica e avançada permite localizar rapidamente seus ativos.
seo-description: Você pode pesquisar formulários e ativos em sua instância AEM usando a pesquisa AEM. A pesquisa básica e avançada permite localizar rapidamente seus ativos.
uuid: db6970aa-910a-4190-9790-9ffbbdc8adcc
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: f7f19679-cfc2-4ac0-9a26-685fad09276f
translation-type: tm+mt
source-git-commit: db4d19e3af11f04369fc7f6a7c13377962f0650a
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 4%

---


# Pesquisar formulários e ativos {#searching-for-forms-and-assets}

É possível pesquisar por formulários ou ativos de formulário, usando uma string de texto ou uma string de texto junto com curingas. Você também pode restringir sua pesquisa usando os critérios disponíveis em várias categorias no painel Pesquisar.

Quando você seleciona um ou mais critérios e também especifica uma string de texto, a interseção do texto e dos critérios são retornados como resultados de pesquisa. Os resultados da pesquisa são tão bons quanto o formulário e os metadados do ativo fornecidos.

Clique em ![aem6forms_search](assets/aem6forms_search.png)para mostrar ou ocultar o painel de pesquisa.

## Pesquisa básica {#basic-search}

Uma pesquisa básica é a pesquisa padrão, executada sem especificar filtros. A AEM Forms realiza uma pesquisa de texto completo sobre propriedades de metadados.

Para executar uma pesquisa básica, insira o query de pesquisa no campo de texto e pressione a tecla de retorno. Você também pode inserir o caractere curinga (&amp;ast;) para corresponder a qualquer número de caracteres.

A Adobe Experience Manager pesquisa o texto inserido nas propriedades de metadados e retorna os resultados correspondentes. Se você digitar mais de uma palavra, a operação de pesquisa corresponderá ao texto completo para pesquisa.

Observe os seguintes pontos sobre a pesquisa básica:

* A pesquisa é realizada usando as propriedades de metadados do formulário e do ativo.
* Se você digitar mais de uma palavra, a operação de pesquisa corresponderá ao texto completo para pesquisa.
* A pesquisa não diferencia maiúsculas de minúsculas. Por exemplo, quando você digita `geometrixx`, os ativos com títulos `Geometrixx`, `GEOMETRIXX`e `GeoMetRixx` são exibidos nos resultados da pesquisa.

* Correspondências parciais de uma palavra não são suportadas. Para pesquisar usando strings parciais, use &amp;ast; coringa. Entretanto, se o query de pesquisa corresponder a uma palavra completa, o formulário ou ativo correspondente será exibido.
* Espaços extras são respeitados e não são aparados durante a pesquisa. Por exemplo, não `My form` é o mesmo query de pesquisa `My form`.

* Se os valores de dados e exibição dos campos nas propriedades de metadados forem diferentes, não será possível usar os valores de exibição como parâmetros de pesquisa. Por exemplo, não é possível pesquisar com base em um status, como Modificado ou Publicado, pois essas propriedades são armazenadas em um formato diferente.

## Advanced search {#advanced-search}

Nos critérios de pesquisa, além do query, você pode especificar alguns parâmetros de pesquisa para tornar a pesquisa básica mais eficiente e focalizada.

![Campo de pesquisa e parâmetros ou filtros para pesquisa AEM formulário e ativos](assets/search_forms_assets.png)

### Caminho do ativo {#asset-path}

Usando o filtro de caminho de ativo, você pode limitar os resultados da pesquisa ao diretório atual. Se a opção Pesquisar no diretório atual não estiver selecionada, os resultados da pesquisa conterão ativos do diretório base. Se a página atual não for um diretório e a opção &quot;pesquisar no diretório atual&quot; estiver selecionada, a pesquisa retornará os ativos presentes no diretório pai.

### Modificação de ativos {#asset-modification}

Selecione uma das opções a seguir para pesquisar por todos os ativos modificados dentro de um período de tempo específico.

| **Opção** | **Descrição** |
|---|---|
| Há duas horas | Pesquise todos os ativos que foram modificados nas últimas duas horas. |
| Uma semana atrás | Pesquise todos os ativos que foram modificados na última semana. |
| Há um mês | Pesquise todos os ativos que foram modificados no último mês. |
| Há um ano | Pesquise todos os ativos que foram modificados no último ano. |

### Status do ativo {#asset-status}

Você pode pesquisar ativos usando um dos seguintes status:

* **Publicado**: Pesquise todos os ativos publicados e não modificados após a publicação.

* **Não publicado**: Pesquise todos os ativos que nunca foram publicados.

* **Modificado**: Pesquise todos os ativos que são modificados ou não publicados após a publicação.

### Tipo de ativo {#asset-type}

Você pode selecionar qualquer número de tipos de ativos. A pesquisa retorna a união de todos os tipos de ativos selecionados.

<table> 
 <tbody>
  <tr>
   <th>Opção</th> 
   <th>Descrição</th> 
  </tr>
  <tr>
   <td>Modelo de formulário<br /> </td> 
   <td>Pesquise em todos os modelos de formulário.<br /> </td> 
  </tr>
  <tr>
   <td>Formulário PDF</td> 
   <td>Pesquise em todos os documentos PDF.</td> 
  </tr>
  <tr>
   <td>Documento</td> 
   <td>Pesquise em todos os documentos.</td> 
  </tr>
  <tr>
   <td>Formulário adaptativo<br /> </td> 
   <td>Pesquise em todos os formulários adaptativos.</td> 
  </tr>
  <tr>
   <td>Recurso</td> 
   <td>Pesquise em todos os recursos.<br /> </td> 
  </tr>
 </tbody>
</table>

### Tags {#tags}

As tags são etiquetas anexadas aos ativos para identificação. Ao pesquisar, selecione qualquer número de tags na lista suspensa ou adicione tags personalizadas, se necessário. Um resultado de pesquisa contém a interseção das tags selecionadas.
