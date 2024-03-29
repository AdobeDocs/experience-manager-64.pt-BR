---
title: Arquitetura dos formulários HTML5
seo-title: Architecture of HTML5 forms
description: Os formulários HTML5 são implantados como um pacote na instância de AEM incorporada e expõe a funcionalidade como ponto final REST em HTTP/S usando a arquitetura RESTful Apache Sling.
seo-description: HTML5 forms is deployed as a package within the embedded AEM instance and exposes the functionality as REST end point over HTTP/S using RESTful Apache Sling architecture.
uuid: f32f9946-20f6-4c64-b1bd-03882517e11a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 599f1925-a17e-4bae-93d9-b54edcee92b0
feature: Mobile Forms
exl-id: 5bb8b307-93f0-4ccd-89ac-de82d65021e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2042'
ht-degree: 0%

---

# Arquitetura dos formulários HTML5 {#architecture-of-html-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Arquitetura {#architecture}

A funcionalidade de formulários do HTML5 é implantada como um pacote dentro da instância de AEM incorporada e é exposta como um ponto final REST sobre HTTP/S usando RESTful [Arquitetura do Apache Sling](https://sling.apache.org/).

![02-aem-forms-architecture_large](assets/02-aem-forms-architecture_large.jpg)

### Uso da Estrutura Sling {#using-sling-framework}

[Apache Sling](https://sling.apache.org/) O é centrado em recursos. Usa um URL de solicitação para resolver o recurso pela primeira vez. Cada recurso tem uma **sling:resourceType** ou **sling:resourceSuperType**). Com base nessa propriedade, no método de solicitação e nas propriedades do URL da solicitação, um script sling é então selecionado para lidar com a solicitação. Esse script sling pode ser um JSP ou um servlet. Para formulários HTML5, **Perfil** nós atuam como recursos sling e **Renderizador de perfil** atua como o script de sling que lida com a solicitação para renderizar o formulário móvel com um perfil específico. A **Renderizador de perfil** é um JSP que lê parâmetros de uma solicitação e chama o serviço OSGi do Forms.

Para obter detalhes sobre o endpoint REST e os parâmetros de solicitação suportados, consulte [Renderizar modelo de formulário](/help/forms/using/rendering-form-template.md).

Quando um usuário faz uma solicitação de um dispositivo cliente, como um navegador iOS ou Android, o Sling primeiro resolve o Nó de perfil com base no URL da solicitação. Neste nó do perfil, ele lê **sling:resourceSuperType** e **sling:resourceType** para determinar todos os scripts disponíveis que podem lidar com essa solicitação de Renderização de formulário. Em seguida, ele usa seletores de solicitação do Sling junto com o método de solicitação para identificar o script mais adequado para lidar com essa solicitação. Quando a solicitação atinge um JSP do renderizador de perfil, o JSP chama o serviço OSGi da Forms.

Para obter mais detalhes sobre a resolução do script sling, consulte [Folha de Corte de AEM](https://docs.adobe.com/content/docs/en/cq/current/developing/sling_cheatsheet.html) ou [Composição do Url do Apache Sling](https://sling.apache.org/site/url-decomposition.html).

### Fluxo de chamada de processamento de formulário típico {#typical-form-processing-call-flow}

Os formulários HTML5 armazenam em cache todos os objetos intermediários necessários para processar (renderização ou envio) um formulário na primeira solicitação. Ele não armazena em cache os objetos dependentes dos dados, pois esses objetos provavelmente serão alterados.

O Formulário Móvel mantém dois níveis diferentes de cache, cache PreRender e Cache de Renderização. O cache preRender contém todos os fragmentos e imagens de um modelo resolvido e o cache Render contém conteúdo renderizado, como o HTML.

![Fluxo de trabalho de formulários HTML5](assets/cacheworkflow.png)
**Figura:** *Fluxo de trabalho de formulários HTML5*

Os formulários HTML5 não armazenam em cache modelos com referências ausentes de fragmentos e imagens. Se os formulários HTML5 levarem mais do que o tempo normal, verifique os registros do servidor para ver se há referências e avisos ausentes. Além disso, verifique se o tamanho máximo do objeto não foi atingido.

O serviço OSGi da Forms processa uma solicitação em duas etapas:

* **Geração de layout e estado inicial do formulário**: O serviço de renderização OSGi do Forms chama o componente Cache do Forms para determinar se o formulário já foi armazenado em cache e não foi invalidado. Se o formulário estiver armazenado em cache e for válido, ele fornecerá o HTML gerado a partir do cache. Se o formulário for invalidado, o serviço de renderização OSGi do Forms gera o Layout do formulário inicial e o Estado do formulário no formato XML. Esse XML é transformado em HTML layout e no Estado do formulário JSON inicial pelo serviço OSGi da Forms e armazenado em cache para solicitações subsequentes.
* **Forms pré-preenchido**: Durante a renderização, se um usuário solicitar formulários com dados pré-preenchidos, o serviço de renderização OSGi do Forms chamará o contêiner de serviço do Forms e gerará um novo estado de Formulário com dados unidos. No entanto, como o layout já foi gerado na etapa acima, essa chamada é mais rápida do que a primeira chamada. Essa chamada só executa a união de dados e os scripts são executados nos dados.

Se houver alguma atualização no formulário ou qualquer um dos ativos usados no formulário, o componente de cache de formulário a detectará e o cache desse formulário específico será invalidado. Quando o serviço OSGi da Forms conclui o processamento, o renderizador de perfil jsp adiciona referências e estilo da biblioteca JavaScript a esse formulário e retorna a resposta ao cliente. Um servidor Web típico como [Apache](https://httpd.apache.org/) pode ser usado aqui com a compactação HTML ativada. Um servidor da Web reduziria significativamente o tamanho da resposta, o tráfego da rede e o tempo necessário para transmitir os dados entre o servidor e a máquina cliente.

Quando um usuário envia o formulário, o navegador envia o estado do formulário no formato JSON para a [enviar proxy de serviço](/help/forms/using/service-proxy.md); em seguida, o proxy do serviço de envio gera um XML de dados usando dados JSON e envia esse XML de dados para enviar o terminal.

## Componentes {#components}

Você precisa de um pacote do complemento AEM Forms para ativar os formulários HTML5. Para obter informações sobre como instalar o pacote complementar do AEM Forms, consulte [Instalação e configuração do AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).

### Componentes do OSGi (adobe-lc-forms-core.jar) {#osgi-components-adobe-lc-forms-core-jar}

**Renderizador de Forms do Adobe XFA (com.adobe.livecycle.adobe-lc-forms-core)** é o nome de exibição do pacote OSGi de formulários do HTML5 quando visualizado na Visualização de pacote do console de administração do Felix (https://[host]:[porta]/system/console/bundles).

Esse componente contém componentes OSGi para renderização, gerenciamento de cache e configurações.

#### Serviço OSGi da Forms {#forms-osgi-service}

Este Serviço OSGi contém a lógica para renderizar um XDP como HTML e manipula a submissão de um formulário para gerar dados XML. Esse serviço usa o contêiner de serviço Forms. O contêiner de serviço Forms chama internamente o componente nativo `XMLFormService.exe` que executa o processamento.

Se uma solicitação de renderização for recebida, esse componente chamará o contêiner de serviço do Forms para gerar informações de layout e estado que são processadas posteriormente para gerar estados DOM de formulário HTML e JSON.

Esse componente também é responsável pela geração de dados XML a partir do JSON de estado de formulário enviado.

#### Componente de cache {#cache-component}

Os formulários HTML5 usam o armazenamento em cache para otimizar a taxa de transferência e o tempo de resposta. Você pode configurar o nível do serviço de cache para ajustar a compensação entre desempenho e uso do espaço.

<table> 
 <tbody> 
  <tr> 
   <th>Estratégia de cache</th> 
   <th>Descrição</th> 
  </tr> 
  <tr> 
   <td>Nenhum</td> 
   <td>Não armazenar artefatos em cache<br /> </td> 
  </tr> 
  <tr> 
   <td>Conservador</td> 
   <td>Armazenar em cache apenas artefatos intermediários que são gerados antes da renderização do formulário, como um modelo contendo fragmentos em linha e imagens</td> 
  </tr> 
  <tr> 
   <td>Agressivo</td> 
   <td>Conteúdo de HTML de cache renderizado<br /> Armazene em cache todos os artefatos em cache no nível Conservador.<br /> <strong>Observação</strong>: Essa estratégia resulta em melhor desempenho, mas consome mais memória para armazenar os artefatos em cache.</td> 
  </tr> 
 </tbody> 
</table>

Os formulários HTML5 executam o armazenamento em cache na memória usando a estratégia LRU. Se a estratégia de cache estiver definida como Nenhum cache, os dados existentes do cache não serão criados e, se houver, serão apagados. Além da estratégia de armazenamento em cache, você também pode configurar o tamanho total do cache na memória, o que pode ajudar a ter o limite máximo no tamanho do cache e, se for além disso, usará o modo LRU para liberar recursos do cache.

>[!NOTE]
>
>O cache na memória não é compartilhado entre nós do cluster.

#### Serviço de configuração {#configuration-service}

O Serviço de configuração permite ajustar os parâmetros de configuração e as configurações de cache para formulários HTML5.

Para atualizar essas configurações, vá para o CQ Felix Admin Console (disponível em `https://[server]:[port]/system/console/configMgr`), procure e selecione Configuração do Mobile Forms.

Você pode configurar o tamanho do cache ou desabilitar o cache usando o serviço de configuração. Você também pode ativar a depuração usando o parâmetro Opções de depuração. Mais informações sobre como depurar formulários podem ser encontradas em [Depuração de formulários HTML5](/help/forms/using/debug.md).

### Componentes de tempo de execução (adobe-lc-forms-runtime-pkg.zip) {#runtime-components-adobe-lc-forms-runtime-pkg-zip}

O Pacote de tempo de execução contém as bibliotecas do lado do cliente usadas para renderizar formulários HTML.

**Componentes importantes disponíveis como parte do pacote Runtime:**

#### Mecanismo de script {#scripting-engine}

A implementação do Adobe XFA suporta dois tipos de linguagens de script para permitir a execução lógica definida pelo usuário nos formulários: JavaScript e FormCalc.

O mecanismo de scripts do HTML Forms é gravado em JavaScript para oferecer suporte à API de scripts XFA em ambas as linguagens.

No momento da renderização, o script FormCalc é convertido (e armazenado em cache) em JavaScript no servidor e transparente para o usuário ou designer.

Esse mecanismo de script usa parte do recurso de ECMAScript5 como Object.defineProperty. O mecanismo/biblioteca é fornecido como Client Lib do CQ com o nome da categoria **xfaforms.profile**. Também fornece **API do FormBridge** para permitir que portais ou aplicativos externos interajam com o formulário. Usando o FormBridge, um aplicativo externo pode ocultar programaticamente determinados elementos, obter ou definir seus valores ou alterar seus atributos.

Para obter mais detalhes, consulte a [Form Bridge](/help/forms/using/form-bridge-apis.md) artigo 10. o

#### Mecanismo de layout {#layout-engine}

O layout e o aspecto visual dos formulários HTML5 são baseados nos recursos SVG 1.1, jQuery, BackBone e CSS3. A aparência inicial de um formulário é gerada e armazenada em cache no servidor. O ajuste desse layout inicial e quaisquer outras alterações adicionais no layout do formulário são gerenciadas no cliente. Para isso, o pacote Runtime contém um mecanismo de layout gravado em JavaScript e com base em jQuery/Backbone. Esse mecanismo manipula todos os comportamentos dinâmicos, como Adicionar/Remover instâncias repetíveis, Layout de objeto expansível. Esse mecanismo de layout renderiza um formulário uma página de cada vez. Inicialmente, um usuário exibe apenas uma página e a barra de rolagem horizontal é responsável apenas pela primeira página. No entanto, quando um usuário rola para baixo, a próxima página inicia a renderização. Essa representação página por página reduz a quantidade de tempo necessária para renderizar a primeira página em um navegador e melhora o desempenho percebido do formulário. Esse mecanismo/biblioteca faz parte do Client Lib do CQ com o nome da categoria **xfaforms.profile**.

O Mecanismo de layout também contém um conjunto de widgets usados para capturar o valor dos campos de formulário de um usuário. Esses widgets são modelados como [Widgets da interface do usuário do jQuery](https://api.jqueryui.com/jQuery.widget/) que implementam determinado contrato adicional para funcionar de maneira simples com o mecanismo de layout.

Para obter mais detalhes sobre widgets e os contratos correspondentes, consulte [Widgets personalizados para formulários HTML5](/help/forms/using/introduction-widgets.md).

#### Estilo {#styling}

O estilo associado aos elementos HTML é adicionado em linha ou com base no bloco CSS incorporado. Alguns estilos comuns que não dependem do formulário fazem parte do Client Lib do CQ com o nome da categoria xfaforms.profile.

Além das propriedades de estilo padrão, cada elemento de formulário também contém certas classes CSS com base no tipo de elemento, nome e outras propriedades. Usando essas classes, é possível redefinir os elementos especificando seu próprio CSS.

Para obter mais detalhes sobre estilos e classes padrão, consulte [Introdução a estilos](/help/forms/using/css-styles.md).

#### Script do lado do servidor e serviços da Web {#server-side-script-and-web-services}

Qualquer script marcado para executar no servidor ou marcado para chamar um serviço da Web (independentemente de onde está marcado para executar) sempre é executado no servidor.

O mecanismo de script do cliente:

1. Faz uma chamada síncrona para o servidor que passa o estado do Formulário atual no formato JSON
1. Executa o script ou o serviço da Web no servidor
1. Gera um novo estado JSON
1. Mescla o novo estado JSON no cliente quando a resposta é retornada.

#### Pacotes de recursos de localização {#localization-resource-bundles}

Os formulários HTML5 são compatíveis com os idiomas italiano (it), espanhol (es), português brasileiro (pt_BR), chinês simplificado (zh_CN), chinês tradicional (suporte limitado apenas) (zh_TW), coreano (ko_KR), inglês (en_US), francês (fr_FR), alemão (de_DE) e japonês (ja). Com base na localidade recebida no cabeçalho da solicitação, o Pacote de Recursos correspondente é enviado para o cliente. Esse pacote de recursos é adicionado ao JSP do perfil como um Client Lib do CQ com nome de categoria **xfaforms.I18N**. Você pode substituir a lógica de escolher o pacote de localidade no perfil.

### Componentes do Sling (adobe-lc-forms-content-pkg.zip) {#sling-components-adobe-lc-forms-content-pkg-zip}

O pacote Sling contém conteúdo relacionado a Perfis e Renderizador de perfil.

#### Perfis {#profiles}

Perfis são os nós de recurso no sling que representam um formulário ou família de Forms. No nível do CQ, esses perfis são nós JCR. Os nós residem sob o **/conteúdo** pasta no repositório JCR e pode estar dentro de qualquer subpasta na **/conteúdo** pasta.

#### Renderizadores de perfil {#profile-renderers}

O nó Perfil tem uma propriedade **sling:resourceSuperType** com valor **xfaforms/profile**. Essa propriedade envia internamente solicitações de encaminhamento para o script sling para os nós do Perfil localizados na **/libs/xfaforms/profile** pasta. Esses scripts são páginas JSP, que são contêineres para unir os formulários HTML e os artefatos JS/CSS necessários. As páginas incluem referências a:

* **xfaforms.I18N.&lt;locale>**: Esta biblioteca contém dados localizados.
* **xfaforms.profile**: Esta biblioteca contém implementação para scripts XFA e mecanismo de layout.

Essas bibliotecas são modeladas como Bibliotecas do cliente CQ, o que tira vantagens dos recursos de concatenação automática, minificação e compactação das bibliotecas JavaScript da estrutura do CQ.\
Para obter mais informações sobre as bibliotecas do cliente CQ, consulte [Documentação da Clientlib CQ](https://docs.adobe.com/docs/en/cq/current/developing/components/clientlibs.html).

Como descrito acima, o renderizador de perfil JSP chama o Forms Service por meio de uma inclusão de sling. Esse JSP também define várias opções de depuração com base na configuração do administrador ou nos parâmetros de solicitação.

Os formulários HTML5 permitem que os desenvolvedores criem o Perfil e o Renderizador de perfil para personalizar a aparência dos formulários. Por exemplo, formulários HTML permitem que os desenvolvedores integrem formulários em um painel ou &lt;div> de um HTML portal existente.\
Para obter mais detalhes sobre como criar perfis personalizados, consulte [Criação de um perfil personalizado](/help/forms/using/custom-profile.md).
