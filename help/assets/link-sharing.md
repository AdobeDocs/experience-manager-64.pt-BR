---
title: Compartilhamento de link de ativos
description: Como compartilhar ativos, pastas e coleções dentro do AEM Assets como um URL para terceiros.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 13%

---


# Compartilhamento de link de ativos {#asset-link-sharing}

Os ativos Adobe Experience Manager (AEM) permitem que você compartilhe ativos, pastas e coleções como um URL com membros de sua organização e entidades externas, incluindo parceiros e fornecedores. Compartilhar ativos por meio de um link é uma maneira conveniente de disponibilizar recursos para terceiros, sem que eles precisem primeiro fazer logon na AEM Assets.

>[!NOTE]
>
>Você precisa da permissão Editar ACL nas pastas e ativos que deseja compartilhar como um link.

## Compartilhar ativos {#share-assets}

Para gerar o URL dos ativos que deseja compartilhar com os usuários, use a caixa de diálogo Compartilhamento de links. Os usuários com privilégios de administrador ou com permissões de leitura no `/var/dam/share` local podem visualização os links compartilhados com eles.

>[!NOTE]
>
>Antes de compartilhar um link com os usuários, verifique se o [!UICONTROL Day CQ Mail Service] está configurado. Ocorre um erro se você tentar compartilhar um link sem primeiro [configurar o Serviço](link-sharing.md#configure-day-cq-mail-service)de e-mail Day CQ.

1. Na interface do usuário Ativos, selecione o ativo a ser compartilhado como um link.
1. Na barra de ferramentas, clique/toque no ícone **[!UICONTROL Compartilhar]** ativos do Link ![](assets/assets_share.png).

   Um link de ativo é criado automaticamente no campo **[!UICONTROL Compartilhar link]** . Copie este link e compartilhe-o com os usuários. A hora de expiração padrão do link é um dia.

   ![Diálogo com o compartilhamento de links](assets/chlimage_1-542.png)

   Como alternativa, prossiga para executar as etapas 3 a 7 desse procedimento para adicionar recipient de e-mail, configurar o tempo de expiração do link e enviá-lo da caixa de diálogo.

   >[!NOTE]
   >
   >Para compartilhar links de seu autor de AEM para entidades externas, exponha somente os seguintes URLs usados para compartilhamento de links, para solicitações de GET. Bloqueie outros URLs para garantir que sua implantação AEM esteja segura.
   >
   >* &lt;Servidor AEM>/linkshare.html
   * &lt;Servidor AEM>/linksharepreview.html
   * &lt;Servidor AEM>/linkexpired.html


   >[!NOTE]
   Se um ativo compartilhado for movido para um local diferente, seu link para de funcionar. Recriar o link e compartilhar novamente com os usuários.

1. No console da Web, abra a configuração do **[!UICONTROL Day CQ Link Externalizer]** e modifique as seguintes propriedades no campo **[!UICONTROL Domínios]** com os valores mencionados em relação a cada:

   * local
   * author
   * publicação

   Para as propriedades `local` e `author` , forneça o URL para as instâncias local e autor, respectivamente. As propriedades `local` e `author` as propriedades têm o mesmo valor se você executar uma única instância do autor AEM. Por exemplo, `publish`forneça o URL da instância de publicação.

1. Na caixa de endereço de email da caixa de diálogo **[!UICONTROL Compartilhamento de links]**, digite a ID de email do usuário com o qual deseja compartilhar o link. Além disso, é possível compartilhar o link com vários usuários.

   Se o usuário for membro de sua organização, selecione a ID de email do usuário nas IDs de email sugeridas que aparecem na lista abaixo da área de digitação. Para um usuário externo, digite a ID de email completa e selecione-a na lista.

   Para permitir o envio de emails para usuários, configure os detalhes do servidor SMTP no [Day CQ Mail Service](link-sharing.md#configure-day-cq-mail-service).

   ![Compartilhar links com ativos diretamente da caixa de diálogo Compartilhamento de links](assets/chlimage_1-543.png)

   Compartilhar links com ativos diretamente da caixa de diálogo Compartilhamento de links

   >[!NOTE]
   Se você inserir uma ID de email de um usuário que não seja membro de sua organização, as palavras &quot;Usuário externo&quot; receberão o prefixo ID de email do usuário.

1. Na caixa **[!UICONTROL Assunto]** , informe um assunto para o ativo que deseja compartilhar.
1. Na caixa **[!UICONTROL Mensagem]** , digite uma mensagem opcional.
1. No campo **[!UICONTROL Expiração]** , especifique uma data e hora de expiração para o link usando o seletor de datas. Por padrão, a data de expiração é definida para uma semana a partir da data em que você compartilha o link.

   ![Definir data e hora de expiração do link compartilhado](assets/chlimage_1-544.png)

1. Para permitir que os usuários baixem a imagem original junto com as execuções, selecione **[!UICONTROL Permitir download do arquivo]** original.

   >[!NOTE]
   Por padrão, os usuários podem baixar somente as representações do ativo que você compartilha como um link.

1. Clique em **[!UICONTROL Compartilhar]**. Uma mensagem confirma que o link é compartilhado com os usuários por meio de um email.
1. Para visualização do ativo compartilhado, clique/toque no link no email enviado ao usuário. O ativo compartilhado é exibido na página do [!UICONTROL Adobe Marketing Cloud] .

   ![Os ativos compartilhados estão disponíveis no Adobe Marketing Cloud](assets/chlimage_1-545.png)

   Para alternar para a visualização da lista, clique/toque no ícone de layout na barra de ferramentas.

1. Para gerar uma visualização do ativo, clique/toque no ativo compartilhado. Clique/toque em **[!UICONTROL Voltar]** na barra de ferramentas para fechar a pré-visualização e retornar à página [!UICONTROL Marketing Cloud] . Se tiver compartilhado uma pasta, clique/toque em **[!UICONTROL Pasta pai]** para retornar à pasta principal.

   ![chlimage_1-546](assets/chlimage_1-546.png)

   >[!NOTE]
   AEM suporta gerar a pré-visualização de ativos desses tipos MIME: JPG, PNG, GIF, BMP, INDD, PDF e PPT. Você só pode baixar os ativos dos outros tipos MIME.

1. Para baixar o ativo compartilhado, clique/toque no ícone **[!UICONTROL Selecionar]** na barra de ferramentas, clique/toque no ativo e, em seguida, clique/toque em **[!UICONTROL Download]** na barra de ferramentas.

   ![Opção da barra de ferramentas para baixar o ativo compartilhado](assets/chlimage_1-547.png)

1. Para visualização dos ativos compartilhados como links, vá para a interface do usuário Ativos e clique/toque no ícone **[!UICONTROL GlobalNav]** . Escolha **[!UICONTROL Navegação]** na lista para exibir o painel de Navegação.
1. No painel Navegação, escolha **[!UICONTROL Links compartilhados]** para exibir uma lista de ativos compartilhados.
1. Para cancelar o compartilhamento de um ativo, selecione-o e toque/clique em **[!UICONTROL Cancelar compartilhamento]** na barra de ferramentas. Uma mensagem confirma que você não compartilhou o ativo. Além disso, a entrada do ativo é removida da lista.

## Configurar o serviço de correio Day CQ {#configure-day-cq-mail-service}

1. Clique ou toque no logotipo do AEM e navegue até **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. Na lista de serviços, localize o **[!UICONTROL Dia CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * Nome do host do servidor SMTP: nome do host do servidor de email
   * Porta do servidor SMTP: porta do servidor de email
   * Usuário SMTP: nome de usuário do servidor de email
   * Senha SMTP: senha do servidor de email

   ![chlimage_1-548](assets/chlimage_1-548.png)

1. Click/tap **[!UICONTROL Save]**.

## Configurar tamanho máximo de dados {#configure-maximum-data-size}

Quando você baixa ativos do link compartilhado usando o recurso Compartilhamento de link, AEM compacta toda a hierarquia de ativos do repositório e retorna o ativo em um arquivo ZIP. No entanto, na ausência de limites para a quantidade de dados que pode ser compactada em um arquivo ZIP, grandes quantidades de dados são submetidas à compactação, o que causa erros de memória esgotada no JVM. Para proteger o sistema de um possível ataque de negação de serviço devido a essa situação, configure o tamanho máximo usando o parâmetro **[!UICONTROL Máximo de tamanho de conteúdo (descompactado)]** para o Servlet **[!UICONTROL Proxy de compartilhamento de ativos ad hoc do]** Day CQ DAM no Configuration Manager. Se o tamanho descompactado do ativo exceder o valor configurado, as solicitações de download do ativo serão rejeitadas. O valor padrão é 100 MB.

1. Clique/toque no logotipo do AEM e acesse **[!UICONTROL Ferramentas > Operações > Console da Web]**.
1. No console da Web, localize a configuração do Servlet **[!UICONTROL Adhoc de Compartilhamento de ativos Ad hoc do]** Day CQ DAM.
1. Abra a configuração do **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** no modo de edição e modifique o valor do parâmetro **[!UICONTROL Tamanho máximo de conteúdo (descompactado)]**.

   ![chlimage_1-549](assets/chlimage_1-549.png)

1. Salve as alterações.

## Best practices and troubleshooting {#best-practices-and-troubleshooting}

* Pastas de ativos ou Coleções que contêm um espaço em branco em seu nome podem não ser compartilhadas.
* Se os usuários não puderem baixar os ativos compartilhados, verifique com o administrador AEM quais são os limites [de](#configure-maximum-data-size) download.
* Se você não puder enviar e-mail com links para ativos compartilhados ou se os outros usuários não puderem receber seu e-mail, verifique com seu administrador AEM se o serviço [de](#configure-day-cq-mail-service) e-mail está configurado ou não.
* Se você não puder compartilhar ativos usando a funcionalidade de compartilhamento de links, verifique se você tem as permissões apropriadas. Consulte [compartilhar ativos](#share-assets).
