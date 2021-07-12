---
title: Configuração de mensagens
seo-title: Configuração de mensagens
description: Mensagens das comunidades
seo-description: Mensagens das comunidades
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Configuração de mensagens {#configuring-messaging}

## Visão geral {#overview}

O recurso de mensagens para o AEM Communities fornece a capacidade de visitantes (membros) do site conectados enviarem mensagens para outros que sejam acessíveis quando conectados ao site.

As mensagens são ativadas para um site da comunidade marcando uma caixa durante [criação do site da comunidade](sites-console.md).

Nesta página estão informações sobre a configuração padrão e possíveis ajustes.

Para obter informações adicionais para desenvolvedores, consulte [Messaging Essentials](essentials-messaging.md).

## Serviço de Operações de Mensagens {#messaging-operations-service}

O [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica o ponto de extremidade que lida com solicitações relacionadas a mensagens, as pastas que o serviço deve usar para armazenar mensagens e, se as mensagens puderem incluir anexos de arquivo, quais tipos de arquivo são permitidos.

Para sites da comunidade criados usando o [console Sites das Comunidades](sites-console.md), já existe uma instância do serviço, com a caixa de entrada definida como `/mail/community/inbox`.

### Serviço de operações de mensagens da comunidade {#community-messaging-operations-service}

Como mostrado abaixo, existe uma configuração do serviço para sites criados com o [assistente de criação de sites](sites-console.md). A configuração pode ser exibida ou editada selecionando o ícone de lápis ao lado da configuração:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nova configuração {#new-configuration}

Para adicionar uma nova configuração, selecione o ícone de adição &#39;**+**&#39; ao lado do nome do serviço:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Lista de]**
permissões dos campos de mensagem Especifica as propriedades do componente Compor mensagem que os usuários podem editar e persistir. Se novos elementos de formulário forem adicionados, a ID do elemento precisará ser adicionada se desejar ser armazenada no SRP. O padrão é duas entradas: 
** assunto e  *conteúdo*.

* **[!UICONTROL Limite de tamanho da caixa de mensagem]**
O número máximo de bytes na caixa de mensagem de cada usuário. O padrão é 
*1073741824*  (1 GB).

* **[!UICONTROL Message count]**
limitO número total de mensagens permitidas por usuário. Um valor de -1 indica que um número ilimitado de mensagens é permitido, sujeito ao limite de tamanho da caixa de mensagem. O padrão é 
*10000*  (10.000)

* **[!UICONTROL Notificar]**
falha de entrega. Se marcada, notifique o remetente se o delivery de mensagem falhar para alguns destinatários. O padrão é 
*verificado*.

* **[!UICONTROL Falha no]**
idName do remetente do delivery que aparece na mensagem de falha do delivery. O padrão é 
*failureNotifier*.

* **[!UICONTROL Caminho do modelo de mensagem de falha]**
Caminho absoluto para a raiz do modelo de mensagem de falha de delivery. O padrão é 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNúmero de vezes para tentar reenviar uma mensagem que não foi entregue. O padrão é 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNumber de segundos para aguardar entre tentativas de reenviar a mensagem após a falha do envio. O padrão é *100 *(segundos).

* **[!UICONTROL Count update pool]**
sizeNúmero de threads simultâneos usados para atualizar a contagem. O padrão é 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a  **`inbox`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a  **`senditems`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/sentitems* .

* **[!UICONTROL supportAttachments.]**
nameSe marcada, os usuários poderão adicionar anexos às suas mensagens. O padrão é 
*verificado*.

* **[!UICONTROL batchSize.]**
nameNumber das mensagens a serem agrupadas em lote para um envio ao enviar para um grande grupo de recipients. O padrão é 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSe supportAttachments estiver marcado, esse valor especifica o tamanho total máximo permitido (em bytes) de todos os anexos. O padrão é 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
nameUm lista de bloqueios de extensões de arquivo, com o prefixo &#39;
**.**&quot;, que será rejeitado pelo sistema. Se não incluir na lista de bloqueios, a extensão será permitida. As extensões podem ser adicionadas ou removidas usando os ícones &#39;**+**&#39; e &#39;**-**&#39;. O padrão é *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Ação necessária*)** Uma  lista de permissões das extensões de arquivo, o oposto da  lista de bloqueios. Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &#39;**-**&#39; para remover a única entrada vazia.

* **[!UICONTROL serviceSelector.name]**
 (*Obrigatório*) Um caminho absoluto (endpoint) pelo qual o serviço é chamado (um recurso virtual). A raiz do caminho escolhido deve ser uma incluída na configuração *Caminhos de execução* de configuração do OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/` e `/services/`. Para selecionar essa configuração para o recurso de mensagens de um site, esse terminal é fornecido como o valor **`Service selector`** para o `Message List and Compose Message components` (consulte [Recurso de Mensagem](configure-messaging.md)). O padrão é */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Campos de mensagem Lista de permissões**.

>[!CAUTION]
>
>Cada vez que uma configuração `Messaging Operations Service` é aberta para edição, se `allowedAttachmentTypes.name` tiver sido removida, uma entrada vazia é adicionada novamente para tornar a propriedade configurável. Uma única entrada vazia desativa os anexos do arquivo.
>
>Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &#39;**-**&#39; para (novamente) remover a única entrada vazia antes de clicar em **[!UICONTROL Salvar]**.

## Resolução de problemas {#troubleshooting}

Uma maneira de solucionar problemas é ativar [mensagens de depuração no log.](../../help/sites-administering/troubleshooting.md)

Consulte também [Registradores e Escritores para Serviços Individuais](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

O pacote a ser monitorado é `com.adobe.cq.social.messaging`.
