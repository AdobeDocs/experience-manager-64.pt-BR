---
title: Blog Essentials
seo-title: Blog Essentials
description: Visão geral do blog
seo-description: Visão geral do blog
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---


# Blog Essentials {#blog-essentials}

Desde AEM 6.1 Communities, um blog é uma atividade comunitária. Os artigos de blog agora são publicados a partir do ambiente de publicação, onde anteriormente os artigos de blog só podiam ser criados no ambiente do autor e publicados.

Os artigos de blog agora podem ser criados por qualquer membro da comunidade, a menos que restritos a membros privilegiados.

Esta página fornece as informações essenciais para trabalhar com o recurso de blog.

>[!NOTE]
>
>A infraestrutura subjacente do recurso de blog é o recurso do journal.

## Essentials for Client-Side {#essentials-for-client-side}

O recurso de blog é composto de dois componentes principais que estão disponíveis ao adicionar a [função de blog](functions.md#blog-function) ou ao adicionar os componentes a uma página no modo de edição do autor.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusivo</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>consulte <a href="blog-feature.md">Recurso de blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra lateral do blog {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**inclusivo**](scf.md#add-or-include-a-communities-component) | Não |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **modelos** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propriedades** | consulte [Recurso de blog](blog-feature.md) |

* [Personalizações do cliente](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API do blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Pontos de extremidade do blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizações do servidor](server-customize.md)

### Função do blog {#blog-function}

Uma estrutura de site da comunidade que inclui a [função Bog](functions.md#blog-function) terá configurado os componentes `Blog` e `Blog Sidebar`. A função Blog suporta a identificação de um [grupo de usuários membro privilegiado](users.md#privileged-members-group).

### Acesso às entradas do blog (UGC) {#accessing-blog-entries-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM Comunidades 6.1, o uso de uma [loja comum](working-with-srp.md) para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral](srp.md)  do provedor de recursos do armazenamento - introdução e visão geral do uso do repositório
* [SRP e UGC Essentials](srp-and-ugc.md)  - métodos e exemplos de utilitários SRP
* [Acesso ao UGC com diretrizes de codificação do SRP](accessing-ugc-with-srp.md) 
* [Refatoração](socialutils.md)  do SocialUtils - mapeamento de métodos de utilitário obsoletos para os métodos atuais do utilitário SRP

## Editor principal {#primary-publisher}

Quando a implantação for um farm de publicação, será necessário identificar um editor principal que pesquisará artigos programados para publicação.

Consulte [Editor principal](deploy-communities.md#primary-publisher) para obter mais detalhes.

## Permitir mídia avançada {#allowing-rich-media}

A plataforma AEM bloqueia links de outros sites para impedir ataques XSS, conforme descrito em

* [Protect contra script entre sites (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partir do AEM 6.2, as modificações anteriormente necessárias para serem feitas manualmente são incluídas no arquivo de configuração padrão do AntiSamy.

A mídia avançada é incorporada em um artigo do blog selecionando o ícone `Embed Media from External Sites`:  ![chlimage_1-471](assets/chlimage_1-471.png)

