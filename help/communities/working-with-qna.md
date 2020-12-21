---
title: Recurso do fórum de perguntas e respostas
seo-title: Recurso do fórum de perguntas e respostas
description: Adicionar o recurso de fórum QnA a uma página
seo-description: Adicionar o recurso de fórum QnA a uma página
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Recurso do fórum de perguntas e respostas {#q-a-forum-feature}

## Introdução {#introduction}

O recurso de fórum QnA (perguntas e respostas) fornece uma área para os membros da comunidade fazerem e responderem perguntas:

* Criar novas perguntas
* Imagens embutidas (com suporte para arrastar e soltar)
* Visualização e perguntas de resposta
* Procurar uma pergunta
* Ajuda a moderar o conteúdo QnA
* Identificar as melhores respostas
* Mover perguntas QnA de uma página para outra

Esta seção da documentação descreve

* Adicionar o recurso de fórum QnA a um site AEM
* Configurações do componente `QnA`

## Adicionar um fórum de P&amp;R a uma página {#adding-a-q-a-forum-to-a-page}

Para adicionar um componente `QnA` a uma página no modo de autor, use o navegador de componentes para localizar `Communities / QnA` e arraste-o para o lugar em uma página onde o fórum QnA deve aparecer.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](qna-essentials.md#essentials-for-client-side) forem incluídas, o componente `QnA` aparecerá desta forma:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configurando o QnA {#configuring-qna}

Selecione o componente `QnA` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Configurações]**, especifique as configurações para tópicos (perguntas) e respostas (respostas):

* **[!UICONTROL Tópicos por]**
páginaDefine o número de perguntas/postagens exibidas por página. O padrão é 10.

* ****
ModeradoSe marcado, a publicação de tópicos e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* ****
FechadoSe marcado, o fórum é fechado para novas perguntas e comentários. O padrão está desmarcado.

* **[!UICONTROL Rich Text]**
EditorSe marcado, os tópicos e os comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
marcaçãoSe marcada, permita que os membros adicionem etiquetas à sua postagem (consulte  **[!UICONTROL Tag]** field tab). O padrão está desmarcado.

* **[!UICONTROL Permitir]**
uploads de arquivoSe marcada, permita que os anexos de arquivo sejam adicionados à pergunta ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Tamanho máx.]**
do arquivoRelevante somente se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Permitidos]**
Tipos de ArquivoRelevante somente se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, o upload dos não especificados não será permitido. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Tamanho máx. do arquivo de imagem anexadaRelevante somente se Permitir uploads de arquivo estiver marcado.]**
Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir]**
seguidoresSe marcada, inclua o seguinte recurso para postagens do fórum, que permite que os membros sejam  [](notifications.md) notificados sobre novas postagens. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
fixaçãoSe marcada, os tópicos do fórum podem ser fixados na parte superior da lista de tópicos. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
assinaturas de e-mailSe marcada, permita que os membros sejam notificados de novas publicações por e-mail ([subscrição](subscriptions.md)). Exige que `Allow Following` seja verificado e [e-mail configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Permitir]**
respostasSe marcada, permita respostas a comentários postados na pergunta. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e]**
tópicosSe marcada, permita que os membros excluam os comentários e perguntas que publicaram. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
votaçãoSe marcada, inclua o recurso de votação com uma pergunta. O padrão está desmarcado.

* **[!UICONTROL Mover a resposta selecionada para o]**
inícioSe marcada, a primeira resposta mostrada é uma resposta selecionada. O padrão está marcado.

* **[!UICONTROL Exibir]**
emblemasSe marcada, exibe os  [](implementing-scoring.md) emblemas ganhados e atribuídos com a entrada do blog de um membro. O padrão está desmarcado.

* **[!UICONTROL Se a opção Permitir]**
conteúdo em destaque estiver marcada, a ideia poderá ser identificada como conteúdo [ em ](featured.md)destaque. O padrão está desmarcado.

#### Guia Moderação do usuário {#user-moderation-tab}

Na guia **[!UICONTROL Moderação do usuário]**, especifique como os tópicos publicados (perguntas) e as respostas (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

* **[!UICONTROL Negar]**
respostasSe marcada, os moderadores de membros confiáveis poderão negar as respostas publicadas e impedir que a resposta apareça no fórum público de perguntas e respostas. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir]**
tópicosSe marcada, os moderadores de membros confiáveis podem fechar uma pergunta (tópico) para outras edições e respostas, e também podem reabrir uma pergunta. O padrão está desmarcado.

