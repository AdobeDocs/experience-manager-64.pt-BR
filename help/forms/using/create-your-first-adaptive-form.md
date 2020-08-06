---
title: Criar seu primeiro formulário adaptável
seo-title: Criar seu primeiro formulário adaptável
description: 'Saiba como criar formulários de classe empresarial, interativos e responsivos. '
seo-description: 'Saiba como criar formulários de classe empresarial, interativos e responsivos. '
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
translation-type: tm+mt
source-git-commit: fae6d621ad61a26db99994482c16c9d9a5f88ad9
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 0%

---


# Criar seu primeiro formulário adaptável {#do-not-publish-create-your-first-adaptive-form}

![01-create-first-adaptive-form-herói-image](assets/01-create-first-adaptive-form-hero-image.png)

## Introdução {#introduction}

Você está procurando uma experiência **de** formulários para dispositivos móveis que simplifique as inscrições, aumente o envolvimento e reduza o tempo de resposta, os formulários **** adaptáveis são adequados para você? Formulários adaptáveis oferecem uma experiência móvel, de automação e de formulários compatíveis com a análise. Você pode criar facilmente formulários que sejam responsivos e interativos na natureza, usar processos automatizados para reduzir tarefas administrativas e repetitivas e usar análises de dados para melhorar e personalizar a experiência que os clientes têm com seus formulários.

Este tutorial fornece uma estrutura completa para criar um formulário adaptável. O tutorial é organizado em um caso de uso e em várias guias. Cada guia o ajuda a aprender e adicionar novos recursos ao formulário adaptativo criado neste tutorial. Você tem um formulário adaptativo funcionando depois de cada guia. O guia para criar um formulário adaptável está disponível. Guias subsequentes estarão disponíveis em breve. No final deste tutorial, você poderá:

* Crie um formulário adaptável e um modelo de dados de formulário.
* Estilo do formulário adaptável.
* Use o editor de regras de formulário adaptável para criar regras de negócios.
* Teste e publique um formulário adaptável.

![create-daptive-form-workflow](assets/create-daptive-form-workflow.png)

A jornada start com o aprendizado do caso de uso:

Um site oferta uma variedade de produtos para diversos clientes. Os clientes navegam pelo portal, selecionam e solicitam os produtos. Cada cliente cria uma conta e fornece endereços de remessa e faturamento. Uma cliente já existente, Sara Rose, está procurando adicionar seu endereço de entrega ao site. O site fornece um formulário on-line para adicionar e atualizar endereços de envio.

O site é executado no Adobe Experience Manager (AEM) e usa o AEM Forms para captura e processamento de dados. O formulário de adição e atualização de endereço é um formulário adaptável. O site armazena os detalhes do cliente em um banco de dados. Eles usam a adição de endereço e o formulário de atualização para recuperar e exibir endereços disponíveis. Eles também usam o formulário adaptável para aceitar endereços atualizados e novos.

### Pré-requisitos {#prerequisite}

