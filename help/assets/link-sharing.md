---
title: Compartilhar ativos usando um link
description: Compartilhe ativos, pastas e coleções como um URL.
contentOwner: AG
feature: Link Sharing,Asset Management
role: User
exl-id: bf4b0acf-4103-4da1-8666-c6d9fe80c41f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 6%

---

# Compartilhar ativo por meio de um link {#asset-link-sharing}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] permite compartilhar ativos, pastas e coleções como um URL com membros de sua organização e entidades externas, incluindo parceiros e fornecedores. O compartilhamento de ativos por meio de um link é uma maneira conveniente de disponibilizar recursos para terceiros, sem que eles precisem primeiro fazer logon no [!DNL Assets].

>[!PREREQUISITES]
>
>* Você precisa de permissão Editar ACL na pasta ou no ativo que deseja compartilhar como um link.
>* Para enviar emails para os usuários, configure os detalhes do servidor SMTP em [Day CQ Mail Service](#configmailservice).


## Compartilhar ativos {#share-assets}

Para gerar o URL para ativos que você deseja compartilhar com usuários, use a caixa de diálogo Compartilhamento de links . Usuários com privilégios de administrador ou com permissões de leitura em `/var/dam/share` Os locais podem exibir os links compartilhados com eles.

1. No [!DNL Assets] na interface do usuário, selecione o ativo a ser compartilhado como um link.
1. Na barra de ferramentas, clique no botão **[!UICONTROL Compartilhar link]** ![ícone compartilhar ativos](assets/assets_share.png). O link que será criado após clicar **[!UICONTROL Compartilhar]** é exibida com antecedência na variável [!UICONTROL Compartilhar link] campo. O link ainda não foi criado até você clicar **[!UICONTROL Enviar]**.

   ![Caixa de diálogo com o compartilhamento de links](assets/chlimage_1-542.png)

   *Figura: A caixa de diálogo para compartilhar ativos como um link.*

1. Na caixa de endereço de email da caixa de diálogo **[!UICONTROL Compartilhamento de links]**, digite a ID de email do usuário com o qual deseja compartilhar o link. Você pode adicionar um ou mais usuários.

   ![Compartilhar links para ativos diretamente da caixa de diálogo Compartilhamento de links](assets/chlimage_1-543.png)

   *Figura: Compartilhar links para ativos diretamente da [!UICONTROL Compartilhamento de link] caixa de diálogo.*

   >[!NOTE]
   >
   >Se você inserir uma ID de email de um usuário que não seja membro de sua organização, as palavras [!UICONTROL Usuário externo] recebem o prefixo da ID de email do usuário.

1. No **[!UICONTROL Assunto]** , insira um assunto para o ativo que deseja compartilhar.
1. No **[!UICONTROL Mensagem]** digite uma mensagem opcional.

1. No **[!UICONTROL Expiração]** , especifique uma data e hora de expiração para o link parar de funcionar. O tempo de expiração padrão do link é de um dia.

   ![Definir a data de expiração do link compartilhado](assets/chlimage_1-544.png)

1. Para permitir que os usuários baixem o ativo original junto com as representações, selecione **[!UICONTROL Permitir download do arquivo original]**. Por padrão, os usuários só podem baixar as representações do ativo que você compartilha como um link.

1. Clique em **[!UICONTROL Compartilhar]**. Uma mensagem confirma que o link é compartilhado com os usuários por meio de um email.

1. Para exibir o ativo compartilhado, clique no link do email enviado ao usuário. Para gerar uma pré-visualização do ativo, clique no ativo compartilhado. Para fechar a visualização, clique em **[!UICONTROL Voltar]**. Se tiver compartilhado uma pasta, clique em **[!UICONTROL Pasta pai]** para retornar à pasta principal.

   ![chlimage_1-546](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] O suporta a geração de visualização de ativos somente dos tipos de arquivos suportados. Se outros tipos MIME forem compartilhados, você só poderá baixar os ativos e não poderá visualizar.

1. Para baixar o ativo compartilhado, clique em **[!UICONTROL Selecionar]** na barra de ferramentas, clique no ativo e, em seguida, clique em **[!UICONTROL Baixar]** na barra de ferramentas.

   ![Opção da barra de ferramentas para baixar o ativo compartilhado](assets/chlimage_1-547.png)

1. Para exibir os ativos compartilhados como links, acesse [!DNL Assets] e clique na [!DNL Experience Manager] logotipo. Choose **[!UICONTROL Navegação]**. No painel Navegação, escolha **[!UICONTROL Links compartilhados]** para exibir uma lista de ativos compartilhados.

1. Para cancelar o compartilhamento de um ativo, selecione-o e clique em **[!UICONTROL Cancelar compartilhamento]** na barra de ferramentas. Uma mensagem de confirmação é exibida. A entrada do ativo é removida da lista.

## Configurar o serviço de email Day CQ {#configure-day-cq-mail-service}

1. No [!DNL Experience Manager] página inicial, navegue até **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
1. Na lista de serviços, localize **[!UICONTROL Day CQ Mail Service]**.
1. Clique em **[!UICONTROL Editar]** ao lado do serviço e configure os seguintes parâmetros para **[!UICONTROL Day CQ Mail Service]** com os dados mencionados em relação aos respectivos nomes:

   * Nome do host do servidor SMTP: nome do host do servidor de email
   * Porta do servidor SMTP: porta do servidor de email
   * Usuário SMTP: nome de usuário do servidor de email
   * Senha SMTP: senha do servidor de email

   ![chlimage_1-548](assets/chlimage_1-548.png)

1. Clique em **[!UICONTROL Salvar]**.

## Configurar o tamanho máximo dos dados {#configure-maximum-data-size}

Ao baixar ativos do link compartilhado com o recurso Compartilhamento de link , [!DNL Experience Manager] compacta a hierarquia de ativos do repositório e retorna o ativo em um arquivo ZIP. No entanto, na ausência de limites para a quantidade de dados que pode ser compactada em um arquivo ZIP, grandes quantidades de dados são sujeitas a compactação, o que causa erros de falta de memória na JVM. Para proteger o sistema de um possível ataque de negação de serviço devido a essa situação, configure o tamanho máximo usando o **[!UICONTROL Tamanho máximo do conteúdo (descompactado)]** parâmetro para **[!UICONTROL Servlet proxy de compartilhamento de ativos ad hoc do Day CQ DAM]** no Configuration Manager. Se o tamanho descompactado do ativo exceder o valor configurado, as solicitações de download de ativos serão rejeitadas. O valor padrão é 100 MB.

1. Clique no botão [!DNL Experience Manager] logotipo e, em seguida, acesse **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.
1. No Console da Web, localize a variável **[!UICONTROL Servlet proxy de compartilhamento de ativos ad hoc do Day CQ DAM]** configuração.
1. Abra a configuração do **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** no modo de edição e modifique o valor do parâmetro **[!UICONTROL Tamanho máximo de conteúdo (descompactado)]**.

   ![chlimage_1-549](assets/chlimage_1-549.png)

1. Salve as alterações.

## Práticas recomendadas e solução de problemas {#best-practices-and-troubleshooting}

* As pastas de ativos ou as Coleções que contêm um espaço em branco no nome podem não ser compartilhadas.
* Se os usuários não conseguirem baixar os ativos compartilhados, verifique com [!DNL Experience Manager] administrador e o [limites de download](#configure-maximum-data-size) são.
* Se não for possível enviar emails com links para ativos compartilhados ou se os outros usuários não puderem receber seu email, verifique com [!DNL Experience Manager] administrador se a variável [serviço de email](#configure-day-cq-mail-service) está configurado ou não.
* Se não for possível compartilhar ativos usando a funcionalidade de compartilhamento de link, verifique se você tem as permissões apropriadas. Consulte [compartilhar ativos](#share-assets).
* Se um ativo compartilhado for movido para um local diferente, seu link para de funcionar. Recrie o link e compartilhe-o com os usuários.

* Se você deseja compartilhar links de seu [!DNL Experience Manager] Implantação do autor em entidades externas, certifique-se de expor apenas os seguintes URLs usados para compartilhamento de link, para `GET` somente solicitações . Bloquear outros URLs por motivos de segurança.

   * `http://[aem_server]:[port]/linkshare.html`
   * `http://[aem_server]:[port]/linksharepreview.html`
   * `http://[aem_server]:[port]/linkexpired.html`
   Em [!DNL Experience Manager] interface, acesso **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**. Abra o **[!UICONTROL Externalizador de links CQ do dia]** e modifique as seguintes propriedades no **[!UICONTROL Domínios]** com os valores mencionados em `local`, `author`e `publish`. Para o `local` e `author` , forneça o URL para as instâncias local e Autor, respectivamente. Se você executar um [!DNL Experience Manager] Instância do autor, use o mesmo valor para `local` e `author` propriedades. Para instâncias de Publicação , forneça o URL do [!DNL Experience Manager] Instância de publicação.
