---
title: Recurso do Fórum de Perguntas e Respostas
seo-title: Q&A Forum Feature
description: Adicionar o recurso de fórum QnA a uma página
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 1%

---

# Recurso do Fórum de Perguntas e Respostas {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso de fórum QnA (perguntas e respostas) fornece uma área para os membros da comunidade fazerem e responderem perguntas:

* Criar novas perguntas
* Imagens embutidas (com suporte para arrastar e soltar)
* Exibir e responder perguntas
* Pesquisar uma pergunta
* Ajuda a moderar o conteúdo de QnA
* Identificar as melhores respostas
* Mover perguntas QnA de uma página para outra

Esta seção da documentação descreve

* Adicionar o recurso de fórum QnA a um site AEM
* Configurações para o `QnA`componente

## Adicionar um fórum de perguntas e respostas a uma página {#adding-a-q-a-forum-to-a-page}

Para adicionar uma `QnA` para uma página no modo autor, use o navegador de componentes para localizar `Communities / QnA` e arraste-o para o local em uma página onde o fórum QnA deve aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](qna-essentials.md#essentials-for-client-side) são incluídos, é assim que a variável `QnA` componente será exibido:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configuração de QnA {#configuring-qna}

Selecione o `QnA` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique as configurações dos tópicos (perguntas) e respostas (respostas):

* **[!UICONTROL Tópicos por página]**
Define o número de perguntas/postagens exibidas por página. O padrão é 10.

* **[!UICONTROL Moderado]**
Se marcada, a publicação de tópicos e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**
Se marcada, o fórum é fechado para novas perguntas e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor de Rich Text]**
Se marcada, tópicos e comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir marcação]**
Se marcada, permitir que membros adicionem rótulos de tag à publicação (consulte **[!UICONTROL Campo de tag]** ). O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, permita que anexos de arquivo sejam adicionados à pergunta ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Tamanho máximo do arquivo]**
Relevante apenas se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivo permitidos]**
Relevante apenas se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não poderão ser carregados. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem anexada]**
Relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir Seguindo]**
Se marcada, inclua o seguinte recurso para publicações do fórum, que permite que os membros sejam [notificado](notifications.md) de novos posts. O padrão está desmarcado.

* **[!UICONTROL Permitir Prender]**
Se marcada, os tópicos do fórum podem ser fixados ao topo da lista de tópicos. O padrão está desmarcado.

* **[!UICONTROL Permitir assinaturas por email]**
Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([assinatura](subscriptions.md)). Exige `Allow Following` a verificar e [email configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Permitir respostas]**
Se marcada, permita respostas para comentários postados na pergunta. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e tópicos]**
Se marcada, permita que os membros excluam os comentários e perguntas publicados. O padrão está desmarcado.

* **[!UICONTROL Permitir votação]**
Se marcada, inclua o recurso Votação com uma pergunta. O padrão está desmarcado.

* **[!UICONTROL Mover A Resposta Selecionada Para O Topo]**
Se marcada, a primeira resposta mostrada é uma resposta selecionada. O padrão está marcado.

* **[!UICONTROL Exibir emblemas]**
Se marcada, exibir ganhado e atribuído [emblemas](implementing-scoring.md) com a entrada de um membro no blog. O padrão está desmarcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
se marcada, a ideia poderá ser identificada como [conteúdo em destaque](featured.md). O padrão está desmarcado.

#### Guia Moderação do usuário {#user-moderation-tab}

Em **[!UICONTROL Moderação do usuário]** , especifique como os tópicos publicados (perguntas) e as respostas (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

* **[!UICONTROL Negar respostas]**
Se marcada, os moderadores de membros confiáveis poderão negar as respostas publicadas e impedir que elas apareçam no fórum público de perguntas e respostas. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir Tópicos]**
Se marcada, os moderadores de membros confiáveis podem fechar uma pergunta (tópico) para outras edições e respostas, e também podem reabrir uma pergunta. O padrão está desmarcado.

