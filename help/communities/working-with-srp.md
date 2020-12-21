---
title: SRP - Armazenamento de conteúdo da comunidade
seo-title: SRP - Armazenamento de conteúdo da comunidade
description: A partir do AEM Communities 6.1, o conteúdo gerado pelo usuário (UGC) é armazenado em uma única loja comum fornecida por um provedor de recursos do armazenamento (SRP)
seo-description: A partir do AEM Communities 6.1, o conteúdo gerado pelo usuário (UGC) é armazenado em uma única loja comum fornecida por um provedor de recursos do armazenamento (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP - Armazenamento de conteúdo da comunidade {#srp-community-content-storage}

## Introdução {#introduction}

A partir do AEM Communities 6.1, o conteúdo gerado pelo usuário (UGC) é armazenado em uma única loja comum fornecida por um provedor de recursos do armazenamento (SRP). Há várias opções de SRP a partir das quais escolher, como ASRP, MSRP e JSRP.

Diferentemente das versões anteriores, não há replicação reversa/direta do UGC em instâncias AEM. Em vez disso, o SRP torna o UGC diretamente acessível para operações de criação, leitura, atualização e exclusão (CRUD) de todas as instâncias de autor e publicação, com uma exceção para JSRP.

Veja a seguir as [características de cada opção SRP](#characteristics-of-srp-options), que são informações cruciais para o processo de decisão ao escolher o SRP adequado e [implantação subjacente](topologies.md).

Para obter detalhes sobre o uso do SRP para UGC, consulte [Visão geral do provedor de recursos do Armazenamento](srp.md).

>[!NOTE]
>
>O SRP se aplica somente ao conteúdo da comunidade. Isso não afeta o local onde o conteúdo do site é armazenado ([armazenamento de nó](../../help/sites-deploying/data-store-config.md)) e não afeta a manipulação segura do registro do usuário, perfis do usuário e grupos de usuários entre AEM instâncias (consulte também [Gerenciamento de dados do usuário](#managing-user-data)).

>[!CAUTION]
>
>A partir AEM 6.1, [o UGC nunca será replicado](#ugc-never-replicated).
>
>Quando a implantação não incluir um armazenamento comum, como a topologia padrão [JSRP](topologies.md#jsrp), o UGC estará visível somente na instância de publicação ou autor AEM na qual foi inserido. Somente se a topologia incluir um cluster de publicação, o UGC estará visível em qualquer instância de publicação.

## Características das opções de SRP {#characteristics-of-srp-options}

[ASRP - Provedor de Recursos de Armazenamento de Adobe](asrp.md)\
Com essa opção, o UGC é mantido remotamente em um serviço de nuvem hospedado e gerenciado pelo Adobe. Requer uma licença adicional e trabalhar com um representante de conta para fornecer a conta dessa licença específica.

* Requer um serviço de nuvem associado fornecido e suportado pela Adobe para armazenar conteúdo da comunidade
* Requer a escolha de um data center em uma região específica (EUA, EMEA, APAC)
* Exige que todo o acesso programático ao UGC seja feito por meio da API SRP
* Adequado para o farm de publicação do TarMK
* Adequado quando não houver intenção de investir em armazenamentos locais

>[!NOTE]
>
>Há um limite para carregar anexos em postagens (ou comentários) no ASRP, que é de 50 MB.

[MSRP - Provedor de recursos do Armazenamento MongoDB](msrp.md)\
Com essa opção, o UGC é persistente diretamente em uma instância do MongoDB local.

* Requer uma instalação local e licenciada do MongoDB para armazenar conteúdo da comunidade
* Requer uma instalação local do Apache Solr
* Exige que todo o acesso programático ao UGC seja feito por meio da API SRP
* Adequado para um farm de publicação TarMK existente
* Adequado para um cluster MongoMK ou RdbMK
* Adequado ao esperar grandes volumes de conteúdo da comunidade

[DSRP - Provedor de Recursos de Armazenamento de Banco de Dados Relacional](dsrp.md)\
Com essa opção, o UGC é persistente diretamente em uma instância de banco de dados MySQL local.

* Requer uma instalação local do MySQL para armazenar conteúdo da comunidade
* Requer uma instalação local do Apache Solr
* Exige que todo o acesso programático ao UGC seja feito por meio da API SRP
* Adequado para um farm de publicação TarMK existente
* Adequado para um cluster MongoMK ou RdbMK
* Adequado ao esperar grandes volumes de conteúdo da comunidade

[JSRP - Provedor de recursos do Armazenamento JCR](jsrp.md)\
Com a opção padrão, não há armazenamento comum. O UGC é persistente somente no mesmo repositório JCR que a instância AEM na qual foi inserido.

* Armazena o conteúdo da comunidade no repositório JCR do autor ou instância de publicação AEM em que foi postada
* Exige que todo o acesso programático ao UGC seja feito por meio da API SRP
* Requer um cluster de publicação se mais de uma instância de publicação estiver implantada (não há mecanismo de replicação entre instâncias de publicação em um farm do TarMK)
* A moderação é executada somente no ambiente de publicação (não há mecanismo de replicação reversa/direta entre o autor e a publicação)
* Geralmente melhor para desenvolvimento, demonstrações e treinamento

## Configuração do SRP {#configuring-srp}

A especificação da opção de armazenamento padrão, com base na implantação subjacente, é feita pelo [console de Configuração do Armazenamento](srp-config.md).

Para obter detalhes de configuração de cada opção, consulte:

* [ASRP - Provedor de Recursos de Armazenamento de Adobe](asrp.md)
* [MSRP - Provedor de recursos do Armazenamento MongoDB](msrp.md)
* [DSRP - Provedor de Recursos de Armazenamento de Banco de Dados Relacional](dsrp.md)
* [JSRP - Provedor de recursos do Armazenamento JCR](jsrp.md)

Se nenhuma opção de armazenamento estiver ativamente selecionada, o JSRP será ativado por padrão.

## Informações adicionais {#additional-information}

### UGC Nunca Replicou {#ugc-never-replicated}

No ambiente do autor, um autor cria o conteúdo da página e o replica no ambiente de publicação. Quando uma página inclui um recurso interativo do AEM Communities, como comentários, revisões, fórum, blog ou QnA, a interação dos membros (conectados aos visitantes do site) em uma instância de publicação resulta em conteúdo gerado pelo usuário (UGC) inserido no ambiente de publicação.

Anteriormente, esse conteúdo da comunidade era replicado reverso para instâncias do autor e do autor replicado para instâncias de publicação. Foi problemático manter a consistência entre instâncias AEM com replicação reversa e posterior.

A partir do AEM Communities 6.1, a necessidade de replicação do UGC foi eliminada usando armazenamento compartilhado para UGC, conforme descrito acima.

Embora o conteúdo do site seja replicado, o UGC nunca é replicado.

### Gerenciando Dados do Usuário {#managing-user-data}

Além disso, é de interesse para as Comunidades serem [*usuários*, *grupos de usuários* e *perfis de usuário*](users.md). Esses dados relacionados ao usuário, quando criados e atualizados no ambiente de publicação, precisam ser disponibilizados para outras instâncias de publicação quando a topologia for um [farm de publicação](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

A partir do AEM Communities 6.1, os dados relacionados ao usuário são sincronizados usando a distribuição Sling em vez da replicação. Para obter mais informações, visite [Sincronização do usuário](sync.md).

### Atualização para o AEM Communities 6.2 {#upgrading-to-aem-communities}

Ao atualizar para o AEM Communities 6.3, se o UGC pré-existente precisar ser retido, as etapas devem ser realizadas dependendo se a comunidade AEM 5.6.1 ou AEM 6.0 usou o armazenamento Adobe sob demanda ou o armazenamento local do UGC.

Para obter detalhes, visite [Atualizando para o AEM Communities 6.3](upgrade.md).
