---
title: "Tutorial: Planejar a comunicação interativa"
seo-title: Plan your Interactive Communication
description: Planeje a anatomia de sua comunicação interativa
seo-description: Plan the anatomy for your Interactive Communication
uuid: 1c2b5c5b-c655-4559-8748-3e0b343779c2
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 75b2d424-91d3-45b4-a5d7-fb49ab558582
feature: Interactive Communication
exl-id: 40f6297d-7238-4e56-9fd1-6df3a6362724
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 3%

---

# Tutorial: Planejar a comunicação interativa {#tutorial-plan-the-interactive-communication}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Planeje a anatomia de sua comunicação interativa

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Este tutorial é uma etapa do [Criar sua primeira comunicação interativa](/help/forms/using/create-your-first-interactive-communication.md) série. É recomendável seguir a série em sequência cronológica para entender, executar e demonstrar o caso de uso tutorial completo.

A primeira etapa no planejamento de uma comunicação interativa é finalizar o conteúdo da comunicação interativa. Especialistas de assuntos de departamentos como jurídico, financeiro, suporte ou marketing podem ajudá-lo a finalizar o conteúdo. Após a finalização do conteúdo, é necessário analisá-lo para identificar os vários tipos de ativos necessários para criar a Comunicação interativa.

## Considerações sobre planejamento {#planning-considerations}

Uma comunicação interativa inclui os seguintes elementos:

* **Texto estático** A maioria inclui as partes da comunicação interativa que são de natureza genérica e estão incluídas na comunicação com todos os clientes. Por exemplo, cabeçalho, rodapé, saudação ou isenções de responsabilidade.
* **Dados provenientes de um sistema de back-end (modelo de dados de formulário)** O é específico do cliente e é dinamicamente mesclado com a comunicação interativa. Por exemplo, o número ou o endereço da política podem ser obtidos usando o modelo de dados de formulário.
* **Layout ou modelos** para as versões Imprimir e Web da Comunicação Interativa.
* **Pedido** em que os vários parágrafos de texto aparecem na Comunicação interativa.
* **Dados inseridos por um funcionário de linha de frente (interface do usuário do agente)** quem está personalizando a comunicação antes de enviá-la. Por exemplo, a data de vencimento do pagamento.

* **Dados condicionais** que é preenchida com base em condições predefinidas. Por exemplo, a data em que a comunicação interativa é gerada.
* **Imagens armazenadas em um repositório**, como logotipos e imagens de assinatura. Imagens como logotipos corporativos apareceriam na maioria ou em toda a comunicação interativa.
* **Tabelas e gráficos** necessário para simplificar a representação de dados complexos em uma comunicação interativa

## Anatomia da Comunicação Interativa {#anatomy-of-the-interactive-communication}

