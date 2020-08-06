---
title: Recurso Ideação
seo-title: Recurso Ideação
description: Adicionar e configurar o recurso Ideação
seo-description: Adicionar e configurar o recurso Ideação
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# Recurso Ideação {#ideation-feature}

## Introdução {#introduction}

O recurso de ideação fornece uma área para visitantes de site conectados (membros da comunidade) no ambiente de publicação para:

* Crie ideias para compartilhar com a comunidade
* Visualização e comentários sobre ideias
* Siga uma ideia
* Votar uma ideia

Esta seção da documentação descreve

* Adicionar o recurso de ideação a um site AEM
* Configurações do componente Ideação

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

Para adicionar um `Ideation` componente a uma página no modo de autor, use o navegador de componentes para localizá-lo `Communities / Ideation` e arrastá-lo para o lugar em uma página onde a ideia deve aparecer.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando as bibliotecas [do lado do cliente](ideation.md#essentials-for-client-side) necessárias forem incluídas, o `Ideation`componente será exibido desta forma:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configuração de uma ideia {#configuring-an-ideation}

Selecione o componente inserido a ser acessado e selecione o `Ideation` `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Configurações]** , especifique as configurações para ideias e comentários:

* **[!UICONTROL Título]** da ideiaO título de exibição da ideia. O padrão é 
`Ideation`.

* **[!UICONTROL Descrição]** da ideiaUma descrição para exibir como um subtítulo da ideia. O padrão não é descrição.

* **[!UICONTROL Tópicos por página]** Define o número de ideias/postagens exibidas por página. O padrão é 10.

* **[!UICONTROL Moderado]** Se marcado, a postagem de ideias e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]** Se marcado, o fórum de ideação é fechado para novas ideias e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor]** de Rich Text Se marcado, ideias e comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir marcação]** Se marcada, permita que os membros adicionem etiquetas à sua postagem (consulte a guia Campo **[!UICONTROL de]** tag ). O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivoSe marcada, permita que anexos de arquivo sejam adicionados à ideia ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Tamanho]** máximo do arquivo relevante somente se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos]** de arquivo permitidos relevantes somente se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, o upload dos não especificados não será permitido. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Tamanho]** de arquivo de imagem de anexo máximo relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir respostas]** Se marcada, permita respostas a comentários postados na ideia. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e tópicos]** Se marcados, permitirá que os membros excluam os comentários e ideias que publicaram. O padrão está desmarcado.

* **[!UICONTROL Permitir após]** Se marcada, inclua o seguinte recurso para publicações de ideias, que permite que os membros sejam [notificados](notifications.md) sobre novas publicações. O padrão está desmarcado.

* **[!UICONTROL Permitir Subscrições]** por email Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([subscrição](subscriptions.md)). Requer `Allow Following` a verificação e configuração [de](email.md)email. O padrão está desmarcado.

* **[!UICONTROL Permitir votação]** Se marcada, permitir a votação dos comentários de uma ideia. O padrão está desmarcado.

* **[!UICONTROL Exibir emblemas]** Se marcada, exibe [emblemas](implementing-scoring.md) ganhados e atribuídos com a ideia de um membro. O padrão está desmarcado.

* **[!UICONTROL Permitir conteúdo]** em destaque se marcado, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está desmarcado.

### Guia Moderação do usuário {#user-moderation-tab}

Na guia Moderação **[!UICONTROL do]** usuário, especifique como as ideias e os comentários publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

* **[!UICONTROL Negar publicações]** Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir tópicos]** Se marcados, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

* **[!UICONTROL Sinalizar publicações]** Se marcada, permita que os membros sinalizem os tópicos ou comentários de outras pessoas como inadequados. O padrão está desmarcado.

* **[!UICONTROL Sinalizar Lista]** do motivo Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para sinalizar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo]** de sinalização personalizado Se marcado, permita que os membros insiram seu próprio motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite]** de moderaçãoInsira o número de vezes que um tópico ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 (uma vez).

* **[!UICONTROL Limite de sinalização]** Digite o número de vezes que um tópico ou comentário deve ser sinalizado antes de ser ocultado da visualização pública. Se definido como -1, o tópico ou comentário sinalizado nunca será ocultado da visualização pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

### Guia Campo de tag {#tag-field-tab}

Na guia Campo **[!UICONTROL de]** tag , as tags que podem ser aplicadas, se permitidas na guia **[!UICONTROL Configurações]** , são limitadas de acordo com as namespaces escolhidas.

* **[!UICONTROL Namespaces]** relevantes permitidas se 
`Allow Tagging` está marcada na guia **Configurações** . As marcas que podem ser aplicadas são limitadas às da categoria verificada. A lista do namespace inclui &quot;Tags padrão&quot; (a namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todas as namespaces são permitidas.

* **[!UICONTROL Limite de sugestão]** Insira o número de tags a serem exibidas como uma sugestão para o membro postar no fórum. Um valor de 
**-** 1 significa sem limite. O padrão é 0.

### Guia Configurações de classificação {#sort-settings-tab}

Na guia **[!UICONTROL Classificar configurações]** , especifique como os comentários publicados são classificados quando exibidos.

* **[!UICONTROL Classificar por]** Marque todas as seleções de classificação permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. O padrão é `Newest, Oldest, Last Updated`.

* **[!UICONTROL Defina como Padrão]** Puxe para baixo para selecionar uma das opções de classificação marcadas para aparecer como padrão. O padrão é 
`Newest`.

* **[!UICONTROL Selecione Opções de tempo para o Analytics Classificar]** Puxar para baixo para selecionar uma das opções de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. O padrão é `All`.

## Experiência com o Visitante do site {#site-visitor-experience}

### Criando ideia {#creating-idea}

Como acontece com todos os recursos das Comunidades, se não estiverem conectados, um visitante do site só poderá ler ideias e visualização opiniões de outras pessoas (através de comentários e votação/curtir).

Depois de conectado, um membro pode criar uma nova ideia.

![chlimage_1-32](assets/chlimage_1-32.png)

Antes de enviar a ideia, é possível que o membro salve um rascunho.

Ao selecionar o `Save as Draft` botão, um rascunho é salvo.

![chlimage_1-33](assets/chlimage_1-33.png)

Ao exibir rascunhos salvos na `My Drafts` guia, selecione `Read More` para entrar novamente no modo de edição:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Fornecer feedback {#providing-feedback}

Uma vez publicada a ideia, outros membros podem fazer logon, abrir a ideia ( `Read More`) e gostar da ideia, adicionando ao número de votos e fazendo comentários.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Ideation Essentials](ideation.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo](tag-ugc.md)gerado pelo usuário.
