---
title: Salvar um formulário HTML5 como rascunho
seo-title: Salvar um formulário HTML5 como rascunho
description: Salve um formulário HTML5 como rascunho e retome o preenchimento do formulário em uma etapa posterior.
seo-description: Salve um formulário HTML5 como rascunho e retome o preenchimento do formulário em uma etapa posterior.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
translation-type: tm+mt
source-git-commit: db4d19e3af11f04369fc7f6a7c13377962f0650a
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 4%

---


# Salvar um formulário HTML5 como rascunho {#saving-an-html-form-as-a-draft}

É possível salvar um formulário HTML5 como rascunho e retomar o preenchimento do formulário em uma etapa posterior. O Forms Portal permite que qualquer usuário salve e restaure um formulário HTML5. Para ativar a funcionalidade Salvar como rascunho, adicione as seguintes configurações ao nó do perfil:

## Perfil personalizado para permitir o recurso Salvar como rascunho {#custom-profile-to-allow-save-as-draft-feature}

A AEM Forms fornece um perfil **Salvar como rascunho** . É possível renderizar um formulário com o perfil Salvar como rascunho para ativar a funcionalidade de rascunho para um formulário HTML5. Você pode especificar um perfil de renderização HTML para um formulário no [Forms Manager](/help/forms/using/introduction-managing-forms.md).

Para ativar a funcionalidade Salvar como rascunho para seu perfil [](/help/forms/using/custom-profile.md)personalizado existente, adicione as seguintes propriedades ao nó do perfil personalizado:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome da Propriedade</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Valor</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>mfAllowFPDraft</td> 
   <td>Sequência de caracteres</td> 
   <td>verdadeiro</td> 
   <td><p>Permite salvar como recurso de rascunho</p> <p>para este perfil.</p> </td> 
  </tr> 
  <tr> 
   <td>mfAllowAttachments</td> 
   <td>Sequência de caracteres</td> 
   <td>verdadeiro</td> 
   <td><p>Permite o carregamento de anexos</p> <p>com este perfil.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Rascunhos armazenamento e listagem {#drafts-storage-and-listing}

Depois de ativar a funcionalidade Salvar como rascunho para um formulário; quando o formulário é salvo, ele é listado no componente [](/help/forms/using/draft-submission-component.md)Rascunhos e Envio. Você pode recuperar e preencher o start do formulário salvo no componente Rascunho e Envio.

Para ativar a listagem de formulários para o componente Rascunho e Envio, adicione a seguinte propriedade ao nó do perfil:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome da Propriedade</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Valor</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>fp.enablePortalSubmit</td> 
   <td>Sequência de caracteres</td> 
   <td>verdadeiro</td> 
   <td>Para permitir que rascunhos e formulários sejam listados no componente Rascunhos e envios do Forms Portal após o envio<br /></td> 
  </tr> 
 </tbody> 
</table>

Por padrão, a AEM Forms armazena os dados do usuário associados ao rascunho e ao envio de um formulário no nó /content/forms/fp na instância Publicar. Você pode adicionar seu provedor de armazenamentos personalizado, para obter detalhes, consulte armazenamento [personalizado para o componente](/help/forms/using/adding-custom-storage-provider-forms.md)Rascunhos e envios.
