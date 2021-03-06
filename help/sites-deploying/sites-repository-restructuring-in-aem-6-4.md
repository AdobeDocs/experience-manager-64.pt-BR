---
title: Restruturação do repositório de sites no AEM 6.4
seo-title: Restruturação do repositório de sites no AEM 6.4
description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para Sites.
seo-description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para Sites.
uuid: 6dc5f8bd-1680-40af-9b8f-26c1f4bc3304
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 3eccb2d5-c325-43a6-9c03-5f93f7e30712
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 1%

---


# Restruturação do repositório de sites no AEM 6.4{#sites-repository-restructuring-in-aem}

Conforme descrito na página principal [Reestruturação do Repositório AEM 6.4](/help/sites-deploying/repository-restructuring.md), os clientes que atualizam para AEM 6.4 devem usar esta página para avaliar o esforço de trabalho associado às alterações do repositório que afetam a solução da AEM Sites. Algumas alterações exigem esforço de trabalho durante o processo de atualização do AEM 6.4, enquanto outras podem ser adiadas até uma atualização do 6.5.

**Com a atualização 6.4**

* [Segmentos ContextHub](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#contexthub-segments)

**Antes da atualização do 6.5**

* [Bibliotecas de clientes do Adobe Analytics](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#adobe-analytics-client-libraries)
* [Microsoft Word clássico para designs de página da Web](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#classic-microsoft-word-to-web-page-designs)
* [Configurações do emulador de dispositivo móvel](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#mobile-device-emulator-configurations)
* [Configurações do Blueprint do gerenciador de vários sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#multi-site-manager-blueprint-configurations)
* [Configurações de implementação do gerenciamento de vários sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#multi-site-manager-rollout-configurations)
* [Modelo de email de notificação de evento da página](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#page-event-notification-e-mail-template)
* [Andaime da página](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#page-scaffolding)
* [Grelha responsiva MENOR](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#responsive-grid-less)
* [Designs de modelo estático](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#static-template-designs)
* [Bibliotecas de clientes de integração do Adobe Search&amp;Promote](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#adobe-search-and-promote-integration-client-libraries)
* [Bibliotecas de clientes de integração da Adobe Target](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#adobe-target-integration-client-libraries)
* [Bibliotecas de clientes do WCM Foundation](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md#wcm-foundation-client-libraries)

## Com a atualização 6.4 {#with-upgrade}

### Segmentos ContextHub {#contexthub-segments}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/segmentation/contexthub</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/apps/settings/wcm/segments</code> </p> <p><code>/conf/settings/settings/wcm/segments</code> </p> <p><code>/conf/&lt;tenant&gt;/settings/wcm/segments</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Se qualquer segmento novo ou modificado do ContextHub for destinado a ser editado no controle de origem em vez de ser editado no AEM, ele deverá ser migrado para o novo local:</p> 
    <ol> 
     <li>Copie quaisquer segmentos do ContextHub novos ou modificados do local anterior para o novo local adequado (/<code>apps</code>, <code>/conf/global</code> ou <code>/conf/&lt;tenant&gt;</code>)</li> 
     <li>Atualize referências aos segmentos do ContextHub no local anterior para os segmentos do ContextHub migrados nos novos locais (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li> 
    </ol> <p>A consulta do QueryBuilder a seguir localiza todas as referências aos segmentos do ContextHub nos locais anteriores.<br /> <br /> <code class="code">path=/content
       property=cq:segments
       property.operation=like
       property.value=/etc/segmentation/contexthub/%</code><br /> <br /> Isso pode ser executado por  <a href="/help/sites-developing/querybuilder-api.md" target="_blank">AEM interface do usuário do QueryBuilder Debugger</a>. Observe que esta é uma consulta de percurso, portanto, não a execute em relação à produção e assegure-se de ajustar os limites de percurso conforme necessário.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>Os segmentos do ContextHub persistiram no local anterior são exibidos como somente leitura em <strong>AEM &gt; Personalização &gt; Públicos-alvo</strong>.</p> <p>Se os segmentos do ContextHub forem editáveis no AEM, eles deverão ser migrados para o novo local (<code>/conf/global</code> ou <code>/conf/&lt;tenant&gt;</code>). Qualquer novo segmento de Segmentos do ContentHub criado em AEM é mantido no novo local (<code>/conf/global</code> ou <code>/conf/&lt;tenant&gt;</code>).</p> <p>As Propriedades da página do AEM Sites permitem apenas que o Local anterior (<code>/etc</code>) ou um único novo local (<code>/apps</code>, <code>/conf/global</code> ou <code>/conf/&lt;tenant&gt;</code>) seja selecionado, portanto, os Segmentos do ContextHub devem ser migrados de acordo.</p> <p>Qualquer segmento do ContextHub não utilizado AEM sites de referência pode ser removido e não migrado para o Novo local:</p> 
    <ul> 
     <li>/etc/segmentation/geometrixx/</li> 
     <li>/etc/segmentation/geometrixx-outdoors</li> 
    </ul> <p>Observação: Se o ClientContext estiver em uso, é recomendável converter para o ContextHub.</p> </td> 
  </tr>
 </tbody>
</table>

## Antes da atualização do 6.5 {#prior-to-upgrade}

### Bibliotecas de clientes do Adobe Analytics {#adobe-analytics-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/sitecatalyst</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer uso personalizado dessas Bibliotecas de clientes deve fazer referência à Biblioteca de clientes por categoria e não por caminho:</p> 
    <ol> 
     <li>Qualquer referência à Biblioteca de clientes por caminho no Local anterior deve ser atualizada para usar <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM estrutura de referência da Biblioteca de clientes</a>.</li> 
     <li>Se AEM estrutura de referência da Biblioteca do cliente não puder ser usada, o caminho absoluto das Bibliotecas do cliente poderá ser referenciado por meio AEM servlet de Proxy da biblioteca do cliente.
      <ul> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/appmeasurement.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/plugins.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/tracking.js</code></li> 
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/util.js</code></li> 
      </ul> </li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>A edição dessas bibliotecas de clientes nunca foi suportada.</p> <p>Para obter as categorias da Biblioteca de clientes , visite cada nó <code>cq:ClientLIbraryFolder</code> por meio do CRXDELite e inspecione a propriedade categories .</p> 
    <ul> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/appmeasurement</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/plugins</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/tracking</code></li> 
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/util</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Microsoft Word clássico para designs de página da Web {#classic-microsoft-word-to-web-page-designs}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/designs/wordDesign</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/libs/settings/wcm/designs/wordDesign</code></p> <p><code>/apps/settings/wcm/designs/wordDesign</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Para quaisquer Designs gerenciados no SCM e não gravados em tempo de execução por meio de Caixas de Diálogo de Design.</p> 
    <ol> 
     <li>Copie os designs do local anterior para o novo local (<code>/apps</code>).</li> 
     <li>Converta qualquer CSS, JavaScript e recursos estáticos no Design em uma <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Biblioteca do cliente</a> com <code>allowProxy = true</code>.</li> 
     <li>Atualize referências para o Local anterior na propriedade cq:designPath.</li> 
     <li>Atualize quaisquer Páginas que façam referência ao Local anterior para usar a nova categoria Biblioteca de clientes (isso requer a atualização do código de implementação da Página).</li> 
     <li>Atualize AEM regras do Dispatcher para permitir o serviço de bibliotecas de clientes por meio do servlet proxy <code>/etc.clientlibs/</code>.</li> 
    </ol> <p>Para qualquer Designs que NÃO seja gerenciado no SCM e tempo de execução modificado por meio de Caixas de Diálogo de Design:</p> 
    <ul> 
     <li>Não mova os Designs que podem ser do autor para fora de <code>/etc</code>.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurações do emulador de dispositivo móvel {#mobile-device-emulator-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/mobile</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/libs/settings/mobile</code></p> <p><code>/apps/settings/mobile</code></p> <p><code>/conf/global/settings/mobile</code></p> <p><code>/conf/&lt;tenant&gt;/settings/mobile</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td>Qualquer nova configuração do emulador de dispositivo móvel deve ser migrada para o novo local.
    <ol> 
     <li>Copie quaisquer novas configurações do emulador de dispositivo móvel do local anterior para o novo local (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li> 
     <li>Para quaisquer páginas do AEM Sites que dependam dessas configurações do emulador de dispositivo móvel, atualize o <span class="code"> da página
       <code>
        jcr
       </code>
       Nó <code>
        :content
       </code></span>: <br /> <span class="code">[cq:Page]/jcr:content@cq:
       <code>
        deviceGroups
       </code> = String[ mobile/groups/responsive ]</span></li> 
     <li>Para quaisquer Modelos editáveis que dependam dessas configurações do emulador de dispositivo móvel, atualize os Modelos editáveis, apontando <span class="code">
       <code>
        cq
       </code>:
       <code>
        deviceGroups
       </code></span> para o novo local.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>A resolução Configurações do emulador de dispositivo móvel ocorre na seguinte ordem:</p> 
    <ol> 
     <li><code>/conf/&lt;tenant&gt;/settings/mobile</code></li> 
     <li><code>/conf/global/settings/mobile</code></li> 
     <li><code>/apps/settings/mobile</code></li> 
     <li><code>/libs/settings/mobile</code></li> 
     <li><code>/etc/mobile</code></li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### Configurações do Blueprint do gerenciador de vários sites {#multi-site-manager-blueprint-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/blueprints</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/apps/msm</code> (Configurações do Customer Blueprint)</p> <p><code>/libs/msm</code> (Configurações do Blueprint prontas para uso no Screens, Commerce)</p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer configuração do Blueprint do Gerenciador de Vários Sites nova ou modificada deve ser migrada para o Novo Local (<code>/apps</code>).</p> 
    <ol> 
     <li>Copie quaisquer configurações do blueprint do gerenciador de vários sites novas ou modificadas do local anterior para o novo local (<code>/apps</code>).</li> 
     <li>Remova todas as configurações do Blueprint do gerenciador de vários sites migradas do local anterior.</li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>Todas as AEM fornecidas Configurações do Blueprint do Gerenciador de Vários Sites existem no Novo Local em <code>/libs</code>.</p> <p>O conteúdo não faz referência às Configurações azuis do gerenciador de vários sites, portanto, não há referências de conteúdo para ajustar.</p> </td> 
  </tr>
 </tbody>
</table>

### Configurações de implantação do gerenciador de vários sites {#multi-site-manager-rollout-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/msm/rolloutConfigs</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/libs/msm/wcm/rolloutconfigs</code></p> <p><code>/apps/msm/wcm/rolloutconfigs</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Todas as configurações de implementação do gerenciamento de vários sites novas ou modificadas devem ser migradas para o novo local.</p> 
    <ol> 
     <li>Copie quaisquer configurações de implantação do gerenciamento de vários sites novas ou modificadas do local anterior para o novo local (<code>/apps</code>).</li> 
     <li>Atualize quaisquer referências nas Páginas AEM para Configurações de Implantação do Gerenciador de Vários Sites no Local Anterior, para apontar para seus homólogos em Novos Locais (<code>/libs</code> ou <code>/apps</code>).</li> 
    </ol> <p>Remova as configurações de implantação do gerenciador de vários sites migradas do local anterior.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>A não remoção das Configurações de implementação do gerenciamento de vários sites migradas do Local anterior resulta em opções de implementação duplicadas exibidas para AEM autores.</td> 
  </tr>
 </tbody>
</table>

### Modelo de email de notificação de evento da página {#page-event-notification-e-mail-template}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Os únicos novos modelos de email de notificação de evento de página compatíveis são oferecer suporte a novas localidades.</p> <p>A resolução do Modelo de email do evento da página ocorre na seguinte ordem:</p> 
    <ol> 
     <li><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></li> 
     <li><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></li> 
     <li><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></li> 
    </ol> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>Qualquer modelo de email de notificação de evento de página novo ou modificado deve ser migrado para o novo local em <code>/apps</code>:</p> 
    <ol> 
     <li>Copie qualquer modelo de email de notificação de evento de página novo ou modificado do local anterior para o novo local (<code>/apps</code>).</li> 
     <li>Remova qualquer modelo de email de notificação de evento de página migrado do local anterior.</li> 
    </ol> </td> 
  </tr>
 </tbody>
</table>

### Andaime da página {#page-scaffolding}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/scaffolding</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><p><span class="code">/libs/settings/
      <code>
       wcm
      </code>/templates-types/scaffolding/scaffolding</span></p> <p><span class="code">/apps/settings/
      <code>
       wcm
      </code>/templates-types/scaffolding/scaffolding</span></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td>O scaffolding criado no Local anterior usa a estrutura herdada Scaffolding e não pode ser migrado para o Novo local. Para alinhar com o novo local, qualquer scaffolding herdado deve ser redesenvolvido usando a estrutura Scaffolding compatível.</td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Grade Responsiva MENOR {#responsive-grid-less}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer referência ao Local anterior nos arquivos personalizados MENOS deve ser atualizada para ser importada do Novo local.</p> 
    <ul> 
     <li>Atualize qualquer arquivo LESS personalizado que faça referência a grid_base.less no Local anterior para fazer referência ao novo local.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>Fazer referência a um arquivo <code>grid_base.less</code> não existente resulta no funcionamento do Modo de layout da página e do Editor de modelo, além de uma interrupção do layout da página.</td> 
  </tr>
 </tbody>
</table>

### Designs de modelo estático {#static-template-designs}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/designs/&lt;custom-site&gt;</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/apps/settings/wcm/designs/&lt;custom-site&gt;</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Para quaisquer Designs gerenciados no SCM e não gravados em tempo de execução por meio de Caixas de Diálogo de Design.</p> 
    <ol> 
     <li>Copie os designs do local anterior para o novo local (<code>/apps</code>).</li> 
     <li>Converta qualquer CSS, JavaScript e recursos estáticos no Design em uma <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Biblioteca do cliente</a> com <code>allowProxy = true</code>.</li> 
     <li>Atualize referências ao Local anterior na propriedade <code>cq:designPath</code> por meio de <strong>AEM &gt; Sites &gt; Páginas personalizadas do site &gt; Propriedades da página &gt; Guia Avançado &gt; Campo de design</strong>.</li> 
     <li>Atualize quaisquer Páginas que façam referência ao Local anterior para usar a nova categoria Biblioteca de clientes (isso requer a atualização do código de implementação da Página).</li> 
     <li>Atualize AEM regras do Dispatcher para permitir o fornecimento de Bibliotecas de Clientes por meio do servlet proxy <code>/etc.clientlibs/</code>.</li> 
    </ol> <p>Para qualquer Designs que NÃO seja gerenciado no SCM e tempo de execução modificado por meio de Caixas de Diálogo de Design:</p> 
    <ul> 
     <li>Não mova os Designs que podem ser do autor para fora de <code>/etc</code>.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>A abordagem recomendada é criar AEM Sites e Páginas usando Modelos editáveis que usam Conteúdo e políticas de estrutura no lugar de Designs.</td> 
  </tr>
 </tbody>
</table>

### Bibliotecas de clientes de integração Adobe Search and Promote {#adobe-search-and-promote-integration-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/searchpromote</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer uso personalizado dessas Bibliotecas de clientes deve fazer referência à Biblioteca de clientes por categoria e não por caminho.</p> 
    <ol> 
     <li>Qualquer referência à Biblioteca de clientes por caminho no Local anterior deve ser atualizada para usar <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM estrutura de referência da Biblioteca de clientes</a>.</li> 
     <li>Se AEM estrutura de referência da Biblioteca do cliente não puder ser usada, o caminho absoluto das Bibliotecas do cliente poderá ser referenciado por meio AEM servlet de proxy da biblioteca do cliente:</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/cq/searchpromote/clientlibs/searchpromotei.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>A edição dessas bibliotecas de clientes nunca foi suportada.</p> <p>Para obter as categorias da Biblioteca de clientes , visite cada nó cq:ClientLIbraryFolder via CRXDELite e inspecione a propriedade categories :</p> 
    <ul> 
     <li><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Bibliotecas de clientes da integração do Adobe Target {#adobe-target-integration-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/clientlibs/foundation/target</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/cq/testandtarget/clientlibs/testandtarget</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer uso personalizado dessas Bibliotecas de clientes deve fazer referência à Biblioteca de clientes por categoria e não por caminho.</p> 
    <ol> 
     <li>Qualquer referência à Biblioteca de clientes por caminho no Local anterior deve ser atualizada para usar <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM estrutura de referência da Biblioteca de clientes</a>.</li> 
     <li>Se AEM estrutura de referência da Biblioteca do cliente não puder ser usada, o caminho absoluto das Bibliotecas do cliente poderá ser referenciado por meio AEM servlet de proxy da biblioteca do cliente:</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/testandtarget.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs-integration.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/init.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/mbox.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/parameters.js</code></li> 
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/util.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>A edição dessas bibliotecas de clientes nunca foi suportada.</p> <p>Para obter as categorias da Biblioteca de clientes , visite cada nó cq:ClientLIbraryFolder via CRXDELite e inspecione a propriedade categories :</p> 
    <ul> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/testandtarget</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs-integration</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/init</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/mbox</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/parameters</code></li> 
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/util</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

### Bibliotecas de clientes do WCM Foundation {#wcm-foundation-client-libraries}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><p><code>/etc/clientlibs/wcm/foundation</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/wcm/foundation/clientlibs</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Qualquer uso personalizado dessas Bibliotecas de clientes deve fazer referência à Biblioteca de clientes por categoria e não por caminho.</p> 
    <ol> 
     <li>Qualquer referência à Biblioteca de clientes por caminho no Local anterior deve ser atualizada para usar <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM estrutura de referência da Biblioteca de clientes</a>.</li> 
     <li>Se AEM estrutura de referência da Biblioteca do cliente não puder ser usada, o caminho absoluto das Bibliotecas do cliente poderá ser referenciado por meio AEM servlet de Proxy da biblioteca do cliente.</li> 
    </ol> 
    <ul> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/accessibility.css</code></li> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.css</code></li> 
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.js</code></li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td><p>A edição dessas bibliotecas de clientes nunca foi suportada.</p> <p>Para obter as categorias da Biblioteca de clientes , visite cada nó <code>cq:ClientLIbraryFolder</code> por meio do CRXDELite e inspecione a propriedade categories :</p> 
    <ul> 
     <li><code>/libs/wcm/foundation/clientlibs/accessibility</code></li> 
     <li><code>/libs/wcm/foundation/clientlibs/main</code></li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

