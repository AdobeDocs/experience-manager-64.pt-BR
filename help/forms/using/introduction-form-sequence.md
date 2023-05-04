---
title: Introdução à sequência de formulários em várias etapas
seo-title: Introduction to multi-step form sequence
description: Com o AEM Forms, é possível definir uma sequência de painéis de formulário na qual os usuários devem navegar e preencher um formulário adaptável.
seo-description: With AEM Forms, you can define a sequence of form panel in which you want users to navigate and fill an adaptive form.
uuid: b2b94e4c-0c28-47ba-8e23-fd8742baf71c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 4a51ebc4-e019-4fc5-93a1-d97f695126f5
feature: Adaptive Forms
exl-id: eec8bcbe-e2ba-42f1-98ea-08a4ca723e48
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 51%

---

# Introdução à sequência de formulários em várias etapas {#introduction-to-multi-step-form-sequence}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Formulários adaptáveis permitem que os autores de formulários criem uma experiência de captura de dados em várias etapas com grande facilidade. Eles possuem suporte integrado para criar vários painéis e associar cada painel a diferentes padrões de navegação. Os autores do formulário podem agrupar campos de formulário em seções lógicas e representar um grupo como um painel. A navegação geral entre painéis é controlada com o layout do painel. Os autores podem optar por organizar painéis em diferentes layouts, por exemplo, colocando sequencialmente usando o layout do Assistente ou de maneira ad hoc usando o layout de Tabelas. Para obter informações sobre layouts de painel, consulte [Recursos de layout de formulários adaptáveis](/help/forms/using/layout-capabilities-adaptive-forms.md).

Em uma experiência típica de preenchimento de formulário, há mais etapas envolvidas do que apenas capturar dados. Um envio de formulário completo pode incluir outras etapas, como a assinatura digital do formulário, a verificação das informações preenchidas no formulário, o processamento de pagamentos e assim por diante. Há diferenças de caso para caso.

Se o seu caso de uso determinar um conjunto de etapas para a captura de dados ou houver regulamentos que precisam de determinadas etapas a serem seguidas, a AEM Forms fornecerá uma maneira de aplicar essa estrutura comum em todos os formulários. A implementação premeditada da estrutura do formulário define a sequência de etapas de um formulário. ![Exemplo de uma sequência de formulário em várias etapas](assets/formpipeline.png)

Use um caso de uso em que é necessário criar uma sequência para preencher, verificar, assinar e confirmar as etapas de um formulário. As etapas para criar essa sequência são as seguintes:

1. Definir um modelo de formulário e adicionar a ele o painel requerido. Observe que deve haver um painel para cada etapa na sequência. No entanto, é possível incluir subpainéis dentro de um painel.

   Nesse exemplo, podemos adicionar os seguintes painéis:

   * **Preenchimento**: contém campos de formulários para capturar dados. Aqui, você pode incluir subpainéis aninhados para criar seções para diferentes tipos de informações, como pessoais, familiares, financeiras e assim por diante.
   * **Verificar**: Ele contém a variável **Verificar** componente que pode ser usado em um formulário adaptável baseado em XFA. Ele exibe as informações capturadas no painel Preenchimento no modo somente leitura para verificação.
   * **Assinatura eletrônica**: Ele contém a variável **Sign** componente que pode ser usado em um formulário adaptável baseado em XFA. ela fornece os seguintes serviços de assinatura:

      * Serviços de assinatura eletrônica da Adobe Document Cloud
      * Assinatura escrita
   * **Confirmação**: contém o componente **Resumo** que exibe uma mensagem confirmando o envio do formulário depois que um usuário o assina e atinge a etapa de Confirmação (Resumo) da sequência. Os autores podem configurar o texto do componente Resumo: mostrar uma mensagem de agradecimento, mostrar um link para o PDF gerado e assim por diante.


1. Selecione o layout do painel raiz como **[!UICONTROL Assistente]**.
1. Conclua as etapas restantes para criar o modelo de formulário. Para obter mais informações, consulte [Criação de um modelo de formulário adaptável personalizado](/help/forms/using/custom-adaptive-forms-templates.md).

Depois de definir a sequência de formulário no modelo de formulário, é possível usá-lo para criar formulários que terão a estrutura básica definida como a sequência em vigor, embora seja sempre possível personalizar o formulário para atender às suas necessidades.
