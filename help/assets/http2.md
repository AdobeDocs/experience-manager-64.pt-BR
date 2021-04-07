---
title: Entrega de conteúdo HTTP2
seo-title: Entrega de conteúdo HTTP2
description: HTTP/2 melhora a forma como os navegadores e servidores se comunicam, permitindo uma transferência mais rápida de informações e reduzindo a quantidade de poder de processamento necessário.
seo-description: HTTP/2 melhora a forma como os navegadores e servidores se comunicam, permitindo uma transferência mais rápida de informações e reduzindo a quantidade de poder de processamento necessário.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Gerenciamento de ativos
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---

# Entrega HTTP2 de conteúdo {#http-delivery-of-content}

A Adobe está animada em anunciar a disponibilidade da entrega de conteúdo HTTP/2 com o benefício geral de um melhor desempenho.

## O que é HTTP/2? {#what-is-http}

O HTTP/2 melhora a forma como os navegadores e servidores se comunicam, permitindo uma transferência mais rápida de informações e ao mesmo tempo reduzindo a quantidade de poder de processamento necessário.

O site a seguir descreve o HTTP/2 e seus benefícios de uma forma breve e simples:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Quais são os principais benefícios da migração para HTTP/2 para a entrega de conteúdo? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

A melhoria de desempenho varia muito com base em fatores como o código do seu site, a forma como você está usando o Dynamic Media, o dispositivo do consumidor, a tela e o local, e assim por diante.

Resultados dos testes próprios:

* Para imagens, o tempo de resposta melhorou de 7% a 28%, dependendo do dispositivo e do navegador. Os ganhos de desempenho mais notáveis foram em dispositivos iOS.
* Para visualizadores, o desempenho do tempo de carregamento melhorou em 15%.

A demonstração a seguir ilustra a diferença entre o carregamento HTTP/1 e HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Posso mudar para HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Para usar HTTP/2, você deve atender aos seguintes requisitos:

* Use HTTPS seguro para suas solicitações de mídia avançada.
* Use a CDN (rede de entrega de conteúdo) fornecida pelo Adobe como parte de sua licença da Dynamic Media.
* Use um domínio dedicado (não-company-h.assetsadobe#.com).

   Se você já tiver um domínio dedicado, poderá aceitar por meio do Suporte técnico.

   Se você não tiver um domínio dedicado, o Adobe agendará sua transição para HTTP/2 em 2018.

## Qual é o processo para habilitar HTTP/2 para minha conta Dynamic Media? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Você deve iniciar a solicitação para mudar para HTTP/2; isso não é feito automaticamente para você.

1. Inicie uma solicitação do Suporte Técnico para mudar para HTTP2. Consulte [Acessar o portal de suporte AEM](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

   1. Forneça as seguintes informações em sua solicitação de suporte:

      1. Nome do contato principal, email, telefone.
      1. Todos os domínios a serem transferidos para HTTP2.
      1. Verifique se você está usando HTTPS seguro para solicitações de mídia avançada.
      1. Verifique se você está usando a CDN por meio do Adobe e não é gerenciada com uma relação direta.
      1. Verifique se você está usando um domínio dedicado. Se você usar o Dynamic Media, você já estará usando um domínio dedicado.
   1. O Suporte Técnico adicionará você à lista de espera do cliente HTTP/2 na ordem em que as solicitações foram enviadas.
   1. Quando o Adobe estiver pronto para lidar com sua solicitação, o suporte entrará em contato com você para coordenar a transição e definir uma data de destino.
   1. Você será notificado após a conclusão e poderá verificar a transição bem-sucedida para HTTP2.

      Como o navegador não declara esse fato, é necessário baixar uma extensão.

      Para o Firefox e o Chrome há uma extensão chamada &quot;HTTP/2 e Indicador SPDY&quot;. Os navegadores só suportam http/2 com segurança, portanto, é necessário chamar um URL com https para verificar. Se http/2 for suportado, isso será indicado pela extensão na forma de um símbolo de Flash azul e um cabeçalho &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.


## Quando posso esperar uma transição para HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

As solicitações serão processadas na ordem em que são recebidas pelo Suporte Técnico.

>[!NOTE]
>
>Pode haver um lead time longo, pois a transição para HTTP/2 envolve a limpeza do cache. Portanto, apenas algumas transições de clientes podem ser tratadas por vez.

## Quais são os riscos com a mudança para HTTP/2? {#what-are-the-risks-with-moving-to-http}

A transição para HTTP/2 limpa seu cache no CDN porque envolve mudar para uma nova configuração de CDN.

O conteúdo armazenado em cache atinge diretamente os servidores de origem não-Adobe até que o cache seja recriado novamente. Por causa disso, o Adobe planeja lidar com algumas transições de clientes de cada vez, para que o desempenho aceitável seja mantido ao puxar solicitações de nossa origem.

## Como é possível verificar se um URL ou site está ativado com HTTP/2? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Como o navegador não declara esse fato, é necessário baixar uma extensão.

Para o Firefox e o Chrome há uma extensão chamada &quot;HTTP/2 e Indicador SPDY&quot;. Os navegadores só suportam http/2 com segurança, portanto, é necessário chamar um URL com https para verificar. Se http/2 for suportado, isso será indicado pela extensão na forma de um símbolo de Flash azul e um cabeçalho &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.
