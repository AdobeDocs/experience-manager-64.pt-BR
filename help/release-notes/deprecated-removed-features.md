---
title: Recursos obsoletos e removidos
description: Notas de versão específicas de recursos obsoletos e removidos do Adobe Experience Manager 6.4.
translation-type: tm+mt
source-git-commit: 543f66c760d7b25681a79d5df3d8ab6e8c0b2f47
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 27%

---


# Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe avalia as funcionalidades do produto constantemente, para reinventar ou substituir recursos mais antigos por alternativas mais modernas, de forma a melhorar o valor do cliente em geral, sempre sob considerações cuidadosas de compatibilidade com versões anteriores.

As seguintes regras se aplicam para comunicar a remoção/substituição iminente das funcionalidades do AEM:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora obsoletos, os recursos ainda estão disponíveis, mas não serão aprimorados.
1. A remoção de funcionalidades obsoletas ocorrerá assim que possível na versão principal seguinte. A data definida para a remoção será anunciada.

Esse processo oferece ao usuário ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

## Recursos obsoletos {#deprecated-features}

The table below lists features and capabilities that have been marked as deprecated with AEM 6.4. Generally, features that are planned to be removed in a future release are set to deprecated first, with an alternative provided.

Os clientes são instruídos a analisar se usam o recurso/funcionalidade em sua implementação no momento, bem como a planejar a alteração de sua implementação para usar a alternativa fornecida.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Área | Recurso | Substituição |
|---|---|---|
| Interface | A Adobe não planeja fazer aprimoramentos adicionais à interface do usuário clássica. O AEM 6.4 tem a interface do usuário clássica incluída, e os clientes que atualizam de versões anteriores podem continuar a usando da mesma forma. Observe que a interface do usuário clássica permanece completamente compatível mesmo enquanto obsoluta. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Editor de página) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Recomenda-se que os clientes alternem para usar a nova interface do usuário AEM. |
| Componentes | O Adobe não planeja fazer mais aprimoramentos nos Componentes básicos listados abaixo. AEM 6.4 inclui os componentes básicos, e os clientes que atualizam de versões anteriores podem continuar a usá-los como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos. <ul> <li> fundação/componentes/conta/nome da conta </li> <li> fundação/componentes/conta/ações </li> <li> fundação/componentes/conta/senha </li> <li> base/componentes/conta/confirmação de solicitação </li> <li> fundação/componentes/imagem adaptável </li> <li> fundação/componentes/assetsharepage </li> <li> fundação/componentes/navegação estrutural </li> <li> fundação/componentes/formulário/cartão de crédito </li> <li> fundação/componentes/listdren </li> <li> fundação/componentes/login </li> <li> fundação/componentes/logotipo </li> <li> fundação/componentes/mobilefoter </li> <li> fundação/componentes/mobileimage </li> <li> fundação/componentes/mobilelist </li> <li> fundação/componentes/mobilelogo </li> <li> fundação/componentes/mobilereference </li> <li> fundação/componentes/mobiletextimage </li> <li> fundação/componentes/mobiletopnav </li> <li> fundação/componentes/pesquisa </li> <li> fundação/componentes/mapa do site </li> <li> fundação/componentes/tabela </li> <li> fundação/componentes/barra de ferramentas </li> <li> fundação/componentes/topnav </li> <li> base/componentes/informações do usuário </li> </ul> | Recomenda-se que os clientes usem os componentes principais para projetos futuros. Os sites existentes não precisam ser alterados. |
| Componentes | O Adobe não planeja fazer mais aprimoramentos nos Componentes básicos listados abaixo. AEM 6.4 inclui os componentes básicos, e os clientes que atualizam de versões anteriores podem continuar a usá-los como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos. <ul><li>fundação/componentes/tempo</li></ul> | O Adobe não pretende fornecer uma substituição. |
| Portal Director | O Portal Director é um conjunto de recursos que permite a hospedagem de conteúdo AEM via Portlet em servidores de terceiros. O Adobe não pretende realizar mais melhorias no recurso do Portal Director no local listado abaixo. AEM 6.4 inclui o Portal Director e os clientes que atualizam de versões anteriores podem continuar usando como estão. Observe que o Portal Direct permanece totalmente compatível enquanto está sendo descontinuado. <ul><li>/libs/portal/diretor</li></ul> | O Adobe não pretende fornecer uma substituição. |
| Componente do portlet | Os componentes do portlet em /base/componentes/portlet habilitam a hospedagem de portlets JSR em AEM como componentes. O Adobe não planeja fazer mais aprimoramentos no recurso Componente do portlet. AEM 6.4 inclui o Portlet Component, e os clientes que atualizam de versões anteriores podem continuar usando como está. Observe que o componente Portlet permanece totalmente compatível enquanto está sendo descontinuado. | O Adobe não pretende fornecer uma substituição. |
| Forms | O suporte para o serviço Adobe Central Migration Bridge foi substituído porque o produto Adobe Central não é mais compatível. | Nenhuma substituição |
| Forms | Uso obsoleto de JSONObject em Query e OperationOptions. As seguintes APIs estão obsoletas: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Usar a `IValueMap` API |
| Forms | Serviço da Central Migration Bridge obsoleto. | Nenhuma substituição é oferecida. |
| Ativos | A descarga de ativos foi substituída a partir do AEM 6.4. |  |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## Recursos removidos {#removed-features}

