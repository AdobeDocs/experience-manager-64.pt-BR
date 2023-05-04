---
title: Expiração de objetos estáticos
seo-title: Expiration of Static Objects
description: Saiba como configurar AEM para que objetos estáticos não expirem (por um período de tempo razoável).
seo-description: Learn how to configure AEM so that static objects do not expire (for a reasonable period of time).
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: Configuring
exl-id: 3551d25c-c852-4f59-84fe-5e62f57ae63f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Expiração de objetos estáticos{#expiration-of-static-objects}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Os objetos estáticos (por exemplo, ícones) não são alterados. Por conseguinte, o sistema deve ser configurado de modo a não expirar (por um período de tempo razoável), reduzindo assim o tráfego desnecessário.

Isso tem o seguinte impacto:

* Descarrega solicitações da infraestrutura do servidor.
* Aumenta o desempenho do carregamento de página, à medida que o navegador armazena em cache objetos no cache do navegador.

As expirações são especificadas pelo padrão HTTP em relação à &quot;expiração&quot; dos arquivos (consulte, por exemplo, o capítulo 14.21 de [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot; Protocolo de transferência de hipertexto — HTTP 1.1&quot;). Esse padrão usa o cabeçalho para permitir que os clientes armazenem objetos em cache até que sejam considerados obsoletos; esses objetos são armazenados em cache pelo tempo especificado sem que seja feita qualquer verificação de status no servidor de origem.

>[!NOTE]
>
>Essa configuração é completamente separada do Dispatcher (e não funcionará para ele).
>
>O objetivo do Dispatcher é armazenar dados em cache na frente do AEM.

Todos os arquivos, que não são dinâmicos e que não mudam ao longo do tempo, podem e devem ser armazenados em cache. A configuração do servidor HTTPD do Apache pode ser semelhante a um dos seguintes - dependendo do ambiente:

>[!CAUTION]
>
>Você deve tomar cuidado ao definir o período durante o qual um objeto é considerado atualizado. Como há *sem verificação até que o período especificado tenha expirado*, o cliente pode acabar apresentando o conteúdo antigo do cache.

1. **Para uma instância de autor:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Isso permite que o cache intermediário (por exemplo, o cache do navegador) armazene arquivos CSS, Javascript, PNG e GIF por até um mês, até que expirem. Isso significa que elas não precisam ser solicitadas do AEM ou do servidor da Web, mas podem permanecer no cache do navegador.

   Outras seções do site não devem ser armazenadas em cache em uma instância do autor, pois estão sujeitas a alterações a qualquer momento.

1. **Para uma instância de publicação:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   Isso permite que o cache intermediário (por exemplo, o cache do navegador) armazene arquivos CSS, Javascript, PNG e GIF por até um dia em caches de clientes. Embora este exemplo ilustre as configurações globais para tudo o que está abaixo `/content` e `/etc/designs`, é necessário torná-lo mais granular.

   Dependendo da frequência com que seu site é atualizado, você também pode considerar o armazenamento em cache de páginas de HTML. Um prazo razoável seria de 1 hora:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Após configurar os objetos estáticos, verifique `request.log`, ao selecionar páginas que contêm esses objetos, para confirmar que nenhuma solicitação (desnecessária) está sendo feita para objetos estáticos.
