---
title: Blog Essentials
seo-title: Blog Essentials
description: Visão geral do blog
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# Blog Essentials {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A partir AEM 6.1 Communities, um blog é uma atividade comunitária. Os artigos de blog agora são publicados no ambiente de publicação, onde antes os artigos de blog só podiam ser criados no ambiente de criação e publicados .

Artigos de blog agora podem ser criados por qualquer membro da comunidade, a menos que restritos a membros privilegiados.

Esta página fornece as informações essenciais para trabalhar com o recurso de blog.

>[!NOTE]
>
>A infraestrutura subjacente do recurso de blog é o recurso de diário.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

O recurso de blog é composto de dois componentes principais que estão disponíveis ao adicionar o [Função do blog](functions.md#blog-function) ou adicionando os componentes a uma página no modo de edição do autor.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/diário/componentes/hbs/diário</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>see <a href="blog-feature.md">Recurso de blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra lateral do blog {#blog-sidebar}

| **resourceType** | social/diário/componentes/hbs/barra lateral |
|---|---|
| [**incondicional**](scf.md#add-or-include-a-communities-component) | Não |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **modelos** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propriedades** | see [Recurso de blog](blog-feature.md) |

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [API do blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Pontos de extremidade do blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

### Função do blog {#blog-function}

Uma estrutura de site da comunidade que inclui a variável [Função de blog](functions.md#blog-function) terá configurado `Blog` e `Blog Sidebar` componentes. A função Blog suporta a identificação de um [grupo de usuários membro privilegiado](users.md#privileged-members-group).

### Acesso a Entradas de Blog (UGC) {#accessing-blog-entries-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM 6.1 Comunidades, uso de um [loja comum](working-with-srp.md) O para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - diretrizes de codificação
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais

## Editor principal {#primary-publisher}

Quando a implantação é um farm de publicação, é necessário identificar um editor principal que pesquisará artigos agendados para publicação.

Consulte [Editor principal](deploy-communities.md#primary-publisher) para obter mais detalhes.

## Permitir mídias avançadas {#allowing-rich-media}

A plataforma de AEM bloqueia links de outros sites para impedir ataques de XSS, conforme descrito em

* [Protect contra script entre sites (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partir do AEM 6.2, as modificações anteriormente necessárias manualmente são incluídas no arquivo de configuração padrão do AntiSamy.

A mídia avançada é incorporada em um artigo do blog, selecionando o `Embed Media from External Sites` ícone :  ![chlimage_1-471](assets/chlimage_1-471.png)
