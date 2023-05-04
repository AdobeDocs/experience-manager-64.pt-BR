---
title: Configuração da página de redirecionamento
seo-title: Configuring redirect page
description: Depois de preencher um formulário adaptável, os usuários podem ser redirecionados para uma página da Web que os autores de formulários podem configurar ao criar o formulário.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# Configuração da página de redirecionamento {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os autores de formulários podem configurar uma página para cada formulário, para a qual os usuários do formulário são redirecionados após enviar um formulário.

1. No modo de edição, selecione um componente e clique em ![nível de campo](assets/field-level.png) > **Contêiner de formulário adaptável** e, em seguida, clique em ![cmppr](assets/cmppr.png).

1. Na barra lateral, clique em **Submissão**.

1. Forneça o URL da página de redirecionamento em Página de agradecimento na seção Envio .
1. Como opção, em Enviar ação, para a ação Enviar para o ponto de extremidade REST, você pode configurar o parâmetro a ser transmitido à página de redirecionamento.

![Redirecionar configuração da página](assets/thank-you-setting-1.png)
**Figura:** *Redirecionar configuração da página*

Os autores de formulários podem usar os seguintes parâmetros passados para a página de agradecimento. Para todas as ações de envio disponíveis, `status` e `owner` parâmetros são passados. Além desses dois parâmetros, alguns parâmetros adicionais são passados para as seguintes ações de envio:

* **Ação de armazenamento de conteúdo** (obsoleto) : `contentPath`—o caminho do nó no repositório onde os dados enviados são armazenados é passado.

* **PDF de armazenamento** (obsoleto) : `contentPath`—dos dados enviados e do caminho para o nó que armazena o arquivo de PDF no repositório — é transmitido.

* **Enviar para o fluxo de trabalho do Forms**: Os parâmetros de saída retornados do fluxo de trabalho de formulários são passados.

* **Enviar para ponto de extremidade REST**: Os parâmetros adicionados para mapeamento de parâmetro no campo são passados. `status` e `owner` parâmetros não são passados nesta ação de envio. Para obter mais informações, consulte [Configuração da ação Enviar para envio do ponto de extremidade REST](/help/forms/using/configuring-submit-actions.md).
