---
title: Renderização de SPA e do servidor
seo-title: SPA and Server-Side Rendering
description: "Renderização de SPA e do servidor"
seo-description: null
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
exl-id: 89e45231-885a-4d35-839b-2b50239503ad
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1807'
ht-degree: 2%

---

# Renderização de SPA e do servidor{#spa-and-server-side-rendering}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>O recurso Editor de aplicativo de página única (SPA) requer [AEM 6.4 service pack 2](https://helpx.adobe.com/br/experience-manager/6-4/release-notes/sp-release-notes.html) ou mais recente.
>
>O Editor de SPA é a solução recomendada para projetos que exigem renderização do lado do cliente baseada em SPA estrutura (por exemplo, Reagir ou Angular).

>[!NOTE]
>
>AEM 6.4.5.0 ou posterior é necessário para usar os recursos de renderização do lado do servidor SPA conforme descrito neste documento.

## Visão geral {#overview}

Aplicativos de página única (SPA) podem oferecer ao usuário experiências ricas e dinâmicas que reagem e se comportam de formas familiares, normalmente como aplicativos nativos. [Isso é feito contando com o cliente para carregar o conteúdo antecipadamente e depois fazer o pesado levantamento da manipulação da interação do usuário](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) e, assim, minimizar a quantidade de comunicação necessária entre o cliente e o servidor, tornando o aplicativo mais reativo.

No entanto, isso pode levar a tempos de carregamento iniciais mais longos, especialmente se o SPA for grande e rico em seu conteúdo. Para otimizar os tempos de carregamento, parte do conteúdo pode ser renderizado no lado do servidor. O uso da renderização do lado do servidor (SSR) pode acelerar a carga inicial da página e, em seguida, transmitir mais renderização para o cliente.

## Quando utilizar o SSR {#when-to-use-ssr}

A RSS não é necessária em todos os projetos. Embora o AEM seja totalmente compatível com o JS SSR para SPA, o Adobe não recomenda implementá-lo sistematicamente para cada projeto.

Ao decidir implementar a SSR, você deve primeiro estimar qual complexidade adicional, esforço e custo adicional a SSR representa realisticamente para o projeto, incluindo a manutenção de longo prazo. Uma arquitetura RSS só deve ser escolhida quando o valor acrescentado exceder claramente os custos estimados.

O SSR geralmente fornece algum valor quando há um claro &quot;sim&quot; para qualquer uma das seguintes perguntas:

* **SEO:** O SSR ainda é necessário para que seu site seja indexado corretamente pelos mecanismos de pesquisa que trazem tráfego? Lembre-se de que os principais rastreadores de mecanismo de pesquisa agora avaliam o JS.
* **Velocidade da página:** O SSR fornece uma melhoria mensurável da velocidade em ambientes reais e adiciona à experiência geral do usuário?

Somente quando uma dessas duas perguntas for respondida com um &quot;sim&quot; claro para o seu projeto o Adobe recomenda a implementação do SSR. As seções a seguir descrevem como fazer isso usando o Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-io-runtime}

