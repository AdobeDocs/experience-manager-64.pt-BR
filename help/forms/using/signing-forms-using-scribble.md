---
title: Aplicar assinaturas eletrônicas a um formulário usando assinaturas do scribble
seo-title: Apply electronic signatures to a form using scribble signatures
description: Assinar formulários usando o scribble
seo-description: Signing forms using scribble
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
exl-id: a870c4b7-4040-4bd8-b477-286ebe6a4b01
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---

# Aplicar assinaturas eletrônicas a um formulário usando assinaturas do scribble {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode usar o **Assinatura do Scribble** componente e **Etapa de assinatura** componente para desenhar (Scribble) assinatura em um formulário adaptável. O componente Etapa de assinatura exibe uma versão PDF do formulário adaptável. É necessário ativar uma opção Documento de registro ou formulários adaptáveis baseados em modelo de formulário para usar o componente Etapa de assinatura.

Ambos os componentes fornecem uma janela, conforme exibido abaixo, para assinar um formulário. Você também pode clicar no ícone de geolocalização ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) para adicionar geolocalização à assinatura.

![Caixa de diálogo de sinal de rabisco](assets/scribble-signature.png)

## Configurar um formulário adaptável para usar a Assinatura do Scribble {#configure-an-adaptive-form-to-use-scribble-signature}

1. Crie uma opção Documento de registro ativada ou um formulário adaptável baseado em modelo de formulário. Para obter informações passo a passo, consulte [Criação de um formulário adaptável](/help/forms/using/creating-adaptive-form.md).
1. Arraste e solte a **Assinatura do Scribble** componente do navegador de componentes para o formulário adaptável.
1. Toque no **Configurar** ![configure](assets/configure.png) ícone . Ele abre o navegador de propriedades e exibe as propriedades do componente Assinatura do rabisco. Configure as propriedades do componente Assinatura do Scribble.
1. Arraste e solte o componente Etapa de assinatura do navegador de componentes para o formulário adaptável.

   >[!NOTE]
   >
   >O componente Etapa de assinatura ocupa a largura total disponível para o formulário. É recomendável não ter nenhum outro componente na seção que contenha o componente Etapa de assinatura.

1. No navegador Conteúdo, toque em **Contêiner de formulário** e toque no **Configurar** ![configure](assets/configure.png) ícone . Ele abre o navegador de propriedades e exibe as propriedades do contêiner do Formulário adaptável. Navegar para **Contêiner de formulário adaptável** > **Assinatura eletrônica** e desmarque a opção **Ativar o Acrobat Sign** opção. Toque em Concluído ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para salvar as alterações.

   >[!NOTE]
   >
   >Quando você adiciona um componente Etapa de assinatura a um formulário adaptável, a opção Habilitar Acrobat Sign é selecionada automaticamente.

1. Toque no **Configurar** ![configure](assets/configure.png) ícone . Ele abre o navegador de propriedades e exibe as propriedades da etapa Assinatura. Configure as seguintes propriedades:

   * **Nome do elemento**: Especifique o nome do componente.
   * **Título:** Especifique o título exclusivo do componente.
   * **Mensagem do modelo:** Especifique a mensagem a ser exibida enquanto o PDF de assinatura está sendo carregado. Os serviços da Acrobat Sign levam algum tempo para preparar e carregar o PDF de assinatura.
   * **Serviço de assinatura:** Selecione o **Assinatura do Scribble** opção.
   * **Classe CSS**: Especifique a classe CSS da biblioteca do cliente, se houver. Recomenda-se a utilização de [temas](/help/forms/using/themes.md) e [estilos em linha](/help/forms/using/inline-style-adaptive-forms.md) em vez de Classe CSS.

   Toque em Concluído ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para salvar as alterações. A Assinatura é configurada com êxito.

   Agora, ao preencher um formulário, é exibida uma versão PDF do formulário adaptável e são fornecidas opções para assinar o documento PDF. Para obter informações detalhadas, consulte [Assinar um formulário adaptável usando a Assinatura do Scribble](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## Assinar um formulário adaptável usando a Assinatura do Scribble {#sign-an-adaptive-form-using-scribble-signature}

1. Depois de preencher um formulário adaptável e chegar à página Etapa de assinatura, a tela de assinatura é exibida.

   ![Tela de assinatura para a página do EchoSign](assets/esignscribblesign.jpg)

1. Clique em **[!UICONTROL Sign]**. A caixa de diálogo de sinal de rabisco é exibida. Assine o formulário e clique em Concluído ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) para salvar a assinatura.

   ![Caixa de diálogo de sinal de rabisco](assets/scribblewidget.jpg)

1. Clique em concluir para concluir o processo de assinatura.

   ![Concluir o processo de assinatura](assets/scribblecomplete.jpg)

As assinaturas são adicionadas ao formulário e o controle do formulário é movido para o próximo painel.
