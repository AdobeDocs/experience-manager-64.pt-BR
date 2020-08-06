---
title: Recurso do fórum
seo-title: Recurso do fórum
description: Como adicionar e configurar o recurso do fórum
seo-description: Como adicionar e configurar o recurso do fórum
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# Recurso do fórum {#forum-feature}

## Introdução {#introduction}

O recurso de fórum fornece uma área para visitantes de site conectados (membros da comunidade) no ambiente de publicação para:

* Criar novos tópicos
* Visualização e resposta aos tópicos
* Siga um tópico
* Pesquisar em um fórum
* Ajudar a moderar o conteúdo do fórum
* Mover tópicos do fórum de uma página para outra

Esta seção da documentação descreve

* Adicionar o recurso do fórum a um site AEM
* Configurações do `Forum`componente

## Adding a Forum to a Page {#adding-a-forum-to-a-page}

Para adicionar um `Forum` componente a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Forum`

E arraste-o para o lugar em uma página onde o fórum deve aparecer.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando as bibliotecas [do lado do cliente](essentials-forum.md#essentials-for-client-side) necessárias forem incluídas, o `Forum`componente será exibido desta forma:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuração de um fórum {#configuring-a-forum}

Selecione o componente inserido a ser acessado e selecione o `Forum` `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Configurações]** , especifique as configurações para tópicos e respostas:

* **[!UICONTROL Tópicos por página]** Define o número de tópicos/postagens exibidos por página. O padrão é 10.

* **[!UICONTROL Moderado]** Se marcado, a publicação de tópicos e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]** Se marcado, o fórum é fechado para novos tópicos e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor]** de Rich Text Se marcado, os tópicos e os comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir marcação]** Se marcada, permita que os membros adicionem etiquetas à sua postagem (consulte a guia Campo **[!UICONTROL de]** tag ). O padrão está desmarcado.

* **[!UICONTROL Permitir uploads]** de arquivoSe marcada, permita que os anexos de arquivo sejam adicionados ao tópico ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Permitir seguidores]** Se marcada, inclua o seguinte recurso para postagens do fórum, que permite que os membros sejam [notificados](notifications.md) de novas postagens. O padrão está desmarcado.

* **[!UICONTROL Permitir fixação]** Se marcada, os tópicos do fórum podem ser fixados na parte superior da lista de tópicos. O padrão está desmarcado.

* **[!UICONTROL Permitir conteúdo]** em destaque se marcado, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está desmarcado.

* **[!UICONTROL Permitir Subscrições]** por email Se marcada, permita que os membros sejam notificados sobre novas postagens por email ([subscrição](subscriptions.md)). Requer `Allow Following` a verificação e configuração [de](email.md)email. O padrão está desmarcado.

* **[!UICONTROL Tamanho]** máximo do arquivo relevante somente se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos]** de arquivo permitidos relevantes somente se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, o upload dos não especificados não será permitido. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Tamanho]** de arquivo de imagem de anexo máximo relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir respostas encadeadas]** Se marcada, permita respostas a comentários postados no tópico. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e tópicos]** Se marcados, permita que os membros excluam os comentários e tópicos publicados. O padrão está desmarcado.

* **[!UICONTROL Permitir votação]** Se marcada, inclua o recurso de votação com um tópico. O padrão está desmarcado.

* **[!UICONTROL Mostrar navegações estruturais]** Se marcada, mostrar navegações estruturais nas páginas de tópicos. O padrão está marcado.

* **[!UICONTROL Exibir emblemas]** Se marcada, exibe [emblemas ganhados e atribuídos](implementing-scoring.md) com a entrada de blog de um membro. O padrão está desmarcado.

>[!NOTE]
>
>Pode ser necessário verificar tanto `AllowThreaded Replies` quanto `Allow users to Delete Comments and Topics` para permitir comentários sobre um tópico.

### Guia Moderação do usuário {#user-moderation-tab}

Na guia Moderação **[!UICONTROL do]** usuário, especifique como os tópicos e as respostas publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

* **[!UICONTROL Negar publicações]** Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir tópicos]** Se marcados, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

* **[!UICONTROL Mover tópicos]** Se marcada, permita que os moderadores do lado da publicação movam tópicos. O padrão está marcado.

* **[!UICONTROL Sinalizar publicações]** Se marcada, permita que os membros sinalizem os tópicos ou comentários de outras pessoas como inadequados. O padrão está desmarcado.

* **[!UICONTROL Sinalizar Lista]** do motivo Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para sinalizar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo]** de sinalização personalizado Se marcado, permita que os membros insiram seu próprio motivo para marcar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite]** de moderaçãoInsira o número de vezes que um tópico ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 (uma vez).

* **[!UICONTROL Limite de sinalização]** Digite o número de vezes que um tópico ou comentário deve ser sinalizado antes de ser ocultado da visualização pública. Se definido como -1, o tópico ou comentário sinalizado nunca será ocultado da visualização pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

### Guia Campo de tag {#tag-field-tab}

Na guia Campo **[!UICONTROL de]** tag , as tags que podem ser aplicadas, se permitidas na guia **[!UICONTROL Configurações]** , são limitadas de acordo com as namespaces escolhidas.

* **[!UICONTROL Namespaces]** relevantes permitidas se `Allow Tagging` estiverem marcadas na guia **[!UICONTROL Configurações]** . As marcas que podem ser aplicadas são limitadas às da categoria verificada. A lista do namespace inclui &quot;Tags padrão&quot; (a namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todas as namespaces são permitidas.

* **[!UICONTROL Limite de sugestão]** Insira o número de tags a serem exibidas como uma sugestão para o membro postar no fórum. O padrão é 
**-** 1 (sem limites).

### Guia Tradução {#translation-tab}

Na guia **[!UICONTROL Tradução]** , se a tradução estiver ativada para o site da comunidade, a tradução pode ser definida para traduzir o tópico inteiro ou as publicações selecionadas.

* **[!UICONTROL Traduzir tudo]** Se estiver marcado, o thread do fórum será traduzido para o idioma preferencial do usuário. O padrão está desmarcado.

### Guia Configurações de classificação {#sort-settings-tab}

Na guia **[!UICONTROL Classificar configurações]** , especifique como os comentários publicados são classificados quando exibidos.

* **[!UICONTROL Classificar por]** Marque todas as seleções de classificação permitidas: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. O padrão é `Newest, Oldest, Last Updated`.

* **[!UICONTROL Defina como Padrão]** Puxe para baixo para selecionar uma das opções de classificação marcadas para aparecer como padrão. O padrão é 
`Newest`.

* **[!UICONTROL Selecione Opções de tempo para o Analytics Classificar]** Puxar para baixo para selecionar uma das opções de 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. O padrão é `All`.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Fórum Essentials](essentials-forum.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo](tag-ugc.md)gerado pelo usuário.

Para obter a tradução de tópicos e comentários publicados, consulte [Traduzindo conteúdo](translate-ugc.md)gerado pelo usuário.
