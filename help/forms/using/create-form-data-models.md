---
title: Criar modelo de dados de formulário
seo-title: Create form data model
description: Saiba como criar modelos de dados de formulário com ou sem fontes de dados configuradas.
seo-description: Learn how to create form data models with or without configured data sources.
uuid: bed1a82e-a799-4034-9068-1478b95e6c70
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 3a3a6ede-52af-4c37-8a51-c2ea721a28dc
feature: Form Data Model
exl-id: 16d1d5ea-6076-448d-9f63-78a0f2ff2756
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---

# Criar modelo de dados de formulário {#create-form-data-model}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Saiba como criar modelos de dados de formulário com ou sem fontes de dados configuradas.

![](do-not-localize/data-integeration.png)

A integração de dados do AEM Forms oferece uma interface de usuário intuitiva para criar e trabalhar com modelos de dados de formulário. Um modelo de dados de formulário depende de fontes de dados para o intercâmbio de dados; no entanto, é possível criar um modelo de dados de formulário com ou sem uma fonte de dados. Existem duas abordagens para criar um a partir do modelo de dados, dependendo se você configurou as fontes de dados:

* **Uso de fontes de dados pré-configuradas**: Se você configurou fontes de dados conforme descrito em [Configurar fontes de dados](/help/forms/using/configure-data-sources.md), é possível selecioná-los ao criar um modelo de dados de formulário. Ele traz todos os objetos, propriedades e serviços do modelo de dados das fontes de dados selecionadas disponíveis para uso no modelo de dados de formulário.

* **Sem fontes de dados**: Se você não tiver configurado fontes de dados para seu modelo de dados de formulário, ainda poderá criá-lo sem fontes de dados. Você pode usar o modelo de dados de formulário para criar formulários adaptáveis e comunicação interativa e testá-los usando dados de amostra. Quando as fontes de dados estão disponíveis, é possível vincular o modelo de dados de formulário às fontes de dados, o que refletirá automaticamente nos formulários adaptáveis associados e nas comunicações interativas.

>[!NOTE]
>
>Você deve ser um membro de ambos **fdm-author** e **usuário de formulários** para criar e trabalhar com o modelo de dados de formulário. Entre em contato com o administrador do AEM para se tornar membro dos grupos.

## Criar modelo de dados de formulário {#data-sources}

Verifique se você configurou as fontes de dados que pretende usar no modelo de dados de formulário, conforme descrito em [Configurar fontes de dados](/help/forms/using/configure-data-sources.md). Faça o seguinte para criar um modelo de dados de formulário com base em fontes de dados configuradas:

1. Em AEM instância do autor, navegue até **[!UICONTROL Forms > Integrações de dados]**.
1. Toque **[!UICONTROL Criar > Modelo de dados de formulário]**.
1. Na caixa de diálogo Criar modelo de dados de formulário :

   * Especifique um nome para o modelo de dados de formulário.
   * (**Opcional**) Especifique o título, a descrição e as tags para o modelo de dados de formulário.
   * (**Opcional e aplicável somente se as fontes de dados estiverem configuradas**) Toque no ícone de marca de verificação ao lado do **[!UICONTROL Configuração da Fonte de Dados]** e selecione o nó de configuração onde residem os serviços de nuvem das fontes de dados que você deseja usar. Ele restringe a lista de fontes de dados disponíveis para seleção na próxima página às disponíveis no nó de configuração selecionado. No entanto, qualquer banco de dados JDBC e fontes de dados de perfil de usuário AEM são listadas por padrão. Se você não selecionar um nó de configuração, as fontes de dados de todos os nós de configuração serão listadas.

   Toque **[!UICONTROL Próximo]**.

1. (**Aplicável somente se as fontes de dados estiverem configuradas**) **[!UICONTROL Selecionar fonte de dados]** lista as fontes de dados disponíveis, se houver. Selecione fontes de dados que deseja usar no modelo de dados de formulário.
1. Toque **[!UICONTROL Criar]** e na caixa de diálogo de confirmação, toque em **[!UICONTROL Abrir]** para abrir o editor de modelo de dados de formulário.

