---
title: Recurso de calendário
seo-title: Recurso de calendário
description: Fornece informações de eventos da comunidade em um formato de calendário
seo-description: Fornece informações de eventos da comunidade em um formato de calendário
uuid: 6f1f327f-bf4b-4357-b8fd-4bec74016921
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 8b8e74c5-8b65-4117-9ef0-da9d9e47191f
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Recurso de calendário {#calendar-feature}

## Introdução {#introduction}

O recurso de calendário oferece suporte ao fornecimento de informações de eventos da comunidade em um formato de calendário para todos os visitantes do site ou somente para visitantes do site que fizeram logon (membros da comunidade), enquanto apenas membros autorizados podem adicionar eventos.

Esta seção da documentação descreve:

* Adicionar o recurso de calendário a um site do AEM
* Configurações para `Calendar`componentes

## Adding a Calendar to a Page {#adding-a-calendar-to-a-page}

Para adicionar um `Calendar` componente a uma página no modo de autor, use o navegador de componentes para localizar

* `Communities / Calendar`

e arraste-o para o lugar em uma página, como uma posição relativa ao recurso que os usuários devem revisar.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando as bibliotecas [do lado do cliente](calendar-basics-for-developers.md#essentials-for-client-side) necessárias forem incluídas, será assim que o `Calendar` componente será exibido.

![chlimage_1-112](assets/chlimage_1-112.png)

### Configurar calendário {#configuring-calendar}

Selecione o `Calendar`componente inserido a ser acessado e selecione o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-113](assets/chlimage_1-113.png) ![chlimage_1-114](assets/chlimage_1-114.png)

#### Guia Configurações {#settings-tab}

Na guia **[!UICONTROL Configurações]** , especifique se as tags devem ou não ser aplicadas às entradas do calendário.

* **[!UICONTROL Eventos por página]**

   Define o número de eventos exibidos por página. O padrão é 10.

* **[!UICONTROL Moderada]**

   Se marcada, a publicação de eventos de calendário e comentários deve ser aprovada antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Fechado]**

   Se marcada, o calendário é fechado para novas entradas e comentários do evento. O padrão está desmarcado.

* **[!UICONTROL Editor de Rich Text]**

   Se marcada, os eventos do calendário e os comentários podem ser inseridos com marcação. O padrão está marcado.

* **[!UICONTROL Permitir marcação]**

   Se marcada, permita que os membros adicionem rótulos de tags aos eventos que publicam (consulte a guia Campo **** de tag). O padrão está marcado.

* **[!UICONTROL Permitir carregamento de arquivos]**

   Se marcada, permita que os anexos de arquivo sejam adicionados a um evento de calendário ou comentário. O padrão está marcado.

* **[!UICONTROL Permitir monitoramento]**

   Se marcada, permita que os membros sigam eventos postados no calendário. O padrão está marcado.

* **[!UICONTROL Tamanho máximo do arquivo]**

   Relevante apenas se `Allow File Uploads` for verificada. Este campo limitará o tamanho (em bytes) de um arquivo carregado. O padrão é 104857600 (10 Mb).

* **[!UICONTROL Tipos de arquivos permitidos]**

   Relevante apenas se `Allow File Uploads` for verificada. Uma lista separada por vírgulas de extensões de arquivos com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, o upload dos não especificados não será permitido. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Tamanho máximo do arquivo de imagem a ser anexado]**

   Relevante somente se a opção Permitir uploads de arquivo estiver marcada. Número máximo de bytes que um arquivo de imagem carregado pode ter. O padrão é 2097152 (2 Mb).

* **[!UICONTROL Tipos de imagem de capa permitidos]**

   Uma lista separada por vírgulas de extensões de arquivos de imagem com o separador &quot;ponto&quot;. O padrão é `.jpg,.jpeg,.png,.gif,.bmp`.

* **[!UICONTROL Permitir respostas encadeadas]**

   Se marcada, permita respostas para comentários postados no evento de calendário. O padrão está marcado.

* **[!UICONTROL Permitir que usuários excluam comentários e eventos]**

   Se marcada, permita que os membros excluam os comentários e os eventos de calendário publicados. O padrão está marcado.

* **[!UICONTROL Permitir votação]**

   Se marcada, inclua o recurso Voto com um evento de calendário. O padrão está marcado.

* **[!UICONTROL Mostrar navegações estruturais]**

   Mostrar navegações estruturais na página do evento. O padrão está marcado.

* **[!UICONTROL Filtro do intervalo de datas]**

   Define o número de dias adicionados à data atual para calcular o valor &quot;Até&quot; do filtro da página de listagem de eventos do calendário. O número padrão é 30.

* **[!UICONTROL Ativar conteúdo em destaque]**

   Se marcada, a ideia pode ser identificada como conteúdo [em](featured.md)destaque. O padrão está desmarcado.

Na guia Moderação **[!UICONTROL do]** usuário, especifique como os tópicos e respostas publicados (conteúdo gerado pelo usuário) são gerenciados. Para obter mais informações, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

#### Guia Moderação do usuário {#user-moderation-tab}

