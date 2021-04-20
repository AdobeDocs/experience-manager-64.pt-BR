---
title: Criação de um formulário adaptável
seo-title: Criação de um formulário adaptável
description: Como criar um formulário adaptável usando o AEM Forms. Os formulários adaptáveis são formulários HTML5 responsivos que simplificam a coleta e o processamento de informações.
seo-description: Como criar um formulário adaptável usando o AEM Forms. Os formulários adaptáveis são formulários HTML5 responsivos que simplificam a coleta e o processamento de informações.
uuid: 444f461a-9e88-4385-b5ee-e985067ab7bc
content-type: reference
topic-tags: author
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f06b8cb2-6f98-465f-beec-1e91e3f45707
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2044'
ht-degree: 0%

---


# Criação de um formulário adaptável {#creating-an-adaptive-form}

## <strong>Criar um formulário adaptável</strong> {#strong-create-an-adaptive-form-strong}

Siga estas etapas para criar um formulário adaptável.

1. Acesse a instância do autor do AEM Forms em `https://[server]:[port]/<custom-context-if-any>.`

   ```
   
   ```

1. Insira suas credenciais na página de logon AEM.

   Depois de fazer logon, no canto superior esquerdo, toque em **[!UICONTROL Adobe Experience Manager > Forms > Forms &amp; Documents]**.

   >[!NOTE]
   >
   >Para uma instalação padrão, o logon é `admin` e a senha é `admin`.

