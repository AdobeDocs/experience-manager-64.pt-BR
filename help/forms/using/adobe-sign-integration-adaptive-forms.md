---
title: Integrar o Acrobat Sign ao AEM Forms
seo-title: Integrate Acrobat Sign with AEM Forms
description: Saiba como configurar o Acrobat Sign para AEM Forms
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 0%

---

# Integrar o Acrobat Sign ao AEM Forms {#integrate-adobe-sign-with-aem-forms}

O Acrobat Sign habilita fluxos de trabalho de assinatura eletrônica para formulários adaptáveis. As assinaturas eletrônicas melhoram os fluxos de trabalho para processar documentos para áreas legais, de vendas, de folha de pagamento, de gerenciamento de recursos humanos e muitas outras.

Em um cenário típico de Acrobat Sign e formulários adaptáveis, um usuário preenche um formulário adaptável para **solicitar um serviço**. Por exemplo, um aplicativo de cartão de crédito e um formulário de benefícios para o cidadão. Quando um usuário preenche, envia e assina o formulário de aplicativo, ele é enviado ao provedor de serviços para que você possa realizar mais ações. O provedor de serviços revisa o aplicativo e usa o Acrobat Sign para marcar o aplicativo aprovado. Para ativar fluxos de trabalho de assinatura eletrônica semelhantes, você pode integrar o Acrobat Sign com o AEM Forms.

Para usar o Acrobat Sign com o AEM Forms, configure o Acrobat Sign nos Serviços da nuvem do AEM:

## Pré-requisitos {#prerequisites}

Você precisa do seguinte para integrar o Acrobat Sign com o AEM Forms:

