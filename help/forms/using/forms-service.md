---
title: Serviço do Forms
seo-title: Forms Service
description: O artigo descreve o serviço Forms e as tarefas relacionadas ao formulário que você pode executar usando o serviço Forms.
seo-description: The article describes Forms service and the form-related tasks you can perform using Forms service.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
exl-id: a1c7c90f-6b50-4bc1-9972-1d3bdf8887ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 1%

---

# Serviço do Forms {#forms-service}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O serviço Forms permite criar aplicativos clientes interativos de captura de dados que validam, processam, transformam e entregam formulários normalmente criados no Designer. O serviço Forms renderiza como PDF documenta qualquer design de formulário desenvolvido.

O serviço Forms também permite que as organizações estendam seus processos inteligentes de captura de dados, implantando formulários eletrônicos como PDF de Adobe. Também é possível usar o serviço para importar e exportar dados de e para PDF forms existentes, respectivamente.

Use o serviço Forms para fazer o seguinte:

* Renderizar PDF forms com base no modelo e dados XML.
* Habilite a integração de dados de formulário para importar dados e extrair dados do PDF forms.
* Renderizar formulários com base em fragmentos.

## Criação de PDF forms  {#creating-pdf-forms-nbsp}

Use o serviço Formulário para criar PDF forms para captura de dados. Normalmente, você começa com um modelo do AEM Forms Designer. Use o `renderPDFForm` (link para Javadoc) do serviço Forms para converter esse modelo em um formulário PDF.

O primeiro parâmetro da variável `renderPDFForm` operation é o nome do arquivo de modelo (por exemplo, `ExpenseClaim.xdp`). Você pode armazenar o arquivo de modelo em um sistema de arquivos local, repositório CRX ou em um local HTTP ou FTP. Você pode especificar o local do arquivo de modelo, definindo a raiz de conteúdo no `PDFFormRenderOptions` do `renderPDFForm` operação. Consulte Javadoc para obter detalhes sobre outras opções que você pode especificar para a variável `PDFFormRenderOptions` parâmetro.

O `renderPDFForm` também pode aceitar dados XML. Os dados XML são unidos ao modelo ao criar um Formulário PDF para que o formulário PDF gerado contenha os dados especificados. O segundo parâmetro para o `renderPDFForm` operação pode aceitar um objeto Document (Javadoc) que contenha dados XML.

## Extrair dados de PDF forms  {#extracting-data-from-pdf-forms-nbsp}

Use o `exportData` (Javadoc) operação do serviço Forms para extrair dados XML de um formulário PDF. Essa operação aceita um documento como seu primeiro parâmetro. Você pode exportar os dados como um documento XDP ou um arquivo XML. Se você exportar os dados como um arquivo XML, os dados exportados removerão o envelope XDP e retornará um arquivo XML simples. Você pode especificar essa disposição usando o segundo parâmetro.

## Importação de dados para o PDF forms {#importing-data-into-pdf-forms}

O serviço Forms também permite mesclar um formulário PDF criado usando o AEM Forms Designer ou o `renderPDFForm` operação com dados XML. O `importData` (Javadoc) a operação do serviço Forms aceita o formulário PDF e os dados XML e retorna um formulário PDF com dados XML.

## Renderização de formulários com base em fragmentos {#rendering-forms-based-on-fragments}

O serviço Forms pode renderizar formulários com base em fragmentos criados usando o AEM Forms Designer. Um fragmento é uma parte reutilizável de um formulário. Ele é salvo como um arquivo XDP separado que pode ser inserido em vários designs de formulário. Por exemplo, um fragmento pode incluir um bloco de endereço ou texto legal.

O uso de fragmentos simplifica e acelera a criação e a manutenção de um grande número de formulários. Ao criar um formulário, insira uma referência no fragmento necessário para que o fragmento apareça no formulário. A referência de fragmento contém um subformulário que aponta para o arquivo XDP físico.

Estas são as vantagens do uso de fragmentos:

* **Reutilização de conteúdo**: É possível reutilizar o conteúdo em vários designs de formulário. Para reutilizar rapidamente partes do mesmo conteúdo em vários formulários, crie um fragmento. Copiar ou recriar o conteúdo leva mais tempo. O uso de fragmentos também garante que as partes de um design de formulário usadas com frequência tenham conteúdo e aparência consistentes em todos os formulários de referência.
* **Atualizações globais**: É possível fazer alterações globais em vários formulários apenas uma vez em um arquivo. É possível alterar o conteúdo, objetos de script, vínculos de dados, layout ou estilos em um fragmento. Todos os formulários XDP que fazem referência ao fragmento refletem as alterações.
* **Criação de formulário compartilhado**: É possível compartilhar a criação de formulários entre vários recursos. Os desenvolvedores de formulários com experiência em scripts ou outros recursos avançados do AEM Forms Designer podem desenvolver e compartilhar fragmentos que usam propriedades dinâmicas e de scripts. Os designers de formulários podem usar os fragmentos para projetar formulários. Além disso, é possível usar os fragmentos para garantir que todas as partes de um formulário tenham uma aparência e funcionalidade consistentes em vários formulários.