* **[!UICONTROL Mover]**
tópicosSe marcada, permita que os moderadores do lado da publicação movam perguntas. O padrão está desmarcado.

* **[!UICONTROL Sinalizar]**
postagensSe marcada, permita que os membros sinalizem as perguntas ou respostas de outras pessoas como inadequadas. O padrão está desmarcado.

* **[!UICONTROL Sinalizar]**
lista de motivosSe estiver marcada, permita que os membros escolham, em uma lista suspensa, o motivo para sinalizar uma pergunta ou resposta como inadequada. O padrão está desmarcado.

* **[!UICONTROL Sinalizador personalizado]**
MotivoSe estiver marcado, permita que os membros insiram seu próprio motivo para sinalizar uma pergunta ou resposta como inadequada. O padrão está desmarcado.

* **[!UICONTROL Limiar de moderaçãoInsira o número de vezes que uma pergunta ou resposta deve ser sinalizada pelos membros antes que os moderadores sejam notificados.]**
O padrão é 1 (uma vez).

* **[!UICONTROL Limite]**
de sinalizaçãoInsira o número de vezes que uma pergunta ou resposta deve ser sinalizada antes de ser ocultada da visualização pública. Se definido como -1, a pergunta ou resposta sinalizada nunca será ocultada da visualização pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

#### Guia Campo de tag {#tag-field-tab}

Na guia **[!UICONTROL Campo de tag]**, as tags que podem ser aplicadas, se permitidas na guia **[!UICONTROL Settings]**, são limitadas de acordo com as namespaces escolhidas.

* **[!UICONTROL Espaços de]**
nomes permitidosRelevante se 
`Allow Tagging` está marcada na guia  **** Configurações. As marcas que podem ser aplicadas são limitadas às da categoria verificada. A lista do namespace inclui &quot;Tags padrão&quot; (a namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todas as namespaces são permitidas.

* **[!UICONTROL Limite de]**
sugestãoInsira o número de tags a serem exibidas como uma sugestão para o membro postar no fórum. Um valor de 
`-1` significa que não há limites. O padrão é 0.

#### guia Configurações de classificação {#sort-settings-tab}

Na guia **[!UICONTROL Classificar configurações]**, especifique como os comentários publicados são classificados quando exibidos.

* **[!UICONTROL Classificar]**
porMarque todas as seleções de classificação permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. O padrão é `Newest, Oldest, Last Updated`.

* **[!UICONTROL Defina como]**
DefaultPull para baixo para selecionar uma das opções de classificação marcadas para serem exibidas como padrão. O padrão é 
`Newest`.

* **[!UICONTROL Selecione Opções de tempo para]**
classificação do AnalyticsPuxe para baixo para selecionar uma das opções de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. O padrão é `All`.

## Experiência de Visitante do site {#site-visitor-experience}

### Identificando respostas {#identifying-answers}

Uma resposta pode ser marcada como uma resposta correta ou útil usando o botão `Select Answer`. Quando uma pergunta é marcada como Respondida, outra resposta não pode ser selecionada até que a primeira seja desmarcada usando o botão `Unmark Chosen Answer`.

Depois de selecionada como uma resposta viável, ela pode ser desmarcada usando o botão `Unmark Chosen Answer`.

Depois que uma resposta é selecionada como resposta viável, uma indicação de que a pergunta foi `Answered`é exibida ao lado do tópico da pergunta na página principal de QnA.

### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar as tarefas de moderação permitidas pela configuração do componente, independentemente de quem criou a pergunta ou resposta.

Eles também têm a capacidade de identificar respostas.

### Membros {#members}

Quando o visitante do site estiver conectado, dependendo da configuração, eles poderão

* Publicar uma nova pergunta
* Editar ou excluir perguntas que eles criaram
* Pode também sinalizar perguntas ou respostas de outras pessoas
* Pode identificar respostas para perguntas que eles criaram

### Anônimo {#anonymous}

Os visitantes do site que não estão conectados só podem ler perguntas e respostas publicadas, traduzi-las se houver suporte, mas não podem adicionar nem perguntas nem respostas, nem sinalizar as publicações de outras pessoas.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [QnA Essentials](qna-essentials.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).
