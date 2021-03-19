---
title: Integrar o Adobe Sign ao AEM Forms
seo-title: Integrar o Adobe Sign ao AEM Forms
description: Saiba como configurar o Adobe Sign para AEM Forms
seo-description: Saiba como configurar o Adobe Sign para AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Adobe Sign
translation-type: tm+mt
source-git-commit: 5944eab0bf38551970685eaa98d90c4459720245
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---


# Integrar o Adobe Sign ao AEM Forms {#integrate-adobe-sign-with-aem-forms}

O Adobe Sign habilita fluxos de trabalho de assinatura eletrônica para formulários adaptáveis. As assinaturas eletrônicas melhoram os fluxos de trabalho para processar documentos para áreas legais, de vendas, de folha de pagamento, de gerenciamento de recursos humanos e muitas outras.

Em um cenário típico de Adobe Sign e formulários adaptáveis, um usuário preenche um formulário adaptável para **se aplicar a um serviço**. Por exemplo, um aplicativo de cartão de crédito e um formulário de benefícios para o cidadão. Quando um usuário preenche, envia e assina o formulário de aplicativo, ele é enviado ao provedor de serviços para que você possa realizar mais ações. O provedor de serviços revisa o aplicativo e usa o Adobe Sign para marcar o aplicativo aprovado. Para ativar fluxos de trabalho de assinatura eletrônica semelhantes, você pode integrar o Adobe Sign com o AEM Forms.

Para usar o Adobe Sign com o AEM Forms, configure o Adobe Sign nos Serviços da nuvem do AEM:

## Pré-requisitos {#prerequisites}

Você precisa do seguinte para integrar o Adobe Sign com o AEM Forms:

