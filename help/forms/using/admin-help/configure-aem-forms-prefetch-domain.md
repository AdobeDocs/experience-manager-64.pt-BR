---
title: Configurar formulários AEM para obter previamente informações de domínio
seo-title: Configure AEM forms to prefetchdomain information
description: Configure AEM formulários para buscar previamente informações de domínio se você passar por um tempo de resposta mais lento devido a grupos profundamente aninhados ou se for membro de muitos grupos.
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: 6b431cbd-2cea-4ae2-ad26-587ba524d2f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Configurar formulários AEM para obter previamente informações de domínio {#configure-aem-forms-to-prefetchdomain-information}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os usuários podem experimentar um tempo de resposta mais lento se pertencerem a muitos grupos (por exemplo, 500 ou mais) ou se os grupos estiverem profundamente aninhados (por exemplo, 30 níveis). Se você estiver enfrentando esse problema, é possível configurar AEM formulários para buscar previamente informações de determinados domínios.

1. No console de administração, clique em **[!UICONTROL Configurações > Gerenciamento De Usuário > Configuração > Importar E Exportar Arquivos De Configuração]**.
1. Para exportar a configuração atual para um arquivo, clique em **[!UICONTROL Exportar]** e salve o arquivo de configuração em outro local.
1. Adicione o seguinte nó (marcado em negrito):

   ```as3
    <node name="UM"> 
    <map/>  
    <node name="PrincipalCache"> 
        <map> 
            <entry key="principalCacheSize" value="1000"/> 
            <entry key="principalCacheBatchFetchSize" value="10"/> 
            <entry key="rebuildCacheAfterSync" value="true /> 
            <entry key="enableFullPrefetch" value="false"/> 
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/> 
        <map> 
    </node> 
    <node name="APSAuditService">
   ```

   Neste exemplo, vários domínios são configurados para busca prévia. Os nomes de domínio são separados por um &quot;/&quot;. Isso é mostrado no exemplo acima com *Domain_Name1*, *Domain_Name2* e *Domain_Name3*.

1. Para importar o arquivo atualizado, em Gerenciamento de usuários, clique em **[!UICONTROL Configuração > Importar E Exportar Arquivos De Configuração]**.
1. Clique em **[!UICONTROL Procurar]** para localizar o arquivo, clique em Importar e, em seguida, clique em **[!UICONTROL OK]**.
