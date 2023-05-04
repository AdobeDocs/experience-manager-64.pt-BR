---
title: Recursos obsoletos e removidos
description: Notas de versão específicas para recursos obsoletos e removidos do Adobe Experience Manager 6.4.
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1344'
ht-degree: 14%

---

# Recursos obsoletos e removidos {#deprecated-and-removed-features}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A Adobe avalia as funcionalidades do produto constantemente, para reinventar ou substituir recursos mais antigos por alternativas mais modernas, de forma a melhorar o valor do cliente em geral, sempre sob considerações cuidadosas de compatibilidade com versões anteriores.

Para comunicar a remoção/substituição iminente de recursos de AEM, as seguintes regras se aplicam:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora obsoletos, os recursos ainda estão disponíveis, mas não serão aprimorados.
1. A remoção de recursos obsoletos ocorrerá na seguinte versão principal, o mais tardar. A data de destino real para remoção será anunciada.

Esse processo oferece ao usuário ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

## Recursos obsoletos {#deprecated-features}

A tabela abaixo lista os recursos e funcionalidades que foram marcados como obsoletos no AEM 6.4. Geralmente, os recursos que estão planejados para serem removidos em uma versão futura são definidos como obsoletos primeiro, com uma alternativa fornecida.

Os clientes são instruídos a analisar se usam o recurso/funcionalidade em sua implementação no momento, bem como a planejar a alteração de sua implementação para usar a alternativa fornecida.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Área | Destaque | Substituição |
|---|---|---|
| Interface | O Adobe não planeja fazer aprimoramentos adicionais à interface clássica. O AEM 6.4 tem a interface do usuário clássica incluída e os clientes que atualizam de versões anteriores podem continuar a usá-la como estão. Observe que a interface do usuário clássica permanece totalmente compatível enquanto está obsoleta. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Editor de página) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Recomenda-se que os clientes alternem para usar a nova interface do usuário do AEM. |
| Componentes | O Adobe não planeja fazer aprimoramentos adicionais aos componentes de base listados abaixo. O AEM 6.4 tem os componentes de base incluídos e os clientes que atualizam de versões anteriores podem continuar a usá-los como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetssharepage </li> <li> foundation/components/breadcrumb </li> <li> fundação/componentes/formulário/cartão de crédito </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> fundação/componentes/logotipo </li> <li> foundation/components/mobilefoter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> fundação/componentes/tabela </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Recomenda-se que os clientes usem os Componentes principais para projetos futuros. Os sites existentes não precisam ser alterados. |
| Componentes | O Adobe não planeja fazer aprimoramentos adicionais aos componentes de base listados abaixo. O AEM 6.4 tem os componentes de base incluídos e os clientes que atualizam de versões anteriores podem continuar a usá-los como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos. <ul><li>fundação/componentes/tempo</li></ul> | O Adobe não planeja fornecer uma substituição. |
| Portal Director | O Portal Director é um conjunto de recursos que permite a hospedagem de conteúdo AEM via Portlet em servidores de terceiros. O Adobe não planeja fazer aprimoramentos adicionais ao recurso Director do Portal no local listado abaixo. AEM 6.4 tem o Portal Director incluído, e os clientes que atualizam de versões anteriores podem continuar usando como estão. Observe que o Portal Direct permanece totalmente compatível enquanto está obsoleto. <ul><li>/libs/portal/diretor</li></ul> | O Adobe não planeja fornecer uma substituição. |
| Componente portlet | Componentes do portlet em /foundation/components/portlet habilita a hospedagem de portlets JSR no AEM como componentes. O Adobe não planeja fazer aprimoramentos adicionais ao recurso Componente de portlet. AEM 6.4 inclui o Portlet Component e os clientes que atualizam de versões anteriores podem continuar usando como estão. Observe que o Portlet Component permanece totalmente compatível enquanto está obsoleto. | O Adobe não planeja fornecer uma substituição. |
| Forms | O suporte para o serviço Adobe Central Migration Bridge foi preterido, pois o produto Adobe Central não é mais compatível. | Sem substituição |
| Forms | Uso obsoleto de JSONObject em Query e OperationOptions. As seguintes APIs estão obsoletas: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Use o `IValueMap` API |
| Forms | Serviço Central Migration Bridge obsoleto. | Nenhuma substituição é oferecida. |
| Assets | A descarregamento de ativos foi descontinuada a partir do AEM 6.4. |  |
| Desenvolvedores | Biblioteca do cliente Lodash/underscore. O Adobe não planeja manter e atualizar a biblioteca do cliente Lodash/underscore que é enviada como parte da distribuição (Quickstart) | O Adobe recomenda que os clientes ainda solicitem o Lodash/underscore para que seu código o adicione à base de código do projeto. |

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

A tabela abaixo lista os recursos e funcionalidades removidos do AEM 6.4. As versões anteriores tiveram esses recursos marcados como obsoletos.

