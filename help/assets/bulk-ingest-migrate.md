---
title: Instalação do Feature Pack 18912 para migração de ativos em massa
seo-title: Instalação do Feature Pack 18912 para migração de ativos em massa
description: O pacote de recursos 18912 permite que você ingira ativos em massa por FTP ou migre ativos do Dynamic Media Classic para o Dynamic Media no AEM. Este pacote opcional de recursos está disponível no suporte da Adobe.
seo-description: O pacote de recursos 18912 permite que você ingira ativos em massa por FTP ou migre ativos do Dynamic Media Classic para o Dynamic Media no AEM. Este pacote opcional de recursos está disponível no suporte da Adobe.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Instalação do pacote de recursos 18912 para migração de ativos em massa {#installing-feature-pack}

A instalação do pacote de recursos 18912 é _opcional_.

O pacote de recursos 18912 permite que você ingira ativos em massa diretamente no Dynamic Media - modo Scene 7 no AEM por meio de FTP ou migre ativos do Dynamic Media Classic para o Dynamic Media - modo Scene7 no AEM. O pacote de recursos está disponível no [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Embora seja possível usar o pacote de recursos para migrar ativos em massa por conta própria do Dynamic Media Classic para o modo Dynamic Media - Scene 7 no AEM ou migrar ativos em massa usando o recurso FTP no Dynamic Media Classic, a Adobe *não* recomenda esse método devido à complexidade envolvida.
>
>Dessa forma, os pacotes de recursos de migração, como este, *só* são suportados como parte de um projeto de migração por meio dos [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Antes de instalar este pacote de recursos, você deve primeiro criar um usuário de serviço e fornecer essas informações à Adobe.

Consulte também [Configuração do Dynamic Media - modo](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)Scene7.

**Para instalar o pacote de recursos 18912 para migração** de ativos em massa,

1. Em sua instância do AEM, navegue até **[!UICONTROL Ferramentas > Segurança > Usuários > Criar usuário]**. Este usuário de serviço deve ter permissões de leitura/gravação para `/content/dam`.
1. Nos campos **[!UICONTROL ID]** e **[!UICONTROL senha]** , digite um nome de usuário e uma senha; por exemplo, `FTP User`. Esse nome aparece na linha do tempo como o usuário que criou o ativo. Quando um ativo é carregado do FTP, um ativo é considerado criado quando é carregado no servidor FTP e enviado para o AEM.
1. Entre em contato com o suporte [Adobe Enterprise para obter o Experience Manager](https://helpx.adobe.com/br/contact/enterprise-support.ec.html) para solicitar acesso ao pacote de recursos 18912 para download. Você pode precisar das seguintes informações ao entrar em contato com o suporte:

   * Endereço IP do servidor para a instância do autor, incluindo o número da porta (por padrão, o número da porta é 4502).
   * Nome de usuário e senha do serviço AEM da etapa anterior.

1. O suporte empresarial da Adobe para o AEM fornece as credenciais FTP e o acesso ao pacote de recursos 18912.

1. Quando receber o pacote de recursos 18912, instale-o.

   Consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md) para obter mais informações sobre como usar a Distribuição de software e os pacotes no AEM.
