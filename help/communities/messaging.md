---
title: Configuração de mensagens
seo-title: Configuring Messaging
description: Mensagens das comunidades
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# Configuração de mensagens {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O recurso de mensagens para o AEM Communities fornece a capacidade de visitantes (membros) do site conectados enviarem mensagens para outros que sejam acessíveis quando conectados ao site.

As mensagens são ativadas para um site da comunidade ao marcar uma caixa durante [criação de site da comunidade](sites-console.md).

Nesta página estão informações sobre a configuração padrão e possíveis ajustes.

Para obter mais informações para desenvolvedores, consulte [Fundamentos das mensagens](essentials-messaging.md).

## Serviço de Operações de Mensagens {#messaging-operations-service}

O [Serviço de operações de mensagens da AEM Communities](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica o endpoint que lida com solicitações relacionadas a mensagens, as pastas que o serviço deve usar para armazenar mensagens e, se as mensagens podem incluir anexos de arquivo, quais tipos de arquivo são permitidos.

Para sites da comunidade criados usando o [Console de sites das comunidades](sites-console.md), uma instância do serviço já existe, com a caixa de entrada definida como `/mail/community/inbox`.

### Serviço de operações de mensagens da comunidade {#community-messaging-operations-service}

Como mostrado abaixo, existe uma configuração do serviço para sites criados com o [assistente de criação de sites](sites-console.md). A configuração pode ser exibida ou editada selecionando o ícone de lápis ao lado da configuração:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nova configuração {#new-configuration}

Para adicionar uma nova configuração, selecione o sinal de mais &#39;**+**&#x200B;Ícone &#39; ao lado do nome do serviço:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Campos de mensagem Lista de permissões]**
Especifica as propriedades do componente Escrever mensagem que os usuários podem editar e persistir. Se novos elementos de formulário forem adicionados, a ID do elemento precisará ser adicionada se desejar ser armazenada no SRP. O padrão é duas entradas: 
*assunto* e *conteúdo*.

* **[!UICONTROL Limite de tamanho da caixa de mensagem]**
O número máximo de bytes na caixa de mensagem de cada usuário. O padrão é 
*1073741824* (1 GB).

* **[!UICONTROL Limite da contagem de mensagens]**
O número total de mensagens permitidas por usuário. Um valor de -1 indica que um número ilimitado de mensagens é permitido, sujeito ao limite de tamanho da caixa de mensagem. O padrão é 
*10000* (10.000)

* **[!UICONTROL Notificar falha de entrega]**
Se marcada, notifique o remetente se o delivery da mensagem falhar para alguns recipients. O padrão é 
*verificado*.

* **[!UICONTROL Falha na ID do remetente do delivery]**
Nome do remetente que aparece na mensagem de falha do delivery. O padrão é 
*failureNotifier*.

* **[!UICONTROL Caminho do modelo de mensagem de falha]**
Caminho absoluto para a raiz do modelo de mensagem com falha de delivery. O padrão é 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
Número de vezes para tentar reenviar a mensagem que não foi entregue. O padrão é 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
Número de segundos para aguardar entre tentativas de reenviar a mensagem após falha do envio. O padrão é *100 *(segundos).

* **[!UICONTROL Tamanho do pool de atualizações de contagem]**
Número de threads simultâneos usados para atualização de contagem. O padrão é 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obrigatório*) O caminho, em relação ao nó do usuário (/home/users/*username*), para usar o para **`inbox`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Obrigatório*) O caminho, em relação ao nó do usuário (/home/users/*username*), para usar o para **`senditems`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]**
Se marcada, os usuários poderão adicionar anexos às suas mensagens. O padrão é 
*verificado*.

* **[!UICONTROL batchSize.name]**
Número de mensagens a serem agrupadas em lote para um envio ao enviar para um grande grupo de recipients. O padrão é 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
Se supportAttachments estiver marcado, esse valor especifica o tamanho total máximo permitido (em bytes) de todos os anexos. O padrão é 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**
Um lista de bloqueios das extensões de arquivo, com o prefixo &#39;
**.**&quot;, que será rejeitado pelo sistema. Se não incluir na lista de bloqueios, a extensão será permitida. As extensões podem ser adicionadas ou removidas usando o &quot;**+**&#39; e &#39;**-**&#x200B;Ícones &#39;. O padrão é *PADRÃO*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Ação necessária*)** Uma  lista de permissões de extensões de arquivo, o oposto da lista de bloqueios. Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o &quot;**-**&#x200B;ícone &#39; para remover a única entrada vazia.

* **[!UICONTROL serviceSelector.name]**
(*Obrigatório*) Um caminho absoluto (endpoint) pelo qual o serviço é chamado (um recurso virtual). A raiz do caminho escolhido deve ser uma incluída no *Caminhos de execução* configuração da configuração da configuração OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/`e `/services/`. Para selecionar essa configuração para o recurso de mensagens de um site, esse terminal é fornecido como **`Service selector`** para a variável `Message List and Compose Message components` (consulte [Recurso de mensagem](configure-messaging.md)). O padrão é */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Use 
**Campos de mensagem Lista de permissões**.

>[!CAUTION]
>
>Cada vez que uma `Messaging Operations Service` a configuração é aberta para edição, se `allowedAttachmentTypes.name` tiver sido removida, uma entrada vazia será adicionada novamente para tornar a propriedade configurável. Uma única entrada vazia desativa os anexos do arquivo.
>
>Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o &quot;**-**&#x200B;ícone &#39; para (novamente) remover a única entrada vazia antes de clicar em **[!UICONTROL Salvar]**.

## Resolução de problemas {#troubleshooting}

Uma maneira de solucionar problemas é ativar [depurar mensagens no log.](../../help/sites-administering/troubleshooting.md)

Consulte também [Registradores e escritores para serviços individuais](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

O pacote a ser monitorado é `com.adobe.cq.social.messaging`.
