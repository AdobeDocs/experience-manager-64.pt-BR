---
title: Visão geral das comunicações interativas
seo-title: Interactive Communications Overview
description: Este artigo inclui visão geral, casos de uso de exemplo, fluxo de trabalho de criação e diferenças entre comunicação interativa e carta.
seo-description: Interactive Communication key capabilities, sample use cases, creation workflow, and differences between Interactive Communication and Correspondence Management
uuid: a06b4ac7-ca20-4d6d-b2b7-87b21e2f5cf9
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 67b03098-c58d-4a57-90e0-e4ddd78e5d99
exl-id: 386fc8b2-c92d-4731-8445-1bb6af54fd98
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 7%

---

# Visão geral das comunicações interativas {#interactive-communications-overview}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Este artigo inclui visão geral, casos de uso de exemplo, fluxo de trabalho de criação e diferenças entre comunicação interativa e carta.

![](do-not-localize/correspondence-management.png)

As Comunicações interativas centralizam e gerenciam a criação, montagem e delivery de correspondências seguras, personalizadas e interativas, como correspondência comercial, documentos, declarações, avisos de benefícios, emails de marketing, contas e kits de boas-vindas.

## Principais recursos {#key-capabilities}

Veja a seguir os principais recursos das Comunicações interativas:

* Integração imediata com o modelo de dados de formulário para permitir o acesso fácil e simplificado a bancos de dados back-end e outros sistemas CRM, como o MS® Dynamics
* Interface de criação integrada para canais de impressão e Web com capacidade de gerar automaticamente canal da Web a partir do canal de impressão
* Gráficos para apresentar informações em formatos visuais facilmente compreensíveis em impressão e web
* Fragmentos de documento suportam o editor de regras e o modelo de dados de formulário
* A interface do usuário do agente exibe a pré-visualização da Web e impressão da Comunicação interativa
* Arrastar e soltar componentes para construir rapidamente canais de impressão e da Web

## Caso de uso de exemplo {#sample-use-case}

O [kit de boas-vindas para um cliente de cartão de crédito](/help/forms/using/finance-reference-site-walkthrough.md#credit-card-application-walkthrough) caso de uso de exemplo mostra os recursos de uma Comunicação interativa.

## Criação de comunicação interativa  {#interactive-communication-creation}

![interative_communication-01](assets/interactive_communication-01.jpg)

### Fluxo de trabalho {#workflow}

Para criar uma comunicação interativa, faça com que [blocos de construção](#buildingblocks) para comunicação interativa pronta e depois conclua as seguintes etapas:

1. Escolha para [criar uma comunicação interativa](/help/forms/using/create-interactive-communication.md).

1. Especifique a [modelo de dados de formulário](/help/forms/using/data-integration.md), serviço de preenchimento prévio e [modelos de canal de impressão e Web](/help/forms/using/web-channel-print-channel.md). Você pode optar por gerar o canal da Web a partir do canal de impressão.

1. Usar o [interface de arrastar e soltar](/help/forms/using/introduction-interactive-communication-authoring.md), adicione fragmentos de documento, imagens, componentes para imprimir e canal da Web da Comunicação interativa, conforme necessário.
1. Configure as propriedades dos componentes inseridos, como o seguinte:

   1. Imagens
   1. [Tabelas](/help/forms/using/create-interactive-communication.md#tables) (Incluindo Fragmentos de Layout)
   1. [Gráficos](/help/forms/using/chart-component-interactive-communications.md)
   1. [Fragmentos de documento](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. Visualize canais de impressão e da Web e, se necessário, edite a Comunicação interativa.
1. O agente usa a interface do agente para [preparar a comunicação interativa](/help/forms/using/prepare-send-interactive-communication.md) para enviá-lo ao recipient/pós-processo.

### Blocos de construção {#buildingblocks}

A seguir estão os blocos de construção necessários para criar uma Comunicação Interativa:

* [Modelo de dados do formulário](/help/forms/using/data-integration.md)
* [Modelos de canal de impressão e Web](/help/forms/using/web-channel-print-channel.md)
* [Fragmentos de documento](/help/forms/using/document-fragments.md)
* Imagens
* [Temas](/help/forms/using/themes.md) para o canal Web

## Comunicações Interativas E Gerenciamento De Correspondência {#interactive-communications-vs-correspondence-management}

A Comunicação interativa é a abordagem padrão e recomendada para criar comunicações com clientes. Para continuar usando as letras que criam no AEM 6.3 Forms e no AEM 6.2 Forms, é necessário [instalar um pacote de compatibilidade](/help/forms/using/compatibility-package.md). Veja a seguir uma comparação entre os recursos de Comunicação interativa e carta.

<table> 
 <tbody>
  <tr>
   <td><strong>Recurso</strong></td> 
   <td><strong>Comunicação interativa</strong></td> 
   <td><strong>Carta</strong></td> 
  </tr>
  <tr>
   <td>Saída</td> 
   <td>Impressão e Web</td> 
   <td>Imprimir</td> 
  </tr>
  <tr>
   <td>Schema</td> 
   <td>Modelo de dados do formulário </td> 
   <td>Dicionário de dados </td> 
  </tr>
  <tr>
   <td>Localização</td> 
   <td>Não suportado no modelo de dados de formulário</td> 
   <td>Suportado no dicionário de dados</td> 
  </tr>
  <tr>
   <td>Editor de regras</td> 
   <td>
    <ul> 
     <li>Editor de regras de suporte a texto e condição para criar condições em linha</li> 
     <li>O editor de comunicação interativa oferece suporte à aplicação de regras em componentes do canal da Web</li> 
    </ul> </td> 
   <td>Nenhuma interface do usuário para criação de expressão condicional</td> 
  </tr>
  <tr>
   <td>Criação  </td> 
   <td>Arrastar e soltar interface para construir canal de impressão e da Web</td> 
   <td>Nenhum mecanismo de arrastar e soltar </td> 
  </tr>
  <tr>
   <td>Gráficos</td> 
   <td>Gráficos suportados em impressão e canal da Web</td> 
   <td>Não suportado</td> 
  </tr>
  <tr>
   <td>Temas</td> 
   <td>Usa temas para criar estilo no canal da Web</td> 
   <td>Não apoia temas</td> 
  </tr>
  <tr>
   <td>Auditoria e Controle de Versão</td> 
   <td>Não suportado</td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Rascunhos e gerenciamento de instâncias</td> 
   <td>Não suportado</td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Processamento em lote</td> 
   <td>Compatível </td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Assinatura do agente</td> 
   <td>Não suportado</td> 
   <td>Compatível</td> 
  </tr>
  <tr>
   <td>Funções remotas</td> 
   <td>Não suportado</td> 
   <td>Compatível</td> 
  </tr>
 </tbody>
</table>
