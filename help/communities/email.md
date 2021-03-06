---
title: Configuração de email
seo-title: Configuração de email
description: Configuração de email para comunidades
seo-description: Configuração de email para comunidades
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Configuração de email {#configuring-email}

O AEM Communities usa email para

* [Notificações de comunidades](notifications.md)
* [Assinaturas das Comunidades](subscriptions.md)

Por padrão, o recurso de email não é funcional, pois requer a especificação de um servidor SMTP e usuário SMTP.

>[!CAUTION]
>
>O email para notificações e assinaturas deve ser configurado somente no [editor primário](deploy-communities.md#primary-publisher).

## Configuração padrão do serviço de email {#default-mail-service-configuration}

O serviço de email padrão é necessário para notificações e assinaturas.

* No editor principal
* Conectado com privilégios de administrador
* Acesse o [Console da Web](../../help/sites-deploying/configuring-osgi.md)

   * Por exemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localize o `Day CQ Mail Service`
* Selecione o ícone de edição

Isso é baseado na documentação de [Configuração de notificação por email](../../help/sites-administering/notification.md), mas com uma diferença no fato de o campo `"From" address` ser *não* necessário e deve ser deixado em branco.

Por exemplo (preenchido com valores somente para fins ilustrativos):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nome]** do host do servidor SMTP:  *(obrigatório)* O servidor SMTP a ser usado.

* **[!UICONTROL Porta do servidor SMTP]** *(obrigatório)* A porta do servidor SMTP deve ser 25 ou superior.

* **[!UICONTROL Usuário]** SMTP:  *(obrigatório)* O usuário SMTP.

* **[!UICONTROL Senha]** SMTP:  *(obrigatório)* A senha do usuário SMTP.

* **[!UICONTROL Endereço]** &quot;De&quot;: Deixe em branco
* **[!UICONTROL SMTP use SSL]**: Se marcada, enviará email seguro. Verifique se a porta está definida como 465 ou conforme necessário para o servidor SMTP.
* **[!UICONTROL Email]** de depuração: Se marcada, ativa o registro de interações do servidor SMTP.

## Configuração de email do AEM Communities {#aem-communities-email-configuration}

Depois que o [serviço de email padrão](#default-mail-service-configuration) é configurado, as duas instâncias existentes da configuração `AEM Communities Email Reply Configuration` OSGi, incluída na versão, tornam-se funcionais.

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

A instância de `AEM Communities Email Reply Configuration` configuração do OSGi com o email Nome é para o recurso de notificações. Esse recurso não inclui a resposta por email.

Essa configuração não deve ser alterada.

* Localize o `AEM Communities Email Reply Configuration`
* Selecione o ícone de edição
* Verifique se o **Nome** é `email`

* Verifique se **Criar publicação a partir do email de resposta** é `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configuração para assinaturas {#configuration-for-subscriptions}

Para assinaturas do Communities, é possível habilitar ou desabilitar a capacidade de um membro postar conteúdo respondendo a um email.

* Localize o `AEM Communities Email Reply Configuration`
* Selecione o ícone de edição
* Verifique se o **Nome** é `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nome]** :  *(obrigatório)* `subscriptions-email`. Não Editar.

* **[!UICONTROL Criar publicação por email]** de resposta: Se marcada, o recipient do email de assinatura pode publicar o conteúdo enviando uma resposta. O padrão está marcado.
* **[!UICONTROL Adicionar id rastreada ao cabeçalho]**: O padrão é  `Reply-To`.

* **[!UICONTROL Comprimento máximo do Assunto]**: Se a ID do rastreador for adicionada à linha de assunto, esse será o comprimento máximo do assunto, excluindo a id rastreada, depois disso ela será cortada. Observe que isso deve ser o menor possível para evitar que as informações de id rastreada sejam perdidas. O padrão é 200.
* **[!UICONTROL Endereço]** &quot;De&quot; do email:  *(obrigatório)* Endereço do qual o email de notificação será entregue. Provavelmente o mesmo **usuário SMTP** especificado para o [serviço de email padrão](#configuredefaultmailservice). O padrão é `no-reply@example.com`.

* **[!UICONTROL Responder para delimitador]**: Se a ID do rastreador for adicionada ao cabeçalho Responder para , esse delimitador será usado. O padrão é `+` (sinal de mais).

* **[!UICONTROL Prefixo da ID do rastreador no assunto]**: Se a ID do rastreador for adicionada à linha de assunto, esse prefixo será usado. O padrão é `post#`.

* **[!UICONTROL Prefixo da ID do rastreador no corpo]** da mensagem: Se a ID do rastreador for adicionada ao corpo da mensagem, esse prefixo será usado. O padrão é `Please do not remove this:`.

* **[!UICONTROL Email como HTML]**: Se marcada, o Tipo de conteúdo do email será definido como  `"text/html;charset=utf-8"`. O padrão está marcado.

* **[!UICONTROL Nome]** de usuário padrão: Esse nome será usado para usuários sem nome. O padrão é `no-reply@example.com`.

* **[!UICONTROL Caminho]** raiz dos modelos: O email é criado usando o modelo armazenado nesse caminho raiz. O padrão é `/etc/community/templates/subscriptions-email`.

## Configurar Importador de Pesquisa {#configure-polling-importer}

Para que o email seja trazido para o repositório, é necessário configurar um importador de pesquisa e configurar suas propriedades no repositório manualmente.

### Adicionar novo importador de pesquisa {#add-new-polling-importer}

* No editor principal
* Conectado com privilégios de administrador
* Navegue até o console do importador de pesquisa
Por exemplo, [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Selecione **[!UICONTROL Adicionar]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Tipo]**:  *(obrigatório)* Puxe para baixo para selecionar  `POP3 (over SSL).`

* **[!UICONTROL URL]**:  *(obrigatório)* O servidor de email de saída. Por exemplo, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importar para Caminho]**&amp;ast;:  *(obrigatório)* Defina como  `/content/usergenerated/mailFolder/postEmails`
navegando até a variável 
`postEmails`e selecione  **OK**

* **[!UICONTROL Intervalo de atualização em segundos]**:  *(opcional)* O servidor de email configurado para o serviço de email padrão pode ter requisitos relacionados ao valor do intervalo de atualização. Por exemplo, o Gmail pode exigir um intervalo de `300`.

* **[!UICONTROL Logon]**:  *(opcional)*

* **[!UICONTROL Senha]**:  *(opcional)*

* Selecione **[!UICONTROL OK]**

### Ajustar Protocolo para Novo Importador de Polling {#adjust-protocol-for-new-polling-importer}

Depois que a nova configuração de pesquisa é salva, é necessário modificar ainda mais as propriedades do importador de email de assinatura para alterar o protocolo de `POP3` para `emailreply`

Usando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* No editor principal
* Conectado com privilégios de administrador
* Navegue até [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importer/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Selecione a configuração recém-criada
* Modifique as seguintes propriedades

   * **feedType**: substituir  `pop3s` por  **`emailreply`**
   * **fonte**: substitua o protocolo da origem  `pop3s://` por  **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Os triângulos vermelhos indicam as propriedades modificadas. Certifique-se de salvar as alterações:

* Selecione **[!UICONTROL Salvar tudo]**
