---
title: Notas de versão do AEM Communities
seo-title: AEM Communities
description: Notas de versão específicas das comunidades do Adobe Experience Manager 6.4.
seo-description: Notas de versão específicas das comunidades do Adobe Experience Manager 6.4.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 12%

---


# AEM Communities Notas de versão {#aem-communities-release-notes}

Esta seção fornece informações sobre as melhorias para AEM Communities desde a versão 6.3. Para saber mais detalhes sobre os novos recursos, consulte [Novidades no AEM 6.4 Comunidades](/help/communities/whats-new-aem-communities.md).

To obtain the latest release, see the [Deploying Communities](/help/communities/deploy-communities.md#latest-releases) section of the documentation.

## Melhorias principais {#main-improvements}

Sites da comunidade:

* Agora, os administradores da comunidade podem:

   * Excluir permanentemente os sites da comunidade
   * Selecione uma pasta de configuração sensível ao contexto para Sites da comunidade

Grupos de comunidades:

* Agora, os administradores da comunidade podem:

   * Excluir grupos da comunidade permanentemente
   * Criar grupos da comunidade em vários idiomas
   * Adicionar catálogo e atribuições de ativação dentro dos Grupos da comunidade

* Os gerentes de ativação agora podem

   * Criar e atribuir recursos e caminhos de aprendizado em grupos da comunidade

Biblioteca de arquivos:

* Os membros da comunidade agora têm várias melhorias na Biblioteca de arquivos, por exemplo, ordenar pedidos, marcar...

Notificações:

* Os membros da Comunidade recebem agora notificações mediante aprovação de contribuições que passaram por um processo de moderação

Moderação:

* Filtro de Detecção de Spam Automatizado
* Os Moderadores da comunidade têm filtros adicionais de moderação (por exemplo, perguntas respondidas/não respondidas)
* Os Moderadores da comunidade podem marcar e vincular a moderação a filtros predefinidos (por exemplo, todas as publicações que aguardam aprovação)

Compatibilidade global com as alterações fundamentais no AEM 6.4.

Observação: todos esses recursos também estão disponíveis para a AEM 6.3. Verifique as notas de versão do AEM Communities para [6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html).

## Problemas conhecidos {#known-issues}

* **Moderação** - Não é possível excluir a publicação-pai como uma única operação de exclusão da interface do usuário de moderação em massa (CQ-4236797)
* **Console** - o link Esqueceu o nome de usuário ou a senha está sendo redirecionado para a Página de logon em vez do formulário de recuperação de senha correspondente (CQ-4237682)

## Selecionar recursos {#select-features}

A Expert Scoring (*Powered by Sensei*) é usada para habilitar a gamificação, que é uma maneira eficaz de encorajar e recompensar um comportamento valioso da comunidade. Também pode ser usado para identificar especialistas para fins de recomendação ou marketing.

## Demonstrações {#demonstrations}

Todos esses recursos podem ser demonstrados usando a Máquina [de demonstração de](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) AEM disponível publicamente no GitHub.com ao usar o cenário de demonstração de AEM Communities e também dentro da nova implementação de referência We.Retail.
