---
title: Configuração de armazenamento
seo-title: Storage Configuration
description: Como acessar o Console de Configuração de Armazenamento
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 905b6dc5-cf17-4f58-a687-27e2910a0729
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Configuração de armazenamento {#storage-configuration}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A configuração de armazenamento é o meio de identificar o armazenamento escolhido para o conteúdo da comunidade, também conhecido como conteúdo gerado pelo usuário (UGC).

Essa configuração informa o código AEM Communities sobre qual implementação do SRP (Storage Resource Provider, provedor de recursos de armazenamento) deve ser usada ao acessar o UGC e deve refletir a topologia estabelecida quando o AEM foi implantado.

Para uma discussão sobre opções de armazenamento e topologias de implantação, visite

* [Armazenamento de conteúdo da comunidade](working-with-srp.md)
* [Topologias recomendadas](topologies.md)

## Console de configuração de armazenamento {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

No ambiente de criação, para acessar o console de configuração de armazenamento

* Na navegação global: **[!UICONTROL Ferramentas > Comunidades > Configuração de armazenamento]**

Para selecionar uma opção de armazenamento diferente do JCR padrão:

* selecionar uma opção
* Configurar adequadamente

   * Veja detalhes para [selecionando o MSRP](msrp.md#select-msrp)
   * Veja detalhes para [selecionando DSRP](dsrp.md#select-dsrp)
   * Veja detalhes para [selecionando ASRP](asrp.md#select-asrp)

* Selecione **[!UICONTROL Enviar]**

### Sobre o armazenamento JCR {#about-jcr-storage}

Esteja ciente de que se nenhuma seleção for feita, o padrão será o repositório AEM, o JCR.

JCR é *not* uma loja comum compartilhada pelos ambientes de criação e publicação. O conteúdo da comunidade será visível somente no ambiente de criação ou publicação em que foi criado.

Visita [Loja JCR](jsrp.md) para obter mais informações.

>[!NOTE]
>
>A ausência do nó `srpc`under `/etc/socialconfig` indica o padrão [Loja JCR](jsrp.md).
