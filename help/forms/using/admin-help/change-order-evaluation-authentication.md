---
title: Alterar a ordem de avaliação para autenticação
seo-title: Alterar a ordem de avaliação para autenticação
description: 'É possível alterar a ordem na qual AEM formulários avalia vários provedores de autenticação. '
seo-description: 'É possível alterar a ordem na qual AEM formulários avalia vários provedores de autenticação. '
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Alterar a ordem de avaliação para autenticação {#change-the-order-of-evaluation-for-authentication}

Se você tiver configurado vários provedores de autenticação, poderá alterar a ordem em que AEM formulários os avaliam para autenticação. A ordem dos provedores de autenticação listados no arquivo config.xml determina a ordem de avaliação para autenticação.

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Configuração > Importar e exportar arquivos de configuração.
1. Para exportar a configuração atual para um arquivo, clique em Exportar e salve o arquivo de configuração em outro local.
1. Encontre o seguinte nó no arquivo:

   ```as3
    <node name="AuthSchemes"> 
        <map />  
            <node name="CertificateAuth"> 
                <map> 
                    <entry key="order" value="3" />  
                    <entry key="name" value="edc.server.auth.scheme.certificate" />  
                </map> 
        </node> 
        <node name="Kerberos"> 
            <map> 
                <entry key="kerberosSPN" value="defaultSPN" />  
                <entry key="order" value="1" />  
                <entry key="name" value="edc.server.auth.scheme.kerberos" />  
            </map> 
    </node>
   ```

   Em `<entry key="order" value="3" />`, edite o valor de cada nó para definir a ordem da avaliação de autenticação.

1. Para importar o arquivo atualizado, em Gerenciamento de usuários, clique em Configuração > Importar e exportar arquivos de configuração.
1. Clique em Procurar para localizar o arquivo, clique em Importar e em OK.

