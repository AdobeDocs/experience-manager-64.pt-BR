---
title: Envio de uma confirmação de envio de formulário por email
seo-title: Sending a form submission acknowledgement via email
description: O AEM Forms permite configurar a ação de envio de email que envia uma confirmação a um usuário ao enviar o formulário.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# Envio de uma confirmação de envio de formulário por email {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Envio de dados do formulário adaptável {#adaptive-form-data-submission}

Formulários adaptáveis oferecem vários recursos prontos para uso [enviar ações](/help/forms/using/configuring-submit-actions.md) fluxos de trabalho para enviar os dados do formulário para diferentes pontos de extremidade.

Por exemplo, a variável **Ação de email** enviar ação envia um email após o envio bem-sucedido de um formulário adaptável. Ele também pode ser configurado para enviar os dados do formulário e o PDF no email.

Este artigo detalha as etapas para habilitar a ação Email em um formulário adaptável e diferentes configurações fornecidas.

>[!NOTE]
>
>Também é possível usar a variável **PDF de email** para enviar o formulário preenchido por email como anexo de PDF. As opções de configuração disponíveis para esta ação são as mesmas opções disponíveis para a ação Email . A ação PDF de email está disponível somente para formulários adaptáveis baseados em XFA

## Ação de email {#email-action}

A ação Email permite que um autor envie emails automaticamente para um ou mais recipients no envio bem-sucedido de um formulário adaptável.

>[!NOTE]
>
>Para usar a ação Email , é necessário configurar o serviço de email AEM conforme descrito em [Configuração do serviço de email](/help/sites-administering/notification.md#configuring-the-mail-service).

### Ativar ação de email em um formulário adaptável {#enabling-email-action-on-an-adaptive-form}

1. Abra um formulário adaptável no modo de edição.

1. Clique em **Editar** ao lado do **Início de um formulário adaptável** barra de ferramentas.

   A caixa de diálogo Editar componente é aberta.

   ![Caixa de diálogo Editar componente para um formulário adaptável](assets/start_of_adp_form.png)

1. Selecione o **Enviar ações** e escolha **Ação de email** na lista suspensa Enviar ação .

   A guia exibe as opções para configurar a ação Email para o formulário atual.

   ![Guia Enviar ações](assets/dialog.png)

1. Especifique IDs de email válidas nos campos Mailto, CC e Cco.

   Especifique o assunto e o corpo do email nos campos Assunto e Modelo de email , respectivamente.

   Também é possível especificar espaços reservados variáveis nos campos, nesse caso, os valores dos campos são processados quando o formulário é enviado com êxito por um usuário final. Para obter mais informações, consulte [Uso de nomes de campos de formulário adaptáveis para criar conteúdo de email dinamicamente](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Selecione Incluir anexos se o formulário incluir anexos de arquivo e desejar anexar esses arquivos no email.

   >[!NOTE]
   >
   >Se você escolher a variável **PDF de email**, é necessário selecionar a opção Include attachment .

1. Clique em **OK** para salvar as alterações.

### Uso de nomes de campos de formulário adaptáveis para criar conteúdo de email dinamicamente {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Os nomes de campo em um formulário adaptável são chamados de espaços reservados que são substituídos pelo valor desse campo depois que um usuário envia o formulário.

Na guia Ação de email , é possível usar espaços reservados que são processados quando a ação é executada. Isso implica que os cabeçalhos do email (como Mailto, CC, BCC, assunto) sejam gerados quando o usuário envia o formulário.

Para definir um espaço reservado, especifique `${<field name>}` em um campo na guia Submit actions .

Por exemplo, se o formulário contiver a variável **Endereço de email** campo, nome `email_addr`, para capturar a ID do email de um usuário, é possível especificar o seguinte nos campos Mailto, CC ou CCO.

`${email_addr}`

Quando um usuário envia o formulário, um email é enviado para a ID de email inserida na variável `email_addr` do formulário.

>[!NOTE]
>
>Você pode encontrar o nome de um campo na variável **Editar** para o campo.

Os marcadores de posição de variável também podem ser usados na variável **Assunto** e **Modelo de email** campos.

Por exemplo:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Os campos em painéis repetíveis não podem ser usados como espaços reservados variáveis.
