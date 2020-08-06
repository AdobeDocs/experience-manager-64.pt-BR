---
title: Recurso Biblioteca de arquivos
seo-title: Recurso Biblioteca de arquivos
description: O recurso Biblioteca de arquivos permite que visitantes do site com logon façam upload, gerenciem e baixem arquivos
seo-description: O recurso Biblioteca de arquivos permite que visitantes do site com logon façam upload, gerenciem e baixem arquivos
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---


# Recurso Biblioteca de arquivos {#file-library-feature}

## Introdução {#introduction}

O recurso de biblioteca de arquivos fornece um local para visitantes do site com logon (membros da comunidade) carregarem, gerenciarem e baixarem arquivos no site da comunidade.

Esta seção da documentação descreve

* Adicionar o recurso da biblioteca de arquivos a um site AEM
* Configurações para o `File Library` componente

## Adicionar uma biblioteca de arquivos a uma página {#adding-a-file-library-to-a-page}

Para adicionar um `File Library` componente a uma página no modo de autor, localize o componente

* `Communities / File Library`

e arraste-o para o lugar em uma página.

Para obter as informações necessárias, visite Noções básicas sobre componentes [das comunidades](basics.md).

Quando as bibliotecas [do lado do cliente](essentials-file-library.md#essentials-for-client-side) necessárias forem incluídas, o `File Library` componente aparecerá desta forma:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configuração da biblioteca de arquivos {#configuring-file-library}

Selecione o componente inserido a ser acessado e selecione o `File Library` `Configure` ícone que abre a caixa de diálogo de edição.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Guia Comentários {#comments-tab}

Na guia **[!UICONTROL Comentários]** , especifique se e como os comentários dos arquivos carregados serão exibidos:

* **[!UICONTROL Permitir comentários em arquivos]** Se marcada, permita comentários em arquivos carregados. O padrão está desmarcado.

* **[!UICONTROL Comentários por página]** Limita o número de comentários exibidos por página, bem como o número de respostas exibidas. O padrão é 
**10**.

* **[!UICONTROL Tamanho]** máx. do arquivo Esse valor limitará o tamanho do arquivo carregado. O limite padrão é 104857600 (10 Mb).

* **[!UICONTROL Extensão]** máxima da mensagem Número máximo de caracteres que podem ser inseridos na caixa de texto. O padrão é 4096 caracteres.

* **[!UICONTROL Tipos]** de arquivos permitidosUma lista separada por vírgulas de extensões de arquivos com o separador &quot;ponto&quot;. Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, os não especificados não serão permitidos. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Editor]** de Rich Text Se marcado, os comentários poderão ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Excluir comentários]** Se esta opção estiver marcada, os usuários poderão excluir seus próprios comentários. O padrão está marcado.

* **[!UICONTROL Permitir marcação]** Se marcada, a capacidade de adicionar uma tag ao arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Namespaces permitidas]** Se a opção Permitir marcação estiver marcada, as tags disponíveis serão limitadas às namespaces verificadas. Se nenhum estiver marcado, então todos são permitidos. O padrão é todas as namespaces.

* **[!UICONTROL Limite de sugestão]** Se a opção Permitir marcação estiver marcada, essa configuração limita o número de tags sugeridas a serem exibidas. Se definido como -1, não há limite. O padrão é -1.

* **[!UICONTROL Permitir votação]** Se marcada, a capacidade de votar em um arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Permitir acompanhamento]** Se marcado, inclua o seguinte recurso para artigos de blog, que permite que os membros sejam [notificados](notifications.md) sobre novas publicações. O padrão está desmarcado.

* **[!UICONTROL Permitir respostas encadeadas]** Se marcada, permita respostas a comentários postados. O padrão está desmarcado.

### Guia Moderação do usuário {#user-moderation-tab}

Na guia Moderação **[!UICONTROL do]** usuário, configure a moderação de comentários, se forem permitidos comentários:

* **[!UICONTROL Pré-moderação]** Se marcada, os comentários devem ser aprovados antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Excluir comentários]** Se marcada, o visitante que publicou o comentário terá a capacidade de excluí-lo. O padrão está marcado.

* **[!UICONTROL Negar comentários]** Se esta opção estiver marcada, permita que os moderadores de membros confiáveis neguem comentários. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir comentários]** Se esta opção estiver marcada, permita que os moderadores de membros confiáveis fechem e reabram os comentários. O padrão está desmarcado.

* **[!UICONTROL Sinalizar comentários]** Se marcada, permita que os visitantes sinalizem comentários como inadequados. O padrão está desmarcado.

* **[!UICONTROL Sinalizar Lista]** do motivo Se marcada, permita que os visitantes escolham, em uma lista suspensa, o motivo para sinalizar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Motivo]** de sinalização personalizado Se marcado, permita que os visitantes insiram seu próprio motivo para marcar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limiar]** de moderaçãoInsira o número de vezes que um comentário deve ser sinalizado por visitantes antes que os moderadores sejam notificados. O padrão é uma vez (
**1**).

* **[!UICONTROL Limite de sinalização]** Digite o número de vezes que um comentário deve ser sinalizado antes de ser ocultado da visualização pública. Esse número deve ser maior ou igual a 
**Limite de moderação**. O padrão é 5.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [File Library Essentials](essentials-file-library.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo](moderate-ugc.md)gerado pelo usuário.

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo](tag-ugc.md)gerado pelo usuário.
