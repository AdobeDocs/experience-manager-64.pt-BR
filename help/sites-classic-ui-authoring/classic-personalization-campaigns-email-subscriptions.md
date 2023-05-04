---
title: Gerenciamento de assinaturas
seo-title: Managing Subscriptions
description: Os usuários podem ser solicitados a se inscrever em listas de distribuição do Provedor de serviços de email com a ajuda do componente Formulário usado em uma página da Web AEM. Para preparar uma página de AEM com um formulário de inscrição para assinatura das listas de distribuição do serviço de email, você deve aplicar a configuração de serviço correspondente à página de AEM que o possível assinante visitará.
seo-description: Users can be asked to subscribe to Email Service Provider's mailing lists with the help of the Form component used on an AEM web page. To prepare an AEM page with a sign-up form for subscription to your e-mail service mailing lists, you must apply the corresponding service configuration to the AEM page that the potential subscriber will visit.
uuid: b2578a3d-dba1-4114-b21a-5f34c0cccc5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 295cb0a6-29db-42aa-824e-9141b37b5086
exl-id: a1c47909-d186-4a3d-a74b-27ed95b5ed6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 1%

---

# Gerenciamento de assinaturas{#managing-subscriptions}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>O Adobe não planeja aprimorar mais esse recurso (Gerenciamento de leads e listas).\
>A recomendação é aproveitar [Adobe Campaign e sua integração AEM](/help/sites-administering/campaign.md).

Os usuários podem ser solicitados a se inscrever **do Provedor de serviços de email** listas de distribuição com a ajuda do **Formulário** componente usado em uma página AEM da Web. Para preparar uma página de AEM com um formulário de inscrição para assinatura das listas de distribuição do serviço de email, você deve aplicar a configuração de serviço correspondente à página de AEM que o possível assinante visitará.

## Aplicação da configuração do serviço de email a uma página {#applying-email-service-configuration-to-a-page}

Para configurar uma página de AEM:

1. Navegue até o **Sites** guia .
1. Selecione a página que precisa ser configurada para o serviço. Clique com o botão direito do mouse na página e selecione **Propriedades**.

1. Selecionar **Cloud Services** then **Adicionar Serviço**. Selecione uma configuração na lista de configurações disponíveis.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Clique em **OK**.

## Criação de um formulário de inscrição em uma página de AEM para assinar/cancelar a assinatura de listas {#creating-a-sign-up-form-on-an-aem-page-for-subscribing-unsubscribing-to-lists}

Para criar um formulário de inscrição e configurá-lo para assinaturas de listas de distribuição do Provedor de serviços de email:

1. Abra a página de AEM que o usuário visitará.
1. Aplique a configuração do Provedor de serviços de email à página.

1. Adicione um **Formulário** para a página, arrastando o componente do sidekick. Se o componente não estiver disponível, alterne para o modo de design e ative **Formulário** grupo.
1. Clique em **Editar** no **Início do formulário** e navegue até a **Avançado** guia .
1. No **Formulário** , selecione **Serviço de e-mail: Criar Assinante** e adicionar à lista.
1. Na parte inferior da caixa de diálogo, abra o **Configuração de ação** , que permite selecionar uma ou mais listas de assinaturas.
1. No **Selecionar lista**, selecione a lista que deseja que os usuários assinem. É possível adicionar várias listas usando o botão de adição (**Adicionar item**).

   ![chlimage_1-10](assets/chlimage_1-10.jpeg)

   >[!NOTE]
   >
   >Sua caixa de diálogo pode ser diferente dependendo do provedor de serviços de email.

