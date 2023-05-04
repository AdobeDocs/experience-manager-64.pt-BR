---
title: Configuração de endpoints remotos
seo-title: Configuring Remoting endpoints
description: Saiba como configurar endpoints remotos.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---

# Configuração de endpoints remotos {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Um terminal remoto permite que um aplicativo criado com o Flex chame o serviço usando (obsoleto para formulários AEM) AEM Remoção de formulários. Um terminal remoto é criado automaticamente para cada serviço ativado. Um destino Flex com o mesmo nome do ponto de extremidade é criado e os clientes Flex podem criar objetos remotos que apontam para esse destino para chamar operações no serviço relevante.

## Remoção das configurações de ponto de extremidade {#remoting-endpoint-settings}

**Método de autenticação de cliente Flex:** Determina o tipo de resposta que o servidor envia para o cliente quando o serviço chamado está habilitado para segurança, a operação invocada não oferece suporte a invocações anônimas e o cliente transmite nenhuma ou credenciais inválidas.
