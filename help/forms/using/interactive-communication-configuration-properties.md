---
title: Propriedades de configuração do Interative Communications
seo-title: Propriedades de configuração de comunicação interativa
description: Editar propriedades de configuração padrão para Comunicações interativas
seo-description: Editar propriedades de configuração padrão para Comunicações interativas
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 8%

---


# Propriedades de configuração de Comunicações interativas {#interactive-communications-configuration-properties}

Editar propriedades de configuração padrão para Comunicações interativas

As Comunicações interativas incluem propriedades que são configuradas automaticamente após a instalação do pacote do complemento [AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Os autores do Interative Communication podem editar essas propriedades de configuração padrão usando a página **Adobe Experience Manager Web Console Configuration**.

Abra a página **Configuração do Console da Web do Adobe Experience Manager** usando o seguinte URL:

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

As propriedades de configuração incluem:

* [Configuração de fragmentos de documento](#document-fragments-configuration)
* [Criar configuração de correspondência](#create-correspondence-configuration)
* [Configuração do canal Web de comunicação interativa e formulário adaptável](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuração de Tema de Canal da Web de Comunicação Adaptável e Interativa](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuração de Fragmentos de Documento {#document-fragments-configuration}

Toque em **Configuração de fragmentos de documento** na página **Configuração do console da Web do Adobe Experience Manager** para exibir as propriedades de configuração dos fragmentos de documento.

<table> 
 <tbody> 
  <tr> 
   <td>Propriedade</td> 
   <td>Descrição</td> 
   <td>Padrão</td> 
   <td>Valores aceitáveis</td> 
  </tr> 
  <tr> 
   <td>Formatos de exibição de dados</td> 
   <td>Formato de exibição específico de localidade para campos, variáveis e elementos de modelo de dados de formulário disponíveis ao criar uma Comunicação interativa para canais de impressão e da Web.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR e ja_JP</li> 
     <li>dateFormat = dd-MM-aaaa</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Recuo</td> 
   <td>A largura de uma única unidade de recuo aplicada ao texto em fragmentos de documento de lista.</td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Largura mínima dos números romanos</td> 
   <td>Largura mínima a ser aplicada ao campo de marcador ou número, ao usar números romanos em fragmentos de documento de lista. </td> 
   <td>12,7 mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Largura mínima do número</td> 
   <td>Largura mínima a ser aplicada ao campo de marcador ou número, ao usar listas numeradas além de números romanos em fragmentos de documento de lista.</td> 
   <td>8,0 mm</td> 
   <td>Número</td> 
  </tr> 
 </tbody> 
</table>

## Criar configuração de correspondência {#create-correspondence-configuration}

Toque em **Criar configuração de correspondência** na página **Configuração do console da Web Adobe Experience Manager** para exibir as propriedades de configuração da interface do usuário do agente.

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar conteúdo resolvido para edição | Marque a caixa de seleção para mostrar o conteúdo resolvido (valores reais em vez de espaços reservados) enquanto edita o módulo de texto na interface do agente. | Não selecionado | Não aplicável |
| Aplicar marca d&#39;água durante a visualização | Marque a caixa de seleção para aplicar marca d&#39;água ao Canal de impressão de comunicação interativa no modo de Visualização. | Não selecionado | Não aplicável |

## Configuração do canal Web de comunicação interativa e formulário adaptável {#adaptive-form-and-interactive-communication-web-channel-configuration}

Toque em **Adaptive Form and Interative Communication Web Channel Configuration** na página **Adobe Experience Manager Web Console Configuration** para exibir as propriedades de configuração do canal Web Adaptive Forms e Interative Communications. A tabela a seguir descreve as propriedades relacionadas às Comunicações interativas:

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar espaço reservado | Marque a caixa de seleção para ativar a exibição de espaços reservados para campos incluídos em formulários adaptáveis e Comunicações interativas. | Selecionado | Não aplicável |
| Máximo de entradas de cache | Defina o número máximo de formulários adaptáveis e Comunicações interativas que podem ser recuperadas usando a memória cache. | 100 | Número |
| Tornar o nome do arquivo exclusivo | Marque a caixa de seleção para ter nomes exclusivos para arquivos incluídos como anexos no Adaptive Forms e nas Comunicações interativas. | Não selecionado | Não aplicável |

## Configuração de Tema do Canal Web de Comunicação Ativa e Interativa {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Toque em **Adaptive Form and Interative Communication Web Channel Theme Configuration** na página **Adobe Experience Manager Web Console Configuration** para exibir as propriedades de configuração de temas de canal Web Adaptive Forms e Interative Communications.

<table> 
 <tbody> 
  <tr> 
   <td>Propriedade</td> 
   <td>Descrição</td> 
   <td>Padrão</td> 
   <td>Valores aceitáveis</td> 
  </tr> 
  <tr> 
   <td>Nome da lista de fontes</td> 
   <td>Lista de fontes disponíveis para uso ao criar o Adaptive Forms e o Interative Communications.</td> 
   <td><p>Geórgia</p> <p>Livro Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impacto</p> <p>Linotipo de Palatino</p> </td> 
   <td>Todas as fontes válidas do servidor Adobe</td> 
  </tr> 
 </tbody> 
</table>

