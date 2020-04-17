---
title: Recursos obsoletos e removidos
seo-title: Recursos obsoletos e removidos
description: Notas de versão específicas de recursos obsoletos e removidos do Adobe Experience Manager 6.4.
seo-description: Notas de versão específicas de recursos obsoletos e removidos do Adobe Experience Manager 6.4.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 08cf51186b7e9ad62b92a266e95022d7d7a34a9b

---


# Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe avalia as funcionalidades do produto constantemente, para reinventar ou substituir recursos mais antigos por alternativas mais modernas, de forma a melhorar o valor do cliente em geral, sempre sob considerações cuidadosas de compatibilidade com versões anteriores.

As seguintes regras se aplicam para comunicar a remoção/substituição iminente das funcionalidades do AEM:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Enquanto obsoletas, as funcionalidade continuam disponíveis, mas não serão aprimoradas.
1. A remoção de funcionalidades obsoletas ocorrerá assim que possível na versão principal seguinte. A data definida para a remoção será anunciada.

Esse processo oferece ao usuário ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

## Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades que foram marcados como obsoleto no AEM 6.4. Normalmente, os recursos são, em primeiro lugar, marcados como obsoletos, com remoção planejada para uma versão futura, com uma alternativa fornecida.

Os clientes são instruídos a analisar se usam o recurso/funcionalidade em sua implementação no momento, bem como a planejar a alteração de sua implementação para usar a alternativa fornecida.

