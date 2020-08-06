---
title: Incorporação do componente de link em uma página
seo-title: Incorporação do componente de link em uma página
description: 'Você pode usar o componente de link para vincular um documento adaptável ou um formulário adaptável de qualquer página.  '
seo-description: 'Você pode usar o componente de link para vincular um documento adaptável ou um formulário adaptável de qualquer página.  '
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 1%

---


# Incorporação do componente de link em uma página{#embedding-link-component-in-a-page}

## Pré-requisitos {#prerequisites}

O componente de link é um membro da categoria de Serviços do Documento. Certifique-se de que a categoria dos Serviços de Documento esteja visível no navegador de componentes AEM. Se a categoria não estiver listada, siga as etapas listadas em [Ativar componentes](/help/forms/using/enabling-forms-portal-components.md)do portal de formulários.

## Componente do link {#link-component}

O componente Link permite que os autores do portal de formulários criem um link para um formulário adaptável de qualquer lugar em uma página. O componente Link está disponível na seção Serviços de Documento no navegador de componentes.

Execute as seguintes etapas para adicionar um componente Link à página:

1. Arraste o componente **Link** na página. Selecione o componente e toque em ![cmppr](assets/cmppr.png). A caixa de diálogo Editar componente de link é aberta.

   ![edit-link-component](assets/edit-link-component.png)

1. Na guia **Exibir** , especifique o seguinte:

   * **Legenda** do link: Texto ou legenda do link.
   * **Dica de ferramenta** do link: Dica de ferramenta para o link.
   * **Modelo** de layout: Modelo para o layout do componente Link.

1. Abra a guia Informações **do** ativo e especifique o tipo do ativo. Um ativo pode ser um **formulário**. Dependendo do tipo de ativo selecionado, as opções listadas abaixo são exibidas:

   * **Caminho** do ativo: Caminho do repositório no qual o ativo é armazenado.
   * **Tipo** de renderização: O formato de renderização — PDF, HTML ou Automático. O tipo de renderização automática detecta o ambiente do usuário e, portanto, renderiza o formulário como HTML ou PDF. Por exemplo, se o formulário for acessado de um dispositivo móvel, o tipo de renderização Automática renderizará o formulário em HTML.
   * **Enviar URL:**  URL para o servlet onde os dados do formulário são enviados.
   * **Perfil** HTML: Perfil para renderizar o formulário como HTML.
   * **Perfil** PDF: Perfil para renderizar o formulário como documento PDF.

1. Abra a guia **Avançado.** Você pode especificar os parâmetros adicionais no formato de par de valor chave. Quando o link é clicado, esses parâmetros adicionais são passados com o formulário.

   Toque em **Concluído** para salvar a configuração.

## Práticas recomendadas para usar o componente Link {#best-practices-for-using-link-component-br}

* Certifique-se de selecionar PDF como o tipo de renderização se o caminho especificado em Caminho do formulário apontar para um documento que tenha PDF como o formato de renderização permitido.
* O URL de envio de um formulário pode ser especificado em vários locais e sua ordem de precedência é a seguinte:

   1. O URL de envio incorporado no formulário (no botão Enviar) tem a prioridade mais alta.
   1. O URL de envio mencionado no Forms Manager tem prioridade média.
   1. O URL de envio mencionado no portal de formulários tem a prioridade mais baixa.

