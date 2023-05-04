---
title: Integração JCR
seo-title: JCR Integration
description: Dicas para quando você deve integrar no nível do JCR
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---

# Integração JCR{#jcr-integration}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Preferir a API do recurso Sling para a API JCR {#prefer-the-sling-resource-api-to-jcr-api}

A API do Sling funciona em um nível mais alto e mais abstrato que a API do JCR. Isso permite que seu código seja mais reutilizável e independente do armazenamento subjacente. Isso facilita a inclusão de dados virtuais externos por meio do mecanismo ResourceProvider, se necessário.

## Evite consultas sempre que possível {#avoid-queries-wherever-possible}

É sempre mais rápido navegar no repositório para recuperar dados do que executar um query. Há casos em que as consultas serão necessárias, como uma consulta de usuário final ou a necessidade de localizar conteúdo estruturado em todo o repositório, mas para todos os outros casos, é preferível navegar até os nós necessários. As consultas devem ser sempre evitadas na lógica de renderização, como componentes de navegação, uma &quot;lista de itens recentes&quot;, contagens de itens e assim por diante. Nesses casos, é melhor percorrer a hierarquia ou pré-armazenar o resultado em cache para que ele possa ser usado diretamente quando renderizado.

## Restringir o escopo da observação do JCR {#restrict-the-scope-of-jcr-observation}

Ao acompanhar eventos no repositório, é importante restringir o escopo o máximo possível. Por exemplo, é muito melhor ouvir um evento em `/etc/mycompany` do que ouvir `/etc`. Nunca acompanhe eventos na raiz do repositório. Além disso, certifique-se de que os métodos de retorno de chamada sejam executados o mais rápido possível quando não houver nada para eles fazerem.

## Eliminar o uso do acesso do administrador do JCR {#eliminate-use-of-jcr-admin-access}

A partir do AEM 6, o login administrativo foi descontinuado, pois recebeu uma sessão administrativa do ResourceResolverFactory. Em vez disso, devem ser criadas contas de serviço para as operações de back office que exigiriam esse tipo de acesso e o ResourceResolverFactory pode ser usado para obter um ResourceResolver para esta conta.
