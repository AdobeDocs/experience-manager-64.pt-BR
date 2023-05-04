---
title: Instalação do Feature Pack 18912 para migração de ativos em massa
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: O Feature Pack 18912 permite assimilar ativos em massa por FTP ou migrar ativos do Dynamic Media Classic para o Dynamic Media no AEM. Este pacote de recursos opcional está disponível no suporte ao Adobe.
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 4%

---

# Instalando o feature pack 18912 para a migração de ativos em massa {#installing-feature-pack}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A instalação do feature pack 18912 é _opcional_.

O Feature Pack 18912 permite assimilar ativos em massa diretamente no modo Dynamic Media - Scene 7 no AEM por meio de FTP ou migrar ativos do Dynamic Media Classic para o modo Dynamic Media - Scene7 no AEM. O pacote de recursos está disponível em [Adobe Professional Services](https://business.adobe.com/br/customers/consulting-services/main.html).

>[!NOTE]
>
>Embora seja possível usar o pacote de recursos para migrar ativos em massa por conta própria do Dynamic Media Classic para o Dynamic Media - Scene7 no modo AEM ou migrar ativos em massa usando o recurso FTP no Dynamic Media Classic, o Adobe faz *not* recomende esse método devido à complexidade envolvida.
>
>Sendo assim, os pacotes de recursos de migração, como este, são *only* suportado como parte de um projeto de migração por meio de [Adobe Professional Services](https://business.adobe.com/br/customers/consulting-services/main.html).

Antes de instalar este feature pack, primeiro crie um usuário de serviço e forneça essas informações para o Adobe.

Consulte também [Configuração do Dynamic Media - Modo Scene7](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**Para instalar o feature pack 18912 para migração de ativos em massa**,

1. Na instância do AEM, navegue até **[!UICONTROL Ferramentas > Segurança > Usuários > Criar usuário]**. Este usuário de serviço deve ter permissões de leitura/gravação para `/content/dam`.
1. No **[!UICONTROL ID]** e **[!UICONTROL Senha]** digite um nome de usuário e senha; por exemplo, `FTP User`. Esse nome aparece na linha do tempo como o usuário que criou o ativo. Quando um ativo é carregado a partir do FTP, um ativo é considerado criado quando é carregado no servidor FTP e é enviado ao AEM.
1. Contato [Suporte ao cliente do Adobe para Experience Manager](https://helpx.adobe.com/br/contact/enterprise-support.ec.html) para solicitar acesso ao feature pack 18912 para download. Você pode precisar das seguintes informações quando entrar em contato com o suporte:

   * Endereço IP do servidor para a instância do Autor, incluindo o número da porta (por padrão, o número da porta é 4502).
   * AEM nome de usuário do serviço e senha da etapa anterior.

1. O Suporte ao Cliente do Adobe para AEM fornece as credenciais do FTP e o acesso ao feature pack 18912.

1. Quando receber feature pack 18912, instale-o.

   Consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md) para obter mais informações sobre o uso da Distribuição de software e dos pacotes no AEM.
