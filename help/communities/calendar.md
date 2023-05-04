---
title: Recurso de calendário
seo-title: Calendar Feature
description: Fornece informações de evento da comunidade em um formato de calendário
seo-description: Provides community event information in a calendar format
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
exl-id: f95d1471-82a1-4c37-ac5b-0eb861c823a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 7%

---

# Recurso de calendário {#calendar-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso de calendário oferece suporte para o fornecimento de informações de evento da comunidade em um formato de calendário para todos os visitantes do site ou somente visitantes do site que tenham feito logon (membros da comunidade), enquanto apenas membros autorizados poderão adicionar eventos.

Esta seção da documentação descreve:

* Adicionar o recurso de calendário a um site AEM
* Configurações para `Calendar`componentes

## Adicionar um calendário a uma página {#adding-a-calendar-to-a-page}

Para adicionar uma `Calendar` para uma página no modo autor, use o navegador de componentes para localizar

* `Communities / Calendar`

e arraste-a para o local em uma página, como uma posição relativa ao recurso que os usuários devem analisar.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](calendar-basics-for-developers.md#essentials-for-client-side) são incluídos, é assim que a variável `Calendar` será exibido.

![chlimage_1-112](assets/chlimage_1-112.png)

### Configurar calendário {#configuring-calendar}

Selecione o `Calendar`para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### Guia Configurações {#settings-tab}

Em **[!UICONTROL Configurações]** , especifique se permite ou não a aplicação de tags às entradas do calendário.

* **[!UICONTROL Eventos por página]**

   Define o número de eventos exibidos por página. O padrão é 10.

* **[!UICONTROL Moderada]**

   Se marcada, a postagem de eventos e comentários do calendário deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**

   Se marcada, o calendário é fechado para novas entradas de evento e comentários. O padrão está desmarcado.

* **[!UICONTROL Editor de rich text]**

   Se marcada, eventos de calendário e comentários podem ser inseridos com marcação. O padrão está marcado.

* **[!UICONTROL Permitir marcação]**

   Se marcada, permitir que membros adicionem rótulos de tag aos eventos que publicam (consulte **Campo de tag** ). O padrão está marcado.

* **[!UICONTROL Permitir carregamento de arquivos]**

   Se marcada, permita que anexos de arquivo sejam adicionados a um evento de calendário ou comentário. O padrão está marcado.

* **[!UICONTROL Permitir monitoramento]**

   Se marcada, permita que os membros sigam eventos publicados no calendário. O padrão está marcado.

* **[!UICONTROL Tamanho máximo do arquivo]**

   Relevante apenas se `Allow File Uploads` está marcada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivos permitidos]**

   Relevante apenas se `Allow File Uploads` está marcada. Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não poderão ser carregados. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem a ser anexado]**

   Relevante somente se Permitir uploads de arquivo estiver marcado. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Tipos de imagem de capa permitidos]**

   Uma lista separada por vírgulas de extensões de arquivo de imagem com o separador &quot;ponto&quot;. O padrão é `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL Permitir respostas encadeadas]**

   Se marcada, permita respostas para comentários postados no evento de calendário. O padrão está marcado.

* **[!UICONTROL Permitir que usuários excluam comentários e eventos]**

   Se marcada, permita que os membros excluam os comentários e os eventos do calendário publicados. O padrão está marcado.

* **[!UICONTROL Permitir votação]**

   Se marcada, inclua o recurso Voto com um evento de calendário. O padrão está marcado.

* **[!UICONTROL Mostrar navegações estruturais]**

   Mostrar navegações estruturais na página do evento. O padrão está marcado.

* **[!UICONTROL Filtro do intervalo de datas]**

   Define o número de dias adicionados à data atual para calcular o valor &quot;Para&quot; do filtro de página de listagem de eventos do calendário. O número padrão é 30.

* **[!UICONTROL Ativar conteúdo em destaque]**

   Se marcada, a ideia pode ser identificada como [conteúdo em destaque](featured.md). O padrão está desmarcado.

Em **[!UICONTROL Moderação do usuário]** , especifique como os tópicos e as respostas publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

#### Guia Moderação do usuário {#user-moderation-tab}

* **[!UICONTROL Negar postagens]**

   Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está marcado.

* **[!UICONTROL Fechar / Reabrir eventos]**

   Se marcada, os moderadores de membros confiáveis podem fechar um evento para outras edições e comentários, e também podem reabrir um evento. O padrão está marcado.

* **[!UICONTROL Sinalizar postagens]**

   Se marcada, permita que os membros sinalizem eventos ou comentários de outras pessoas como inadequados. O padrão está marcado.

* **[!UICONTROL Sinalizar lista de motivo]**

   Se marcada, permita que os membros escolham, em uma lista suspensa, o motivo para marcar um evento ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo personalizado de sinalização]**

   Se marcada, permita que os membros insiram seu próprio motivo para marcar um evento ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**

   Insira o número de vezes que um evento ou comentário deve ser sinalizado por membros antes que os moderadores sejam notificados. O padrão é 1 ( uma vez).

* **[!UICONTROL Limite de sinalização]**

   Insira o número de vezes que um evento ou comentário deve ser sinalizado antes de ser oculto da exibição pública. Se definido como -1, o tópico ou comentário sinalizado nunca será oculto da exibição pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

#### Guia Campo de tag {#tag-field-tab}

Em **[!UICONTROL Campo de tag]** , as tags que podem ser aplicadas, se permitidas sob a variável **[!UICONTROL Configurações]** , são limitadas de acordo com os namespaces escolhidos.

* **[!UICONTROL Namespaces permitidos]**

   Relevante se `Allow Tagging` é verificada sob o **[!UICONTROL Configurações]** guia . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite sugerido]**

   Insira o número de tags a serem exibidas como sugestão para o membro postando no fórum. O padrão é `-1` (sem limites).

>[!NOTE]
>
>Visita [Administração de tags](../../help/sites-administering/tags.md) para saber como adicionar um novo namespace de tag (taxonomia).

#### Guia Tradução {#translation-tab}

Em **[!UICONTROL Tradução]** , se a tradução estiver ativada para o site da comunidade, a tradução poderá ser definida para traduzir todo o encadeamento (evento e comentários) em vez de postagens específicas.

* **[!UICONTROL Converter tudo]**

   Se marcada, o evento e os comentários são traduzidos para o idioma preferencial do usuário. O padrão está marcado.

## Experiência de visitante do site {#site-visitor-experience}

No ambiente de publicação, o recurso de calendário exibirá um campo de pesquisa com um intervalo de datas padrão e quaisquer eventos de calendário que estejam dentro desse intervalo.

Quando um evento de calendário é selecionado, os detalhes, a descrição e os comentários do evento de calendário são exibidos.

Outras capacidades dependem se o visitante do site é um moderador, administrador, membro da comunidade, membro privilegiado ou anônimo.

### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar [tarefas de moderação](moderate-ugc.md) (conforme permitido pela configuração do componente) em todos os eventos de calendário e comentários postados em um evento.

![chlimage_1-115](assets/chlimage_1-115.png)

### Membros {#members}

Quando o usuário conectado é um membro da comunidade ou [membro privilegiado](users.md#privileged-members-group) (dependendo da configuração), eles podem selecionar `New Event` para criar e publicar um novo evento de calendário.

Especificamente, podem

* Criar um novo evento de calendário
* Publicar um comentário em um evento de calendário
* Editar seu próprio evento de calendário ou comentário
* Excluir seu próprio evento de calendário ou comentário
* Sinalizar eventos ou comentários de calendário de outras pessoas

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### Anônimo {#anonymous}

Os visitantes do site que não estiverem conectados podem ler somente os eventos de calendário publicados, traduzi-los, se houver suporte, mas não podem adicionar um evento ou comentário, nem sinalizar eventos ou comentários de outras pessoas.

![chlimage_1-118](assets/chlimage_1-118.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos do calendário](calendar-basics-for-developers.md) página para desenvolvedores.

Para obter a moderação de eventos e comentários do calendário, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar eventos e comentários do calendário, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).

Para obter a tradução de eventos e comentários do calendário, consulte [Tradução de conteúdo gerado pelo usuário](translate-ugc.md).
