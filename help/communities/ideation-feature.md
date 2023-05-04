---
title: Recurso de idealização
seo-title: Ideation Feature
description: Adicionar e configurar o recurso Ideação
seo-description: Adding and configuring the Ideation feature
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 1%

---

# Recurso de idealização {#ideation-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso de ideação fornece uma área para visitantes do site com logon (membros da comunidade) no ambiente de publicação para:

* Crie ideias para compartilhar com a comunidade
* Exibir e comentar ideias
* Siga uma ideia
* Voto uma ideia

Esta seção da documentação descreve

* Adicionar o recurso de ideação a um site AEM
* Configurações do componente Ideação

## Adicionar uma ideia a uma página {#adding-a-ideation-to-a-page}

Para adicionar uma `Ideation` para uma página no modo autor, use o navegador de componentes para localizar `Communities / Ideation` e arraste-a para o lugar em uma página onde a ideia deve aparecer.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](ideation.md#essentials-for-client-side) são incluídos, é assim que a variável `Ideation`componente será exibido:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuração de uma Ideia {#configuring-an-ideation}

Selecione o `Ideation` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique as configurações para ideias e comentários:

* **[!UICONTROL Título da Ideação]**
O título de exibição da ideia. O padrão é 
`Ideation`.

* **[!UICONTROL Descrição da Ideação]**
Uma descrição para exibir como um subtítulo para a ideia. O padrão não é descrição.

* **[!UICONTROL Tópicos por página]**
Define o número de ideias/postagens exibidas por página. O padrão é 10.

* **[!UICONTROL Moderado]**
Se marcada, a postagem de ideias e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**
Se marcada, o fórum de ideação é fechado para novas ideias e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor de Rich Text]**
Se marcada, ideias e comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir marcação]**
Se marcada, permitir que membros adicionem rótulos de tag à publicação (consulte **[!UICONTROL Campo de tag]** ). O padrão está desmarcado.

* **[!UICONTROL Permitir uploads de arquivo]**
Se marcada, permita que anexos de arquivo sejam adicionados à ideia ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Tamanho máximo do arquivo]**
Relevante apenas se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivo permitidos]**
Relevante apenas se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não poderão ser carregados. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem anexada]**
Relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir respostas]**
Se marcada, permita respostas para comentários postados na ideia. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e tópicos]**
Se marcada, permita que os membros excluam os comentários e ideias que publicaram. O padrão está desmarcado.

* **[!UICONTROL Permitir Seguindo]**
Se marcada, inclua o seguinte recurso para publicações de ideias, o que permite que os membros sejam [notificado](notifications.md) de novos posts. O padrão está desmarcado.

* **[!UICONTROL Permitir assinaturas por email]**
Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([assinatura](subscriptions.md)). Exige `Allow Following` a verificar e [email configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Permitir votação]**
Se for marcada, permita votar os comentários de uma ideia. O padrão está desmarcado.

* **[!UICONTROL Exibir emblemas]**
Se marcada, exibir ganhado e atribuído [emblemas](implementing-scoring.md) com a ideia de um membro. O padrão está desmarcado.

* **[!UICONTROL Permitir conteúdo em destaque]**
se marcada, a ideia poderá ser identificada como [conteúdo em destaque](featured.md). O padrão está desmarcado.

### Guia Moderação do usuário {#user-moderation-tab}

Em **[!UICONTROL Moderação do usuário]** , especifique como as ideias e os comentários publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

* **[!UICONTROL Negar publicações]**
Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir Tópicos]**
Se marcada, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

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
Relevante se 
`Allow Tagging` é verificada sob o **Configurações** guia . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite de Sugestão]**
Insira o número de tags a serem exibidas como sugestão para o membro postando no fórum. Um valor de 
**-** 1 significa sem limite. O padrão é 0.

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

## Experiência de visitante do site {#site-visitor-experience}

### Criar ideia {#creating-idea}

Assim como em todos os recursos das Comunidades, se não estiverem conectados, um visitante do site só poderá ler ideias e visualizar outras opiniões (por meio de comentários e voto/curtir).

Depois de conectado, um membro pode criar uma nova ideia.

![chlimage_1-32](assets/chlimage_1-32.png)

Antes de enviar a ideia, é possível que o membro salve um rascunho.

Ao selecionar a variável `Save as Draft` , um rascunho é salvo.

![chlimage_1-33](assets/chlimage_1-33.png)

Ao exibir rascunhos salvos no `My Drafts` guia , selecione `Read More` para entrar novamente no modo de edição:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fornecer feedback {#providing-feedback}

Uma vez publicada a ideia, outros membros podem entrar, abrir a ideia ( `Read More`) e curtir a ideia, assim adicionando à contagem de votos e faça comentários.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos da Ideação](ideation.md) página para desenvolvedores.

Para obter moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).