* **[!UICONTROL Negar postagens]**

   Se marcada, os moderadores de membros confiáveis poderão negar publicações e impedir que a publicação apareça no fórum público. O padrão está marcado.

* **[!UICONTROL Fechar / Reabrir eventos]**

   Se marcada, os moderadores de membros confiáveis podem fechar um evento para outras edições e comentários, e também podem reabrir um evento. O padrão está marcado.

* **[!UICONTROL Sinalizar postagens]**

   Se marcada, permita que os membros sinalizem eventos ou comentários de outras pessoas como inadequados. O padrão está marcado.

* **[!UICONTROL Sinalizar lista de motivo]**

   Se marcada, permita que os membros escolham, em uma lista suspensa, seu motivo para marcar um evento ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo personalizado de sinalização]**

   Se marcada, permita que os membros digitem seu próprio motivo para marcar um evento ou comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**

   Insira o número de vezes que um evento ou comentário deve ser sinalizado pelos membros antes que os moderadores sejam notificados. O padrão é 1 (uma vez).

* **[!UICONTROL Limite de sinalização]**

   Insira o número de vezes que um evento ou comentário deve ser sinalizado antes de ser ocultado da exibição pública. Se definido como -1, o tópico ou comentário sinalizado nunca será ocultado da exibição pública. Caso contrário, esse número deve ser maior ou igual ao Limite de moderação. O padrão é 5.

#### Guia Campo de tag {#tag-field-tab}

Na guia Campo **[!UICONTROL de]** tag , as tags que podem ser aplicadas, se permitidas na guia **[!UICONTROL Configurações]** , são limitadas de acordo com os namespaces escolhidos.

* **[!UICONTROL Espaços de nomes permitidos]**

   Relevante se `Allow Tagging` estiver marcado na guia **[!UICONTROL Configurações]** . As tags que podem ser aplicadas são limitadas àquelas dentro das categorias de namespace verificadas. A lista de namespaces inclui &quot;Tags padrão&quot; (o namespace padrão) e &quot;Incluir todas as tags&quot;. O padrão não está marcado, o que significa que todos os namespaces são permitidos.

* **[!UICONTROL Limite sugerido]**

   Insira o número de tags a serem exibidas como uma sugestão para o membro postando no fórum. O padrão é `-1` (sem limites).

>[!NOTE]
>
>Visite [Administrando tags](../../help/sites-administering/tags.md) para saber como adicionar um novo namespace de tag (taxonomia).

#### Guia Tradução {#translation-tab}

Na guia **[!UICONTROL Tradução]** , se a tradução estiver ativada para o site da comunidade, a tradução pode ser definida para traduzir o thread inteiro (evento e comentários) em vez de postagens específicas.

* **[!UICONTROL Converter tudo]**

   Se marcada, o evento e os comentários são traduzidos para o idioma preferencial do usuário. O padrão está marcado.

## Experiência do visitante do site {#site-visitor-experience}

No ambiente de publicação, o recurso de calendário exibirá um campo de pesquisa com um intervalo de datas padrão e quaisquer eventos de calendário que se encaixem nesse intervalo.

Quando um evento de calendário é selecionado, os detalhes, a descrição e os comentários do evento de calendário são exibidos.

Outras capacidades dependem de o visitante do site ser um moderador, administrador, membro da comunidade, membro privilegiado ou anônimo.

### Moderadores e administradores {#moderators-and-administrators}

Quando o usuário conectado tem privilégios de moderador ou administrador, ele pode executar tarefas [de](moderate-ugc.md) moderação (conforme permitido pela configuração do componente) em todos os eventos de calendário e comentários postados em um evento.

![chlimage_1-115](assets/chlimage_1-115.png)

### Membros {#members}

Quando o usuário conectado é membro da comunidade ou membro [](users.md#privileged-members-group) privilegiado (dependendo da configuração), ele pode optar por `New Event` criar e publicar um novo evento de calendário.

Especificamente, podem

* Criar um novo evento de calendário
* Publicar um comentário em um evento de calendário
* Editar seu próprio evento de calendário ou comentário
* Excluir seus próprios eventos ou comentários do calendário
* Sinalizar eventos de calendário ou comentários de outras pessoas

![chlimage_1-116](assets/chlimage_1-116.png) ![chlimage_1-117](assets/chlimage_1-117.png)

### Anônimo {#anonymous}

Os visitantes do site que não estão conectados só podem ler eventos de calendário publicados, traduzi-los se houver suporte, mas não podem adicionar eventos ou comentários nem sinalizar eventos ou comentários de outras pessoas.

![chlimage_1-118](assets/chlimage_1-118.png)

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [Calendar Essentials](calendar-basics-for-developers.md) para desenvolvedores.

Para moderação de eventos e comentários do calendário, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

Para marcar eventos de calendário e comentários, consulte [Marcação de conteúdo](tag-ugc.md)gerado pelo usuário.

Para obter a tradução de eventos de calendário e comentários, consulte [Traduzindo conteúdo](translate-ugc.md)gerado pelo usuário.
