---
title: Renderização do SPA e do servidor
seo-title: Renderização do SPA e do servidor
description: 'null'
seo-description: 'null'
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
translation-type: tm+mt
source-git-commit: 0e7f4a78f63808bea2aa7a5abbb31e7e5b9d21b3
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 1%

---


# Renderização do SPA e do servidor{#spa-and-server-side-rendering}

>[!NOTE]
>O recurso Editor de aplicativo de página única (SPA) requer [AEM 6.4 service pack 2](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) ou mais recente.
>
>O Editor SPA é a solução recomendada para projetos que exigem renderização do lado do cliente baseada em estrutura SPA (por exemplo, Reagir ou Angular).

>[!NOTE]
>
>É necessário AEM 6.4.5.0 ou posterior para usar os recursos de renderização do lado do servidor SPA, conforme descrito neste documento.

## Visão geral {#overview}

Os aplicativos de página única (SPAs) podem oferta ao usuário de experiências ricas e dinâmicas que reagem e se comportam de maneiras familiares, geralmente como os aplicativos nativos. [Isso é feito contando com o cliente para carregar o conteúdo antecipadamente e, em seguida, fazer um pesado levantamento da manipulação da interação](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) do usuário, minimizando a quantidade de comunicação necessária entre o cliente e o servidor, tornando o aplicativo mais reativo.

No entanto, isso pode levar a tempos de carregamento iniciais mais longos, especialmente se o SPA for grande e rico em seu conteúdo. Para otimizar o tempo de carregamento, parte do conteúdo pode ser renderizada no lado do servidor. O uso da renderização no lado do servidor (SSR) pode acelerar a carga inicial da página e passar a renderização para o cliente.

## Quando usar o SSR {#when-to-use-ssr}

A SSR não é necessária em todos os projetos. Embora AEM suporte totalmente o JS SSR para SPA, o Adobe não recomenda implementá-lo sistematicamente para cada projeto.

Ao decidir implementar a SSR, você deve primeiro estimar o que a complexidade adicional, o esforço e a adição de custo representa realisticamente para o projeto, incluindo a manutenção de longo prazo. Uma arquitetura de SSR só deve ser escolhida se o valor acrescentado exceder claramente os custos estimados.

A SSR geralmente fornece algum valor quando há um claro &quot;sim&quot; a qualquer uma das seguintes perguntas:

* **SEO:** O SSR ainda é necessário para que seu site seja indexado corretamente pelos mecanismos de pesquisa que trazem tráfego? Lembre-se de que os principais rastreadores de mecanismo de pesquisa agora avaliam o JS.
* **Velocidade da página:** A SSR fornece uma melhoria mensurável da velocidade em ambientes reais e adiciona à experiência geral do usuário?

Somente quando uma dessas duas perguntas for respondida com um claro &quot;sim&quot; para o seu projeto é que o Adobe recomenda a implementação da SSR. As seções a seguir descrevem como fazer isso usando o Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-io-runtime}