1. Toque em **[!UICONTROL Criar]** e selecione **[!UICONTROL Formulário adaptável]**.
1. Uma opção para selecionar um modelo é exibida. Para obter mais informações sobre modelos, consulte [Adaptive form templates](/help/forms/using/creating-adaptive-form.md#p-adaptive-form-templates-p). Toque em um modelo para selecioná-lo e toque em Próximo.
1. Uma opção para &quot;Adicionar propriedades&quot; é exibida. Especifique os valores para os seguintes campos de propriedade. Os campos Título e Nome são obrigatórios:

   * **[!UICONTROL Título:]** Especifica o nome de exibição do formulário. O título ajuda a identificar o formulário na interface do usuário do AEM Forms.
   * **[!UICONTROL Nome:]** Especifica o nome do formulário. Um nó com o nome especificado é criado no repositório. À medida que você começa a digitar um título, o valor do campo de nome é gerado automaticamente. Você pode alterar o valor sugerido. O campo de nome pode incluir somente caracteres alfanuméricos, hifens e sublinhados. Todas as entradas inválidas são substituídas por um hífen.
   * **[!UICONTROL Descrição:]** Especifica as informações detalhadas sobre o formulário.
   * **[!UICONTROL Tags:]** Especifica tags para identificar exclusivamente o formulário adaptável. As tags ajudam a pesquisar o formulário. Para criar tags, digite novos nomes de tag na caixa **Tags**.

1. Você pode criar um formulário adaptável com base em um dos seguintes modelos de formulário:

   * [Modelo de dados do formulário](#fdm)
   * [Modelo de formulário XFA](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)
   * [Esquema XML ou JSON](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)
   * Nenhum ou sem qualquer modelo de formulário

   Você pode configurá-los na guia **[!UICONTROL Modelo de formulário]** na página **[!UICONTROL Adicionar propriedades]**. Por padrão, o modelo de formulário selecionado é **[!UICONTROL None]**.

1. Toque em **Criar**. Um formulário adaptável é criado, e uma caixa de diálogo para abrir o formulário para edição é exibida.

   Quando terminar de especificar todas as propriedades, clique em **[!UICONTROL Criar]**. Um formulário adaptável é criado, e uma caixa de diálogo para abrir o formulário para edição é exibida.

   Quando terminar de especificar todas as propriedades, clique em **[!UICONTROL Criar]**. Um formulário adaptável é criado, e uma caixa de diálogo para abrir o formulário para edição é exibida.

1. Toque em **[!UICONTROL Abrir]** para abrir o formulário recém-criado em uma nova guia. O formulário é aberto para edição e exibe o conteúdo disponível no modelo. Também exibe a barra lateral para personalizar o formulário recém-criado de acordo com as necessidades.

   Com base no tipo de formulário adaptável, os elementos de formulário presentes no modelo de formulário XFA, esquema XML ou esquema JSON associados são exibidos na guia **[!UICONTROL Objetos de Modelo de Dados]** do **[!UICONTROL Navegador de Conteúdo]** na barra lateral. Também é possível arrastar e soltar esses elementos para criar seu formulário adaptável.

   Para obter informações sobre a interface de criação de formulários adaptáveis e os componentes disponíveis, consulte [Introdução à criação de formulários adaptáveis](/help/forms/using/introduction-forms-authoring.md).

   >[!NOTE]
   >
   >Permita que janelas pop-up no navegador abram o formulário recém-criado em uma nova guia.

## Criar um formulário adaptável com base em um modelo de dados de formulário {#fdm}

[A ](/help/forms/using/data-integration.md) integração de dados do AEM Forms permite integrar várias fontes de dados e unir suas entidades e serviços para criar um modelo de dados de formulário. É uma extensão do esquema JSON. É possível usar um modelo de dados de formulário para criar um formulário adaptável. As entidades ou objetos de modelo de dados configurados em um modelo de dados de formulário estão disponíveis como objetos de modelo de dados para a criação de formulário. Eles são vinculados às respectivas fontes de dados e usados para preencher previamente um formulário e gravar os dados enviados de volta nas respectivas fontes de dados. Também é possível chamar os serviços configurados em um modelo de dados de formulário usando regras de formulário adaptáveis.

Para usar um modelo de dados de formulário para criar um formulário adaptável:

1. Na guia Modelo de formulário na tela Adicionar propriedades, selecione **[!UICONTROL Modelo de dados de formulário]** na lista suspensa **[!UICONTROL Selecionar de]**.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Toque para expandir **[!UICONTROL Selecionar Modelo de Dados de Formulário]**. Todos os modelos de dados de formulário disponíveis são listados.

   Selecione um do modelo de dados.

   ![create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>Também é possível alterar o modelo de dados de formulário para um formulário adaptável. Para etapas detalhadas, consulte [Editar propriedades do Modelo de formulário de um formulário adaptável](#edit-form-model).

## Criar um formulário adaptável com base em um modelo de formulário XFA {#create-an-adaptive-form-based-on-an-xfa-form-template}

Você pode redefinir o objetivo dos modelos de formulário XFA para criar formulários adaptáveis. Para redefinir a finalidade, carregue e associe um modelo de formulário XFA a um formulário adaptável. Os elementos do modelo de formulário (formulário XFA) são disponibilizados para uso no localizador de conteúdo no momento da criação do formulário adaptável. No Localizador de conteúdo, é possível arrastar e soltar os elementos do modelo de formulário no formulário.

>[!NOTE]
>
>[Faça upload do ](/help/forms/using/get-xdp-pdf-documents-aem.md) modelo de formulário XFA para o AEM Forms antes de começar a criar um formulário adaptável com base no modelo de formulário.

Faça o seguinte para usar um modelo de formulário XFA como modelo de formulário para seu formulário adaptável:

1. Na página **[!UICONTROL Adicionar propriedades]**, abra a guia **[!UICONTROL Modelo de formulário]**.
1. Na guia Modelo de formulário , na lista suspensa, selecione **[!UICONTROL Modelos de formulário]**. Todos os modelos de formulário que são carregados no repositório por meio da interface do usuário do AEM Forms são listados para seleção. Selecione um modelo na lista.

   ![Associar modelo de formulário XFA a um formulário adaptável](assets/form_model_xfa_associate.png)
   **Figura:** *Seleção de um modelo de formulário*

   >[!NOTE]
   >
   >Também é possível alterar o modelo de formulário para um formulário adaptável. Para etapas detalhadas, consulte [Editar propriedades do Modelo de formulário de um formulário adaptável](#edit-form-model).

## Criar um formulário adaptável com base no esquema XML ou JSON {#create-an-adaptive-form-based-on-xml-or-json-schema}

Os esquemas XML e JSON representam a estrutura na qual os dados são produzidos ou consumidos pelo sistema de back-end na organização. Você pode associar um esquema a um formulário adaptável e usar seus elementos para adicionar conteúdo dinâmico ao formulário adaptável. Os elementos do esquema estão disponíveis na guia Objeto do modelo de dados do navegador de conteúdo para a criação de formulários adaptáveis. Você pode arrastar e soltar os elementos do esquema para criar o formulário.

Consulte os seguintes documentos para entender como projetar um esquema XML ou JSON para a criação de formulários adaptáveis.

* [Criação de formulários adaptáveis usando o esquema XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Criação de formulários adaptáveis usando o esquema JSON](/help/forms/using/adaptive-form-json-schema-form-model.md)

Faça o seguinte para usar o esquema XML ou JSON como modelo de formulário para um formulário adaptável:

1. Na etapa **[!UICONTROL Adicionar propriedades]** da página de criação de formulário adaptável, toque na guia **[!UICONTROL Modelo de formulário]**.
1. Na guia Modelo de formulário, selecione **[!UICONTROL Esquema]** no campo suspenso **[!UICONTROL Selecionar de]**.

1. Toque em **[!UICONTROL Selecionar Esquema]** e siga um destes procedimentos:

   * **[!UICONTROL Fazer upload do disco]**  - Selecione esta opção e toque em Fazer upload da definição de esquema para procurar e fazer upload de um esquema XML ou JSON do seu sistema de arquivos. O arquivo de esquema carregado reside no formulário e não está acessível a outros formulários adaptáveis.
   * **[!UICONTROL Pesquisar no repositório]**  - Selecione esta opção para selecionar na lista de arquivos de definição de esquema disponíveis no repositório. Selecione o arquivo de esquema XML ou JSON como modelo de formulário. O schema selecionado será associado ao formulário por referência e estará acessível para uso em outros formulários adaptáveis.

   >[!CAUTION]
   >
   >Certifique-se de que o nome de arquivo do esquema JSON termine com **.schema.json**. Por exemplo: mySchema.schema.json

   ![Seleção do esquema XML ou JSON](assets/upload-schema.png)
   **Figura:** *Seleção do esquema XML ou JSON*

1. (Somente para esquema XML) Após selecionar ou carregar um esquema XML, especifique um elemento raiz do arquivo XSD selecionado a ser mapeado com o formulário adaptável.

   ![Selecionar elemento raiz XSD](assets/xsd-root-element.png)
   **Figura:** *Seleção do elemento raiz XSD*

>[!NOTE]
>
>Também é possível alterar o schema de um formulário adaptável. Para etapas detalhadas, consulte [Editar propriedades do Modelo de formulário de um formulário adaptável](#edit-form-model).

## Modelos de formulário adaptável {#adaptive-form-templates}

Um modelo fornece uma estrutura básica e define a aparência (layouts e estilos) de um formulário adaptável. Ele tem componentes pré-formatados contendo determinadas propriedades e estrutura de conteúdo. Pronto para uso, o AEM Forms fornece alguns modelos de formulário adaptáveis. Para obter o pacote de modelo completo, incluindo modelos avançados, é necessário instalar o pacote complementar do AEM Forms. Para obter mais informações, consulte [Instalação do pacote complementar do AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).

Além disso, você pode usar o editor de modelos para criar seus próprios modelos. Para obter mais informações sobre como trabalhar com modelos, consulte [Adaptive form templates](/help/forms/using/template-editor.md).

>[!NOTE]
>
>Ao abrir um formulário adaptável criado usando o modelo avançado para edição, uma mensagem de erro é exibida. O modelo avançado tem um componente Etapa de assinatura e o Adobe Sign é ativado para ele por padrão. Crie e selecione uma [Configuração da nuvem Adobe Sign](/help/forms/using/adobe-sign-integration-adaptive-forms.md) e [configure um assinante](/help/forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) para resolver o erro.

## Editar as propriedades do Modelo de formulário de um formulário adaptável {#edit-form-model}

Os formulários adaptáveis são criados sem um modelo de formulário (usando a opção Nenhum para o modelo de formulário) ou usando um modelo de formulário, como um modelo de formulário, esquema XML ou esquema JSON, ou modelo de dados de formulário. É possível alterar o modelo de formulário para um formulário adaptável de Nenhum para outro modelo de formulário. Para formulários adaptáveis baseados em um modelo de formulário, é possível escolher outro modelo de formulário, esquema XML, esquema JSON ou modelo de dados de formulário para o mesmo modelo de formulário. No entanto, não é possível alterar de um modelo de formulário para outro.

1. Selecione o formulário adaptável e toque no ícone **Propriedades**.
1. Abra a guia **[!UICONTROL Modelo de formulário]** e faça o seguinte:

   * Se o formulário adaptável não tiver um modelo de formulário, é possível escolher outro modelo de formulário e, consequentemente, selecionar um modelo de formulário, esquema XML ou JSON ou modelo de dados de formulário.
   * Se o formulário adaptável for baseado em um modelo de formulário, você poderá escolher outro modelo de formulário, esquema XML ou JSON ou modelo de dados de formulário para o mesmo modelo de formulário.

1. Toque em **[!UICONTROL Salvar]** para salvar as propriedades.

## Salvar automaticamente um formulário adaptável {#auto-save-an-adaptive-form}

Por padrão, o conteúdo de um formulário adaptável é salvo em uma ação do usuário, como ao pressionar o botão Salvar. Você também pode configurar um formulário adaptável para começar a salvar automaticamente o conteúdo com base em um evento ou intervalo de tempo. A opção de salvar automaticamente é útil em:

* Salvar automaticamente o conteúdo para usuários anônimos e conectados
* Salvar o conteúdo de um formulário sem a intervenção mínima do usuário
* Comece a salvar o conteúdo de um formulário com base em um evento de usuário
* Salvar o conteúdo de um formulário repetidamente após um intervalo de tempo especificado

### Ativar Salvar automaticamente para um formulário adaptável {#enable-auto-save-for-an-adaptive-form}

Por padrão, a opção de salvar automaticamente não está ativada. Você pode ativar a opção de salvamento automático na guia Salvar automaticamente de um formulário adaptável. A guia Salvar automaticamente também fornece várias outras opções de configuração. Execute as seguintes etapas para habilitar e configurar a opção de salvamento automático para um formulário adaptável:

1. Para acessar a seção de salvamento automático nas propriedades, selecione um componente, em seguida, toque em ![field-level](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]** e toque em ![cmppr](assets/cmppr.png).
1. Na seção **[!UICONTROL Salvar automaticamente]**, **[!UICONTROL Ativar]** a opção de salvar automaticamente.
1. Na caixa **[!UICONTROL Adaptive Form Event]**, especifique 1 ou TRUE para começar a salvar automaticamente o formulário quando o formulário for carregado no navegador. Também é possível especificar uma expressão condicional para um evento, que, quando acionada e retorna true, começa a salvar o conteúdo do formulário.
1. Especifique o Acionador. O salvamento automático é acionado com base em sua configuração. Suas opções são:

   * **[!UICONTROL Baseado em tempo:]** selecione a opção para começar a salvar o conteúdo com base em um intervalo de tempo específico.
   * **[!UICONTROL Baseado em evento:]** selecione a opção para começar a salvar o conteúdo com base em quando um evento é acionado.

   Quando você seleciona um acionador, a caixa Configuração de estratégia é ativada. A caixa Configuração de estratégia permite:

   * Especifique um intervalo de tempo se você selecionar o acionador **[!UICONTROL Time based]**.
   * Especifique um nome de evento se você selecionar o acionador **[!UICONTROL Event based]**.

   Você também pode criar e adicionar sua própria estratégia personalizada à lista. Para obter detalhes, consulte [Implementar uma estratégia personalizada para salvar automaticamente os formulários](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Somente salvamento automático com base em tempo) Execute as seguintes etapas para configurar opções para o salvamento automático com base em tempo.

   1. Na caixa **[!UICONTROL Salvar automaticamente neste intervalo]**, especifique o intervalo em segundos. O formulário é salvo repetidamente após o número de segundos especificado na caixa de intervalo expirar.

1. (Somente para salvar automaticamente com base em eventos) Execute as etapas a seguir para configurar opções de Salvar automaticamente com base em eventos.

   1. Na caixa **Salvar automaticamente após esse evento**, especifique um evento [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html). O formulário é salvo sempre que a expressão é avaliada como TRUE.

1. (Opcional) Para salvar automaticamente o conteúdo para usuários anônimos, selecione a opção **Ativar salvamento automático para usuários anônimos** e clique em **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Para que a opção de salvamento automático funcione para usuários anônimos, certifique-se de configurar o Serviço de Configuração Comum da Forms para permitir que todos os usuários visualizem, verifiquem e assinem formulários.
   >
   >Para configurar o serviço, vá para AEM configuração do Web Console em `https://[server]:[host]/system/console/configMgr` e edite o **[!UICONTROL Forms Common Configuration Service]** para escolher a opção **[!UICONTROL All Users]** no campo **[!UICONTROL Allow]** e salve a configuração.