---
title: Configuração de fontes de fallback
seo-title: Configuring fallback fonts
description: Saiba como configurar fontes de fallback.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---

# Configuração de fontes de fallback {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você pode configurar manualmente o arquivo FontManagerResources.properties para mapear as fontes padrão AEM formulários para fallback (ou substituto) se as fontes padrão não estiverem disponíveis no servidor. Esse arquivo de propriedade está localizado no arquivo adobe-fontmanager.jar.

>[!NOTE]
>
>A configuração de fonte de fallback também se aplica ao serviço de montagem.

1. Navegue até o adobe-livecycle-*[appserver]* Arquivo .ear no *[raiz do aem-forms]*/configurationManager/export, faça uma cópia de backup e descompacte o original.
1. Localize o arquivo adobe-fontmanager.jar e descompacte-o.
1. Localize o arquivo FontManagerResources.properties e abra-o em um editor de texto.
1. Modifique os locais e nomes das fontes Genéricas e de Fallback, conforme necessário, e salve o arquivo.

   As entradas de fonte no arquivo FontManagerResources.properties são relativas à variável *[raiz do aem-forms]* diretório /fonts. Se você especificar fontes que não são padrão AEM fontes de formulários, deverá instalar essas fontes dentro dessa estrutura de diretório (em um diretório existente ou em um recém-criado).

   >[!NOTE]
   >
   >Se a fonte ou fonte padrão especificada não contiver um caractere unicode específico ou se não estiver disponível, o caractere será retirado de uma fonte de fallback de acordo com a seguinte prioridade:

   * Fonte específica da localidade
   * Fonte RAIZ se a localidade não estiver definida
   * Fonte genérica, pesquisada por ordem definida na tabela de fallback

1. Reempacote o arquivo adobe-fontmanager.jar.
1. Reempacote o adobe-livecycle-*[appserver]* Arquivo .ear e, em seguida, reimplante-o manualmente ou executando o Configuration Manager.

>[!NOTE]
>
>Não use o Configuration Manager para reempacotar o adobe-livecycle-[appserver]Arquivo .ear porque substituirá suas modificações pelos valores padrão dos formulários AEM.