Se você estiver [confiante de que seu projeto requer a implementação da SSR](#when-to-use-ssr), a solução Adobe recomendada é usar a Adobe I/O Runtime

Para obter mais informações sobre o Adobe I/O Runtime, consulte

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - para obter uma visão geral do serviço
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - para obter a documentação detalhada sobre a plataforma

As seções a seguir detalham como a Adobe I/O Runtime pode ser usada para implementar a SSR para seu SPA em dois modelos diferentes:

* [Fluxo de comunicação orientado por AEM](#aem-driven-communication-flow)
* [Fluxo de comunicação direcionado para E/S em tempo de execução de Adobe](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>O Adobe recomenda uma instância do Adobe I/O Runtime separada para cada ambiente AEM (autor, publicação, estágio etc.).

## Configuração remota do renderizador de conteúdo {#remote-content-renderer-configuration}

AEM deve saber onde o conteúdo renderizado remotamente pode ser recuperado. Independentemente do modelo [que você escolher implementar para SSR](#adobe-io-runtime), será necessário especificar para AEM como acessar esse serviço de renderização remota.

Isso é feito por meio do serviço **RemoteContentRenderer - OSGi de fábrica** de configuração. Procure a string &quot;RemoteContentRenderer&quot; no console Configuração do console da Web em `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Os seguintes campos estão disponíveis para a configuração:

* **Padrão** do caminho do conteúdo - expressão regular para corresponder a uma parte do conteúdo, se necessário
* **URL** de ponto de extremidade remoto - URL do ponto de extremidade responsável pela geração do conteúdo
   * Use o protocolo HTTPS protegido se não estiver na rede local.
* **Cabeçalhos** de solicitação adicionais - Cabeçalhos adicionais a serem adicionados à solicitação enviada ao terminal remoto
   * Padrão: `key=value`
* **Tempo limite** da solicitação - Tempo limite da solicitação de host remoto em milissegundos

>[!NOTE]
>
>Independentemente de se optar por implementar o fluxo [de comunicação orientado por](#aem-driven-communication-flow) AEM ou o fluxo [controlado pela](#adobe-io-driven-communication-flow)Adobe I/O Runtime, é necessário definir uma configuração de renderizador de conteúdo remoto.
>
>Essa configuração também deve ser definida se você optar por [usar um servidor](#using-node-js)Node.js personalizado.

>[!NOTE]
>
>Essa configuração aproveita o [Remote Content Renderer](#remote-content-renderer), que tem opções adicionais de extensão e personalização disponíveis.

## Fluxo de comunicação orientado por AEM {#aem-driven-communication-flow}

Ao usar a SSR, o fluxo de trabalho [de interação do](/help/sites-developing/spa-overview.md#workflow) componente de SPAs no AEM inclui uma fase na qual o conteúdo inicial do aplicativo é gerado pela Adobe I/O Runtime.

1. O navegador solicita o conteúdo SSR da AEM.
1. AEM publica o modelo no Adobe I/O Runtime.
1. A Adobe I/O Runtime retorna o conteúdo gerado
1. AEM serve o HTML retornado pela Adobe I/O Runtime por meio do modelo HTL do componente de página de backend.

![server-side-rendering-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Fluxo de comunicação orientado pela Adobe I/O Runtime {#adobe-io-driven-communication-flow}

A seção Fluxo [de comunicação orientado por](#aem-driven-communication-flow) AEM descreve a implementação padrão e recomendada da renderização do lado do servidor em relação aos SPAs no AEM, onde AEM executa o carregamento de conteúdo e o fornecimento de conteúdo.

Como alternativa, a SSR pode ser implementada para que a Adobe I/O Runtime seja responsável pela inicialização, revertendo efetivamente o fluxo de comunicação.

Ambos os modelos são válidos e suportados pela AEM. No entanto, é preciso considerar as vantagens e desvantagens de cada um antes de implementar um modelo específico.

| Bootstrapping | Vantagens | Desvantagens |
|---|---|---|
| via AEM | AEM gerencia bibliotecas injetáveis onde<br>necessárioOs recursos só precisam ser mantidos em AEM | Possivelmente estranho para o desenvolvedor SPA |
| via Adobe I/O Runtime | Mais familiar para desenvolvedores de SPA | Os recursos clientlib necessários para o aplicativo, como CSS e JavaScript, precisarão ser disponibilizados pelo desenvolvedor AEM por meio da [`allowProxy` propriedade. Os recursos devem ser sincronizados entre AEM e o Adobe I/O](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br><br>RuntimePara habilitar a criação do SPA, pode ser necessário um servidor proxy para Adobe I/O Runtime |

## Planejamento para SSR {#planning-for-ssr}

Geralmente, apenas parte de um aplicativo precisa ser renderizada no lado do servidor. O exemplo comum é o conteúdo que será exibido acima da dobra na carga inicial da página que precisa ser renderizada no lado do servidor. Isso economiza tempo fornecendo ao cliente conteúdo já renderizado. Conforme o usuário interage com o SPA, o conteúdo adicional é renderizado pelo cliente.

Ao considerar implementar a renderização do lado do servidor para o SPA, é necessário revisar quais partes do aplicativo ele exigirá SSR.

## Desenvolvimento de um SPA usando SSR {#developing-an-spa-using-ssr}

Os componentes SPA podem ser renderizados pelo cliente (no navegador) ou pelo servidor. Quando o servidor renderizado, as propriedades do navegador, como tamanho e localização da janela, não estão presentes. Por conseguinte, os componentes do SPA devem ser isomórficos, não assumindo qualquer hipótese quanto ao local em que serão apresentados.

Para aproveitar o SSR, será necessário implantar seu código no AEM e no Adobe I/O Runtime, que é responsável pela renderização no servidor. A maioria do código será o mesmo, no entanto, tarefas específicas do servidor serão diferentes.

## SSR para SPAs em AEM {#ssr-for-spas-in-aem}

A SSR para SPAs em AEM exige a Adobe I/O Runtime, que é chamada para a renderização do lado do servidor de conteúdo do aplicativo. No HTL do aplicativo, um recurso no Adobe I/O Runtime é chamado para renderizar o conteúdo.

Da mesma forma que o AEM suporta as estruturas SPA Angular e React prontas, a renderização no lado do servidor também é compatível com aplicativos Angular e React. Consulte a documentação do NPM para obter mais detalhes sobre ambas as estruturas.

* Reagir: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Para obter um exemplo simplista, consulte o aplicativo de Journal [We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Ele renderiza todo o lado do servidor de aplicativos. Embora este não seja um exemplo real, ele ilustra o que é necessário para implementar a SSR.

>[!CAUTION]
>O aplicativo [Journal](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) We.Retail é apenas para fins de demonstração e, portanto, usa Node.js como um exemplo simples em vez do Adobe I/O Runtime recomendado. Este exemplo não deve ser usado para nenhum trabalho de projeto.

>[!NOTE]
>Qualquer projeto AEM deve aproveitar o [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html), que suporta projetos SPA usando React ou Angular e aproveita o SDK do SPA.

## Uso de Node.js {#using-node-js}

A Adobe I/O Runtime é a solução recomendada para implementar a SSR para SPAs em AEM.

Para instâncias de AEM no local, também é possível implementar a SSR usando uma instância do Node.js personalizada da mesma forma que a descrita acima. Embora seja suportado pelo Adobe, isso não é recomendado.

Node.js não é compatível com instâncias de AEM hospedadas por Adobe.

>[!NOTE]
>
>Se o SSR precisar ser implementado via Node.js, o Adobe recomenda uma instância diferente de Node.js para cada ambiente AEM (autor, publicação, estágio etc.).

## Renderizador de conteúdo remoto {#remote-content-renderer}

A Configuração [do renderizador de conteúdo](#remote-content-renderer-configuration) remoto necessária para usar o SSR com seu SPA AEM toca em um serviço de renderização mais generalizado que pode ser estendido e personalizado para atender às suas necessidades.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` é um serviço OSGi para recuperar conteúdo renderizado em um servidor remoto, como de E/S de Adobe. O conteúdo enviado para o servidor remoto é baseado no parâmetro de solicitação passado.

`RemoteContentRenderingService` pode ser inserido por inversão de dependência em um modelo Sling personalizado ou servlet quando for necessária manipulação de conteúdo adicional.

Esse serviço é usado internamente pelo [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

O `RemoteContentRendererRequestHandlerServlet` pode ser usado para definir programaticamente a configuração da solicitação. `DefaultRemoteContentRendererRequestHandlerImpl`, a implementação do manipulador de solicitações padrão fornecido permite que você crie várias configurações OSGi para mapear um local na estrutura do conteúdo para um terminal remoto.

Para adicionar um Manipulador de solicitações personalizado, implemente a `RemoteContentRendererRequestHandler` interface. Certifique-se de definir a propriedade do `Constants.SERVICE_RANKING` componente para um número inteiro superior a 100, que é a classificação do `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configurar a configuração OSGi do manipulador padrão {#configure-default-handler}

A configuração do manipulador padrão deve ser configurada conforme descrito na seção Configuração [do renderizador de conteúdo](#remote-content-renderer-configuration)remoto.

###  Uso do Renderizador de Conteúdo Remoto {#usage}

Para obter um servlet e retornar algum conteúdo que possa ser inserido na página:

1. Verifique se o servidor remoto está acessível.
1. Adicione um dos seguintes trechos ao modelo HTL de um componente AEM.
1. Como opção, crie ou modifique as configurações do OSGi.
1. Procurar o conteúdo do site

Normalmente, o modelo HTL de um componente de página é o recipient principal desse recurso.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Requisitos {#requirements}

Os servlets aproveitam o Exportador do Modelo Sling para serializar os dados do componente. Por padrão, os adaptadores `com.adobe.cq.export.json.ContainerExporter` e `com.adobe.cq.export.json.ComponentExporter` são suportados como Sling Model. Se necessário, é possível adicionar classes para as quais a solicitação deve ser adaptada para usar o `RemoteContentRendererServlet` e implementar o `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. As classes adicionais devem estender o `ComponentExporter`.