Após finalizar o conteúdo e os elementos usados para criar sua Comunicação interativa, você pode criar uma anatomia da Comunicação interativa. A anatomia deve ter os detalhes listados no [Considerações sobre planejamento](/help/forms/using/planning-interactive-communications.md#planning-considerations) seção. Baseado no nosso caso de uso, o exemplo a seguir é uma anatomia da conta mensal que um operador de telecom envia para seus clientes.

A anatomia inclui dados com os seguintes modos de entrada:

* Texto estático
* Modelo de dados do formulário
* IU do agente
* Dados condicionais
* Imagens

Em cada seção, o texto em negrito representa texto estático. O banco de dados inclui tabelas de clientes, contas e chamadas. Um modelo de dados de formulário pode receber dados de qualquer uma dessas tabelas. Para obter mais informações, consulte [Criar modelo de dados de formulário](create-form-data-model-tutorial.md).

A tabela a seguir ilustra a fonte de dados para cada campo na anatomia da comunicação interativa:

<table> 
 <tbody>
  <tr>
   <td>Seção</td> 
   <td>Texto estático</td> 
   <td>FDM </td> 
   <td>IU do agente</td> 
   <td>Imagens</td> 
  </tr>
  <tr>
   <td>Detalhes da Lista</td> 
   <td><p>Números da fatura</p> <p>Data da Cobrança</p> <p>Período de Faturamento</p> <p>Seu plano</p> </td> 
   <td><p>Valor para <strong>Seu plano </strong>campo</p> <p>Tabela - cliente</p> </td> 
   <td><p>Valores para os seguintes campos:</p> 
    <ul> 
     <li>Números da fatura</li> 
     <li>Data da Cobrança</li> 
     <li>Período de Faturamento</li> 
    </ul> <p> </p> </td> 
   <td>—</td> 
  </tr>
  <tr>
   <td>Detalhes do cliente</td> 
   <td><p>Local de fornecimento</p> <p>Código do Estado</p> <p>Número do celular</p> <p>Número de Contato Alternativo</p> <p>Número do relacionamento</p> <p>Número de Conexões</p> </td> 
   <td><p>Valores para os seguintes campos:</p> 
    <ul> 
     <li>Nome</li> 
     <li>Endereço</li> 
     <li>Número do celular</li> 
     <li>Número de Contato Alternativo</li> 
     <li>Número do relacionamento</li> 
    </ul> <p>Tabela - cliente</p> </td> 
   <td><p>Valores para os seguintes campos:</p> 
    <ul> 
     <li>Local de fornecimento</li> 
     <li>Código do Estado</li> 
     <li>Número de Conexões</li> 
    </ul> </td> 
   <td>--</td> 
  </tr>
  <tr>
   <td>Resumo da Lista</td> 
   <td><p>Saldo anterior</p> <p>Pagamentos</p> <p>Ajustamentos</p> <p>Encargos do período de faturamento atual</p> <p>Valor devido</p> <p>Data de vencimento</p> </td> 
   <td><p>Valor para a variável <strong>Encargos do período de faturamento atual </strong> campo</p> <p>Tabela - faturas</p> </td> 
   <td><p>Valores para os seguintes campos:</p> 
    <ul> 
     <li>Saldo anterior</li> 
     <li>Pagamentos</li> 
     <li>Ajustamentos</li> 
     <li>Valor devido</li> 
     <li>Data de vencimento</li> 
    </ul> </td> 
   <td>--</td> 
  </tr>
  <tr>
   <td>Resumo dos encargos</td> 
   <td><p>Encargos de Chamada</p> <p>Encargos de Chamada em Conferência</p> <p>Encargos SMS </p> <p>Tarifas de Internet Móvel</p> <p>Encargos de roaming nacional</p> <p>Encargos de roaming internacional</p> <p>Encargos de Serviços de Valor Acrescentado</p> <p>Encargos Totais</p> <p>TOTAL A PAGAR</p> <p>Condição no campo Encargos de Serviços de Valor Agregado</p> </td> 
   <td><p>Valores para os seguintes campos:</p> 
    <ul> 
     <li>Encargos de Chamada</li> 
     <li>Encargos de Chamada em Conferência</li> 
     <li>Encargos SMS </li> 
     <li>Tarifas de Internet Móvel</li> 
     <li>Encargos de roaming nacional</li> 
     <li>Encargos de roaming internacional</li> 
     <li>Encargos de Serviços de Valor Acrescentado</li> 
     <li>Encargos Totais (usagecharges campo calculado)</li> 
     <li>TOTAL PAGÁVEL (taxas de utilização calculadas, campo)</li> 
    </ul> <p>Tabela - faturas</p> </td> 
   <td>Nenhum campo</td> 
   <td>--</td> 
  </tr>
  <tr>
   <td>Chamadas discriminadas - Saída</td> 
   <td><p>Nomes das colunas:</p> 
    <ul> 
     <li>Data</li> 
     <li>Hora</li> 
     <li>Número</li> 
     <li>Duração</li> 
     <li>Encargos</li> 
    </ul> </td> 
   <td><p>Todos os valores</p> <p>Tabela - chamadas</p> </td> 
   <td>Nenhum campo</td> 
   <td>--</td> 
  </tr>
  <tr>
   <td>Pagar Agora</td> 
   <td>--</td> 
   <td>--</td> 
   <td>--</td> 
   <td>PagarAgora</td> 
  </tr>
  <tr>
   <td>Serviços de valor agregado</td> 
   <td>--</td> 
   <td>--</td> 
   <td>--</td> 
   <td>ValueAddedServices</td> 
  </tr>
 </tbody>
</table>