A tabela abaixo lista recursos e recursos que foram removidos da AEM 6.4. As versões anteriores tinham esses recursos marcados como obsoletos.

| Área | Recurso | Substituição |
|---|---|---|
| Analytics Activity Map | A versão do Activity Map está inclusa no AEM. | Devido a alterações de segurança na API do Adobe Analytics, não é mais possível usar a versão do Activity Map incluída no AEM. The [ActivityMap plug-in provided by Adobe Analytics](https://docs.adobe.com/content/help/br/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used. |
| Componentes-Forms | Captcha de formulário (fundação/componentes/formulário/captcha) | Use o componente ReCaptcha pelo Google |
| Componentes | Apresentação de slides (base/componentes/apresentação de slides) | Nenhuma substituição |
| Componentes | Flash (fundação/componentes/flash) | Nenhuma substituição |
| Componentes | Remoção do suporte para arquivos SWF de reprodução no componente de vídeo (fundação/componentes/vídeo) | Use formatos de vídeo baseados em flash. |
| Componentes | Tabela do produto (commerce/components/product_table) | Nenhuma substituição |
| Gerenciamento de tarefas | Gerenciamento de Tarefa da interface clássica (/libs/cq/taskmanagement/content/taskmanager.html) | Obsoleto desde 6.0. Use o novo gerenciamento de tarefas combinado com a interface do fluxo de trabalho. |
| Fluxo de trabalho | Interface de notificação usada entre 5.6 e 6.2 (/libs/cq/workflow/content/notifications.html) | Caixa de entrada do fluxo de trabalho /aem/inbox |
| Forms | O formato Export PDF para PDF/E-1 usando o Gerador de PDF foi removido. | O Gerador de PDF continua a oferecer suporte à exportação de PDF para formatos PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b. |
| Forms | O suporte para imagens nos fragmentos do documento foi removido. | As comunicações interativas fornecem a capacidade de usar imagens diretamente em canais impressos e da Web. |
| Forms | Atualização fora do local | O suporte para executar a atualização fora do local não está disponível |
| Forms | Integrado para migrações TarMK para DocumentMK | Você pode exportar os dados de um sistema mais antigo e depois importá-los em um sistema de configuração recente. Para obter instruções detalhadas, consulte AEM Forms em documentações de atualização do JEE |
| Forms | AEM Forms no instalador JEE de 32 bits não disponíveis. | O Adobe parou de enviar AEM Forms no instalador JEE de 32 bits. Você pode continuar usando o instalador de 64 bits para instalar AEM Forms no JEE. |
| Forms | Remoção do suporte para o uso de imagens DAM no Componente de fragmento do Documento. | Você pode usar o componente Imagem e Gráfico no canal de impressão da comunicação interativa. Se você estiver usando um componente de fragmento de documento adaptável em formulários adaptáveis, ele deixará de funcionar após a atualização para AEM 6.4 Forms. |
| Forms | Removido o recurso Documentos adaptáveis | Você pode usar o recurso de comunicações interativas para criar comunicações impressas e baseadas na Web. Se você usar Documentos adaptativos, instale o pacote de compatibilidade para continuar usando os documentos adaptáveis existentes |
| Forms | AEM Forms removidos na landing page específica de JEE. | AEM Forms na landing page JEE são substituídas por AEM landing page (/aem/start.html) |
| Forms | Remoção do suporte para Captcha padrão | Use o serviço reCAPTCHA do Google. |
| Forms | Remoção do suporte para campos flash no AEM Designer. AEM Designer não permite a edição de campos flash usados em um formulário. | Você pode usar AEM Designer lançado para uma versão anterior para editar esses formulários. |
| Communities | O suporte para verificação do Captcha foi removido. | Use a integração de captcha personalizada (como reCAPTCHA do Google) para verificação. |

## Anúncio prévio da próxima versão {#pre-announcement-for-next-release}

A tabela abaixo fornece uma lista de alterações para versões futuras, que não estão obsoletas, mas podem afetar os clientes. Elas são fornecidas para propósito de planejamento.

| Área | Recurso | Anúncio |
|---|---|---|
| Suporte ao navegador | Microsoft Internet Explorer | AEM 6.4 é a última versão que suporta o Microsoft Internet Explorer 11. |
| Foundation | Estrutura da interface do usuário | O Adobe está substituindo os componentes da interface do usuário Coral 2 em 2019. AEM 6.4 é completamente baseado na interface do usuário Coral 3 (apresentada com AEM 6.2). A Adobe recomenda que seus clientes e parceiros que criaram interfaces de usuário personalizadas com a Coral 2 as refatorizem para a Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/dialog-conversion.md). |