* Uma conta ativa de desenvolvedor [Adobe Sign.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Um servidor AEM Forms [SSL habilitado](/help/sites-administering/ssl-by-default.md).
* Um [aplicativo da API do Adobe Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credenciais (ID do cliente e Segredo do cliente) do aplicativo da API do Adobe Sign.
* Ao reconfigurar, remova a configuração existente do Adobe Sign das instâncias de autor e de publicação.
* Use [chave de criptografia idêntica](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) para criar e publicar instâncias.

## Configurar o Adobe Sign com AEM Forms {#configure-adobe-sign-with-aem-forms}

Depois que os pré-requisitos estiverem em vigor, execute as seguintes etapas para configurar o Adobe Sign com o AEM Forms na instância do autor:

1. Na instância do autor do AEM Forms, navegue até **Ferramentas** ![martelo](assets/hammer.png) > **Geral** > **Navegador de configuração**.
   * Consulte a [documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.
1. Na página **[!UICONTROL Navegador de configuração]**, toque em **[!UICONTROL Criar]**.
1. Na caixa de diálogo **[!UICONTROL Criar configuração]**, especifique um **[!UICONTROL Título]** para a configuração, ative **[!UICONTROL Configurações de nuvem]** e toque em **[!UICONTROL Criar]**. Ele cria um contêiner de configuração para serviços de nuvem.
1. Navegue até **Ferramentas** ![martelo](assets/hammer.png) > **Cloud Services** > **Adobe Sign** e selecione o contêiner de configuração que você criou na etapa acima.

   >[!NOTE]
   >
   >Você pode executar as etapas 1 a 4 para criar um novo contêiner de configuração e criar uma configuração do Adobe Sign no contêiner ou usar a pasta `global` existente em **Ferramentas** ![martelo](assets/hammer.png) > **Cloud Services** > **Adobe Sign**. Se você criar a configuração no novo contêiner de configuração, especifique o nome do contêiner no campo **[!UICONTROL Contêiner de configuração]** ao criar um formulário adaptável.

   >[!NOTE]
   Certifique-se de que o URL da página de configuração dos serviços de nuvem comece com **HTTPS**. Caso contrário, [ative SSL](/help/sites-administering/ssl-by-default.md) para o servidor AEM Forms.

1. Na página de configuração, toque em **[!UICONTROL Create]** para criar a configuração do Adobe Sign no AEM Forms.
1. Na guia **[!UICONTROL General]** da página **[!UICONTROL Criar configuração do Adobe Sign]**, especifique um **Nome** para a configuração e toque em **Próximo**. Como opção, você pode especificar um título e procurar para selecionar uma miniatura para a configuração.

1. Copie o URL na janela atual do navegador para um bloco de notas. É necessário configurar o aplicativo Adobe Sign com o AEM Forms.

1. Defina as configurações de OAuth para o aplicativo Adobe Sign:

   1. Abra uma janela do navegador e faça logon na conta de desenvolvedor do Adobe Sign.
   1. Selecione o aplicativo configurado para AEM Forms e toque em Configurar OAuth para aplicativo.
   1. Na caixa **Redirecionar URL**, adicione o URL HTTPS copiado na etapa anterior e clique em **Salvar**.
   1. Ative as seguintes configurações OAuth para o aplicativo Adobe Sign e clique em **Salvar**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Para obter informações passo a passo para definir as configurações OAuth para um aplicativo Adobe Sign e obter as chaves, consulte [Definir configurações de Auth para a documentação do desenvolvedor do aplicativo](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![Configuração OAuth](assets/oauthconfig_new.png)

1. Volte para a página **Criar configuração do Adobe Sign**. Na guia **[!UICONTROL Settings]**, o campo **[!UICONTROL OAuth URL]** menciona o seguinte URL padrão:

   `https://secure.na1.echosign.com/public/oauth`

   em que:

   **na1** se refere ao compartilhamento de banco de dados padrão.

   Você pode modificar o valor do compartilhamento de banco de dados. Reinicie o servidor para poder usar o novo valor para o compartilhamento de banco de dados.

1. Especifique o **ID do cliente** (também conhecido como ID do aplicativo) e **Segredo do cliente**. Selecione a opção **Ativar Adobe Sign para anexos também** para anexar arquivos anexados a um formulário adaptável ao documento Adobe Sign correspondente enviado para assinatura.

   Toque em **[!UICONTROL Conectar-se ao Adobe Sign]**. Quando solicitado a fornecer credenciais, forneça o nome de usuário e a senha da conta usada ao criar o aplicativo Adobe Sign.

   Toque em **[!UICONTROL Criar]** para criar a configuração do Adobe Sign.

1. Abra AEM Console da Web. O URL é `https://'[server]:[port]'/system/console/configMgr`
1. Abra **Forms Common Configuration Service.**
1. No campo **Permitir**, **selecione** Todos os usuários - Todos os usuários, anônimos ou conectados, podem visualizar anexos, verificar e assinar formulários e clique em **Salvar.** A instância do autor é configurada para usar o Adobe Sign.
1. Use [replication](/help/sites-deploying/replication.md) para criar configurações idênticas nas instâncias de publicação correspondentes.

Agora, o Adobe Sign é integrado ao AEM Forms e pronto para uso em formulários adaptáveis. Para [usar o serviço Adobe Sign em um formulário adaptável](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), especifique o contêiner de configuração criado acima nas propriedades de formulário adaptável.

## Configure o Adobe Sign scheduler para sincronizar o status de assinatura {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Um formulário adaptável habilitado para Adobe Sign é enviado somente após todos os signatários concluírem o processo de assinatura. Por padrão, os serviços do Adobe Sign Scheduler são agendados para verificar (pesquisar) a resposta do assinante após cada 24 horas. Você pode alterar o intervalo padrão do seu ambiente. Execute as seguintes etapas para alterar o intervalo padrão:

1. Faça logon no servidor do AEM Forms com credenciais de administrador e navegue até **Ferramentas** > **Operações** > **Console da Web**.

   Você também pode abrir o seguinte URL em uma janela do navegador:
   `https://[localhost]:'port'/system/console/configMgr`

1. Localize e abra a opção **Adobe Sign Configuration Service**. Especifique uma [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) no campo **Status Update Scheduler Expression** e clique em **Save**. Por exemplo, para executar o serviço de configuração diariamente às 00:00 am, especifique `0 0 0 1/1 * ? *` no campo **Status Update Scheduler Expression**.

O intervalo padrão para sincronizar o status do Adobe Sign agora é alterado.

## Artigos relacionados {#related-articles}

* [Uso do Adobe Sign em um formulário adaptável](../../forms/using/working-with-adobe-sign.md)
* [Uso do Adobe Sign com AEM Forms (Vídeo)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integrar o Adobe Sign ao AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
