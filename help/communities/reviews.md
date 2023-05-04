---
title: Usando o Resumo de Revisões e Revisões (Exibição)
seo-title: Using Reviews and Reviews Summary (Display)
description: Adicionar os componentes Revisões e Resenhas do Resumo a uma página
seo-description: Adding the Reviews and Reviews Summary components to a page
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
exl-id: 5aae7744-73cc-472b-a4e6-ecd88284b70c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 1%

---

# Usando o Resumo de Revisões e Revisões (Exibição) {#using-reviews-and-reviews-summary-display}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O `Reviews`componente é um composto de [ `Comments`](comments.md) e [ `Rating`](rating.md) componentes prontos para uso.

O `Reviews Summary (Display)` componente fornece um resumo de uma instância ativa ou fechada de um `Reviews` componente para exibição em outro lugar do site.

>[!NOTE]
>
>A publicação anônima de uma revisão não é suportada. Os visitantes do site devem se registrar (se tornar um membro) e fazer logon para participar. O visitante conectado pode atualizar sua revisão a qualquer momento.

## Adicionar uma revisão a uma página {#adding-a-review-to-a-page}

Para adicionar uma `Reviews` para uma página no modo autor, use o navegador de componentes para localizar `Communities / Reviews` e arraste-a para o local em uma página, como uma posição relativa ao recurso que os usuários devem analisar.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](reviews-basics.md#essentials-for-client-side) são incluídos, é assim que a variável `Reviews`será exibido.

![chlimage_1-340](assets/chlimage_1-340.png)

## Configuração de Revisões {#configuring-reviews}

Selecione o `Reviews` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-341](assets/chlimage_1-341.png)

Em **[!UICONTROL Classificações permitidas]** , especifique a lista completa de classificações a serem mostradas aos membros. A primeira notação deve ser global/geral, uma vez que é a notação que fornece a notação média para a `Review Summary (Display)` componente. As próximas duas classificações na configuração padrão devem receber um título diferente de &quot;Subrating 1&quot; ou &quot;Subrating 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Classificações permitidas]**

   Uma lista de classificações que um membro pode escolher.

   Use a seta para cima, a seta para baixo e os botões Excluir para modificar as seleções visíveis.

   Clique em **[!UICONTROL Adicionar item]** para adicionar outra opção de classificação.

Em **[!UICONTROL Classificações necessárias]** , insira novamente os itens da lista de **[!UICONTROL Classificações permitidas]** que devem ser classificadas. Se um item for especificado somente na guia Classificações permitidas , ele poderá ficar sem marca quando for enviado pelo membro.

No site, as classificações necessárias são marcadas com um asterisco. Se um item for necessário e não estiver marcado, uma mensagem será exibida para o membro e a submissão será negada até que todas as classificações necessárias sejam marcadas.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Classificações necessárias]**

   Um subconjunto de classificações permitidas, indicando quais classificações são necessárias.

   Use a seta para cima, a seta para baixo e os botões Excluir para modificar as seleções visíveis.

   Clique em **[!UICONTROL Adicionar item]** para adicionar outra opção de resposta.

>[!NOTE]
>
>Se um item for inserido na **[!UICONTROL Classificações necessárias]** que não é especificada na variável **[!UICONTROL Classificações permitidas]** , então não é incluído nos itens para classificar.

Em **[!UICONTROL Resenhas]** , especifique como as revisões são tratadas.

![chlimage_1-344](assets/chlimage_1-344.png)

* **[!UICONTROL Permitir respostas]**
Se marcada, permita respostas a revisões. O padrão está desmarcado.

* **[!UICONTROL Fechado]**
Se marcada, a revisão é fechada para novas revisões e respostas. O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, permita que os anexos do arquivo sejam carregados para a revisão. O padrão está desmarcado.

* **[!UICONTROL Tamanho máximo do arquivo]**
Relevante apenas se **[!UICONTROL Permitir uploads de arquivo]** está marcada. Este campo limita o tamanho (em bytes) de um arquivo carregado. O padrão é 10 MB.

* **[!UICONTROL Extensão Máx. da Mensagem]**
Número máximo de caracteres que podem ser inseridos na caixa de texto. O padrão é 4096 caracteres.

* **[!UICONTROL Tipos de arquivo permitidos]**
Relevante apenas se **[!UICONTROL Permitir uploads de arquivo]** está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não serão permitidos. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Editor de Rich Text]**
Se marcada, as publicações podem ser inseridas com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir votação]**
Se marcada, inclua o recurso Votação de um tópico. O padrão está desmarcado.

Em **[!UICONTROL Moderação do usuário]** , especifique como as revisões publicadas são gerenciadas. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Pré-moderação]**
Se marcada, as revisões devem ser aprovadas antes de serem exibidas em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Excluir Revisões]**
Se marcada, o membro que postou a revisão terá a capacidade de excluí-la. O padrão está desmarcado.

* **[!UICONTROL Negar Revisões]**
Se marcada, permita que os moderadores neguem as revisões. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir Revisões]**
Se marcada, permita que os moderadores fechem e reabram as revisões. O padrão está desmarcado.

