---
title: Configuração da página de redirecionamento
seo-title: Configuração da página de redirecionamento
description: Depois de preencher um formulário adaptável, os usuários podem ser redirecionados para uma página da Web que os autores de formulários podem configurar ao criar o formulário.
seo-description: Depois de preencher um formulário adaptável, os usuários podem ser redirecionados para uma página da Web que os autores de formulários podem configurar ao criar o formulário.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Formulários adaptáveis
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Configuração da página de redirecionamento {#configuring-redirect-page}

Os autores de formulários podem configurar uma página para cada formulário, para a qual os usuários do formulário são redirecionados após enviar um formulário.

1. No modo de edição, selecione um componente, em seguida, clique em ![nível de campo](assets/field-level.png) > **Contêiner de formulário adaptável** e clique em ![cmppr](assets/cmppr.png).

1. Na barra lateral, clique em **Submission**.

1. Forneça o URL da página de redirecionamento em Página de agradecimento na seção Envio .
1. Como opção, em Enviar ação, para a ação Enviar para o ponto de extremidade REST, você pode configurar o parâmetro a ser transmitido à página de redirecionamento.

![Redirecionar ](assets/thank-you-setting-1.png)
**configuração da páginaFigura:** *Redirecionar configuração da página*

Os autores de formulários podem usar os seguintes parâmetros passados para a página de agradecimento. Para todas as ações de envio disponíveis, os parâmetros `status` e `owner` são passados. Além desses dois parâmetros, alguns parâmetros adicionais são passados para as seguintes ações de envio:

* **Armazenar ação de conteúdo**  (obsoleto) :  `contentPath`—o caminho do nó no repositório onde os dados enviados são armazenados é passado.

* **Armazenar ação de PDF**  (obsoleto) :  `contentPath`—dos dados enviados e do caminho para o nó que armazena o arquivo PDF no repositório — é transmitido.

* **Enviar para o fluxo de trabalho** do Forms: Os parâmetros de saída retornados do fluxo de trabalho de formulários são passados.

* **Enviar para o ponto de extremidade** REST: Os parâmetros adicionados para mapeamento de parâmetro no campo são passados. `status` e  `owner` os parâmetros não são passados nesta ação de envio. Para obter mais informações, consulte [Configuração da ação de envio do ponto de extremidade Submeter para REST](/help/forms/using/configuring-submit-actions.md).

