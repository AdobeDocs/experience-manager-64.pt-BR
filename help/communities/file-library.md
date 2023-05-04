---
title: Recurso da biblioteca de arquivos
seo-title: File Library Feature
description: O recurso Biblioteca de arquivos permite que visitantes do site que fizeram logon façam upload, gerenciem e baixem arquivos
seo-description: The File Library feature lets signed-in site visitors upload, manage, and download files
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# Recurso da biblioteca de arquivos {#file-library-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Introdução {#introduction}

O recurso biblioteca de arquivos fornece um local para visitantes do site com logon (membros da comunidade) fazerem upload, gerenciamento e download de arquivos no site da comunidade.

Esta seção da documentação descreve

* Adicionar o recurso da biblioteca de arquivos a um site AEM
* Configurações para o `File Library` componente

## Adicionar uma biblioteca de arquivos a uma página {#adding-a-file-library-to-a-page}

Para adicionar uma `File Library` para uma página no modo autor, localize o componente

* `Communities / File Library`

e arraste-a para o local em uma página.

Para obter as informações necessárias, visite [Noções básicas sobre componentes do Communities](basics.md).

Quando a variável [bibliotecas obrigatórias do lado do cliente](essentials-file-library.md#essentials-for-client-side) são incluídos, é assim que a variável `File Library` componente será exibido:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configuração da biblioteca de arquivos {#configuring-file-library}

Selecione o `File Library` para acessar e selecionar o `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Guia Comentários {#comments-tab}

Em **[!UICONTROL Comentários]** , especifique se e como os comentários dos arquivos carregados são exibidos:

* **[!UICONTROL Permitir comentários em arquivos]**
Se marcada, permita comentários em arquivos carregados. O padrão está desmarcado.

* **[!UICONTROL Comentários por página]**
Limita o número de comentários exibidos por página, bem como o número de respostas exibidas. O padrão é 
**10**.

* **[!UICONTROL Tamanho máximo do arquivo]**
Esse valor limitará o tamanho do arquivo carregado. O limite padrão é 104857600 (10 Mb).

* **[!UICONTROL Extensão Máx. da Mensagem]**
Número máximo de caracteres que podem ser inseridos na caixa de texto. O padrão é 4096 caracteres.

* **[!UICONTROL Tipos de arquivo permitidos]**
Uma lista separada por vírgulas de extensões de arquivo com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se qualquer tipo de arquivo for especificado, os não especificados não serão permitidos. O padrão é nenhum especificado, de modo que todos os tipos de arquivo são permitidos.

* **[!UICONTROL Editor de Rich Text]**
Se marcada, os comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Excluir comentários]**
Se marcada, os usuários poderão excluir seus próprios comentários. O padrão está marcado.

* **[!UICONTROL Permitir marcação]**
Se marcada, a capacidade de adicionar uma tag ao arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Espaços de nomes permitidos]**
Se a opção Permitir marcação estiver marcada, as tags disponíveis serão limitadas aos namespaces marcados. Se nenhum estiver marcado, então todos são permitidos. O padrão é todos os namespaces.

* **[!UICONTROL Limite de Sugestão]**
Se a opção Permitir marcação estiver marcada, essa configuração limitará o número de tags sugeridas a serem exibidas. Se definido como -1, não há limite. O padrão é -1.

* **[!UICONTROL Permitir votação]**
Se marcada, a capacidade de votar em um arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Permitir Seguindo]**
Se marcada, inclua o seguinte recurso para artigos do blog, que permite que os membros sejam [notificado](notifications.md) de novos posts. O padrão está desmarcado.

* **[!UICONTROL Permitir respostas encadeadas]**
Se marcada, permita respostas para comentários postados. O padrão está desmarcado.

### Guia Moderação do usuário {#user-moderation-tab}

Em **[!UICONTROL Moderação do usuário]** , configure a moderação de comentários, se os comentários forem permitidos:

* **[!UICONTROL Pré-moderação]**
Se marcada, os comentários devem ser aprovados antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Excluir comentários]**
Se marcada, o visitante que postou o comentário tem a capacidade de excluí-lo. O padrão está marcado.

* **[!UICONTROL Negar comentários]**
Se marcada, permita que os moderadores de membros confiáveis neguem comentários. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir Comentários]**
Se marcada, permita que os moderadores de membros confiáveis fechem e reabram comentários. O padrão está desmarcado.

* **[!UICONTROL Sinalizar comentários]**
Se marcada, permita que os visitantes sinalizem comentários como inadequados. O padrão está desmarcado.

* **[!UICONTROL Lista de Motivos do Sinalizador]**
Se marcada, permita que os visitantes escolham, em uma lista suspensa, o motivo para marcar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo do Sinalizador Personalizado]**
Se marcada, permita que os visitantes insiram seu próprio motivo para marcar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Insira o número de vezes que um comentário deve ser sinalizado por visitantes antes de os moderadores serem notificados. O padrão é uma vez (
**1**).

* **[!UICONTROL Limite de sinalização]**
Insira o número de vezes que um comentário deve ser sinalizado antes de ser oculto da exibição pública. Esse número deve ser maior ou igual a 
**Limite de moderação**. O padrão é 5.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas no [Fundamentos da biblioteca de arquivos](essentials-file-library.md) página para desenvolvedores.

Para obter moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).
