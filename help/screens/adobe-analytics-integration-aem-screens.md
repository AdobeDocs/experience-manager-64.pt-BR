---
title: Integração do Adobe Analytics com o AEM Screens
seo-title: Integração do Adobe Analytics com o AEM Screens
description: Siga esta página para saber mais sobre a integração pronta do AEM Screens com o Adobe Analytics e fornecer uma prova de reprodução.
seo-description: Siga esta página para saber mais sobre a integração pronta do AEM Screens com o Adobe Analytics e fornecer uma prova de reprodução.
uuid: f4f71c85-ab6b-4e4d-94d3-5ba55ec0a246
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 2784b590-3402-492f-94a6-36fe16633e89
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Integração do Adobe Analytics com o AEM Screens{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.4.2 Feature Pack 2 e o AEM 6.3.3 Feature Pack 4.

>Para obter acesso a qualquer um desses Pacotes de recursos, entre em contato com o Suporte da Adobe e solicite acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.
>
Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Detalhes da arquitetura**
* **Configuração das propriedades**

## Visão geral {#overview}

***O AEM Screens*** aproveita o Adobe Analytics e, com isso, você pode obter algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo exibido no local com outras fontes de dados.

O AEM Screens fornece uma integração imediata com o Adobe Analytics e fornece uma prova de reprodução.

Esta seção descreve a seguinte funcionalidade envolvida na conexão de um projeto do AEM Screens com o Adobe Analytics:

* Permite relatórios de prova de reprodução por dispositivo
* Permite relatório de comprovação de reprodução por ativo
* Garante que todos os eventos do player sejam capturados e com carimbo de data e hora
* Garante que todos os eventos do player sejam armazenados localmente se a reprodução não estiver conectada a uma rede

Assim, a integração do Adobe Analytics com o AEM Screens impõe os seguintes *objetivos*:

* Ativar o ROI das implementações de sinalização digital
* Integrar o Analytics como base para a futura ativação de coletar e analisar informações de uso

## Detalhes da arquitetura {#architectural-details}

O diagrama de arquitetura a seguir explica a integração do Adobe Analytics com o AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Ativação do Adobe Analytics no AEM Screens {#enabling-adobe-analytics-in-aem-screens}

As configurações do Adobe Analytics podem ser definidas no console OSGi.

Navegue até Configuração **do console da Web do** Adobe Experience Manager para configurar o Adobe Analytics para telas AEM, como mostrado na figura abaixo:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

### Configuração das propriedades {#configuring-the-properties}

>[!CAUTION]
Antes de configurar as propriedades, entre em contato com seu Gerente de relacionamento da Adobe para criar um ticket para obter uma chave **de API do** Analytics e um projeto **do** Analytics para uso com o AEM Screens.

A tabela a seguir destaca as propriedades com sua descrição para configurar o Adobe Analytics para AEM Screens:

<table> 
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td><strong>URL do Analytics</strong></td> 
   <td>URL para publicar dados de análise do player<br /> </td> 
  </tr>
  <tr>
   <td><strong>Chave da API do Analytics</strong></td> 
   <td>Chave da API para autenticação no servidor do Adobe Analytics (fornecida pelo Gerenciador de contas)</td> 
  </tr>
  <tr>
   <td><strong>Projeto do Analytics</strong></td> 
   <td>Projeto do AEM Screens configurado em sua análise para receber dados (fornecido pelo Gerente de contas)</td> 
  </tr>
  <tr>
   <td><strong>Autor</strong></td> 
   <td><p>Estágio ou ambiente de produção.</p> <p><em>
   Para desenvolvimento/estágio</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>For Production</em> - https://cc-api-data.adobe.io/ingest/</p> </td> 
  </tr>
  <tr>
   <td><strong>Frequência de envio do Analytics</strong></td> 
   <td>Frequência em minutos para enviar dados de análise dos players. Por padrão, é definido como 15 minutos.</td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
Por padrão, a **Frequência de envio do Analytics **é de 15 minutos.

#### Usar o Adobe Analytics Service no AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Esse cenário chama a API do Analytics por meio de chamadas REST de um serviço de análise no firmware e nos componentes de núcleo de telas de instrumentos para criar e enviar explicitamente eventos específicos para um caso de uso específico e permitir a extensibilidade em que qualquer mensagem personalizada pode ser enviada ao Analytics a partir de um canal desenvolvido personalizado.

Os eventos do Analytics são armazenados offline no indexedDB e posteriormente são separados e enviados para a nuvem.

>[!NOTE]
Para saber mais sobre o ***Sequenciamento*** e o Modelo de dados padrão para eventos ***, consulte*** Configuração do Adobe Analytics para telas [](configuring-adobe-analytics-aem-screens.md) AEM na seção do desenvolvedor do AEM Screens.