* Configure uma instância do autor AEM.
* Instale o complemento [do](/help/forms/using/installing-configuring-aem-forms-osgi.md) AEM Forms na instância do autor.
* Obtenha o driver de banco de dados JDBC (arquivo JAR) do provedor de banco de dados. Os exemplos no tutorial são baseados no banco de dados MySQL e usam o driver [de banco de dados](https://dev.mysql.com/downloads/connector/j/5.1.html)MySQL JDBC da Oracle.

* Configure um banco de dados contendo dados do cliente com os campos exibidos abaixo. Um banco de dados não é essencial para criar um formulário adaptável. Este tutorial usa um banco de dados para exibir o modelo de dados do formulário e os recursos de persistência do AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Etapa 1: Criar um formulário adaptável {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

Os formulários adaptáveis são de nova geração, envolventes, responsivos, dinâmicos e adaptáveis na natureza. Usando formulários adaptáveis, você pode fornecer experiências personalizadas e direcionadas. A AEM Forms fornece um editor WYSIWYG para arrastar e soltar para criar formulários adaptáveis. Para obter mais informações sobre formulários adaptáveis, consulte [Introdução à criação de formulários](/help/forms/using/introduction-forms-authoring.md)adaptáveis.

Objetivos:

* Crie um formulário adaptável que permita ao cliente adicionar um endereço de entrega
* Campos de layout de um formulário adaptável para exibir e aceitar informações de um cliente
* Criar ação de envio para enviar um email contendo conteúdo de formulário
* Pré-visualização e envio de um formulário adaptável

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](create-adaptive-form.md)

## Step 2: Create Form Data Model {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Um modelo de dados de formulário permite conectar um formulário adaptável a fontes de dados diferentes. Por exemplo, AEM perfil do usuário, serviços Web RESTful, serviços Web baseados em SOAP, serviços OData e bancos de dados relacionais. Um modelo de dados de formulário é um schema de representação de dados unificado de entidades de negócios e serviços disponíveis em fontes de dados conectadas. Você pode usar o modelo de dados de formulário com um formulário adaptável para recuperar, atualizar, excluir e adicionar dados a fontes de dados conectadas.

Objetivos:

* Configurar a instância do banco de dados do site (banco de dados MySQL) como fontes de dados
* Criar o modelo de dados de formulário usando o banco de dados MySQL como uma fonte de dados
* Adicionar objetos de modelo de dados ao modelo de dados de formulário
* Configurar serviços de leitura e gravação para o modelo de dados de formulário
* Testar modelo de dados de formulário e serviços configurados com dados de teste

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](create-form-data-model.md)

## Etapa 3: Aplicar regras a campos de formulário adaptáveis {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Formulários adaptáveis fornecem um editor para escrever regras em objetos de formulário adaptáveis. Essas regras definem ações para acionar objetos de formulário com base em condições predefinidas, entradas do usuário e ações do usuário no formulário. Ele ajuda a garantir a precisão e acelera a experiência de preenchimento do formulário.

Objetivos:

* Criar e aplicar regras a campos de formulário adaptáveis
* Usar regras para acionar serviços de modelo de dados de formulário para atualizar dados para o banco de dados

## Etapa 4: Estilo do formulário adaptável {#step-style-your-adaptive-form}

![09-Estilo-sua-forma-adaptativa_pequena](assets/09-Style-your-adaptive-form_small.png)

Os formulários adaptativos fornecem temas e um [editor](/help/forms/using/themes.md) para criar temas para os formulários adaptáveis. Um tema contém detalhes de estilização para componentes e painéis, e você pode reutilizar um tema em diferentes formas. Os estilos incluem propriedades como cores de plano de fundo, cores de estado, transparência, alinhamento e tamanho. Quando o tema é aplicado ao formulário, o estilo especificado é refletido nos componentes correspondentes do formulário. Formulários adaptáveis também suportam estilos em linha para estilos específicos de um formulário.

Objetivos:

* Aplicar um tema predefinido a um formulário adaptável
* Criar um tema para formulário adaptável usando o editor de temas
* Usar fontes da Web em um tema personalizado

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Etapa 5: Teste o formulário adaptável {#step-test-your-adaptive-form}

![11-teste-sua-forma adaptativa](assets/11-test-your-adaptive-form.png)

Formulários adaptáveis são parte integrante das interações do cliente. É importante testar seus formulários adaptáveis com todas as alterações feitas neles. Testar cada campo de um formulário é tedioso. A AEM Forms fornece um SDK (Calvin SDK) para automatizar o teste de formulários adaptáveis. O Calvin permite que você automatize o teste de seus formulários adaptáveis no navegador da Web.

Objetivos:

* Instalar o Calvin SDK
* Criar conjunto de testes e casos de teste para o formulário de endereço de alteração

Para saber mais sobre o SDK, consulte [Uso de testes automatizados com AEM formulário](/help/forms/using/calvin.md)adaptável.

## Etapa 6: Publicar seu formulário adaptativo {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Você pode publicar formulários adaptáveis como um formulário independente (aplicativo de página única), incluir AEM página [de](/help/forms/using/embed-adaptive-form-aem-sites.md)sites ou lista em um site AEM usando o [Forms Portal](/help/forms/using/introduction-publishing-forms.md).

Objetivos:

* Publicar o formulário adaptável como um aplicativo de página única

