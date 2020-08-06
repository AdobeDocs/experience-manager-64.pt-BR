---
title: Propriedades de configuração do Interative Communications
seo-title: Propriedades de configuração do Interative Communication
description: Editar propriedades de configuração padrão para o Interative Communications
seo-description: Editar propriedades de configuração padrão para o Interative Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 7%

---


# Propriedades de configuração do Interative Communications {#interactive-communications-configuration-properties}

Editar propriedades de configuração padrão para o Interative Communications

O Interative Communications inclui propriedades que são configuradas automaticamente após a instalação do pacote complementar [do](/help/forms/using/installing-configuring-aem-forms-osgi.md) AEM Forms. Os autores do Interative Communication podem editar essas propriedades de configuração padrão usando a página Configuração **do Console da Web do** Adobe Experience Manager.

Abra a página Configuração **do console da Web do** Adobe Experience Manager usando o seguinte URL:

https://&lt;servidor>:&lt;porta>/&lt;contextPath>/system/console/configMgr

As propriedades de configuração incluem:

* [Configuração de fragmentos de Documento](#document-fragments-configuration)
* [Criar configuração de correspondência](#create-correspondence-configuration)
* [Configuração de formulário adaptável e de Canal da Web de comunicação interativa](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuração do tema do Canal da Web de formulário adaptável e comunicação interativa](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuração de fragmentos de Documento {#document-fragments-configuration}

Toque em Configuração **de fragmentos de** Documento na página Configuração **do console da Web do** Adobe Experience Manager para visualização das propriedades de configuração dos fragmentos de documento.

<table> 
 <tbody> 
  <tr> 
   <td>Propriedade</td> 
   <td>Descrição</td> 
   <td>Padrão</td> 
   <td>Valores aceitáveis</td> 
  </tr> 
  <tr> 
   <td>Formatos de Exibição de Dados</td> 
   <td>O formato de exibição específico da localidade para campos, variáveis e elementos de modelo de dados de formulário está disponível ao criar uma Comunicação Interativa para canais da Web e Impressos.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR e ja_JP</li> 
     <li>dateFormat = dd-MM-aaaa</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>--</p> </td> 
  </tr> 
  <tr> 
   <td>Recuo</td> 
   <td>A largura de uma unidade de recuo aplicada ao texto em fragmentos de documento de lista.</td> 
   <td>12.7mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Largura mínima dos números romanos</td> 
   <td>Largura mínima a ser aplicada ao campo de marcador ou número, ao usar números romanos em fragmentos de documento de lista. </td> 
   <td>12.7mm</td> 
   <td>Número</td> 
  </tr> 
  <tr> 
   <td>Largura mínima do número</td> 
   <td>Largura mínima a ser aplicada ao campo de marcador ou número, ao usar listas numeradas além de números romanos em fragmentos de documento de lista.</td> 
   <td>8.0mm</td> 
   <td>Número</td> 
  </tr> 
 </tbody> 
</table>

## Criar configuração de correspondência {#create-correspondence-configuration}

Toque em **Criar Configuração** de Correspondência na página Configuração **do Console da Web do** Adobe Experience Manager para visualização das propriedades de configuração da interface do usuário do agente.

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar conteúdo resolvido para edição | Marque a caixa de seleção para mostrar o conteúdo resolvido (valores reais em vez de espaços reservados) enquanto edita o módulo de texto na interface do agente. | Não selecionado | Não aplicável |
| Aplicar marca d&#39;água durante a pré-visualização | Marque a caixa de seleção para aplicar a marca d&#39;água ao Imprimir canal de comunicação interativa no modo de Pré-visualização. | Não selecionado | Não aplicável |

## Configuração de formulário adaptável e de Canal da Web de comunicação interativa {#adaptive-form-and-interactive-communication-web-channel-configuration}

Toque em Formulário **adaptável e Configuração** de Canal da Web de comunicação interativa na página Configuração **do console da Web da** Adobe Experience Manager para visualização das propriedades de configuração do canal da Web Adaptive Forms e Interative Communications. A tabela a seguir descreve as propriedades relacionadas ao Interative Communications:

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar espaço reservado | Marque a caixa de seleção para ativar a exibição de espaços reservados para campos incluídos em formulários adaptáveis e Comunicações interativas. | Selecionado | Não aplicável |
| Máximo de entradas de cache | Defina o número máximo de formulários adaptáveis e de Comunicações interativas que podem ser recuperados usando a memória cache. | 100 | Número |
| Tornar o nome do arquivo único | Marque a caixa de seleção para ter nomes exclusivos para arquivos incluídos como anexos no Adaptive Forms e no Interative Communications. | Não selecionado | Não aplicável |

## Configuração do tema do Canal da Web de formulário adaptável e comunicação interativa {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Toque em Formulário **adaptável e Configuração** de tema de Canal da Web de comunicação interativa na página Configuração **do console da Web da** Adobe Experience Manager para visualização das propriedades de configuração dos temas adaptáveis Forms e Interative Communications da Web.

<table> 
 <tbody> 
  <tr> 
   <td>Propriedade</td> 
   <td>Descrição</td> 
   <td>Padrão</td> 
   <td>Valores aceitáveis</td> 
  </tr> 
  <tr> 
   <td>Nome da Lista da fonte</td> 
   <td>Lista de fontes disponíveis para uso ao criar o Forms adaptativo e o Interative Communications.</td> 
   <td><p>Geórgia</p> <p>Livro Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impacto</p> <p>Linotipo de Palatino</p> </td> 
   <td>Todas as fontes válidas do servidor de Adobe</td> 
  </tr> 
 </tbody> 
</table>

