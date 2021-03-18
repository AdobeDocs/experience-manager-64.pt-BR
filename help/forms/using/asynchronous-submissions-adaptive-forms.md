---
title: Envio assíncrono de formulários adaptáveis
seo-title: Envio assíncrono de formulários adaptáveis
description: Saiba como configurar o envio assíncrono para formulários adaptáveis.
seo-description: Saiba como configurar o envio assíncrono para formulários adaptáveis.
uuid: 3b8aeac8-cb38-4a2b-8375-556b2736d58b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 6e4e3af5-4260-4f38-9b29-0818e92bc182
feature: Formulários adaptáveis
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---


# Envio assíncrono de formulários adaptáveis {#asynchronous-submission-of-adaptive-forms}

Tradicionalmente, os formulários web são configurados para envio síncrono. Quando os usuários enviam um formulário, ele é redirecionado para uma página de confirmação ou, em caso de falha no envio, para uma página de erro. No entanto, experiências modernas da Web, como aplicativos de página única, estão ganhando popularidade, onde a página da Web permanece estática, enquanto a interação cliente-servidor acontece em segundo plano. Agora você pode fornecer essa experiência com formulários adaptáveis configurando o envio assíncrono. Nesse caso, um formulário adaptável se comporta como um aplicativo de página única, pois o formulário não é recarregado ou sua URL não é alterada quando os dados do formulário enviados são validados no servidor.

Leia para obter detalhes sobre o envio assíncrono em formulários adaptáveis.

## Configurar envio assíncrono {#configure}

Para configurar o envio assíncrono para um formulário adaptável:

1. No modo de criação de formulário adaptável, selecione o objeto Contêiner de formulário e toque em ![cmppr1](assets/cmppr1.png) para abrir suas propriedades.
1. Na seção **[!UICONTROL Submission]** properties , habilite **[!UICONTROL Use asynchronous submit]**.
1. Na seção **[!UICONTROL Ao enviar]**, selecione uma das seguintes opções para executar no envio bem-sucedido do formulário.

   * **[!UICONTROL Redirecionar para URL]**: Redireciona para o URL ou página especificada no envio do formulário. Você pode especificar um URL ou navegar para escolher o caminho para uma página no campo **[!UICONTROL Redirect URL/Path]**.
   * **[!UICONTROL Mostrar mensagem]**: Exibe uma mensagem no envio do formulário. Você pode escrever uma mensagem no campo de texto abaixo da opção Mostrar mensagem. O campo de texto oferece suporte à formatação Rich Text.

1. Toque em ![check-button1](assets/check-button1.png) para salvar as propriedades.

## Como o envio assíncrono funciona {#how-asynchronous-submission-works}

O AEM Forms fornece manipuladores de erros e sucesso prontos para uso para envios de formulários. Os manipuladores são funções do lado do cliente que são executadas com base na resposta do servidor. Quando um formulário é enviado, os dados são transmitidos ao servidor para validação, o que retorna uma resposta ao cliente com informações sobre o sucesso ou o evento de erro do envio. As informações são passadas como parâmetros para o manipulador relevante para executar a função.

Além disso, autores e desenvolvedores de formulários podem gravar regras no nível de formulário para substituir manipuladores padrão. Para obter mais informações, consulte [Substituir manipuladores padrão usando regras](#custom).

Vamos primeiro analisar a resposta do servidor em busca de eventos bem-sucedidos e de erros.

### Resposta do servidor para evento bem-sucedido de envio {#server-response-for-submission-success-event}

A estrutura para a resposta do servidor para o evento bem-sucedido de envio é a seguinte:

```
{
  contentType : "<xmlschema or jsonschema>", 
  data : "<dataXML or dataJson>" , 
  thankYouOption : <page/message>, 
  thankYouContent : "<thank you page url/thank you message>"
}
```

A resposta do servidor em caso de envio de formulário bem-sucedido inclui:

* Tipo de formato de dados do formulário: XML ou JSON
* Dados do formulário no formato XML ou JSON
* Opção selecionada para redirecionar para uma página ou exibir uma mensagem conforme configurado no formulário
* URL da página ou conteúdo da mensagem, conforme configurado no formulário

O manipulador de sucesso lê a resposta do servidor e, de acordo, redireciona para o URL da página configurada ou exibe uma mensagem.

### Resposta do servidor para evento de erro de envio {#server-response-for-submission-error-event}

A estrutura para a resposta do servidor para o evento de erro de envio é a seguinte:

```
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

A resposta do servidor em caso de erro no envio do formulário inclui:

* Motivo do erro, CAPTCHA com falha ou validação do lado do servidor
* Lista de objetos de erro, que inclui a expressão SOM do campo que falhou na validação e a mensagem de erro correspondente

O manipulador de erros lê a resposta do servidor e, portanto, exibe a mensagem de erro no formulário.

## Substituir manipuladores padrão usando regras {#custom}

Desenvolvedores e autores de formulários podem gravar regras, no nível de formulário, no editor de códigos para substituir manipuladores padrão. A resposta do servidor para eventos bem-sucedidos e de erro é exposta no nível do formulário, que os desenvolvedores podem acessar usando `$event.data` nas regras.

Execute as etapas a seguir para gravar regras no editor de códigos para lidar com eventos bem-sucedidos e de erro.

1. Abra o formulário adaptável no modo de criação, selecione qualquer objeto de formulário e toque em ![edit-rules1](assets/edit-rules1.png) para abrir o editor de regras.
1. Selecione **[!UICONTROL Formulário]** na árvore Objetos de formulário e toque em **[!UICONTROL Criar]**.
1. Selecione **[!UICONTROL Editor de código]** no menu suspenso de seleção de modo.
1. No editor de código, toque em **[!UICONTROL Editar código]**. Toque em **[!UICONTROL Editar]** na caixa de diálogo de confirmação.
1. Escolha **[!UICONTROL Envio bem-sucedido]** ou **[!UICONTROL Erro no Envio]** no menu suspenso **[!UICONTROL Evento]**.
1. Escreva uma regra para o evento selecionado e toque em **[!UICONTROL Concluído]** para salvar a regra.

