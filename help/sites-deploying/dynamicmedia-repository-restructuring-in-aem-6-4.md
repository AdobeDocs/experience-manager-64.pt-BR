---
title: Reestruturação do repositório do Dynamic Media no AEM 6.4
seo-title: Reestruturação do repositório do Dynamic Media no AEM 6.4
description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura do repositório no AEM 6.4 para o Dynamic Media.
seo-description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura do repositório no AEM 6.4 para o Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
translation-type: tm+mt
source-git-commit: 5dce4bcf4b10cce65798fd142a3eeb1956caf726
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 4%

---


# Reestruturação do repositório do Dynamic Media no AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

Conforme descrito na página principal [Reestruturação do repositório AEM 6.4](/help/sites-deploying/repository-restructuring.md) , os clientes que atualizam para a AEM 6.4 devem usar esta página para avaliar o esforço de trabalho associado às alterações no repositório que afetam a Solução de Dynamic Media. Algumas alterações exigem esforço de trabalho durante o processo de atualização do AEM 6.4, enquanto outras podem ser adiadas até uma atualização do 6.5.

**Antes da atualização do 6.5**

* [Configurações personalizadas de codificação de vídeo adaptável](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configuração da nuvem do Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configuração de Cloud Service do Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - Configuração de Cloud Service do YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Misc](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Antes da atualização do 6.5 {#prior-to-upgrade}

### Configurações personalizadas de codificação de vídeo adaptável  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Você pode executar o seguinte script de migração para migrar para o novo local:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Como alternativa, você pode editar a configuração AEM interface do usuário e as alterações serão salvas no novo local.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media (DMS7) Cloud configuration {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>O cliente pode executar um script de migração neste local:<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Reinicie o pacote OSGi do Dynamic Media.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

### Configuração do Cloud Service do Dynamic Media (DM Hybrid) {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>Você pode executar o script de migração abaixo para alinhar ao modelo mais recente:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - Configuração do Cloud Service do YouTube  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>1. Cancele a publicação de todos os vídeos do YouTube<br /> 2. Crie a configuração do YouTube usando a nova interface do usuário do Touch (de <code>/conf</code>), incluindo a cópia de todos os Canais do local<br /> antigo 3. Publique todos os vídeos no YouTube.</p> <p>Esse fluxo de trabalho resulta em novos URLs do YouTube. Se você não cancelar a publicação antes de criar uma nova configuração do YouTube para TouchUI, você terá vários URLs do YouTube listados em Propriedades, pois os Canais recriados serão publicados novamente, se houver chance. Isso significa que você terá URLs inúteis listados em Propriedades.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Misc {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>O cliente pode executar o script de migração abaixo.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>Como alternativa, você pode editar a configuração AEM interface do usuário e as alterações serão salvas no novo local.</p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Novos locais</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>O cliente pode executar o script de migração abaixo.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Notas</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

