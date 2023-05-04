---
title: Restruturação do repositório Dynamic Media no AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Saiba como fazer as alterações necessárias para migrar para a nova estrutura de repositório no AEM 6.4 para Dynamic Media.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# Restruturação do repositório Dynamic Media no AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Conforme descrito no pai [Reestruturação do repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md) , os clientes que atualizam para o AEM 6.4 devem usar esta página para avaliar o esforço de trabalho associado às alterações do repositório que afetam a solução da Dynamic Media. Algumas alterações exigem esforço de trabalho durante o processo de atualização do AEM 6.4, enquanto outras podem ser adiadas até uma atualização do 6.5.

**Antes da atualização do 6.5**

* [Configurações personalizadas de codificação de vídeo adaptável](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configuração da nuvem Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configuração do Cloud Service Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - Configuração do YouTube Cloud Service](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
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
   <td><strong>Novas localizações</strong></td> 
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

### Configuração da nuvem do Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
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
   <td><strong>Novas localizações</strong></td> 
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

### Dynamic Media - Configuração do YouTube Cloud Service  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Localização anterior</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Novas localizações</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Orientação relativa à reestruturação</strong></td> 
   <td><p>1. Cancele a publicação de todos os vídeos do YouTube<br /> 2. Crie a configuração do YouTube usando a nova interface sensível ao toque (de <code>/conf</code>) incluindo copiar todos os Canais do local antigo<br /> 3. Publique todos os vídeos de volta no YouTube.</p> <p>Esse workflow resulta em novos URLs do YouTube. Se você não cancelar a publicação antes de criar uma nova configuração do TouchUI YouTube, você terá vários URLs do YouTube listados em Propriedades, pois os Canais recriados serão publicados novamente, se tiver a chance. Isso significa que você terá URLs inúteis listados em Propriedades.</p> </td> 
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
   <td><strong>Novas localizações</strong></td> 
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
   <td><strong>Novas localizações</strong></td> 
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
