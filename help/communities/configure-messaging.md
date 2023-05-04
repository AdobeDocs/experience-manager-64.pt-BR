---
title: Recurso Mensagens
seo-title: Messaging Feature
description: Configuração de componentes de mensagens
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 1%

---

# Recurso Mensagens {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Além das interações publicamente visíveis que ocorrem em fóruns e comentários, o recurso de mensagens do AEM Communities permite que membros da comunidade interajam mais privadamente.

Esse recurso pode ser incluído quando uma [site da comunidade](overview.md#communitiessites) é criada.

Os recursos de mensagens oferecem a capacidade de:

* Enviar uma mensagem para um ou mais membros da comunidade
* Enviar uma mensagem para um grupo de membros da comunidade
* Enviar uma mensagem com anexos
* Encaminhar uma mensagem
* Responder a uma mensagem
* Excluir uma mensagem
* Restaurar uma mensagem excluída

Para ativar e modificar o recurso de mensagens, visite

* [Configuração de mensagens](messaging.md) para administradores
* [Fundamentos das mensagens](essentials-messaging.md) para desenvolvedores

>[!NOTE]
>
>Não há suporte para adicionar `Compose Message, Message, or Message List` componentes (encontrados em `Communities`grupo de componentes) para uma página no modo de edição do autor.

## Configuração de componentes de mensagens {#configuring-messaging-components}

Quando as mensagens são ativadas para um site da comunidade, elas são completamente configuradas, sem necessidade de configuração adicional. Essas informações são fornecidas se houver a necessidade de alterar a configuração padrão.

### Configuração da lista de mensagens (mensagem) {#configuring-message-list-messagebox}

Para modificar a configuração da lista de mensagens para **Caixa de entrada**, **Itens enviados** e **Lixeira** páginas do recurso de mensagens, abra o site em [modo de edição do autor](sites-console.md#authoring-site-content).

Em `Preview` selecione o **[!UICONTROL Mensagens]** para abrir a página principal de mensagens. Em seguida, selecione **[!UICONTROL Caixa de entrada, itens enviados ou lixeira]** para configurar o componente para a lista de mensagens.

Em `Edit` , selecione o componente na página.

Para acessar a caixa de diálogo de configuração, é necessário cancelar a herança selecionando o `link`ícone .

Quando a configuração for concluída, é necessário restaurar a herança selecionando a variável `broken link` ícone .

![chlimage_1-396](assets/chlimage_1-396.png)

Após cancelar a herança, será possível selecionar a variável `configure` para abrir a caixa de diálogo de configuração.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Guia Básico {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Seletor de serviço]**
(*Obrigatório*) Defina isso como o valor da propriedade `serviceSelector.name` do [Serviço de operações de mensagens da AEM Communities](messaging.md#messaging-operations-service).

* **[!UICONTROL Compor página]**
(*Obrigatório*) A página a ser aberta quando um membro clicar no `Reply` botão. A página de destino deve conter a variável **[!UICONTROL Escrever mensagem]** formulário.

* **[!UICONTROL Responder/Exibir como Recurso]**
Se marcada, o URL de resposta e o URL de exibição farão referência a um recurso, caso contrário, os dados serão passados como parâmetros de consulta no URL.

* **[!UICONTROL Formulário de exibição de perfil]**
O formulário de perfil a ser usado para exibir o perfil de remetentes.

* **[!UICONTROL Pasta Lixeira]**
Se marcada, esse componente Lista de mensagens exibe apenas mensagens sinalizadas como excluídas (lixeira).

* **[!UICONTROL Caminhos de pasta]**
(*Obrigatório*) Fazendo referência aos valores definidos para `inbox.path.name` e `sentitems.path.name` no [Serviço de operações de mensagens da AEM Communities](messaging.md#messaging-operations-service). Ao configurar para um `Inbox`, adicione uma entrada usando o valor de `inbox.path.name`. Ao configurar para um `Outbox`, adicione uma entrada usando o valor de `sentitems.path.name`. Ao configurar para `Trash`, adicione duas entradas com ambos os valores.

#### Guia Exibir {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Botão Marcar Leitura]**
Se marcada, exibe uma 
`Read`que permite que uma mensagem seja marcada como lida.

* **[!UICONTROL Botão Marcar Não Lido]**
Se marcada, exibe uma 
`Mark Unread` que permite que uma mensagem seja marcada como lida.

* **[!UICONTROL Botão Excluir]**
Se marcada, exibe uma 
`Delete`que permite que uma mensagem seja marcada como lida. Duplicará a funcionalidade de exclusão se **`Message Options`** também está marcada.

* **[!UICONTROL Opções de mensagem]**
Se marcada, será exibida 
**`Reply`**, **`Reply All`**, **`Forward`** e **`Delete`** botões que permitem reenviar ou excluir uma mensagem. Duplicará a funcionalidade de exclusão se **`Delete Button`** também está marcada.

* **[!UICONTROL Mensagens por página]**
O número especificado é o número máximo de mensagens exibidas por página em um esquema de paginação. Se nenhum número for especificado (deixado em branco), todas as mensagens serão exibidas e não haverá paginação.

* **[!UICONTROL Padrões de carimbo de data e hora]**
Forneça padrões de carimbo de data e hora para um ou mais idiomas. O padrão é en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Exibir usuário]**
Escolha um 
**`Sender`** ou **`Recipients`** para determinar se o Remetente ou o Recipients deve ser exibido.

### Configuração da mensagem de composição {#configuring-compose-message}

Para modificar a configuração da página de mensagens de composição, abra o site em [modo de edição do autor](sites-console.md#authoring-site-content).

Em `Preview`selecione o **[!UICONTROL Mensagens]** para abrir a página principal de mensagens. Em seguida, selecione o botão New Message para abrir o `Compose Message` página..

Em `Edit` , selecione o componente principal na página que contém o corpo da mensagem.

Para acessar a caixa de diálogo de configuração, é necessário cancelar a herança selecionando o `link`ícone .

Quando a configuração for concluída, é necessário restaurar a herança selecionando a variável `broken link` ícone .

![chlimage_1-400](assets/chlimage_1-400.png)

Após cancelar a herança, será possível selecionar a variável `configure` para abrir a caixa de diálogo de configuração.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Guia Básico {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL Redirecionar URL]**
Insira o URL da página mostrada depois que a mensagem é enviada. Por exemplo, 
`../messaging.html`.

* **[!UICONTROL Cancelar URL]**
Insira o URL da página mostrada se o remetente cancelar a mensagem. Por exemplo, 
`../messaging.html`.

* **[!UICONTROL Comprimento máximo do assunto da mensagem]**
O número máximo de caracteres permitidos no campo Assunto. Por exemplo, 500. O padrão não é limite.

* **[!UICONTROL Comprimento máximo do corpo da mensagem]**
O número máximo de caracteres permitidos no campo Conteúdo. Por exemplo, 10000. O padrão não é limite.

* **[!UICONTROL Seletor de serviço]**
(*Obrigatório*) Defina isso como o valor da propriedade **`serviceSelector.name`** do [Serviço de operações de mensagens da AEM Communities](messaging.md#messaging-operations-service).

#### Guia Exibir {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostrar campo de assunto]**
Se marcada, mostre a variável 
`Subject` e ativar a adição de um assunto à mensagem. O padrão não está marcado.

* **[!UICONTROL Rótulo do Assunto]**
Insira o texto a ser exibido ao lado do 
`Subject` campo. O padrão é `Subject`.

* **[!UICONTROL Mostrar campo Anexar arquivo]**
Se marcada, mostre a variável 
`Attachment` e habilite a adição de anexos de arquivo à mensagem. O padrão não está marcado.

* **[!UICONTROL Anexar Rótulo do Arquivo]**
Insira o texto a ser exibido ao lado do 
`Attachment` campo. O padrão é **`Attach File`**.

* **[!UICONTROL Mostrar campo de conteúdo]**
Se marcada, mostre a variável 
`Content` e habilite a adição de um corpo de mensagem. O padrão não está marcado.

* **[!UICONTROL Rótulo de conteúdo]**
Insira o texto a ser exibido ao lado do 
`Content` campo. O padrão é **`Body`**.

* **[!UICONTROL Com o Editor de Rich Text]**
Se marcada, indica o uso de uma caixa de texto Conteúdo personalizada com seu próprio editor de rich text. O padrão não está marcado.

* **[!UICONTROL Padrões de carimbo de data e hora]**
Forneça padrões de carimbo de data e hora para um ou mais idiomas. O padrão é en, de, fr, it, es, ja, zh_CN, ko_KR.
