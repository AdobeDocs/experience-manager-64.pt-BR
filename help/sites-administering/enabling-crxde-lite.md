---
title: Ativar o CRXDE Lite AEM
seo-title: Enabling CRXDE Lite in AEM
description: Saiba como ativar o CRXDE Lite no AEM.
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 4%

---

# Ativar o CRXDE Lite AEM{#enabling-crxde-lite-in-aem}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para garantir que as instalações de AEM sejam o mais seguras possível, a lista de verificação de segurança recomenda [desabilitando o WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) em ambientes de produção.

No entanto, o CRXDE Lite depende do `org.apache.sling.jcr.davex` para funcionar corretamente, de modo que a desativação do WebDAV também desativará o CRXDE Lite.

Quando isso acontecer, navegue para `https://serveraddress:4502/crx/de/index.jsp` exibirá um nó raiz vazio e todas as solicitações HTTP para recursos do CRXDE Lite falharão:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Embora essa recomendação tenha como objetivo reduzir ao máximo as superfícies de ataque, os administradores do sistema às vezes precisam acessar o CRXDE Lite para navegar pelo conteúdo ou depurar problemas em instâncias de produção.

Se estiver desativado, você pode ativar o CRXDE Lite seguindo o procedimento abaixo:

1. Vá para o console Componentes do OSGi em `http://localhost:4502/system/console/components`
1. Procure pelo seguinte componente:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Clique no ícone da chave inglesa ao lado dele para ver suas opções de configuração:

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Crie a seguinte configuração:

   * **Caminho raiz:** `/crx/server`
   * Marque a caixa abaixo **Usar URIs absolutos**.

1. Ao terminar de usar o CRXDE Lite, desative o WebDAV novamente.

Você também pode ativar o CRXDE Lite via cURL, executando este comando:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Outros recursos {#other-resources}

Para obter mais informações sobre AEM 6 recursos de segurança, consulte as seguintes páginas:

* [Lista de verificação de segurança AEM](/help/sites-administering/security-checklist.md)
* [Executando AEM no modo Pronto para produção](/help/sites-administering/production-ready.md)
