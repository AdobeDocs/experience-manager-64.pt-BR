---
title: Criar o primeiro formulário adaptável
seo-title: Create your first adaptive form
description: Saiba como criar formulários de classe empresarial, interativos e responsivos.
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 1%

---

# Criar o primeiro formulário adaptável {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Introdução {#introduction}

Você está procurando uma **experiência de formulários** que simplifica a inscrição, aumenta o engajamento e reduz o tempo de resposta, **formulários adaptáveis** é perfeito para você. Os formulários adaptáveis oferecem uma experiência de formulários móveis, automatizada e compatível com análises. É possível criar facilmente formulários responsivos e interativos por natureza, usar processos automatizados para reduzir tarefas administrativas e repetitivas e usar a análise de dados para melhorar e personalizar a experiência que os clientes têm com seus formulários.

Este tutorial fornece uma estrutura completa para criar um formulário adaptável. O tutorial é organizado em um caso de uso e vários guias. Cada guia ajuda você a aprender e adicionar novos recursos ao formulário adaptável criado neste tutorial. Você tem um formulário adaptável em funcionamento após cada guia. O guia para criar um formulário adaptável está disponível. Os guias subsequentes estarão disponíveis em breve. Ao final deste tutorial, você poderá:

* Crie um formulário adaptável e um modelo de dados de formulário.
* Estilo do formulário adaptável.
* Use o editor de regras de formulário adaptável para criar regras de negócios.
* Teste e publique um formulário adaptável.

![create-daptive-form-workflow](assets/create-daptive-form-workflow.png)

A jornada começa com o aprendizado do caso de uso:

Um site da Web oferece uma variedade de produtos para diversos clientes. Os clientes navegam pelo portal, selecionam e solicitam os produtos. Cada cliente cria uma conta e fornece endereços de envio e faturamento. Uma cliente já existente, Sara Rose, está procurando adicionar seu endereço de envio ao site. O site fornece um formulário online para adicionar e atualizar endereços de envio.

O site é executado no Adobe Experience Manager (AEM) e usa o AEM Forms para captura e processamento de dados. O formulário de adição e atualização de endereço é um formulário adaptável. O site armazena os detalhes do cliente em um banco de dados. Eles usam o formulário de adição e atualização de endereço para recuperar e exibir os endereços disponíveis. Eles também usam o formulário adaptável para aceitar endereços atualizados e novos.

### Pré-requisitos {#prerequisite}

* Configure uma instância do autor de AEM.
* Instalar [Complemento do AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) na instância do autor.
* Obtenha o driver de banco de dados JDBC (arquivo JAR) do provedor de banco de dados. Os exemplos no tutorial são baseados no banco de dados MySQL e usam o Oracle [Driver de banco de dados JDBC do MySQL](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Configure um banco de dados contendo dados do cliente com os campos exibidos abaixo. Um banco de dados não é essencial para criar um formulário adaptável. Este tutorial usa um banco de dados para exibir o modelo de dados de formulário e os recursos de persistência do AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Etapa 1: Criar um formulário adaptável {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Os formulários adaptáveis são de nova geração, envolvente, responsivo, dinâmico e adaptável por natureza. Usando formulários adaptáveis, você pode fornecer experiências personalizadas e direcionadas. A AEM Forms fornece um editor WYSIWYG de arrastar e soltar para criar formulários adaptáveis. Para obter mais informações sobre formulários adaptáveis, consulte [Introdução à criação de formulários adaptáveis](/help/forms/using/introduction-forms-authoring.md).

Metas:

* Crie um formulário adaptável que permita ao cliente adicionar um endereço de envio
* Campos de layout de um formulário adaptável para exibir e aceitar informações de um cliente
* Criar ação de envio para enviar um email contendo conteúdo de formulário
* Visualizar e enviar um formulário adaptável

[ ](create-adaptive-form.md)

## Etapa 2: Criar Modelo de Dados de Formulário {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Um modelo de dados de formulário permite conectar um formulário adaptável a diferentes fontes de dados. Por exemplo, AEM perfil de usuário, serviços da Web RESTful, serviços da Web baseados em SOAP, serviços OData e bancos de dados relacionais. Um modelo de dados de formulário é um esquema de representação de dados unificado de entidades comerciais e serviços disponíveis em fontes de dados conectadas. É possível usar o modelo de dados de formulário com um formulário adaptável para recuperar, atualizar, excluir e adicionar dados a fontes de dados conectadas.

Metas:

* Configurar a instância do banco de dados do site (banco de dados MySQL) como fontes de dados
* Criar o modelo de dados de formulário usando o banco de dados MySQL como uma fonte de dados
* Adicionar objetos de modelo de dados ao modelo de dados de formulário
* Configurar serviços de leitura e gravação para o modelo de dados de formulário
* Testar modelo de dados de formulário e serviços configurados com dados de teste

[ ](create-form-data-model.md)

## Etapa 3: Aplicar regras a campos de formulário adaptáveis {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Os formulários adaptáveis fornecem um editor para gravar regras em objetos de formulário adaptáveis. Essas regras definem ações a serem acionadas em objetos de formulário com base em condições predefinidas, entradas de usuário e ações de usuário no formulário. Ele ajuda a garantir a precisão e acelera a experiência de preenchimento de formulários.

Metas:

* Criar e aplicar regras a campos de formulário adaptáveis
* Usar regras para acionar serviços de modelo de dados de formulário para atualizar dados para o banco de dados

## Etapa 4: Estilo do formulário adaptável {#step-style-your-adaptive-form}

![09-Estilo-o-formulário-adaptável_pequeno](assets/09-Style-your-adaptive-form_small.png)

Os formulários adaptáveis fornecem temas e um [editor](/help/forms/using/themes.md) para criar temas para as formas adaptáveis. Um tema contém detalhes de estilo para componentes e painéis, e você pode reutilizar um tema em diferentes formas. Os estilos incluem propriedades como cores de plano de fundo, cores de estado, transparência, alinhamento e tamanho. Quando o tema é aplicado ao formulário, o estilo especificado reflete nos componentes correspondentes do formulário. Formulários adaptáveis também oferecem suporte ao estilo em linha para estilos específicos de um formulário.

Metas:

* Aplicar um tema pronto para uso a um formulário adaptável
* Criar um tema para um formulário adaptável usando o editor de temas
* Usar fontes da Web em um tema personalizado

[ ](style-your-adaptive-form.md)

## Etapa 5: Testar o formulário adaptável {#step-test-your-adaptive-form}

![11-teste-o-formulário adaptável](assets/11-test-your-adaptive-form.png)

Os formulários adaptáveis são parte integrante das interações do cliente. É importante testar seus formulários adaptáveis com todas as alterações feitas neles. Testar cada campo de um formulário é entediante. A AEM Forms fornece um SDK (Calvin SDK) para automatizar o teste de formulários adaptáveis. O Calvin permite automatizar o teste de seus formulários adaptáveis no navegador da Web.

Metas:

* Instalar o SDK do Calvin
* Criar conjunto de testes e casos de teste para o formulário de endereço de alteração

Para saber mais sobre o SDK, consulte [Uso de testes automatizados com AEM formulário adaptável](/help/forms/using/calvin.md).

## Etapa 6: Publicar o formulário adaptável {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Você pode publicar formulários adaptáveis como um formulário independente (aplicativo de página única), incluindo em AEM [página sites](/help/forms/using/embed-adaptive-form-aem-sites.md)ou listar em um site AEM usando [Forms Portal](/help/forms/using/introduction-publishing-forms.md).

Metas:

* Publicar o formulário adaptável como um aplicativo de página única
