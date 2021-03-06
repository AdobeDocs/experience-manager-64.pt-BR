---
title: Topologias recomendadas para comunidades
seo-title: Topologias recomendadas para comunidades
description: Como abordar a manipulação de conteúdo gerado pelo usuário (UGC)
seo-description: Como abordar a manipulação de conteúdo gerado pelo usuário (UGC)
uuid: 4bc1c423-0ba9-4f2e-b11c-4d6824f45641
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 46f135de-a0bf-451d-bdcc-fb29188250aa
translation-type: tm+mt
source-git-commit: 3db2abacf2161f8de715a2972bafacdad43563ef
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---


# Topologias recomendadas para Comunidades {#recommended-topologies-for-communities}

A partir do AEM Communities 6.1, uma abordagem única foi adotada para lidar com o conteúdo gerado pelo usuário (UGC) enviado por visitantes do site (membros) do ambiente de publicação.

Essa abordagem é fundamentalmente diferente da forma como a plataforma AEM lida com o conteúdo do site, geralmente gerenciado pelo ambiente do autor.

A plataforma AEM usa uma loja de nós que replica o conteúdo do site do autor para a publicação, enquanto a AEM Communities usa uma única loja comum para UGC que nunca é replicada.

Para a loja UGC comum, é necessário escolher um [provedor de recursos do armazenamento (SRP)](working-with-srp.md). As opções recomendadas são:

* [DSRP - Provedor de Recursos de Armazenamento de Banco de Dados Relacional](dsrp.md)
* [MSRP - Provedor de recursos do Armazenamento MongoDB](msrp.md)
* [ASRP - Provedor de Recursos de Armazenamento de Adobe](asrp.md)

Outra opção SRP, [JSRP - Provedor de recursos do Armazenamento JCR](jsrp.md), não oferece suporte a uma loja UGC comum para o autor e para a publicação de ambientes a ambos os acessos.

Exigir um armazenamento comum resulta nas seguintes topologias recomendadas.

>[!NOTE]
>
>Para AEM Communities, [UGC nunca é replicado](working-with-srp.md#ugc-never-replicated).
>
>Quando a implantação não incluir um [armazenamento comum](working-with-srp.md), o UGC estará visível somente na instância de publicação ou autor AEM na qual foi inserido.

>[!NOTE]
>
>Para obter mais informações sobre a plataforma AEM, consulte [Implantações recomendadas](../../help/sites-deploying/recommended-deploys.md) e [Introdução à plataforma AEM](../../help/sites-deploying/data-store-config.md).

## Para produção {#for-production}

A criação de uma loja comum para o UGC é essencial e, portanto, a implantação subjacente depende da sua capacidade de suportar uma loja comum.

Dois exemplos:

1) Se o volume esperado de UGC for alto e uma instância MongoDB local for possível, a escolha será [MSRP](msrp.md).

2) Para obter o desempenho ideal para o conteúdo da página, a escolha de um [farm de publicação](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) e [ASRP](asrp.md) proporcionaria o dimensionamento ideal do UGC com operações relativamente simples.

Para ambos, a implantação pode ser baseada em qualquer microkernel OAK.

Para escolher a loja comum apropriada, considere cuidadosamente as [características](working-with-srp.md#characteristics-of-srp-options) exclusivas de cada uma.

Para obter mais detalhes sobre os microkernals Oak, visite [Implantações recomendadas](../../help/sites-deploying/recommended-deploys.md).

### Farm de publicação do TarMK {#tarmk-publish-farm}

Quando a topologia é um farm de publicação, os tópicos relevantes de importância são

* [Sincronização do usuário](sync.md)
* [Gerenciamento de usuários e grupos de usuários](users.md)

### Recomendado: DSRP, MSRP ou ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | CONTEÚDO DO LOCAL | CONTENTREPOSITÓRIO GERADO PELO USUÁRIO | PROVEDOR DE RECURSOS DO armazenamento | LOJA COMUM |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| qualquer | JCR | MySQL | DSRP | Sim |
| qualquer | JCR | MongoDB | MSRP | Sim |
| qualquer | JCR | Adobe on-demand storage | ASRP | Sim |

### JSRP {#jsrp}


| Implantação | CONTEÚDO DO LOCAL | CONTENTREPOSITÓRIO GERADO PELO USUÁRIO | PROVEDOR DE RECURSOS DO armazenamento | LOJA COMUM |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| Farm TarMK (padrão) | JCR | JCR | JSRP | Não |
| Cluster Oak | JCR | JCR | JSRP | Sim somente para ambiente de publicação |

## Para Desenvolvimento {#for-development}

Para ambientes que não sejam de produção, o [JSRP](jsrp.md) oferece simplicidade na configuração de um ambiente de desenvolvimento com uma instância do autor e uma instância de publicação.

Se você selecionar [ASRP](asrp.md), [DSRP](dsrp.md) ou [MSRP](msrp.md) para produção, também será possível configurar um ambiente de desenvolvimento semelhante usando o armazenamento Adobe sob demanda ou o MongoDB. Para obter um exemplo, consulte [Como configurar MongoDB para Demo](demo-mongo.md).

## Referências {#references}

* [Sincronização do usuário](sync.md)

   Discute a sincronização dos dados do usuário entre as instâncias do farm de publicação.

* [Gerenciamento de usuários e grupos de usuários](users.md)

   Discute as funções de usuários e grupos de usuários nos ambientes de autor e publicação.

* UGC [loja comum](working-with-srp.md)

   Descreve o armazenamento do conteúdo da comunidade separadamente do conteúdo do site

* [Armazenamento de nós e armazenamento de dados](../../help/sites-deploying/data-store-config.md)

   Basicamente, o conteúdo do site é armazenado em um armazenamento de nós. Para Ativos, um armazenamento de dados pode ser configurado para armazenar dados binários. Para Comunidades, um armazenamento comum deve ser configurado para selecionar o SRP.

* [Elementos do armazenamento no AEM 6.3](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Descreve as implementações de armazenamento de dois nós: Tar e MongoDB.
