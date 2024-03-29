---
title: Criar novas pastas para categorizar formulários
seo-title: Create new folders to categorize forms
description: Use pastas para organizar modelos de formulário, PDF, recursos e formulários adaptáveis.
seo-description: Use folders to organize your form templates, PDFs, resources, and adaptive forms.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Admin
exl-id: 6c989701-10c7-466e-b3e5-008a6d377574
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 2%

---

# Criar novas pastas para categorizar formulários {#create-new-folders-to-categorize-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode organizar seus ativos melhor usando pastas. Como o AEM Forms suporta vários tipos de ativos, como modelos de formulário, PDF, documentos, recursos e formulários adaptáveis, com vários metadados, você pode usar pastas para categorizar seus formulários com base nos critérios desejados.

O AEM Forms permite alterar o título de uma pasta. O título não é o mesmo do nó sob o qual a pasta é armazenada no repositório. Em vez disso, o título é mantido como metadados para a pasta. Se você alterar o título de uma pasta, o caminho de qualquer ativo presente na pasta não será afetado.

## Crie uma pasta  {#create-a-folder}

Você pode criar uma pasta no AEM Forms de uma das seguintes maneiras:

* Faça upload de um arquivo ZIP contendo ativos na estrutura de pastas desejada (consulte [Obter documentos XDP e PDF no AEM Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Criar uma nova pasta vazia

1. Faça logon na interface do usuário do AEM Forms em `https://<server>:<port>/aem/forms.html`.
1. Navegue até o local em que deseja criar uma pasta.
1. Clique no botão ![aem6forms_add](assets/aem6forms_add.png) na barra de ferramentas e selecione **[!UICONTROL Criar pasta]**.

1. Insira os seguintes detalhes:

   * **Título:** Nome de exibição para a pasta
   * **Nome:** *(Obrigatório)* O nome do nó no qual você deseja armazenar a pasta no repositório

   >[!NOTE]
   >
   >Por padrão, o valor do campo de nome é preenchido automaticamente a partir do título. O nome só pode conter caracteres alfanuméricos ou os caracteres especiais de hífen (-) e sublinhado (_). Quaisquer outros caracteres especiais inseridos no título serão substituídos automaticamente por um hífen e você será solicitado a confirmar o novo nome. Você pode optar por continuar com o nome sugerido ou editá-lo ainda mais.

1. Clique em **[!UICONTROL Enviar].**

   Uma nova pasta com o título definido é exibida no local atual na lista de ativos.

   Se existir uma pasta com o nome especificado, o envio falhará com um erro. Você pode exibir a mensagem de erro passando o mouse sobre o erro ![aem6forms_error_alert](assets/aem6forms_error_alert.png) ícone que aparece ao lado do campo de nome.

### Editar o título da pasta {#edit-the-folder-title-br}

1. Selecione a pasta cujo título você deseja editar.
1. Clique na edição ![aem6forms_edit](assets/aem6forms_edit.png) na barra de ferramentas.
1. Insira o novo título. O campo de texto é pré-preenchido com o valor atual do título da pasta. Você pode alterá-lo para um novo valor.
1. Clique em **[!UICONTROL Enviar].**
