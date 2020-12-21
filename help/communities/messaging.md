---
title: Configuração de mensagens
seo-title: Configuração de mensagens
description: Mensagens de comunidades
seo-description: Mensagens de comunidades
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

As mensagens são ativadas para um site da comunidade marcando uma caixa durante [criação do site da comunidade](sites-console.md).

Nesta página estão informações sobre a configuração padrão e possíveis ajustes.

Para obter informações adicionais para desenvolvedores, consulte [Messaging Essentials](essentials-messaging.md).

## Serviço de Operações de Mensagens {#messaging-operations-service}

O [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica o ponto de extremidade que lida com solicitações relacionadas a mensagens, as pastas que o serviço deve usar para armazenar mensagens e, se as mensagens podem incluir anexos de arquivo, quais tipos de arquivos são permitidos.

Para sites da comunidade criados usando o console [Communities Sites](sites-console.md), já existe uma instância do serviço, com a caixa de entrada definida como `/mail/community/inbox`.

### Community Messaging Operations Service {#community-messaging-operations-service}

Como mostrado abaixo, existe uma configuração do serviço para sites criados com o [assistente de criação de sites](sites-console.md). A configuração pode ser visualizada ou editada selecionando o ícone de lápis ao lado da configuração:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nova configuração {#new-configuration}

Para adicionar uma nova configuração, selecione o ícone de adição &#39;**+**&#39; ao lado do nome do serviço:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Campos de mensagem Lista]**
permitidaEspecifica as propriedades do componente Compor mensagem que os usuários podem editar e persistir. Se novos elementos de formulário forem adicionados, a ID do elemento precisará ser adicionada se desejar ser armazenada no SRP. O padrão são duas entradas: 
** subjetivo e  *conteúdo*.

* **[!UICONTROL Tamanho]**
limite da caixa de mensagemO número máximo de bytes na caixa de mensagem de cada usuário. O padrão é 
*1073741824* (1 GB).

* **[!UICONTROL Limite]**
de contagem de mensagensO número total de mensagens permitidas por usuário. Um valor de -1 indica que um número ilimitado de mensagens é permitido, sujeito ao limite de tamanho da caixa de mensagem. O padrão é 
*10000*  (10 mil).

* **[!UICONTROL Notificar]**
falha do deliverySe marcada, notifique o remetente se o delivery da mensagem falhar para alguns recipient. O padrão é 
*verificado*.

* **[!UICONTROL Falha]**
idName do remetente do delivery que aparece na mensagem de falha do delivery. O padrão é 
*failureNotifier*.

* **[!UICONTROL Caminho do modelo de mensagem de falhaCaminho absoluto para a raiz do modelo de mensagem de falha do delivery.]**
O padrão é 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNúmero de vezes para tentar reenviar a mensagem que não foi entregue. O padrão é 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNúmero de segundos para aguardar entre as tentativas de reenviar a mensagem após falha no envio. O padrão é *100 *(segundos).

* **[!UICONTROL Contagem de]**
tamanho do pool de atualizaçõesNúmero de threads simultâneos usados para atualização de contagem. O padrão é 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a  **`inbox`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/inbox*.

* **[!UICONTROL sentitems.path.name]**
(
*Obrigatório*) O caminho, relativo ao nó do usuário (/home/users/*username*), a ser usado para a  **`senditems`** pasta. O caminho NÃO deve terminar com uma barra à direita &#39;/&#39;. O padrão é */mail/sentitems*.

* **[!UICONTROL supportAttachments.]**
nameSe marcada, os usuários poderão adicionar anexos às suas mensagens. O padrão é 
*verificado*.

* **[!UICONTROL batchSize.]**
nameNúmero de mensagens a serem agrupadas em lote para um envio ao enviar para um grande grupo de recipient. O padrão é 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSe supportAttachments estiver marcado, esse valor especifica o tamanho total máximo permitido (em bytes) de todos os anexos. O padrão é 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
nameUma lista de bloqueios de extensões de arquivo, com o prefixo &#39;
**.**&quot;, isso será rejeitado pelo sistema. Se não for incluir na lista de bloqueios, a extensão será permitida. As extensões podem ser adicionadas ou removidas usando os ícones &#39;**+**&#39; e &#39;**-**&#39;. O padrão é *DEFAULT*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Ação necessária*)** Uma lista de permissões de extensões de arquivo, o oposto da  lista de bloqueios. Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &#39;**-**&#39; para remover a única entrada vazia.

* **[!UICONTROL serviceSelector.name]**
(*obrigatório*) Um caminho absoluto (ponto final) pelo qual o serviço é chamado (um recurso virtual). A raiz do caminho escolhido deve ser uma incluída na configuração *Caminhos de execução* de configuração do OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), como `/bin/`, `/apps/` e `/services/`. Para selecionar essa configuração para o recurso de mensagem de um site, esse terminal é fornecido como o valor **`Service selector`** para `Message List and Compose Message components` (consulte [Recurso de mensagem](configure-messaging.md)). O padrão é */bin/messaging*.

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Campos de mensagem Lista de permissões**.

>[!CAUTION]
>
>Sempre que uma configuração `Messaging Operations Service` for aberta para edição, se `allowedAttachmentTypes.name` tiver sido removida, uma entrada vazia será adicionada novamente para tornar a propriedade configurável. Uma única entrada vazia efetivamente desativa anexos de arquivo.
>
>Para permitir todas as extensões de arquivo, exceto aquelas incluir na lista de bloqueios, use o ícone &#39;**-**&#39; para (novamente) remover a entrada vazia única antes de clicar em **[!UICONTROL Salvar]**.

## Resolução de problemas {#troubleshooting}

Uma maneira de solucionar problemas é ativar [mensagens de depuração no log.](../../help/sites-administering/troubleshooting.md)

Consulte também [Registradores e Escritores para Serviços Individuais](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

O pacote a ser monitorado é `com.adobe.cq.social.messaging`.
