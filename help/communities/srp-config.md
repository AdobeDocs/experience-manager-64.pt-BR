---
title: Configuração de armazenamento
seo-title: Configuração de armazenamento
description: Como acessar o Console de Configuração de Armazenamento
seo-description: Como acessar o Console de Configuração de Armazenamento
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 905b6dc5-cf17-4f58-a687-27e2910a0729
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 3%

---

# Configuração de armazenamento {#storage-configuration}

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

   * Veja detalhes para [selecionar MSRP](msrp.md#select-msrp)
   * Veja detalhes para [selecionar DSRP](dsrp.md#select-dsrp)
   * Veja detalhes para [selecionar ASRP](asrp.md#select-asrp)

* Selecione **[!UICONTROL Enviar]**

### Sobre o armazenamento JCR {#about-jcr-storage}

Esteja ciente de que se nenhuma seleção for feita, o padrão será o repositório AEM, o JCR.

O JCR é *e não* um armazenamento comum compartilhado pelos ambientes de autor e publicação. O conteúdo da comunidade será visível somente no ambiente de criação ou publicação em que foi criado.

Visite [JCR Store](jsrp.md) para obter mais informações.

>[!NOTE]
>
>A ausência do nó `srpc`em `/etc/socialconfig` indica o [armazenamento JCR padrão](jsrp.md).
