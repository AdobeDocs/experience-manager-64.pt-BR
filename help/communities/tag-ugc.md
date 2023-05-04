---
title: Marcação de conteúdo gerado pelo usuário
seo-title: Tagging User Generated Content
description: A marcação do conteúdo gerado pelo usuário (UGC) é a forma como os membros da comunidade podem ajudar outros membros a pesquisar conteúdo
seo-description: Tagging of user generated content (UGC) is how community members can help other members search for content
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
role: Admin
exl-id: 834df392-df38-498c-9e2a-489484e20e0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 6%

---

# Marcação de conteúdo gerado pelo usuário {#tagging-user-generated-content}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

A marcação do conteúdo gerado pelo usuário (UGC) é o meio pelo qual os membros da comunidade podem ajudar outros membros a pesquisar conteúdo.

Normalmente, as tags são aplicadas por autores e administradores no ambiente de criação. A marcação do UGC é exclusiva no fato de as tags UGC serem aplicadas pelos membros da comunidade no ambiente de publicação.

Os namespaces e as taxonomias de tags são iguais para ambos os aplicativos.

## Recursos das comunidades {#communities-features}

Os recursos do AEM Communities que podem ser configurados para permitir a marcação são

* [Blog](blog-feature.md)
* [Calendário](calendar.md)
* [Biblioteca de arquivo](file-library.md)
* [Fórum](forum.md#configuretheaddedforum)
* [Perguntas e respostas](working-with-qna.md)

## Administração de tags {#administering-tags}

Consulte [Administração de tags](../../help/sites-administering/tags.md#tagging-console) para criar e gerenciar namespaces e taxonomias de tags.

Consulte [Tag Essentials](tag.md) para obter informações sobre desenvolvedores.

Consulte [Uso da Nuvem de tags sociais](tagcloud.md) para adicionar um componente Nuvem de tag social a uma página, a fim de facilitar a pesquisa por UGC publicado usando as tags aplicadas.

### Permissões de tag {#tag-permissions}

As permissões padrão são definidas para não permitir que os namespaces de tags sejam lidos por todos no ambiente de publicação.

Como as tags são aplicadas ao UGC no ambiente de publicação, a permissão de leitura precisa ser ativada para os membros da comunidade para que possam selecionar tags a serem aplicadas.

Consulte [Definir permissões de tag](../../help/sites-administering/tags.md#setting-tag-permissions).

Veja a seguir como ele aparece no CRXDE quando um administrador aplica permissões de leitura a `/etc/tag/discussions` para o grupo `*Community Engage Members*`.

![chlimage_1-74](assets/chlimage_1-74.png)
