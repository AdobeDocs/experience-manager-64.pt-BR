---
title: Notas de versão da AEM Communities
seo-title: AEM Communities
description: Notas de versão específicas das Comunidades do Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 6%

---

# Notas de versão da AEM Communities {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Esta seção fornece informações sobre as melhorias no AEM Communities desde a versão 6.3. Para saber mais sobre os novos recursos, consulte [Novidades AEM Comunidades 6.4](/help/communities/whats-new-aem-communities.md).

Para obter a versão mais recente, consulte [Implantação de comunidades](/help/communities/deploy-communities.md#latest-releases) da documentação.

## Melhorias principais {#main-improvements}

Sites da comunidade:

* Agora, os administradores da comunidade podem:

   * Excluir permanentemente os sites da comunidade
   * Selecione uma pasta de configuração sensível ao contexto para os Sites da comunidade

Grupos de comunidades:

* Agora, os administradores da comunidade podem:

   * Eliminar grupos de comunidade permanentes
   * Criar grupos de comunidade em vários idiomas
   * Adicionar catálogo de ativação e atribuições nos Grupos da comunidade

* Agora os Gerentes de ativação podem

   * Criar e atribuir recursos e caminhos de aprendizagem nos grupos da comunidade

Biblioteca de arquivo:

* Os membros da comunidade agora têm várias melhorias na Biblioteca de arquivos, por exemplo, ordenar pedidos, marcar...

Notificações:

* Os membros da Comunidade recebem agora notificações após a aprovação de contribuições que passaram por um processo de moderação

Moderação:

* Filtro de detecção automática de spam
* Os moderadores da comunidade têm filtros de moderação adicionais (por exemplo, perguntas respondidas/não respondidas)
* Os Moderadores da comunidade podem marcar e vincular a moderação a filtros predefinidos (por exemplo, todas as publicações pendentes de aprovação)

Compatibilidade global com as alterações fundamentais no AEM 6.4.

Observação: todos esses recursos também estão disponíveis para o AEM 6.3. Verifique as notas de versão do AEM Communities para ver [6,3](https://helpx.adobe.com/br/experience-manager/6-3/release-notes.html).

## Problemas conhecidos {#known-issues}

* **Moderação** - Não é possível excluir a publicação-pai como uma única operação de exclusão da interface do usuário de moderação em massa (CQ-4236797)
* **Console** - Esqueceu o nome de usuário ou o link Senha está redirecionando para a Página de logon em vez do formulário de recuperação de senha correspondente (CQ-4237682)

## Selecionar recursos {#select-features}

Pontuação de especialistas (*Alimentado pela Sensei*) - é utilizado para permitir a gamificação, que é uma forma eficaz de encorajar e recompensar um comportamento comunitário valioso. Também pode ser usado para identificar especialistas para fins de recomendação ou marketing.

## Manifestações {#demonstrations}

Todos esses recursos podem ser demonstrados usando o [Máquina de demonstração AEM](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponível publicamente em GitHub.com ao usar o cenário de demonstração do AEM Communities e também na nova implementação de referência We.Retail.
