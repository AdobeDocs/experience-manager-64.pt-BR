---
title: Recurso do fórum
seo-title: Forum Feature
description: Como adicionar e configurar o recurso do fórum
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 1%

---

# Recurso do fórum {#forum-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso de fórum fornece uma área para visitantes do site com logon (membros da comunidade) no ambiente de publicação para:

* Criar novos tópicos
* Exibir e responder aos tópicos
* Siga um tópico
* Pesquisar um fórum
* Ajude a moderar o conteúdo do fórum
* Mover tópicos do fórum de uma página para outra

Esta seção da documentação descreve

* Adicionar o recurso do fórum a um site AEM
* Configurações para o `Forum`componente

## Adicionar um fórum a uma página {#adding-a-forum-to-a-page}

Para adicionar uma `Forum` para uma página no modo autor, use o navegador de componentes para localizar

* `Communities / Forum`

E arraste-o para o lugar em uma página onde o fórum deve aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](essentials-forum.md#essentials-for-client-side) são incluídos, é assim que a variável `Forum`componente será exibido:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configurar um fórum {#configuring-a-forum}

Selecione o `Forum` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique as configurações dos tópicos e respostas:

* **[!UICONTROL Tópicos por página]**
Define o número de tópicos/postagens exibidos por página. O padrão é 10.

* **[!UICONTROL Moderado]**
Se marcada, a publicação de tópicos e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**
Se marcada, o fórum é fechado para novos tópicos e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor de Rich Text]**
Se marcada, tópicos e comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir marcação]**
Se marcada, permitir que membros adicionem rótulos de tag à publicação (consulte **[!UICONTROL Campo de tag]** ). O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, permita que anexos de arquivo sejam adicionados ao tópico ou comentário. O padrão está desmarcado.

* **[!UICONTROL Permitir Seguindo]**
Se marcada, inclua o seguinte recurso para publicações do fórum, que permite que os membros sejam [notificado](notifications.md) de novos posts. O padrão está desmarcado.

* **[!UICONTROL Permitir Prender]**
Se marcada, os tópicos do fórum podem ser fixados ao topo da lista de tópicos. O padrão está desmarcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
se marcada, a ideia poderá ser identificada como [conteúdo em destaque](featured.md). O padrão está desmarcado.

* **[!UICONTROL Permitir assinaturas por email]**
Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([assinatura](subscriptions.md)). Exige `Allow Following` a verificar e [email configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Tamanho máximo do arquivo]**
Relevante apenas se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivo permitidos]**
Relevante apenas se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não poderão ser carregados. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem anexada]**
Relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir respostas encadeadas]**
Se marcada, permita respostas para comentários publicados no tópico. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e tópicos]**
Se marcada, permita que os membros excluam os comentários e tópicos publicados. O padrão está desmarcado.

* **[!UICONTROL Permitir votação]**
Se marcada, inclua o recurso Votação com um tópico. O padrão está desmarcado.

* **[!UICONTROL Mostrar navegação estrutural]**
Se marcada, mostrar navegação estrutural nas páginas de tópicos. O padrão está marcado.

* **[!UICONTROL Exibir emblemas]**
Se marcada, exibir ganhado e atribuído [emblemas](implementing-scoring.md) com a entrada de um membro no blog. O padrão está desmarcado.

>[!NOTE]
>
>Pode ser necessário verificar ambos `AllowThreaded Replies` e `Allow users to Delete Comments and Topics` para permitir comentários em um tópico.

### Guia Moderação do usuário {#user-moderation-tab}

Em **[!UICONTROL Moderação do usuário]** , especifique como os tópicos e as respostas publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

* **[!UICONTROL Negar publicações]**
Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir Tópicos]**
Se marcada, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

* **[!UICONTROL Mover tópicos]**
Se marcada, permita que moderadores do lado da publicação movam tópicos. O padrão está marcado.

* **[!UICONTROL Sinalizar publicações]**
Se marcada, permita que os membros sinalizem os tópicos ou comentários de outras pessoas como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Lista de Motivos do Sinalizador]**
Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo do Sinalizador Personalizado]**
Se marcada, permita que os membros insiram seu próprio motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Insira o número de vezes que um tópico ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 ( uma vez).

* **[!UICONTROL Limite de sinalização]**
Insira o número de vezes que um tópico ou comentário deve ser sinalizado antes de ser oculto da exibição pública. Se definido como -1, o tópico ou comentário sinalizado nunca será oculto da exibição pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

### Guia Campo de tag {#tag-field-tab}

Em **[!UICONTROL Campo de tag]** , as tags que podem ser aplicadas, se permitidas sob a variável **[!UICONTROL Configurações]** , são limitadas de acordo com os namespaces escolhidos.

* **[!UICONTROL Espaços de nomes permitidos]**
Relevante se `Allow Tagging` é verificada sob o **[!UICONTROL Configurações]** guia . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite de Sugestão]**
Insira o número de tags a serem exibidas como sugestão para o membro postando no fórum. O padrão é 
**-** 1 (sem limites).

### Guia Tradução {#translation-tab}

Em **[!UICONTROL Tradução]** , se a tradução estiver ativada para o site da comunidade, a tradução poderá ser definida para traduzir o tópico inteiro ou as publicações selecionadas.

* **[!UICONTROL Traduzir tudo]**
Se marcada, o thread do fórum é traduzido para o idioma preferencial do usuário. O padrão está desmarcado.

### Guia Configurações de classificação {#sort-settings-tab}

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

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos do fórum](essentials-forum.md) página para desenvolvedores.

Para obter moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).

Para obter a tradução de tópicos e comentários publicados, consulte [Tradução de conteúdo gerado pelo usuário](translate-ugc.md).