* **[!UICONTROL Mover tópicos]**
Se marcada, permita que os moderadores do lado da publicação movam perguntas. O padrão está desmarcado.

* **[!UICONTROL Sinalizar publicações]**
Se marcada, permita que os membros sinalizem as perguntas ou respostas de outras pessoas como inapropriadas. O padrão está desmarcado.

* **[!UICONTROL Lista de Motivos do Sinalizador]**
Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para marcar uma pergunta ou resposta como inadequada. O padrão está desmarcado.

* **[!UICONTROL Motivo do Sinalizador Personalizado]**
Se marcada, permita que os membros insiram seu próprio motivo para marcar uma pergunta ou resposta como inadequada. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Insira o número de vezes que uma pergunta ou resposta deve ser sinalizada por membros antes que os moderadores sejam notificados. O padrão é 1 ( uma vez).

* **[!UICONTROL Limite de sinalização]**
Insira o número de vezes que uma pergunta ou resposta deve ser sinalizada antes de ser ocultada da exibição pública. Se definida como -1, a pergunta ou resposta sinalizada nunca será ocultada da exibição pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

#### Guia Campo de tag {#tag-field-tab}

Em **[!UICONTROL Campo de tag]** , as tags que podem ser aplicadas, se permitidas sob a variável **[!UICONTROL Configurações]** , são limitadas de acordo com os namespaces escolhidos.

* **[!UICONTROL Espaços de nomes permitidos]**
Relevante se 
`Allow Tagging` é verificada sob o **Configurações** guia . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite de Sugestão]**
Insira o número de tags a serem exibidas como sugestão para o membro postando no fórum. Um valor de 
`-1` significa que não há limites. O padrão é 0.

#### Guia Configurações de classificação {#sort-settings-tab}

Em **[!UICONTROL Classificar configurações]** , especifique como os comentários publicados são classificados quando exibidos.

* **[!UICONTROL Ordenar por]**
Marque todas as seleções de classificação permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. O padrão é `Newest, Oldest, Last Updated`.

* **[!UICONTROL Definir como padrão]**
Puxe para baixo para selecionar uma das opções de classificação marcadas que serão exibidas como padrão. O padrão é 
`Newest`.

* **[!UICONTROL Selecionar opções de tempo para classificação do Analytics]**
Puxe para baixo para selecionar um dos 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. O padrão é `All`.

## Experiência de visitante do site {#site-visitor-experience}

### Identificação de respostas {#identifying-answers}

Uma resposta pode ser marcada como uma resposta correta ou útil usando o `Select Answer` botão. Depois que uma Pergunta é marcada como Respondida, outra resposta não poderá ser selecionada até que a primeira seja desmarcada usando o `Unmark Chosen Answer`botão.

Depois de selecionado como uma resposta viável, ele pode ser desmarcado usando o `Unmark Chosen Answer` botão.

Depois que uma resposta é selecionada como resposta viável, uma indicação de que a pergunta foi `Answered`é exibida ao lado do tópico da pergunta na página principal do QnA.

### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar as tarefas de moderação permitidas pela configuração do componente, independentemente de quem criou a pergunta ou resposta.

Eles também têm a capacidade de identificar respostas.

### Membros {#members}

Quando o visitante do site está conectado, dependendo da configuração, ele pode

* Postar uma nova pergunta
* Editar ou excluir perguntas criadas por eles
* Pode também sinalizar perguntas ou respostas de outras pessoas
* Pode identificar respostas para perguntas criadas por eles

### Anônimo {#anonymous}

Os visitantes do site que não estiverem conectados só poderão ler perguntas e respostas publicadas, traduzi-las se houver suporte, mas não poderão adicionar perguntas nem respostas, nem sinalizar publicações de outros.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos de QnA](qna-essentials.md) página para desenvolvedores.

Para obter moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).
