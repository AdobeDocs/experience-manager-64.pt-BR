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
* Configurações do componente `Forum`

## Adicionar um fórum a uma página {#adding-a-forum-to-a-page}

Para adicionar um componente `Forum` a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Forum`

E arraste-o para o lugar em uma página onde o fórum deve aparecer.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](essentials-forum.md#essentials-for-client-side) forem incluídas, será assim que o componente `Forum`aparecerá:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configuração de um fórum {#configuring-a-forum}

Selecione o componente `Forum` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Configurações]**, especifique as configurações para tópicos e respostas:

* **[!UICONTROL Tópicos por]**
páginaDefine o número de tópicos/postagens exibidos por página. O padrão é 10.

* ****
ModeradoSe marcado, a publicação de tópicos e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* ****
FechadoSe marcado, o fórum é fechado para novos tópicos e comentários. O padrão está desmarcado.

* **[!UICONTROL Rich Text]**
EditorSe marcado, os tópicos e os comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
marcaçãoSe marcada, permita que os membros adicionem etiquetas à sua postagem (consulte  **[!UICONTROL Tag]** field tab). O padrão está desmarcado.

* **[!UICONTROL Permitir]**
uploads de arquivoSe marcada, permita que os anexos de arquivo sejam adicionados ao tópico ou ao comentário. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
seguidoresSe marcada, inclua o seguinte recurso para postagens do fórum, que permite que os membros sejam  [](notifications.md) notificados sobre novas postagens. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
fixaçãoSe marcada, os tópicos do fórum podem ser fixados na parte superior da lista de tópicos. O padrão está desmarcado.

* **[!UICONTROL Se a opção Permitir]**
conteúdo em destaque estiver marcada, a ideia poderá ser identificada como conteúdo [ em ](featured.md)destaque. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
assinaturas de e-mailSe marcada, permita que os membros sejam notificados de novas publicações por e-mail ([subscrição](subscriptions.md)). Exige que `Allow Following` seja verificado e [e-mail configurado](email.md). O padrão está desmarcado.

* **[!UICONTROL Tamanho máx.]**
do arquivoRelevante somente se 
`Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Permitidos]**
Tipos de ArquivoRelevante somente se 
`Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, o upload dos não especificados não será permitido. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Tamanho máx. do arquivo de imagem anexadaRelevante somente se Permitir uploads de arquivo estiver marcado.]**
Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Permitir]**
respostas encadeadasSe marcada, permita respostas a comentários postados no tópico. O padrão está desmarcado.

* **[!UICONTROL Permitir que os usuários excluam comentários e]**
tópicosSe marcada, permita que os membros excluam os comentários e tópicos publicados. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
votaçãoSe marcada, inclua o recurso de votação com um tópico. O padrão está desmarcado.

* **[!UICONTROL Mostrar]**
navegações estruturaisSe marcada, mostrar navegações estruturais nas páginas de tópicos. O padrão está marcado.

* **[!UICONTROL Exibir]**
emblemasSe marcada, exibe os  [](implementing-scoring.md) emblemas ganhados e atribuídos com a entrada do blog de um membro. O padrão está desmarcado.

>[!NOTE]
>
>Pode ser necessário marcar `AllowThreaded Replies` e `Allow users to Delete Comments and Topics` para ativar os comentários em um tópico.

### Guia Moderação do usuário {#user-moderation-tab}

Na guia **[!UICONTROL Moderação do usuário]**, especifique como os tópicos e as respostas publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

* **[!UICONTROL Negar]**
publicaçõesSe marcada, os moderadores de membros confiáveis poderão negar as publicações e impedir que a publicação apareça no fórum público. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir]**
tópicosSe marcados, os moderadores de membros confiáveis podem fechar um tópico para outras edições e comentários, e também podem reabrir um tópico. O padrão está desmarcado.

* **[!UICONTROL Mover]**
tópicosSe marcada, permita que os moderadores do lado da publicação movam tópicos. O padrão está marcado.

* **[!UICONTROL Sinalizar]**
postagensSe marcada, permita que os membros sinalizem os tópicos ou comentários de outras pessoas como inadequados. O padrão está desmarcado.

* **[!UICONTROL Sinalizar]**
lista de motivosSe estiver marcada, permita que os membros escolham, em uma lista suspensa, seu motivo para sinalizar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Sinalizador personalizado]**
MotivoSe selecionado, permita que os membros insiram seu próprio motivo para sinalizar um tópico ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Digite o número de vezes que um tópico ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 (uma vez).

* **[!UICONTROL Limite]**
de sinalizaçãoInsira o número de vezes que um tópico ou comentário deve ser sinalizado antes de ser ocultado da visualização pública. Se definido como -1, o tópico ou comentário sinalizado nunca será ocultado da visualização pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

### Guia Campo de tag {#tag-field-tab}

Na guia **[!UICONTROL Campo de tag]**, as tags que podem ser aplicadas, se permitidas na guia **[!UICONTROL Settings]**, são limitadas de acordo com as namespaces escolhidas.

* **[!UICONTROL Namespaces Permitidos]**
Relevante se  `Allow Tagging` estiver marcado na guia  **** Configurações. As marcas que podem ser aplicadas são limitadas às da categoria verificada. A lista do namespace inclui &quot;Tags padrão&quot; (a namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todas as namespaces são permitidas.

* **[!UICONTROL Limite de]**
sugestãoInsira o número de tags a serem exibidas como uma sugestão para o membro postar no fórum. O padrão é 
**-** 1 (sem limites).

### Guia Tradução {#translation-tab}

Na guia **[!UICONTROL Tradução]**, se a tradução estiver ativada para o site da comunidade, a tradução poderá ser definida para traduzir o tópico inteiro ou as publicações selecionadas.

* **[!UICONTROL Traduzir]**
tudoSe estiver marcado, o thread do fórum será traduzido para o idioma preferencial do usuário. O padrão está desmarcado.

### guia Configurações de classificação {#sort-settings-tab}

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

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Fórum Essentials](essentials-forum.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).

Para obter a tradução de tópicos e comentários postados, consulte [Traduzindo conteúdo gerado pelo usuário](translate-ugc.md).
