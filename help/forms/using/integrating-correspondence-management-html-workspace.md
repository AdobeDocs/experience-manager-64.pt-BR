---
title: Integração de aplicativos de terceiros na área de trabalho do AEM Forms
seo-title: Integrating third-party applications in AEM Forms workspace
description: Como integrar aplicativos de terceiros como o Gerenciamento de correspondência na área de trabalho do AEM Forms.
seo-description: How-to integrate third-party apps like Correspondence Management in AEM Forms workspace.
uuid: 9649157c-fe28-43bf-a7d3-52ed55a0bf4f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: f2bde2e8-da95-48ac-a652-85ead87f2cd3
exl-id: 4df9a16c-0853-4bbf-81bb-1856ab55c5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# Integração de aplicativos de terceiros na área de trabalho do AEM Forms {#integrating-third-party-applications-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM Forms workspace oferece suporte ao gerenciamento de atividades de atribuição e conclusão de tarefas para formulários e documentos. Esses formulários e documentos podem ser XDP Forms, Flex® forms ou Guias (obsoleto) que foram renderizados nos formatos XDP, PDF, HTML ou Flex.

Esses recursos são aprimorados ainda mais. O AEM Forms agora oferece suporte à colaboração com aplicativos de terceiros que oferecem suporte a funcionalidade semelhante ao espaço de trabalho do AEM Forms. Uma parte comum dessa funcionalidade é o fluxo de trabalho de atribuição e aprovação subsequente de uma tarefa. O AEM Forms fornece uma única experiência unificada para usuários corporativos da AEM Forms, para que todas as atribuições ou aprovações de tarefas para os aplicativos compatíveis possam ser tratadas por meio da área de trabalho do AEM Forms.

Como exemplo, considere o Gerenciamento de correspondência como o candidato de amostra para integração com o espaço de trabalho do AEM Forms. O Gerenciamento de correspondência tem o conceito de &quot;Carta&quot;, que pode ser renderizada e permite ações.

## Criar ativos de gerenciamento de correspondência {#create-correspondence-management-assets}

Comece criando uma amostra de modelo de Gerenciamento de correspondência renderizada no espaço de trabalho do AEM Forms. Para obter mais detalhes, consulte [Criar um modelo de carta](/help/forms/using/create-letter.md).

Acesse o modelo de Gerenciamento de correspondência no URL para verificar se o modelo de Gerenciamento de correspondência pode ser renderizado com êxito. O URL tem um padrão semelhante ao `https://[server]:[port]/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

em que `encodedLetterId` é a ID da letra codificada no URL. Especifique a mesma ID de letra, ao definir o processo de renderização para a tarefa do espaço de trabalho no Workbench.

## Criar uma tarefa para renderizar e enviar uma carta no AEM Workspace {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

Antes de executar essas etapas, verifique se você é membro dos seguintes grupos:

* cm-agent-users
* Usuários do Workspace

Para obter mais informações, consulte [Adicionar e configurar usuários](/help/forms/using/admin-help/adding-configuring-users.md).

Use as etapas a seguir para criar uma tarefa para renderizar e enviar uma carta AEM Workspace:

1. Inicie o Workbench. Faça logon no localhost como administrador.
1. Clique em Arquivo > Novo > Aplicativo. No campo Nome do Aplicativo , informe `CMDemoSample` e, em seguida, clique em Concluir.
1. Selecionar `CMDemoSample/1.0` e clique com o botão direito do mouse `NewProcess`. No campo de nome, digite `CMRenderer` e, em seguida, clique em Concluir.
1. Arraste o seletor de atividade do Ponto de início e configure-o:

   1. Em Dados de apresentação, selecione Usar um ativo CRX.

      ![useacxasset](assets/useacrxasset.png)

   1. Procure um ativo. Na caixa de diálogo Selecionar ativo de formulário, a guia Cartas lista todas as letras no servidor.

      ![lettertab](assets/lettertab.png)

   1. Selecione a letra apropriada e clique em **OK**.

1. Clique em Gerenciar perfis de ação. A caixa de diálogo Gerenciar perfil de ação é exibida. Certifique-se de que o Processo de Renderização e o Processo de Envio estejam selecionados adequadamente.
1. Para abrir a carta com um arquivo XML de dados, procure e selecione o arquivo de dados apropriado no Processo de preparação de dados.
1. Clique em OK.
1. Defina as variáveis para Saída do ponto de início e Anexos da tarefa. As variáveis definidas conterão os dados de Saída do ponto de início e Anexos de tarefa.
1. (Opcional) Para adicionar outro usuário no fluxo de trabalho, arraste um seletor de atividades, configure-o e atribua-o a um usuário. Escreva um wrapper personalizado (exemplo fornecido abaixo) ou baixe e instale o DSC (fornecido abaixo) para expor o modelo Carta, Saída de Ponto Inicial e Anexo de Tarefa.

   Um exemplo de wrapper personalizado é como listado abaixo:

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

   [Obter arquivo](assets/dscsample.zip)
Baixar DSC: Um exemplo de DSC está disponível no `DSCSample.zip` arquivo anexado acima. Baixe e descompacte o `DSCSample.zip` arquivo. Antes de usar o serviço DSC, é necessário configurá-lo. Para obter mais informações, consulte [Configurar o serviço DSC](/help/forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p).

   Na caixa de diálogo Definir atividade , selecione a atividade apropriada, como getLetterInstanceInfo e clique em **OK**.

1. Implante o aplicativo. Se solicitado, faça o check-in e salve os ativos.
1. Faça logon no espaço de trabalho AEM formulários em `https://[server]:[port]/lc/content/ws`.
1. Abra a tarefa adicionada, CMRenderer. A carta de Gerenciamento de correspondência é exibida.

   ![cminworkspace](assets/cminworkspace.png)

1. Preencha os dados necessários e envie a carta. A janela é fechada. Nesse processo, a tarefa é atribuída ao usuário especificado no fluxo de trabalho na etapa 9.

   >[!NOTE]
   >
   >O botão Enviar não é ativado até que todas as variáveis necessárias na carta sejam preenchidas.