Se você [confiante de que o projeto requer a implementação do SSR](#when-to-use-ssr), Adobe recomendado é usar a solução Adobe I/O Runtime.

Para obter mais informações sobre o Adobe I/O Runtime, consulte

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - para obter uma visão geral do serviço
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - para obter documentação detalhada sobre a plataforma

As seções a seguir detalham como o Adobe I/O Runtime pode ser usado para implementar o SSR para seu SPA em dois modelos diferentes:

* [Fluxo de comunicação orientado por AEM](#aem-driven-communication-flow)
* [Fluxo de comunicação orientado por Adobe I/O-Runtime](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>O Adobe recomenda um espaço de trabalho Adobe I/O Runtime separado por ambiente (estágio, produção, teste etc.). Isso permite padrões típicos de ciclo de vida de desenvolvimento de sistemas (SDLC) com diferentes versões de um único aplicativo implantado em diferentes ambientes. Consulte o documento [CI/CD para aplicativos do Project App Builder](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) para obter mais informações.
>
>Um espaço de trabalho separado não é necessário por instância (autor, publicação), a menos que haja diferenças na implementação de tempo de execução por tipo de instância.

## Configuração do renderizador de conteúdo remoto {#remote-content-renderer-configuration}

AEM deve saber onde o conteúdo renderizado remotamente pode ser recuperado. Independente de [qual modelo você escolhe implementar para SSR](#adobe-io-runtime), será necessário especificar para AEM como acessar esse serviço de renderização remota.

Isso é feito por meio da variável **RemoteContentRenderer - Fábrica de Configuração** Serviço OSGi. Procure a string &quot;RemoteContentRenderer&quot; no console Configuração do Console da Web em `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Os seguintes campos estão disponíveis para a configuração:

* **Padrão de caminho de conteúdo** - Expressão regular para corresponder a uma parte do conteúdo, se necessário
* **URL do terminal remoto** - URL do endpoint responsável pela geração do conteúdo
   * Use o protocolo HTTPS seguro se não estiver na rede local.
* **Cabeçalhos de solicitação adicionais** - Cabeçalhos adicionais a serem adicionados à solicitação enviada ao terminal remoto
   * Padrão: `key=value`
* **Tempo limite da solicitação** - Tempo limite da solicitação de host remoto em milissegundos

>[!NOTE]
>
>Independentemente de você optar por implementar a variável [Fluxo de comunicação orientado por AEM](#aem-driven-communication-flow) ou [Fluxo orientado pela Adobe I/O Runtime](#adobe-io-driven-communication-flow), é necessário definir uma configuração remota do renderizador de conteúdo.
>
>Essa configuração também deve ser definida se você optar por [usar um servidor Node.js personalizado](#using-node-js).

>[!NOTE]
>
>Essa configuração utiliza o [Renderizador de conteúdo remoto](#remote-content-renderer), que tem opções adicionais de extensão e personalização disponíveis.

## Fluxo de comunicação orientado por AEM {#aem-driven-communication-flow}

Ao usar o SSR, a variável [fluxo de trabalho de interação do componente](/help/sites-developing/spa-overview.md#workflow) O SPA no AEM inclui uma fase na qual o conteúdo inicial do aplicativo é gerado pelo Adobe I/O Runtime.

1. O navegador solicita o conteúdo SSR do AEM.
1. AEM publica o modelo no Adobe I/O Runtime.
1. O Adobe I/O Runtime retorna o conteúdo gerado
1. AEM serve o HTML retornado pelo Adobe I/O Runtime por meio do template HTL do componente de página de back-end.

![server-side-rendering-cms-drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Fluxo de comunicação orientado pela Adobe I/O Runtime {#adobe-io-driven-communication-flow}

A seção [Fluxo de comunicação orientado por AEM](#aem-driven-communication-flow) descreve a implementação padrão e recomendada da renderização do lado do servidor no que diz respeito ao SPA no AEM, onde o AEM executa o bootstrapping e o fornecimento de conteúdo.

Como alternativa, o SSR pode ser implementado para que a Adobe I/O Runtime seja responsável pelo bootstrapping, revertendo efetivamente o fluxo de comunicação.

Ambos os modelos são válidos e aceitos pela AEM. No entanto, deve-se considerar as vantagens e desvantagens de cada um antes de implementar um modelo específico.

| Bootstrapping | Vantagens | Desvantagens |
|---|---|---|
| via AEM | O AEM gerencia bibliotecas injetáveis, quando necessário<br>Os recursos só precisam ser mantidos em AEM | Possivelmente desconhecido do desenvolvedor SPA |
| via Adobe I/O Runtime | Mais familiar aos desenvolvedores de SPA | Os recursos clientlib necessários para o aplicativo, como CSS e JavaScript, precisarão ser disponibilizados pelo desenvolvedor do AEM por meio da [`allowProxy` propriedade](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>Os recursos devem ser sincronizados entre o AEM e o Adobe I/O Runtime<br>Para habilitar a criação do SPA, pode ser necessário um servidor proxy para o Adobe I/O Runtime |

## Planejamento para SSR {#planning-for-ssr}

Geralmente, apenas parte de um aplicativo precisa ser renderizada no lado do servidor. O exemplo comum é o conteúdo que será exibido acima da dobra no carregamento inicial da página que precisa ser renderizado no lado do servidor. Isso economiza tempo fornecendo ao cliente conteúdo já renderizado. Conforme o usuário interage com a SPA, o conteúdo adicional é renderizado pelo cliente.

Ao considerar a implementação da renderização do lado do servidor para o seu SPA, é necessário revisar quais partes do aplicativo serão necessárias para SSR.

## Desenvolvimento de um SPA usando o SSR {#developing-an-spa-using-ssr}

SPA componentes podem ser renderizados pelo cliente (no navegador) ou pelo lado do servidor. Quando renderizado no lado do servidor, as propriedades do navegador, como tamanho e local da janela, não estarão presentes. Por conseguinte, os componentes SPA devem ser isóficos, não assumindo qualquer hipótese quanto ao local em que serão apresentados.

Para usar o SSR, será necessário implantar seu código no AEM e no Adobe I/O Runtime, que é responsável pela renderização do lado do servidor. A maioria do código será o mesmo, no entanto, as tarefas específicas do servidor serão diferentes.

## SSR para SPA em AEM {#ssr-for-spas-in-aem}

O SSR para SPA no AEM requer o Adobe I/O Runtime, que é chamado para a renderização do lado do servidor de conteúdo do aplicativo. No HTL do aplicativo, um recurso no Adobe I/O Runtime é chamado para renderizar o conteúdo.

Assim como o AEM suporta as estruturas Angular e React SPA prontas para uso, a renderização do lado do servidor também é compatível com os aplicativos Angular e React. Para obter mais detalhes, consulte a documentação do NPM para ambas as estruturas.

* Reagir: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Para obter um exemplo simplista, consulte o [Aplicativo de diário We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Ele renderiza todo o lado do servidor de aplicativos. Embora este não seja um exemplo real, ele ilustra o que é necessário para implementar o SSR.

>[!CAUTION]
>O [Aplicativo de diário We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) O é somente para fins de demonstração e, portanto, usa o Node.js como um exemplo simples, em vez da Adobe I/O Runtime recomendada. Este exemplo não deve ser usado para qualquer trabalho de projeto.

>[!NOTE]
>Qualquer projeto do AEM deve utilizar o [Arquétipo de projeto do AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=pt-BR), que aceita projetos SPA que usam o React ou Angular e utiliza o SDK do SPA.

## Uso de Node.js {#using-node-js}

O Adobe I/O Runtime é a solução recomendada para implementar o SSR para SPA no AEM.

Para instâncias de AEM no local, também é possível implementar o SSR usando uma instância Node.js personalizada da mesma forma como descrito acima. Embora isso seja suportado pelo Adobe, não é recomendado.

Node.js não é compatível com instâncias de AEM hospedadas por Adobe.

>[!NOTE]
>
>Se o SSR precisar ser implementado via Node.js, o Adobe recomenda uma instância diferente de Node.js para cada ambiente de AEM (autor, publicação, estágio etc.).

## Renderizador de conteúdo remoto {#remote-content-renderer}

O [Configuração do renderizador de conteúdo remoto](#remote-content-renderer-configuration) que é necessário para usar o SSR com seu SPA em AEM toques em um serviço de renderização mais generalizado que pode ser estendido e personalizado para atender às suas necessidades.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` é um serviço OSGi para recuperar conteúdo renderizado em um servidor remoto, como a partir do Adobe I/O. O conteúdo enviado para o servidor remoto é baseado no parâmetro de solicitação transmitido.

`RemoteContentRenderingService` pode ser inserido por inversão de dependência em um modelo Sling personalizado ou servlet, quando for necessária manipulação de conteúdo adicional.

Esse serviço é usado internamente pela variável [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

O `RemoteContentRendererRequestHandlerServlet` pode ser usada para definir programaticamente a configuração da solicitação. `DefaultRemoteContentRendererRequestHandlerImpl`, a implementação do manipulador de solicitação padrão fornecida permite criar várias configurações de OSGi para mapear um local na estrutura de conteúdo a um terminal remoto.

Para adicionar um Manipulador de solicitação personalizado, implemente o `RemoteContentRendererRequestHandler` interface. Certifique-se de definir a variável `Constants.SERVICE_RANKING` propriedade do componente para um número inteiro superior a 100, que é a classificação da variável `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configurar a configuração OSGi do manipulador padrão {#configure-default-handler}

A configuração do manipulador padrão deve ser configurada conforme descrito na seção [Configuração do renderizador de conteúdo remoto](#remote-content-renderer-configuration).

### Uso do Renderizador de Conteúdo Remoto {#usage}

Para ter uma busca de servlet e retornar algum conteúdo que possa ser inserido na página:

1. Verifique se o servidor remoto está acessível.
1. Adicione um dos seguintes trechos ao modelo HTL de um componente de AEM.
1. Opcionalmente, crie ou modifique as configurações do OSGi.
1. Procurar o conteúdo do seu site

Normalmente, o modelo HTL de um componente de página é o principal recipient de tal recurso.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Requisitos {#requirements}

Os servlets usam o Exportador de Modelo do Sling para serializar os dados do componente. Por padrão, ambas as variáveis `com.adobe.cq.export.json.ContainerExporter` e `com.adobe.cq.export.json.ComponentExporter` são compatíveis como adaptadores do Sling Model. Se necessário, você pode adicionar classes para as quais a solicitação deve ser adaptada ao uso da variável `RemoteContentRendererServlet` e a execução `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. As classes adicionais devem estender o `ComponentExporter`.