1. No **Formulário** , selecione a página de agradecimento que deseja que os usuários acessem depois de enviarem o formulário (se deixado em branco, o formulário será exibido novamente após o envio). Clique em **OK**. Um **ID de email** componente aparece no Formulário, o que permite criar um formulário em que os usuários podem enviar seus endereços de email para assinar ou cancelar a assinatura de uma lista de endereçamento.
1. Adicione o **Enviar** componente de botão do **Formulário** no sidekick.

   O formulário está pronto. Publique a página configurada nas etapas acima junto com o **obrigado** para a instância de publicação. Qualquer assinante em potencial que visitar a página pode preencher o formulário e se inscrever na lista fornecida na configuração.

   >[!NOTE]
   >
   >Para que a assinatura do formulário funcione corretamente, [chaves de criptografia do autor precisam ser exportadas e importadas na instância de publicação](#exporting-keys-from-author-and-importing-on-publish).

## Exportar chaves do autor e importar na publicação {#exporting-keys-from-author-and-importing-on-publish}

Para que a assinatura e o cancelamento de assinatura do serviço de email funcionem por meio do formulário de inscrição na instância de publicação, é necessário seguir estas etapas:

1. Na instância do autor, navegue até o Gerenciador de pacotes.
1. Crie um novo pacote. Defina o filtro como `/etc/key`.
1. Crie e baixe o pacote.
1. Navegue até o Gerenciador de pacotes na instância de publicação e faça upload desse pacote.
1. Navegue até o console do osgi de Publicação e reinicie o pacote chamado **Suporte a criptografia do Adobe Granite**.

## Cancelamento de inscrição de usuários em listas {#unsubscribing-users-from-lists}

Para cancelar a assinatura de usuários em listas:

1. Abra as propriedades da página de AEM que tem o formulário de inscrição para cancelar a assinatura de um lead.
1. Aplique a configuração de serviço à página.
1. Crie um formulário de inscrição na página.
1. Ao configurar o componente, selecione a ação **Serviço de email**: **Cancelar inscrição do usuário da lista.**
1. No menu suspenso, selecione a lista apropriada da qual o usuário será removido ao cancelar a assinatura.

   ![chlimage_1-11](assets/chlimage_1-11.jpeg)

1. Exporte as chaves do autor para publicar.

## Configuração de emails de resposta automática para o serviço de email {#configuring-auto-responder-emails-for-email-service}

Para configurar um email de resposta automática para um assinante:

1. Abra as propriedades da página de AEM que têm o formulário de inscrição para configurar a resposta automática para um lead.
1. Aplique a configuração do ExactTarget à página.

1. Adicione um **Formulário** para a página, arrastando o componente do sidekick. Se o componente não estiver disponível, alterne para o modo de design e ative o **Formulário** grupo.
1. Clique em **Editar** no **Início do formulário** e navegue até a **Avançado** guia .
1. No **Formulário** , selecione **Serviço de e-mail: Envie um email de resposta automática.**
1. **Selecionar um email** (esse é o email enviado como um email de resposta automática).

1. **Selecionar classificação** (essa classificação é usada para enviar o email).
1. Selecione o **Obrigado** página (a página para a qual os usuários são direcionados depois de enviarem o formulário).

   No **Formulário** selecione a página de agradecimento que deseja que os usuários acessem depois de enviarem o formulário. (Caso deixado em branco, o formulário será exibido novamente após o envio.) Clique em **OK**.

1. Exporte as chaves do autor para publicar.
1. Adicione o **Enviar** componente de botão do **Formulário** no sidekick.

   O formulário de inscrição está pronto. Publique a página configurada nas etapas acima junto com o **obrigado** para a instância de publicação. Qualquer assinante em potencial que visitar a página pode preencher o formulário e, ao enviá-lo, o visitante receberá um email de resposta automática na ID de email preenchida no formulário.

   >[!NOTE]
   >
   >Para fazer com que a assinatura do formulário de inscrição funcione corretamente, [chaves de criptografia do autor precisam ser exportadas e importadas na instância de publicação](#exporting-keys-from-author-and-importing-on-publish).

   ![chlimage_1-12](assets/chlimage_1-12.jpeg)
