---
title: Diretrizes de codificação
seo-title: Coding Guidelines
description: Diretrizes, dicas e truques do desenvolvedor do Communities
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: 022043cd-35ed-49b1-b5b4-5cc92d29cef4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 4%

---

# Diretrizes de codificação {#coding-guidelines}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Diretrizes, dicas e truques {#guidelines-tips-and-tricks}

Trabalhar com o AEM Communities evoluiu de depender muito das páginas do servidor Java para flexibilidade na escolha de linguagens de script de modelo, onde a lógica de negócios, o estilo e o conteúdo da página são distintos um do outro.

Mais flexibilidade no trabalho com conteúdo gerado pelo usuário (UGC) é por meio da API SocialResourceProvider, o que elimina a necessidade de conscientização da qual [SRP](srp.md) foi escolhida para a implantação.

A seguir estão várias diretrizes de codificação e práticas recomendadas para desenvolvedores do AEM Communities:

### Código {#code}

* [Acesso ao UGC com SRP](accessing-ugc-with-srp.md) - como evitar escrever um aplicativo que só funciona quando o UGC é armazenado no JCR (JSRP).
* [Refatoração do SocialUtils](socialutils.md) - métodos de utilidade para SRP que substituem o SocialUtils.
* [Convenções de nomenclatura](naming-conventions.md) - convenções de nomenclatura para classes Java personalizadas.

### Scripts {#scripts}

* [Componentes de comunidades de sideload](sideloading.md) - como adicionar dinamicamente um componente após o carregamento da página.
* [Princípios básicos do editor de rich text](rte.md) - como personalizar a interface do usuário de rich text fornecida aos membros para publicação de conteúdo.

### IDE {#ide}

* [Uso do Maven para comunidades](maven.md) - como incluir o jar da API das Comunidades.
* [Refatoração do SocialUtils](socialutils.md) - métodos de utilidade para SRP que substituem o SocialUtils.
