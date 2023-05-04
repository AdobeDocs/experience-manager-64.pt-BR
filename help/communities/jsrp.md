---
title: JSRP - Provedor de recursos de armazenamento JCR
seo-title: JSRP - JCR Storage Resource Provider
description: O JSRP geralmente é mais adequado para ambientes de demonstração ou desenvolvimento de uma instância de publicação e uma instância de autor
seo-description: JSRP is generally best suited for demonstration or development environments of one publish instance and one author instance
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
role: Admin
exl-id: 73c59497-43fe-4e15-afda-e3cf5264696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---

# JSRP - Provedor de recursos de armazenamento JCR {#jsrp-jcr-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Sobre o JSRP {#about-jsrp}

Quando o AEM Communities usa o JSRP como sua opção de armazenamento (o padrão), o conteúdo da comunidade é armazenado no JCR e o conteúdo gerado pelo usuário (UGC) é acessível somente a partir da instância de autor ou publicação na qual foi publicado.

Devido à simplicidade da implantação, o JSRP geralmente é mais adequado para ambientes de demonstração ou desenvolvimento de uma instância de publicação e uma instância de autor.

Consulte também [Características das opções de SRP](working-with-srp.md#characteristics-of-srp-options) e [Topologias recomendadas](topologies.md).

## Configuração {#configuration}

### Selecione JSRP {#select-jsrp}

Por padrão, o JSRP é a opção de armazenamento para UGC.

O [Console de configuração de armazenamento](srp-config.md) permite a seleção da configuração de armazenamento padrão, que identifica qual implementação do SRP usar.

No ambiente de criação, para acessar o console Configuração de armazenamento

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Configuração de armazenamento]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Selecionar **[!UICONTROL Provedor de recursos de armazenamento JCR (JSRP)]**
* Selecione **[!UICONTROL Enviar]**

### Publicar a configuração {#publishing-the-configuration}

Embora o JSRP seja a configuração padrão, para garantir que a configuração idêntica seja definida no ambiente de publicação:

* No autor:

   * Na navegação global: **[!UICONTROL Ferramentas > Implantação > Replicação]**
   * Selecionar **[!UICONTROL Ativar árvore]**
   * **[!UICONTROL Caminho de início]**:

      * Navegue até `/conf/global/settings/community/srpc/`
   * Selecionar **[!UICONTROL Ativar]**


## Gerenciar dados do usuário {#managing-user-data}

Para obter informações sobre *usuários*, *perfis de usuário* e *grupos de usuários*, normalmente inserido no ambiente de publicação, visite

* [Sincronização de usuários](sync.md)
* [Gerenciar usuários e grupos de usuários](users.md)

## Resolução de problemas {#troubleshooting}

### UGC não visível no JCR {#ugc-not-visible-in-jcr}

Verifique se o JSRP foi configurado para ser o provedor padrão verificando a configuração da opção de armazenamento. Por padrão, o provedor de recursos de armazenamento é o JSRP.

Em todas as instâncias de criação e publicação AEM, revise o console Configuração de armazenamento ou verifique o repositório AEM:

* no JCR, se [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Não contém um [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) , significa que o provedor de armazenamento é JSRP
   * Se o nó srpc existir e contiver nó [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration), as propriedades da configuração padrão devem definir o JSRP como o provedor padrão

### UGC não visível na instância do autor {#ugc-not-visible-on-author-instance}

Isso não é um erro. Uma característica do JSRP é que o conteúdo da comunidade inserido no ambiente de publicação só estará visível no ambiente de publicação.

### UGC não visível na instância de publicação {#ugc-not-visible-on-publish-instance}

Se uma única instância de publicação ou se um cluster de publicação estiver implantado, siga as instruções para [UGC não visível no JCR](#ugc-not-visible-in-jcr).

Se um farm de publicação for implantado, uma característica do JSRP é que o conteúdo da comunidade só será visível na instância de publicação em que foi publicado.

Para que o UGC fique visível de qualquer instância de publicação, é necessário um cluster de publicação.