<table> 
 <tbody>
  <tr>
   <td>Área</td> 
   <td>Recurso</td> 
   <td>Substituição</td> 
  </tr>
  <tr>
   <td>Interface</td> 
   <td><p>A Adobe não planeja fazer aprimoramentos adicionais à interface do usuário clássica. O AEM 6.4 tem a interface do usuário clássica incluída, e os clientes que atualizam de versões anteriores podem continuar a usando da mesma forma. Observe que a interface do usuário clássica permanece completamente compatível mesmo enquanto obsoluta. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/caixa de entrada</li> 
     <li>/marcação</li> 
     <li>/cf# (Editor de páginas)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Recomenda-se que os clientes alternem para usar a nova interface do usuário do AEM.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td><p>A Adobe não planeja fazer mais aprimoramentos nos Componentes básicos listados abaixo. O AEM 6.4 inclui os componentes básicos, e os clientes que atualizam de versões anteriores podem continuar usando-os como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos. </p> 
    <ul> 
     <li>fundação/componentes/conta/nome da conta</li> 
     <li>fundação/componentes/conta/ações</li> 
     <li>fundação/componentes/conta/senha</li> 
     <li>base/componentes/conta/confirmação de solicitação</li> 
     <li>fundação/componentes/imagem adaptável</li> 
     <li>fundação/componentes/assetsharepage</li> 
     <li>fundação/componentes/navegação estrutural</li> 
     <li>fundação/componentes/formulário/cartão de crédito</li> 
     <li>fundação/componentes/listdren</li> 
     <li>fundação/componentes/login</li> 
     <li>fundação/componentes/logotipo</li> 
     <li>fundação/componentes/mobilefoter</li> 
     <li>fundação/componentes/mobileimage</li> 
     <li>fundação/componentes/mobilelist</li> 
     <li>fundação/componentes/mobilelogo</li> 
     <li>fundação/componentes/mobilereference</li> 
     <li>fundação/componentes/mobiletextimage</li> 
     <li>fundação/componentes/mobiletopnav</li> 
     <li>fundação/componentes/pesquisa</li> 
     <li>fundação/componentes/mapa do site</li> 
     <li>fundação/componentes/tabela</li> 
     <li>fundação/componentes/barra de ferramentas</li> 
     <li>fundação/componentes/topnav</li> 
     <li>base/componentes/informações do usuário</li> 
    </ul> </td> 
   <td>Recomenda-se que os clientes usem os componentes principais para projetos futuros. Os sites existentes não precisam ser alterados.</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td><p>A Adobe não planeja fazer mais aprimoramentos nos Componentes básicos listados abaixo. O AEM 6.4 inclui os componentes básicos, e os clientes que atualizam de versões anteriores podem continuar usando-os como estão. Observe que os componentes de base permanecem compatíveis ainda que obsoletos.</p> 
    <ul> 
     <li>fundação/componentes/tempo</li> 
    </ul> </td> 
   <td>A ponto de escrever, não se planeja fornecer um substituto.</td> 
  </tr>
  <tr>
   <td>Diretor do portal</td> 
   <td><p>O Portal Diretor é um conjunto de recursos que permite a hospedagem de conteúdo do AEM via Portlet em servidores de terceiros.</p> <p>A Adobe não planeja fazer mais aprimoramentos no recurso Portal Diretor no local listado abaixo. O AEM 6.4 tem o Portal Diretor incluído, e os clientes que atualizam de versões anteriores podem continuar usando como está. Observe que o Portal Direct permanece totalmente compatível enquanto está sendo descontinuado.</p> 
    <ul> 
     <li>/libs/portal/diretor</li> 
    </ul> </td> 
   <td>A ponto de escrever, não se planeja fornecer um substituto.</td> 
  </tr>
  <tr>
   <td>Componente do portlet</td> 
   <td><p>Os componentes do portlet em /base/componentes/portlet habilitam a hospedagem de portlets JSR no AEM como componentes.</p> <p>A Adobe não planeja fazer mais aprimoramentos no recurso Componente do portlet. O AEM 6.4 tem o componente Portlet incluído, e os clientes que atualizam de versões anteriores podem continuar usando-o como está. Observe que o componente Portlet permanece totalmente compatível enquanto está sendo descontinuado.</p> </td> 
   <td>A ponto de escrever, não se planeja fornecer um substituto.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>O suporte ao serviço Adobe Central Migration Bridge foi substituído, pois o produto Adobe Central não é mais compatível.</p> </td> 
   <td>Nenhuma substituição </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Uso obsoleto de JSONObject em Query e OperationOptions. As seguintes APIs estão obsoletas:
   <ul><li>setArguments(argumentos JSONObject)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, argumentos JSONObject</li><li>JSONObject getArguments()</li><li>void setArguments (argumentos JSONObject)</li></ul>
   </p> </td> 
   <td>Usar a API IValueMap </td> 
  </tr>
  <tr>
   <td>Ativos</td> 
   <td><p>A descarga de ativos foi substituída a partir do AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Recursos removidos {#removed-features}

Esta seção lista recursos e recursos que foram removidos do AEM 6.4. As versões anteriores tinham esses recursos marcados como obsoletos.

<table> 
 <tbody>
  <tr>
   <td><strong>Área</strong></td> 
   <td><strong>Recurso</strong></td> 
   <td><strong>Substituição</strong></td> 
  </tr>
  <tr>
   <td>Mapa de Atividades do Analytics</td> 
   <td>A versão do Mapa de Atividades incluída no AEM.</td> 
   <td>Devido a alterações de segurança na API do Adobe Analytics, não é mais possível usar a versão do Activity Map incluída no AEM.<br><br>O plug-in <a href="https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">Activity Map fornecido pelo Adobe Analytics</a> agora deve ser usado.</td> 
  </tr>
  <tr>
   <td>Componentes-formulários</td> 
   <td>Captcha<br /> de formulário (fundação/componentes/formulário/captcha)</td> 
   <td>Use o componente ReCaptcha pelo Google</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Apresentação de slides<br /> (base/componentes/apresentação de slides)</td> 
   <td>Nenhuma substituição</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Flash<br /> (fundação/componentes/flash)</td> 
   <td>Nenhuma substituição</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Remoção do suporte para arquivos SWF de reprodução no componente<br /> de vídeo (fundação/componentes/vídeo)</td> 
   <td>Use formatos de vídeo baseados em flash.</td> 
  </tr>
  <tr>
   <td>Componentes</td> 
   <td>Tabela<br /> do produto (commerce/components/product_table)</td> 
   <td>Nenhuma substituição</td> 
  </tr>
  <tr>
   <td>Gerenciamento de tarefas</td> 
   <td>Gerenciamento<br /> de Tarefa da interface clássica (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>Obsoleto desde 6.0. Use o novo gerenciamento de tarefas combinado com a interface do fluxo de trabalho.</td> 
  </tr>
  <tr>
   <td>Fluxo de trabalho</td> 
   <td>Interface de usuário de notificação usada entre 5.6 e 6.2<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>Caixa de entrada do fluxo de trabalho /aem/caixa de entrada</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>A exportação de PDF para o formato PDF/E-1 usando o Gerador de PDF foi removida.</td> 
   <td>O Gerador de PDF continua a oferecer suporte à exportação de PDF para formatos PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>O suporte para imagens nos fragmentos do documento foi removido. </td> 
   <td>As comunicações interativas fornecem a capacidade de usar imagens diretamente em canais impressos e da Web.<br /> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td> Atualização fora do local </td> 
   <td>O suporte para executar a atualização fora do local não está disponível <br/> </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Integrado para migrações TarMK para DocumentMK </td> 
   <td> Você pode exportar os dados de um sistema mais antigo e depois importá-los em um sistema de configuração recente. Para obter instruções detalhadas, consulte Formulários AEM em documentações de atualização do JEE <br/> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
 <td>AEM Forms no instalador JEE de 32 bits não disponível.</td> 
   <td>A Adobe parou de enviar o AEM Forms no instalador JEE de 32 bits. Você pode continuar usando o instalador de 64 bits para instalar o AEM Forms no JEE. </td>  
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Remoção do suporte para o uso de imagens DAM no Componente de fragmento do Documento.</td> 
    <td> Você pode usar o componente Imagem e Gráfico no canal de impressão da comunicação interativa. Se você estiver usando um componente de fragmento de documento adaptável em formulários adaptáveis, ele deixará de funcionar após a atualização para o AEM 6.4 Forms. </td>  
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Removido o recurso Documentos adaptáveis</td> 
   <td> Você pode usar o recurso de comunicações interativas para criar comunicações impressas e baseadas na Web. Se você usar Documentos adaptativos, instale o pacote de compatibilidade para continuar usando os documentos adaptáveis existentes<br/> </td> 
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Formulários AEM removidos na landing page específica JEE.</td> 
    <td>O AEM Forms na landing page JEE é substituído pela landing page AEM (/aem/start.html) </td>  
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Remoção do suporte para Captcha padrão</td> 
   <td>Use o serviço reCAPTCHA do Google.</td> 
  </tr>
  <tr>
   <td>Communities</td> 
   <td>O suporte para verificação do Captcha foi removido.</td> 
   <td>Use a integração de captcha personalizada (como reCAPTCHA do Google) para verificação.</td> 
  </tr>
 </tbody>
</table>

## Anúncio prévio da próxima versão {#pre-announcement-for-next-release}

Esta seção é usada para anunciar previamente as alterações na versão futura, que não estão obsoletas, mas afetará os clientes. Elas são fornecidas para propósito de planejamento.

<table> 
 <tbody>
  <tr>
   <td>Área<br /> </td> 
   <td>Recurso<br /> </td> 
   <td>Anúncio</td> 
  </tr>
  <tr>
   <td>Suporte ao navegador</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>O AEM 6.4 é a última versão que oferece suporte ao Microsoft Internet Explorer 11.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>Estrutura da interface do usuário</td> 
   <td>A Adobe está substituindo os componentes da interface do usuário Coral 2 em 2019. O AEM 6.4 é completamente baseado na interface do usuário Coral 3 (introduzida com o AEM 6.2). A Adobe recomenda que seus clientes e parceiros que criaram interfaces personalizadas com o Coral 2 as refatorizem para o Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
