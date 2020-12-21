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


# Recurso de biblioteca de arquivos {#file-library-feature}

## Introdução {#introduction}

O recurso de biblioteca de arquivos fornece um local para visitantes do site com logon (membros da comunidade) carregarem, gerenciarem e baixarem arquivos no site da comunidade.

Esta seção da documentação descreve

* Adicionar o recurso da biblioteca de arquivos a um site AEM
* Configurações do componente `File Library`

## Adicionar uma biblioteca de arquivos a uma página {#adding-a-file-library-to-a-page}

Para adicionar um componente `File Library` a uma página no modo de autor, localize o componente

* `Communities / File Library`

e arraste-o para o lugar em uma página.

Para obter as informações necessárias, visite [Informações básicas sobre componentes das comunidades](basics.md).

Quando as [bibliotecas obrigatórias do lado do cliente](essentials-file-library.md#essentials-for-client-side) forem incluídas, o componente `File Library` aparecerá desta forma:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configurando a biblioteca de arquivos {#configuring-file-library}

Selecione o componente `File Library` inserido para acessar e selecione o ícone `Configure` que abre a caixa de diálogo de edição.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Guia Comentários {#comments-tab}

Na guia **[!UICONTROL Comments]**, especifique se e como os comentários dos arquivos carregados serão exibidos:

* **[!UICONTROL Permitir comentários em]**
arquivosSe marcada, permita comentários em arquivos carregados. O padrão está desmarcado.

* **[!UICONTROL Comentários por]**
páginaLimita o número de comentários exibidos por página, bem como o número de respostas exibidas. O padrão é 
**10**.

* **[!UICONTROL Tamanho máx.]**
do arquivoEsse valor limitará o tamanho do arquivo carregado. O limite padrão é 104857600 (10 Mb).

* **[!UICONTROL Extensão Máx. da MensagemNúmero máximo de caracteres que podem ser inseridos na caixa de texto.]**
O padrão é 4096 caracteres.

* **[!UICONTROL Tipos de arquivos permitidosUma lista separada por vírgulas de extensões de arquivos com o separador &quot;ponto&quot;.]**
Por exemplo: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se algum tipo de arquivo for especificado, os não especificados não serão permitidos. O padrão não é especificado, de modo que todos os tipos de arquivos sejam permitidos.

* **[!UICONTROL Rich Text]**
EditorSe marcado, os comentários podem ser inseridos com marcação. O padrão está desmarcado.

* **[!UICONTROL Excluir]**
comentáriosSe esta opção estiver marcada, os usuários poderão excluir seus próprios comentários. O padrão está marcado.

* **[!UICONTROL Permitir]**
marcaçãoSe marcada, a capacidade de adicionar uma tag ao arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Espaços de]**
nomes permitidosSe a opção Permitir marcação estiver marcada, as tags disponíveis serão limitadas às namespaces verificadas. Se nenhum estiver marcado, então todos são permitidos. O padrão é todas as namespaces.

* **[!UICONTROL Limite]**
de sugestãoSe a opção Permitir marcação estiver marcada, essa configuração limita o número de tags sugeridas a serem exibidas. Se definido como -1, não há limite. O padrão é -1.

* **[!UICONTROL Permitir]**
votaçãoSe marcada, a capacidade de votar em um arquivo será ativada. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
seguidoresSe estiver marcada, inclua o seguinte recurso para artigos de blog, que permite que os membros sejam  [](notifications.md) notificados sobre novas publicações. O padrão está desmarcado.

* **[!UICONTROL Permitir]**
respostas encadeadasSe marcada, permita respostas a comentários postados. O padrão está desmarcado.

### Guia Moderação do usuário {#user-moderation-tab}

Na guia **[!UICONTROL Moderação do usuário]**, configure a moderação de comentários, se forem permitidos comentários:

* **[!UICONTROL Pré-]**
moderaçãoSe marcada, os comentários devem ser aprovados antes de serem exibidos em um site de publicação. O padrão está desmarcado.

* **[!UICONTROL Excluir]**
comentáriosSe marcada, o visitante que publicou o comentário terá a capacidade de excluí-lo. O padrão está marcado.

* **[!UICONTROL Negar]**
comentáriosSe esta opção estiver marcada, permita que os moderadores de membros confiáveis neguem comentários. O padrão está desmarcado.

* **[!UICONTROL Fechar / Reabrir]**
comentáriosSe estiver marcada, permita que os moderadores de membros confiáveis fechem e reabram os comentários. O padrão está desmarcado.

* **[!UICONTROL Sinalizar]**
comentáriosSe estiver marcada, permita que os visitantes sinalizem comentários como inadequados. O padrão está desmarcado.

* **[!UICONTROL Sinalizar]**
lista de motivosSe estiver marcada, permita que os visitantes escolham, em uma lista suspensa, seu motivo para sinalizar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Sinalizador personalizado]**
MotivoSe selecionado, permita que os visitantes insiram seu próprio motivo para sinalizar um comentário como inapropriado. O padrão está desmarcado.

* **[!UICONTROL Limite de moderação]**
Digite o número de vezes que um comentário deve ser sinalizado por visitantes antes que os moderadores sejam notificados. O padrão é uma vez (
**1**).

* **[!UICONTROL Limite]**
de sinalizaçãoInsira o número de vezes que um comentário deve ser sinalizado antes de ser ocultado da visualização pública. Esse número deve ser maior ou igual a 
**Limite de moderação**. O padrão é 5.

## Informações adicionais {#additional-information}

Mais informações podem ser encontradas na página [File Library Essentials](essentials-file-library.md) para desenvolvedores.

Para moderação de tópicos e comentários publicados, consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

Para marcar tópicos e comentários publicados, consulte [Marcação de conteúdo gerado pelo usuário](tag-ugc.md).
