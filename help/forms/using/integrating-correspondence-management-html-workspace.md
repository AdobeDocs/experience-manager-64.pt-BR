---
title: Integração de aplicativos de terceiros na área de trabalho AEM Forms
seo-title: Integração de aplicativos de terceiros na área de trabalho AEM Forms
description: Como integrar aplicativos de terceiros como o Gerenciamento de correspondência na área de trabalho da AEM Forms.
seo-description: Como integrar aplicativos de terceiros como o Gerenciamento de correspondência na área de trabalho da AEM Forms.
uuid: 9649157c-fe28-43bf-a7d3-52ed55a0bf4f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: f2bde2e8-da95-48ac-a652-85ead87f2cd3
translation-type: tm+mt
source-git-commit: 3c67867637cb3fdcdce77a5d494b9b150f128a20
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# Integração de aplicativos de terceiros na área de trabalho AEM Forms {#integrating-third-party-applications-in-aem-forms-workspace}

A área de trabalho da AEM Forms oferece suporte ao gerenciamento de atividades de atribuição e conclusão de tarefas para formulários e documentos. Esses formulários e documentos podem ser XDP Forms, Flex® ou Guias (obsoletos) que foram renderizados nos formatos XDP, PDF, HTML ou Flex.

Esses recursos são aprimorados ainda mais. A AEM Forms agora oferece suporte à colaboração com aplicativos de terceiros que oferecem suporte a funcionalidades semelhantes à área de trabalho da AEM Forms. Uma parte comum dessa funcionalidade é o fluxo de trabalho da atribuição e aprovação subsequente de uma tarefa. A AEM Forms fornece uma única experiência unificada para usuários corporativos AEM Forms para que todas as atribuições ou aprovações de tarefa para os aplicativos suportados possam ser tratadas por meio da área de trabalho da AEM Forms.

Como exemplo, consideremos o Gerenciamento de correspondência como o candidato de amostra para integração com a área de trabalho da AEM Forms. O Gerenciamento de correspondência tem o conceito de &quot;Carta&quot;, que pode ser renderizada e permite ações.

## Criar ativos do Gerenciamento de correspondência {#create-correspondence-management-assets}

Start criando um modelo de gerenciamento de correspondência de amostra que é renderizado na área de trabalho do AEM Forms. Para obter mais detalhes, consulte [Criar um modelo de carta](/help/forms/using/create-letter.md).

Acesse o modelo de Gerenciamento de Correspondência em seu URL para verificar se o modelo de Gerenciamento de Correspondência pode ser renderizado com êxito. O URL tem um padrão semelhante a `https://[server]:[port]/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

em que `encodedLetterId` é a ID da letra codificada por URL. Especifique a mesma ID de letra ao definir o processo de renderização para a tarefa de espaço de trabalho no Workbench.

## Criar uma tarefa para renderizar e enviar uma carta AEM Workspace {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

Antes de executar essas etapas, verifique se você é membro dos seguintes grupos:

* cm-agent-users
* Usuários da Workspace

Para obter mais informações, consulte [Adicionar e configurar usuários](/help/forms/using/admin-help/adding-configuring-users.md).

Use as seguintes etapas para criar uma tarefa para renderizar e enviar uma carta AEM Workspace:

1. Inicie o Workbench. Faça logon no localhost como administrador.
1. Clique em Arquivo > Novo > Aplicativo. No campo Nome do aplicativo, digite `CMDemoSample` e clique em Concluir.
1. Selecione `CMDemoSample/1.0` e clique com o botão direito do mouse em `NewProcess`. No campo de nome, digite `CMRenderer` e clique em Concluir.
1. Arraste o seletor de atividade do Ponto de Start e configure-o:

   1. Em Dados de apresentação, selecione Usar um ativo CRX.

      ![useacrxasset](assets/useacrxasset.png)

   1. Procurar um ativo. Na caixa de diálogo Selecionar ativo de formulário, a guia Letras lista todas as letras do servidor.

      ![guia](assets/lettertab.png)

   1. Selecione a letra apropriada e clique em **OK**.

1. Clique em Gerenciar Perfis de ação. A caixa de diálogo Gerenciar Perfil de ação é exibida. Certifique-se de que o Processo de renderização e o Processo de envio estejam selecionados adequadamente.
1. Para abrir a carta com um arquivo XML de dados, procure e selecione o arquivo de dados apropriado no Processo de preparação de dados.
1. Clique em OK.
1. Defina as variáveis para Saída do ponto de Start e Anexos de Tarefa. As variáveis definidas conterão dados de Saída de ponto de Start e Anexos de Tarefa.
1. (Opcional) Para adicionar outro usuário no fluxo de trabalho, arraste um seletor de atividade, configure-o e atribua-o a um usuário. Escreva um invólucro personalizado (exemplo fornecido abaixo) ou baixe e instale o DSC (fornecido abaixo) para o modelo Carta extinto, Saída de Ponto de Start e Anexo de tarefa.

   Uma amostra de invólucro personalizado está conforme listado abaixo:

   ```java
   public LetterInstanceInfo getLetterInstanceInfo(Document dataXML) throws Exception {
   try {
   if(dataXML == null)
   throw new Exception("dataXML is missing");
   
   CoreService coreService = getRemoteCoreService();
   if (coreService == null)
   throw new Exception("Unable to retrive service. Please verify connection details.");
   Map<String, Object> result = coreService.getLetterInstanceInfo(IOUtils.toString(dataXML.getInputStream(), "UTF-8"));
   LetterInstanceInfo letterInstanceInfo = new LetterInstanceInfo();
   
   List<Document> attachmentDocs = new ArrayList<Document>();
   List<byte[]> attachments = (List<byte[]>)result.get(CoreService.ATTACHMENT_KEY);
   if (attachments != null){
   for (byte[] attachment : attachments)
   { attachmentDocs.add(new Document(attachment)); }
   
   }
   letterInstanceInfo.setLetterAttachments(attachmentDocs);
   
   byte[] updateLayout = (byte[])result.get(CoreService.LAYOUT_TEMPLATE_KEY);
   if (updateLayout != null)
   { letterInstanceInfo.setLetterTemplate(new Document(updateLayout)); }
   
   else
   { throw new Exception("template bytes missing while getting Letter instance Info."); }
   
   return letterInstanceInfo;
   } catch (Exception e)
   { throw new Exception(e); }
   
   }
   ```

   [Obter DSC ](assets/dscsample.zip)
FileDownload: Uma amostra de DSC está disponível no  `DSCSample.zip` arquivo anexado acima. Baixe e descompacte o arquivo `DSCSample.zip`. Antes de usar o serviço DSC, é necessário configurá-lo. Para obter informações, consulte [Configurar o serviço DSC](/help/forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p).

   Na caixa de diálogo Definir Atividade, selecione a atividade apropriada, como getLetterInstanceInfo e clique em **OK**.

1. Implante o aplicativo. Se solicitado, faça check-in e salve os ativos.
1. Faça logon na área de trabalho dos formulários AEM em `https://[server]:[port]/lc/content/ws`.
1. Abra a tarefa que você adicionou, CMRenderer. A carta de Gerenciamento de correspondência é exibida.

   ![cminworkspace](assets/cminworkspace.png)

1. Preencha os dados necessários e envie a carta. A janela fecha. Nesse processo, a tarefa é atribuída ao usuário especificado no fluxo de trabalho na etapa 9.

   >[!NOTE]
   >
   >O botão Enviar não é ativado até que todas as variáveis necessárias na letra sejam preenchidas.