Vamos analisar os diferentes componentes da interface do usuário do editor de modelo de dados de formulário.

![Um modelo de dados de formulário com três fontes de dados - um serviço RESTful, AEM perfil de usuário e um RDBMS](assets/fdm-ui.png)

**A. Fontes de dados** Lista as fontes de dados em um modelo de dados de formulário. Expanda uma fonte de dados para exibir seus objetos e serviços do modelo de dados.

**B. Atualizar Definições da Fonte de Dados** Busca todas as alterações nas definições da fonte de dados de fontes de dados configuradas e as atualiza na guia Fontes de dados do editor de modelo de dados de formulário.

**C. Modelo** Área de conteúdo na qual os objetos de modelo de dados adicionados são exibidos.

**D. Serviços** Área de conteúdo onde são exibidas operações ou serviços de fonte de dados adicionados.

**E. Barra de ferramentas** Ferramentas para trabalhar com o modelo de dados de formulário. A barra de ferramentas mostra mais opções dependendo do objeto selecionado no modelo de dados de formulário.

**F. Adicionar Selecionado** Adiciona objetos e serviços de modelo de dados selecionados ao modelo de dados de formulário.

Para obter mais informações sobre o editor de modelo de dados de formulário e como trabalhar com ele para editar e configurar o modelo de dados de formulário, consulte [Trabalhar com o modelo de dados de formulário](/help/forms/using/work-with-form-data-model.md).

## Atualizar fontes de dados {#update}

Faça o seguinte para adicionar ou atualizar fontes de dados a um modelo de dados de formulário existente.

1. Ir para **[!UICONTROL Forms > Integrações de dados]**, selecione o modelo de dados de formulário no qual deseja adicionar ou atualizar fontes de dados e toque em **[!UICONTROL Propriedades]**.
1. Nas propriedades do modelo de dados de formulário, acesse **[!UICONTROL Atualizar origem]** guia .

   Na guia Atualizar fonte :

   * Toque no ícone de navegação na **[!UICONTROL Configuração sensível ao contexto]** e selecione um nó de configuração em que reside a configuração da nuvem para a fonte de dados que você deseja adicionar. Se você não selecionar um nó, as configurações de nuvem residentes somente na variável `global` são listados ao tocar **[!UICONTROL Adicionar fontes]**.
   * Para adicionar uma nova fonte de dados, toque em **[!UICONTROL Adicionar fontes]** e selecione as fontes de dados a serem adicionadas ao modelo de dados do formulário. Todas as fontes de dados configuradas em `global` e o nó de configuração selecionado, se houver, serão exibidos.
   * Para substituir uma fonte de dados existente por outra fonte de dados do mesmo tipo, toque no **[!UICONTROL Editar]** ícone para a fonte de dados e selecione na lista de fontes de dados disponíveis.
   * Para excluir uma fonte de dados existente, toque no **[!UICONTROL Excluir]** ícone para a fonte de dados. O ícone Excluir será desativado se um objeto de modelo de dados na fonte de dados for adicionado ao modelo de dados de formulário.

   ![fdm-properties](assets/fdm-properties.png)

1. Toque **[!UICONTROL Salvar e fechar]** para salvar as atualizações.

>[!NOTE]
>
>Depois de adicionar novas fontes de dados ou atualizar fontes de dados existentes em um modelo de dados de formulário, atualize as referências de vínculo, conforme apropriado, em formulários adaptáveis e comunicações interativas que usam o modelo de dados de formulário atualizado.

## Próximas etapas {#next-steps}

Agora há um modelo de dados de formulário com fontes de dados adicionadas a ele. Em seguida, é possível editar o modelo de dados de formulário para adicionar e configurar objetos e serviços de modelo de dados, adicionar associações entre objetos de modelo de dados, editar propriedades, adicionar objetos e propriedades de modelo de dados personalizados, gerar dados de amostra e assim por diante.

Para obter mais informações, consulte [Trabalhar com o modelo de dados de formulário](/help/forms/using/work-with-form-data-model.md).