| Área | Destaque | Substituição |
|---|---|---|
| Integração com o [!DNL Experience Cloud] | Você pode sincronizar ativos com [!DNL Experience Cloud] usando uma configuração via [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] era anteriormente chamado [!DNL Adobe Marketing Cloud]. | Se você tiver consultas, entre em contato com [Suporte ao cliente Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;lang=pt-BR#support). |
| Activity Map do Analytics | A versão do Activity Map incluída no AEM. | Devido a alterações de segurança na API do Adobe Analytics, não é mais possível usar a versão do Activity Map incluída no AEM. O [Plug-in do Activity Map fornecido pelo Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=pt-BR) deve ser usada. |
| Componentes-Forms | Captcha de formulário (foundation/components/form/captcha) | Em vez disso, use o ReCaptcha do componente Google |
| Componentes | Apresentação de slides (foundation/components/slideshow) | Sem substituição |
| Componentes | Flash (foundation/components/flash) | Sem substituição |
| Componentes | Remoção do suporte para arquivos SWF de reprodução no componente de vídeo (foundation/components/video) | Use formatos de vídeo sem flash. |
| Componentes | Tabela de produtos (comércio/componentes/product_table) | Sem substituição |
| Gerenciamento de tarefas | Gerenciamento de tarefas da interface clássica (/libs/cq/taskmanagement/content/taskmanager.html) | Obsoleto desde a versão 6.0. Use o novo gerenciamento de tarefas combinado com a interface do usuário do workflow. |
| Fluxo de trabalho | Interface de notificação usada entre 5.6 e 6.2 (/libs/cq/workflow/content/notifications.html) | Caixa de entrada do fluxo de trabalho /aem/inbox |
| Forms | O formato Export PDF para PDF/E-1 usando PDF-Generator foi removido. | O PDF Generator continua a ser compatível com a exportação de formatos PDF para PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b. |
| Forms | O suporte para imagens dentro de fragmentos de documento foi removido. | As comunicações interativas fornecem a capacidade de usar imagens diretamente em canais de impressão e da Web. |
| Forms | Atualização de local | O suporte para executar a atualização fora do local não está disponível |
| Forms | Integrado do TarMK para migrações do DocumentMK | Você pode exportar os dados de um sistema mais antigo e depois importá-los em um sistema de configuração recente. Para obter instruções detalhadas, consulte AEM Forms nas documentações de atualização do JEE |
| Forms | O AEM Forms no instalador JEE de 32 bits não está disponível. | O Adobe interrompeu o envio do AEM Forms no instalador JEE de 32 bits. Você pode continuar usando o instalador de 64 bits para instalar o AEM Forms no JEE. |
| Forms | Remoção do suporte para uso de imagens DAM no Componente de fragmento do documento. | Você pode usar o componente Imagem e Gráfico no canal de impressão da comunicação interativa. Se você estiver usando o componente de fragmento do documento adaptável em formulários adaptáveis, ele deixará de funcionar após a atualização para AEM 6.4 Forms. |
| Forms | Remoção do recurso Documentos adaptativos | Você pode usar o recurso de comunicações interativas para criar comunicações impressas e baseadas na Web. Se você usar Documentos adaptativos, instale o pacote de compatibilidade para continuar usando os documentos adaptáveis existentes |
| Forms | Remoção do AEM Forms na página de aterrissagem específica do JEE. | O AEM Forms na página de aterrissagem JEE é substituído por AEM página de aterrissagem (/aem/start.html) |
| Forms | Remoção do suporte para Captcha padrão | Use o serviço reCAPTCHA da Google. |
| Forms | Remoção do suporte para campos flash no AEM Designer. AEM Designer não permite editar campos flash usados em um formulário. | Você pode usar AEM Designer lançado em uma versão anterior para editar esses formulários. |
| Communities | O suporte para verificação de Captcha foi removido. | Use a integração de captcha personalizada (como reCAPTCHA da Google) para verificação. |

## Pré-anúncio para a próxima versão {#pre-announcement-for-next-release}

A tabela abaixo fornece uma lista de alterações para a versão futura, que não estão obsoletas, mas podem afetar os clientes. Elas são fornecidas para fins de planejamento.

| Área | Destaque | Anúncio |
|---|---|---|
| Suporte para navegador | Microsoft Internet Explorer | AEM 6.4 é a última versão que oferece suporte ao Microsoft Internet Explorer 11. |
| Foundation | Estrutura da interface do usuário | O Adobe descontinuará os componentes da interface Coral 2 em 2019. O AEM 6.4 é completamente baseado na interface do usuário Coral 3 (introduzida com o AEM 6.2). O Adobe recomenda que seus clientes e parceiros que criaram interfaces de usuário personalizadas com o Coral 2 as refatorem para o Coral 3. O Adobe oferece uma ferramenta para converter caixas de diálogo do Coral 2 para o Coral 3 - [Leia mais.](/help/sites-developing/modernization-tools.md) |
