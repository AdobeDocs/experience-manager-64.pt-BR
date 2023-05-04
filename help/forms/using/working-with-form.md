---
title: Como trabalhar com um formulário
seo-title: Working with a Form
description: Exibir e atualizar o formulário associado a uma tarefa ou ponto de partida no aplicativo AEM Forms
seo-description: View and update the form associated with a task or Startpoint in the AEM Forms app
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
exl-id: ae565dbd-2631-4364-89f7-675700b43320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 2%

---

# Como trabalhar com um formulário {#working-with-a-form}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Se um formulário estiver habilitado para sincronização no aplicativo forms, ele será baixado e você poderá trabalhar diretamente com ele.

Os formulários são baixados no aplicativo e estão disponíveis offline. Por exemplo, você está executando uma empresa bancária e um cliente preenche um aplicativo em seu site. O aplicativo é um formulário adaptável que aceita informações de seus clientes e as armazena para revisão. O administrador revisa o formulário e cria um formulário de verificação AEM instância do autor. O administrador habilita a sincronização do formulário com o aplicativo AEM Forms. Se o formulário de verificação estiver disponível no aplicativo AEM Forms, o agente de campo poderá usar um dispositivo móvel para verificar os detalhes do cliente. O dispositivo móvel é sincronizado com o servidor e o formulário de verificação é carregado no aplicativo. Seu agente de campo pode visitar seu cliente, verificar os detalhes, salvar dados como rascunho ou enviar o formulário de verificação. O formulário é sincronizado com o servidor sempre que seu aplicativo está online.

Para sincronizar o formulário no aplicativo AEM Forms:

1. Na instância do autor, selecione um formulário e clique em **Propriedades da exibição**.

1. Na página de propriedades, clique em **Avançado.**
1. Em Avançado, habilite a opção : **Sincronizar com o aplicativo AEM Forms** e toque em **Salvar**.

Para sincronizar vários formulários, na instância de autor, selecione vários formulários no Gerenciador de formulários e toque em **Sincronizar com o aplicativo AEM Forms**. Quando o formulário é publicado, o aplicativo AEM Forms pode se conectar ao servidor de publicação e buscar os formulários.

>[!NOTE]
>
>Formulários compatíveis:
>
>* Formulários adaptáveis (sem carregamento lento)
>* Formulários móveis
>
>Os anexos no nível do formulário não são suportados nos formulários adaptáveis buscados no aplicativo AEM Forms sincronizado com o servidor OSGi da AEM Forms. Os usuários podem anexar arquivos em um campo, se o autor tiver ativado anexos em nível de campo no momento da criação do formulário.

**Para abrir e atualizar um formulário**

1. Para abrir um formulário, toque no formulário na tela inicial.
1. É possível atualizar os campos do formulário, adicionar anexos, salvar como rascunho e enviá-lo.
