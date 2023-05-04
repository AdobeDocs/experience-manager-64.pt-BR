---
title: Integração da interface Criar correspondência com o portal personalizado
seo-title: Integrating Create Correspondence UI with your custom portal
description: Saiba como integrar criar interface de usuário de correspondência com seu portal personalizado
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 5%

---

# Integração da interface Criar correspondência com o portal personalizado {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Este artigo detalha como é possível integrar a Solução de criação de correspondência ao seu ambiente.

## Invocação baseada em URL {#url-based-invocation}

Uma maneira de chamar o aplicativo Criar correspondência de um portal personalizado é preparar o URL com os seguintes parâmetros de solicitação:

* o identificador para o modelo de letra (usando o parâmetro cmLetterId) ou o nome do modelo Carta (usando o parâmetro cmLetterName)

* o URL para os dados XML obtidos da fonte de dados desejada (usando o parâmetro cmDataUrl ).

Por exemplo, o portal personalizado prepararia o URL como\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, que pode ser o href de um link no portal.\
Se o portal tiver o nome do modelo Carta em mãos, o URL poderá ser\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Chamar dessa forma não é seguro, pois os parâmetros necessários são passados como uma solicitação do GET, expondo o mesmo (claramente visível) no URL.

>[!NOTE]
>
>Antes de chamar o aplicativo Criar correspondência , salve e faça upload dos dados para chamar a interface do usuário Criar correspondência no dataURL fornecido. Isso pode ser feito pelo próprio portal personalizado ou por outro processo back-end.

## Invocação embutida baseada em dados {#inline-data-based-invocation}

Outra maneira (e mais segura) de chamar o aplicativo Criar correspondência pode ser simplesmente pressionar o URL em `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, ao enviar os parâmetros e dados para chamar o aplicativo Create Correspondence como uma solicitação do POST (ocultando-os do usuário final). Isso também significa que agora é possível transmitir os dados XML para o aplicativo Create Correspondence em linha (como parte da mesma solicitação, usando o parâmetro cmData ), que não era possível/ideal na abordagem anterior.

### Parâmetros para especificação de carta {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>String</td> 
   <td>O identificador da instância da carta.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>String</td> 
   <td><p>O identificador do modelo de carta. </p> <p>Se houver várias letras CM com o mesmo nome em um servidor, o uso do parâmetro cmLetterName no URL acionará um erro "Existem várias letras com o nome". Nesse caso, use o parâmetro cmLetterId no URL em vez de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>String</td> 
   <td>O nome do modelo Carta.</td> 
  </tr>
 </tbody>
</table>

A ordem dos parâmetros na tabela especifica a preferência dos parâmetros usados para carregar a carta.

### Parâmetros para especificar a fonte de dados XML {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Dados XML de um arquivo de origem usando protocolos básicos como cq, ftp, http ou arquivo.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>String</td> 
   <td>Uso de dados xml disponíveis em Instância de Carta.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Para reutilizar os dados de teste anexados no dicionário de dados.</td> 
  </tr>
 </tbody>
</table>

A ordem dos parâmetros na tabela especifica a preferência dos parâmetros usados para carregar os dados XML.

### Outros parâmetros {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booleano</td> 
   <td>Verdadeiro para abrir a carta no modo de visualização<br /> </td> 
  </tr>
  <tr>
   <td>Aleatório</td> 
   <td>Carimbo de data e hora</td> 
   <td>Para resolver os problemas de cache do navegador.</td> 
  </tr>
 </tbody>
</table>

Se você estiver usando o protocolo http ou cq para cmDataURL, o URL de http/cq deve ser acessível anonimamente.
