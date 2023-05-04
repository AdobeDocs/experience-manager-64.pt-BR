---
title: Fundamentos da biblioteca de arquivos
seo-title: File Library Essentials
description: Trabalhar com o recurso biblioteca de arquivos
seo-description: Working with the file library feature
uuid: 0630f13e-97b4-4f93-9dce-07f559287c29
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9019b967-fff8-4dda-bc5a-fd4a3e14a4ef
exl-id: 0e9d508e-d7dc-478a-99c0-c6885bcdcb81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 4%

---

# Fundamentos da biblioteca de arquivos {#file-library-essentials}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta página fornece as informações essenciais para trabalhar com o recurso biblioteca de arquivos.

## Fundamentos para o lado do cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/filelibrary/components/hbs/filelibrary</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incondicional</strong></a></td> 
   <td>Não</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.filelibrary</td> 
  </tr>
  <tr>
   <td> <strong>modelos</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td> 
  </tr>
  <tr>
   <td><strong> propriedades</strong></td> 
   <td>Consulte <a href="file-library.md">Recurso da biblioteca de arquivos</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizações do lado do cliente](client-customize.md)

## Fundamentos para o lado do servidor {#essentials-for-server-side}

* [API da biblioteca de arquivos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [Endpoints da biblioteca de arquivos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [Personalizações do lado do servidor](server-customize.md)

### Função da biblioteca de arquivo {#file-library-function}

Uma estrutura de site da comunidade que inclui a variável [Função Biblioteca de arquivos](functions.md#file-library-function), inclui um `file library` componente.

### Acessar comentários publicados para bibliotecas de arquivos (UGC) {#accessing-comments-posted-for-file-libraries-ugc}

O UGC deve ser moderado usando um dos métodos padrão de moderação.\
Consulte [Moderação de conteúdo gerado pelo usuário](moderate-ugc.md).

A partir AEM 6.1 Comunidades, uso de um [loja comum](working-with-srp.md) O para UGC inclui acesso programático ao UGC, independentemente da opção de armazenamento escolhida (como ASRP, MSRP ou JSRP).

**A localização e o formato do UGC no repositório estão sujeitos a alterações sem aviso prévio**.

Consulte:

* [Visão geral do provedor de recursos de armazenamento](srp.md) - introdução e visão geral do uso do repositório
* [Princípios básicos de SRP e UGC](srp-and-ugc.md) - Métodos e exemplos de utilitários SRP
* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - diretrizes de codificação
* [Refatoração do SocialUtils](socialutils.md) - mapeamento de métodos de utilitário obsoletos para os métodos de utilitário SRP atuais