* **[!UICONTROL Revisões de Sinalizador]**
Se marcada, permita que os membros sinalizem revisões como inapropriadas. O padrão está desmarcado.

* **[!UICONTROL Lista de Motivos do Sinalizador]**
Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para marcar uma revisão como inadequada. O padrão está desmarcado.

* **[!UICONTROL Motivo do Sinalizador Personalizado]**
Se marcada, permita que os membros insiram seu próprio motivo para marcar uma revisão como inadequada. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Insira o número de vezes que uma revisão deve ser sinalizada por membros antes que os moderadores sejam notificados. O padrão é uma vez (1).

* **[!UICONTROL Limite de sinalização]**
Insira o número de vezes que uma revisão deve ser sinalizada antes de ser ocultada da exibição pública. Esse número deve ser maior ou igual a **[!UICONTROL Limite de moderação]**. O padrão é 5.

### Adicionar um resumo de revisão (exibição) a uma página {#adding-a-review-summary-display-to-a-page}

Para adicionar uma `Reviews Summary (Display)` para uma página no modo autor, localize o componente

* `Communities / Reviews Summary (Display)`

e arraste-o para o local em uma página onde um resumo de uma revisão ativa ou fechada deve ser exibido.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](reviews-basics.md#essentials-for-client-side) são incluídos, é assim que a variável `Reviews Summary (Display)`será exibido.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>A &quot;Média&quot; reflete os votos do primeiro item listado nas guias Classificações permitidas da revisão que está sendo resumida.

### Configuração do Resumo das Revisões (Exibição) {#configuring-reviews-summary-display}

Selecione o `Reviews Summary (Display)` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-347](assets/chlimage_1-347.png)

Em **[!UICONTROL Resumo da revisão]** guia

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   entre ou navegue até a instância localizada do `reviews`componente para resumir, por exemplo, se adicionado à Página da Web da [Site Geometrixx Engage,](getting-started.md) o caminho seria:

   /content/sites/engagement/en/page/jcr:content/content/primary/views

* `Include histogram`

   Se marcada, inclua a exibição de um gráfico de barras indicando quantos de cada classificação de estrela há nas revisões que estão sendo resumidas. O padrão está desmarcado.

### Alterar para um tipo de revisão personalizada {#changing-to-a-custom-review-type}

O componente Revisões usa o Sistema de comentários.

Ao alterar o Tipo de recurso do comentário, o sistema de comentários não gerará mais uma instância de um comentário usando o padrão, mas uma que foi personalizada (estendida) pelos desenvolvedores.

Quando os tipos de recursos personalizados forem conhecidos, insira [Modo Design](../../help/sites-authoring/default-components-designmode.md) e clique duas vezes no `Comments` para abrir uma caixa de diálogo com uma guia adicional.

Em **[!UICONTROL Tipos de recursos]** , especifique o resourceType personalizado para novas instâncias do `Comments or Voting`componentes:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Tipo de recursos de comentários]**

   Navegue até o resourceType de um `comment`componente (comentário único) em /apps. Por exemplo, `/apps/social/commons/components/hbs/comments/comment`

   Esse recurso identificará o resourceType do UGC criado quando um visitante postar um comentário.

* **[!UICONTROL Tipo de recursos para pesquisa]**

   Navegue até o resourceType de um `voting`componente em /apps. Por exemplo, `/apps/social/components/hbs/voting`

   Esse recurso identificará o tipo de recurso do UGC criado quando um visitante posta um voto.

* **[!UICONTROL Tipo de Recurso do Sistema de Comentários]**

   Navegue até o resourceType de um `comments`componente (Sistema de comentários) em /apps. Deixe em branco, a menos que o modelo da página [inclui dinamicamente](scf.md#add-or-include-a-communities-component) o Sistema de comentários no script subjacente em vez de ser adicionado à página como um recurso (nó de comentários). Saiba mais ao ler sobre o [{{include}} auxiliar](handlebars-helpers.md#include)

## Experiência de visitante do site {#site-visitor-experience}

### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar as tarefas de moderação permitidas pela configuração do componente, independentemente de quem criou a revisão.

### Membros {#members}

Quando o visitante do site está conectado, dependendo da configuração, ele pode

* Publicar uma nova revisão
* Editar sua própria revisão
* Excluir sua própria revisão
* Sinalizar comentários de revisão de outras pessoas

Só é permitida uma classificação por membro. O membro pode alterar a sua notação a qualquer momento.

### Anônimo {#anonymous}

Os visitantes do site que não estiverem conectados podem ler somente as revisões postadas, traduzi-las se houver suporte, mas não podem adicionar uma classificação ou uma revisão, nem sinalizar os comentários de revisão de outras pessoas.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos da revisão](reviews-basics.md) página para desenvolvedores.

Para obter a moderação dos comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para obter a tradução de comentários postados, consulte [Tradução de conteúdo gerado pelo usuário](translate-ugc.md).
