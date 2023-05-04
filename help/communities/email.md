---
title: Configuração de email
seo-title: Configuring Email
description: Configuração de email para comunidades
seo-description: Email configuration for Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 2%

---

# Configuração de email {#configuring-email}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM Communities usa email para

* [Notificações de comunidades](notifications.md)
* [Assinaturas das Comunidades](subscriptions.md)

Por padrão, o recurso de email não é funcional, pois requer a especificação de um servidor SMTP e usuário SMTP.

>[!CAUTION]
>
>Email para notificações e subscrições deve ser configurado somente no [editor principal](deploy-communities.md#primary-publisher).

## Configuração padrão do serviço de email {#default-mail-service-configuration}

O serviço de email padrão é necessário para notificações e assinaturas.

* No editor principal
* Conectado com privilégios de administrador
* Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md)

   * Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localize a variável `Day CQ Mail Service`
* Selecione o ícone de edição

Isso é baseado na documentação de [Configuração de notificação por email](../../help/sites-administering/notification.md), mas com uma diferença nesse campo `"From" address` é *not* obrigatório e deve ficar vazio.

Por exemplo (preenchido com valores somente para fins ilustrativos):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nome do host do servidor SMTP]**: *(obrigatório)* O servidor SMTP a ser usado.

* **[!UICONTROL Porta do servidor SMTP]** *(obrigatório)* A porta do servidor SMTP deve ser 25 ou superior.

* **[!UICONTROL Usuário SMTP]**: *(obrigatório)* O usuário SMTP.

* **[!UICONTROL Senha SMTP]**: *(obrigatório)* A senha do usuário SMTP.

* **[!UICONTROL Endereço &quot;De&quot;]**: Deixe em branco
* **[!UICONTROL SMTP use SSL]**: Se marcada, enviará email seguro. Verifique se a porta está definida como 465 ou conforme necessário para o servidor SMTP.
* **[!UICONTROL Depurar email]**: Se marcada, ativa o registro de interações do servidor SMTP.

## Configuração de email do AEM Communities {#aem-communities-email-configuration}

Uma vez [serviço de email padrão](#default-mail-service-configuration) for configurada, as duas instâncias existentes do `AEM Communities Email Reply Configuration` A configuração do OSGi, incluída na versão, torna-se funcional.

Somente a instância para assinaturas precisa ser configurada posteriormente ao permitir a resposta por email.

1. ` [email](#configuration-for-notifications)` instância

   para notificações, que não suporta email de resposta e não deve ser alterado

1. ` [subscriptions-email](#configuration-for-subscriptions)` instância

   requer configuração para habilitar totalmente a criação de postagem a partir do email de resposta

Para acessar as instâncias de configuração de email do Communities:

* No editor principal
* Conectado com privilégios de administrador
* Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md)

   * Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localizar `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configuração para notificações {#configuration-for-notifications}

A instância de `AEM Communities Email Reply Configuration` A configuração OSGi com o email Nome é para o recurso de notificações. Esse recurso não inclui a resposta por email.

Essa configuração não deve ser alterada.

* Localize a variável `AEM Communities Email Reply Configuration`
* Selecione o ícone de edição
* Verifique o **Nome** é `email`

* Verificar **Criar publicação por email de resposta** é `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configuração para assinaturas {#configuration-for-subscriptions}

Para assinaturas do Communities, é possível habilitar ou desabilitar a capacidade de um membro postar conteúdo respondendo a um email.

* Localize a variável `AEM Communities Email Reply Configuration`
* Selecione o ícone de edição
* Verifique o **Nome** é `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nome]** : *(obrigatório)* `subscriptions-email`. Não Editar.

* **[!UICONTROL Criar publicação por email de resposta]**: Se marcada, o recipient do email de assinatura pode publicar o conteúdo enviando uma resposta. O padrão está marcado.
* **[!UICONTROL Adicionar id rastreada ao cabeçalho]**: O padrão é `Reply-To`.

* **[!UICONTROL Comprimento máximo do Assunto]**: Se a ID do rastreador for adicionada à linha de assunto, esse será o comprimento máximo do assunto, excluindo a id rastreada, depois disso ela será cortada. Observe que isso deve ser o menor possível para evitar que as informações de id rastreada sejam perdidas. O padrão é 200.
* **[!UICONTROL Endereço &quot;De&quot; do email]**: *(obrigatório)* Endereço do qual o e-mail de notificação seria entregue. Provavelmente o mesmo **Usuário SMTP** especificado para o [serviço de email padrão](#configuredefaultmailservice). O padrão é `no-reply@example.com`.

* **[!UICONTROL Responder para delimitador]**: Se a ID do rastreador for adicionada ao cabeçalho Responder para , esse delimitador será usado. O padrão é `+` (sinal de mais).

* **[!UICONTROL Prefixo da ID do rastreador no assunto]**: Se a ID do rastreador for adicionada à linha de assunto, esse prefixo será usado. O padrão é `post#`.

* **[!UICONTROL Prefixo da ID do rastreador no corpo da mensagem]**: Se a ID do rastreador for adicionada ao corpo da mensagem, esse prefixo será usado. O padrão é `Please do not remove this:`.

* **[!UICONTROL Enviar email como HTML]**: Se marcada, o Tipo de conteúdo do email será definido como `"text/html;charset=utf-8"`. O padrão está marcado.

* **[!UICONTROL Nome de usuário padrão]**: Esse nome será usado para usuários sem nome. O padrão é `no-reply@example.com`.

* **[!UICONTROL Caminho raiz dos modelos]**: O email é criado usando o modelo armazenado nesse caminho raiz. O padrão é `/etc/community/templates/subscriptions-email`.

## Configurar Importador de Pesquisa {#configure-polling-importer}

Para que o email seja trazido para o repositório, é necessário configurar um importador de pesquisa e configurar suas propriedades no repositório manualmente.

### Adicionar novo importador de pesquisa {#add-new-polling-importer}

* No editor principal
* Conectado com privilégios de administrador
* Navegue até o console do importador de pesquisa Por exemplo, [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Selecionar **[!UICONTROL Adicionar]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Tipo]**: *(obrigatório)* Puxe para baixo para selecionar `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(obrigatório)* O servidor de correio de saída. Por exemplo, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importar para Caminho]**&amp;ast;: *(obrigatório)* Defina como `/content/usergenerated/mailFolder/postEmails`
navegando até o 
`postEmails`e selecione **OK**

* **[!UICONTROL Intervalo de atualização em segundos]**: *(opcional)* O servidor de correio configurado para o serviço de correio padrão pode ter requisitos relacionados ao valor do intervalo de atualização. Por exemplo, o Gmail pode exigir um intervalo de `300`.

* **[!UICONTROL Logon]**: *(opcional)*

* **[!UICONTROL Senha]**: *(opcional)*

* Selecionar **[!UICONTROL OK]**

### Ajustar Protocolo para Novo Importador de Polling {#adjust-protocol-for-new-polling-importer}

Depois que a nova configuração de pesquisa for salva, é necessário modificar ainda mais as propriedades do importador de email de assinatura para alterar o protocolo de `POP3` para `emailreply`

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* No editor principal
* Conectado com privilégios de administrador
* Navegue até [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importer/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Selecione a configuração recém-criada
* Modifique as seguintes propriedades

   * **feedType**: replace `pop3s` com **`emailreply`**
   * **source**: substituir o protocolo da origem `pop3s://` com **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Os triângulos vermelhos indicam as propriedades modificadas. Certifique-se de salvar as alterações:

* Selecionar **[!UICONTROL Salvar tudo]**
