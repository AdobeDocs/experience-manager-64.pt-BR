---
title: Recurso de mensagens
seo-title: Recurso de mensagens
description: Configuração de componentes de mensagens
seo-description: Configuração de componentes de mensagens
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# Recurso de mensagens {#messaging-feature}

Além das interações publicamente visíveis que ocorrem em fóruns e comentários, o recurso de mensagens da AEM Communities permite que os membros da comunidade interajam mais privadamente.

Este recurso pode ser incluído quando um site [da](overview.md#communitiessites) comunidade é criado.

Os recursos de mensagens fornecem a capacidade de:

* Enviar uma mensagem para um ou mais membros da comunidade
* Enviar uma mensagem para um grupo de membros da comunidade
* Enviar uma mensagem com anexos
* Encaminhar uma mensagem
* Responder a uma mensagem
* Excluir uma mensagem
* Restaurar uma mensagem excluída

Para ativar e modificar o recurso de mensagens, visite

* [Configuração de mensagens](messaging.md) para administradores
* [Princípios básicos](essentials-messaging.md) de mensagens para desenvolvedores

>[!NOTE]
>
>Não há suporte para adicionar `Compose Message, Message, or Message List` componentes (encontrados no grupo de `Communities`componentes) a uma página no modo de edição do autor.

## Configuração de componentes de mensagens {#configuring-messaging-components}

Quando as mensagens são ativadas para um site da comunidade, elas são completamente configuradas sem necessidade de outras configurações. Essas informações são fornecidas se houver necessidade de alterar a configuração padrão.

### Configurando a Lista de mensagens (caixa de mensagens) {#configuring-message-list-messagebox}

Para modificar a configuração da lista de mensagens para as páginas **Caixa de entrada**, Itens **** enviados e **Lixeira** do recurso de mensagem, abra o site no modo [de edição do](sites-console.md#authoring-site-content)autor.

No `Preview` modo, selecione o link **[!UICONTROL Mensagens]** para abrir a página principal de mensagens. Em seguida, selecione **[!UICONTROL Caixa de entrada, Itens enviados ou Lixeira]** para configurar o componente para essa lista de mensagem.

No `Edit` modo, selecione o componente na página.

Para acessar a caixa de diálogo de configuração, é necessário cancelar a herança selecionando o `link`ícone.

Quando a configuração for concluída, será necessário restaurar a herança selecionando o `broken link` ícone.

![chlimage_1-396](assets/chlimage_1-396.png)

Depois que a herança for cancelada, será possível selecionar o `configure` ícone para abrir a caixa de diálogo de configuração.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Basic tab {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Seletor]** de serviço (*obrigatório*) Defina isso como o valor da propriedade `serviceSelector.name` do Serviço [de Operações de Mensagens do](messaging.md#messaging-operations-service)AEM Communities.

* **[!UICONTROL Compor página]**(*obrigatório*) A página a ser aberta quando um membro clicar no `Reply` botão. A página público alvo deve conter o formulário **[!UICONTROL Compor mensagem]** .

* **[!UICONTROL Responder/Visualização como Recurso]** Se marcada, o URL de resposta e o URL de Visualização farão referência a um recurso, caso contrário, os dados serão transmitidos como parâmetros de query no URL.

* **[!UICONTROL Formulário]** de exibição de PerfilO formulário de perfil a ser usado para exibir o perfil de remetentes.

* **[!UICONTROL Pasta]** de lixeira Se marcada, esse componente de Lista de mensagem exibirá somente as mensagens sinalizadas como excluídas (lixeira).

* **[!UICONTROL Caminhos]** da pasta (*obrigatório*) Referenciando os valores definidos para `inbox.path.name` e `sentitems.path.name` no Serviço [de Operações de Mensagens do](messaging.md#messaging-operations-service)AEM Communities. Ao configurar para uma `Inbox`, adicione uma entrada usando o valor de `inbox.path.name`. Ao configurar para uma `Outbox`, adicione uma entrada usando o valor de `sentitems.path.name`. Ao configurar para `Trash`, adicione duas entradas com ambos os valores.

#### Guia Exibir {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Marcar botão]** de leitura Se marcada, exibe uma 
`Read`permitindo que uma mensagem seja marcada como lida.

* **[!UICONTROL Botão]** Marcar não lido Se marcado, exibe uma 
`Mark Unread` permitindo que uma mensagem seja marcada como lida.

* **[!UICONTROL Botão Excluir]** Se marcada, exibe uma 
`Delete`permitindo que uma mensagem seja marcada como lida. A funcionalidade de exclusão será duplicado se **`Message Options`** também estiver marcada.

* **[!UICONTROL Opções]** de mensagem Se marcada, exibe 
**`Reply`**, **`Reply All`**, **`Forward`** e **`Delete`** permitir que uma mensagem seja reenviada ou excluída. A funcionalidade de exclusão será duplicado se **`Delete Button`** também estiver marcada.

* **[!UICONTROL Mensagens por página]** O número especificado é o número máximo de mensagens exibidas por página em um esquema de paginação. Se nenhum número for especificado (deixado em branco), todas as mensagens serão exibidas e não haverá paginação.

* **[!UICONTROL Padrões]** de carimbo de data e hora Fornecem padrões de carimbo de data e hora para um ou mais idiomas. O padrão é en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Exibir usuário]** Escolher 
**`Sender`** ou **`Recipients`** para determinar se o Remetente ou os Recipient devem ser exibidos.

### Configurando a mensagem de composição {#configuring-compose-message}

Para modificar a configuração da página de mensagem de composição, abra o site no modo [de edição do](sites-console.md#authoring-site-content)autor.

No `Preview`modo, selecione o link **[!UICONTROL Mensagens]** para abrir a página principal de mensagens. Em seguida, selecione o botão Nova mensagem para abrir a `Compose Message` página.

No `Edit` modo, selecione o componente principal na página que contém o corpo da mensagem.

Para acessar a caixa de diálogo de configuração, é necessário cancelar a herança selecionando o `link`ícone.

Quando a configuração for concluída, será necessário restaurar a herança selecionando o `broken link` ícone.

![chlimage_1-400](assets/chlimage_1-400.png)

Depois que a herança for cancelada, será possível selecionar o `configure` ícone para abrir a caixa de diálogo de configuração.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Basic tab {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL]** de redirecionamentoInsira o URL da página exibida após o envio da mensagem. Por exemplo, 
`../messaging.html`.

* **[!UICONTROL Cancelar URL]** Insira o URL da página exibida se o remetente cancelar a mensagem. Por exemplo, 
`../messaging.html`.

* **[!UICONTROL Comprimento máximo do assunto]** da mensagem O número máximo de caracteres permitidos no campo Assunto. Por exemplo, 500. O padrão não é limite.

* **[!UICONTROL Comprimento máximo do corpo]** da mensagem O número máximo de caracteres permitidos no campo Conteúdo. Por exemplo, 10000. O padrão não é limite.

* **[!UICONTROL Seletor]** de serviço (*obrigatório*) Defina isso como o valor da propriedade **`serviceSelector.name`** do Serviço [de Operações de Mensagens do](messaging.md#messaging-operations-service)AEM Communities.

#### Guia Exibir {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostrar campo]** de assunto Se marcado, mostre a variável 
`Subject` e ativar a adição de um assunto à mensagem. O padrão não está marcado.

* **[!UICONTROL Rótulo do assunto]** Insira o texto a ser exibido ao lado da 
`Subject` campo. O padrão é `Subject`.

* **[!UICONTROL Mostrar campo]** Anexar arquivo Se marcada, mostre a variável 
`Attachment` e ativar a adição de anexos de arquivo à mensagem. O padrão não está marcado.

* **[!UICONTROL Anexar rótulo]** Digite o texto a ser exibido ao lado da 
`Attachment` campo. O padrão é **`Attach File`**.

* **[!UICONTROL Mostrar campo]** de conteúdo Se marcada, mostre a variável 
`Content` e ativar a adição de um corpo de mensagem. O padrão não está marcado.

* **[!UICONTROL Rótulo]** do conteúdoInsira o texto a ser exibido ao lado da 
`Content` campo. O padrão é **`Body`**.

* **[!UICONTROL Com o Editor]** de Rich Text Se marcada, indica o uso de uma caixa de texto Conteúdo personalizada com seu próprio editor de Rich Text. O padrão não está marcado.

* **[!UICONTROL Padrões]** de carimbo de data e hora Fornecem padrões de carimbo de data e hora para um ou mais idiomas. O padrão é en, de, fr, it, es, ja, zh_CN, ko_KR.

