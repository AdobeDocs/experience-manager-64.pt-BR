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
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Configuração de mensagens {#configuring-messaging}

## Visão geral {#overview}

O recurso de mensagens para o AEM Communities fornece a capacidade de visitantes de sites conectados (membros) enviarem mensagens entre si que podem ser acessadas quando conectados ao site.

As mensagens são ativadas para um site da comunidade marcando uma caixa durante a criação [do site da](sites-console.md)comunidade.

Nesta página estão informações sobre a configuração padrão e possíveis ajustes.

Para obter informações adicionais para desenvolvedores, consulte [Messaging Essentials](essentials-messaging.md).

## Serviço de Operações de Mensagens {#messaging-operations-service}

O Serviço [de Operações de Mensagens do](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities identifica o ponto de extremidade que lida com solicitações relacionadas a mensagens, as pastas que o serviço deve usar para armazenar mensagens e, se as mensagens podem incluir anexos de arquivo, quais tipos de arquivos são permitidos.

Para sites da comunidade criados usando o console [Sites das](sites-console.md)Comunidades, já existe uma instância do serviço, com a caixa de entrada definida como `/mail/community/inbox`.

### Serviço de Operações de Mensagens da Comunidade {#community-messaging-operations-service}

Como mostrado abaixo, existe uma configuração do serviço para sites criados com o assistente [de criação de](sites-console.md)sites. A configuração pode ser visualizada ou editada selecionando o ícone de lápis ao lado da configuração:

![chlimage_1-63](assets/chlimage_1-63.png)

### New Configuration {#new-configuration}

Para adicionar uma nova configuração, selecione o ícone de adição &quot;**+**&quot; ao lado do nome do serviço:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Campos de mensagem Lista de permissões]** Especifica as propriedades do componente Compor mensagem que os usuários podem editar e persistir. Se novos elementos de formulário forem adicionados, a ID do elemento precisará ser adicionada se desejar ser armazenada no SRP. O padrão são duas entradas: 
*assunto* e *conteúdo*.

* **[!UICONTROL Limite]** de tamanho da caixa de mensagem O número máximo de bytes na caixa de mensagem de cada usuário. O padrão é 
*1073741824* (1 GB).

* **[!UICONTROL Limite]** de contagem de mensagens O número total de mensagens permitidas por usuário. Um valor de -1 indica que um número ilimitado de mensagens é permitido, sujeito ao limite de tamanho da caixa de mensagem. O padrão é 
*10000* (10 mil).

* **[!UICONTROL Notificar falha]** do delivery Se marcada, notifique o remetente se o delivery da mensagem falhar para alguns recipient. O padrão é 
*verificado*.

* **[!UICONTROL Falha ID]** do remetente do delivery Nome do remetente que aparece na mensagem de falha do delivery. O padrão é 
*failureNotifier*.

* **[!UICONTROL Caminho do modelo de mensagem de falha Caminho]** absoluto para a raiz do modelo de mensagem de falha do delivery. O padrão é 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]** Número de vezes que tentar reenviar a mensagem que falhou ao ser entregue. O padrão é 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]** Número de segundos para aguardar entre as tentativas de reenviar a mensagem após falha no envio. O padrão é *100 *(segundos).

* **[!UICONTROL Contagem do tamanho]** do pool de atualizações Número de threads simultâneos usados para atualização de contagem. O padrão é 
*10*.

* **[!UICONTROL inbox.path.name]**(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a **`inbox`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/caixa de entrada* .

* **[!UICONTROL sentitems.path.name]**(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a **`senditems`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]** Se marcado, os usuários poderão adicionar anexos às suas mensagens. O padrão é 
*verificado*.

* **[!UICONTROL batchSize.name]** Número de mensagens a serem agrupadas em lote para um envio ao enviar para um grande grupo de recipient. O padrão é 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** Se supportAttachments estiver marcado, esse valor especifica o tamanho total máximo permitido (em bytes) de todos os anexos. O padrão é 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]** Uma lista de bloqueios de extensões de arquivo, com o prefixo &#39;
**.**&quot;, isso será rejeitado pelo sistema. Se não for incluir na lista de bloqueios, a extensão será permitida. As extensões podem ser adicionadas ou removidas usando os ícones &quot;**+**&quot; e &quot;**-**&quot;. O padrão é *PADRÃO*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Ação necessária*)** Uma lista de permissões de extensões de arquivo, o oposto da  lista de bloqueios. Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &quot;**-**&quot; para remover a única entrada vazia.

* **[!UICONTROL serviceSelector.name]**(*obrigatório*) Um caminho absoluto (ponto final) pelo qual o serviço é chamado (um recurso virtual). A raiz do caminho escolhido deve ser uma incluída na configuração Caminhos *de execução* da configuração do OSGi [ , como `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`e `/apps/``/services/`. Para selecionar essa configuração para o recurso de mensagens de um site, esse terminal é fornecido como o **`Service selector`** valor para o `Message List and Compose Message components` (consulte Recurso [](configure-messaging.md)de mensagem). O padrão é */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]** Use 
**Campos de mensagem Lista de permissões**.

>[!CAUTION]
>
>Sempre que uma `Messaging Operations Service` configuração é aberta para edição, se `allowedAttachmentTypes.name` foi removida, uma entrada vazia é adicionada novamente para tornar a propriedade configurável. Uma única entrada vazia efetivamente desativa anexos de arquivo.
>
>Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &quot;**-**&quot; para (novamente) remover a única entrada vazia antes de clicar em **[!UICONTROL Salvar]**.

## Resolução de Problemas{#troubleshooting}

Uma maneira de solucionar problemas é ativar a [depuração de mensagens no registro.](../../help/sites-administering/troubleshooting.md)

Consulte também [Loggers e Writers for Individual Services](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

O pacote a ser monitorado é `com.adobe.cq.social.messaging`.
