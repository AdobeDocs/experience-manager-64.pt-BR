---
title: Compatibilidade com versões anteriores no AEM 6.4
seo-title: Compatibilidade com versões anteriores no AEM 6.4
description: Saiba como manter seus aplicativos e configurações compatíveis com o AEM 6.4
seo-description: Saiba como manter seus aplicativos e configurações compatíveis com o AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---


# Compatibilidade com versões anteriores no AEM 6.4{#backward-compatibility-in-aem}

## Visão geral {#overview}

>[!NOTE]
>
>Para obter uma lista de alterações de conteúdo e configuração que não estão no escopo do Pacote de Compatibilidade, consulte [Reestruturação do Repositório no AEM 6.4](/help/sites-deploying/repository-restructuring.md).

No AEM 6.4, todos os recursos foram desenvolvidos tendo em mente a compatibilidade com versões anteriores.

Na maioria dos casos, os clientes que executam o AEM 6.3 não devem precisar alterar o código ou as personalizações ao fazer a atualização. Para clientes AEM 6.1 e 6.2, não há alterações adicionais de quebra que seriam enfrentadas durante uma atualização para o 6.3.

Para exceções em que os recursos não podiam ser mantidos compatíveis com versões anteriores, a compatibilidade com versões anteriores de pacotes e conteúdo pode ser alcançada instalando um Pacote de Compatibilidade para a versão 6.3 (consulte como configurar abaixo para obter detalhes sobre onde baixar). Este pacote de compatibilidade restaurará a compatibilidade para aplicativos compatíveis com o AEM 6.3.

O Pacote de Compatibilidade permite executar AEM no modo de compatibilidade e adiar o desenvolvimento personalizado em relação aos novos recursos de AEM:

>[!NOTE]
>
>Observe que o pacote de compatibilidade é apenas uma solução temporária para adiar o desenvolvimento necessário para ser compatível com o AEM 6.4, seu recomendado somente como uma última opção se você não conseguir resolver problemas de compatibilidade por meio do desenvolvimento imediatamente após a atualização. É altamente recomendável alternar para o modo nativo e desinstalar o pacote de compatibilidade depois de decidir prosseguir com o desenvolvimento personalizado baseado no 6.4 e aproveitar a funcionalidade 6.4 completa.

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

O Pacote de Compatibilidade tem dois modos: **Encaminhamento Ativado** e **Encaminhamento Desativado**.

Isso permite que o AEM 6.4 seja executado em três modos:

**Modo nativo:**

O modo nativo é para clientes que desejam usar todos os novos recursos do AEM 6.4 e estão prontos para fazer desenvolvimento para fazer com que suas personalizações funcionem com todos os novos recursos.

Isso significa que talvez seja necessário fazer ajustes em seu aplicativo imediatamente após a atualização.

**Modo de Compatibilidade: Pacote de Compatibilidade Instalado com Roteamento Ativado**

O Modo de Compatibilidade é para clientes que têm personalizações de interfaces que não são compatíveis com versões anteriores. Isso permite que o AEM seja executado no modo de compatibilidade e adie o desenvolvimento personalizado necessário em relação aos novos recursos de AEM que não são compatíveis com alguns de seus códigos personalizados.

**Modo herdado: Pacote de Compatibilidade Instalado com Roteamento Desativado**

O modo herdado é para clientes que têm interfaces personalizadas baseadas em código herdado ou obsoleto do AEM que foi movido para fora no pacote de compatibilidade.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Como configurar {#how-to-set-up}

O Pacote de Compatibilidade do AEM 6.3 pode ser instalado como um pacote usando o Gerenciador de Pacotes. Você pode baixar o [AEM Pacote de Compatibilidade 6.3 do site Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63).

Quando o Pacote de Compatibilidade estiver instalado, o roteamento poderá ser ativado ou desativado usando um switch na configuração OSGI, conforme mostrado abaixo:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Quando o Pacote de Compatibilidade estiver instalado e configurado, os recursos serão usados com base no modo de compatibilidade que foi escolhido.
