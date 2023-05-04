---
title: Propriedades de configuração do Interative Communications
seo-title: Interactive Communication configuration properties
description: Editar propriedades de configuração padrão para Comunicações interativas
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 8%

---

# Propriedades de configuração do Interative Communications {#interactive-communications-configuration-properties}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Editar propriedades de configuração padrão para Comunicações interativas

O Interative Communications inclui propriedades configuradas automaticamente após a instalação do [Complemento do AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) pacote. Os autores do Interative Communication podem editar essas propriedades de configuração padrão usando o **Configuração do Console da Web do Adobe Experience Manager** página.

Abra o **Configuração do Console da Web do Adobe Experience Manager** página usando o seguinte URL:

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

As propriedades de configuração incluem:

* [Configuração de fragmentos de documento](#document-fragments-configuration)
* [Criar configuração de correspondência](#create-correspondence-configuration)
* [Configuração do canal Web de comunicação interativa e formulário adaptável](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuração de Tema de Canal da Web de Comunicação Adaptável e Interativa](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuração de fragmentos de documento {#document-fragments-configuration}

Toque **Configuração de fragmentos de documento** no **Configuração do Console da Web do Adobe Experience Manager** para exibir as propriedades de configuração dos fragmentos de documento.

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

Toque **Criar configuração de correspondência** no **Configuração do Console da Web do Adobe Experience Manager** para exibir as propriedades de configuração da interface do usuário do agente.

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar conteúdo resolvido para edição | Marque a caixa de seleção para mostrar o conteúdo resolvido (valores reais em vez de espaços reservados) enquanto edita o módulo de texto na interface do agente. | Não selecionado | Não aplicável |
| Aplicar marca d&#39;água durante a visualização | Marque a caixa de seleção para aplicar marca d&#39;água ao Canal de impressão de comunicação interativa no modo de Visualização. | Não selecionado | Não aplicável |

## Configuração do canal Web de comunicação interativa e formulário adaptável {#adaptive-form-and-interactive-communication-web-channel-configuration}

Toque **Configuração do canal Web de comunicação interativa e formulário adaptável** no **Configuração do Console da Web do Adobe Experience Manager** para exibir as propriedades de configuração do canal da Web Adaptive Forms e Interative Communications. A tabela a seguir descreve as propriedades relacionadas às Comunicações interativas:

| Propriedade | Descrição | Padrão | Valores aceitáveis |
|---|---|---|---|
| Mostrar espaço reservado | Marque a caixa de seleção para ativar a exibição de espaços reservados para campos incluídos em formulários adaptáveis e Comunicações interativas. | Selecionado | Não aplicável |
| Máximo de entradas de cache | Defina o número máximo de formulários adaptáveis e Comunicações interativas que podem ser recuperadas usando a memória cache. | 100 | Número |
| Tornar o nome do arquivo exclusivo | Marque a caixa de seleção para ter nomes exclusivos para arquivos incluídos como anexos no Adaptive Forms e nas Comunicações interativas. | Não selecionado | Não aplicável |

## Configuração de Tema de Canal da Web de Comunicação Adaptável e Interativa {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Toque **Configuração de Tema de Canal da Web de Comunicação Adaptável e Interativa** no **Configuração do Console da Web do Adobe Experience Manager** para visualizar as propriedades de configuração dos temas do canal da Web Adaptive Forms e Interative Communications.

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