* Uma atividade [Conta de desenvolvedor do Acrobat Sign.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Um [SSL habilitado](/help/sites-administering/ssl-by-default.md) Servidor AEM Forms.
* Um [Aplicativo de API do Acrobat Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credenciais (ID do cliente e Segredo do cliente) do aplicativo da API do Acrobat Sign.
* Ao reconfigurar, remova a configuração existente do Acrobat Sign das instâncias de autor e de publicação.
* Use [chave de criptografia idêntica](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) para instâncias de criação e publicação.

## Configurar o Acrobat Sign com o AEM Forms {#configure-adobe-sign-with-aem-forms}

Depois que os pré-requisitos estiverem em vigor, execute as seguintes etapas para configurar o Acrobat Sign com o AEM Forms na instância do autor:

1. Na instância do autor do AEM Forms, navegue até **Ferramentas** ![martelo](assets/hammer.png) > **Geral** > **Navegador de configuração**.
   * Consulte a [Documentação do Navegador de configuração](/help/sites-administering/configurations.md) para obter mais informações.
1. No **[!UICONTROL Navegador de configuração]** página, toque em **[!UICONTROL Criar]**.
1. No **[!UICONTROL Criar configuração]** , especifique um **[!UICONTROL Título]** para a configuração, habilite **[!UICONTROL Configurações da nuvem]** e toque em **[!UICONTROL Criar]**. Ele cria um contêiner de configuração para serviços de nuvem.
1. Navegar para **Ferramentas** ![martelo](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** e selecione o contêiner de configuração criado na etapa acima.

   >[!NOTE]
   >
   >Você pode executar as etapas 1 a 4 para criar um novo contêiner de configuração e criar uma configuração do Acrobat Sign no contêiner ou usar o `global` pasta em **Ferramentas** ![martelo](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. Se você criar a configuração no novo contêiner de configuração, especifique o nome do contêiner na **[!UICONTROL Contêiner de configuração]** ao criar um formulário adaptável.

   >[!NOTE]
   Certifique-se de que o URL da página de configuração dos serviços em nuvem comece com **HTTPS**. Caso contrário, [habilitar SSL](/help/sites-administering/ssl-by-default.md) para servidor AEM Forms.

1. Na página de configuração, toque em **[!UICONTROL Criar]** para criar a configuração do Acrobat Sign no AEM Forms.
1. No **[!UICONTROL Geral]** da guia **[!UICONTROL Criar configuração do Acrobat Sign]** especifique um **Nome** para a configuração e toque em **Próximo**. Como opção, você pode especificar um título e procurar para selecionar uma miniatura para a configuração.

1. Copie o URL na janela atual do navegador para um bloco de notas. É necessário configurar o aplicativo Acrobat Sign com o AEM Forms.

1. Defina as configurações de OAuth para o aplicativo Acrobat Sign:

   1. Abra uma janela do navegador e faça logon na conta de desenvolvedor do Acrobat Sign.
   1. Selecione o aplicativo configurado para AEM Forms e toque em Configurar OAuth para aplicativo.
   1. No **Redirecionar URL** , adicione o URL HTTPS copiado na etapa anterior e clique em **Salvar**.
   1. Ative as seguintes configurações OAuth para o aplicativo Acrobat Sign e clique em **Salvar**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Para obter informações passo a passo para definir as configurações do OAuth para um aplicativo Acrobat Sign e obter as chaves, consulte [Definir configurações de oAuth para o aplicativo](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) documentação do desenvolvedor.

   ![Configuração OAuth](assets/oauthconfig_new.png)

1. Volte para o **Criar configuração do Acrobat Sign** página. No **[!UICONTROL Configurações]** , a variável **[!UICONTROL URL de OAuth]** menciona o seguinte URL padrão:

   `https://secure.na1.echosign.com/public/oauth`

   em que:

   **na1** refere-se ao compartilhamento de banco de dados padrão.

   Você pode modificar o valor do compartilhamento de banco de dados. Reinicie o servidor para poder usar o novo valor para o compartilhamento de banco de dados.

1. Especifique a **ID do cliente** (também referido como ID do pedido) e **Segredo do cliente**. Selecione o **Habilitar o Acrobat Sign para anexos também** opção para anexar arquivos anexados a um formulário adaptável ao documento Acrobat Sign correspondente enviado para assinatura.

   Toque **[!UICONTROL Conectar-se ao Acrobat Sign]**. Quando solicitado a fornecer credenciais, forneça o nome de usuário e a senha da conta usada ao criar o aplicativo Acrobat Sign.

   Toque **[!UICONTROL Criar]** para criar a configuração do Acrobat Sign.

1. Abra AEM Console da Web. O URL é `https://'[server]:[port]'/system/console/configMgr`
1. Abrir **Serviço de configuração comum Forms.**
1. No **Permitir** campo , **select** Todos os usuários - Todos os usuários, anônimos ou conectados, podem visualizar anexos, verificar e assinar formulários e clicar em **Salvar.** A instância do autor é configurada para usar o Acrobat Sign.
1. Use [replicação](/help/sites-deploying/replication.md) para criar configurações idênticas nas instâncias de publicação correspondentes.

Agora, o Acrobat Sign é integrado ao AEM Forms e pronto para uso em formulários adaptáveis. Para [usar o serviço Acrobat Sign em um formulário adaptável](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), especifique o contêiner de configuração criado acima nas propriedades do formulário adaptável.

## Configurar o Acrobat Sign scheduler para sincronizar o status de assinatura {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Um formulário adaptável habilitado para Acrobat Sign é enviado somente após todos os signatários concluírem o processo de assinatura. Por padrão, os serviços do Acrobat Sign Scheduler são agendados para verificar (pesquisar) a resposta do assinante após cada 24 horas. Você pode alterar o intervalo padrão do seu ambiente. Execute as seguintes etapas para alterar o intervalo padrão:

1. Faça logon no servidor do AEM Forms com credenciais de administrador e navegue até **Ferramentas** > **Operações** > **Console da Web**.

   Você também pode abrir o seguinte URL em uma janela do navegador:
   `https://[localhost]:'port'/system/console/configMgr`

1. Localize e abra o **Serviço de configuração do Acrobat Sign** opção. Especifique um [expressão cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) no **Expressão do Scheduler de Atualização de Status** e clique em **Salvar**. Por exemplo, para executar o serviço de configuração diariamente às 00:00, especifique `0 0 0 1/1 * ? *` no **Expressão do Scheduler de Atualização de Status** campo.

O intervalo padrão para sincronizar o status do Acrobat Sign agora é alterado.

## Artigos relacionados {#related-articles}

* [Uso do Acrobat Sign em um formulário adaptável](../../forms/using/working-with-adobe-sign.md)
* [Uso do Acrobat Sign com AEM Forms (Vídeo)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integrar o Acrobat Sign ao AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
